---
# required metadata

title: Data entities - Procurement and sourcing | Microsoft Docs
description: This article provides a list of the data entities that are available for the Procurement and sourcing functionality in Microsoft Dynamics AX.
author: kfend
manager: AnnBe
ms.date: 2016-06-29 14:19:42
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
ms.custom: 95983
ms.assetid: 8e866f01-b02e-4554-94a4-96918e5c0a0f
ms.region: Global
# ms.industry: 
ms.author: kfend

---

# Data entities - Procurement and sourcing

This article provides a list of the data entities that are available for the Procurement and sourcing functionality in Microsoft Dynamics AX.

Available data entities
-----------------------

Suggested sequence

Entity name

Area

Entity type

Dependency

Comments

**23.1.001 PRO - Summary parameters**

1

Purchase summary update parameters

Procurement and sourcing

Setup

None

**23.1.002 PRO - Purchase order setup**

2

Purchase pools

Procurement and sourcing

Setup

None

**23.1.003 PRO - Distribution setup**

3

Terms of delivery

Procurement and sourcing

Setup

None

4

Modes of delivery

Procurement and sourcing

Setup

None

5

Destination code

Procurement and sourcing

Setup

None

**23.1.004 PRO - Form setup**

6

Request for quotation form printing configurations

Procurement and sourcing

Setup

Document type

7

Purchase requisition form printing configurations

Procurement and sourcing

Setup

Document type

8

Purchase order form printing configurations

Procurement and sourcing

Setup

Document type

9

Receipt list form printing configurations

Procurement and sourcing

Setup

None

10

Product receipt form printing configurations

Procurement and sourcing

Setup

None

11

Purchase agreement form printing configurations

Procurement and sourcing

Setup

Document type

12

Purchase inquiry form printing configurations

Procurement and sourcing

Setup

None

**23.1.005 PRO - Prices discounts setup**

13

Trade agreement journal name

Procurement and sourcing

Setup

None

14

Trade agreement journal table

Procurement and sourcing

Setup

None

15

Activate purchase prices and discounts

Procurement and sourcing

Setup

None

**23.1.006 PRO - External item setup**

16

External item description vendor groups

Procurement and sourcing

Setup

None

17

External item descriptions for vendors

Procurement and sourcing

Setup

None

**23.1.007 PRO - Vendor setup**

18

Vendor groups

Procurement and sourcing

Setup

None

19

Line of business

Procurement and sourcing

Setup

None

20

Approved vendor list by products

Procurement and sourcing

Setup

Vendors, Released products

**23.1.008 PRO - Supp item setup**

21

Supplementary item - item groups

Procurement and sourcing

Setup

None

22

Supplementary item - vendor groups

Procurement and sourcing

Setup

None

**23.1.009 PRO - Rebate setup**

23

Item rebate groups

Procurement and sourcing

Setup

None

24

Vendor rebate group

Procurement and sourcing

Setup

None

25

Vendor rebate parameters

Procurement and sourcing

Setup

None

**23.1.010 PRO - Price tol setup**

26

Price tolerance setup

Procurement and sourcing

Setup

None

**23.1.011 PRO - Discount groups setup**

27

Line discount vendor groups

Procurement and sourcing

Setup

None

28

Multiline discount item groups

Procurement and sourcing

Setup

None

29

Multiline discount vendor groups

Procurement and sourcing

Setup

None

30

Total discount vendor groups

Procurement and sourcing

Setup

None

**23.1.012 PRO - Policies setup**

31

Procurement type document entry policies

Procurement and sourcing

Setup

None

32

Procurement type document processing policies

Procurement and sourcing

Setup

Trade agreement journal name

33

Procurement type document default values

Procurement and sourcing

Setup

Purchase pools, Return actions

34

Purchase line update parameters

Procurement and sourcing

Setup

None

**23.1.013 PRO - Purchase agreement classification**

35

External purchase agreement classification

Procurement and sourcing

Setup

None

36

Purchase agreement classification

Procurement and sourcing

Setup

None

37

Purchase agreement classification translation

Procurement and sourcing

Setup

Purchase agreement classification

**23.4.002 PRO - Purchase agreements**

38

Purchase agreements

Procurement and sourcing

Master

Purchase agreement classification

**23.4.003 PRO - Purchase agreement lines**

39

Purchase agreement lines

Procurement and sourcing

Master

Purchase agreements, Released products

**23.4.001 PRO - Charges setup**

40

Item charge groups

Procurement and sourcing

Master

None

41

Vendor charges group

Procurement and sourcing

Master

None

**23.8.001 PRO - Purchase orders**

42

Purchase orders

Procurement and sourcing

Transactional

None

**23.8.002 PRO - Purchase order lines**

43

Purchase order lines

Procurement and sourcing

Transactional

Purchase orders, Approved vendor list by products

See also
--------

[Data entities and packages framework](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/data-entities/using-data-entities-and-data-packages)

[Data entities home page](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/data-entities/data-entities-home-page)

