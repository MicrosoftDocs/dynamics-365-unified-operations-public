---
# required metadata

title: Class extension: Method wrapping and Chain of Commandf (CoC)
description: This topic discusses the functionality of extending the business logic of public and protected methods using method "wrapping". 
author: robadawy
manager: AnnBe
ms.date: 08/21/2017
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
ms.search.scope: AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 26961
ms.assetid: 8a2b3107-247d-4362-8d4d-6ee6257abfcc
ms.search.region: Global
# ms.search.industry: 
ms.author: robadawy
ms.search.validFrom: 2017-08-21
ms.dyn365.ops.version: AX 7.0.0

---

# Overview
The functionality of class extension (also known as class augmentation) has been improved to allow developers to wrap logic around methods defined in the base class being augmented. This allows extending the logic of public and protected methods without the need to use event handlers. When you wrap a method, you can also access public and protected methods and variables of the base class. This way, you can start transactions and easily manage state variables associated with your class.
Consider the following situation. A model contains the following code.
```
class BusinessLogic1
{
    str DoSomething(int arg) {
    …
    }
}
```
It is now possible to augment the functionality of the method DoSomething inside an extension class by reusing the same method name. An extension class must belong to a package that references the model where the augmented class is defined.
```
[ExtensionOf(ClassStr(BusinessLogic1))]
final class BusinessLogic1_Extension
{
    str DoSomething(int arg) {
        // Part 1
        var s = next DoSomething(arg + 4);
        // Part 2
        return s;
    }
}
```
Wrapping DoSomething and the required use of the next keyword creates a Chain of Command (CoC) for the method. Here is what happens when the following code executes.
BusinessLogic1 c = new BusinessLogic1();
info(c.DoSomething(33));
The system will find any method that wraps the method DoSomething. It will randomly execute one of these methods (say, DoSomething of the BusinessLogic1_Extension class). When the call to next DoSomething() occurs, the system randomly picks another method in the CoC or calls the original implementation if no further wrapped methods exist.
