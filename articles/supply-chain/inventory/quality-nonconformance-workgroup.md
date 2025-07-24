---
title: Nonconformance work groups (preview)
description: Learn how to use nonconformance work groups to define group names that you can assign to nonconformance records to make your nonconformances easier to classify.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: QMSInventNonConformanceWorkGroup
ms.topic: how-to
ms.date: 04/25/2025
ms.custom: 
  - bap-template
---

# Nonconformance work groups (preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until 10.0.45 GA -->

Use *nonconformance work groups* to define group names that you can assign to nonconformance records to make your nonconformances easier to classify. For example, you might create a group for inspecting receipts and another one for inspecting production output.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Prerequisites

Before you can use the features that are described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.44 or later.
- The feature that is named *Advanced quality management* must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Manage nonconformance work groups

1. Go to **Inventory management** \> **Setup** \> **Quality management** \> **Non conformance work groups**.
1. Use the buttons on the Action Pane to create new nonconformance work groups in the grid or edit existing ones. (You can also delete existing work groups.)
1. Set the following fields for each row:

    - **Work group** – Enter a unique ID or name for the work group.
    - **Description** – Enter a short description of the work group.

## Assign a work group to a nonconformance

To assign a work group to a nonconformance, edit the **Work group** field when you [create or edit a nonconformance](tasks/create-process-non-conformance.md).
