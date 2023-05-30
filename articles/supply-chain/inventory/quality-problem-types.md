---
# required metadata

title: Problem types for nonconformances
description: This article describes how to create and use problem types for nonconformances.
author: yufeihuang
ms.date: 03/23/2021
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

ms.search.form: InventProblemType, InventProblemTypeSetup
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: kamaybac
# ms.tgt_pltfrm:
ms.assetid: a1d9417b-268f-4334-8ab6-8499d6c3acf0
ms.search.region: Global
ms.search.industry: Distribution
ms.author: yufeihuang
ms.search.validFrom: 2020-06-17
ms.dyn365.ops.version: AX 7.0.0

---

# Problem types for nonconformances

[!include [banner](../includes/banner.md)]

This article describes how to create and use problem types for nonconformances.

You use the **Problem types** page to define a classification of the quality problems that might occur for the various nonconformance types. For each problem type that you create, you must specify the types of nonconformances that the problem type can be used with. You can set up the following nonconformance types:

- **Internal** – Nonconformances of this type are related to on-hand inventory (for example, quality orders or quarantine orders).
- **Customer** – Nonconformances of this type are related to sales orders.
- **Vendor** – Nonconformances of this type are related to purchase orders.
- **Service request** – Nonconformances of this type are related to service orders.
- **Production** – Nonconformances of this type are related to batch orders or production orders.
- **Co-product production** – Nonconformances of this type are related to batch orders for co-products.

When you create a new problem type, select **Non conformance types** on the Action Pane to create a list of one or more nonconformance types that are authorized for the problem type. For example, a problem type that is related to a defect code might apply to all nonconformance types. However, a problem type that is related to customer complaints might apply only to the **Customer** and **Service request** nonconformance types.

## Examples of problem types

Here are some examples of scenarios for problem types that can be used with the different nonconformance types:

- **Customer:** A customer filed a complaint, a customer made a return, or quality specifications weren't met.
- **Vendor:** The product was damaged, quality specifications weren't met, or the wrong product was received.
- **Service request:** Quality specifications weren't met, a customer filed a complaint, or machine maintenance is required.
- **Production:** Quality specifications weren't met, machine maintenance is required, or the product was damaged.
- **Co-product production:** Quality specifications weren't met, machine maintenance is required, or the product was damaged.

## Create a problem type and assign it to nonconformance types

1. Go to **Inventory management \> Setup \> Quality management \> Problem types**.
1. On the Action Pane, select **New** to add a row to the grid. Then set the following fields for the new row:

    - **Problem type** – Enter a unique ID or name for the problem type.
    - **Description** – Enter a detailed description of the problem type.

1. While the new row is still selected, select **Non conformance types** on the Action Pane.
1. On the Action Pane, select **New** to add a row to the grid. Then, for the new row, set the **Non conformance type** field to the nonconformance type that you want to allow for the problem type.
1. Repeat the previous step for each additional nonconformance type that you want to authorize for the problem type.
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
