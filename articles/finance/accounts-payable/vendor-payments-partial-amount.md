---
# required metadata

title: Vendor payments for a partial amount
description: Sometimes, you might make a payment to a vendor that is less than the amount of an invoice. This article describes the various options for handling this situation. 
author: angelad116
ms.date: 10/24/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LedgerJournalTransVendPaym, VendOpenTrans
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.assetid: 9a17075e-5325-4d55-a1e5-1791b8c460a0
ms.search.region: Global
# ms.search.industry: 
ms.author: angelading
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Vendor payments for a partial amount

[!include [banner](../includes/banner.md)]

Sometimes, you might make a payment to a vendor that is less than the amount of an invoice. This article describes the various options for handling this situation. The options that are available to you depend on your business requirements and configuration. 

## Cash discount amounts

A vendor can offer you a cash discount for paying an invoice before the due date. For example, you enter an invoice for 100.00 that specifies a 2-percent cash discount if the invoice is paid within 10 days. The due date terms are 30 days. If a payment proposal uses the cash discount as a criterion for selecting an invoice, and if the proposal is run on or before the cash discount date, the invoice is selected for payment, and the payment is created for 98.00. A cash discount can also be taken for a one-off payment that was created manually.

## Partial payments with cash discounts
When you make a partial payment, you might plan to make an additional partial payment to fully settle the invoice. To take a cash discount for a partial payment, you must set the **Calculate cash discounts for partial payments** option to **Yes** on the **Account payable parameters** page. 

For example, you receive a 2-percent cash discount if the invoice is paid within 10 days after it's issued. An invoice is posted for 100.00. If you make a payment of 49.00 within 10 days, you enter a debit of 49.00 in a payment journal. When you settle the partial payment on the **Settle open transactions** page, **1.00** appears in the **Cash discount amount to take** field. 

> [!NOTE] 
> If you enter a partial payment and leave the full invoice amount in the **Amount to settle** field, the **Cash discount amount to take** field is automatically recalculated when you post the transactions.

## Credit notes with cash discounts
You might return some of the items on an invoice and receive a credit note. If a cash discount was taken on the original invoice, you can subtract the value of the discount and receive a refund for the correct amount. If the **Calculate cash discounts for credit notes** option is set to **Yes** on the **Accounts payable parameters** page, the discount is automatically calculated for the credit note. 

For example, you receive a 2-percent cash discount if the invoice is paid within 10 days after it's issued. An invoice for 100.00 is posted. If you return the goods and receive a credit note, you can enter the credit note for the full amount of the original invoice, 100.00, together with the 2-percent cash discount that is also defined on the credit memo.  When you view the credit note on the **Settle transactions** page, **98.00** appears in the **Amount to settle** field, and **-2.00** appears in the **Cash discount amount** field. The discount amount is posted to a cash discount account.

## Overpayment/underpayment amounts
You might make a partial payment where the amount that must still be settled is very small. For example, the vendor invoice is for 1,000.00, and you pay 999.90. If the remaining amount is less than the amount that is specified for overpayments or underpayments on the **Accounts payable parameters** page, the difference is automatically posted to an overpayment/underpayment ledger account.


For more information, see [Vendor payment overview](../cash-bank-management/tasks/vendor-payment-overview.md).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
