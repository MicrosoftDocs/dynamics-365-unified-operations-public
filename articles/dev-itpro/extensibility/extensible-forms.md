---
# required metadata

title: Write extensible forms
description: This article provides information about how to write extensible forms.
author: smithanataraj
manager: AnnBe
ms.date: 09/09/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 


# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 268724
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: Smitha Nataraj
ms.search.validFrom: 2018-09-09
ms.dyn365.ops.version: Platform update 20
---

# Write extensible forms

## Methods on forms
+ The guidelines for writing extensible methods generally apply to form methods.
+ Chain of Command (CoC) gives access to the form non-private members, which is the same as for classes.
+ CoC is enabled for nested classes which implies that methods that are defined within various levels on the form are extensible.

> [!NOTE]
> One limitation to this is related to form data source methods. Only methods that are defined in the kernel are enabled for extensions.

## Field groups
+ Consider using field groups whenever possible, this way ISVs get their fields added for free when they extend a field group.

## Form controls
+ Moving around form controls could potentially break, if the controls are now made non-extensible by moving.
