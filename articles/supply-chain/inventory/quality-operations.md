---
# required metadata

title: Operations for nonconformances
description: This article describes how to create and use operations for nonconformances.
author: yufeihuang
ms.date: 03/23/2021
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

ms.search.form: InventTestOperations, InventTestRelatedOperations
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

# Operations for nonconformances

[!include [banner](../includes/banner.md)]

This article describes how to create and use operations for nonconformances.

You can use the **Operations** page to define classifications of the work that can be performed for an approved nonconformance. When you assign a related operation to a nonconformance, you can provide details such as the associated material, labor hours, and charges that are required to do the operation. The system uses this information to calculate an estimated cost for the operation. The detailed information and estimated costs are for reference. The related operations for quality differ from the operations that can be defined for a production route.

> [!NOTE]
> Although you can track costs, time, and the items that are used in an operation that is related to a nonconformance, the data that you enter is only informational. It isn't automatically integrated with the general ledger, inventory subledger, or the **Time and attendance** module.

## Examples of operations

You work for a manufacturing company. A nonconformance was created and approved for items that failed a quality test. A correction was created to indicate that the problem was related to a bad bearing on a machine. Several steps are required to replace the bearing, and the responsibility for each operation is tracked. For example, the following steps might be required:

1. The production line is stopped, and the clean-out routine is performed.
1. Maintenance personnel replace the bearing.
1. Quality assurance personnel inspect the machine before it's turned back on.

For this example, the following operations can be created to represent the work that must be done:

- Stop the production line.
- Clean out the production line.
- Perform machine maintenance.
- Inspect the machine.

## Create an operation

1. Go to **Inventory management \> Setup \> Quality management \> Operations**.
1. On the Action Pane, select **New** to add a row to the grid. Then set the following fields for the new row:

    - **Operation** – Enter a unique ID or name for the operation.
    - **Description** – Enter a detailed description of the operation.
    - **Type** – If the operation can be used only with nonconformances that are related to a specific type of order, select the order type (*Purchase order* or *Sales order*).

1. Close the page.

## Additional resources

- [Quality management overview](quality-management-processes.md)
- [Enable quality and nonconformance management](enable-quality-management.md)
- [Create and process nonconformances](tasks/create-process-non-conformance.md)
- [Workers responsible for approving nonconformances](quality-responsible-workers.md)
- [Quarantine zones for nonconformances](quality-quarantine-zones.md)
- [Diagnostic types for nonconformances](quality-diagnostic-types.md)
- [Quality charges for nonconformances](quality-charges.md)
- [Problem types for nonconformances](quality-operations.md)
- [Quality management for warehouse processes](quality-management-for-warehouses-processes.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
