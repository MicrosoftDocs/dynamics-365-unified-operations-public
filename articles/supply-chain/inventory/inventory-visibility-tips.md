---
title: Inventory Visibility tips
description: This topic provides a few tips to consider when setting up and using the Inventory Visibility Add-in.
author: yufeihuang
ms.date: 08/02/2021
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: yufeihuang
ms.search.validFrom: 2021-08-02
ms.dyn365.ops.version: 10.0.21
---

# Inventory Visibility tips

[!include [banner](../includes/banner.md)]

Here are a few tips to consider when setting up and using the Inventory Visibility Add-in:

- Currently, the Inventory Visibility Add-in only supports Dataverse environments that were created using Lifecycle Services (LCS). If your Dataverse environment was created in some other way (for example, by using the Power Apps admin center), and if it's linked to your Supply Chain Management environment, you must first contact the Inventory Visibility product team at [inventvisibilitysupp@microsoft.com](mailto:inventvisibilitysupp@microsoft.com) and ask them to fix the mapping issue. They will let you know when your environment is ready for you to install Inventory Visibility.

- If you have more than one LCS environment, create a different Azure AD application for each environment. If you use same application ID and tenant ID to install the Inventory Visibility Add-in for different environments, a token issue will occur for older environments. Only the last one that was installed will be valid.

- Inventory Visibility isn't currently supported for cloud-hosted environments. It is only supported for tier-2+ environments.

- The API currently supports querying up to 100 individual items by `ProductID`. Multiple `SiteID` and `LocationID` values can also be specified in each query. The maximum limit is defined as `NumOf(SiteID) * NumOf(LocationID) <= 100`.

- The `fno` data source is reserved for Dynamics 365 Supply Chain Management. If your Inventory Visibility Add-in is integrated with a Supply Chain Management environment, we recommend against deleting configurations related to `fno` in the [data source](inventory-visibility-configuration.md#data-source-configuration)..

- The [partition configuration](inventory-visibility-configuration.md#partition-configuration) currently consists of two base dimensions (`SiteId` and `LocationId`), which indicate how the data is distributed. Operations under the same partition can deliver higher performance at lower cost. The solution is delivered with this default partition configuration already in place, *so you don't have to define it yourself*. Don't customize the default partition configuration because deleting or changing it is likely to result in an unexpected error.

- Base dimensions that are defined in the partition configuration should not be defined in the [product index hierarchy configuration](inventory-visibility-configuration.md##index-configuration)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
