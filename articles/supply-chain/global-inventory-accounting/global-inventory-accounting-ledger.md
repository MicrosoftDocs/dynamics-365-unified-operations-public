---
title: Global Inventory Accounting ledger
description: This topic describes the Global Inventory Accounting ledger, which is defined by its combination of currency, calendar, convention, and association to a legal entity
author: AndersGirke
ms.date: 06/18/2021
ms.topic: article
# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: aevengir
ms.search.validFrom: 2021-06-18
ms.dyn365.ops.version: 10.0.20
---

# Global Inventory Accounting ledger

[!include [banner](../includes/banner.md)]

As with financial ledgers, there is separate ledger for Global Inventory Accounting. The system processes each inventory-related transaction entered in the linked legal entity. A ledger is a register of debit and credit measures. These measures are classified using cost elements and subledger accounts. A Global Inventory Accounting ledger is defined by its combination of currency, calendar, convention, and association to a legal entity.

To set up your Global Inventory Accounting ledgers, go to **Cost management > Cost accounting service> Setup > Cost accounting ledgers**. For each ledger, make the following settings:

- **Name** – Enter the name of the ledger
- **Description** – Enter a description of the ledger
- **Fiscal calendar** – Specify the fiscal calender for the ledger
- **Currency and exchange rate type** – Select the accounting currency used by the ledger and the exchange rate type. This currency can be different from the one used by the legal entity. With Global Inventory Accounting, users can define as many costing ledgers as required. Inventory accounting in multiple currencies and in multiple valuations is supported. Make the following settings on this FastTab:
    - **Currency** - Select the costing currency in which inventory-related values are maintained. For example, inventory value, cost of goods sold, inventory in transit, all kinds of variance, and so on.
    - **Exchange rate type** - Select the exchange rate the system should use to convert the transaction amount in the transaction currency and the standard cost of the items into the costing currency.
- **Convention name** – A convention is a collection of policies that establish how costs will be accounted in this ledger.
- **Legal entity** – This ledger will account the documents posted to the selected legal entity.
- **Priming** – Choose whether to process legacy inventory transactions according to the currency and convention in the ledger. Please note that you will *not* be able to come back to do it after you enter new documents. Select one of the followign values:
    - *Activated* - If you want the ledger to process legacy transactions created before the ledger was created.
    - *Deactivated* - Only include transactions created after the ledger was created.
- **Status** - The system will automatically set the status of newly created ledgers to *Prepare*.
