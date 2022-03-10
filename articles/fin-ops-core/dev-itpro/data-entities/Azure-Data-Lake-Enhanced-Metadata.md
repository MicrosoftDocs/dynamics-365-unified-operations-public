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

When data in Finance and Operations apps gets updated, corresponding data rows in CSV files in the table folders are updated. When a new row is added to a table in Finance and Operations apps, or an existing row is deleted, new rows are added or deleted from corresponding CSV files. Number of CSV files in the lake depends on size of data rows. System makes an effort to keep each CSV file around 200MB in size to optimize write and read operations.    


## What is metadata and how are they stored in the Data lake?

Metadata describes the names, data type, size and nature of data. Along with Data files in the lake, you will notice metadata files at a folder level. Metadata in the lake is written using a machine readable format described by the [Common Data Model standard](https://docs.microsoft.com/common-data-model/sdk/overview)


If you are familiar with Dynamics applications such as Finance and Supply chain, you may be familiar with the rich metadata structures present in the application. In addition to basic types, Dynamics metadata includes; 

-   **Extended Data Types (EDTs)** that offer richer data types that describe behavior and business rules applicable to "Business data types" such as Bank Accounts, Ledger Account and Phone numbers. 
-   You may also be familiar with **descriptive names – along with translated labels available in many languages**.
-   **Relationships** between tables enables you to navigate thru data easily
    (these relationships are not implemented in the underlying relational
    database)
-   Higher level data abstractions such as **Entity definitions**


When the data structures change in Finance and Operations apps, for an example, when a new field is added to a table, metadata files in the lake are updated to reflect the change. The system may also repopulate the entire table folder (all the CSV files) in case the data structure change is destructive. For an example, in case a field is removed from a table in a Finance and Operations app, a rare but more destructive scenario, the entire table folder is repopulated. Whereas when a new field is added, all the data files are not repopulated. Only the data files that contain changed rows are updated to include the new field. Because many consuming tools can work with newly added data fields (a feature called *schema drift*) the system does not repopulate the entire folder. 


## What is Export to Azure Data Lake?

Export to Azure Data Lake lets you connect your Finance and Operations environment to a data lake to unlock insights that are hidden in your data.

Data exported from Finance and Operations is stored in the lake as raw files
(ie. Comma separated files, or CSV files). In addition to data, rich metadata
stored in Finance and Operations application layer (ie. Application Object
Server, or AOS) is also available in Data lake. Having rich metadata enables you
to consume the data using client tools without having to work with raw files.
The following sections describe the preview features that are available.

> [!NOTE]
> Preview features aren't complete. However, they are made available on a preview basis, so that customers can get early access and provide feedback. Preview features might have limited or restricted functionality, they aren't meant for production use, and they might be available only in selected geographic areas.
>
> By enabling preview features, you agree to the [Supplemental Terms of Use](../../fin-ops/get-started/public-preview-terms.md).


