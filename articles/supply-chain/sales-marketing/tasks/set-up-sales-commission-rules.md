--- 
# required metadata 
 
title: Set up sales commission rules
description: This procedure shows you how to set up and enable sales commission calculation and tracking. 
author: omulvad
manager: AnnBe 
ms.date: 11/03/2017
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: omulvad
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Set up sales commission rules

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure shows you how to set up and enable sales commission calculation and tracking. The procedure shows how to create both customer and item commission groups, and then how to link a selected customer and product to the respective groups. Those groups are then used in the commission calculation setup to create a customer, item, and sales representatives combination that must be matched by the sales order to entitle the sales people to a commission. Creating customer and item commission groups are optional, as the calculation of commission can also be done for an individual customer and/or item. You can run this procedure in demo data company USMF or on your own data.


## Set up commission groups and commission rates
1. Go to Sales and marketing > Commissions > Customer groups for commission.
2. Click New.
3. In the Group field, type a value.
4. In the Name field, type a value.
5. Click Save.
6. Close the page.
7. Go to Sales and marketing > Commissions > Item groups.
8. Click New.
9. In the Group field, type a value.
10. In the Name field, type a value.
11. Close the page.
12. Go to Sales and marketing > Commissions > Sales groups.
    * A Commission sales group specifies the employees in sales representative roles who are eligible to receive a commission when a customer associated with the relevant sales group buys certain items.  
    * In the USMF demo data company, there is a sales group called "Sales reps US."  
13. On the Action Pane, click General.
14. Click Sales rep.
    * The Sales rep. page displays a list of the company's sales people who are associated with a specific commission group. You can assign multiple sales representatives to the same group and define their respective share of the total commission fee as a percentage value. The total commission share across all employees must not exceed 100.  
15. In the list, mark the selected row.
16. Click Edit.
17. Set Commission share to '50'.
18. Click New.
19. In the Name field, click the drop-down button to open the lookup.
20. Use the Quick Filter to find records. For example, filter on the Name field with a value of 'Susan Burk'.
21. Click Select.
22. Set Commission share to '50'.
23. Click Save.
24. Go to Sales and marketing > Commissions > Commission calculation.
    * In the Commission calculation page you define the commission rate that the employee is to receive for a sales transaction when it contains the pre-set combination of customer and product. As part of the commission rate setup, you must specify the commission calculation basis and whether it should include or exclude discounts. You can also enter a validity period for when the commission rate is active.  
25. Click New.
26. In the Item code field, select 'Group'.
27. In the Item relation field, click the drop-down button to open the lookup.
28. In the list, find and select the group that you created earlier.
29. In the list, click the link in the selected row.
30. In the Customer code field, select 'Group'.
31. In the Customer relation field, click the drop-down button to open the lookup.
32. In the list, select the group that you set up earlier.
33. In the Sales rep. relation field, click the drop-down button to open the lookup.
34. In the list, find and select the desired record.
    * Keep the "Before line discount" option.  
    * Keep the "Revenue" option as the basis for commission value calculation.    
35. In the Commission percentage field, enter a number.
36. Click Save.

## Setting up commission posting
1. Go to Sales and marketing > Commissions > Commission posting.
    * Commission fees are payable to the employees and must therefore be set up to ensure correct financial posting to the appropriate accounts in the General ledger. This is done in the Commission posting page. Review the setup that is available for the current company. Typically, the commission amounts are posted to a dedicated expense account and are offset to a dedicated payable account. If you don't have the commission posting rules set up, the system will fail to complete invoicing of a sales order which has eligible commissions.  
2. Close the page.

## Assign a commission group to a customer and a product
1. Go to Sales and marketing > Customers > All customers.
2. In the list, find and select the desired record.
3. In the list, click the link in the selected row.
4. Click Edit.
5. Expand the Sales order defaults section.
6. In the Commission group field, click the drop-down button to open the lookup.
7. In the list, select the group that you created earlier.
8. In the Sales group field, click the drop-down button to open the lookup.
9. In the list, find and select the desired record.
10. Click Save.
11. Go to Product information management > Products > Released products.
12. Use the Quick Filter to find records. For example, filter on the Item number field with a value of 'T0020 '.
13. In the list, click the link in the selected row.
14. Click Edit.
15. Expand the Sell section.
16. In the Commission group field, click the drop-down button to open the lookup.
17. In the list, select the commission group that you created earlier.

