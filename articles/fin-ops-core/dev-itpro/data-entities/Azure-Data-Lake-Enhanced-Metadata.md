---
title: Data and metadata stored in Azure Data Lake
description: Learn about how data and metadata are stored in Microsoft Azure Data Lake, including an overview of enhanced metadata.
author: MilindaV2
ms.author: johnmichalak
ms.topic: overview
ms.date: 01/16/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2021-11-30
---

# Data and metadata stored in Azure Data Lake

[!include [banner](../includes/banner.md)]

> [!NOTE]
> Over the past 12 months, the product team worked to fill in gaps and add new features that members of the user community highlighted. [Azure Synapse Link for Dataverse service built into Power Apps](/power-apps/maker/data-platform/azure-synapse-link-select-fno-data), the successor to the **Export to Data Lake** feature in finance and operations apps, is generally available and ready for you. Azure Synapse Link provides one experience for working with data from all Microsoft Dynamics 365 apps.
>
> To benefit from the enhanced performance, flexibility, and improved user experience that Azure Synapse Link offers, use it as soon as possible. Therefore, Microsoft announced the deprecation of the **Export to Data Lake** feature, effective October 15, 2023. If you're already using the **Export to Data Lake** feature, you can continue to use it until November 1, 2024. If you're new to the **Export to Data Lake** feature or are planning to adopt this feature in the coming months, use Azure Synapse Link instead.
>
> The transition might seem daunting, but Microsoft wants to provide a smoother experience and offer guidance. To get started, see the [Azure Synapse Link transition guide](https://aka.ms/TransitionToSynapseLink). The product team is listening closely to the community and is working on multiple features to help make the transition smoother. They announce these other improvements to the transition process as they bring new features online. If you want to stay in touch, join the community at [https://aka.ms/SynapseLinkforDynamics](https://aka.ms/SynapseLinkforDynamics).

## How data is stored in the data lake

Data in Microsoft Azure Data Lake is stored as comma-separated values (CSV) files in a folder structure that the system maintains. This folder structure is based on the organization of data in finance and operations apps. For example, you find folders that have names such as **Finance**, **Supply Chain**, and **Commerce**. Inside these folders, you find subfolders that have names such as **Accounts Receivable** and **Accounts Payable**. Further down the hierarchy, you find folders that contain the actual data for each table. Inside these table-level folders, you find one or more CSV files, and also metadata files that describe the format of the data.

When you update data in finance and operations apps, the system updates corresponding data rows in CSV files inside the table-level folders. When you add a new row to a table in finance and operations apps, or delete an existing row, the system adds new rows or deletes existing rows in corresponding CSV files.

The number of CSV files in the data lake depends on the size of data rows. The system tries to keep the size of each CSV file at about 200 megabytes (MB) to optimize read and write operations. If the size of a CSV file exceeds 200 MB, the system might split the data into multiple files.

Data files don't contain field headers or any other information. You have to read the metadata to understand the structure of the files.

## How metadata is stored in the data lake

Metadata describes the name, data type, size, and nature of data. In addition to the data files in the data lake, you notice metadata files at a folder level that corresponds to the data files. Metadata in a data lake is written in a machine-readable format that is described by the [Common Data Model (CDM) standard](/common-data-model/sdk/overview). When you install the Export to Data Lake feature and select data to add to the data lake, the system writes metadata files in addition to the data.

Both Microsoft and third parties provide tools that understand the CDM metadata format. These tools make it easy to work with data in the data lake. Azure Synapse Analytics serverless SQL pools let you use the Transact-SQL (T-SQL) language to consume data in the data lake. T-SQL is widely supported by many tools. You can define a Synapse workspace over the data in the data lake, and then use T-SQL, Spark, or Synapse Pipelines as though you're consuming data from a database. To create a Synapse workspace over your data in the data lake, you can use [FastTrack Solutions for Dynamics 365 - CDMUtilSolution](https://github.com/microsoft/Dynamics-365-FastTrack-Implementation-Assets/tree/master/Analytics/CDMUtilSolution). This solution creates external table definitions in Azure Synapse Analytics serverless SQL pools by using metadata in the data lake.

If you select the **Enhanced metadata** option when you install Export to Data Lake, the system adds even more metadata.

## Enhanced metadata

If you're familiar with Dynamics 365 applications such as Dynamics 365 Finance and Dynamics 365 Supply Chain Management, you might be familiar with the rich metadata structures that are present in them. In addition to basic types, enhanced metadata includes the following types:

- **Extended data types (EDTs)**, which offer richer data types that describe behavior and business rules that apply to "business data types," such as bank accounts, ledger accounts, and telephone numbers.
- **Descriptive names**, together with **translated labels** that are available in many languages.
- Higher-level data abstractions, such as **entity definitions**.

When you enable the **Enhanced metadata** option, the system writes more metadata that is derived from Dynamics 365 into the data lake. Client tools that can understand and work with the additional metadata properties can then provide a better experience to users.

### Prerequisites for enabling the Enhanced metadata feature

1. The finance and operations app version must be later than the following versions:

    - Version 10.0.22 with the latest updates (version 10.0.995.146 or later)
    - Version 10.0.23 with the latest updates (version 10.0.1037.133 or later)
    - Version 10.0.24 with the latest updates (10.0.1084.89 or later)
    - Version 10.0.25 and later

1. The administrator must select the **Enable enhanced metadata** option when installing the Export to Data Lake add-in. You can't enable the enhanced metadata feature unless this option is selected during the installation stage.
1. In the finance and operations app, you must select **Republish metadata** on the **Manage** tab on the Action Pane of the **Export to Data Lake** page the first time that you open it. You have to complete this step only once. The system then continues to republish metadata as changes happen.

   > [!NOTE]
   > In version 10.0.23 and later, the system automatically runs the **Republish metadata** command the first time that you open the **Export to Data Lake** page.

### Changes introduced by the Enhanced metadata feature

If you're currently using the Export to Data Lake feature, you see the folder structure and metadata in the data lake. When you enable the Enhanced metadata feature by reinstalling the add-in, you might see several changes. These changes are described in more detail later in this article.

- Data that was previously stored in the Custom folder might be moved to a folder structure that consists of subject areas. These subject areas are based on the metadata that is defined in Dynamics 365. If you're using the metadata files to navigate and find data, you can go to the correct folder structure. However, if you hard-coded the folder structure in consuming tools, you might need to update those tools.
- In some cases, the folder structure under the Custom folder remains, together with metadata files. No data files are present in this folder.

## Folder structure in the data lake

Finance and operations apps have more than 10,000 tables and more than 2,500 entities. (If extensions and customizations are included, the numbers are larger.) To help secure data in the data lake in a granular way, developers organize tables and entities into modules that represent application areas. In the data lake, this organization is reflected in a folder structure that mimics the organization of application areas in Dynamics 365.

### Table folder structure

The table folder structure has three levels:

1. **Application area** – This level groups modules in finance and operations apps. For example, a folder at this level might be named **Finance**.
1. **Module** – This level comes from a table-level **Module** metadata property in finance and operations apps. For example, a folder at this level might be named **General Ledger**.
1. **Table type** – This level comes from the existing **TableGroup** metadata property. For example, a folder at this level might be named **Main**.

You can [view the application area \> module \> table type hierarchy](/common-data-model/schema/core/operationscommon/tables/overview) for tables that are part of finance and operations apps.

> [!NOTE]
> When you enable the Enhanced metadata feature, tables that system integrators and partners introduce (*custom tables*) follow the same structure if you add the same metadata properties to tables in finance and operations apps. If you don't enable the Enhanced metadata feature, all custom tables go in the Custom folder.
>
> The table-level **Module** metadata property uses an extensible enumeration (enum) named **ModuleAxapta**. This enum has predefined modules that Microsoft releases. However, you can extend the enum by adding your own module definitions. In this way, you can use your own modules in addition to the predefined modules. The Export to Data Lake feature puts custom tables in appropriate folders, based on the table-level **Module** property.
>
> Finance and operations apps define the mapping of application areas to modules and you can't currently modify it. If you define a new **Module** property, it probably won't appear in the application area–to–module mapping. The Export to Data Lake feature puts the table in an application area folder named **Custom**.
>
> Systems integrators and partners can't modify the **Module** property for tables that Microsoft releases. Although you can modify the **Module** property for custom tables, avoid frequent modifications. Changing the **Module** property changes the location of the table in the data lake. Therefore, consuming applications that assume a specific location for data files might be affected every time that you modify the **Module** property.
>
> If the **Module** property isn't defined for a custom table, the table goes in the Custom folder.

### Entity folder structure

Finance and operations apps have fewer entities than tables. The entity folder structure has only two levels:

1. **Application area** – This level groups modules in finance and operations apps. The grouping is similar to the grouping for tables. For example, a folder at this level might be named **Finance**.
1. **Module** – This level comes from an entity-level **Module** metadata property in finance and operations apps. For example, a folder at this level might be named **General Ledger**.

Just as systems integrators and partners can extend the table-level **Module** property by introducing custom tables, they can extend the entity-level **Module** property by introducing custom entities. The entity-level **Module** property uses the same **ModuleAxapta** extensible enum as the table-level **Module** property.

## Changes to metadata

New software updates can change metadata in finance and operations apps. For example, a developer might add a new field to an existing table or entity. In less frequent cases, a developer might remove an existing field from a table or change the data type of an existing field.

If you change the structure of a table or entity, and especially if you remove a field from the table or entity, you might need to update consuming applications. The Export to Data Lake feature is designed to minimize the downstream impact but also reflect metadata changes in the data lake. This section explains how metadata changes are reflected in the data lake.

> [!NOTE]
> Finance and operations apps include governance processes and developer tools that help developers learn about such changes and their impact. However, users who consume data in the date lake by creating and running a Power BI report, for example, might not be aware of changes in finance and operations apps.

When you add a new field to a table, the system updates metadata files in the data lake to reflect the change. All the records in the CSV files that include the newly added data contain the new field. If a CSV file isn't modified, or if no new rows are added, the file doesn't contain the new field. This behavior helps minimize the data writes to the data lake. Most data pipeline tools, and especially those tools that understand the CDM standard, support a feature that can adapt to changes. This feature is known as *schema drift*.

If you make a destructive change to the data structure, the system might repopulate the whole table folder (that is, all the CSV files). For example, in a rare but destructive change, a developer removes a field from a table in a finance and operations app. In this case, the whole table folder is repopulated, together with the updated metadata. Destructive changes might require changes to downstream reports, especially if the report is expecting a data field that was removed.

## Any questions, feedback?

The product team is actively working on this and other features. To stay in touch and ask questions of the product team or your fellow customers or partners, join the [Preview Early Access](https://engage.cloud.microsoft/main/org/microsoft.com/groups/eyJfdHlwZSI6Ikdyb3VwIiwiaWQiOiIyMzc5NDE5MzIwMzIifQ) community on Microsoft Viva Engage. You can provide feedback directly to the product team. You can attend weekly online "office hours" meetings and use the Viva Engage online forums to stay in touch and ask questions.
