---
# required metadata

title: Ledger journal types
description: This article describes the journal types that you can set up for financial journals.
author: kweekley
ms.date: 10/10/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LedgerJournalSetup
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.assetid: 81613b31-bc3c-43a0-8474-e01c9a482c40
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Ledger journal types

[!include [banner](../includes/banner.md)]

This article describes the journal types that you can set up for financial journals. Use the **Journal names** page to set up journals that you can use throughout Dynamics 365 Finance.

| Journal type                      | Purpose                       | Enter transactions on this page                                |
|-----------------------------------|-------------------------------|----------------------------------------------------------------|
| Allocation                        | Create allocation transactions in an allocations journal. Before you can create an allocation journal, you must create an allocation rule on the **Ledger allocation rule** page.      | Process allocation request             |
| Approval                          | Post vendor invoices that have been approved to the appropriate ledger accounts.  | Invoice approval journal                                       |
| Bank check reversal               | Reverse a posted check. To use this journal type, select the **Use review process for payment reversals** option on the **Cash and bank management parameters** page.   | Check reversals, Payment reversal                   |
| Bank deposit slip cancellation    | Cancel a deposit slip. To use this journal type, select the **Use review process for deposit slip payment cancellations** option on the **Cash and bank management parameters** page.   | Deposit slip payment cancellations            |
| Budget                            | Process budget appropriations. To use this journal type, select the **Enable budget appropriation** option on the **General ledger parameters** page. The budget journal entries will include information that is based on the ledger accounts that are defined on the **Posting definitions** page.                                                        |                                                                |
| Customer accept bill of exchange  | Create customer acceptance transactions for bills of exchange.             | Draw bill of exchange journal, Redraw bill of exchange journal |
| Customer bank remittance          | Create a bill of exchange remittance file that can be sent to your organization’s bank. To use this journal type, clear the **Automatic settlement** option on the **Accounts** **receivable parameters** page.            | Remittance                                                     |
| Customer draw bill of exchange    | Create customer draw bill of exchange transactions. To use this journal type, clear the **Create and post draw journal automatically when posting invoices** option on the **Methods of payment - customers** page.   | Draw bill of exchange journal                                  |
| Customer payment                  | Create customer payment transactions.                             | Payment journal             |
| Customer protest bill of exchange | Create customer protest bill of exchange transactions.                    | Protest bill of exchange journal                               |
| Customer redraw bill of exchange  | Create customer redraw bill of exchange transactions.                     | Redraw bill of exchange journal                                |
| Customer settle bill of exchange  | Create customer settle bill of exchange transactions.                       | Settle bill of exchange journal                                |
| Daily                             | Create daily transactions in a general journal.                          | General journal                                                |
| Elimination                       | Create elimination transactions in an eliminations journal. To use this journal type, select the **Use for financial elimination process** and **Use for financial consolidation process** options on the **Legal entities** page. Before you can use this journal type, you must create a ledger elimination rule on the **Ledger elimination rule** page. | Elimination                                                    |
| Fixed asset budget                | Create fixed asset budget register entries.                                                                                                                                                                                                                                                                                                                 | Fixed asset budget                                             |
| Invoice register                  | Register basic information about vendor invoices.                                                                                                                                                                                                                                                                                                           | Invoice register                                               |
| Payroll disbursement              | Issue payments that are based on Payroll pay statements. You can’t manually enter transactions in this journal. You must generate pay statements and then submit those statements for payment.                                                                                                                                                              |                                                                |
| Periodic                          | Create periodic transactions for the periodic journal.                                                                                                                                                                                                                                                                                                      | Periodic journals                                              |
| Post fixed assets                 | Post fixed asset transactions.                                                                                                                                                                                                                                                                                                                              | Fixed assets                                                   |
| Project - expenses                | Create project expense transactions.                                                                                                                                                                                                                                                                                                                        | Expense                                                        |
| Reporting currency adjustment     | Create adjustments in the reporting currency for balances on ledger accounts.               | Reporting currency adjustment journals                         |
| Statistic transactions            | Create statistical transactions.                                                                                                                                                                                                                                                                                                                            |                                                                |
| Vendor bank remittance            | Create a promissory note remittance file that can be sent to your organization’s bank.                                                                                                                                                                                                                                                                      | Remittance journal                                             |
| Vendor disbursement               | Create vendor disbursement transactions.                                                                                                                                                                                                                                                                                                                    | Payment journal                                                |
| Vendor draw promissory note       | Draw vendor promissory notes as a method of payment. To use this journal type, clear the **Create and post draw journal automatically when posting invoices** option on the **Methods of payment - vendors** page.                                                                                                                                          | Draw promissory note journal                                   |
| Vendor invoice pool excl. posting | Create vendor invoice transactions that haven't yet been posted to a temporary arrival account.                                                                                                                                                                                                                                                             | Vendor invoice pool excluding posting details                  |
| Vendor invoice pool               | Create vendor invoice pool transactions.                                                                                                                                                                                                                                                                                                                    |                                                                |
| Vendor invoice recording          | Post vendor invoices that are in a journal.                                                                                                                                                                                                                                                                                                                 | Invoice journal                                                |
| Vendor redraw promissory note     | Redraw a promissory note that has previously been honored by your organization’s bank.                                                                                                                                                                                                                                                                      | Redraw promissory note journal                                 |
| Vendor settle promissory note     | Create vendor settle promissory note transactions.                                                                                                                                                                                                                                                                                                          | Settle promissory note journal                                 |







[!INCLUDE[footer-include](../../includes/footer-banner.md)]
