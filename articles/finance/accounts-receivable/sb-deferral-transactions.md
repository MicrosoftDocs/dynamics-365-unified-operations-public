---
# required metadata

title: Deferral transactions in Subscription billing
description: This topic describes the various transactions that can be used in deferral transactions as part of Revenue and expense deferrals in Subscription billing.
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

This topic describes the transactions that allow for revenue and expense deferrals. Deferral schedules are always based on and are dependent on an originating document or billing schedule. Deferral schedules are created based on defaults and can't be entered or created separately.

## Sales order transaction deferral

Use the **Deferrals** or the **Create credit note** page to enter or edit the deferral parameters for a sales order line. 

> [!Note] 
> When a sales order is created from a billing schedule, all values in this page are read-only, and the deferral parameters cannot be edited. To edit the values, use the **Modify Schedule** page. 

### Edit deferral options

Edit deferral options for a line: 
1. Create a sales order transaction. 
2. Select the line and click **Deferrals**. 
3. On the **Transaction deferral** page, the **Deferred** option needs to be **Yes**. Edit any fields as needed. 
4. To view a preview of the deferral schedule, click **Preview**. 
5. If you made any changes to the transaction deferral, select **OK**, and return to the transaction page. 
6. Commit and post the transaction. 

After the transaction is posted, open the **All deferral schedules** page to view the deferral schedule. 

### Create a credit note

To create a credit note, follow these steps: 
1. Create a sales order transaction. 
2. In the **Sales order lines** area, select the item for which you want to create a credit note. 
3. Select **Sales order line** > **New**, select **Credit note**.  
4. Select **Deferrals** to open the **Sales order transaction deferral** page. 
5. For the item, set **Adjust existing schedule** to **Yes**.
6. In **Adjusted schedule**, select the deferral schedule to which you want to apply the credit note. 
7. Update the **Recalculate date** and **End date** as needed.
8. Select **OK**.
9. Finish posting the sales order transaction.

### Purchase order and Purchase invoice

If you want to use the deferral functionality for a purchase order, generate the invoice first. Then use the **Pending vendor invoices** to edit or add deferral items. You can't edit or add deferrals directly on a purchase order.

1. Use the **Pending vendor invoices** page to enter a vendor invoice. 
2. When you enter a line, the deferral is automatically set for the item or procurement category selected. This is based on the deferral setup on the **Deferral defaults** pages. The deferrals can be edited or added at the distribution level. 
3. On the purchasing line, select **Financials > Distribute amounts**. 
4. Select **Deferrals** for each distribution amount. When the invoice is posted, a deferral schedule is created for each distribution that has a deferral set.

### Tax

In some cases, the tax amount can be fully or partially non-recoverable. When the tax amount of a deferrable line contains a non-recoverable amount, the non-recoverable tax amount is included in the deferrable schedule amount when the invoice is posted.

### Variance

If a difference between the vendor invoice line amount and the purchase order line amount exists, variance distributions are created. If the line is deferred, the ledger account for these distributions is set to the deferral account and the amounts are included in the deferrable schedule amount when the invoice is posted. These distributions are **Price variance** and **Cost variance**.

### General journal and Invoice journal

Use the **Deferrals** page to enter the deferral parameters for a journal voucher line. You can also see a preview of the deferral schedule for straight line deferrals. When you enter a line, the deferral is automatically set based on the deferral accounts setup on the **Deferral Defaults** page. You can manually change the deferral options for each line. When the journal voucher is posted, the deferral schedule is created. 

### Post and transfer

When you post the journal voucher, use the **Post and transfer** menu item. The deferral options will follow the line to which it applies. For vouchers that don't have errors, a deferral schedule is created if it's deferred. For vouchers that have errors and are transferred, any deferral options are also transferred with it. 

### Tax

In some cases, the tax amount can be fully or partially non-recoverable. When the tax amount of a deferrable line contains a non-recoverable amount, the non-recoverable tax amount is included in the deferrable schedule amount when the invoice is posted.

## Free text invoice transaction deferral

Use the **Deferrals** page to enter the deferral parameters for a free text invoice line distribution. When a distribution is entered, the deferral is automatically set based on the deferral settings on the **Deferral defaults** page. 
 
## Fields

The **Transaction deferral** page contains the following fields: 

|Field| Description|
| :------- |:------| 
|**Deferred**|Select if the line is a deferral: <br />**Yes**: The line is a deferral. <br />**No**: The line is not a deferral. <br />When set to **Yes**, the **Adjust existing schedule** option isn't available. For items and charges already set up as deferred, this option is set to **Yes**. For items and charges that aren't set as deferred by default, change the option to **Yes**. |
|**Adjust existing schedule**|Select if the line is an adjustment to an existing deferral schedule: <br />**Yes**: The new sales line is an adjustment to an existing deferral schedule. When selected, you can then select the **Adjust schedule**. <br />**No**: The new sales line isn't an adjustment to an existing deferral schedule. <br />When set to **Yes**, the **Deferred** option isn't available. |
|**Adjusted schedule**|Select the deferral schedule for which this line is adjusting. When selected, all values in this page are updated with the values from the originating deferral schedule. These values can't be edited. <br />Available when **Adjust existing schedule** is **Yes**. |
|**Recalculation date**|Specify the start date of the period from which you want to recalculate the remaining amount. The default date is the date of the next unrecognized period.<br />Available when **Adjust existing schedule** is **Yes**. |
|**End date**|Depending on the type of deferral, the end date may or may not be updated: <br />For a straight line deferral, specify the new end date of the schedule. The default date is the existing end date for the deferral schedule. <br />For an event based deferral, specify the end date of the credit event line. This date may be blank. <br />Available when **Adjust existing schedule** is **Yes**. |
|**Billing schedule number**|Displays the billing schedule number. <br />Available for Recurring contract billing schedules only. |
|**Deferral adjustment method**|Displays the deferred adjustment method. This value is the same as the value on the Recurring contract billing **Mass termination processing** page. <br />Available for Recurring contract billing schedules only. |
|**Accounts - Revenue**|   |
|**Deferral account**|Displays the deferral account is the posting account that appears on the **Sales order** page. <br />When the line isn't a deferred, this account is cleared. The posting account becomes the default revenue account. |
|**Recognition account**|Specify the account used when a deferral is recognized. This account must be different than the deferral account. <br />When **Deferral** is initially set to **Yes**, the dimension values used in the deferral account are copied to the recognition account. If the dimension in the deferral account doesn't exist for the recognition account, then it's ignored. |
|**Initial recognition account**|Select the account for the initial revenue recognition. The default value is from the **Deferral defaults** page.<br />Available only when **Deferral posting method** is **Profit and loss** on the **Revenue and expense deferrals parameters** page. |
|**Recognition offset account**|Select the account for revenue recognition offset. The default value is from the **Deferral defaults** page.<br />Available only when **Deferral posting method** is **Profit and loss** on the **Revenue and expense deferrals parameters** page. |
|**Accounts - Discount**|This section appears for deferred items only, and is hidden for deferred charges. |
|**Deferral account**|Specify the discount deferral account number. The default value is from the **Deferral defaults** page. <br />Available when **Discount deferral option** is set to **Separate schedule for discount** on the **Revenue and expense deferrals parameters** page and when a discount is applied to the line.|
|**Recognition account**|Specify the discount recognition account number. The default value is from the **Deferral defaults** page. <br />Available when **Discount deferral option** is set to **Separate schedule for discount** on the **Revenue and expense deferrals parameters** page and when a discount is applied to the line.|
|**Initial recognition account**|Select the account for the initial discount recognition. The default value is from the **Deferral defaults** page.<br />Available only when **Deferral posting method** is **Profit and loss** on the **Revenue and expense deferrals parameters** page and when a discount is applied to the line. |
|**Recognition offset account**|Select the account for offsetting revenue recognition. The default value is from the **Deferral defaults** page.<br />Available only when **Deferral posting method** is **Profit and loss** on the **Revenue and expense deferrals parameters** page and when a discount is applied to the line.|
|**Accounts - Consumption**|This section appears for deferred items only, and is hidden for deferred charges. |
|**Deferral account**|Specify the consumption deferral account number.<br />For standard products, two deferral schedules are created: <br /> Standard sales: A revenue schedule with a credit balance. <br />Select the consumption deferral account. <br />Consumption: A consumption (COGS) expense schedule with a debit balance.<br />Select the consumption recognition account.<br />When the invoice is posted, the consumption amount is posted to the consumption deferral account specified. These fields aren't available for service items.|
|**Recognition account**|Specify the consumption recognition account number. |
|**Initial recognition account**|Specify the account for the initial consumption recognition amount. The default value is from the **Deferral defaults** page.<br />Available only when **Deferral posting method** is **Profit and loss** on the **Revenue and expense deferrals parameters** page.  |
|**Recognition offset account**|Specify the account for consumption recognition offset amount. The default value is from the **Deferral defaults** page.<br />Available only when **Deferral posting method** is **Profit and loss** on the **Revenue and expense deferrals parameters** page. |
|**Schedule**|
|**Schedule type**|Select the deferral schedule type: **Straight line** (default) or **Event based**. <br />The options that appear on this page are based on the deferral schedule type. <br />If the default template is set on the **Deferral Defaults** page for this transaction line, the deferral schedule type is based on the type of template selected.|
|**Schedule - Straight Line**|
|**Consolidate prior periods**|Select if you want to consolidate deferral schedule lines for prior periods: <br />**Yes**: Consolidates the deferral schedule lines for prior periods. <br />**No**: Doesn't consolidate deferral schedule lines for prior periods. <br />The default value is from the **Parameters** page.
|**Equal per period**|Specify whether the number of days in a period are equal or different based on the period: <br />**Yes**: Each period has the same number of days. <br />**No**: The number of days within a period are not equal. <br />When the periods don't have an equal number of days, the number of days in a period is considered when the amount in each period for a deferral schedule is calculated. <br />The default value is from the **Parameters** page.|
|**Schedule from template**|Specify whether the deferral schedule is created based on a template or an end date:<br />**Yes**: The deferral schedule is created based on a template. <br />**No**: The deferral schedule is created based on an end date. |
|**Template**|Select the deferral template.|
|**Override start date**|Select to override the start date:<br />**Yes**: Override the start date with the date that you enter in the **Start date** field. <br />* **No**: The start date is the **Default deferral start date** rule that is applied to the invoice date specified on the **Posting invoice** page. This rule can be set on the **Revenue and expense deferrals parameters** page.|
|**Deferral start date**|Specify the start date of the deferral. The transaction date is the default value. |
|**Deferral end date**|Displays the end date of the deferral.<br />This date is automatically calculated based on the deferral template. If no template is selected, you must manually enter the date. |
|**Schedule - Event Based**|
|**Template**|Select the even-based template. Optional. <br />When you select a template, the values from the template overwrite all event-based data and event lines. |
|**Allocation type**|Select the allocation type for the event lines: <br />**Variable amounts**: A specific allocation amount for each line is entered.<br />**Equal amounts**: The amount is allocated equally for each line.<br />**Percentage**: An amount is allocated based on the percentage value entered for each line.<br /> **Percentage of completion**: A cumulative completion value for each line is entered.<br />**Variable quantity**: A specific allocation quantity for each line is entered.<br />If you want to select **Percentage of completion**, the dates must be in ascending order.|
|**Create separate events per unit**|
|**Description**|Select whether to separate events per unit: <br />**Yes**: Separates each event line into one line per quantity. <br />For example, three event lines exist, and the invoice has a quantity of four. The resulting deferral schedule has 12 lines. <br />**No**: Doesn't separate the event lines.|
|**Expiration account**|Select the account to be used for recognized expired lines. You can select the account after the deferral schedule is created. <br />When an expiration date is set for an event, during the recognition process, the recognition amount goes to the expiration account instead of the recognition account. |
|**Schedule - Event Based Lines**|
|**Description**|Displays a description of the event.|
|**Deferral end date**|Select the end date of the event. <br />**Note:** When you select the end date, the **Expiration date** is cleared. You can't use both the end date and expiration date. |
|**Expiration date**|Select the expiration date of the event. <br />**Note:** When you select the end date, the **Expiration date** is cleared. You can't use both the end date and expiration date. |
|**Quantity**|Specify the allocation quantity. The default value for all lines is zero (0). If you update the quantity, the total quantity of all lines must be equal to or less than the quantity specified for the line item on the sales order. <br />Available when **Allocation type** is **Variable quantity**. <br />If the quantity of the line item on the sales order is changed to be lower than the original quantity and the invoice is created, fewer event-based lines are created. The total allocated quantity doesn't exceed the quantity specified on originating the sales order or billing schedule. |
|**Allocation percentage**|Specify the allocation percentage. You can manually type the percentage when **Allocation type** is **Percentage** or **Percentage of completion**. Otherwise, this value is automatically calculated. <br />When **Allocation type** is **Percentage**, the total of the percentage must equal 100. |
|**Amount**|Specify the allocation amount. You can type this amount when **Allocation type** is **Variable amounts** or **Percentage of completion**. <br />When **Allocation type** is **Percentage of completion**, and you type the amount, the **Completion percentage** is automatically calculated. <br />Because of rounding, the amount calculated may not exactly be what is manually entered. If you need an exact amount, use **Variable amounts**. |
|**Completion percentage**|Specify the percentage of completion. Available only when **Allocation type** is **Percentage of completion**. <br />This value must be between zero (0) and 100. |
|**Completion amount**|Displays the calculated total sum for all lines in the deferral schedule. Available only when **Allocation type** is **Percentage of completion**. <br />When **Allocation type** is **Percentage of completion**, you can manually type an amount. If you type the amount, the **Completion percentage** is calculated based on this amount. <br />Because of rounding, the amount calculated may not exactly be what is manually entered. |
|**Recognize on post**|Determines whether the line is automatically recognized as soon as the transaction is posted: <br />**Selected**: The line is automatically recognized as soon as the transaction is posted. <br />**Cleared**: The line isn't recognized as soon as the transaction is posted.|
|**Recognition account**|Specify the recognition account for the event (if the account is different from the entire deferral schedule). <br />You can use this account in conjunction with the **Recognize on post** option. |

