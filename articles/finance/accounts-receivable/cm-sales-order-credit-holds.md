---
title: Credit holds for sales orders
description: Learn about how to set up rules used to place a sales order on credit hold, including an outline on setting up blocking rules and exclusion rules. 
author: JodiChristiansen
ms.author: twheeloc
ms.topic: article
ms.date: 03/28/2024
ms.custom:  
ms.reviewer: twheeloc 
audience: Application User
ms.search.region: Global
ms.search.validFrom:
ms.search.form:
ms.dyn365.ops.version: 
---

# Credit holds for sales orders
[!include [banner](../includes/banner.md)]

This article describes how to set up rules that are used to place a sales order on credit hold. The credit management blocking rules can apply to an individual customer or a group of customers. Blocking rules define responses to the following circumstances:

1. Number of days overdue
2. Accounts status
3. Terms of payment
4. Credit limit expired
5. Overdue amount
6. Sales order amount
7. Portion of available credit used

In addition, two parameters control additional scenarios that block a sales order:

1. Change in payment terms
2. Change in settlement discounts

## Set up blocking rules and exclusion rules

When a customer initiates a sales transaction, the information on the sales order is reviewed against a set of blocking rules. Those rules guide the decision of whether or not to extend credit to the customer and allow the sale to move forward. You can also define exclusions that override the blocking rules and allow a sales order to be processed. You can set up blocking rules and exclusion rules on the **Credit management > Setup > Credit management setup > Blocking rules** page.

As of version 10.0.21, the blocking rules in Credit management are re-architected in the following ways:

- Extensibility requests are enabled, and blocking rules can be created. 
- The **Release sales order** checkbox is available for all blocking rules. Previously, it was available only for the Sales order blocking rule. When this checkbox is selected, the exclusion rule releases the sales order without considering any other rules that can block sales orders. This checkbox is available only for the **Exclusion** rule type.

Blocking rules and Credit management checkpoints are required to check the credit limit on a sales order. In version 10.0.34 and earlier, there was a bug that allowed the credit check without the blocking rules setup. As of version 10.0.35, this bug has been fixed, and blocking rules are required with Credit management. 

### Days overdue

Open the **Days overdue** tab if the blocking rule applies to a customer with one or more invoices that have been past due for a certain number of days.
1. Select the range of customer that this rule is **Valid for**.
   - Select **Table** if the rule applies to a specific customer.
   - Select **Group** if the rule is applied at the customer group level. 
   - Select **All** if the rule applies to all customers.
2. After the range is selected, specify the **Account/group** used in the range.
   - For the **Table** range, the lookup provides a list of customers to select. 
   - Select a **Group** if the rule applies to a customer credit management group.
   - Select **All** if the rule applies to all customers. 
3. Select a **Risk group** to use criteria for applying a credit management hold on customers that are grouped by a common set of factors. Factors can include their Dun and Bradstreet rating, the number of years that they've been in business, and the amount of time they've been your customer. If you're using a risk group, an account group must be selected first. 
4. Select the type of rule that you are setting up. The **Blocking** option creates a rule that blocks an order. The **Exclusion** option creates a rule that excludes another rule from blocking an order. 
5. Select a **Value type**. The default entry is a fixed number of days. If you are creating an exclusion, you can specify a fixed number of days or an amount instead. 
6. Enter the number of days **Overdue** allowed for the selected blocking rule before an order is placed on credit management hold for review. The number of days overdue represents an additional number of grace days added to the number of days beyond the payment due date before the invoice is considered overdue. If you specified the **Value type** as an amount for an exclusion, enter an amount and a currency for that amount. This amount represents the total amount overdue for the customer. It isn't the sales order amount.

**Example 1:** You want to block sales orders (put them on a credit hold) for all customers if they have invoices that are more than 61 days past due. However, you want to exclude some customers (or groups) from a credit hold if they're less than 100 days past due. Provided that the value type is the same, the exclusion rule overrides the blocking rule. 

[![Screenshot that shows a days overdue example where only the Days value type is used.](./media/DaysOverdueDaysvaluetype.png)](./media/DaysOverdueDaysvaluetype.png)

**Example 2:** You want to block sales orders (put them on a credit hold) for all customers if they have invoices that are more than 61 days past due. However, you want to exclude customer US-001 from a credit hold if their total amount overdue is less than $1,000. In addition, you want to exclude customer US-009 from a credit hold if their overdue amount is less than $2,500. Because the **Amount** value type differs from the **Days** value type, the exclusion rule at the customer (or group) level doesn't override the blocking rule. In this case, the **Release sales order** checkbox must be selected for this scenario to work. 

[![Screenshot that shows a days overdue example where the Days and Amount value types are used.](./media/DaysOverdueDaysAmountvaluetype.png)](./media/DaysOverdueDaysAmountvaluetype.png)


### Account status

Open the **Account status** tab if the blocking rule applies to a customer with the selected account status.
1. Select the type of rule that you are setting up. **Blocking** creates a rule that blocks an order. **Exclusion** creates a rule that excludes a rule from blocking an order. 
2. Select the **Account status** that causes the rule to place a sales order on hold or to exclude it.

### Terms of payment

Select **Terms of payment** if the blocking rule applies to the selected payment term.
1. Select the type of rule that you are setting up. **Blocking** creates a rule that blocks an order. **Exclusion** creates a rule that excludes a rule from blocking an order. 
2. Select the **Terms of payment** that cause the rule to place a sales order on hold or to exclude it.

### Credit limit expired

Open the **Credit limit expired** tab if the blocking rule applies to customers with credit limits that have expired.
1. Select the range of customers that this rule is **Valid for**.
   - Select **Table** if the rule applies to a specific customer.
   - Select **Group** if the rule is applied at the customer group level. 
   - Select **All** if the rule applies to all customers.
2. After the range is selected, specify the **Account/group** used in the range.
   - For the **Table** range, the lookup provides a list of customers to select from. 
   - Select a **Group** if the rule applies to a customer credit management group.
   - Select **All** if the rule applies to all customers. 
3. Select a **Risk group** to further limit the list of customers that will be placed on credit management hold. If you're using a risk group, an account group must be selected first.
4. Select the type of rule that you are setting up. 
   - Select **Blocking** to create a rule that blocks an order. 
   - Select **Exclusion** to create a rule that will exclude another rule from blocking an order. 
5. Enter the **Days credit limit expired** for the selected blocking rule before an order is placed on credit management hold. The number of days overdue represents additional grace days that are added to the number of days that the credit limit has been expired.

### Overdue amount

Open the **Overdue Amount** tab if the blocking rule applies to customers with overdue invoice amounts.
1. Select the range of customer that this rule is **Valid for**.
   - Select **Table** if the rule applies to a specific customer.
   - Select **Group** if the rule is applied at the Customer group level. 
   - Select **All** if the rule applies to all customers.
2. Once you have specified the range, you must specify the **Account/group** used in the range.
   - For the **Table** range, the lookup provides a customer lookup. 
   - Select a **Group** if the rule applies to a customer credit management group.
   - Select **All** if the rule applies to all customers. 
3. Select a **Risk group** if you want to further limit the list of customers that go on credit management hold. If you're using a risk group, an account group must be selected first.
4. Select the type of rule that you are setting up. 
   - Select **Blocking** to create a rule that blocks an order. 
   - Select **Exclusion** to create a rule that excludes another rule from blocking an order. 
5. Enter the **Overdue amount** for the selected blocking rule before an order is placed on credit management hold for review. 
6. Select the **Value type** that defines the type of value that is used to test how much of the credit limit has been used. Blocking rules and exclusion rules allow a percentage only for **Overdue amount**. The **Threshold** relates to the **Credit limit**.
7. Enter the **Credit limit threshold** value for the selected rule before a customer goes on credit management hold. 
8. The rule checks that the **Overdue amount** is exceeded and the **Credit limit threshold** is exceeded. 

### Sales order 

Select **Sales order** if the blocking rule applies to value of the sales order.
1. Select the range of customer that this rule is **Valid for**.
   - Select **Table** if the rule applies to a specific customer.
   - Select **Group** if the rule is applied at the Customer group level. 
   - Select **All** if the rule applies to all customers.
2. After the range is selected, specify the **Account/group** used in the range.
   - For the **Table** range, the lookup provides a customer lookup. 
   - Select a **Group** if the rule applies to a customer credit management group.
   - Select **All** if the rule applies to all customers. 
3. Select a **Risk group** if you want to further limit the list of customers that go on credit management hold. If you're using a risk group, an account group must be selected first.
4. Select the type of rule that you are setting up.  
   - Select **Blocking** to create a rule that blocks an order. 
   - Select **Exclusion** to create a rule that will exclude another rule from blocking an order. 
5. Enter the **Sales order amount** for the selected blocking rule before an order is placed on credit management hold. 

### Credit limit used

Select **Credit limit used** if the blocking rule applies to the customer credit limit amount utilized.
1. Select the range of customer that this rule is **Valid for**.
   - Select **Table** if the rule applies to a specific customer.
   - Select **Group** if the rule is applied at the Customer group level. 
   - Select **All** if the rule applies to all customers.
2. After the range is selected, specify the **Account/group** used in the range.
   - For the **Table** range, the lookup provides a customer lookup. 
   - Select a **Group** if the rule applies to a customer credit management group.
   - Select **All** if the rule applies to all customers. 
3. Select a **Risk group** if you want to further limit the list of customers that go on credit management hold. If you're using a risk group, an account group must be selected first.
4. Select the type of rule that you are setting up.
   - Select **Blocking** to create a rule that blocks an order. 
   - Select **Exclusion** to create a rule that will exclude another rule from blocking an order. 
5. Select the **Threshold remaining** that defines the percentage of the credit limit that will block the sales order. If the value of an order increases the amount of the credit limit used above the percentage, the order is placed on hold. 

## Put a sales order on hold based on other criteria
  
### Rank payment terms	

You can force the credit control rules to be executed when payment terms are changed. You must rank the payment terms and assign them a ranking value. If you change the payment terms on the order to payment terms that are ranked higher than the old payment terms, the order is sent to credit management and requires approval.

To set up the payment terms rankings, follow these steps.
1. Go to **Credit management \> Setup \> Credit management setup \> Rank payment terms**.
2. In the **Terms of payment** field, select payment terms to rank. 
3. In the **Rank** field, select the rank of the payment terms. The values are all relative to each other. Therefore, you can use 1,2,3 or 10,20,30. You can also use the same value for most of the payment terms, so that only one or two payment terms trigger a credit check.

### Rank settlement discounts	

You can force the credit control rules to be executed when settlement discounts are changed. You must rank the settlement discounts and assign them a ranking value. If you change the settlement discounts on the order to settlement discounts that are ranked higher than the old settlement discounts, then the order is sent to credit management and require approval.

You can set up the payment terms rankings on the **Credit management > Setup > Credit management setup > Rank settlement discounts** page.

1. Select the **Cash discount** that you want to rank. The **Description** of the settlement discount is displayed.
2. Select the **Rank** value. The values are all relative to each other. Therefore, you can use 1,2,3 or 10,20,30. You can also use the same value for most of the settlement discounts, so that only one or two settlement discounts trigger the credit check.

## Sequence the application of rules

Rules are run in a specific order to suit the needs of your organization. 

- Any exclusion rule can override all rules that might block a sales order. In each blocking rule, you can create an exclusion rule and mark the **Release Sales order** option. The order won't be put on hold if that exclusion rule is true, and no other rules are checked.
- Blocking rules can place the order on hold.
- Exclusion rules are run after blocking rules. Exclusion rules only affect the rule on which they are defined. 
- Blocking and exclusion rules are run in **Table**, then **Group**, and then **All** orders. Because of this order of processing, it's possible to have a blocking rule at the **All** level that won't run because of an exclusion rule at the **Table** or **Group** level. This fact is true when the value type of the blocking and exclusion rules is the same. See the examples in the [Days overdue](#days-overdue) section earlier in this article.
- Exclusions don't override the blocking rule if they are at the same level. For example, an exclusion rule at the **Group** level won't override the blocking rule at the **Group** level. You don't need to set up exclusions at the **All** level except as noted earlier with the use of the **Release sales order** checkbox. 

The behavior of the **Credit limit used** rule changes based on the settings for the **Check credit limit for sales order** parameter on the **Credit and collections parameters** page.
- If the parameter is set to **No**, then the **Credit limit used** rule isn't run. 
- If the parameter is set to **Yes**, then the **Credit limit used** rule is run.
- Blocking rules must be set up to put the sales order on a credit hold.  

## Settings that will change the way an order is placed on hold

Orders can be excluded from credit management even if there are rules in place. 

- If you change the **Exclude customer from credit management** in **All customers > Select a customer > Credit and collections** FastTab to **Yes**, no orders for that customer are processed.
- If you change the **Exclude from credit management** on the **Sales orders header** in the **Credit management fast tab** to **Yes**, then the credit management rules aren't processed. 

## Processing orders on hold using the credit management hold list

The **Credit management hold** list displays all sales orders placed on hold and the holds removed when the credit issues have been mitigated. You can view the hold list on the **All credit holds** page (**Credit management > Credit management hold list > All credit holds**).
Sales orders from all legal entities are sent to the same credit management hold list, providing a centralized view of all transactions that require attention. Users see information for the legal entities that they have access to. Go to **Credit and collections > Setup > Credit management setup > Credit management reasons** in each legal entity where the credit hold is released to set up **Release reason codes**. 

A sales order can be placed in the hold list for the following reasons:
1. The customer has an invoice that has been overdue for a specified number of days. 
2. The order has a specific account status.
3. The order has specific terms of payment.
4. The customer has an expired credit limit.
5. The customer has an overdue amount and has used a specified percentage of its credit limit.
6. The sales order exceeds a certain amount.
7. The customer has exceeded a certain percentage of its credit limit.
8. The payment terms differ from the default payment terms for the customer.
9. The settlement discounts differ from the default settlement discount for the customer.

The blocking reason is displayed for each sales order in the hold list. If there's more than one reason for the hold, the reason displays **Multiple**. Use **Blocking reasons** to view the reasons why the sales order was placed on hold. You can also view the **Blocking reasons** in a FactBox.

### Releasing orders from the hold list for processing

After the reasons for the hold are mitigated, the sales orders can be released for further processing.

1. Select a line in the hold list. You can release multiple orders by selecting more than one line.
2. Select a **Release reason** for the order that has been selected for release.  
3. Enter the **Review date** for each order that has been selected for release.  
4. Select the **Release** menu on the action pane to release an order. This menu is available after transactions have been selected. The user is presented with two options:
   - **With posting** - This option removes the hold and posts the document using the same posting process used when it was placed on hold. For example, if the sales order confirmation was placed on hold, the sales order confirmation would be completed after the release. The sales order posting page lets the user post the confirmation.
   - **Without posting** - This option removes the hold without doing any further processing. The sales order can be manually posted.

### Rejecting orders in the hold list
You can use the **Reject** menu on the action pane to reject a sales order.
1. Select a line in the hold list. You can release multiple orders by selecting more than one line.
2. The order is removed from the hold list and the sales order header is updated to show that the order was rejected.

### Automatically releasing credit management holds
Sales orders are placed in the hold list based on the blocking rules. Some reasons for the holds may changes over time if the sales order remains in the hold list for a period of time. For example, a customer may pay their bill, freeing up their credit limit. 

You can use the **Evaluate for release** menu to review the sales orders in the hold list and automatically release them if the reason for the hold has been mitigated.
1.	Select the **Evaluate for release** menu.
2.	Select **Process blocking rules** to review all of the sales orders. Select **Process blocking rules for selected lines** to review only the lines that you have selected.
3. A slider will appear so that you can select a single customer. Leave the customer drop down blank for all customers. 
4. When you click **Ok**, the process is run in the background, and you can continue working on other tasks. If you select batch processing before you click on **Ok**, the process will run in batch when you click **Ok**. It may take some time to process the orders on hold in the list. Click **Refresh** to update the status of the orders. 
5.	If a blocking reason is no longer applicable for an order, the blocking reason is no longer valid, and you won't see a check mark next to the reason when you view the blocking reasons.
6.	If all of the blocking reasons are cleared, then **Ready to release** is added to the list of blocking reasons. The sales order can be automatically released.
7.	If the **Automatically release** parameter in **Credit and collections > Setup > Credit and collections parameters > Credit > Auto release** tab is set to **With posting**, you'll be prompted to post using the posting page for the document that was blocked.
8.	If the **Automatically release** parameter in **Credit and collections > Setup > Credit and collections parameters > Credit > Auto release** tab is set to **Without posting**, then post the order manually.

### Credit management approval workflow

You can also create **Credit management workflows** to control the release of credit holds. After you have set up workflow using the **Credit management > Setup > Credit management workflows** page, the orders marked for release or rejection will be sent to workflow where they must be approved first before they will be released or rejected. 

If you include the tasks for release with posting or release without posting in your workflow, the workflow approval will release the sales order. If there's a failure in the release process, recall the sales order from workflow, fix the issue that caused the failure, and submit the order to workflow again.

If you don't include the tasks for release with posting or release without posting in your workflow, the workflow approval process enables you to release the sales order manually after the approval is complete.

### Forced credit hold	
  
Sales orders may need to be blocked even though the order doesn't meet the criteria of the blocking rules. For example, a credit manager may be notified of a non-credit related issue with the customer and decide to manually put orders on hold immediately until the issue is cleared up. You can manually force a sales order to be on hold.

1. Open the sales order that you want to place on hold.  
2. Select **Force credit hold** in the **Credit management** tab on the **Credit management** action pane.
3. Select a **Forced hold reason**.
4. Click **OK.** The sales order will be returned to the **Credit management hold list**.

You can also force multiple orders to be on hold using the **Credit management > Periodic tasks > Force credit hold** page. For example, you can place all sales orders on hold for a specific customer.
1. Select **Forced hold reason**. 
2. Click **Records to include** to select the sales orders to place on hold. 
3. Click **OK** to process the selected sales orders.

Sales orders that have been forced on hold can't be processed with workflow.

#### Releasing orders that were added to the credit management hold list with a forced credit hold
Sales orders that have a forced hold reason can't be released automatically. If the sales order was forced on hold and you have used a process that automatically releases sales orders, the sales order shows as **Ready to release** and remains in the hold list. Use the **Release** menu to release the order.
 
## Free text invoices, orders, and project invoice support in Credit management 
Credit management can only be used currently for sales orders. Free text invoices, point of sales orders and call center orders will use the temporary credit limits and insurance/guarantees that are added to adjust the credit limit. They won't use the blocking rules and they won't be placed in the hold list if there is an issue with the credit limit.

There's no support for project invoices in credit management.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
