---
# required metadata

title: When customer is trying to select the LOTID field the Batch number which is already entered is vanishing.
description: When customer is trying to select the LOTID field the Batch number which is already entered is vanishing.
author: SmithaNataraj
manager: tfehr
ms.date: 4/11/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ProdJournalTransBOM
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
submittedBy: datra@microsoft.com

---

# When customer is trying to select the LOTID field the Batch number which is already entered is vanishing.

KB Number: 4613107

When customer is trying to select the LOTID field the Batch number which is already entered is vanishing.


## Resolution
This is working as expected. When changing LOT, the whole item context is changed and thus, the batch number is reset.

If the batch number wants to be associated with the LOT, then user has to set the LOT first.


