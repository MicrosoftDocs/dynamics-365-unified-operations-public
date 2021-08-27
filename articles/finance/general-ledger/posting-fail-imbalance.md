---
# required metadata

title: Journal posting failure because of imbalance
description: This topic explains why debits and credits might not be balanced in voucher transactions, so that the transactions can't be posted. The topic also includes steps for fixing the issue.
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

# Journal posting failure because of imbalance

[!include [banner](../includes/banner.md)]

This topic explains why debits and credits might not be balanced in voucher transactions, so that the transactions can't be posted. The topic also includes steps for fixing the issue.

## Symptom

In some cases, a journal can't be posted, and the following message is shown: "The transactions on a specific voucher don't balance as of a certain date (accounting currency: 0.01 - reporting currency: 0.06)." Why can't the journal be posted?

## Resolution

During posting to General ledger, every voucher must be balanced in the transaction currency, accounting currency, and reporting currency, if those currencies are defined on the **Ledger setup** page. (Vouchers are balanced when the total debits equal the total credits.)

At the bottom of the journal lines page, totals are shown in the accounting currency and reporting currency. They are **not** shown in the transaction currency for foreign currency transactions. Additionally, the error message that users receive during simulation or posting shows the differences only in the accounting currency and reporting currency. It doesn't show them in the transaction currency, because a single voucher can have more than one transaction currency, and the journal can include vouchers in different transaction currencies. Therefore, it's important that you verify that the transaction currency amounts for every voucher are balanced.

### Transaction currency

During simulation and posting, the system verifies that every voucher is balanced in the transaction currency. For every voucher that is entered, there can be one or more currencies for the transaction currency. For example, a voucher that is entered in the general journal might have two transaction currencies when cash is transferred from a bank account that uses euros (EUR) to a bank account that uses Canadian dollars (CAD).

If a voucher has only one transaction currency, the total debits must equal the total credits for that voucher. Customers have encountered the following scenarios where the posting correctly failed because the transaction currency amounts weren't balanced:

- The total debits and total credits were **not** balanced in the transaction currency, but they were balanced for the accounting currency and reporting currency. A customer assumed that the voucher would still be posted. However, that assumption was incorrect. **The transaction currency amounts on a voucher must always be balanced when all lines of the voucher have the same currency.**
- The voucher was imported through Microsoft Excel, and the user thought that the transaction currency amounts were balanced. In the Excel workbook, the amounts that were imported were set as **Numeric** values, not **Currency** values. In this scenario, the numeric amounts in the workbook had more than two decimal places, and more than two decimal places were included when the amounts were imported. Therefore, the debits didn't equal the credits, because they were off by a fraction of a penny. The journal didn't reflect this difference on the lines of the voucher, because the amounts that are shown have only two decimal places.
- The voucher was imported through Excel, and the user thought that the transaction currency amounts were balanced. Although the voucher was balanced, some lines on the voucher had different transaction dates. If you added the total debits and total credits per voucher and transaction date, they weren't balanced. The system now prevents this scenario. A voucher can have only one transaction date. This requirement is enforced when you enter a voucher through the general journal in the system. However, it wasn't originally enforced when a voucher was imported through Excel.

In one supported scenario, a voucher can have more than one transaction currency. In this case, the system does **not** verify that the debits equal the credits in the transaction currency, because the currencies don't match. Instead, the system verifies that the accounting currency amounts are balanced.

### Accounting currency

If all the lines of a voucher have the same transaction currency, and if the transaction currency amounts are balanced, the system verifies that the accounting currency amounts are balanced. If the voucher is entered in a foreign currency, the exchange rate on the voucher lines is used to translate the transaction currency amounts to the accounting currency. First, each line of the voucher is translated. Then the lines are summed to determine the total debits and total credits. Because each line is translated, the total debits and total credits might not be balanced. Nevertheless, if the difference is within the **Maximum penny difference** value that is defined on the **General ledger parameters** page, the voucher will be posted, and the difference will automatically be posted to the Penny difference account.

If the voucher has more than one transaction currency, each line of the voucher is translated to the accounting currency, and then the lines are summed to determine the total debits and total credits. To be considered balanced, the debits and credits must be balanced, and there must be no penny rounding difference.

### Reporting currency

If all the lines of a voucher have the same transaction currency, and if the transaction currency amounts are balanced, the system verifies that the reporting currency amounts are balanced. If the voucher is entered in a foreign currency, the exchange rate on the voucher lines is used to translate the transaction currency amounts to the reporting currency. First, each line of the voucher is translated. Then the lines are summed to determine the total debits and total credits. Because each line is translated, the total debits and total credits might not be balanced. Nevertheless, if the difference is within the **Maximum penny-rounding in the reporting currency** value that is defined on the **General ledger parameters** page, the voucher will be posted, and the difference will automatically be posted to the Penny difference account.

If the voucher has more than one transaction currency, each line of the voucher is translated to the reporting currency, and then the lines summed to determine the total debits and total credits. To be considered balanced, the debits and credits must be balanced, and there must be no penny rounding difference.
