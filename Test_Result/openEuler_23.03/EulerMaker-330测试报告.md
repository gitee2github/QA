![openEuler ico](../../images/openEuler.png)

版权所有 © 2021  openEuler社区
您对“本文档”的复制、使用、修改及分发受知识共享(Creative Commons)署名—相同方式共享4.0国际公共许可协议(以下简称“CC BY-SA 4.0”)的约束。为了方便用户理解，您可以通过访问[*https://creativecommons.org/licenses/by-sa/4.0/*](https://creativecommons.org/licenses/by-sa/4.0/) 了解CC BY-SA 4.0的概要 (但不是替代)。CC BY-SA 4.0的完整协议内容您可以访问如下网址获取：[*https://creativecommons.org/licenses/by-sa/4.0/legalcode*](https://creativecommons.org/licenses/by-sa/4.0/legalcode)。

修订记录

| 日期       | 修订版本 | 修改章节 | 修改描述   |
| ---------- | -------- | -------- | ---------- |
| 2023/4/11 | 1.1.0    | 初始     |yangshicheng |

**关键词：**

统一构建平台测试策略 web界面 单包构建 全量构建 增量构建 镜像定制 分层定制 任务优先级设置 秘钥管理 多用户队列 过载控制 资源监控。

**摘要：**

文本主要描述统一构建 330版本的整体测试过程，详细叙述测试覆盖情况，并通过问题分析对版本整体质量进行评估和总结。


# 1   概述

统一构建平台是一个支持多种形式创建任务，简化多包构建，提升包构建效率，任务可追溯，支持重复构建，支持结果发布的一个构建系统。除此之外，该平台可针对不同用户设置不同的任务优先级，并为用户提供个性化、智能化的镜像定制与分层定制服务。该平台利用过载控制、资源监控等方式来防止任务大量堆积造成构建堵塞，进一步保证了服务质量以及构建效率。

本文主要描述统一构建 330版本的总体测试活动，按照社区开发模式进行运作，结合社区release-manager团队制定的版本计划规划相应的测试计划及活动。测试报告覆盖新需求测试执行情况和评估，并结合各类专项测试活动和版本问题单总体情况进行整体的说明和质量评估。

# 2   测试版本说明

1.统一构建 330版本新增单包及构建任务的执行效率提升、分层定制、构建任务优先级设置、软件包可重复构建、镜像定制、git-mirror服务效率提升、秘钥管理、用户贡献仓滚动更新发布场景建设、多用户队列、上传签名、过载控制、限流以及系统资源监控需求：


| 特性名称   | EBS-330-SDV1 | EBS-330-SDV2| EBS-330-SDV3 | EBS-330-SDV4 |  EBS-330-SIT1 |  EBS-330-SIT2 |    EBS-330-SIT3 |
| ----------|   --------    |   --------    |   --------   |   --------   |    --------   |   --------   |   --------    |
| 单包及构建任务的执行效率提升                  | 0201-0203    |  0207-0210 | 0213-0217 | 0220-0224  |  0225-0302 | 0303-0307 | 0308-0325 |
| 秘钥管理                                    | 0201-0203   | 0207-0210  | 0213-0217 | 0220-0224  |  0225-0302 | 0303-0307 | 0308-0325 |
| 分层定制                                    | 0201-0203   | 0207-0210  | 0213-0217 | 0220-0224  |  0225-0302 | 0303-0307 | 0308-0325 |
| 软件包可重复构建                             |  /   | 0207-0210  | 0213-0217 | 0220-0224  |  0225-0302 | 0303-0307 | 0308-0325 |
| 镜像定制                                    |  /   | 0207-0210  | 0213-0217 | 0220-0224  |  0225-0302 | 0303-0307 | 0308-0325 |
| git-mirror服务效率提升                        |  /   | 0207-0210  | 0213-0217 | 0220-0224  |  0225-0302 | 0303-0307 | 0308-0325 |
| 构建任务优先级设置                            |  / | 0207-0210  | 0213-0217 | 0220-0224  |  0225-0302 | 0303-0307 | 0308-0325 |
| 用户贡献仓滚动更新发布场景建设                 | /   | 0207-0210  | 0213-0217 | 0220-0224  |  0225-0302 | 0303-0307 | 0308-0325 |
| 多用户队列                                   |  /  | /  | / | / |  0225-0302 | 0303-0307 | 0308-0325 |
| 上传签名                                     |  /  | /  | / | / |  0225-0302 | 0303-0307 | 0308-0325 |
| 过载控制、限流                               |  /  | /  | / | / |  0225-0302 | 0303-0307 | 0308-0325 |
| 系统资源监控                                 |  /  | /  | / | / |  0225-0302 | 0303-0307 | 0308-0325 |

测试的环境如下：

| 测试机                            | 配置信息                                                                          |个数| 备注                      |
| ----------------------------------- | ------------------------------------------------------------------------------------- | ------------------------- | ------------------------- |
| kubeoperator部署机| ARCH: arm<br />CPU: 8P<br />MEM: 15G<br />DISK_OS: 200G|1台|测试执行机|
| kubeoperator部署机| ARCH: x86<br />CPU: 8P<br />MEM: 16G<br />DISK_OS: 200G|1台|测试执行机|
| server01| ARCH: arm<br />CPU: 48P<br />MEM: 96G<br />DISK_OS: 200G|1台|测试执行机|
| testbox| ARCH: arm<br />CPU: 48P<br />MEM: 188G<br />DISK_OS: 200G|1台|测试执行机|
| testbox| ARCH: x86<br />CPU: 64P<br />MEM: 128G<br />DISK_OS: 200G|4台|测试执行机|

# 3   版本概要测试结论

   统一构建 330版本整体测试按照release-manager团队的计划，共完成了四轮模块测试+三轮全量测试和回归测试；其中第一轮模块测试主要聚焦在新特性全量功能的验证以及平台web页面基础功能的测试；第二轮模块测试一方面针对新特性的功能进行全量测试，除此之外，对第一轮模块测试重点特性功能进行测试并验证第一轮模块测试的问题单验证和影响程度，同时开展安全测试；第三、第四轮模块测试，主要是针对问题单较多的模块进行全量测试，以及对现有的功能模块进行集成性的验证，验证问题单的修复情况以及是否因修复引入新的问题。第一轮回归测试对风险较大的模块进行重点覆盖和扩展测试，并针对新的需求进行模块化的测试。第二轮、第三轮回归测试主要是针对前几轮遗留问题单进行回归验证，并对重点功能模块进行全量以及扩展测试，验证问题的修复和影响程度；旨在保证发布件和测试验证过程交付件的一致性。330版本按照测试策略完成了全量功能验证和专项测试(性能、可靠性、安全)，所有测试任务均按计划完成。本版本计划交付SR需求12个，实际交付12个，交付率100%，所有发布需求均验证通过。

​    统一构建 330版本共发现问题124个，有效问题120个，回归测试遗留结果正常。版本整体特性质量基本可用，遗留少量问题。

# 4   版本详细测试结论

版本详细测试内容包括：

1、完成单包及构建任务的执行效率提升，完成软件包分层定制，构建任务优先级设置，软件包可重复构建，镜像定制，git-mirror服务效率提升，秘钥管理，用户贡献仓滚动更新发布场景建设，多用户队列，上传签名，过载控制，限流以及系统资源监控等特性的全量功能验证，特性质量较好；

2、专项测试包括性能专项、安全专项、可靠性测试；

## 4.1   特性测试结论

### 4.1.1   新需求评价

建议以表格的形式汇总新特性测试执行情况及遗留问题单情况的评估,给出特性质量评估结论。

| **序号** | **特性名称**                                         | **测试覆盖情况**                                             | **约束依赖说明** | **遗留问题单** | **质量评估**               | **备注<img width=50/>**                                      |
| -------- | ---------------------------------------------------- | ------------------------------------------------------------ | ---------------- | -------------- | -------------------------- | ------------------------------------------------------------ |
| 1        |        单包及构建任务的执行效率提升                              | 覆盖ccache使能前后对单包构建效率提升的场景、 查看ccache命中率、对比初次编译和第二次编译时长是否缩短、后端查看相应的ccache共享卷容器是否建立、yum cache使能前后对全量和增量构建效率提升情况、执行机使能环境检查、查看实际分配的CPU和内存大小是否与描述一致等相关功能，并检查在全量构建中软件包构建范围识别、校验不同情况下全量构建的最终返回值是否正常；共执行用例13条，整体质量良好 | NA               | NA             | <font color=blue>▲</font> |                                                             |
| 2        | 平台支持分层定制                              | 覆盖支持yaml带条件的值解析、支持多层定制，软件包的配置值可进行合并输出、支持值类型校验，当值不满足要求是进行报错，支持用户设置构建标识、yaml及shell分立文件合并、转换工具可以将原始spec文件转换为分立文件、web端可以编辑修改分层url、支持yaml转spec,可以基于转换后的spec 进行构建。共执行用例81条，整体质量良好| NA               | NA             | <font color=green>█</font>  |  |
|3| 支持构建任务优先级设置 | 覆盖在以下场景vip用户的任务是否会被优先执行：vip用户与其他用户提交单包构建、vip用户提交单包构建，其他用户提交全量构建或增量构建、VIP用户提交全量构建其他用户提交单包构建、vip用户与其他用户都提交全量构建；以及验证vip用户是否只能注册一个。共执行用例6条，整体质量良好 |NA|NA|<font color=green>█</font>  | |
| 4        | 平台支持软件包可重复构建                                         | 两次单包，全量，增量构建faketime使能，faketime不使能，一次使能一次不使能，对比二进制文件MD5值是否一致，共执行用例数9条，未发现问题，质量良好| NA               | NA             | <font color=green>█</font> |                                                              |
| 5        | 镜像定制，支持基于用户配置定制容器、虚拟、iso镜像     | 覆盖镜像定制模块web页面功能测试场景，包括web页面上界面信息校验、流水线的创建、克隆、删除、查询功能，对不同镜像格式（iso、docker、mini_docker、cpio、mini_cpio）流水线配置的内容进行填写、修改及查看，对构建历史详情镜像检查，支持构建不同格式镜像产物、查看镜像构建日志信息、访问下载构建产物功能；完成镜像image software source配置验证（包括https/http协议）、参数配置页面repo源格式以及镜像输输入框字符长度等校验，相关镜像名称、版本号等内容的填写、修改、保存和取消、用户管理界面用户添加、删除、检索、权限修改功能；后端查看用户上传文件存储路径、流水线配置信息及构建产物存放路径，完成对每种构建产物镜像安装验证。共执行用例172条，整体质量良好  | NA               | NA             | <font color=green>█</font> |                                                              |
| 6        | git-mirror服务效率提升                               | 覆盖有代码更新的仓库会拉取代码，没有代码更新的仓库不会有拉取代码的操作，同一个工程首次构建比第二次构建拉取代码时长缩短。共执行用例3条，整体质量良好| NA               | NA             | <font color=green>█</font> |                                                              |
| 7        | 平台支持秘钥管理，用于软件包签名                             | 更新密钥完成签明，查看签明是否使用新生成的子密钥进行签明，并检查密钥长度及加密算法，共执行3条用例，提出自动完成密钥配置文件更新需求，问题单已解决，质量良好 | NA               | NA             | <font color=green>█</font> |                                                              |
| 8        | 用户贡献仓，滚动更新发布场景建设                            | web页面及后端上用户贡献仓支持修改、增加、删除功能；后端滚动更新发布支持配置文件各个字段参数校验，同时可设定多个定时任务；共执行用例11条，发现问题已解决，整体质量良好 | NA               | NA             | <font color=green>█</font> |                                                              |
| 9        |    平台支持多用户队列设置不同优先级                         | 覆盖设置用户优先级后查询是否设置成功、设置优先级的用户与不设置优先级的用户相比构建任务是否优先被执行、多个用户设置不同优先级，任务执行顺序是否按照优先级顺序执行，不同用户设置相同优先级，不同权重，权重大的是否有更高概率优先被执行、用户设置优先级不在规定范围内能否设置成功、设置了优先级的用户，优先级能否取消。共执行用例8条，整体质量良好 | NA               | NA             | <font color=green>█</font> |                                                              |
| 10        |   平台支持rpm上传签名设计                        | 检查签名由发布时改为构建任务结束结果上过上传后做签名，共执行用例1条，发现问题已解决| NA               | NA             | <font color=green>█</font> |
| 11       |    任务构建支持过载控制、限流                         | 限流部分校验单工程任务的上限值、系统工程任务的上限值及用户提交任务的上限值在不同构建场景是否生效，检查前端错误信息提示，两种方式（redis、configmap.yaml）修改不同上限值是否生效，验证admin用户权限；过载控制部分校验了三个上限值（total_jobs_quota、soft_quota、hard_quota）是否生效、检查超过上限值时日志提示信息、改变调整上限值是否生效、并验证观察上限值异常设置时的报错信息。共执行用例45条，整体质量良好 | NA               | NA             | <font color=green>█</font> |
| 12       |    平台支持系统资源监控             | 检查新增，删除被监控机器wgcloud是否同步更新监控列表，以及被监控服务器数据显示是否正常，共执行3条用例，质量良好 | NA               | NA             | <font color=green>█</font> |

<font color=red>●</font>： 表示特性不稳定，风险高

<font color=blue>▲</font>： 表示特性基本可用，遗留少量问题

<font color=green>█</font>： 表示特性质量良好


### 性能测试

| **指标大项** | **指标小项**                                                 | **指标值**                   | 测试结论                 |
| ------------- | ------------------------------------------------------------ | ---------------------------- | ------------------------ |
| 接口性能    | 10并发，5秒内启动，持续时长300s | tips 0.27/sec| 除delete_pipeline接口其余均达到基线要求      |
| web端网页页面响应时间      | 新增4个页面，测试覆盖4个页面，覆盖率100%，首屏时长取3次测试平均值小于3s, 质量良好         | 3s | 达到基线要求      |

## 接口测试

<table>
    <tr>
        <th>接口</th><th>线程数</th><th>启动时间</th><th>持续时间</th><th>Samples</th><th>Average</th><th>Median</th><th>90%Line</th><th>95%Line</th><th>99%Line</th><th>Min</th><th>Max</th><th>Error %</th><th>Throughput</th><th>Received</th><th>Sent KB/sec</th>
    </tr>
    <tr>
        <td rowspan="2">add_user</td><td>1</td><td>5s</td><td>300s</td><td>3948</td><td>75</td><td>74</td><td>79</td><td>91</td><td>106</td><td>68</td><td>171</td><td>0.00%</td><td>13.15684</td><td>36.62</td><td>13.45</td>
    </tr>
    <tr>
        <td>10</td><td>5s</td><td>300s</td><td>24849</td><td>119</td><td>106</td><td>179</td><td>200</td><td>240</td><td>70</td><td>367</td><td>0.00%</td><td>82.79274</td><td>230.43</td><td>84.65</td>
    </tr>
    <tr>
        <td rowspan="2">delete_user</td><td>1</td><td>5s</td><td>300s</td><td>3959</td><td>75</td><td>73</td><td>81</td><td>90</td><td>109</td><td>67</td><td>169</td><td>0.00%</td><td>13.19385</td><td>36.36</td><td>13.32</td>
    </tr>
    <tr>
        <td>10</td><td>5s</td><td>300s</td><td>23013</td><td>129</td><td>117</td><td>193</td><td>214</td><td>252</td><td>69</td><td>1163</td><td>0.00%</td><td>76.67575</td><td>211.31</td><td>77.42</td>
    </tr>
    <tr>
        <td rowspan="2">create_pipeline</td><td>1</td><td>5s</td><td>300s</td><td>3566</td><td>83</td><td>82</td><td>88</td><td>104</td><td>113</td><td>75</td><td>173</td><td>0.00%</td><td>11.88651</td><td>12.11</td><td>13.65</td>
    </tr>
    <tr>
        <td>10</td><td>5s</td><td>300s</td><td>18208</td><td>163</td><td>139</td><td>265</td><td>290</td><td>342</td><td>78</td><td>501</td><td>0.00%</td><td>60.66037</td><td>61.79</td><td>69.66</td>
    </tr>
    <tr>
        <td rowspan="2">show_pipelines</td><td>1</td><td>5s</td><td>300s</td><td>459</td><td>654</td><td>645</td><td>699</td><td>713</td><td>721</td><td>608</td><td>769</td><td>0.00%</td><td>1.52765</td><td>171.51</td><td>1.41</td>
    </tr>
    <tr>
        <td>10</td><td>5s</td><td>300s</td><td>2690</td><td>1109</td><td>881</td><td>1845</td><td>2236</td><td>2707</td><td>620</td><td>3208</td><td>0.00%</td><td>8.92765</td><td>1002.34</td><td>8.23</td>
    </tr>
    <tr>
        <td rowspan="2">show_pipeline</td><td>1</td><td>5s</td><td>300s</td><td>8634</td><td>34</td><td>34</td><td>36</td><td>36</td><td>62</td><td>30</td><td>78</td><td>0.00%</td><td>28.77731</td><td>32.15</td><td>28.13</td>
    </tr>
    <tr>
        <td>10</td><td>5s</td><td>300s</td><td>79231</td><td>37</td><td>34</td><td>47</td><td>61</td><td>73</td><td>30</td><td>272</td><td>0.00%</td><td>264.0937</td><td>295.04</td><td>258.16</td>
    </tr>
    <tr>
        <td rowspan="2">update_pipeline</td><td>1</td><td>5s</td><td>300s</td><td>4026</td><td>74</td><td>72</td><td>79</td><td>89</td><td>105</td><td>67</td><td>139</td><td>0.00%</td><td>13.41763</td><td>35.94</td><td>28.21</td>
    </tr>
    <tr>
        <td>10</td><td>5s</td><td>300s</td><td>23669</td><td>125</td><td>112</td><td>188</td><td>211</td><td>255</td><td>69</td><td>1118</td><td>0.00%</td><td>78.80735</td><td>211.1</td><td>165.7</td>
    </tr>
    <tr>
        <td rowspan="2">delete_pipeline</td><td>1</td><td>5s</td><td>300s</td><td>2864</td><td>97</td><td>97</td><td>105</td><td>123</td><td>131</td><td>47</td><td>267</td><td>0.06075%</td><td>10.27945</td><td>10.03</td><td>10.27</td>
    </tr>
    <tr>
        <td>10</td><td>5s</td><td>300s</td><td>12456</td><td>186</td><td>142</td><td>315</td><td>351</td><td>580</td><td>43</td><td>30902</td><td>0.31744%</td><td>45.66384</td><td>36.22</td><td>45.43</td>
    </tr>
    <tr>
        <td rowspan="2">create_task</td><td>1</td><td>5s</td><td>300s</td><td>179</td><td>1677</td><td>1678</td><td>1705</td><td>1714</td><td>1737</td><td>1638</td><td>1752</td><td>0.00%</td><td>0.59608</td><td>1.41</td><td>0.6</td>
    </tr>
    <tr>
        <td>10</td><td>5s</td><td>300s</td><td>540</td><td>5571</td><td>7023</td><td>8198</td><td>8230</td><td>8264</td><td>1663</td><td>8345</td><td>0.00%</td><td>1.7622</td><td>4.17</td><td>1.78</td>
    </tr>
    <tr>
        <td rowspan="2">show_task</td><td>1</td><td>5s</td><td>300s</td><td>8898</td><td>33</td><td>33</td><td>34</td><td>35</td><td>61</td><td>29</td><td>81</td><td>0.00%</td><td>29.65921</td><td>18.91</td><td>28.91</td>
    </tr>
    <tr>
        <td>10</td><td>5s</td><td>300s</td><td>80846</td><td>36</td><td>33</td><td>50</td><td>60</td><td>73</td><td>29</td><td>137</td><td>0.00%</td><td>269.4597</td><td>171.83</td><td>262.62</td>
    </tr>
</table>


## Web页面响应
|**web页面**|**first time**|**second time**|**third time**| **average  value**                 |
| ------------- | ------------------------------------------------------------ | ---------------------------- |---------------------------- | ------------------------ |
|  流水线列表FCP  |700ms | 598.08ms | 681.89ms | 659.99ms |
|  流水线详情FCP  | 681.92ms | 519.2ms | 501.22ms|567.45ms |
|  构建历史FCP  | 533.0ms | 524.8ms | 524.0ms| 527.27ms |
|  用户管理FCP  | 537.0ms| 498.3ms | 520.4ms | 518.57ms |

# 5   问题单统计

给出版本问题单的分布或分类统计及问题单走势分析。

统一构建 330版本共发现问题单124（不包含安全扫描问题）个，其中缺陷类问题单85个，需求类问题单39个，有效问题120个，其中修复问题单115个，回归均通过, 待修复的5个问题中，1个经过CCB评审确认遗留，剩余4个问题属于需求类问题，待SE纳入需求管道。详细分布见下表:

| 测试阶段     | 问题单数 | 需求单 | 缺陷单 | 有效问题单数 | 无效问题单数 |
| ------------ | :-:  | :-:|:-:| :-:  | :-:|
| EBS-330-SDV1 | 15   | 3 | 12 | 15 | 0 |
| EBS-330-SDV2 | 14   | 3 | 11 | 14 | 0 |
| EBS-330-SDV3 | 32   | 5 | 27 | 31 | 1 |
| EBS-330-SDV4 | 13   | 5 | 8 | 13 | 0 |
| EBS-330-SIT1 | 11   | 6 | 5 | 10 | 1 |
| EBS-330-SIT2 | 15   | 9 | 6 | 14 | 1 |
| EBS-330-SIT3 | 24  | 8 | 16 | 23 | 1 |

330版本功能测试用例356条，接口功能测试用例150条，接口性能测试用例10条，整体看版本问题单呈收敛趋势明显。

# 6 附件

## 遗留问题列表

| 序号 | 问题简述                            | 问题级别 | 问题分析                                                     | 影响分析                                                     | 规避措施                           |
| ---- | ----------------------------------- | -------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ---------------------------------- |
| 1    | yum cache使能，全量构建出现构建失败 | 中       | yum cache本身的锁机制决定了不支持多进程同时执行 makecache/download/install的操作 | 全量构建任务在保障每日定时执行的前提下，少量构建失败的包，对外几乎不感知，而且这些包不一定非得构建，因为总会在上一次或者下一次的增量构建中构建成功 | 申请足够多的执行机资源，并发度调低 |

