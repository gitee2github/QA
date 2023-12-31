![openEuler ico](../../images/openEuler.png)

版权所有 © 2021  openEuler社区
 您对“本文档”的复制、使用、修改及分发受知识共享(Creative Commons)署名—相同方式共享4.0国际公共许可协议(以下简称“CC BY-SA 4.0”)的约束。为了方便用户理解，您可以通过访问https://creativecommons.org/licenses/by-sa/4.0/ 了解CC BY-SA 4.0的概要 (但不是替代)。CC BY-SA 4.0的完整协议内容您可以访问如下网址获取：https://creativecommons.org/licenses/by-sa/4.0/legalcode

修订记录

| 日期       | 修订版本 | 修改描述 | 作者     |
| ---------- | -------- | -------- | -------- |
| 2021/09/28 | 初稿     | 初始     | 王宇翔   |

 关键词： 嵌入式   工控   轻量化   安全加固   容器



摘要：



缩略语清单：

| 缩略语 | 英文全名 | 中文解释 |
| ------ | -------- | -------- |
| iSula  | iSula    | 轻量级容器引擎  |
|        |          |          |

# 1     特性概述

openEuler 21.09推出面向嵌入式、工控领域的创新版本，提供轻量化、安全和容器等基础能力，支持ARM32、ARM64芯片架构。并将协同openEuler社区生态伙伴、用户、开发者，逐步扩展支持PowerPC、RISC-V芯片架构，增加工业中间件、仿真系统等能力，打造面向嵌入式和工控领域全栈解决方案。

# 2     特性测试信息

| 版本名称                 | 测试起始时间 | 测试结束时间 |
| ------------------------ | ------------ | ------------ |
| openEuler embedded创新版 | 2021-09-17   | 2021-09-28   |

硬件环境信息如下：

| 型号                     | 硬件配置信息                              | 备注                |
| -------------------------| ------------------------------------------| --------------------|
| 华为云主机               | Intel(R) Xeon(R) Gold 6266C CPU @ 3.00GHz | X86服务器           |
| Huawei RH2288H V3        | Intel(R) Xeon(R) CPU E5-2620 v3 @ 2.40GHz | fusioncompute 6.5   |

# 3     测试结论概述

## 3.1   测试整体结论

嵌入式OS预览版，共计执行73个用例，主要覆盖了轻量化测试、安全加固测试和容器功能测试，发现问题已解决，回归通过，无遗留风险，整体质量良好；
OS镜像< 5M，空载情况下，运行底噪< 15M，重启时间< 5s

| 测试活动     | 活动评价                                              |
| ------------ | ----------------------------------------------------- |
| 轻量化测试   | 镜像体积、内存底噪及启动时间满足规格要求(arm64:镜像体积4.1M，启动时间0.8s，内存底噪6.37M；arm32:镜像体积3.7M，启动时间1.2s，内存底噪6.27M)  |
| 安全加固测试 | 安全加固配置均正常生效                                |
| 容器（iSula）功能测试 | iSula基本功能正常，在启动、停止时有Error打印不影响功能 |

## 3.2   约束说明

无

## 3.3   遗留问题分析

### 3.3.1 遗留问题影响以及规避措施

| 问题单号 | 问题描述                     | 问题级别 | 问题影响和规避措施 | 当前状态     |
| -------- | ---------------------------- | -------- | ------------------ | ------------------------ |
| https://gitee.com/openeuler/iSulad/issues/I4CA3Y?from=project-issue | isula run及stop时有Error打印 | 一般 | 不影响功能 | 待办的 |
|          |                              |          |                    |              |

### 3.3.2 问题统计

|        | 问题总数 | 严重 | 主要 | 次要 | 不重要 |
| ------ | -------- | ---- | ---- | ---- | ------ |
| 数目   |   1      | 0    |  0   |  1   |   0    |
| 百分比 |   100%   | 0%   |  0%  | 100% |   0%   |

# 4     测试执行

## 4.1   测试执行统计数据


| 版本名称        | 测试用例数 | 用例执行结果 | 发现问题单数 |
| --------------- | ---------- | ------------ | ------------ |
| 小型化tiny镜像  |  3         |  pass        |   0          |
| 标准镜像        |  70        |  失败1个     |   1          |

*数据项说明：*

*测试用例数－－到本测试活动结束时，所有可用测试用例数；*

*发现问题单数－－本测试活动总共发现的问题单数。*

# 3     附件

无
