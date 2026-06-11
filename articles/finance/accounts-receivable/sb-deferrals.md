---
title: Revenue and expense deferrals in Subscription billing
description: Learn how to set up revenue and expense deferrals in Subscription billing, including an overview on revenue and expense deferral parameters.
author: twheeloc
ms.author: twheeloc
ms.topic: article
ms.date: 06/04/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2021-11-05
ms.search.form:  
ms.dyn365.ops.version: 10.0.24
---

# Revenue and expense deferrals in Subscription billing

This article explains how to set up and use revenue and expense deferrals in Subscription billing. Deferral schedules always depend on an underlying originating document or billing schedule. Because default values create them, you can't enter or create deferral schedules separately.

The process of setting up and using revenue and expense deferrals occurs on multiple pages:

- On the **Revenue and expense deferral parameters** page, define the company preferences.
- On the **Deferral defaults** page, set up the default accounts and templates that are used for the deferral schedules.
- On the **Deferral templates** and **Event based deferral templates** pages, define the templates that are used for the deferral schedules.
- On the **All deferral schedules** page, view and edit any deferral schedule.

Use revenue and expense deferrals together with recurring contract billing.

## Revenue and expense deferral parameters

The **Revenue and expense deferral parameters** page contains the following fields.

| Field | Description |
|---|---|
| **Schedule** tab | |
| Equal per period | <p>Specify whether the number of days in a period is used when the amount per period is calculated for a deferral schedule:</p><ul><li>**Yes** – The amount for each period is the same, regardless of the number of days in the period. Partial periods (such as periods at the beginning or end of a deferral schedule) are prorated.</li><li>**No** – The amount is calculated based on the number of days in each period.</li></ul><p>You can override this setting at the transaction level.</p> |
| Sales discount deferral option | <p>Specify whether separate deferral schedules are created for the discount and the sales order amounts:</p><ul><li>**Separate schedule for discount** – The discount amount is kept separate from the revenue amount.<p>In this case, two deferral schedules are created when a sales order is created and then posted. The discount and revenue amounts go to different deferral accounts.</p></li><li>**Merge discount with revenue** – The discount amount is combined with the revenue amount. One deferral schedule is created, and both the discount amount and the revenue amount go to the same deferral account.<p>In this case, one deferral schedule is created when a sales order is created and then posted. Both the discount amount and the revenue amount go to the same deferral account.</p></li></ul><p>**Note:** To apply discounts to items that use the unbilled revenue feature, select the **Separate schedule for discount** option. You can then apply discounts to all items, regardless of whether the unbilled revenue feature is used. If you select the **Merge discount with revenue** option, you can't apply discounts to items that use the unbilled revenue feature.</p> |
| Purchasing discount deferral option | <p>Select whether separate deferral schedules are created for the discount and purchase order amounts:</p><ul><li>**Separate schedule for discount** – The discount amount is kept separate from the expense amount.<p>In this case, two deferral schedules are created when a purchase order is created and then posted. The discount and expense amounts are posted to different deferral accounts.</p></li><li>**Merge discount with revenue** – The discount amount is combined with the expense amount. One deferral schedule is created, and both the discount amount and the expense amount are posted to the same deferral account.<p>In this case, one deferral schedule is created when a purchase order is created and then posted. Both the discount amount and the expense amount are posted to the same deferral account.</p></li></ul> |
| Consolidate prior periods | <p>Specify whether deferral schedule lines for previous periods are consolidated:</p><ul><li>**Yes** – If the deferral start date is in a period before the transaction date, all amounts up through the period of the transaction date are combined onto a single deferral schedule line.</li><li>**No** – The amounts from all periods are kept on separate deferral schedule lines.<p>If the deferral start date is in the same period as or a later period than the transaction date, this option has no effect.</p></li></ul><p>You can update this setting at the transaction level.</p> |
| Default deferral start date | <p>Select the rule that is used to determine the start date of the deferral schedule:</p><ul><li>**Transaction date** – Use the transaction date as the start date.</li><li>**Beginning of current month** – Use the first of the current month as the start date. If the transaction date is the first of any month, the first of the current month is the start date.</li><li>**Beginning of next month** – Use the first of the next month as the start date. If the transaction date is on the first, the transaction date is used. Otherwise, the first of the next month is used.</li><li>**Rule of 15** – If the transaction date is between the first and the fifteenth, use the first of the current month as the start date. If the transaction date is the sixteenth or later, use the first of the next month as the start date.</li></ul><p>You can update this setting at the transaction level.</p> |
| Short-term deferral method | <p>Select the short-term deferral method: **None**, **Rolling periods**, or **Fixed year**.</p> |
| Deferral posting method | <p>Select the method that is used to create deferral transactions:</p><ul><li>**Balance sheet** – Use the balance sheet posting method to create deferral transactions.</li><li>**Profit and loss** – Use the profit and loss posting method to create deferral transactions. When you post transactions, you can review the invoice voucher to see the extra entries that balance the initial recognition and recognition offset amounts.</li></ul> |
| Reverse profit and loss on credit | <p>**Note:** This field is available only when the **Deferral posting method** field is set to **Profit and loss**.</p><p>Specify whether the profit and loss amounts are reversed when a reversal, termination, or refund is applied to a billing schedule or sales order:</p><ul><li>**Yes** – Reverse the profit and loss amounts, and apply a credit adjustment amount to the deferral schedule.<p>If the reversal occurs halfway through a billing period, the amounts are prorated.</p></li><li>**No** – No reversal transaction is created for the profit and loss when a reversal, termination, or refund is applied to a billing schedule or sales order.</li></ul> |
| **Recognition** tab | |
| Automatically post general journals | <p>Specify whether journal entries that are created by revenue and expense deferrals are automatically posted:</p><ul><li>**Yes** – Automatically post journal entries that are created by revenue and expense deferrals.<p>**Tip:** By selecting **Yes**, you can help prevent accounting inconsistencies that are caused by manual changes to vouchers.</p></li><li>**No** – Journal entries that are created by revenue and expense deferrals aren't automatically posted. You must manually post any journals.</li></ul> |
| Summarize recognition journal | <p>Specify whether recognition vouchers are consolidated by default:</p><ul><li>**Yes** – Create a single voucher for all recognition lines that have the same date. All lines in a voucher that have the same account are consolidated onto a single line.</li><li>**No** – Create a voucher for each recognition line.</li></ul><p>You can update this setting on the **Recognition processing** page.</p> |
| Default journal name | Select the journal name for journals that are created from revenue and expense deferral processes, such as recognition processing. |
| Recognition journal line description | <p>Select the description that appears in the journal voucher line description:</p><ul><li>**Schedule line dates** – Show the schedule line dates in the journal line description.</li><li>**Originating transaction details** – Show the originating transaction information in the journal line description.<p>**Example:** USMF-0001, CIV-00839, Software Revenue</p></li></ul> |
| **Number sequences** tab | Use this tab to set the default values for lease number sequences. The number sequence generation wizard is used to automatically generate and assign number sequences. You don't have to change the number sequence unless you want to make manual changes to the generated number sequences. |
| Schedule number | The number that is sequence used for deferral schedules. |

## Deferral templates

Use the **Deferral templates** page to define straight-line templates for deferral schedules.

Here are some advantages of using a template:

- The deferral length is automatically calculated.
- You can create deferral schedules with periods where recognition is skipped.
- You can automate deferrals by assigning the template to a product, product group, product category, customer, or customer group. Assign templates from the **Deferral defaults** page.

Templates support several period frequencies: daily, monthly, or fiscal periods.

The template lines consist of a type (**Recognized** or **Skipped**) and the period length. Skipped lines have an amount of 0 (zero) on the deferral schedule lines. This behavior is useful if you don't want to recognize revenue in all periods.

### Create a deferral template

To create a deferral template, follow these steps:

1. On the **Deferral templates** page, select **New**.
1. In the **Template** field, enter a name.
1. In the **Description** field, enter a description.
1. In the **Period frequency** field, select the period frequency.
1. Select **Add** to add a line to the top of the list of lines, or select **Append** to add a line to the bottom of the list.
1. In the **Type** field, select the type of period.
1. In the **Period length** field, specify the length of the period.
1. Repeat steps 5 through 7 for each additional line that you require.
1. Select **Save**.

## Deferral defaults

Use the **Deferral defaults** page to set up default deferral accounts for items and to assign default templates to deferrable items. You can also set up deferral accounts for charges and assign templates to the deferrable charges.

**Defer by item**

For transactions that have an item (for example, sales orders), you can assign accounts and templates to specific items and customers. These settings serve as default values when you defer a transaction. To make the transaction deferrable by default, set up the items on the **Deferrable items** page.

**Defer by account**

For transactions that don't have items (for example, general journals), specify the deferral accounts. When you use these accounts on a transaction line, the system automatically marks the transaction as deferred. The corresponding template and recognition account are assigned to the transaction line.

**All transaction types (for example, on the Sales order, Purchasing, and General journal tabs)**

The accounts on the page are the main accounts that don't have financial dimensions. The financial dimensions of the recognition account come from the customer or item, based on your organization.

Each template line must have either a straight line template or an event-based template. It can't have both.

### For sales orders

To specify the deferral default values for sales orders, follow these steps:

1. On the **Sales order** tab, select the deferral type.
1. Select **Add** to add a line.
1. In the **Item code** field, select the item code. The item code determines how the deferral default values are applied.
1. Specify how the item code is applied:

    - If you set the **Item code** field to **Table** or **Group**, select the item relation in the **Item relation** field.
    - If you set the **Item code** field to **Category**, select the category relation in the **Category relation** field.
    - If you set the **Item code** field to **All**, the default values apply to all applicable records.

1. Specify how the account code is applied:

    - If you set the **Account code** field to **Table** or **Group**, select the account relation in the **Account relation** field.
    - If you set the **Account code** field to **All**, the account applies to all records.

1. In the **Main account** field, select the main account for the deferral.
1. If you set the **Deferral posting method** field to **Profit and loss**, select the initial revenue account in the **Initial revenue account** field and the revenue offset account in the **Revenue offset account** field.
1. If you set the **Short-term deferral method** field to **Rolling periods** or **Fixed year**, select the short-term deferral account in the **Short-term deferral account** field.
1. For a template, select **Add** to add a line.
1. In the **Item code** field, select the item code.
1. Specify how the item code is applied:

    - If you set the **Item code** field to **Table** or **Group**, select the item relation in the **Item relation** field.
    - If you set the **Item code** field to **Category**, select the category relation in the **Category relation** field.
    - If you set the **Item code** field to **All**, the default values apply to all applicable records.

1. Specify how the account code is applied:

    - If you set the **Account code** field to **Table** or **Group**, select the account relation in the **Account relation** field.
    - If you set the **Account code** field to **All**, the account applies to all applicable records.
    - Select the straight line template in the **Straight line template** field or the event-based template in the **Event based template** field.

1. Select **Save**.

### For purchase orders

To specify the deferral default values for purchase orders, follow these steps:

1. On the **Purchasing** tab, select the deferral type.
1. Select **Add** to add a line.
1. In the **Item code** field, select the item code.
1. Specify how the item code is applied:

    - If you set the **Item code** field to **Table** or **Group**, select the item relation in the **Item relation** field.
    - If you set the **Item code** field to **Category**, select the category relation in the **Category relation** field.
    - If you set the **Item code** field to **All**, the default values apply to all applicable records.

1. Specify how the account code is applied:

    - If you set the **Account code** field to **Table** or **Group**, select the account relation in the **Account relation** field.
    - If you set the **Account code** field to **All**, the account applies to all applicable records.

1. In the **Main account** field, select the main account for the deferral.
1. If you set the **Deferral posting method** field to **Profit and loss**, select the initial revenue account in the **Initial revenue account** field and the revenue offset account in the **Revenue offset account** field.
1. If you set the **Short-term deferral method** field to **Rolling periods** or **Fixed year**, select the short-term deferral account in the **Short-term deferral account** field.
1. For a template, select **Add** to add a line.
1. In the **Item code** field, select the item code.
1. Specify how the item code is applied:

    - If you set the **Item code** field to **Table** or **Group**, select the item relation in the **Item relation** field.
    - If you set the **Item code** field to **Category**, select the category relation in the **Category relation** field.
    - If you set the **Item code** field to **All**, the default values apply to all applicable records.

1. Specify how the account code is applied:

    - If you set the **Account code** field to **Table** or **Group**, select the account relation in the **Account relation** field.
    - If you set the **Account code** field to **All**, the account applies to all applicable records.
    - Select the straight line template in the **Straight line template** field or the event-based template in the **Event based template** field.

1. Select **Save**.

### For general journals

To specify the deferral default values for general journal entries, follow these steps:

1. Select the **General journal** tab.
1. For a deferral, select **Add** to add a line.
1. If the **Short-term deferral method** field is set to **Rolling periods** or **Fixed year**, select the short-term deferral account in the **Short-term deferral account** field.
1. In the **Deferral account** field, select the deferral account.
1. In the **Recognition account** field, select the recognition account.
1. If the **Deferral posting method** field is set to **Profit and loss**, select the initial revenue account in the **Initial revenue account** field and the revenue offset account in the **Revenue offset account** field.
1. Select the straight line template in the **Straight line template** field or the event-based template in the **Event based template** field.
1. Select **Save**.

### For free text invoices

To specify the deferral default values for free text invoices, follow these steps:

1. Select the **Free text invoice** tab.
1. For a deferral, select **Add** to add a line.
1. Specify how the account code is applied:

    - If you set the **Account code** field to **Table** or **Group**, select the account relation in the **Account relation** field.
    - If you set the **Account code** field to **All**, the account code applies to all applicable records.

1. In the **Deferral account** field, select the deferral account.
1. If you set the **Short-term deferral method** field to **Rolling periods** or **Fixed year**, select the short-term deferral account in the **Short-term deferral account** field.
1. In the **Recognition account** field, select the recognition account.
1. If you set the **Deferral posting method** field to **Profit and loss**, select the initial revenue account in the **Initial revenue account** field and the revenue offset account in the **Revenue offset account** field.
1. Select the straight line template in the **Straight line template** field or the event-based template in the **Event based template** field.
1. Select **Save**.

### For invoice journals

To specify the deferral default values for invoice journal entries, follow these steps:

1. Select the **Invoice journal** tab.
1. For a deferral, select **Add** to add a line.
1. Specify how the account code is applied:

    - If you set the **Account code** field to **Table** or **Group**, select the account relation in the **Account relation** field.
    - If you set the **Account code** field to **All**, the account code applies to all applicable records.

1. In the **Deferral account** field, select the deferral account.
1. If you set the **Short-term deferral method** field to **Rolling periods** or **Fixed year**, select the short-term deferral account in the **Short-term deferral account** field.
1. In the **Recognition account** field, select the recognition account.
1. If you set the **Deferral posting method** field to **Profit and loss**, select the initial revenue account in the **Initial revenue account** field and the revenue offset account in the **Revenue offset account** field.
1. Select the straight line template in the **Straight line template** field or the event-based template in the **Event based template** field.
1. Select **Save**.

### Items that are deferred by default

Use the **Items deferred by default** page to define which items are deferred by default. Set up the types of transactions that the items are deferred for. Specify whether a single item is deferred, or a whole item group or category.

When you set up items as deferred, select the default accounts and templates on the **Deferral defaults** page. If you don't select the accounts and templates, transaction lines where you enter those items aren't deferred.

For items that are deferred based on the sales or purchasing category that they're associated with, the deferral settings are based on the category. However, if you don't select the category in the **Category relation** field, the deferral settings of the category that's higher in rank are used. For example, you add a **Home video** sales category but not a **Television** sales category. When you add a deferral item that is associated with the **Television** category, the deferral settings of the **Home video** category are used for the item.

### Set up deferred items

To set up items that are deferred by default, follow these steps:

1. On **Items deferred by default**, select the tab that you want: **Sales order** or **Purchasing**.
1. Select **Add** to add a line.
1. In the **Item code** field, select the item code.
1. Specify how the item code is applied:

    - If you set the **Item code** field to **Group** or **Table**, select the item relation in the **Item relation** field.
    - If you set the **Item code** field to **Category**, select the category relation in the **Category relation** field.

1. Repeat steps 2 through 4 for each additional line that you require.
1. Select **Save**.

## Deferred charges

Use the **Deferral charges** page to define which charges are deferred by default.

> [!NOTE]
>
> - Currently, deferrable charges are available for sales orders only.
> - You can defer charges at the line level only. To defer a charge at the sales order header level, set up the charge as a deferred item on a separate line on the sales order.
> - To defer a charge for a free text invoice, enter the charge as a separate deferred invoice line.
> - This functionality isn't available for support charges and the revenue split functionality.

### Set up deferred charges

To set up deferred charges, follow these steps:

1. On **Deferral charges**, select **Add** to add a line.
1. In **Charge code**, select the charge code.
1. In **Charge relation**, select the charge relation.
1. For each additional line that you require, repeat steps 1 through 3.
1. Select **Save**.

## Event-based deferral templates

Use **Event based deferral templates** to define event-based deferral templates that you can use in deferral transactions and assign on **Deferral defaults**.

### Create an event-based template

To create an event-based deferral template, follow these steps:

1. On the **Event based deferral templates** page, select **New**.
1. In the **Template** field, enter a unique name for the template.
1. In the **Description** field, enter a description.
1. In **Allocation type**, select the allocation type:

    - **Variable amount** – Allocate a specific amount for each line that you enter.
    - **Equal amount** – Allocate the same amount for each line that you enter.
    - **Percentage** – Allocate an amount that’s based on the percentage value that you enter for each line.
    - **Percentage of completion** – Allocate a cumulative completion value for each line that you enter.
    - **Variable quantity** – Allocate a specific quantity for each line that you enter.

1. Set the **Create separate events per unit** option to **Yes** if you want each event line to split evenly by the number of units on the invoice transaction. Set it to **No** if you don't want to split the event lines.
1. In the **Expiration account** field, select the expiration account.
1. Select **Add** to add a line to the top of the list of lines, or select **Append** to add a line to the bottom of the list.
1. In the **Description** field, enter a description of the event.
1. If the **Allocation type** field is set to **Percentage**, specify the allocation percentage in the **Allocation percentage** field. The percentage must be between 0 (zero) and 100. If you leave the **Allocation percentage** field blank, the percentage is considered 0. The sum of all percentages is shown in the **Total percentage** field at the bottom of the page and must equal 100.
1. In the **Months to expiration** field, specify the number of months that the event is valid. The expiration date on the transaction deferral is automatically entered based on this value.
1. Select the **Recognize when posted** checkbox to automatically recognize revenue when the transaction is posted. If you leave the checkbox cleared, the revenue must be manually recognized.
1. In the **Recognition account** field, select the recognition account for the event, if the event uses a different account than the whole deferral schedule. This field is used together with the **Recognize when posted** checkbox.
1. Repeat steps 7 through 12 for each additional line that you require.
1. Select **Save**.
