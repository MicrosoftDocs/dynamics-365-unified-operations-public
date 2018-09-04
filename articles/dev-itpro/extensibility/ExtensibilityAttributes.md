---
# required metadata

title: Attributes making methods extensible
description: This article describes attributes making methods extensible.
author: mfp
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
ms.author: mfp
ms.search.validFrom: 2018-09-09
ms.dyn365.ops.version: Platform update 20
---

# Attributes making methods extensible

This topic describes the various attributes used to control extensibility capability for methods.

Default attributes based on access modifiers:

|Hookable |	Wrappable |	Replaceable |
|---------|----------|-----------|
| Private |	Not-supported |	Not-supported |	Not-supported |
| Protected |	Yes |	Yes |	No |
| Public | Yes |	Yes |	No |

## Hookable
Methods that are hookable allow extenders to subscribe to pre- and post events.

For protected and public methods, you can opt out, by decorating the method with:
```[Hookable(false)]```

You cannot opt-in for private methods.

Best practices when writing code
+ When a method is hookable the compiler will generate extra IL code to enable the method as an extension point. This extra code has a small performance overhead, which in most cases is negligible. However, for performance critical methods, consider marking the method as not hookable.

## Wrappable
Methods that are wrappable allow extenders to wrap the method using chain-of-command. Extenders must call next - they are not allowed to break the chain of command.

Methods must be hookable to be wrappable; methods that are wrappable are hookable.

For protected and public methods, you can opt out, by decorating the method with:
```[Wrappable(false)]```

You cannot opt-in for private methods.

### Best practices when writing code
+ Chain-of-command has many similarities with inheritance. In situations where you want to allow others to call your method, but not change it you would typically mark the method as final. Consider marking these methods as not wrappable; or even not hookable.

## Replaceable 
Methods that are replaceable allow extenders to wrap the method using chain-of-command without unconditionally calling next. Extenders can break the chain of command; however expectations are they only break the chain conditionally. The compiler is not enforcing calls to next.

Methods must be wrappable to be replaceable.

For wrappable methods, you can opt in by decorating the method with:
```[Replaceable]```

### Best practices when writing code
Replaceable provides the ability to extend a method using chain of command and to skip the execution of next. Hence, an important consideration to make before allowing a method to be replaceable is to thoroughly assess the functional impact, when the execution of the method is skipped by the extender.
			
+ DO ensure that methods decorated with ```[Replaceable]``` have XML documentation describing the responsibility of the method.
+ DO NOT use ```[Replaceable]``` to allow consumers to skip the replaced logic and do nothing.
+ DO NOT use ```[Replaceable]``` for factory methods, when ```SysExtension``` can be used instead.
+ AVOID using ```[Replaceable]``` when the method is changing database or class state.
+ AVOID using ```[Replaceable]``` if the method performs multiple operations and has multiple responsibilities.
+ Refactor the method into separate methods with single responsibility and consider which methods should actually be replaceable.
+ CONSIDER using ```[Replaceable]``` for solving transformations
  - Example: Enum conversion with switch statement over enum values, with the default block with a throw.
+ CONSIDER using ```[Replaceable]``` for overriding 
  - Lookups
  - Jumprefs

### Best practices for extenders
+ DO NOT write logic with a different responsibility than the logic being replaced.
+ DO call the base functionality (call next) when the replacing logic does not apply.
+ AVOID replacing logic completely by not calling the base functionality (call next)

