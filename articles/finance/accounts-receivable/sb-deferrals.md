---
# required metadata
title: Revenue and expense deferrals in Subscription billing.
description: This topic explains how to set up revenue and expense deferrals in Subscription billing.
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

# Revenue and expense deferrals

This topic describes how to set up and use revenue and expense deferrals. Deferral schedules are always based on and are dependent on an underlying originating document or billing schedule. Deferral schedules are created based on defaults and can't be entered or created separately. 

 - On the **Revenue and expense parameters** page, you can define the company preferences. 
 - On the **Deferral defaults** page, you can set up the default accounts and templates to use for the deferral schedules. 
 - On the **Event based deferral templates** and **Deferral templates** pages, define the templates used for the deferral schedules. 
 - On the **All deferral schedules** page, you can view and edit any deferral schedule.

Revenue and expense deferrals can be used along with Recurring contract billing.

## Revenue and expense deferral parameters

The **Revenue and expense deferral parameters** page contains the following fields:

|Field| Description|
| :------- |:-------| 
|**Schedule**|
|**Equal per period**|Specify if the number of days in a period should be used when calculating the amount per period for a deferral schedule.<br />* **Yes**: The amount for each period is the same regardless of the number of days in the period. Partial periods (such as at the beginning or end of a deferral schedule) will be prorated. <br />* **No**: The amount is calculated based on the number of days in each period. <br />You can override this setting at the transaction level. |
|**Sales discount deferral option**|Select if separate deferral schedules are created for the discount and the sales order amounts: <br /> **Separate schedule for discount**: Discount amount is kept separate from revenue amount. <br />When a sales order is created and then posted, two deferral schedules are created. The discount and revenue amounts will be posted to different deferral accounts. <br />**Merge discount with revenue**: Discount amount is combined with revenue amount. One deferral schedule is created and both the discount and revenue amounts are posted to the same deferral account. <br />When a sales order is created and then posted, one deferral schedule is created. Both the discount and revenue amounts are posted to the same deferral account. <br />**Note:** To apply discounts to items that use the unbilled revenue feature, select the **Separate schedule for discount** option. This will allow discounts to be applied to all items, regardless if the unbilled revenue feature is used or not. If the **Merge discount with revenue** option is selected, discounts can't be applied to items that use the unbilled revenue feature. |
|**Purchasing discount deferral option**|Select whether separate deferral schedules are created for the discount and the purchase order amounts: <br /> **Separate schedule for discount**: Discount amount is kept separate from the expense amount. <br />When a purchase order is created and then posted, two deferral schedules are created. The discount and expense amounts are posted to different deferral accounts. <br /> **Merge discount with revenue**: Discount amount is combined with expense amount. One deferral schedule is created and both the discount and expense amounts are posted to the same deferral account. <br />When a purchase order is created and then posted, one deferral schedule is created. Both the discount and expense amounts are posted to the same deferral account. |
|**Consolidate prior periods**|Select whether to consolidate deferral schedule lines for prior periods. <br />**Yes**: If the deferral start date is in a period before the transaction date. All amounts up to and including the period of the transaction date are combined into a single deferral schedule line. <br />**No**: The amounts from all periods will be in separate deferral schedule lines. <br />If the deferral start date is in the same or later period as the transaction date, this option has no effect. <br />This setting can be updated at the transaction level. |
|**Default deferral start date**|Select which rule that will be used to determine the start date for the deferral schedule: <br /> **Transaction date**: Use the transaction date as the start date.<br /> **Beginning of current month**: Use the first of the current month as the start date. If the transaction date is the first of any month, then the first of the current month is the start date. <br />**Beginning of next month**: Use the first of the next month as the start date. If the transaction date is on the first, the transaction date is used, otherwise the first of the following month is used. <br />**Rule of 15**: If the transaction date is between the first and the 15<sup>th</sup>, use the first of the current month as the start date. If the transaction date is the 16<sup>th</sup>or later, uses the first of the next month as the start date. <br />You can update this setting at the transaction level. |
|**Short-term deferral method**|Select the short-term deferral method: **None**, **Rolling periods**, or **Fixed year**. <br />For information om how these settings work, see **Short-Term deferral calculation**. |
|**Deferral posting method**|Select the method used to create deferral transactions: <br />**Balance sheet**: Use the balance sheet posting method to create deferral transactions. <br />**Profit and loss**: Use the profit and loss posting method to create deferral transactions. When transactions are posted, you can review the invoice voucher to see the extra entries for balancing the initial recognition and recognition offset amounts. |
|**Reverse profit and loss on credit**|Available when the **Deferral posting method** is **Profit and Loss**. <br />Select whether the profit and loss amounts are reversed when a reversal, termination, or refund is applied to a billing schedule or sales order. <br />**Yes**: Reverses the profit and loss amounts and applies a credit adjustment amount to the deferral schedule. <br />If the reversal occurs halfway through a billing period, the amounts are prorated. <br />**No**: No reversal transaction for the profit and loss is created when a reversal, termination, or refund is applied to a billing schedule or sales order. |
|**Recognition**|
|**Automatically post general journals**|Select whether journal entries that are created by **Revenue and expense deferrals** should be automatically posted.<br /> **Yes**: Automatically posts journal entries created by revenue and expense deferrals. <br />**Tip:** By selecting **Yes**, you can avoid and prevent any accounting inconsistencies caused by manual changes to vouchers.<br />**No**: Journal entries created by revenue and expense deferrals aren't automatically posted. You must manually post any journals.|
|**Summarize recognition journal**|Select whether to consolidate recognition vouchers by default. <br />**Yes**: Creates a single voucher for all recognition lines with the same date. All lines in a voucher with the same account are consolidated into a single line. <br />* **No**: Creates a voucher for each recognition line. <br />You can update this setting on the **Recognition processing** page.|
|**Default journal name**|Select the journal name for journals created from **Revenue and expense deferrals** processes, such as recognition processing. |
|**Recognition journal line description**|Select the description that you want to appear in the journal voucher line description: <br />**Schedule line dates**: Select this option to display the schedule line dates in the journal line description. <br />**Originating transaction details**: Select this option to display the originating transaction information in the journal line description.  <br /> For example: USMF-0001, CIV-00839, Software Revenue. |
|**Number sequences**|Use this tab to set the default values for lease number sequences. Number sequences are automatically generated and assigned using the number sequence generation wizard. You don't need to change the number sequence unless you want to make manual changes on top of the generated number sequences.|
|**Schedule number**|Displays the number sequence used for deferral schedules. |

  ## Deferral templates
  
Use the **Deferral templates** page to define straight-line templates that are used for deferral schedules. 

Advantages of using a template include: 
* Automatically calculate the length of the deferral 
* Allow deferral schedules that have periods where the recognition is skipped
* Automate deferrals by assigning the template to product, product group, product category, customers, or customer group.   
The template assignment is done from the **Deferral defaults** page. 

A template can have a period frequency of daily, monthly, or fiscal periods. 

The template lines consist of the type **Recognized** or **Skipped**, and the period length. Skipped lines have an amount of zero (0) on the deferral schedule lines. This can be used if you don't want to recognize revenue in all periods.

### Create a deferral template

To create a deferral template, follow these steps: 
1. On the **Deferral templates** page, select **New**. 
2. In the **Template** field, enter a name. 
3. In the **Description** field, enter a description. 
4. Select the **Period frequency**. 
5. Select **Add** to add a line to the top of the lines, or select **Append** to add a line to the bottom of the lines. For each line, select the period **Type** and specify the **Period length**. 
6. Select **Save**.


## Deferral defaults

Use the **Deferral defaults** page to set up default deferral accounts for items and assign default templates to deferrable items. You can also set up deferral accounts for charges and assign templates to the deferrable charges.

**Defer by item**

For transactions with an item (for example, sales orders), you can assign accounts and templates to specific items and customers. These settings will be the default values used when a transaction is deferred. To make the transaction deferrable by default, the items must be set up on the **Deferrable items** page.

**Defer by account**

For transactions without items (for example, general journals), you can specify the deferral accounts. When these accounts are used in a transaction line, the transaction is automatically marked as deferred. The corresponding template and recognition account will be assigned to the transaction line.
  
**All transaction types** (Sales Order, Purchasing, General Journal, etc. tabs)

The accounts on this page are the main accounts without financial dimensions. The financial dimensions of the recognition account are from the customer or item based on your organization.

Each template line must have either a straight line template or an event based template, but not both.

### For sales orders

To specify the deferral default values for sales orders, follow these steps: 
1. Select the **Sales order** tab. 
2. Select the deferral type, and add a line: 
   a. Select **Add**. 
   b. Select the **Item code**, which determines how the deferral default values are applied. 
      * If the **Item code** is **Table** or **Group**, select the **Item relation**. 
      * If the **Item code** is **Category**, select the **Category relation**. 
      * If the **Item code** is **All**, the default value applies to all applicable records. 
   c. Select how the **Account code** is applied. 
      * If the **Account code** is **Table** or **Group**, select **Account relation**. 
      * If the **Item code** is **All**, the account will apply to all records. 
   d. Select the **Main account** for the deferral. 
   e. If the **Deferral posting method** is **Profit and loss**, select the **Initial revenue account** and **Revenue offset account**. 
   f. If the **Short-term deferral method** is **Rolling periods** or **Fixed year**, select the **Short-term deferral account**.
3. For a template, you can add a line: 
   a. Select **Add**. 
   b. Select the **Item code**, which determines how the deferral default values are applied. 
      * If the **Item code** is **Table** or **Group**, select the **Item relation**. 
      * If the **Item code** is **Category**, select the **Category relation**. 
      * If the **Item code** is **All**, the default values applies to all applicable records.
   c. Select how the **Account code** is applied. 
      * If the **Account code** is **Table** or **Group**, select the **Account relation**. 
      * If the **Item code** is **All**, the account applies to all applicable records.
   d. Select the **Straight line template** or the **Event based template**. 
4. Select **Save**. 

### For purchasing

To specify the deferral default values for purchase orders, follow these steps:
1. Select the **Purchasing** tab. 
2. Select the deferral type and add a line: 
   a. Select **Add**. 
   b. Select the **Item code**. 
      * If the **Item code** is **Table** or **Group**, select the **Item relation**. 
      * If the **Item code** is **Category**, select the **Category relation**. 
      * If the **Item code** is **All**, the default values applies to all applicable records. 
   c. Select how the **Account code** is applied. 
      * If the **Account code** is **Table** or **Group**, select the **Account relation**. 
      * If the **Item code** is **All**, the account applies to all applicable records.
   d. Select the **Main account** for the deferral. 
   e. If the **Deferral posting method** is **Profit and loss**, select the **Initial revenue account** and **Revenue offset account**.
   1. If the **Short-term deferral method** is **Rolling periods** or **Fixed year**, select the **Short-term deferral account**.
3. For **Template**, add a line as follows: 
   a. Select **Add**. 
   b. Select the **Item code**. 
      * If the **Item code** is **Table** or **Group**, select the **Item relation**. 
      * If the **Item code** is **Category**, select the **Category relation**. 
      * If the **Item code** is **All**, the default values applies to all applicable records. 
   c. Select how the **Account code** is applied. 
      * If the **Account code** is **Table** or **Group**, select the **Account relation**. 
      * If the **Item code** is **All**, the account applies to all applicable records.
   d. Select the **Straight line template** or **Event based template**. 
4. Select **Save**. 

### For a general journal 

To specify the deferral default values for general journal entries, follow these steps: 
1. Select the **General journal** tab. 
2. For **Deferral**, add a line as follows: 
   a. Select **Add**. 
   b. If the **Short-term deferral method** is **Rolling periods** or **Fixed year**, select the **Short-term deferral account**.
   c. Select the **Deferral account**.
   d. Select the **Recognition account**. 
   e. If the **Deferral posting method** is **Profit and loss**, select the **Initial revenue account** and **Revenue offset account**.
   f. Select the **Straight line template** or **Event based template**. 
3. Select **Save**.

### For a free text invoice

To specify the deferral default values for free text invoices, follow these steps:
1. Select the **Free text invoice** tab. 
2. For **Deferral**, add a line as follows: 
   a. Select **Add**. 
   b. Select how the **Account code** is applied. 
      * If **Account code** is **Table** or **Group**, select the **Account relation**. 
      * If **Item code** is **All**, the account code applies to all applicable records. 
   c. Select the **Deferral account**.
   d. If the **Short-term deferral method** is **Rolling periods** or **Fixed year**, select the **Short-term deferral account**.
   e. Select the **Recognition account**. 
   f. If the **Deferral posting method** is **Profit and loss**, select the **Initial revenue account** and **Revenue offset account**.
   g. Select the **Straight line template** or **Event based template**.
3. Select **Save**.

### For an invoice journal

To specify the deferral default values for invoice journal entries: 
1. Select the **Invoice journal** tab. 
2. For **Deferral**, add a line as follows: 
   a. Select **Add**. 
   b. Select how the **Account code** is applied. 
      * If the **Account code** is **Table** or **Group**, select the **Account relation**. 
      * If the **Item code** is **All**, the account code applies to all applicable records. 
   c. Select the **Deferral account**.
   d. If the **Short-term deferral method** is **Rolling periods** or **Fixed year**, select the **Short-term deferral account**.
   e.  Select the **Recognition account**. 
   f. If the **Deferral posting method** is **Profit and loss**, select the **Initial revenue account** and **Revenue offset account**.
   g. Select the **Straight line template** or **Event based template**.
3. Select **Save**.

### Items deferred by default
  
Use the **Items deferred by default** page to define which items are deferred by default. You can set up which types of transactions that the items will be deferred. You can specify whether a single item or and entire item groups or categories are deferred. 

When setting up items as deferred, select the default accounts and templates on the **Deferral defaults** page. If the accounts and templates aren't selected, any transaction line entered with these items won't be deferred.

For items that are deferred based on the sales or purchasing category that they're associated with, the deferral settings are based on the category. However, if the category isn't selected in the **Category relation**, the deferral settings of the category that is higher in rank is used. For example, you add a sales category for **Home video**, but not for **Television**. When you add a deferral item that is associated with the **Television** category, the deferral settings of the **Home video** are used for the item. 

### Set up deferred items

To set items that are deferred by default, follow these steps: 
1. Select the tab you want: **Sales order** or **Purchasing**. 
2. For each line you add, select **Add**, then select the **Item Code**.
      * If **Item Code** is **Group** or **Table**, select the **Item relation**. 
      * If **Item Code** is **Category**, select the **Category relation**. 
3. Select **Save**. 

## Deferred charges

Use the **Deferral charges** page to define which charges are deferred by default. 

> [!Note]
> Currently, deferrable charges are available for sales orders only. 
* Charges can be deferred at the line level only. To defer a charge at the sales order header level, the charge can be set up as a deferred item as a separate line in the sales order. 
* To defer a charge for a free text invoice, the charge must be entered as a separate deferred invoice line. 
* This functionality isn't available for support charges and revenue split functionality. 


### Set up deferred charges

To set up deferred charges, follow these steps: 
1. For each line you add, select **Add**, then select the **Charge Code**, and the **Charge relation**.  
2. Select **Save**.
  
## Event based deferral templates

Use the **Event based deferral templates** page to define event based deferral templates for use in deferral transactions and to assign in the **Deferral defaults** page.

### Create event based template

Create an event based deferral template:
1. Select **New**. 
2. Enter a unique **Template** name and **Description**. 
3. Select the **Allocation type**: 
   a. **Variable amount** will allocate a specific amount for each line entered.
   b. **Equal amount** will allocate the same amount for each line entered. 
   c. **Percentage allocates** an amount based on the percentage value entered for each line.
   d. **Percentage of completion** allocates a cumulative completion value for each line entered.
   e. **Variable quantity** allocates a specific quantity for each line entered.
4. Select whether to **Create separate events per unit**. Select **Yes** if you want each event line to be split evenly by the number of units on the invoice transaction. Select **No** to not split the event lines.
5. Select the **Expiration account**.
6. Select **Add** to add the line to the top of the lines, or select **Append** to add a line to the bottom of the lines. 
For each line:
   a. Enter a **Description** for the event.
   b. If the **Allocation type** is **Percentage**, specify the **Allocation percentage**. The percentage must be between zero (0) and 100. An empty percentage is considered zero. The sum of all percentages must equal 100 as shown in the **Total percentage** field at the bottom.
   c. Specify the **Months to expiration**. The expiration date on the transaction deferral is automatically entered based on this value.
   d. Select the **Recognize when posted** checkbox to automatically recognize revenue when the transaction is posted. If not checked the revenue must be manually recognized.
   e. Select the **Recognition account** for the event (if the account is different from the entire deferral schedule). This is used with the Recognize when posted above.
   f. Select **Save**.

  

