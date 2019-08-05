---
# required metadata

title: Wave step codes
description: This topic provides an overview of wave step codes and how they are used.
author: josaw1
manager: AnnBe
ms.date: 08/05/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: perlynne
ms.search.validFrom: 2019-08-31
ms.dyn365.ops.version: 10.0.5

---

# Wave step codes

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

## About wave step codes

Wave step codes allow users to set up codes that will be used to link
specific wave method instances with their corresponding template. This covers
templates for replenishment, containerization, label printing, load building,
and sorting. 

Without wave step codes, users must reference a specific
template from the wave process method using only free text. Free text is is error prone, as it requires a user to manually ensure that the wave step text
added for a specific wave step process method in a wave template matches the
exact wave step text in the target template. 

Wave step codes are set up for a
specific wave step type in a separate form. Each wave step method in a wave
template that needs a wave step code requires the wave step code to be
selected from a dropdown list, instead of a free text entry. Linking a wave step method
in a wave template to a target template for the method is based on setup codes, reducing the risk and impact of human
errors.

> [!NOTES]
> The use of wave step codes is optional. 
> Uptake for wave step codes is per legal entity. As such, all
existing wave steps codes in the specific legal entity will be upgraded into the
new structure.

Simple demo setup 
==================

Pre-condition: Demo data, Company USMF

Enable wave step codes, navigate to Warehouse management Setup Warehouse
management parameters General Wave processing Enable wave step codes.

Note: *Once the upgrade of all existing wave step free texts into the new
structure ends with success for a legal entity, the menu item Enable wave step
codes will no longer be available in the form. During the upgrade, more
validations are performed and if the upgrade fails, then the user is presented
an error messages. Reasons for upgrade failure can be, but is not excluded to,
duplicate wave step code free texts, customizations, mismatch on a wave step
free text associated with a wave step method which does not match the expected
template type. Once the user has resolved the conflicts identified during the
validations, the upgrade process can be re-run.*

When the upgrade succeeds the following form be accessible:

Navigate to Warehouse management Setup Waves Wave step codes.

In this form you can see the wave step codes upgraded during the enabling
process. This is also the form where you create and delete wave step codes. The
wave step code, the ID, must be unique across all wave step types and is
specified for a specific wave step type.

Once the appropriate wave steps codes have been defined, they can be applied for
the wave processing methods. In order to do such, navigate to the appropriate
target template. The target templates for which the wave step codes are
designated to point to are:

**Replenishment Templates**: Warehouse management Setup Replenishment
Replenishment Templates

**Load Build Templates**: Warehouse management Setup Load Load Build Templates

**Sort Templates**: Warehouse management Setup Packing Outbound Sorting
Templates

**Containerization Templates**: Warehouse management Setup Containers Container
Build Templates

**Label Printing Templates**: Warehouse management Setup Document Routing Wave
Label Templates

The above templates will be applied when referenced from a wave processing
method selected in a wave templates. When the wave step code on a wave
processing method in a wave template matches the wave step code on a one of the
5 templates types, then the template on applied.

Consider the setup:

Navigate to Warehouse management Setup Waves Wave step codes. Create a wave step
code for the type **Replenishment**. Navigate to Warehouse management Setup
Replenishment Replenishment Templates. Create a replenishment template. On the
replenishment template select the wave step code created for the type. Navigate
to Warehouse management Setup Waves Wave Templates. Select the wave template
that you intent to use. On the template, in the **Methods** fast tab, select the
method Replenishment. Once selected, in the wave step code field, select the
wave step code you also selected for the replenishment template.

With these steps you have now ensured that the replenishment template created
will be the replenishment template that will be applied for the wave template
when used as the wave step codes selected match.
