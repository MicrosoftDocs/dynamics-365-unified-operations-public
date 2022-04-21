---
# required metadata

title: Consolidation account groups and additional consolidation accounts
description: This topic provides information about consolidation account groups and additional consolidation accounts, and explains how they're used.
author: panolte
ms.date: 01/11/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LedgerConsolidateAccountGroup
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
ms.custom: 265544
ms.assetid: 71c31df7-b655-46a8-8844-4f92a8bd71b0
ms.search.region: Global
# ms.search.industry: 
ms.author: roschlom
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Consolidation account groups and additional consolidation accounts

[!include [banner](../includes/banner.md)]

This topic provides information about consolidation account groups and additional consolidation accounts, and explains how they're used.

## Consolidation account groups

Consolidation account groups let you create groups of the accounts that you want to use to consolidate data. Typically, a consolidation account group represents a government-mandated chart of accounts. A consolidation account group can also map accounts to a group that's defined by the company's headquarters. You can find consolidation account groups in the **Setup** area of the **Consolidations** module. When you add a new group, you enter a unique identifier for the account group, as well as a name.

## Additional consolidation accounts
Additional consolidation accounts let you assign an account from an existing chart of accounts to a consolidation account group. You can then specify a consolidation account value and name. 

You can find additional consolidation accounts in the **Setup** area of the **Consolidations** module. When you create a new consolidation account, you must specify the following information:

-   **Main account** – This field is a lookup that shows all the main accounts that are based on the chart of accounts that you selected on the page. When you select an account, the name is automatically entered in the **Main account name** field.
-   **Consolidation account group** – Use this field to specify the group to assign the account to. If you consolidate in two different ways, you must add the same account to all four consolidation account groups.
-   **Consolidation account** – Enter the value of the consolidation account. This value doesn't have to be an account from a chart of accounts. It can be any value that you require.
-   **Consolidation account name** – Enter the name of account as you want it to appear on inquiries and reports.
-   **SAT level** – This field is used to report account statements to the Mexican tax authorities. 

When you've finished creating your consolidation account groups and additional consolidation accounts, you can select the group in the Consolidate online process.


For more information, see [Create consolidation groups and additional consolidation accounts](../general-ledger/tasks/create-consolidation-groups.md). 





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
