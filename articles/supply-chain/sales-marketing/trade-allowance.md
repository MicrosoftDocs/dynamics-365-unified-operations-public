---
# required metadata

title: Trade allowance management
description: This topic describes trade allowance management for Microsoft Dynamics 365 for Finance and Operations.
author: t-benebo
manager: AnnBe
ms.date: 08/02/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form:  
audience: IT Pro
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: t-benebo
ms.search.validFrom: 2018-01-31
ms.dyn365.ops.version: July 2017 update
---

# Trade allowance management

[!include [banner](../includes/banner.md)]

Trade allowance management helps companies manage sales promotion programs that offer retail "pay-for-performance" monetary rewards to customers that achieve volume and behavioral goals.

This topic provides an overview for the most common tasks that are involved in managing a sales promotion program. The overview covers the following tasks:

- Review the promotional fund and a trade allowance agreement.
- Perform sales under the planned merchandising event, and generate bill-back claims.
- Process claims, and pass them as deductions to Accounts receivable (A/R).
- Settle deductions that are due and customer short-pays on the Deduction workbench.
- Analyze the effectiveness of the promotion and fund consumption.

## Audience and purpose

The information in this document is intended for business decision makers in enterprise companies, in positions such as purchase manager, chief financial officer (CFO), and accounting manager, who have the following responsibilities:

- High-level budgets and fund allocation
- Planning and analyzing sales promotions
- Managing staff that processes bill-back claims, runs payments based on merchandizing events, and settles short-pays and deductions

People in these roles are looking for ways to achieve these goals:

- Better use marketing promotional funds.
- Flexibly accommodate different types of promotion programs and allowances.
- Reduce the administrative burden and errors that are associated with monitoring promotion performance and processing claims.
- Improve cash flow forecasts by accruing for future liability.
- Have a quantified basis for ongoing and future negotiations with customers about promotions.

## Review details of a promotional fund and trade allowance agreement

A trade allowance agreement is an incentive program where pay-for-performance monetary rewards are offered to customers that achieve specific volume targets and/or behavioral goals. Promotional funds are budgeted expenditures. In that way, the promotional campaigns can be captured.

### Promotional fund

Funds that are allocated to trade allowance agreements are recorded on the **Funds** page. To open the **Funds** page, select **Sales and marketing** \> **Trade allowances** \> **Funds** \> **Funds**.

![Funds page](./media/trade-allowance-management-funds-page.png "Funds page")

On the **Funds** page, you can view the details of promotional funds.

The **General** FastTab shows the period that the fund is valid for and its budgeted amount. In the **Status** field, a value of **Approved** indicates that the fund is ready to be allocated to promotion agreements.

The **Customers** FastTab shows the customer hierarchy. To select the customers that the fund targets, drag them so that they are under **Fund customers**. This FastTab also shows how the total amount of the fund is distributed.

The **Items** FastTab shows the items that are included in the promotion.

### Trade allowance agreement

After the fund definition is in place, the next step in promotion planning is to register promotion contracts (which are known as trade allowance agreements), allocate funds, and define performance goals for each merchandizing event.

Trade allowance agreements are recorded on the **Trade allowance agreements** page. To open the **Trade allowance agreements** page, select **Sales and marketing** \> **Trade allowances** \> **Trade allowance agreements**.

![Trade allowance agreements page](./media/trade-allowance-management-agreements-page.png "Trade allowance agreements page")

#### Header

Select **Header** to switch to the Header view.

On the **General** FastTab, the **Order to** and **Order from** fields define the period when the agreement is valid. An approval status of **Internal approved** for the agreement indicates that the agreement isn't yet valid and can't be applied during sales order processing.

The **Analysis** section of the **General** FastTab contains important fields that define the quantities and costs that are used for promotion evaluation:

- The **Base units** field specifies the quantity of products that must be sold to the selected customers before the promotion is applied.
- The **Calculated ship quantity** value is calculated based on the **Lift percent** value, which is a planned target increase for this promotion.
- The **Trade allowance cost** field is calculated based on the quantities of the various events in the trade allowance agreement.

On the **Customers** FastTab, in the list on the left, you can select and view customer groups, which are set up as predefined hierarchies. You can then select the whole hierarchy or specific accounts as targets for the allowance agreement.

On the **Items** FastTab, as on the **Items** FastTab of the **Funds** page, products are added to the agreement to associate its sales with the allowance that was agreed on.

On the **Funds** FastTab, you can view the promotion funds that are associated with this contract. You can also view the contract's event cost allocation. An event cost allocation of 100 percent means that this promotion will be financed exclusively from one fund. Alternatively, a promotion agreement can draw on several funds, and can use equal or differential percentage allocation.

#### Lines

Next, select **Lines** to switch to the Lines view.

The **Merchandizing events** tab shows the types of events that this agreement covers. Examples include bill-back events and lump sum events.

When you select the merchandizing event and then select the **Amounts** tab, the details for the event are found.

![Trade allowance agreement lines](./media/trade-allowance-management-agreements-lines.png "Trade allowance agreement lines")

In the **Trade allowance lines** section, you specify the quantity or amount ranges that the customer must achieve for definitions to obtain the rewards.

In the case of a merchandizing event of the **Lump sum** type, the **Amounts** tab shows the quantity that will be paid to the customer in the form of a deduction when the customer achieves specific performance. An approval status of **Open** indicates that the lump sum hasn't yet been paid.

Finally, to apply the agreement to sales orders that meet the agreement's conditions, you must set the agreement's status to **Confirmed**. On the **Trade allowance** page, on the Action Pane, select **Confirmed**.

## Perform sales under the planned merchandising event and generate bill-back claims

When you create a sales order that has lines that fulfill the requirements of the agreement, you can view the related information on the **Sales order** page by selecting **Sales order line** \> **View** \> **Price details**.

On the **Price details** page, on the **Rebates** FastTab, the sales clerk can see a bill-back from the valid trade allowance agreement (the rebate program ID is shown) and the total amount that is applied to the line. This amount is calculated by multiplying the line quantity by the bill-back amount per product unit that applies, according to the conditions of the bill-back agreement. This amount is also shown in the **Rebate amount** field in the **Margin estimation** section of the **Price details** page.

You can generate the invoice for the sales order from the **Sales order** page. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**. Then, on the **Posting invoice** page, select **OK**. When the sales invoice is posted, a corresponding bill-back claim is generated for each invoice line.

Select **Sales and marketing** \> **Trade allowances** \> **Bill back workbench**. On the **Bill back workbench** page, notice that the claims that were created for the sales order have a status of **To be calculated**.

> [!NOTE]
> On the **Procurement and sourcing parameters** page, on the **Prices** tab, verify that the **Enable price details** option is set to **Yes**. If the option is set to **No**, you won't be able to view the rebates.

## Process claims and pass them as deductions to A/R

The next steps in the process for handling bill-backs are to review, calculate, and approve claims, and then convert them into deductions.

The Bill back workbench is where the promotion agreement owner periodically reviews and processes the claims that are generated. It's also where the A/R administrator converts the approved claims into deductions or regular payments, depending on the payment method for the claim.

On the **Bill back workbench** page, you can review the claim lines. If there are different lines that have quantities, and if the bill-back depends on ranges of quantities, the claims must be recalculated for any cumulative effect.

### Recalculate claims

To recalculate the claims, on the Action Pane, select **Cumulate**. Then, in the **Cumulate rebates** dialog box, select the customer.

As a result of the recalculation, the program generates new claims for the amounts to adjust the original claims to the qualifying amount per unit. One adjustment claim is generated for each unique combination of a customer, an item, a currency, a unit of measure, inventory dimensions, financial dimensions, and a sales tax group. These adjustment claims have the same reference to the sales order and invoice number as the claims that are being adjusted (that is, the claims that were originally created from the sales document).

After the recalculation is completed, the status of the claims is changed to **Calculated**, and the **Bill back workbench** page shows the claim recalculations. To approve the recalculations, on the Action Pane, select **Approve**.

### Process claims and pass them to A/R

The claims are now ready for A/R processing. To process them, on the Action Pane, select **Process**. Then, in the **Process rebates** dialog box, select the customer.

Together, the messages in the Message Center and the fact that the status of the claims has changed to **Mark** indicate that a journal posting has caused the following events to occur. (The journal that is posted is the Rebate accrual journal, as specified in the A/R parameters.)

- The claims have been transferred to the temporary customer balance as deductions.
- The Rebate accrual account has been credited to represent the future liability for the customer.
- The Rebate expense account has been debited to recognize the cost that was incurred in connection with the sales.

To complete the process, the A/R clerk must now handle the accrual deductions by transferring them to the customers balance as a credit note (liability).

Select **Sales and marketing** \> **Customers** \> **All customers**, and use the filter to find the desired customer. On the Action Pane, select **Collect** \> **Settle transactions**. Then, on the **Settle transactions** page, select **Functions** \> **Bill back program**. This rebate page shows all the bill-back claims that were previously processed.

If you want to create a credit note, select the **Mark** check box for all lines, and then select **Functions** \> **Create credit note**.

A message bar informs you that a journal has been posted. (The journal that is posted is the AR consumption journal, as specified in the A/R parameters.) As a result, the real liability (credit) amount has been moved to the customer balance. Financially, this situation implies that the following events have occurred:

- The customer's Receivable account has been credited.
- The Rebate accrual account has been debited.

To approve a merchandising event of the **Lump sum** type, select the event on the **Trade allowance agreements** page, and then, on the **Amount** tab, select **Approve**.

## Settle the deduction that is due and the customer short-pay by using the Deduction workbench

Often, in anticipation of bill-backs, customer choose to short-pay selected invoices. To prevent payment reconciliation issues in the future, the A/R clerk registers those short-pays as deductions when he or she records the actual customer payments. Then, on the Deduction workbench, those customer deductions can easily be settled against the claim amounts that are due from the company.

To register a customer's short-pay in the Payment journal, select **Accounts receivable** \> **Payments** \> **Payment journal**, and create a new payment journal. Then, on the Action Pane, select **Deductions**. On the **Deduction** page, you can create and track the amount that was short-paid.

## Analyze the effectiveness of the promotion and fund consumption

To get an overview of the program's key statistics and fund use, you can use several reports and analytical views that are available in Trade allowance management.

Select **Sales and marketing** \> **Trade allowances** \> **Trade allowance activity** \> **Trade allowance activity**.

On the **Trade allowance activity** page, the **Overview** tab shows the main details of the trade allowance agreement. The other tabs show more specific details about the associated documents, payments, and other events that are related to the program.

Select the **Summary** tab to view the total quantity of products that have been sold under the promotion, the sales amount that has been invoiced, and the bill-backs and lump sums that have been paid.

Select the **Bill back credits** tab to view the details of individual bill-backs that have been credited to the customer.

To get a more analytical overview of the various performance measures for the promotion, you can use the Analysis view.

Select **Save**.
