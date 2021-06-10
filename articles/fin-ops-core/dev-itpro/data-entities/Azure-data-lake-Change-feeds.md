---
# required metadata

title: Changed data in Azure Data lake
description: This topic explains change data in the lake and what you can do with it.
author: MilindaV2
ms.date: 06/08/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: NOINDEX, NOFOLLOW
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend

# ms.tgt_pltfrm: 
ms.custom: 96283
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: milindav
ms.search.validFrom: 2020-06-01
ms.dyn365.ops.version: Platform Update 40

---

# Change data in Azure Data Lake

[!include [banner](../includes/banner.md)]

> [!NOTE]
> The **Export to Data Lake** feature is in public preview in the United States, Canada, United Kingdom, Europe, South East Asia, East Asia, Australia, and Japan regions. If your Finance and Operations environment is in any of those regions, you can enable this feature in your environment by using Microsoft Dynamics Lifecycle Services (LCS). Before you can use this feature, see [Configure export to Azure Data Lake](configure-export-data-lake.md).
>

Change data in the lake enable you to trigger downstream data pipelines for data changes in Dynamics. **Change feed** folder in the lake contains each of the data changes in Dynamics. Change feed folder is automatically created by the **Export to Data Lake** feature in Finance and Operations Apps. 

## Why do you need change data in the lake?
Data in the lake is often used for reporting purposes. While you can create
reports using the table data in the lake, you may create additional copies of
the data to improve your reporting. For an example, you may have a data mart
designed to enable your Power users where you may have simplified, often
aggregated fact tables and dimension tables.

As table data in the lake gets updated, you need to keep corresponding fact
tables and dimension tables in the lake updated so that your reports will
reflect latest data.

Simplest way to update fact tables and dimension tables would be to create a
full copy on a periodic basis using tables. However, that approach may be
inefficient – ie. If your tables are large, say tens or even hundreds of
millions of rows, refreshing a fact table by creating a full copy may take hours
and may consume a lot of compute resources. Your users may not get the reports
they need in time (ie. Have to wait for hours to see latest data in reports),
and also, due to consuming compute resources to re-process data each time, you
may get a larger bill from the services you have consumed.

Incrementally updating your fact and dimension tables, that is choosing only the
changed records from source tables and updating them in corresponding fact and
dimension tables provides the answer to both these problems. Incremental update
is a standard capability in most ETL and data transformation tools. However, for
incremental update feature to work, you do need to identify the records that
changed in source tables.

Change feeds folder provides a history of table data changes in the lake such
that ETL processes can be designed for incremental update.

## Change feeds explained

Change feed feature relies on SQL Server Change Data Capture (CDC) feature –
which is the native approach for capturing change data within the database
layer. Change feed feature enables you to access the CDC change log in your Data
lake.

Following diagram explains how change feeds operate in Finance and Operations.

![](media/Change-feed-overview-picture.png)

1.  Whenever a data change happens in the Finance and Operations, underlying
    database (AXDB) gets updated. The update is reflected in the database using
    a native SQL server feature called Change Data Capture (CDC). CDC feature
    captures the changes in a log, (**Change Log**) along with a Logical
    Sequence Number (**LSN**), a Date-time stamp (**Change DateTime**) as well
    as the **Change Payload** which identifies the data that changed

2.  **Export to Data Lake** microservices capture the changes in the database
    and write the Change Log to customer’s Data lake. **Change feed folders** in
    the lake contains the Change log organized into folders.

3.  In addition to change feed folders, each of the rows in **Tables folder**
    (that changed) also contain several new fields. Each row contains the LSN
    number of the corresponding change record and the Change DateTime. While you
    can use the LSN, Change date time fields in the Tables folders to identify
    whether a row changed, they only contain the latest change. If the same row
    changed multiple times, only the latest change is shown in the tables
    folder.

A given change feed folder in the Data lake as well as the changed fields in
respective tables folders are consistent. This means, both the change feed
folder and the corresponding table are updated in the data lake at the exact
same time by a single microservice.

