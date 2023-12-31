![openEuler ico](../../images/openEuler.png)

版权所有 © 2023 openEuler社区  
您对“本文档”的复制、使用、修改及分发受知识共享(Creative Commons)署名—相同方式共享4.0国际公共许可协议(以下简称“CC BY-SA
4.0”)的约束。为了方便用户理解，您可以通过访问<https://creativecommons.org/licenses/by-sa/4.0/>了解CC BY-SA 4.0的概要 (但不是替代)。CC BY-SA
4.0的完整协议内容您可以访问如下网址获取：<https://creativecommons.org/licenses/by-sa/4.0/legalcode>。

 修订记录

| 日期 | 修订版本     | 修改描述  | 作者 |
| ---- | ----------- | -------- | ---- |
| 2023-02-13 |  1.0.0    |  初稿     | shidongdong |

关键词： kmesh,网格数据面

 
摘要：
随着对serviceMesh应用的逐步深入，当前基于sidecar的网格架构在数据面存在明显的时延性能差，底噪开销大等问题；Kmesh基于可编程内核，将网格流量治理下沉OS，数据路径3跳->1跳，大幅提升网格数据面的时延性能


缩略语清单：

| 缩略语 | 英文全名 | 中文解释 |
| ------ | -------- | -------- |
|OS|Operating System|操作系统|


# 特性描述
<!-- 主要介绍特性实现的背景、功能以及作用 -->

## 需求清单
|no|feature|status|sig|owner|发布方式|涉及软件包列表|
|:----|:---|:---|:--|:----|:----|:----|
|[I65S7M](https://gitee.com/openeuler/release-management/issues/I65S7M?from=project-issue)| 【openEuler 23.03】新增高性能服务网格数据面Kmesh   | Testing   |sig-high-performance-network   | @MrRlu    | extras    | kmesh    |

## 风险项
<!-- 主要描述特性已知风险项 -->
- 暂无

# 特性分层策略
## 总体测试策略
<!-- 主要描述特性的整体测试策略，主要开展哪些测试(接口/功能/场景/专项) -->
- 测试目标：Kmesh功能，性能目标达成
- 时间进度：待评估
- 风险评估：NA
- 重点事项：kmesh功能可满足需求设计规格要求；时延性能达到需求预期目标
- 争议事项：NA


## 特性测试约束
<!-- 主要描述特性测试的约束条件 -->
NA

## 接口测试
<!-- 主要描述接口级测试策略及测试设计思路 -->
| 接口描述 | 设计思路 | 测试重点 | 备注 |
| ------- | ------- | ------- | ---- |
| kmesh-deamon | 等价类参数测试 | 等价类参数  |      |
| kmesh服务 | 服务启动/重启 | 各种操作以后服务状态 |      |

## 功能测试
<!-- 主要描述特性提供的功能的测试策略及测试思路 -->
| 功能描述 | 设计思路 | 测试重点 | 备注 |
| ------- | ------- | ------- | ---- |
|   升级   |kmesh服务启动以后，执行安装包升级|      |
|   kmesh规则   |启动服务，导入规则后重启服务         |      |

## 场景测试
<!-- 主要描述对特性使用的主要场景的测试策略及测试思路 -->
| 场景描述 | 设计思路 | 测试重点 | 备注 |
| ------- | ------- | ------- | ---- |
| fortio场景测试 | 部署istiod业务，配置并启动kmesh，部署fortio客户端服务端，客户端像服务端打流 |  |  |

## 专项测试
<!-- 主要描述其他专项测试,如安全测试 稳定性测试 性能测试 兼容性测试等 -->
| 专项测试类型 | 专项测试描述 | 测试预期结果 | 备注 |
| ----------- | ----------- | ----------- | ---- |
| 性能测试 | 验证预期性能目标 | 时延性能达到需求预期目标 |      |

# 特性测试环境描述
<!-- 主要描述执行测试的硬件信息 -->
| 硬件型号 | 硬件配置信息 | 备注 |
| -------- | ------------ | ---- |

# 特性测试执行策略

## 测试计划
<!-- 测试执行策略主要描述该轮次执行的分层策略中的测试项 -->
| Stange name   | Begin time | End time   | Days | 测试执行策略                   | 备注   |
| :------------ | :--------- | :--------- | ---- | ----------------------------- | ------ |
|     round1-round2          |  2023/2/20          |2023/3/3           | 13     | 全量测试                               |        |
|     round3           |   2023/3/6         |  2023/3/10          |5      |   回归测试                            |        |


# 入口标准  
1.特性满足质量标准，功能以及性能达成目标

# 出口标准  
1.策略规划的测试活动涉及测试用例100%执行完毕  
2.版本无严重问题遗留，其他问题有规避措施

# 附件
