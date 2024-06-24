---
title: Inventory Visibility tips
description: Access a few tips that you should consider when you set up and use the Inventory Visibility Add-in, including tips about Microsoft Entra environments.
author: yufei-huang
ms.author: yufeihuang
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: conceptual
ms.date: 06/24/2024
audience: Application User
ms.custom: 
  - bap-template
---

# Inventory Visibility tips

[!include [banner](../includes/banner.md)]
[!INCLUDE [azure-ad-to-microsoft-entra-id](../../includes/azure-ad-to-microsoft-entra-id.md)]

Here are a few tips that you should consider when you set up and use the Inventory Visibility Add-in:

- If *all* of the following are true for your installation, then you must [fix the mapping issue](../../fin-ops-core/dev-itpro/data-entities/dual-write/lcs-setup.md#linking-mismatch) before installing the Inventory Visibility Add-in.

    - You installed the Inventory Visibility Add-in using Lifecycle Services.
    - Your Dataverse environment wasn't created by Lifecycle Services (for example, because it was created using the Power Platform admin center).
    - Your Dataverse environment is linked to your Supply Chain Management environment.

    See [Linking mismatch](../../fin-ops-core/dev-itpro/data-entities/dual-write/lcs-setup.md#linking-mismatch) for information about how to fix the mapping issue. Once the mapping issue is resolved, you can then proceed to install Inventory Visibility.

- If you have more than one Supply Chain Management environment, create a different Microsoft Entra application for each environment. If you use the same application ID and tenant ID to install the Inventory Visibility Add-in for different environments, a token issue will occur for older environments. Only the latest installation of the Inventory Visibility Add-in will be valid.
- Inventory Visibility isn't currently supported for cloud-hosted environments. It's supported only for Tier-2+ environments.
- The application programming interface (API) allows multiple `SiteID` and `LocationID` values to be specified in each query. The maximum limit is defined by the following equation: `NumOf(SiteID)` &times; `NumOf(LocationID)` &le; 100.
- The `fno` data source is reserved for Supply Chain Management. If your Inventory Visibility Add-in is integrated with a Supply Chain Management environment, we recommend that you not delete configurations that are related to `fno` in the [data source](inventory-visibility-configuration.md#data-source-configuration).
- Inventory Visibility can't change any data for the `fno` data source. The data flow is one-way, which means that all quantity changes for the `fno` data source must come from your Supply Chain Management environment. Therefore, you can't use the API to send on-hand change or reservation requests for the `fno` data source.
- If you add one or more new measures to your Supply Chain Management environment, you should also add them in Inventory Visibility. However, all quantity changes for new measures must come from your Supply Chain Management environment.
- A [partition configuration](inventory-visibility-power-platform.md#data-partition) controls how data is distributed. Operations that are performed inside the same partition provide better performance, at lower cost, than operations that cross partitions. By default, partition configuration is automatically set up and should not be customized.
- Base dimensions that are reserved in a partition configuration (set number *0*) should not be included in other [on-hand index configurations](inventory-visibility-power-platform.md#index).
- Your [on-hand index configuration](inventory-visibility-power-platform.md#index) must include at least one on-hand index in addition to the partition configuration (set number *0*). If you aren't interested in querying specific dimension combinations, you can set up an index that has only one base dimension, `Empty`. Otherwise, queries will fail, and you will receive the following error: "No index hierarchy has been set."
- Data source `@iv` is a predefined data source and the physical measures defined in `@iv` with prefix `@` are predefined measures. These measures are a predefined configuration for the allocation feature and soft reservation feature, so don't change or delete them or you're likely to encounter unexpected errors when using these two features.
- You can add new physical measures to the predefined calculated measure `@iv.@available_to_allocate`, but you must not change its name.
- If you restore a Supply Chain Management database or copy a Dataverse environment, additional steps are required to run Inventory Visibility in your target environment. See [Supply Chain Management Database and Dataverse Movement](inventory-visibility-setup.md#supply-chain-management-database-and-dataverse-movement) for details.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
