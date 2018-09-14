---
# required metadata

title: Advance invoices for Retail for Eastern Europe
description: 
author:  
manager: epopov
ms.date: 10/01/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Retail, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Eastern Europe
ms.search.industry: Retail
ms.author: v-kikozl
ms.search.validFrom: 2018-10-01
ms.dyn365.ops.version: 8.1
---
# Advance invoices for Retail for Eastern Europe


*Applies To: Dynamics 365 for Finance and Operations*

When company receives a prepayment from customer via POS in some European countries (Poland, Hungary, Czech Republic) this prepayment must be registered for tax purposes and special document Advance invoice with prepayment amount must be created and printed. Additionally, in Poland Advance invoice transactions must be posted in general ledger.

Then invoice for the sales order is finally posted, the final document should include advance invoice with prepayments. For sales orders in the Accounts receivable module this functionality works in manual way, for more details go to [Advance invoices for Eastern Europe](https://docs.microsoft.com/en-us/dynamics365/unified-operations/financials/localizations/emea-advance-invoice). 
The same functionality is used for Sales orders and payments registered via POS, but in this case the system generates and posts advance invoices automatically.

## Supported scenarios

This functionality supports the following scenarios:
- Advance invoice creation and posting

- Changing deposit amount
  
  If customer decided to increase a deposit amount, additional Advance invoice will be issued. For all other changes of deposit amount including editing a customer order, the credit note will be created for previous Advance invoice and new Advance invoice for corrected amount will be posted. 

- Cancelation Sales order with linked advance invoices

  In this case a credit note will be created for Advance invoice.

- Invoice posting for a Sales order which has linked advance invoice
  
  The advance invoice, linked to Sales order, will be reversed for the amount of Sales invoice. The Advance invoice transactions will be settled with advance invoice reversal transactions.

  Note: Printing advance invoices from POS is not currently supported.

## Set up Advance invoices

1. Activate advance invoice creation. Open tab **_Customer orders_** in **_Retail > Headquarters setup > Parameters > Retail parameters_** form, then on FastTab **_Order_** toggle **Create advance invoice for deposit** field to Yes.

2. Define the parameters responsible for Advance invoice posting in **_Accounts receivable > Setup > Accounts receivable parameters_** form.
   - If **Posting profile**, **Sales tax group** and **Item sales tax group** are specified in FastTab **_Advance invoice_** on the tab **_Updates_**, the Advance invoice will be posted. If these parameters aren't specified there will be no posting for Advance invoice. 

   - Sales tax on prepayment journal voucher must not be posted if Advance invoice posting is ON. This requirement regulated by setup - following fields in FastTab **_Payment_** on tab **_Ledger and sales tax_**  of the form **_Accounts receivable parameters_**  should be blank or set to No: **Sales tax on prepayment journal voucher**, **Posting profile with prepayment journal voucher**,  **Tax group for prepayment**, **Item Sales tax group**.
