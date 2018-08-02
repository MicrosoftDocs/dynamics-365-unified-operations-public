---
# required metadata

title: Trade allowance management
description: This topic describes Trade allowance management for Microsoft Dynamics 365 for Finance and Operations.
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

Trade allowance management helps companies manage sales promotion programs that offer retail customers pay-for-performance monetary rewards for achieving volume and behavioral goals. 

This topic provides an overview for the most common tasks in managing a sales promotion program. The overview covers the following tasks:
-	Review the promotional fund and a trade allowance agreement
-	Perform sales under the planned merchandising event and generate bill-back claims
-	Process claims and pass them as deductions to A/R
-	Settle the deduction that is due and customer short-pay in the Deduction workbench
-	Analyze the effectiveness of the promotion and fund consumption

## Audience and purpose

The information in this document is intended for business decision makers in enterprise companies, in positions such as purchase manager, chief financial officer (CFO), and accounting manager, who have the following responsibilities:
-	High-level budgets and fund allocation 
-	Planning and analyzing sales promotions 
-	Managing staff that processes bill-back claims, runs payments based on merchandizing events, and settles short-pays and deductions 
-	People in these roles are looking for ways to achieve these goals: 
-	Better use marketing promotion funds. 
-	Flexibly accommodate different types of promotion programs and allowances. 
-	Reduce administrative burden and errors that are associated with monitoring promotion performance and processing claims. 
-	Improve cash flow forecasts by accruing for future liability. 
-	Have a quantified basis for ongoing and future negotiations with customers about promotions. 

## Review details of a promotional fund and trade allowance agreement

A trade allowance agreement is an incentive program which consists in offering “pay-for-performance” monetary rewards to customers for achieving specific volume targets and/or behavioral goals. To capture these promotional campaigns, a promotional fund is a budgeted expenditure. Funds allocated to trade allowance agreements are recorded on the **Funds** page.

To open the **Funds** page, select **Sales and marketing** > **Trade allowances** > **Funds** > **Funds**. 

![Trade allowance management funds page](./media/trade%20allowance%20management%20funds%20page.png  "Trade allowance management funds page")

On the **Funds** page, you can view the details about the fund. 

Under the **General** FastTab, the period for which the fund is valid is defined as well as its budgeted amount. In the **Status** field, the **Approved** value indicates that the fund is ready to be allocated to promotion agreements.  

Under the **Customers** FastTab, the customer hierarchy is found. To select the customers who the fund is targeting at select them and drag them under **Fund customers**. How the total amount of the fund is distributed can also be found on this tab.  

Under the **Items** FastTab, the items that will be included in the promotion are found. 

After the fund definition is in place, the next step in promotion planning is to register promotion contracts (which are known as trade allowance agreements), allocate funds, and define performance goals for each merchandizing event. Trade allowance agreements are recorded in the **Trade allowance agreements** page. 

![Trade allowance management agreements page](./media/trade%20allowance%20management%20agreements%20page.png  "Trade allowance management agreements page")

To open the **Trade allowance agreements** page, select **Sales and marketing** > **Trade allowances** > **Trade allowance agreements**.

Select **Header** to switch to **Header view**. 

Under the **General** Fasttab, the period when the agreement is valid, as specified by the **Order to** and **Order from** fields. The agreement status value **Internal approved** indicates that the agreement isn’t yet valid and can’t be applied during sales order processing.

The **Analysis** section on the **General** FastTab contains key fields that define the quantities and costs that are used for promotion evaluation:
- The **Base units** field specifies the quantity of products that must be sold to the selected customers before the promotion is applied.
- The **Calculated ship quantity** value is calculated based on the Lift percent value, which is a planned target increase for this promotion.
- The **Trade allowance cost** field is calculated based on the quantities of the different events in the trade allowance agreement.

On the **Customers** FastTab, in the list on the left, you can select and view customer groups, which are set up as predefined hierarchies, and then select the whole hierarchy or specific accounts as targets for this allowance agreement.

On the **Items** FastTab, as in the fund setup, the products are added to the agreement to associate its sales with the agreed allowance. 

Clicking on the **Funds** Fasttab, you can see the promotion funds associated with this contract and its **Event cost allocation**. An event cost allocation of 100 percent means that this promotion will be financed exclusively from one fund. Alternatively, a promotion agreement can draw on several funds, and can use equal or differential percentage allocation. 

Click **Lines** to switch to the Lines view. 

The **Merchandizing events** tab shows the types of event that are covered by this agreement. For example, these could be bill-back and lump sum. 

When selecting the merchandizing event and then clicking the **Amounts** tab, the details for the event are found. 

![Trade allowance agreements lines](./media/trade%20allowance%20management%20agreements%20lines.png  "Trade allowance agreements lines")

In the **Trade allowance lines** section, you specify the quantity or amount ranges that the customer must achieve for definitions to obtain the rewards. 

In the case of a merchandizing event of the **Lump sum** type, in the **Amounts** tab you could see the quantity that will be paid to the customer in the form of a deduction when the customer achieves specific performance. To indicate that the lump sum hasn’t yet been paid, the approval status would be set to **Open**. 

Finally, to apply the agreement to sales orders that meet the agreement’s conditions the agreement’s status must be set to Confirmed, clicking **Confirmed** on the Action Pane in the Trade allowance page. 

## Perform sales under the planned merchandising event and generate bill-back claims

When creating a sales order with lines that fulfills the requirements of the agreement, you can see the related information on the **Sales order** page and clicking on **Sales order line** > **View** > **Price details**. 

On the **Price details** page, click the **Rebates** FastTab. 

On the **Rebates** FastTab, the sales clerk can see that a bill-back from the valid trade allowance agreement (here you can see the rebate program ID) and the total amount which is applied to the line. This amount is calculated as the line quantity multiplied by the bill-back amount per product unit that applies according to the conditions of the bill-back agreement. This amount is also shown in the **Rebate amount** field in the **Margin estimation** section of the **Price details** page. 

When the invoice is generated for the Sales order, clicking **Invoice** on the **Sales order** page, on the Action Pane, on the **Invoice** tab, in the **Generate** group. Then, click **OK** in the Posting Invoice page.  When the sales invoice is posted corresponding bill-back claim is generated for each invoice line. 

Under **Sales and marketing** > **Trade allowances** > **Bill back workbench** you can notice the claims created for the sales order that have a status of **To be calculated**. 

**Note**: On the **Procurement and sourcing parameters** page, on the **Prices** tab, verify that the **Enable price details** option is set to **Yes**. If the option is set to **No**, you won’t be able to view the rebates.

## Process claims and pass them as deductions to A/R

The next steps in the bill-back handling process are to review, calculate, and approve claims, and convert them into deductions.  

The Bill back workbench is where the promotion agreement owner periodically reviews and processes the claims that are generated. It’s also where the A/R administrator converts the approved claims into deductions or regular payments, depending on the claim payment method. 

On the **Bill back workbench** page, you can review the claim lines.  If there are different lines with quantities and the bill-back is dependent on ranges of quantities, the claims must be recalculated for any cumulative effect. 

To recalculate the claims click **Cumulate** on the Action Pane and select the customer in the **Cumulate rebates** dialog box.

As a result of the recalculation, Dynamics AX creates new claims for the amounts (one for each unique combination of customer, item, currency, unit of measure, inventory dimensions, financial dimensions, and sales tax group) to adjust the original claims to the qualifying amount per unit. These adjustment claims have the same reference to the sales order and invoice number as the claims that are being adjusted (that is, the claims that were originally created from the sales document). 

The status of the claims is changed to **Calculated**. 

On the **Bill back workbench** page claim recalculations will be shown and can be approved by clicking on **Approve**, on the Action Pane. 

The claims are now ready for A/R processing. To process them, click on Process on the Action Pane. Then, in the **Process rebates dialog** box, the customer must be selected. 

Together, the messages in the Message Center and the fact that the status of the claims has changed to **Mark** indicate that a journal posting (the Rebate accrual journal, as specified in the A/R parameters) has caused the following events to occur: 
- The claims have been transferred to the temporary customer balance as deductions. 
- The Rebate accrual account has been credited to represent the future liability toward the customer. 
- The Rebate expense account has been debited in recognition of the cost that was incurred in connection with the sales. 

To complete the process, the A/R clerk will now handle the accrual deductions by transferring them to the customers balance as a credit note (liability). 

Find the customer desired going to **Sales and marketing** > **Customers** > **All customers** and using the filter. On the Action Pane, click **Collect** > **Settle transactions**. And then, on the **Settle transactions** page, click **Functions** > **Bill back program**. On this rebate page, you will see all the bill-back claims that were previously processed. 

If desired, you can create a credit note by selecting the **Mark** check box for all lines, and then click **Functions** > **Create credit note**. 

The message bar informs the user that a journal (AR consumption journal, as specified in the A/R parameters) has been posted. As a result, the real liability (credit) amount has been moved to the customer balance. Financially, this situation implies that the following events have occurred: 
- The customer’s Receivable account has been credited. 
- The Rebate accrual account has been debited. 

To approve a merchandising event of the **Lump sum** type, select the event in the **Trade allowance agreements** page, and click Approve on the **Amount** tab. 

## Settle the deduction that is due and customer short-pay in the Deduction bench

The customer often, in anticipation of those bill-backs chooses to short-pay selected invoices. To avoid potential payment reconciliation issues in the future, the A/R clerk registers those short-pays as deductions when he or she records the actual customer payments. After those customer deductions are in the system, they can easily be settled against the claim amounts that are due from the company in the Deduction workbench.

To register the customer’s short-pay in the Payment journal, go to **Accounts receivable** > **Payments** > **Payment journal**, create a new payment journal and click **Deductions** on the Action Pane once it is created. On the **Deduction** page, you can create and keep track of the amount short-paid. 

## Analyze the effectiveness of the promotion and fund consumption

To get an overview of the program’s key statistics and the fund’s usage, they use several reports and analytical views that are available in Trade allowance management.

Click **Sales and marketing** > **Trade allowances** > **Trade allowance activity** > **Trade allowance activity**. 

On the **Trade allowance activity** page, the **Overview** tab shows the main details of the trade allowance agreement, whereas other tabs show more specific details about the associated documents, payments, and other events that are related to the program. 

Click the **Summary** tab to see the total quantity of products that have been sold under the promotion, the sales amount that has been invoiced, and the bill-backs and lump sums that have been paid. 

Click the **Bill back credits** tab to see the details of individual bill-backs that have been credited to the customer. 

To get a more analytical overview of the various performance measures for the promotion, the Analysis view can be used. Click **Sa
