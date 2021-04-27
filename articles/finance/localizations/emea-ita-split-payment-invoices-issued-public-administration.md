---
# required metadata

title: Split payment for invoices issued to the Public Administration
description: This topic provides information about the split payment accounting schema.
author: EvgenyPopovMBS
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: TaxBookSection, TaxGroup
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 261314
ms.search.region: Italy
# ms.search.industry: 
ms.author: epopov
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Split payment for invoices issued to the Public Administration

[!include [banner](../includes/banner.md)]

This topic provides information about the split payment accounting schema.

The split payment accounting schema is valid for the sale of goods and services rendered to the Public Administration. The split payment mechanism transfers the tax payment obligation to the Public Administration who are obligated to pay only the taxable base to the supplier. The VAT is credited to a specific reserved account. Companies that have relationships with the Public Administration should ensure that the relevant VAT is recorded in the register sales, without contributing to the periodic VAT payment.

## Prerequisites
The following table shows the prerequisites that must be in place before you start.

**Category**

**Prerequisite**

**Setup:** Sales tax posting

Create a new main account for VAT split payment, and then select **Sales tax** in the **Posting type** field. Create a posting group for VAT split payment, and then select the created ledger account in the **Sales tax payable**, **Sales tax receivable**, and **Settlement account** fields.

**Setup:** Sales tax

Create a **Sales tax group** for the Public Administration, and then select the **Split payment** option. Create a sales tax code for VAT split payment. Set the value applicable for the country/region, and then add the sales tax code in the **Sales tax group** and **Item Sales tax group**.

**Setup:** Accounts receivable

Set up the **Number sequence** for the **Split payment voucher** reference in Accounts payable parameters. Select the number sequence code to post the reversed VAT for invoices under the split payment mechanism for the **Split payment voucher** reference. Create a number sequence group for the Customer – Public Administration. On the **Number sequences** tab, select the line with the **Free text invoice voucher** reference, and then click the **Group** button. In the **Number sequence groups** page, create a new group, and then select a number sequence for the following references:

-   Free text invoice voucher
-   Free text credit note voucher
-   Customer invoice voucher
-   Sales credit note voucher

Set up a **Sales tax group** and **Number sequence group** for the Customers-Public Administration on the **All Customers** page.

**Setup:** VAT book and VAT book section

Create a new VAT book to register invoices to Public administration. Create a new section for the VAT book.

**Related transactions**

-   Register a sale to a customer with split payment settings.
-   Register a free text invoice for a customer with split payment settings.

## Working with the split payment invoices
When posting the invoice, such as sales order, free text invoice, or project invoice. with the Split payment sales tax group, the reversing sales tax transactions with relevant tax codes are posted to eliminate the tax being accrued. To reduce the customer balance, a customer transaction for the sales tax amount is created and automatically settled with the invoice while invoice posting. This reduces the customer balance by the VAT amount. **Note:** The tax transactions posted with the **Split payment **option selected are excluded from the sales tax payment process. eInvoices created using the Split payment process have an "S" in the tag &lt;EsigibilitaIVA&gt;.

### Booking example for sales invoice

The following table shows an example of general ledger transactions for two customer transactions сreated for a split payment invoice.

** **

**Account**

**Debit**

**Credit**

**Invoice accounting**

Customer\_Public Company

1220

Sales revenue

1000

VAT split payment

220

**VAT debt elimination**

Customer\_Public Company

220

VAT split payment

220







[!INCLUDE[footer-include](../../includes/footer-banner.md)]