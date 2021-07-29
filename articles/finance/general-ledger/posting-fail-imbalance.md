---
# required metadata

title: Journal posting failure due to imbalance 
description: This topic describes the reasons why debits and credits might not be in balance in voucher transactions, which will prevent the transactions from posting. The topic also includes steps for resolving the issue.
author: kweekley
ms.date: 08/03/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global 
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2021-8-03
ms.dyn365.ops.version: 10.0.14

---

# Journal posting failure due to imbalance

[!include [banner](../includes/banner.md)]

This topic describes the reasons why debits and credits might not be in balance in voucher transactions, which will prevent the transactions from posting. The topic also includes steps for resolving the issue. 

## Symptom

In some cases, a journal can’t be posted and the message “The transactions on a specific voucher don’t balance as of a certain date (accounting currency: 0.01 - reporting currency: 0.06)” is displayed. Why can’t the journal be posted? 

## Resolution

When posting to General ledger, each voucher must balance (Total debits = Total credits) in the transaction currency, accounting currency and reporting currency (if those currencies are defined on the **Ledger setup** page). The totals shown at the bottom of the journal lines page are for the accounting and reporting currency amounts; totals are *not* shown in the transaction currency for foreign currency transactions. Also, the error message presented to the user during simulation or posting doesn’t display the differences in the transaction currency amounts, but only in the amounts in the accounting and reporting currencies. This is because a single voucher can have more than one transaction currency, and the journal can include vouchers in different transaction currencies. Because of this, it’s important to verify that the transaction currency amounts for each voucher are in balance.

### Transaction currency

During simulation and posting, the system verifies that each voucher is balanced in the transaction currency. Each voucher can be entered with one ore more currencies for the transaction currency. For example, a voucher could be entered in the general journal with two transaction currencies when transferring cash from a EUR bank account to a CAD bank account.

If the voucher has only one transaction currency, the total debits must equal the total credits for each voucher. The following scenarios have been encountered by customers where the posting correctly failed because the transaction currency amounts didn’t balance:

- The total debits and total credits were *not* in balance in the transaction currency, but the total debits and total credits balanced for the accounting currency and reporting currency. A customer assumed the voucher would still post. That assumption is incorrect. **The transaction currency amounts on a voucher must always be in balance when the same currency exists on all lines of the voucher**.

- The voucher was imported through Excel, and the user thought the transaction currency amounts were in balance. The amounts imported were set as Numeric, not Currency, in the spreadsheet. In this situation, the numeric amounts in the spreadsheet included more than two decimal places, which is how they were imported. The debits didn’t equal the credits as a result, because they were off by a fraction of a penny. The journal didn’t reflect this difference on the lines of the voucher because the amounts only display with two decimal places. 

- The voucher was imported through Excel, and the user thought the transaction currency amounts were in balance. The voucher was in balance but some lines within the voucher had different transaction dates. If you added the total debits and total credits per voucher and transaction date, they weren’t in balance. that the system now prevents this scenario. A voucher can only have one transaction date. This is enforced when you enter a voucher through the general journal in the system, but it wasn’t originally enforced when importing through Excel.

If a voucher has more than one transaction currency (which is a supported scenario), the system does *not* verify that the debits equal credits in the transaction currency because the  currencies don’t match. Instead, it verifies that the accounting currency amounts are in balance.

### Accounting currency
If the transaction currency is the same for all the lines on the voucher, and if the transaction currency is in balance, the system will verify  that the accounting currency is in balance.  If the voucher is entered in a foreign currency, the transaction currency amounts are translated to the accounting currency using the exchange rate on the line of the voucher.  Each line of the voucher is translated first, and then summed to determine the total debits and total credits.  Due to the translation of each line, the total debits and total credits might not be in balance. As long as the difference is within the Maximum penny difference that’s defined on the **General ledger parameters** page, the voucher will post, with the difference automatically posted to the Penny difference account.

If the voucher has more than one transaction currency, each line of the voucher is translated to the accounting currency and then summed to determine the total debits and total credits.  They debits and credits must balance, with no penny rounding difference, to be considered in balance. 

### Reporting currency
If the transaction currency is the same for all lines on a voucher, and if the transaction currency is in balance, the system also verifies that the reporting currency is in balance.  If the voucher is entered in a foreign currency, the transaction currency amounts are translated to the reporting currency using the exchange rate on the voucher line.  Each line of the voucher is translated first, and then summed to determine the total debits and total credits.  Because each line is translated, the total debits and total credits might not be in balance. As long as the difference is within the **Maximum penny-rounding in the reporting currency** defined on the **General ledger parameters** page, the voucher will post, with the difference automatically posted to the Penny difference account. 

If the voucher has more than one transaction currency, each line of the voucher is translated to the reporting currency and then summed to determine the total debits and total credits.  They must be in balance, with no penny rounding difference, to be considered in balance.
