---
# required metadata

title: Diagnostic types for nonconformances
description: This article describes how to use and create diagnostic types that can be used with nonconformances.
author: yufeihuang
ms.date: 03/23/2021
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

ms.search.form: InventTestDiagnosticType, InventTestCorrection
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

# Diagnostic types for nonconformances

[!include [banner](../includes/banner.md)]

This article describes how to use and create diagnostic types that can be used with nonconformances.

You use the **Diagnostic types** page to define a classification of diagnostic actions. Then, when you create a correction for a nonconformance, you select a diagnostic. A correction specifies what type of diagnostic action should be taken for an approved nonconformance, and who should take that action. It also specifies the requested completion date and the planned completion date.

## Examples of diagnostic types

You work for a manufacturing company, and several items have failed quality tests. Those items are moved into a quarantine area and marked as nonconforming products. A nonconformance record is created in Microsoft Dynamics 365 Supply Chain Management to track the details through issue resolution.

In this case, the quality issues are occurring because bearings in the machine that packages the items have gone bad and are overheating. The correction for this problem is to replace the parts in the machine.

When you configure the diagnostic types, you can create multiple records, each of which represents a different type of problem that the machine might have. Alternatively, you can create one generic diagnostic type that represents machine repair.

## Create a diagnostic type

1. Go to **Inventory management \> Setup \> Quality management \> Diagnostic types**.
1. On the Action Pane, select **New** to add a row to the grid. Then set the following fields for the new row:

    - **Diagnostic** – Enter a unique ID or name for the diagnostic type.
    - **Description** – Enter a detailed description of the diagnostic type.

1. Close the page.

## Additional resources

- [Quality management overview](quality-management-processes.md)
- [Enable quality and nonconformance management](enable-quality-management.md)
- [Workers responsible for approving nonconformances](quality-responsible-workers.md)
- [Quarantine zones for nonconformances](quality-quarantine-zones.md)
- [Problem types for nonconformances](quality-problem-types.md)
- [Quality charges for nonconformances](quality-charges.md)
- [Operations for nonconformances](quality-operations.md)
- [Quality management for warehouse processes](quality-management-for-warehouses-processes.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
