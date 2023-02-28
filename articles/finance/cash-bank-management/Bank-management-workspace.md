---
# required metadata

title: Bank management workspace
description: This article provides information about the Bank management workspace. This workspace shows information that's related to company bank accounts.   
author: music727
ms.date: 02/15/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  BankTreasurerWorkspace
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global 
# ms.search.industry: 
ms.author: mbeinary
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: July 2017 update
---
# Bank management workspace

[!include [banner](../includes/banner.md)]

The **Bank management** workspace shows information that is related to company bank accounts. This workspace includes a **Summary** view and an **Analytics** page. The **Summary** view shows summary tiles, bank account information, a balance chart, and related information. The **Analytics** page uses the capabilities of Microsoft Power BI to show visuals that are related to bank account balances.

## Summary view

### Summary

The tiles in the **Summary** section give an overview of your bank accounts and provide quick access to the pages that you most often have to use. The bank reconciliation information is specific to the Advanced bank reconciliation functionality. Information is included only for those bank accounts that have the **Advanced bank reconciliation** option set to **Yes** on the **Bank account** page. From the **Summary** section, you can import electronic bank files for bank accounts across all legal entities.

### Bank accounts

Each bank account in the legal entity is represented by a card in the **Bank accounts** section. The current balance is shown, and you can drill down to the transactions that make up that summary balance amount. The **Bridged transactions** amount also lets you drill down to the transactions that make up that summary amount. Bridged transactions are any pending transactions that have been posted by using bridging functionality, but that haven't yet been cleared. The **Pending balance** amount is the current balance minus the bridged, or pending, transactions.

The card also shows when the bank account was last reconciled. This information is shown only if Advanced bank reconciliation is enabled for the bank account.

### Balance

The **Balance** chart shows either historic balance information for the bank account that is selected in the **Bank accounts** section or a summary of historic balance information for all bank accounts in the legal entity. This information is available for various periods: the current week, the current month, the current year, the last five years, and all periods (the full history of the bank account). 

If you're viewing the **Balance** chart for a single bank account, the historic balances are shown in the bank account currency. If you're viewing the chart for all bank accounts in the legal entity, the historic balances are shown in the accounting currency. 

Information about when the data was last updated appears at the top of the chart. You can update the data as you require.

> [!NOTE] 
> The bank account balance and trial balance of the main account associated to the bank will not be the same in all scenarios. The trial balance of a main account and a bank account will match when:
>1. The main account is set for only one bank account.
>2. The posting type of all the related main account transactions is **Bank**.  

### Related information

From the **Related information** section, you can open the **General journal** page to complete bank transfers. You can also quickly open the **Bank transactions** and **Bridged transactions** pages.

## Analytics view

The **Analytics** page provides important metrics about the bank accounts in the current company. The following visualizations are available on the page:

-   Total bank balance in system currency
-   Balance by legal entity
-   Today’s actual vs forecasted balance in bank account currency
-   Balance by bank account
-   Balance by currency

You can view bank analytics across all companies from the **Cash overview – all companies** workspace. For more information, see [Cash overview Power BI content](Cash-Overview-Power-BI-content.md).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
