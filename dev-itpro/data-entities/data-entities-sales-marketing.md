---
# required metadata

title: Data entities - Sales and marketing (Execution)
description: This article provides a list of the data entities that are available for the Sales and marketing execution functionality in Microsoft Dynamics AX.
author: kfend
manager: AnnBe
ms.date: 2016-06-29 14 - 18 - 43
ms.topic: article
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
ms.custom: 95683
ms.assetid: 1ea2bd7c-5a44-4b92-b954-f5b35b8b4bb1
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Data entities - Sales and marketing (Execution)

This article provides a list of the data entities that are available for the Sales and marketing execution functionality in Microsoft Dynamics AX.

Available data entities
-----------------------

Suggested sequence

Entity name

Area

Entity type

Dependency

Comments

**28.1.011 SLM – Commissions Setup**

1

Commission sales group

Sales and marketing

Setup

None

**28.1.012 SLM - Summary Parameters**

2

Sales summary update parameters

Sales and marketing

Setup

None

**28.1.013 SLM - Sales Order Setup**

3

Sales order pools

Sales and marketing

Setup

None

4

Sales order origin codes

Sales and marketing

Setup

None

5

Sales order hold codes

Sales and marketing

Setup

None

**28.1.014 SLM - Distribution Setup**

6

Terms of delivery

Sales and marketing

Setup

None

7

Delivery modes

Sales and marketing

Setup

None

8

Reason of delivery

Sales and marketing

Setup

None

9

Destination code

Sales and marketing

Setup

None

10

Carrier

Sales and marketing

Setup

None

**28.1.015 SLM - Form Setup**

11

Packing slip form printing configurations

Sales and marketing

Setup

Document type must exist in the system.

12

Sales agreement form printing configurations

Sales and marketing

Setup

Document type must exist in the system.

13

Sales invoice form printing configurations

Sales and marketing

Setup

Document type must exist in the system.

14

Sales order confirmation form printing configurations

Sales and marketing

Setup

Document type must exist in the system.

15

Sales quotation form printing configurations

Sales and marketing

Setup

Document type must exist in the system.

16

Picking list form printing configurations

Sales and marketing

Setup

Document type must exist in the system.

17

Shipment form printing configurations

Sales and marketing

Setup

Document type must exist in the system.

**28.1.016 SLM - Prices Discounts Setup**

18

Trade agreement journal name

Sales and marketing

Setup

None

19

Trade agreement journal table

Sales and marketing

Setup

None

20

Activate sales prices and discounts

Sales and marketing

Setup

None

21

Sales price smart rounding versions

Sales and marketing

Setup

None

22

Sales price smart rounding version rules

Sales and marketing

Setup

None

23

Sales price smart rounding version currencies

Sales and marketing

Setup

None

**28.1.017 SLM - External Item Setup**

24

External item description customer groups

Sales and marketing

Setup

None

25

External item descriptions for customers

Sales and marketing

Setup

None

**28.1.018 SLM - Customer Setup**

26

Customer classification groups

Sales and marketing

Setup

None

**28.1.019 SLM - Supp Item Setup**

27

Supplementary item - customer groups

Sales and marketing

Setup

None

**28.1.020 SLM - Returns Setup**

28

Return reason code groups

Sales and marketing

Setup

None

29

Return reason codes

Sales and marketing

Setup

None

30

Disposition code

Sales and marketing

Setup

None

**28.1.021 SLM - Discount Groups Setup**

31

Line discount customer groups

Sales and marketing

Setup

None

32

Multiline discount customer groups

Sales and marketing

Setup

None

33

Multiline discount item groups

Sales and marketing

Setup

None

**28.1.022 SLM - Policies Setup**

34

Sales type document entry policies

Sales and marketing

Setup

None

35

Sales type document processing policies

Sales and marketing

Setup

None

36

Sales type document default values

Sales and marketing

Setup

None

37

Sales order line update parameters

Sales and marketing

Setup

None

**28.1.023 SLM - SLM Parameters**

38

Campaign creation policies

Sales and marketing

Setup

None

39

Lead processing policies

Sales and marketing

Setup

None

40

Marketing mail policies

Sales and marketing

Setup

None

41

Opportunity maintenance policies

Sales and marketing

Setup

None

42

Prospect creation policies

Sales and marketing

Setup

None

43

Prospect statistics default values

Sales and marketing

Setup

None

44

Sales activity creation policies

Sales and marketing

Setup

None

45

Transaction logging policies

Sales and marketing

Setup

None

**28.1.024 SLM - Sales Agreement Classification**

46

External sales agreement classification

Sales and marketing

Setup

None

47

Sales agreement classification

Sales and marketing

Setup

None

48

Sales agreement classification translation

Sales and marketing

Setup

Sales agreement classification

**28.4.006 SLM - Charges Setup**

49

Customer charge groups

Sales and marketing

Master

None

**28.8.001 SLM - Sales Orders**

50

Sales orders

Sales and marketing

Transactional

None

Demo data that is related to dates. For example, **Requested receipt date** and **Requested ship date** must to be rolled forward to future dates when this data entity is imported by using demo data.

**28.8.002 SLM - Sales Order Lines**

51

Sales order lines

Sales and marketing

Transactional

Sales orders

See also
--------

[Data entities and packages framework](data-entities-data-packages.md)

[Data entities home page](data-entities.md)

