---
title: Credit limit adjustments
description: Learn about how to set up and add credit limit adjustments, including a step-by-step process on setting up credit limit adjustments.
author: JodiChristiansen
ms.author: twheeloc
ms.topic: article
ms.date: 09/04/2019
ms.custom:  
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom:
ms.search.form:
ms.dyn365.ops.version: 
---

# Credit limit adjustments 

[!include [banner](../includes/banner.md)]

Credit limit adjustments let credit managers update the credit limits and expiration dates of a single customer, a group of customers, or all customers through a posting process. You can add credit limit adjustment entries to update customers and customer credit groups, or you can use them to calculate automatic credit limits. The entries can then be reviewed, sent for approval through a workflow, and posted to customer accounts.

## Set up credit limit adjustments

You can create entries in the **Credit limit adjustment** journal on the **Credit limit adjustment** page (**Credit management \> Credit limit adjustments \> Credit limit adjustments**).

1. Select **New**. A new group of entries is created that has a credit limit adjustment number.
2. Select the credit limit adjustment type:

    - Select **Credit limit** to change the customer's credit limit.
    - Select **Temporary credit limit** to create a temporary credit limit instead of changing the customer's current credit limit. Temporary credit limits override a customer's credit limit for a defined period. After that period ends, the customer's credit limit is used again.
3. Enter a description. 

If the **Posted** check box is selected, the credit limits have been applied. The **Approval status** field indicates the workflow status of the journal. A workflow is optional.

### Add credit limit adjustments

To manually add credit limit adjustments, select **Lines**, and then follow these steps.

1. To add a credit limit adjustment for a customer, use the **Customer adjustments** menu. To add a credit limit for a customer credit group, select **Customer credit group adjustments**.
2. Enter a customer account for the invoice customer account that should be updated with the new credit limit. If you selected **Customer credit group adjustments** in step 1, enter the customer credit group. You can't enter both a customer account and a customer credit group ID on the same journal line.

    The current credit limit is shown, and the name automatically appears.

3. Enter the new credit limit that should replace the current credit limit when the credit limit entry is posted.
4. Enter a date to define the new expiration date for the customer credit limit. You must enter a credit limit expiration date when you create a credit limit adjustment.

The **Approval status** field indicates the workflow status of the journal line.

If you want the credit limit adjustments to be automatically generated, you can use the **Generate** menu on the Action Pane.
 
### Add temporary credit limit adjustments

To manually add temporary credit limit adjustments, follow these steps for the journal lines.

1. To add a credit limit adjustment for a customer, use the **Customer adjustments** menu. To add a credit limit for a customer credit group, select **Customer credit group adjustments**.
2. Enter a customer account for the invoice customer account that should be updated with the new credit limit. If you selected **Customer credit group adjustments** in step 1, enter the customer credit group. You can't enter both a customer account and a customer credit group ID on the same journal line.

    If an active or future temporary credit limit already exists, the current temporary credit limit and date ranges appear for each temporary credit limit. The name automatically appears.

3. Enter the new credit limit that should replace the current credit limit.
4. In the **New from date** and **New to date** fields, define the period when the advanced credit limit is valid. You must enter credit limit expiration dates when you create a credit limit adjustment journal.

The **Approval status** field indicates the workflow status of the journal line.

## Generate credit limit adjustments

You can also have credit limits automatically adjusted. On the Action Pane, select **Generate**, and then select one of the following options:

- From existing customer
- From existing customer credit group
- Automatic credit limits

### From existing customer

You can create journal lines from existing customers. When you select **Generate \> From existing customer**, a dialog box appears where you can provide criteria for selecting customers and calculating the new limits.

1. Enter an adjustment value to add or subtract an amount from the credit limit. Enter a negative value to decrease the current credit limit or a positive value to increase it.
2. In the **Value type** field, select how the value that you entered in step 1 should be used to calculate the new credit limit:

    - Select **Fixed value** to change the credit limit by an amount.
    - Select **Percentage** to change the credit limit by a percentage.

3. Enter a value that is used to round the calculated credit limit. For example, enter **10.00** to round the credit limit to the nearest 10.00 currency units.
4. Set the **Rounding form** field to specify whether the remainder should be rounded up or down.
5. Select the method that is used to adjust dates.

    - If you select **Absolute**, you can enter dates that define the date range for the credit limits.
    - If you select **Relative**, you can enter offset dates for the range. The current date range for the credit limit will be adjusted by the offset.

6. Use the **Records to include** FastTab to filter the list of customers that are included. If you don't include filters, credit limit entries will be generated for all customers.
7. Select **OK** to create the credit limit adjustment entries.

### From existing customer credit group

You can create journal lines from existing customer credit groups. When you select **Generate \> From existing customer credit group**, a dialog appears where you can provide criteria for selecting customer credit groups and calculating the new limits. The criteria are the same criteria that are used to create journal lines from existing customers. See the steps in the previous section.

### Automatic credit limits

You can create automatic credit limits to define and update customer credit limits. The automatic credit limits are created for a risk group, and they are based on specific values that are used in the scoring groups. You can use these automatic credit limits to generate credit limit entries. If a customer has been assigned to a specific risk group, and the customer's credit information matches the criteria for an automatic credit limit, a credit limit adjustment entry is created.

#### Create automatic credit limits

You create automatic credit limits by using credit limit adjustments. When you select **Generate \> Automatic credit limits**, a dialog appears where you can set an expiration date for the new credit limits that will be created based on the risk groups that customers are assigned to. When you've finished, select **OK** to create the credit limit adjustment lines.

### Post adjustments

After you've created credit limit adjustment lines, you can use the **Post** button on the Action Pane to post the entries and update the customer credit limits. However, if you've set up a workflow, you must select **Workflow \> Submit** on the Action Pane to submit the journal for approval.

### Credit limit adjustments workflows

The **Credit limit adjustments** workflows can be used to send credit limit adjustments through a workflow approval process. You can create two workflows on the **Credit management worfklow** page (**Credit management \> Setup \> Credit management worfklow**):

- **Credit limit adjustments** – This workflow can be used to approve entries at the header level.
- **Credit limit adjustments line** – This workflow can be used to approve the adjustment entries so that the entries can be approved by different people, based on the criteria in the workflow.

> [!NOTE]
> When you create the **Credit limit adjustments** workflow, you can set it up so that the adjustments are automatically posted after the lines are approved. Just include the **Post Journal automatically** task in the workflow.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
