---
# required metadata

title: Pay a vendor by endorsing a bill of exchange
description: In Japan, bills of exchange (BOEs) are often endorsed to a vendor and used as a method of payment. In Microsoft Dynamics 365 for Finance and Operations, Enterprise edition, a list page for BOEs provides centralized management of the BOE lifecycle.
author: yijialuan
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: CustBillOfExchangeEndorseListPage, CustBillOfExchangeEndorseToVendor
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 28791
ms.search.region: Japan
# ms.search.industry: 
ms.author: riluan
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Pay a vendor by endorsing a bill of exchange

[!include[banner](../includes/banner.md)]


In Japan, bills of exchange (BOEs) are often endorsed to a vendor and used as a method of payment. In Microsoft Dynamics 365 for Finance and Operations, Enterprise edition, a list page for BOEs provides centralized management of the BOE lifecycle.

To start managing a BOE in Finance and Operations, open the Draw bill of exchange journal. When this type of journal is posted, if the status of the BOE is **Drawn**, users can manage the BOE lifecycle in following stages.

## Endorse a BOE to a vendor
The list page shows customer BOEs that have been drawn. You can select one or more BOEs to endorse to a vendor. However, if multiple BOEs are selected, they all must have a status of **Drawn** before you can endorse them. An accounting voucher will be generated to record the balance change in the endorsed BOE account and the accounts payable account.

## Settle vendor transactions
When a BOE is endorsed, its status changes to **Endorsed**. An Accounts payable user can then settle the vendor transaction against a vendor invoice. The status of the BOE itself doesn't change when the vendor transaction is settled.

## Settle endorsed BOEs
The lifecycle of a BOE ends when the BOE is paid or expires. For endorsed BOEs, you can select the BOE and settle the endorsement. An accounting voucher will be generated to record the balance change in the endorsed BOE account and the drawn BOE account.

## Reserve endorsement
If the status of a BOE is **Endorsed**, a user can reserve its endorsement.

## Additional resources
- [Pay a vendor transaction by endorsing a customer bill of exchange](./tasks/pay-vendor-transaction.md)
- [Reverse an endorsed bill of exchange](./tasks/reverse-endorsed-bill-exchange.md)
- [Set up Japan payment by endorsing a customer bill of exchange](./tasks/setup-japan-payment-endorsing-customer-bill-exchange.md)
- [Settle an endorsed bill of exchange](./tasks/settle-endorsed-bill-exchange.md)

