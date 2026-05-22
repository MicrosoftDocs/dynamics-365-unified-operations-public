---
title: Register subclasses for factory methods
description: Learn about how to register your own variations for the factories, including an overview on introducing new variants.
author: MichaelFruergaardPontoppidan
ms.author: mfp
ms.topic: how-to
ms.date: 03/27/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: Platform update 9
---

# Register subclasses for factory methods

[!include [banner](../includes/banner.md)]

Class inheritance is a central concept in X++, as in other object-oriented languages. The X++ business logic uses the object-oriented strategy pattern. In this pattern, you encapsulate variations in behavior by using subclasses, and the business process uses an abstract base class or interface. A factory method determines the variation that it uses by creating an instance of a specific subclass.

This article describes how to register your own variations for the factories.

In X++, the factories use reflection to perform the following tasks:

+ Find the correct subclass. The factory uses an extension framework to search all subclasses in a hierarchy for a specific set of attributes. If the attributes that decorate a subclass match the parameters that you pass to the factory, the factory uses that specific class.
+ Create an instance. After the factory identifies the right type, it uses reflection to create an instance of the class.

The following illustration shows a typical decorated hierarchy.

:::image type="content" source="media/hierarchy.png" alt-text="Screenshot of a class hierarchy that has three subclasses, each of which is decorated with an attribute.":::

In X++, two extension frameworks serve the same purpose. The implementer of the factory method determines which extension framework to use:

+ [SysExtension](https://community.dynamics.com/365/financeandoperations/b/mfp/posts/sysextension-framework-to-the-rescue)

  - This extension framework uses custom attributes that make it easier to consume.
  - It supports singletons that save a little performance when the same instance is created repeatedly. This extension framework is especially useful for stateless subclasses.
  - It seamlessly supports extensible enums that are often used to determine the variant.

+ SysPlugin

  - This extension framework is based on the Managed Extension Framework. The Managed Extension Framework makes the SysPlugin extension framework available to non-X++ code.
  - It uses the **ExportMetadataAttribute** attribute to decorate the variants and is string-based.
  - It uses the **ExportAttribute** attribute to make the variant discoverable.

## Introduce a new variant

1. Identify the base class or interface of the variant that you need to implement.
1. Create a new subclass of the base class, and implement your variation.
1. Identify which attribute is required to register your class. Use two approaches to find the attribute:

    + Look for attributes that other subclasses in the hierarchy define.
    + Look at the implementation of the factory method. That implementation contains the attributes that the factory method searches for.

1. Decorate your subclass with the attribute that matches your variation.

## SysExtension example

```xpp
[WHSWorkExecuteMode(WHSWorkExecuteMode::About)]
class WHSWorkExecuteDisplayAbout extends WHSWorkExecuteDisplay
{
    // Your code here.
}
```

## SysPlugin example

```xpp
[ExportMetadataAttribute('CaseIAssociation', 'Lead'),
ExportAttribute('Dynamics.AX.Application.CaseIAssociation')]
class smmLeadCaseAssociationProvider implements CaseIAssociation
{
    // Your code here.
}
```


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
