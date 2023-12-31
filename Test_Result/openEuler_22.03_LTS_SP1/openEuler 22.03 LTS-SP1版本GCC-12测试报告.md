![openEuler ico](../../images/openEuler.png)

版权所有 © 2022  openEuler社区
 您对“本文档”的复制、使用、修改及分发受知识共享(Creative Commons)署名—相同方式共享4.0国际公共许可协议(以下简称“CC BY-SA 4.0”)的约束。为了方便用户理解，您可以通过访问https://creativecommons.org/licenses/by-sa/4.0/ 了解CC BY-SA 4.0的概要 (但不是替代)。CC BY-SA 4.0的完整协议内容您可以访问如下网址获取：https://creativecommons.org/licenses/by-sa/4.0/legalcode。

修订记录

| 日期        | 修订   版本 | 修改描述 | 作者 |
| ----       | ----------- | -------- | ---- |
| 2022/12/29 |   v1.0      | GCC-12测试报告 | 王丹 |


摘要：依据测试要求，对GCC编译器特性进行各测试套执行

 

# 1     特性概述

GCC（GNU Compiler Collection，GNU编译器套件）是由GNU开发的编程语言器。GNU编译器套件包括C、C++、Objective-C、Fortran、java、Ada和Go语言前端，也包括了这些语言的库（如libstdc++，libgcj等。）

# 2     特性测试信息

本节描述被测对象的版本信息和测试的时间及测试轮次，包括依赖的硬件。

| 版本名称 | 测试起始时间 | 测试结束时间 |
| -------- | ------------ | ------------ |
| openEuler22.03 LTS SP1 RC2 | 2022-12-02 | 2022-12-08 |
| openEuler22.03 LTS SP1 RC3 | 2022-12-09 | 2022-12-15 |

描述特性测试的硬件环境信息

| 硬件型号 | 硬件配置信息 | 备注 |
| -------- | ------------ | ---- |
| 虚拟机 | 8U 16G | aarch64 |
| 2288H V5 | 64U 186G | x86_64 |

# 3     测试结论概述

## 3.1   测试整体结论

GCC-12编译器测试，无遗留问题，整体质量良好。

| 测试活动 | 活动评价 |
| -------- | -------- |
| Intel SPR仿真器 | 使用GCC-12执行测试套：deja；执行通过|
| 典型应用 | 使用GCC-12执行应用：kernel、mysql、spec2017；mysql 8.0.20编译失败|
| 安装 | 依赖GCC软件包安装时不会误安装gcc-12；执行通过 |
| SPR硬件测试 | 使用GCC-12执行测试套：deja；执行通过； |


## 3.2   约束说明

无

## 3.3   遗留问题分析

### 3.3.1 遗留问题影响以及规避措施

| 序号 | 问题单号        | 问题简述         | 问题级别 | 影响分析              | 规避措施           |
| ---- | ----------- | ----------------- | -------- | ------------ | ---------------- |
| 1    | [I69WOV](https://gitee.com/src-openeuler/gcc-12/issues/I69WOV) | 【22.03 LTS-SP1】【arm】gcc12编译mysql 8.0.20报错        | 主要     | 此问题属于兼容性问题，当前MySQL暂时不支持使用GCC 12编译，MySQL官方支持最新的编译器是使用GCC 11编译MySQL 8.0.29：http://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-29.html |  使用GCC 10.3.1编译MySQL 8.0.20   |

### 3.3.2 问题统计

|        | 问题总数 | 严重 | 主要 | 次要 | 不重要 | 非问题 |
| ------ | -------- | ---- | ---- | ---- | ------ |------ |
| 数目   |  2       | 0     |  1    | 0     | 0       | 1 |
| 百分比 |  100%     |  0    |  50%    |  0    |  0      | 50% |

# 4     测试执行

## 4.1   测试执行统计数据

*本节内容根据测试用例及实际执行情况进行特性整体测试的统计，可根据第二章的测试轮次分开进行统计说明。*

| 版本名称 | 测试用例数 | 用例执行结果 | 发现问题单数 | 问题单 | 备注 |
| -------- | ---------- | ------------ | ------------ | ------------ |------------ |
| openEuler22.03 LTS SP1 RC2 | 10w+ | 全部通过 | 0   | NA| NA |
| openEuler22.03 LTS SP1 RC3 | 4 | kernel、mysql |  2    |  [I66EYK](https://gitee.com/src-openeuler/gcc-12/issues/I66EYK) [I69WOV](https://gitee.com/src-openeuler/gcc-12/issues/I69WOV) |  kernel编译失败为非问题 |

*数据项说明：*

*测试用例数－－到本测试活动结束时，所有可用测试用例数；*

*发现问题单数－－本测试活动总共发现的问题单数。*

## 4.2   后续测试建议


# 5     附件

*无*

 



 

 
