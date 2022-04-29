---
# required metadata

title: Periodic tasks in Recurring contract billing
description: This topic describes the periodic tasks in Recurring contract billing
author: JodiChristiansen
ms.date: 04/29/2022
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
# Periodic tasks

This topic describes the periodic tasks available in Recurring contract billing. 

## Generate invoice

Use the **Generate invoice** page to create mass monthly recurring invoices with the information that you set up on the **All billing schedules** and the **View billing detail** pages. When an invoice is created, the sales order processing line item description is updated with the item description and the billing start date and end dates for the schedule line that is invoiced.

## Generate invoice batch processing

Use the **Generate invoice batch processing** page to create recurring invoices in a recurring batch process. The same parameters are available as on the **Generate invoice page** but can be saved in a batch process to run again. 

## Price update

Use the **Price update** utility to update the prices of several items on multiple billing schedules in a single action. The prices can be updated based on a specified percent or a specified amount. The lines list shows the current unit prices of the items only. It doesn't show the prices after the price update. 

The price update feature can be used for line items: 
- If the sales order for a specific year has already been created, meaning the item has been billed, the price of the items isn't affected. 
- Items that have a status of **Active** or **On hold** can use the price update utility. For items on hold, the **Adjust schedule** option must have been set to **No** when the hold was placed. 
- The price update feature can't be used for line items that are usage items or items that use escalation, milestone billing, or revenue splitting. 

### Price update example

A billing schedule is created and a renewal item is added. The unit price is $750.
- The first year of the item is paid on December 15, 2021. 
- The billing schedule is created for the period January 1, 2022 to December 31, 2022. 

At renewal time, **Generate invoice** creates the sales order for the year 2022. After the price update utility is run, the price is updated from $750 to $800. 

The sales order and billing schedule for 2022 aren't affected and the unit price remains at $750 because the billing schedule for 2022 has already been billed. The billing schedule line and line detail for 2023 are updated to $800 since it hasn't been billed yet.

### Updating prices - Flat pricing method

When updating prices for items that use the flat pricing method, you can specify a percent or amount to increase the price. 

To run the price update utility for items that use the flat pricing method:
1. On the **Price update** utility page, select the **Flat** pricing method. 
2. Select the **Increase method** used to update the price of the items, specify the **Percent** or **Amount**.
3. On the **Records to include** FastTab, use the **Filter** button to add data filters. 
4. Select **View preview** to see the range of records.
5. If there are lines that you don't want to process, mark them and select **Remove**. 
6. Select **OK**.

### Updating prices - Standard pricing method

If the price of an item has changed on the item record, the item price can be updated for all billing schedule lines if the item uses the standard pricing method.

1. On the **Price update** utility page, select the **Standard** pricing method. 
2. On the **Records to include** FastTab, use the **Filter** button to add data filters. 
3. Select **View preview** to see the range of records.
4. If there are lines that you don't want to process, mark them and select **Remove**. 
5. Select **OK**.

## Mass hold processing

Use the **Mass hold** page to apply hold options to several billing schedules at the same time. If you want to put one billing schedule on hold or a single billing schedule line on hold go to the **All billing schedules** page and use **Place hold**. To remove a hold, use the **Remove hold** page. 

### Put billing schedules on hold
To put a bill on several billing schedules:
1. On the **Mass hold** page, set **Process option** to **Apply hold**. 
2. Select the **Reason code**. 
3. When **Adjust schedule** is set to **Yes**, specify the **Hold date**. Any billing schedule lines after the hold date are removed. 
4. When **Adjust schedule** is set to **No**, the billing schedule lines aren't changed, only the status is changed to **On hold**.
5. In the **Records to include** FastTab, use the **Filter** button to add data filters. 
6. Select **View preview** to see the range of records. 
7. If there are lines that you don't want to process, mark them and select **Remove**. 
8. Select **OK**.

When you return to the list of billing schedules, the status of the billing schedules has changed to **On hold**. 

### Remove a hold from several billing schedules
1. On the **Mass hold** page, set the **Process option** to **Remove hold**.
2. Enter a **Reason code**.
3. Select the **Remove date**.
4. If needed, select the **Resumption date** and the **Deferral date**. The deferral date is added to all lines that are deferrable.
5. On the **Records to include** FastTab, use the **Filter** button to add data filters. 
6. Select **View preview** to see the range of records. 
7. If there are lines that you don't want to process, mark them and select **Remove**. 
8. Select **OK**.

> [Note]
> To remove a hold, you must set up the **Remove hold user group override** on **Recurring contract billing parameters** page. 

For example, a billing line has a start date of February 1, 2022 and an end date of February 28, 2022 with a billing amount of $200. The **Hold date** is February 10, 2022 which means the February period is adjusted to exclude any date after February 10. The new period is February 1, 2022 - February 9, 2022 with an amount of $64.29 (daily proration). All billing schedule lines after and including February 10, 2022 are removed. If the **Remove hold** process is completed with a **Remove date** of February 10, 2022, there will be two billing periods. The first billing period is Feb 1-Feb 9 for $64.29. The second is Feb 10-Feb 28 for $135.71.

## Mass termination processing

Use the **Mass termination** page to terminate currently displayed billing schedule lines using a specified termination date. 

If you are using Revenue and expense deferrals, billing schedules that have **Termination date** set to **Adjust schedule** on the **All billing schedules** page are eligible for a refund. 

Billing schedules that use the multiple element allocation functionality in Multiple element revenue allocation don't appear on this page. You can still terminate an individual billing schedule using the termination functionality on the billing schedule. 

> [Note]
> Billing schedule lines that are currently included in a **Generate invoice** batch aren't available for this process. 

See Terminate billing schedules for specific information on each field and the process. 

## Mass archive process

Use the **Mass archive** page to archive multiple billing schedules. Only terminated billing schedules can be archived. 
After a billing schedule has been archived, the following occurs: 
- The status is changed to **Archived**.
- The billing schedules are permanently locked.
- The billing schedule lines aren't available on inquiry pages.

> [Note]
> Archiving a billing schedule is a permanent action and cannot be reversed. 

To archive billing schedules, follow these steps:
1. On the **Mass archive** page, specify the **Billing end date**. To see all terminated billing schedules, leave this date empty.
2. Expand the **Records to include** FastTab and use the **Filter** button to restrict the records that appear after selecting **View preview**.
3. Mark any records you don't want to archive and select **Remove**. 
4. Select **OK** to archive the records on the page.

## Mass stubbing process

Use the **Mass stubbing** page to mark all selected billing schedule lines as billed (stub) or unbilled (reverse stub). Stubbing or reverse stubbing is most often performed on imported billing schedule lines that were previously billed in another system. Stubbed billing schedule lines will show as stubbed and will not create an invoice for the customer. 

### Stub records
1. On the **Mass stubbing** page, in the **Process options** field, select **Stub**.
2. Specify the **Cutoff date**, which displays the lines to which you want to apply the process. Only records that have a billing start date that is earlier than or the same as the cutoff date specified will show.
3. Select **View preview** to display the lines you want to stub. 
4. Mark a line and select **Remove** button to exclude that line from the process. 
5. Select **Process** to stub the lines. 

### Reverse stub records
1. On the **Mass stubbing** page, in **Process options** field, select **Reverse stub**.
2. Specify the **Cutoff date**, which displays the lines to which you want to apply the process. Only records that have a billing start date that is earlier than or the same as the cutoff date specified will show.
3. Select **View preview** to display the lines you want to reverse stub. 
4. Mark a line and select **Remove** button to exclude that line from the process. 
5. Select **Process** to reverse stub the lines. 

## Update completion date process

Use the **Update completion date** page to update the completion date for specific milestone items for multiple billing schedules or end users. 
You can also update the completion percentage for items on milestone templates that use the **Percent completed** method. 
1. Go to **Milestone processing**, select **Update completion percentage**. 
2. Enter the total percentage complete in the **Percentage amount** field. 
3. Select the item number that relates to the milestone template. 
4. Under **Records to include** select the **Filter** button to select a specific **End user account**, **Billing schedule number** or **Item numbers** in the **Criteria**. 
5. Click **Ok** to process the change. When complete, a new line will be added to the milestone allocation representing the percentage complete for the milestone template. 

## Unbilled revenue mass processing

Use the **Unbilled revenue mass processing** page to create the unbilled revenue journal entry or stub the journal entry for one or more selected billing schedules or billing detail lines. 

1. **Create journal entry** - This will create unbilled revenue journal entries for multiple billing schedule lines. Use **Filter** button under **Records to include** to select the range of records to appear in the list. Only billing schedule lines where the unbilled revenue journal entries haven't been created appear in the list. The initial journal entries are created. For deferral items, the deferral schedules are also created.

2. **Stub journal entry** - This marks the billing schedule lines that have the unbilled journal entries already created. This option is used if the unbilled journal entry was already posted in another system. This marks the unbilled revenue journal as stubbed and doesn't post a transaction to the General ledger. 

3. **Reverse stub journal entry** - This will reverse stub journal entries that have been processed. If a mistake was made when processing **Stub journal entry**, this will clear the **Stubbed** checkbox for the billing schedule line. 

4. **Stub billing detail line** - Use this process when Unbilled revenue was processed in an external system and some of the billing detail lines have already been billed. This will make sure the correct amount is in the unbilled revenue accounts. 

5. **Reverse stub billing detail line** - This process will reverse any Stub billing detail line actions. 
The **Journal name** is used to post the **Create journal entry** to the General ledger. 

>[!Note]
>The stub process doesn't post amounts to the General ledger. The **Journal name** field isn't available for all stub and reverse stub processes. 

### Unbilled revenue stub example

A billing schedule is set up for one year, October 2021 to September 2022. The unbilled revenue was already processed in an external system. Nine months of the billing schedule have already been billed. Each billing period is $250. The total amount posted to Unbilled revenue would be $3000 at the beginning of the year. After nine months, $750 would be left in unbilled revenue and $2250 has already been billed. 

To set up the billing schedule with only three months left in unbilled revenue, follow these steps:
1. Create a billing schedule October 2021 to September 2022, Item S0001 for $250 per month in **View billing detail**. 
2. Use **Create journal entry** for the billing schedule. This will post $3000 to unbilled revenue. 
3. Use **Stub billing detail line** with a transaction date of June 2022 (9 months). The billing schedule lines won't show in preview, the lines affected are based on the transaction date. Select **OK**.
4. This will stub the first nine months that have been billed. 

[![View billing detail lines stub.](./media/01_View-billing-detail-stub.png)](./media/01_View-billing-detail-stub.png)

6. This will reverse the $3000 from unbilled revenue and post the $750 that is left for unbilled revenue. The unbilled revenue postings can be seen on the **Line Details > Renewals tab > Unbilled revenue journal entry audit** button. 

[![Unbilled revenue journal entry audit.](./media/02_Unbilled-rev-journal-audit.png)](./media/02_Unbilled-rev-journal-audit.png)

> [!Note]
> The unbilled revenue journal entry can be created for any renewal term, provided all billing detail lines from the previous term have been billed. For example, a billing schedule line has a monthly billing frequency for a 12-month period, January to December 2021. The line has three terms: the initial term, a second term (January to December 2022), and a third term (January to December 2023). After the invoice has been created for all billing detail lines from the initial 12 months in 2021, the journal entry for unbilled revenue can be created for the second term. 
For deferral items that use the unbilled revenue feature, the billing line and the discount lines are processed. For these items, the unbilled revenue journal entry and the deferral schedule for the billing line and the discount line are created. 
The journal entries that are created for non-deferrable items and the deferrable items post a credit to different revenue accounts. 
