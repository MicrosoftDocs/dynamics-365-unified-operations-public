---
# required metadata

title: Azure Data Lake overview
description: This topic provides information about...
author: MilindaV2
manager: AnnBe
ms.date: 01/15/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: NOINDEX, NOFOLLOW
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations

# ms.tgt_pltfrm: 
ms.custom: 96283
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: milindav
ms.search.validFrom: 2020-03-01
ms.dyn365.ops.version: Platform Update 34

---

# Azure Data Lake overveiw

[!include [banner](../includes/banner.md)]

What is Azure Data Lake?
------------------------

Azure Data Lake is a technology designed to enable big data Analytics and AI in
the Azure cloud. When referring to Azure Data Lake, we specifically refer to
Azure Data Lake Gen2 (ADLS) based storage technology.

 

Data lakes provide cheap cloud storage compared to a relational database. This
enables storing large amounts of data in the cloud - both business data
(traditionally stored in business systems and data warehouses) to device and
sensor data such as signals from devices. In addition to cheap storage, Azure
Data lake supports a range of tools and programming languages that enable
Reporting, querying and transforming large amounts of data.

 

For an overview of Azure Data Lake Gen2, pl. see the documents here:
<https://docs.microsoft.com/en-us/azure/storage/blobs/data-lake-storage-introduction>\>

 

Dynamics 365 products including Finance and Operations (F&O) leverages Azure
Data Lake for AI and Analytics scenarios thereby providing enabling customers to
leverage the strengths and cost advances offered by this technology. Following
sections offer an overview of scenarios.

Analytical workspaces
---------------------

Analytical workspaces provide contextual and actionable insights within F&O.
Analytical workspaces provide a birds-eye view of a business process – enables
your users to get relevant information immediately. They can also take action
then and there.

Analytical workspaces leverage embedded PowerBI technology to provide rich,
interactive visuals over F&O data. Using Analytical workspaces is fun and
exciting – it invites your users to explore data.

 

Analytical workspaces can be leveraged for operational Analytics scenarios in 2
ways

-   Use and extend the ready-made analytical workspaces without the need to
    build from scratch

-   Built your own PowerBI based analytical reports

 

See the section below

<https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/embed-power-bi-workspaces?toc=/dynamics365/commerce/toc.json>

 

BYOD
----

Bring your Own Database (BYOD) is a service that enables, customers to extract
data from F&O into their own data warehouses. BYOD is recommended when you need
to combine data from F&O with other systems as well as with reporting with
legacy data.

 

See more on BYOD here:
<https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/export-entities-to-your-own-database>

 

Azure data lake combines BYOD and Entity store
----------------------------------------------

Customers use a combination of Analytical workspaces (based on Entity store) as
well as BYOD for different scenarios.

<to do: add the image \EntityStore-or-BYOD-PPT>

![](media/642f61ee6087e2ccda71d7ad90e64005.png)

Azure Data Lake combines both these services into a single service that offers "best of both worlds" as follows
 
•	Customers can bring their own Azure Data Lake (ie. Azure Data Lake in their own subscription) and integrate with F&O. F&O will leverage your own data lake to store Entity store data and operate Analytical workspaces. Analytical workspaces continue to work as before.
 
•	Entity store (staged in your Azure Data lake), provides a set of simplified (de-normalized) data structures for easier reporting. Now, your users can be given direct access to data best suited for creating their own reports with a tool of their choice.
 
•	As opposed to exporting data (with BYOD), customers can choose the data they want to be staged in the Azure Data Lake. Data feed service (part of F&O services) keeps the data fresh in the Data Lake.
 
•	Customers can bring their own data into the Data Lake to augment the data provided by F&O. This capability enables easy data mash-up scenarios in the Data Lake.
o	Using hundreds of ready-made connectors available in tools such as PowerBI data flows and Azure Data factory, data from many external sources can be easily ingested into the data lake
o	Historical and legacy data (often inherited as a part of transitioning into F&O) can be directly ingested into the Data lake.
o	Data lakes provide options to ingest non-business data - for an example, device data can be easily ingested into the data lake.
 
•	Cloud based services enable both power users as well as developers to consume this data.
 
  
 
  
Common Data Model folders
Data is stored in Azure Data Lake to comply with Common Data Model (CDM) folder standard. This means
•	Data staged ion Azure Data Lake by F&O is organized into a set of folders 
•	CDM folders contain metadata definitions in addition to data files - metadata definitions are kept in model files in accordance with the standard specified by CDM language
•	Presence of metadata (and complying with CDM folder standard) enables Azure and other services to read and transform this data.

CDM folder structure form F&O is shown below

 

For more information on CDM in Azure Data lake see here: https://docs.microsoft.com/en-us/common-data-model/data-lake
 
For an example,
•	You can attach a CDM folder into PowerBI dataflows as a reference Dataflow. You can work with PowerBI data flows and further re-shape the data, or to create PowerBI datasets and reports
•	You can use Azure Data Factory or other data transformation tools to further shape the data
 
Similar to F&O, other services (including CDS), Azure IoT as well as a host of third-party tools and service can understand and work with data in CDM folders. The list of services is growing. Following are a few examples

Common Data Service enables exporting data to your own Azure Data Lake
https://powerapps.microsoft.com/en-us/blog/exporting-cds-data-to-azure-data-lake-preview/ 

Power users can transform data in Azure Data Lake using CDS Data Flows. See the following document for more details  
https://docs.microsoft.com/en-us/common-data-model/data-lake





 

