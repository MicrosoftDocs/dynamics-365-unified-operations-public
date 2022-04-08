---
# required metadata

title: Deferral transactions in Subscription billing
description: This topic describes the various transactions that can be used in deferral transactions as part of revenue and expense deferrals in Subscription billing.
author: JodiChristiansen
ms.date: 11/04/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 539093
ms.search.region: Global
# ms.search.industry: 
ms.author: jchrist
ms.search.validFrom: 2021-11-05
ms.dyn365.ops.version: 10.0.24

---

# Deferral default transactions

This topic describes the transactions that allow for revenue and expense deferrals. Deferral schedules are always based on and depend on an originating document or billing schedule. Deferral schedules are created based on defaults, and can't be entered or created separately.

## Sales order transaction deferral

Use the **Deferrals** or **Create credit note** page to enter or edit the deferral parameters for a sales order line.

> [!NOTE]
> When a sales order is created from a billing schedule, all values on the **Deferrals** or **Create credit note** page are read-only, and the deferral parameters can't be edited. To edit the values, use the **Modify schedule** page.

### Edit deferral options

To edit the deferral options for a line, follow these steps.

1. Create a sales order transaction.
2. Select the line, and then select **Deferrals**.
3. On the **Transaction deferral** page, the **Deferred** option must be set to **Yes**. Edit other fields as you require.
4. To preview the deferral schedule, select **Preview**.
5. If you made any changes to the transaction deferral, select **OK**, and return to the transaction page.
6. Commit and post the transaction.

After the transaction is posted, open the **All deferral schedules** page to view the deferral schedule.

### Create a credit note

To create a credit note, follow these steps.

1. Create a sales order transaction.
2. In the **Sales order lines** section, select the item that you want to create a credit note for.
3. Select **Sales order line** \> **New**, and then select **Credit note**.
4. Select **Deferrals**.
5. On the **Sales order transaction deferral** page, set the **Adjust existing schedule** option to **Yes** for the item.
6. In the **Adjusted schedule** field, select the deferral schedule that you want to apply the credit note to.
7. Update the **Recalculate date** and **End date** fields as you require.
8. Select **OK**.
9. Finish posting the sales order transaction.

### Purchase orders and purchase invoices

If you want to use the deferral functionality for a purchase order, generate the invoice first. Then use the **Pending vendor invoices** page to edit or add deferral items. You can't edit or add deferrals directly on a purchase order.

1. Use the **Pending vendor invoices** page to enter a vendor invoice.

    When you enter a line, the deferral is automatically set for the item or procurement category that you select. This deferral is based on the deferral setup on the **Deferral defaults** page. The deferrals can be edited or added at the distribution level.

3. On the purchasing line, select **Financials \> Distribute amounts**.
4. For each distribution amount, select **Deferrals**. When the invoice is posted, a deferral schedule is created for each distribution that a deferral is set for.

### Tax

In some cases, the tax amount can be fully or partially non-recoverable. If the tax amount of a deferrable line contains a non-recoverable amount, the non-recoverable tax amount is included in the deferrable schedule amount when the invoice is posted.

### Variance

If the amount on the vendor invoice line differs from the amount on the purchase order line, variance distributions are created. If the line is deferred, the ledger account for these distributions is set to the deferral account, and the amounts are included in the deferrable schedule amount when the invoice is posted. These distributions are named **Price variance** and **Cost variance**.

### General journals and invoice journals

Use the **Deferrals** page to enter the deferral parameters for a journal voucher line. You can also preview the deferral schedule for straight line deferrals. When you enter a line, the deferral is automatically set based on the setup of deferral accounts on the **Deferral defaults** page. You can manually change the deferral options for each line. When the journal voucher is posted, the deferral schedule is created.

#### Post and transfer

To post the journal voucher, use the **Post and transfer** command. The deferral options will follow the line that the voucher applies to. For vouchers that don't have errors, a deferral schedule is created if it's deferred. For a voucher that has an error and are transferred, any deferral options are also transferred with it.

#### Tax

In some cases, the tax amount can be fully or partially non-recoverable. If the tax amount of a deferrable line contains a non-recoverable amount, the non-recoverable tax amount is included in the deferrable schedule amount when the invoice is posted.

## Free text invoice transaction deferral

Use the **Deferrals** page to enter the deferral parameters for a free text invoice line distribution. When a distribution is entered, the deferral is automatically set based on the deferral settings on the **Deferral defaults** page.

## Fields

The **Transaction deferral** page contains the following fields.

| Field | Description |
|-------|-------------|
| Deferred | <p>Specify whether the line is a deferral:</p><ul><li>**Yes** – The line is a deferral.</li><li>**No** – The line isn't a deferral.</li></ul><p>When this option is set to **Yes**, the **Adjust existing schedule** option isn't available. For items and charges that are already set up as deferred, this option is set to **Yes**. For items and charges that aren't set up as deferred by default, set this option to **Yes**.</p> |
| Adjust existing schedule | <p>Specify whether the line is an adjustment to an existing deferral schedule:</p><ul><li>**Yes** – The new sales line is an adjustment to an existing deferral schedule. In this case, you can select a deferral schedule in the **Adjusted schedule** field.</li><li>**No** – The new sales line isn't an adjustment to an existing deferral schedule.</li></ul><p>When this option is set to **Yes**, the **Deferred** option isn't available.</p> |
| Adjusted schedule | <p>Select the deferral schedule that the line is adjusting. All values on the page are then updated with the values from the originating deferral schedule. Those values can't be edited.</p><p>This field is available only when the **Adjust existing schedule** option is set to **Yes**.</p> |
| Recalculation date | <p>Specify the start date of the period that you want to recalculate the remaining amount from. The default date is the date of the next unrecognized period.</p><p>This field is available only when the **Adjust existing schedule** option is set to **Yes**.</p> |
| End date | <p>Depending on the type of deferral, the end date might or might not be updated:</p><ul><li>For a straight line deferral, specify the new end date of the schedule. The existing end date of the deferral schedule is the default value.</li><li>For an event based deferral, specify the end date of the credit event line. This date can be blank.</li></ul><p>This field is available only when the **Adjust existing schedule** option is set to **Yes**.</p> |
| Billing schedule number | <p>The billing schedule number.</p><p>This field is available only for recurring contract billing schedules.</p> |
| Deferral adjustment method | <p>The deferred adjustment method. The value matches the value on the **Mass termination processing** page for the recurring contract billing schedule.</p><p>This field is available only for recurring contract billing schedules.</p> |
| **Accounts - Revenue** | |
| Deferral account | <p>The deferral account, which is the posting account that appears on the **Sales order** page.</p><p>If the line isn't deferred, this field is blank. In this case, the posting account is the default revenue account.</p> |
| Recognition account | <p>Specify the account that is used when a deferral is recognized. This account must differ from the deferral account.</p><p>When the **Deferred** option is initially set to **Yes**, the dimension values that are used in the deferral account are copied to the recognition account. If the dimension in the deferral account doesn't exist for the recognition account, it's ignored.</p> |
| Initial recognition account | <p>Select the account for the initial revenue recognition. The default value is from the **Deferral defaults** page.</p><p>This field is available only when the **Deferral posting method** field is set to **Profit and loss** on the **Revenue and expense deferrals parameters** page.</p> |
| Recognition offset account | <p>Select the account for offsetting revenue recognition. The default value is from the **Deferral defaults** page.</p><p>This field is available only when the **Deferral posting method** field is set to **Profit and loss** on the **Revenue and expense deferrals parameters** page.</p> |
| **Accounts - Discount** | This section appears only for deferred items. It's hidden for deferred charges. |
| Deferral account | <p>Specify the discount deferral account number. The default value is from the **Deferral defaults** page.</p><p>This field is available only when the **Discount deferral option** field is set to **Separate schedule for discount** on the **Revenue and expense deferrals parameters** page and a discount is applied to the line.</p> |
| Recognition account | <p>Specify the discount recognition account number. The default value is from the **Deferral defaults** page.</p><p>This field is available only when the **Discount deferral option** field is set to **Separate schedule for discount** on the **Revenue and expense deferrals parameters** page and a discount is applied to the line.</p> |
| Initial recognition account | <p>Select the account for the initial discount recognition. The default value is from the **Deferral defaults** page.</p><p>This field is available only when the **Deferral posting method** field is set to **Profit and loss** on the **Revenue and expense deferrals parameters** page and a discount is applied to the line.</p> |
| Recognition offset account | <p>Select the account for offsetting revenue recognition. The default value is from the **Deferral defaults** page.</p><p>This field is available only when the **Deferral posting method** field is set to **Profit and loss** on the **Revenue and expense deferrals parameters** page and a discount is applied to the line.</p> |
| **Accounts - Consumption** | This section appears only for deferred items. It's hidden for deferred charges. |
| Deferral account | <p>Specify the consumption deferral account number.</p><p>For standard products, two deferral schedules are created:</p><ul><li>**Standard sales** – A revenue schedule that has a credit balance. In this case, select the consumption deferral account.</li><li>**Consumption** – A consumption (cost of goods sold \[COGS\]) expense schedule that has a debit balance. In this case, select the consumption recognition account.</li></ul><p>When the invoice is posted, the consumption amount is posted to the specified consumption deferral account. These fields aren't available for service items.</p> |
| Recognition account | Specify the consumption recognition account number. |
| Initial recognition account | <p>Specify the account for the initial consumption recognition amount. The default value is from the **Deferral defaults** page.</p><p>This field is available only when the **Deferral posting method** field is set to **Profit and loss** on the **Revenue and expense deferrals parameters** page.</p> |
| Recognition offset account | <p>Specify the account for the consumption recognition offset amount. The default value is from the **Deferral defaults** page.</p><p>This field is available only when the **Deferral posting method** field is set to **Profit and loss** on the **Revenue and expense deferrals parameters** page.</p> |
| **Schedule** | |
| Schedule type | <p>Select the deferral schedule type: **Straight line** (default) or **Event based**.</p><p>The options that appear on the page are based on the deferral schedule type that you select.</p><p>If the default template is set on the **Deferral defaults** page for the transaction line, the deferral schedule type is based on the type of template that is selected.</p> |
| **Schedule - Straight line** | |
| Consolidate prior periods | <p>Specify whether you want to consolidate deferral schedule lines for earlier periods:</p><ul><li>**Yes** – Consolidate the deferral schedule lines for earlier periods.</li><li>**No** – Don't consolidate deferral schedule lines for earlier periods.</li></ul><p>The default value is from the **Revenue and expense deferrals parameters** page.</p> |
| Equal per period | <p>Specify whether the number of days in every period is equal or varies by period:</p><ul><li>**Yes** – Every period has the same number of days.</li><li>**No** – Periods don't have the same number of days.</li></ul><p>When this option is set to **No**, the number of days in a period is considered when the amount in each period for a deferral schedule is calculated.</p><p>The default value is from the **Revenue and expense deferrals parameters** page.</p> |
| Schedule from template | <p>Specify whether the deferral schedule is created based on a template or an end date:</p><ul><li>**Yes** – The deferral schedule is created based on a template.</li><li>**No** – The deferral schedule is created based on an end date.</li></ul> |
| Template | Select the deferral template. |
| Override start date | <p>Specify whether you want to override the start date:</p><ul><li>**Yes** – Override the start date with the date that you enter in the **Start date** field.</li><li>**No** – The start date is the **Default deferral start date** rule that is applied to the invoice date that is specified on the **Posting invoice** page. This rule can be set on the **Revenue and expense deferrals parameters** page.</li></ul> |
| Deferral start date | Specify the start date of the deferral. The transaction date is the default value. |
| Deferral end date | <p>The end date of the deferral.</p><p>This date is automatically calculated based on the deferral template. If no template is selected, you must manually enter the date.</p> |
| **Schedule - Event based** | |
| Template | <p>Select the event-based template. This field is optional.</p><p>If you select a template, the values from the template overwrite all event-based data and event lines.</p> |
| Allocation type | <p>Select the allocation type for the event lines:</p><ul><li>**Variable amounts** – A specific allocation amount is entered for each line.</li><li>**Equal amounts** – The amount is allocated equally for each line.</li><li>**Percentage** – An amount is allocated based on the percentage value that is entered for each line.</li><li>**Percentage of completion** – A cumulative completion value is entered for each line.</li><p>**Variable quantity** – A specific allocation quantity is entered for each line.</li></ul><p>**Note:** If you want to select **Percentage of completion**, the dates must be in ascending order.</p> |
| **Create separate events per unit** | |
| Description | <p>Specify whether you want to separate events per unit:</p><ul><li>**Yes** – Separate the event lines so that there is one line per quantity.<p>For example, there are three event lines, and the invoice has a quantity of four. In this case, the resulting deferral schedule has 12 lines.</p></li><li>**No** – Don't separate the event lines.</li></ul> |
| Expiration account | <p>Select the account that is used for recognized expired lines. You can select the account after the deferral schedule is created.</p><p>If an expiration date is set for an event, during the recognition process, the recognition amount goes to the expiration account instead of the recognition account.</p> |
| **Schedule - Event based lines** | |
| Description | A description of the event. |
| Deferral end date | <p>Select the end date of the event.</p><p>**Note:** If you select an end date, the **Expiration date** field is cleared. You can't use both an end date and an expiration date.</p> |
| Expiration date | <p>Select the expiration date of the event.</p><p>**Note:** If you select an end date, the **Expiration date** field is cleared. You can't use both an end date and an expiration date.</p> |
| Quantity | <p>Specify the allocation quantity. The default value for all lines is **0** (zero). If you update the quantity, the total quantity of all lines must be equal to or less than the quantity that is specified for the line item on the sales order.</p><p>This field is available only when the **Allocation type** field is set to **Variable quantity**.</p><p>If the quantity of the line item on the sales order is changed so that it's less than the original quantity, and the invoice is created, fewer event-based lines are created. The total allocated quantity doesn't exceed the quantity that is specified on the originating sales order or billing schedule.</p> |
| Allocation percentage | <p>Specify the allocation percentage. If the **Allocation type** field is set to **Percentage** or **Percentage of completion**, you can manually enter a percentage. Otherwise, it's automatically calculated.</p><p>If the **Allocation type** field is set to **Percentage**, the total of the percentages must equal 100.</p> |
| Amount | <p>Specify the allocation amount. If the **Allocation type** field is set to **Variable amounts** or **Percentage of completion**, you can manually enter an amount.</p><p>If the **Allocation type** field is set to **Percentage of completion**, and you enter an amount here, the value of the **Completion percentage** field is automatically calculated.</p><p>Because of rounding, the calculated amount might not exactly match what is manually entered. If you require an exact amount, set the **Allocation type** field to **Variable amounts**.</p> |
| Completion percentage | <p>Specify the percentage of completion. The value must be between 0 (zero) and 100.</p><p>This field is available only when the **Allocation type** field is set to **Percentage of completion**.</p> |
| Completion amount | <p>The calculated total for all lines in the deferral schedule.</p><p>If the **Allocation type** field is set to **Percentage of completion**, you can manually enter an amount. In this case, the value of the **Completion percentage** field is calculated based on the amount that you enter.</p><p>Because of rounding, the calculated amount might not exactly match what is manually entered.</p><p>This field is available only when the **Allocation type** field is set to **Percentage of completion**.</p> |
| Recognize on post | <p>Specify whether the line is automatically recognized as soon as the transaction is posted:</p><ul><li>**Selected** – The line is automatically recognized as soon as the transaction is posted.</li><li>**Cleared** – The line isn't recognized as soon as the transaction is posted.</li></ul> |
| Recognition account | <p>Specify the recognition account for the event, if the account differs from the account that is used for the whole deferral schedule.</p><p>You can use this field in conjunction with the **Recognize on post** option.</p> |
