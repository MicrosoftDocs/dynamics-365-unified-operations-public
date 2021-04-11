---
# required metadata

title: Inconsistency in backflushing of warehouse managed raw material when formula item is warehouse managed vs when formula item is not warehouse managed.
description: Inconsistency in backflushing of warehouse managed raw material when formula item is warehouse managed vs when formula item is not warehouse managed.
author: SmithaNataraj
manager: tfehr
ms.date: 4/11/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ProdTableListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
submittedBy: johanho@microsoft.com

---

# Inconsistency in backflushing of warehouse managed raw material when formula item is warehouse managed vs when formula item is not warehouse managed.

KB Number: 4612640

Inconsistency in backflushing of warehouse managed raw material when formula item is warehouse managed vs when formula item is not warehouse managed.


## Resolution
The Microsoft core team has investigated this case and with a by-design resolution. In the current design it is possible to backflush raw materials enabled for the advanced warehouse processes in an un-reserved state. This is not possible for raw materials that are not enabled for the advanced warehouse processes.
We need to run this batch "Automatic release of BOM and formula lines" to update the inventory transaction for formula line with location.


