---
# required metadata

title: Data entities - Workflow
description: This article provides a list of the data entities that are available for the Workflow functionality in Microsoft Dynamics 365 for Operations.
author: kfend
manager: AnnBe
ms.date: 2016-06-29 14 - 19 - 13
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
ms.custom: 95833
ms.assetid: 52ff351c-7eb5-4bf3-9aa4-0144413a3ff0
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.dyn365.ops.intro: Feb-16
ms.dyn365.ops.version: AX 7.0.0

---

# Data entities - Workflow

This article provides a list of the data entities that are available for the Workflow functionality in Microsoft Dynamics 365 for Operations.

Available data entities
-----------------------

These entities should be used as a mechanism to move existing and tested workflows between Microsoft Dynamics 365 for Operations environments. The IDs in these entities aren't intended to be created manually. Because of the length of some fields in the workflow data entities, the target data format must be comma-separated values (CSV). The CSV format can cause issues where preceding zeros (0) appear in some fields if the files are open between export and import. Be aware that some fields in a CSV file might show “151”, for example, whereas the actual value is 00151. Additionally, some fields might be split into different columns because of length.

Suggested sequence

Entity name

Area

Entity type

Dependency

Comments

**02.1.003 WF – Workflow** **- SHARED**

1

Expression

Workflow

Setup

None

The overall picture of the workflow **Note:** If you're using demo data, two expressions will fail on import. The failure of these two expressions will cause records to fail in other data entities in this package that depend on the Expression entity.

2

Workflow version

Workflow

Setup

Users, Expression

The list of all workflows that have ever been activated **Note:** Because of a known issue that involves Workflow owners in the demo data, several records will fail on import. The data has been corrected in the packages that are available on Microsoft Dynamics Lifecycle Services (LCS)*.*

3

Workflow version notes

Workflow

Setup

Workflow version

Notes that document the changes that were made to the previous version

4

Workflow version notification

Workflow

Setup

Workflow version notes

The notification that is provided together with the version

5

Workflow version notification message

Workflow

Setup

Workflow version notification message

The message that is related to each notification

6

Workflow parallel branch

Workflow

Setup

Expression

A workflow element that includes two or more workflow branches that run at the same time

7

Workflow subworkflow

Workflow

Setup

Expression

A workflow that runs in the context of another workflow

8

Workflow element

Workflow

Setup

Expression, Workflow version

A workflow consists of elements of various types.

9

Workflow element action

Workflow

Setup

Workflow element

The action that must be taken for each element

10

Workflow element notification

Workflow

Setup

Workflow element

The notification about action that is required for each element

11

Workflow element notification message

Workflow

Setup

Workflow element notification

The message that is associated with each notification

12

Workflow element link

Workflow

Setup

Workflow element

The connector between elements in a workflow

13

Workflow element outcome message

Workflow

Setup

Workflow element

The message about the status of the workflow

14

Workflow step

Workflow

Setup

Workflow element

Each stop of the workflow

15

Workflow step message

Workflow

Setup

Workflow step

The message at each step

16

Workflow escalation path

Workflow

Setup

Workflow step

The path to take if action isn't taken

See also
--------

[Data entities and packages framework](data-entities-data-packages.md)

[Data entities home page](data-entities-home-page.md)

