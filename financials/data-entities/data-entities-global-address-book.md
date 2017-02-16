---
# required metadata

title: Data entities - Global address book
description: This article provides a list of the data entities that are available for the Global address book functionality in Microsoft Dynamics 365 for operations.
author: kfend
manager: AnnBe
ms.date: 2016-06-29 14 - 19 - 07
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
ms.custom: 95803
ms.assetid: f950dd8e-25fd-41d1-8ef9-c9fc13a7c5bd
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.dyn365.ops.intro: Feb-16
ms.dyn365.ops.version: AX 7.0.0

---

# Data entities - Global address book

This article provides a list of the data entities that are available for the Global address book functionality in Microsoft Dynamics 365 for operations.

Available data entities
-----------------------

Suggested sequence

Entity name

Area

Entity type

Dependency

Comments

**02.1.001 GAB - Teams**

**For Teams:** If user names are associated with **Administrator**, clear the selection of those user names during import. Then reimport the Teams data entity after employees and users have been imported into the system.

1

Team types

Organization administration

Setup

None

Categorize teams, and restrict membership to specific groups of people, such as contractors. This entity is part of Organization administration.

2

Teams

Organization administration

Setup

Team types

**02.1.002 GAB - Post address setup**

If you're using demo data, some Party relationships and Party postal addresses records will fail during import because of known issues that involve those data entities. The specific error will be related to a value for **Expiration** that isn't valid. You might see the same error on your own data set. The People data entity can be used to relate people and parties. This step is optional if your purpose is just to export people from the legal entity and import people into it. However, the Global address book data entity will bring in relationships for vendors, customers, employees, leads, opportunities, contact person, and others.

3

Global address book

Organization administration

Setup

Team types

Stores party record information for each organization or person that your organization has contact with, such as customers, vendors, competitors, and workers. A party is a person or organization that is either internal or external to your organization. Each party has its own record. **Note: **Before import, delete the **OperatingUnitTypeStr** column.

4

Party relationships

Organization administration

Setup

Global address book

Define relationships between parties.

5

Party postal addresses

Organization administration

Setup

Global address book

Postal address information that is related to a party.

6

Party contacts

Organization administration

Setup

Global address book

Define electronic contacts for parties.

7

\*People

Organization administration

Setup

Global address book

Define relationships between parties and people.

\*This optional data entity that is used to export and import isn't part of the data package that is available in Microsoft Dynamics Lifecycle Services (LCS).

See also
--------

[Data entities and packages framework](data-entities-data-packages.md)

[Data entities home page](data-entities-home-page.md)

