---
# required metadata

title: Planned orders are getting generated for phantom item after running master planning
description: Planned orders are getting generated for phantom item after running master planning
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
submittedBy: anderso@microsoft.com

---

# Planned orders are getting generated for phantom item after running master planning

KB Number: 4614729

Planned orders are getting generated for phantom item after running master planning


## Resolution
The "Phantom" checkmark on the released product is used to determine what the default line type on the BOM should be. There will still be created planned orders for the item, however they will have the "Directly derived" flag set to true. This means that the planned production order cannot be firmed on its own, it will always be included automatically when the parent production is firmed, and the BOM lines of the planned "phantom" order will be included in the BOM of the parent production.  


