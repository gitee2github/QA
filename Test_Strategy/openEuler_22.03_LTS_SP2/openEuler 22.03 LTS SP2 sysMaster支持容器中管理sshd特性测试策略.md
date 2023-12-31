![openEuler ico](../../images/openEuler.png)

版权所有 © 2023 openEuler社区  
您对“本文档”的复制、使用、修改及分发受知识共享(Creative Commons)署名—相同方式共享4.0国际公共许可协议(以下简称“CC BY-SA
4.0”)的约束。为了方便用户理解，您可以通过访问<https://creativecommons.org/licenses/by-sa/4.0/>了解CC BY-SA 4.0的概要 (但不是替代)。CC BY-SA
4.0的完整协议内容您可以访问如下网址获取：<https://creativecommons.org/licenses/by-sa/4.0/legalcode>。

 修订记录

| 日期 | 修订版本     | 修改描述  | 作者 |
| ---- | ----------- | -------- | ---- |
| 2023-05-16 |  1.0.0    |  初稿     | shidongdong |

关键词：sysMaster

摘要：sysMaster作为传统init守护进程的优化版本，引入多种故障检测和自愈技术。在系统容器场景中，可以支持sshd服务管理

缩略语清单：

| 缩略语 | 英文全名 | 中文解释 |
| ------ | -------- | -------- |


# 特性描述
<!-- 主要介绍特性实现的背景、功能以及作用 -->
背景：传统的init守护进程，功能冗余复杂，问题长期不收敛。可靠性不足
功能：sysmaster在容器中提可作为1号进程提供特定服务管理能力，当前重点支持sshd服务的管理

## 需求清单
|no|feature|status|sig|owner|发布方式|涉及软件包列表|
|:----|:---|:---|:--|:----|:----|:----|
|[I6VFA7](https://gitee.com/openeuler/release-management/issues/I6VFA7)| [openEuler 22.03-LTS SP2] 添加sysMaster组件，支持系统容器中拉起运行sshd服务 | Developing |dev-utils |@overweight | ISO  | sysMaster |

## 风险项
<!-- 主要描述特性已知风险项 -->
- 暂无

# 特性分层策略
## 总体测试策略
<!-- 主要描述特性的整体测试策略，主要开展哪些测试(接口/功能/场景/专项) -->
- 测试目标：sysmaster在容器中可管理sshd服务
- 时间进度：待评估
- 风险评估：NA
- 重点事项：在自研容器以及开源容器中，均可以正常管理sshd服务功能，容器运行正常
- 争议事项：NA


## 特性测试约束
<!-- 主要描述特性测试的约束条件 -->
在特定场景作为替代的1号进程使用，该场景是系统容器中运行sysMaster来管理sshd服务。

## 接口测试
<!-- 主要描述接口级测试策略及测试设计思路 -->
| 接口描述 | 设计思路 | 测试重点 | 备注 |
| ------- | ------- | ------- | ---- |
| NA | NA  | NA  | NA  |


## 功能测试
<!-- 主要描述特性提供的功能的测试策略及测试思路 -->
| 功能描述 | 设计思路 | 测试重点 | 备注 |
| ------- | ------- | ------- | ---- |
| sshd服务状态 | 启动，停止，重启服务操作正常，服务状态正常 |   |      |
| sshd服务功能 | 启动，停止，重启服务操作正常，服务功能正常 |   |      |


## 场景测试
<!-- 主要描述对特性使用的主要场景的测试策略及测试思路 -->
| 场景描述 | 设计思路 | 测试重点 | 备注 |
| ------- | ------- | ------- | ---- |
| sysmaster场景测试 | 在不同容器引擎中，操作sshd服务，sshd服务状态均正常，sshd服务功能也正常 |  |  |

## 专项测试
<!-- 主要描述其他专项测试,如安全测试 稳定性测试 性能测试 兼容性测试等 -->
| 专项测试类型 | 专项测试描述 | 测试预期结果 | 备注 |
| ----------- | ----------- | ----------- | ---- |
| 可靠性测试 | sysmaster服务可靠性测试，关注内存资源使用 |  |      |
| 安全测试 | sysmaster安全性操作 |  |      |

# 特性测试环境描述
<!-- 主要描述执行测试的硬件信息 -->
| 硬件型号 | 硬件配置信息 | 备注 |
| -------- | ------------ | ---- |

# 特性测试执行策略

## 测试计划
<!-- 测试执行策略主要描述该轮次执行的分层策略中的测试项 -->
| Stange name   | Begin time | End time   | Days | 测试执行策略                   | 备注   |
| :------------ | :--------- | :--------- | ---- | ----------------------------- | ------ |
|     round2-round3          |  2023-05-24          |2023-06-09          | 16     | 全量测试                               |        |
|     round4           |   2023-06-10         |  2023-06-16          |7      |   回归测试                            |        |


# 入口标准  
1.特性满足质量标准，达成需求设计要求目标

# 出口标准  
1.策略规划的测试活动涉及测试用例100%执行完毕  
2.版本无严重问题遗留，其他问题有规避措施

# 附件