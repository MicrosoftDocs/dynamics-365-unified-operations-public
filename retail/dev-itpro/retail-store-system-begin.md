---
# required metadata

title: Retail Store Scale Unit overview
description: This topic describes the Retail Store Scale Unit and when to use it.
author: MargoC
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
# ms.reviewer: robinr
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 219714
ms.assetid: 773fb32d-14c1-4dc8-8330-0332c6a037a2
ms.search.region: Global
ms.search.industry: Retail
ms.author: athinesh
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Retail Store Scale Unit overview

[!include[banner](../includes/banner.md)]


This topic describes the Retail Store Scale Unit and when to use it.

Overview
--------

Retail Store Scale Unit is a set of features that supports selling products in a store that does not have constant Internet connectivity to a back office or headquarters (HQ). The Store Scale Unit is designed specifically for in-store operation, and enables cross terminal transactions and shift operations even when you are not connected to the back office. By automatically connecting to the back office, when you do have Internet connectivity, your store can process credit card transactions, issue gift cards, and sync data with HQ seamlessly. The Store Scale Unit is available for download in the standard HQ deployment.

## Is the Retail Store Scale Unit right for you?
Before you begin setting up Store Scale Unit, take a moment determine whether this option is the right fit for your store. Store Scale Unit is a deployment choice intended for retailers with store locations that have slow or intermittent Internet connectivity, who need the flexibility of the Store Scale Unit deployed on premise in each store. If you have a stable Internet connection you should consider operating your store as Cloud only, without setting up a Store Scale Unit. Consider the following before you begin:

-   You only have one opportunity to set up a store as a Store Scale Unit or a Cloud-only system. Moving from a Store Scale Unit-enabled store to a Cloud-Only store is not supported by default, and will require manual configuration.
-   Store Scale Unit will support both MPOS and Cloud POS within the store.
-   Store Scale Unit can be set up in a one-box deployment topology on a single computer (recommended) or in a multi-box topology on different computers.
-   If you choose the one-box Store Scale Unit option, most of the settings are pre-configured. For a multi-box topology you will have to manually configure connections between components.
-   In Store Scale Unit, users can perform cross-terminal scenarios across multiple POS devices, like suspend/recall transactions and shift operations.
-   In Store Scale Unit, users cannot perform any real time operations such as issuing gift cards, looking up products, or performing credit card transactions, unless there is Internet connectivity to HQ or a payment provider. If the majority of your transactions involve real time transactions, then your Store Scale Unit will always need Internet connectivity to enable the connection to HQ or payment provider.
-   Direct database connectivity from POS to the channel database is not supported in the Store Scale Unit. The POS devices in the Store Scale Unit will always use the Retail Server for performing operations. You will need customization to enable direct database connectivity and bypass Retail Server.

Get started with Store Scale Unit
=================================

To get started, review the following topic on configuring the Store Scale Unit, [Retail Store Scale Unit configuration and installation](retail-store-scale-unit-configuration-installation.md).

See also
--------

[Retail Store Scale Unit download and configuration through self-service](retail-store-scale-unit-configuration-installation.md)



