---
# required metadata

title: Importing a sales order record through DMF not picking up auto charges
description: Importing a sales order record through DMF not picking up auto charges
author: SmithaNataraj
manager: tfehr
ms.date: 4/11/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: DataManagement
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
submittedBy: henrikan@microsoft.com

---

# Importing a sales order record through DMF not picking up auto charges

KB Number: 4612088

Importing a sales order record through DMF not picking up auto charges

## Resolution
Microsoft has investigated the reported issue. It is not a bug, but works as intended. I works in this manner.  The data entity has a SkipCreateAutoCharges field. This field controls whether or not auto charges are calculated upon import. In order to have auto charges calculated on import, set the value of the SkipCreateAutoCharges field in the imported file to No. Then auto charges will be calculated.


