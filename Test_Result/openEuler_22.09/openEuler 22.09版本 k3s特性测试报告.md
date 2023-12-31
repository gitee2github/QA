![openEuler ico](../../images/openEuler.png)

版权所有 © 2022  openEuler社区
 您对“本文档”的复制、使用、修改及分发受知识共享(Creative Commons)署名—相同方式共享4.0国际公共许可协议(以下简称“CC BY-SA 4.0”)的约束。为了方便用户理解，您可以通过访问https://creativecommons.org/licenses/by-sa/4.0/ 了解CC BY-SA 4.0的概要 (但不是替代)。CC BY-SA 4.0的完整协议内容您可以访问如下网址获取：https://creativecommons.org/licenses/by-sa/4.0/legalcode。

修订记录

| 日期      | 修订   版本 | 修改描述 | 作者          |
| --------- | ----------- | -------- | ------------- |
| 2022-09-7 | 1.0         | 新增报告 | @zhu-yuncheng |

 关键词： 
k3s, 边缘场景

摘要：

本报告主要描述基于openEuler 22.09 版本进行的k3s软件的部署测试过程，报告对测试情况进行说明，对k3s在server 和 agent部署的测试进行评估和总结。

缩略语清单：

| 缩略语 | 英文全名 | 中文解释 |
| ------ | -------- | -------- |
|        |          |          |

# 1     特性概述

K3s 是一个轻量级的 Kubernetes 发行版，它针对边缘计算、物联网等场景进行了高度优化 。


# 2     特性测试信息

被测对象的版本信息和测试的时间及测试轮次：

| 版本名称                    | 测试起始时间 | 测试结束时间 |
| --------------------------- | ------------ | ------------ |
| openEuler22.09 test round 2 | 2022-08-18   | 2022-08-18   |
| openEuler22.09 test round 4 | 2022-09-08   | 2022-09-08   |

特性测试的硬件环境信息：

| 硬件型号 | 硬件配置信息 | 备注 |
| -------- | ------------ | ---- |
| NA       | NA           | NA   |

# 3     测试结论概述

## 3.1   测试整体结论

使用openEuler 22.09 版本rc4 iso进行装机并下载k3s进行部署，成功在server和agent端部署，服务端可纳管agent节点。


| 测试活动 | 活动评价                                                  |
| -------- | --------------------------------------------------------- |
| 功能测试 | k3s集群在server、agent节点部署成功，服务端可纳管agent节点 |

## 3.2   约束说明

* 两台机器的hostname需设置为不同的名字。



## 3.3   遗留问题分析

### 3.3.1 遗留问题影响以及规避措施

NA

### 3.3.2 问题统计

|        | 问题总数 | 严重 | 主要 | 次要 | 不重要 |
| ------ | -------- | ---- | ---- | ---- | ------ |
| 数目   | 0        | 0    | 0    | 0    | 0      |
| 百分比 | 0        | 0    | 0    | 0    | 0      |

# 4     测试执行

## 4.1   测试执行统计数据

*本节内容根据测试用例及实际执行情况进行特性整体测试的统计，可根据第二章的测试轮次分开进行统计说明。*

| 版本名称        | 测试用例数 | 用例执行结果 | 发现问题单数 |
| --------------- | ---------- | ------------ | ------------ |
| openEuler 22.09 | 1          | 通过         | 0            |

*数据项说明：*

*测试用例数－－到本测试活动结束时，所有可用测试用例数；*

*发现问题单数－－本测试活动总共发现的问题单数。*

## 4.2   后续测试建议

* 可挖掘更多功能点进行测试。


# 5     附件

NA