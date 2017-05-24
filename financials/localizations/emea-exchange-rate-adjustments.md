---
# required metadata

title: Exchange rate adjustments
description: This topic provides information about the exchange rate adjustment functionality for users in legal entities in Estonia, Hungary, Czech Republic, Latvia, Lithuania, Poland, and Russia.
author: ShylaThompson
manager: AnnBe
ms.date: 04/10/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: LedgerParameters
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: ShylaThompson
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 272683
ms.assetid: cd1b9f11-4640-41a1-a114-222483333972
ms.search.region: Czech Republic, Estonia, Hungary, Latvia, Lithuania, Poland, Russia
# ms.search.industry: 
ms.author: v-elgolu
ms.dyn365.ops.intro: Version 1611
ms.search.validFrom: 2016-11-30

---

# Exchange rate adjustments

[!include[banner](../includes/banner.md)]


This topic provides information about the exchange rate adjustment functionality for users in legal entities in Estonia, Hungary, Czech Republic, Latvia, Lithuania, Poland, and Russia.

The functionality for exchange rate adjustments for Estonia, Hungary, Czech Republic, Latvia, Lithuania, Poland, and Russia includes the following extensions that are relevant for Accounts receivable and Accounts payable:

-   Postings of exchange rate adjustments can be reversed as corrections (negative amounts) to the original adjustments.
-   When consecutive unrealized adjustments are posted, the same general ledger posting account and transaction type are used, regardless of whether the adjustments represent a gain or a loss.
-   Calculated exchange rate gains are always posted to gain accounts, and calculated exchange rate losses are always posted to loss accounts.

Legal entities that have their primary address in the Czech Republic can use a special method for exchange rate adjustment. This method is known as the Incremental method. When this method is turned on, changes that the current feature introduces aren't applied. Unrealized and realized gains or losses are calculated against the last exchange rate that was used. The adjusted amount is used instead of the original amount as the basis of calculation. To switch to the Incremental exchange rate adjustment method, on the **General ledger parameters** page, in the **Foreign currency revaluation** section, in the **Calculation method** field, select **Incremental**. The following example shows how the exchange rate adjustment functionality works for Estonia, Hungary, Czech Republic, Latvia, Lithuania, Poland, and Russia. Here is the business scenario for this example:

-   An invoice in a foreign currency is posted on December 1, 2012.
-   The payment in the foreign currency is posted on January 3, 2013
-   Settlement is done to apply the payment to the invoice.
-   Exchange rates adjustment is done on December 31, 2012 (method = Standard).
-   Exchange rates adjustment is done on January 1, 2013 (method = Invoice date).

Here are the exchange rates for Canadian dollars (CAD) to U.S. dollars (USD) for this example:

-   December 1, 2012: 400.0000
-   December 31, 2012: 450.0000
-   January 3, 2013: 420.0000

| Event                                       | Date                             | Debit/credit | Amounts               | General ledger (GL) account    | Transaction type             | Posting type       | Credit | Correction |
|---------------------------------------------|----------------------------------|--------------|-----------------------|--------------------------------|------------------------------|--------------------|--------|------------|
| Invoice                                     | 1-Dec-12                         | Debit        | 10,000 CAD/40,000 USD | AR                             | Invoice                      | Customer balance   |        |            |
| Invoice                                     | 1-Dec-12                         | Credit       | 10,000 CAD/40,000 USD | Offset                         | Invoice                      | Ledger journal     | X      |            |
| Payment                                     | 3-Jan-13                         | Debit        | 10,000 CAD/42,000 USD | Offset                         | Payment                      | Ledger journal     |        |            |
| Payment                                     | 3-Jan-13                         | Credit       | 10,000 CAD/42,000 USD | AR                             | Payment                      | Customer balance   | X      |            |
| Settlement                                  | January 3, 2013 (= payment date) | Debit        | 0 CAD/2,000 USD       | AR                             | Customer                     | Exchange rate gain |        |            |
| Settlement                                  | January 3, 2013 (= payment date) | Credit       | 0 CAD/2,000 USD       | Realized currency adj profit   | Customer                     | Exchange rate gain | X      |            |
| Revaluation  (Standard method; date = December 31, 2012) | 31-Dec-12           | Debit        | 0 CAD/5,000 USD       | AR                             | Foreign currency revaluation | Exchange rate gain |        |            |
| Revaluation  (Standard method; date = December 31, 2012) | 31-Dec-12           | Credit       | 0 CAD/5,000 USD       | Unrealized currency adj profit | Foreign currency revaluation | Exchange rate gain | X      |            |
| Revaluation  (Standard method; date = December 31, 2012) | 3-Jan-13            | Debit        | 0 CAD/5,000 USD       | AR                             | Foreign currency revaluation | Exchange rate gain |        | X          |
| Revaluation  (Standard method; date = December 31, 2012) | 3-Jan-13            | Credit       | 0 CAD/5,000 USD       | Unrealized currency adj profit | Foreign currency revaluation | Exchange rate gain | X      | X          |



For the preceding revaluation, notice that the entry from January 3, 2013, is a direct reversal of the entry above it (from December 31, 2012). Even the GL accounts and posting types are the same. Additionally, notice that the **Correction** flag has been set.
||||||||||
|-----------------------------------------------------------|----------|--------|-----------------|--------------------------------|------------------------------|--------------------|---|---|
|Revaluation (Invoice date method; date = January 1, 2013)  | 1-Jan-13 | Debit  | 0 CAD/5,000 USD | AR                             | Foreign currency revaluation | Exchange rate gain |   | X |
| Revaluation (Invoice date method; date = January 1, 2013) | 1-Jan-13 | Credit | 0 CAD/5,000 USD | Unrealized currency adj profit | Foreign currency revaluation | Exchange rate gain | X | X |
| Revaluation (Invoice date method; date = January 1, 2013) | 3-Jan-13 | Debit  | 0 CAD/5,000 USD | AR                             | Foreign currency revaluation | Exchange rate gain |   |   |
| Revaluation (Invoice date method; date = January 1, 2013) | 3-Jan-13 | Credit | 0 CAD/5,000 USD | Unrealized currency adj profit | Foreign currency revaluation | Exchange rate gain | X |   |

For the preceding revaluation, notice that the entry from January 1, 2013, is a direct reversal of the entry below it (from January 3, 2013). Even the GL accounts and posting types are the same. Additionally, notice that the **Correction** flag has been set.

The system behavior is the same, regardless of whether the **Correction** option in the **Transaction reversal** section on the **General ledger parameters** page is set to **Yes** or **No**.




