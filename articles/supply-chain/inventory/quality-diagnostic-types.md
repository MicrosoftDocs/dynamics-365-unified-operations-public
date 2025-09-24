---
title: Diagnostic types for nonconformances
description: Learn how to use and create diagnostic types that can be used with nonconformances, including examples of diagnostic types.
author: johanhoffmann
ms.author: johanho
ms.topic: article
ms.date: 04/25/2025
ms.reviewer: kamaybac
ms.search.form: InventTestDiagnosticType, InventTestCorrection, QMSInventTestDiagnosticGroup
ms.assetid: a1d9417b-268f-4334-8ab6-8499d6c3acf0
---

# Diagnostic types for nonconformances

[!include [banner](../includes/banner.md)]

This article describes how to use and create diagnostic types that can be used with nonconformances.

*Diagnostic types* define classifications of diagnostic actions. When you create a *correction* for a nonconformance, you select a diagnostic. A correction specifies what type of diagnostic action should be taken for an approved nonconformance and who should take that action. It also specifies the requested completion date and the planned completion date.

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

## Diagnostic groups

Use *diagnostic groups* to collect related diagnostic types so that you can quickly apply them all at once as corrections to a nonconformance. For example, you might create a group of diagnostic types that together describe how to diagnose an issue with raw material quality (such as repair and retest).

### Prerequisites

Before you can use diagnostic groups, your system must meet the following requirements:

- You must be running Supply Chain Management version 10.0.44 or later.
- The feature that is named *Advanced quality management* must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

### Manage diagnostic groups

1. Go to **Inventory management** \> **Setup** \> **Quality management** \> **Diagnostic groups**.
1. Use the buttons on the Action Pane to create a new diagnostic group in the list pane or edit an existing one. (You can also delete existing groups.)
1. On the heading of the new or selected group, enter a name and description for the group.
1. On the **Diagnostic** FastTab, use the buttons on the toolbar to add and remove diagnostics that belong to the current group. For each row, select the diagnostic that should be performed and the worker who should perform it.

## Related information

- [Quality management overview](quality-management-processes.md)
- [Enable quality and nonconformance management](enable-quality-management.md)
- [Workers responsible for approving nonconformances](quality-responsible-workers.md)
- [Quarantine zones for nonconformances](quality-quarantine-zones.md)
- [Problem types for nonconformances](quality-problem-types.md)
- [Quality charges for nonconformances](quality-charges.md)
- [Operations for nonconformances](quality-operations.md)
- [Quality management for warehouse processes](quality-management-for-warehouses-processes.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
