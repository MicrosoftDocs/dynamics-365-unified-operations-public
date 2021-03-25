---
# required metadata

title: The last closed work line must be a Put
description: The last closed work line must be a Put
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

# The last closed work line must be a Put

Error code: WAX1285

The system displays the following error message:

> The last closed work line must be a Put.

## Symptoms
The work can’t be canceled in current state.
The last work line that has **Work status** set to *Closed*, do not have **Work type** set to *Put*.




## Resolution
To cancel the work, use the following steps:
1. Go to **Warehouse management \> Periodic tasks \> Clean up \> Cancel work**.
1. In the **Work ID** field, specify the work ID that you want to cancel.
1. Select **OK**.
1. Select **Yes** to confirm that you want to cancel the work.

More information: Cancel warehouse work for exception handling



