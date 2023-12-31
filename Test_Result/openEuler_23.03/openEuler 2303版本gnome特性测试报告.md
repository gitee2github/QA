![avatar](../../images/openEuler.png)


版权所有 © 2023  openEuler社区
 您对“本文档”的复制、使用、修改及分发受知识共享(Creative Commons)署名—相同方式共享4.0国际公共许可协议(以下简称“CC BY-SA 4.0”)的约束。为了方便用户理解，您可以通过访问https://creativecommons.org/licenses/by-sa/4.0/ 了解CC BY-SA 4.0的概要 (但不是替代)。CC BY-SA 4.0的完整协议内容您可以访问如下网址获取：https://creativecommons.org/licenses/by-sa/4.0/legalcode。

修订记录

| 日期      | 修订   版本 | 修改描述      | 作者   |
| --------- | ----------- | ------------- | ------ |
| 2023/3/31 | v1.0        | Gnome测试报告 | 轩豪磊 |
|           |             |               |        |

关键词： Gnome测试报告

摘要：

按照测试要求，针对openEuler-23.03测试镜像对Gnome的安装、主要功能进行测试。测试结果良好，基本支持Gnome主要功能的正常使用。




# 1     特性概述

本测试报告为Gnome 43.2桌面在openEuler-23.03操作系统上的测试报告，目的在于总结测试阶段发现的问题以及按版本及平台的测试结果，测试的范围主要包括安装、使用、稳定性等。

# 2     特性测试信息

本节描述被测对象的版本信息和测试的时间及测试轮次，包括依赖的硬件。

| 版本名称             | 测试起始时间  | 测试结束时间  |
| -------------------- | ------------- | ------------- |
| openEuler-23.03-rc-1 | 2023年2月24日 | 2022年3月1日  |
| openEuler-23.03-rc-4 | 2023年3月23日 | 2022年3月27日 |
| openEuler-23.03-rc-5 | 2023年3月29日 | 2023年3月31日 |

描述特性测试的硬件环境信息

| 硬件型号 | 硬件配置信息                             | 备注   |
| -------- | ---------------------------------------- | ------ |
| aarch64  | CPU核数：4<br>内存：8G<br>硬盘容量：120G | 虚拟机 |
| x86_64   | CPU核数：4<br>内存：8G<br>硬盘容量：120G | 虚拟机 |

# 3     测试结论概述

## 3.1   测试整体结论

* 软件总体评估

Gnome 43.2 在openEuler-23.03版本上，共经过3轮测试，执行201个测试项，整体核心功能稳定正常。

* 重要组件测试

重要组件测试中，共执行了141个测试项，其中140个通过，1个未通过。

* 系统插件测试

系统插件测试中，共执行了60个测试项，其中60个通过，0个未通过。

| 测试活动     | 活动评价                               |
| ------------ | -------------------------------------- |
| 功能接口测试 | 覆盖桌面各个主要使用场景，整体符合预期 |
| 专项测试     | 无                                     |



## 3.2   约束说明

* 安装文档

<https://gitee.com/openeuler/docs/blob/master/docs/zh/docs/desktop/Install_GNOME.md>

已测试验证，按照此文档可正常安装Gnome。

* 用户使用文档

<https://gitee.com/openeuler/docs/blob/master/docs/zh/docs/desktop/Gnome_userguide.md>

已测试验证。

## 3.3   遗留问题分析

### 3.3.1 遗留问题影响以及规避措施

| 问题单号 | 问题简述 | 问题级别 | 问题影响和规避措施 | 影响分析 |
| --- | ------- | ------ | ------- | ------- |
| https://gitee.com/src-openeuler/gnome-boxes/issues/I6RCA2 | gnome-boxes无法正常创建虚拟机（x86/aarch64） | 严重     | gnome-boxes是虚拟机管理器，无法创建虚拟机。可以使用virt-manager来代替。等待后续支持,本次先从release剔除。https://gitee.com/src-openeuler/qemu/issues/I4CZRV |         |
|  |  |  |  | |

### 3.3.2 问题统计

|        | 问题总数 | 严重 | 主要 | 次要 | 不重要 |
| ------ | -------- | ---- | ---- | ---- | ------ |
| 数目   | 1        | 1    | 0    | 0    | 0      |
| 百分比 | 100%     | 100% |      |      |        |

问题列表:

| 问题单号                                                  | 问题简述                                                     | 问题级别 | 问题影响和规避措施          | 当前状态 |
| :-------------------------------------------------------- | ------------------------------------------------------------ | -------- | --------------------------- | -------- |
| https://gitee.com/src-openeuler/gnome-boxes/issues/I6RCA2 | qemu的configure默认参数是--disable-smartcard，是qemu的这个原因导致无法创建虚拟机。 | 严重     | qemu暂无计划使能smartcard。 | 未解决   |
| https://gitee.com/src-openeuler/phodav/pulls/21           | spice-webdavd.service服务启动失败                            | 次要     |                             | 已解决   |

# 4 详细测试结论

# 5     测试执行

## 5.1   测试执行统计数据

*本节内容根据测试用例及实际执行情况进行特性整体测试的统计，可根据第二章的测试轮次分开进行统计说明。*

| 版本名称             | 测试用例数 | 用例执行结果 | 发现问题单数 |
| -------------------- | ---------- | ------------ | ------------ |
| openEuler-23.03-rc-1 | 201        | 全部通过     | 0            |
| openEuler-23.03-rc-4 | 201        | 失败2个      | 2            |
| openEuler-23.03-rc-5 | 201        | 失败1个      | 1            |

*数据项说明：*

*测试用例数－－到本测试活动结束时，所有可用测试用例数；*

*发现问题单数－－本测试活动总共发现的问题单数。*

## 5.2   后续测试建议

后续测试需要关注点(可选)





 

 