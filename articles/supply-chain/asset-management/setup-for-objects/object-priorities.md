---
title: Asset service levels
description: Learn about asset service levels in Asset Management, including examples and a step-by-step process on setting up asset service levels.
author: johanhoffmann
ms.author: johanho
ms.topic: article
ms.date: 06/26/2019
ms.reviewer: kamaybac
ms.search.form: 
ms.assetid: 2f3e0441-414d-402b-b28b-7ab0d650d658
---

# Asset service levels

[!include [banner](../../includes/banner.md)]

 

This article explains asset service levels in Asset Management. Asset service levels are related to assets, and are transferred to maintenance requests and work orders. They are used to calculate the priority of work orders during work order scheduling. Asset service levels can be changed, if changes are required.

For more information about the setup that is related to the calculation of rating scores for work order scheduling, see [Asset Management parameters](../setup-for-objects/enterprise-asset-management-parameters.md). You must set up at least one default record for the asset service level. This default record is used if no other match is found during work order scheduling.

**Example 1:** The default service level that is used if no other match is found. In this record, you select only a service level.

**Example 2:** A high service level that is used to schedule jobs for a Volvo truck engine. In this record, you select a relevant asset type (such as **Truck Engine**), a manufacturer (**Volvo**), and a service level.

## Set up asset service levels

1. Select **Asset management** \> **Setup** \> **Asset service levels**.
2. Select **New** to create a record.
3. Depending on the detail level that is required for the asset service level, make relevant selections in the **Functional location**, **Asset type**, **Manufacturer**, **Model**, **Asset**, **Work order type**, and **Service level** fields.

    > [!NOTE]
    > When the asset service level is used for maintenance requests and work orders, Asset Management goes through all asset service level records to check for a possible match. It always checks the most specific combination first. In other words, Asset Management first checks for a match for the **Work order type** field. If no match is found, it checks for a match for the **Asset** field, and so on. As you can see in the layout of the **Asset service levels** page, this behavior means that, to find the most specific combination, Asset Management checks each record from right to left for a match. If no match is found, the default record that has no selections in those fields is used.

4. In the **Service level** field, select a number that indicates the service level (priority).


> [!NOTE]
> If you change an asset service level record on the **Asset service levels** page after you've already used it on a work order, the service level on maintenance requests and work orders isn't updated accordingly.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]