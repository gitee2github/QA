![openEuler ico](https://gitee.com/openeuler/QA/raw/master/images/openEuler.png)

版权所有 © 2023 openEuler社区
您对“本文档”的复制、使用、修改及分发受知识共享(Creative Commons)署名—相同方式共享4.0国际公共许可协议(以下简称“CC BY-SA 4.0”)的约束。为了方便用户理解，您可以通过访问[https://creativecommons.org/licenses/by-sa/4.0/](https://gitee.com/link?target=https%3A%2F%2Fcreativecommons.org%2Flicenses%2Fby-sa%2F4.0%2F)了解CC BY-SA 4.0的概要 (但不是替代)。CC BY-SA 4.0的完整协议内容您可以访问如下网址获取：[https://creativecommons.org/licenses/by-sa/4.0/legalcode](https://gitee.com/link?target=https%3A%2F%2Fcreativecommons.org%2Flicenses%2Fby-sa%2F4.0%2Flegalcode)。

修订记录

| 日期      | 修订版本 | 修改章节 | 修改描述 | 作者     |
| --------- | -------- | -------- | -------- | -------- |
| 2023-5-16 | 1.0.0    |          | 初稿     | liyidong |

关键词：安全

摘要：本文为openEuler 22.03 SP2版本安全测试策略，用于指导后续安全测试活动的开展

缩略语清单：

| 缩略语 | 英文全名                             | 中文解释       |
| ------ | ------------------------------------ | -------------- |
| OS     | Operation System                     | 操作系统       |
| CVE    | Common Vulnerabilities and Exposures | 公共漏洞和暴露 |



# 特性描述

openEuler 22.03 SP2版本无安全相关新增需求。

## 需求清单

openEuler 22.03 SP2版本无安全相关新增需求。

## 风险项

# 测试分层策略

## 总体测试策略

openEuler作为社区开源版本，在系统整体安全上需要进行保证，以发现系统中存在的安全脆弱性与风险，为版本的安全提供切实的依据，推动产品完成安全问题整改，提高产品的安全。整体安全测试需要覆盖：

1. linux系统安全配置/权限管理等
2. 特性涉及到的安全需求验证
3. CVE漏洞/敏感信息/端口矩阵/交付件病毒扫描
4. 白盒安全测试

| 测试类         | 描述                      | 具体测试内容                                                 |
| -------------- | ------------------------- | ------------------------------------------------------------ |
| 安全扫描类     | CVE扫描/敏感信息/编译选项 | 通过工具进行相应的扫描，扫描结果采用增量的方式进行分析；编译选项和敏感信息需要针对新开源特性及新增软件包进行； |
| 安全配置管理类 | Linux安全规范             | Linux安全规范包括：服务管理，账号密码管理、文件及用户权限管理、内核参数配置管理、日志管理等；需对openEuler版本进行上述安全配置测试 |
| 白盒安全测试类 | Fuzz测试                  | Fuzz测试是能发现接口参数类问题和内存相关问题的有效方法，所以需要针对操作系统重点软件包开展fuzz；通过部署kasan版本的内核，进行syzkaller的测试；对重点软件包开展oss-fuzz测试；利用开源测试工具csmith/javafuzzer/jfuzz对对编译器组件进行fuzz测试；虚拟化组件qemu的asan版本开展fuzz测试； |

## 安全扫描类测试

| 测试内容         | 测试策略                                           |
| ---------------- | -------------------------------------------------- |
| 开源软件漏洞扫描 | 针对全量开源软件进行漏洞扫描                       |
| 安全编译选项扫描 | 针对新开源特性及新增软件包进行安全编译选项扫描     |
| 敏感信息扫描     | 针对新开源特性及新增软件包进行敏感信息扫描         |
| 病毒扫描         | 对交付件进行病毒扫描                               |
| 开放端口扫描     | 对安装后操作系统进行开发端口扫描，确认开放端口范围 |

## 安全配置管理类测试

对质量目标涉及安全属性进行测试，测试策略如下：

| 安全属性               | 是否涉及 | 测试策略                   |
| ---------------------- | -------- | -------------------------- |
| 访问通道控制           | 不涉及   |                            |
| 操作系统安全           | 涉及     | 存量用例执行               |
| 协议与接口防攻击       | 涉及     | 存量用例执行               |
| Web安全                | 不涉及   |                            |
| 数据库安全             | 不涉及   |                            |
| 敏感数据保护           | 涉及     | 存量用例执行               |
| 系统管理               | 涉及     | 存量用例执行               |
| 安全资料               | 涉及     | 存量用例执行               |
| 监听接口及防止非法监听 | 涉及     | 存量用例执行，安全工具扫描 |



## 白盒安全类测试

Fuzz测试工具：oss-fuzz

测试策略：对重点软件包开展oss-fuzz测试。

# 特性测试执行策略

## 测试计划

| Stage name   | Begin time | End time  | Days | Note                                                         |
| ------------ | ---------- | --------- | ---- | ------------------------------------------------------------ |
| Test round 1 | 2023/5/17  | 2023/5/23 | 7    | 开源软件漏洞扫描、安全编译选项扫描、自研加固类测试           |
| Test round 2 | 2023/5/24  | 2023/6/2  | 7    | 敏感信息扫描、病毒扫描、Fuzz测试                             |
| Test round 3 | 2023/6/3   | 2023/6/9 | 7    | 端口扫描、安全组件测试、加固指南测试、自研加固类测试         |
| Test round 4 | 2023/6/10  | 2023/6/16 | 7    | 开源软件漏洞扫描、安全编译选项扫描、病毒扫描、加固指南测试、自研加固类测试 |
| Test round 5 | 2023/6/17  | 2023/6/23 | 7    | 敏感信息扫描、端口扫描、安全组件测试                         |

## 入口标准

1. 转测版本的冒烟无阻塞性问题

## 出口标准

1. 策略规划的测试活动涉及用例100%执行完毕
2. 版本无安全问题遗留

# 附件

无
