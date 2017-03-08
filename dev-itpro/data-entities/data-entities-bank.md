---
# required metadata

title: Data entities - Bank
description: This article provides a list of the data entities that are available for the Bank and cash management functionality in Microsoft Dynamics AX.
author: kfend
manager: AnnBe
ms.date: 2016-06-29 14 - 19 - 20
ms.topic: reference
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 95863
ms.assetid: 3e2212f7-c34c-4034-a0fa-cbf382eb0c8d
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.dyn365.ops.intro: 01-02-2016
ms.dyn365.ops.version: AX 7.0.0

---

# Data entities - Bank

This article provides a list of the data entities that are available for the Bank and cash management functionality in Microsoft Dynamics AX.

Available data entities
-----------------------

Suggested sequence

Entity name

Area

Entity type

Dependency

Comments

**03.1.001 BANK – Bank setup**

1

Bank transaction type

Bank

Setup

None

Define the types of transactions that are made in company bank accounts, such as deposit slips, fees, and interest charges.

2

Bank transaction groups

Bank

Setup

Bank transaction type

Define groups of bank transaction types.

3

Bank parameters

Bank

Setup

None

Define the legal entity’s Cash and bank management parameters.

4

Payment purpose codes

Bank

Setup

None

Define payment purpose codes for the central bank, if it's required.

5

Customer charge groups

Accounts receivable

Setup

None

Define charges groups for customers or vendors.

**03.1.002 BANK – Bank accounts**

**Note:** To help guarantee a successful import, you might have to unmap some fields or attributes that are set on the bank account. If these fields haven't all been imported yet, you can add the entities to the Bank setup package.

6

Bank groups

Bank

Setup

None

Define general information about the bank groups that you have accounts in.

7

Bank accounts

Bank

Setup

Bank groups

Define bank accounts.

8

Check layout

Bank

Setup

Bank accounts

Define the layout of checks for the bank accounts.

See also
--------

[Data entities and packages framework](data-entities-data-packages.md)

[Data entities home page](data-entities-home-page.md)

