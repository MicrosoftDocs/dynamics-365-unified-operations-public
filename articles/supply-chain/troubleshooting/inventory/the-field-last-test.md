---
title: The field ‘last tested date’ is not updated when multiple quality order is created. 
description: The field ‘last tested date’ is not updated when multiple quality order is created. 
author: SmithaNataraj
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: InventBatch
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: smnatara
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# The field ‘last tested date’ is not updated when multiple quality order is created. 

KB Number: 4612803

The field ‘last tested date’ is not updated when multiple quality order is created. 


## Resolution
This works as expected. Last tested date is not driven by quality order, it saves the first date when the finished goods are purchased or manufactured. This date will be used to calculate the shelf life advice day. 


