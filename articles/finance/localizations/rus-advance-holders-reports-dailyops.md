---
# required metadata

title: Advance reports with budget control (Russia)
description: This topic shows how to generate subledgers from source documents such as invoices, packing slips, and picking lists for customers and vendors. 
author: ShylaThompson
ms.date: 11/16/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: roschlom
ms.dyn365.ops.version: 8.1
ms.search.validFrom: 2018-10-31

---

# Advance reports with budget control (Russia)

[!include [banner](../includes/banner.md)]

An advance report is used to report travel expenses that an employee incurs during a business trip. You can distribute the expense amount across ledger dimensions. You can view the ledger entries and verify the distribution of the expense amount. Advance report posting supports ledger line functions, exchange adjustments, and advance adjustments. If the advance report transactions are split by distribution, the canceled advance report supports the creation of a storno accounting transaction to account the distribution.

For more information, see [Daily operations for advance holders in Russia](rus-advance-holders-daily-operations.md).

## Budget control for advance reports

By using budget control, you can make sure that sufficient funds are available for planned or actual purchases. After you set up basic budgeting, you can set up budget control. You can use budget control to confirm whether budget funds are available on source documents, such as purchase orders, expense reports, advance reports, and accounting journals. If the budget funds exceed the budget limit that is set, additional processing of the document can be prevented.

An advance report is primarily used to report travel expenses that an employee incurs during a business trip. If the expenses that are incurred on an advance report exceed the budget that is set, budget control indicates that the funds aren't available.

To enable budget control for advance reports, follow these steps.

1. On the **Budget control configuration** page, on the **Select source documents** tab, select **Advance reports** as a source document for budget control, and enable budget checks for advance report lines.
2. On the **Budget funds available** tab, define the calculation that determines whether budget funds for advance reports are available.

### Budget calculation

When you define the budget calculation for advance reports, you should consider actual expenditures and unposted actual expenditures.

**Example**

Budget funds available = (Original budget + Budget revisions + Budget transfers) – (Actual expenditures + Unposted actual expenditures)

You can view the actual expenditures and unposted actual expenditures for each advance report line on the **Actual expenditures** page.

### Budget checking

Budget checking for advance reports makes sure that budget funds are available for planned or future expenditures. The budget checking process runs automatically when an advance report line is saved, or when the report is posted.

## Accounting distributions and subledger journals

Subledger journal lines are accounting entries that are posted to the general ledger by using the general journal. You can generate subledgers from source documents such as invoices, packing slips, and picking lists for customers and vendors. Before you post the voucher information to the general ledger, you can view or modify subledger journals by using the distribution method. This method lets you allocate posting amounts among multiple financial dimensions. Depending on your user permissions, you can also change the default ledger account number or financial dimension values. Distributions serve as an interface to the subledger journals and contain only one side of the accounting entry.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]