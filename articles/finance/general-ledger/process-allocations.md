---
# required metadata

title: Process allocations
description: This article provides information about allocations, the options for processing them in Microsoft Dynamics 365 Finance, and how they can be used in budget planning. Allocations are used to distribute amounts across multiple ledger account combinations. They help ensure that expenses or revenues are charged to the correct object in accounting.
author: kweekley
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: AccountingDistribution, LedgerAllocationRule, MainAccount
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.assetid: 04c8548a-0af9-492b-954b-946b4f8ca023
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Process allocations

[!include [banner](../includes/banner.md)]

This article provides information about allocations, the options for processing them, and how they can be used in budget planning. Allocations are used to distribute amounts across multiple ledger account combinations. They help ensure that expenses or revenues are charged to the correct object in accounting.

The following capabilities support this process:

-   Manually allocate transaction amounts by using the Split action in accounting distributions, or by applying financial dimension default templates to a document. For more information, see [Accounting distributions](../accounts-payable/accounting-distributions.md).
-   Automatically allocate transactions amounts based on allocation terms defined on individual main account. Allocation account entries will be generated for each journal based on the percentage and destination ledger account whenever an accounting entry meets the criteria defined as the source ledger account. For more information, see [Main account allocation terms](../general-ledger/main-account-allocation-terms.md)
-   Automatically allocate ledger balances or fixed amounts based on ledger allocation rules. The ledger allocation rules are processed on a periodic basis using allocation journals. For more information, see [Allocation rules](../general-ledger/ledger-allocation-rules.md).

###  Allocations in budget planning

Ledger allocation rules can be used for budget plans. When you use ledger allocation rules in budget planning, the allocation rules work the same way they would in the ledger, but the source data and destination data comes from the budget plan. You can manually select ledger allocation rules to use for budget plans. Alternatively, you can use an allocation schedule that runs as part of a workflow process.

> [!NOTE]
> You can’t use intercompany ledger allocation rules for budget planning.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
