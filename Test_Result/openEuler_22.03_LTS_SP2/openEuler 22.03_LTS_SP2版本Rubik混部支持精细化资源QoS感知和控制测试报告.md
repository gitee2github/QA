![avatar](../../images/openEuler.png)


版权所有 © 2023  openEuler社区
 您对“本文档”的复制、使用、修改及分发受知识共享(Creative Commons)署名—相同方式共享4.0国际公共许可协议(以下简称“CC BY-SA 4.0”)的约束。为了方便用户理解，您可以通过访问https://creativecommons.org/licenses/by-sa/4.0/ 了解CC BY-SA 4.0的概要 (但不是替代)。CC BY-SA 4.0的完整协议内容您可以访问如下网址获取：https://creativecommons.org/licenses/by-sa/4.0/legalcode。

修订记录

| 日期 | 修订   版本 | 修改描述 | 作者 |
| ---- | ----------- | -------- | ---- |
| 2023-06-21     |     1.0        |    创建      |   雷杰   |

关键词：rubik PSI quotaTurbo fssr

摘要：
rubik提供对系统资源感知能力，并对节点pod/容器动态控制。

缩略语清单：

| 缩略语 | 英文全名 | 中文解释 |
| ------ | -------- | -------- |
|        |          |          |


# 1     特性概述

特性主要分为三个方面：
    1.psi可观测性 : 对在线业务和离线业务进行动态监控，资源堵塞时对离线业务进行调控
    2.quotaTurbo支持弹性限流：对pod资源消耗进行弹性限流
    3.异步内存分级回收：对离线业务内存资源动态调节

# 2     特性测试信息

| 版本名称 | 测试起始时间 | 测试结束时间 |
| -------- | ------------ | ------------ |
| openEuler 22.03_LTS_SP2 RC3 | 2023-06-05   | 2023-06-14   |
| openEuler 22.03_LTS_SP2 RC4 | 2023-06-15   | 2023-06-25   |
| openEuler 22.03_LTS_SP2 RC5 | 2023-06-26   | -   |

描述特性测试的硬件环境信息

| 硬件型号 | 硬件配置信息 | 备注 |
| -------- | ------------ | ---- |
|    NA      |       NA       |    虚拟机  |

# 3     测试结论概述

## 3.1   测试整体结论

Rubik混部支持精细化资源QoS感知和控制特性，共计执行35个用例，主要覆盖了功能测试和继承特性测试，发现问题已解决，回归通过，遗留风险小，整体质量良好。

| 测试活动 | 测试子项 | 活动评价 |
| ------- | -------- | ------- |
| 继承功能测试 | quotaTurbo支持弹性限流特性测试 | 继承用例全部测试通过     |
| 功能测试 | psi可观测性特性测试 |  功能测试通过    |
| 功能测试 | 异步内存分级回收特性测试 |  功能测试通过    |
| 功能测试 | quotaTurbo支持弹性限流特性测试 | 功能测试通过     |
| 可靠性测试 | quotaTurbo支持弹性限流特性测试 | 可靠性测试通过     |



## 3.2   约束说明

NA

## 3.3   遗留问题分析

### 3.3.1 遗留问题影响以及规避措施

NA

# 4 详细测试结论

## 4.1 功能测试

### 4.1.1 继承特性测试结论

| 序号 | 组件/特性名称 | 特性质量评估 | 备注 |
| --- | ----------- | :--------: | --- |
|1 |quotaTurbo支持弹性限流 | <font color=green>■</font> | 继承用例全部执行成功 |

### 4.1.2 新增特性测试结论

| 序号 | 组件/特性名称 | 特性质量评估 | 备注 |
| --- | ----------- | :--------: | --- |
|1 |quotaTurbo支持弹性限流 | <font color=green>▲</font> |   |
|2 |异步内存分级回收 | <font color=green>▲</font> |   |
|3 |quotaTurbo支持弹性限流 | <font color=green>▲</font> |   |


## 4.2 兼容性测试结论

NA

## 4.3 DFX专项测试结论

### 4.3.1 性能测试结论

NA

### 4.3.2 可靠性/韧性测试结论

通过

### 4.3.3 安全测试结论

NA

## 4.4 资料测试结论

https://gitee.com/openeuler/docs/pulls/4828

## 4.5 其他测试结论

NA

# 5     测试执行

## 5.1   测试执行统计数据

| 版本名称 | 测试用例数 | 用例执行结果 | 发现问题单数 |
| -------- | ---------- | ------------ | ------------ |
| openEuler 22.03_LTS_SP2 RC3 | 3   | 失败1个 | 1 | 
| openEuler 22.03_LTS_SP2 RC4 | 35  | 失败2个 | 1 | 
| openEuler 22.03_LTS_SP2 RC5 | 35  | 失败0个 | 0 |   

## 5.2   后续测试建议

NA

# 6     附件

*此处可粘贴各类专项测试数据或报告*

 



 

 