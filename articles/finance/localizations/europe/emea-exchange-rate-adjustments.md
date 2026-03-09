---
title: Exchange rate adjustments
description: Learn about the exchange rate adjustment functionality for users in legal entities in Estonia, Hungary, Czech Republic, Latvia, Lithuania, Poland, and Russia.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: overview
ms.custom: 
  - bap-template
ms.date: 03/06/2026
ms.reviewer: johnmichalak
ms.search.region: Czech Republic, Estonia, Hungary, Latvia, Lithuania, Poland, Russia
ms.search.validFrom: 2016-11-30
ms.search.form: LedgerParameters
---

# Exchange rate adjustments

[!include [banner](../../includes/banner.md)]

This article provides information about the exchange rate adjustment functionality for users in legal entities in Estonia, Hungary, Czech Republic, Latvia, Lithuania, Poland, and Russia.

The functionality for exchange rate adjustments for Estonia, Hungary, Czech Republic, Latvia, Lithuania, Poland, and Russia includes the following extensions that are relevant for Accounts receivable and Accounts payable:

- You can reverse postings of exchange rate adjustments as corrections (negative amounts) to the original adjustments.
- When you post consecutive unrealized adjustments, the system uses the same general ledger posting account and transaction type, regardless of whether the adjustments represent a gain or a loss.
- The system always posts calculated exchange rate gains to gain accounts, and calculated exchange rate losses to loss accounts.

Legal entities that have their primary address in the Czech Republic can use a special method for exchange rate adjustment. This method is known as the **Incremental** method. When you turn on this method, the system doesn't apply the changes that the current feature introduces. The system calculates unrealized and realized gains or losses against the last exchange rate that was used. The adjusted amount is used instead of the original amount as the basis of calculation. To switch to the **Incremental** exchange rate adjustment method, on the **General ledger parameters** page, in the **Foreign currency revaluation** section, in the **Calculation method** field, select **Incremental**. The following example shows how the exchange rate adjustment functionality works for Estonia, Hungary, Czech Republic, Latvia, Lithuania, Poland, and Russia. Here's the business scenario for this example:

- You post an invoice in a foreign currency on December 1, 2012.
- You post the payment in the foreign currency on January 3, 2013.
- You settle the transaction to apply the payment to the invoice.
- You adjust the exchange rates on December 31, 2012 (method = Standard).
- You adjust the exchange rates on January 1, 2013 (method = Invoice date).

Here are the exchange rates for Canadian dollars (CAD) to U.S. dollars (USD) for this example:

- December 1, 2012: 400.0000
- December 31, 2012: 450.0000
- January 3, 2013: 420.0000

## Invoice

| Date                             | Debit/credit | Amounts               | General ledger (GL) account    | Transaction type             | Posting type       | Credit | Correction |
|----------------------------------|--------------|-----------------------|--------------------------------|------------------------------|--------------------|--------|------------|
| December 1, 2012                | Debit        | 10,000 CAD/40,000 USD | AR                             | Invoice                      | Customer balance   |        |            |
| December 1, 2012                | Credit       | 10,000 CAD/40,000 USD | Offset                         | Invoice                      | Ledger journal     | X      |

### Payment

| Date                             | Debit/credit | Amounts               | General ledger (GL) account    | Transaction type             | Posting type       | Credit | Correction |
|----------------------------------|--------------|-----------------------|--------------------------------|------------------------------|--------------------|--------|------------|
| January 3, 2013                 | Debit        | 10,000 CAD/42,000 USD | Offset                         | Payment                      | Ledger journal     |        |            |
| January 3, 2013                 | Credit       | 10,000 CAD/42,000 USD | AR                             | Payment                      | Customer balance   | X      |            |

### Settlement

| Date                             | Debit/credit | Amounts               | General ledger (GL) account    | Transaction type             | Posting type       | Credit | Correction |
|----------------------------------|--------------|-----------------------|--------------------------------|------------------------------|--------------------|--------|------------|
|January 3, 2013 (payment date) | Debit        | 0 CAD/2,000 USD       | AR                             | Customer                     | Exchange rate gain |        |            |
|January 3, 2013 (payment date) | Credit       | 0 CAD/2,000 USD       | Realized currency adj profit   | Customer                     | Exchange rate gain | X      |            |

### Revaluation  (Standard method; date = December 31, 2012)

For this revaluation example, the entry from January 3, 2013, directly reverses the December 31, 2012 entry. Even the GL accounts and posting types match. Additionally, the **Correction** flag is set.

| Date                             | Debit/credit | Amounts               | General ledger (GL) account    | Transaction type             | Posting type       | Credit | Correction |
|----------------------------------|--------------|-----------------------|--------------------------------|------------------------------|--------------------|--------|------------|
| 31-Dec-12           | Debit        | 0 CAD/5,000 USD       | AR                             | Foreign currency revaluation | Exchange rate gain |        |            |
| 31-Dec-12           | Credit       | 0 CAD/5,000 USD       | Unrealized currency adj profit | Foreign currency revaluation | Exchange rate gain | X      |            |
| 3-Jan-13            | Debit        | 0 CAD/5,000 USD       | AR                             | Foreign currency revaluation | Exchange rate gain |        | X          |
 | 3-Jan-13            | Credit       | 0 CAD/5,000 USD       | Unrealized currency adj profit | Foreign currency revaluation | Exchange rate gain | X      | X          |

### Revaluation (Invoice date method; date = January 1, 2013)

For this revaluation, the entry from January 1, 2013, directly reverses the January 3, 2013 entry. Even the GL accounts and posting types match. Additionally, the **Correction** flag is set.

| Date   | Debit/credit | Amounts | General ledger (GL) account| Transaction type| Posting type| Credit | Correction |
|--------|--------------|---------|----------------------------|----------------|--------|------------|--------------|
|1-Jan-13 | Debit  | 0 CAD/5,000 USD | AR                             | Foreign currency revaluation | Exchange rate gain |   | X |
|1-Jan-13 | Credit | 0 CAD/5,000 USD | Unrealized currency adj profit | Foreign currency revaluation | Exchange rate gain | X | X |
|3-Jan-13 | Debit  | 0 CAD/5,000 USD | AR                             | Foreign currency revaluation | Exchange rate gain |   |   |
|3-Jan-13 | Credit | 0 CAD/5,000 USD | Unrealized currency adj profit | Foreign currency revaluation | Exchange rate gain | X |   |

The system behaves the same way, regardless of whether you set the **Correction** option in the **Transaction reversal** section on the **General ledger parameters** page to **Yes** or **No**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
