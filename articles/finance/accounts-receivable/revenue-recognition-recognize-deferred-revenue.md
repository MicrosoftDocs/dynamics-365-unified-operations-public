---
title: Recognize deferred revenue 
description: Learn about how to recognize revenue by using the Revenue recognition feature, including an overview on viewing schedule details. 
author: twheeloc
ms.author: twheeloc
ms.topic: article
ms.date: 05/26/2026
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.search.region: Global 
ms.search.validFrom: 2018-08-30
ms.search.form: Customer
ms.dyn365.ops.version: 8.0.4
---

# Recognize deferred revenue

[!include [banner](../includes/banner.md)]

> [!NOTE]
>This functionality was deprecated in January 2024. New users should use subscription billing.

This article describes the process of recognizing revenue in the revenue recognition schedule. After you post an invoice for a sales order, the system creates a revenue recognition schedule for each sales order line that has a revenue schedule. The revenue schedule on a line determines whether the line's revenue should be deferred.

## View revenue recognition schedule details

There are two ways to access the details of the revenue recognition schedule.

- You can open the revenue recognition schedule directly from an invoiced sales order. In this case, the system filters the information in the revenue schedule to show the details only for the selected sales order. This approach is useful when you're validating the schedule details for a sales order.
- You can open the revenue recognition schedule from the **Revenue recognition \> Periodic tasks** page. This approach is often used when revenue is recognized at the end of a period. When you first open the page, no information is shown. Use the filters above the grid to define criteria for the schedule details that should be shown. You can filter on the invoice dates by entering a date range, sales order, customer, project ID, or state.

:::image type="content" source="./media/revenue-recognition-schedule-page.png" alt-text="Screenshot of the Revenue schedules page." lightbox="./media/revenue-recognition-schedule-page.png":::

The **Financial dimension** FastTab, which appears below the grid, shows the financial dimensions of the sales order line. The system considers these dimensions during posting to deferred revenue. The system also considers these dimensions when the revenue is recognized. The dimension values that are used depend on the account structure that is assigned to the revenue and deferred revenue main accounts.

## Recognize revenue

You recognize revenue by running the **Create journal** process from the **Recognize revenue** page. You can open this page from either the sales order or **Periodic tasks**. If you run the process from the sales order, it recognizes revenue only for the selected sales order. Typically, you run the process from **Periodic tasks** instead, so that it recognizes revenue for all posted sales order invoices.

To define the criteria for selecting and posting revenue, select **Create journal** to open the **Create journal** dialog box.

:::image type="content" source="./media/revenue-recognition-create-journal.png" alt-text="Screenshot of the Create journal parameter options." lightbox="./media/revenue-recognition-create-journal.png":::

In the dialog box, use the options in the **Processing date** field group to define the posting date that is used when revenue is recognized. If you select **Selected date**, you can enter a posting date in the **Transaction date** field. If you select **Revenue schedule date**, the transaction date isn't used. Instead, the value of the **Recognize date** field on each line of the schedule is used as the posting date.

Next, in the **As of date** field, enter the "as-of" date for recognizing revenue. Any lines of the schedule where the recognize date is on or before the "as-of" date are recognized, provided that they aren't on hold.

After you finish defining the dates, select **OK** in the dialog box to create the journal. You receive an informational message that shows the number of transactions that are created and the journal where they're created. The journal isn't automatically posted. Therefore, the revenue recognition manager has time to validate which lines of the schedule are being recognized.

After the process runs, the lines on the schedule that are transferred to the journal are marked as **Processed**. The **Processed** flag indicates that the lines are transferred to the journal, but they can be posted or unposted. After the revenue recognition journal is posted, the **Processed** flag remains. If the revenue recognition journal is deleted, or if a line is deleted, the **Processed** flag is removed. In that way, the line can be recognized when the **Create journal** process runs again.

:::image type="content" source="./media/revenue-recognition-rev-recog-schedule-02.png" alt-text="Screenshot of the Revenue recognition schedules page." lightbox="./media/revenue-recognition-rev-recog-schedule-02.png":::

On the **Revenue recognition journal** page (**Revenue recognition \> Journal entries \> Revenue recognition journal**), open **Lines** to view the details of what is being recognized. A separate transaction is always created for each line of the schedule that's being recognized, even if all the lines are posted on the same date by using the same ledger accounts.

:::image type="content" source="./media/revenue-recognition-journal-voucher.png" alt-text="Screenshot of the Journal voucher page." lightbox="./media/revenue-recognition-journal-voucher.png":::

The **Account** column shows the deferred revenue ledger account. You can't edit this ledger account. This restriction helps guarantee that the correct deferred revenue ledger account is relieved. This ledger account isn't validated against the account structure, because it might have changed since posting to the referred revenue ledger account last occurred.

The **Offset account** column shows the revenue ledger account. By default, the revenue ledger account is taken from Inventory posting profiles, and the financial dimensions are taken from the sales order line. This ledger account is validated against the current account structure. However, it can be edited if the account structure has changed and requires additional financial dimensions.

The default amount is from the corresponding line of the schedule, and you can't change it.

BY default, if the sales order is a multicurrency sales order, the exchange rate is set to the exchange rate from the invoice. This behavior helps guarantee that the accounting currency and reporting currency amounts are fully relieved. Because of rounding, the exchange rate for the last line of the schedule might differ slightly from the rate on the invoice.

After the revenue recognition journal is posted, the voucher is entered on the schedule. If there's more than one voucher for the same line of the schedule, an asterisk (\*) appears on the line. To view the vouchers that were posted for that line, select **Voucher transactions**.

## Modify the revenue recognition schedule details

Most of the data in the revenue schedule details can't be edited. New lines can't be added to the schedule, and existing lines can't be deleted. The revenue schedule details for each sales order line must be maintained to help guarantee that, over time, an organization recognizes the same amount that was deferred.

### Edit schedule lines

You can make some edits on the lines of the schedule. You can change the following fields on the lines:

- **On hold** – This flag can be set or cleared before the line is processed. To clear the flag, select the row, and then select **Remove hold**. Revenue can't be recognized on lines that are on hold. Lines can automatically be put on hold if the revenue schedule is set up for automatic holds.

    :::image type="content" source="./media/revenue-recognition-rev-revenue-schedules.png" alt-text="Screenshot of the Revenue schedules page showing edit schedule lines." lightbox="./media/revenue-recognition-rev-revenue-schedules.png":::

- **Recognize date** – The recognize date can be changed before the line is processed. When the process that creates the journal for recognizing revenue is run, a date is entered in the **Recognize revenue as of date** field. That date is compared to the date in the **Recognize date** field to determine which lines should be recognized.
- **Amount to release** – The amount that will be released can be changed before the line is processed. You can decrease the amount of revenue that is recognized, but you can't increase it. This field lets an organization recognize part of the revenue on the recognize date. If the amount is changed, the amount in the **Remaining amount** field shows how much revenue must still be recognized.
- **Quantity to release** – If the revenue schedule is set up for one occurrence or one month, the **Quantity to release** field shows the quantity for the sales order line. This field can also be edited and provides another way to recognize part of the revenue. For example, if the quantity on the line is 5, you can override the quantity so that it's less than 5. The amount in the **Amount to release** field is updated proportionately.

### Update contract terms

The revenue schedule details are created based on the revenue schedule that is assigned to the sales order line when the invoice is posted. If the revenue schedule on the sales order line is incorrect, it can't be changed on the sales order after the sales order is invoiced. Instead, you must use the **Update contract terms** button to change the revenue schedule. The revenue schedule can be changed either before or after revenue has been recognized.

To change the schedule, select any schedule line for the item that you're changing. In the following illustration, the line for item S0008 that was posted by using a 12-month revenue schedule is selected. When you select **Update contract terms**, a dialog box shows the contract start and end dates, and the revenue schedule.

:::image type="content" source="./media/revenue-recognition-rev-revenue-schedule-update-cntrct-dates-schedule.png" alt-text="Screenshot of the contract start and end dates dialog box." lightbox="./media/revenue-recognition-rev-revenue-schedule-update-cntrct-dates-schedule.png":::

Change the contract start and end dates so that they reflect the correct date range. When you change the date range, the value in the **Number of occurrences** field must match a revenue schedule that has been defined in the system. In this example, because the contract was changed to a 24-month contract, a 24-month revenue schedule must be set up. Because the 24-month revenue schedule exists, it's entered by default, and the contract can be changed. If a revenue schedule that has a matching number of occurrences doesn't exist, the contract can't be changed. After you've finished updating the contract terms and revenue schedule as you require, select **OK** in the dialog box to save your changes.

:::image type="content" source="./media/revenue-recognition-rev-revenue-schedule-update-cntrct-dates-schedule-02.png" alt-text="Screenshot of the updated contract date range." lightbox="./media/revenue-recognition-rev-revenue-schedule-update-cntrct-dates-schedule-02.png":::

The contract changes have the following effects on the revenue schedule details:

- If no revenue is recognized for the product, the system removes all the previous schedule details and replaces them with the new revenue schedule details. For example, item S0008 originally had 12 lines in the schedule details. The system removes those 12 lines and replaces them with 24 lines, based on the new revenue schedule.
- If revenue is recognized for the product, some revenue was incorrectly recognized because recognition was based on the incorrect revenue schedule. You must reverse those lines and recognize them again, based on the new schedule. In this scenario, the system creates new revenue schedule lines that have negative amounts on the original recognize date. The system then creates new lines to recognize the amounts based on the new revenue schedule. For example, on August 8, 2019, you recognized revenue for $10.53. On September 8, 2019, you recognized revenue for $13.16. Therefore, two new lines are created on the same dates. One line is for -$10.53, and the other line is for -$13.16. 24 new lines are then created, and the total deferred revenue of $160.61 is allocated across them. You can post the reversing lines by running the **Create journal** process.

:::image type="content" source="./media/revenue-recognition-rev-recog-schedule-03.png" alt-text="Screenshot of the Revenue recognition schedule." lightbox="./media/revenue-recognition-rev-recog-schedule-03.png":::

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
