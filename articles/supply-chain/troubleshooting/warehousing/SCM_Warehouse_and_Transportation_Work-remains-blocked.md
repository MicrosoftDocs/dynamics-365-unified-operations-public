---
# required metadata

title: Work remains blocked
description: Work remains blocked
author: SmithaNataraj
manager: tfehr
ms.date: 3/24/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: WHSWorkTableListPage_WHSWorkUnblocking
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

# Work remains blocked

Error code: WHSWorkBlockingExecutingWaveReason_ErrorMessage

The system displays the following error message:

> Work %1 remains blocked because the related wave %2 has status %3.

## Symptoms
The work is currently being processed on a wave and can't be unblocked. See one of the following symptoms:
- On the **Blocking reasons** tab, the **Work blocking reason** is set to *Processing wave* one of the lines.
- On the Action Pane, open the **Related information** and, from the **Related information** group, select **Wave**. The **Wave status** is set to *Processing*.




## Resolution
On the Action Pane, open the **Related information** and, from the **Related information** group, select **Wave**. On Action Pane of the **Waves** page, open the **Wave ** tab and, from the **Wave** group, select **Cleanup wave data**.

## Workaround
If the previous steps didn't resolve the issue, you can cancel the work using the following steps:
1. Go to **Warehouse management \> Periodic tasks \> Clean up \> Cancel work**.
1. In the **Work ID** field, specify the work ID that you want to cancel, and which currently has a **Work status** of *Open*, *In progress*, *Cancelled*, *Combined* or *Closed*.
1. Select **OK**.
1. Select **Yes** to confirm that you want to cancel the work.
More information: Cancel warehouse work for exception handling
