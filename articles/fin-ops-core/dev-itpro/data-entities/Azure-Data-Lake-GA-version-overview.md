---
title: Export to Azure Data Lake overview
description: Learn how you can connect your finance and operations environment to a data lake to unlock insights that are hidden in your data.
author: MilindaV2
ms.author: milindav
ms.topic: overview
ms.date: 10/16/2023
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2021-11-30
---

# Export to Azure Data Lake overview

[!include [banner](../includes/banner.md)]

## What is Export to Azure Data Lake?

Export to Azure Data Lake lets you connect your finance and operations environment to a data lake to unlock insights that are hidden in your data.

> [!NOTE]
> Over the past 12 months, we've been working to fill in gaps and add new features that members of the user community have highlighted. [Synapse Link for Dataverse service built into Power Apps](/power-apps/maker/data-platform/azure-synapse-link-select-fno-data), the successor to the **Export to Data Lake** feature in finance and operations apps, is generally available and ready for you. Synapse Link provides one experience for working with data from all Microsoft Dynamics 365 apps.
>
> We want you to benefit from the enhanced performance, flexibility, and improved user experience that Synapse Link offers as soon as possible. Therefore, we've announced the deprecation of the **Export to Data Lake** feature, effective October 15, 2023. If you're already using the **Export to Data Lake** feature, you can continue to use it until November 1, 2024. If you're new to the **Export to Data Lake** feature or are planning to adopt this feature in the coming months, we recommend that you use Synapse Link instead. 
>
> We understand that that transition might seem daunting, but we want to provide a smoother experience and offer guidance. To get started, see the [Synapse Link transition guide](https://aka.ms/TransitionToSynapseLink). We're listening closely to the community and are working on multiple features to help make the transition smoother. We'll announce these other improvements to the transition process as we bring new features online. If you want to stay in touch, join the community at [https://aka.ms/SynapseLinkforDynamics](https://aka.ms/SynapseLinkforDynamics).

When you enable the Export to Azure Data Lake add-in, you connect your finance and operations environment to a designated data lake. Authorized users can then copy data from your finance and operations environment to that data lake. Tools such as Power BI and Azure Synapse enable analytics, business intelligence, and machine learning scenarios for data in the data lake.

When you select data in finance and operations apps, the system makes an initial copy of the data in the data lake. After that initial copy is made, the system keeps the data in the data lake fresh by continuously inserting, updating, and deleting data that changed. You don't have to manage exports or monitor the service, and there's no more burden on your finance and operations workloads.

Data that is stored in the data lake is organized using [Common Data Model](https://powerplatform.microsoft.com/common-data-model/). Common Data Model enhances the value of your data in the lake. For example, it provides more metadata in a machine-readable JavaScript Object Notation (JSON) format, so that downstream tools can determine the semantics of the data. The extra metadata includes the table structure, descriptions, and data types.

Export to Azure Data Lake is a fully managed, scalable, and highly available service from Microsoft. It includes built-in disaster recovery. Here are some of the features that are supported:

- You can select up to 350 tables. All changes to data are continuously updated in the data lake. These changes include insert, update, and delete operations.
- You can select data by using tables or entities. If you use entities, underlying tables are selected by the service.
- You can select both standard and custom entities and tables.
- You can work with data in the data lake by using Microsoft Azure Synapse Analytics or many other third-party tools.

The storage account must be in the same Azure region as your finance and operations environment. You can select to enable near real-time data changes and business events when installing the service.


## Enable near real-time data changes 
When you select this feature, data is inserted, updated, and deleted in your data lake in near real-time. As data changes in your finance and operations environment, the same data is updated in the data lake within a few minutes.

In addition, you can update downstream data warehouses by using changed data in the data lake. By using the change data folder, you can easily identify the changes that were made to the data and create near-real-time data pipelines.

For more information about near-real-time change feeds, see [Change data in Azure Data Lake](azure-data-lake-change-feeds.md).

## Business events 
By enabling this feature, you can be alerted when something important happens in the data lake. For example, you can be alerted when data is initialized in the lake. The system generates a business event when the initial copy of data is completed. [Business events](/powerapps/developer/data-platform/business-events) is a framework in Dynamics 365 and Dataverse that lets you easily create intelligent actions and automations. For example, by using [Power Automate](https://powerautomate.microsoft.com/), a tool that is integrated into Power Platform, you can build an automated workflow to perform actions such as automatically triggering a downstream data pipeline.

For more information about business events that are generated by the Export to Data Lake service, see [Business events generated by the Export to Azure Data Lake service](Azure-Data-Lake-Generates-Biz-events.md).

## Enhanced Metadata 

Besides data, the data lake contains metadata that describes the name, data type, and size of data. In the lake, you notice, in addition to data files, metadata files at a folder level that corresponds to the data files. When you install the Export to Data Lake feature and select data to add to the data lake, the system writes metadata files in addition to data. If you select the **Enhanced metadata** option when you install Export to Data Lake, the system adds even more metadata. For more information about metadata and the Enhanced Metadata feature, see [Data and metadata stored in Azure Data Lake](Azure-Data-Lake-Enhanced-Metadata.md).

## Frequently asked questions

### What is Azure Data Lake, and what benefits do data lakes offer?

Azure Data Lake is a technology in the Azure cloud that lets you store and work with "big data" for analytics, and apply machine learning and AI. When this article mentions "Data Lake," it's referring specifically to storage technology that is based on Azure Data Lake Storage Gen2.

Data lakes provide cloud storage that is less expensive than the cloud storage that relational databases provide. Therefore, large amounts of data can be stored in the cloud. This data includes both business data that is traditionally stored in business systems and data warehouses, and device and sensor data, such as signals from devices. In addition, Data Lake supports a range of tools and programming languages that enable large amounts of data to be reported on, queried, and transformed.

### How much does this service cost?

You must provision a data lake in your own subscription. The Export to Azure Data Lake service copies data into your own data lake. You can query the data in your data lake by using Power BI, Spark, and many other tools from Microsoft and other sources.

Export to Azure Data Lake is an add-on service that is included with your subscription to Dynamics 365 services.

Because Data Lake Storage Gen2 is in your own subscription, you must pay for data storage and input/output (I/O) costs that are incurred when data is read from and written to the data lake. You might also incur I/O costs because finance and operations apps write data to the data lake or update data in it. To help reduce intra-region I/O costs, finance and operations apps require that data lakes be provisioned in the same country or geographic region as the finance and operations environment.

The FastTrack solution templates provide a tool that you can use to estimate the cost of storage, based on your business volumes in finance and operations apps. For more information, see [FastTrack for Dynamics 365 - CostCalculator](https://github.com/microsoft/Dynamics-365-FastTrack-Implementation-Assets/tree/master/Analytics/CostCalculator).

### I'm currently using a BYOD service. Why should I transition to Data Lake?

Customers use [bring your own database (BYOD)](../analytics/export-entities-to-your-own-database.md) to extract data from finance and operations apps so that they can use it for reporting or analytics. BYOD requires that customers provision and maintain an Azure SQL database to store data that is exported from finance and operations apps.

In operational reporting scenarios, exported data in BYOD (that is, an SQL database) is used to create reports.

For more complex, data warehousing scenarios, BYOD is used as a staging area, where a *snapshot* of the finance and operations data is retained. You might then have downstream data pipelines that copy the data from the BYOD staging area to the data warehouse.

If you're currently using BYOD for these types of scenarios, you can transition to the Export to Data Lake feature. In this case, you might benefit in the following ways:

- **Because data is already present, export isn't required.** Data Lake integration manages continuous export of data to the data lake as it changes in finance and operations apps. You don't have to monitor and manage data exports as you do in BYOD.
- **The cost of data storage is reduced.** Data is stored in a data lake instead of in the SQL database that BYOD requires. Therefore, customers can use a storage medium that is much less expensive than Azure SQL Database to stage data.
- **Existing downstream/consumption pipelines can be preserved.** Using [Azure Synapse Analytics serverless SQL pools](/azure/synapse-analytics/sql/on-demand-workspace-overview), you can create T-SQL view definitions over data in the lake and read data the same way as you read data from BYOD. Your data integration pipeline might be repointed to consume data in the lake without incurring major costs. 

The BYOD solution exports entity data shapes from finance and operations apps into Azure SQL database. The **Export to Data Lake** feature lets you choose data using entity shapes or tables. Using data exported to the lake, you can re-create entity shapes in Azure Synapse Analytics serverless SQL pools using [FastTrack for Dynamics 365 - CDMUtilSolution](https://github.com/microsoft/Dynamics-365-FastTrack-Implementation-Assets/tree/master/Analytics/CDMUtilSolution).  

### How is the data stored in the lake?
Data in the lake is stored as CSV files in a folder structure maintained by the system. The folder structure is based on data organization in finance and operations apps. For example, you see folders with names such as **Finance**, **Supply Chain**, **Commerce**, and within these folders you see subfolders with names such as **Accounts Receivable** or **Accounts Payable**. Further down the hierarchy, you see folders that contain the actual data for each table. Within a table-level folder, you see one or more CSV files and metadata files that describe the format of the data. 

When data in finance and operations apps gets updated, corresponding data rows in CSV files in the table folders are updated. When a new row is added to a table in finance and operations apps, or an existing row is deleted, new rows are added or deleted from corresponding CSV files. 

When the data structures change in finance and operations apps, for example, when a new field is added to a table, metadata files in the lake are updated to reflect the change. The system might also repopulate the entire table folder (all the CSV files) in case the data structure change is destructive. For example, in case a field is removed from a table in a finance and operations app, a rare but more destructive scenario, the entire table folder is repopulated. Whereas when a new field is added, all the data files aren't repopulated. Only the data files that contain changed rows are updated to include the new field. Because many consuming tools can work with newly added data fields (a feature called *schema drift*) the system doesn't repopulate the entire folder.  

### How can I consume data in the lake?
You can work with data in the data lake using various tools from Microsoft, and third parties. Most tools can consume data in the lake stored as CSV files.  

Using Azure Synapse Analytics serverless SQL pools, you can consume data in the lake using Transact-SQL language (T-SQL). T-SQL language is widely supported by many tools. You can define a Synapse workspace over the data in the lake and use T-SQL, Spark, or Synapse Pipelines as if you're consuming data from a database. To create a Synapse workspace over your data in the lake, you can use [FastTrack Solutions for Dynamics 365 - CDMUtilSolution](https://github.com/microsoft/Dynamics-365-FastTrack-Implementation-Assets/tree/master/Analytics/CDMUtilSolution).

You can also use ready-made solution templates to copy data from the lake into an SQL Server data warehouse or to another destination. For more information, see [FastTrack Solutions for Dynamics 365 - SynapseToSQL_ADF](https://github.com/microsoft/Dynamics-365-FastTrack-Implementation-Assets/tree/master/Analytics/SynapseToSQL_ADF).

### How often is data in the data lake updated?

When you select data, the Export to Azure Data Lake service makes an initial copy of the data in the data lake. If you select multiple tables, the system makes the initial copy by taking 10 tables at a time. Depending on the size of the data and the number of records in the table, this process might take a few minutes or even a few hours. The export progress is shown on-screen.

After the initial copy is made, the system continuously updates the data as changes occur in finance and operations apps. When records are inserted, updated, or deleted, data records in the data lake are inserted, updated, or deleted accordingly.

If you use the optional, near real-time change feature, data in the data lake is updated within minutes of a change in the finance and operations environment. Otherwise, data in the data lake is updated within a few hours of a change in the finance and operations environment.

The **Export to Data Lake** page in a finance and operations environment shows the time stamp of the last update of the data in the data lake. The system also adds data fields that help you identify the time when the data in the data lake was updated. Your downstream processes can use the time stamps to detect and process data as it changes in the data lake.

### Why don't I see the Export to Data Lake feature in my environment?

The Export to Data Lake feature is available only in the United States, Canada, United Kingdom, Europe, Switzerland, South East Asia, India, East Asia, Australia, Latin America, and Japan regions. If your finance and operations environment is in any of those regions, you can enable this feature in your environment by using Microsoft Dynamics Lifecycle Services. The feature will eventually be made available in more regions.

The Export to Data Lake feature isn't available in Tier-1 (developer) environments. To enable this feature, you must have a cloud-based Tier-2 or higher sandbox environment.

In your Tier-1 (developer) environment, you can use a prototype or plan the feature implementation by using [FastTrack for Dynamics 365 - GitHub tools](https://github.com/microsoft/Dynamics-365-FastTrack-Implementation-Assets/blob/master/Analytics/AzureDataFactoryARMTemplates/SQLToADLSFullExport/ReadmeV2.md). The tools let you export data from your Tier-1 or sandbox environment into a storage account in the same format that the feature exports in.

### How can I stay in touch about upcoming features?

In the coming months, Microsoft will enable the Export to Data Lake feature in more regions. We're also actively working on other features. Do you want to stay in touch and ask questions of the product team or your fellow customers or partners? Do you want to provide feedback directly to the product team? If you do, you can join the [Synapse Link for Dynamics preview Yammer group](https://www.yammer.com/dynamicsaxfeedbackprograms/#/threads/inGroup?type=in_group&feedId=32768909312&view=all). You can then attend weekly online "office hours" meetings and use the Yammer online forums to stay in touch and ask questions.
