# 3.0 COUNTER报告的技术规格

## 3.1 图书馆的COUNTER报告

R5的报告由四个主报告组成，这些主报告使馆员可以过滤和配置来为他们的使用数据创建自定义视图。R5还明确了标准视图（预设的过滤器/配置）。

为了达到合规性，内容提供商必须提供适用于他们的Host_Type的**主报告**和**标准视图**，始终为空的标准视图除外（比如不会发生被拒绝的情况，那么一个**拒绝访问的标准视图**就是始终为空的）。

内容提供者可以根据《行为准则》为报告设置的规则提供合规或自定义报告不需要的额外的主报告和标准视图。对于这些报告（见11.2节），不需要审核。

### 3.1.1 主报告

主报告包括所有相关指标和属性；它们旨在通过应用**过滤器**和其他配置选项进行自定义，从而使馆员可以创建针对其需求的报告。表3.a中显示了四个主报告以及它们需要的Report_ID，Report_Name和Host_Type。有关Host_Types的详细信息，请参见下面的3.3.1节。

表3.a 主报告

| Report_ID | Report_Name                          | Details                                                      | Host_Types |
| --------- | ------------------------------------ | ------------------------------------------------------------ | ------------------------------------------ |
| PR        | 平台主报告（Platform Master Report） | 可自定义的报告，总结了内容提供商平台上的活动，允许用户应用过滤器并选择其他配置选项。 | All Host_Types: <br/>A&I_Database<br/>Aggregated_Full_Content<br/>Data_Repository*<br/>Discovery_Service<br/>eBook<br/>eBook_Collection<br/>eJournal<br/>Full_Content_Database<br/>Multimedia<br/>Multimedia_Collection<br/>Repository<br/>Scholarly_Collaboration_Network |
| DR | 数据库主报告（Database Master Report） | 可定制的数据库详细活动报告，允许用户应用过滤器并选择其他配置选项。 | A&I_Database<br/>Aggregated_Full_Content<br/>Discovery_Service<br/>eBook_Collection<br/>Full_Content_Database<br/>Multimedia_Collection |
| TR | 标题主报告（Title Master Report） | 可自定义的标题级别（期刊，书籍等）的详细活动报告，允许用户应用过滤器并选择其他配置选项。 | Aggregated_Full_Content<br/>eBook<br/>eBook_Collection<br/>eJournal |
| IR | 项主报告（Item Master Report） | 细粒度的可自定义报告，显示项（文章，章节，媒体对象等）级别的活动，允许用户应用过滤器并选择其他配置选项。 | Data_Repository*<br/>Multimedia<br/>Repository<br/>Scholarly_Collaboration_Network |

### 3.1.2 标准视图

标准视图的目标是提供一个主报告的预过滤视图集，覆盖了图书馆需要的最常见的集合。标准视图的Report_ID是从它们基于的主报表的Report_ID派生的。格式为*{Master Report_ID}* _ *{View ID}*。

#### 3.1.2.1 平台使用标准视图

平台使用标准视图派生自平台主报告，提供给定的平台活动的总结以支持平台的评估，并提供高层次的统计数据来支持调查和对资助者汇报。

表 3.b: 平台使用标准视图

| Report_ID | Report_Name                | Details                                           | Host_Types                                                   |
| --------- | -------------------------- | ------------------------------------------------- | ------------------------------------------------------------ |
| PR_P1     | 平台使用（Platform Usage） | 以指标类型（Metric_Type）总结的平台级别使用情况 . | All Host_Types:<br/>A&I_Database<br/>Aggregated_Full_Content<br/>Data_Repository*<br/>Discovery_Service<br/>eBook<br/>eBook_Collection<br/>eJournal<br/>Full_Content_Database<br/>Multimedia<br/>Multimedia_Collection<br/>Repository<br/>Scholarly_Collaboration_Network |

有关平台使用报告的详细信息，请参见下面的第4.2节。

#### 3.1.2.2 数据库使用标准视图

数据库使用标准视图支持评估给定资源数据库（例如，全文数据库，A＆I数据库或多媒体集合）的价值。

表 3.c: 数据库使用标准视图

| Report_ID | Report_Name                    | Details                                                      | Host_Types                                                   |
| --------- | ------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| DR_D1     | Database Search and Item Usage | 评估数据库所需的关键搜索，访问和请求指标报告                 | A&I_Database Aggregated_Full_Content Discovery_Service eBook_Collection Full_Content_Database Multimedia_Collection |
| DR_D2     | Database Access Denied         | 用户因为同时使用许可证超出限制，或者他们的机构没有这个数据库的许可证而被拒绝访问的数据库拒绝访问活动报告。 | A&I_Database Aggregated_Full_Content Discovery_Service eBook_Collection Full_Content_Database Multimedia_Collection |

有关数据库使用报告的详细信息，请参见下面的第4.2节。