![openEuler ico](../../images/openEuler.png)

版权所有 © 2022  openEuler社区
 您对“本文档”的复制、使用、修改及分发受知识共享(Creative Commons)署名—相同方式共享4.0国际公共许可协议(以下简称“CC BY-SA 4.0”)的约束。为了方便用户理解，您可以通过访问https://creativecommons.org/licenses/by-sa/4.0/ 了解CC BY-SA 4.0的概要 (但不是替代)。CC BY-SA 4.0的完整协议内容您可以访问如下网址获取：https://creativecommons.org/licenses/by-sa/4.0/legalcode。

修订记录

| 日期 | 修订   版本 | 修改描述 | 作者 |
| ---- | ----------- | -------- | ---- |
| 2022/3/21 | 1.0.0 | OpenResty1.19.3.1在openEuler22.03-LTS测试报告| @Jacean |

 关键词： 

 openEuler LTS OpenResty

摘要：

文本主要描述 OpenResty 1.19.3.1 在 openEuler 22.03-LTS arm及x86操作系统上的整体测试过程，详细叙述测试覆盖情况，并通过问题分析对版本整体质量进行评估和总结。 

缩略语清单：

| 缩略语 | 英文全名 | 中文解释 |
| ------ | -------- | -------- |
| LTS |long time support|长时间维护|

# 1     特性概述

OpenResty(又称：ngx_openresty) 是一个基于 NGINX 的可伸缩的 Web 平台，提供了很多高质量的第三方模块。

OpenResty 是一个强大的 Web 应用服务器，Web 开发人员可以使用 Lua 脚本语言调动 Nginx 支持的各种 C 以及 Lua 模块,更主要的是在性能方面，OpenResty可以 快速构造出足以胜任 10K 以上并发连接响应的超高性能 Web 应用系统。

# 2     特性测试信息

本节描述被测对象的版本信息和测试的时间及测试轮次，包括依赖的硬件。

| 版本名称 | 测试起始时间 | 测试结束时间 |
| -------- | ------------ | ------------ |
| OpenResty 1.19.3.1 | 2022-03-12  | 2022-03-17 |


描述特性测试的硬件环境信息

| 硬件型号 | 硬件配置信息 | 备注 |
| -------- | ------------ | ---- |
| Dell 服务器 | x86: Intel(R) Xeon(R) W-2102 (2.9GHz,4C, 8.25M 缓存, 无 Turbo, 无 HT, (120W)) 内存: 32GB 2X16GB DDR4 3200MHZ RDIMM ECC   |  使用 openEuler-22.03-LTS-x86_64-dvd.iso 安装 openEuler 22.03-LTS 操作系统   |
| 浪潮（INSPUR）英信 NF2180M3机架式服务器 | arm: 飞腾FT-2000+ CPU 64核 内存：64GB   |  使用 openEuler-22.03-LTS-aarch64-dvd.iso 安装 openEuler 22.03-LTS 操作系统   |

# 3     测试结论概述

## 3.1   测试整体结论

成功验证了 OpenResty 1.19.3.1 在 openEuler 22.03-LTS arm及x86操作系统上的功能正确性。

| 测试活动 | 活动评价 |
| -------- | -------- |
| 功能测试 | 通过脚本对 openEuler 22.03-LTS（x86） 上安装的 OpenResty 1.19.3.1 进行测试，并成功输出hello world |
| 功能测试 | 通过脚本对 openEuler 22.03-LTS（aarch64） 上安装的 OpenResty 1.19.3.1 进行测试，并成功输出hello world |

## 3.2   约束说明

特性可靠性暂不保证，只需保证基本功能正常

## 3.3   遗留问题分析

### 3.3.1 遗留问题影响以及规避措施

### 3.3.2 问题统计

|        | 问题总数 | 严重 | 主要 | 次要 | 不重要 |
| ------ | -------- | ---- | ---- | ---- | ------ |
| 数目   |     0     |  0    |  0    | 0     |   0     |
| 百分比 |     0     |  0    |  0    |  0    |  0     |

# 4     测试执行

## 4.1   测试执行统计数据


| 版本名称 | 测试用例数 | 用例执行结果 | 发现问题单数 |
| -------- | ---------- | ------------ | ------------ |
| OpenResty 1.19.3.1 | 1 | 成功输出hello world | 0 |

*数据项说明：*

*测试用例数－－到本测试活动结束时，所有可用测试用例数；*

*发现问题单数－－本测试活动总共发现的问题单数。*

## 4.2   后续测试建议

后续测试需要关注点(可选)

# 5     附件

*此处可粘贴各类专项测试数据或报告*
