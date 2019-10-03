---
# required metadata

title: Credit holds for sales orders
description: 
author: mikefalkner
manager: AnnBe
ms.date: 01/25/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mfalkner
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Credit holds for sales orders
[!include [banner](../includes/banner.md)]

Credit management blocking rules are used to define scenarios when a customer or group of customers should be put on credit management review hold.  Blocking rules define scenarios for:
1. Overdue account
2. Credit limit exceeded
3. Manually blocked customer
4. Force on hold
5. Terms amendment
6. Cash discount amendment

## THESE NEED TO MATCH THE RULES BELOW
The combination of the blocking rules, the exclusion rules, and the credit limit determine when and why an order will go on hold for credit management review.

## Set up blocking rules and exclusion rules

Sales order information is compared to blocking rules to determine if a sales order should be blocked. You can also define exclusions that will override the blocking rules and allow the sales orders to be processed. You can set up blocking rules and exclusion rules on the **Credit management > Setup > Credit management setup > Credit management rules setup** page.

**FIX THIS AFTER THE FORMS ARE MERGED -- probably better to split this up by single rule because there are all very different**

1. Select the **Rule type** to define a rule as blocking or as an exclusion.
2. Select the **Blocking rule** to identify the type of information that will be reviewed to determine if an order should be blocked:
   - Select **Days overdue** if the blocking rule applies to customer with overdue invoices.
   - Select **Account status** if the blocking rule applies to a customer with the selected account status.
   - Select **Terms of payment** if the blocking rule applies to the selected payment term.
   - Select **Overdue Amount** if the blocking rule applies to customers with overdue amounts.
   - Select **Credit limit used**  if the blocking rule applies to the customer credit limit amount utilized.
   - Select **Credit limit expired** if the blocking rule applies to customers with credit limits that have expired.
3. Select the range of customer that this rule is **Valid for**.
   - Select **Table** if the rule applies to a specific customer.
   - Select **Group** if the rule is applied at the Customer group level. 
   - Select **All** if the rule applies to all customers.
4. Once you have specified the range, you must specify the **Customer relation** used in the range.
   - For the **Table** range, the lookup will change to match the information needed for the blocking rule category. For payment terms, you will see a list of payment terms in the lookup.  For account status, you will see the credit management account status in the lookup. For all other values, you will see a customer lookup. 
   - Select a **Group** if the rule applies to a customer credit management group.
   - Select **All** if the rule applies to all customers. 
5. Select a **Risk group** if you want to further limit the list of customers that go on credit management hold. 
6. Enter the **Grace** days allowed for the selected blocking rule before an order is placed on credit management hold for review. If the blocking rule is set to “Days overdue” or “Overdue amount”, then the number of days overdue allows you to add additional grace days to the number of overdue days that the invoice can have before it is considered overdue. If the blocking rule is set to “Expired credit limit”, then the number of days are added to the expiration date to determine if the credit limit has expired.
7. Enter the **Threshold** value for the selected rule before a customer goes on credit management hold. This can be an amount or a percentage based on the value type select in the next field.
8. Select the **Value type** that defines the adjustment value as a fixed value or percentage.
shold.  The Threshold relates to the Credit limit.

Now let’s look at a scenario for one customer with the settings as per above and the expected results of this scenario when a document which is credit checked is posted i.e. Confirmation:


## Managing the priority of executing rules

Rules are executed in a specific order
1. The Sales order rule allows you to override all rules if an exclusion rule is true. If you mark an exclusion rule so that the Release Sales order is checked, the order will not be put on hold if that rule is true and no other rules will be checked.
2. Blocking rules are executed for every rule. Any rule can place the order on hold and all of the rules that block the order will be shown in the Blocking rules list on the credit management hold page.
3. Exclusion rules are executed last. If an exclusion rule is true on one rule, it will not override the blocking rule for the same rule. Exclusions will only affect the rule on which they are defined. 
4. Blocking and exclusion rules are executed in Table, then Group, then All order. Because of this order of processing, it is possible to have a blocking rule at the All level that will not be executed because an exclusion rule at the Table or Group level is executed.

The behavior of the **Credit limit used** rule will change based on the settings for the **Check credit limit for sales order** parameter found in the Credit and Collections parameter form.
1. If the parameter is set to No, then the Credit limit used rule will not be executed
2. If the parameter is set to Yes and the **Message when exceeding credit limit** is set to warning, then you will get a warning when the credit limit is exceeded. The **Credit limit used** rules will be executed to see if you have rules that you want executed. However, for this scenario, you would normally not add any rules.
3. If the parameter is set to Yes and the **Message when exceeding credit limit** is set to error, then the credit limit will be checked and the order will be put on hold if credit limit is exceeded. In addition, the **Credit limit used** rules will be executed to see if you have additional rules that you want executed. An error message will not be shown but the "Exceeded credit limit** blocking reason will be shown. 

## MOVE Set up reasons to a better location
## Set up Reasons	

When you place an order on hold or release an order from hold, you must specify the reasons for the hold actions. Hold reasons are used when setting orders on hold and are available on the customer detail form and on the forced hold periodic job.  Release reasons are used when releasing orders from credit management review in the credit management queue. 

You can set up Reasons on the **Credit management > Setup > Reasons** page.

1. Select the **Reason type** for the reason. You can select Hold or Release
2. Enter the **Reason** name for the reason.
2. Enter the **Description** for the reason code.

## Put a sales order on hold based on other criteria
  
### Rank Payment Terms	

You can force the credit control rules to be executed when payment terms are changed. You must rank the payment terms and assign them a ranking value. If you change the payment terms on the order to payment terms that are ranked higher than the old payment terms, then the order will be sent to credit management and require approval.

You can set up the payment terms rankings on the **Credit management > Setup > Credit management setup > Rank payment terms** page.

1. Select the **Terms of payment** that you want to rank. The **Description** of the terms of payment will be displayed.
2. Select the **Rank** value. The values are all relative to each other so you can use 1,2,3 or 10,20,30. You can also use the same value for most of the terms of payment so that only one or two terms of payment will trigger the credit check.

### Rank settlement discounts	

You can force the credit control rules to be executed when settlement discounts are changed. You must rank the settlement discounts and assign them a ranking value. If you change the settlement discounts on the order to settlement discounts that are ranked higher than the old settlement discounts, then the order will be sent to credit management and require approval.

You can set up the payment terms rankings on the **Credit management > Setup > Credit management setup > Rank settlement discounts** page.

1. Select the **Cash discount** that you want to rank. The **Description** of the settlement discount will be displayed.
2. Select the **Rank** value. The values are all relative to each other so you can use 1,2,3 or 10,20,30. You can also use the same value for most of the settlement discounts so that only one or two settlement discounts will trigger the credit check.

## Processing orders on hold using the credit management queue

The Credit management queue allows credit managers to view all sales orders that have been placed on hold and enables them to remove the holds once the credit issues have been mitigated. The **Credit management queue** page shows all sales orders that have been placed on hold and add to the credit management queue. You can view the queue on the **Credit management > Credit management queue > All** page.

Sales orders from all legal entities are sent to the same credit management queue, providing a centralized view of all transactions that require attention. Users will only see information for the legal entities that they have access to.

The following sales order transactions can be placed in the queue:
1. An order for a customer with an overdue invoice. 
2. An order for a customer who has exceeded its credit limit.
3. An order for a customer who has been stopped for invoice or all transactions.
4. An order with specific terms of payment.
5. An order with a specific account status.
6. An order for a customer with an expired credit limit.
7. An order where the payment terms or settlement discounts differ from the default customer master payment terms or settlement discounts.

The block reason is displayed for each sales order in the queue. If there are more than one reason for the hold, the reason will show as "Multiple". You can use the **Information > Blocking reasons** menu on the action pane to view all of the reasons why the sales order was placed on hold.

### Releasing orders from the queue for processing	

Once you have researched the reasons for the hold and you have mitigated them, you can release the sales orders for further processing.

1) Click on the **Check box** on each line to ‘mark’ records as selected. You can release multiple orders by selecting more than one line.
2) Select a **Release reason** for each order that has been selected for release.  
3) Enter the **Review date** for each order that has been selected for release.  
4) Select the **Release** menu on the action pane to release an order. This menu will only be available after transactions have been selected. The user is presented with two options:
   - Select **Original posting** to remove the hold and post the document at the stage that it was sent. For example, if the sales order confirmation was placed on hold, the sales order confirmation would be completed after the release.The sales order posting form will be displayed allowing the user to post the confirmation.
   - Select **Without posting** to remove the hold without doing any further processing
### Rejecting orders in the queue
You can use the **Reject** menu on the action pane to reject a sales order
1. Click on the **Check box** on each line to ‘mark’ records as selected. You can reject multiple orders by selecting more than one
2. The order will be removed from the queue and the sales order header will be updated to show that the order was rejected.

### Credit management approval workflow

You can also create **Credit management workflows** to control the release of credit holds. Once you have set up workflow using the **Credit management > Setup > Credit management workflows** page, the orders marked for release or rejection will be sent to workflow where they must be approved first before they will be released or rejected. 

### Forced Credit Hold	
  
At times, sales orders may be released prematurely when a credit manager reviews a blocked order, releases it and then later discovers another reason for it to remain on hold.  You can manually force a sales order to be on hold if that situation occurs.

1. Open the sales order that you want to place on hold.  
2. Select **Force credit hold** in the **Credit management** tab on the **Credit management** action pane.
3. Select a **Forced Hold Reason**.
4. Click **OK.** The sales order will be returned to the Credit Management Queue.

You can also force multiple orders to be on hold using the **Credit management > Periodic tasks > Force Credit Hold** page. For example, you can place all sales orders on hold for a specific customer.
1. Select the **Forced hold reason**. 
2. Click **Records to include** to select the sales orders to place on hold. 
3. Click **OK** to process the selected sales orders.
