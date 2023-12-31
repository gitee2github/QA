![avatar](../images/openEuler.png)

版权所有 © 2022  openEuler社区
您对“本文档”的复制、使用、修改及分发受知识共享(Creative Commons)署名—相同方式共享4.0国际公共许可协议(以下简称“CC BY-SA 4.0”)的约束。为了方便用户理解，您可以通过访问https://creativecommons.org/licenses/by-sa/4.0/ 了解CC BY-SA 4.0的概要 (但不是替代)。CC BY-SA 4.0的完整协议内容您可以访问如下网址获取：https://creativecommons.org/licenses/by-sa/4.0/legalcode。

修订记录

| 日期 | 修订   版本 | 修改描述 | 作者 |
| ---- | ----------- | -------- | ---- |
|2022年3月22日|初稿             |混合部署测试报告 |惠瑞楠      |

 关键词： 
混合部署、Rubik
 

摘要：

 

缩略语清单：

| 缩略语 | 英文全名 | 中文解释 |
| ------ | -------- | -------- |
|        |          |          |
|        |          |          |

# 1     特性概述

服务器资源利用率低一直是业界公认的难题，随着云原生技术的发展，将在线离线业务混合部署成为了当下提高资源利用率有效手段。Rubik容器调度在业务混合部署的场景下，根据QoS分级，对资源进行合理调度，从而实现在保障在线业务的服务体验情况下，大幅提升CPU和内存资源利用率。

Rubik以daemonSet形式部署在每一个k8s node节点上，北向接口采用HTTP API与kubelet通信。在kubelet启动容器时增加调用rubik接口流程，发送对应pod的QosLevel信息给rubik，rubik根据接收到的pod信息，往pod对应的cpu/memory子cgroup文件cpu.qos_level/memory.qos_level中写入值（在线业务为0，离线业务为-1）设置其优先级。内核根据cgroup优先级值对pod进程进行优先级设置，保证在线业务进程的抢占能力和稳定性。除启动pod设置cgroup优先级外，rubik还支持更新pod优先级，启动校验等功能。


# 2     特性测试信息

本节描述被测对象的版本信息和测试的时间及测试轮次，包括依赖的硬件。

| 版本名称                                | 测试起始时间  | 测试结束时间 |
| --------                                | ------------ | ------------ |
| openEuler-22.03-LTS:2022-03-05-12-01-45 |2022-03-07    | 2022-03-08   |

# 3     测试结论概述

## 3.1   测试整体结论
Rubik特性，共计执行55个用例，主要覆盖了功能测试、异常配置测试、安全测试、性能测试，当前ARM在配置CPU限制场景下存在优先级设置无效的风险，遗留风险小，整体质量良好。

## 3.2   约束说明

•rubik接受HTTP请求并发量上限1000QPS，并发量超过上限则报错。
•rubik接受的单个请求中pod上限为100个，pod数量越界则报错。
•每个k8s节点只能部署一个rubik，多个rubik会冲突。
•rubik不提供端口访问，只能通过sock通信。
•rubik只接收合法http请求路径及网络协议：http://localhost/（POST）、http://localhost/ping（GET）、http://localhost/version（GET）。
•rubik磁盘使用需求，配额1GB+。
•rubik内存使用需求，配额100MB+。
•kubelet创建pod时需要调用rubik并确保成功，否则不保证数据一致性。
•禁止低优先级往高优先级切换。如业务A先被设置为低优先级（-1），接着请求设置为高优先级（0），rubik报错。
•用户添加注解、修改注解、修改yaml中的注解并重新apply等操作不会触发Pod重建。Rubik不会监控Pod注解变化情况，因此Pod的优先级和注解一致性需要kubelet及上层组件保证。
•rubik不接受任何命令行参数，若添加参数启动会报错退出。
•容器挂载目录时，rubik本地套接字/run/rubik的目录权限需由业务侧保证最小权限（如700）。
•rubik服务端可用时，单个请求超时时间为120s。如果rubik进程进入T、D状态，则服务端不可用，此时服务不会响应任何请求。为了避免此情况的发生，请在客户端设置超时时间，避免无限等待。
•禁止将任务从在线组迁移到离线组后再迁移回在线组，此操作会导致该任务QoS异常。
•禁止将重要的系统服务和内核线程加入到离线组中，否则可能导致调度不及时，进而导致系统异常。
•cpu和memory的在线、离线配置需要统一，否则可能导致两个子系统的QoS冲突。
•使用混部后，原始的cpu share功能存在限制。具体表现为：
若当前cpu中同时存在在线任务和离线任务，则离线任务的cpu share无法生效。
若当前cpu中只有在线任务或只有离线任务，cpu share能生效。

•用户态的优先级反转、smt、cache、numa负载均衡、离线任务的负载均衡，当前不支持。


## 3.3   遗留问题分析

### 3.3.1 遗留问题影响以及规避措施

| 问题单号 | 问题描述 | 问题级别 | 问题影响和规避措施 | 当前状态 |
| -------- | -------- | -------- | ------------------ | -------- |
| https://gitee.com/src-openeuler/rubik/issues/I4XOBG?from=project-issue         | ARM环境下，当容器绑核，混部优先级限制失效         |  一般        | 优先级反转的特性还没有上库，之前讨论是在update版本提供                   |  挂起        |

### 3.3.2 问题统计

|        | 问题总数 | 严重 | 主要 | 次要 | 不重要 |
| ------ | -------- | ---- | ---- | ---- | ------ |
| 数目   |  1        |      |      |   1   |        |
| 百分比 |  100%        |      |      | 100%     |        |

# 4     测试执行

## 4.1   测试执行统计数据

*本节内容根据测试用例及实际执行情况进行特性整体测试的统计，可根据第二章的测试轮次分开进行统计说明。*

| 版本名称 | 测试用例数 | 用例执行结果 | 发现问题单数 |
| -------- | ---------- | ------------ | ------------ |
| openEuler-22.03-LTS:2022-03-05-12-01-45         |  55   |  arm环境失败3个   |   1个           |

失败的3个用例均与容器绑核有关，且只在arm环境下失败（X86全量测试通过）

*数据项说明：*

*测试用例数－－到本测试活动结束时，所有可用测试用例数；*

*发现问题单数－－本测试活动总共发现的问题单数。*
 