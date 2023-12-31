![avatar](../images/openEuler.png)

版权所有 © 2020 openEuler社区  
您对“本文档”的复制、使用、修改及分发受知识共享(Creative
Commons)署名—相同方式共享4.0国际公共许可协议(以下简称“CC BY-SA
4.0”)的约束。为了方便用户理解，您可以通过访问<https://creativecommons.org/licenses/by-sa/4.0/>
了解CC BY-SA 4.0的概要 (但不是替代)。CC BY-SA
4.0的完整协议内容您可以访问如下网址获取：<https://creativecommons.org/licenses/by-sa/4.0/legalcode>。

修订记录

| 日期 | 修订版本 | CR号 | 修改  章节 | 修改描述 | 作者 |
|------|----------|------|------------|----------|------|
| 2023.02.14     | 1.0.0         |      |            |     初稿     |   liuyu   |
|      |          |      |            |          |      |

***

# 测试策略

## 总体测试策略

23.03 版本新版内核的回归测试。

## 继承feature/组件测试设计策略

### 硬件兼容性测试

| 硬件型号 | 硬件配置信息 | 备注 |
| -------- | ------------ | ---- |
| 树莓派 4B 卡 | CPU:Cortex-A72 * 4 内存：8GB 存储设备：SanDisk Ultra 16GB micro SD | 默认测试环境，数量 1 |
| 树莓派 3B+ 卡 | CPU:Cortex-A53 * 4 内存：1GB 存储设备：SanDisk Ultra 16GB micro SD | 硬件兼容性测试环境，数量 1 |
| 树莓派 3B 卡 | CPU:Cortex-A53 * 4 内存：1GB 存储设备：SanDisk Ultra 16GB micro SD | 硬件兼容性测试环境，数量 1 |

硬件兼容性测试项：供电接口、USB 口、Micro HDMI、RJ 45 接口、wifi、蓝牙。

### 软件功能测试

下列软件功能测试以树莓派 4B 卡为准。

#### 安装测试

镜像写卡、启动、内核版本检查、系统版本检查。

#### 基本功能测试

基本常用服务包、开发环境、库。

#### 管理工具测试

dnf 软件管理、管理服务。

#### 可靠性测试

reboot 100。

### 测试计划

| Stange name | Begin time | End time | Days | 测试执行策略 | 备注 |
|----|----|----|----|-----|----|
| round 1 | 2023/2/20 | 2023/2/24 | 5 | 全量测试 |  |
| round 3 | 2023/3/6 | 2023/3/10 | 5 | 回归测试 |  |

### 测试重点

检验内核版本、各项基本功能的回归测试、各支持机型的硬件兼容性测试。
