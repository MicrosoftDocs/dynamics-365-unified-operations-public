---
# required metadata

title: Customer payments for a partial amount
description: Sometimes, customers make a payment that is less than the amount of an invoice. This article describes the various options for handling this situation. The options that are available to you depend on your business requirements and configuration.
author: ShivamPandey-msft
ms.date: 01/08/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: CustPaymEntry
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.assetid: 20423a2d-6997-4e1c-a596-a77016600071
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Customer payments for a partial amount

[!include [banner](../includes/banner.md)]

Sometimes, customers make a payment that is less than the amount of an invoice. This article describes the various options for handling this situation. The options that are available to you depend on your business requirements and configuration.

## Partial payment with no discount

Customers might make a partial payment because they just don't have enough cash on hand to pay the invoice in full, or because there is a dispute about an item on the invoice. In this situation, the invoice can be partially settled with the payment. The invoice will remain open and will show a balance.

## Discount amounts
You can offer customers a cash discount for paying an invoice before the due date. For example, you enter an invoice for 100.00 that specifies a 2-percent cash discount if the invoice is paid within 10 days. The due-date terms are 30 days. If you receive a payment of 98.00 within 10 days, you enter the payment for 98.00. Then, when the invoice is marked for settlement, the cash discount it taken automatically.

## Partial payments with cash discounts
When customers make a partial payment, they might plan to make an additional partial payment to fully settle the invoice. To take a cash discount for a partial payment, you must set the **Calculate cash discounts for partial payments** option to **Yes** on the **Accounts receivable parameters** page. 

For example, you offer a 2-percent cash discount if the invoice is paid within 10 days after it's issued. An invoice is posted for 100.00. If you receive a payment of 49.00 within 10 days, you enter a credit of 49.00 in a payment journal. When you settle the partial payment on the **Settle transactions** page, **1.00** appears in the **Cash discount amount to take** field. The discount amount is posted to a cash discount account. 

> [!NOTE] 
> If you enter a partial payment and leave the full invoice amount in the **Amount to settle** field, the **Cash discount amount to take** field is automatically recalculated when you post the transactions.

## Credit notes with discounts
If customers return some of the items on an invoice, you might issue a credit note. If a cash discount was taken on the original invoice, the credit memo to the customer should be net of the cash discount that was taken by the customer. If the **Calculate cash discounts for credit notes** option is set to **Yes** on the **Accounts receivable parameters** page, the discount is automatically calculated for the credit note. 

For example, you offered terms of payment that specify a 2-percent cash discount if the invoice is paid within 10 days after it's issued. An invoice for 100.00 was posted, and the customer took the cash discount. If the customer returns the goods and you issue a credit note, you can enter the credit note for -100.00. When you view the credit note on the **Settle open transactions** page, **98.00** appears in the **Amount to settle** field, and **-2.00** appears in the **Cash discount amount** field. The discount amount is posted to a cash discount account.

## Overpayment/underpayment amounts
When customers make a payment, there might be a very small amount that must still be settled. For example, you invoice the customer for 1,000.00, and the customer pays 999.90. If the remaining amount is less than the amount that is specified for overpayments or underpayments on the **Accounts receivable parameters** page, the difference is automatically posted to an overpayment/underpayment ledger account.

## Full settlement
Customers might make a partial payment where the remaining amount won't be paid but is greater than the underpayment amount that is specified on the **Account payable parameters** page. If you want to mark the invoice as fully settled, you can use the **Full settlement** option on the **Settle transaction** page. (You can enable the full settlement functionality by using a configuration key.) For example, an invoice is posted for 1,000.00, and the customer makes a payment of 990.00. You've agreed that the customer doesn't have to pay the remaining 10.00. After you mark the invoice for settlement, you can also mark select **Full settlement**. The invoice will then be considered fully settled. The 10.00 difference is posted to a cash discount account as an additional cash discount amount.


For more information, see [Deposit customer payments](tasks/deposit-customer-payments.md).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
