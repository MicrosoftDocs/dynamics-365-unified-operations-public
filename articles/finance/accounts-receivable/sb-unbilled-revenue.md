---
# required metadata

title: Unbilled revenue 
description: This topic explains how to set up items to use the unbilled revenue feature in Subscription billing and how to set up the unbilled revenue accounts.
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
# Unbilled revenue

This topic describes the unbilled revenue feature that lets you include the amounts for entire billing schedules on the balance sheet. These amounts are included in an unbilled revenue account and unbilled revenue offset account and the contract is billed through installments. 

## Set up Unbilled revenue 

These steps need to be completed to use the Unbilled revenue feature:
 - On the **Recurring contract billing parameters** page, set up the **Unbilled revenue** section. 
 - The unbilled revenue feature can be used for items where **Item type** is **Standard**. This feature can also be used for deferral items. To use the unbilled revenue feature with the short-term functionality, set up the short-term options on the **Recurring contract billing parameters**. 


Use the steps below on the **Unbilled revenue setup** page, to set up the items and accounts to use for the unbilled revenue feature.

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
4. Select the accounts for the unbilled revenue, unbilled discount, unbilled revenue offset. To use the short-term accounts, set **Short-term unbilled method** to **Rolling periods** or **Fixed year** on the **Recurring contract billing parameters** page.  
5. Repeat these steps to add more lines. 
6. Select **Save**.

### Using unbilled revenue 

1. On the **All billing schedules** page, create a billing schedule as usual. If the item isn't already set up to use the unbilled revenue feature, select **Unbilled revenue** for the billing schedule line. 
2. Set the **Unbilled revenue** option to **Yes**. Review and edit the unbilled revenue, discount and unbilled revenue offset accounts as needed. 
3. On the billing schedule, select **Create journal entry** under **Unbilled revenue processing** to create the initial journal entry for unbilled revenue. This needs to be completed before the billing schedule is invoiced.  
4. Once the initial journal entry is created, use **Generate invoice** to create sales orders and post the invoices for the billing schedules. 
5. After the invoices are posted, you can review the audit information on the **Renewals** tab of the **All billing schedules** page. 

**Milestone billing**: The milestone billing functionality can work with the unbilled revenue feature with the following conditions: 
- When the milestone parent item is unbilled (the **Unbilled revenue** check box is selected) and the milestone child items aren't unbilled (the **Unbilled revenue** check box is cleared), the start and end dates for the parent item must be specified. These dates are used for creating the initial journal entry. 
- When the milestone parent item is unbilled (the **Unbilled revenue** check box is cleared) and the milestone child items aren't unbilled (the **Unbilled revenue** check box is selected), the end date for only the child items for which you want to create the initial journal entry must be specified.   
Each milestone child item can be processed separately. The end dates can be specified when you're ready to create the initial journal entry. 

>[!Note]
>If the initial journal entry for the milestone parent or child items has already been created or an invoice has been created, the start and end dates can't be edited. 

### Unbilled revenue with straight line deferrals

To use the unbilled revenue feature with straight line deferral schedules, follow these steps:
1. On the **All billing schedules** page, create a billing schedule as usual.
2. Add an item to the **Billing schedule lines**.  
3. Select **Deferrals** action for the line. On the **Transaction deferral** page, do the following: 
  - Set **Deferred** to **Yes**. 
  - Change the **Accounts** as needed. 
  - In the **Schedule** section, select **Straight line**, and edit other values as needed. 
  - Select **OK**.
4. Select the **Unbilled revenue** action for the line. 
    - Set **Unbilled revenue** to **Yes**. 
    - Select the accounts to use for the revenue, discount and revenue offset. 
5. For the billing schedule, select **Create journal entry** under **Unbilled revenue processing** or use the **Unbilled revenue mass processing** page to create the journal entry.
6. The deferral schedule is created. You can review the details on the **All deferral schedules** page. After the deferral schedule is created, you can edit various values for the billing schedule line item. For example, unit price, quantity, or dates. 

### Unbilled Revenue with event based deferrals

To use the unbilled revenue feature with event based deferral schedules, follow these steps:
1. On the **All billing schedules** page, create a billing schedule as usual.
2. Add an item to the **Billing schedule lines**.  
3. Select **Deferrals**. On the **Transaction deferral** page, do the following: 
    - Set **Deferred** to **Yes**. 
    - Change the **Accounts** as needed. 
    - In the **Schedule** section, select **Event based**, **Template**, **Allocation type**, and **Expiration account**.
    - Select **OK**.
4. Select the **Unbilled revenue** for the line. 
    - Set **Unbilled revenue** to **Yes**. 
    - Select the accounts to use for the revenue, discount and revenue offset. 
5. For the billing schedule, select **Create journal entry** under **Unbilled revenue processing** or use the **Unbilled revenue mass processing** page to create the journal entry. 
6. The deferral schedule is created. You can review the details of the deferral **All deferral schedules** page. After the deferral schedule is created, you can edit various values for the billing schedule line item. For example, unit price, quantity, or dates. The deferral schedule is recalculated based on the new values. 

The distributions are recalculated based on the **Allocation type** selected (**Percentage**, **Percentage completion**, or **Equal amounts**). For the **Variable amounts allocation** type, the distribution is recalculated based on the percent equivalent of the initial value for the event. For example, the original unit price is 100.00, the percent of the initial value is 55.00, which is 55%. When the unit price is changed to 200.00, the variable amount of the event becomes 110.00, which is 55%. 

>[!Note]
>If deferral schedule lines have been recognized, the billing schedule line item can't be edited. If needed, the recognized lines must be reversed first, and then the billing schedule line can be updated. 

### Unbilled revenue and top billing

A billing schedule is entered for 3 years with the invoices billed annually over a 3-year period. The whole contract amount is recorded in the unbilled revenue account from which annual invoices are created. The offset account is the revenue or the deferred revenue account. 

>[!Note]
>The top billing and the unbilled revenue features don't and can't work together because reconciliation issues in the General Ledger can occur. 

For example, on the **Item group setup** page, ItemGroupA is set up with the **Number of top lines** set to 2. On the **Billing schedules** page, three items are added. All three items belong to ItemGroupA. When the initial journal entry is created for the unbilled revenue feature, the amount for all three items are processed to the unbilled account. When the invoice for the billing schedule is created, only the amounts for the top two items are included. As a result, the invoice amount doesn't match the amount processed to the unbilled revenue account, and reconciliation issues in the General Ledger occur. 

If you want to use the unbilled revenue feature, don't set up the **Item Group Setup** page with any item groups, or set all item groups that have the **Number of top lines** to zero (0). If you want to use the top billing feature, all **Unbilled revenue** actions aren't available. 

### Unbilled revenue examples
As of 10.0.27 a new account is introduced when using Unbilled revenue. When posting the initial **Create journal entry**, the credit is to a new account Unbilled revenue offset. This account is used instead of the revenue account because the same value needs to be reversed out when the billing schedule is invoiced. If there are differences in exchange rates or rounding, the amounts calculated during the **Generate invoice** process could be different. This ensures the accounts net to zero. 

This example explains how to use the unbilled revenue feature to recognize the entire amount of a contract on the balance sheet as unbilled revenue. The other side of the entry is the unbilled revenue offset. When you invoice the customer, the unbilled revenue and unbilled revenue offset are reversed. Revenue recognition will happen at the time of invoicing or will be recognized based on the deferral recognition schedule that was set up.

### The following example shows the unbilled revenue functionality

Assume the following: 
 - a customer signs a 3-year $390 contract on January 1 of the current year. 
 - The contract includes two parts, licenses and a maintenance agreement. 
 - The sales price of the license portion is $300, and that the customer will be invoiced $100 on January 1 of each contract year. The $300 license fee will be taken as revenue when the contract is signed. 
 - The sales price of the maintenance fee is $90, and the customer will be invoiced $30 on January 1, for each of the upcoming years. The $90 maintenance fee will be deferred with $2.50 being recognized each month over the life of the contract. 
 - The customer will be invoiced $130 at the beginning (January 1) of each of the three years of the contract.

1. Assuming the two items already exist as released products, the first step is to set up the two items as unbilled items. Use the **Unbilled revenue setup** to set up the items that use the unbilled revenue feature by default and the accounts that are used when the items are added to the billing schedule.  
2. In the example, the maintenance fee is deferred. The item requires a deferral template, which is set up on the **Deferral templates** page. The template needs a **Monthly** period frequency and a recognition period length of 36 months. As a result, the revenue per month will be 2.50. 
3. Set the **Maintenance fee** as a **Deferrable item** in **Items deferred by default** page. This step and the next step for **Deferral defaults** will cause the **Maintenance fee** item to be deferred by default when it is sold or included on a billing schedule.
4. In the **Deferral defaults**, **Template** option, add the item for the maintenance fee and the straight-line template from step two. The maintenance fee item will be linked to a 36-month deferral schedule.
5. Next, create a billing schedule with the two unbilled items on it. The billing schedule for the contract is set up with the following items:

|Item|Start date|End date|Amount|Billing frequency|Deferral item|Unbilled revenue|Description|
|:-----|:-----|:-----|-----:|:-----|:-----|:-----|:-----|
|License|January 01, CY|December 31 CY+2|100.00|Annually|No|Yes|The customer will be invoiced 100.00 each year. The 300.00 total will be recorded upfront as unbilled revenue on the balance sheet and as revenue on the profit and loss. Each invoice will reduce the unbilled amount.|
|Maintenance|January 01, CY|December 31 CY+2|30.00|Annually|Yes|Yes|The customer will be invoiced 30.00 each year. The 90.00 total will be recorded upfront as unbilled revenue and deferred revenue on the balance sheet. Each invoice will reduce the unbilled amount. The deferred revenue will be recognized monthly over 36 months.|

6. On the **All billing schedules** page, use **Create journal entry** to post the contract value to the balance sheet as unbilled revenue. It will create two journal entries, one for each line on the billing schedule:

| Unbilled revenue account| Unbilled revenue offset account | Debit amount | Credit amount |
|:-----|:-----|-----:|-----:|
|Unbilled revenue account| |300.00| &nbsp; |
| &nbsp; |Unbilled revenue offset account| |300.00|

| Unbilled revenue account| Deferred revenue | Debit amount | Credit amount |
|:-----|:-----|-----:|-----:|
|Unbilled revenue account| &nbsp; |90.00| &nbsp; |
| &nbsp; |Deferred maintenance revenue| &nbsp; |90.00|

The first journal entry is posted to unbilled revenue offset account and the second is posted to a deferred revenue account. If the billing line has both unbilled revenue and deferred revenue, the deferred revenue account is used, not the unbilled revenue offset. The contract requires that the invoice for the customer to be created at the beginning of each year. Use **Generate invoice** to create the invoice. When the invoice is created, the journal entry is as follows: 

| Main account| Unbilled revenue account | Debit amount | Credit amount |
|:-----|:-----|-----:|-----:|
|Unbilled revenue offset| &nbsp; |100.00| &nbsp; |
| |Unbilled revenue account| |100.00|
|Accounts receivable| &nbsp; |100.00| &nbsp; |
| |Revenue account| |100.00|

| Main account| Unbilled revenue account | Debit amount | Credit amount |
|:-----|:-----|-----:|-----:|
|Deferred maintenance revenue account| &nbsp; |30.00| &nbsp; |
| |Unbilled revenue account| |30.00|
|Accounts receivable| &nbsp; |30.00| &nbsp; |
| |Deferred maintenance revenue account| |30.00|

This same journal entry will be created by invoices posted at the beginning of the next two years. The deferred revenue account nets to zero in this example because there is no rounding or exchange rate differences. The deferred revenue needs to be reversed out exactly as it was credited during the **Create journal entry** process. Since revenue is still deferred and will be recognized later, the credit to the deferred revenue account happens again. 

In the last step, the recognition journal entry is created each month to recognize the deferred maintenance fee revenue. The journal entry can be created using the **Recognition processing** page or the **Recognize** for the lines on the **Deferral schedule** pages.

| Deferred revenue account| Revenue account | Debit amount | Credit amount |
|:-----|:-----|-----:|-----:|
|Deferred Maintenance Revenue| &nbsp; |2.50||
| &nbsp; |Maintenance Revenue| &nbsp; |2.50|

This journal entry will be created each time the recognition process is run for this deferred item (a total of 36 times).

#### Short-term: Fixed year

The unbilled revenue feature can be used with the short-term functionality by setting the **Short-term unbilled** field in **Recurring contract billing parameters**. The following example explains the calculations that occur when the unbilled revenue feature is used with the fixed year short-term unbilled method. 

A billing schedule with the following is created: 
- Start Date: June 01, 2020 
- End Date: December 31, 2021
- Unit Price: 100.00
- Frequency: Monthly

On the **All billing schedules** page, the initial journal entry is created from **Create journal entry**. The current short-term and long-term amounts are calculated as follows: 
- Current short-term unbilled revenue amount: $700
- Current long-term unbilled revenue amount: $1200

The invoice for the billing period June 01, 2020, to November 30, 2020, is created. The current short-term and long-term amounts are calculated as follows: 
- Current short-term unbilled revenue amount: $100
- Current long-term unbilled revenue amount: $1200

The invoice for the billing period December 01, 2020, to December 31, 2020, is created. The current short-term and long-term amounts are calculated as follows: 
- Current short-term unbilled revenue amount: $1200
- Current long-term unbilled revenue amount: $0

#### Short-term: Rolling periods

The unbilled revenue feature can be used with the short-term functionality by setting the short-term unbilled method in **Recurring contract billing parameters**. The following example explains the calculations that occur when the unbilled revenue feature is used with the rolling periods short-term unbilled method. 

A billing schedule with the following criteria is created: 
- Start Date: June 01, 2020
- End Date: December 31, 2021
- Unit Price: 100.00
- Frequency: Monthly

On the **All billing schedules** page, the initial journal entry is created from **Create journal entry**. The current short-term and long-term amounts are calculated as follows: 
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

Item 1000 is sold together with Insurance (Item number S0021):
- Billing frequency: Monthly for 12 months 
- Unit price: 20.00 per month
- Standalone selling price: 25.00
- Contract revenue: 264.74

Since both items use the unbilled revenue feature and revenue allocation, the total contract amount on the renewal line is zero (0). A column called **Contract revenue** appears and shows the contract revenue amount. 

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
| &nbsp; |Credit unbilled revenue account| &nbsp; |1,465.26|
 | &nbsp; |Credit unbilled revenue account| &nbsp; |274.74|
 |Debit AR account (130100)| &nbsp; |1,488.16| &nbsp; |

**Changes to the billing schedule line, billing detail line, or revenue allocation**

When the unit price or quantity is changed, the contract revenue amount for each item that is part of the revenue allocation must be updated. As a result, the journal entry is recalculated. 

The unit price for Item 1000 is changed from 1,500 to 1,600. The contract revenue amount is automatically recalculated and becomes 1,549.47. The contract revenue for Item S0021 is recalculated and becomes 290.53. 

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

