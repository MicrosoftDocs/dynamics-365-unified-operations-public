---
# required metadata

title: Unbilled revenue setup
description: This topic explains how to set up items that use the unbilled revenue feature in Subscription billing by default, and how to set up the unbilled revenue accounts for the items you select.
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
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 539093
ms.search.region: Global
# ms.search.industry: 
ms.author: jchrist
ms.search.validFrom: 2021-11-05
ms.dyn365.ops.version: 10.0.24

---

# Unbilled revenue setup

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

Modules > Advanced recurring contract billing > Setup > Unbilled revenue setup

This topic explains how to set up items that use the unbilled revenue feature by default, and how to set up the unbilled revenue accounts for the items you select.

## Set Up Unbilled Revenue Items {#UnbilledItems}

To set up items to use the unbilled revenue feature by default, follow these steps: 
1. Select the **Items** tab. 
2. Select **Add**.
3. For the line, select the **Item code** and the **Item relation**. 
4. Repeat these steps to add more  lines. 
5. Select **Save**.

## Set Up Unbilled Revenue Accounts {#UnbilledAcct}

To set up items and the default unbilled revenue accounts, follow these steps: 
1. Select the **Accounts** tab. 
2. Select **Add**.
3. For the line, select the **Item code** and the **Item relation**. 
4. Select the accounts for the unbilled revenue and the unbilled discount. 
5. Repeat these steps to add more  lines. 
6. Select **Save**.

## Fields

This page contains the following fields: 

| Field| Description|
| :------------- |:-------------| 
| **Items tab**| Use this tab to set up items to use the unbilled revenue feature by default.| 
| **Item code**| Select how the item code is applied: <br />- **Table**: Applies to a single item, specified in  the **Item relation** field.<br />- **Group**: Applies  to an item group, specified in the **Item relation** field.|  
| **Item relation<**| Select the item code or item group. |  
| **Accounts tab**| Use this tab to setup the default accounts for either individual items , groups or “all”.| 
| **Item code**| Select how the item code is applied: <br />- **Table**: Applies to a single item, specified in  the **Item relation** field.<br />- **Group**: Applies  to an item group, specified in the **Item relation** field.<br />- **All**: Applies to both single items and item groups. |  
| **Item relation**| Select the item code or item group. |  
| **Unbilled revenue account**| Select the account for the unbilled revenue journal entry. | 
| **Short-term unbilled revenue account**| Select the account for the short-term unbilled revenue journal entry. <br />To set this account, on the **[Advanced Recurring Contract Billing Parameters](Parameters.md)** page, set **Short-term unbilled method** to **Rolling periods** or **Fixed year**. |  
| **Unbilled discount account**| Select the account for the unbilled discount journal entry. | 
| **Short-term Unbilled discount account**| Select the account for the short-term unbilled discount journal entry. >br />To set this account, on the **[Advanced Recurring Contract Billing Parameters](Parameters.md)** page, set **Short-term unbilled method** to **Rolling periods** or **Fixed year**. |  
| ****| content|  


This topic describes the unbilled revenue feature that lets you include the amounts for whole billing schedules on the balance sheet. These amounts are included in an unbilled revenue account and the contract are billed through installments. 

For example, a billing schedule is for 3 years with the invoices billed annually over a 3-year period. The whole contract amount is recorded in the unbilled revenue account from which annual invoices are created. The offset account is the revenue or the deferred revenue account. 

> [!NOTE]
> The top billing and the unbilled revenue features do not and cannot work together because reconciliation issues in the General Ledger can occur. 

### View example

For example, on the [Item Group Setup](../setup/TopBill.md) page, ItemGroupA is set up with the **Number of top lines** set to 2. On the [Billing Schedules](../enduser/BillSched.md) page, three items are added. All three items belong to ItemGroupA. When the initial journal entry is created for the unbilled revenue feature, the amount for all three items are processed to the unbilled account. However, when the invoice for the billing schedule is created, only the amounts for the top two items are included. As a result, the invoice amount does not match the amount processed to the unbilled revenue account, and reconciliation issues in the General Ledger occur. 
</details>

- If you want to use the unbilled revenue feature, do not set up the [Item Group Setup](../setup/TopBill.md) page with any item groups, or ensure that all item groups have the **Number of top lines** set to zero (0). 
- If you want to use the top billing feature, keep in mind that all **Unbilled revenue** actions are not available. 

## Set up workflow for unbilled revenue

Ensure a system administrator completes the following setup tasks:
1. On the [Advanced Recurring Contract Billing Parameters](../setup/Parameters.md) page, set up the **Unbilled Revenue** section. 
2. On the [Unbilled Revenue Setup](../setup/Unbilled.md) page, set up the item and accounts to use for the unbilled revenue feature. <br />The unbilled revenue feature can be used for items where **Item Type** is **Standard**. This feature can also be used for deferral items. <br />To use the unbilled revenue feature with the short-term functionality, ensure to set up the short-term options on the [Advanced Recurring Contract Billing Parameters](../setup/Parameters.md) and the [Unbilled Revenue Setup](../setup/Unbilled.md). 

## Basic Workflow

To use the unbilled revenue feature, follow this general workflow: 
1. On the [Billing Schedules](../enduser/BillSched.md) page, create a billing schedule as usual. <br />If the item is not already set up to use the unbilled revenue feature, select the **Unbilled revenue** action for the line. Set the **Unbilled revenue** option to **Yes**, and review and edit the unbilled revenue and discount accounts as needed. 
2. For the billing schedule, select **Unbilled Revenue Processing &amp;amp;gt; Create unbilled revenue initial  journal entry**. 
3. On the [Unbilled Revenue Mass Processing](../enduser/MassUnbilledRevJE.md) page, create the journal entry. <br />![Tip icon](../../../Resources/images/icons/iAXtip.png)**Tip:** This window can also be used for creating journal entries for several billing schedules. 
4. To create sales orders and post the invoices for the billing schedules, use the [Invoice Creator](../enduser/InvCreator.md) page. 
5. After the invoices are posted, you can review the audit information on the **Renewal** tab of the [Billing Schedules](../enduser/BillSched.md) page. 

**Milestone billing**: The milestone billing functionality can work with the unbilled revenue feature with the following conditions satisfied: 
- When the milestone parent item is unbilled (the **Unbilled revenue** check box is selected) and the milestone child items are not unbilled (the **Unbilled revenue** check box are cleared) , the start and end dates for the parent item must be specified. These dates are used for creating the initial journal entry. 
- When the milestone parent item is unbilled (the **Unbilled revenue** check box is cleared) and the milestone child items are not unbilled (the **Unbilled revenue** check box are selected), the end date for only the child items for which you want to create the initial journal entry must be specified.   
Each milestone child item can be processed separately and the end dates can be specified when you are ready to create the initial journal entry. 

> [!NOTE]
> If the initial journal entry for the milestone parent or child items has already been created or an invoice has been created, the start and end dates cannot be edited. 

## Unbilled Revenue with Straight Line Deferrals

To use the unbilled revenue feature with straight line deferral schedules, follow this general workflow:
1. On the [Billing Schedules](../enduser/BillSched.md) page, create a billing schedule as usual.
2. Add an item to the **Billing schedule lines**.  
3. If the item is not already a deferral item or you want to change the default values, select **Advanced Deferrals** action for the line. On the [Transaction Deferral](../enduser/TransDef.md) page, do the following: 
   - Set **Deferred** to **Yes**. 
   - Change the **Accounts** as needed. 
   - In the **Schedule** section, select **Straight line**, and edit other values as needed. 
   - Select **OK**.
4. If the item is not already set up to use the unbilled revenue feature, or if you want to change the default settings, select the **Unbilled revenue** action for the line. 
   - Set **Unbilled revenue** to **Yes**. 
   - Select the accounts to use for the revenue and discount. 
5. For the billing schedule, select **Unbilled Revenue Processing > Create unbilled revenue initial journal entry**. 
6. On the [Unbilled Revenue Mass Processing](../enduser/MassUnbilledRevJE.md) page, create the journal entry. 

The deferral schedule is created. You can review the details on the [Schedules](../../AX_ARED/endUser/ComSched.md) page. 

After the deferral schedule is created, you can edit various values for the billing schedule line item, for example, unit price, quantity, dates, etc. The deferral schedule is updated with the new values. 

## Unbilled Revenue with Event Based Deferrals

To use the unbilled revenue feature with event based deferral schedules, follow this general workflow:
1. On the [Billing Schedules](../enduser/BillSched.md) page, create a billing schedule as usual.
2. Add an item to the **Billing schedule lines**.  
3. If the item is not already a deferral item or you want to change the default values, select **Advanced Deferrals** action for the line. On the [Transaction Deferral](../enduser/TransDef.md) page, do the following: 
   - Set **Deferred** to **Yes**. 
   - Change the **Accounts** as needed. 
   - In the **Schedule** section, select **Event based**, **Template**, **Allocation type**, and **Expiration account**. 
   - Select **OK**.
4. If the item is not already set up to use the unbilled revenue feature, or if you want to change the default settings, select the **Unbilled revenue** action for the line. 
   - Set **Unbilled revenue** to **Yes**. 
   - Select the accounts to use for the revenue and discount. 
5. For the billing schedule, select **Unbilled Revenue Processing > Create unbilled revenue initial journal entry**. 
6. On the [Unbilled Revenue Mass Processing](../enduser/MassUnbilledRevJE.md) page, create the journal entry. 

The deferral schedule is created. You can review the details on the deferral [Schedules](../../AX_ARED/endUser/ComSched.md) page. 

After the deferral schedule is created, you can edit various values for the billing schedule line item, for example, unit price, quantity, dates, etc. The deferral schedule is recalculated based on the new values. 

The distributions are recalculated based on the allocation type selected (Percentage , Percentage Completion, Equal Amounts). For the Variable amounts allocation type, the distribution is recalculated based on the percent equivalent of the initial value for the event. For example, the original unit price is 100.00, the percent of the initial value is 55.00, which is 55%. When the unit price is changed to 200.00, the variable amount of the event becomes 110.00, which is 55%. 

> [!NOTE]
> If deferral schedule lines have been recognized, the billing schedule line item cannot be edited. If needed, the recognized lines must be reversed first, and then the billing schedule line can be updated. 

## Event-based termination or hold with adjustment

After a event line has been recognized, the billing schedule line can be terminated or put on hold with an adjustment. Review the following scenarios for terminating a billing schedule line before the invoice is created. 
- One event line is recognized <br />When the billing schedule line is terminated, an adjustment line is created in the deferral schedule. The deferral end date for the adjustment line will be the termination date.
- The unrecognized event line  does not have a deferral end date <br />When the billing schedule line is terminated, the termination date becomes the deferral end date for that event line.
- The unrecognized event line has only the expiration date <br />When the billing schedule line is terminated, the termination date becomes deferral end date of the event line.

When putting a hold on a billing schedule line with **Adjust schedule** set to **Yes**, the deferral schedule lines are affected the same as described for terminating a billing schedule line. 

---

# Unbilled Revenue examples

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic describes how to use the unbilled revenue feature to recognize the entire amount of a contract on the balance sheet as unbilled revenue. The other side of the entry is charged to either a revenue or deferred revenue account, depending on the accounting requirements for the transaction. When you recognized unbilled revenue in this way, the customer invoices draw down the unbilled amount and update accounts receivable. No revenue recognition happens at the time of invoicing as the revenue was either recognized when the unbilled amount was posted or will be recognized based deferral recognition schedule that was set up.

## Processing unbilled revenue

Review the following example to better understand the unbilled revenue functionality.

Assume a customer signs a 3-year $390 contract on January 1 of the current year. The contract includes two parts, licenses and a maintenance agreement.
- Assume the sales price of the license portion is $300, and that the customer will be invoiced $100 on January 1 of each contract year. The $300 license fee will be taken as revenue when the contract is signed.
- The sales price of the maintenance fee is $90, and the customer will be invoiced $30 on January 1, for each of the upcoming years. The $90 maintenance fee will be deferred with $2.50 being recognized each month over the life of the contract.

The customer will be invoiced $130 at the beginning (January 1st) of each of the 3 years of the contract.

1. Assuming the two items already exist as released products, your first step is to ensure the two items are set up as unbilled items. Use the **[Unbilled revenue setup](../../AX_ARCB/setup/Unbilled.md)** to set up the items that use the unbilled revenue feature by default and the accounts  that are used when the items are added to the billing schedule.  
2. In the example, the maintenance fee is deferred. The item requires a deferral template, which is set up on the **[Deferral templates](../setup/DefTemplate.md)**. The template needs a Monthly period frequency and a recognition period length of 36 months. As a result, the revenue per month will be 2.50. 
3. Set the Maintenance Fee as a Deferrable item (see **[Deferrable items](../setup/DefItems.md)**). This step and the next step for Deferral defaults will cause the Maintenance Fee item to be deferred by default when it is sold or included on a billing schedule.
4. Set the **[Deferral defaults](../setup/DefDefault.md)** for the maintenance fee. The  maintenance fee item will be linked to a 36-month deferral schedule.
5. Next [create a billing schedule](../../AX_ARCB/enduser/BillSched.htm#CreateBillSched) with the two unbilled items on it. The billing schedule for the contract is set up with the following items:

|Item|Start Date|End Date|Amount|Billing Frequency|Deferral Item|Unbilled Revenue|Description|
|:-----|:-----|:-----|-----:|:-----|:-----|:-----|:-----|
|License|January 01, CY|December 31 CY+2|100.00|Annually|No|Yes|The customer will be invoiced 100.00 each year. The 300.00 total will be recorded upfront as unbilled revenue on the balance sheet and as revenue on the profit and loss. Each invoice will reduce the unbilled amount.|
|Maintenance|January 01, CY|December 31 CY+2|30.00|Annually|Yes|Yes|The customer will be invoiced 30.00 each year. The 90.00 total will be recorded upfront as unbilled revenue and deferred revenue on the balance sheet. Each invoice will reduce the unbilled amount. The deferred revenue will be recognized monthly over 36 months.|

1. On the **[Billing schedules](../../AX_ARCB/enduser/BillSched.md)** page, use the **Create unbilled revenue initial journal entry** action to post the  contract value to the balance sheet as unbilled revenue. It will create two journal entries, one for each line on the billing schedule:

| Unbilled revenue account| Revenue account | Debit amount | Credit amount |
|:-----|:-----|-----:|-----:|
|Unbilled Revenue account| |300.00| &nbsp; |
| &nbsp; |License Revenue account| |300.00|

| Unbilled revenue account| Deferred revenue account | Debit amount | Credit amount |
|:-----|:-----|-----:|-----:|
|Unbilled Revenue account| &nbsp; |90.00| &nbsp; |
| &nbsp; |Deferred Maintenance Revenue| &nbsp; |90.00|

Notice that the first journal entry is posted to a revenue account and the second is posted to a deferred revenue account.
1. The contract requires that the invoice for the customer to be created at the beginning of each year. Use the [Invoice creator](../../AX_ARCB/enduser/InvCreator.md) to create the invoice. When the invoice is created, the journal entry is as follows: 

| Main account| Unbilled revenue account | Debit amount | Credit amount |
|:-----|:-----|-----:|-----:|
|AR| &nbsp; |130.00| &nbsp; |
| |Unbilled Revenue account| |130.00|

This same journal entry will be created by invoices posted at the beginning of the next two years.
1. In the last step, the recognition journal entry is created each month to recognize the deferred maintenance fee revenue. The journal entry can be created using the **[Recognition processing](../endUser/RecogProc.md)** page or the **Recognize** action for the lines on the **[Schedules](../endUser/ComSched.md)** pages.

| Deferred revenue account| Revenue account | Debit amount | Credit amount |
|:-----|:-----|-----:|-----:|
|Deferred Maintenance Revenue| &nbsp; |2.50||
| &nbsp; |Maintenance Revenue| &nbsp; |2.50|

This journal entry will be created each time the recognition process is run for this deferred item (a total of 36 times).

## Short-term: Fixed year

The unbilled revenue feature can be used with the short-term functionality. Review the following example to better understand the calculations that occur when the unbilled revenue feature is used with the fixed year short-term calculation method. 

A billing schedule with the following criteria is created: 
- Start Date: June 01, 2020 
- End Date: December 31, 2021
- Unit Price: 100.00
- Frequency: Monthly

On the **[Billing schedules](../../AX_ARCB/enduser/BillSched.md)** page, the initial journal entry is created from the header action (**Unbilled revenue processing &amp;amp;amp;gt; Create unbilled revenue journal entry**). The current short-term and long-term amounts are calculated as followings: 
- Current short-term unbilled revenue amount: $700
- Current long-term unbilled revenue amount: $1200

The invoice for the billing period June 01, 2020, to November 30, 2020, is created. The current short-term and long-term amounts are calculated as followings: 
- Current short-term unbilled revenue amount: $100
- Current long-term unbilled revenue amount: $1200

The invoice for the billing period December 01, 2020, to December 31, 2020, is created. The current short-term and long-term amounts are calculated as followings: 
- Current short-term unbilled revenue amount: $1200
- Current long-term unbilled revenue amount: $0

## Short-term: Rolling periods

The unbilled revenue feature can be used with the short-term functionality. Review the following example to better understand the calculations that occur when the unbilled revenue feature is used with the rolling periods short-term calculation method. 

A billing schedule with the following criteria is created: 
- Start Date: June 01, 2020
- End Date: December 31, 2021
- Unit Price: 100.00
- Frequency: Monthly

On the **[Billing schedules](../../AX_ARCB/enduser/BillSched.md)** page, the initial journal entry is created from the header action (**Unbilled revenue processing ? Create unbilled revenue journal entry**). The current short-term and long-term amounts are calculated as followings: 
- Current short-term unbilled revenue amount: $1200
- Current long-term unbilled revenue amount: $700

The invoice for the billing period June 01, 2020, to November 30, 2020, is created. The current short-term and long-term amounts are calculated as followings: 
- Current short-term unbilled revenue amount: $1200
- Current long-term unbilled revenue amount: $100

The invoice for the billing period December 01, 2020, to December 31, 2020, is created. The current short-term and long-term amounts are calculated as followings: 
* Current short-term unbilled revenue amount: $1200
* Current long-term unbilled revenue amount: $0

## Items with revenue allocation

Two items with different billing frequencies are added to a billing schedule. Both use the unbilled revenue feature and are deferrable items. 

Surface Pro 128GB (Item number 1000): 
- Billing frequency: One-time 
- Unit price: 1,500
- Standalone selling price: 1,600
- Contract revenue: 1,465.26

Item 1000 is sold in a bundle with Insurance (Item number S0021):
- Billing frequency: Monthly for 12 months 
- Unit price: 20.00 per month
- Standalone selling price: 25.00
- Contract revenue: 264.74

![UnbilledMERA01](../../AX_ARCB/_images/UnbilledMERA01.png)

![UnbilledMERA02](../../AX_ARCB/_images/UnbilledMERA02.png)

Since both items use the unbilled revenue feature and revenue allocation, the total contract amount on the renewal line is zero (0). Instead, a column called **Contract revenue** appears and shows the contract revenue amount. 

![UnbilledMERA03](../../AX_ARCB/_images/UnbilledMERA03.png)

The initial journal entry for the items and the invoice are as follows: 

|Unbilled revenue account| Deferred revenue account | Debit amount | Credit amount |
|:-----|:-----|-----:|-----:|
|**Item 1000 Journal entry**| &nbsp; | &nbsp; | &nbsp; |
|Debit unbilled revenue account (401250)| |1,465.26|
||Credit deferred revenue account (250600)| &nbsp; |1,465.26|
|**Item 0021 Journal entry**| &nbsp; | &nbsp; | &nbsp; |
 |Debit unbilled revenue account (401250)| &nbsp; |274.74|
 | &nbsp; |Credit deferred revenue account (250600)| &nbsp; |274.74|
|**Invoice**| &nbsp; | &nbsp; | &nbsp; |
| &nbsp; |Credit deferred revenue account| &nbsp; |1,465.26|
 | &nbsp; |Credit deferred revenue account| &nbsp; |274.74|
 |Debit AR account (130100)| &nbsp; |1,488.16| &nbsp; |

**Changes to the billing schedule line, billing detail line, or revenue allocation**

When the unit price or quantity is changed, the contract revenue amount for each item that is part of the revenue allocation must be updated. As a result, the journal entry is recalculated. 

The unit price for Item 1000 is changed from 1,500 to 1,600. The contract revenue amount is automatically recalculated and become 1,549.47. At the same time, the contract revenue for Item S0021 is recalculated and becomes 290.53. 

When the changed is confirmed and committed, the initial journal entries for both items are reversed and new journal entries are created: 
- Item 1000: Original initial journal entry of 1,465.26 is reversed. New journal entry for 1,549.47 is created. 
- Item S0021: Original initial journal entry of 274.74 is reversed. New journal entry for 290.53 is created. 

**Termination**

Item S0021 that has a start date of January 2020 and end date on December 2020 is terminated on June 2020. The contract revenue amount for both items must be recalculated: 
- Contract revenue for Item 1000 becomes 1,567.67. 
- Contract revenue for Item S0021 becomes 124.00. 

An adjustment journal entry is created for the line that is terminated. The journal entry for the line that belongs to the same MEA number is reversed and a new journal entry is created: 
- Item 1000: Original initial journal entry of 1,465.26. An adjustment journal entry for 1,549.47 is created. 
- Item S0021: Original initial journal entry of 274.74 is reversed. New journal entry for 124.00 is created. 

## Revenue allocation and renewals 

Items that use both the revenue allocation and renewal features must satisfy the following conditions: 
- Billing frequency must be a recurring frequency (e.g., Daily, Weekly, Monthly, etc.)  
- Items that have a billing frequency of **One time** cannot be renewed. 
- Billing start and end dates and MEA number must be the same.   
- These items are renewed together. 

**Adding a renewal term**

A renewal term can be added at any time during for an active billing schedule. When a renewal term is added, note the following: 
- The allocation or renewal total extended amount is zero (no initial allocation). The amount is updated after the invoice for all lines has been created, and the allocation for the renewal term is calculated. 
-  After the invoice for a line has been created, the new allocation is created based on the lines that have renewal terms. 
- If the item does not have a standalone selling price amount, the standalone selling price amount from the previous term is used. 

To better understand how the unbilled revenue feature works with items that use both revenue allocation and renewal features, review the following example. 

A billing schedule with the following items is created: 

|Line|Item|Product name|Billing frequency|Start date|End date|Unit price|Total extended amount|Contract revenue amount|
|:----|:----|:----|:----|:----|:----|----:|----:|----:|
|1|1000|Desktop computer|One time|January-01-2020|December-31-2020|  2,000.00 | &nbsp; |1,846.81|
|2|S0001|Insurance|Monthly|January-01-2020|December-31-2020| 20.00 |240.00|316.56|
|3|S0002|Software|Monthly|January-01-2020|December-31-2020| 20.00 |240.00|316.56|

The revenue allocation is as follows: 
- MEA type: Single
- MEA number: 12345
- Deferred contract revenue account: 110110

|Item number|Billing frequency|Contract value|MEA number|SSP origin|Standalone selling price|Contract SSP|Total contract revenue|Deferred contract revenue account|
|:----|:----|:----|:----|:----|----:|----:|----:|----:|
|1000|One time|2,000.00|12345|Amount|  2,100.00 |  2,100.00 |1,846.81|110110|
|S0001|Monthly|240.00|12345|Amount| 30.00 |360.00|316.56|110110|
|S0002|Monthly|240.00|12345|Amount| 30.00 |360.00|316.56|110110|

For item 1000, a renewal term cannot be added because the billing frequency is **One time**. 

Renewal term for both items S0001 and S0002 are added with the following new values (both are the same): 
- Start/End date: January 01, 2021 to December 31, 2021
- Unit price is 25.00
- Total extended amount: 300.00
- Total contract amount: 0.00

The allocation amounts for both renewal terms have not been calculated yet. 

![UnbilledRenew01](../../AX_ARCB/_images/UnbilledRenew01.png)

After invoices for all periods for both items (S0001 and S0002) have been created, the existing revenue allocation is moved to the history. The new revenue allocation is created and calculated based on only the two lines that are renewed. 

![UnbilledRenew02](../../AX_ARCB/_images/UnbilledRenew02.png)

Also, the current renewal lines are updated with the new total contract revenue. 

## Use with milestone billing

The unbilled revenue functionality can be used with a milestone parent item or with a milestone child item. 

### Milestone parent item

When using the unbilled revenue feature with items that use the milestone billing functionality, ensure that the following areas are completed for the milestone parent item in the [Billing schedule lines](../../AX_ARCB/enduser/BillSched.htm#LinesGrid): 
- The **Unbilled revenue** check box is selected
- The start and end dates are specified  
The end date is required for creating the initial journal entry. 
- Billing frequency must be **One time**  
Only the **One time** billing frequency is available. Currently, the renewals functionality is not available for unbilled items that use the milestone billing feature. 
- For a deferral item, the **Deferred** check box is selected  
Currently, the deferral functionality for all child items works through the parent milestone item only. Only one deferral schedule for the entire milestone contract based on the milestone parent item and all changes are applied to the child items. 

Changes to the milestone parent item can only be made on the **[Milestone allocation](../../AX_ARCB/enduser/MilestnAlloc.md)** page. After changes are made, the initial journal entry must be recalculated. 

<details open>
<summary>Unbilled milestone parent example. </summary>
A software company sets up a contract with a customer for a software implementation. The total contract is 100,000.00 with Implementation Services as the main item. The milestone items are as follows: 

- 50% = Deposit
- 30% = User acceptance testing (UAT)
- 20% = Go live

The contract is deferred and the service item is unbilled revenue. The contract runs from January 2021 to December 2021. 

The contract journal entry that is attached to the milestone parent item is as follows: 

| Unbilled revenue account | Deferred revenue account | Debit amount | Credit amount |
|:----|:----|----:|----:|
|Debit unbilled revenue account||100,000.00| &nbsp; |
| &nbsp; |Credit deferred revenue account | &nbsp; |100,000.00|

**First milestone (Deposit)**: The invoice is created, and the billing end date is set: 

| Debit account for unbilled revenue | Credit account for unbilled revenue | Debit amount | Credit amount |
|:----|:----|----:|----:|
|Debit unbilled revenue account (50% of the contract)| &nbsp; |50,000.00| &nbsp; |
| &nbsp; |Credit unbilled revenue account | &nbsp; |50,000.00|

**Second milestone (UAT)**: The invoice is created and the billing end date is set: 

| Debit unbilled revenue account | Credit unbilled revenue account | Debit amount | Credit amount |
|:----|:----|----:|----:|
|Debit unbilled revenue account (30% of the contract)| &nbsp; |30,000.00| &nbsp; |
| &nbsp; |Credit unbilled revenue account | &nbsp; |30,000.00|

**Third milestone (Go live)**: The invoice is created: 

| Debit account for unbilled revenue | Credit account for unbilled revenue | Debit amount | Credit amount |
|:----|:----|----:|----:|
|Debit unbilled revenue account (20% of the contract)| &nbsp; |20,000.00| &nbsp; |
| &nbsp; |Credit unbilled revenue account | &nbsp; |20,000.00|

</details>

### Milestone child item

When using the unbilled revenue feature with milestone child items, keep in mind the following criteria for the milestone parent item or milestone child item in the **[Billing schedule lines](../../AX_ARCB/enduser/BillSched.htm#LinesGrid)**:
- To use the unbilled revenue feature for one or more milestone child items, both the **Deferred** and **Unbilled revenue** check boxes  for the  milestone parent item must be cleared. 
- When one or more milestone child items are deferred and/or uses the unbilled revenue feature, both  the **Deferred** and **Unbilled revenue** check boxes  for the milestone parent item are not available. 
- Billing frequency must be **One time**  

Only the **One time** billing frequency is available. Currently, the renewals functionality is not available for unbilled items that use the milestone billing feature.
- When the milestone child items area processed, the unbilled revenue journal entries and the deferral schedules are attached to the corresponding milestone child items.   
The milestone parent item acts like a regular item and the billing end date for the milestone parent item cannot be edited. 
- After the unbilled revenue initial journal entry is created for one or more milestone child items, the billing schedule line for the milestone parent item cannot be edited. 
- The main account for the milestone child items can be edited. Each milestone child item can use a different financial dimensions, but the main account is the same for all milestone child items. However, if the milestone parent item uses the unbilled revenue feature, all milestone child items must use the same main account as the parent item. 
- For the unbilled revenue initial journal entry to be created, the milestone child item requires an end date. 

Changes to the milestone child item can only be made on the **[Milestone allocation](../../AX_ARCB/enduser/MilestnAlloc.md)** page. After changes are made, the initial journal entry must be recalculated. 

The following journal entries are created for milestone child items: 

| Item | Account | Debit | Credit | Commenmt |
|:----|:----|:----|:---|:---|
|Non-deferred item | &nbsp; | &nbsp; | &nbsp; |Comment|
|Unbilled revenue account| |Debit| |Unbilled revenue account for the line item. |
| &nbsp; |Revenue account | &nbsp; |Credit| &nbsp; |
|Deferred item| &nbsp; | &nbsp; | &nbsp; | &nbsp; | 
|Unbilled revenue account| &nbsp; |Debit| |Unbilled revenue account for the line item.|
| &nbsp; |Deferred revenue account | &nbsp; |Credit|The deferral schedule is created after the unbilled revenue 

<details open>
<summary>Unbilled milestone child item example. </summary>

A software company sets up a contract with a customer for a software implementation. The total contract is 100,000.00 with Implementation Services as the main item. The milestone items are as follows: 
- 50% = Deposit
- 30% = User acceptance testing (UAT)
- 20% = Go live

One of the milestone child items (Go live) is deferred and the child item is also unbilled revenue. The contract runs from January 2021 to December 2021. 

The contract journal entry that is attached to the milestone child item is as follows: 

| Debit account | Credit account | Debit amount | Credit amount |
|:-----|:-----|-----:|-----:|
|Debit unbilled revenue account| &nbsp; |20,000.00| &nbsp; |
| &nbsp; |Credit revenue account | &nbsp; |20,000.00|

**First milestone (Deposit)**: The invoice is created, and the billing end date is set: 

| Debit account | Credit account | Debit amount | Credit amount |
|:-----|:-----|-----:|-----:|
|Debit revenue account (50% of the contract)| &nbsp; |50,000.00| &nbsp; |
| &nbsp; |Credit revenue account | &nbsp; |50,000.00|

**Second milestone (UAT)**: The invoice is created and the billing end date is set: 

| Debit account | Credit account | Debit amount | Credit amount |
|:-----|:-----|-----:|-----:|
|Debit revenue account (30% of the contract)| &nbsp; |30,000.00||
| &nbsp; |Credit revenue account | &nbsp; |30,000.00|

**Third milestone (Go live)**: The invoice is created: 

| Debit account | Credit account | Debit amount | Credit amount |
|:-----|:-----|-----:|-----:|
|Debit revenue account (20% of the contract)| &nbsp; |20,000.00 | &nbsp; |
| &nbsp; |Credit unbilled revenue account (parent account)| &nbsp; |20,000.00 |

</details>

