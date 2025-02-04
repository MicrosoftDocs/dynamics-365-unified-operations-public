---
title: Global Inventory Accounting ledger
description: Learn about Global Inventory Accounting ledgers, which are defined by a combination of a currency, a calendar, a convention, and an association with a legal entity.
author: prasungoel
ms.author: prasungoel
ms.topic: article
ms.date: 06/18/2021
ms.reviewer: kamaybac
ms.search.form:
---

# Global Inventory Accounting ledger

[!include [banner](../includes/banner.md)]

Global Inventory Accounting has its own set of ledgers. Each time an inventory-related transaction is processed for a relevant legal entity, the system can account for that transaction in any number of Global Inventory Accounting ledgers, as required.

A ledger is a register of debit and credit measures. These measures are classified by using cost elements and subledger accounts. A Global Inventory Accounting ledger is defined by its combination of a currency, a calendar, a convention, and an association with a legal entity.

To set up your Global Inventory Accounting ledgers, go to **Global inventory accounting \> Setup \> Global inventory accounting ledgers**. For each ledger, set the following fields:

- **Name** – Enter the name of the ledger.
- **Description** – Enter a description of the ledger.
- **Fiscal calendar** – Specify the fiscal calendar for the ledger.
- **Currency and exchange rate type** – Use the fields on this FastTab to select the accounting currency that the ledger uses, and the exchange rate type. The currency that you select can differ from the currency that the legal entity uses. In Global Inventory Accounting, users can define as many costing ledgers as they require. Global Inventory Accounting supports inventory accounting in multiple currencies and in multiple valuations. Set the following fields:

    - **Currency** – Select the costing currency that inventory-related values are maintained in. These values include the inventory value, cost of goods sold, inventory in transit, and all kinds of variance.
    - **Exchange rate type** – Select the exchange rate that the system should use to convert the transaction amount in the transaction currency and the standard cost of the items into the costing currency.

- **Convention name** – Specify a convention. A convention is a collection of policies that establish how costs will be accounted in this ledger.
- **Legal entity** – The ledger will account the documents that are posted to the selected legal entity.
- **Priming** – Select whether inventory transactions that were created before the ledger was created should be processed according to the currency and convention in the ledger. Select one of the following values:

    - **Activated** – The ledger should process transactions that were created before the ledger was created.
    - **Deactivated** – The ledger should process only transactions that are created after the ledger was created.

    > [!IMPORTANT]
    > You will **not** be able to come back and set this field after you enter new documents.

- **Status** – The system automatically sets the status of newly created ledgers to *Prepare*.
