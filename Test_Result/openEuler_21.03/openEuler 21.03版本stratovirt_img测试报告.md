![openEuler ico](../../images/openEuler.png)

版权所有 © 2021  openEuler社区
 您对“本文档”的复制、使用、修改及分发受知识共享(Creative Commons)署名—相同方式共享4.0国际公共许可协议(以下简称“CC BY-SA 4.0”)的约束。为了方便用户理解，您可以通过访问https://creativecommons.org/licenses/by-sa/4.0/ 了解CC BY-SA 4.0的概要 (但不是替代)。CC BY-SA 4.0的完整协议内容您可以访问如下网址获取：https://creativecommons.org/licenses/by-sa/4.0/legalcode。

修订记录

| 日期     | 修订   版本 | 修改描述                   | 作者   |
| -------- | ----------- | -------------------------- | ------ |
| 2021/3/9 | v1.0        | 添加stratovirt_img测试报告 | zhk128 |

 关键词： stratovirt img 镜像 测试报告

 

摘要：依据测试要求，对镜像进行各项指令操作、功能测试、性能测试等。

 

缩略语清单：

| 缩略语 | 英文全名 | 中文解释 |
| ------ | -------- | -------- |
| img    | image    | 镜像     |

# 1     特性概述

stratovirt_img是提供给StratoVirt组件在轻量化场景下使用的镜像，支持aarch64和x86两个架构，内容精简，仅作用户体验，不建议直接商用。

# 2     特性测试信息

本节描述被测对象的版本信息和测试的时间及测试轮次，包括以来的硬件。

| 版本名称             | 测试起始时间 | 测试结束时间 |
| -------------------- | ------------ | ------------ |
| openEuler-21.03-RC-1 | 2021/3/3     | 2021/3/4     |

描述特性测试的硬件环境信息

| 硬件型号    | 硬件配置信息 | 备注        |
| ----------- | ------------ | ----------- |
| 2288H V5    | 32U256G      | X86架构     |
| TaiShan 200 | 128U512G     | aarch64架构 |

# 3     测试结论概述

## 3.1   测试整体结论

stratovirt_img，可以提供虚拟机镜像基本能力。各种测试结果基本符合预期，质量良好。

使用该镜像及内核启动虚拟机，覆盖以下测试点：

1.文件操作（创建、删除、拷贝、修改权限）

2.虚拟机的基本生命周期和设备调整命令(磁盘和网卡)

3.配置yum源，并使用yum安装依赖包

4.时钟设备、内存弹性、内存大页、对接kata等特性功能测试



使用该镜像及内核启动虚拟机，性能测试：

1.冷启动时长：

在128U512G的Kunpeng-920硬件平台上，测试得出StratoVirt在该环境下平均启动时间为：35.208 ms。

2.内存占用：

使用musl工具链编译得到stratovirt的情况下，使用1U256M规格虚拟机测试得出：

X86：2208Kib

Aarch64：2688Kib

## 3.2   约束说明

## 3.3   遗留问题分析

### 3.3.1 遗留问题影响以及规避措施

| 问题单号                                                     | 问题描述                                                     | 问题级别 | 问题影响和规避措施                                           | 当前状态 |
| ------------------------------------------------------------ | ------------------------------------------------------------ | -------- | ------------------------------------------------------------ | -------- |
| https://gitee.com/openeuler/stratovirt/issues/I3BG4J?from=project-issue | 每日构建交付的内核镜像启动的stratovirt虚拟机，Guest内部时间和Host时间不一致。 | 次要     | 问题影响：影响较多，不一一赘述。等规避措施 ：待问题修复即可。 | 关闭     |

### 3.3.2 问题统计

|        | 问题总数 | 严重 | 主要 | 次要 | 不重要 |
| ------ | -------- | ---- | ---- | ---- | ------ |
| 数目   | 2        | 0    | 0    | 2    | 0      |
| 百分比 | 100%     | 0    | 0    | 100% | 0      |

# 4     测试执行

## 4.1   测试执行统计数据

*本节内容根据测试用例及实际执行情况进行特性整体测试的统计，可根据第二章的测试轮次分开进行统计说明。*

| 版本名称             | 测试用例数 | 用例执行结果   | 发现问题单数 |
| -------------------- | ---------- | -------------- | ------------ |
| openEuler-21.03-RC-1 | 50         | 49pass 1failed | 2            |
|                      |            |                |              |

*数据项说明：*

*测试用例数－－到本测试活动结束时，所有可用测试用例数；*

*发现问题单数－－本测试活动总共发现的问题单数。*

## 4.2   后续测试建议

stratovirt_img只提供了基本能力，如果测试需要编译工具、连接网络等，需要先为镜像扩容并安装相应的依赖包。

# 5     附件

*无*

 



 

 