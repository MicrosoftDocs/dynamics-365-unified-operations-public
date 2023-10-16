---
# required metadata

title: New Financial dimension sets
description: This article describes the updated functionality for financial dimension sets. 
author: rcarlson
ms.date: 10/16/2023
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
ms.author: rcarlson
ms.search.validFrom: 2023-10-16
ms.dyn365.ops.version: 10.0.38

---

# New Financial dimension sets 

[!include [banner](../includes/banner.md)]

> [!NOTE]
> Beginning in application 10.0.38, a new feature **Performance enhancement for general ledger dimension set balance calculation** is available.

Turning on this feature will initiate the process of creating new balances which may take several hours on large amounts of transactional data. Reports and inquiries using dimension sets will not be available until the processing is complete. You can view the status on the Dimension set page. This feature allows your trial balance inquiry page and reports that use financial dimension sets to run more efficiently. The financial dimension sets stores data more efficiently using less space and allowing the trial balance to show current balance data more quickly. This feature uses process automation to keep the balance amounts up to date.


## Balance status

The **balance status** button will allow you to view the current calculation state of the Financial dimension set.  Opening this page will show the status of the dimension set balance for each legal entity in the system.  It will also show the date and time the dimension set was last updated by the automatic background process. 

## Enable balances

Use the **Enable balances** button to initialize and begin tracking balances for a dimension set that doesn't currently have balances.

> [!NOTE]
> We recommend that you limit the number of dimension sets that have balances, because balance updates affect all General ledger posting activities.

## Disable balances

Use the **Disable balances** button to turn off tracking balances for a given dimension set. 


## Rebuild balances

Use the **Rebuild balances** button on the balance status page to re-create the balances from the root General ledger transactional data. In this way, you help ensure that they match the data in General ledger. A rebuild of balances requires lots of processing and should **rarely** be required. 


## Delete a dimension set

If you no longer require a dimension set you can remove it by pressing the delete buttong. Do not **delete and recreate** dimension sets as any form of workaround to solve potential issues with the balance data for a specific dimension set. Recreating a dimension set is costly. For further assistance with issues, contact customer support. 


For more information, see [Financial dimensions](financial-dimensions.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
