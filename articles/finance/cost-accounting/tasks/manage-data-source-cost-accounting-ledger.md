--- 
title: Manage a data source for the cost accounting ledger
description: Use this procedure to manage the general ledger data source for a cost accounting ledger, including a step-by-step process of managing data sources. 
author: twheeloc
ms.author: kfend
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

[!include [banner](../../includes/banner.md)]

Use this procedure to manage the general ledger data source for a cost accounting ledger. Before you complete this task, make sure that you play the "Create a cost accounting ledger" and "Define cost control units" task guides. This recording uses the USP2 demo data company.

1. Go to **Cost accounting > Ledger setup > Cost accounting ledgers**.
2. In the list, find and select the desired record.
3. Click **Actual versions**.
4. On the Action Pane, click **Manage**.
5. Click **General ledger**.
6. Click **New**.
7. In the **Name** field, type a value.
8. In the **Data provider** field, enter or select a value.
    * For this example, select Dynamics 365 Finance - General ledger entries.  
9. In the **Cost element dimension** field, enter or select a value.
    * For this example, select Cost elements.  
10. Click **Save**.
11. Click **Configure data provider**.
12. In the **Legal entity** field, enter or select a value.
    * For this example, select USP2.  
13. Click **New**.
14. In the **Posting layer** field, select **Current**.
15. Click **OK**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
