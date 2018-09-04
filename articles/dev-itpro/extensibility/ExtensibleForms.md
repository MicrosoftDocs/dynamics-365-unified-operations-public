---
# required metadata

title: Writing extensible forms
description: This article how to write extensible forms.
author: SmithaNataraj, Moustafa
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
ms.author: ivanv
ms.search.validFrom: 2018-09-09
ms.dyn365.ops.version: Platform update 20
---

# Forms

## Methods on forms:
+ The guidelines for writing extensible methods also applies in general to form methods.
+ CoC give access to the form non private members, the same as for classes.
+ CoC is enabled for nested classes which implies that methods defined within various levels on the form is extensible.

> One limitation to this is for form data source methods - only methods defined in the kernel are enabled for extensions. The ability to extend methods defined on the form datasource will be available in one of the coming platform updates.

## Field groups:
+ Consider using field groups whenever possible, this way ISVs get their fields added for free when they extend a field group.

## Form controls:
+ Moving around form controls could potentially break, if the controls are now made non-extensible by moving.
