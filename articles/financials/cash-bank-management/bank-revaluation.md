---
# required metadata

title: Bank foreign currency revaluation 
description: This topic provides an overview of the bank foreign currency revaluation process -  setup, running the process, calculation for the process, and how to reverse the revaluation transactions, if necessary. 
author: mikefalkner
manager: AnnBe
ms.date: 02/28/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: BankCurrencyRevalHistory
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 62153
ms.assetid: 842e8561-560f-4cc6-8668-70cca60b1ba3
ms.search.region: Global
# ms.search.industry: 
ms.author: mikefalkner
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Bank foreign currency revaluation 

[!include [banner](../includes/banner.md)]

This topic provides an overview of the bank foreign currency revaluation process -  setup, running the process, calculation for the process, and how to reverse the revaluation transactions, if necessary. 

As part of a period-end, accounting conventions require bank account balances in foreign currencies to be revalued using different exchange rate types (current, historical, average, etc.). The bank foreign currency revaluation can be used to revalue one or more bank accounts. 

> [!NOTE]
When you run the revaluation process, the balance in each bank account posted in a foreign currency will be revalued. The unrealized gain or loss transactions that are created during the revaluation process are system-generated. Two transactions might be created, one for the accounting currency and a second for the reporting currency, if relevant. Each accounting entry will post to the unrealized gain or loss and the main account being revalued.

## Prepare to run foreign currency revaluation
Before you run the revaluation process, the following setup is required.

-   On the **Ledger** page:
-   Specify the **Exchange rate type**. If the exchange rate type is not defined on the main account, this exchange rate type will be used during foreign currency revaluation.
-   Specify the realized gain, realized loss, unrealized gain, and unrealized loss accounts for currency revaluation. Realized gain and realized loss accounts are used when settling AR and AP transactions, and unrealized gain and unrealized loss accounts are used for revaluing open transactions and general ledger main accounts.

-   On the **Currency revaluation accounts** page:
-   Select different currency revaluation accounts for each currency and company. If no accounts are defined, the accounts from the **Ledger** page are used.

## Enable foreign currency revaluation

You must enable the foreign currency revaluation feature before you can process foreign currency revaluations. 
-   Use the **Cash and bank management, Cash and bank management parameters** page and click on the **Features** tab. 
-   Click on **Yes** under **Foreign currency revaluation** to enable the feature for the current legal entity. 
-   Refresh your browser to view the **Foreign currency revaluation** menu under the **Periodic tasks** section of the area page.

You must enable the feature for any legal entity that will use foreign currency revaluation. 
-   You can change your legal entity and click on **Yes** or you can click on the **Enable this feature for other companies** menu next to the foreign currency revaluation field. 
-   You will be prompted to select the legal entities for which you want to enable the feature. 
-   You will only be able to enable the feature in the legal entities that you have security access to.
-   Click **Ok** to enable the feature across the legal entities that you selected. 

The **Foreign currency revaluation** menu will appear in all legal entities. If you select the menu item but you have not enabled the feature, you will receive a warning message that you can't process foreign currency revaluations when you open the page.

If your legal entity is in Russian, Poland, or Hungary, you already have the ability to do foreign currency revaluation. You many choose to use the new foreign currency revaluation or the version that you already have. The menus for each method will appear on your area page.

## Process foreign currency revaluation
After the setup is complete, use the **Foreign currency revaluation** page in **Cash and Bank Management** to revalue the balances of one or more bank accounts across all legal entities. You can run the process in real time or schedule it to run by using a batch. 

The **Foreign currency revaluation** page will display the history of each revaluation process, including when the process was run, what criteria was defined, a link to the voucher created for the revaluation, and a record if a previous revaluation was reversed. To run the revaluation process, select the **Foreign currency revaluation** button. 

The **Revalue as of date** values define the cutoff date for calculating the foreign currency balance that will be revalued. The sum of all bank transactions that have occurred up to and including the date are revalued. 

The **Date of rate** can be used to define the date for which the exchange rate should default. For example, you can revalue the balances as of January 31, but use the exchange rate defined for February 1. 

The revaluation process can be run for one or more legal entities. The lookup will display only the legal entities to which you have access. Select the legal entities for which you want to select the bank accounts that are eligible for foreign currency revaluation. All of the bank accounts for those legal entities will be displayed in the grid that follows. 

Set **Preview before posting** to **Yes** if you would like to review the result of the Bank revaluation. The foreign currency revaluation has a preview which can be posted, without having to run the revaluation process again. The results of the preview can be exported to Microsoft Excel to retain the history of how the amounts were calculated. You cannot use batch processing if you want to preview the results of the revaluation. 

Click **Ok** to process the foreign currency revaluation. A record will be created to track the history of each run.  A separate record will be created for each legal entity and posting layer.

## Calculate unrealized gain/loss
In Cash and Bank Management, a transaction is created for the delta between the balance of the bank account, including any previous revaluation amounts, and the new value based on the exchange rate for the Date of Rate. The foreign currency revaluation is based on the bank currency and currency being revalued. This calculation is done for the accounting currency and the reporting currency, resulting in two transactions. These entries are marked as reconciled. No entry is made for the accounting currency if the bank currency matches the accounting currency.  No entry is made for the reporting currency if the bank currency matches the reporting currency.

## Reverse foreign currency revaluation
If you need to reverse the revaluation transaction, select the **Reverse transaction** button on the **Foreign currency revaluation** page. A new foreign currency revaluation historical record will be created to maintain the historical audit trail of when the revaluation occurred or was reversed. 

If you need to reverse several revaluations, you must reverse the most current revaluation first and continue to reverse older revaluations in date order. You can then process new revaluations for the periods that you have reversed. 
