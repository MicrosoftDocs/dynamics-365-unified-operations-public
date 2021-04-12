---
# required metadata

title: Master planning batch job filter is not working as expected
description: Master planning batch job filter is not working as expected
author: SmithaNataraj
manager: tfehr
ms.date: 4/11/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ReqTransPo
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
submittedBy: ilebedev@microsoft.com

---

# Master planning batch job filter is not working as expected

KB Number: 4612572

Customer is unable torun the master planning as per the provided filter. The filter is not workingwhen the batch job is created as well


## Resolution
The observed behavior is by design as batch job filter is used solely to filter items to include in the planning, after that we run planning for all the coverage groups those filtered items have. Including a particular coverage group in items filter does not affect the planning output once the item actually included in the run.


