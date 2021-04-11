---
# required metadata

title: The field ‘last tested date’ is not updated when multiple quality order is created. 
description: The field ‘last tested date’ is not updated when multiple quality order is created. 
author: SmithaNataraj
manager: tfehr
ms.date: 4/11/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: InventBatch
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

# The field ‘last tested date’ is not updated when multiple quality order is created. 

KB Number: 4612803

The field ‘last tested date’ is not updated when multiple quality order is created. 


## Resolution
This works as expected. Last tested date is not driven by quality order, it saves the first date when the finished goods are purchased or manufactured. This date will be used to calculate the shelf life advice day. 


