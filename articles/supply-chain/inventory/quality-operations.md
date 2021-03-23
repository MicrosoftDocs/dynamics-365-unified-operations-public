---
# required metadata

title: Operations for nonconformances
description: This topic describes how to create and use operations for nonconformances.
author: rachel-profitt
manager: tfehr
ms.date: 03/23/2021
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata

ms.search.form: InventTestOperations, InventTestRelatedOperations
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm:
ms.custom: 94003
ms.assetid: a1d9417b-268f-4334-8ab6-8499d6c3acf0
ms.search.region: Global
ms.search.industry: Distribution
ms.author: raprofit
ms.search.validFrom: 2020-06-17
ms.dyn365.ops.version: AX 7.0.0

---

# Operations for nonconformances

[!include [banner](../includes/banner.md)]

This topic describes how to create and use operations for nonconformances.

You can use the **Operations** page to define classifications of the work that can be performed for an approved nonconformance. When you assign a related operation to a nonconformance, you can provide detailed information, such as information about the associated material, labor hours, and charges that are required in order to perform the operation. This information is used to calculate an estimated cost for the operation. The detailed information and estimated costs are for reference. The related operations for quality differ from the operations that can be defined for a production route.

> [!NOTE]
> Although you can track costs, time, and items that are used in an operation related to a nonconformance, the data entered here is informational only and does not automatically integrate with the general ledger, inventory sub ledger, or time and attendance module.

## Examples of operations

You work for a manufacturing company. A nonconformance was created and approved for items that failed a quality test. A correction was created to indicate the problem was related to a bad bearing on a machine. To replace the bearing and get the production line back up and running, multiple operations or steps must occur and the responsibility for each operation is tracked. For example, the following steps might be required:

1. Stop the production line and perform the clean-out routine.
2. Maintenance personnel replace the bearing.
3. Quality assurance personnel inspect the machine before turning the machine back on.

In this example, three or four operations could be created to represent the work to be done. The following list shows what the operations could be for the provided example:

- Stop the production line.
- Clean out the production line.
- Perform machine maintenance.
- Inspect the machine.

## Create an operation

1. Go to **Modules > Inventory management >  Setup > Quality management > Operations**.
1. On the Action pane, select **New** to add a new row to the grid, and then make the following settings for it:
    - **Operation** - Enter a unique ID or name for the operation.
    - **Description** - Enter a detailed description for the operation.
    - **Type** - If the operation can only be used with nonconformances related to a specific type of order, then select the order type (*Purchase order* or *Sales order*).
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