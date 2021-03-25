---
# required metadata

title: You cannot cancel work that is on a user
description: You cannot cancel work that is on a user
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

# You cannot cancel work that is on a user

Error code: WAX708

The system displays the following error message:

> You cannot cancel work that is on a user.

## Symptoms
The work is locked by a user and can't be canceled.
On the **General** tab, **Work status** is set to *In progress*, and the **Locked by** is set to a User ID.




## Resolution
To cancel the work, use the following steps:
1. Go to **Warehouse management \> Periodic tasks \> Clean up \> Cancel work**.
1. In the **Work ID** field, specify the work ID that you want to cancel.
1. Select **OK**.
1. Select **Yes** to confirm that you want to cancel the work.

More information: Cancel warehouse work for exception handling



