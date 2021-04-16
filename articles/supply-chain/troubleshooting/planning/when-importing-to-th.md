---
title: You are asked to save item coverage settings after making no changes
description: You are asked to save item coverage settings after making no changes
author: SmithaNataraj
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: DataManagementWorkspace_
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: angarmas
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# You are asked to save item coverage settings after making no changes

<!-- KFM: Missing KB number? -->

## Issue description

In some scenarios, you may receive the following message on accessing **Item coverage** page after importing items to the *Item coverage V2* entity:

> Do you want to save your changes before closing?

You see this message even though you haven't made any changes.

## Resolution

The **Item coverage** page includes complex defaulting logic that might lead to the observed message after direct modifications have recently been made in the database, such as entity imports.

<!-- KFM: The following instruction is not clear. How/when/where do we do this? We normally should not use internal field names. Talk directly to the reader; don't tell them what "a user" needs to do. -->
To change PRODUCTCOVERAGEGROUPID through the entity a user needs to set AREGENERALSETTINGSOVERRIDDEN to Yes
