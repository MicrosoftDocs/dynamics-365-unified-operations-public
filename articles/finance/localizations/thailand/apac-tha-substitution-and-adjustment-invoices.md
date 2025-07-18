---
title: Substitution/adjustment tax invoices for Thailand
description: Learn how to work with substitution/adjustment tax invoices for Thailand in Microsoft Dynamics 365 Finance.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/21/2025
ms.reviewer: johnmichalak
ms.search.region: Thailand
ms.search.validFrom: 2017-06-30
ms.search.form: CustInvoiceJournal, CustInvoiceJourAdjustment, ProjInvoiceListPage, CustParameters
---

# Substitution/adjustment tax invoices for Thailand

[!include [banner](../../includes/banner.md)]

This article explains how to work with substitution/adjustment tax invoices for Thailand in Microsoft Dynamics 365 Finance.

You can track how many times copies of tax invoices for customers are printed. Whenever a copy of a tax invoice must be printed, the reason for the reprinted invoice must be specified. The reprinted invoice is a substitution for the original invoice. A special comment is printed on the copy of the tax invoice copy. This comment includes the reason for the substitution and the number of copies that have been printed.

When you print a copy of an invoice, you can also select the **Adjustment** option to adjust the customer information that is printed on the tax invoice. The information that you can adjust includes the customer name, address, contact information, tax registration number, branch number, and branch name. The adjusted tax invoice receives a new tax invoice number and references the original tax invoice.

## Prerequisites

Before you can print a substitution tax invoice or an adjustment tax invoice for Thailand, you must complete the following setup procedure. 

To fulfill the prerequisites, follow these steps.

1. In Dynamics 365 Finance, go to the **General ledger parameters** page.
1. On the **Sales tax** FastTab, enable the **Manage realized and unrealized VAT** and **Use tax branch** parameters.
1. In the account structures for the legal entity, enable the **Taxbranch** financial dimension. For more information about how to work with charts of accounts and account structures, see [Plan your chart of accounts](../../general-ledger/plan-chart-of-accounts.md).
1. On the **Tax branch** page, create the values for the **Taxbranch** financial dimension.
1. On the **Sales tax codes** page, set the **Tax type** value for applicable sales tax codes.
1. On the **Legal entities** page, on the **Tax registration** FastTab, set the **Tax registration number** value for the legal entity.
1. On the **Registration categories** page, map the **THA** registration type to the **Enterprise ID (COID)** registration category.
1. Set up the **Taxbranch** dimension for customers, vendors, projects, and so on.
1. On the **Manage addresses** page, set up customer and vendor addresses:
    1. Add registration IDs that have the **THA** registration type.
    1. On the **Tax information** page, specify the **Tax address type** and **Branch number** values.
1. On the **Print management setup** page that is opened from the **Form setup** page in either Accounts receivable or Project management and accounting, set up report formats for customer invoices, free text invoices, and project invoices. Select **SalesInvoice.ReportTH**, **FreeTextInvoice.ReportTH**, and **PSAProjInvoice.ReportTH**, respectively.
1. On the **Accounts receivable parameters** page, on the **Update** and **Project** tabs, select the **Enable tax document's substitution/adjustment function** checkbox for accounts receivable invoices and project invoices, respectively.

## Print a substitution invoice

If the substitution/adjustment tax invoice functionality is enabled, the original tax invoice can be printed only one time. If you try to reprint it, you receive an error. Follow these steps to reprint the tax invoice.

To print a substitution invoice, follow these steps.

1. In Dynamics 365 Finance, go to the **Invoice journal** page and select the invoice to reprint.
1. On the Action Pane, on the **Invoice** tab, select **Adjustment**.
1. On the **Adjust tax invoice** page, create a new record, and then set the **Adjustment type** field to **Substitution**.
1. In the **Description** field, enter the reason for the substitution.
1. Return to the **Invoice journal** page, and select **View** \> **Substitution preview**. Confirm that you want to print the substitution invoice.

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

 To adjust the customer information and reprint the tax invoice, follow these steps.

1. In Dynamics 365 Finance, go to the **Invoice journal** page and select the invoice to reprint.
1. On the Action Pane, on the **Invoice** tab, select **Adjustment**.
1. On the **Adjust tax invoice** page, create a new record, and set the **Adjustment type** field to **Adjustment**. In the **Description** field, enter the reason for the adjustment.
1. Adjust the customer information fields as you require.
1. Return to the **Invoice journal** page, and select **View** \> **Adjustment preview**. Confirm that you want to print the tax invoice.

The adjusted tax invoice includes a new tax invoice number and adjusted customer information. All other information is the same as the information on the original tax invoice. A comment is added to the bottom of the adjusted tax invoice. This comment includes the reference to the original tax invoice, the reason for the adjustment, and the date of the adjustment.

You can adjust a tax invoice multiple times. For each adjustment, a new tax invoice number is allocated, and the adjusted invoice references the previous adjustment or the original tax invoice.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
