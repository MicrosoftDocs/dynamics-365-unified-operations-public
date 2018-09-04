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
#### Any data model change, that requires a data upgrade script to be executed
  + Consumers may not be able to synchronize their data model
  + Consumers might loose access to data.
  
#### Data Types
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
+ Changing the Enum type of a Enum type EDT when the Enum is extensible 
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

