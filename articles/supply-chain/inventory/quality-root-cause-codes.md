---
title: Nonconformance root cause codes
description: Learn how to manage nonconformance root cause codes for root causes that are associated with corrections for nonconformance issues that are often encountered at your company.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: QMSInventTestRootCause
ms.topic: how-to
ms.date: 04/25/2025
ms.custom: 
  - bap-template
---

# Nonconformance root cause codes

[!include [banner](../../includes/banner.md)]

Use *nonconformance root cause codes* to establish standard codes for root causes that are associated with corrections for nonconformance issues that are often encountered at your company. For example, you might create codes for wind damage, water damage, training issues, or other common issues that you encounter. Root cause code give you a consistent way to identify causes that you can apply to the relevant corrective actions.

## Prerequisites

Before you can use the features that are described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.44 or later.
- The feature that is named *Advanced quality management* must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Manage root cause codes

1. Go to **Inventory management** \> **Setup** \> **Quality management** \> **Correction root cause codes**.
1. Use the buttons on the Action Pane to add new root cause codes or edit existing ones. (You can also delete existing codes.)
1. Set the following fields for each row:

    - **Root cause code** – Enter a unique ID or name for the root cause code.
    - **Description** – Enter a short description of the root cause code.

## Assign a root cause code to a nonconformance correction

You can assign a root cause code to each correction that you create for a nonconformance. Learn more in [Create and process nonconformances](tasks/create-process-non-conformance.md).
