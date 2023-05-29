---
# required metadata

title: Charges for nonconformance operations
description: This article describes how to create quality charges that can be used with operations for a nonconformance.
author: yufeihuang
ms.date: 03/23/2021
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

ms.search.form: InventTestMiscCharges
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

# Charges for nonconformance operations

[!include [banner](../includes/banner.md)]

This article describes how to create quality charges that can be used with operations for a nonconformance.

You use the **Quality charges** page to define the types of charges that can be added to operations for a nonconformance. Charges let you track details about fees or charges that you owe to a customer for nonconforming products, or that a vendor owes to you for nonconforming products that you received. You might also use charges to track costs that are required for external vendors or services to perform an operation.

## Examples of quality charges

You work for a manufacturing company. Your company has contracts with several vendors. Those contracts outline standards for on-time shipment, damages, and product quality for items. Likewise, several of your customers have agreements with your company about returns, damages, and product quality.

A fee structure is defined for each circumstance and specified in the contract. You can configure quality charges to outline the various types of charges, such as *Damages*, *Late shipment*, and *Quality*. Then, when you create a nonconformance, you add one or more operations. For each operation, you select **Charges** to define the details about the fees.

## Create a quality charge

1. Go to **Inventory management \> Setup \> Quality management \> Quality charges**.
1. On the Action Pane, select **New** to add a row to the grid. Then set the following fields for the new row:

    - **Charges code** – Enter a unique ID or name for the quality charge.
    - **Description** – Enter a detailed description of the quality charge.

1. Close the page.

## Add a quality charge to an operation for a nonconformance

For details about how to add operations to a nonconformance and apply charges to them, see [Operations for nonconformances](quality-operations.md).

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
