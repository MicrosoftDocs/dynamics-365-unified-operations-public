---
# required metadata

title: Cumulating customer rebates using item rebate groups fails
description: Cumulating customer rebates using item rebate groups fails
author: SmithaNataraj
manager: tfehr
ms.date: 4/11/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: PdsRebateTableListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
submittedBy: smnatara@microsoft.com

---

# Cumulating customer rebates using item rebate groups fails

KB Number: 4611372

When usingcustomer rebate agreements (type amount) in combination with item rebate groups,rebates are calculated but the cumulation of these calculated rebates fail



## Resolution
This is by design as the item group only group the items that have the same threshold condition.


