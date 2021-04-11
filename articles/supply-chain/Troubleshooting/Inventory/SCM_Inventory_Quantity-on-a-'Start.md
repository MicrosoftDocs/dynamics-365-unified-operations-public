---
# required metadata

title: Quantity on a 'Started' Quarantine Order does not update when the order is 'Split'.
description: Quantity on a 'Started' Quarantine Order does not update when the order is 'Split'.
author: SmithaNataraj
manager: tfehr
ms.date: 4/11/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: InventQuarantineOrder
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
submittedBy: shawan@microsoft.com

---

# Quantity on a 'Started' Quarantine Order does not update when the order is 'Split'.

KB Number: 4613113

When customer istrying to create a quarantine order and trying to split the order the orderquantity is not getting updated to the split remaining quantity.



## Resolution
This works well. We don't change original qty from quarantine order and make sure customer can track the original qty is created for this quarantine order. But we have a field QuantityThatHasSplitIntoOtherQuarantineOrders in the back end to track how many qty is split from this quarantine order and this field is not visible in user interface.


