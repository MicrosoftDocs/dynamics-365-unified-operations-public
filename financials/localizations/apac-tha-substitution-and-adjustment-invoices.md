---
# required metadata

title: Substitution/adjustment tax invoice for Thailand
description: The substitution/adjustment tax invoice feature enables tracking of printing of copies of tax invoices, as well as adjusting customer information in the tax invoice header.
author: EvgenyPopovMBS
ms.author: epopov
ms.date: 16.06.2017
ms.topic: article
# ms.prod: [If you use ms.prod, don't use ms.service]
ms.service: dynamics-ax-applications
# ms.technology: [Required for some ms.prod values; leave blank if ms.service is specified]

# optional metadata

manager: vastrup
ms.search.form: CustInvoiceJournal, CustInvoiceJourAdjustment, ProjInvoiceListPage, CustParameters
audience: Application User
# ms.devlang: [Development language for the topic]
ms.reviewer: shylaw
# ms.search.scope: [Which Operations client to show this topic as help for]
# ms.tgt_pltfrm: [Target platform (for example, ios or android).]
# ms.custom: [used by loc for topics migrated from the wiki]
# ms.assetid: [Go get from guidgenerator.com]
ms.search.region: Thailand
# ms.search.industry: [industry; e.g. retail]
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: Enterprise edition, July 2017 update
---

# Substitution/adjustment tax invoice for Thailand

The Substitution/adjustment tax invoice feature enables tracking of printing of copies of tax invoices for customers. Whenever a copy of an invoice needs to be printed, it is required to specify the reason for the substitution. A special remark is printed in the tax invoice copy that includes the reason of the substitution and the number of copies printed.

In addition, if the Adjustment option is used, it is also possible to adjust the customer information printed in the tax invoice, including the customer name, address, contact information, tax registration number, and branch number and name. The adjusted tax invoice gets a new invoice number, and references the original invoice.

## Setting up the Substitution/adjustment tax invoice functionality

The following common setup for Thailand is required to use the Substitution/adjustment tax invoice functionality:

1. Enable the parameters **Manage realized and unrealized VAT** and **Use tax branch** on the **General ledger parameters** page, fast-tab **Sales tax**;

2. Enable the financial dimension **Taxbranch** in the account structures for the legal entity. See [Plan your chart of accounts](../general-ledger/plan-chart-of-accounts.md) for more details on working with charts of accounts and account structures;

3. Create the **Taxbranch** financial dimension values on the **Tax branch** page;

4. Set **Tax type** field for applicable sales tax codes on the **Sales tax codes** page;

5. Set **Tax registration number** of the legal entity on the **Legal entities** page, fast-tab **Tax registration**;

6.  Map the registration type **THA** to the registration category **Enterprise ID (COID)** on the **Registration categories** page;

7. Set up the **Taxbranch** dimension for customers, vendors, projects, etc.

8. Set up customer and vendor addresses on the **Manage addresses** page:

    - Add registration IDs with the registration type **THA**;

    - Specify **Tax address type** and **Branch number** on the **Tax information** page;

9. Set up report formats for customer invoice, free text invoice and project invoice on the **Print management setup** page opened from the **Form setup** page in the **Accounts receivable** or **Project management and accounting** modules. Select **SalesInvoice.ReportTH**, **FreeTextInvoice.ReportTH** and **PSAProjInvoice.ReportTH** respectively.

10. Select the **Enable tax document's substitution/adjustment function** check-boxes for accounts receivable invoices and project invoices on the **Accounts receivable parameters** page,  tabs **Update** and **Project** respectively.

## Printing substitution invoices

If the substitution/adjustment tax invoice functionality is enabled, it is only possible to print a tax invoice original once. If you try to re-print it again, an error will be generated. Complete the following steps to re-print the tax invoice:

1. On the **Invoice journal** page, select the invoice to be re-printed.

2. Click **Adjustment** on the **Invoice** tab of the action pane.

3. On the **Adjust tax invoice** page, create a new record and set **Adjustment type** as **Substitution**. In the **Description** field, specify the reason for the substitution.

4. Return to the **Invoice journal** page and click **View > Substitution preview**. Confirm printing the substitution invoice.

The substitution tax invoice includes the same information as the original tax invoice. It also bears the "Substitution" mark. A remark is added to the bottom of the tax invoice that includes the reason for the substitution, the sequence number and the date of the substitution.

Note that you need to create a new substitution each time you need to re-print a tax invoice.

## Adjusting customer information in tax invoice

If the substitution/adjustment tax invoice functionality is enabled, it is possible to adjust the customer information printed in a tax invoice, and re-print the tax invoice. The following information can be adjusted:

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

The adjusted tax invoice gets a new tax invoice number and adjusted customer information. All other information is the same as in the original tax invoice. A remark is added to the bottom of the tax invoice that includes the reference to the original tax invoice, the reason for the adjustment, and the date of the adjustment.

You can adjust a tax invoice multiple time. A new tax invoice number is allocated for each adjustment, and the adjusted invoice references the previous adjustment or the original tax invoice, respectively.
