---
title: Set up sales commission rules
description: Learn how to set up and enable sales commission calculation and tracking, including a step-by-step process using the USMF demo data company.
author: AditiPattanaik
ms.author: adpattanaik
ms.reviewer: kamaybac
ms.search.form: CommissionCustomerGroup, CommissionItemGroup, CommissionSalesGroup, CommissionSalesMember, DirPartyLookup, CommissionCalc, InventPosting, CustTable, EcoResProductDetailsExtended, CommissionEmplSalesGroup 
ms.topic: how-to
ms.date: 08/26/2024
ms.custom: 
  - bap-template
---

# Set up sales commission rules

[!include [banner](../../includes/banner.md)]

This procedure shows you how to set up and enable sales commission calculation and tracking. The procedure shows how to create both customer and item commission groups, and then how to link a selected customer and product to the respective groups. Those groups are then used in the commission calculation setup to create a customer, item, and sales representatives combination that must be matched by the sales order to entitle the sales people to a commission. Creating customer and item commission groups are optional, as the calculation of commission can also be done for an individual customer and/or item. You can run this procedure in demo data company USMF or on your own data.

## Set up commission groups and commission rates

1. Go to **Sales and marketing > Commissions > Customer groups for commission**.
2. Select **New**.
3. In the **Group** field, type a value.
4. In the **Name** field, type a value.
5. Select **Save**.
6. Close the page.
7. Go to **Sales and marketing > Commissions > Item groups**.
8. Select **New**.
9. In the **Group** field, type a value.
10. In the **Name** field, type a value.
11. Select **Save**.
12. Close the page.
13. Go to **Sales and marketing > Commissions > Sales groups**.
    - A Commission sales group specifies the employees in sales representative roles who are eligible to receive a commission when a customer associated with the relevant sales group buys certain items.  
    - In the USMF demo data company, there's a sales group called *Sales reps US*.  
14. On the Action Pane, select **General**.
15. Select **Sales rep.**. The Sales rep. page displays a list of the company's sales people who are associated with a specific commission group. You can assign multiple sales representatives to the same group and define their respective share of the total commission fee as a percentage value. The total commission share across all employees must not exceed 100.
16. In the list, mark the selected row.
17. Select **Edit**.
18. Set **Commission share** to *50*.
19. Select **New**.
20. In the **Name** field, select the drop-down button to open the lookup.
21. Use the **Quick Filter** to find records. For example, filter on the Name field with a value of *Susan Burk*.
22. Select **Select**.
23. Set **Commission share** to *50*.
24. Select **Save**.
25. Go to **Sales and marketing > Commissions > Commission calculation**. In the **Commission calculation** page, you define the commission rate that the employee is to receive for a sales transaction when it contains the preset combination of customer and product. As part of the commission rate setup, you must specify the commission calculation basis and whether it should include or exclude discounts. You can also enter a validity period for when the commission rate is active.  
26. Select **New**.
27. In the **Item code** field, select *Group*.
28. In the **Item relation** field, select the drop-down button to open the lookup.
29. In the list, find and select the group that you created earlier.
30. In the **Customer code** field, select *Group*.
31. In the **Customer relation** field, select the drop-down button to open the lookup.
32. In the list, select the group that you set up earlier.
33. In the **Sales rep. relation** field, select the drop-down button to open the lookup.
34. In the list, find and select the desired record.
    - Keep the *Before line discount* option.  
    - Keep the *Revenue* option as the basis for commission value calculation.
35. In the Commission percentage field, enter a number.
36. Select **Save**.

## Setting up commission posting

1. Go to **Sales and marketing > Commissions > Commission posting**. Commission fees are payable to the employees and must therefore be set up to ensure correct financial posting to the appropriate accounts in the **General ledger**. This is done in the **Commission posting** page. Review the setup that is available for the current company. Typically, the commission amounts are posted to a dedicated expense account and are offset to a dedicated payable account. If you don't have the commission posting rules set up, the system will fail to complete invoicing of a sales order that has eligible commissions.  
2. Close the page.

## Assign a commission group to a customer and a product

1. Go to **Sales and marketing > Customers > All customers**.
2. In the list, find and select the desired record.
3. In the list, select the link in the selected row.
4. Select **Edit**.
5. Expand the **Sales order defaults** section.
6. In the **Commission group** field, select the drop-down button to open the lookup.
7. In the list, select the group that you created earlier.
8. In the **Sales group** field, select the drop-down button to open the lookup.
9. In the list, find and select the desired record.
10. Select **Save**.
11. Go to **Product information management > Products > Released products**.
12. Use the **Filter** to find records. For example, filter on the Item number field with a value of *T0020*.
13. In the list, select the link in the selected row.
14. Select **Edit**.
15. Expand the **Sell** section.
16. In the **Commission group** field, select the drop-down button to open the lookup.
17. In the list, select the commission group that you created earlier.
18. Select **Save**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
