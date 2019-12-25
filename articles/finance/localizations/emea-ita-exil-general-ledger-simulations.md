---
# required metadata

title: General ledger simulations (Italy)
description: General ledger simulations.
author: ilkond
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

Feature allows to post ledger transactions as simulation from the general journal.
Simulated ledger transactions can be deleted, modified and moved to the real general ledger.
Simulated ledger transactions can be shown in the following reports: **Trial balance**, **Dimension statement**.


## Prerequisites

- The primary address of the legal entity must be in Italy.
- In the **Feature management** workspace, turn on the **General ledger simulations** feature. For more information, see [Feature management overview](../../fin-and-ops/get-started/feature-management/feature-management-overview.md).

## Setup 
### Simulation general journal transfer Number Sequence

Create Number sequence for the Simulation general journal transfer and then setup in the **General ledger parameters**:
1.	Go to **General ledger > Ledger setup > General ledger parameters**.
2.	Click the **Number sequences** tab.
3.	Set the sequence in the field **Simulation general journal transfer**.

### Create Simulation Journal
Go to **General ledger > Journal setup > Journal name** and create Simulation Journal.
Set **Journal type** as **Daily**.
Set **Simulation** to **Yes**.
Set **Requires validation** to **Yes** under **Simulation journal** fields group, to indicate that the journal must be validated before executing simulation posting.


## Use...

### Post

When you post...

> [!NOTE]
> Warning...
