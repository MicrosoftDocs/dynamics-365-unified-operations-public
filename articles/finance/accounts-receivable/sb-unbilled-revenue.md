---
# required metadata

title: Unbilled revenue 
description: This topic explains how to set up items that use the unbilled revenue feature in Subscription billing and how to set up the unbilled revenue accounts for the items you select. Examples of using unbilled revenue are also included.
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
# Unbilled revenue

This topic describes the unbilled revenue feature that lets you include the amounts for entire billing schedules on the balance sheet. These amounts are included in an unbilled revenue account and unbilled revenue offset account and the contract is billed through installments. 

## Unbilled revenue setup

This topic explains how to set up items that use the unbilled revenue feature by default, and how to set up the unbilled revenue accounts for the items you select.

These steps need to be completed to use the Unbilled revenue feature:
On the **Recurring contract billing parameters** page, set up the **Unbilled revenue** section. 
Use the steps below on the **Unbilled revenue setup** page, to set up the items and accounts to use for the unbilled revenue feature. The unbilled revenue feature can be used for items where **Item type** is **Standard**. This feature can also be used for deferral items. To use the unbilled revenue feature with the short-term functionality, set up the short-term options on the **Recurring contract billing parameters** along with the steps below. 

Modules > Subscription billing > Recurring contract billing > Setup > Unbilled revenue setup

To set up items to use the unbilled revenue feature by default, follow these steps: 
1. Select the **Items** tab. 
2. Select **Add**.
3. For the line, select the **Item code** and the **Item relation**. 
4. Repeat these steps to add more lines. 
5. Select **Save**.

To set up items and the default unbilled revenue accounts, follow these steps: 
1. Select the **Accounts** tab. 
2. Select **Add**.
3. For the line, select the **Item code** and the **Item relation**. 
4. Select the accounts for the unbilled revenue, unbilled discount, unbilled revenue offset. To use the short-term accounts set **Short-term unbilled method** to **Rolling periods** or **Fixed year** on the **Recurring contract billing parameters** page.  
5. Repeat these steps to add more lines. 
6. Select **Save**.

### Using unbilled revenue 

1. On the **All billing schedules** page, create a billing schedule as usual. If the item is not already set up to use the unbilled revenue feature, select the **Unbilled revenue** action for the billing schedule line. Set the **Unbilled revenue** option to **Yes**, and review and edit the unbilled revenue, discount and unbilled revenue offset accounts as needed. 
2. On the billing schedule, select **Create journal entry** under **Unbilled revenue processing** to create the initial journal entry for unbilled revenue. This needs to be completed before the billing schedule is invoiced. Alternatively, use the **Unbilled revenue mass processing** page to create the journal entry for multiple billing schedules. 
3. Once the initial journal entry is created, use **Generate invoice** to create sales orders and post the invoices for the billing schedules. 
4. After the invoices are posted, you can review the audit information on the **Renewals** tab of the **All billing schedules** page. 

**Milestone billing**: The milestone billing functionality can work with the unbilled revenue feature with the following conditions satisfied: 
- When the milestone parent item is unbilled (the **Unbilled revenue** check box is selected) and the milestone child items are not unbilled (the **Unbilled revenue** check box is cleared) , the start and end dates for the parent item must be specified. These dates are used for creating the initial journal entry. 
- When the milestone parent item is unbilled (the **Unbilled revenue** check box is cleared) and the milestone child items are not unbilled (the **Unbilled revenue** check box is selected), the end date for only the child items for which you want to create the initial journal entry must be specified.   
Each milestone child item can be processed separately and the end dates can be specified when you are ready to create the initial journal entry. 

**Note:** If the initial journal entry for the milestone parent or child items has already been created or an invoice has been created, the start and end dates cannot be edited. 

### Unbilled revenue with straight line deferrals

To use the unbilled revenue feature with straight line deferral schedules, follow these steps:
1. On the **All billing schedules** page, create a billing schedule as usual.
2. Add an item to the **Billing schedule lines**.  
3. If the item is not already a deferral item or you want to change the default values, select **Deferrals** action for the line. On the **Transaction deferral** page, do the following: 
   a. Set **Deferred** to **Yes**. 
   b. Change the **Accounts** as needed. 
   c. In the **Schedule** section, select **Straight line**, and edit other values as needed. 
   d. Select **OK**.
4. If the item is not already set up to use the unbilled revenue feature, or if you want to change the default settings, select the **Unbilled revenue** action for the line. 
   a. Set **Unbilled revenue** to **Yes**. 
   b. Select the accounts to use for the revenue, discount and revenue offset. 
5. For the billing schedule, select **Create journal entry** under **Unbilled revenue processing** or use the **Unbilled revenue mass processing** page to create the journal entry.
6. The deferral schedule is created. You can review the details on the **All deferral schedules** page. After the deferral schedule is created, you can edit various values for the billing schedule line item; for example, unit price, quantity, dates, etc. The deferral schedule is updated with the new values. 

### Unbilled Revenue with Event Based Deferrals

To use the unbilled revenue feature with event based deferral schedules, follow these steps:
1. On the **All billing schedules** page, create a billing schedule as usual.
2. Add an item to the **Billing schedule lines**.  
3. If the item is not already a deferral item or you want to change the default values, select **Deferrals** action for the line. On the **Transaction deferral** page, do the following: 
   a. Set **Deferred** to **Yes**. 
   b. Change the **Accounts** as needed. 
   c. In the **Schedule** section, select **Event based**, **Template**, **Allocation type**, and **Expiration account**. 
   d. Select **OK**.
4. If the item is not already set up to use the unbilled revenue feature, or if you want to change the default settings, select the **Unbilled revenue** action for the line. 
   a. Set **Unbilled revenue** to **Yes**. 
   b. Select the accounts to use for the revenue, discount and revenue offset. 
5. For the billing schedule, select **Create journal entry** under **Unbilled revenue processing** or use the **Unbilled revenue mass processing** page to create the journal entry. 
6. The deferral schedule is created. You can review the details of the deferral **All deferral schedules** page. After the deferral schedule is created, you can edit various values for the billing schedule line item, for example, unit price, quantity, dates, etc. The deferral schedule is recalculated based on the new values. 

The distributions are recalculated based on the allocation type selected (Percentage, Percentage completion, Equal amounts). For the Variable amounts allocation type, the distribution is recalculated based on the percent equivalent of the initial value for the event. For example, the original unit price is 100.00, the percent of the initial value is 55.00, which is 55%. When the unit price is changed to 200.00, the variable amount of the event becomes 110.00, which is 55%. 

**Note:** If deferral schedule lines have been recognized, the billing schedule line item cannot be edited. If needed, the recognized lines must be reversed first, and then the billing schedule line can be updated. 

### Unbilled revenue and top billing

A billing schedule is entered for 3 years with the invoices billed annually over a 3-year period. The whole contract amount is recorded in the unbilled revenue account from which annual invoices are created. The offset account is the revenue or the deferred revenue account. 

**Note:** The top billing and the unbilled revenue features do not and cannot work together because reconciliation issues in the General Ledger can occur. 

For example, on the **Item group setup** page, ItemGroupA is set up with the **Number of top lines** set to 2. On the **Billing schedules** page, three items are added. All three items belong to ItemGroupA. When the initial journal entry is created for the unbilled revenue feature, the amount for all three items are processed to the unbilled account. However, when the invoice for the billing schedule is created, only the amounts for the top two items are included. As a result, the invoice amount does not match the amount processed to the unbilled revenue account, and reconciliation issues in the General Ledger occur. 

If you want to use the unbilled revenue feature, do not set up the **Item Group Setup** page with any item groups, or set all item groups that have the **Number of top lines** to zero (0). If you want to use the top billing feature, keep in mind that all **Unbilled revenue** actions are not available. 

### Unbilled revenue examples
charged to either a revenue or deferred revenue account, depending on the accounting requirements for the transaction
This topic describes how to use the unbilled revenue feature to recognize the entire amount of a contract on the balance sheet as unbilled revenue. The other side of the entry is the unbilled revenue offset. When you invoice the customer the unbilled revenue and unbilled revenue offset are reversed. Revenue recognition happens at the time of invoicing or will be recognized based on the eferral recognition schedule that was set up.

Review the following example to better understand the unbilled revenue functionality.

Assume a customer signs a 3-year $390 contract on January 1 of the current year. The contract includes two parts, licenses and a maintenance agreement. Assume the sales price of the license portion is $300, and that the customer will be invoiced $100 on January 1 of each contract year. The $300 license fee will be taken as revenue when the contract is signed. The sales price of the maintenance fee is $90, and the customer will be invoiced $30 on January 1, for each of the upcoming years. The $90 maintenance fee will be deferred with $2.50 being recognized each month over the life of the contract. The customer will be invoiced $130 at the beginning (January 1st) of each of the 3 years of the contract.

1. Assuming the two items already exist as released products, your first step is to setup the two items as unbilled items. Use the **Unbilled revenue setup** to set up the items that use the unbilled revenue feature by default and the accounts that are used when the items are added to the billing schedule.  
2. In the example, the maintenance fee is deferred. The item requires a deferral template, which is set up on the **Deferral templates** page. The template needs a Monthly period frequency and a recognition period length of 36 months. As a result, the revenue per month will be 2.50. 
3. Set the Maintenance fee as a Deferrable item in **Items deferred by default** page. This step and the next step for Deferral defaults will cause the Maintenance fee item to be deferred by default when it is sold or included on a billing schedule.
4. In the **Deferral defaults**, Template option, add the item for the maintenance fee and the straight-line template from step two. Now the maintenance fee item will be linked to a 36-month deferral schedule.
5. Next create a billing schedule with the two unbilled items on it. The billing schedule for the contract is set up with the following items:

|Item|Start date|End date|Amount|Billing frequency|Deferral item|Unbilled revenue|Description|
|:-----|:-----|:-----|-----:|:-----|:-----|:-----|:-----|
|License|January 01, CY|December 31 CY+2|100.00|Annually|No|Yes|The customer will be invoiced 100.00 each year. The 300.00 total will be recorded upfront as unbilled revenue on the balance sheet and as revenue on the profit and loss. Each invoice will reduce the unbilled amount.|
|Maintenance|January 01, CY|December 31 CY+2|30.00|Annually|Yes|Yes|The customer will be invoiced 30.00 each year. The 90.00 total will be recorded upfront as unbilled revenue and deferred revenue on the balance sheet. Each invoice will reduce the unbilled amount. The deferred revenue will be recognized monthly over 36 months.|

1. On the **All billing schedules** page, use the **Create journal entry** action to post the contract value to the balance sheet as unbilled revenue. It will create two journal entries, one for each line on the billing schedule:

| Unbilled revenue account| Unbilled revenue offset account | Debit amount | Credit amount |
|:-----|:-----|-----:|-----:|
|Unbilled revenue account| |300.00| &nbsp; |
| &nbsp; |Unbilled revenue offset account| |300.00|

| Unbilled revenue account| Unbilled revenue offset account | Debit amount | Credit amount |
|:-----|:-----|-----:|-----:|
|Unbilled revenue account| &nbsp; |90.00| &nbsp; |
| &nbsp; |Unbilled revenue offset account| &nbsp; |90.00|

Notice that the first journal entry is posted to a revenue account and the second is posted to a deferred revenue account. The contract requires that the invoice for the customer to be created at the beginning of each year. Use **Generate invoice** to create the invoice. When the invoice is created, the journal entry is as follows: 

| Main account| Unbilled revenue account | Debit amount | Credit amount |
|:-----|:-----|-----:|-----:|
|AR| &nbsp; |130.00| &nbsp; |
| |Unbilled Revenue account| |130.00|

This same journal entry will be created by invoices posted at the beginning of the next two years.

In the last step, the recognition journal entry is created each month to recognize the deferred maintenance fee revenue. The journal entry can be created using the **Recognition processing** page or the **Recognize** action for the lines on the **Deferral schedule** pages.

| Deferred revenue account| Revenue account | Debit amount | Credit amount |
|:-----|:-----|-----:|-----:|
|Deferred Maintenance Revenue| &nbsp; |2.50||
| &nbsp; |Maintenance Revenue| &nbsp; |2.50|

This journal entry will be created each time the recognition process is run for this deferred item (a total of 36 times).

#### Short-term: Fixed year

The unbilled revenue feature can be used with the short-term functionality by setting the Short-term unbilled method in **Recurring contract billing parameters**. Review the following example to better understand the calculations that occur when the unbilled revenue feature is used with the fixed year short-term unbilled method. 

A billing schedule with the following criteria is created: 
- Start Date: June 01, 2020 
- End Date: December 31, 2021
- Unit Price: 100.00
- Frequency: Monthly

On the **All billing schedules** page, the initial journal entry is created from the header action **Create journal entry**. The current short-term and long-term amounts are calculated as follows: 
- Current short-term unbilled revenue amount: $700
- Current long-term unbilled revenue amount: $1200

The invoice for the billing period June 01, 2020, to November 30, 2020, is created. The current short-term and long-term amounts are calculated as follows: 
- Current short-term unbilled revenue amount: $100
- Current long-term unbilled revenue amount: $1200

The invoice for the billing period December 01, 2020, to December 31, 2020, is created. The current short-term and long-term amounts are calculated as follows: 
- Current short-term unbilled revenue amount: $1200
- Current long-term unbilled revenue amount: $0

#### Short-term: Rolling periods

The unbilled revenue feature can be used with the short-term functionality by setting the short-term unbilled method in **Recurring contract billing parameters**. Review the following example to better understand the calculations that occur when the unbilled revenue feature is used with the rolling periods short-term unbilled method. 

A billing schedule with the following criteria is created: 
- Start Date: June 01, 2020
- End Date: December 31, 2021
- Unit Price: 100.00
- Frequency: Monthly

On the **All billing schedules** page, the initial journal entry is created from the header action **Create journal entry**. The current short-term and long-term amounts are calculated as follows: 
- Current short-term unbilled revenue amount: $1200
- Current long-term unbilled revenue amount: $700

The invoice for the billing period June 01, 2020, to November 30, 2020, is created. The current short-term and long-term amounts are calculated as follows: 
- Current short-term unbilled revenue amount: $1200
- Current long-term unbilled revenue amount: $100

The invoice for the billing period December 01, 2020, to December 31, 2020, is created. The current short-term and long-term amounts are calculated as follows: 
* Current short-term unbilled revenue amount: $1200
* Current long-term unbilled revenue amount: $0

### Items with revenue allocation

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

Since both items use the unbilled revenue feature and revenue allocation, the total contract amount on the renewal line is zero (0). Instead, a column called **Contract revenue** appears and shows the contract revenue amount. 

The initial journal entry for the items and the invoice are as follows: 

|Unbilled revenue account| Deferred revenue account | Debit amount | Credit amount |
|:-----|:-----|-----:|-----:|
|**Item 1000 journal entry**| &nbsp; | &nbsp; | &nbsp; |
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

The unit price for Item 1000 is changed from 1,500 to 1,600. The contract revenue amount is automatically recalculated and becomes 1,549.47. At the same time, the contract revenue for Item S0021 is recalculated and becomes 290.53. 

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

### Revenue allocation and renewals 

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


