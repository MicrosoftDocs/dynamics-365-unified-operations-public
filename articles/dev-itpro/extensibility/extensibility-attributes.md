---
# required metadata

title: Attributes that make methods extensible
description: This article provides information about attributes that make methods extensible.
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

# Attributes that make methods extensible

This topic describes the various attributes that can be used to control extensibility capabilities for methods.

The following table provides an overview of the default extensibility support:

|  | Hookable |	Wrappable |	Replaceable |
|---------|----------|-----------|-------|
| Private |	Not-supported |	Not-supported |	Not-supported |
| Protected |	Yes |	Yes |	No |
| Public | Yes |	Yes |	No |

## Hookable
Methods that are hookbale allow extenders to subscribe to pre- and post events.
For protected and public methods, you can opt out, by adding the following to the method:
```[Hookable(false)]```

You can't opt-in for private methods.

#### Best practices when writing code
When a method is hookable, the compiler will generate extra IL code to enable the method as an extension point. This extra code has a small performance overhead, which in most cases is negligible. However, for performance critical methods, consider marking the method as not hookable.

## Wrappable
Methods that are wrappable allow extenders to wrap the method using Chain of Command (CoC). Extenders must call next as they are not allowed to break the chain of command.
To be wrappable, a method must also be hookable and therefore, methods that are wrappable are hookable.

For protected and public methods, you can opt out, by adding the following to the method:
```[Wrappable(false)]```

You can't opt-in for private methods.

#### Best practices when writing code
Coc has many similarities with inheritance. In situations where you want to allow others to call your method but not change it, you would typically mark the method as final. Consider marking these methods as not wrappable, or not hookable.

## Replaceable 
Methods that are replaceable allow extenders to wrap the method using CoC without unconditionally calling next. Extenders can break the CoC, however expectations are they only break the chain conditionally. The compiler is not enforcing calls to next.

Methods must be wrappable to be replaceable.

For wrappable methods, you can opt in by adding the following to the method:
```[Replaceable]```

#### Best practices when writing code
Replaceable provides the ability to extend a method using CoC and to skip the execution of next. An important consideration to make before allowing a method to be replaceable, is to thoroughly assess the functional impact when the execution of the method is skipped by the extender.
			
+ DO ensure that methods with ```[Replaceable]``` have XML documentation describing the responsibility of the method.
+ DO NOT use ```[Replaceable]``` to allow consumers to skip the replaced logic and do nothing.
+ DO NOT use ```[Replaceable]``` for factory methods, when ```SysExtension``` can be used instead.
+ AVOID using ```[Replaceable]``` when the method is changing databases or class state.
+ AVOID using ```[Replaceable]``` if the method performs multiple operations and has multiple responsibilities.
+ Refactor the method into separate methods with single responsibility and consider which methods should actually be replaceable.
+ CONSIDER using ```[Replaceable]``` for solving transformations. 
  - Example: Enum conversion with switch statement over enum values, with the default block with a throw.
+ CONSIDER using ```[Replaceable]``` for overriding lookups and jumprefs.
 
#### Best practices for extenders
+ DO NOT write logic with a different responsibility than the logic being replaced.
+ DO call the base functionality (call next) when the replacing logic does not apply.
+ AVOID replacing logic completely by not calling the base functionality (call next).

### When used in conjunction

The general rule is that hookable is required by wrappable which is required by replaceable. This is outlined in the following table.

| 	| Hookable |	Wrappable |	Replaceable |
| ---------------|--------------|----------------|------|
| [Hookable(true)] |	Yes |	No |	No |
| [Hookable(false)] |	No |	No |	No |
| [Wrappable(true)] |	Yes |	Yes |	No |
| [Wrappable(false)] |	Depends on if the method is hookable (see table above) |	No |	No |
| [Replaceable(true)] |	Yes |	Yes |	Yes |
| [Replaceable(false)] | Depends on if the method is hookable (see above table) |Depends on if the method is wrappable (see table above) |	N |
