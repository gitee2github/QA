![openEuler ico](../../images/openEuler.png)

版权所有 © 2023  openEuler社区
 您对“本文档”的复制、使用、修改及分发受知识共享(Creative Commons)署名—相同方式共享4.0国际公共许可协议(以下简称“CC BY-SA 4.0”)的约束。为了方便用户理解，您可以通过访问https://creativecommons.org/licenses/by-sa/4.0/ 了解CC BY-SA 4.0的概要 (但不是替代)。CC BY-SA 4.0的完整协议内容您可以访问如下网址获取：https://creativecommons.org/licenses/by-sa/4.0/legalcode。

修订记录

| 日期        | 修订   版本 | 修改描述 | 作者 |
| ----       | ----------- | -------- | ---- |
| 2023/03/30 |   v1.0      | GCC测试报告 | 王丹 |


摘要：依据测试要求，对GCC编译器进行基础功能测试

 

# 1     特性概述

GCC（GNU Compiler Collection，GNU编译器套件）是由GNU开发的编程语言器。GNU编译器套件包括C、C++、Objective-C、Fortran、java、Ada和Go语言前端，也包括了这些语言的库（如libstdc++，libgcj等。）

# 2     特性测试信息

本节描述被测对象的版本信息和测试的时间及测试轮次，包括依赖的硬件。

| 版本名称 | 测试起始时间 | 测试结束时间 |
| -------- | ------------ | ------------ |
| openEuler23.03 RC3 | 2023-03-22 | 2023-03-24 |

描述特性测试的硬件环境信息

| 硬件型号 | 硬件配置信息 | 备注 |
| -------- | ------------ | ---- |
| TaiShan 200 | 96U 512G | aarch64 |

# 3     测试结论概述

## 3.1   测试整体结论

GCC编译器测试，继承特性（Mul64: -fmerge-mull; 指针压缩：-fipa-struct-reorg=4 --param compressed-pointer-size=[8,16,32]、-fipa-struct-reorg=5; 循环拆分：-ftree-slp-transpose-vectorize; semi-relayout:-fipa-struct-reorg=6 --param semi-relayout-level=[11,12,13,14,15]）基本功能测试，无遗留风险，整体质量良好。

| 测试活动 | 活动评价 |
| -------- | -------- |
| 基本功能测试 | 执行测试套：冒烟测试、dejanu、库上特性用例、bstest、llvmcase、Anghabench、jotai-benchmarks，测试通过，无风险； |
| 汇编一致性测试 | 根据speccpu2017生成二进制并反汇编，比对结果一致； |


## 3.2   约束说明

无

## 3.3   遗留问题分析

### 3.3.1 遗留问题影响以及规避措施

无

### 3.3.2 问题统计

|        | 问题总数 | 严重 | 主要 | 次要 | 不重要 |
| ------ | -------- | ---- | ---- | ---- | ------ |
| 数目   |  0       | 0     |  0    | 0     | 0       |
| 百分比 |  0     |  0    |  0    |  0    |  0      |

# 4     测试执行

## 4.1   测试执行统计数据

*本节内容根据测试用例及实际执行情况进行特性整体测试的统计，可根据第二章的测试轮次分开进行统计说明。*

| 版本名称 | 测试用例数 | 用例执行结果 | 发现问题单数 | 发现问题测试活动 | 问题单 |
| -------- | ---------- | ------------ | ------------ | ------------ | ------------ |
| openEuler23.03 RC3 | 100w+ | 成功 |   0  | NA  | NA  |

*数据项说明：*

*测试用例数－－到本测试活动结束时，所有可用测试用例数；*

*发现问题单数－－本测试活动总共发现的问题单数。*

## 4.2   后续测试建议


# 5     附件

*无*

 



 

 
