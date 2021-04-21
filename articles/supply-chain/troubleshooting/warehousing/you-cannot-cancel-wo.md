---
title: You can't cancel work that is on a user
description: You can't cancel work that is on a user
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

# You can't cancel work that is on a user

Error code: WAX708

The system shows the following error message:

> You cannot cancel work that is on a user.

## Issue description

The work is locked by a user and can't be canceled.

On the **General** tab, the **Work status** field is set to *In progress*, and the **Locked by** field is set to a user ID.

## Resolution

To cancel the work, follow these steps.

1. Go to **Warehouse management \> Periodic tasks \> Clean up \> Cancel work**.
1. In the **Work ID** field, specify the ID of the work that you want to cancel.
1. Select **OK**.
1. Select **Yes** to confirm that you want to cancel the work.

For more information, see [Cancel warehouse work for exception handling](../../warehousing/cancel-warehouse-work.md).
