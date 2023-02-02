---
title: Commerce Scale Unit (self-hosted)
description: This article describes Microsoft Dynamics 365 Commerce Scale Unit (self-hosted) and when to use it.
author: josaw1
ms.date: 02/02/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2016-11-30
ms.custom: 219714
ms.assetid: 773fb32d-14c1-4dc8-8330-0332c6a037a2

---

# Commerce Scale Unit (self-hosted)

[!include [banner](../includes/banner.md)]

This article describes Microsoft Dynamics 365 Commerce Scale Unit (self-hosted) and when to use it.

Commerce Scale Unit (self-hosted) is a set of features that supports selling products in a store that has inconsistent internet connectivity to Commerce headquarters. The Store Scale Unit is designed specifically for in-store operation, and enables cross-terminal transactions and shift operations despite poor internet service. By automatically connecting to the back office, when you do have internet connectivity, your store can seamlessly process credit card transactions, issue gift cards, and sync data with HQ. The Store Scale Unit is available for download in the standard HQ deployment.

## Is Commerce Scale Unit (self-hosted) right for you?

Before you begin setting up Commerce Scale Unit (self-hosted), take a moment determine whether this option is the right fit for your store. Commerce Scale Unit (self-hosted) is a deployment choice intended for retailers with store locations that have slow or intermittent internet connectivity, and who need the flexibility of the Commerce Scale Unit deployed on premises in each store. 
In scenarios where a stable internet connection is available and there is low latency to the cloud environment, then it is recommended to consider operating the store as Cloud only, without setting up a Commerce Scale Unit. Consider the following before you begin:

-   Carefully choose the store topology configuration for each store to either operate with a self-hosted or cloud-hosted Commerce Scale Unit topology. Reconfiguring a live store from a self-hosted to cloud-hosted Commerce Scale Unit or vice versa may cause a service disruption.
-   Commerce Scale Unit will support both the Store Commerce app and Store Commerce for web within the store.
-   Commerce Scale Unit (self-hosted) can be set up in a one-box deployment topology on a single computer (recommended) or in a multi-box topology on different computers.
-   If you choose the one-box option, most of the settings are pre-configured. For a multi-box topology, you will have to manually configure connections between components.
-   With Commerce Scale Unit (self-hosted), users can perform cross-terminal scenarios across multiple POS devices, like suspend/recall transactions and shift operations, even with temporary network disruption to HQ.
-   With Commerce Scale Unit (self-hosted), users cannot perform any real-time operations such as issuing gift cards, looking up products, or performing credit card transactions, unless there is internet connectivity to HQ or a payment provider. If most of your transactions involve real-time transactions, then you will always need internet connectivity to enable the connection to HQ or payment provider.
-   Direct database connectivity from POS to the channel database is not supported in the Commerce Scale Unit. The POS devices always use the Commerce Scale Unit for performing operations.

> [!IMPORTANT]
> Commerce Scale Unit (self-hosted) does not replace offline. Currently, using the Store Commerce app with an offline database is the only way to have offline capabilities. 

## Get started with Commerce Scale Unit (self-hosted)

To get started, review the following article on configuring the Commerce Scale Unit (self-hosted), [Configure and install Commerce Scale Unit (self-hosted)](retail-store-scale-unit-configuration-installation.md).

## Additional resources

[Configure and install Commerce Scale Unit (self-hosted)](retail-store-scale-unit-configuration-installation.md)



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
