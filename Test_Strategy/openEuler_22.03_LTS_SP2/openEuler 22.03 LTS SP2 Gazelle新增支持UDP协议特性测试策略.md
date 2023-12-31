![openEuler ico](../../images/openEuler.png)

版权所有 © 2023 openEuler社区  
您对“本文档”的复制、使用、修改及分发受知识共享(Creative Commons)署名—相同方式共享4.0国际公共许可协议(以下简称“CC BY-SA
4.0”)的约束。为了方便用户理解，您可以通过访问<https://creativecommons.org/licenses/by-sa/4.0/>了解CC BY-SA 4.0的概要 (但不是替代)。CC BY-SA
4.0的完整协议内容您可以访问如下网址获取：<https://creativecommons.org/licenses/by-sa/4.0/legalcode>。

 修订记录

| 日期 | 修订版本     | 修改描述  | 作者 |
| ---- | ----------- | -------- | ---- |
| 2023-05-18 |  1.0.0    |  初稿     | shidongdong |

关键词：Gazelle 用户态协议栈

摘要：Gazelle是一款高性能用户态协议栈。它基于DPDK在用户态直接读写网卡报文，共享大页内存传递报文，使用轻量级LwIP协议栈。能够大幅提高应用的网络I/O吞吐能力。专注于数据库网络性能加速

缩略语清单：

| 缩略语 | 英文全名 | 中文解释 |
| ------ | -------- | -------- |


# 特性描述
<!-- 主要介绍特性实现的背景、功能以及作用 -->
背景：内核态网络协议栈读写时延较长，I/O吞吐能力有局限性，业界对时延要求非常高
功能：Gazelle支持UDP协议的报文

## 需求清单
|no|feature|status|sig|owner|发布方式|涉及软件包列表|
|:----|:---|:---|:--|:----|:----|:----|
|[I727E2](https://gitee.com/openeuler/release-management/issues/I727E2)| 【openEuler 22.03 LTS SP2】Gazelle新增支持UDP协议 | Developing |sig-high-performance-network| @kircher| ISO  | gazelle |

## 风险项
<!-- 主要描述特性已知风险项 -->
- 暂无

# 特性分层策略
## 总体测试策略
<!-- 主要描述特性的整体测试策略，主要开展哪些测试(接口/功能/场景/专项) -->
- 测试目标：Gazelle正常支持UDP协议报文
- 时间进度：待评估
- 风险评估：NA
- 重点事项：需求所述功能正常，系统运行正常
- 争议事项：NA


## 特性测试约束
<!-- 主要描述特性测试的约束条件 -->
NA

## 接口测试
<!-- 主要描述接口级测试策略及测试设计思路 -->
| 接口描述 | 设计思路 | 测试重点 | 备注 |
| ------- | ------- | ------- | ---- |
| NA | NA  | NA  | NA  |


## 功能测试
<!-- 主要描述特性提供的功能的测试策略及测试思路 -->
| 功能描述 | 设计思路 | 测试重点 | 备注 |
| ------- | ------- | ------- | ---- |
| gazelle功能 | 可正常支持UDP收发包 |   |      |


## 场景测试
<!-- 主要描述对特性使用的主要场景的测试策略及测试思路 -->
| 场景描述 | 设计思路 | 测试重点 | 备注 |
| ------- | ------- | ------- | ---- |
| UDP场景测试 | 支持单播/组播收发包 |  |  |

## 专项测试
<!-- 主要描述其他专项测试,如安全测试 稳定性测试 性能测试 兼容性测试等 -->
| 专项测试类型 | 专项测试描述 | 测试预期结果 | 备注 |
| ----------- | ----------- | ----------- | ---- |
| 兼容性测试 | 继承功能不变 |  |      |
| 可靠性测试 | 特性长稳执行，没有资源泄露，网络异常，收发包丢包等问题 |  |      |

# 特性测试环境描述
<!-- 主要描述执行测试的硬件信息 -->
| 硬件型号 | 硬件配置信息 | 备注 |
| -------- | ------------ | ---- |

# 特性测试执行策略

## 测试计划
<!-- 测试执行策略主要描述该轮次执行的分层策略中的测试项 -->
| Stange name   | Begin time | End time   | Days | 测试执行策略                   | 备注   |
| :------------ | :--------- | :--------- | ---- | ----------------------------- | ------ |
|     round2-round3          |  2023-05-24          |2023-06-09         | 16     | 全量测试                               |        |
|     round4           |   2023-06-10         |  2023-06-16          |7      |   回归测试                            |        |


# 入口标准  
1.特性满足质量标准，达成需求设计要求目标

# 出口标准  
1.策略规划的测试活动涉及测试用例100%执行完毕  
2.版本无严重问题遗留，其他问题有规避措施

# 附件