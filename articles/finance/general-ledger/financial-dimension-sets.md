---
# required metadata

title: Financial dimension sets
description: This article describes financial dimension sets and provides some tips for optimizing their use.
author: yukonpeegs
ms.date: 03/07/2022
ms.topic: article
ems.prod: 
ms.technology: 

# optional metadata

ms.search.form: DimensionFocus, LedgerTrialBalanceListPage
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: epegors
ms.search.validFrom: 2021-03-23
ms.dyn365.ops.version: 10.0.16

---

# Financial dimension sets

[!include [banner](../includes/banner.md)]

This article describes financial dimension sets and provides some tips for optimizing their use.

A dimension set is an ordered list of financial dimensions that can be used to summarize General ledger data in a user-defined way. A primary use of dimension sets is to define a trial balance.

The only standard dimension set is the dimension set that contains only the main account.

You use the **Financial dimension sets** page to create and manage financial dimension sets.

## Dimension set balances

A dimension set can have balances that are based on its financial dimensions. The balances exist in General ledger and are based on the dimension set definition. The balances are summarized from the General ledger data to help improve performance when they are retrieved (for example, when a trial balance is generated).

## Create balances

Use the **Create balances** button to initialize the balances for a dimension set that doesn't currently have balances.

> [!NOTE]
> We recommend that you limit the number of dimension sets that have balances, because balance updates affect all General ledger posting activities.

## Update balances

Use the **Update balances** button to include the latest General ledger posting activity in the balances. Balance updates are light operations. They must process only the General ledger posting activity that has occurred since the last update.

> [!NOTE]
> Display of the trial balance forces an update, to ensure that the balances that are shown are current. Consider using a recurring batch job so that updates to your most frequently used dimension sets are quick. In this way, you help minimize the time that trial balance users must wait.

## Rebuild balances

Use the **Rebuild balances** button to re-create the balances from scratch. In this way, you help ensure that they match the data in General ledger. A rebuild of balances requires lots of processing and should not usually be required.

> [!NOTE]
> If you have a scenario that regularly requires a rebuild of balances, we recommend that you contact customer support. Customer support can help you determine why balances don't match the data in General ledger.

## Clear balances

Use the **Clear balances** button to remove the balances and stop any further updates. The dimension set will no longer have an impact on General ledger posting activities.

## Delete a dimension set

Don't **delete and recreate** dimension sets as any form of workaround to solve potential issues with the balance data for a specific dimension set. Recreating a dimension set is costly. For further assistance with issues, contact customer support. 


For more information, see [Financial dimensions](financial-dimensions.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
