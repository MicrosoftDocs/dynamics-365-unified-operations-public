---
# required metadata

title: Naming guidelines
description: This topic describes the naming guidelines for extensions.
author: LarsBlaaberg
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: Operations, Platform
# ms.tgt_pltfrm: 
ms.custom: 89563
ms.assetid: 8DA4DA85-0C2D-4CAF-B350-DAC9C1BE4DF9
ms.search.region: Global
# ms.search.industry: 
ms.author: lolsen
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: Platform update 9
---

# Naming Guidelines

## Naming model elements
Any element in a model must be given a name, which is unique across all models at installation time. 
Given that all potential models, that your model will be installed together with, are unknown at implementation time, then every element name should include a prefix, which is specific to your solution. 
If a model contains multiple solutions, then each solution within the model can be identified by different prefixes.

The prefix must be carefully chosen to minimize the risk that other models from other parties have chosen the same prefix for their elements.
By including the prefix when naming elements in your model, then you have significantly lowered the risk of naming conflicts, when your model is later installed alongside other models.

When you extend functionality in other models, then elements being extended already contains a prefix. Instead of adding your prefix to the extension elements resulting in multiple prefixes after each other, then you should rather include your prefix or another term or abbreviation as an infix when naming the extension element.

Here are details about the specific naming of extensions.

## Naming Extensions

An extension element, i.e. table extension, view extension, form extension, etc.,  must be given a unique name, that minimizes the risk of conflicts with extensions in other models; both now and in the future. To minimize the risk of conflicts, the name should therefore include a term, abbreviation or infix, that distinguishes the extension from other extension to the same element in other models.

- **DO** include either the name of the model in which the extension element resides, or the prefix the extension is associated with.
An extension of the HCMWorker table by a Warehousing module using the WHS prefix to name all other elements, could be named HCMWorker.WHSExtension. The prefix used to name other elements in the module, is inserted as an infix in the name.
An extension of the ContactPerson table in the ApplicationSuite could be named ContactPerson.ApplicationSuiteExtension, if the extension is meant to contain all extensions to the ContactPerson table from the ApplicationSuite model.

- **DO** suffix the name with the term Extension.
An extension of the InventLocation table should follow the following pattern InventLocation.<Model>Extension

- **DO** NOT name the extension simply as <ElementBeingExtended>.Extension.
An extension of the InventLocation table must not be named InventLocation.Extension, as the risk of conflicts is too high.


## Naming Extension classes

Extension classes used to augment logic on tables, classes, or other elements which can be extended through augmentation, need to be given a name which is unique across all types in all models; both now and in the future.

It is preferable that the extension class includes the name of the type being extended, but at the same time, the name must also include a term, abbreviation or prefix, that distinguishes the class from other types.

- **DO** start the name of the extension class with the name of the type being augmented, and end it with the term _Extension.
An extension class augmenting the ContactPerson table should start with the name ContactPerson, and end with _Extension, e.g. ContactPersonWHS_Extension

- **DO** include either the name of the model in which the extension element resides, or the prefix the extension is associated with.
An extension class augmenting the ContactPerson table by a Warehousing module using the WHS prefix to name all other elements, could be named ContactPersonWHS_Extension. The prefix used to name other elements in the module, is inserted as an infix in the name.
An extension class augmenting the ContactPerson table in the ApplicationSuite model could be named ContactPersonApplicationSuite_Extension, if the extension class is meant to contain all extension to the ContactPerson table in the ApplicationSuite model.

- **DO NOT** name the extension simply as <ElementBeingExtended>_Extension.
An extension class augmenting the InventLocation table must not be named InventLocation_Extension, as the risk of conflicts is too high.

## Naming Fields, Field groups, Indexes, Relations and other metadata nodes in Extension elements

Fields, indexes, relations and other metadata elements on extension elements also need be unique across both the element being extended as well as other extension elements.
These metadata nodes therefore also need to include a term, abbreviation or prefix, that limits the risk of conflicts across models.

- **DO** include a prefix, term, or abbreviation in the beginning of the metadata node name.
An approving worker foreign key field added to as part of a table extension could be named WHSApprovingWorker, assuming WHS is one of prefixes dedicated to other elements in the hosting model.


## Naming members in extension classes
Class level variables, and methods on extension classes must be provided a name that is unique across the type being augmented, and all other extension classes augmenting the same type.

- **DO** include a prefix, term, or abbreviation in the beginning of the member name.
An approving worker class level variable could be named WHSApprovingWorker, if WHS is one of the prefixes used by other element in the model.
An approveWork method could be named WHSApproveWork, if WHS is one of the prefixes used by other elements in the hosting model.

