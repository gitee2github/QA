![openEuler ico](../../images/openEuler.png)

版权所有 © 2022 openEuler社区
您对“本文档”的复制、使用、修改及分发受知识共享(Creative Commons)署名—相同方式共享4.0国际公共许可协议(以下简称“CC BY-SA
4.0”)的约束。为了方便用户理解，您可以通过访问<https://creativecommons.org/licenses/by-sa/4.0/>了解CC BY-SA 4.0的概要 (但不是替代)。CC BY-SA
4.0的完整协议内容您可以访问如下网址获取：<https://creativecommons.org/licenses/by-sa/4.0/legalcode>。

修订记录

| 日期       | 修订版本 | 修改  章节       | 修改描述               | 作者       |
| ---------- | -------- | ---------------- | ---------------------- | ---------- |
| 2022-7-21  | 1.0.0    |            | 初稿                   | saarloos |

目 录

1 概述

>   1.1 版本背景

>   1.2 需求范围

2 风险

3 测试分层策略

4 测试分析设计策略

>   4.1 新增feature测试设计策略

>   4.2 继承feature/组件测试设计策略

>   4.3 专项测试策略

5 测试执行策略

6 附件

**Keywords 关键词**：

openEuler embedded 测试策略

Abstract 摘要：

本文是openEuler 22.09 embedded 版本的整体测试策略，用于指导该版本后续测试活动的开展

缩略语清单：

| 缩略语 | 英文全名                             | 中文解释       |
| ------ | ------------------------------------ | -------------- |
| OS     | Operation System                     | 操作系统       |
| CVE    | Common Vulnerabilities and Exposures | 公共漏洞和暴露 |

# 概述

openEuler Embedded是基于openEuler社区面向嵌入式场景的Linux版本。当前openEuler内核源于Linux实现软实时能力，同时具备soc内多平面混合部署，开放基于Yocto构建包的小型化定制裁剪能力，是由全球开源贡献者构建的高效、稳定、安全的开源操作系统。

本文主要描述openEuler 22.09 embedded 版本的总体测试策略，按照社区开发模式进行运作，结合社区release-manager团队制定的版本计划规划相应的测试活动。整体测试策略覆盖新需求、继承需求的测试分析和执行，明确各个测试周期的测试策略及出入口标准，指导后续测试活动。

## 版本背景

openEuler embedded 22.09版本是基于openEuler embedded 22.03 LTS版本，根据嵌入式设备的特点及技术发展规划，对22.03版本的特色特性进行增强，具体功能如下：

1. 增强混合关键部署技术，完成基础串口/SHELL服务，实现基于树莓派的SOC内的实时与非实时多平面混合部署。
2. 基于分布式软总线扩展生态互联互通，实现openEuler设备与openHarmony设备间的相互识别和通信。

## 需求范围

openEuler 22.09 embedded版本交付需求列表如下：

| **no** | **feature**                                                  | **status** | **sig**                 | **owner**                                      | **发布方式** | **涉及软件包列表** |
| ------ | ------------------------------------------------------------ | ---------- | ----------------------- | ---------------------------------------------- | -----------  | -----------------|
|[I5G7WM](https://gitee.com/openeuler/yocto-meta-openeuler/issues/I5G7WM)|混合关键部署技术|Developing|sig-yocto|[@linzichang](https://gitee.com/linzichang) [@beiling.xie](https://gitee.com/beilingxie) [@zhengjunling](https://gitee.com/junling_zheng) [@ilisimin](https://gitee.com/open_euler/dashboard/members/ilisimin) [@任慰](https://gitee.com/open_euler/dashboard/members/vonhust)|embedded|yocto-meta-openeuler,dsoftbus_standard, yocto-embedded-tools, OpenAMP | 源码 + 镜像包含 | dsoftbus_standard, libCoAP, yocto-embedded-tools, yocto-meta-openeuler |
|[I5G7UI](https://gitee.com/openeuler/yocto-meta-openeuler/issues/I5G7UI)|基于分布式软总线扩展生态互联互通|Developing|sig-yocto|[@linzichang](https://gitee.com/linzichang) [@beiling.xie](https://gitee.com/beilingxie) [@zhengjunling](https://gitee.com/junling_zheng) [@ilisimin](https://gitee.com/open_euler/dashboard/members/ilisimin) [@任慰](https://gitee.com/open_euler/dashboard/members/vonhust)|embedded|yocto-meta-openeuler,dsoftbus_standard, yocto-embedded-tools, OpenAMP | 源码 + 镜像包含 | libmetal, OpenAMP, yocto-embedded-tools, yocto-meta-openeuler |

# 风险

| 问题类型 | 问题描述 | 问题等级 | 应对措施 | 责任人 | 状态 |
| -------- | -------- | -------- | -------- | ------ | ---- |
|          |          |          |          |        |      |

# 测试分层策略

本次LTS版本的具体测试分层策略如下：

| **需求**                        | **开发主体**          | **测试主体**      | **测试分层策略**                                             |
| ------------------------------- | --------------------- | ----------------- | ------------------------------------------------------------ |
| 混合关键部署技术 | sig-yocto | sig-Yocto | 测试混合关键部署技术开放接口api，新增的串口/SHELL服务，混合部署生命周期管理以及在树莓派上的混合部署 |
| 基于分布式软总线扩展生态互联互通 | sig-yocto | sig-yocto | 测试分布式软总线开放接口api，重点关注本次新增适配的认证模块，验证与openHarmony的互相识别和通信 |

# 测试分析设计策略

## 新增feature测试设计策略

| *序号* | *Feature*                    | *重点*                                                       | *设计思路*                                                   | *备注* |
| ------ | ---------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------ |
| 1 | 混合关键部署技术 | 串口/SHELL服务、树莓派上的混合部署以及混合部署的生命周期管理 | 在树莓派上启动混合部署，调用串口/SHELL服务来进行混合部署间的调用和通信，混合部署生命周期管理 | |
| 2 | 基于分布式软总线扩展生态互联互通 | 认证模块，与openHarmony的识别和通信 | 启动openEuler设备和openHarmony设备，并启动分布式软总线服务，编写客户端验证两者设别和通信 | |


## 继承feature/组件测试设计策略

从老版本继承的功能特性的测试策略如下：

| Feature/组件                              | 策略                                                         |
| ----------------------------------------- | ------------------------------------------------------------ |
| 基于Linux 5.10内核提供软实时能力 | 直接继承已有测试能力  |
| 开放基于Yocto构建包的小型化定制裁剪能力 | 直接继承已有测试能力 |
| 支持树莓派4B作为嵌入式通用硬件 | 直接继承已有测试能力 |
| 混合关键部署框架能力 | 直接继承已有测试能力 |
| 分布式软总线基础能力 | 直接继承已有测试能力 |

## 软件包变更测试设计策略

openEuler embedded 22.09版本软件包版本随社区软件包22.09分支一同变更，与openEuler embedded 22.03版本相比部分软件包版本进行了升级，版本测试中仅对基础软件的变更进行基础功能的测试，其他选用的软件包的测试由对应sig测试。

## bugfix测试策略

openEuler embedded 22.09版本是基于openEuler embedded 22.03 LTS版本的功能增强，对于22.03版本发布以来的功能缺陷类的issue，在openEuler embedded 22.09版本测试中进行回归测试。

## 专项测试策略

### 安全测试

openEuler作为社区开源版本，在系统整体安全上需要进行保证，以发现系统中存在的安全脆弱性与风险，为版本的安全提供切实的依据，推动产品完成安全问题整改，提高产品的安全。整体安全测试需要覆盖：

1.  linux系统安全配置/权限管理等

2.  特性涉及到的安全需求验证

3.  CVE漏洞/敏感信息/端口矩阵/交付件病毒扫描

| 测试类         | 描述                      | 具体测试内容                                                 |
| :------------- | ------------------------- | ------------------------------------------------------------ |
| 安全扫描类     | CVE扫描/敏感信息/编译选项 | 通过工具进行相应的扫描，扫描结果采用增量的方式进行分析；编译选项和敏感信息需要针对新开源特性及新增软件包进行； |
| 安全配置管理类 | 社区嵌入式安全配置规范 | 社区嵌入式安全配置包括：服务管理，账号密码管理、文件及用户权限管理、内核参数配置管理、日志管理等；需对openEuler版本进行上述安全配置测试 |

### 可靠性测试

可靠性是版本测试中需重点考虑的测试活动，在各类资源异常/抢占竞争/压力/故障等背景下，通过功能的并发、反复操作进行长时间的测试；过程中通过监控系统资源、进程运行等状态，及时发现系统/特性隐藏的问题。

可靠性的测试建议从关键特性、重要组件、新增特性的可靠性指标和系统级的可靠性进行分析和设计，已保证特性和系统在各类异常、故障及压力背景下的持续提供服务的能力。

| 测试类性     | 具体测试内容                                                 |
| ------------ | ------------------------------------------------------------ |
| 操作系统长稳 | 系统在各种压力背景下，通过构造资源类和服务类等异常，随机执行LTP、系统管理操作等测试；过程中关注系统重要进程/服务，日志等异常情况；建议稳定性测试时长7\*24 |

### 性能测试

对嵌入式操作系统进行性能评估，需要结合特定的硬件和使用场景。我们使用树莓派，一款在社区有广泛使用度的硬件。OS基础性能利用业界普遍的UnixBanch进行测试，对软实时特性使用cyclictest进行测试，与LTS基线数据差异小于5%以内可接受。

| **指标大项** | **指标小项**                                                                               | **指标值**              | **说明**                          |
|--------------|--------------------------------------------------------------------------------------------|-------------------------|-----------------------------------|
| OS基础性能   | 进程调度子系统，内存管理子系统、进程通信子系统、系统调用、锁性能、文件子系统、网络子系统。 | 参考LTS版本相应指标基线 | 与LTS基线数据差异小于5%以内可接受 |
| 软实时性能   | 中断时延加调度时延 | 参考LTS版本相应指标基线 | 与LTS基线数据差异小于5%以内可接受 |

### 兼容性测试

南向兼容性测试为整机适配测试。

本次LTS版本的整机兼容性适配测试会从acpi、impi、memory、系统兼容性、CPU特性、kabi规范性、稳定性等方面进行适配，适配完成后将在社区发布本次LTS版本的整机兼容性清单。

整机适配兼容性测试交付清单如下：

| **嵌入式硬件**  | **CPU型号**  | **测试主体** | **测试计划** |
|--|--|--|--|
| 树莓派4B | BCM2711 | sig-yocto |  |


### 资料测试

资料测试主要是对版本交付的资料进行测试，重点是保证各个资料描述说明的清晰性和功能的正确性，另外openEuler作为一个开源社区，除提供中文的资料还有英文文档也需要重点测试。资料交付清单如下：

| **手册名称**       | **覆盖策略**                                                           | **中英文测试策略** |
|--------------------|------------------------------------------------------------------------|--------------------|
| openEuler Embedded用户指南 | 安装步骤的准确性及各特性使用的正确性 | 英文描述的准确性   |
| openEuler Embedded yocto构建指南 | 构建步骤的准确性 | 英文描述的准确性   |


# 测试执行策略

openEuler embedded 22.09版本按照社区release-manger团队既定的版本计划，共有5轮测试，按照社区研发模式，所有的需求都在拉分支前已完成合入，因此版本测试采取1+3+1的测试方式，即1轮基本功能保障发布beta版本可以提供给外部开发者，3轮全量保障本次版本发布所有特性(新增&继承)以及系统其他dfx能力，1轮回归。

### 测试计划

openEuler 22.09 embedded 版本按照社区开发模式进行运作，结合社区release-manager团队制定的版本计划规划相应的测试活动。供适配开发使用

| Stange name   | Begin time | End time   | Days | Note                          |
| :------------ | :--------- | :--------- | ---- | ----------------------------- |
| Branch        | 2022/7/5   | 2022/7/20  | 1    | 22.09版本从Master分支拉取 |
| Build & Alpha | 2022/7/21  | 2022/7/31  | 5    | 版本DailyBuild & 开发自验证   |
| Test round 1  | 2022/8/22  | 2022/8/28  | 7    | 版本启动测试                           |
| Test round 2  | 2022/8/29  | 2022/9/4   | 7    | 版本全量集成测试                         |
| Test round 3  | 2022/9/5   | 2022/9/11  | 7    | 版本分支代码冻结：管控合入，原则上只允许bug fix   |
| Test round 4  | 2022/9/12  | 2022/9/15  | 4    | 回归测试      |
| Test round 5  | 2022/9/16  | 2022/9/19  | 4    | 回归测试 (9.20~9.29预留buffer)     |
| Release       | 2022/9/30  | 2022/9/30  | 1    |  |

### 测试重点

测试阶段1：
1. 基础OS质量保障：linux系统调用、基本功能测试
2. 基础开源软件包功能验证：存在性、基础功能
3. 兼容性测试：南向硬件测试+北向软件测试
4. 关键新特性的测试验证

测试阶段2：
1. 关键新特性的测试验证
2. 安全测试

测试阶段3：
1. 长稳测试：保证版本的长时间稳定运行，建议运行时长7\*24
2. 性能测试
3. 断电重启测试

测试阶段4：
1. 端到端用户使用场景测试
2. 资料测试

测试阶段5：
1. 问题单回归全量测试

### 入口标准

1.  上个阶段无block问题遗留

2.  转测版本的冒烟无阻塞性问题

### 出口标准

1.  策略规划的测试活动涉及测试用例100%执行完毕

2.  发布特性/新需求/性能基线等满足版本规划目标

3.  版本无block问题遗留，其它严重问题要有相应规避措施或说明

# 附件

无
