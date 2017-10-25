---
# required metadata

title: Prepayment invoices vs. prepayments
description: This article provides describes and contrasts the two methods that organizations can use for advance payments (prepayments). In one method, you create a prepayment invoice that is associated with a purchase order. In the other method, you create prepayment journal vouchers by creating journal entries and marking them as prepayment journal vouchers.
author: ShivamPandey-msft
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: LedgerJournalTransVendPaym, PurchTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 15871
ms.assetid: a0bb5220-73d4-48ae-84d0-46a171c224fa
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Prepayment invoices vs. prepayments

[!include[banner](../includes/banner.md)]


This article provides describes and contrasts the two methods that organizations can use for advance payments (prepayments). In one method, you create a prepayment invoice that is associated with a purchase order. In the other method, you create prepayment journal vouchers by creating journal entries and marking them as prepayment journal vouchers.

Organizations might issue prepayments (advance payments) to vendors for goods or services before those goods or services are fulfilled. Two methods can be used to issue prepayments to vendors. To minimize risk, you can track prepayments by defining the prepayment on a purchase order. For this method, you must create a prepayment invoice that is associated with a purchase order. This method is referred to as prepayment invoicing. Organizations that don't want to track prepayments as closely or don't receive a prepayment invoice from their vendor can use prepayment journal vouchers instead of the prepayment invoicing method. You can create prepayment journal vouchers by creating journal entries and marking them as prepayment journal vouchers. For this method, you can't track which prepayments to a vendor are made against which purchase orders. However, you can mark a posted prepayment for settlement against a purchase order.

## When to use prepayment invoicing vs. prepayments
| Prepayment invoicing                                                                | Prepayments                                                              |
|-------------------------------------------------------------------------------------|--------------------------------------------------------------------------|
| Define a prepayment value on the purchase order.                                    | No prepayment value is defined on the purchase order.                    |
| Key: A prepayment invoice and a final invoice must be posted.                       | No prepayment invoice must be posted.                                    |
| Liability for the prepayment is held in the prepayment account, not the AP account. | Liability for the prepayment is held in the AP account.                  |
| The vendor balance doesn’t reflect the prepayment value throughout the process.     | The vendor balance reflects the prepayment value throughout the process. |
| Prepayment invoicing is available in Accounts payable only.                         | Prepayments are available in Account payable and Accounts receivable.    |

## Overview of the prepayment process
Accounting practices in many countries/regions require that prepayments from a customer or to a vendor not be posted to the usual summary accounts for the customer or vendor. Instead, these prepayments are posted to special ledger accounts for prepayments. When a sales order or purchase order is created, an invoice is issued to the customer or from the vendor. When the invoice is paid, the prepayment and sales tax prepayment voucher on the prepayment ledger accounts are reversed, and the invoice amounts are automatically posted to the usual summary accounts. Follow these steps to create a prepayment.

1.  Set up a posting profiles for prepayments.
2.  In Accounts receivable parameters and Accounts payable parameters, under **Ledger and sales tax**, select the new posting profile by using the **Posting profile for payment journal with prepayment** parameter.
3.  Create a payment journal, and then create the new payment.
4.  You can flag the payment as a prepayment. If a payment is flagged as a prepayment, the payment is posted to the ledger accounts that are defined on the posting profile that you set up in steps 1 and 2. Additionally, if the payment is flagged as a prepayment, taxes are calculated. Some government require that taxes be paid when a prepayment is recorded, even if there isn't an invoice.
5.  Post the prepayment.
6.  Optional: You can settle the prepayment against the purchase order or sales order before you create the invoice. On the sales order or purchase order page, on the Action Pane, use **Settle transactions**.
7.  After the vendor delivers the goods or services, record the invoice. If you settled the prepayment against the purchase order or sale order in step 6, the prepayment is automatically settled against the invoice that you created. If you didn't settle the prepayment against the purchase order or sales order, you can manually settle it against the invoice by using **Settle transactions** on the customer or vendor page. The prepayment amount is then reversed out of the temporarily AP/AR ledger account. Additionally, if taxes were calculated, they are reversed, because the invoice has the actual taxes.

## Overview of the prepayment invoicing process
Prepayment invoices are a common business practice. A vendor issues prepayment invoices to require a deposit on the purchase before the purchase order is fulfilled. For example, some vendors require a prepayment for custom goods or services. If an vendor issues an invoice that requests prepayment, you can use the prepayment invoicing feature. A prepayment value can be defined on the purchase order, a prepayment invoice is recorded and paid, and then the prepayment invoice is applied to the final invoice. Follow these steps to create a prepayment.

1.  The purchasing agent creates, confirms, and then submits a purchase order that the vendor has requested prepayment for. The prepayment value is defined on the purchase order as part of the agreement.
2.  The vendor submits a prepayment invoice.
3.  The Accounts payable coordinator records the prepayment invoice against the purchase order, and then the prepayment invoice is paid.
4.  After the vendor delivers the goods or services, and the related vendor invoices have been received, the Accounts payable coordinator applies the prepayment amount that was already paid against the invoice.
5.  The Accounts payable coordinator pays and settles the remaining amount of the invoice.




