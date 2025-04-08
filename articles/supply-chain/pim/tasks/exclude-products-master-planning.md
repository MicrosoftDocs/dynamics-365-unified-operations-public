--- 
title: Create a product lifecycle state to exclude products from Master planning
description: Learn how to create a new product lifecycle state that excludes the products from Master planning and BOM-level calculation. 
author: sgmsft
ms.author: shwgarg
ms.topic: how-to
ms.date: 12/05/2017
ms.custom: 
ms.reviewer: kamaybac   
ms.search.form:  
---

# Create a product lifecycle state to exclude products from Master planning

[!include [banner](../../includes/banner.md)]

This procedure shows how to create a new product lifecycle state that excludes the products from Master planning and BOM-level calculation.


## Create an obsolete state
1. Go to Product information management > Setup > Product lifecycle state.
2. Click New.
3. In the State field, type a value.
4. Select No in the Is active for planning field.
5. In the Description field, type a value.

## Associate the obsolete state to a released product
1. Close the page.
2. Go to Product information management > Products > Released products.
3. Use the Quick Filter to find records. For example, filter on the Search name field with a value of 'M00'.
4. Click Edit.
5. In the list, mark the selected row.
6. In the Product lifecycle state field, enter or select a value.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]