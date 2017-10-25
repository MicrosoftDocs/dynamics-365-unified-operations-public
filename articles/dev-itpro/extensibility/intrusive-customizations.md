---
# required metadata

title: Intrusive customizations
description: This topic defines the characteristics of an intrusive customization.
author: MichaelFruergaardPontoppidan
manager: AnnBe
ms.date: 07/11/2017
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
ms.search.scope: Operations, Platform, AX Platform
# ms.tgt_pltfrm: 
ms.custom: 89563
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mfp
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: Platform update 9
---

# Intrusive customizations

This topic defines the characteristics of an intrusive customization. Customizations that are implemented using overlayering are intrusive, and won't be supported as we go forward. Intrusive customizations are the major obstacle to continuous upgrades at upgrade and support costs that are close to zero. Some types of intrusive customizations can be prevented by tooling, whereas other types remain the responsibility of the author of the extension. The X++ compiler and Microsoft Visual Studio designers will prevent some types of intrusive customizations. However, a subset of intrusive customizations can't be detected by tooling but might still prevent continuous upgrades. Ultimately, the developer is responsible for avoiding intrusive customizations.

A customization that violates any of the following principles is intrusive.

# Don't change type definitions
Types are referenced by their definition. A change to a type’s definition is a breaking change and requires that all references be updated. It's impossible to guarantee that future references will be implemented correctly (for example, in the model that hosts the type). There are several implications:

+ Don't change a method signature. The method signature includes the return type, the name (which includes casing), and the parameters (which include optional parameters).
+ Don't change requirements for implementers of interfaces and table maps. For example, don't add a new method to an interface or a new field to a table map.
+ Don't change requirements for classes that are derived from abstract classes. For example, don'tadd a new abstract method to a class.
+ Don't reduce access modifiers for types or members. For example, don't change classes, tables, or methods from public to private.
+ Don't change constraints that are defined on a table or a data entity. Restraints include allowing editing, mandatory constraints, uniqueness constraints, and referential constraints.

# Don't break encapsulation
The author of a model must be able improve the product by remaining in control of encapsulated code and types. Model owners must be able to change and delete encapsulated code and types at will, without prior notice, and without risk of downstream impact on extensions and customizations. Encapsulation is broken if, for example a private method is deleted. Here are some of the implications:

+ Don't increase access modifiers for types or members. For example, don't change classes, tables, or methods from private to public.
+ If something should be closed for modification, don't open it for customizing behavior. Extension capabilities must be designed as open for extensibility but closed for modification.
            
# Be additive in nature
New behaviors are enabled through added functionality as part of extensions. Extension capabilities must be designed in and open for extensions, and they must support multiple extensions that exist side by side in the same installation. There are several implications:

+ Don't overlayer. Overlayering replaces the default implementation and prevents multiple solutions from changing the same element.
+ Don't significantly change the characteristics of the standard functionality. These characteristics include the user experience and performance. For example, performance must not be adversely affected if an extension is installed but isn't used.
+ Don't unconditionally set results in **EventHandlerResult** classes, and don't unconditionally set return values in **XppPrePostArgs** classes.
+ Don't replace existing behavior by default, unless the replacing logic conforms to the Liskov Substitution Principle.  

> [!NOTE]
> The author of the extension is responsible for not violating these principles.
