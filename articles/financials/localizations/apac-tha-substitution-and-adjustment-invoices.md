---
# required metadata

title: Substitution/adjustment tax invoices for Thailand
description: This topic provides information about the substitution/adjustment tax invoice feature. This feature lets you track the printing of copies of tax invoices. You can also track adjustments that are made to customer information in the tax invoice header.
author: EvgenyPopovMBS
ms.date: 06/16/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

manager: vastrup
ms.search.form: CustInvoiceJournal, CustInvoiceJourAdjustment, ProjInvoiceListPage, CustParameters
audience: Application User
ms.reviewer: shylaw
ms.search.scope: Core, Operations, UnifiedOperations
ms.search.region: Thailand
# ms.search.industry: [industry; e.g. retail]
ms.author: epopov
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: July 2017 update
---

# Substitution/adjustment tax invoice for Thailand

You can track how many times copies of tax invoices for customers are printed. Whenever a copy of a tax invoice must be printed, the reason for the reprinted invoice must be specified. The reprinted invoice is a substitution for the original invoice. A special comment is printed on the copy of the tax invoice copy. This comment includes the reason for the substitution and the number of copies that have been printed.

When you print a copy of an invoice, you can also select the **Adjustment** option to adjust the customer information that is printed on the tax invoice. The information that you can adjust includes the customer name, address, contact information, tax registration number, branch number, and branch name. The adjusted tax invoice receives a new tax invoice number and references the original tax invoice.

## Prerequisites

Before you can print a substitution tax invoice or an adjustment tax invoice for Thailand, you must complete the following setup. 

- On the **General ledger parameters** page, on the **Sales tax** FastTab, enable the **Manage realized and unrealized VAT** and **Use tax branch** parameters.
- In the account structures for the legal entity, enable the **Taxbranch** financial dimension. For more information about how to work with charts of accounts and account structures, see [Plan your chart of accounts](../general-ledger/plan-chart-of-accounts.md).
- On the **Tax branch** page, create the values for the **Taxbranch** financial dimension.
- On the **Sales tax codes** page, set the **Tax type** value for applicable sales tax codes.
- On the **Legal entities** page, on the **Tax registration** FastTab, set the **Tax registration number** value for the legal entity.
- On the **Registration categories** page, map the **THA** registration type to the **Enterprise ID (COID)** registration category.
- Set up the **Taxbranch** dimension for customers, vendors, projects, and so on.
- On the **Manage addresses** page, set up customer and vendor addresses:

    - Add registration IDs that have the **THA** registration type.
    - On the **Tax information** page, specify the **Tax address type** and **Branch number** values.

- On the **Print management setup** page that is opened from the **Form setup** page in either Accounts receivable or Project management and accounting, set up report formats for customer invoices, free text invoices, and project invoices. Select **SalesInvoice.ReportTH**, **FreeTextInvoice.ReportTH**, and **PSAProjInvoice.ReportTH**, respectively.
- On the **Accounts receivable parameters** page, on the **Update** and **Project** tabs, select the **Enable tax document's substitution/adjustment function** check box for accounts receivable invoices and project invoices, respectively.

## Print a substitution invoice

If the substitution/adjustment tax invoice functionality is enabled, the original tax invoice can be printed only one time. If you try to reprint it, you receive an error. Follow these steps to reprint the tax invoice.

1. On the **Invoice journal** page, select the invoice to reprint.
2. On the Action Pane, on the **Invoice** tab, click **Adjustment**.
3. On the **Adjust tax invoice** page, create a new record, and set the **Adjustment type** field to **Substitution**. In the **Description** field, enter the reason for the substitution.
4. Return to the **Invoice journal** page, and click **View** > **Substitution preview**. Confirm that you want to print the substitution invoice.

The substitution tax invoice includes the same information as the original tax invoice, but it has a "Substitution" mark. Additionally, a comment is added to the bottom of the substitution tax invoice. This comment includes the reason for the substitution, the sequence number, and the date of the substitution.

> [!NOTE]
> You must create a new substitution every time that you reprint a tax invoice.

## Adjust customer information on a tax invoice

If the substitution/adjustment tax invoice functionality is enabled, you can adjust the customer information that is printed on a tax invoice and then reprint the tax invoice. You can adjust the following information:

- Customer name
- Address
- Telephone
- Fax
- Registration number
- Branch number
- Branch name

Follow these steps to adjust the customer information and reprint the tax invoice.

1. On the **Invoice journal** page, select the invoice to reprint.
2. On the Action Pane, on the **Invoice** tab, click **Adjustment**.
3. On the **Adjust tax invoice** page, create a new record, and set the **Adjustment type** field to **Adjustment**. In the **Description** field, enter the reason for the adjustment.
4. Adjust the customer information fields as you require.
5. Return to the **Invoice journal** page, and click **View** > **Adjustment preview**. Confirm that you want to print the tax invoice.

The adjusted tax invoice includes a new tax invoice number and adjusted customer information. All other information is the same as the information on the original tax invoice. A comment is added to the bottom of the adjusted tax invoice. This comment includes the reference to the original tax invoice, the reason for the adjustment, and the date of the adjustment.

You can adjust a tax invoice multiple times. For each adjustment, a new tax invoice number is allocated, and the adjusted invoice references the previous adjustment or the original tax invoice.
