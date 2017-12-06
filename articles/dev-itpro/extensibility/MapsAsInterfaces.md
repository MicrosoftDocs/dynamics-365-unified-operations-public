---

# required metadata

title: Extending table maps used as interfaces
description: This topic describes how to extend table maps that are used as interfaces.
author: Lars Blaaberg
manager: AnnBe
ms.date: 12/10/2017
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
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 89563
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: lolsen
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: Platform update 11
---

# Extending table maps used as interfaces

Two of the table maps where we have received the most request to support the ability to add a field or method, are the SalesPurchLine and SalesPurchTable table maps. The two table maps expose a set of common fields and methods which are leveraged by a variety of business logic in the application. The table maps therefore essentially define a common interface to a set of implementing tables.

We have therefore refactored the mapping of fields and the implementation of methods into being performed as part of a class hierarchy. At a high level, an overview of these changes would be:
	• Methods on the table maps have been moved to the class hierarchy and the fields are exposed through parm-methods on the class hierarchy as well.
	• The table map still exists and tables are still implementing (mapping) the table map, but the fields on the table map have been obsoleted, and field mapping has been removed.
	• The methods on the table map have been obsoleted as well.

## The SalesPurchTableInterface hierarchy:

The new SalesPurchTableInterface class is the abstract base class for all ApplicationSuite functionality, which has been introduced when refactoring the SalesPurchTable table map. The class contains abstract methods for fields and methods which must exist for each table implementing the interface, and it contains the default logic in methods which is common across all implementations.

Each table which is implementing the SalesPurchTable table map, must be represented as a derived class in the SalesPurchTableInterface class hierarchy.

Each derived class must be decorated with a SalesPurchTableInterfaceFactory attribute class. The attribute is used to associate the derived class with the table, such that it is possible to instantiate a class of the correct type depending on a SalesPurchTable record.

![MapsAsInterfaces](media/MapsAsInterfaces1.png)

Note, that even though the table map methods have been obsoleted, the corresponding methods still exist on the implementing tables. The logic in these methods have been refactored from delegating calls to the method on the table map, to the corresponding method on the base class of the hierarchy.

## Extension scenario walk-through

Assuming an ISVModule2 model wants to extend the interface class hierarchy and the tables implementing the SalesPurchTable table map, then the ISVModule2 engineer must perform the following steps:
	1. Add fields and/or methods through table extension to the necessary tables implementing the SalesPurchTable table map.
	2. Create a new interface class hierarchy exposing the new fields as parm-methods and other additional methods.
		a. The base class of the class hierarchy must be concrete and not abstract.
	3. Create derived classes for each table which has been extended with fields and/or methods.
		a. Decorate each derived class with the SalesPurchTableInterfaceFactory attribute class to associate the class with the correct table.
		b. Create a static factory method on the base class of the new class hierarchy. The factory method should instantiate the proper derived class leveraging the SalesPurchTableInterfaceFactory attribute. In case no derived class can be found, then an instance of the base class must be returned.
	4. Create an extension class of the SalesPurchTableInterface class
		a. The class augments the SalesPurchTableInterface class with a method which creates an instance from the new class hierarchy by calling the factory method on the new class hierarchy.
	
The class and extensions described above are shown in the below diagram:

![MapsAsInterfacesWalkThrough](media/MapsAsInterfaces2.png)

The diagram also contains an ISVModule1 model which includes the ISV1Header table, that implements the SalesPurchTable table map and also contain its own SalesPurchTableInterface derived class.
The model is independent of the ISVModule2, so when logic in the ISVModule2 creates an instance from the ISV2SalesPurchTableInterface class hierarchy, then an instance of the base class will be returned, when the SalesPurchTable record is of type ISV1Header.

As long as the methods on the base class returns a reasonable result for unknown tables, then the two ISV model should be able to co-exist within the same installation.
