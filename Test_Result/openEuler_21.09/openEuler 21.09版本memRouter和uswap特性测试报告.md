![openEuler ico](../../images/openEuler.png)

版权所有 © 2021  openEuler社区
 您对“本文档”的复制、使用、修改及分发受知识共享(Creative Commons)署名—相同方式共享4.0国际公共许可协议(以下简称“CC BY-SA 4.0”)的约束。为了方便用户理解，您可以通过访问https://creativecommons.org/licenses/by-sa/4.0/ 了解CC BY-SA 4.0的概要 (但不是替代)。CC BY-SA 4.0的完整协议内容您可以访问如下网址获取：https://creativecommons.org/licenses/by-sa/4.0/legalcode。

修订记录

| 日期 | 修订   版本 | 修改描述 | 作者 |
| ---- | ----------- | -------- | ---- |
| 2021/09/23|  V1           | memRouter和uswap测试报告|  史冬冬    |

 关键词： 
 memdcd  uswap 内存分级 用户态swap
 

摘要：
 文本主要描述openEuler 21.09版本中memRouter和uswap特性的测试情况，主要覆盖特性基本功能测试，安全测试，以及可靠性测试
 

缩略语清单：

| 缩略语 | 英文全名 | 中文解释 |
| ------ | -------- | -------- |
|        |          |          |
|        |          |          |

# 1     特性概述

memRouter扫描进程使用的内存块，根据内存的使用频率对内存页进行排序，根据配置文件中设置的水线大小，使用socket通信的方式将一定数量的页面发送到uswap
uswap将接受的页面交换到指定的存储介质中去
本文主要描述memRouter和uswap的测试情况


# 2     特性测试信息

本节描述被测对象的版本信息和测试的时间及测试轮次，包括以来的硬件。

| 版本名称 | 测试起始时间 | 测试结束时间 |
| -------- | ------------ | ------------ |
| openEuler 21.09-RC1 | 2021-08-24  | 2021-08-26   |
| openEuler 21.09-RC2 | 2021-08-30  | 2021-08-31   |

描述特性测试的硬件环境信息
| 硬件型号 | 硬件配置信息 | 备注 |
| -------- | ------------ | ---- |
|  2288H V5|CPU_Silver_4116@2.10GHz*2  |  x86架构 |
|  TaiShan 2280|1620CS 2*32cores |  arm架构 |

# 3     测试结论概述

## 3.1   测试整体结论

内存分级扩展特性，共计执行8个用例，覆盖范围包括特性的功能、可靠性，安全。上述功能在一定的约束限制下都能发挥其特性能力。

| 测试活动 | 活动评价 |
| -------- | -------- |
| 功能测试 |   功能测试符合预期，可以正常实现目标进程冷页面uswap操作       |
| 可靠性测试 | 异常场景中特性均能够正常运行，表现稳定         |


## 3.2   约束说明
1、测试组件的客户端和服务端需要在同一个服务器上部署，不支持跨服务器通信的场景。
2、memRouter特性约束说明请参见特性使用手册 
2、使用uswap特性自带demo等相关工具时，请严格遵守demo使用场景约束


## 3.3   遗留问题分析

### 3.3.1 遗留问题影响以及规避措施

| 问题单号 | 问题描述 | 问题级别 | 问题影响和规避措施 | 当前状态 |
| -------- | -------- | -------- | ------------------ | -------- |
|          |          |          |                    |          |
|          |          |          |                    |          |

### 3.3.2 问题统计

|        | 问题总数 | 严重 | 主要 | 次要 | 不重要 |
| ------ | -------- | ---- | ---- | ---- | ------ |
| 数目   |   5      |  2   |   1   |  2    |   0     |
| 百分比 |          |  40%   |   20%   |  40%    |      0  |

# 4     测试执行

## 4.1   测试执行统计数据

*本节内容根据测试用例及实际执行情况进行特性整体测试的统计，可根据第二章的测试轮次分开进行统计说明。*

| 版本名称 | 测试用例数 | 用例执行结果 | 发现问题单数 |
| -------- | ---------- | ------------ | ------------ |
|  openEuler 21.09-RC1  |      8      |     failed         |      5       |
|  openEuler 21.09-RC2  |      8      |     success        |      0       |
|          |            |              |              |

*数据项说明：*

*测试用例数－－到本测试活动结束时，所有可用测试用例数；*

*发现问题单数－－本测试活动总共发现的问题单数。*

## 4.2   后续测试建议

后续测试需要关注点(可选)

# 5     附件

*此处可粘贴各类专项测试数据或报告*