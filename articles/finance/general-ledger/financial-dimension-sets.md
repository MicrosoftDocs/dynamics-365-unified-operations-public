---
# required metadata

title: Financial dimension sets
description: This topic describes various information related to financial dimension sets.
author: yukonpeegs
manager: AnnBe
ms.date: 03/23/2021
ms.topic: article
ems.prod: 
ms.technology: 

# optional metadata

ms.search.form: DimensionFocus, LedgerTrialBalanceListPage
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
ms.custom: 25871
ms.search.region: Global
# ms.search.industry: 
ms.author: epegors
ms.search.validFrom: 2021-03-23
ms.dyn365.ops.version: 10.0.16

---

# Financial dimension sets

[!include [banner](../includes/banner.md)]

This topic describes financial dimension sets and provides some tips for optimizing their use.

Use the **Financial dimension sets** page to create and manage financial dimension sets.

A dimension set is an ordered list of financial dimensions that can be used to summarize General ledger data in a user-defined way. The dimension set that contains only the main account is the only standard dimension set. A primary use of a dimension set is to define a trial balance.

## Dimension set balances

A dimension set can have balances that are based on the financial dimensions of the dimension set. The balances exist and are summarized from the data in General ledger to improve performance related to retrieving the balances. The balances are based on the dimension set definition and are summarized from the General ledger data to improve performance when the balances are retrieved, for example, when a trial balance is generated.

## Create balances

Use the **Create balances** button to initialize the balances on a dimension set that does not currently have balances.

> [!NOTE]
> We recommend limiting the number of dimension sets with balances, because updating the balances has an impact on all General ledger posting activities.

## Update balances

Use the **Update balances** button to include the latest General ledger posting activity in the balances. Updating balances is a light operation and only has to process the General ledger posting activity since the last update.

> [!NOTE]
> Displaying the trial balance forces an update to make sure the balances are current. Consider using a recurring batch job to make sure updates to your most frequently used dimension sets are quick because that will minimize the wait for the trial balance user.

## Rebuild balances

Use the **Rebuild balances** button to recreate the balances from scratch, ensuring they match the data in General ledger. Rebuilding balances requires a lot of processing and shouldn't be necessary most of the time.

> [!NOTE]
> If you have a scenario that regularly requires rebuilding balances, we recommend contacting customer support for help in determining the reason that balances don't match the the data in General ledger.

## Clear balances

Use **Clear balances** to remove the balances and stop any further updates. The dimension set will no longer have an impact on General ledger posting activities.

For more information, see [Financial dimensions](tasks/financial-dimensions.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
