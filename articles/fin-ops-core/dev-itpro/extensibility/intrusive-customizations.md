---
title: Intrusive customizations
description: This article defines the characteristics of an intrusive customization.
author: MichaelFruergaardPontoppidan
ms.date: 04/10/2018
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: mfp
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: Platform update 9
ms.assetid: 
---

# Intrusive customizations

[!include [banner](../includes/banner.md)]

This article defines the characteristics of an intrusive customization. Intrusive customizations are the major obstacle to keeping continuous upgrade costs close to zero. Some types of intrusive customizations can be prevented by tooling, whereas other types remain the responsibility of the author of the extension. The X++ compiler and Microsoft Visual Studio designers will prevent some types of intrusive customizations. However, a subset of intrusive customizations can't be detected by tooling but might still prevent continuous upgrades. Ultimately, the developer is responsible for avoiding intrusive customizations.

A customization that violates any of the following principles is intrusive.

 > [!NOTE]
> When extending other solutions you are expected to be responsible. This includes:
> + Accepting the responsibility of your extension. You are introducing new behavior and therefore own the full responsibility of the change.
> + Allowing other extensions to co-exist. Recognize that you are not the only consumer of an extension point. For example, only respond when needed.
> + Only adding extensions that are coherent with the extension point. The longevity of a solution is defined by its resilience to change. Recognize that extension points may be exercised in more or fewer scenarios in future versions. For example, only add relevant validation logic to a validate() method.
> + Avoiding dependencies on implementation details. Implementation details are likely to change in future versions. Make your solution resilient by avoiding dependencies on local variables, call-stacks and, calling sequences and avoid using reflection.


## Don't change type definitions
Types are referenced by their definition. A change to a type’s definition is a breaking change and requires that all references be updated. It's impossible to ensure that future references will be implemented correctly (for example, in the model that hosts the type). There are several implications:

+ Don't change a method signature. The method signature includes the return type, the name (which includes casing), and the parameters (which include optional parameters).
+ Don't change requirements for implementers of interfaces and table maps. For example, don't add a new method to an interface or a new field to a table map.
+ Don't change requirements for classes that are derived from abstract classes. For example, don't add a new abstract method to a class.
+ Don't reduce access modifiers for types or members. For example, don't change classes, tables, or methods from public to private.
+ Don't change constraints that are defined on a table or a data entity. Constraints include allowing editing, mandatory constraints, uniqueness constraints, and referential constraints.

## Don't break encapsulation
The author of a model must be able improve the product by remaining in control of encapsulated code and types. Model owners must be able to change and delete encapsulated code and types at will, without prior notice, and without risk of downstream impact on extensions and customizations. Encapsulation is broken if, for example, a private method is deleted. Here are some of the implications:

+ Don't increase access modifiers for types or members. For example, don't change classes, tables, or methods from private to public.
+ If something should be closed for modification, don't open it for customizing behavior. Extension capabilities must be designed as open for extensibility but closed for modification.
            
## Be additive in nature
New behaviors are enabled through added functionality as part of extensions. Extension capabilities must be designed in and open for extensions, and they must support multiple extensions that exist side by side in the same installation. There are several implications:

+ Don't overlayer. Overlayering replaces the default implementation and prevents multiple solutions from changing the same element.
+ Don't significantly change the characteristics of the standard functionality. These characteristics include the user experience and performance. For example, performance must not be adversely affected if an extension is installed but isn't used.
+ Don't unconditionally set results in **EventHandlerResult** classes, and don't unconditionally set return values in **XppPrePostArgs** classes.
+ Don't replace existing behavior by default, unless the replacing logic conforms to the Liskov Substitution Principle.  

> [!NOTE]
> The author of the extension is responsible for not violating these principles.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
