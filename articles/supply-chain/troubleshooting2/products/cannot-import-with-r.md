---
# required metadata

title: Cannot import with Released products V2 entity
description: Cannot import with Released products V2 entity
author: SmithaNataraj
manager: tfehr
ms.date: 4/11/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: EcoResProductDetailsExtended, DataManagementWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
submittedBy: myvakalo@microsoft.com

---

# Cannot import with Released products V2 entity

KB Number: 4611825

When trying to import an item using the Released Products V2 entity, it is giving error message: Cannot create a record in Items - tracking dimension groups (EcoResTrackingDimensionGroupItem). Item number: 2040663, Batch. The record already exists.
 


## Resolution
In order to import new released products, the released product creation V2 entity must be used. The released products V2 entity must not be used.  


