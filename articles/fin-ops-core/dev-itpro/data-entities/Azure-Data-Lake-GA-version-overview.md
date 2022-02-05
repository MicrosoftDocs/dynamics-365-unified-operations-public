---
# required metadata

title: Export to Azure Data Lake overview
description: This topic explains how you can connect your Finance and Operations environment to a data lake to unlock insights that are hidden in your data.
author: MilindaV2
ms.date: 11/20/2021
ms.topic: overview
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: milindav
ms.search.validFrom: 2021-11-30

---

# Export to Azure Data Lake overview

[!include [banner](../includes/banner.md)]

## What is Export to Azure Data Lake?

Export to Azure Data Lake lets you connect your Finance and Operations environment to a data lake to unlock insights that are hidden in your data.

When you enable the Export to Azure Data Lake add-in, you connect your Finance and Operations environment to a designated data lake. Authorized users can then copy data from your Finance and Operations environment to that data lake. Tools such as Power BI and Azure Synapse enable analytics, business intelligence, and machine learning scenarios for data in the data lake.

When you select data in Finance and Operations apps, the system makes an initial copy of the data in the data lake. After that initial copy is made, the system keeps the data in the data lake fresh by continuously inserting, updating, and deleting data that changed. You don't have to manage exports or monitor the service, and there is no additional burden on your Finance and Operations workloads.

Data that is stored in the data lake is organized in a folder structure that uses Common Data Model format. Common Data Model format provides additional metadata in a machine-readable JavaScript Object Notation (JSON) format, so that downstream tools can determine the semantics of the data. The additional metadata includes the table structure, descriptions, and data types.

Export to Azure Data Lake is a fully managed, scalable, and highly available service from Microsoft. It includes built-in disaster recovery. Here are some of the features that are supported:

- You can select up to 200 tables. All changes to data are continuously updated in the data lake. These changes include insert, update, and delete operations.
- You can select data by using tables or entities. If you use entities, underlying tables are selected by the service.
- You can select both standard and custom entities and tables.
- You can work with data in the data lake by using Transact-SQL (T-SQL) with Synapse SQL Serverless. You can easily integrate data in the data lake with Synapse workspaces by using a set of ready-made solution templates that is named [CDMUtilSolution](https://github.com/microsoft/Dynamics-365-FastTrack-Implementation-Assets/tree/master/Analytics/CDMUtilSolution).

The storage account must be in the same Azure region as your Finance and Operations environment.

The following sections describe the preview features that are available.

> [!NOTE]
> Preview features aren't complete. However, they are made available on a preview basis, so that customers can get early access and provide feedback. Preview features might have limited or restricted functionality, they aren't meant for production use, and they might be available only in selected geographic areas.
>
> By enabling preview features, you agree to the [Supplemental Terms of Use](../../fin-ops/get-started/public-preview-terms.md).

## Enable near real-time data changes (preview)

When you select this preview feature, data is inserted, updated, and deleted in your data lake in near-real time. As data changes in your Finance and Operations environment, the same data is updated in the data lake within a few minutes.

When you use this feature, the number of tables that you can select increases to 350.

In addition, you can update downstream data warehouses by using changed data in the data lake. By using the change data folder, you can easily identify the changes that were made to the data and create near-real-time data pipelines.

For more information about near-real-time change feeds, see [Change data in Azure Data Lake](azure-data-lake-change-feeds.md).


## Frequently asked questions

### What is Azure Data Lake, and what benefits do data lakes offer?

Azure Data Lake is a technology in the Azure cloud that lets you store and work with "big data" for analytics, and apply machine learning and AI. When this topic mentions "Data Lake," it's referring specifically to storage technology that is based on Azure Data Lake Storage Gen2.

Data lakes provide cloud storage that is less expensive than the cloud storage that relational databases provide. Therefore, large amounts of data can be stored in the cloud. This data includes both business data that is traditionally stored in business systems and data warehouses, and device and sensor data, such as signals from devices. In addition, Data Lake supports a range of tools and programming languages that enable large amounts of data to be reported on, queried, and transformed.

### How much does this service cost?

You must provision a data lake in your own subscription. The Export to Azure Data Lake service copies data into your own data lake. You can query the data in your data lake by using Power BI, Spark, and many other tools from Microsoft and other sources.

Export to Azure Data Lake is an add-on service that is included with your subscription to Dynamics 365 services.

Because Data Lake Storage Gen2 is in your own subscription, you must pay for data storage and input/output (I/O) costs that are incurred when data is read from and written to the data lake. You might also incur I/O costs because Finance and Operations apps write data to the data lake or update data in it. To help reduce intra-region I/O costs, Finance and Operations apps require that data lakes be provisioned in the same country or geographic region as the Finance and Operations environment.

The FastTrack solution templates provide a tool that you can use to estimate the cost of storage, based on your business volumes in Finance and Operations apps. For more information, see [CostCalculator](https://github.com/microsoft/Dynamics-365-FastTrack-Implementation-Assets/tree/master/Analytics/CostCalculator).

### I am currently using a BYOD service. Why should I transition to Data Lake?

Customers use [bring your own database (BYOD)](../analytics/export-entities-to-your-own-database.md) to extract data from Finance and Operations apps so that they can use it for reporting or analytics. BYOD requires that customers provision and maintain an Azure SQL database to store data that is exported from Finance and Operations apps.

In operational reporting scenarios, exported data in BYOD (that is, a SQL database) is used to create reports.

For more complex, data warehousing scenarios, BYOD is used as a staging area, where a *snapshot* of the Finance and Operations data is retained. You might then have downstream data pipelines that copy the data from the BYOD staging area to the data warehouse.

If you're currently using BYOD for these types of scenarios, you can transition to the Export to Data Lake feature. In this case, you might benefit in the following ways:

- **Because data is already present, export isn't required.** Data Lake integration manages continuous export of data to the data lake as it changes in Finance and Operations apps. You don't have to monitor and manage data exports as you do in BYOD.
- **The cost of data storage is reduced.** Data is stored in a data lake instead of in the SQL database that BYOD requires. Therefore, customers can use a storage medium that is much less expensive than Azure SQL Database to stage data.
- **Existing downstream/consumption pipelines can be preserved.** In the first type of scenario, many reporting tools work with SQL databases, because they can use T-SQL to read data. You can create a SQL Server endpoint by using Azure Synapse Analytics. Synapse includes SQL-on-demand capability that enables Data Lake to be queried by using the T-SQL language. Although you can use the T-SQL endpoint for the second type of scenario, your data integration pipeline might also be able to consume files in a data lake. Either way, you can transition from BYOD without incurring major costs.

### How often is data in the data lake updated?

When you select data, the Export to Azure Data Lake service makes an initial copy of the data in the data lake. If you select multiple tables, the system makes the initial copy by taking 10 tables at a time. Depending on the size of the data and the number of records in the table, this process might take a few minutes or even a few hours. The export progress is shown on-screen.

After the initial copy is made, the system continuously updates the data as changes occur in Finance and Operations apps. When records are inserted, updated, or deleted, data records in the data lake are inserted, updated, or deleted accordingly.

If you use the optional near-real-time change feature (currently in preview), data in the data lake is updated within minutes of a change in the Finance and Operations environment. Otherwise, data in the data lake is updated within a few hours of a change in the Finance and Operations environment.

The **Export to Data Lake** page in a Finance and Operations environment shows the time stamp of the last update of the data in the data lake. The system also adds data fields that help you identify the time when the data in the data lake was updated. Your downstream processes can use the time stamps to detect and process data as it changes in the data lake.

### Why don't I see the Export to Data Lake feature in my environment?

The Export to Data Lake feature is available only in the **United States**, **Canada**, **United Kingdom**, **Europe**, **South East Asia**, **India**, **East Asia**, **Australia**, and **Japan** regions. If your Finance and Operations environment is in any of those regions, you can enable this feature in your environment by using Microsoft Dynamics Lifecycle Services (LCS). The feature will eventually be made available in more regions.

The Export to Data Lake feature isn't available in Tier-1 (developer) environments. To enable this feature, you must have a cloud-based Tier-2 or higher sandbox environment.

In your Tier-1 (developer) environment, you can prototype or plan the feature implementation by using [GitHub tools](https://github.com/microsoft/Dynamics-365-FastTrack-Implementation-Assets/blob/master/Analytics/AzureDataFactoryARMTemplates/SQLToADLSFullExport/ReadmeV2.md). The tools let you export data from your Tier-1 or sandbox environment into a storage account in the same format that the feature exports in.

### How can I stay in touch about upcoming features?

In the coming months, Microsoft will enable the Export to Data Lake feature in more regions. We are also actively working on other features. Do you want to stay in touch and ask questions of the product team or your fellow customers or partners? Do you want to provide feedback directly to the product team? If you do, you can join the [preview Yammer group](https://www.yammer.com/dynamicsaxfeedbackprograms/#/threads/inGroup?type=in_group&feedId=32768909312&view=all). You can then attend weekly online "office hours" meetings and use the Yammer online forums to stay in touch and ask questions.
