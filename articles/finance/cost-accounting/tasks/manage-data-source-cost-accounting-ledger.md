--- 
title: Manage a data source for the cost accounting ledger
description: Use this procedure to manage the general ledger data source for a cost accounting ledger, including a step-by-step process of managing data sources. 
author: twheeloc
ms.author: twheeloc
ms.topic: how-to
ms.date: 03/27/2023
ms.custom:
ms.reviewer: twheeloc
audience: Application User   
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: CAMAXGeneralLedgerEntryProviderConfiguration
ms.dyn365.ops.version: AX 7.0.0 
---

# Manage a data source for the cost accounting ledger

[!INCLUDE [banner](../../includes/banner.md)]

Use this procedure to manage the general ledger data source for a cost accounting ledger. Before you complete this task, make sure that you complete the "Create a cost accounting ledger" and "Define cost control units" task guides. This recording uses the USP2 demo data company.

1. Go to **Cost accounting > Ledger setup > Cost accounting ledgers**.
1. In the list, find and select the desired record.
1. Select **Actual versions**.
1. On the Action Pane, select **Manage**.
1. Select **General ledger**.
1. Select **New**.
1. In the **Name** field, type a value.
1. In the **Data provider** field, enter or select a value.
    * For this example, select **Dynamics 365 Finance - General ledger entries**.  
1. In the **Cost element dimension** field, enter or select a value.
    * For this example, select **Cost elements**.  
1. Select **Save**.
1. Select **Configure data provider**.
1. In the **Legal entity** field, enter or select a value.
    * For this example, select **USP2**.  
1. Select **New**.
1. In the **Posting layer** field, select **Current**.
1. Select **OK**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
