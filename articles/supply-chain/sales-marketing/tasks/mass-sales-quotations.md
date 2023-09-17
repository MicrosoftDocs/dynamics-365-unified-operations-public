--- 
# required metadata 
 
title: Mass create sales quotations
description: This procedure demonstrates how to efficiently create quotations offering a set of products or services that are to be sent to multiple customers. 
author: Henrikan
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: SalesQuotationTemplateGroup, SalesQuotationListPage, SalesCreateQuotation, SalesQuotationTable, SysQueryForm, SalesQuickQuote   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: henrikan
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Mass create sales quotations

[!include [banner](../../includes/banner.md)]

This procedure demonstrates how to efficiently create quotations offering a set of products or services that are to be sent to multiple customers. This mass quotation creation is based on quotation templates. You can run this procedure on your own data or in demo data company USMF.


## Create a quotation template
1. Go to Sales and marketing > Setup > Quotations > Template groups.
2. Click New.
3. In the Group ID field, type an ID of your choice.
4. In the Description field, type a value.
5. Click Save.
6. Close the page.
7. Go to Sales and marketing > Sales quotations > All quotations.
8. Click New.
9. In the Account type field, select 'Customer'.
10. In the Customer account field, enter or select a value.
11. Click OK.
    * For a quotation to become a template you must carry out  setup steps on the quotation header. This must be done before you add lines to the quotation.   
12. On the Action Pane, click Options.
13. Click Change view.
14. Click Header view.
15. Expand the Setup section.
16. In the Group ID field, enter or select a value.
17. In the Template name field, type a value.
18. Select Yes in the Active field.
    * Only active templates can be used when you apply a template to a new sales quotation.  
19. On the Action Pane, click Options.
20. Click Change view.
21. Click Line view.
22. In the Item field, enter or select a value.
23. In the Item field, type a value.
24. Close the page.
25. In the Discount percent field, enter a number.
26. Click Add line.
27. In the Item field, enter or select a value.
28. In the Item field, type a value.
29. Close the page.
30. In the Unit price field, enter a new price or change the current one.
31. Click Add line.
32. In the Item field, enter or select a value.
33. In the Item field, type a value.
34. Close the page.
35. In the Quantity field, enter a number.
36. In the Discount field, enter a number.
37. Click Save.

## Apply the template to create a single quotation
1. Go to Sales and marketing > Sales quotations > All quotations.
    * Note that the quotation you have just created is marked as template.  
2. Click New.
3. In the Account type field, select 'Customer'.
4. In the Customer account field, enter or select a value.
5. Expand the Template section.
6. In the Group ID field, enter or select a value.
7. In the Template name field, enter or select a value.
8. In the Calculation method field, select 'Based on template values'.
9. Click OK.
    * The new quotation has now been created, based on the data and terms of the template.  
10. Close the page.
11. Close the page.

## Apply the template to mass create quotations
1. Go to Sales and marketing > Sales quotations > Quotation update > Mass create quotations.
2. In the Account type field, select 'Customer'.
3. In the Group ID field, enter or select a value.
4. In the Template name field, enter or select a value.
5. In the Calculation method field, select 'Based on template values'.
6. Expand the Records to include section.
7. Click Filter.
8. In the Criteria field, set the filter to cover a range of customers you want to include in this mass quotation creation. Use the following format "Customer1..CustomerN.
    * For example, you could set the filter to: US-001..US-004  
9. Click OK.
10. Click OK.
11. Go to Sales and marketing > Sales quotations > All quotations.
    * Verify that quotations have been created for all the customers specified in the mass update routine, as based on the selected template.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]