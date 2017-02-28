---
# required metadata

title: Data entities - Product information management
description: This article provides a list of the data entities that are available for the Product information management functionality in Microsoft Dynamics AX.
author: kfend
manager: AnnBe
ms.date: 2016-06-29 14 - 19 - 37
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
ms.custom: 95953
ms.assetid: 2d8ca9fc-e231-41f0-9fbc-d17a7f7c6892
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.dyn365.ops.intro: 01-02-2016
ms.dyn365.ops.version: AX 7.0.0

---

# Data entities - Product information management

This article provides a list of the data entities that are available for the Product information management functionality in Microsoft Dynamics AX.

Available data entities
-----------------------

Suggested sequence

Entity name

Area

Entity type

Dependency

Comments

**24.1.001 PIM - Dimension groups - Shared**

1

Storage dimension groups

Product information management

Setup

None

2

Tracking dimension groups

Product information management

Setup

None

3

Product dimension groups

Product information management

Setup

None

**24.1.002 PIM - Product variant groups - Shared**

4

Sizes

Product information management

Setup

None

5

Product size groups

Product information management

Setup

None

6

Colors

Product information management

Setup

None

7

Product color groups

Product information management

Setup

None

8

Styles

Product information management

Setup

None

9

Product style groups

Product information management

Setup

None

**24.1.003 PIM - Size assignments** **- Shared**

10

Product size group lines

Product information management

Setup

Sizes, Product size groups

11

Product size group line translations

Product information management

Setup

Product size group lines

**24.1.004 PIM - Color assignments** **- Shared**

12

Product color group lines

Product information management

Setup

Colors, Product color groups

13

Product color group line translations

Product information management

Setup

Product color group lines

**24.1.005 PIM - Style assignments** **- Shared**

14

Product style group lines

Product information management

Setup

Styles, Product style groups

15

Product style group line translations

Product information management

Setup

Product style group lines

**24.1.006 PIM - Category setup** **- Shared**

16

Product category hierarchies

Product information management

Setup

None

17

Product category hierarchy roles

Product information management

Setup

None

18

Product category hierarchy translations

Product information management

Setup

None

19

Product categories

Product information management

Setup

None

**24.1.007 PIM - Attribute types** **- Shared**

20

Product attribute enumeration types

Product information management

Setup

None

21

Product attribute enumeration type translations

Product information management

Setup

Product attribute enumeration types

22

Product attribute value types

Product information management

Setup

Units

**24.1.008 PIM - Product attributes** **- Shared**

23

Product attributes

Product information management

Setup

Product attribute enumeration types

24

Product attribute translations

Product information management

Setup

Product attributes

**24.4.001 PIM - Attribute groups** **- Shared**

25

Attribute group

Product information management

Master

None

**24.4.002 PIM - Products** **- Shared**

26

Products

Product information management

Master

None

**24.4.003 PIM - Product UOM conversions** **- Shared**

27

Product specific unit conversions

Product information management

Master

Products, Units

**24.4.004 PIM - Product variants** **- Shared**

28

Product variants

Product information management

Master

None

**24.4.005 PIM - Released product creation**

29

Released product creation

Product information management

Master

None

Used to create shared products and released products that have basic attributes when the Shared products data entity fails.

**24.4.006 PIM - Released products**

30

Released products

Product information management

Master

Products

**24.4.007 PIM - Released product variants**

31

Released product variants

Product information management

Master

Released products

**24.4.008 PIM - Category Attributes**

32

Product category attributes

Product information management

Master

Product categories

**24.4.009 PIM - Attribute values**

33

Product attribute values

Product information management

Master

Product category attributes

See also
--------

[Data entities and packages framework](data-entities-data-packages.md)

[Data entities home page](data-entities-home-page.md)

