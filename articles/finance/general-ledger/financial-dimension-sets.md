---
title: Financial dimension sets
description: Learn about financial dimension sets and provides some tips for optimizing their use, including an outline on dimension set balances.
author: JodiChristiansen  
ms.author: twheeloc
ms.topic: article
ms.date: 02/09/2026
ms.update-cycle: 1095-days
ms.custom: 
  - bap-template
  - evergreen
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2021-03-23
ms.search.form: DimensionFocus, LedgerTrialBalanceListPage
ms.dyn365.ops.version: 10.0.16
---

# Financial dimension sets

[!include [banner](../includes/banner.md)]

This article describes financial dimension sets and provides some tips for optimizing their use.

A dimension set is an ordered list of financial dimensions that can be used to summarize General ledger data in a user-defined way. A primary use of dimension sets is to define a trial balance.

The only standard dimension set is the dimension set that contains only the main account.

You use the **Financial dimension sets** page to create and manage financial dimension sets.

A **Performance enhancement for general ledger dimension set balance calculation** feature is available to address performance. For more information, see [New financial dimension sets](financial-dimension-set-new.md).

## Dimension set balances

A dimension set can have balances that are based on its financial dimensions. The balances exist in General ledger and are based on the dimension set definition. The balances are summarized from the General ledger data to help improve performance when they are retrieved (for example, when a trial balance is generated).

## Create balances

Use the **Create balances** button to initialize the balances for a dimension set that doesn't currently have balances.

> [!NOTE]
> Updating balances affect all General ledger posting activies. We recommend that you limit the number of dimension sets that have balances. 

## Update balances

Use the **Update balances** button to include the latest General ledger posting activity in the balances. Balance updates are light operations. They must process only the General ledger posting activity that has occurred since the last update.

> [!NOTE]
> Display of the trial balance forces an update, to ensure that the balances that are shown are current. Consider using a recurring batch job so that updates to your most frequently used dimension sets are quick. In this way, you help minimize the time that trial balance users must wait.

## Rebuild balances

Use the **Rebuild balances** button to re-create the balances from scratch. In this way, you help ensure that they match the data in General ledger. A rebuild of balances requires lots of processing and should not usually be required.

> [!Important]
> Rebuilding balances should only be performed when incorrect or missing balance values are observed on the trial balance. This operation can significantly increase database load and processing time, depending on the volume of transactional data. During the rebuild, the affected dimension set is locked for recalculation and the trial balance can't be accessed until processing is complete. In environments with large sets of transactions this may take several hours or, in rare cases, multiple days.</p>
> To avoid performance impacts:
>  - Don't rebuild balances for multiple dimension sets at the same time. Running parallel rebuilds can introduce additional blocking and negatively affect system performance.
>  - Always attempt a date range-specific rebuild first. Use targeted rebuilds to recalculate only the periods where the discrepancies may exist. This approach should be tried before performing a full clear and rebuild of all balances.

If you have a scenario that regularly requires a rebuild of balances, we recommend that you contact customer support. Customer support can help you determine why balances don't match the data in General ledger.

## Clear balances

Use the **Clear balances** button to remove the balances and stop any further updates. The dimension set will no longer have an impact on General ledger posting activities.

## Delete a dimension set

Don't **delete and recreate** dimension sets as any form of workaround to solve potential issues with the balance data for a specific dimension set. Recreating a dimension set is costly. For further assistance with issues, contact customer support. 


For more information, see [Financial dimensions](financial-dimensions.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
