---
title: Pay a vendor by endorsing a bill of exchange for Japan
description: Learn about endorsing bills of exchange (BOE) to pay a vendor in Japan, including outlines on endorsing a BOE to a vendor and settling vendor transactions.
author: EricWangChen
ms.author: wangchen
ms.topic: article
ms.date: 12/08/2025
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Japan
ms.search.validFrom: 2016-02-28
ms.search.form: CustBillOfExchangeEndorseListPage, CustBillOfExchangeEndorseToVendor
ms.dyn365.ops.version: AX 7.0.0
---

# Pay a vendor by endorsing a bill of exchange for Japan

[!include [banner](../../includes/banner.md)]

In Japan, you can endorse bills of exchange (BOE) to a vendor and use them as a method of payment. A list page for BOEs provides centralized management of the BOE lifecycle.

To start managing a BOE, open the Draw bill of exchange journal. When you post this type of journal, if the status of the BOE is **Drawn**, you can manage the BOE lifecycle in the following stages.

## Endorse a BOE to a vendor

The list page shows customer BOEs that you drew. You can select one or more BOEs to endorse to a vendor. However, if you select multiple BOEs, they all must have a status of **Drawn** before you can endorse them. The system generates an accounting voucher to record the balance change in the endorsed BOE account and the accounts payable account.

## Settle vendor transactions

When you endorse a BOE, its status changes to **Endorsed**. An Accounts payable user can then settle the vendor transaction against a vendor invoice. The status of the BOE itself doesn't change when the vendor transaction is settled.

## Settle endorsed BOEs

The lifecycle of a BOE ends when you pay or it expires. For endorsed BOEs, you can select the BOE and settle the endorsement. The system generates an accounting voucher to record the balance change in the endorsed BOE account and the drawn BOE account.

## Reserve endorsement

If the status of a BOE is **Endorsed**, a user can reserve its endorsement.

## Additional resources

- [Pay a vendor transaction by endorsing a customer bill of exchange](pay-vendor-transaction.md)
- [Reverse an endorsed bill of exchange](reverse-endorsed-bill-exchange.md)
- [Setup Japan payment by endorsing a customer bill of exchange](setup-japan-payment-endorsing-customer-bill-exchange.md)
- [Settle an endorsed bill of exchange](settle-endorsed-bill-exchange.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
