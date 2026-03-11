---
title: Penalties for past due customer payments in France
description: Learn about penalties for past due customer payments in France.
author: EvgenyPopovMBS
ms.author: evgenypopov
ms.topic: how-to
ms.date: 03/11/2026
ms.reviewer: johnmichalak
ms.search.region: France
ms.search.validFrom: 2016-02-28
ms.search.form: CustInvoiceJournal, CustFormletterParameters
ms.custom: 
  - bap-template
---

# Penalties for past due customer payments in France

[!include [banner](../../includes/banner.md)]

In France, you can apply a penalty when a customer payment is past due. You can also print the lump sum recovery text that displays the penalty amount that must be paid on the invoice, and the due date of the payment.

The lump sum recovery text shows the penalty amount and the due date for the payment. The penalty amount is applied if the payment is past the due date. You print the lump sum recovery text on the customer invoice. You can specify the penalty amount and the currency along with any instructions in the Lump sum recovery text field in the Invoice area on the Form setup form.

To print the lump sum recovery text on a customer invoice, use the Form setup page to set up the parameters to print the lump sum recovery text. Next, use the Posting invoice page or the Invoice journal page to print the lump sum recovery text on a customer invoice. For more information, see [Print lump sum recovery text on a customer invoice](emea-fra-print-lump-sum-recovery-text.md).

You can apply a penalty on a customer payment when the payment isn't received by the due date.

After you set up the parameter to print the lump sum recovery text, it's printed on the following customer documents:

- Customer invoices
- Free text invoices
- Customer proforma invoices
- Customer credit notes

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]