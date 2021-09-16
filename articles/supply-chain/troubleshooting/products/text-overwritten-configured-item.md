--- 
title: Text overwritten when item is configured on sales order line 
description: When a product is configured on a sales order line, modified text is overwritten with standard text. Change the text after you configure the line, not before. 
author: SmithaNataraj 
ms.date: 06/24/2021 
ms.topic: troubleshooting 
# ms.search.form: 
audience: Application User 
ms.reviewer: kamaybac 
ms.search.region: Global 
ms.author: smnatara 
ms.search.validFrom: 2021-06-24 
ms.dyn365.ops.version: 10.0.20 
--- 

# Item text is overwritten when a product is configured on a sales order line

## Symptoms

This issue occurs when you create a sales order line for a configurable item and then modify the item text. When you configure the item and select **OK**, the text is overwritten with the standard text.

## Resolution

This behavior is expected. The text field includes the variant name, which is filled in only after you configure the line. Therefore, you must change the text after you've configured the line, not before.
