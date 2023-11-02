---
title: GB-00002 Set up item sales tax groups for reverse charge VAT
description: This task walks you through setting up item sales tax groups, assigning the default values to products and procurements categories subject to reverse charge VAT for the United Kingdom.
author: EricWangChen
ms.date: 08/29/2018
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: United Kingdom
ms.author: wangchen
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: TaxItemGroup, DefaultDashboard, EcoResProductDetailsExtended, ProcCategoryHierarchyManagement
---
# GB-00002 Set up item sales tax groups for reverse charge VAT

[!include [banner](../../includes/banner.md)]

This task walks you through setting up item sales tax groups, assigning the default values to products and procurements categories subject to reverse charge VAT for the United Kingdom.

This walkthrough was created using the demo company GBSI.

This task requires that the following sales tax codes are created for Reverse charge purposes.  

REV17.5 – positive value

REV-17.5 – negative value

1. Go to Tax > Indirect taxes > Sales tax > Item sales tax groups.
2. In the list, find and select the item sales tax group RC-VAT
    * In the Setup tab, you can add sales tax codes to this sales tax group.  Verify that the following sales tax codes exist for Reverse charge purposes:  REV17.5 – positive value  REV-17.5 – negative value  
3. Verify the setup tab and close the form
    * Verify that the following sales tax codes included in the 'RC-VAT' item sales tax group for Reverse charge purposes:  REV17.5 – positive value  REV-17.5 – negative value  
4. Go to Product information management > Products > Released products.
    * In this form you'll assign the item sales tax group to the products that are subject to reverse charge.  
5. In the list, find and select item S0012
6. In the list, click the link in the selected row.
7. Expand or collapse the Purchase section.
8. Click Edit.
9. In the Item sales tax group field, click the drop-down button to open the lookup.
    * For this example, select 'RC-VAT'.  
10. In the list, find and select the desired record.
    * For this example, select 'RC-VAT'.  
11. Expand or collapse the Sell section.
12. In the Item sales tax group field, click the drop-down button to open the lookup.
    * For this example, select 'RC-VAT'.  
13. In the list, find and select the desired record.
    * For this example, select 'RC-VAT'.  
14. Click Save.
15. Close the form
16. In the list, find and select the item S0020
17. In the list, click the link in the selected row.
18. In the Item sales tax group field, click the drop-down button to open the lookup.
    * For this example, select 'RC-VAT'.  
19. In the list, click the link in the selected row.
    * For this example, select 'RC-VAT'.  
20. In the Item sales tax group field, click the drop-down button to open the lookup.
    * For this example, select 'RC-VAT'.  
21. In the list, click the link in the selected row.
    * For this example, select 'RC-VAT'.  
22. Close the page.
23. Go to Procurement and sourcing > Procurement categories.
    * In this form you'll assign the item sales tax group to the categories that are subject to reverse charge.  
24. In the tree, expand 'Expand the category tree and select a category.'.
    * For this example, select Cleaning.  
25. In the tree, select 'Select a category'.
    * For this example, select Cleaning.  
26. Expand or collapse the Item sales tax groups section.
27. In the Item sales tax group: field, click the drop-down button to open the lookup.
    * For this example, select 'RC-VAT'.  
28. In the list, click the link in the selected row.
    * For this example, select 'RC-VAT'.  
29. Click Save.
30. Close the page.

> [!NOTE]
> The reverse charge should be set up for specific scenarios, including:
>
> - Domestic reverse charge. For example, the purchase of UK services, gold, computers chips, or mobile phones.
> - European service purchase. For the European goods (items) purchasing, the **Use tax** can be activated on the sales tax group.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
