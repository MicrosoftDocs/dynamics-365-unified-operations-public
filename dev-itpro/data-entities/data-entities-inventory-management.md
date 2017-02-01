---
# required metadata

title: Data entities - Inventory management | Microsoft Docs
description: This article provides a list of the data entities that are available for the Inventory management functionality in Microsoft Dynamics 365 for Operations.
author: kfend
manager: AnnBe
ms.date: 2016-06-29 14:19:52
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: 51
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 96043
ms.assetid: 6c4503d8-d671-451e-8387-7f51d04888a7
ms.region: Global
# ms.industry: 
ms.author: kfend

---

# Data entities - Inventory management

This article provides a list of the data entities that are available for the Inventory management functionality in Microsoft Dynamics 365 for Operations.

Available data entities
-----------------------

Suggested sequence

Entity name

Area

Entity type

Dependency

Comments

**19.1.001 INV - Site setup**

1

Inventory status

Inventory management

Setup

None

2

Sites

Inventory management

Setup

Inventory status

3

Site current postal addresses

Inventory management

Setup

Sites

This is a shared data entity. Filter this entity by company.

**19.1.002 INV - Warehouse setup**

4

Warehouse workers

Inventory management

Setup

HCM Worker

5

Warehouse location types

Inventory management

Setup

None

6

Warehouses

Inventory management

Setup

Quarantine warehouse, Transit warehouse, Identification group warehouse worker

Complete one of these steps:

-   Import the warehouse data package multiple times.
-   Sort the import data so that dependent warehouses are created later.
-   Create quarantine and transit warehouses before you create other warehouses that depend on this data.

7

Inventory aisle

Inventory management

Setup

Warehouses

8

Warehouse locations

Inventory management

Setup

Inventory aisle, Warehouse location types

**19.1.003 INV - Group setup**

9

Tracking number groups

Inventory management

Setup

None

10

Item groups

Inventory management

Setup

Purchase item sales tax group, Sales item sales tax group

11

Item model group inventory policies

Inventory management

Setup

None

12

Buyer groups

Inventory management

Setup

None

13

Counting groups

Inventory management

Setup

None

**19.1.004 INV - Journal setup**

14

Inventory movement journal names

Inventory management

Setup

None

15

Inventory adjustment journal names

Inventory management

Setup

None

16

Inventory transfer journal names

Inventory management

Setup

None

17

Inventory counting journal names

Inventory management

Setup

None

18

Inventory tag counting journal names

Inventory management

Setup

None

19

Bill of materials journal names

Inventory management

Setup

None

**19.1.005 INV - Packing setup**

20

Packing material groups

Inventory management

Setup

None

21

Packing material codes

Inventory management

Setup

Units

22

Packing material fees

Inventory management

Setup

Packing material codes

**19.1.006 INV - Posting definitions**

23

Ledger posting definition for inventory

Inventory management

Setup

None

24

Ledger posting definition for procurement

Inventory management

Setup

Product categories, Products

25

Ledger posting definition for production

Inventory management

Setup

None

26

Ledger posting definition for sales

Inventory management

Setup

None

27

Ledger posting definition for standard cost variance

Inventory management

Setup

None

**19.1.007 INV - Price discount setup**

28

Line discount item groups

Inventory management

Setup

None

29

Item price tolerance groups

Inventory management

Setup

None

30

Price customer groups

Inventory management

Setup

None

31

Price vendor groups

Inventory management

Setup

None

**19.1.008 INV - Inventory parameters**

32

Inventory dimensions parameters

Inventory management

Setup

None

33

Inventory parameters

Inventory management

Setup

Inventory dimensions parameters, Calculation groups

**19.4.001 INV - Charge groups**

34

Item charge groups

Inventory management

Master

None

35

Customer charge groups

Inventory management

Master

None

36

Vendor charges group

Inventory management

Master

None

**19.8.001 INV - Inventory movement journals**

37

Inventory movement journal headers and lines

Inventory management

Transactional

Released products, Released product variants

Exports all journal entries (posted and unposted). If a journal number isn't specified in the import file, a new journal is created for every 1,000 lines. If a journal number is specified in the import file, the unposted journal header record must exist in Microsoft Dynamics 365 for Operations before import. The import file should contain fewer than 1,000 lines.

**19.8.002 INV - Inventory adjustment journals**

38

Inventory adjustment journal headers and lines

Inventory management

Transactional

Released products, Released product variants

Exports all journal entries (posted and unposted). If a journal number isn't specified in the import file, a new journal is created for every 1,000 lines. If a journal number is specified in the import file, the unposted journal header record must exist in Dynamics 365 for Operations before import. The import file should contain fewer than 1,000 lines.

See also
--------

[Data entities and packages framework](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/data-entities/using-data-entities-and-data-packages)

[Data entities home page](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/data-entities/data-entities-home-page)

