--- 
# required metadata 
 
title: Create batch attributes for a product
description: This procedure shows how to create a batch attribute, assign default value ranges, and include the attribute in a group. 
author: t-benebo
ms.date: 11/14/2016
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: PdsBatchAttrib
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
# Create batch attributes for a product

[!include [banner](../../includes/banner.md)]

This procedure shows how to create a batch attribute, assign default value ranges, and include the attribute in a group. The demo data company used to create this procedure is the USP2 Company.

1. Go to Inventory management > Setup > Batch > Batch attributes.
2. Click New.
3. In the Attribute field, type a value.
4. In the Description field, type a value.
5. In the Attribute type field, select 'Fraction'.
    * This procedure uses the Fraction type to enable decimal values. You can select other attribute types. If you select the Enumeration type, you must enter values in the enumeration list before you can enter a value in the Target field.  
6. In the Minimum field, enter a number.
7. In the Maximum field, enter a number.
8. In the Increment field, enter a number.
9. In the Target field, type a value.
10. Click Save.
11. Close the page.
12. Go to Inventory management > Setup > Batch > Batch attribute groups.
13. Click New.
14. In the Attribute group field, type a value.
15. In the Description field, type a value.
16. Click Save.
17. Click Group attributes.
18. Click New.
19. In the Attribute field, click the drop-down button to open the lookup.
20. In the list, find and select the desired record.
21. In the list, click the link in the selected row.
    * An attribute can be included in any of the groups.  
22. Click Save.
23. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]