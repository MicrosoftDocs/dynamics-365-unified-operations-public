---
# required metadata

title: Tax reimbursement documents for Hungary
description: This topic provides information about setting up and creating tax reimbursement documents.
author: ShylaThompson
manager: AnnBe
ms.date: 03/09/2017
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
ms.search.region: Austria
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Tax reimbursement documents for Hungary

[!include[banner](../includes/banner.md)]

## Set up parameters for tax reimbursement documents

A customer might be a person who resides in a country/region that is not a member of the European Union (EU). A customer of this kind might request reimbursement of value-added tax (VAT) that was paid on purchases in Hungary. The customer might also ask you to provide documentation for the amount of VAT that he or she paid to you. You can create a tax reimbursement document from the customer invoice. 

### Set up a default exchange rate
Use this procedure to set up an exchange rate that is automatically selected in tax reimbursement documents. 
1. Click Accounts receivable > Setup > Accounts receivable parameters. 
2. In the Accounts receivable parameters form, in the left pane, click Updates. 
3. In the Other FastTab, in the Tax reimbursement slip field, select the type of exchange rate to use by default for tax reimbursement documents. 

### Set up a number sequence
Use this procedure to set up a number sequence that is automatically assigned to tax reimbursement documents. 
1. Click Accounts receivable > Setup > Accounts receivable parameters. 
2. In the Accounts receivable parameters form, in the left pane, click Number sequences. 
3. In the Reference field, select Tax reimbursement document. 
4. In the Number sequence code field, select a number sequence for tax reimbursement documents. 
5. Complete the remaining optional fields. 

## Create and print a tax reimbursement document

You can provide a tax reimbursement document to a customer who has paid value-added tax (VAT) to you. Customers can use the tax reimbursement document to claim a VAT reimbursement from authorities. 

The tax reimbursement document is available only if the customer is set up as a person on the **Customers** page. On the **Customers** page, on the **General** FastTab, confirm that the **Record typ**e field is set to **Person**. 

### Set up print management for a tax reimbursement document

1. Click Accounts receivable > Setup > Forms > Form setup. 
2. In the Form setup form, in the General area, click Print management. 
3. In the Print management setup form, in the Module - accounts receivable section, click Tax reimbursement slip. 
4. In the Module - inventory management section, in the Picking list group, select either Original or Copy. 
5. In the right pane, enter information about what to print. 
6. Optional: In the Footer text field, enter text to print at the bottom of the tax reimbursement document. 

### Select invoice lines for a tax reimbursement document

1. Click Accounts receivable > Inquiries and reports > Journals > Invoice journal. 
2. In the Invoice journal form, on the Overview tab, select the customer invoice for which the customer is requesting tax reimbursement. 
3. Select the Tax reimbursement check box for the selected invoice. 
4. By default, on the Lines tab, in the Tax reimbursement lines field, all invoice lines are selected. Clear the check boxes for the invoice lines to exclude from the tax reimbursement document. 
5. On the Overview tab, on the menu bar, click Tax reimbursement > Original preview to view the document before you print it. 
6. Optional: Click Tax reimbursement > Use print management to modify the print settings, such as the number of copies to print. 
7. In the View original form, review the information, and then Print the tax reimbursement document. 

When you print a tax reimbursement document, the document number that is assigned to the document is displayed in the Invoice journal form, in the Tax reimbursement document field. The Tax reimbursement check box is unavailable for the lines that you included in the tax reimbursement document. 

### Settle a tax reimbursement

When your organization reimburses a customer for VAT, you must indicate the reimbursement in the invoice journal to prevent a duplicate reimbursement. Use the following procedure to settle invoice lines for which a customer received a VAT reimbursement. 
1. Click Accounts receivable > Inquiries and reports > Journals > Invoice journal. 
2. In the Invoice journal form, on the Overview tab, select the customer invoice for which the customer received a VAT reimbursement. 
3. On the Overview tab, on the menu bar, click Tax reimbursement > VAT settled. 

The Vat settled check box is selected for the invoice and the invoice lines. 
