---
# required metadata

title: Set up a subsidiary legal entity for consolidation
description: 
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
ms.search.validFrom: 2020-10-31
ms.dyn365.ops.version: 8.0.1

---

# Set up a subsidiary legal entity for consolidation 

[!include banner] 

The method that you use to prepare subsidiary accounts for consolidation depends, in part, on the extent to which the structure of the chart of accounts in the subsidiary legal entity reflects the chart of accounts in the consolidated legal entity.

Before you start a consolidation as part of period-end closing, complete the preparatory activities for the period-end closing, but do not close the subsidiary accounts until the consolidation is completed. For more information about period-end closing, see [Closing the month, period, and fiscal year](closing-the-month-period-and-fiscal-year.md) and [Fiscal year closing checklist](fiscal-year-closing-checklist.md).


> [!NOTE]
> <P>We recommend that you use Management Reporter for Microsoft Dynamics ERP to combine the financial results for multiple legal entities in a consolidated format. Management Reporter lets you create consolidated financial reports across legal entities, use Microsoft Excel to import consolidation data from other sources, and translate amounts into any number of reporting currencies without having to run the consolidation process in Microsoft Dynamics AX.</P>
> <P>For more information about how to consolidate transactions by using Management Reporter, see <A href="https://go.microsoft.com/fwlink/?linkid=389548">Financial consolidations and currency translation</A>.</P>

## Map subsidiary main accounts to consolidated main accounts

If the chart of accounts in the subsidiary legal entity does not follow the chart of accounts in the consolidated legal entity, you can map the main accounts in the subsidiary to the main accounts in the consolidated legal entity. Follow these steps in the subsidiary legal entity.

1.  Click **General ledger** \> **Setup** \> **Chart of accounts** \> **Chart of accounts**.

2.  Select a chart of accounts. On the **Main accounts** FastTab, select a main account, and then click **Edit**.

3.  Select each subsidiary main account that must be mapped to a consolidated main account. On the **General** FastTab, in the **Consolidation account** field, enter the account to which the balance or transactions of the selected subsidiary main account must be transferred in the consolidated legal entity. You can enter the same consolidated main account for several subsidiary accounts.
    

    > [!NOTE]
    > <P>If the main account types of the subsidiary accounts that are mapped differ from the main account types of the accounts in the consolidated legal entity, the values of accounts that have a main account type of <STRONG>Total</STRONG> are overwritten during consolidation.</P>



4.  To prepare reports and financial statements for the consolidated legal entity that are based on financial dimensions, map the financial dimensions that are used in the subsidiary accounts to the financial dimensions in the consolidated legal entity.
    
    1.  In the subsidiary legal entity, open the **Financial dimension values** form. (Click **General ledger** \> **Setup** \> **Financial dimensions** \> **Financial dimensions**. Select a financial dimension, and then click **Financial dimension values**.)
    
    2.  Select the financial dimension value to map to a different financial dimension value in the consolidated legal entity.
    
    3.  On the **General** FastTab, in the **Group dimension** field, enter the financial dimension in the consolidated legal entity. During consolidation, this financial dimension is assigned to transactions and balances that use the selected financial dimension in the subsidiary legal entity. The financial dimensions that you enter here must be used in the consolidated legal entity. You can assign the financial dimension that is used as the group financial dimension to several subsidiary financial dimensions.

5.  If you are performing an online consolidation, use the **Consolidate** **\[** **Online** **\]** form in the consolidated legal entity. (Click **General ledger** \> **Periodic** \> **Consolidate** \> **Consolidate \[Export to\]**.) To make sure that the transfers occur as you intend, select the **Use consolidation account:** check box on the **Criteria** tab.
    
    You must also select the appropriate financial dimensions on the **Financial dimensions** tab in the **Consolidate** **\[** **Online** **\]** form. For each financial dimension that you select, enter a number in the **Segment order** field to indicate the order in which the dimensions are displayed

## Maintain the same chart of accounts in both the subsidiary and consolidated legal entities

The main accounts in the subsidiary legal entity might have the same account numbers and the same structure for the chart of accounts as the main accounts in the consolidated legal entity. In this case, you do not have to manually map the main accounts in the subsidiary to the main accounts in the consolidated legal entity.

Follow this step in the consolidated legal entity: In the **Consolidate** **\[** **Online** **\]** form, select the **Use consolidation account:** check box before you start the consolidation. During consolidation, transactions and balances are automatically transferred to the correct account.

> [!NOTE]
> <P>If the accounts do not correspond, the consolidation stops, and a message is displayed.</P>

## Create a chart of accounts for the consolidated legal entity, based on an existing chart of accounts

You can perform the consolidation even if a chart of accounts has not already been created in the consolidated legal entity.

  - If you have planned the account structure to use in the consolidated legal entity, you can map the subsidiary accounts to this structure.

  - If you do not map any subsidiary accounts, the accounts in the consolidated legal entity are created automatically when subsidiary data is transferred to the consolidated legal entity. These accounts are based on the main account. Subsequent data is accumulated in accounts in the consolidated legal entity that have the same account number as the subsidiary accounts.

Regardless of whether you have mapped accounts, clear the **Use consolidation account:** check box in the **Consolidate** form in the consolidated legal entity before you run this kind of consolidation.

> [!NOTE]
> <P>You can use this method to create a chart of accounts in the consolidated legal entity from the chart of accounts in one of the subsidiary legal entities. Delete the consolidation transactions by using the instructions in <A href="view-and-delete-consolidation-transactions.md">View and delete consolidation transactions</A>. Then assign an appropriate consolidation conversion principle to each consolidated main account, and run the consolidation for all the subsidiary legal entities.</P>

