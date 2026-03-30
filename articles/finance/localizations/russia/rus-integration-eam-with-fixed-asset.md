---
title: Integration of the asset management module with the fixed asset (Russia) module
description: Learn how to work with the the fixed asset module for Russia after integration with the asset management module in Microsoft Dynamics 365 Finance.
author: evgenypopov
ms.author: evgenypopov
ms.topic: overview
ms.custom: 
  - bap-template
ms.date: 08/22/2025
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2022-01-27
---

# Integration of the asset management module with the fixed asset (Russia) module

[!include [banner](../../includes/banner.md)]

This article explains how to work with the the fixed asset module for Russia after integration with the asset management module in Microsoft Dynamics 365 Finance.

Manufacturers and some distributors invest in and operate assets that help them perform necessary product transformations that add value to the supply chain that they are part of. In Microsoft Dynamics 365 Finance version 10.0.25, substantial additions were made to support various types of maintenance, such as predictive, corrective, condition, and preventive maintenance. These additions also enable asset-sensitive operations to enroll the base application without requiring investment in additional solutions.

The **Asset management** module has been integrated with the **Fixed asset (Russia)** module. This integration provides new functionality that lets you perform the following tasks:

- Relate an asset to a Russian fixed asset.
- Create an asset, and view the asset and costs that are related to the fixed asset from the Russian fixed asset record.

To relate an asset to a Russian fixed asset, follow these steps:

1. In Dynamics 365 Finance, go to **Asset management** \> **Assets** \> **All assets**.
1. Select the asset record, and then, on the **Fixed asset** FastTab, in the **Fixed asset (Russia)** section, select the fixed asset.

You can create an asset directly from a Russian fixed asset. In this case, the system automatically relates the new asset to the fixed asset.

To create an asset directly from a Russian fixed asset, follow these steps:

1. In Dynamics 365 Finance, go to **Fixed asset (Russia)** \> **Common** \> **Fixed assets**.
1. Select the fixed asset record, and then, on the Action Pane, on the **Assets management** tab, select **Create maintenance asset**. 

You can open the asset that's related to the Russian fixed asset from a Russian fixed asset record. In this way, you can track the asset cost.

To open the asset that's related to the Russian fixed asset from a Russian fixed asset record, follow these steps:

1. In Dynamics 365 Finance, go to **Fixed asset (Russia)** \> **Common** \> **Fixed assets**.
1. Select the fixed asset record, and then, on the Action Pane, on the **Assets management** tab, select **Maintenance asset** or **Maintenance cost**. 

> [!NOTE]
> When you create a work order, if the investment type is from an asset that is related to a Russian fixed asset, the system doesn't set that fixed asset in the project that is created. Integration of the Fixed asset (Russia) module with the Project management and accounting module is out of scope.

## Additional resources

[Asset management overview](../../../supply-chain/asset-management/index.md)

[Functional locations and assets](../../../supply-chain/asset-management/overview/functional-locations-and-objects.md)

[Functional locations and assets](../../../supply-chain/asset-management/overview/objects-and-work-orders.md)




[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
