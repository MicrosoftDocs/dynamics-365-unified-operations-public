--- 
# required metadata 
 
title: Generate and process customer rebates
description: This procedure demonstrates how to process customer rebates from claim generation to the point of passing them as accruals to Accounts receivable. 
author: Henrikan
ms.date: 06/25/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: PdsRebateAgreement, SalesTableListPage, SalesCreateOrder, SalesTable, MCRPriceHistory, SalesEditLines,  PdsRebateTableListPage, MCRBrokerWriteOffReason, MRCHierarchyAddCust, PdsItemRebateGroup, PdsRebate, PdsRebateProgramTMATable, PdsRebateTable, PdsRebateTableListPagePreviewPane, PdsRebateTrans, PdsRebateType_CustLookup   
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
# Generate and process customer rebates

[!include [banner](../../includes/banner.md)]

This procedure demonstrates how to process customer rebates from claim generation to the point of passing them as accruals to Accounts receivable. It walks you through a specific example to explain how the various conditions on the rebate lines affect the final amounts that will be credited to the customer. You need to use the USMF demo data company, and carry out the following tasks before you start the guide: (1) Go to the Accounts receivable parameters page, and expand the Prices tab and then the Price details tab, and check that the Enable price details option is set to Yes. (2) Go to the Rebate agreements page and select the customer rebate agreement: USMF-000001. If the Workflow approval status field is not set to Approved, you need click Validation on the Action Pane to approve it.


## Review a customer rebate agreement
1. Go to **Sales and marketing > Customer rebates > Rebate agreements**.
    - The next few steps look at the conditions of agreement USMF-000001. This makes it easier to understand how the customer credit values are calculated later in the procedure.  
    - The agreement is for an individual customer, in this example customer US-009.  
    - Rebates are given to the customer when they purchase a specific product. In this case, the product has item number T0020.   
    - The customer's sales performance, against which the rebate amounts are estimated, is to be accumulated on a weekly basis.  
    - The setting for "Price taken from" is Gross, which means that line's sales amount on which basis the claim is estimated is not reduced by the line discount.  
    - The Rebate line break type field shows the method for calculating rebates. In this case, the sales target against which the rebates are to be estimated is set to Quantity.   
    - The agreement's lines specify the rebate amount type, the actual rebate value, and the thresholds. In this example, the customer will qualify for a rebate of 20 USD per unit sold, if their weekly purchases of the product fall within 1 to 50 units; and a rebate of 40 USD per unit sold, if they purchase above 50 units.  
2. Close the page.

## Generate rebate claims
1. Go to **Sales and marketing > Sales orders > All sales orders**.
2. Click **New**. To mimic the way in which rebate claims would be generated, the next task is to create a sales order, where the product and quantity will qualify the customer in question for a rebate.    
3. In the **Customer account** field, enter or select a value.
4. Click **OK**.
5. In the **Item number** field, enter or select a value.
6. Set **Quantity** to '40'.
7. Under the **Sales order lines** section, click **Sales order line**.
8. Click **Price details**. If you don't see this option, it's because you didn't set the **Enable price details option** to 'Yes' before you started the guide.     
9. Expand the **Rebates** section. The **Rebates** tab lists all the rebate agreements that are applicable to the current order line and shows the estimated rebate amount. Note that the displayed amounts are only indications of what future rebate claims may be. The actual rebate amounts may be different depending on: the total sales volume achieved by the customer under a periodic rebate agreement; whether the customer had returned all or partial quantities; and whether the applicable sales order was invoiced.
10. Close the page.
11. Click **Add line**.
12. In the **Item number** field, enter or select a value.
13. Set **Quantity** to '60'.
14. Click **Save**.
15. On the **Action Pane**, click **Invoice**.
16. Click **Invoice**.
17. Expand the **Parameters** section.
18. In the **Quantity** field, select 'All'.
19. Click **OK**.
20. Click **OK**.

## Process rebate claims
1. Go to **Sales and marketing > Customer rebates > Rebates**.
    - The Rebates page acts as a workbench in which you can review, approve, and process rebate claims. You'll now process the claims that were created as a result of invoicing a sales order for customer US-009, who is the subject of the rebate agreement USMF-000001.   
    - The first line represents a rebate claim for 800 USD, which is based on the sales of 40 units of product T0020, calculated at 20 USD per unit. This matches the conditions of the first quantity break in the rebate agreement.  
    - The second claim is for 2,400 USD, which is based on the sales of 60 units of product T0020, calculated at 40 USD per unit, as per the second quantity break in the agreement.  
    - Both claims are in the "To be calculated" state. This means that they are associated with an agreement that tracks the customer's sales performance on periodic basis and that they have to be re-calculated to account for the total sales volume within the respective period.   
2. Click **Cumulate**.
3. In the **Customer** field, enter or select a value.
4. In the **Start date** field, select today's date.
5. Click **OK**. As a result of running the **Cumulate** function, the estimated claim amount has now been adjusted to account for the fact that the customer's total sales volume in the relevant period is higher than when the first rebate was generated. More specifically, because the total purchased quantity has reached 100 units, the customer now qualifies for 40 USD per unit (as per the agreement's second quantity break), or 4,000 USD of total rebate amount. The difference is recorded as a new claim "adjustment" for the additional 800 USD. The status of the rebate claims that were included in the Cumulate update are now set to Calculated. 
6. In the list, mark all rows.
7. Click **Approve**.
8. Click **Process**.
9. In the **Customer** field, enter or select a value.
10. Click **OK**. A message shows that the rebate was processed successfully, and the status of the claims has been changed to Mark. This means that as a result of a Rebate accrual journal being posted:
    - The claims have now been transferred to the temporary customer balance as deductions.
    - The Rebate accrual account has been credited to represent the future liability towards the customer.
    - The Rebate expense account has been debited, in recognition of the cost incurred in connection with the sales.   



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
