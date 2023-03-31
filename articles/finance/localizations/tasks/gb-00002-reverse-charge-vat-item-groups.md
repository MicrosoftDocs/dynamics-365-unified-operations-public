---
title: GB-00002 Set up reverse charge VAT item groups, rules, and parameters
description: This task walks you through setting up reverse charge item groups, applicability rules for purchasing and for sales purposes, and reverse charge parameters for the United Kingdom.
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
ms.search.form: ReverseChargeItemGroup_W, EcoResCategorySingleLookup, ReverseChargeRule_W, LedgerParameters, TaxGroupLookup
---
# GB-00002 Set up reverse charge VAT item groups, rules, and parameters

[!include [banner](../../includes/banner.md)]

This task walks you through setting up reverse charge item groups, applicability rules for purchasing and for sales purposes, and reverse charge parameters for the United Kingdom.  Before you complete this task, be sure to set up sales tax groups and item sales tax groups for reverse charge VAT. 

This walkthrough was created using the demo company GBSI.


## Set up reverse charge item groups
1. Go to Tax > Setup > Sales tax > Reverse charge item groups.
2. Click New.
3. In the Name field, type a value.
    * For this example, enter DEVICES.  
4. Click the Reverse charge sales list slider.
    * Setting this to "Yes"  means that this group will be included in Reverse Charge Sales list report.  
5. Click Save.
6. Click Add.
7. In the Item relation field, type a value.
    * For this example, enter S0020.  
8. Click Add.
9. In the Item relation field, click the drop-down button to open the lookup.
    * The item code on this line should be Table.  
10. In the list, find and select the desired record.
    * For this example, select S0012.  
11. Click Save.
12. In the Sales/Purchase field, select 'Sales'.
13. Click Add.
14. In the Item code field, select an option.
    * For this example, select Group.  
15. In the Item relation field, click the drop-down button to open the lookup.
    * For this example, select the item group ProjItem.  
16. In the list, click the link in the selected row.
    * For this example, select the item group Select ProjItem.  
17. Click Save.
18. Click New.
19. In the Name field, type a value.
    * For this example, enter SERVICES.  
20. Click Save.
21. In the Sales/Purchase field, select 'Purchase'.
22. Click Add.
23. In the Item code field, select 'Group'.
    * For this example, select Group.  
24. In the Item relation field, click the drop-down button to open the lookup.
    * For this example, select the item group Services.  
25. In the list, find and select the desired record.
    * For this example, select the item group Services.  
26. Click Add.
27. In the Item code field, select 'Category'.
28. In the Category field, click the drop-down button to open the lookup.
29. In the tree, expand 'Expand the category tree and select a category.'.
    * For this example, select Cleaning.  
30. In the tree, select 'Select the caterory from the list'.
    * For this example, select category Cleaning.  
31. Click OK.
32. Click Save.

## Set up reverse charge rules
1. Go to Tax > Setup > Sales tax > Reverse charge rules.
2. Click New.
3. In the Partner country/region type field, select an option.
    * For this example, select Domestic.  
4. In the Reverse charge item group field, click the drop-down button to open the lookup.
    * For this example, select DEVICES.  
5. In the list, click the link in the selected row.
    * For this example, select DEVICES.  
6. In the Threshold amount field, enter a number.
    * For this example, enter 5000.  
7. Select the Empty tax base for outgoing tax check box.
    * Selecting this check box provides a zero tax base amount in Box 6 of the VAT 100 report.  
8. In the Action field, select an option.
    * Select 'Set' to update the Sales tax group with the reverse charge VAT group when the rule is applied.  
9. In the Effective field, enter a date.
10. Click Save.
11. Click New.
12. In the Partner country/region type field, select 'Foreign'.
    * For this example, select Foreign.  
13. Select the Domestic delivery address check box.
    * Select this check box if the rule should be applied to domestic delivery.  
14. In the Reverse charge item group field, click the drop-down button to open the lookup.
    * Select 'SERVICES'  
15. In the list, find and select the desired record.
    * For this example, select SERVICES.  
16. In the Action field, select an option.
    * Select 'Set' to update the Sales tax group with the reverse charge VAT group when the rule is applied.  
17. In the Effective field, enter a date.
18. Click New.
19. In the Document type field, select an option.
    * For this example, select Vendor invoice.  
20. In the Partner country/region type field, select an option.
    * For this example, select EU.  
21. Select the Domestic delivery address check box.
    * Select this check box if the rule applies to the domestic delivery.  
22. In the Reverse charge item group field, click the drop-down button to open the lookup.
    * For this example, select SERVICES.  
23. In the list, find and select the desired record.
24. In the Action field, select an option.
    * Select Set to update the sales tax group with the reverse charge VAT group when the rule is applied.  
25. In the Effective field, enter a date.
26. Click New.
27. In the Document type field, select an option.
    * For this example, select Sales order as the document type.  
28. In the Partner country/region type field, select an option.
    * For this example, select Domestic.  
29. In the Reverse charge item group field, click the drop-down button to open the lookup.
    * For this example, select DEVICES.  
30. In the Threshold amount field, enter a number.
    * For this example, enter 5000.  
31. In the Action field, select an option.
    * Select 'Prompt' to get notification when the rule is applied.  
32. In the Effective field, enter a date.
33. Click Save.
34. Close the page.

## Configure general ledger parameters for reverse charge VAT
1. Go to Tax > Setup > Parameters > General ledger parameters.
2. Click the Reverse charge tab.
3. Click the Enable reverse charge slider.
4. In the Purchase order sales tax group field, click the drop-down button to open the lookup.
    * For this example, select RC-VAT.  
5. In the list, find and select the desired record.
    * For this example, select RC-VAT.  
6. In the Sales order sales tax group field, click the drop-down button to open the lookup.
    * For this example, select RC-VAT-AR.  
7. In the list, find and select the desired record.
    * Select 'RC-VAT-AR'  
8. Click Save.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
