---
# required metadata

title: Conditional sales tax for protested promissory notes or bills of exchange
description: For legal entities in Spain, if a promissory note payment for a vendor or a bill of exchange payment for a customer is settled against an invoice that includes conditional tax, and you protest the settlement, the cancellation of conditional tax is registered with a voucher that is related to the settlement cancellation voucher.
author: ShylaThompson
manager: AnnBe
ms.date: 04/25/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 271503
ms.search.region: Spain
# ms.search.industry: 
ms.author: v-elgolu
ms.dyn365.ops.version: Version 1611
ms.search.validFrom: 2016-11-30

---

# Conditional sales tax for protested promissory notes or bills of exchange
[!include[banner](../includes/banner.md)]


For legal entities in Spain, if a promissory note payment for a vendor or a bill of exchange payment for a customer is settled against an invoice that includes conditional tax, and you protest the settlement, the cancellation of conditional tax is registered with a voucher that is related to the settlement cancellation voucher.

*Conditional sales tax* is sales tax that is paid proportionally to the actual amount that is paid on an invoice. For more information about conditional tax, see [Sales tax overview](../general-ledger/indirect-taxes-overview.md). A *promissory note* is a written agreement in which the maker of the note promises to pay a specific amount at a specific time. A *bill of exchange* is a written or electronic order from a customer that specifies that another party (usually a bank) should pay a stated amount to the company. For more information about bills of exchange, see [Set up bills of exchange](../accounts-receivable/set-up-bills-exchange.md).

## Conditional sales tax for protested promissory notes
When a user posts a Redraw promissory note journal, transactions that were previously posted are reversed if a promissory note was settled against a vendor invoice. If the invoice included conditional tax when it was settled against a promissory note, a tax transaction for the conditional tax is posted. For legal entities in Spain, if the promissory note was settled against an invoice that includes conditional tax, the tax transaction is reversed when a Redraw promissory note journal is posted. To view reverse transactions, go to **Voucher transactions** &gt; **Related vouchers**.

## Conditional sales tax for protested bills of exchange
When a user posts a Protest bill of exchange journal, transactions that were previously posted are reversed if a bill of exchange was settled against a customer invoice. If the invoice included conditional tax when it was settled against a bill of exchange, a tax transaction for the conditional tax is posted. For legal entities in Spain, if the bill of exchange was settled against an invoice that includes conditional tax, the tax transaction is reversed when a Protest bill of exchange journal is posted. To view reverse transactions, go to **Voucher transactions** &gt; **Related vouchers**.


