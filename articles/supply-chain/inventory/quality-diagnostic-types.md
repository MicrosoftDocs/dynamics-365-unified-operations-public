---
# required metadata

title: Diagnostic types for nonconformances
description: This topic describes how to use and create diagnostic types for use with nonconformances.
author: rachel-profitt
manager: tfehr
ms.date: 03/23/2021
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata

ms.search.form: InventTestDiagnosticType, InventTestCorrection
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

# Diagnostic types for nonconformances

[!include [banner](../includes/banner.md)]

This topic describes how to use and create diagnostic types for use with nonconformances.

Use the **Diagnostic types** page to define a classification of diagnostic actions. You select a **Diagnostic** when you create a correction for a nonconformance. A correction specifies what type of diagnostic action should be taken for an approved nonconformance, and who should take that action. It also specifies the requested completion date and the planned completion date.

## Examples of diagnostic types

You work for a manufacturing company and several items have failed quality tests. The items are moved into a quarantine area and marked as nonconforming products. A nonconformance record is created in Dynamics 365 Supply Chain Management to track the details through the issue resolution. It is found that bearings in the machine that packages the items have gone bad and are overheating, which is causing the quality issues. The correction for this problem is to replace the parts on the machine. When you configure the diagnostic types, you could create multiple records to represent each type of possible problem with the machine or you could create one generic diagnostic type to represent machine repair.

## Create a diagnostic type

1. Go to **Inventory management >  Setup > Quality management > Diagnostic types**.
1. On the Action pane, select **New** to add a new row to the grid, and then make the following settings for it:
    - **Diagnostic** - Enter a unique ID or name for the diagnostic type.
    - **Description** - Enter a detailed description for the diagnostic type.
1. Close the page.

## Additional resources

- [Quality management overview](quality-management-processes.md)
- [Nonconformance management](enable-nonconformance-management.md)
- [Workers responsible for approving nonconformances](quality-responsible-workers.md)
- [Quarantine zones for nonconformances](quality-quarantine-zones.md)
- [Problem types for nonconformances](quality-problem-types.md)
- [Quality charges for nonconformances](quality-charges.md)
- [Operations for nonconformances](quality-operations.md)
- [Quality management for warehouse processes](quality-management-for-warehouses-processes.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]