---
title: Inventory Visibility tips
description: Access a few tips that you should consider when you set up and use the Inventory Visibility Add-in, including tips about Microsoft Entra environments.
author: yufei-huang
ms.author: yufeihuang
ms.search.form: 
ms.topic: conceptual
ms.date: 06/24/2024
ms.custom: 
  - bap-template
---

# Inventory Visibility tips

[!include [banner](../includes/banner.md)]
[!INCLUDE [azure-ad-to-microsoft-entra-id](../../includes/azure-ad-to-microsoft-entra-id.md)]

Here are a few tips that you should consider when you set up and use the Inventory Visibility Add-in:

- Unless you using the [unified developer experience](/power-platform/developer/unified-experience/finance-operations-dev-overview), you should check for linking mismatch warnings in Lifecycle Services before you install Inventory Visibility. To do so, open the details page for your environment in Lifecycle Services and look for a warning that resembles the following example: "Microsoft has detected that your environment is linked via dual-write to a different destination than specified in Power Platform Integration, which isn't recommended." If you see this warning, it's possible that your dual-write environment is linked to a Dataverse instance, but Lifecycle Services isn't set up for Power Platform integration. This linking mismatch can cause unexpected behavior. For information about how to fix this issue, see [Linking mismatch](../../fin-ops-core/dev-itpro/data-entities/dual-write/lcs-setup.md#linking-mismatch). After the linking mismatch is fixed, you can install Inventory Visibility.
- If you have more than one Supply Chain Management environment, create a different Microsoft Entra application for each environment. If you use the same application ID and tenant ID to install the Inventory Visibility Add-in for different environments, a token issue will occur for older environments. Only the latest installation of the Inventory Visibility Add-in will be valid.
- Inventory Visibility isn't currently supported for cloud-hosted environments. It's supported only for Tier-2+ environments.
- The application programming interface (API) allows multiple `SiteID` and `LocationID` values to be specified in each query. The maximum limit is defined by the following equation: `NumOf(SiteID)` &times; `NumOf(LocationID)` &le; 100.
- The `fno` data source is reserved for Supply Chain Management. If your Inventory Visibility Add-in is integrated with a Supply Chain Management environment, we recommend that you not delete configurations that are related to `fno` in the [data source](inventory-visibility-configuration.md#data-source-configuration).
- Inventory Visibility can't change any data for the `fno` data source. The data flow is one-way, which means that all quantity changes for the `fno` data source must come from your Supply Chain Management environment. Therefore, you can't use the API to send on-hand change or reservation requests for the `fno` data source.
- If you add one or more new measures to your Supply Chain Management environment, you should also add them in Inventory Visibility. However, all quantity changes for new measures must come from your Supply Chain Management environment.
- A [partition configuration](inventory-visibility-power-platform.md#data-partition) controls how data is distributed. Operations that are performed inside the same partition provide better performance, at lower cost, than operations that cross partitions. By default, partition configuration is automatically set up and should not be customized.
- Base dimensions that are reserved in a partition configuration (set number *0*) should not be included in other [on-hand index configurations](inventory-visibility-power-platform.md#index).
- Your [on-hand index configuration](inventory-visibility-power-platform.md#index) must include at least one on-hand index in addition to the partition configuration (set number *0*). If you aren't interested in querying specific dimension combinations, you can set up an index that has only one base dimension, `Empty`. Otherwise, queries will fail, and you will receive the following error: "No index hierarchy has been set."
- Data source `@iv` is a predefined data source and the physical measures defined in `@iv` with prefix `@` are predefined measures. These measures are a predefined configuration for the allocation feature and the soft reservation feature. Therefore, don't change or delete them. Otherwise, you're likely to encounter unexpected errors when you use those two features.
- You can add new physical measures to the predefined calculated measure `@iv.@available_to_allocate`, but you must not change its name.
- If you restore a Supply Chain Management database or copy a Dataverse environment, additional steps are required to run Inventory Visibility in your target environment. For details, see [Move data between Supply Chain Management Database and Dataverse](inventory-visibility-setup.md#move-data).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
