---
title: Unbilled revenue
description: Learn how to set up items and accounts to use the unbilled revenue feature in Subscription billing, including an overview on setting up unbilled revenue.
author: JodiChristiansen
ms.author: jchrist
ms.topic: article
ms.date: 10/10/2022
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2021-11-05
ms.search.form: 
ms.dyn365.ops.version: 10.0.24
---

# Unbilled revenue

This article describes the unbilled revenue feature that lets you include the amounts for entire billing schedules on the balance sheet. These amounts are included in an unbilled revenue account and an unbilled revenue offset account, and the contract is billed through installments.

## Set up unbilled revenue

To set up unbilled revenue, follow these steps.

- On the **Recurring contract billing parameters** page, set the fields in the **Unbilled revenue** section.
- The unbilled revenue feature can be used for items where the **Item type** field is set to **Standard**. It can also be used for deferral items. To use unbilled revenue with the short-term functionality, set up the short-term options on the **Recurring contract billing parameters** page.

To set up items to use unbilled revenue, follow these steps.

1. On the **Unbilled revenue setup** page, on the **Items** tab, select **Add**.
2. On the new line, in the **Item code**, select the item code.
3. In the **Item relation** field, select the item relation.
4. Repeat these steps to add more lines.
5. Select **Save**.

To set up items and the unbilled revenue accounts, follow these steps.

1. On the **Unbilled revenue setup** page, on the **Accounts** tab, select **Add**.
2. On the new line, in the **Item code**, select the item code.
3. In the **Item relation** field, select the item relation.
4. Select the accounts for the unbilled revenue, unbilled discount, and unbilled revenue offset. To use the short-term accounts, you must set the **Short-term unbilled method** field to **Rolling periods** or **Fixed year** on the **Recurring contract billing parameters** page.
5. Repeat these steps to add more lines.
6. Select **Save**.

## Use unbilled revenue

1. On the **All billing schedules** page, create a billing schedule.
2. If the item isn't yet set up to use unbilled revenue, select the **Unbilled revenue** checkbox on the billing schedule line.
3. Set the **Unbilled revenue** option to **Yes**. Then review and edit the unbilled revenue, discount, and unbilled revenue offset accounts as required.
4. On the billing schedule, under **Unbilled revenue processing**, select **Create journal entry** to create the initial journal entry for unbilled revenue. This step must be completed before the billing schedule is invoiced.
5. After the initial journal entry is created, select **Generate invoice** to create sales orders and post the invoices for the billing schedules.
6. After the invoices are posted, you can review the audit information on the **Renewals** tab of the **All billing schedules** page.

### Milestone billing

Milestone billing works with unbilled revenue under the following conditions:

- If the milestone parent item is unbilled (the **Unbilled revenue** checkbox is selected), and the milestone child items are billed (the **Unbilled revenue** checkbox is cleared), the start and end dates for the parent item must be specified. These dates are used to create the initial journal entry.
- If the milestone parent item is unbilled (the **Unbilled revenue** checkbox is cleared), and the milestone child items are billed (the **Unbilled revenue** checkbox is selected), the end date must be specified only for the child items that you want to create the initial journal entry for.

Each milestone child item can be processed separately. The end dates can be specified when you're ready to create the initial journal entry.

> [!NOTE]
> If the initial journal entry for the milestone parent item or child items has already been created, or an invoice has been created, the start and end dates can't be edited.

### Unbilled revenue with straight line deferrals

To use unbilled revenue with straight line deferral schedules, follow these steps.

1. On the **All billing schedules** page, create a billing schedule.
2. Add an item to the billing schedule lines.
3. Select **Deferrals** for the line.
4. On the **Transaction deferral** page, follow these steps:

    1. Set the **Deferred** option to **Yes**.
    2. Change the accounts as you require.
    3. In the **Schedule** section, select **Straight line**, and edit other values as you require.
    4. Select **OK**.

5. Select **Unbilled revenue** for the line, and then follow these steps:

    1. Set the **Unbilled revenue** option to **Yes**.
    2. Select the accounts to use for the revenue, discount, and revenue offset.

6. On the billing schedule, under **Unbilled revenue processing**, select **Create journal entry**. Alternatively, use the **Unbilled revenue mass processing** page to create the journal entry.
7. The deferral schedule is created. You can review the details on the **All deferral schedules** page. After the deferral schedule is created, you can edit various values for the billing schedule line item. For example, you can edit the unit price, quantity, or dates.

### Unbilled revenue with event-based deferrals

To use unbilled revenue with event-based deferral schedules, follow these steps.

1. On the **All billing schedules** page, create a billing schedule.
2. Add an item to the billing schedule lines.
3. Select **Deferrals** for the line.
4. On the **Transaction deferral** page, follow these steps:

    1. Set the **Deferred** option to **Yes**.
    2. Change the accounts as you require.
    3. In the **Schedule** section, select **Event based**, **Template**, **Allocation type**, and **Expiration account**.
    4. Select **OK**.

5. Select **Unbilled revenue** for the line, and then follow these steps:

    - Set the **Unbilled revenue** option to **Yes**.
    - Select the accounts to use for the revenue, discount, and revenue offset.

6. On the billing schedule, under **Unbilled revenue processing**, select **Create journal entry**. Alternatively, use the **Unbilled revenue mass processing** page to create the journal entry.
7. The deferral schedule is created. You can review the details on the **All deferral schedules** page. After the deferral schedule is created, you can edit various values for the billing schedule line item. For example, you can edit the unit price, quantity, or dates. The deferral schedule is recalculated based on the new values.

The distributions are recalculated based on the allocation type that is selected (**Percentage**, **Percentage completion**, or **Equal amounts**). For the **Variable amounts** allocation type, the distribution is recalculated based on the percentage equivalent of the initial value for the event. For example, the original unit price is $100.00, and the percentage of the initial value is $55.00 (55 percent). If the unit price is changed to $200.00, the variable amount of the event becomes $110.00 (still 55 percent).

> [!NOTE]
> If deferral schedule lines have been recognized, the billing schedule line item can't be edited. To edit the line item, you must first reverse the recognized lines. The billing schedule line can then be updated.

### Unbilled revenue and top billing

A billing schedule is entered for three years, and the invoices are billed annually over a three-year period. The whole contract amount is recorded in the unbilled revenue account that annual invoices are created from. The offset account is the revenue or deferred revenue account.

Top billing and unbilled revenue don't work together, because reconciliation issues can occur in the general ledger. For example, on the **Item group setup** page, item group A is set up so that the **Number of top lines** field is set to **2**. On the **Billing schedules** page, three items are added. All three items belong to item group A. When the initial journal entry is created for the unbilled revenue feature, the amount for all three items is processed to the unbilled account. When the invoice for the billing schedule is created, only the amounts for the top two items are included. Therefore, the invoice amount doesn't match the amount that was processed to the unbilled revenue account, and reconciliation issues occur in the general ledger.

If you want to use unbilled revenue, leave the **Item group setup** page blank, or set up all item groups so that the **Number of top lines** field is set to **0** (zero). If you want to use top billing, no unbilled revenue actions are available.

### Examples

As of version 10.0.29, a new parameter is added to Recurring contract billing parameters. When set to Yes, the **Use unbilled offset accounts** parameter enables two new accounts in **Unbilled revenue setup**. The Unbilled revenue offset and Unbilled discount offset accounts become available and are best used when billing schedules are created in a currency other than the accounting currency. Using the offset accounts ensures that the unbilled revenue and unbilled discount accounts are reversed out using the same exchange rates as their initial entries. The initial **Create journal entry** process is the same with the debit to unbilled revenue and credit to revenue. If using a discount the initial journal entry is the same with a debit to Discount and credit to unbilled discount. 

This example shows how to use unbilled revenue to recognize the whole amount of a contract on the balance sheet as unbilled revenue. The other side of the entry is the revenue or deferred revenue. When you invoice the customer, the unbilled revenue is reversed. Revenue recognition will occur either at the time of invoicing or according to the deferral recognition schedule that was set up.

#### Assumptions

- On January 1 of the current year, a customer signs a three-year contract for $390.
- The contract includes two parts: licenses and a maintenance agreement.
- The sales price of the license fee is $300, and the customer will be invoiced $100 on January 1 of each contract year. The $300 license fee will be taken as revenue when the contract is signed.
- The sales price of the maintenance fee is $90, and the customer will be invoiced $30 on January 1 of each contract year. The $90 maintenance fee will be deferred, and $2.50 will be recognized each month of the life of the contract.
- The customer will be invoiced $130 at the beginning (January 1) of each of the three years of the contract.

#### Steps

1. Set up the two released items as unbilled items. Use the **Unbilled revenue setup** page to set up the items and accounts that use unbilled revenue.
2. In this example, the maintenance fee is deferred. The item requires a deferral template, which is set up on the **Deferral templates** page. The template has a **Monthly** period frequency and a recognition period length of 36 months. Therefore, the revenue per month is $2.50.
3. On the **Items deferred by default** page, set the **Maintenance fee** field to **Deferrable item**. This step and the next will cause the maintenance fee item to be deferred when it's sold or included on a billing schedule.
4. Select **Deferral defaults** \> **Template**, and add the item for the maintenance fee and the straight-line template from step 2. The maintenance fee item will be linked to a 36-month deferral schedule.
5. Create a billing schedule that includes the two unbilled items. The billing schedule for the contract is set up with the following items.

    | Item | Start date | End date | Amount | Billing frequency | Deferral item | Unbilled revenue | Description |
    |---|---|---|---|---|---|---|---|
    | License | January 01, 2022 | December 31, 2024 | $100.00 | Annually | No | Yes | The customer will be invoiced $100.00 each year. The $300.00 total will be recorded up front as unbilled revenue on the balance sheet, and as revenue on the profit and loss. Each invoice will reduce the unbilled amount. |
    | Maintenance | January 01, 2022 | December 31, 2024 | $30.00 | Annually | Yes | Yes | The customer will be invoiced $30.00 each year. The $90.00 total will be recorded up front as unbilled revenue and deferred revenue on the balance sheet. Each invoice will reduce the unbilled amount. The deferred revenue will be recognized monthly over 36 months. |

6. On the **All billing schedules** page, use the **Create journal entry** process to post the contract value to the balance sheet as unbilled revenue.

Two journal entries are created, one for each line on the billing schedule.

| Account | Debit amount | Credit amount |
|---|---|---|
| Unbilled revenue account | $300.00 | |
| Revenue account | | $300.00 |

| Account | Debit amount | Credit amount |
|---|---|---|
| Unbilled revenue account | $90.00 | |
| Deferred revenue | | $90.00 |

The contract requires that the invoice for the customer be created at the beginning of each year. Use the **Generate invoice** process to create the invoice. When the invoice is created, the following invoice voucher is posted.

| Account| Debit amount | Credit amount |
|---|---|---|
| Unbilled revenue account | | $130.00 |
| Accounts receivable | $130.00 | |

This same journal entry will be created by invoices that are posted at the beginning of the next two years. The Unbilled revenue account is reduced each year during the **Generate invoice** process. The Unbilled revenue offset account is used to balance the unbilled revenue account when different exchange rates are used. 

In the last step, the recognition journal entry is created each month to recognize the deferred revenue from the maintenance fee. The journal entry can be created by using the **Recognition processing** page. Alternatively, it can be created by selecting **Recognize** for the lines on the **Deferral schedule** pages.

| Main account | Debit amount | Credit amount |
|---|---|---|
| Deferred revenue | $2.50 | |
| Revenue | | $2.50 |

This journal entry will be created each time that the recognition process is run for this deferred item (a total of 36 times).

#### Short-term: Fixed year

You can use unbilled revenue together with the short-term functionality by setting the **Short-term unbilled** field on the **Recurring contract billing parameters** page. The following example shows the calculations that are done when unbilled revenue is used together with **Fixed year** short-term unbilled method.

A billing schedule that has the following criteria is created:

- **Start Date:** June 1, 2020
- **End Date:** December 31, 2021
- **Unit Price:** $100
- **Frequency:** Monthly

On the **All billing schedules** page, the initial journal entry is created by the **Create journal entry** process. The current short-term and long-term amounts are calculated in the following way:

- **Current short-term unbilled revenue amount:** $700
- **Current long-term unbilled revenue amount:** $1,200

The invoice is created for the billing period from June 1, 2020, through November 30, 2020. The current short-term and long-term amounts are calculated in the following way:

- **Current short-term unbilled revenue amount:** $100
- **Current long-term unbilled revenue amount:** $1,200

The invoice is created for the billing period from December 1, 2020, through December 31, 2020. The current short-term and long-term amounts are calculated in the following way:

- **Current short-term unbilled revenue amount:** $1,200
- **Current long-term unbilled revenue amount:** $0

#### Short-term: Rolling periods

You can use unbilled revenue together with the short-term functionality by setting the short-term unbilled method on the **Recurring contract billing parameters** page. The following example shows the calculations that are done when unbilled revenue is used together with the **Rolling periods** short-term unbilled method.

A billing schedule that has the following criteria is created:

- **Start Date:** June 1, 2020
- **End Date:** December 31, 2021
- **Unit Price:** $100
- **Frequency:** Monthly

On the **All billing schedules** page, the initial journal entry is created by the **Create journal entry** process. The current short-term and long-term amounts are calculated in the following way:

- **Current short-term unbilled revenue amount:** $1,200
- **Current long-term unbilled revenue amount:** $700

The invoice is created for the billing period from June 1, 2020, through November 30, 2020. The current short-term and long-term amounts are calculated in the following way:

- **Current short-term unbilled revenue amount:** $1,200
- **Current long-term unbilled revenue amount:** $100

The invoice is created for the billing period from December 1, 2020, through December 31, 2020. The current short-term and long-term amounts are calculated in the following way:

- **Current short-term unbilled revenue amount:** $1,200
- **Current long-term unbilled revenue amount:** $0

### Items with revenue allocation

Two items that have different billing frequencies are added to a billing schedule. Both use unbilled revenue and are deferrable items.

- **Item number 1000:** Surface Pro 128GB

    - **Billing frequency:** One time
    - **Unit price:** $1,500
    - **Standalone selling price:** $1,600
    - **Contract revenue:** $1,465.26

- **Item number S0021:** Insurance that is sold together with item number 1000

    - **Billing frequency:** Monthly for 12 months
    - **Unit price:** $20 per month
    - **Standalone selling price:** $25
    - **Contract revenue:** $264.74

Because both items use unbilled revenue and revenue allocation, the total contract amount on the renewal line is 0 (zero). The **Contract revenue** column is added and shows the contract revenue amount.

The following table shows the initial journal entry for the items and the invoice.

| Main account | Debit amount | Credit amount |
|---|---|---|
| **Item 1000 journal entry** | | | 
| Unbilled revenue account (401250) | $1,465.26 | |
| Deferred revenue account (250600) | | $1,465.26 |
| **Item 0021 Journal entry** | | | 
| Unbilled revenue account (401250) | $274.74 | |
| Deferred revenue account (250600) | | $274.74 |
| **Invoice** | | |
| Unbilled revenue account | | $1,465.26 |
| Unbilled revenue account | | $274.74 |
| AR account (130100) | $1,488.16 | |

#### Changes to the billing schedule line, billing detail line, or revenue allocation

When the unit price or quantity is changed, the contract revenue amount for each item that is part of the revenue allocation must be updated. Therefore, the journal entry is recalculated.

For example, the unit price for item 1000 is changed from $1,500 to $1,600. In this case, the contract revenue amount is automatically recalculated as $1,549.47. The contract revenue for item S0021 is recalculated as $290.53.

When the changed is confirmed and committed, the initial journal entries for both items are reversed, and new journal entries are created:

- **Item 1000:** The original initial journal entry of $1,465.26 is reversed. A new journal entry for $1,549.47 is created.
- **Item S0021:** The original initial journal entry of $274.74 is reversed. A new journal entry for $290.53 is created.

#### Termination

Item S0021 has a start date in January 2020 and an end date in December 2020, but is terminated in June 2020. The contract revenue amount for both items must be recalculated:

- **Item 1000:** The contract revenue is recalculated as $1,567.67.
- **Item S0021:** The contract revenue is recalculated as $124.00.

An adjustment journal entry is created for the line that is terminated. The journal entry for the line that belongs to the same multiple element arrangement (MEA) number is reversed, and a new journal entry is created:

- **Item 1000:** The original initial journal entry of $1,465.26 is reversed. An adjustment journal entry for $1,549.47 is created.
- **Item S0021:** The original initial journal entry of $274.74 is reversed. A new journal entry for $124.00 is created.
