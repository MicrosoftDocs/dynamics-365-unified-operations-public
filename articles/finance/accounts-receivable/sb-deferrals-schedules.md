---
# required metadata

title: Deferral schedules in Revenue and expense deferrals
description: This Subscription billing topic describes the deferral schedules in Revenue and expense deferrals. 
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

# Deferral schedules

Modules > Subscription billing > Revenue and expense deferrals > Deferral schedules > All deferral schedules 

Modules > Subscription billing > Revenue and expense deferrals > Deferral schedules > Active deferral schedules 


Use this page to review the details about a deferral schedule. The information that appears includes the deferral schedule lines and the total amounts for the deferral schedule. You can also use this page to modify the deferral schedule. 

The details that are shown depend on whether the deferral schedule is a straight line or event based deferral schedule, and also on the transaction type.

Deferral schedules are created after a transaction has been posted. 


## Recognize Revenue

To recognize revenue for a deferral schedule, follow these steps: 
1. From the **[Schedules](#)** page in the **Lines** grid, select the lines you want to recognize, and click **Recognize**. 
1. On the **[Recognition Processing](RecogProc.md)** page, set **Recognition action** to **Create recognition journal** and select the **Cutoff date**. <br />The **Cutoff date** is the date until which to include lines. Only the lines that have an end date earlier or the same as the **Cutoff date** are included in the processing. 
1. Click **Select** and add data filters so that only the range of records that you want appears in the list.
1. From the lines list, select the lines that you do not want to process, and click **Remove**.
1. The journal **Name** and **Description** are automatically updated with the default values. If needed change the values.   
You can select whether to summarize the recognition journal entry.  
1. For the **Transaction date** section, select whether to override the transaction date with a specific date to process the transaction. And you can specify the transaction date for closed periods.  
1. To  process as part of a batch, click **Batch**, which opens the **Batch processing** page.   
Complete the parameters for the batch and click **OK** to return back to the **[Recognition Processing](RecogProc.md)** page.   
The revenue recognition is processed at a later time when the batch is processed. 
1. Select **OK**.  <br />If you did not add this transaction to a batch, all lines are processed immediately. Otherwise, the lines are processed when the batch is processed. 

## Modify Schedule

To modify a deferral schedule, follow these steps: 
1. From the **[All Deferral Schedules](ComSchedList.md)** list or the **[Schedules](#)** form, select the deferral schedule you want, and click **Accounting > Modify schedule**. 
1. On the **[Modify Schedule](ComModSched.md)** page, edit any of the options that you want to change. <br />Depending on the deferral schedule, you can edit only some of the options. 
1. Click **Preview** to review the changes of the deferral schedule, and then close the preview. 
1. Select **OK**.

## Modify Deferral or Recognition Account

To modify the deferral or recognition account for a deferral schedule, follow these steps: 
1. From the **[All Deferral Schedules](ComSchedList.md)** list or the **[Schedules](#)** form, select the deferral schedule you want, and click **Accounting > Modify account**. 
1. On the **[Modify Account](ComSchedReclass.md)** page, select the account you want to change  (deferral, short-term, or recognition). 
1. Select the **New account**. 
1. Select whether changing the account creates adjustment journal entries. If you select yes, select the **Journal name** and specify the **Transaction date**. 
1. Select **OK**.

## Put Schedule on Hold

To put a deferral schedule on hold, follow these steps: 
1. From the **[All Deferral Schedules](ComSchedList.md)** list or the **[Schedules](#)** form, select the deferral schedule you want, and click **Hold > Place hold**. 
1. On the **[Place Hold](ComSchedHoldPlace.md)** page, select whether you want to  transfer the balance from the deferral account ot the hold account. 
1. If you select to transfer the balance, select the **Journal name** and the **On hold account**, and specify the **Transaction date**. 
1. Select **OK**.

## Remove Hold from Schedule

Remove a deferral schedule from a hold: 
1. From the **[All Deferral Schedules](ComSchedList.md)** list  or the **[Schedules](#)** form, select the deferral schedule you want, and click **Hold > Remove hold**. <br />The **[Remove Hold](ComSchedHoldRmv.md)** page opens. 
1. When this page opens, do the following: 
   1. Select the **Journal name**. 
   1. Specify the **Transaction date**. 
   1. Select **OK**.

## Cancel Unrecognized Amounts

To cancel unrecognized amounts on a deferral schedule, follow these steps: 
1. From the **[All Deferral Schedules](ComSchedList.md)** list  or the **[Schedules](#)** form, select the deferral schedule you want, and click **Cancel > Unrecognized amounts**. 
1. On the **[Cancel Unrecognized Amount](ComSchedCnclUnregnz.md)** page, select whether to **Create cancellation entries**. 
1. If you choose to create cancellation entries, select  the **Journal name** and the **Cancellation account**, and specify the **Transaction date**. 
1. Select **OK**.

## Cancel Entire Schedule

to cancel an entire deferral schedule, follow these steps: 
1. From the **[All Deferral Schedules](ComSchedList.md)** list  or the **[Schedules](#)** form, select the deferral schedule you want, and click **Cancel > Entire Schedule**. 
1. On the **[Cancel Entire Schedule](ComSchedCnclEntire.md)** page, select whether to **Create cancellation entries**. 
1. If you select to create cancellation entries, select  the **Journal name** and the **Cancellation account**. Also, specify the **Transaction date**. 
1. Select **OK**.

## Reverse Transactions

To reverse transactions for a deferral schedule, follow these steps: 
1. From the **[Schedules](#)** page in the **Lines** grid, select the lines you want to recognize, and click **Reverse**. 
1. On the **[Recognition Processing](RecogProc.md)** page, set **Recognition action** to **Reverse recognition journal** and select the **Cutoff date**.<br />The **Cutoff date** is the date until which to include lines. Only the lines that have an end date earlier or the same as the **Cutoff date** are included in the processing. 
1. Click **Select** and add data filters so that only the range of records that you want appears in the list.
1. From the lines list, select the lines that you do not want to process, and click **Remove**.
1. The journal **Name** and **Description** are automatically updated with the default values. If needed change the values.   
You can select whether to summarize the recognition journal entry. 
1. For the **Transaction date** section, select whether to override the transaction date with a specific date to process the transaction. And you can specify the transaction date for closed periods. 
1. To  process as part of a batch, click **Batch**, which opens the **Batch processing** page.   
Complete the parameters for the batch and click **OK** to return back to the **[Recognition Processing](RecogProc.md)** page.   
The revenue recognition is processed at a later time when the batch is processed.
1. Select **OK**.  <br />If you did not add this transaction to a batch, all lines are processed immediately. Otherwise, the lines are processed when the batch is processed. 



## Apply or Unapply a Credit Note

To apply a credit note, follow these steps: 

In most situations, these steps are not needed. When you create a credit note from the [Sales Order Transaction Deferral](TransSalesOrderDef.md) page, and set **Adjust existing schedule** to **Yes**, the credit not is automatically applied to the schedule when the credit note is posted. 
1. From the **[All Deferral Schedules](ComSchedList.md)** list  or the **[Schedules](#)** form, select the deferral schedule you want. 
1. In the **Credit adjustments** lines, select a line and click **Apply**. 
1. On the **[Apply Credit Note (Deferrals)](ApplyCrNote.md)** page, specify the **Recalculation date** and **End date** as needed. 
1. In the **Header** list, select the **Sales order** that has credit notes you want to review and process. 
1. In the **Lines** list, select the line you want to process. 
1. Select **OK**.
1. When you are asked to confirm the action, select **Yes**.

![Note icon](../../../Resources/images/icons/iAXnote.gif)**Note:** To apply a credit note to several individual items from different invoices, you must repeat these steps. 

To unapply a credit note, follow these steps: 
1. From the [All Deferral Schedules](ComSchedList.md) list  or the [Schedules](#) page, select the deferral schedule you want. 
1. In the **Credit adjustments** lines, select the **Invoice** you want and click **Unapply**. 
1. When you are asked to confirm the action, select **Yes**.



## Fields

This page contains the following fields: 


| Fields |Description| 
| :------- |:------| 
|**Header**
|**Schedule**|
|**Deferral schedule number**|Displays the deferral schedule number. |
|**Schedule status**|Displays the status of the deferral schedule. |
|**Schedule type**|Displays the deferral schedule type. |
|**Allocation type**|For event-based deferrals, displays the allocation type: **Percentage** or **Amount**. |
|**Description**|Displays a description for the deferral schedule. |
|**Reclassification date**|Displays the most recent date on which the short-term reclassification for a deferral schedule is processed. This date is updated each time the [Event Short-Term Reclassification Processing](ShrtTrmRecalcProc.md) is used for the deferral schedule. <br />Available only when the short-term deferral method used is rolling periods or fixed year. |
|**Account**
|**Deferral account**|Displays the account used for the deferral amount. |
|**Recognition account**|Displays the account used for the recognition amount. |
|**Recognition type**|Displays the recognition type. |
|**Distribution type**|Displays the distribution type.  For information purposes only.|
|**Transaction**|
|**Creation source**|Displays the source from which the transaction was created. |
|**Transaction type**|Displays the transaction type. |
|**Sales order**|Displays the sales order number. |
|**Invoice**|Displays the invoice number.|
|**Item *|Displays the item number. |
|**Billing Schedule**|
|**Billing schedule number**|Displays the number of the corresponding billing schedule. Select the link to view the [Billing Schedules](../../AX_ARCB/enduser/BillSched.md) page. |
|**Billing line status**|Displays the status of corresponding the billing schedule line item. |
|**External references**|Displays the information for external references from the billing schedule: **External** and **Line number**. |
|**Totals**|Displays the following amount totals for the deferral schedule: <br />* Long-term (sum total of the long-term deferred amounts)  <br />Available when **Short-term deferral method** is **None** on the [Advanced Revenue &amp; Expense Deferrals Parameters](../setup/Parameter.md) page, or the short-term amount is greater than zero. <br />* Short-term ( sum total of the short-term deferred amounts)  <br />Available when **Short-term deferral method** is **None** on the [Advanced Revenue &amp; Expense Deferrals Parameters](../setup/Parameter.md) page, or the short-term amount is greater than zero.<br />* Unrecognized (sum total of the unrecognized amount for all lines)<br />* Stubbed (sum total of the stubbed amount for all lines)<br />* Recognized (sum total of the recognized amount for all lines.)<br />* Stubbed and recognized (sum total of the stubbed and recognized amount for all lines. )<br />* Total amount ( sum total of the amount for all lines)|
|**Schedule lines**|
|**Line**|Displays the line sequence number. |
|**Deferral start date**|Displays the start date of the deferral schedule. |
|**Deferral  end date**|Displays the end date of the deferral schedule. |
|**Amount**|Displays the deferral amount. |
|**Stubbed**|Displays whether the line has been stubbed or not. |
|**Recognized**|Displays whether the line has been recognized or not. |
|**Recognition date**|Displays the recognition date. |
|**Journal batch number**|Displays the batch number in which the amount was recognized. |
|**Voucher**|Displays the voucher number for the line. |
|**Event Description**|Displays a description of the event. Available for event-based deferral schedules. |
|**Credit adjustments**|
|**Invoice**|Displays the invoice number.<br />This invoice for the credit note adjustment that has already been applied to the deferral schedule. |
|**Applied amount**|Displays the credit adjustment amount that has already been applied to the deferral schedule. |
|**Applied date**|Displays the date on which the credit adjustment was applied. |
|**User**|Displays the user ID who performed the transaction. |
|**Adjustment**|The adjustment values appear only if a credit memo was processed for the deferral schedule. If no credit note is processed, these values are hidden. |
|**Adjustment amount**|Displays a sum total of the adjustment amount, calculated as follows: original amount - schedule amount. |
|**Original end date**|Displays the original end date for the deferral schedule.|
|**Original schedule amount**|Displays a sum total of the original deferral schedule. |






