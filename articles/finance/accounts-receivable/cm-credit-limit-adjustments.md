---
# required metadata

title: Credit limit adjustments
description: 
author: mikefalkner
manager: AnnBe
ms.date: 09/04/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschloma
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

# Credit limit adjustments 

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

Credit limit adjustments allows credit managers to update the credit limits and expiration dates of a single customer, group of customers, or all customers using a posting process. You can add credit limit adjustment entries to update customers and customer credit groups or use them to calculate automatic credit limits. The entries can then be reviewed, sent for approval through workflow, and posted to the customer accounts.

## Set up adjustments

You can create entries in the Credit limit adjustment journal on the **Credit limit adjustment** page (**Credit management > Credit limit adjustments > Credit limit adjustments**).

1.	When you select **New**, a new group of entries is created with a credit limit adjustment number.

2.	Select the credit limit adjustment type. You can select **Credit limit** to adjust the customer credit limit. You can select **Temporary credit limit** to create temporary credit limits instead of changing the existing credit limits. Temporary credit limits override a customer's credit limit for a defined period of time, after which the customer's credit limit is used again.

3.	Enter a description. 

The **Posted** check box indicates that the credit limits have been applied. The **Approval status** indicates the workflow status of the journal. Workflow is optional.

Select **Lines** to enter credit limit changes manually. You can also use the Generate menu to create the credit limit changes automatically.

### Adding credit limit adjustments

To enter credit limit changes manually, add the following information to the lines:

1.	Select the **Customer adjustments** menu to create an adjustment for a customer. Select **Customer credit group adjustments** to add a credit limit for a customer credit group.

2.	Enter a customer account for the invoice customer account that will be updated with the new credit limit. If you selected Customer credit group adjustments, then enter the customer credit group. You cannot enter both a customer account and customer credit group ID on the same journal line. The current credit limit will be displayed and the name will appear automatically.

3. Enter the new credit limit that will replace the current credit limit when the credit limit entry is posted.

4.	Enter the new to date to define the new expiration date for the customer credit limit. You must enter a credit limit expiration date when you create a credit limit adjustment. The **Approval status** indicates the workflow status of the journal line.

### Adding temporary credit limit adjustments

To enter temporary credit limit changes manually, add the following information to the journal lines:

1.	Select the **Customer adjustments** menu to create an adjustment for a customer. Select **Customer credit group adjustments** to add a credit limit for a customer credit group.

2.	Enter a customer account for the invoice customer account that will be updated with the new credit limit. If you selected Customer credit group adjustments, then enter the customer credit group. You cannot enter both a customer account and customer credit group ID on the same journal line. If an active or future temporary credit limit already exists, the current temporary credit limit and date ranges will appear for each temporary credit limit. The name will appear automatically.

3.	Enter the new credit limit that will replace the current credit limit..

4.	Enter a date in the **New from date** to define the new expiration date for the advanced credit limit.

5.	Enter a date in the **New to date** to define the new expiration date for the advanced credit limit. You must enter credit limit expiration dates when you create a credit limit adjustment journal. The approval status indicates the workflow status of the journal line.

## Generating credit limit adjustments
You can also generate credit limits automatically using the **Generate** menu in the Action Pane.

- From existing customer
- From existing customer credit group
- Automatic credit limits

### From existing customers

When you select **Generate > From existing customer**, a dialog displays that you can use to provide criteria for selecting customers and calculating the new limits:

1. Enter an adjustment value to add or subtract an amount from the credit limit. Enter a negative value to decrease the current credit limit or a positive to increase it. The setting of the **Value type** field controls how the value will be used to calculate the new credit limit.  Select **Fixed value** to change the credit limit by an amount, or select **Percentage** to change it by a percentage.

2. Enter a value to round off the calculated credit limit. For example, 10.00 will round the credit limit to the nearest 10.00 currency units.

3. Set the **Rounding form** field to determine whether the remainder is rounded up or down.

4. Select the method for adjusting dates. If you click **Absolute**, you can enter dates that define the date range for the credit limits. If you click **Relative**, you can enter a offset dates for the range that will adjust the current ranges for the credit limits by the offset.

5. Use the **Records to include** tab to filter down the list of customers to include. If you do not include filters, you will generate credit limit entries for all customers.

8. Click **OK** to create the credit limit adjustment entries.

### From existing customer credit groups

You can create journal lines from existing customers. When you select **Generate > From existing customer credit groups**, a dialog is presented that you can use the dialog that displays to provide criteria for selecting customer credit groups and calculating the new limits. The criteria is the same as shown in the preceding section on adjusting credit limits for existing customers.

Click **OK** to create the credit limit adjustment journal entries.

## Automatic Credit Limits

You can create automatic credit limits to define and update customer credit limits. The automatic credit limits are created for a risk group and are based on specific values used in the scoring groups. You can use these automatic credit limits to generate credit limits entries. If a customer has been assigned to a specific risk group and the customer's credit information matches the criteria for an automatic credit limit, then a credit limit adjustment entry is created.

### Creating automatic credit limits

You create automatic credit limits using credit limit adjustments. When you select **Generate > Automatic limits**, a dialog displays  that you can use to set an expiration date for the new credit limits that will be created based on the risk groups that customers are assigned to. Click **OK** to create the credit limit adjustment lines.

## Posting adjustments

Once you have created credit limit adjustment lines, you can use the Post button in the action pane to post the entries and update the customer credit limits. However, if you have set up workflow, you will need to use the **Workflow > Submit** button on the Action Pane to submit the journal for approval.

## Credit Limit Adjustment Workflow

The **Credit limit adjustment workflow** can be used to send credit limit adjustments through a workflow approval. There are two workflows that you can create on the **Credit management worfklow** page (**Credit management > Setup > Credit management worfklow**).

1.	The **Credit limit adjustments** workflow can be used to approve entries at the header level.

2.	The **Credit limit adjustments line** workflow can be use to approve the adjustment entries so that the entries can be approved by different people based on the criteria in the workflow.

> [!NOTE] 
> When creating the **Credit limit adjustments workflow**, you can set up the workflow to Post the adjustments once the lines are approved. Include the **Post Journal automatically** task in the workflow to automatically post the entries.

