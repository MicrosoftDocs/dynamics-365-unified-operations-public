---
# required metadata

title: Data and metadata stored in Azure Data Lake
description: This article explains how data and metadata are stored in Microsoft Azure Data Lake.
author: MilindaV2
ms.date: 09/08/2022
ms.topic: overview
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: milindav
ms.search.validFrom: 2021-11-30

---

# Data and metadata stored in Azure Data Lake

[!include [banner](../includes/banner.md)]

## How data is stored in the data lake

Data in Microsoft Azure Data Lake is stored as comma-separated values (CSV) files in a folder structure that is maintained by the system. This folder structure is based on the organization of data in finance and operations apps. For example, you will find folders that have names such as **Finance**, **Supply Chain**, and **Commerce**. Inside these folders, you will find sub-folders that have names such as **Accounts Receivable** and **Accounts Payable**. Further down the hierarchy, you will find folders that contain the actual data for each table. Inside these table-level folders, you will find one or more CSV files, and also metadata files that describe the format of the data.

When data in finance and operations apps is updated, corresponding data rows are updated in CSV files inside the table-level folders. When a new row is added to a table in finance and operations apps, or an existing row is deleted, new rows are added or existing rows are deleted in corresponding CSV files.

The number of CSV files in the data lake depends on the size of data rows. The system tries to keep the size of each CSV file at about 200 megabytes (MB) to optimize read and write operations. If the size of a CSV file exceeds 200 MB, the system might split the data into multiple files.

Data files don't contain field headers or any other information. You will have to read the metadata to understand the structure of the files.

## How metadata is stored in the data lake

Metadata describes the name, data type, size, and nature of data. In addition to the data files in the data lake, you will notice metadata files at a folder level that corresponds to the data files. Metadata in a data lake is written in a machine-readable format that is described by the [Common Data Model (CDM) standard](/common-data-model/sdk/overview). When you install the Export to Data Lake feature and select data to add to the data lake, the system writes metadata files in addition to the data.

Both Microsoft and third parties provide tools that understand the CDM metadata format. These tools make it easy to work with data in the data lake. Azure Synapse Analytics serverless SQL pools let you use the Transact-SQL (T-SQL) language to consume data in the data lake. T-SQL is widely supported by many tools. You can define a Synapse workspace over the data in the data lake, and then use T-SQL, Spark, or Synapse Pipelines as though you're consuming data from a database. To create a Synapse workspace over your data in the data lake, you can use [FastTrack Solutions for Dynamics 365 - CDMUtilSolution](https://github.com/microsoft/Dynamics-365-FastTrack-Implementation-Assets/tree/master/Analytics/CDMUtilSolution). This solution creates external table definitions in Azure Synapse Analytics serverless SQL pools by using metadata in the data lake.

If you select the **Enhanced metadata** option when you install Export to Data Lake, the system adds even more metadata.


## Enhanced metadata

If you're familiar with Dynamics 365 applications such as Dynamics 365 Finance and Dynamics 365 Supply Chain Management, you might be familiar with the rich metadata structures that are present in them. In addition to basic types, enhanced metadata includes the following types:

- **Extended data types (EDTs)**, which offer richer data types that describe behavior and business rules that are applicable to "business data types," such as bank accounts, ledger accounts, and telephone numbers.
- **Descriptive names**, together with **translated labels** that are available in many languages.
- Higher-level data abstractions, such as **entity definitions**.

When you enable the **Enhanced metadata** option, the system writes additional metadata that is derived from Dynamics 365 into the data lake. Client tools that can understand and work with the additional metadata properties can then provide a better experience to users.

### Prerequisites for enabling the Enhanced metadata feature

1. The finance and operations app version must be later than the following versions:

    - Version 10.0.22 with the latest updates (version 10.0.995.146 or later)
    - Version 10.0.23 with the latest updates (version 10.0.1037.133 or later)
    - Version 10.0.24 with the latest updates (10.0.1084.89 or later)
    - Version 10.0.25 and later

2. When your administrator installs the Export to Data Lake add-in, they must select the **Enable enhanced metadata** option. You can't enable the enhanced metadata feature unless this option is selected during the installation stage.
3. In the finance and operations app, you must select **Republish metadata** on the **Manage** tab on the Action Pane of the **Export to Data Lake** page the first time that you open it. You have to complete this step only once. The system will then continue to republish metadata as changes happen.

   > [!NOTE]
   > In version 10.0.23 and later, the system automatically runs the **Republish metadata** command the first time that you open the **Export to Data Lake** page.

### Changes introduced by the Enhanced metadata feature

If you're currently using the Export to Data Lake feature, you will notice the folder structure and metadata in the data lake. When you enable the Enhanced metadata feature by reinstalling the add-in, you might notice several changes. These changes are described in more detail later in this article.

- Data that was previously stored in the Custom folder might be moved to a folder structure that consists of subject areas. These subject areas are based on the metadata that is defined in Dynamics 365. If you're using the metadata files to navigate and find data, you will be able to go to the correct folder structure. However, if you hard-coded the folder structure in consuming tools, you might have to update those tools.
- In some cases, the folder structure under the Custom folder will remain, together with metadata files. No data files will be present in this folder.

## Folder structure in the data lake

finance and operations apps have over 10,000 tables and over 2,500 entities. (If extensions and customizations are included, the numbers are much larger.) To help secure data in the data lake in a granular way, tables and entities are organized into modules that represent application areas. In the data lake, this organization is reflected in a folder structure that mimics the organization of application areas in Dynamics 365.

### Table folder structure

The table folder structure is three levels deep:

1. **Application area** – This level is a grouping of modules in finance and operations apps. For example, a folder at this level might be named **Finance**.
2. **Module** – This level is derived by using a table-level **Module** metadata property in finance and operations apps. For example, a folder at this level might be named **General Ledger**.
3. **Table type** – This level is derived by using the existing **TableGroup** metadata property. For example, a folder at this level might be named **Main**.

You can [view the application area \> module \> table type hierarchy](/common-data-model/schema/core/operationscommon/tables/overview) for tables that are part of finance and operations apps.

> [!NOTE]
> When the Enhanced metadata feature is enabled, tables that are introduced by system integrators and partners (*custom tables*) will follow the same structure, provided that the same metadata properties are added to tables in finance and operations apps. If the Enhanced metadata feature isn't enabled, all custom tables will be put in the Custom folder.
>
> The table-level **Module** metadata property is backed by an extensible enumeration (enum) that is named **ModuleAxapta**. This enum contains predefined modules that are released by Microsoft. However, you can extend the enum by adding your own module definitions. In this way, you can use your own modules in addition to the predefined modules. The Export to Data Lake feature will put custom tables in appropriate folders, based on the table-level **Module** property.
>
> The mapping of application areas to modules is defined in finance and operations apps and can't currently be modified. If you define a new **Module** property, it probably won't be reflected in the application area–to–module mapping. In this case, the Export to Data Lake feature will put the table in an application area folder that is named **Custom**.
>
> Systems integrators and partners can't modify the **Module** property for tables that are released by Microsoft. Although you can modify the **Module** property for custom tables, we recommend that you avoid frequent modifications. Modification of the **Module** property causes the location of the table in the data lake to change. Therefore, consuming applications that assume a specific location for data files might be affected every time that you modify the **Module** property.
>
> If the **Module** property isn't defined for a custom table, that table will be put in the Custom folder.

### Entity folder structure

There are fewer entities than tables in finance and operations apps. The entity folder structure is only two levels deep:

1. **Application area** – This level is a grouping of modules in finance and operations apps. The grouping is similar to the grouping for tables. For example, a folder at this level might be named **Finance**.
2. **Module** – This level is derived by using an entity-level **Module** metadata property in finance and operations apps. For example, a folder at this level might be named **General Ledger**.

Just as systems integrators and partners can extend the table-level **Module** property by introducing custom tables, they can extend the entity-level **Module** property by introducing custom entities. The entity-level **Module** property is backed by the same **ModuleAxapta** extensible enum that backs the table-level **Module** property.

## Changes to metadata

New software updates can cause metadata in finance and operations apps to change. For example, a developer might add a new field to an existing table or entity. In less frequent cases, a developer might remove an existing field from a table or change the data type of an existing field.

If the structure of a table or entity is changed, and especially if a field is removed from the table or entity, consuming applications might have to be updated. The Export to Data Lake feature is designed to minimize the downstream impact but also reflect metadata changes in the data lake. This section explains how metadata changes are reflected in the data lake.

> [!NOTE]
> Finance and operations apps include governance processes and developer tools that help developers learn about such changes and their impact. However, users who consume data in the date lake by creating and running a Power BI report, for example, might not be aware of changes in finance and operations apps.

When a new field is added to a table, metadata files in the data lake are updated to reflect the change. All the records in the CSV files that include the newly added data will contain the new field. If a CSV file isn't modified, or no new rows are added, the file won't contain the new field. This behavior helps minimize the data writes to the data lake. Most data pipeline tools, and especially those tools that understand the CDM standard, support a feature that can adapt to changes. This feature is known as *schema drift*.

If the change to the data structure is destructive, the system might repopulate the whole table folder (that is, all the CSV files). For example, in a rare but destructive change, a field might be removed from a table in a finance and operations app. In this case, the whole table folder is repopulated, together with the updated metadata. Destructive changes might require changes to downstream reports, especially if the report is expecting a data field that was removed.

## Any questions, feedback?

We are actively working on this and other features. Do you want to stay in touch and ask questions of the product team or your fellow customers or partners? Do you want to provide feedback directly to the product team? If you do, you can join the [Preview Yammer group](https://www.yammer.com/dynamicsaxfeedbackprograms/#/threads/inGroup?type=in_group&feedId=32768909312&view=all). You can then attend weekly online "office hours" meetings and use the Yammer online forums to stay in touch and ask questions.

