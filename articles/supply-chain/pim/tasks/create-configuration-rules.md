--- 
# required metadata 
 
title: Create configuration rules
description: This procedure creates configuration rules that can be used for dimension-based configuration to enforce or prevent certain combinations of BOM lines. 
author: t-benebo
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: BOMTable, BOMConfigRule, ConfigItemIdLookup   
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
# Create configuration rules

[!include [banner](../../includes/banner.md)]

This procedure creates configuration rules that can be used for dimension-based configuration to enforce or prevent certain combinations of BOM lines. The demo data company used to create this procedure is USMF. This is the seventh procedure out of eight that explains how to build combinations for dimension-based configuration.

1. Go to Product information management > Bills of materials and formulas > Bills of materials.
2. In the list, find and select the desired record.
    * Find and select the BOM for the dimension-based configuration.  
3. On the Action Pane, click Options.
4. Click Change view.
5. Click Header view.
    * Open the header view to access the Configuration route FastTab.  
6. Expand or collapse the Configuration route section.
    * The Configuration route FastTab must be in the expanded mode.  
7. Click Configuration rules.
8. Click New.
9. In the list, mark the selected row.
10. In the Item number field, click the drop-down button to open the lookup.
    * The items in the current configuration group are displayed. Select the one that represents the condition in the rule.  
11. In the list, click the link in the selected row.
12. In the Method field, select an option.
    * It is possible to enforce either a selection or a deselection of an item from another configuration group.  
13. In the Derived group field, click the drop-down button to open the lookup.
14. In the list, find and select the desired record.
15. In the list, click the link in the selected row.
    * Select the desired configuration group.  
16. In the Derived item number field, click the drop-down button to open the lookup.
17. In the list, click the link in the selected row.
    * Select the item number that will be either selected or deselected depending on the chosen method.  
18. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]