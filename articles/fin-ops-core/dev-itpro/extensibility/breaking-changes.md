---
title: Breaking changes
description: This topic provides information about breaking changes.
author: smithanataraj
ms.date: 09/09/2018
ms.topic: article
ms.prod: 
ms.technology: 


# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: tfehr
# ms.tgt_pltfrm: 
ms.custom: 268724
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: smnatara
ms.search.validFrom: 2018-09-09
ms.dyn365.ops.version: Platform update 20
---

# Breaking changes

[!include [banner](../includes/banner.md)]

When you make your solution extensible, you also help guarantee that you won't break the extension points later. A breaking change is any change that can break a consumer of your code.

This topic lists some of the types of changes that can break your code. 

> [!IMPORTANT]
> This list isn't exhaustive. Other types of changes that aren't listed here could also be breaking changes.

## Data model changes

### General
If any data model change requires that a data upgrade script be run, consumers might no longer be able to synchronize their data model, or they might lose access to data.

### Data types
+ **Changing an enumeration (enum) from extensible to non-extensible** – Consumers might have extensions to the enum.
+ **Changing an enum from non-extensible to extensible** – Consumers might be using the enums in comparisons. For more details, see [Write extensible enums](extensible-enums.md).
+ **Decreasing the decimal precision of an extended data type (EDT) of the real type** – Consumers might have dependencies on the ability to enter data that uses the precision.
+ **Decreasing the size of an EDT of the string type** – Consumers might have dependencies on the size of the string.
+ **Specializing the EDT by making it extend another EDT** – Consumers might have string length or decimal precision extensions to the EDT.
+ **Changing the enum type of an EDT of the enum type when the enum is extensible** – Consumers might have extensions to the enum.
 
### Data model
+ **Making a table obsolete and stopping information from being entered in the table** – Consumers might have a dependency on the table that information is entered in.
+ **Making a table field obsolete and stopping information from being entered in the field** – Consumers might have a dependency on the field that information is entered in.
+ **Renaming a field group** – Consumers might have extensions to field group, or code or metadata dependencies to it.
+ **Changing constraints or indexes**
+ **Making a table map obsolete and stopping the table map from being used**
+ **Make a table map field obsolete**
+ **Adding a table map field**
+ **Removing a table map field mapping**
+ **Making a data entity obsolete**
+ **Making a data entity field obsolete**

## Code changes

### Class members
+ **Deleting or renaming public or protected class-level members** – Consumers might be using these members in the extension classes.
+ **Changing a class member from public or protected to protected or private** – Consumers might have queried or assigned values to the field.

### Classes and interfaces
+ **Adding an abstract method to a class** – Consumers might have created a derived type.
+ **Adding final to a class** – Consumers might have created a derived type.
+ **Adding a method to an interface** – Consumers might have implemented the interface on their own type.
+ **Making a public class obsolete and stopping instantiation of the class** – Consumers might have overridden, wrapped, or subscribed to the instance methods.

### Methods
+ **Changing the access modifier from protected or public to another access modifier** – Consumers might have called, overridden, wrapped, or subscribed to the method.
+ **Making a concrete public or protected method abstract** – Consumers might have subclasses to the class, and those subclasses might not have implemented the method, or they might even call super.
+ **Renaming method parameters** – Consumers might have dependencies on parameters by name (via arguments or externally from C\#, for example).
+ **Adding, removing, or changing the type of a method parameter on a protected or public method** – Consumers might have called, overridden, wrapped, or subscribed to the method.
+ **Adding or removing a default method parameter on a protected or public method** – Consumers might have wrapped or subscribed to the method.
+ **Changing the return type of a method** – Consumers might have called, overridden, wrapped, or subscribed to the method.
+ **Adding Hookable(false) to a protected or public method** – Consumers might have wrapped or subscribed to the method.
+ **Adding Wrappable(false) to a protected or public method** – Consumers might have wrapped the method.
+ **Removing Hookable(true) from a private or protected method** – Consumers might have subscribed to the method.
+ **Removing Wrappable(true) from a private method** – Consumers might have wrapped the method.
+ **Removing Replaceable(true) from a method** – Consumers might have conditionally wrapped the method.
+ **Adding final to a protected or public method** – Consumers might have overridden, wrapped, or subscribed to the method.
+ **Changing a method from instance to static or from static to instance** – Consumers might have called, overridden, wrapped, or subscribed to the method.
+ **Making a method obsolete and stopping invocation of the method** – Consumers might have called, overridden, wrapped, or subscribed to the method.
+ **Changing the responsibility of a method** – Consumers might have called, overridden, wrapped, or subscribed to the method.
+ **Removing the reference to a method** – Consumers might have overridden, wrapped, or subscribed to the method, and they might expect their logic to run.

### Delegates
+ **Making any change in signature** – Consumers might have subscribed dynamically.
+ **Removing the reference to a delegate** – Consumers might have subscribed, and they might expect their logic to run.

## Label changes
+ **Modifying or deleting a label** – Consumers might be using the label in the current context of the label text and the parameters that were passed, and so on. We recommend that, going forward, you add new labels in the event of a label change.

## Application element changes
+ **Removing any element** – Consumers might have a compile time dependency on the existence of the element.
	 
## Metadata extensions
+ **Not following the naming guidelines for metadata or augmentation classes** – Consumers might have elements that have the same name.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]