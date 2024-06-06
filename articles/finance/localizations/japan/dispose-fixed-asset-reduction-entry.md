---
title: Dispose of a fixed asset with reduction entry
description: Learn how to dispose of a fixed asset with reduction entry for Japan, including a step-by-step process using the JPMF demo data company.
author: kfend
ms.author: kfend
ms.topic: how-to
ms.date: 08/29/2018
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: LedgerJournalTable, LedgerJournalTransAsset, SysQueryForm
ms.dyn365.ops.version: Version 7.0.0
---

# Dispose of a fixed asset with reduction entry

[!include [banner](../../includes/banner.md)]

Use this task to learn how to dispose of a fixed asset with reduction entry for Japan.



In order to complete this task, the Fixed Asset configuration key must be selected.



This task was completed using the JPMF demo data company.

1. Go to Fixed assets > Journal entries > Fixed assets journal.
2. Click New.
3. In the Name field, type a value.
4. Click Lines.
5. Click Proposals.
6. Click Disposal - scrap.
7. Enter the date of disposal transaction
8. Click Filter.
9. In the Criteria field, type a value.
10. Click OK.
11. Click OK.
12. Enter the main accounts where the fixed asset disposal expenses will be posted to.
    * You can also choose to enter the disposal expenses later in a journal.     The fixed asset main account and accumulated depreciation main account and other fixed asset related accounts are automatically determined by the configuration in the fixed asset posting profile.  
    * The disposal of reduction entry document is separated from that of the fixed asset.  
    * The original subsidy amount and accumulated amortization amount are automatically determined by the configuration in the fixed asset posting profile.  
13. Click Post.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
