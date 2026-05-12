---
title: General ledger simulations (Italy)
description: Learn about posting ledger transactions as a simulation from the general journal and then review reports that include the simulated transactions.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 05/01/2026
ms.reviewer: johnmichalak
ms.search.region: Italy
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: 10.0.9
---

# General ledger simulations

[!include [banner](../../includes/banner.md)]

General ledger simulations enable you to post simulated ledger transactions from the general journal and then review reports that include the simulated transactions.

This feature is available only for legal entities with a primary address in Italy.

You can post simulation transactions only for journal lines where **Account type** and **Offset account type** are both set to **Ledger**.
You can delete the simulated ledger transactions, modify them, and move them to the real general ledger posted transactions.
You can review the posted simulation ledger transactions in the reports, **Trial balance** and **Dimension statement with simulation**.

## Prerequisites

Before you can use the General ledger simulations feature, ensure the following prerequisites are met:

- The primary address of the legal entity is in Italy.
- Enable the **General ledger simulations** feature in the **Feature management** workspace. For more information, see [Feature management overview](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Setup

### Create a number sequence for the simulated general journal transfer

1. Go to **General ledger** > **Ledger setup** > **General ledger parameters**.
1. On the **Number sequences** tab, set the sequence to **Simulation general journal transfer**.

### Create a simulation journal

1. Go to **General ledger** > **Journal setup** > **Journal name** and create a new journal named **Simulation**.
1. Set the **Journal type** to **Daily**.
1. In the **Simulation** field, select **Yes**.
1. In the **Simulation journal** field group, set **Requires validation** to **Yes** to indicate that the journal must be validated before the simulated posting is executed.

## Operations

### Create and post simulation transaction

1. Go to **General Ledger** > **Journal Entries** > **Simulation journals**.
1. Create journal lines as **Ledger - Ledger** in the standard way, and then select **Post** > **Post simulation** to post the simulation transactions. This action makes the transaction effective for simulation calculations, and the journal becomes *simulation posted*.
1. Select **Post** > **Reopen** to make the posted simulation transaction editable.
1. Select **Post** > **Post** to move the posted simulation transaction to an ordinary ledger.

> [!IMPORTANT]
> The function that closes a fiscal period or a fiscal year verifies that the simulation transactions are either posted as typical transactions or deleted. If there are pending simulated general ledger transactions for the period, an error message appears.

## Periodic operations

### Post all simulation transactions

- To post simulation transactions for all simulation journals, go to **Periodic tasks** > **Simulations** > **Post simulation journals**.

- After you post all journals, transactions no longer include simulation transactions.

### Reopen all simulation journals

- To reopen all simulation journals, go to **Periodic tasks** > **Simulations** > **Reopen simulation journals**.

The system reopens all simulation posted simulation journals. You can edit the simulation journals and post simulation again.

### Delete all simulation journals

- To delete all open simulation journals, go to **Periodic tasks** > **Simulations** > **Delete simulation journals**.

## Review simulation transactions in reports

You can review simulation transactions in several ledger reports.

> [!NOTE]
> Simulation transactions don't appear on the Italian fiscal journal until they become real transactions.

### Create a simulation journal name group

1. Go to **General ledger** > **Journal setup** > **Simulations** > **Simulation journal group**.
1. Create a simulation journal group.
1. On the **Simulation journals** tab, select simulation journals to include in this group from the list of available simulation journals.

### Trial balance

1. Go to **General Ledger** > **Inquiries and reports** > **Trial balance**.
1. On the **Parameters** FastTab of the **Trial balance** report header, select a value in the **Simulation journal group** field.
1. Enter other parameters and calculate the balances.
1. Verify that the report contains columns that consider simulation transactions, this includes:

- **Debit (simulation)**
- **Credit (simulation)**
- **Closing balance (with simulations)** - This is the total of the values in the **Closing balance**, **Debit (simulation)** and **Credit (simulation)** columns.

### Dimension statement with simulation

1. Go to **General Ledger** > **Inquiries and reports** > **Ledger reports** > **Dimension statement with simulation**.
1. Set **Simulation journal transactions** to **Yes** in the **Statement by dimension** dialog menu.
1. Select a value in the **Simulation journal group** field, and then select **OK**.
1. Verify that the report contains posted simulation transactions and standard ledger transactions.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
