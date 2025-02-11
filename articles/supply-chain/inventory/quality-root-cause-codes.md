---
title: Correction root cause codes (preview)
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

# Nonconformance root cause codes (preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Use *nonconformance root cause codes* to establish standard codes for root causes associated with corrections for nonconformance issues that are often applied at your company. For example, you might create codes for wind damage, water damage, training issues, or other common issues that you encounter. By using root cause codes, you'll have a consistent way of identifying causes that you can apply to the relevant corrective actions.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.44 or later.
- The feature that is named *(Preview) Advanced quality management* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Manage root cause codes

1. Go to **Inventory management \> Setup \> Quality management \> Correction root cause codes**.
1. Use the buttons on the Action Pane to create, delete, or edit root cause codes in the grid.
1. Make the following settings for each row:
    - **Root cause code** – Enter a unique ID or name for the root cause code.
    - **Description** – Enter a short description of the root cause code.

## Assign a root cause code to a nonconformance correction

You can assign a root cause code to each correction that you create for a nonconformance. Learn more in [Create and process nonconformances](tasks/create-process-non-conformance.md).
