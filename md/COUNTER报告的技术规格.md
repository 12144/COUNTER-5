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

#### 3.1.2.3 标题使用标准视图

标题使用标准视图用于支持对连载（例如期刊，杂志或报纸）或专著（例如书籍，电子书，教科书或参考书目）的标题的价值进行评估。

表 3.d: 标题使用标准视图

| Report_ID | Report_Name                                 | Details                                                      | Host_Types                                             |
| --------- | ------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------ |
| TR_B1     | Book Requests (Excluding OA_Gold)           | 报告书籍的全文活动，不包括Gold Open Access内容，如 **Total_Item_Requests**和**Unique_Title_Requests**。<br/>**Unique_Title_Requests**提供了跨图书平台的可比较方法。**Total_Item_Requests**显示总体活动；但是，根据内容的交付方式（例如，作为一本完整的书还是按章节交付），站点之间的数量将有很大不同。 | Aggregated_Full_Content<br/>eBook<br/>eBook_Collection |
| TR_B2     | Book Access Denied                          | 用户因为同时使用许可证超出限制，或者他们的机构没有这个书籍的许可证而被拒绝访问的书籍拒绝访问活动报告。 | Aggregated_Full_Content<br/>eBook<br/>eBook_Collection |
| TR_B3     | Book Usage by Access Type                   | 书籍使用的报告，显示了按Access_Type细分的所有适用的Metric_Type。 | Aggregated_Full_Content<br/>eBook<br/>eBook_Collection |
| TR_J1     | Journal Requests (Excluding OA_Gold)        | 期刊内容使用报告, 不包括Gold Open Access内容，如 **Total_Item_Requests**和**Unique_Item_Requests**。<br/>**Unique_Item_Requests**通过减少自动显示HTML全文但用户随后访问PDF版本时产生的重复访问影响，在整个期刊平台上提供可比较的方法。**Total_Item_Requests**显示总体活动。 | Aggregated_Full_Content eJournal                       |
| TR_J2     | Journal Access Denied                       | 用户因为同时使用许可证超出限制，或者他们的机构没有这个标题的许可证而被拒绝访问的期刊拒绝访问活动报告。 | Aggregated_Full_Content eJournal                       |
| TR_J3     | Journal Usage by Access Type                | 报告按Access_Type细分的所有Metric_Type的期刊内容使用情况。   | Aggregated_Full_Content eJournal                       |
| TR_J4     | Journal Requests by YOP (Excluding OA_Gold) | 按出版年份（YOP）细分期刊内容（不包括Gold Open Access内容）的使用情况， 并提供**Metric_Types**（**Total_Item_Requests**和**Unique_Item_Requests**）的计数。提供分析备份文件或永久访问协议所涵盖内容的使用所必需的细节。请注意，COUNTER报告不提供访问模型或永久访问权限详细信息。 | Aggregated_Full_Content eJournal                       |

关于标题使用标准视图的详细信息，请参见下面的4.3节。

#### 3.1.2.4 项使用标准视图

项级报告的标准视图旨在支持最常见的报告需求。存储库的标准视图（期刊文章请求）提供了对各个期刊文章的用法的了解。多媒体的标准视图（多媒体项目请求）允许在标题级别评估多媒体。

表 3.e：项使用标准视图

| Report_ID | Report_Name              | Details                                                      | Host_Types                                 |
| --------- | ------------------------ | ------------------------------------------------------------ | ------------------------------------------ |
| IR_A1     | Journal Article Requests | 文章级别的期刊文章请求报告。这个报告仅限于有文章的**Data_Type**，期刊的**Parent_Data_Type**和**Metric_Types**的**Total_Item_Requests**和**Unique_Item_Requests**的内容。仅在以下情况下必须提供此标准视图：（a）在IR中清楚所有文章是否为期刊文章，并且（b）所有期刊文章都知道父项。 | Repository Scholarly_Collaboration_Network |
| IR_M1     | Multimedia Item Requests | 在项级别报告多媒体请求。                                     | Multimedia                                 |

有关项目使用情况报告的详细信息，请参见下面的第4.4节。

## 3.2 COUNTER报告的格式

R5报告能够以表格形式或通过COUNTER_SUSHI API以机器可读数据（JSON）的形式传送。表格形式必须是Excel或制表符分隔值（TSV）文件。JSON和TSV格式的报告必须使用**UTF-8**进行编码。JSON格式必须符合COUNTER_SUSHI API规范（请参阅第8节）。

所有的COUNTER报告都具有相同的布局和结构。图3.b提供了“期刊请求（不包括OA_Gold）”标准视图的示例。图3.c显示了表格报告的布局，这将是本文档中讨论的重点。请注意，COUNTER_SUSHI API规范包含名称相同或相似的相同元素。因此，理解表格报告将转化为对通过COUNTER_SUSHI API检索的报告中需要的内容的理解。

图 3.b 期刊请求（不包括OA_Gold）标准视图样例

![](img\TR_J1.png)

图 3.c COUNTER表格报表的布局

![](img\image3.png)

所有COUNTER报告都有标题。在表格报告中，标题与正文之间用空白行分隔（以方便在Excel中进行排序和过滤）。在此之下是带有列标题的报告正文。正文的内容因报告而异。图3.c标识了您可以在报告中找到的各种信息以及此信息的相对位置。所有这些将在下面更详细地讨论。

### 3.2.1 报告标题

表格COUNTER报表的前12行包含标题，而第13行始终为空白。标题信息以一系列名称/值对的形式显示，名称显示在A列中，相应的值显示在B列中。所有表格COUNTER报告在A列中具有相同的名称。B列条目因报告而异。

图3.d：通用报告标题信息

![](img\FIG-3D.png)

图3.d显示了常见标题的布局。下表更详细地讨论了列A中的12个元素和列B中的值。请注意，元素名称（A列）务必与此处显示的一样展示在COUNTER报告中。大写，拼写和标点必须完全匹配。

表3.f：COUNTER报告标题元素

| 元素名称          | 值的描述                                                     | 示例                                                         |
| ----------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Report_Name       | 报告的名称                                                   | Journal Requests (Excluding OA_Gold)                         |
| Report_ID         | 报告的唯一标识符                                             | TR_J1                                                        |
| Release           | 此报告遵循的COUNTER版本。                                    | 5                                                            |
| Institution_Name  | 对于基于订阅的服务，是使用所属的机构的名称。对于OA出版商和存储库，无法确定各个机构的使用情况，应将使用情况归于“（全世界）The world”。 | Mt. Laurel University                                        |
| Institution_ID    | 一系列标识符，以*{namespace}*：*{value}*的格式表示机构。多个标识符用分号（“;”）分隔。允许的标识符命名空间是ISIL，ISNI，OCLC，对于由内容提供商分配的本地标识符，则为内容提供商的平台ID。 | ISNI:0000000419369078; pubsiteA:PrncU                        |
| Metric_Types      | 以分号分隔的指标类型列表。请注意，即使请求了Metric_Type，但如果没有报告项使用该类型，则它也可能不包含在报告正文中。 | Unique_Item_Investigations; Unique_Item_Requests             |
| Report_Filters    | 应用于使用报告的一系列过滤器，但**Metric_Type**，**Begin_Date**和**End_Date**除外（它们在表格报告中的单独行中显示，以方便阅读）。通常，过滤器会影响报告的使用量。过滤器以*{filter name}*=*{filter value}*格式出现，多个过滤器以分号(";")分隔，单个过滤器的多个值以竖线分隔符("\|")分隔。 | Access_Type=Controlled; Access_Method=Regular                |
| Report_Attributes | 应用于报告的一系列报告属性。通常，报告属性会影响使用情况的显示方式，但不会改变总数。属性以*{attribute name}*=*{attribute value}*格式出现，多个属性以分号(";")分隔，单个属性的多个值以竖线分隔符("\|")分隔。 | Attributes_To_Show=Access_Type                               |
| Exceptions        | 指明所请求的使用情况与报告中呈现的使用情况之间的一些差异。异常值的格式为*{Exception Number}*: *{Exception Description}* ，多个异常值之间用分号-空格（“; ”）分隔。异常编号和异常描述必须与[附录F的](https://www.projectcounter.org/appendix-f-handling-errors-exceptions/)表F.1中提供的值匹配。数据是可选的。<br/>请注意，对于表格报告，只有少数异常会被应用。 | 3031: Usage Not Ready for Requested Dates (request was for 2016-01-01 to 2016-12-31; however, usage is only available to 2016-08-31) |
| Reporting_Period  | 报告使用的日期范围, 格式为: “Begin_Date=*yyyy-mm-dd*; End_Date=*yyyy-mm-dd*”. | Begin_Date=2016-01-01; End_Date=2016-08-30                   |
| Created           | 使用的日期和时间，格式为RFC3339日期时间格式（*yyyy-mm-ddThh：mm：ssZ*）。 | 2016-10-11T14:37:15Z                                         |
| Created_By        | 创建COUNTER报告的组织或系统的名称。                          | EBSCO Information Services 360 COUNTER                       |
| (blank row)       | 第13行必须为空白。                                           |                                                              |

### 3.2.2 报告正文