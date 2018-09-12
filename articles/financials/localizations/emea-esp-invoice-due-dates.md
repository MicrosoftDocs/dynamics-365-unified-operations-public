---
# required metadata

title: Invoice due dates for Spain
description: This topic provides information about due date for Spain.
author: ShylaThompson
manager: AnnBe
ms.date: 02/20/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Spain
# ms.search.industry: 
ms.author: anasyash
ms.dyn365.ops.version: Version 1611
ms.search.validFrom: 2016-11-30

---

# Calculation due date and generation of report on average period of payment for Spain
[!include[banner](../includes/banner.md)]

## Using delivery dates to calculate invoice due dates

Due dates for sales invoices, purchase invoices, and project invoices are calculated based on the delivery dates or receipt dates of items and services. Private companies and public administration companies can specify the maximum number of days, known as due date limits, within which invoice payments must be made. You can specify due date limits in the Due date limits form. If a due date limit is specified in the Terms of payment and Item groups forms, the calculated invoice due date is checked against the effective due date limit and is adjusted, if required, to comply with it. 
To use delivery dates and calculate invoice due dates for sales invoices and purchase invoices, in the Terms of payment form, on the Setup FastTab, select the Use the delivery date to calculate the payment due date check box. 
For sales invoices, the date that is specified in the Confirmed receipt date field on the Sales order header FastTab in the Sales order form is used as the delivery date. 
For purchase invoices, the delivery date is the date on which the packing slip is posted. If there are multiple packing slips available for a purchase invoice, the earliest packing slip posting date is used as the delivery date. If no packing slip is available, the delivery date that is specified in the Delivery date field on the Purchase order header FastTab in the Purchase order form is used as the delivery date for the invoice. 
> [!NOTE] 
> The Confirmed receipt date and Delivery date values for the sales order lines and purchase order lines are not used for due date calculation. 

Project sales order and project purchase order delivery dates are determined in the same way as those for regular sales invoices and purchase invoices. For the Hour, Expense, Item, Fee, and On-account transaction types, the transaction date is used as the delivery date. 

### Calculate invoice due dates for sales and purchase invoices based on delivery dates and due date limits

To use delivery dates to calculate invoice due dates, in the Terms of payment form, on the Setup tab, select the Use the delivery date to calculate the payment due date check box. 
In this example, if the Use the delivery date to calculate the payment due date check box is selected, the calculated payment due date for the selected terms of payment is displayed as follows. 

|Terms of payment       |Delivery date |Due date limit |Calculated invoice due date |Adjusted invoice due date |
|-----------------------|--------------|---------------|----------------------------|--------------------------|
|Current month + 15 days |June 9, 2018 |30 days |15 days after the end of June, which is July 15, 2018. However, July 15 – June 9 = 36 days, which is more than the actual due date limit of 30 days. |July 9, 2018 |

If there are multiple packing slips available for a purchase invoice, the earliest packing slip posting date is used as the delivery date. For example, if packing slips are posted on June 12, 2018, June 15, 2018, and June 18, 2018, for a purchase invoice, June 12, 2018, is used as the delivery date. 
If more than one due date limit applies to an invoice, the due date limit with the smallest number of days is used to calculate the invoice due date. For example, if due date limits are set up for 30 days and 45 days, the effective due date limit that is used to calculate the invoice due date is 30 days, regardless of where the due date limit is set up. 

## Set up due date limits to calculate invoice due dates
Use the Due date limits form to create due date limits, which are used to specify the maximum number of days within which you can make invoice payments.  

1. Click Accounts payable > Setup > Payment > Due date limits. 
–or– 
Click Accounts receivable > Setup > Payment > Due date limits. 
2. Click New to create a due date limit. 
3. In the Due date limit and Description fields, enter a name and a description for the due date limit. 
4. On the General tab, click Add to add a new line. 
5. In the Period interval field, select the period interval from the following options: 
    - Days – The due date limit is for the number of days that you indicate in the Number of units field. 
    - Months – The due date limit is for the number of months that you indicate in the Number of units field. 
6. In the Number of units field, enter the number of days or months for the due date limit. 

## Assign due date limits to terms of payment to calculate invoice due dates

When you create and post sales invoices or purchase invoices, the invoice due date is calculated based on the terms of payment that are specified for the invoices. The invoice due date that is calculated is verified against the due date limit. The invoice due date is then adjusted, if adjustment is required, to comply with the due date limit. If no due date limit is specified, the invoice due date that is calculated is used as the final invoice due date. 
Use the **Terms of payment** page to specify a due date limit, so that you can make sure that the invoice due date that is calculated is in the specified due date limit. 
1. Click Accounts payable > Setup > Payment > Terms of payment. 
–or– 
Click Accounts receivable > Setup > Payment > Terms of payment. 
2. Press CTRL+N to create terms of payment, or select a terms of payment line. 
3. On the Setup FastTab, select the Use the delivery date to calculate the payment due date check box to calculate the due date by applying terms of payment to the delivery date instead of the invoice date. 
4. In the Due date limit field, select a due date limit. 

## Calculate invoice due dates based on the payment schedule and the payment day

You can specify the payment schedule and the payment day for a customer invoice, a free text invoice, a vendor invoice, or a project invoice before you generate the invoice. Finance and Operations calculates the payment due dates of vendor invoices and project invoices based on the delivery dates of items and services. For customer invoices, Finance and Operations calculates the due dates based on the customer invoice receipt dates. 

You can specify the number of days in the grace period, within which an invoice payment must be made in the Due date limits page. You can select the Use the delivery date to calculate the payment due date check box in the Terms of payment form to use the delivery date to calculate the invoice due dates.  
You must specify a payment due date that comes before the due date limit for an invoice. You can set the payment schedule and the payment day for an invoice and manually calculate the invoice due date. If the date comes after the due date limit that is set in the Due date limits page, then you must correct the due date. 

## Generate the Information on average period of payments to suppliers report
You can generate the  Information on average period of payments to suppliers report, which is a statistics report that contains information about the invoices that are paid during a period that you specify. The report displays the amounts that are paid based on the payment terms, as well as the amounts that are paid outside of the payment terms. The amounts that are paid using payment journals and promissory notes are included in the report. 

To generate this report execute the following steps: 
1. Click General ledger > Inquiries and reports > Ledger reports > Information on average period of payments to suppliers. 
2. In the Parameters of the report in the Current period field group, select the starting and ending dates of the period that the report is generated for. 
3. In the Comparative period field group, select the starting and ending dates of the comparative period. For example, you can select the starting and ending dates of the previous fiscal period.
5. In the calculation field group select the calculation method (invoice date of due date)  
6. Under the Record to include FastTab specify the criteria to select the vendor transactions, such as invoices, payments, and promissory note journals (use Filter to specifying criteria).  
7. Click OK to generate the report. 
