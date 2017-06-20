---
# required metadata

title: Substitution/adjustment tax invoices for Thailand
description: The substitution/adjustment tax invoice feature enables tracking of printing of copies of tax invoices, as well as adjusting customer information in the tax invoice header.
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
ms.search.scope: Operations, Core
ms.search.region: Thailand
# ms.search.industry: [industry; e.g. retail]
ms.author: epopov
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: Enterprise edition, July 2017 update
---

# Substitution/adjustment tax invoice for Thailand

You can keep track of how many times copies of tax invoices for customers is printed. Whenever a copy of a tax invoice needs to be printed, it is required to specify the reason for the reprinted invoice, which is a substitution for the original invoice. A special comment is printed in the tax invoice copy that includes the reason for the substitution and the number of copies that have been printed.

When you print a copy of the invoice, you can also select the Adjustment option which allows you to adjust the customer information printed in the tax invoice, including the customer name, address, contact information, tax registration number, branch number and branch name. The adjusted tax invoice gets a new tax invoice number and references the original tax invoice.

## Prerequisites

Before you can print a substituation or adjustment tax invoice for Thailand, you must complete the following setup: 

    - Enable the parameters **Manage realized and unrealized VAT** and **Use tax branch** on the **General ledger parameters** page, fast-tab **Sales tax**;

    - Enable the financial dimension **Taxbranch** in the account structures for the legal entity. See [Plan your chart of accounts](../general-ledger/plan-chart-of-accounts.md) for more details on working with charts of accounts and account structures;

    - Create the **Taxbranch** financial dimension values on the **Tax branch** page.

    - Set **Tax type** for applicable sales tax codes on the **Sales tax codes** page.

    - Set **Tax registration number** of the legal entity on the **Legal entities** page, fast-tab **Tax registration**.

    - Map the registration type **THA** to the registration category **Enterprise ID (COID)** on the **Registration categories** page.

    - Set up the **Taxbranch** dimension for customers, vendors, projects, etc.

    - Set up customer and vendor addresses on the **Manage addresses** page:

    - Add registration IDs with the registration type **THA**;

    - Specify **Tax address type** and **Branch number** on the **Tax information** page;

    - Set up report formats for customer invoice, free text invoice and project invoice on the **Print management setup** page opened from the **Form setup** page in the **Accounts receivable** or **Project management and accounting** modules. Select **SalesInvoice.ReportTH**, **FreeTextInvoice.ReportTH** and **PSAProjInvoice.ReportTH** respectively.

    - Select the **Enable tax document's substitution/adjustment function** check-boxes for accounts receivable invoices and project invoices on the **Accounts receivable parameters** page,  tabs **Update** and **Project** respectively.

## Printing substitution invoice

If the substitution/adjustment tax invoice functionality is enabled, it is only possible to print a tax invoice original once. If you try to re-print it again, you will get an error. Complete the following steps to re-print the tax invoice:

1. On the **Invoice journal** page, select the invoice to be re-printed.

2. Click **Adjustment** on the **Invoice** tab of the action pane.

3. On the **Adjust tax invoice** page, create a new record and set **Adjustment type** as **Substitution**. In the **Description** field, specify the reason for the substitution.

4. Return to the **Invoice journal** page and click **View** > **Substitution preview**. Confirm  that you want to print the substitution invoice.

The substitution tax invoice includes the same information as the original tax invoice. It also bears the "Substitution" mark. A remark is added to the bottom of the substitution tax invoice that includes the reason for the substitution, the sequence number and the date of the substitution.

> [!NOTE] You need to create a new substitution each time you need to re-print a tax invoice.

## Adjust customer information on a tax invoice

If the substitution/adjustment tax invoice functionality is enabled, you can adjust the customer information printed in a tax invoice, and re-print the tax invoice. You can adjust the following information:

- Customer name

- Address

- Telephone

- Fax

- Registration number

- Branch number

- Branch name

Complete the following steps to adjust the customer information and re-print the tax invoice:

1. On the **Invoice journal** page, select the invoice to be re-printed.

2. Click **Adjustment** on the **Invoice** tab of the action pane.

3. On the **Adjust tax invoice** page, create a new record and set **Adjustment type** as **Adjustment**. In the **Description** field, specify the reason for the adjustment. Adjust the customer information fields, as needed.

4. Return to the **Invoice journal** page and click **View > Adjustment preview**. Confirm printing the tax invoice.

The adjusted tax invoice gets a new tax invoice number and adjusted customer information. All other information is the same as in the original tax invoice. A remark is added to the bottom of the adjusted tax invoice that includes the reference to the original tax invoice, the reason for the adjustment, and the date of the adjustment.

You can adjust a tax invoice multiple time. A new tax invoice number is allocated for each adjustment, and the adjusted invoice references the previous adjustment or the original tax invoice, respectively.
