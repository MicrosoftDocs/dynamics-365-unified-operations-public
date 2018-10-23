---
# required metadata

title: Advance invoices for Retail for Eastern Europe
description: This topic describes how to set up advance notices for Retail for Eastern Europe. 
author: epopov
manager: annbe
ms.date: 10/23/2018
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
[!include [banner](../includes/banner.md)]

This article contains information about Eastern European localization specific for the Retail industry. 

For some European countries (Poland, Hungary, Czech Republic), when you receive a prepayment from a customer via Point of Sale (POS), the prepayment must be registered for tax purposes and you must generate and print an advance invoice document that includes the prepayment amount. In Poland, advance invoice transactions must be posted in general ledger.

When the invoice for the sales order is finally posted, the final document should include the advance invoice with any prepayments indicated. 

If you generate sales orders from the Accounts receivable module, you must generate this document manually using the following procedure: [Advance invoices for Eastern Europe](https://docs.microsoft.com/en-us/dynamics365/unified-operations/financials/localizations/emea-advance-invoice). 

If you generate sales orders via POS, the system generates and posts the advance invoices for you.

## Supported scenarios

The following scenarios are supported:
- Create and post an advance invoice.
- Modify a deposit amount. If the customer decides to increase a deposit amount, an additional advance invoice will be issued. For all other changes to the deposit amount, including editing a customer order, a credit note will be created for the previously generated advance invoice and a new advance invoice for the corrected amount will be generated and posted. 
- Cancel a sales order that has linked advance invoices.  In this case, a credit note will be created for the advance invoice.
- Post a sales order invoice that has linked advance invoices. The advance invoice, linked to a sales order, will be reversed for the amount of the sales invoice. The advance invoice transactions will be settled with advance invoice reversal transactions.

> [!NOTE]
> Printing advance invoices from POS is currently not supported.

## Set up advance invoices

### Enable the advance invoice creation functionality 
  
1. Go to **Retail > Headquarters setup > Parameters > Retail parameters**.
2. Click **Customer orders**.
3. On the FastTab **Order**,  set the **Create advance invoice for deposit** option to **Yes**.

### Define the parameters responsible for Advance invoice posting 

1. Go to **Accounts receivable > Setup > Accounts receivable parameters**.
2. Specify the **Posting profile**, **Sales tax group** and **Item sales tax group** on the **Advance invoice** FastTab on the **Updates** tab. If these fields are set correctly, the advance invoice will be posted. If these fields aren't specified, advance invoices will not post.

### Turn off the posting of the sales tax on prepayment journal voucher

The Sales tax on prepayment journal voucher must not be posted if advance invoice posting is set to **ON**. To verify that this requirement is met, complete the following steps.

1. On the **Accounts receivable parameters** page, click **Ledger and sales tax**. 
2. On the **Payment** FastTab, be sure that the following fields are blank or set to **NO**. 
   - **Sales tax on prepayment journal voucher**
   - **Posting profile with prepayment journal voucher**
   - **Tax group for prepayment**
   - **Item Sales tax group**.

## Printing advance invoices

It is possible to print advance invoices from POS on a Windows printer connected to the hardware station. There are two options how an advance invoice could be printed from POS:
- Print after the conclusion of actransaction on POS. 

  This happens automatically if an advance invoice was generated and a Windows printer was set up properly. In this case, only the last advance invoice linked with the customer order is printed.

- Re-print advance from the transaction journal. 

  Click **Show journal** to open the transactions journal, find a customer order, and then click **Print Advance invoice**. In this case, all advance invoices linked with the customer order will be printed.

## How to set up a Windows printer

Follow the steps below to enable printing documents from POS on a Windows printer connected to the hardware station: 

- Go to **Retail > Channel setup > POS setup > POS profiles > Hardware profiles**.
- Select a hardware profile related to the store where the printer is used.
- Update the settings either in the section **Printer** or **Printer 2**.

  - Select **Windows driver**.

  - Specify the name of the printer in the **Device name** field.

- Go to **Retail > Retail IT > Distribution schedule**.
- Select the **Job 1090** and click **Run now**.
