![openEuler ico](../../images/openEuler.png)

版权所有 © 2022  openEuler社区
 您对“本文档”的复制、使用、修改及分发受知识共享(Creative Commons)署名—相同方式共享4.0国际公共许可协议(以下简称“CC BY-SA 4.0”)的约束。为了方便用户理解，您可以通过访问https://creativecommons.org/licenses/by-sa/4.0/ 了解CC BY-SA 4.0的概要 (但不是替代)。CC BY-SA 4.0的完整协议内容您可以访问如下网址获取：https://creativecommons.org/licenses/by-sa/4.0/legalcode。

修订记录

| 日期        | 修订   版本 | 修改描述 | 作者 |
| ----       | ----------- | -------- | ---- |
| 2022/12/30 |   v1.0      | 插件框架测试报告 | 王丹 |


摘要：依据测试要求，对插件框架进行基础功能测试及回归测试

 

# 1     特性概述

包含通信子系统的GCC插件框架最小系统插件框架主体以单独进程运行，和GCC编译主进程彼此隔离，为了实现进程隔离，编译插件服务端组件和编译插件客户端模块组成代理模式。两者实现统一抽象插件接口，编译器进程需要GCC插件完成的操作，经由GCC插件接口和插件适配器转换，跨进程传递（gRPC）调用插件进程。

# 2     特性测试信息

本节描述被测对象的版本信息和测试的时间及测试轮次，包括依赖的硬件。

| 版本名称 | 测试起始时间 | 测试结束时间 |
| -------- | ------------ | ------------ |
| openEuler22.03 LTS SP1 RC2 | 2022-12-02 | 2022-12-08 |
| openEuler22.03 LTS SP1 RC3 | 2022-12-09 | 2022-12-15 |
| openEuler22.03 LTS SP1 RC5 | 2022-12-23 | 2022-12-26|

描述特性测试的硬件环境信息

| 硬件型号 | 硬件配置信息 | 备注 |
| -------- | ------------ | ---- |
| TaiShan 200 | 96U 512G | aarch64 |
| TaiShan 200K | 96U 256G | aarch64 codedb测试专用 |
| 虚拟机 | 64U 200G | x86_64 |

# 3     测试结论概述

## 3.1   测试整体结论

插件框架共测试7种特性功能：通信引擎功能、运行监控功能、日志记录功能、完整性校验功能、编译插件可配功能、Pass manager功能、Demo插件，主要覆盖功能、可靠性、易用性测试。共发现问题0个。

| 测试活动 | 活动评价 |
| -------- | -------- |
| 功能测试 | 分别在aarch64和x86架构执行功能测试，覆盖7种特性功能共58个规格，共82个用例，aarch64架构下跑通107个codedb应用。|
| 可靠性测试 | 满核执行csmith100w+用例，无FAIL用例；满核并发编译codedb 107个应用，无异常 |
| 易用性测试 | 验证并检查各反向场景错误、告警提示信息明确，正向场景日志打印明确清晰；编译插件、日志打印、超时时间等参数均可配置 |

## 3.2  约束说明

不支持与编译选项-flto、-pipe同时使用

## 3.3  问题分析



### 3.3.1 遗留问题影响以及规避措施


### 3.3.2 问题统计


# 4     测试执行

## 4.1   测试执行统计数据

*本节内容根据测试用例及实际执行情况进行特性整体测试的统计，可根据第二章的测试轮次分开进行统计说明。*

| 版本名称 | 测试用例数 | 用例执行结果 | 发现问题单数 | 发现问题测试活动 |  备注 |
| -------- | ---------- | ------------ | ------------ | --------- | -------- |
| openEuler22.03 LTS SP1 RC2 | 功能用例：82个;fuzz：200w+;codedb：107 | 成功 | 0   |  | 主要测试aarch64架构功能 |
| openEuler22.03 LTS SP1 RC3 | 功能用例：82个;fuzz：200w+;codedb：107 | 成功 |  0  |   | 主要测试aarch64架构功能  |
| openEuler22.03 LTS SP1 RC5 | 功能用例：82个 | 成功 |  0  |   | 主要测试aarch64和x86架构功能 |

*数据项说明：*

*测试用例数－－到本测试活动结束时，所有可用测试用例数；*

*发现问题单数－－本测试活动总共发现的问题单数。*

## 4.2   后续测试建议


# 5     附件

*无*
