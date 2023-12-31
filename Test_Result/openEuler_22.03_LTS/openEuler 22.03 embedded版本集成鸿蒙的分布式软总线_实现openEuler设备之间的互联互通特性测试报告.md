![openEuler ico](../../images/openEuler.png)

版权所有 © 2022  openEuler社区
 您对“本文档”的复制、使用、修改及分发受知识共享(Creative Commons)署名—相同方式共享4.0国际公共许可协议(以下简称“CC BY-SA 4.0”)的约束。为了方便用户理解，您可以通过访问https://creativecommons.org/licenses/by-sa/4.0/ 了解CC BY-SA 4.0的概要 (但不是替代)。CC BY-SA 4.0的完整协议内容您可以访问如下网址获取：https://creativecommons.org/licenses/by-sa/4.0/legalcode。

修订记录

| 日期 | 修订   版本 | 修改描述 | 作者 |
| ---- | ----------- | -------- | ---- |
| 2022-03-29 | 1.0 | 创建 | @saarloos |
| 2022-03-30 | 1.1 | 更新测试数据 | @Jevin  |

关键词：
鸿蒙 分布式软总线


摘要：

本报告主要描述基于openEuler 22.03-LTS embedded版本进行的集成鸿蒙的分布式软总线，实现openEuler设备之间的互联互通特性的测试过程，报告对测试情况进行说明，对特性的测试充分度进行评估和总结。


缩略语清单：

| 缩略语 | 英文全名 | 中文解释 |
| ------ | -------- | -------- |
|  |  |  |

***

# 1     特性概述

将OpenHarmony的分布式软总线能力迁移到openEuler，实现欧拉嵌入式设备间的互通互联。
具体能力如下：
1.软总线独立构建能力
2.支持coap协议的设备发现能力
3.支持以太网的数据传输能力
4.软总线依赖能力替换（system ability、认证、IPC等）

# 2     特性测试信息

本节描述被测对象的版本信息和测试的时间及测试轮次，以及硬件环境信息。

| 版本名称 | 测试起始时间 | 测试结束时间 |
| -------- | ------------ | ------------ |
| openEuler embedded 22.03 RC5 | 2022/3/29  | 2022/3/31   |

描述特性测试的硬件环境信息

| 硬件型号 | 硬件配置信息 | 备注 |
| -------- | ------------ | ---- |
| 树莓派4B卡 | CPU:BCM2711(Cortex-A72 * 4) <br />内存：4GB/8GB <br />存储设备：SanDisk Ultra 64GB micro SD |        |
| qemu | CPU:Cortex-A15/A57 <br /> 最小启动内存：512M |        |

# 3     测试结论概述

## 3.1   测试整体结论

<!-- 测试结论可以以一句话描述，如：XX特性，共计执行XX个用例，主要覆盖了XX测试和XX测试，通过经过fuzz和7*24的长稳测试，发现问题已解决，回归通过，无遗留风险，整体质量良好；或者表格的方式进行说明 -->

分布式软总线能力特性，在标准以太网的连接方式下，测试了两台嵌入式设备间的发现、连接和传输的API接口，验证了不同设备间基于dsoftbus通信的互通互联，共计执行10个用例，主要覆盖了接口测试、功能测试，发现问题已解决，回归通过，无遗留风险，整体质量良好；

| 测试活动 | 活动评价 |
| -------- | -------- |
| 接口测试 |     测试了publishservice等用户接口的参数测试，测试通过     |
| 功能测试 |     通过2~3台设备组网，覆盖发布、发现、传输等功能场景，测试通过     |


## 3.2   约束说明
  无

## 3.3   遗留问题分析

### 3.3.1 遗留问题影响以及规避措施

| 问题单号 | 问题描述 | 问题级别 | 问题影响和规避措施 | 当前状态 |
| -------- | -------- | -------- | ------------------ | -------- |
|          |          |          |                    |          |
|          |          |          |                    |          |

### 3.3.2 问题统计


|      | 问题总数 | 严重 | 主要 | 次要 | 不重要 |
| ------ | -------- | ---- | ---- | ---- | ------ |
| 数目   |   4       |  1    |  2    |   1   |        |
| 百分比 |    100%      |  25%    |   50%   |   25%   |        |


# 4     测试执行

## 4.1   测试执行统计数据

*本节内容根据测试用例及实际执行情况进行特性整体测试的统计，可根据第二章的测试轮次分开进行统计说明。*

| 版本名称 | 测试用例数 | 用例执行结果 | 发现问题单数 |
| -------- | ---------- | ------------ | ------------ |
| openEuler embedded 22.03 RC4 |       10     |      测试通过        |       1       |
| openEuler embedded 22.03 RC5 |       10     |      测试通过        |       3       |

*数据项说明：*

*测试用例数－－到本测试活动结束时，所有可用测试用例数；*

*发现问题单数－－本测试活动总共发现的问题单数。*

## 4.2   后续测试建议

后续测试需要关注点(可选)

# 5     附件

*此处可粘贴各类专项测试数据或报告*
