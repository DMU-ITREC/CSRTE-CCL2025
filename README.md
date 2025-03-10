# CCL2025面向中文语音的实体关系三元组抽取评测

## 1.组织者及联系方式

评测组织者：宁金忠（大连海事大学）、潘怡霖（大连海事大学）、张益嘉（大连海事大学教授）、帕尔哈提•吐拉江(大连理工大学/新疆师范大学)、孙媛媛（大连理工大学教授）、林鸿飞（大连理工大学教授）

任务负责人、联系人：宁金忠（ningjinzhong@dlmu.edu.cn）

报名&LeaderBoard：天池竞赛平台（[链接](https://tianchi.aliyun.com/competition/entrance/532296)）

## 2.任务内容

传统的关系三元组抽取任务主要集中于书面文本，通过识别实体及其相互关系来构建结构化的知识图谱。然而，语音作为人机交互的主要形式之一，在智能助手、智能客服、语音搜索等诸多应用中发挥着日益重要的作用。因此，如何高效、准确地从语音数据中提取有价值的结构化信息成为研究的热点之一。

面向中文语音的实体关系三元组抽取任务（**C**hinese **S**peech Entity-**R**elation **T**riple **E**xtraction Task，**CSRTE**）旨在从中文语音数据中端到端地自动识别并提取实体及其相互关系，构建结构化的语音关系三元组（头实体、关系、尾实体）。任务的目标在于提升中文语音关系三元组抽取的准确性和效率，增强系统在不同语境和复杂语音环境下的鲁棒性，实现从语音输入到三元组输出的全流程自动化处理。通过本次评测，旨在推动中文语音信息抽取技术的发展，促进语音与自然语言处理技术的深度融合，为智能应用提供更加丰富和精准的基础数据支持。

## 3.评测数据
### 3.1数据集概述
本次评测所使用的数据集来源于开源的Common Voice 17中文子集和AISHELL语音识别数据集，经过专业标注人员对其中的实体及其关系进行精确标注，构建了中文语音关系三元组抽取的评测数据集。该数据集总计约40小时的中文语音数据，包含约20,000条语句，每条语句均提供对应的语音文件以及其中包含的实体文本和关系标注结果（不含原始的转录文本）。标注的实体类别涵盖人物、组织、地点、产品、著作等10类，关系类型预定义超过50种，确保涵盖多样化的语义关系。数据内容涵盖新闻报道、日常对话、正式演讲等多种场景，保证了数据的多样性和代表性，旨在支持系统在不同语境和复杂语音环境下的全面评测。

### 3.2实体和关系类型
 数据集中有'组织'，'人物','地点','产品','著作','金钱','事件','称号','规则条例,'时间'这十类实体。

 所有的预定义关系类型如下：

| **序号** | **头实体类型** | **关系类型** | **尾实体类型** |
| --- | --- | --- | --- |
| 1 | **PERSON（人物）** | 工作/商业/学业关联 | **PERSON（人物）** |
| 2 | **PERSON（人物）** | 亲属关系 | **PERSON（人物）** |
| 3 | **PERSON（人物）** | 伤害 | **PERSON（人物）** |
| 4 | **PERSON（人物）** | 竞争 | **PERSON（人物）** |
| 5 | **PERSON（人物）** | 共指 | **PERSON（人物）** |
| 6 | **PERSON（人物）** | 隶属于 | **ORG（组织）** |
| 7 | **PERSON（人物）** | 提供服务 | **ORG（组织）** |
| 8 | **PERSON（人物）** | 解除关系 | **ORG（组织）** |
| 9 | **PERSON（人物）** | 创立 | **ORG（组织）** |
| 10 | **PERSON（人物）** | 隶属于NORP组织 | **ORG(NORP类组织)** |
| 11 | **PERSON（人物）** | 领导NORP组织 | **ORG(NORP类组织)** |
| 12 | **PERSON（人物）** | 居住于 | **Location（地点）** |
| 13 | **PERSON（人物）** | 工作于 | **Location（地点）** |
| 14 | **PERSON（人物）** | 出生于 | **Location（地点）** |
| 15 | **PERSON（人物）** | 曾到达某地 | **Location（地点）** |
| 16 | **PERSON（人物）** | 死于/埋葬于 | **Location（地点）** |
| 17 | **PERSON（人物）** | 拥有/使用 | **Product（产品）** |
| 18 | **PERSON（人物）** | 参与制造/设计 | **Product（产品）** |
| 19 | **PERSON（人物）** | 参与代言 | **Product（产品）** |
| 20 | **PERSON（人物）** | 参与创作 | **WORK_OF_ART（著作）** |
| 21 | **PERSON（人物）** | 参与表演 | **WORK_OF_ART（著作）** |
| 22 | **PERSON（人物）** | 评论 | **WORK_OF_ART（著作）** |
| 23 | **PERSON（人物）** | 作为角色一员 | **WORK_OF_ART（著作）** |
| 24 | **PERSON（人物）** | 收入金钱 | **MONEY（金钱）** |
| 25 | **PERSON（人物）** | 支出金钱 | **MONEY（金钱）** |
| 26 | **PERSON（人物）** | 持有称号/职业 | **TITLE（称号/职业）** |
| 27 | **PERSON（人物）** | 参与提出过程 | **REGULATION（规则条例）** |
| 28 | **PERSON（人物）** | 遵守/支持 | **REGULATION（规则条例）** |
| 29 | **PERSON（人物）** | 违反/反对 | **REGULATION（规则条例）** |
| 30 | **PERSON（人物）** | 参与事件 | **EVENT（事件）** |
| 31 | **ORG（组织）** | 隶属于 | **ORG（组织）** |
| 32 | **ORG（组织）** | 协作 | **ORG（组织）** |
| 33 | **ORG（组织）** | 位于/业务地点 | **Location（地点）** |
| 34 | **ORG（组织）** | 研发/生产/销售 | **Product（产品）** |
| 35 | **ORG（组织）** | 管理/使用 | **Product（产品）** |
| 36 | **ORG（组织）** | 出版/发行 | **WORK_OF_ART（作品）** |
| 37 | **ORG（组织）** | 收入 | **MONEY（金钱）** |
| 38 | **ORG（组织）** | 支出 | **MONEY（金钱）** |
| 39 | **ORG（组织）** | 参与制定过程 | **REGULATION（规则条例）** |
| 40 | **ORG（组织）** | 遵守 | **REGULATION（规则条例）** |
| 41 | **ORG（组织）** | 违反/反对 | **REGULATION（规则条例）** |
| 42 | **ORG（组织）** | 设立职位/称号/奖项 | **TITLE（称号/职业）** |
| 43 | **ORG（组织）** | 参与事件 | **EVENT（事件）** |
| 44 | **ORG（组织）** | 组织 | **EVENT（事件）** |
| 45 | **Location（地点）** | 位于 | **Location（地点）** |
| 46 | **Location（地点）** | 临近 | **Location（地点）** |
| 47 | **Product（产品）** | 价值/售价 | **MONEY（金钱）** |
| 48 | **Product（产品）** | 发布日期 | **Date（时间）** |
| 49 | **Product（产品）** | 产地关系 | **Location（地点）** |
| 50 | **WORK_OF_ART（著作）** | 发布日期 | **Date（事件）** |
| 51 | **Event（事件）** | 发生时间 | **Date（时间）** |
| 52 | **Event（事件）** | 发生地 | **Location（地点）** |

### 3.3数据样例

```
{
    "audio_id": "sample",
    "data_annotation": [
        [
            [
                "沙玛什",
                "持有称号/职业",
                "正义之神"
            ]
        ],
        [
            [
                "沙玛什",
                "隶属于",
                "苏美尔乌图神"
            ],
            [
                "沙玛什",
                "隶属于NORP组织",
                "苏美尔乌图神"
            ]
        ],
        [
            [
                "苏美尔乌图神",
                "设立职位/称号/奖项",
                "正义之神"
            ]
        ]
    ]
}
```
[此处获取音频BAC009S0193W0470](https://github.com/DMU-ITREC/CSRTE-CCL2025/blob/main/example.wav)




## 4.评价标准

评测任务将采用以下指标对参赛系统的三元组抽取性能进行评估：

准确率（P）： 正确抽取的三元组数与系统抽取的总三元组数之比。

$P=\frac{\text{正确抽取的三元组数}}{\text{系统抽取的总三元组数}}$

召回率（R）： 正确抽取的三元组数与数据集中真实三元组总数之比。

$R=\frac{\text{正确抽取的三元组数}}{\text{数据集中真实三元组总数}}$


F1值（F1-score）： 准确率和召回率的调和平均数，作为综合性能指标。

$F1=2\times \frac{P\times R}{P+R}$

**额外说明：在评测过程中，抽取的实体仅将边界与标注数据进行严格匹配原则，不包含实体的类型。**

## 5.评测赛程

| 任务                           | 日期                      |
|--------------------------------|---------------------------|
| 评测任务发布                    | 2025/01/01                |
| 报名时间                        | 2025/01/01 - 2025/05/01   |
| 训练集发布                      | 2025/03/01                |
| 测试集A榜发布时间（非最终测试集，不计分） | 2025/03/15                |
| 测试集A榜提交截至时间            | 2025/05/02                |
| 测试集B榜发布时间（即最终排名成绩） | 2025/05/03                |
| 测试集B榜提交截至时间            | 2025/05/10                |
| 获奖队伍提交材料（核实无误即可获得颁奖资格，不合格者被延顺） | 2025/05/10 - 2025/05/17   |
| 公布颁奖队伍                    | 2025/05/17 - 2025/05/20   |
| 撰写并提交技术报告              | 2025/05/21 - 2025/06/10   |
| 评测论文审稿 & 录用通知         | 2025/06/11 - 2025/06/20   |
| 评测论文Camera-ready版提交     | 2025/06/25                |
| 评测论文纠错排版 & 提交ACL/CCL Anthology收录 | 2025/07/01                |
| CCL 2025技术评测研讨会          | 2025/08                   |


## 6.资助情况

本次测评由 AutoDL  赞助。[AutoDL.com](AutoDL.com) 是目前全国最大的C端AI算力租用平台之一，面向“大 AI 圈”内的科研工作者和科技企业，提供弹性、省钱、好用的普惠AI云算力服务。

一等奖0-1名，奖金合计6000元；

二等奖0-2名，奖金合计6000元；

三等奖0-4名，奖金合计6000元。

