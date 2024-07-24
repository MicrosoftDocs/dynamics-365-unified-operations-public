---
title: Correspondence of accounts
description: Learn about correspondence of accounts in Russia, including a table that outlines how types of correspondence are affected by correspondence.
author: evgenypopov
ms.author: evgenypopov
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/27/2024
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1
---

# Correspondence of accounts

[!include [banner](../../includes/banner.md)]

Correspondence of accounts is an approach to continuous and interrelated registration of business transactions in corresponding general ledger accounts. It's based on the double-entry bookkeeping system. Ledger vouchers are represented together with corresponding accounts by using the Russian accounting standards.

You can enter multidimensional transactions in the ledger journals and other modules. In most cases, transactions that are automatically created from other modules are multidimensional. These transactions should be changed to two-dimensional. This change might involve splitting ledger transactions. In this case, the following correspondence cases are specified.

<table>
<thead>
<tr>
<th>Type of correspondence</th>
<th>Before correspondence</th>
<th>After correspondence</th>
</tr>
</thead>
<tbody>
<tr>
<td>One-to-one</td>
<td>
<p>Account A 200 (debit transaction)</p>
<p>Account B 200 (credit transaction)</p>
</td>
<td>
<p>Account A – Account B 200</p>
<p>(Two transactions)</p>
</td>
</tr>
<tr>
<td>One-to-many</td>
<td>
<p>Account A 200 (debit transaction)</p>
<p>Account B 160 (credit transaction)</p>
<p>Account C 40 (credit transaction)</p>
</td>
<td>
<p>Account A – Account B 160</p>
<p>Account A – Account C 40</p>
<p>(Four transactions)</p>
</td>
</tr>
<tr>
<td>Many-to-one</td>
<td>
<p>Account A 200 (debit transaction)</p>
<p>Account B 160 (debit transaction)</p>
<p>Account C 360 (credit transaction)</p>
</td>
<td>
<p>Account A – Account C 200</p>
<p>Account B – Account C 160</p>
<p>(Four transactions)</p>
</td>
</tr>
<tr>
<td>Many-to-many</td>
<td>
<p>Account A 200 (debit transaction)</p>
<p>Account B 160 (debit transaction)</p>
<p>Account C 260 (credit transaction)</p>
<p>Account D 100 (credit transaction)</p>
</td>
<td>
<p>Individual processing</p>
<p>(Multiple transactions)</p>
</td>
</tr>
</tbody>
</table>

When the transactions correspondence mechanism is turned on, each new accounting transaction that is created consists of a set of two-way corresponding transactions. When the accounting transactions are posted, the corresponding relationship is automatically defined. If the mechanism isn't turned on, no correspondence relationships are created between transactions.

If any non-corresponding accounts exist before the account correspondence mechanism is turned on, they aren't automatically linked. You must manually define relationships for the transactions.

## Turn on the account correspondence mechanism for accounting transactions 

The account correspondence mechanism lets you create correspondence relations between transactions. Follow these steps to turn it on.

1. Go to **General ledger** \> **Ledger setup** \> **General ledger parameters**.
2. On the **Ledger** tab, set the **Use corresponding mechanism** option to **Yes** to turn on the account correspondence mechanism.

> [!NOTE]
> After the correspondence mechanism is turned on, all new transactions will have correspondence relations. If you can't establish a correspondence link for a transaction, you receive a warning message. Select this message to use the manual transaction correspondence function to manually correspond the transactions.

## Manually define correspondence relations for transactions

Use the manual transaction correspondence function to define a relationship between non-corresponding transactions. When the account correspondence mechanism is turned off in the ledger, all transactions are generated in the usual way. No correspondence link is established between accounts. The manual transaction correspondence function isn't retroactive. When the account correspondence mechanism is turned on, correspondence isn't established for transactions that were performed earlier.

1. Go to **General ledger** \> **Periodic tasks** \> **Manual correspondence**.
2. In the left pane, view the list of vouchers that have been posted.
3. In the **Show only vouchers** field, select which vouchers should be listed:

    - **Not corresponded** − Show only vouchers that have no corresponding ledger transactions.
    - **Corresponded** − Show only vouchers that have corresponding ledger transactions.
    - **All** − Show all vouchers.

4. Select a voucher, and then, on the **Overview** FastTab, view the voucher transactions.
5. On the **Offset** FastTab, follow one of these steps:

    - To correspond selected debit and credit transactions for the selected voucher, select a row in the **Debit transactions** grid, select a row in the **Credit transactions** grid, and then select the **\<-\>** button to correspond the transactions.

    - To automatically correspond all credit and debit transactions for the selected voucher, select the **\<\<-\>\>** button.
    Transactions that have been corresponded are moved to the **Details** grid.
    
 <!--add here screenshot Correspondence-Offset from WI-->

7. On the **Offset** FastTab, select **Save** to save the results or **Restore** to cancel the last change.
8. On the Action Pane, select **Refresh data** to update the data on the **Manual correspondence** page.

To remove the correspondence relations for a voucher, select the voucher in the left pane, and then, on the Action Pane, select **Remove ledger bond**. Then select **Refresh data** to update the data on the page.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
