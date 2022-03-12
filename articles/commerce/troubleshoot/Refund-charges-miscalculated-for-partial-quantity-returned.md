---
# required metadata

title: Refundable charges are not calculated based on the quantity returned
description: This topic provides troubleshooting guidance that can help when customer do not see the refundable charges based on the quantity returned in POS.
author: [gvrmohanreddy]
manager: jeffbl
ms.date: 03/10/2022
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 
# optional metadata
# ms.search.form:  
#ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: gmohanv
ms.search.validFrom: 2022-03-10
ms.dyn365.ops.version: 10.0.26
---

# Refundable charges are not calculated based on the quantity returned

[!include [banner](../../includes/banner.md)]

This topic provides troubleshooting guidance that can help when customer do not see the refundable charges based on the quantity returned in POS.

## Description

When a sales order has line-level refundable charges e.g. $5 per item and total charges are $25 for 5 quantity, and returned only for partial quantity e.g. 3 out of 5 quantity returned, entire charges are showed as refundable. In this example cashier sees $25 as refundable charge, instead of $15 based on 3 quantity returned. 

## Resolution

### Enable refunding charges based on the refunded quantity
Starting from Dynamics 365 Commerce version 10.0.26, a change is made to calculate the line-level refundable charges based on the quantity returned.  Follow below steps to enable this feature.



1. Go to **System administrator \> Workspaces\> Feature management **.
1. Under  **All** find **Enable refunding charges based on the refunded quantity** and click **Enable**. 

## Additional resources

[Setup an email notification profile](../omni-auto-charges)

