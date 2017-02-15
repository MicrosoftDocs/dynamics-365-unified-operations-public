---
# required metadata

title: Data management and integration using data entities
description: This article provides a brief overview of the mechanics of synchronous and asynchronous integration.
author: RobinARH
manager: AnnBe
ms.date: 2015-12-13 00 - 15 - 10
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: RobinARH
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 26441
ms.assetid: 1753751f-ab0a-45ef-b4b9-065f216bb0fb
ms.search.region: Global
# ms.search.industry: 
ms.author: kuntalme
ms.dyn365.intro: Feb-16
ms.dyn365.version: AX 7.0.0

---

# Data management and integration using data entities

This article provides a brief overview of the mechanics of synchronous and asynchronous integration.

Synchronous services
--------------------

Synchronous integrations are relatively straightforward. Any entity that has **Is public** enabled is automatically available as a service application programming interface (API) in the following URL: https://\[BaseURL\]/Data/&lt;&lt;Data Entity Public Collection Name&gt;&gt; Currently, OData protocol is used to expose endpoints where all public-enabled entities can be interacted with. **Supported protocol:** OData V4.0 **Data format:** JSON **Metadata URL:** https://\[BaseURL\]/Data/$metadata

## Data import/export and recurring integration scenarios
Integration through the data management platform provides more capabilities and higher throughput for inserting/extracting data through entities. Typically, data goes through three phases in this integration scenario:

-   **Source **– These are inbound data files or messages in the queue. Typical data formats include CSV, XML, and tab-delimited.
-   **Staging **– These are automatically generated tables that map very closely to the data entity. When **Data management enabled** is **true**, staging tables are generated to provide intermediary storage. This enables the framework to do high-volume file parsing, transformation, and some validations.
-   **Target **– This is the data entity where data will be imported.

The following diagram shows an inbound flow. [![Inbound flow](./media/over6-1024x464.png)](./media/over6.png)

