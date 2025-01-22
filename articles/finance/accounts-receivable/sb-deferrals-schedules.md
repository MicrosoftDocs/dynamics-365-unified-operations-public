---
title: Deferral schedules in revenue and expense deferrals
description: Learn about deferral schedules in revenue and expense deferrals, including overviews on recognizing revenue and modifying schedules.
author: twheeloc
ms.author: twheeloc
ms.topic: article
ms.date: 01/22/2025
ms.reviewer: twheeloc 
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2021-11-05
ms.search.form: 
ms.dyn365.ops.version: 10.0.24
---

# Deferral schedules

Deferral schedules are created after a transaction has been posted.

You can use the **All deferral schedules** or **Active deferral schedules** page to review the details about a deferral schedule. The information that is shown depends on the type of deferral schedule (straight line or event-based) and the transaction type. It includes the deferral schedule lines and the total amounts for the deferral schedule. You can use the page to modify the deferral schedule.

## Recognize revenue

> [!NOTE]
> - To recognize revenue for one deferral schedule, start at step 1.
> - To recognize revenue for multiple schedules, start at step 2.

1. On the **All deferral schedules** page, in the **Schedule lines** grid, select the lines that you want to recognize, and then select **Recognize**.
2. On the **Recognition processing** page, set the **Recognition action** field to **Create recognition journal**.
3. In the **Cutoff date** field, select the cutoff date. The processing will include only lines where the end date is earlier than or the same as the selected cutoff date.
4. Select **Filter**, and add data filters so that the list shows only the range of records that you want.
5. Select **View preview** to view the lines.
6. In the list of lines, select any lines that you don't want to process, and then select **Remove**.
7. Select whether you want to summarize the recognition journal entry.
8. In the **Transaction date** section, you can override the transaction date with a specific date to process the transaction. The transaction date can be specified for closed periods.
9. To do the processing as part of a batch, select **Batch**. In the **Batch processing** dialog box, set the parameters for the batch, and then select **OK** to return to the **Recognition processing** page. The revenue recognition will be processed later, when the batch is processed.
10. Select **Process**. If you didn't add the transaction to a batch, all lines are immediately processed. Otherwise, the lines will be processed when the batch is processed.

## Modify a schedule

To modify a deferral schedule, follow these steps.

1. On the **All deferral schedules** page, select the deferral schedule, and then select **Accounting \> Modify schedule**.
2. On the **Modify schedule** page, edit the options that you want to change. Depending on the deferral schedule, you won't be able to edit all the options.
3. Select **Preview** to review the changes to the deferral schedule.
4. Select **OK**.

### Straight line deferral schedules

If the deferral schedule has no recognized or externally posted lines, you can modify the whole deferral schedule, including the start date.

If the deferral schedule has any recognized or externally posted lines, and you modify the deferral schedule, the resulting behavior of the deferral schedule depends on the recalculation date and the deferral end date of recognized lines. By default, the first period that wasn't recognized determines the deferral end date.

To use the date of recognition, select one of the following values in the **Start of schedule** field: 
- **Catch up** – The amount after all recognized lines are recalculated.
- **Reversal** – Any lines after the recalculation date are reversed by using the specified journal name and posting date. The amount after the recalculation date is then recalculated.

If a template is used, the skipped periods are ignored, and the template is used only to calculate the end date.

### Event-based deferral schedules

For an event based deferral schedule, you can modify all unrecognized lines.

If the deferral schedule has any recognized or externally posted lines, you can't modify the template and allocation type for the deferral schedule. When you modify an existing deferral schedule, you can't change the value of the **Create separate events per unit** field.

If a line is recognized or externally posted, the **Recognized** checkbox is selected.

## Modify a deferral or recognition account

To modify the deferral or recognition account for a deferral schedule, follow these steps.

1. On the **All deferral schedules** page, select the deferral schedule, and then select **Accounting \> Modify account**.
2. On the **Modify Account** page, select the account that you want to change (deferral, short-term, or recognition).
3. In the **New account** field, select the new account.
4. Select whether changes to the account create adjustment journal entries.
5. If you set the option to **Yes** in the previous step, select the journal name in the **Journal name** field, and specify the transaction date in the **Transaction date** field.
6. Select **OK**.

## Put a deferral schedule on hold

To put a deferral schedule on hold, follow these steps.

1. On the **All deferral schedules** page, select the deferral schedule, and then select **Hold \> Place hold**.
2. On the **Place hold** page, select whether you want to transfer the balance from the deferral account or the hold account.
3. If you selected to transfer the balance, select the journal name in the **Journal name** field, select the hold account in the **On hold account** field, and specify the transaction date in the **Transaction date** field.
4. Select **OK**.

>[!NOTE]
> The **Deferral balance** report doesn't display the billing schedules that are currently on hold. To view the report, go to **Revenue and expense deferral** > **Inquiries and reports** > **Deferral balance**. 

## Remove a hold from a deferral schedule

To remove a deferral schedule from a hold, follow these steps.

1. On the **All deferral schedules** list, select the deferral schedule, and then select **Hold \> Remove hold**.
2. In the **Journal name** field, select the journal name.
3. In the **Transaction date** field, specify the transaction date.
4. Select **OK**.

## Cancel unrecognized amounts

> [!NOTE]
> Any lines that have already been recognized or externally posted are excluded from this process.

To cancel unrecognized amounts on a deferral schedule, follow these steps.

1. On the **All deferral schedules** page, select the deferral schedule, and then select **Cancel \> Unrecognized amounts**.
2. On the **Cancel unrecognized amount** page, select whether you want to create cancellation entries.
3. If you selected to create cancellation entries, select the journal name in the **Journal name** field, select the cancellation account in the **Cancellation account** field, and specify the transaction date in the **Transaction date** field.
4. Select **OK**.

## Cancel a completed schedule

Use the **All deferral schedules** page to reverse any recognized or externally posted amounts and cancel the deferral schedule to prevent further recognition.

To cancel a whole deferral schedule, follow these steps.

1. On the **All deferral schedules** page, select the deferral schedule, and then select **Cancel \> Complete schedule**.
2. On the **Cancel complete schedule** page, select whether you want to create cancellation entries.
3. If you selected to create cancellation entries, select the journal name in the **Journal name** field, select the account in the **Cancellation account** field, and specify the transaction date in the **Transaction date** field.
4. Select **OK**.

## Reverse transactions

> [!NOTE]
> - To reverse revenue recognition for one deferral schedule, start at step 1.
> - To reverse revenue recognition for multiple schedules, start at step 2.

1. On the **All deferral schedules** page, in the **Schedule lines** grid, select the lines that you want to unrecognize, and then select **Reverse**.
2. On the **Recognition processing** page, set the **Recognition action** field to **Reverse recognition journal**.
3. In the **Cutoff date** field, select the cutoff date. The processing will include only lines where the end date is earlier than or the same as the specified cutoff date.
4. Select **Filter**, and add data filters so that the list shows only the range of records that you want.
5. Select **View preview** to view the lines.
6. In the list of lines, select any lines that you don't want to process, and then select **Remove**.
7. The **Name** and **Description** fields are automatically updated with the default journal name and description. You can change the values as you require. You can also select whether you want to summarize the recognition journal entry.
8. In the **Transaction date** section, you can override the transaction date with a specific date to process the transaction. The transaction date can be specified for closed periods.
9. To do the processing as part of a batch, select **Batch**. In the **Batch processing** dialog box, set the parameters for the batch, and then select **OK** to return to the **Recognition processing** page. The reverse revenue recognition will be processed later, when the batch is processed.
10. Select **OK**. If you didn't add the transaction to a batch, all lines are immediately processed. Otherwise, the lines will be processed when the batch is processed.

## Apply or unapply a credit note

To apply a credit note, follow these steps.

> [!NOTE]
> When you create a credit note from the **Sales order transaction deferral** page and set the **Adjust existing schedule** option to **Yes**, the credit note is automatically applied to the schedule when the credit note is posted.

1. On the **All deferral schedules** page, select the deferral schedule.
2. In the **Credit adjustments** list, select a line, and then select **Apply**.
3. On the **Apply credit note (deferrals)** page, specify the recalculation date in the **Recalculation date** field and the end date in the **End date** field.
4. In the **Header** list, select the **Sales order** that has credit notes.
5. In the **Lines** list, select the line.
6. Select **OK**.
7. Select **Yes**.

> [!NOTE]
> To apply a credit note to several individual items from different invoices, you must repeat these steps.

To unapply a credit note, follow these steps.

1. On the **All deferral schedules** page, select the deferral schedule.
2. In the **Credit adjustments** list, select the invoice, and then select **Unapply**.
3. Select **Yes**.

## Fields

The **All deferral schedules** page contains the following fields.

| Fields | Description |
|--------|-------------|
| **Header** | |
| **Schedule** | |
| Allocation type | The allocation type, for event-based deferrals: **Percentage** or **Amount**. |
| Reclassification date | <p>The most recent date when the short-term reclassification for a deferral schedule was processed. This date is updated each time that the **Event short-term reclassification** is used for the deferral schedule.</p>This field is available only when the rolling periods or fixed year short-term deferral method is used. |
| **Account** | |
| Deferral account | The account that is used for the deferral amount. |
| Recognition account | The account that is used for the recognition amount. |
| Recognition type | The recognition type. |
| Distribution type | The distribution type. |
| **Transaction** | |
| Creation source | The source that the transaction was created from. |
| Transaction type | The transaction type. |
| Sales order | The sales order number. |
| Invoice | The invoice number. |
| Item | The item number. |
| **Billing schedule** | |
| Billing schedule number | The number of the corresponding billing schedule. |
| Billing line status | The status of the corresponding billing schedule line item. |
| External references | Information about external references from the billing schedule: **External** and **Line number**. |
| Totals | <p>Amount totals for the deferral schedule:</p><ul><li>**Long-term** – The sum of long-term deferred amounts. This value is available only when the **Short-term deferral method** field is set to **None** on the **Revenue and expense deferrals parameters** page, or the short-term amount is more than 0 (zero).</li><li>**Short-term** – The sum of short-term deferred amounts. This value is available only when the **Short-term deferral method** field is set to **None** on the **Revenue and expense deferrals parameters** page, or the short-term amount is more than 0 (zero).</li><li>**Unrecognized** – The sum of unrecognized amounts for all lines.</li><li>**Stubbed** – The sum of externally posted amounts for all lines.</li><li>**Recognized** –The sum of recognized amounts for all lines.</li><li>**Externally posted and recognized** – The sum of externally posted and recognized amounts for all lines.</li><li>**Total amount** – The sum of amounts for all lines.</li></ul> |
| **Schedule lines** | |
| Line | The line sequence number. |
| Deferral start date | The start date of the deferral schedule. |
| Deferral end date | The end date of the deferral schedule. |
| Amount | The deferral amount. |
| Externally posted | A value that indicates whether the line has been externally posted. |
| Recognized | A value that indicates whether the line has been recognized. |
| Journal batch number | The batch number that the amount was recognized in. |
| Event Description | A description of the event. This field is available only for event-based deferral schedules. |
| **Credit adjustments** | |
| Invoice | <p>The invoice number.</p><p>The value indicates the invoice for the credit note adjustment that has already been applied to the deferral schedule.</p> |
| Applied amount | The credit adjustment amount that has already been applied to the deferral schedule. |
| Applied date | The date when the credit adjustment was applied. |
| **Adjustment** | The adjustment values appear only if a credit memo was processed for the deferral schedule. If no credit note was processed, these values are hidden. |
| Adjustment amount | The total adjustment amount, calculated as *Original amount* – *Schedule amount*. |
| Original end date | The original end date of the deferral schedule. |
| Original schedule amount | The total of the original deferral schedule. |
