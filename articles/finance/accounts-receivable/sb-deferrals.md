---
# required metadata

title: Revenue and expense deferrals
description: This topic 
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

This topic describes how to setup and use revenue and expense deferrals. Deferral schedules are always based on and are dependent on an underlying originating document or billing schedule. Deferral schedules are created based on setup defaults and cannot be entered or created separately. On the **Revenue and expense parameters** page define the company preferences. On the **Deferral defaults** page, setup the default accounts and templates to use for the deferral schedules. On the **Event based deferral templates** and **Deferral templates** pages, define the templates used for the deferral schedules. On the **All deferral schedules** page you can view and edit any deferral schedule.

Revenue and expense deferrals can be used as a stand-alone module or it can be used along with Recurring contract billing.

## Revenue and expense deferral parameters

Modules > Subscription billing > Revenue and expense deferrals > Setup > Revenue and expense deferral parameters

|Field| Description|
| :------- |:-------| 
|**Schedule**|
|**Equal per period**|Specify whether the number of days in a period is taken into consideration when calculating the amount in each period for a deferral schedule.<br />* **Yes**: The amount for each period is the same regardless  of the number of days in the period, except for partial periods (such as at the beginning or end of a deferral schedule) which will be prorated. <br />* **No**: The amount is calculated based on the number of days in each period. Default setting. <br />You can override this setting at the transaction level. |
|**Sales discount deferral option**|Select whether separate deferral schedules are created for the discount and the sales order amounts: <br />* **Separate schedule for discount**: Discount amount is kept separate from revenue amount. <br />When a sales order is created and then posted, two deferral schedules are created, and the discount and revenue amounts are posted to different deferral accounts. <br />* **Merge discount with revenue**: Discount amount is combined with revenue amount. One deferral schedule is created and both the discount and revenue amounts are posted to the same deferral account. <br />When a sales order is created and then posted, one deferral schedule is created and both the discount and revenue amounts are posted to the same deferral account. <br />**Note:** To be able to apply discounts to items that use the unbilled revenue feature, select the **Separate schedule for discount** option. By selecting this option, discounts can be applied to all items, regardless if the unbilled revenue feature is used or not. If the **Merge discount with revenue** option is selected, discounts cannot be applied to items that use the unbilled revenue feature. |
|**Purchasing discount deferral option**|Select whether separate deferral schedules are created for the discount and the purchase order amounts:  <br />* **Separate schedule for discount**: Discount amount is kept separate from the expense amount.  <br />When a purchase order is created and then posted, two deferral schedules are created, and the discount and expense amounts are posted to different deferral accounts.  <br />* **Merge discount with revenue**: Discount amount is combined with expense amount. One deferral schedule is created and both the discount and expense amounts are posted to the same deferral account.  <br />When a purchase order is created and then posted, one deferral schedule is created and both the discount and expense amounts are posted to the same deferral account. |
|**Consolidate prior periods**|Select whether to consolidate deferral schedule lines for prior periods.  <br />* **Yes**: If the  deferral start date is in a period before the transaction date, all amounts up to and including the period of the transaction date are combined into a single deferral schedule line. Default setting.  <br />* **No**: The amounts from all periods are in separate deferral schedule lines regardless of the date.  <br />If the deferral start date is in the same or a later period as the transaction date, this option has no effect.  <br />You can override this setting at the transaction level. |
|**Default deferral start date**|Select the rule to apply to the transaction date to get the start date for the deferral schedule:  <br />* **Transaction date**: Uses the transaction date as the start date. Default.<br />* **Beginning of current month**:  Uses the  1<sup>st</sup> of the current month as the start date. If the transaction  date is the  1<sup>st</sup> of any month, then the  1<sup>st</sup> of the current month is the start date. <br />* **Beginning of next month**: Uses the  1<sup>st</sup> of the next month as the start date. If the transaction date is on the  1<sup>st</sup>, the transaction date is used, otherwise the  1<sup>st</sup> of the following month is used. <br />* **Rule of 15**: If the transaction date is between the 1<sup>st</sup>and the 15<sup>th</sup>, uses the  1<sup>st</sup> of the current month as the start date. If the transaction date is the  16<sup>th</sup>or later, uses the 1<sup>st</sup> of the next month as the start date. <br />You can override this setting at the transaction level. |
|**Short-term deferral method**|Select the short-term deferral method: **None** (default), **Rolling periods**, or **Fixed year**. <br />For information on how these settings work, see **Short-Term deferral calculation** |
|**Deferral posting method**|Select the method used to create deferral transactions: <br />* **Balance ****sheet**: Uses the balance sheet posting method to create deferral transactions. Default option. <br />* **Profit and loss**: Uses the profit and loss posting method to create deferral transactions. When transactions are posted, you can review the invoice voucher to see the extra entries for balancing the initial recognition and recognition offset amounts. |
|**Reverse profit and loss on credit**|Available when **Deferral posting method** is **Profit and Loss**. <br />Select whether the profit and loss amounts are reversed when a reversal, termination, or refund is applied to a billing schedule or sales order. <br />* **Yes**: Reverses the profit and loss amounts and applies a credit adjustment amount to the deferral schedule. Default. <br />If the reversal occurs halfway through a billing period, the amounts are prorated. <br />* **No**: No reversal transaction for the profit and loss is created when a reversal, termination, or refund is applied to a billing schedule or sales order. |
|**Recognition**|
|**Automatically post general journals**|Select whether any journal entries created by **Revenue and expense deferrals**, such as those from recognition processing, should be automatically posted.<br />* **Yes**: Automatically posts journal entries created by revenue and expense deferrals. Default setting. <br />**Tip:** By selecting **Yes**, you can avoid and prevent any accounting inconsistencies caused by manual changes to vouchers.<br />* **No**: Does not automatically post journal entries created by revenue and expense deferrals. You must manually post any journals. |
|**Summarize recognition journal**|Select whether to consolidate recognition vouchers by default. <br />* **Yes**: Creates a single voucher for all recognition lines with the same date. All lines in a voucher with the same account are consolidated into a single line. <br />* **No**: Creates a voucher for each recognition line. Default setting. <br />You can override this setting on the **Recognition processing** page.|
|**Default journal name**|SElect the journal name for any journal created from **Revenue and expense deferrals** processes, such as recognition processing. You can override this setting at the transaction level. |
|**Recognition journal line description**|Select the description that you want to appear in the journal voucher line description: <br />* **Schedule line dates**: Displays the schedule line dates in the journal line description. Default. <br />The format of the description is: <span class="reference">ScheduleNumber: LineStartDate - Line EndDate** (for example, USMF-0001 : 1/1/2018 - 1/31/2018). <br />* **Originating transaction details**: Displays the originating transaction information in the journal line description.  <br />The format of the description is as follows: **ScheduleNumber, InvoiceOrVoucherNumber, LineOrVoucherDescription** (for example, USMF-0001, CIV-00839, Software Revenue). |
|**Number sequences**|Use this tab to set the default values for lease number sequences. Number sequences are automatically generated and assigned using the number sequence generation wizard. You do not need to change the number sequence unless you want to make manual changes on top of the generated number sequences.|
|**Schedule number**|Displays the number sequence used for deferral schedules. |

  ## Deferral templates

  ## Deferral defaults

Modules > Subscription billing > Revenue and expense deferrals > Setup > Deferral defaults

Use this page to set up default deferral accounts for items and assign default templates to deferrable items. You can also set up deferral accounts for charges and assign templates to the deferrable charges.

**Defer by Item**

For transactions with an item (for example, sales orders), you can assign accounts and templates to specific items and customers. These settings become the default values used when a transaction is deferred. To make the transaction deferrable by default, the items must also be set in the **Deferrable Items** page.

**Defer by Account**

For transactions without items (for example, general journals), you can specify the deferral accounts. When these accounts are used in a transaction line, the transaction is automatically marked as deferred, and the corresponding template and recognition account is assigned to the transaction line.
  
**All transaction types (Sales Order, Purchasing, General Journal, etc. tabs)**

The accounts on this page are the main accounts without financial dimensions. The financial dimensions of the recognition account are from the customer or item based on standard functionality.

Each template line must have either a straight line template or an event based template, but not both.


### For Sales Orders

To specify the deferral default values for sales orders, follow these steps: 
1. Select the **Sales order** tab. 
2. Select the deferral type (e.g., revenue, discount),  and add a line as follows: 
   a. Select **Add**. 
   b. Select the **Item code**, which determines how the deferral default values are applied. 
      * If **Item code** is **Table** or **Group**, select the **Item relation**. 
      * If **Item code** is **Category**, select the **Category relation**. 
      * If **Item code** is **All**, you do not need to select the additional relation because the default value applies to all applicable records. 
   c. Select how the **Account code** is applied. 
      * If **Account code** is **Table** or **Group**, select the **Account relation**. 
      * If **Item code** is **All**, you do not need to select the additional relation because the account applies to all applicable records. 
   d. Select the **Main account** for the deferral. 
   e. If on the **Revenue and expense deferrals parameters** page **Deferral posting method** is **Profit and loss**, select the **Initial revenue account** and **Revenue offset account**. 
   f. If on the **Revenue and expense deferrals parameters** page **Short-term deferral method** is **Rolling periods** or **Fixed year**, select the **Short-term deferral account**.
3. For a template, add a line as follows: 
   a. Select **Add**. 
   b. Select the **Item code**, which determines how the deferral default values are applied. 
      * If **Item code** is **Table** or **Group**, select the **Item relation**. 
      * If **Item code** is **Category**, select the **Category relation**. 
      * If **Item code** is **All**, you do not need to select the additional relation because the default values applies to all applicable records.
   c. Select how the **Account code** is applied. 
      * If **Account code** is **Table** or **Group**, select the **Account relation**. 
      * If **Item code** is **All**,  you do not need to select the additional relation because the account applies to all applicable records.
   d. Select the **Straight line template** or the **Event based template**. 
4. Select **Save**. 

### For Purchasing

To specify the deferral default values for purchase orders, follow these steps:
1. Select the **Purchasing** tab. 
2. Select the deferral type (e.g., expense, discount), add a line as follows: 
   a. Select **Add**. 
   b. Select the **Item code**. 
      * If **Item code** is **Table** or **Group**, select the **Item relation**. 
      * If **Item code** is **Category**, select the **Category relation**. 
      * If **Item code** is **All**, you do not need to select the additional relation because the default values applies to all applicable records. 
   c. Select how the **Account code** is applied. 
      * If **Account code** is **Table** or **Group**, select the **Account relation**. 
      * If **Item code** is **All**, you do not need to select the additional relation because the account applies to all applicable records.
   d. Select the **Main account** for the deferral. 
   e. If on the **Revenue and expense deferrals parameters** page **Deferral posting method** is **Profit and loss**, select the **Initial revenue account** and **Revenue offset account**.
   1. If on the **Revenue and expense deferrals parameters** page **Short-term deferral method** is **Rolling periods** or **Fixed year**, select the **Short-term deferral account**.
3. For **Template**, add a line as follows: 
   a. Select **Add**. 
   b. Select the **Item code**. 
      * If **Item code** is **Table** or **Group**, select the **Item relation**. 
      * If **Item code** is **Category**, select the **Category relation**. 
      * If **Item code** is **All**, you do not need to select the additional relation because the default values applies to all applicable records. 
   c. Select how the **Account code** is applied. 
      * If **Account code** is **Table** or **Group**, select the **Account relation**. 
      * If **Item code** is **All**, you do not need to select the additional relation because the account applies to all applicable records.
   d. Select the **Straight line template** or **Event based template**. 
4. Select **Save**. 

## For General Journal 

To specify the deferral default values for general journal entries, follow these steps: 
1. Select the **General journal** tab. 
2. For **Deferral**, add a line as follows: 
   1. Select **Add**. 
   1. If on the **Revenue and expense deferrals parameters** page **Short-term deferral method** is **Rolling periods** or **Fixed year**, select the **Short-term deferral account**.
   1. Select the **Deferral account**.
   1. Select the **Recognition account**. 
   1. If on the **Revenue and expense deferrals parameters** page **Deferral posting method** is **Profit and loss**, select the **Initial revenue account** and **Revenue offset account**.
   1. Select the **Straight line template** or **Event based template**. 
3. Select **Save**.

## For Free Text Invoice

To specify the deferral default values for free text invoices, follow these steps:
1. Select the **Free text invoice** tab. 
2. For **Deferral**, add a line as follows: 
   a. Select **Add**. 
   b. Select how the **Account code** is applied. 
      * If **Account code** is **Table** or **Group**, select the **Account relation**. 
      * If **Item code** is **All**, you do not need to select the additional relation because the account code applies to all applicable records. 
   c. Select the **Deferral account**.
   d. If on the **Revenue and expense deferrals parameters** page **Short-term deferral method** is **Rolling periods** or **Fixed year**, select the **Short-term deferral account**.
   e.  Select the **Recognition account**. 
   f. If on the **Revenue and expense deferrals parameters** page **Deferral posting method** is **Profit and loss**, select the **Initial revenue account** and **Revenue offset account**.
   g. Select the **Straight line template** or **Event based template**.
3. Select **Save**.

## For Invoice Journals

To specify the deferral default values for invoice journal entries, follow these: 
1. Select the **Invoice journal** tab. 
2. For **Deferral**, add a line as follows: 
   a. Select **Add**. 
   b. Select how the **Account code** is applied. 
      * If **Account code** is **Table** or **Group**, select the **Account relation**. 
      * If **Item code** is **All**, you do not need to select the additional relation because the account code applies to all applicable records. 
   c. Select the **Deferral account**.
   d. If on the **Revenue and expense deferrals parameters** page **Short-term deferral method** is **Rolling periods** or **Fixed year**, select the **Short-term deferral account**.
   e.  Select the **Recognition account**. 
   f. If on the **Revenue and expense deferrals parameters** page **Deferral posting method** is **Profit and loss**, select the **Initial revenue account** and **Revenue offset account**.
   g. Select the **Straight line template** or **Event based template**.
3. Select **Save**.

  
