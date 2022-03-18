--- 
# required metadata 
 
title: Create a new product
description: This topic describes how to create a new shared product. 
author: t-benebo
ms.date: 07/22/2019
ms.topic: business-process 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: EcoResProductListPage, EcoResProductCreate, EcoResProductDetails, EcoResProductInventoryDimensionGroups   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: benebotg
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create a new product

[!include [banner](../../includes/banner.md)]

This topic describes how to create a new shared product. It is usually carried out by a product designer. The demo data company used to create this task is USMF.


## Create a product
1. In the Navigation pane, go to **Modules > Product information management > Products > Products**.
2. Select **New**.
3. In the **Product number** field, type a value. If a number sequence has not been set up for the product number, it must be entered manually.  
4. In the **Product name** field, type a value. The product name defaults to the search name. You can change this if needed.  
5. Select **OK**.

## Set up dimension groups
1. Select **Dimension groups** to open the drop dialog.
2. In the **Storage dimension group** field, enter or select a value. The storage dimension group determines which storage dimensions you must enter on each transaction for the product and how it will be tracked in inventory.  
3. In the **Tracking dimension group** field, enter or select a value. The tracking dimension group determines which tracking dimensions you must enter for each transaction for the product, and how it will be handled in inventory.  
4. Select **OK**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]