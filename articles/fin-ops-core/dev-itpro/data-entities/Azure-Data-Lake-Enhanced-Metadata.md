---
# required metadata

title: Enhanced metadata in the lake 
description: This topic explains how data and metadata are stored in the lake.
author: MilindaV2
ms.date: 03/14/2022
ms.topic: overview
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: milindav
ms.search.validFrom: 2021-11-30

---

# Data and metadata stored in Azure Data Lake

[!include [banner](../includes/banner.md)]

## How is the data stored in the lake?

Data in the lake is stored as CSV files in a folder structure maintained by the system. The folder structure is based on data organization in Finance and Operations apps. For an example, you will see folders with names such as **Finance**, **Supply Chain**, **Commerce**, and within these folders you will see sub-folders with names such as **Accounts Receivable** or **Accounts Payable**. Further down the hierarchy, you will see folders that contain the actual data for each table. Within a table-level folder, you will see one or more CSV files as well as metadata files that describe the format of the data. 

When data in Finance and Operations apps gets updated, corresponding data rows in CSV files in the table folders are updated. When a new row is added to a table in Finance and Operations apps, or an existing row is deleted, new rows are added or deleted from corresponding CSV files. Number of CSV files in the lake depends on size of data rows. System makes an effort to keep each CSV file around 200MB in size to optimize write and read operations. In case data size in a CSV file exceeds 200MB, system may split the data into multiple files.   

Data files do not contain field headers or any other information. You will need to read metadata to understand the structure of the files. 

## How is metadata stored in the Data lake?

Metadata describes the names, data type, size and nature of data. Along with Data files in the lake, you will notice metadata files at a folder level corresponding to data files. Metadata in the lake is written using a machine readable format described by the [Common Data Model standard (CDM)](https://docs.microsoft.com/common-data-model/sdk/overview). When you install Export to Data lake feature and choose data to be added to Data lake, system writes metadata files in addition to data. 

Tools from Microsoft and others that understand CDM metadata format make it easy to work with data in the lake. Using Azure Synapse Analytics serverless SQL pools, you can consume data in the lake using Transact-SQL language (T-SQL). T-SQL language is widely supported by many tools. You can define a Synapse workspace over the data in the lake and use T-SQL, Spark, or Synapse Pipelines as if you are consuming data from a database. To create a Synapse workspace over your data in the lake, you can use [FastTrack Solutions for Dynamics 365 - CDMUtilSolution](https://github.com/microsoft/Dynamics-365-FastTrack-Implementation-Assets/tree/master/Analytics/CDMUtilSolution). This solution creates external table definitions in Azure Synapse Analytics serverless SQL pools using metadata in the lake.

If you choose the "Enhanced metadata (preview)" option when installing Export to Data Lake, the system adds even more metadata.

> [!NOTE]
> Preview features aren't complete. However, they are made available on a preview basis, so that customers can get early access and provide feedback. Preview features might have limited or restricted functionality, they aren't meant for production use, and they might be available only in selected geographic areas.
>
> By enabling preview features, you agree to the [Supplemental Terms of Use](../../fin-ops/get-started/public-preview-terms.md).

## Enhanced metadata (preview)
If you are familiar with Dynamics applications such as Finance and Supply chain, you may be familiar with the rich metadata structures present in the application. In addition to basic types, Dynamics enhanced metadata includes; 

-   **Extended Data Types (EDTs)** that offer richer data types that describe behavior and business rules applicable to "Business data types" such as Bank Accounts, Ledger Account and Phone numbers. 
-   You may also be familiar with **descriptive names – along with translated labels available in many languages**.
-   **Relationships** between tables enables you to navigate thru data easily
    (these relationships are not implemented in the underlying relational
    database)
-   Higher level data abstractions such as **Entity definitions**

When you enable Enhanced metadata (preview) option, system writes additional metadata derived from Dynamics into the data lake. Client tools that can understand and work with these additional metadata properties can provide a better experience to users.

### Pre-requisites for enabling Enhanced metadata (preview)
1. Dynamics 365 Finance and Operations application version needs to be higher than the following versions.
- Release 10.0.22 (PU46) with latest updates (version 10.0.995.146 or higher)
- Release 10.0.23 (PU47) with lates updates (version 10.0.1037.133 or higher)
- Release 10.0.24 (PU48) with latest updates (10.0.1084.89 or higher)
- Release 10.0.25 (PU49) and later

2. Your administrator needs to choose the **Enable enhanced metadata (preview)** option when installing the Export to Data lake add-in. You can't enable Enhanced metadata feature without choosing this option at the installation stage. 

3. You need to choose the **Republish metadata** option in Export to Data lake form, Manage options. in Finance and Operations for the first time. You need to perform this operation only once. The system will continue to republish metadata as changes happen. In Release 10.0.23 (PU47) and later, the system auto triggers this option when you open the form for the first time.

### Changes introduced by Enhanced metadata (preview) feature
If you are currently using Export to Data lake feature, you will notice the folder structure and metadata in the lake. When you enable the "Enhanced metadata (preview)" feature by re-installing the add-in, you may notice several changes. More details of the changes are explained in relevant sections below.
1. Data previously contained in the **Custom** folder may be moved to folder structure within subject areas based on metadata defined in Dynamics 365. If you are using the metadata files to navigate and locate data, you will be able to navigate to correct folder structure. However, if you had hard coded the folder sturcture into consuming tools, you may need to revise them
2. In some cases, folder structure under the "Custom" folder will remain along with metadata files. No data files will be present in this folder. 

## Folder structure in Data lake
Dynamics 365 Finance and Operations has over 10,000 tables and over 2,500 entities (the number including extensions and customizations far exceeds this). To enable securing data in the lake in a granular way, Tables and Entities are organized within Finance and Operations into modules representing application areas. This organization is reflected in the Data lake in a folder structure that mimics organization of application areas in Dynamics 365.

### Table folder structure
Table folder structure is 3 levels deep…

1.  **Application area (ex. Finance)** is a grouping of modules in Finance and
    Operations.

2.  **Module (ex. General Ledger)** is derived using a table level metadata
    property **Module** in Finance and Operations. 
    
3.  **Table type (ex. Main)** is derived using existing **TableGroup** metadata
    property

You can see the Application \> Module \> Table type hierarchy for tables that are part of Finance and Operations [here](https://docs.microsoft.com/en-us/common-data-model/schema/core/operationscommon/tables/overview)

> [!NOTE]
>
> When you enable the **Enhanced metadata (preview)** feature, Tables introduced by Systems integrators and partners (sometimes referred to as
**Custom Tables**) will follow the same structure as long as the same metadata properties are added to tables in Finance and Operations. If you do not have the **Enhanced metadata (preview)** feature enabled, all **Custom tables** will be placed in the custom folder. 
>
> Table level module property is backed by an **extensible Enum** called **ModuleAxapta**, the enum contains pre-defined modules shipped by Microsoft. You can extend this enum by adding your own module definitions in addition to using the pre-defined modules defined by Microsoft. Depending on the module property defined at table level, custom tables will be placed in respective folders by the Export to Data lake feature.
>
> Application area to module mapping is defined within Finance and Operations and can’t be modified at this point in time. If you define a new module property
(that likely won’t be reflected in the Application to module mapping), Export to Data lake feature will place the table in an application area folder called
**Custom**.
>
> Module property in tables shipped by Microsoft can’t be modified by a Systems integrator or a partner. While you can modify the Module property in custom
tables as you wish, frequent changes must be avoided. The module property will change resulting location of the table in the data lake. Consuming applications
that may assume a certain location for data files and these applications may be impacted each time you make a change in the module property.
> 
> If a custom table doesn’t have the module table metadata property defined, it will also be placed in the Custom folder.



### Entity folder structure

There are fewer entities compared to tables and Finance and Operations organizes Entity folder structure into 2 levels.

1.  **Application area (ex. Finance)** is a grouping of modules within Finance
    and Operations. The grouping is similar to tables

2.  **Module (ex. General Ledger)** is derived using a entity level metadata
    property **Module** in Finance and Operations. 

Similar to the Module property added to tables, the **Module property** in
Entities can be extended by systems integrators and partners building custom
Entities. Module property in entities is also backed by the same **extensible
Enum, ModuleAxapta**.


## Changes to metadata
Metadata in Finance and Operations can change with new software updates. A
developer may add a new field to an existing table or an Entity. In some less
frequent cases, she may remove a field from a table or perhaps change the data
type of an existing field.

When a table or Entity structure changes, consuming applications may need to
change. This is especially the case when a field is removed from a table or an
Entity. Export to Data lake feature is designed to minimize the downstream impact while reflecting metadata changes in the lake. Let’s understand how metadata changes are reflected in the Data lake.

> [!NOTE]
>
> There are built-in governance processes and developer tools within Finance and Operations where such changes and the resulting impact is highlighted to the developer. However, your users consuming data in the lake, say, by authoring and running a PowerBI report, may not be aware of changes in Finance and Operations.


## when a new field is added

When a new field is added to a table, metadata files in the lake are updated to reflect the change. All the records in the CSV files with newly added data contains the new field. If a CSV file is not modified or no new rows are added, the file does not contain the newly added field. This behavior is adopted to minimize the data writes to the lake. Most data pipeline tools, especially the ones that understand the CDM standard, are able to support a feature known as "Schema drift" that can adapt to changes. 

The system may repopulate the entire table folder (all the CSV files) in case the data structure change is destructive. For an example, in case a field is removed from a table in a Finance and Operations app, a rare but more destructive scenario, the entire table folder is repopulated along with the updated metadata. Desctrucive changes may require changes to downstream reports especially if the report is expecting the removed data field.  




