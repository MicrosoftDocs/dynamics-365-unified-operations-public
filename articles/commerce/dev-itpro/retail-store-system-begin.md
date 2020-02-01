---
# required metadata

title: Commerce Scale Unit
description: This topic describes the Commerce Scale Unit and when to use it.
author: athinesh99
manager: AnnBe
ms.date: 12/17/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 219714
ms.assetid: 773fb32d-14c1-4dc8-8330-0332c6a037a2
ms.search.region: Global
ms.search.industry: Retail
ms.author: athinesh
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Commerce Scale Unit

[!include [banner](../includes/banner.md)]

This topic describes the Commerce Scale Unit and when to use it.

Overview
--------

Commerce Scale Unit is a set of features that supports selling products in a store that have inconsistent internet connectivity to a back office or headquarters (HQ). The Store Scale Unit is designed specifically for in-store operation, and enables cross-terminal transactions and shift operations despite poor internet service. By automatically connecting to the back office, when you do have internet connectivity, your store can seamlessly process credit card transactions, issue gift cards, and sync data with HQ. The Store Scale Unit is available for download in the standard HQ deployment.

## Is the Commerce Scale Unit right for you?
Before you begin setting up Commerce Scale Unit, take a moment determine whether this option is the right fit for your store. Commerce Scale Unit is a deployment choice intended for retailers with store locations that have slow or intermittent internet connectivity, who need the flexibility of the Commerce Scale Unit deployed on premises in each store. 
In scenarios where a stable internet connection is available and there is low latency to the cloud environment, then it is recommended to consider operating the store as Cloud only, without setting up a Commerce Scale Unit. Consider the following before you begin:

-   You only have one opportunity to set up a store as a Store Scale Unit or a Cloud-only system. Moving from a Commerce Scale Unit-enabled store to a Cloud-Only store is not supported by default, and will require manual configuration.
-   Commerce Scale Unit will support both MPOS and Cloud POS within the store.
-   Commerce Scale Unit can be set up in a one-box deployment topology on a single computer (recommended) or in a multi-box topology on different computers.
-   If you choose the one-box option, most of the settings are pre-configured. For a multi-box topology, you will have to manually configure connections between components.
-   In Commerce Scale Unit, users can perform cross-terminal scenarios across multiple POS devices, like suspend/recall transactions and shift operations.
-   In Commerce Scale Unit, users cannot perform any real-time operations such as issuing gift cards, looking up products, or performing credit card transactions, unless there is internet connectivity to HQ or a payment provider. If most of your transactions involve real time transactions, then you will always need internet connectivity to enable the connection to HQ or payment provider.
-   Direct database connectivity from POS to the channel database is not supported in the Commerce Scale Unit. The POS devices will always use the Commerce Scale Unit for performing operations.

> [!NOTE]
> It is critical to note that a Commerce Scale Unit does not replace offline. Currently, Retail Modern POS with an offline database is the only true way to have offline capabilities. 

## Get started with Store Scale Unit

To get started, review the following topic on configuring the Commerce Scale Unit, [Configure and install Retail Store Scale Unit](retail-store-scale-unit-configuration-installation.md).

Additional resources
--------

[Configure and install Retail Store Scale Unit](retail-store-scale-unit-configuration-installation.md)



