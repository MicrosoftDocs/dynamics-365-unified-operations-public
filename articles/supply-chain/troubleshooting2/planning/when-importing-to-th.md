---
# required metadata

title: When importing to the Item coverage V2 entity in certain scenarios when accessing the Item coverage form after import/update, you will receive the error: "Do you want to save your changes before closing?", even though the user made no changes.
description: When importing to the Item coverage V2 entity in certain scenarios when accessing the Item coverage form after import/update, you will receive the error: "Do you want to save your changes before closing?", even though the user made no changes.
author: SmithaNataraj
manager: tfehr
ms.date: 4/11/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: DataManagementWorkspace_
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
submittedBy: angarmas@microsoft.com

---

# When importing to the Item coverage V2 entity in certain scenarios when accessing the Item coverage form after import/update, you will receive the error: "Do you want to save your changes before closing?", even though the user made no changes.

 

When importing to the Item coverage V2 entity in certain scenarios when accessing the Item coverage form after import/update, you will receive the error: "Do you want to save your changes before closing?", even though the user made no changes.
 


## Symptoms





## Resolution
Coverage form has a complex defaulting logic that might lead to the observed message in case there were direct modifications in the database or entity imports before.
To change PRODUCTCOVERAGEGROUPID  through the entity a user needs to set AREGENERALSETTINGSOVERRIDDEN to Yes




