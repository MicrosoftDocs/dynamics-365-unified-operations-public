---
# required metadata

title: Reverse report as finished with marking creates an open transaction with the quantity reversed having the same inventory dimensions of the transaction reversed
description: Reverse report as finished with marking creates an open transaction with the quantity reversed having the same inventory dimensions of the transaction reversed
author: SmithaNataraj
manager: tfehr
ms.date: 4/11/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ProdTable
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

# Reverse report as finished with marking creates an open transaction with the quantity reversed having the same inventory dimensions of the transaction reversed

KB Number: 4612469

Reverse report as finished with marking createsan open transaction with the quantity reversed having the same inventorydimensions of the transaction reversed


## Resolution
This works as expected.

When reversing the report as finished, the inventory dimension is initialized from production journal, so it gets the batch number. The sales order transactions will inherit the batch number due to marking.

This is not a blocking issue. As the dimension can be reset when posting RAF.




