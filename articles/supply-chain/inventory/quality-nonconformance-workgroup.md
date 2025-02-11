---
title: Nonconformance work groups (preview)
description:
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 04/25/2025
ms.custom: 
  - bap-template
---

# Nonconformance work groups (preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Use *nonconformance work groups* to establish group names that you can assign to your nonconformance records to make it easier to classify your nonconformances. For example, you might create a group for inspecting receipts and another one for inspecting production output.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.44 or later.
- The feature that is named *(Preview) Advanced quality management* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Manage nonconformance work groups

1. Go to **Inventory management \> Setup \> Quality management \> Non conformance work groups**.
1. Use the buttons on the Action Pane to create, delete, or edit groups in the grid.
1. Make the following settings for each row:
    - **Work group** – Enter a unique ID or name for the work group.
    - **Description** – Enter a short description of the work group.

## Assign a workgroup to a nonconformance

To assign a workgroup to a nonconformance, edit the **Work group** field when you [create or edit a nonconformance](tasks/create-process-non-conformance.md).
