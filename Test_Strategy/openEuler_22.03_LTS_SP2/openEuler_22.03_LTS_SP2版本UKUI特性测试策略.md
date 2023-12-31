![avatar](../../images/openEuler.png)

版权所有 © 2022  openEuler社区
 您对“本文档”的复制、使用、修改及分发受知识共享(Creative Commons)署名—相同方式共享4.0国际公共许可协议(以下简称“CC BY-SA 4.0”)的约束。为了方便用户理解，您可以通过访问https://creativecommons.org/licenses/by-sa/4.0/ 了解CC BY-SA 4.0的概要 (但不是替代)。CC BY-SA 4.0的完整协议内容您可以访问如下网址获取：https://creativecommons.org/licenses/by-sa/4.0/legalcode。

 修订记录

| 日期 | 修订版本     | 修改描述  | 作者 |
| ---- | ----------- | -------- | ---- |
| 2023/05/17     |    V1.0         |    初稿      | 裴建康     |
|      |             |          |      |
|      |             |          |      |

目 录

1 概述 

>   1.1 版本背景

>   1.2 需求范围

2 风险

3 测试分析设计策略

>   3.1 新增feature测试设计策略

>   3.2 继承feature/组件测试设计策略

4 特性测试环境描述

5 测试执行策略

6 附件

**Keywords 关键词**：

UKUI 策略


Abstract 摘要：

本文是openEuler 22.03 LTS SP2版本上UKUI3.0桌面环境的整体测试策略，用于指导该版本后续测试活动的开展

缩略语清单：
| 缩略语 | 英文全名                             | 中文解释       |
| ------ | ------------------------------------ | -------------- |
|  OS      |   Operation System       |  操作系统        |
|  LTS      |  Long time support        |   长时间维护       |

# 概述
UKUI 是麒麟软件研发团队开发的基于 Linux 发行版的轻量级桌面环境

## 版本背景

openEuler 22.03 LTS SP2 是基于5.10内核22.03-LTS的增强扩展版本，面向服务器、云、边缘计算和嵌入式场景，持续提供更多新特性和功能扩展，给开发者和用户带来全新的体验，服务更多的领域和更多的用户。该版本基于openEuler 22.03 LTS-Next分支拉出。

## 需求范围
|no|feature|status|sig|owner|发布方式|涉及软件包列表|
|:----|:---|:---|:--|:----|:----|:----|

# 风险

| 问题类型 | 问题描述 | 问题等级 | 应对措施 | 责任人 | 状态 |
| -------- | -------- | -------- | -------- | ------ | ---- |
|          |          |          |          |        |      |

# 测试分析设计策略

## 新增feature测试设计策略

无

## 继承feature/组件测试设计策略

从老版本继承的功能特性的测试策略如下：

| Feature/组件 |  策略                           |
| ----------- | ------------------------------- |
| 应用测试 | 测试系统上常用应用的基本功能，常用应用的打开，使用 |
| 文件管理器测试 | 测试文件管理器的基本使用 |
| 任务栏测试 | 测试任务栏图标和功能 |
| 控制面板测试 | 测试控制面板的功能 |
| 开始菜单测试 | 测试桌面的开始菜单 |
| 窗口管理器测试 | 测试桌面窗口切换拖动功能 |


# 特性测试环境描述
<!-- 主要描述执行测试的硬件信息 -->
| 硬件型号 | 硬件配置信息 | 备注 |
| -------- | ------------ | ---- |
|  aarch64 | 长城擎天服务器<br>DF723 | CPU型号：FT2000+<br>CPU核数：64<br>内存：64G<br>硬盘容量：240G | 1    |
|  x86_64  | 联想启天台式机<br>M425-N000 | CPU 型号：Intel(R) Core(TM) i7-8700 CPU @ 3.20GHz<br>CPU内核总数：6<br>内存容量：16G | 1    | 

# 测试执行策略

### 测试计划
|Stage name|Begin time|End time|Days|Note|
|:----------|:---------|:-------|:---------|:-------|
|Test round 2|2023-05-24|2023-06-02|10|全量测试|
|Test round 3|2023-06-05|2023-06-09|5|全量测试|
|Test round 5|2023-06-17|2023-06-23|7|回归测试|

### 入口标准
1.  上个阶段无block问题遗留

2.  转测版本可以在openEuler 22.03 LTS SP2上成功适配无阻塞性问题

### 出口标准
1.  策略规划的测试活动涉及测试用例100%执行完毕             
                                                           
2.  发布特性/新需求/性能基线等满足版本规划目标             
                                                           
3.  版本无block问题遗留，其它严重问题要有相应规避措施或说明

# 附件
无
