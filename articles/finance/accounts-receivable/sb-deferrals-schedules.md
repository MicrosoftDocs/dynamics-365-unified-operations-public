---
# required metadata

title: Deferral schedules in Revenue and expense deferrals
description: This topic describes deferral schedules in Revenue and expense deferrals. 
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

Use the **All deferral**  or the **Active deferral schedules** page to review the details about a deferral schedule. The information that displays the deferral schedule lines and the total amounts for the deferral schedule. You can use this page to modify the deferral schedule. 

The details that are shown depend on whether the deferral schedule is a straight line or event based deferral schedule, and also on the transaction type.

Deferral schedules are created after a transaction has been posted. 

## Recognize Revenue

> [!Note]
> To recognize revenue for one deferral schedule, start with step one. 
> To recognize revenue for multiple schedules, start with step two.

1. Go to the **All deferral schedules** page, in the **Schedule lines** grid, select the lines you want to recognize, and click **Recognize**. 
2. On the **Recognition processing** page, set **Recognition action** to **Create recognition journal** and select the **Cutoff date**. The **Cutoff date** is the date until which to include lines. Only the lines that have an end date earlier or the same as the **Cutoff date** are included in the processing. 
3. Click **Filter** and add data filters so that the correct range of records are displayed in the list. Select **View preview** to see the lines. 
4. From the lines list, select the lines that you do not want to process, and click **Remove**.
5. Select if you want to summarize the recognition journal entry.  
6. In the **Transaction date** section, select to override the transaction date with a specific date to process the transaction. The transaction date can be specified for closed periods.  
7. To process as part of a batch, click **Batch**, which opens the **Batch processing** page. Complete the parameters for the batch and click **OK** to return back to the **Recognition processing** page. The revenue recognition is processed at a later time when the batch is processed. 
8. Select **Process**. If you did not add this transaction to a batch, all lines are processed immediately.  

## Modify schedule

To modify a deferral schedule, follow these steps: 
1. On the **All deferral schedules** page, select the deferral schedule you want, and click **Accounting > Modify schedule**. 
2. On the **Modify Schedule** page, edit the options that you want to change. Depending on the deferral schedule, you can edit only some of the options. 
3. Click **Preview** to review the changes of the deferral schedule. 
4. Select **OK**.

### Straight line

If the deferral schedule has no recognized or externally posted lines, the whole deferral schedule, including the start date, can be modified. 

If the deferral schedule has any recognized or externally posted lines and you modify the deferral schedule, the resulting behavior of the deferral schedule depends on the **Recalculation date** and the deferral end date of recognized lines. This defaults to the first period not recognized. 

To use the date of recognition select **Start of schedule**.   
**Catch up**: The amount after all recognized lines is recalculated.
**Reversal**: Any lines after the recalculation date are reversed using the specified journal name and posting date. The amount after the recalculation date is then recalculated. 

If a template is used then the skipped periods are ignored, and the template is used only to calculate the end date.

### Event based

For an event based deferral schedule, all unrecognized lines can be modified. 

If recognized or externally posted lines exist, the template and allocation type for the deferral schedule cannot be modified. When modifying an existing deferral schedule, you can't change the value for **Create separate events per unit**. 

If a line is recognized or externally posted, the **Recognized** check box is selected.

## Modify deferral or recognition account

To modify the deferral or recognition account for a deferral schedule: 
1. On the **All deferral schedules** page, select the deferral schedule you want, and click **Accounting > Modify account**. 
2. On the **Modify Account** page, select the account you want to change (deferral, short-term, or recognition). 
3. Select the **New account**. 
4. Select whether changing the account creates adjustment journal entries. If you select yes, select the **Journal name** and specify the **Transaction date**. 
5. Select **OK**.

## Put deferral schedule on Hold

To put a deferral schedule on hold, follow these steps: 
1. On the **All deferral schedules** page, select the deferral schedule you want, and click **Hold > Place hold**. 
2. On the **Place Hold** page, select whether you want to transfer the balance from the deferral account or the hold account. 
3. If you select to transfer the balance, select the **Journal name** and the **On hold account**, and specify the **Transaction date**. 
4. Select **OK**.


## Remove hold from deferral schedule

Remove a deferral schedule from a hold: 
1. On the **All deferral schedules** list, select the deferral schedule you want, and click **Hold > Remove hold**. 
2. Select the **Journal name**. 
3. Specify the **Transaction date**. 
4. Select **OK**.

## Cancel unrecognized amounts

> [!Note]
> Any lines that have already been recognized or posted externally are excluded from this process. 

To cancel unrecognized amounts on a deferral schedule, follow these steps: 
1. On the **All deferral schedules** page, select the deferral schedule you want, and click **Cancel > Unrecognized amounts**. 
2. On the **Cancel unrecognized amount** page, select if you want to **Create cancellation entries**. 
3. If you choose to create cancellation entries, select the **Journal name** and the **Cancellation account**, and specify the **Transaction date**. 
4. Select **OK**.


## Cancel complete schedule

Use the **All deferral schedules** page to reverse any recognized or externally posted amounts and cancel the deferral schedule to prevent further recognition. 

To cancel an entire deferral schedule, follow these steps: 
1. On the **All deferral schedules** page, select the deferral schedule you want, and click **Cancel > Complete schedule**. 
2. On the **Cancel complete schedule** page, select whether to **Create cancellation entries**. 
3. If you select to create cancellation entries, select the **Journal name** and the **Cancellation account**. Also, specify the **Transaction date**. 
4. Select **OK**.

## Reverse Transactions

> [!Note]
> To recognize revenue for one deferral schedule, start with step one. 
> To recognize revenue for multiple schedules, start with step two.

1. On the **All deferral schedules** page in the **Lines** grid, select the lines you want to unrecognize, and click **Reverse**. 
2. On the **Recognition processing** page, set **Recognition action** to **Reverse recognition journal** and select the **Cutoff date**. The **Cutoff date** is the date until which to include lines. Only the lines that have an end date earlier or the same as the **Cutoff date** are included in the processing. 
3. Click **Filter** and add data filters so that only the range of records that you want appears in the list. Select **View preview** to see the lines.
4. From the lines list, select the lines that you do not want to process, and click **Remove**.
5. The journal **Name** and **Description** are automatically updated with the default values. If needed change the values. You can select whether to summarize the recognition journal entry. 
6. For the **Transaction date** section, select whether to override the transaction date with a specific date to process the transaction and specify the transaction date for closed periods. 
7. To  process as part of a batch, click **Batch** to open the **Batch processing** page.   
Complete the parameters for the batch and click **OK** to return back to the **Recognition processing** page.   
The reverse revenue recognition is processed at a later time when the batch is processed.
8. Select **OK**.  If you did not add this transaction to a batch, all lines are processed immediately. Otherwise, the lines are processed when the batch is processed. 


## Apply or Unapply a Credit Note

To apply a credit note, follow these steps: 

When you create a credit note from the **Sales order transaction deferral** page and set **Adjust existing schedule** to **Yes**, the credit note is automatically applied to the schedule when the credit note is posted. 
1. On the **All deferral schedules** page, select the deferral schedule. 
2. In the **Credit adjustments** lines, select a line and click **Apply**. 
3. On the **Apply credit note (deferrals)** page, specify the **Recalculation date** and **End date**. 
4. In the **Header** list, select the **Sales order** that has credit notes. 
5. In the **Lines** list, select the line. 
6. Select **OK**.
7. Select **Yes**.

> [!Note]
> To apply a credit note to several individual items from different invoices, you must repeat these steps. 

To unapply a credit note, follow these steps: 
1. On the **All deferral schedules** page, select the deferral schedule. 
2. In the **Credit adjustments** lines, select the **Invoice** and click **Unapply**. 
3. Select **Yes**.

### Fields

The **All deferral schedules** page contains the following fields: 


| Fields |Description| 
| :------- |:------| 
|**Header**
|**Schedule**|
|**Allocation type**|For event-based deferrals, displays the allocation type: **Percentage** or **Amount**. |
|**Reclassification date**|The most recent date that the short-term reclassification for a deferral schedule was processed. This date is updated each time the **Event short-term reclassification** is used for the deferral schedule. Available only when the short-term deferral method used is rolling periods or fixed year. |
|**Account**
|**Deferral account**|The account used for the deferral amount. |
|**Recognition account**|The account used for the recognition amount. |
|**Recognition type**|The recognition type. |
|**Distribution type**|The distribution type. |
|**Transaction**|
|**Creation source**|The source that the transaction was created. |
|**Transaction type**|The transaction type. |
|**Sales order**|The sales order number. |
|**Invoice**|Displays the invoice number.|
|**Item**|Displays the item number. |
|**Billing Schedule**|
|**Billing schedule number**|Displays the number of the corresponding billing schedule. |
|**Billing line status**|Displays the status of corresponding the billing schedule line item. |
|**External references**|Displays information for external references from the billing schedule: **External** and **Line number**. |
|**Totals**|Displays amount totals for the deferral schedule: <br />Long-term (sum total of the long-term deferred amounts)  <br />Available when **Short-term deferral method** is **None** on the **Revenue and expense deferrals parameters** page, or the short-term amount is greater than zero. <br />Short-term (sum total of the short-term deferred amounts)  <br />Available when **Short-term deferral method** is **None** on the **Revenue and expense deferrals parameters** page, or the short-term amount is greater than zero.<br />Unrecognized (sum total of the unrecognized amount for all lines)<br />Stubbed (sum total of the externally posted amount for all lines)<br />Recognized (sum total of the recognized amount for all lines.)<br />Externally posted and recognized (sum total of the externally posted and recognized amount for all lines).<br />Total amount (sum total of the amount for all lines)|
|**Schedule lines**|
|**Line**|Displays the line sequence number. |
|**Deferral start date**|The start date of the deferral schedule. |
|**Deferral end date**|The end date of the deferral schedule. |
|**Amount**|The deferral amount. |
|**Externally posted**|Displays if the line has been externally posted or not. |
|**Recognized**|Displays if the line has been recognized or not. |
|**Journal batch number**|Displays the batch number in which the amount was recognized. |
|**Event Description**|Displays a description of the event. Available for event-based deferral schedules. |
|**Credit adjustments**|
|**Invoice**|Displays the invoice number.<br />This invoice for the credit note adjustment that has already been applied to the deferral schedule. |
|**Applied amount**|Displays the credit adjustment amount that has already been applied to the deferral schedule. |
|**Applied date**|Displays the date on which the credit adjustment was applied. |
|**Adjustment**|The adjustment values appear only if a credit memo was processed for the deferral schedule. If no credit note is processed, these values are hidden. |
|**Adjustment amount**|Displays a sum total of the adjustment amount, calculated as follows: original amount - schedule amount. |
|**Original end date**|Displays the original end date for the deferral schedule.|
|**Original schedule amount**|Displays a sum total of the original deferral schedule. |






