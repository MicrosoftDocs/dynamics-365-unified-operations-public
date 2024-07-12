---
title: General ledger simulations (Italy)
description: Learn about posting ledger transactions as a simulation from the general journal and then review reports that include the simulated transactions.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/11/2024
ms.reviewer: johnmichalak
ms.search.region: Italy
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: 10.0.9
---

# General ledger simulations

[!include [banner](../../includes/banner.md)]

General ledger simulations allow you to post simulated ledger transactions from the general journal and then review reports that include the simulated transactions.

This feature is available only for legal entities with a primary address in Italy. 

You can post simulation transactions only for journal lines where **Account type** and **Offset account type** are equal to **Ledger**.
You can delete the simulated ledger transactions, modify them, and move them to the real general ledger posted transactions.
You can review the posted simulation ledger transactions in the reports, **Trial balance** and **Dimension statement with simulation**.


## Prerequisites

Before you can use the General ledger simulations, the following prerequisites must be met:

- The primary address of the legal entity is in Italy.
- Enable the **General ledger simulations** feature in the **Feature management** workspace. For more information, see [Feature management overview](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Setup 

### Create a number sequence for the simulated general journal transfer

1.	Go to **General ledger** > **Ledger setup** > **General ledger parameters**.
2.	On the **Number sequences** tab, set the sequence to **Simulation general journal transfer**.

### Create a Simulation journal

1. Go to **General ledger** > **Journal setup** > **Journal name** and create a new journal called 'Simulation'.
2. Set the **Journal type** to **Daily**.
3. In the **Simulation** field, select **Yes**.
4. In the **Simulation journal** field group, set **Requires validation** to **Yes** to indicate that the journal must be validated before the simulated posting is executed.


## Operations

### Create and post simulation transaction

1. Go to **General Ledger** > **Journal Entries** > **Simulation journals**.
2. Create journal lines as **Ledger - Ledger** in the standard way, and then select **Post** > **Post simulation** to post the simulation transactions. This makes the transaction effective for simulation calculations, and the journal becomes *simulation posted*.
3. Select **Post** > **Reopen** to make the posted simulation transaction editable.
4. Select **Post** > **Post** to move the posted simulation transaction to an ordinary ledger.

> [!IMPORTANT]
> The function that closes a fiscal period or a fiscal year verifies that the simulation transactions have been posted as typical transactions or have been deleted. If there are pending simulated general ledger transactions for the period, an error message appears.


## Periodic operations

### Post all simulation transactions 

- To post simulation transactions for all simulation journals, go to **Periodic tasks** > **Simulations** > **Post simulation journals**.

Transactions will be no longer include simulation transactions after all journals are posted.

### Reopen all simulation journals 

- To reopen all simulation journals, go to **Periodic tasks** > **Simulations** > **Reopen simulation journals**.

All simulation posted simulation journals are reopened. You can edit the Simulation journals and post simulation again.

### Delete all simulation journals 

- To delete all open simulation journals, go to **Periodic tasks** > **Simulations** > **Delete simulation journals**. 

## Review simulation transactions in reports

Simulation transactions can be reviewed in several ledger reports.

> [!NOTE] 
> Simulation transactions do not appear on the Italian fiscal journal until they become real transactions.

### Create a Simulation Journal name group 

1. Go to **General ledger** > **Journal setup** > **Simulations** > **Simulation journal group**.
2. Create a simulation journal group. 
3. On the **Simulation journals** tab, select to include simulation journals in this group from the list of available simulation journals. 

### Trial balance

1. Go to **General Ledger** > **Inquiries and reports** > **Trial balance**.
2. On the **Parameters** FastTab of the **Trial balance** report header, select a value in the **Simulation journal group** field.
3. Enter other parameters and calculate the balances.
4. Verify that the report contains columns that consider simulation transactions, this includes:

-	**Debit (simulation)**
-	**Credit (simulation)**
-	**Closing balance (with simulations)** - This is the total of the values in the **Closing balance**, **Debit (simulation)** and **Credit (simulation)** columns.

### Dimension statement with simulation

1. Go to **General Ledger** > **Inquiries and reports** > **Ledger reports** > **Dimension statement with simulation**.
2. Set **Simulation journal transactions** to **Yes** in the **Statement by dimension** dialog menu.
3. Select a value in the **Simulation journal group** field, and then select **OK**.
4. Verify that the report contains posted simulation transactions and standard ledger transactions.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
