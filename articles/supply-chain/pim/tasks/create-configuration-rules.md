---
title: Create configuration rules
description: This procedure creates configuration rules that can be used for dimension-based configuration to enforce or prevent certain combinations of BOM lines. 
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form: BOMTable, BOMConfigRule, ConfigItemIdLookup   
ms.topic: how-to
ms.date: 11/10/2022
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Create configuration rules

[!include [banner](../../includes/banner.md)]

This procedure creates configuration rules that can be used for dimension-based configuration to enforce or prevent certain combinations of BOM lines.

This is the seventh procedure [of an eight-procedure sequence](../dimension-based-product-configuration.md#sequence) that explains how to build combinations for dimension-based configuration. You should do all eight procedures, in order, because each new procedure builds on data created by the previous procedures. To work through this sequence by using the sample records and values that are specified here, you must be on a system where the standard [demo data](../../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed, and you must select the *USMF* legal entity before you begin.

1. Go to **Product information management \> Bills of materials and formulas \> Bills of materials**.
2. In the list, find and select the desired record.
    * Find and select the BOM for the dimension-based configuration.  
3. On the Action Pane, select **Options**.
4. Select **Change view**.
5. Select **Header view**.
    * Open the header view to access the Configuration route FastTab.  
6. Expand or collapse the **Configuration route** section.
    * The **Configuration route** FastTab must be in the expanded mode.  
7. Select **Configuration rules**.
8. Select **New**.
9. In the list, mark the selected row.
10. In the **Item number** field, select the drop-down button to open the lookup.
    * The items in the current configuration group are displayed. Select the one that represents the condition in the rule.  
11. In the list, select the link in the selected row.
12. In the **Method** field, select an option.
    * It is possible to enforce either a selection or a deselection of an item from another configuration group.  
13. In the **Derived group** field, select the drop-down button to open the lookup.
14. In the list, find and select the desired record.
15. In the list, select the link in the selected row.
    * Select the desired configuration group.  
16. In the **Derived item number** field, select the drop-down button to open the lookup.
17. In the list, select the link in the selected row.
    * Select the item number that will be either selected or deselected depending on the chosen method.  
18. Close the page.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]