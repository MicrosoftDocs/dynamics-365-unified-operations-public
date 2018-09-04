---
# required metadata

title: Writing extensible code-breaking changes
description: This article details the breaking changes.
author: lolsen, smnatara
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

# Breaking Changes

When making your solution extensible, you also guarantee to not break those extension point going forward. A breaking change is anything that can break a consumer of your code.

Below is a list of some types of changes that could potentially break someone. 

>**DISCLAIMER:** This is not an exhaustive list - there could be other types of changes that are not listed here below that could be breaking changes. Reach out to the Extensibility team in case of any doubts.

## Data model changes

### General
+ Any data model change, that requires a data upgrade script to be executed
	- Consumers may not be able to synchronize their data model
	- Consumers might loose access to data.
  
### Data Types
  + Changing an Enum from **Extensible to not Extensible**
    - Consumers could have extensions to the enum
  + Changing an Enum from **not Extensible to Extensible**
    - Consumers could be using the enums in comparisons.
  + **Decreasing the decimal precision of a real type EDT**
  	- Consumers could have dependencies on the ability to enter data with the precision
  + **Decreasing the size of string type EDT**
    - Consumers could have dependencies on the size of the string
+ **Specializing the EDT by making it extend another EDT**
	- Consumers could have string length or decimals precision extension to the EDT
+ **Changing the Enum type of a Enum type EDT when the Enum is extensible** 
	- Consumers could have extensions to the Enum
 
### Data model
+ **Obsoleting a table and stop populating the table**
	- Consumers could have a dependency on the table being populated.
+ **Obsoleting a table field and stop populating the field**
	- Consumers could have a dependency on the field being populated.
+ **Renaming a field group**
	- Consumers could have extensions to the field group
	- Consumers could have code or metadata dependency to the field group
+ **Changes to constraints or indexes**
+ **Obsoleting a table map** and stop leveraging the table map
+ **Obsoleting a table map field**
+ **Adding a table map field**
+ **Removing a table map field mapping**
+ **Obsoleting a data entity**
+ **Obsoleting a data entity field**

## Code changes
### Class members
+ **Deleting or renaming public or protected class level members**
	- Consumers could be using these members in the extension classes
+ **Changing a class member from public or protected to protected or private**
	- Consumers could have queried or assigned values to the field
  
### Classes, Interfaces
+ **Adding an abstract method to a class**
	- Consumers could have created a derived type
+ **Adding final to a class**
	- Consumers could have created a derived type
+ **Adding a method to an interface**
	- Consumers could have implemented the interface on their own type
+ **Obsoleting a public class and stop instantiating the class.**
	- Consumers could have overridden, wrapped or subscribed to the instance methods

### Methods
+ **Changing access modifier from protected or public to another access modifier**
	- Consumers could have called, overridden, wrapped or subscribed to the method
+ **Making a concrete public or protected method abstract**
	- Consumers may have subclasses to the class which have not implemented the method and may be even callin super.
+ **Renaming method parameters**
	- Consumers could have dependencies on parameters by name (via args or externally from C#, f. ex.)
+ **Adding, Removing or changing type of a method parameter on a protected or public method**
	- Consumers could have called, overridden, wrapped or subscribed to the method
+ **Adding or Removing a default method parameter on protected or public method**
	- Consumers could have wrapped or subscribed to the method
+ Changing the **return type** of a method
	- Consumers could have called, overridden, wrapped or subscribed to the method
+ **Adding Hookable(false) to a protected or public method**
	- Consumers could have wrapped or subscribed to the method
+ **Adding Wrappable(false) to a protected or public method**
	- Consumers could have wrapped the method
+ **Removing Hookable(true) from a private or protected method**
	- Consumers could have subscribed to the method
+ **Removing Wrappable(true) from a private method**
	- Consumers could have wrapped the method
+ **Removing Replaceable(true) from a method**
	- Consumers could have wrapped the method conditionally
+ Adding **final** to a protected or public method
	- Consumers could have overridden, wrapped or subscribed to the method
+ Changing a method from **instance to static or vice versa**
	- Consumers could have called, overridden, wrapped or subscribed to the method
+ Obsoleting a method and stop invoking it.
	- Consumers could have called, overridden, wrapped or subscribed to the method
+ Changing the responsibility of a method
	- Consumers could have called, overridden, wrapped or subscribed to the method
+ Removing the reference to a method
	- Consumers could have overridden, wrapped or subscribed the method and expecting their logic to run.

### Delegates
+ **Any change in signature**
	- Consumers could have subscribed dynamically.
+ **Removing the reference to a delegate**
	-  Consumers could have subscribed and expect their logic to run.

## Label changes
+ **Modifying or deleting a label**
	- Consumers could be using the label with the current context of the label text and the parameters passed, etc.
	- Going forward it is recommended to add new labels in case of a label change.

## Application element
+ **Removing any element**
	- Consumers could have a compile time dependency on the existence of the element
	 
## Metadata Extensions
+ Not following **naming guidelines** for metadata or augmentation classes
	- Consumers could have elements with the same name.
 
