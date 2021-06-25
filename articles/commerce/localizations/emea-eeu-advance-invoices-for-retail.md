---
# required metadata

title: Advance invoices for Commerce for Eastern Europe
description: This topic explains how to set up advance notices for Commerce for Eastern Europe. 
author: epopov
ms.date: 10/23/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Czech Republic, Estonia, Hungary, Latvia, Lithuania, Poland, Russia 
ms.search.industry: Retail
ms.author: epopov
ms.search.validFrom: 2018-10-01
ms.dyn365.ops.version: 8.1

---

# Advance invoices for Commerce for Eastern Europe

[!include [banner](../includes/banner.md)]

The information in this topic applies to the Eastern European localization and is specific to the commerce industry.

For Poland, Hungary, and Czech Republic, when a prepayment is received from a customer via Point of Sale (POS), the prepayment must be registered for tax purposes, and it's required to generate and print an advance invoice document that includes the prepayment amount. Additionally, for Poland, advance invoice transactions must be posted in the general ledger.

When the invoice for the sales order is finally posted, the final document should include the advance invoice, and any prepayments should be indicated.

If you generate sales orders from Accounts receivable, you must manually generate advance invoices by using the procedure in [Advance invoices for Eastern Europe](/dynamics365/unified-operations/financials/localizations/emea-advance-invoice). If you generate sales orders via POS, the system generates and posts the advance invoices for you.

## Supported scenarios

The following scenarios are supported:

- Create and post an advance invoice.
- Modify a deposit amount. If a customer decides to increase the amount of a deposit, an additional advance invoice is issued. For all other changes to the deposit amount (for example, if a customer order is edited), a credit note is created for the advance invoice that was previously generated, and a new advance invoice is generated and posted for the corrected amount.
- Cancel a sales order that has linked advance invoices. In this case, a credit note is created for the advance invoice.
- Post a sales order invoice that has linked advance invoices. The advance invoice that is linked to a sales order is reversed for the amount of the sales invoice. The advance invoice transactions are settled with advance invoice reversal transactions.

## Set up advance invoices

### Turn on the functionality for creating advance invoices

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters**.
2. On the **Customer orders** tab, on the **Order** FastTab, set the **Create advance invoice for deposit** option to **Yes**.

### Define the parameters for posting advance invoices

1. Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
2. On the **Updates** tab, on the **Advance invoice** FastTab, set the **Posting profile**, **Sales tax group**, and **Item sales tax group** fields. If these fields are set correctly, the advance invoice will be posted. If these fields aren't set, advance invoices won't be posted.

### Turn off posting of the Sales tax on prepayment journal voucher

The Sales tax on prepayment journal voucher must not be posted if advance invoice posting is turned on. To verify that this requirement is met, follow these steps.

1. Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
2. On the **Ledger and sales tax** tab, on the **Payment** FastTab, make sure that the following fields are blank or set to **No**:

    - Sales tax on prepayment journal voucher
    - Posting profile with prepayment journal voucher
    - Tax group for prepayment
    - Item Sales tax group

## Print advance invoices

You can print advance invoices from POS on a Microsoft Windows printer that is connected to the hardware station. There are two options for printing an advance invoice from POS:

- **Print an advance invoice after a transaction is concluded in POS.** This option occurs automatically if an advance invoice was generated and a Windows printer was correctly set up. In this case, only the last advance invoice that is linked to the customer order is printed.
- **Reprint an advance invoice from the transaction journal.** Select **Show journal** to open the transactions journal, find the customer order, and then select **Print Advance invoice**. In this case, all advance invoices that are linked to the customer order are printed.

### Set up a Windows printer

Follow these steps to enable documents to be printed from POS on a Windows printer that is connected to the hardware station.

1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Hardware profiles**.
2. Select a hardware profile that is related to the store where the printer is used.
3. In either the **Printer** section or the **Printer 2** section, update the settings:

    - In the **Printer** field, select **Windows driver**.
    - In the **Device name** field, enter the name of the printer.

4. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**.
5. Select job **1090**, and then select **Run now**.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]