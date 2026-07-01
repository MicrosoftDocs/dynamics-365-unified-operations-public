--- 
title: Generate and process customer rebates
description: Learn how to process customer rebates from claim generation to the point of passing them as accruals to Accounts receivable.
author: AditiPattanaik
ms.author: adpattanaik
ms.topic: how-to
ms.date: 05/22/2026
ms.custom:
ms.reviewer: kamaybac 
ms.search.form: PdsRebateAgreement, SalesTableListPage, SalesCreateOrder, SalesTable, MCRPriceHistory, SalesEditLines,  PdsRebateTableListPage, MCRBrokerWriteOffReason, MRCHierarchyAddCust, PdsItemRebateGroup, PdsRebate, PdsRebateProgramTMATable, PdsRebateTable, PdsRebateTableListPagePreviewPane, PdsRebateTrans, PdsRebateType_CustLookup
---

# Generate and process customer rebates

[!include [banner](../../includes/banner.md)]

This procedure demonstrates how to process customer rebates from claim generation to the point of passing them as accruals to Accounts receivable. It walks you through a specific example to explain how the various conditions on the rebate lines affect the final amounts credited to the customer. Use the USMF demo data company, and complete the following tasks before you start the guide: (1) Go to the **Accounts receivable parameters** page, expand the **Prices** tab, and then the **Price details** tab, and check that the **Enable price details** option is set to **Yes**. (2) Go to the **Rebate agreements** page and select the customer rebate agreement: USMF-000001. If the **Workflow approval status** field isn't set to **Approved**, select **Validation** on the Action Pane to approve it.

## Review a customer rebate agreement

1. Go to **Sales and marketing > Customer rebates > Rebate agreements**.
    - The next few steps look at the conditions of agreement USMF-000001. The conditions makes it easier to understand how the customer credit values are calculated later in the procedure.
    - The agreement is for an individual customer, in this example customer US-009.  
    - Rebates are given to the customer when they purchase a specific product. In this case, the product has item number T0020.
    - The customer's sales performance, against which the rebate amounts are estimated, is to be accumulated on a weekly basis.  
    - The setting for **Price taken from** is **Gross**, which means that the line's sales amount on which basis the claim is estimated isn't reduced by the line discount.  
    - The **Rebate line break type** field shows the method for calculating rebates. In this case, the sales target against which the rebates are to be estimated is set to **Quantity**.
    - The agreement's lines specify the rebate amount type, the actual rebate value, and the thresholds. In this example, the customer qualifies for a rebate of 20 USD per unit sold, if their weekly purchases of the product fall within 1 to 50 units; and a rebate of 40 USD per unit sold, if they purchase above 50 units.  
1. Close the page.

## Generate rebate claims

1. Go to **Sales and marketing > Sales orders > All sales orders**.
1. Click **New**. To mimic the way in which rebate claims would be generated, the next task is to create a sales order, where the product and quantity will qualify the customer in question for a rebate.
1. In the **Customer account** field, enter or select a value.
1. Click **OK**.
1. In the **Item number** field, enter or select a value.
1. Set **Quantity** to 40.
1. Under the **Sales order lines** section, select **Sales order line**.
1. Select **Price details**. If you don't see this option, it's because you didn't set the **Enable price details option** to 'Yes' before you started the guide.
1. Expand the **Rebates** section. The **Rebates** tab lists all the rebate agreements that apply to the current order line and shows the estimated rebate amount. The displayed amounts are only indications of what future rebate claims might be. The actual rebate amounts might be different depending on: the total sales volume the customer achieves under a periodic rebate agreement; whether the customer returns all or partial quantities; and whether the applicable sales order is invoiced.
1. Close the page.
1. Select **Add line**.
1. In the **Item number** field, enter or select a value.
1. Set **Quantity** to 60.
1. Click **Save**.
1. On the Action Pane, select **Invoice**.
1. Select **Invoice**.
1. Expand the **Parameters** section.
1. In the **Quantity** field, select **All**.
1. Click **OK**.
1. Click **OK**.

## Process rebate claims

1. Go to **Sales and marketing > Customer rebates > Rebates**.
    - The **Rebates** page acts as a workbench where you can review, approve, and process rebate claims. You can now process the claims that were created as a result of invoicing a sales order for customer US-009, who is the subject of the rebate agreement USMF-000001.
    - The first line represents a rebate claim for 800 USD, which is based on the sales of 40 units of product T0020, calculated at 20 USD per unit. This matches the conditions of the first quantity break in the rebate agreement.  
    - The second claim is for 2,400 USD, which is based on the sales of 60 units of product T0020, calculated at 40 USD per unit, as per the second quantity break in the agreement.  
    - Both claims are in the **To be calculated** state. This state means that they're associated with an agreement that tracks the customer's sales performance on a periodic basis and that they need to be recalculated to account for the total sales volume within the respective period.
1. Select **Cumulate**.
1. In the **Customer** field, enter or select a value.
1. In the **Start date** field, select today's date.
1. Select **OK**. As a result of running the **Cumulate** function, the estimated claim amount is adjusted to account for the fact that the customer's total sales volume in the relevant period is higher than when the first rebate was generated. More specifically, because the total purchased quantity reaches 100 units, the customer now qualifies for 40 USD per unit (as per the agreement's second quantity break), or 4,000 USD of total rebate amount. The difference is recorded as a new claim "adjustment" for the additional $800 USD. The status of the rebate claims that are included in the **Cumulate** update are now set to **Calculated**.
1. In the list, mark all rows.
1. Select **Approve**.
1. Select **Process**.
1. In the **Customer** field, enter or select a value.
1. Select **OK**. A message shows that the rebate was processed successfully, and the status of the claims changes to **Mark**. This status means that as a result of a Rebate accrual journal being posted:
    - The claims are now transferred to the temporary customer balance as deductions.
    - The Rebate accrual account is credited to represent the future liability towards the customer.
    - The Rebate expense account is debited, in recognition of the cost incurred in connection with the sales.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
