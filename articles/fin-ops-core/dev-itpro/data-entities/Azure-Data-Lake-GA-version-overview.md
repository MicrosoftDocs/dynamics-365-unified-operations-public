---
# required metadata

title: Export to Azue Data Lake overview
description: This topic provides an overview of Microsoft Azure Data Lake.
author: MilindaV2
ms.date: 11/20/2021
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: milindav
ms.search.validFrom: 2021-11-30

---

# Export to Azue Data Lake overview

[!include [banner](../includes/banner.md)]

## What is Export to Azure Data Lake?
Connect your Finance and Operations environment with an Azure Data Lake and unlock insights hidden in your data.

When you enable the Export to Azure Data Lake add-in, you will connect your Finance and Operations environment to a designated Azure Data Lake. Authorized users can copy data from your Finance and Operations environment to your Azure Data Lake. With data in the lake, tools such as Power BI and Azure Synapse enable analytics, business intelligence, and machine learning scenarios.

When you choose data in Finance and Operations, the system makes an initial copy of the data in the lake. After the initial copy, the system keeps the data in the lake fresh by continuously inserting, updating, and deleting data that changed. There is no need to manage exports or to monitor the service. There is no additional burden added to your Finance and Operations workloads.

Data is stored in the lake organized in a folder structure using Common Data Model format. Common Data Model format provides additional metadata, such as table structure, descriptions, and data types in a machine-readable JSON format, such that downstream tools understand the semantics of the data.

Export to Azure Data Lake is a fully managed, scalable, and highly-available service from Microsoft with built-in disaster recovery. Features supported include:

- You can choose up to 200 tables. All changes to data including insert, modify, and delete operations are continuously updated in the lake.

- Choose data using tables or entities. When you choose data using entities, underlying tables are chosen by the service.

- You can choose standard, as well as custom entities and tables.

- You can work with data in the lake using T-SQL with Synapse SQL Serverless. You can easily integrate data in the lake with Synapse workspaces using ready-made, solution templates called [CDMUtilSolution](https://github.com/microsoft/Dynamics-365-FastTrack-Implementation-Assets/tree/master/Analytics/CDMUtilSolution).

The storage account must be in the same Azure region as your Finance and Operations environment.

See the preview features, list below, as well.

> [!NOTE]
> Preview features are not complete, but are made available on a preview basis so customers can get early access and provide feedback. Preview features may have limited or restricted functionality, are not meant for production use, and may be available only in selected geographic areas. 
>
>By enabling preview features, you agree to **Supplemental Terms of Use** described [here] (https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/get started/public-preview-terms).
>

## Enable near real time data changes (preview)

When you choose this preview feature, Data is added, updated and deleted into your data lake in near-real time. As data is updated in your Finance and Operations environment, the same data is updated within a few minutes.

When you choose this option, number of tables you can choose increases to 350 tables.

In addition, you can also update downstream data warehouses using Change data in the lake. Using change data folder, you can easily identify the changes made to the data and create near real-time data pipelines.

See more information on near real time Change feeds [here] (https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/azure-data-lake-change-feeds)

## Enable enhanced metadata in Data lake (preview)
This preview feature provides enhanced metadata stored in Finance and Operations application layer (ie. Application Object Server, or AOS) available in the Data lake as CDM metadata files. Enhanced metadata made available by this feature includes

-   Field names and descriptions present in Finance and Operations

-   Extended Data types including string lengths of character fields

-   Enumerated data types (ex. Yes, No) along with names, labels and values of available options

-   Entity view definitions (enables you to create Entity shapes using Data in the lake using Synapse SQL Serverless)

Metadata is stored in the lake using a machine readable JSON format known as the Common Data Model (CDM) format. When using this preview feature, CDM metadata files are enriched with enhanced metadata.

## Frequently asked questions

### What is Azure Data lake, what benefits do Data lakes offer?

Azure Data Lake is a technology in Azure cloud that enables storing and working with "big data" for analytics and applying machine learning and AI. When this topic mentions "Data Lake," it's referring specifically to storage technology that is based on Azure Data Lake Storage Gen2.

Data lakes provide cloud storage that is less expensive than the cloud storage that relational databases provide. Therefore, large amounts of data can be stored in the cloud. This data includes both business data that is traditionally stored in business systems and data warehouses, device and sensor data, such as signals from devices. In addition, Data Lake supports a range of tools and programming languages that enable large amounts of data to be reported on, queried, and transformed.

### How much will this service cost?

You need to provision an Azure Data lake in your own subscription. Export to Data lake service copies data into your own lake. You can query the data in your lake using PowerBI, Spark as well as many other tools from Microsoft and others.

Export to Data lake service is an add-on service offered by Dynamics 365 Finance and Operations. Export to Data lake add-on service is included with your subscription to Dynamics 365 services.

Because Data Lake Storage Gen2 is in your own subscription, you must pay for data storage and input/output (I/O) costs that are incurred when data is read and written to the data lake. You may also incur I/O costs because Finance and Operations apps write data to the data lake or update the data in it. To help reduce intra-region I/O costs, Finance and Operations apps require that data lakes be provisioned in the same country or geographic region as the Finance and Operations environment.

You can use the tool provided by Fast Track solution templates to estimate the cost of storage based on your business volumes in Finance and Operations.

[Dynamics-365-FastTrack-Implementation-Assets/Analytics/CostCalculator at master · microsoft/Dynamics-365-FastTrack-Implementation-Assets (github.com)](https://github.com/microsoft/Dynamics-365-FastTrack-Implementation-Assets/tree/master/Analytics/CostCalculator)

### We are using BYOD service today, why should we transition to Data lake?

Customers use BYOD to extract data from Finance and Operations apps so that they can use that data for reporting or analytics. BYOD requires that customers provision and maintain an Azure SQL database to store data that is exported from Finance and Operations apps.

In operational reporting scenarios, exported data in BYOD (a SQL database) is used to create reports.

For more complex data warehousing scenarios, BYOD is used as a staging area, where a "snapshot" of the Finance and Operations data is retained. You may have downstream data pipelines that copy the data from the BYOD "staging area" to the data warehouse.

If you're currently using BYOD for these scenarios, you can transition to Export to Data Lake feature. You may benefit in following ways.

-   **Because data is already present, export isn't required.** Data Lake integration manages continuous export of data to the lake as it changes in Finance and Operations apps. You don’t need to monitor and manage data exports as you do in BYOD

-   **Reduced cost of Data storage:** Data is stored in a data lake instead of the SQL database that BYOD requires. Therefore, customer can use a storage medium that is much less expensive than Azure SQL Database for staging data.

-   **Existing downstream/consumption pipelines can be preserved.** In the first scenario, many reporting tools work with SQL databases, because they can use Transact-SQL (T-SQL) to read data. You can create a SQL Server endpoint by using Azure Synapse Analytics. Azure Synapse includes SQL-on-demand capability that enables Data Lake to be queried by using the T-SQL language. While you can use the T-SQL endpoint for the second scenario, your data integration pipeline may also be able to consume files in a lake. Either way, you can transition from BYOD without incuring major costs 

### How often is data updated in the lake?

When you choose data, Export to Data lake service makes an initial copy of the data in the lake. If you choose multiple tables, the system makes the initial copy by taking 10 tables at a time. Depending on the size of the data and the number of records in the table, this may take a few mins or even a few hours. You can see the export progress on screen.

Once the initial copy is done, the system continuously updates the data as changes happen in Finance and Operations. When new records are added, modified or deleted, Data records in the lake are added, modified or deleted accordingly.

Using the optional, near-real time change feature currently in preview, data in the lake is updated within minutes of a change in Finance and Operations.

If you do not use the near real-time update feature, data in the lake is updated within a few hrs of a change in Finance and Operations.

Export to Data lake form in Finance and Operations shows the last time stamp the data was updated in the lake. The system also adds additional data fields that help you identify the time the data was updated in the lake. Using these time stamps, your downstream processes can detect and process data as they change in the lake.

### Why can’t I see "Export to Data lake" feature in my environment?

The Export to Data Lake feature is available in the **United States, Canada, United Kingdom, Europe, South East Asia, India, East Asia, Australia, and Japan** regions. If your Finance and Operations environment is in any of those regions, you can enable this feature in your environment by using Microsoft Dynamics Lifecycle Services (LCS).

This feature will be available in more regions in the future

The Export to Data Lake feature isn't available in Tier-1 (developer) environments. You must have a cloud-based Tier-2 or higher sandbox environment to enable this feature.

In your Tier-1 (developer) environment, you can prototype or plan the feature implementation by using [GitHub tools](https://github.com/microsoft/Dynamics-365-FastTrack-Implementation-Assets/blob/master/Analytics/AzureDataFactoryARMTemplates/SQLToADLSFullExport/ReadmeV2.md). The tools let you export data from your Tier-1 or sandbox environment into a storage account in the same format that is exported by the feature


### How can I stay in touch with upcoming features?

In the coming months, Microsoft will enable this feature in additional regions. We are also actively working additional features. Do you want to stay in touch and ask questions from product team or your fellow customers and partners? Do you want to provide feedback directly to the product team?

You can join the [preview Yammer group](https://www.yammer.com/dynamicsaxfeedbackprograms/#/threads/inGroup?type=in_group&feedId=32768909312&view=all). where can attend weekly online "office hours" meetings and use the Yammer online forums to stay in contact and ask questions.




