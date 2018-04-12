---
# required metadata

title: [Topic name]
description: [Full description that appears in the search results. Often the first paragraph of your topic.]
author: josaw1
manager: AnnBe
ms.date: 04/12/2016
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: [Pick one: Application User/Developer/IT Pro]
# ms.devlang: 
ms.reviewer: [Content Strategist microsoft alias]
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: [Global for most topics. Set Country/Region name for localizations]
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: [author's Microsoft alias]
ms.search.validFrom: 2018-04-30
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update
---

# Improvements around statement posting

## Overview ##

At the 2017 Technical Conference, Microsoft Dynamics 365 for Retail team announced a multi-release plan to enhance the statement posting capabilities in the product. This was warranted due to the multiple reliability, performance & product issues around this feature across multiple versions of the product.

Accordingly, the first set of improvements around the statement posting feature was released in the 7.3.2 release of the product.

## Activation ##

During deployment of the 7.3.2 version of the application, the application is defaulted to the legacy feature for statement postings. To enable the new & improved statement posting feature, the configuration keys for the same must be enabled as per the steps outlined below:

1.  Navigate to System administration > Setup > License configuration and uncheck the configuration key “Retail statements (legacy)” under the Retail node

2.  Navigate to System administration > Setup > License configuration and check the configuration key “Retail statements” under the Retail node

3.  When the new “Retail statements” configuration key is enabled, a new menu item called as “Retail statements” will be enabled using which statements can be created, calculated and posted manually. Any statement resulting in an error using the batch posting process will also be available under this menu item. With the legacy configuration key, the menu item name would be “Open statements”

The following validations are built into the application around these configuration keys:

1.  Both the configuration keys cannot be enabled at the same time

2.  A statement must go through all the various operations in its lifecycle in terms of Create, Calculate, Clear, Post etc. using only one of the configuration keys. For e.g.: One cannot Create and calculate a statement with the “Retail statement (legacy)” configuration key turned ON and then try and post the same statement with the “Retail statement” configuration key turned ON.

***Note:*** As a best practice recommendation, it is advisable to use the new & improved statement posting feature using the “Retail statements” configuration key unless there are compelling reasons to use the legacy option. Microsoft will continue to invest and improve the new statement posting feature and it is important to switch to it at the earliest to reap the benefits from the same. With newer releases, the new feature will be made as the default option for statement postings and the legacy capability will be sunsetted over a period.

## Setup ##

As a part of improvements around statement posting, a few new parameters are introduced in Statement fast tab under Retail Parameters > Posting tab and the details of the same are as below:

**1.  Disable clear statement:** This parameter is only applicable for the legacy feature of statement posting. The recommendation is for this parameter to be set to NO as this will not allow users to Clear statements which are in a semi-posted state. Clearing statements that are in semi-posted state causes further data corruption. This parameter should only be set to YES under exceptional circumstances.

**2.  Reserve inventory during calculation:** The recommended process for inventory reservation is to use the “Post inventory” batch job and the recommendation is to set this parameter to NO. With this parameter set to NO, the new feature will not try to create inventory reservation entries (if not already done through Post inventory batch job) during calculation and will only do it at the time of posting. It was design choice to implement it that way as typically the time window between the calculate process and post process is normally small. However, if a customer does want to reserve inventory at the time of calculation, then they can do so by setting this parameter to YES. The legacy feature would always reserve inventory (if not already done through Post inventory batch job), during the statement calculation process irrespective of any settings of this parameter.

**3.  Disable counting required**: This parameter when set to YES will not stop the statement from the posting process even when the difference between the counted amount and transaction amount on a statement is outside the threshold as defined on the statement fast tab of Retail stores

**4. Maximum number of parallel statement psotings**: This parameter has been introduced under the Batch processing fast tab of Retail parameters > Posting tab. This parameter defines how many executing batch tasks should be run at a time. Currently this parameter must be manually defined by the customer. However, in a future release this will be set heuristically based on customers topology and set-up.

In addition to the above, all the settings & parameters that govern statement postings as defined under Retail Stores and Retail parameters are all applicable even for the new statement posting feature.

## Processing ##

Statements can be calculated and posted using the batch process (Calculate statements in batch & Post statements in batch) or can also be calculated and posted manually using the “Retail statements” menu item using the new feature.

The process & steps to calculate & post statements in a batch remains the same as in the legacy feature. However, there have been significant improvements made in the core back end processing of the statements which in addition to building resiliency into the process, also provides for better visibility in to the states and error information, using which users can fix the root cause of the errors and then continue the posting without causing data corruption and the need for data fixes.

The following are some of the major improvements around the new feature that are surfaced on the UI for “Retail statements” and “Posted statements”:

### 1.  Status details
A new state model has been introduced in the statement posting routine across the calculate & post process and the details of the same are as below: 

**The table below describes the different states & their order during the Calculate process:**

| State order | State      | State description                                                                                                                                |
|-------------|------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
| 1           | Started    | Statement was created and is ready to be calculated                                                                                              |
| 2           | Marked     | The transactions that are in scope for the statement are identified based on the statement parameters and they are marked with the statement id. |
| 3           | Calculated | The statement lines are computed and displayed                                                                                                   |

**The table below describes the different states & their order during the Post process:**

| State order | State                   | State description                                                                                                                                                        |
|-------------|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1           | Checked                 | Multiple validations around parameters (for e.g.: disposition charge), statement & statement lines (for e.g.: difference between counted & transaction amount) are done. |
| 2           | Aggregated              | Sales transactions for named and unnamed customers are aggregated based on configuration. Each aggregated transaction will eventually convert to a sales order           |
| 3           | Customer order created  | Based on the aggregated transaction, Sales orders are created in the system                                                                                              |
| 4           | Customer order invoiced | Sales orders are invoiced                                                                                                                                                |
| 5           | Discounts posted        | Periodic discount journals are posted based on configuration                                                                                                             |
| 6           | Income / Expense posted | Income / Expense transactions are posted as vouchers                                                                                                                     |
| 7           | Vouchers linked         | Payment journals created and linked to the corresponding invoice                                                                                                         |
| 8           | Payments posted         | Payment journals are posted                                                                                                                                              |
| 9           | Gift cards posted       | Gift card transactions are posted as vouchers                                                                                                                            |
| 10          | Posted                  | Statement is marked as posted                                                                                                                                            |

Each of the above state is atomic in nature and there is a hierarchical dependency built between these states that flows from top to bottom. If the system encounters any errors while processing a state, the status of the statement is reverted to the previous state. Any subsequent retry of the process would pick it from the state that was failed and will continue to progress forward.

**The above has the following benefits:**

  1.  User has complete visibility in terms of what state the error has occurred

  2.  Data corruption is avoided. For e.g.: with the legacy feature there were instances of few sales orders invoiced and few left open, few payment journals did not have the corresponding invoice to settle as the invoice posting has an error etc.

 Users can see the current state of a statement using the “Status details” button on the “Execution details” group of the statement. The status details screen has three sections to it as below:

-   Section 1 shows the current status of the statement along with the Error code and a detailed error message whenever applicable

-   Section 2 shows the different states of the Calculate process with visual cues to communicate which state was successfully executed, which state errored out and which state is yet to be executed.

-   Section 3 shows the different states of the Post process with visual cues to communicate which state was successfully executed, which state errored out and which state is yet to be executed

The overall status for the above two sections are also shown on the header part of the corresponding sections.

### 2.  Event logs
A statement goes through different operations in terms of Create, Calculate, Clear & Post and there could be multiple instances of the same operation being called in its lifecycle in. For e.g.: After Create and Calculate, a user can Clear the statement and Calculate it again. The “Event logs” button on the “Execution details” group provides a complete audit trail of the different operations being called on a statement along with information on when those operations were called.

### 3.  Aggregated transactions
During the Post process, the sales transactions are aggregated based on configuration and these aggregated transactions are stored in the system to create sales orders. Each aggregate transaction will create one corresponding sales order in the system. These aggregate transactions can be viewed using the “Aggregated transactions” button on the “Execution details” group of the statement.

The sales order detail tab of the aggregated transaction form shows the following information:

  1.  Record-ID: Aggregate transaction id

  2.  Statement number: The statement to which the aggregated transaction belongs to

  3.  Date: Date on which the aggregated transaction was created

  4.  Sales ID: Sales order id on successful creation of a Sales order from the aggregated transaction. If this field is blank, this denotes that the corresponding sales order has not been created.

  5.  Number of aggregated lines: The total number of lines for the aggregated transaction and sales order

  6.  Status: Shows the last status of the aggregated transaction

  7.  Invoice id: Sales invoice id on successful invoicing of the sales order for the aggregated transaction. If this field is blank, this denotes that invoice for the sales order has not been posted.

The transaction details tab of the aggregated transaction shows all the retail transactions which has been pulled into the aggregated transaction. The aggregated lines on the aggregated transaction shows all the aggregated records from the retail transactions and shows details in terms of item, variant, qty, price, net amount, unit & warehouse. In essence, the aggregated lines will correspond one to one with the sales order lines.

From the aggregated form it is also possible to download the XML for a particular aggregated transaction using the “Export sales order xml” button on the aggregated form. This xml can be used to debug issues around sales order creation & posting by downloading the xml, uploading it to a Test environment and debugging the same in the Test environment. The XML download capability is not available on Posted statements.

The aggregated transaction view provides the following benefits:

  1.  Provides visibility to users on what aggregated transaction failed in sales order creation and what sales orders failed invoicing

  2.  Provides visibility in terms of how transactions are aggregated

  3.  It provides the user a complete audit trail in terms of Retail transactions > Sales order > Sales invoice. This view was not available with the legacy feature.

  4.  Aggregated XML file allows for easier issue identification during sales order creation and invoicing



### 4. Journal vouchers
The “Journal vouchers” button shows all the different voucher transactions around Discounts, Income / Expense account, Gift card etc. that are created for a statement.

The current version of the product only shows this data for posted statements. However, in a future release there will be capability on Retail Statements i.e. unposted statements to see all the different journal vouchers created, journals that were successfully posted and journals that errored out.

### 5. Payment journals
The “Payment journals” button shows all the different payment journals that are created for a statement.

The current version of the product only shows this data for posted statements. However, in a future release there will be capability on Retail Statements i.e. unposted statements to see all the payment journals created, payment journals that were successfully posted and payment journals that errored out.

## Other improvements

Some of the other back end improvements around the new statement posting feature which is transparent to an end user is as follows:

1.  The new statement posting feature does not consider the entities of staff, terminal and shift in the aggregation logic. The reduced count of aggregation parameters results in lesser number of sales order lines to process

2.  Reduced the occurrence of deadlock on retail transaction tables by introducing additional extension tables and performing insert operation instead of update operation on the retail transaction tables

3.  Parameterized and limited the no. of executing batch tasks which can be fine-tuned specifically to a customer’s environment. With the legacy feature, unlimited no. of batch tasks was created at the same time creating unmanageable loads, overhead and bottlenecks on the batch server

4.  Efficient queuing of statements for processing by prioritizing the statements with maximum transactions

5.  Batch processes like “Calculate statements in batch” and “Post statements in batch” are only executed in batch mode. With the legacy feature, users had a choice to execute these batch processes in an interactive mode. Interactive mode of processing statements is a single threaded operation

6.  With the legacy feature, any batch task failure will put the batch job in an error state where as with the new feature, batch task failures do not error out the batch if there are other batch tasks that are successfully completed. The posting status for a batch execution run should be assessed using the “Retail statements” form and any unposted statements due to errors can be seen in this form.

7.  With the legacy feature, the first occurrence of statement failure will fail the entire batch without even processing the remaining statements. With the new feature, the batch process continues processing all statements even if some of the statement errors out. As a result, the user benefits by getting a visibility of the exact number of statements that have errors and the user does not have to get into a loop of fix, run, fix and so on to post the statements

## General guidance around statement posting process

1.  It is recommended to run the statement posting process in a batch as batch runs leverage the power of batch framework in terms of multi-threading which is required to handle the huge volumes of transactions that is normally seen with statement postings

2.  It is recommended to enable negative physical inventory on the Item model group to have a seamless posting experience as there could be scenarios where not having negative physical inventory will not allow statements to post. (For e.g.: if there was only one unit in inventory for an item, and there has been a sale and return transactions for the item, in theory the transaction should be able to post even without negative inventory turned on. However, since the statement posting process pulls both the sale & return transaction in a single customer order it cannot be guaranteed that the sale line would post first followed by the return line and as such could lead to errors. Turning on negative inventory in the above scenario does not negatively impact anything as at the end of the above transaction posting, the inventory would be correctly reflected in the system)

3.  It is highly recommended to use aggregation while calculating & posting statements. Accordingly, the below are the recommended settings for some of the aggregation parameters:

    1.  Retail >  Headquarters setup > Parameters > Retail parameters > Posting > Inventory update > Detail level = Summary

    2.  Retail > Headquarters setup > Parameters > Retail parameters > Posting > Aggregation > Voucher transactions = Yes




# <add title>

[!include[banner](includes/banner.md)]

