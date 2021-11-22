---
title: The last closed work line must be a put
description: The last closed work line must be a put
author: perlynne
ms.date: 04/15/2021
ms.topic: troubleshooting
ms.search.form: WHSWorkTable_WHSWorkCancel, WHSWorkTableListPage_WHSWorkCancel
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: perlynne
ms.search.validFrom: 2021-05-15
ms.dyn365.ops.version: 10.0.18
---
# The last closed work line must be a put

Error code: WAX1285

## Symptoms

The system shows the following error message:

> The last closed work line must be a put.

## Cause

The work can't be canceled in its current state.

On the last work line, the **Work status** field is set to *Closed*, but the **Work type** field isn't set to *Put*.

## Resolution

To cancel the work, follow these steps.

1. Go to **Warehouse management \> Periodic tasks \> Clean up \> Cancel work**.
1. In the **Work ID** field, specify the ID of the work that you want to cancel.
1. Select **OK**.
1. Select **Yes** to confirm that you want to cancel the work.

For more information, see [Cancel warehouse work for exception handling](../../warehousing/cancel-warehouse-work.md).
