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
| Institution_ID    | 一系列标识符，以*{namespace}*：*{value}*的格式表示机构。多个标识符用分号-空格(“; ”)分隔。允许的标识符命名空间是ISIL，ISNI，OCLC，对于由内容提供商分配的本地标识符，则为内容提供商的平台ID。 | ISNI:0000000419369078; pubsiteA:PrncU                        |
| Metric_Types      | 以分号分隔的指标类型列表。请注意，即使请求了Metric_Type，但如果没有报告项使用该类型，则它也可能不包含在报告正文中。 | Unique_Item_Investigations; Unique_Item_Requests             |
| Report_Filters    | 应用于使用报告的一系列过滤器，但**Metric_Type**，**Begin_Date**和**End_Date**除外（它们在表格报告中的单独行中显示，以方便阅读）。通常，过滤器会影响报告的使用量。过滤器以*{filter name}*=*{filter value}*格式出现，多个过滤器以分号-空格(“; ”)分隔，单个过滤器的多个值以竖线分隔符("\|")分隔。 | Access_Type=Controlled; Access_Method=Regular                |
| Report_Attributes | 应用于报告的一系列报告属性。通常，报告属性会影响使用情况的显示方式，但不会改变总数。属性以*{attribute name}*=*{attribute value}*格式出现，多个属性以分号-空格(“; ”)分隔，单个属性的多个值以竖线分隔符("\|")分隔。 | Attributes_To_Show=Access_Type                               |
| Exceptions        | 指明所请求的使用情况与报告中呈现的使用情况之间的一些差异。异常值的格式为*{Exception Number}*: *{Exception Description}* ，多个异常值之间用分号-空格（“; ”）分隔。异常编号和异常描述必须与[附录F的](https://www.projectcounter.org/appendix-f-handling-errors-exceptions/)表F.1中提供的值匹配。数据是可选的。<br/>请注意，对于表格报告，只有少数异常会被应用。 | 3031: Usage Not Ready for Requested Dates (request was for 2016-01-01 to 2016-12-31; however, usage is only available to 2016-08-31) |
| Reporting_Period  | 报告使用的日期范围, 格式为: “Begin_Date=*yyyy-mm-dd*; End_Date=*yyyy-mm-dd*”. | Begin_Date=2016-01-01; End_Date=2016-08-30                   |
| Created           | 使用的日期和时间，格式为RFC3339日期时间格式（*yyyy-mm-ddThh：mm：ssZ*）。 | 2016-10-11T14:37:15Z                                         |
| Created_By        | 创建COUNTER报告的组织或系统的名称。                          | EBSCO Information Services 360 COUNTER                       |
| (blank row)       | 第13行必须为空白。                                           |                                                              |

### 3.2.2 报告正文

图3.b和3.c显示了包含大量数据元素的COUNTER报告的正文。并非所有报告都将包含所有元素。格式化报告时，请保持以下元素的顺序，但仅包括与该报告相关的那些元素。以下讨论将提供有关元素可以包含在哪些报告中的指南。有关元素到报告的广泛映射，请参见第4节。

#### 报告项说明

每个COUNTER报告都会有描述其报告项的列。

表3.g：描述报告项的元素

| 元素名称     | 描述                                                         | 报告                                                         | 示例                                                      |
| ------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | --------------------------------------------------------- |
| Database     | 正在报告其使用情况的数据库的名称。仅适用于数据库报告。       | DR<br/>DR_D1, DR_D2                                          | MEDLINE                                                   |
| Title        | 报告其使用情况的书籍或期刊的名称。仅适用于标题报告。         | TR<br/>TR_B1, TR_B2, TR_B3, TR_J1, TR_J2, TR_J3, TR_J4       | Journal of Economics Gone with the Wind                   |
| Item         | 报告其使用情况的文章，书籍章节，多媒体作品或存储库项目的名称。仅适用于项目报告。 | IR<br/>IR_A1, IR_M1                                          | CRISPR gene-editing tested in a person for the first time |
| Publisher    | 内容项的发行商的名称。请注意，当内容项是数据库时，发布者将是创建该数据库的组织。 | DR, TR, IR <br/>DR_D1, DR_D2, TR_B1, TR_B2, TR_B3, TR_J1, TR_J2, TR_J3, TR_J4, IR_A1, IR_M1 | Taylor & Francis APA                                      |
| Publisher_ID | 发行商的唯一标识符，格式为*{namespace}*:*{value}*。当发行商有多个标识符时，将所有标识符以分号-空格("; ")分隔，但是每种类型仅限一个。允许的标识符名称空间是ISNI，对于内容提供商分配的本地标识符，是内容提供商的平台ID。 | DR, TR, IR                              DR_D1, DR_D2, TR_B1, TR_B2, TR_B3, TR_J1, TR_J2, TR_J3, TR_J4, IR_A1, IR_M1 | ISNI:1234123412341234 ebscohost:PubX                      |

#### 平台

报告中的下一列标识活动发生的平台。

表3.h：标识平台的元素

| 元素名称 | 描述                                                         | 报告                                                         | 示例                             |
| -------- | ------------------------------------------------------------ | ------------------------------------------------------------ | -------------------------------- |
| Platform | 标识活动发生的平台/内容宿主。请注意，如果个别标题或内容组有自己的品牌用户体验，但驻留在一个公共宿主上，则必须使用底层公共宿主的标识作为平台。 | All reports: PR, DR, TR, IR<br/>PR_P1, DR_D1, DR_D2, TR_B1, TR_B2, TR_B3, TR_J1, TR_J2, TR_J3, TR_J4, IR_A1, IR_M1 | EBSCOhost ProQuest ScienceDirect |

#### 报告项标识符

平台右侧的列进一步标识了要报告的项目。

表3.i：报告项标识符的元素

| 元素名称         | 描述                                                         | 报告                                                         | 示例                                   |
| ---------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | -------------------------------------- |
| Authors          | 正在被报告的作品的作者，格式为{author name}* (*{author identifier}*) , author identifier 的格式为 *{namespace}*:*{value}*. 允许的标识符名称空间是ISNI和ORCID。 最多应包括三位作者，且多位作者之间用分号-空格（“; ”）隔开。<br/>请注意，此元素仅在表格报表中使用，在JSON报表中，作者使用Type Author表示为Item_Contributors | IR<br/>IR_A1                                                 | John Smith (ORCID:0000-0001-2345-6789) |
| Publication_Date | 作品的出版日期，格式为*yyyy-mm-dd*。                         | IR <br/>IR_A1                                                | 2018-09-05                             |
| Article_Version  | ALPSP/NISO码指出父作品的版本。可能的值是 Accepted Manuscript, Version of Record, Corrected Version of Record, and Enhanced Version of Record的代码。 | IR<br/>IR_A1                                                 | VoR(Version of Record)                 |
| DOI              | 被报告项的数字对象标识符，格式为*{DOI prefix}*/*{DOI suffix}*. | TR, IR<br/>TR_B1, TR_B2, TR_B3, TR_J1, TR_J2, TR_J3, TR_J4, IR_A1, IR_M1 | 10.1629/uksg.434                       |
| Proprietary_ID   | 内容提供商为要报告的项分配的专有ID 。格式为*{namespace}*:*{value}* ,namespace是分配专有ID的宿主的platform ID。 | DR, TR, IR<br/>DR_D1, DR_D2, TR_B1, TR_B2, TR_B3, TR_J1, TR_J2, TR_J3, TR_J4, IR_A1, IR_M1 | publisherA:jnrlCode123                 |
| ISBN             | 国际标准书号，格式为ISBN-13，带连字符。                      | TR, IR<br/>TR_B1, TR_B2, TR_B3                               | 978-3-16-148410-0                      |
| Print_ISSN       | 分配给连载出版物的印刷实例的国际标准序列号，格式为*nnnn-nnn [nX]*。 | TR, IR<br/>TR_B1, TR_B2, TR_B3, TR_J1, TR_J2, TR_J3, TR_J4, IR_A1 | 0953-1513                              |
| Online_ISSN      | 分配给连载出版物的联机实例的国际标准序列号，格式为*nnnn-nnn [nX]*。 | TR, IR TR_B1, TR_B2, TR_B3, TR_J1, TR_J2, TR_J3, TR_J4, IR_A1 | 2048-7754                              |
| Linking_ISSN     | 国际标准序列号，将分配给连载出版物所有实例的ISSN链接，格式为*nnnn-nnn [nX]*（仅JSON报告）。 | TR, IR<br/>TR_B1, TR_B2, TR_B3, TR_J1, TR_J2, TR_J3, TR_J4, IR_A1 | 0953-1513                              |
| URI              | 通用资源标识符，根据RFC 3986的有效URL或URN。                 | TR, IR<br/>TR_B1, TR_B2, TR_B3, TR_J1, TR_J2, TR_J3, TR_J4, IR_A1, IR_M1 |                                        |

#### 父项说明和标识符

当报告诸如文章和书籍章节之类的内容项的使用情况时，通常需要标识该项的父项，例如其所属的期刊或书籍。下一组分组标识了父级，并由一小部分报告使用。

表3.j：描述父项的元素

| 元素名称                | 描述                                                         | 报告     | 示例                                                         |
| ----------------------- | ------------------------------------------------------------ | -------- | ------------------------------------------------------------ |
| Parent_Title            | 父项的标题。                                                 | IR IR_A1 | The Serials Librarian                                        |
| Parent_Authors          | 父作品的作者。格式参见表3.i中的Authors元素。                 | IR IR_A1 |                                                              |
| Parent_Publication_Date | 父作品的发布日期，格式为*yyyy-mm-dd*。                       | IR       |                                                              |
| Parent_Article_Version  | 指示父作品版本的ALPSP / NISO代码。可能的值是Accepted Manuscript, Version of Record, Corrected Version of Record和Enhanced Version of Record的码值。 | IR IR_A1 | VoR                                                          |
| Parent_Data_Type        | 标识父母的类型。                                             | IR       | Journal                                                      |
| Parent_DOI              | 分配给父项的DOI，格式为*{DOI prefix}*/*{DOI suffix}*。       | IR IR_A1 |                                                              |
| Parent_Proprietary_ID   | 标识父项的专有ID 。格式为*{namespace}*:*{value}* ,namespace是分配专有ID的宿主的platform ID。 | IR IR_A1 | TandF:wser20                                                 |
| Parent_ISBN             | 父项的ISBN，格式为ISBN-13，带连字符。                        | IR       |                                                              |
| Parent_Print_ISSN       | 父项的印刷ISBN，格式为*nnnn-nnn [nX]*。                      | IR IR_A1 | 0361-526X                                                    |
| Parent_Online_ISSN      | 父项的在线ISSN格式为*nnnn-nnn[nX]*。                         | IR IR_A1 | 1541-1095                                                    |
| Parent_URI              | 父项的URI（有效的URL或RFC 3986规定的URN）。                  | IR IR_A1 | https://www.tandfonline.com/action/journalInformation?journalCode=wser20 |

#### 组件项描述和标识符

存储库通常为给定存储库项存储多个组件。这些组件可以采用多个文件或数据集的形式，可以被标识

并在“主报告”中分别报告使用情况。请注意，可能仅对于**Total_Item_Investigations**和**Total_Item_Request**报告组件使用情况。对于其他**Metric_Types**，使用情况不能按组件细分，且对应的单元格必须是空的。

表3.k：描述组件项的元素

| 元素名称                   | 描述                                                         | 报告 | 示例 |
| -------------------------- | ------------------------------------------------------------ | ---- | ---- |
| Component_Title            | 组件项的名称或标题。                                         | IR   |      |
| Component_Authors          | 组件项的作者。格式参见表3.i中的Authors元素。                 | IR   |      |
| Component_Publication_Date | 组件项的发布日期，格式为*yyyy-mm-dd*。                       | IR   |      |
| Component_Data_Type        | 组件项目的数据类型。                                         | IR   |      |
| Component_DOI              | 组件项的DOI，格式为*{DOI prefix}*/*{DOI suffix}*。           | IR   |      |
| Component_Proprietary_ID   | 存储库分配的专有ID，用于唯一标识组件。格式为{namespace}：{value}其中，namespace是分配了专有标识符的存储库的平台ID 。 | IR   |      |
| Component_ISBN             | 组件项目的ISBN，格式为ISBN-13，带连字符。                    | IR   |      |
| Component_Print_ISSN       | 组件项的印刷ISBN，格式为*nnnn-nnn [nX]*。                    | IR   |      |
| Component_Online_ISSN      | 组件项的在线ISSN，格式为*nnnn-nnn[nX]*                       | IR   |      |
| Component_URI              | 组件项的URI（有效的URL或RFC 3986规定的URN）。                | IR   |      |

#### 项和报告属性

表3.l：项和报告属性的元素

| 元素名称      | 描述                                                         | 报告                                  | 示例               |
| ------------- | ------------------------------------------------------------ | ------------------------------------- | ------------------ |
| Data_Type     | 使用的内容的类型。<br/>更多详细信息参见3.3.2。               | PR, DR, TR, IR                        | Book Journal       |
| Section_Type  | 当按块或节访问内容时，此属性描述内容单元的性质。有关更多详细信息，请参见3.3.3 | TR                                    | Article Chapter    |
| YOP           | 报告的项的发行年份。<br/>有关更多详细信息，请参见3.3.7。     | TR, IR<br/>TR_B1, TR_B2, TR_B3, TR_J4 | 1997               |
| Access_Type   | 有关更多详细信息，请参见3.3.5。                              | TR, IR<br/> TR_B3, TR_J3, IR_A1       | Controlled OA_Gold |
| Access_Method | 有关更多详细信息，请参见3.3.6。                              | PR, DR, TR, IR                        | Regular TDM        |

#### 指标类型

表3.m：Metric_Type的报告元素

| 元素名称    | 描述                                                     | 报告                                                         | 示例                      |
| ----------- | -------------------------------------------------------- | ------------------------------------------------------------ | ------------------------- |
| Metric_Type | 被计数的活动的类型。<br/>有关更多详细信息，请参见3.3.4。 | All reports: PR, DR, TR, IR<br/>PR_P1, DR_D1, DR_D2, TR_B1, TR_B2, TR_B3, TR_J1, TR_J2, TR_J3, TR_J4, IR_A1, IR_M1 | Total_Item_Investigations |

#### 使用数据

表3.n：使用数据元素

| 元素                   | 描述                                                         | 报告                                                         | 示例     |
| ---------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | -------- |
| Reporting_Period_Total | 该行涵盖所有月份的总使用量。注意，此元素不出现在JSON报告中，作为代替，JSON格式提供一个粒度报告属性。详细信息，请参见第3.3.8节。 | All reports: PR, DR, TR, IR<br/>PR_P1, DR_D1, DR_D2, TR_B1, TR_B2, TR_B3, TR_J1, TR_J2, TR_J3, TR_J4, IR_A1, IR_M1 | 123456   |
| *Mmm-yyyy*             | 报告涵盖的每月使用情况的一系列列。格式为*Mmm-yyyy*。 注意：在JSON格式中，这由每个月的Begin_Date和End_Date日期元素表示。 | All reports: PR, DR, TR, IR<br/>PR_P1, DR_D1, DR_D2, TR_B1, TR_B2, TR_B3, TR_J1, TR_J2, TR_J3, TR_J4, IR_A1, IR_M1 | May-2016 |

## 3.3 COUNTER报告常见属性和元素

COUNTER行为准则的早期版本侧重于与期刊相关的使用情况统计。之后书籍，文章多媒体集也被加入其中。R5进一步将COUNTER的范围扩展到研究数据和社交媒体领域。为了使用单一的、一致的、连贯的行为准则管理逐步扩大的领域，添加了一些新的元素和属性。

### 3.3.1 载体类型

使用报告支持许多不同的内容载体类型，如eBook, A&I_Database, eJournal等等。使用情况报告的需求因Host_Type而异。为了适应这种差异，R5定义了一组Host_Type类别。尽管Host_Type未出现在COUNTER报告中，但实践准则在本文档中始终使用Host_Type，以帮助内容提供者识别哪些报告，元素，度量标准类型和属性与它们相关。Host_Types是：

表3.o：Host_Type值列表

| Host_Type                       | 描述                                                         | 示例                                                         |
| ------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| A&I_Database                    | 提供对包含支持搜索的学术文章的摘要和索引信息的数据库的访问。 | APA<br/>EBSCOhost <br/>ProQuest                              |
| Aggregated_Full_Content         | 提供对聚合预设数据库的全文和其他在数据库许可的上下文环境中访问的内容。 | EBSCOhost ProQuest                                           |
| Data_Repository                 | 包括学科资料库，机构等。                                     | UK Data Service – ReShare<br/>Figshare<br/>DSpace<br/>Eprints |
| Discovery_Service               | 通过提供对文章、书籍和其他元数据的主要索引的访问，帮助用户发现学术内容。 | EBSCOhost (EDS) ProQuest (Primo/Summon)                      |
| eBook                           | 提供对电子书内容（内容是可单独获取的电子书或打包的电子书）的访问 | EB<br/>EBSCOhost<br/>ScienceDirect                           |
| eBook_Collection                | 提供对电子书集的访问（内容以固定集合的形式售卖，就像数据库一样）。 | EBSCOhost                                                    |
| eJournal                        | 提供对在线连载物（期刊、会议、报纸等等）的访问（内容是可单独获取的标题或包）。 | ScienceDirect                                                |
| Full_Content_Database           | 提供对数据库的访问，这些数据库是不属于系列或专题的内容项的集合。(i.e. 非聚合的). | Cochrane                                                     |
| Multimedia                      | 提供对音频、视频和其他多媒体内容的访问。                     | Alexander Street Press                                       |
| Multimedia_Collection           | 提供对能像数据库一样售卖和访问的多媒体材料的访问。           |                                                              |
| Repository                      | 提供查阅机构研究成果的途径。包括学科资料库、机构、部门等。   | Cranfield CERES                                              |
| Scholarly_Collaboration_Network | 一种研究人员用来分享他们工作的信息的服务。                   | Mendeley Reddit/science                                      |

请注意，给定的内容载体可能具有不同的host_type类型，并希望提供适用于所有类型的报告、度量类型、元素和属性。比如， EBSCOhost可以被分类为 A&I_Database, Aggregated_Full_Content, Discovery_Service, eBook和eBook_Collection。

### 3.3.2 数据类型

R5以多种形式报告学术信息。这些形式被称作数据了类型**Data_Type**，在下表中列出，同时列出了载体类型**Host_Type**以及它们适用的报告。所有的Data_type都应用于平台报告，因为它们汇总了平台上的使用情况。注意，表格仅列出了为了合规需要提供一或多个报告的Host_Types，但是内容提供者可能提供额外的报告。例如，Host_Type eJournal也可以提供IR和IR_A1，然后在这些报告中使用Data_Type Article。

表 3.p: Date_Type的值

| Data_Type               | 描述                                                         | Host_Types                                                   | 报告                                                    |
| ----------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------- |
| Article                 | 一篇文章，通常发表在期刊或参考书上。当文章是项时Data_Type Article只适用于项报告，在标题报告中用Section_Type表示。 | Repository Scholarly_Collaboration_Network                   | PR, IR<br/>PR_P1, IR_A1                                 |
| Book                    | 论文著作                                                     | A&I_Database Aggregated_Full_Content Discovery_Service eBook eBook_Collection Repository Scholarly_Collaboration_Network | PR, DR, TR, IR<br/>PR_P1, DR_D1, TR_B1, TR_B2, TR_B3    |
| Book_Segment            | 书的一部分(如章节、章节等)。注意，Data_Type Book_Segment仅适用于当书的一部分是项时的项目报告，在Title报告中，这由Section_Type表示。 | Repository Scholarly_Collaboration_Network                   | PR, IR<br/>PR_P1                                        |
| Database                | 在数据库的上下文中搜索和访问内容的固定数据库。载体上的给定项可能在多个数据库中，但事务必须归属于特定的数据库。 注意，Data_Type Database只适用于数据库级别的搜索和拒绝访问，以及Full_Content_Databases的访问和请求。 | A&I_Database Aggregated_Full_Content Discovery_Service eBook_Collection Full_Content_Database Multimedia_Collection | PR, DR<br/>PR_P1, DR_D1, DR_D2                          |
| Dataset                 | 一个数据集                                                   | Data_Repository Repository                                   | PR, IR<br/>PR_P1                                        |
| Journal                 | 作为杂志或杂志连续出版的文本内容。                           | A&I_Database Aggregated_Full_Content Discovery_Service eJournal Repository | PR, DR, TR, IR PR_P1, DR_D1, TR_J1, TR_J2, TR_J3, TR_J4 |
| Multimedia              | 多媒体内容，如音频，图片，音频流，视频流和视频。             | Multimedia Multimedia_Collection                             | PR, DR, IR PR_P1, DR_D1, IR_M1                          |
| Newspaper_or_Newsletter | 在报纸或通讯上连续刊登的文本内容。                           | A&I_Database Aggregated_Full_Content Discovery_Service Repository | PR, DR, TR, IR PR_P1, DR_D1                             |
| Other                   | 无法被分类的内容                                             | A&I_Database Aggregated_Full_Content Discovery_Service Repository | PR, DR, TR, IR PR_P1, DR_D1                             |
| Platform                | 一个可以反映多个Data_Types使用情况的内容平台。注意，Data_Type平台只适用于Searches_Platform。 | All Host_Types: A&I_Database Aggregated_Full_Content Data_Repository Discovery_Service eBook eBook_Collection eJournal Full_Content_Database Multimedia Multimedia_Collection Repository Scholarly_Collaboration_Network | PR<br/>PR_P1                                            |
| Report                  | 一个报告。                                                   | A&I_Database Aggregated_Full_Content Discovery_Service Repository | PR, DR, TR, IR PR_P1, DR_D1                             |
| Repository_Item         | 存储库中存储的项的一种通用分类。                             | Repository                                                   | PR, IR PR_P1                                            |
| Thesis_or_Dissertation  | 论文或学术演讲                                               | A&I_Database Aggregated_Full_Content Discovery_Service Repository | PR, DR, TR, IR PR_P1, DR_D1                             |

Full_Content_Databases也可以在主标题报告中使用Data_Type Database。所有其他Host_Types必须报告访问和请求，或者是标题级别的Data_Types(如journa, book, from Host_Type A&I_Database, Aggregated_Full_Content, Discovery_Service, eBook, eBook_Collection 和 eJournal)，或项级别的Data_Types(如 article, Multimedia for a video from Host_Type Data_Repository, Multimedia, Multimedia_Collection, Repository和Scholarly_Collaboration_Network)。必须在需要合规的所有报告中使用这些Data_Types，以确保报告的一致性。

### 3.3.3 部分类型

一些学术内容是在部分访问。例如，用户可以一次访问一个章节或部分。引入Section_Type以根据访问的部分的类型提供事务的分类。例如，图书馆员可以使用“标题主报告”查看按Title和 Section_Type细分的使用情况。下表列出了COUNTER定义的Section_Types和Host_Types以及它们适用的报告。

表3.q：Section_Type值列表

| Section_Type | 描述                                     | Host_Types                                              | 报告 |
| ------------ | ---------------------------------------- | ------------------------------------------------------- | ---- |
| Article      | 文章，例如期刊，百科全书或参考书         | Aggregated_Full_Content eJournal                        | TR   |
| Book         | 一本完整的书，可以作为一个文件进行访问。 | Aggregated_Full_Content eBook eBook_Collection          | TR   |
| Chapter      | 一本书的一章。                           | Aggregated_Full_Content eBook eBook_Collection          | TR   |
| Other        | 列表中未另示的部分中提供的内容。         | Aggregated_Full_Content                                 | TR   |
| Section      | 一组章节或文章。                         | Aggregated_Full_Content eBook eBook_Collection eJournal | TR   |

### 3.3.4 指标类型

Metric_Types代表所计数的活动的性质，可以分为搜索（Searches），访问（investigations），请求（Requests）和拒绝访问（Access Denied）。表3.r，3.s和3.t列出了Metric_Types和Host_Types以及它们适用的报告。

#### 搜索（Searches）

表3.r：搜索的Metric_Type类型列表

| Metric_Type                     | 描述                                                         | Host_Types                                                   | 报告     |
| ------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | -------- |
| 常规搜索<br/>Searches_Regular   | 针对用户选择在UI界面上返回结果的搜索次数。由用户负责选择搜索的数据库或者数据库集。此度量标准仅适用于在数据库级别跟踪的使用情况，而不显示平台级别的。 | A&I_Database Aggregated_Full_Content Discovery_Service eBook_Collection Full_Content_Database Multimedia_Collection | DR DR_D1 |
| 自动搜索<br/>Searches_Automated | 在主机站点或发现服务上进行的搜索，结果在主机UI中返回，无需用户选择数据库就可以搜索多个数据库。此度量标准仅适用于在数据库级别跟踪的使用情况，在平台级别不显示。 | A&I_Database Aggregated_Full_Content Discovery_Service eBook_Collection Full_Content_Database Multimedia_Collection | DR DR_D1 |
| 联合搜索<br/>Searches_Federated | 由联合搜索引擎进行的搜索，其中搜索活动是通过客户端-服务器技术远程进行的。此度量标准仅适用于在数据库级别跟踪的使用情况，而在平台级别不显示。 | A&I_Database Aggregated_Full_Content Discovery_Service eBook_Collection Full_Content_Database Multimedia_Collection | DR DR_D1 |
| 平台搜索<br/>Searches_Platform  | 由用户执行并在平台级别捕获的搜索。不论搜索涉及的数据库数量如何，每个用户启动的搜索都只能计数一次。该指标仅适用于平台报告。 | All Host_Types:<br/>A&I_Database Aggregated_Full_Content Data_Repository* Discovery_Service eBook eBook_Collection eJournal Full_Content_Database Multimedia Multimedia_Collection Repository* Scholarly_Collaboration_Network | PR PR_P1 |

*存储库应该提供这些Metric_Type。

**项和标题的访问和请求**

这组Metric_Types代表检索了内容项（请求）或访问了有关内容项的信息（例如摘要）的活动。可以归属于内容项的任何用户活动都将被视为访问，包括下载或查看该项。请求仅限于与检索或查看内容项本身有关的用户活动。下图提供了访问和请求之间关系的图形表示。

图3e：访问与请求之间的关系

![](img\Picture1-2.png)

**总计，唯一项和唯一标题**

R5还引入了唯一项和唯一标题的概念。以Total开头的Metric_Types与R4的度量非常相似，即，如果在用户会话中多次访问给定的文章，书籍或书籍章节，则该指标将增加访问内容项的次数（过滤了双击行为导致的重复计数）。

R5中引入了Unique_Item度量标准，以帮助消除不同风格的用户界面可能对使用计数产生的影响。使用R5，如果在给定的用户会话中多次访问单个文章，则相应的Unique_Item指标只能增加1，以简单地指示在会话中访问了该内容项。

R5中引入了Unique_Title指标，以帮助规范电子书指标。由于可以将整本电子书下载为单个PDF或作为单独的章节，因此R4的BR1（书籍下载）和BR2（章节下载）的计数是不可比的。使用R5，无论在给定的用户会话中访问了多少（或多少次）章节，该书的Unique_Title指标都只会增加1 。无论平台的性质以及电子书内容的交付方式如何，Unique_Title指标均提供可比较的电子书指标。

Unique_Title指标不得用于Book以外的Data_Type，因为它们对它们没有意义。如果一本书同时包含OA_Gold和Controlled部分或具有不同YOP的部分，则必须按Access_Type和YOP细分使用情况，以使报告之间的总计数，包括和不包括这些列/元素保持一致。

表3.s：请求和访问的Metric_Type列表

| Metric_Type                 | 描述                                                         | Host_Types                                                   | 报告                                                         |
| --------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Total_Item_Investigations   | 内容项或内容项相关的信息被访问的次数。双击过滤器将应用于这些事务。内容项可以是文章，书籍的章节或者多媒体文件。 | All Host_Types:<br/>A&I_Database Aggregated_Full_Content Data_Repository* Discovery_Service<br/>eBook<br/>eBook_Collection<br/>eJournal<br/>Full_Content_Database Multimedia Multimedia_Collection Repository* Scholarly_Collaboration_Network | PR, DR, TR, IR<br/>DR_D1, TR_B3, TR_J3                       |
| Unique_Item_Investigations  | 用户会话中访问的唯一内容项的数量。内容项可以是文章，书籍的章节或者多媒体文件。 | All Host_Types:<br/>A&I_Database Aggregated_Full_Content Data_Repository* Discovery_Service<br/>eBook<br/>eBook_Collection<br/>eJournal Full_Content_Database Multimedia Multimedia_Collection Repository* Scholarly_Collaboration_Network | PR, DR, TR, IR<br/>TR_B3, TR_J3                              |
| Unique_Title_Investigations | 用户会话中访问的唯一标题的数量。标题可以是书。               | A&I_Database Aggregated_Full_Content Discovery_Service eBook eBook_Collection | PR, DR, TR TR_B3                                             |
| Total_Item_Requests         | 请求内容项的总次数（即，下载或查看全文或内容）。双击过滤器将应用于这些事务。内容项可以是文章，书籍的章节或者多媒体文件。 | Aggregated_Full_Content Data_Repository<br/>eBook<br/>eBook_Collection<br/>eJournal Full_Content_Database Multimedia Multimedia_Collection Repository Scholarly_Collaboration_Network | PR, DR, TR, IR PR_P1, DR_D1, TR_B1, TR_B3, TR_J1, TR_J3, TR_J4, IR_A1, IR_M1 |
| Unique_Item_Requests        | 用户会话中请求的唯一内容项的数量。内容项可以是文章，书籍的章节或者多媒体文件。 | Aggregated_Full_Content Data_Repository<br/>eBook<br/>eBook_Collection<br/>eJournal<br/>Full_Content_Database Multimedia Multimedia_Collection Repository Scholarly_Collaboration_Network | PR, DR, TR, IR PR_P1, TR_B3, TR_J1, TR_J3, TR_J4, IR_A1      |
| Unique_Title_Requests       | 用户会话中请求的唯一标题的数量。标题可以是书。               | Aggregated_Full_Content eBook eBook_Collection               | PR, DR, TR PR_P1, TR_B1, TR_B3                               |

*存储库应该提供这些Metric_Type。

**拒绝访问**

表3.t：拒绝访问的Metric_Type类型列表

| Metric_Type    | 描述                                                         | Host_Types                                                   | 报告                               |
| -------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ---------------------------------- |
| No_License     | 由于用户所在的机构没有内容许可，因此拒绝访问的次数。双击过滤将应用于此Metric_Type。<br/>请注意，如果用户自动重定向到摘要，则该操作将被计为No_License以及Item_Investigation。 | A&I_Database Aggregated_Full_Content Discovery_Service<br/>eBook<br/>eBook_Collection<br/>eJournal<br/>Full_Content_Database Multimedia Multimedia_Collection Scholarly_Collaboration_Network | DR, TR, IR<br/>DR_D2, TR_B2, TR_J2 |
| Limit_Exceeded | 由于超出了用户机构许可的同时使用用户限制，因此拒绝访问的次数。双击过滤将应用于此Metric_Type。 | A&I_Database Aggregated_Full_Content Discovery_Service eBook eBook_Collection eJournal Full_Content_Database Multimedia Multimedia_Collection Scholarly_Collaboration_Network | DR, TR, IR DR_D2, TR_B2, TR_J2     |