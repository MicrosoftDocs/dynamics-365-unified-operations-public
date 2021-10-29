# required metadata

title: Export to Data Lake overview
description: This topic provides an overview of Microsoft Azure Data Lake.
author: MilindaV2
ms.date: 11/20/2021
ms.topic: article
ms.prod:
ms.technology: 

# optional metadata

# ms.search.form:
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: ["intro-internal", "NotInToc"]
ms.search.region: Global
# ms.search.industry:
ms.author: milindav
ms.search.validFrom: 2020-03-31
ms.dyn365.ops.version: Platform update 34

---

# Export to Data Lake overview

[!include [banner](../includes/banner.md)]

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

## What is Azure Data Lake?
Connect your Dynamics 365 Finance and Operations environment with an Azure Data
Lake and unlock insights hidden in your data.

When you enable Export to Data lake add-in, you will connect Finance and
Operations environment to a designated Azure Data Lake. Authorized users can
copy data from your Finance and Operations environment to your Azure Data Lake.
With Data in the lake, Azure and other services such as PowerBI and Azure
Synapse Analytics enable Analytics, Business intelligence and machine learning
scenarios.

When authorized users choose data in Finance and Operations, the system makes an
initial copy of the data in the lake. After the initial copy, the system keeps
the data in the lake fresh by continuously inserting, updating and deleting data
that changed. There is no need to manage exports or to monitor the service.
There is no additional burden added to your Finance and Operations workloads.

Data is stored in the lake organized in a rich folder structure using Common
Data Model (CDM) format. CDM format provides additional metadata such as table
structure, descriptions and data types in a machine readable JSON format such
that downstream tools understand the semantics of the data.

Export to Data Lake is a fully managed, scalable and highly available service
from Microsoft with built-in disaster recovery. Feature supported include

-   Users can choose up to 200 tables. All changes to data including insert,
    modify and delete operations are continuously updated in the lake

-   Choose Data using Tables or using Entities. When you choose data using
    Entities, underlying tables are chosen by the service

-   Standard as well as custom Entities and tables are supported

-   Work with data in the lake using T-SQL with Synapse SQL Serverless. You can
    integrate data in the lake with Synapse using ready-made solution templates
    here \<…\>

-   The storage account must be in the same Azure region as your Finance and
    Operations environment

Also see preview features below
