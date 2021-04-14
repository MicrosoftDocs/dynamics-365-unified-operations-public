---
title: The last closed work line must be a put
description: The last closed work line must be a put
author: SmithaNataraj
manager: tfehr
ms.date: 3/24/2021
ms.topic: troubleshooting
ms.search.form: WHSWorkTable_WHSWorkCancel, WHSWorkTableListPage_WHSWorkCancel
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: smnatara
ms.search.validFrom: 2021-03-24
ms.dyn365.ops.version: 10.0.18
---

# The last closed work line must be a put

Error code: WAX1285

The system displays the following error message:

> The last closed work line must be a put.

## Issue description

The work can't be canceled in current state.

The last work line that has **Work status** set to *Closed* and doesn't have **Work type** set to *Put*.

## Resolution

To cancel the work, do the following steps:

1. Go to **Warehouse management \> Periodic tasks \> Clean up \> Cancel work**.
1. In the **Work ID** field, specify the work ID that you want to cancel.
1. Select **OK**.
1. Select **Yes** to confirm that you want to cancel the work.

For more information, see [Cancel warehouse work for exception handling](../../warehousing/cancel-warehouse-work.md)
