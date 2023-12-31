![openEuler ico](../../images/openEuler.png)

版权所有 © 2022  openEuler社区
 您对“本文档”的复制、使用、修改及分发受知识共享(Creative Commons)署名—相同方式共享4.0国际公共许可协议(以下简称“CC BY-SA 4.0”)的约束。为了方便用户理解，您可以通过访问https://creativecommons.org/licenses/by-sa/4.0/ 了解CC BY-SA 4.0的概要 (但不是替代)。CC BY-SA 4.0的完整协议内容您可以访问如下网址获取：https://creativecommons.org/licenses/by-sa/4.0/legalcode。

修订记录

| 日期       | 修订版本 | 修改描述               | 作者 |
|:----------|:--------|:----------------------|:----|
| 2022/3/21 | 1.1.2   | A-ops特性web页面测试报告 | 刘娟 |

关键词：Aops 工作台 资产管理 部署管理 智能定位 配置溯源 架构感知

摘要：按照测试策略，对A-ops运维工具的前台web页面进行功能测试，以及可靠性测试

缩略语清单：

| 缩略语                   | 英文全名                  | 中文解释               |
|:------------------------|:------------------------|:----------------------|
| aops-cli                | aops-cli                | aops命令行安装包        |
| aops-utils              | aops-utils              | aops工具安装包          |
| adoctor-cli             | adoctor-cli             | aops智能定位命令行安装包  |
| aops-manager            | aops-manager            | aops配置管理安装包       |
| aops-database           | aops-database           | aops数据中心安装包       |
| aops-web                | aops-web                | aops web页面安装包       |
| adoctor-check-executor  | adoctor-check-executor  | aops异常检测执行器安装包  |
| adoctor-check-scheduler | adoctor-check-scheduler | aops异常检测调度器安装包  |
| adoctor-diag-executor   | adoctor-diag-executor   | aops故障诊断执行器安装包  |
| adoctor-diag-scheduler  | adoctor-diag-scheduler  | aops故障诊断调度器安装包  |
| gala-ragdoll            | gala-ragdoll            | aops配置溯源安装包       |
| gala-gopher             | gala-gopher             | aops架构感知安装包       |
| gala-spider             | gala-spider             | aops拓扑绘制安装包       |


# 1     特性概述

A-ops智能运维工具，提供了配置溯源、架构感知、故障定位基础能力，当系统发生配置错误问题、兼容性问题、性能问题、稳定性问题时，方便系统运维人员和普通用户快速对故障进行定界定位，从而降低运维成本。
故障定位中的异常检测功能实现定时拉取原始数据，并进行预处理，随后根据异常检测规则进行异常检测，并生成相应的结果存入数据库；故障定位中的故障诊断服务主要依据于故障诊断树，每棵故障树代表了一类问题的专家规则，诊断时首先获取故障树节点的异常检测结果，随后根据定义的故障树的结构推导出最终的根因，最终返回相应的报告。
配置溯源实现OS配置托管服务，能够实现对OS配置的集群式管理，屏蔽不同OS类型的配置差异，实现统一的、可溯源的、预期配置可管理的可信的OS配置运维入口，是集群化、版本化管理OS配置的利器。
架构感知从OS视角自动感知集群系统架构，直观的查看集群节点与节点间的通信依赖关系及拓扑指标信息，实现可视化管理。

# 2     特性测试信息

本节描述被测对象的版本信息和测试的时间及测试轮次区，详细的版本信息和测试时间如下表：

| 版本名称               | 测试起始时间 | 测试结束时间 |
|:----------------------|:----------|:-----------|
| openEuler 22.03-LTS RC1  | 2022-02-16 | 2022-02-22 |
| openEuler 22.03-LTS RC2  | 2022-02-25 | 2022-03-01 |
| openEuler 22.03-LTS RC3  | 2022-03-05 | 2022-03-10 |
| openEuler 22.03-LTS RC4  | 2022-03-12 | 2022-03-17 |
| openEuler 22.03-LTS RC5  | 2022-03-25 | 2022-03-27 |

描述特性测试的硬件环境信息

| 架构    | 环境   | 配置                                 | 数量 |
|:-------|:------|:-------------------------------------|:----|
| arm架构 | 虚拟机 | CPU核数：4<br>内存：4G<br>硬盘容量：50G | 4   |
| x86架构 | 虚拟机 | CPU核数：4<br>内存：4G<br>硬盘容量：50G | 4   |

# 3     测试结论概述

## 3.1   测试整体结论

A-ops特性web页面，共计执行86个用例，覆盖特性web页面的基本功能、可靠性和安全测试。

| 测试活动     | 活动评价                                            |
|:-----------|:---------------------------------------------------|
| 功能测试    | 功能测试符合预期，所有页面的基本功能正常                  |
| 可靠性测试   | 覆盖异常操作，启动流程异常，部署业务异常，主机的hostname异常 |
| 安全测试    | 验证安装包内文件权限，符合要求                          |

## 3.2   约束说明

特性可靠性暂不保证，只需保证基本功能正常

## 3.3   遗留问题分析

### 3.3.1 遗留问题影响以及规避措施

无

### 3.3.2 问题统计

|       | 问题总数 | 严重 | 主要 | 次要 | 不重要 |
|:------|:------- |:----|:----|:-----|:------|
| 数目   | 0       | 0   | 0   | 0     |  0   |
| 百分比 | 0       | 0   | 0   | 0     |  0   |

# 4     测试执行

## 4.1   测试执行统计数据

*本节内容根据测试用例及实际执行情况进行特性整体测试的统计，可根据第二章的测试轮次分开进行统计说明。*

| 版本名称              | 测试用例数 | 用例执行结果 | 发现问题单数 |
|:--------------------|:----------|:-----------|:-----------|
| openEuler 22.03-LTS RC3 | 86        | succeed     | 0         |
| openEuler 22.03-LTS RC4 | 86        | succeed     | 0         |


*数据项说明：*

*测试用例数－－到本测试活动结束时，所有可用测试用例数；*

*发现问题单数－－本测试活动总共发现的问题单数。*

## 4.2   后续测试建议

后续测试需要关注点(可选)

# 5     附件

*此处可粘贴各类专项测试数据或报告*

 



 

 
