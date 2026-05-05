---
title: Set up sales commission rules
description: Learn how to set up and enable sales commission calculation and tracking, including a step-by-step process using the USMF demo data company.
author: AditiPattanaik
ms.author: adpattanaik
ms.reviewer: kamaybac
ms.search.form: CommissionCustomerGroup, CommissionItemGroup, CommissionSalesGroup, CommissionSalesMember, DirPartyLookup, CommissionCalc, InventPosting, CustTable, EcoResProductDetailsExtended, CommissionEmplSalesGroup 
ms.topic: how-to
ms.date: 5/5/2026
ms.custom: 
  - bap-template
---

# Set up sales commission rules

[!include [banner](../../includes/banner.md)]

This procedure shows you how to set up and enable sales commission calculation and tracking. The procedure shows how to create both customer and item commission groups, and then how to link a selected customer and product to the respective groups. Those groups are then used in the commission calculation setup to create a customer, item, and sales representatives combination that must be matched by the sales order to entitle the sales people to a commission. Creating customer and item commission groups are optional, as the calculation of commission can also be done for an individual customer and/or item. You can run this procedure in demo data company USMF or on your own data.

## Set up commission groups and commission rates

1. Go to **Sales and marketing > Commissions > Customer groups for commission**.
1. Select **New**.
1. In the **Group** field, enter a value.
1. In the **Name** field, type a value.
1. Select **Save**.
1. Close the page.
1. Go to **Sales and marketing > Commissions > Item groups**.
1. Select **New**.
1. In the **Group** field, enter a value.
1. In the **Name** field, type a value.
1. Select **Save**.
1. Close the page.
1. Go to **Sales and marketing > Commissions > Sales groups**.
    - A Commission sales group specifies the employees in sales representative roles who are eligible to receive a commission when a customer associated with the relevant sales group buys certain items.  
    - In the USMF demo data company, there's a sales group called *Sales reps US*.  
1. On the Action Pane, select **General**.
1. Select **Sales rep.**. The Sales rep. page displays a list of the company's salespeople who are associated with a specific commission group. You can assign multiple sales representatives to the same group and define their respective share of the total commission fee as a percentage value. The total commission share across all employees must not exceed 100.
1. In the list, mark the selected row.
1. Select **Edit**.
1. Set **Commission share** to *50*.
1. Select **New**.
1. In the **Name** field, select the drop-down button to open the lookup.
1. Use the **Quick Filter** to find records. For example, filter on the Name field with a value of *Susan Burk*.
1. Select **Select**.
1. Set **Commission share** to *50*.
1. Select **Save**.
1. Go to **Sales and marketing > Commissions > Commission calculation**. In the **Commission calculation** page, you define the commission rate that the employee receives for a sales transaction when it contains the preset combination of customer and product. As part of the commission rate setup, specify the commission calculation basis and whether it should include or exclude discounts. You can also enter a validity period for when the commission rate is active.  
1. Select **New**.
1. In the **Item code** field, select *Group*.
1. In the **Item relation** field, select the drop-down button to open the lookup.
1. In the list, find and select the group that you created earlier.
1. In the **Customer code** field, select *Group*.
1. In the **Customer relation** field, select the drop-down button to open the lookup.
1. In the list, select the group that you set up earlier.
1. In the **Sales rep. relation** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
    - Keep the *Before line discount* option.  
    - Keep the *Revenue* option as the basis for commission value calculation.
1. In the Commission percentage field, enter a number.
1. Select **Save**.

## Setting up commission posting

1. Go to **Sales and marketing > Commissions > Commission posting**. Employees receive commission fees, so set up this feature to ensure correct financial posting to the appropriate accounts in the **General ledger**. Set up this feature in the **Commission posting** page. Review the setup that's available for the current company. Typically, the commission amounts are posted to a dedicated expense account and are offset to a dedicated payable account. If you don't have the commission posting rules set up, the system will fail to complete invoicing of a sales order that has eligible commissions.   
1. Close the page.

## Assign a commission group to a customer and a product

1. Go to **Sales and marketing > Customers > All customers**.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. Select **Edit**.
1. Expand the **Sales order defaults** section.
1. In the **Commission group** field, select the drop-down button to open the lookup.
1. In the list, select the group that you created earlier.
1. In the **Sales group** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. Select **Save**.
1. Go to **Product information management > Products > Released products**.
1. Use the **Filter** to find records. For example, filter on the Item number field with a value of *T0020*.
1. In the list, select the link in the selected row.
1. Select **Edit**.
1. Expand the **Sell** section.
1. In the **Commission group** field, select the drop-down button to open the lookup.
1. In the list, select the commission group that you created earlier.
1. Select **Save**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
