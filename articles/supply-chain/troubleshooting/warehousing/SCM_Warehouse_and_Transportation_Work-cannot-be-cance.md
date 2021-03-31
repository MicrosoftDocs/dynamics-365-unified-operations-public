---
title: Work can't be canceled because of status
description: Work can't be canceled because of status
author: SmithaNataraj
manager: tfehr
ms.date: 3/24/2021
ms.topic: troubleshooting
ms.search.form: WHSWorkTable_WHSWorkCancel
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: smnatara
ms.search.validFrom: 2021-03-24
ms.dyn365.ops.version: 10.0.18
---

# Work can't be canceled because of status

Error code: WAX2190

The system displays the following error message:

> You cannot cancel work %1 because it has a status of %2.

## Issue description

The work can't be canceled in its current state.

The work header or work lines do not have the expected **Work status**. The work header **Work status** is not set to *Open* or *In progress*.

## Resolution

To cancel the work, use the following steps:

1. Go to **Warehouse management \> Periodic tasks \> Clean up \> Cancel work**.
1. In the **Work ID** field, specify the work ID that you want to cancel.
1. Select **OK**.
1. Select **Yes** to confirm that you want to cancel the work.

For more information, see [Cancel warehouse work for exception handling](../../warehousing/cancel-warehouse-work.md)
