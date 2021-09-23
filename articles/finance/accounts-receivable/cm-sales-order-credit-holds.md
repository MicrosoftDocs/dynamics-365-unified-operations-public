---
# required metadata

title: Credit holds for sales orders
description: This topic describes the setup of rules used to place a sales order on credit hold. 
author: JodiChristiansen
ms.date: 07/20/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschloma
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: roschlom
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Credit holds for sales orders
[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic describes the setup of rules used to place a sales order on credit hold. The credit management blocking rules can apply to an individual customer, or a group of customers. Blocking rules define responses to the following circumstances:

1. Number of days overdue
2. Accounts status
3. Terms of payment
4. Credit limit expired
5. Overdue amount
6. Sales order amount
7. Portion of available credit used

In addition, there are two parameters that control additional scenarios that will block a sales order

1. Change in payment terms
2. Change in settlement discounts

## Set up blocking rules and exclusion rules

When a customer initiates a sales transaction, the information on the sales order is reviewed against a set of blocking rules that guide the decision of whether or not to extend credit to the customer and allow the sale to move forward. You can also define exclusions that will override the blocking rules and allow a sales order to be processed. You can set up blocking rules and exclusion rules on the **Credit management > Setup > Credit management setup > Blocking rules** page.

As of version 10.0.21, the blocking rules in Credit management have been re-architected in the following ways, to provide more flexibility:

- Extensibility requests have been enabled, so that you can create your own blocking rules.
- The **Release sales order** checkbox is now available for all blocking rules. Previously, it was available only for the Sales order blocking rule. When this checkbox is selected, the exclusion rule will release the sales order without considering any other rules that can block sales orders. This checkbox is available only for the **Exclusion** rule type.

### Days overdue

Open the **Days overdue** tab if the blocking rule applies to customer with one or more invoices that have been past due for a certain number of days.
1. Select the range of customer that this rule is **Valid for**.
   - Select **Table** if the rule applies to a specific customer.
   - Select **Group** if the rule is applied at the customer group level. 
   - Select **All** if the rule applies to all customers.
2. When you have specified the range, you must specify the **Account/group** that will be used in the range.
   - For the **Table** range, the lookup will provide a list of customers to select. 
   - Select a **Group** if the rule applies to a customer credit group.
   - Select **All** if the rule applies to all customers. 
3. Select **Risk group** to use criteria for applying a credit management hold on customers that are grouped by a common set of factors, such as their Dun and Bradstreet rating, the number of years that they've been in business, the amount of time they've been your customer, and so on.  
4. Select the type of rule that you are setting up. The **Blocking** option will create a rule that blocks an order. The **Exclusion** option will create a rule that will exclude another rule from blocking an order. 
5. Select a **Value type**. The default entry is a fixed number of days. If you are creating an exclusion, you can specify a fixed number of days or an amount instead. 
6. Enter the number of days **Overdue** that will be allowed for the selected blocking rule before an order is placed on credit management hold for review. The number of days overdue represents an additional number of grace days that are added to the number of  days beyond the payment due date that the invoice can have before it is considered overdue. If you specified the **Value type** as an amount for an exclusion, then enter an amount and a currency for that amount.

### Account status

Open the **Account status** tab if the blocking rule applies to a customer with the selected account status.
1. Select the type of rule that you are setting up.  **Blocking** will create a rule that blocks an order. **Exclusion** creates a rule that will exclude a rule from blocking an order. 
2. Select the **Account status** that will cause the rule to place a sales order on hold or to exclude it.

### Terms of payment

Select **Terms of payment** if the blocking rule applies to the selected payment term.
1. Select the type of rule that you are setting up.  **Blocking** will create a rule that blocks an order. **Exclusion** creates a rule that will exclude a rule from blocking an order. 
2. Select the **Terms of payment** that will cause the rule to place a sales order on hold or to exclude it.

### Credit limit expired

Open the **Credit limit expired** tab if the blocking rule applies to customers with credit limits that have expired.
1. Select the range of customer that this rule is **Valid for**.
   - Select **Table** if the rule applies to a specific customer.
   - Select **Group** if the rule is applied at the Customer group level. 
   - Select **All** if the rule applies to all customers.
2. Once you have specified the range, you must specify the **Account/group** used in the range.
   - For the **Table** range, the lookup will provide a list of customers to select from. 
   - Select a **Group** if the rule applies to a customer credit management group.
   - Select **All** if the rule applies to all customers. 
3. Select a **Risk group** to further limit the list of customers that will be placed on credit management hold. 
4. Select the type of rule that you are setting up. 
   - Select **Blocking** to create a rule that blocks an order. 
   - Select **Exclusion** to create a rule that will exclude another rule from blocking an order. 
5. Enter the **Days credit limit expired** for the selected blocking rule before an order is placed on credit management hold. The number of days overdue represents additional grace days that are added to the number of days that the credit limit has been expired.

### Overdue amount

Open the **Overdue Amount** tab if the blocking rule applies to customers with overdue amounts.
1. Select the range of customer that this rule is **Valid for**.
   - Select **Table** if the rule applies to a specific customer.
   - Select **Group** if the rule is applied at the Customer group level. 
   - Select **All** if the rule applies to all customers.
2. Once you have specified the range, you must specify the **Account/group** used in the range.
   - For the **Table** range, the lookup will provide a customer lookup. 
   - Select a **Group** if the rule applies to a customer credit management group.
   - Select **All** if the rule applies to all customers. 
3. Select a **Risk group** if you want to further limit the list of customers that go on credit management hold. 
4. Select the type of rule that you are setting up. 
   - Select **Blocking** to create a rule that blocks an order. 
   - Select **Exclusion** to create a rule that will exclude another rule from blocking an order. 
5. Enter the **Overdue amount** for the selected blocking rule before an order is placed on credit management hold for review. 
6. Select the **Value type** that defines the type of value that will be used to also test how much of the credit limit has been used. Blocking rules and exclusion rules allow a percentage only for **Overdue amount**. The Threshold relates to the Credit limit.
7. Enter the **Credit limit threshold** value for the selected rule before a customer goes on credit management hold. This can be an amount or a percentage based on the value type select in the value type.
8. The rule checks that the **Overdue amount** is exceeded and the **Credit limit threshold** is exceeded. 

### Sales order 

Select **Sales order** if the blocking rule applies to value of the sales order.
1. Select the range of customer that this rule is **Valid for**.
   - Select **Table** if the rule applies to a specific customer.
   - Select **Group** if the rule is applied at the Customer group level. 
   - Select **All** if the rule applies to all customers.
2. Once you have specified the range, you must specify the **Account/group** used in the range.
   - For the **Table** range, the lookup will provide a customer lookup. 
   - Select a **Group** if the rule applies to a customer credit management group.
   - Select **All** if the rule applies to all customers. 
3. Select a **Risk group** if you want to further limit the list of customers that go on credit management hold. 
4. Select the type of rule that you are setting up.  
   - Select **Blocking** to create a rule that blocks an order. 
   - Select **Exclusion** to create a rule that will exclude another rule from blocking an order. 
5. Enter the **Sales order amount** for the selected blocking rule before an order is placed on credit management hold. 

### Credit limit used

Select **Credit limit used**  if the blocking rule applies to the customer credit limit amount utilized.
1. Select the range of customer that this rule is **Valid for**.
   - Select **Table** if the rule applies to a specific customer.
   - Select **Group** if the rule is applied at the Customer group level. 
   - Select **All** if the rule applies to all customers.
2. Once you have specified the range, you must specify the **Account/group** used in the range.
   - For the **Table** range, the lookup will provide a customer lookup. 
   - Select a **Group** if the rule applies to a customer credit management group.
   - Select **All** if the rule applies to all customers. 
3. Select a **Risk group** if you want to further limit the list of customers that go on credit management hold. 
4. Select the type of rule that you are setting up.
   - Select **Blocking** to create a rule that blocks an order. 
   - Select **Exclusion** to create a rule that will exclude another rule from blocking an order. 
5. Select the **Threshold remaining** that defines the percentage of the credit limit that will block the sales order. If the value of an order increases the amount of the credit limit used above the percentage, then the order will be placed on hold. 

## Put a sales order on hold based on other criteria
  
### Rank payment terms	

You can force the credit control rules to be executed when payment terms are changed. You must rank the payment terms and assign them a ranking value. If you change the payment terms on the order to payment terms that are ranked higher than the old payment terms, then the order will be sent to credit management and require approval.

You can set up the payment terms rankings on the **Credit management > Setup > Credit management setup > Rank payment terms** page.

1. Select payment terms the **Terms of payment** field to rank; when you select a term, the description will be displayed in the **Description** field.
2. Select the term's rank in the **Rank** field. The values are all relative to each other so you can use 1,2,3 or 10,20,30. You can also use the same value for most of the terms of payment so that only one or two terms of payment will trigger the credit check.

### Rank settlement discounts	

You can force the credit control rules to be executed when settlement discounts are changed. You must rank the settlement discounts and assign them a ranking value. If you change the settlement discounts on the order to settlement discounts that are ranked higher than the old settlement discounts, then the order will be sent to credit management and require approval.

You can set up the payment terms rankings on the **Credit management > Setup > Credit management setup > Rank settlement discounts** page.

1. Select the **Cash discount** that you want to rank. The **Description** of the settlement discount will be displayed.
2. Select the **Rank** value. The values are all relative to each other so you can use 1,2,3 or 10,20,30. You can also use the same value for most of the settlement discounts so that only one or two settlement discounts will trigger the credit check.

## Sequence the application of rules

Rules are run in a specific order that you change to suit the needs of your organization. 

- One instance of the Sales order exclusion rules lets you override all rules that might block a sales order. Create a sales order exclusion rule and mark the **Release Sales order** option. The order will not be put on hold if that exclusion rule is true, and no other rules will be checked.
- Blocking rules can place the order on hold.
- Exclusion rules are run after blocking rules. Exclusion rules will only affect the rule on which they are defined. 
- Blocking and exclusion rules are run in Table, then Group, then All order. Because of this order of processing, it is possible to have a blocking rule at the All level that will not be run because an exclusion rule at the Table or Group level is run.
- Exclusions do not override the blocking rule if they are at the same level. For example, an exclusion rule at the group level will not override the blocking rule at the group level. You will not need to set up exclusions at the All level except as noted above with the one instance of the sales order exclusion rule. 

The behavior of the **Credit limit used** rule will change based on the settings for the **Check credit limit for sales order** parameter found in the Credit and Collections parameter form.
- If the parameter is set to No, then the Credit limit used rule will not be run.
- If the parameter is set to Yes and the **Message when exceeding credit limit** is set to warning, then you will get a warning when the credit limit is exceeded. The **Credit limit used** rules will be run to see if you have rules that you want to be run. However, for this scenario, you would normally not add any rules.
- If the parameter is set to Yes and the **Message when exceeding credit limit** is set to error, then the credit limit will be checked and the order will be put on hold if credit limit is exceeded. In addition, the **Credit limit used** rules will be run to see if there are additional rules that should be run. An error message won't display, but the **Exceeded credit limit** blocking reason will be shown. 

## Settings that will change the way an order is placed on hold

Orders can be excluded from credit management even if there are rules in place. 

- If you change the settings **Exclude customer from credit management** in **All customers > Select a customer > Credit and collections** FastTab to **Yes**, then no orders for that customer will be processed
- If you change the value **Exclude from credit management** on the **sales orders header** in the **Credit management fast tab** to **Yes**, then the credit management rules will not be processed. This setting can only be done by the credit clerk or credit manager.

## Processing orders on hold using the credit management hold list

The Credit management hold list lets credit managers view all sales orders that have been placed on hold and lets them remove the holds when the credit issues have been mitigated. The **Credit management hold list** page shows all sales orders that have been placed on hold. You can view the hold list on the **All credit holds** page (**Credit management > Credit management hold list > All credit holds**).
Sales orders from all legal entities are sent to the same credit management hold list, providing a centralized view of all transactions that require attention. Users will only see information for the legal entities that they have access to.

A sales order can be placed in the hold list for the following reasons:
1. The customer has an invoice that has been overdue for a specified number of days. 
2. The order has a specific account status.
3. The order has specific terms of payment.
4. The customer has an expired credit limit.
5. The customer has an overdue amount and has used a specified percentage of its credit limit
6. The sales order exceeds a certain amount.
7. The customer has exceeded a certain percentage of its credit limit.
8. The payment terms differ from the default payment terms for the customer.
9. The settlement discounts differ from the default settlement discount for the customer.

The blocking reason is displayed for each sales order in the hold list. If there are more than one reason for the hold, the reason will show as **Multiple**. You can use the **Blocking reasons** menu on the Action Pane to view all of the reasons why the sales order was placed on hold. You can also view the **Blocking reasons** in a FactBox.

### Releasing orders from the hold list for processing

When you have researched the reasons for the hold and you have mitigated them, you can release the sales orders for further processing.

1) Select a line in the hold list. You can release multiple orders by selecting more than one line.
2) Select a **Release reason** for the order that has been selected for release.  
3) Enter the **Review date** for each order that has been selected for release.  
4) Select the **Release** menu on the action pane to release an order. This menu will only be available after transactions have been selected. The user is presented with two options:
   - Select **With posting** to remove the hold and post the document using the same posting process that was used when it was placed on hold. For example, if the sales order confirmation was placed on hold, the sales order confirmation would be completed after the release. The sales order posting form will be displayed allowing the user to post the confirmation.
   - Select **Without posting** to remove the hold without doing any further processing. The sales order can be manually posted.

### Rejecting orders in the hold list
You can use the **Reject** menu on the action pane to reject a sales order
1. Select a line in the hold list. You can release multiple orders by selecting more than one line.
2. The order will be removed from the hold list and the sales order header will be updated to show that the order was rejected.

### Automatically releasing credit management holds
Sales orders are placed in the hold list based on the blocking rules. However, some reasons for the holds may changes over time if the sales order remains in the hold list for a period of time. For example, a customer may pay their bill, freeing up their credit limit. 

You can use the **Evaluate for release** menu to review the sales orders in the hold list and automatically release them if the reason for the hold has been mitigated.
1.	Select the **Evaluate for release** menu
2.	Select **Process blocking rules** to review all of the sales orders. Select **Process blocking rules for selected lines** to review only the lines that you have selected.
3. A slider will appear so that you can select a single customer. Leave the customer drop down blank for all customers. 
4. When you click ok, the process is run in the background and you can continue working on other tasks. If you select batch processing before you click on Ok, the process will run in batch when you click Ok. It may take some time to process the orders on hold in the list so use Refresh to update the status of the orders. 
5.	If a blocking reason no longer is applicable for an order, the blocking reason will be considered no longer valid and you will no longer see a check mark next to the reason when you view the blocking reasons.
6.	If all of the blocking reasons are cleared, then a new reason, **Ready to release**, is added to the list of blocking reasons. The sales order can be automatically released.
7.	If the **Automatically release** parameter in **Credit and collections > Setup > Credit and collections parameters > Credit > Auto release** tab is set to **With posting**, then you will be prompted to post using the posting form for the document that was blocked.
8.	If the **Automatically release** parameter in **Credit and collections > Setup > Credit and collections parameters > Credit > Auto release** tab is set to **Without posting**, then you must post the order manually.

### Credit management approval workflow

You can also create **Credit management workflows** to control the release of credit holds. Once you have set up workflow using the **Credit management > Setup > Credit management workflows** page, the orders marked for release or rejection will be sent to workflow where they must be approved first before they will be released or rejected. 

If you include the tasks for release with posting or release without posting in your workflow, the workflow approval will also release the sales order. However, if there is a failure in the release process due to missing setup information or other causes, you will need to recall the sales order from workflow, fix the issue that caused the failure, and then submit the order to workflow again.

If you do not include the tasks for release with posting or release without posting in your workflow, the workflow approval process will simply enable you to release the sales order manually once the approval is complete.

### Forced credit hold	
  
At times, sales orders may need to be blocked even though the order does not meet the criteria of the blocking rules. For example, a credit manager may be notified of a non-credit related issue with the customer and decide to manually put orders on hold immediately until the issue is cleared up. You can manually force a sales order to be on hold if that situation occurs.

1. Open the sales order that you want to place on hold.  
2. Select **Force credit hold** in the **Credit management** tab on the **Credit management** action pane.
3. Select a **Forced Hold Reason**.
4. Click **OK.** The sales order will be returned to the Credit Management Hold list.

You can also force multiple orders to be on hold using the **Credit management > Periodic tasks > Force Credit Hold** page. For example, you can place all sales orders on hold for a specific customer.
1. Select the **Forced hold reason**. 
2. Click **Records to include** to select the sales orders to place on hold. 
3. Click **OK** to process the selected sales orders.

Sales orders that have been forced on hold cannot be processed with workflow.

#### Releasing orders that were added to the credit management hold list with a forced credit hold
Sales orders that have a forced hold reason cannot be released automatically. If the sales order was forced on hold and you have used a process that automatically releases sales orders, the sales order will show as **Ready to release** and remain in the hold list. You must use the **Release** menu to release the order.
 
## Free text invoices, orders, and project invoice support in Credit management 
Credit management can only be used currently for sales orders. Free text invoices, point of sales orders and call center orders will use the temporary credit limits and insurance/guarantees that you add to adjust the credit limit. They will not use the blocking rules and they will not be placed in the hold list if there is an issue with the credit limit.

There is no support for project invoices in credit management.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
