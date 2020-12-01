---
# required metadata

title: Prepare a legal entity for use in the consolidation process
description: In a consolidation, you gather transactions from several sets of legal entity accounts into a single set of legal entity accounts. This topic lists the steps for preparing a legal entity for consolidation.
author: jinniew
manager: AnnBe
ms.date: 10/30/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jiwo
ms.search.validFrom: 2018-10-30
ms.dyn365.ops.version: 8.0.1

---

# Prepare a legal entity for use in the consolidation process

[!include banner] 

In a consolidation, you gather transactions from several sets of legal entity accounts into a single set of legal entity accounts. This topic lists the steps for preparing a legal entity for consolidation. 

> [!NOTE]
> We recommend that you use Management Reporter for Microsoft Dynamics 365 Finance to combine the financial results for multiple legal entities in a consolidated format. Management Reporter lets you create consolidated financial reports across legal entities, use Microsoft Excel to import consolidation data from other sources, and translate amounts into any number of reporting currencies without having to run the consolidation process in Microsoft Dynamics AX.

You can print reports, such as financial statements, from the consolidated legal entity. However, you cannot use the consolidated legal entity for daily transactions.

You can consolidate data from legal entities that use different databases than the database for the consolidated legal entity. This consolidation process is referred to as an import consolidation. Alternatively, the legal entities can use the same database as the consolidated legal entity. This consolidation process is referred to as an online consolidation.

The consolidated legal entity collects the results and balances of the subsidiaries. To prepare a consolidated legal entity for a consolidation, you must follow these steps:

1.  Click **General ledger** > **Setup** > **Organization** > **Legal entities**.

2.  Click **New** to create a new legal entity that will be the consolidated legal entity.

3.  Select the **Use for financial consolidation process** check box, and then enter information about the consolidated legal entity. Enter this information exactly as you want it to appear on financial statements for the consolidated legal entity.

4.  Close the page.

5.  Select the consolidated legal entity from the drop down list in the upper right corner of the screen, and then click **OK**.

6.  Click **General ledger** > **Setup** > **Ledger**.

7.  Select the chart of accounts, the fiscal calendar, the accounting currency, an optional reporting currency, and the default exchange rate type for the consolidated legal entity. 

8.  Click **General ledger** > **Setup** > **Currency** > **Currency exchange rates**.

9.  Set up currency exchange rates in relevant periods for the currencies of the subsidiary legal entities. 

10. Close the page.

11. If the consolidated legal entity has subsidiaries that use foreign currencies, open the **Accounts for automatic transactions** form. (Click **General ledger** > **Setup** > **Posting** > **Accounts for automatic transactions**.) In the **Posting type** field, select an appropriate account:
    
  - If the legal entity has foreign subsidiaries that are financially or operationally interdependent with the parent legal entity, select an appropriate account for the **Profit and loss account for consolidation differences** posting type.
    
   - If you are consolidating a subsidiary that is financially and operationally independent from the parent legal entity, or a legal entity that contains the results of several subsidiaries that are financially and operationally independent from the parent legal entity, and if you are using translation methods to consolidate the data, select an appropriate account for the **Balance account for consolidation differences** posting type.

12. In the **Main account** field, select the main accounts that will be used for foreign currency revaluation adjustments.

13. Close the page.

If you create the consolidated legal entity early in a period, you can revalue the foreign currency amounts as exchange rates change during the consolidation period.

The consolidated legal entity is now set up for the **Consolidate** periodic job. You can specify whether to perform either an online consolidation or an import consolidation:

Click **General ledger** > **Periodic** > **Consolidate** > **Consolidate \[Import from\]**.

–or–

Click **General ledger** \> **Periodic** \> **Consolidate** \> **Consolidate \[Online\]**.


> [!NOTE]
> Before you can process the consolidation, prepare the subsidiary legal entities for consolidation. For more information, see [Set up a subsidiary legal entity for consolidation](set-up-subsidiary-company-for-consolidation.md).


