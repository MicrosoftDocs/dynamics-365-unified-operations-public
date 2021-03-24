---
# required metadata

title: Problem types for nonconformances
description: This topic describes how to create and use problem types for nonconformances.
author: rachel-profitt
manager: tfehr
ms.date: 03/23/2021
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata

ms.search.form: InventProblemType, InventProblemTypeSetup
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: kamaybac
# ms.tgt_pltfrm:
ms.custom: 94003
ms.assetid: a1d9417b-268f-4334-8ab6-8499d6c3acf0
ms.search.region: Global
ms.search.industry: Distribution
ms.author: raprofit
ms.search.validFrom: 2020-06-17
ms.dyn365.ops.version: AX 7.0.0

---

# Problem types for nonconformances

[!include [banner](../includes/banner.md)]

This topic describes how to create and use problem types for nonconformances.

Use the **Problem types** page to define classifications of quality problems that may occur for the various nonconformance types. For each problem type you create, you must define which types of nonconformances the problem type can be used with. You can set up the following nonconformance types:

- **Internal**: These types of nonconformances are related to inventory that is on-hand, a quality order, or quarantine order (for example).
- **Customer**: These types of nonconformances are related to sales orders.
- **Vendor**: These types of nonconformances are related to purchase orders.
- **Service request**: These types of nonconformances are related to service orders.
- **Production**: These types of nonconformances are related to batch or production orders.
- **Co-product production**: These types of nonconformances are related to batch orders for co-products.

When you create a new **Problem type**, select **Non conformance types** on the Action Pane to create a list of one or more nonconformance types that are authorized for the selected problem type. For example, a problem type that is related to a defect code might apply to all nonconformance types, whereas a problem type that is related to customer complaints might apply only to the **Customer** and **Service request** nonconformance types.

## Examples of problem types

The following list includes examples of each type of nonconformance and possible scenarios for problem types.

- **Customer**: Customer complaint, customer return, quality specifications not met
- **Vendor**: Damaged product, quality specifications not met, wrong product received
- **Service request**: Quality specifications not met, customer complaint, machine maintenance
- **Production**: Quality specifications not met, machine maintenance, damaged product
- **Co-product production**: Quality specifications not met, machine maintenance, damaged product

## Create a problem type and assign it to nonconformance types

1. Go to **Inventory management >  Setup > Quality management > Problem types**.
1. On the Action Pane, select **New** to add a new row to the grid and enter the following settings for it:
    - **Problem type** - Enter a unique ID or name for the problem type.
    - **Description** - Enter a detailed description for the problem type.
1. With the new row still selected, select **Non conformance types** in the Action Pane.
1. On the Action Pane, select **New** to add a new row to the grid.
1. For the new row, set **Non conformance type** to the nonconformance type you want to allow for the problem type.
1. Repeat steps 4-5 for each additional nonconformance type you want to allow for the problem type.
1. Close the pages.

## Additional resources

- [Quality management overview](quality-management-processes.md)
- [Enable quality and nonconformance management](enable-quality-management.md)
- [Workers responsible for approving nonconformances](quality-responsible-workers.md)
- [Quarantine zones for nonconformances](quality-quarantine-zones.md)
- [Diagnostic types for nonconformances](quality-diagnostic-types.md)
- [Quality charges for nonconformances](quality-charges.md)
- [Operations for nonconformances](quality-operations.md)
- [Quality management for warehouse processes](quality-management-for-warehouses-processes.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]