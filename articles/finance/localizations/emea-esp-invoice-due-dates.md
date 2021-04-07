---
# required metadata

title: Calculate due dates and report on the average period of payments (Spain)
description: This topic provides information about due dates and the average period of payments for Spain.
author: ShylaThompson
ms.date: 05/15/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Spain
# ms.search.industry: 
ms.author: anasyash
ms.dyn365.ops.version: Version 1611
ms.search.validFrom: 2016-11-30

---

# Calculate due dates and report on the average period of payments (Spain)

[!include[banner](../includes/banner.md)]

## Using delivery dates to calculate invoice due dates

Due dates for sales invoices, purchase invoices, and project invoices are calculated based on the delivery dates or receipt dates of items and services. Private companies and public administration companies can specify the maximum number of days that invoice payments must be made within. This maximum number of days for invoice payment is known as a due date limit. You can specify due date limits on the **Due date limits** page.

If a due date limit is specified on the **Terms of payment** page and the **Item groups** page, the invoice due date that is calculated is verified against the effective due date limit. The invoice due date is then adjusted, if adjustment is required, so that it complies with the effective due date limit.

To use delivery dates and calculate invoice due dates for sales invoices and purchase invoices, set the **Use the delivery date to calculate the payment due date** option to **Yes** on the **Terms of payment** page, on the **Setup** FastTab, .

For sales invoices, the date that is specified in the **Confirmed receipt date** field on the **Sales order header** FastTab on the **Sales order** page is used as the delivery date.

For purchase invoices, the delivery date is the date when the packing slip is posted. If multiple packing slips are available for a purchase invoice, the earliest packing slip posting date is used as the delivery date. If no packing slip is available, the delivery date that is specified in the **Delivery date** field on the **Purchase order header** FastTab on the **Purchase order** page is used as the delivery date for the invoice.

> [!NOTE] 
> The **Confirmed receipt date** and **Delivery date** values for sales order lines and purchase order lines aren't used for due date calculations.

The delivery dates for project sales orders and project purchase orders are determined just like the delivery dates for regular sales invoices and purchase invoices. For the **Hour**, **Expense**, **Item**, **Fee**, and **On-account** transaction types, the transaction date is used as the delivery date.

### Calculate invoice due dates for sales and purchase invoices, based on delivery dates and due date limits

To use delivery dates to calculate invoice due dates, on the **Terms of payment** page, on the **Setup** tab, set the **Use the delivery date to calculate the payment due date** option to **Yes**.

The following example shows what the calculated payment due date for the selected terms of payment looks like, if the **Use the delivery date to calculate the payment due date** option is set to **Yes**.

| Terms of payment        | Delivery date | Due date limit | Calculated invoice due date |Adjusted invoice due date |
|-------------------------|---------------|----------------|-----------------------------|--------------------------|
| Current month + 15 days | June 9, 2018  | 30 days        | 15 days after the end of June, or July 15, 2018. However, the period from June 9 through July 15 has 36 days. Therefore, it exceeds the due date limit of 30 days. | July 9, 2018 |

If multiple packing slips are available for a purchase invoice, the earliest packing slip posting date is used as the delivery date. For example, packing slips for a purchase order are posted on June 12, 2018, June 15, 2018, and June 18, 2018. In this case, June 12, 2018, is used as the delivery date.

If more than one due date limit applies to an invoice, the due date limit that has the smallest number of days is used to calculate the invoice due date. For example, due date limits are set up for 30 days and 45 days. In this case, the effective due date limit that is used to calculate the invoice due date is 30 days, regardless of where the due date limit is set up.

## Set up due date limits to calculate invoice due dates
Use the **Due date limits** page to create due date limits that specify the maximum number of days that invoice payments must be made within.

1. Select **Accounts payable \> Payments setup \> Due date limits**.

    –or–

    Select **Accounts receivable \> Payments setup \> Due date limits**.

2. Select **New** to create a due date limit.
3. In the **Due date limit** field, enter a name for the new due date limit. In the **Description** field, enter a description.
4. On the **General** tab, click **Add** to add a line.
5. In the **Period interval** field, select the period interval type:

    - **Days** – The due date limit is for the number of days that you enter in the **Number of units** field.
    - **Months** – The due date limit is for the number of months that you enter in the **Number of units** field.

6. In the **Number of units** field, enter the number of days or months for the due date limit.

## Assign due date limits to terms of payment to calculate invoice due dates

When you create and post sales invoices or purchase invoices, the invoice due date is calculated based on the terms of payment that are specified for the invoices. The invoice due date that is calculated is verified against the due date limit. The invoice due date is then adjusted, if adjustment is required, so that it complies with the due date limit. If no due date limit is specified, the invoice due date that is calculated is used as the final invoice due date.

Use the **Terms of payment** page to specify a due date limit, so that you can make sure that the invoice due date that is calculated is in the specified due date limit.

1. Select **Accounts payable \> Payments setup \> Terms of payment**.

    –or– 

    Select **Accounts receivable \> Payments setup \> Terms of payment**.

2. Press the **New** button to create terms of payment, or select a terms of payment line.
3. On the **Setup** FastTab, set the **Use the delivery date to calculate the payment due date** option to **Yes** to calculate the due date by applying terms of payment to the delivery date instead of the invoice date.
4. In the **Due date limit** field, select a due date limit.

## Calculate invoice due dates based on the payment schedule and the payment day

You can specify the payment schedule and the payment day for a customer invoice, a free text invoice, a vendor invoice, or a project invoice before you generate the invoice. The payment due dates of vendor invoices and project invoices are calculated based on the delivery dates of items and services. For customer invoices, the due dates are calculated based on the customer invoice receipt dates.

On the **Due date limits** page, you can specify the number of days in the grace period that an invoice payment must be made within. You can set the **Use the delivery date to calculate the payment due date** option to **Yes** on the **Terms of payment** page to use the delivery date to calculate the invoice due dates.

You must specify a payment due date that is before the due date limit for an invoice. You can set the payment schedule and payment day for an invoice, and then manually calculate the invoice due date. If that due date is after the due date limit that is set on the **Due date limits** page, you must correct the due date.

## Generate the Information on average period of payments to suppliers report
You can generate the **Information on average period of payments to suppliers** report This statistical report contains information about the invoices that were paid during a period that you specify. The report shows the amounts that were paid based on the payment terms. It also shows the amounts that were paid outside the payment terms. The report includes the amounts that were paid by using payment journals and promissory notes.

To generate the report, follow these steps.

1. Select **General ledger \> Inquiries and reports \> Ledger reports \> Information on average period of payments to suppliers**.
2. In the **Current period** field group, select the start and end dates of the period that you're generating the report for.
3. In the **Comparative period** field group, select the start and end dates of the comparative period. For example, you can select the start and end dates of the previous fiscal period.
4. In the **Calculation** field group, in the **Calculation method** field select the calculation method (**Invoice date** or **Due date**).
5. On the **Record to include** FastTab, specify the criteria to use to select the vendor transactions, such as invoices, payments, and promissory note journals. (Use **Filter** to specify the criteria.)
6. Select **OK** to generate the report.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]