---
# required metadata

title: General ledger simulations (Italy)
description: General ledger simulations.
author: anasyash
manager: AnnBe
ms.date: 11/15/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Italy
# ms.search.industry: 
ms.author: ilyako
ms.search.validFrom: 2020-06-01
ms.dyn365.ops.version: 10.0.9

---

# General ledger simulations

[!include [banner](../includes/banner.md)]

Feature allows to post ledger transactions as simulation from the general journal. Simulation feature is avaiable only for journal lines with both **Account type** and **Offset account type** equal to **Ledger**.
Posted simulation ledger transactions can be deleted, modified and moved to the real general ledger posted transactions.
Posted simulation ledger transactions can be shown in the reports **Trial balance** and **Dimension statement**.


## Prerequisites

- The primary address of the legal entity must be in Italy.
- In the **Feature management** workspace, turn on the **General ledger simulations** feature. For more information, see [Feature management overview](../../fin-and-ops/get-started/feature-management/feature-management-overview.md).

## Setup 

### Create Number sequence for Simulation general journal transfer.

Create Number sequence for the Simulation general journal transfer and then setup in the **General ledger parameters**:
1.	Go to **General ledger > Ledger setup > General ledger parameters**.
2.	Click the **Number sequences** tab.
3.	Set the sequence in the field **Simulation general journal transfer**.

### Create Simulation Journal
1. Go to **General ledger > Journal setup > Journal name** and create Simulation Journal.
2. Set **Journal type** as **Daily**.
3. Set **Simulation** to **Yes**.
4. Set **Requires validation** to **Yes** under **Simulation journal** fields group, to indicate that the journal must be validated before executing simulation posting.


## Operations

### Create and post simulation transaction
1. Go to **General Ledger > Journal Entries > Simulation journals**
2. Create journal lines as Ledger - Ledger in standard way.
3. Post simulation transaction by clicking **Post > Post simulation**. This makes the transaction effective for simulation calculations, and the journal becomes “simulation posted”.
4. Make posted simulation transaction editable by clicking **Post > Reopen**
5. Move posted simulation transaction to ordinary ledger by clicking **Post > Post**

It is important to keep in mind that the function that closes a fiscal period or a fiscal year checks that the simulation transactions are either posted as normal transaction or deleted. Consequently if there are pending simulated general ledger transactions for the period, an error message appears.

## Review simulation transactions in reports

Simulation transactions can be reviewed in several ledger reports.
Please note, that simulation transactions do not appear on the Italian fiscal journal until they become real transactions.

### Create Simulation Journal name group 
Go to **General ledger > Journal setup > Simulations > Simulation journal group**.
Create simulation journal group. On the **Simulation journals** tab, include simulation journals to this group from the list of available simulation journals. 

### Trial balance
Go to **General Ledger > Inquiries and reports > Trial balance**.
Select **Simulation journal group** on the **Parameters** FastTab of the **Trial balance** report header.
Review that report contains columns which consider simulation tansactions:
-	**Debit (simulation)**
-	**Credit (simultion)**
-	**Closing balance (with simulations)** which is the total of the values in **Closing balance**, **Debit (simulation)** and **Credit (simultion)**.


> [!NOTE]
> Warning...
