![avatar](../../images/openEuler.png)


版权所有 © 2023  openEuler社区
 您对“本文档”的复制、使用、修改及分发受知识共享(Creative Commons)署名—相同方式共享4.0国际公共许可协议(以下简称“CC BY-SA 4.0”)的约束。为了方便用户理解，您可以通过访问https://creativecommons.org/licenses/by-sa/4.0/ 了解CC BY-SA 4.0的概要 (但不是替代)。CC BY-SA 4.0的完整协议内容您可以访问如下网址获取：https://creativecommons.org/licenses/by-sa/4.0/legalcode。

修订记录

| 日期 | 修订   版本 | 修改描述 | 作者 |
| ---- | ----------- | -------- | ---- |
| 2023/03/30 |   v1.0      | 插件框架测试报告 | 纪晓慧 |

摘要：依据测试要求，对插件框架进行基础功能测试、可靠性测试、易用性测试、兼容性测试、压力测试及回归测试


# 1     特性概述

当前编译器的主流框架GCC使用GPL license，任何开发者在GCC上开发的代码都被迫强制开源，为解决GPL License强制性问题，该插件框架基于gcc plugin开发。该插件框架的设计实现特点：1）基于编译器插件的常用操作（如优化扩展和语法解析回调）进行抽象，提供完备的插件开发接口；2）插件框架主体以单独进程运行，和GCC编译主进程彼此隔离，摆脱GCC License的开源约束; 3) 插件框架提供插件操作接口，支持LTO复杂优化，实现插件IR覆盖Gimple 80%的功能。

# 2     特性测试信息

本节描述被测对象的版本信息和测试的时间及测试轮次，包括依赖的硬件。

| 版本名称 | 测试起始时间 | 测试结束时间 |
| -------- | ------------ | ------------ |
| openEuler23.03 RC2 | 2023-03-03 | 2023-03-10 |
| openEuler23.03 RC3 | 2023-03-13 | 2023-03-22 |
| openEuler23.03 RC4 | 2023-03-23 | 2023-03-29 |
| openEuler23.03 RC5 | 2023-03-30 | 2023-03-30 |

描述特性测试的硬件环境信息

| 硬件型号 | 硬件配置信息 | 备注 |
| -------- | ------------ | ---- |
| R5210 G12 | 112U 64G | x86 codedb测试专用 |
| TaiShan 200K | 96U 256G | aarch64 codedb测试专用 |
| 虚拟机 | 4U 8G | x86_64 |
| 虚拟机 | 4U 8G | aarch64 |

# 3     测试结论概述

## 3.1   测试整体结论

插件框架共测试9种特性功能：通信引擎功能、运行监控功能、日志记录功能、完整性校验功能、编译插件可配功能，Pass Manager功能，变量类型识别功能，Gimple类型覆盖，插件框架支持-flto，主要覆盖从功能、可靠性、易用性和压力测试等角度对测试对象进行测试。共发现问题11个，发现问题已解决，回归通过。

| 测试活动 | 活动评价 |
| -------- | -------- |
| 功能测试 | 分别在aarch64和x86架构执行功能测试，覆盖9种特性功能共106个用例；aarch64架构下跑通20个codedb应用，x86架构下跑通35个codedb应用。发现问题全部解决，回归通过 |
| 可靠性测试 | 分别在aarch64和x86架构上满核执行csmith和yarpgen各200w+用例，发现问题全都解决，回归通过 |
| 易用性测试 | 验证并检查各反向场景错误、告警提示信息明确，正向场景日志打印明确清晰；编译插件、日志打印、超时时间等参数均可配置 |
| 压力测试 | 超规格测试用例通过11个 |


## 3.2   约束说明

插件框架在-flto阶段使能时，不支持使用make -j多线程编译

## 3.3   遗留问题分析

### 3.3.1 遗留问题影响以及规避措施

### 3.3.2 问题统计

|        | 问题总数 | 严重 | 主要 | 次要 | 不重要 |
| ------ | -------- | ---- | ---- | ---- | ------ |
| 数目   | 11        | 0    |  11  | 0   | 0       |
| 百分比 |  100%     |  0    |  100%  |  0    |  0      |

# 4     测试执行

## 4.1   测试执行统计数据

*本节内容根据测试用例及实际执行情况进行特性整体测试的统计，可根据第二章的测试轮次分开进行统计说明。*

| 版本名称 | 测试用例数 | 用例执行结果 | 发现问题单数 | 发现问题测试活动 |  备注 |
| -------- | ---------- | ------------ | ------------ | --------- | -------- |
| openEuler23.03 330 RC2  | 功能用例：81个；fuzz:200W+  | 失败6类 |6| 功能用例测试，fuzz测试 | 主要测试aarch64和x86上测试插件框架主要功能 |
| openEuler23.03 330 RC3| 功能用例106个；fuzz：400W+；codedb：arm 20个，x86 35个 | 失败5类 |  5  |  功能用例测试，codedb应用编译 | 主要测试aarch64和x86上测试插件框架主要功能 |
| openEuler23.03 330 RC4 |功能用例106个；fuzz：400W+；codedb：arm 20个，x86 35个  | 成功 |  0  |   | 主要测试aarch64和x86上测试插件框架主要功能 |
| openEuler23.03 330 RC4 |功能用例106个  | 成功 |  0  |   | 主要测试aarch64和x86上测试插件框架主要功能 |

*数据项说明：*

*测试用例数－－到本测试活动结束时，所有可用测试用例数；*

*发现问题单数－－本测试活动总共发现的问题单数。*

## 4.2   后续测试建议

# 5     附件



 



 

 