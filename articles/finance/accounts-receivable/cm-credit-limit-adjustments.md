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

The Credit limit adjustment journal allows credit managers to update the credit limits and expiration dates of a single customer, group of customers, or all customers using a journal process. You can add credit limit adjustment journal entries to update customers and customer credit groups or use it to calculate automatic credit limits. The journal entries can then be reviewed, sent for approval through workflow, and posted to the customer accounts.

You can create entries in the Credit limit adjustment journal on the **Credit limit adjustment journal** page (**Credit management > Journal entries > Credit limit adjustment journal**).

1.	When you select **New**, a new journal is created with a credit limit adjustment journal number.

2.	Select the credit limit adjustment type. You can select **Credit limit** to adjust the customer credit limit. You can select **Temporary credit limit** to create temporary credit limits instead of changing the existing credit limits. Temporary credit limits override a customer's credit limit for a defined period of time, after which the customer's credit limit is used again.

3.	Enter a journal description. 

    The **Posted** check box indicates that the credit limits have been applied. The **Approval status** indicates the workflow status of the journal.

    Selecting **Lines**, lets you enter credit limit changes manually onto the journal lines. You can also use the Generate menu to create the credit limit changes automatically.

To enter credit limit changes manually, add the following information to the journal lines:

1.	Select the **Customer adjustments** menu to create an adjustment for a customer. Select **Customer credit group adjustments** to add a credit limit for a customer credit group.

2.	Enter a customer account for the invoice customer account that will be updated with the new credit limit. If you selected Customer credit group adjustments, then enter the customer credit group.

3.	The name will appear automatically.

4.	If you want to update the credit for a customer credit group, enter the ID  of the group. You cannot enter both a customer account and customer credit group ID on the same journal line. The current credit limit will be displayed.

5.	Enter the new credit limit that will replace the current credit limit when the credit limit journal is posted.

6.	Enter the new to date to define the new expiration date for the customer credit limit. You must enter a credit limit expiration date when you create a credit limit adjustment journal.
   	The **Approval status** indicates the workflow status of the journal line.

To enter temporary credit limit changes manually, add the following information to the journal lines:

1.	Select the **Customer adjustments** menu to create an adjustment for a customer. Select **Customer credit group adjustments** to add a credit limit for a customer credit group.

2.	Enter a customer account for the invoice customer account that will be updated with the new credit limit. If you selected Customer credit group adjustments, then enter the customer credit group. 

    The name will appear automatically and the current credit limit will be displayed. The current **From date** and **To date** for the advanced credit limit will be displayed.

3.	Enter the new credit limit that will replace the current credit limit when the credit limit journal is posted.

4.	Enter a date in the **New from date** to define the new expiration date for the advanced credit limit.

5.	Enter a date in the **New to date** to define the new expiration date for the advanced credit limit. You must enter credit limit expiration dates when you create a credit limit adjustment journal.

    The approval status indicates the workflow status of the journal line.

You can also generate credit limits automatically using the **Generate** menu in the Action Pane.

- From existing customer
- From existing customer credit group
- Automatic credit limits

### From existing customers

You can create journal lines from existing customers. When you select **Generate > From existing customer**, a dialog displays that you can use to provide criteria for selecting customers and calculating the new limits:

1. Select **Yes** in the **Include customer credit limits** field to generate a new credit limit using the current customer credit limit found in the **Customer credit limit** field.

2. Select **Yes** on the **Include advanced credit limits** field to generate a new credit limit using the advanced credit limits.

3. Enter an adjustment value to add or subtract an amount from the credit limit. Enter a negative value to decrease the current credit limit or a positive to increase it. The setting of the **Value type** field controls how the value will be used to calculate the new credit limit.

4. Select a value type that will control how the value is used in the credit limit calculation. Select **Fixed value** to change the credit limit by an amount, or select **Percentage** to change it by a percentage.

5. Enter a value to round off the calculated credit limit. For example, 10.00 will round the credit limit to the nearest 10.00 currency units.

6. Set the **Rounding form** field to determine whether the remainder is rounded up or down.

7. Select the method for adjusting dates. If you click **Absolute**, you can enter dates that define the date range for the credit limits. If you click **Relative**, you can enter a offset dates for the range that will adjust the current ranges for the credit limits by the offset.

8. Click **OK** to create the credit limit adjustment journal entries.

### From existing customer credit groups

You can create journal lines from existing customers. When you select **Generate > From existing customer credit groups**, a dialog is presented that you can use the dialog that displays to provide criteria for selecting customer credit groups and calculating the new limits. The criteria is the same as shown in the preceding section on adjusting credit limits for existing customers.

Click **OK** to create the credit limit adjustment journal entries.

## Automatic Credit Limits

You can create automatic credit limits to define and update customer credit limits. The automatic credit limits are created for a risk group and are based on specific values used in the scoring groups. You can use these automatic credit limits to generate credit limits in credit limit adjustment journals. If a customer has been assigned to a specific risk group and the customer's credit information matches the criteria for an automatic credit limit, then a line in the credit limit adjust journal is created.

### Defining automatic credit limit criteria

You can create Automatic credit limits criteria on the **Automatic credit limits** page (**Credit management > Setup > Risk setup > Automatic credit limits**).

1. Select a risk group to which the automatic credit limit is assigned.

2. Select the currency for the automatic credit limit. You can create multiple automatic credit limits for the same risk group for credit limits in different currencies.

3. Enter the revenue amount that represents the maximum company revenue that can be used for this automatic credit limit. When credit limits are created, the revenue amount is compared to a revenue value found on the **Financials** page (**Accounts Receivable > All customers> Select a customer > General > Statistics > Financial**). The system uses the latest value in the **Overview** section.

Complete the following steps to add lines that represent the credit limit that will be generated based on criteria selected.

1.	Select the scoring group that defines the customer information that will be used to calculate the credit limit.

2.	Select the comparison operator that will be used to define how the scoring group information will be evaluated.

3.	Enter the value that will be compared to scoring group value.

4.	Enter the credit limit that will be assigned if the customer information matches the value specified for the scoring group. For example, you can create an automatic credit limit for the Low scoring group. If the Dun and Bradsheet score is one of the scoring groups, you can define one line that will assign a 100,000 credit limit if the Dun and Bradstreet score is A2, and define another line that will assign a 200,000 credit limit if the Dun and Bradstreet score is A1.

## Creating automatic credit limits

You create automatic credit limits using credit limit adjustments. When you select **Generate > Automatic limits**, a dialog displays  that you can use to set an expiration date for the new credit limits that will be created based on the risk groups that customers are assigned to. Click **OK** to create the credit limit adjustment lines.

## Posting adjustments

Once you have created credit limit adjustment lines, you can use the Post button in the action pane to post the journal lines and update the customer credit limits. However, if you have set up workflow for the journal, you will need to use the **Workflow > Submit** button on the Action Pane to submit the journal for approval.

## Credit Limit Adjustment Journal Workflow

The **Credit limit adjustment journal** workflow can be used to send credit limit adjustment journals through a workflow approval. There are two workflows that you can create on the **Credit management worfklow** page (**Credit management > Setup > Credit management worfklow**).

1.	The **Credit limit adjustment journal** workflow can be used to approve journals at the header level.

2.	The **Credit limit adjustment journal** line workflow can be use to approve the journal lines so that the journal lines can be approved by different people based on the criteria in the workflow.

> [!NOTE] 
> When creating the **Credit limit adjustment journal** workflow, you can set up the workflow to Post the adjustment journal once the lines are approved. Include the **Post Journal automatic** task in the workflow to automatically post the journal.

