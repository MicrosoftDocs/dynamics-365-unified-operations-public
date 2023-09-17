---
# required metadata

title: Ledger allocation rules
description: This article provides information about ledger allocation rules. It describes the various components of these allocation rules and the allocation methods that can be used for them.
author: kweekley
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LedgerAllocation, LedgerAllocationBasisRule, LedgerAllocationRequest, LedgerAllocationRule
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.assetid: 8147e148-7c11-45ef-95c6-f9889a875b54
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Ledger allocation rules

[!include [banner](../includes/banner.md)]

This article provides information about ledger allocation rules. It describes the various components of these allocation rules and the allocation methods that can be used for them.

Ledger allocation rules are used to automatically calculate and generate allocation journals and account entries for the allocation of ledger balances or fixed amounts. Allocation methods can be variable or fixed. The allocation is based on the transaction currency value. For example, foreign currency gain/loss accounting entries are posted to adjust the accounting and reporting currency amounts. These entries are not subject to allocation rules because their transaction currency value is 0.00. The following allocation methods can be used for ledger allocation rules:

-   **Basis** – This variable method is used when the allocation depends on the actual ledger balance, based on filter criteria. For example, advertising expenses can be allocated based on each department's sales in proportion to the total departmental sales.
-   **Fixed percentage** and **Fixed weight** – For these methods, the allocation percentage or weight is defined directly for the rule. For example, advertising expenses can be allocated so that Department A receives 70 percent of the advertising expense and Department B receives 30 percent.
-   **Equally** – This method distributes the amount equally to each defined destination. For example, if destinations are defined for Department A and Department B, advertising expenses can be allocated so that both Department A and Department B receive 50 percent of the advertising expense.

If Basis is used as the allocation method for an allocation rule, you must also define separate ledger allocation basis rules. The "Process allocation request" process lets users process the ledger allocation rule and preview the resulting allocation journal entries before they either post or delete the calculated allocations.

## Components of ledger allocation rules
Each allocation rule has four components: general, source, destination, and offset. An additional component, ledger allocation bases rules, is required if Basis is used as the allocation method. Each component provides a critical piece of the information that is required in order to process allocations.

-   **General** – This component is where the user specifies options such as the allocation method, intercompany rule settings, and whether the rule is active.
-   **Source** – This component is where the user specifies the source data for the allocation. Allocation can be based on ledger balances (**Data source** = **Ledger**) or fixed amounts (**Data source** = **Fixed value**). When **Data source** is set to **Ledger**, source filter criteria must be defined for the ledger allocation rule (for example, for the advertising expenses).
-   **Destination** – This component defines how the result of the allocation calculation should be distributed and accounted for. For example, there can be one destination line for each department.
-   **Offset** – This component defines how main accounts and dimensions should be determined for the offset entries that balance the destination entries. User-defined options are typically used instead of accounts and dimensions that are based on the source. When **Data source** is set to **Fixed value**, **Source** can't be used as an option.
-   **Ledger allocation basis rules** – These rules use their own source filter criteria to determine which ledger balances should be used for allocation (for example, the revenue per department). Each allocation basis rule can be used with multiple allocation rules.






[!INCLUDE[footer-include](../../includes/footer-banner.md)]
