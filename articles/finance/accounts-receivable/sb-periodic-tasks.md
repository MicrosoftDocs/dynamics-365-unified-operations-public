---
title: Periodic tasks in Recurring contract billing
description: Learn about the periodic tasks that are available in Recurring contract billing, including overviews on generating invoices and invoice batch processing.
author: JodiChristiansen
ms.author: jchrist
ms.topic: article
ms.date: 07/30/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.scope: Core, Operations
ms.search.region: Global
ms.search.validFrom: 2021-11-05
ms.search.form: 
ms.dyn365.ops.version: 10.0.24
---

# Periodic tasks in Recurring contract billing

This article describes the periodic tasks that are available in Recurring contract billing.

## Generate invoice

Use the **Generate invoice** page to create mass monthly recurring invoices from the information that you set up on the **All billing schedules** and **View billing detail** pages. When you create an invoice, the item description for the sales order processing line updates with the item description and the billing start and end dates for the schedule line that's invoiced. 

## Generate invoice batch processing

Use the **Generate invoice batch processing** page to create recurring invoices through a recurring batch process. The **Date range** filter lets you select the billing schedules by start date or end date. To use a start date or end date other than today's date, set the **Add the number of days or months** option to **Yes**. Then, in the **Select by days or months** field, select **Days** or **Months**, and enter the number of days or months. For days, a value of **0** represents today. For months, **0** represents the first day through the last day of the current month.

For example, the current month is January, and you want to include billing schedule lines that have a start date through March 1. In this case, select **Months**, and then set the number of months to **2**. (For months, the current month is always included.) If today is January 15, and you want to include billing schedule lines from January 1 through December 31 of the previous year, select **Days**, and then set the number of days to **-350** (= 365 – 15).

The batch processing flag is set to **Yes** and you can't change it to **No**.

## Generate quotation

Use the **Generate quotation** page to create a **Sales quotation** report for multiple billing schedules at the same time. Each billing schedule prints a **Sales quotation** report.

## Price update

Use the Price update utility to update the prices of several items on multiple billing schedules in a single action. You can update the prices based on either a specified percentage or a specified amount. The list of lines shows only the current unit prices of the items. It doesn't show the prices after the price update.

Note the following points about the Price update utility:

- If the sales order for a specific year is already created (that is, the items are billed), the price of the line items isn't affected.
- Use the Price update utility for line items that have a status of **Active** or **On hold**. For items that are on hold, set the **Adjust schedule** option to **No** when you place the hold.
- You can't use the Price update utility for line items that are usage items, that use escalation, milestone billing, or revenue splitting.

### Price update example

You create a billing schedule and add a renewal item. The unit price is $750. You pay for the first year of the item on December 15, 2021. You create the billing schedule for the period from January 1 through December 31, 2022.

At renewal time, the **Generate invoice** process creates the sales order for the year 2022. After you run the Price update utility, the price updates from $750 to $800.

The sales order and billing schedule for 2022 aren't affected, and the unit price remains $750, because the billing schedule for 2022 is already billed. You update the billing schedule line and line detail for 2023 to $800, because the billing schedule for 2023 isn't billed yet.

### Update prices – Flat pricing method

When you update prices for items that use the flat pricing method, you can specify a percentage or amount to increase the price.

To run the Price update utility for items that use the flat pricing method, follow these steps:

1. On the **Price update** utility page, select the **Flat** pricing method.
1. In the **Increase method** field, select the increase method that you want to use to update the price of the items.
1. Depending on the increase method that you selected, specify the percentage in the **Percent** field or the amount in the **Amount** field.
1. On the **Records to include** FastTab, use the **Filter** button to add data filters.
1. Select **View preview** to view the range of records.
1. If you don't want to process some of the lines, mark them, and then select **Remove**.
7. Select **OK**.

### Update prices – Standard pricing method

If you change the price of an item in the item record, you can update that price for all billing schedule lines if the item uses the standard pricing method.

1. On the **Price update** utility page, select the **Standard** pricing method.
1. On the **Records to include** FastTab, use the **Filter** button to add data filters.
1. Select **View preview** to view the range of records.
1. If you don't want to process some of the lines, mark them, and then select **Remove**.
1. Select **OK**.

## Mass hold processing

Use the **Mass hold** page to apply hold options to several billing schedules at the same time.

To put just one billing schedule or one billing schedule line on hold, open the **All billing schedules** page, and select **Place hold**. To remove a hold, use the **Remove hold** page.

### Put billing schedules on hold

To put several billing schedules on hold, follow these steps:

1. On **Mass hold**, set the **Process option** field to **Apply hold**.
1. In the **Reason code** field, select a reason code.
1. Set the **Adjust schedule** option:

    - **Yes** – If you set the option to **Yes**, specify a hold date in the **Hold date** field. The process removes any billing schedule lines after the hold date.
    - **No** – The process doesn't change the billing schedule lines. It changes only the status to **On hold**.

1. On the **Records to include** FastTab, use the **Filter** button to add data filters.
1. Select **View preview** to view the range of records.
1. If you don't want to process some of the lines, mark them, and then select **Remove**.
7. Select **OK**.

When you return to the list of billing schedules, you see that the status of the billing schedules is **On hold**.

### Remove a hold from several billing schedules

1. On **Mass hold**, set the **Process option** field to **Remove hold**.
1. In the **Reason code** field, enter a reason code.
1. In the **Remove date** field, select the date when the hold should be removed.
1. Set the **Resumption date** and **Deferral date** fields as you require. The deferral date applies to all lines that are deferrable.
1. On the **Records to include** FastTab, use the **Filter** button to add data filters.
1. Select **View preview** to view the range of records.
1. If you don't want to process some of the lines, mark them, and then select **Remove**.
1. Select **OK**.

> [!NOTE]
> To remove a hold, you must set the **Remove hold user group override** value on the **Recurring contract billing parameters** page.

For example, a billing line has a start date of February 1, 2022, and an end date of February 28, 2022. The billing amount is $200. The **Hold date** field is set to February 10, 2022. Therefore, the February period is adjusted to exclude any date after February 10. The new period is from February 1 through February 9, and the amount is $64.29 (through daily proration). All billing schedule lines on or after February 10 are removed.

If the **Remove hold** process is completed, and the **Remove date** field is set to February 10, 2022, there are two billing periods. The first billing period is from February 1 through February 9, and the amount is $64.29. The second billing period is from February 10 through February 28, and the amount is $135.71.

## Mass termination processing

Use the **Mass termination** page to terminate billing schedule lines that are currently shown by specifying a termination date and reason code. 

If you're using revenue and expense deferrals, billing schedules where the **Termination date** field is set to **Adjust schedule** on the **All billing schedules** page are eligible for a refund.

Billing schedules that use the multiple element allocation (MEA) functionality don't appear on the **Mass termination** page. You can still terminate an individual billing schedule by using the termination functionality on the billing schedule.

> [!NOTE]
> Billing schedule lines that are currently included in a **Generate invoice** batch aren't available for this process.

On the **Mass termination process** page, in **Process options**, select **Remove termination** to remove the termination from multiple billing schedules or billing schedule lines that are terminated. Use the filter for the **Billing schedule** to select which billing schedules to remove the termination from. If a billing schedule line was terminated with a credit that you invoiced, you can't remove it and those lines don't appear in the preview.

For information about each field and the process, see [Terminate billing schedules](terminate-billing-schedule.md).

## Mass termination table clean up

Use the **Mass termination table clean up** process to clear the mass termination tables after you use the mass termination entity.

## Mass archive process

Use the **Mass archive** page to archive multiple billing schedules. You can only archive terminated billing schedules.

When you archive a billing schedule, the following changes occur:

- The status changes to **Archived**.
- The system permanently locks the billing schedules.
- The billing schedule lines no longer appear on inquiry pages.

> [!NOTE]
> Archiving a billing schedule is a permanent action and can't be reversed.

To archive billing schedules, follow these steps:

1. On the **Mass archive** page, in the **Billing end date** field, enter a billing end date. To view all terminated billing schedules, leave this field blank.
1. On the **Records to include** FastTab, use the **Filter** button to limit the records that are shown.
1. Select **View preview**.
1. If you don't want to archive some of the records, mark them, and then select **Remove**.
1. Select **OK** to archive the records on the page.

## Mass stubbing process

Use the **Mass stubbing** page to mark all selected billing schedule lines as billed (stub) or unbilled (reverse stub). Stubbing or reverse stubbing are most often performed on imported billing schedule lines that were previously billed in another system. Stubbed billing schedule lines appear as stubbed and don't create an invoice for the customer.

### Stub records

1. On **Mass stubbing**, in the **Process options** field, select **Stub**.
1. In the **Cutoff date** field, set a cutoff date to specify the lines that you want to apply the process to. The system shows only records where the billing start date is on or before the cutoff date you specify.
1. Select **View preview** to show the lines that you want to stub.
1. To exclude a line from the process, mark it, and then select **Remove**.
1. Select **Process** to stub the lines.

### Reverse stub records

1. On the **Mass stubbing** page, in **Process options** field, select **Reverse stub**.
1. In the **Cutoff date** field, set a cutoff date to specify the lines that you want to apply the process to. The system shows only records where the billing start date is on or before the cutoff date you specify.
1. Select **View preview** to show the lines that you want to reverse stub.
1. To exclude a line from the process, mark it, and then select **Remove**.
1. Select **Process** to reverse stub the lines.

## Update completion date process

Use the **Update completion date** page to update the completion date for specific milestone items for multiple billing schedules or users. You can also update the completion percentage for items on milestone templates that use the **Percent completed** method.

1. On the **Update completion date** page, go to **Milestone processing**, and select **Update completion percentage**.
1. In the **Percentage amount** field, enter the total percentage that you completed.
1. Select the item number that is related to the milestone template.
1. On the **Records to include** FastTab, select **Filter** to select a specific **End user account**, **Billing schedule number**, or **Item numbers** value as a filter criterion.
1. Select **OK** to process the change. When the processing finishes, the system adds a new line to the milestone allocation. This line represents the percentage that you completed for the milestone template.

## Unbilled revenue mass processing

Use the **Unbilled revenue mass processing** page to create the unbilled revenue journal entry or stub the journal entry for one or more selected billing schedules or billing detail lines.

- **Create journal entry** – Create unbilled revenue journal entries for multiple billing schedule lines. Use the **Filter** button on the **Records to include** FastTab to select the range of records that appear in the list. The list shows only billing schedule lines that unbilled revenue journal entries aren't created for. The process creates the initial journal entries. For deferral items, the process also creates the deferral schedules.
- **Stub journal entry** – Mark the billing schedule lines that the unbilled journal entries are already created for. Use this option if the unbilled journal entry was already posted in another system. It marks the unbilled revenue journal as stubbed and doesn't post a transaction to the general ledger.
- **Reverse stub journal entry** – Reverse stub journal entries that are processed. If a mistake was made during the processing for **Stub journal entry**, this option clears the **Stubbed** checkbox for the billing schedule line.
- **Stub billing detail line** – Use this process when unbilled revenue was processed in an external system, and some of the billing detail lines are already billed. This process ensures that the correct amount appears in the unbilled revenue accounts.
- **Reverse stub billing detail line** – Reverse any **Stub billing detail line** actions.

Use the **Journal name** field to post **Create journal entry** to the general ledger.

> [!NOTE]
> The stub process doesn't post amounts to the general ledger. The **Journal name** field isn't available for all stub and reverse stub processes.

### Unbilled revenue stub example

You set up a billing schedule for one year, from October 2021 through September 2022. An external system already processes the unbilled revenue. You bill nine months of the billing schedule. The amount for each billing period is $250. At the beginning of the year, you post a total of $3,000 to unbilled revenue. After nine months, you bill $2,250, and $750 in unbilled revenue remains.

To set up the billing schedule where only three months' worth of unbilled revenue remains, follow these steps:

1. On **View billing detail**, create a billing schedule for the period from October 2021 through September 2022, item number S0001, and an amount of $250 per month.
1. Select **Create journal entry** for the billing schedule. The amount of $3,000 is posted to unbilled revenue.
1. Select **Stub billing detail line**, and specify a transaction date of June 2022 (nine months). The billing schedule lines don't appear in the preview. The lines that are affected are based on the transaction date.
4. Select **OK**.

The first nine months that you bill are stubbed.

[![View billing detail lines stub.](./media/01_View-billing-detail-stub.png)](./media/01_View-billing-detail-stub.png)

The $3,000 is reversed from unbilled revenue, and the $750 in unbilled revenue that remains is posted. To view the unbilled revenue postings, select **Unbilled revenue journal entry audit** on the **Renewals** tab of the line details page.

[![Unbilled revenue journal entry audit.](./media/02_Unbilled-rev-journal-audit.png)](./media/02_Unbilled-rev-journal-audit.png)

> [!NOTE]
> The unbilled revenue journal entry can be created for any renewal term, provided that all billing detail lines from the previous term have been billed. For example, a billing schedule line has a monthly billing frequency for a 12-month period, from January through December 2021. The line has three terms: the initial term, a second term (January through December 2022), and a third term (January through December 2023). After the invoice has been created for all billing detail lines from the initial 12 months in 2021, the journal entry for unbilled revenue can be created for the second term.
>
> For deferral items that use the unbilled revenue feature, the billing line and the discount lines are processed. For these items, the unbilled revenue journal entry and the deferral schedule for the billing line and the discount line are created.
>
> The journal entries that you create for non-deferrable items and deferrable items post a credit to different revenue accounts.
