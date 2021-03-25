---
# required metadata

title: Work cannot be cancelled because it is blocked
description: Work cannot be cancelled because it is blocked
author: SmithaNataraj
manager: tfehr
ms.date: 3/24/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: WHSWorkTable_WHSWorkCancel
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
submittedBy: hja@microsoft.com

---

# Work cannot be cancelled because it is blocked

Error code: WHSCancellationOfWorkBlockedByExecutingWave_ErrorMessage

The system displays the following error message:

> Work %1 cannot be cancelled because it is blocked by reason type %2. The work must be unblocked before it can be cancelled.

## Symptoms
The work is blocked and can't be canceled.
On the **Work** page, on the **General** tab, **Blocked** is set to *Yes*, which means the work is blocked.
The **Blocking reasons** tab shows why it was blocked.




## Resolution
To unblock the work, go to the **Blocking reasons** tab and do one of the following:
- If the **Work blocking reason** is set to *Undefined reason* then you can unblock the work. On the Action Pane, open the **Work** tab and, from the **Work** group, select **Unblock work**.
- If the **Work blocking reason** is set to *Processing wave* then, on the Action Pane, open the **Related information** and, from the **Related information** group, select **Wave**. On Action Pane of the **Waves** page, open the **Wave ** tab and, from the **Wave** group, select **Cleanup wave data**.

## Workaround
If the previous steps didn't resolve the issue, you can cancel the work using the following steps:
1. Go to **Warehouse management \> Periodic tasks \> Clean up \> Cancel work**.
1. In the **Work ID** field, specify the work ID that you want to cancel, and which currently has a **Work status** of *Open*, *In progress*, *Cancelled*, *Combined* or *Closed*.
1. Select **OK**.
1. Select **Yes** to confirm that you want to cancel the work.
More information: Cancel warehouse work for exception handling
