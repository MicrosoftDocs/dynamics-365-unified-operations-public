---
title: Naming guidelines for extensions
description: This article describes the naming guidelines for extensions. Artifacts must have a name that is unique across all models at installation time.
author: pvillads
ms.date: 07/17/2019
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: pvillads
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: Platform update 9
ms.assetid: 
---

# Naming guidelines for extensions

[!include [banner](../includes/banner.md)]

**High level guidance: use prefixes to reduce conflicts and improve identification**

## Naming model elements
Every element in a model must have a name that is unique across all models at installation time. However, at installation time, you don't know the names of all the models that your model might be installed together with. To accommodate this situation, every element name should include a prefix that is specific to your solution. By including this prefix when you name elements in your model, you significantly reduce the risk of naming conflicts.

+ If a model contains multiple solutions, each solution in the model can be identified by a different prefix. 
+ You must carefully choose the prefix to minimize the risk that other models from other parties use the same prefix for their elements.

When you extend functionality in other models, elements that are being extended already contain a prefix. However, you should not add your prefix to the extension elements, so that the names include multiple successive prefixes. Instead, you should include your prefix or another term or abbreviation as an infix when you name extension elements.

## Naming extensions

An extension element, such as a table extension, view extension, or form extension, must have a unique name that minimizes the risk of conflicts with extensions in other models. To minimize the risk of conflicts, the name should include a term, abbreviation, or infix that distinguishes the extension from other extensions to the same element in other models.

+ Include either the name of the model where the extension element resides or the prefix that the extension is associated with. For example, a Warehousing module extends the HCMWorker table and uses the **WHS** prefix in the name of all other elements. In this case, the extension might be named **HCMWorker.WHSExtension**. Notice that the prefix that is used to name other elements in the module is inserted as an infix in the name. As another example, an extension of the ContactPerson table in the **ContosoCustomizations** model might be named **ContactPerson.ContosoCustomizations** if the extension is intended to contain all extensions to the ContactPerson table from the **ContosoCustomizations** model. The developer tools will default to using the model's name as the extension name, since the model name is already required to be unique.
+ Don't name the extension just **&lt;Element that is being extended&gt;.Extension**. For example, an extension of the InventLocation table must not be named **InventLocation.Extension**, because the risk of conflicts is too high.

## Naming extension classes

Extension classes that are used to augment the logic on tables, classes, or other elements must have a name that is unique across all types in all models. Preferably, the extension class should include the name of the type that is being extended. However, the name must also include a term, abbreviation, or prefix that distinguishes the class from other types.

+ Start the name of the extension class with the name of the type that is being augmented, and end the name with the term **\_Extension**.
Therefore, an extension class that augments the ContactPerson table should start with the name **ContactPerson** and end with **\_Extension**. For example, one extension class might be named **ContactPersonWHS\_Extension**.
+ Include either the name of the model where the extension element resides or the prefix that the extension is associated with. For example, a Warehousing module uses an extension class to augment the ContactPerson table and uses the **WHS** prefix in the name of all other elements. In this case, the extension class might be named **ContactPersonWHS\_Extension**. Notice that the prefix that is used to name other elements in the module is inserted as an infix in the name. As another example, an extension class that augments the ContactPerson table in the ApplicationSuite model might be named **ContactPersonApplicationSuite\_Extension** if the extension class is intended to contain all extensions to the ContactPerson table in the ApplicationSuite model.
+ Consider adding additional element type information in case you create a class extension for elements that can't be declared in the code (like Forms, DataSources, or FormControls). For example, **CustTableFormWHS\_Extension** is the extension for the **CustTable** form.
+ Don't name the extension just **&lt;Element that is being extended&gt;\_Extension**. For example, an extension class that augments the InventLocation table must not be named **InventLocation\_Extension**, because the risk of conflicts is too high.

## Naming fields, field groups, indexes, relations, and metadata elements added in extensions

Fields, field groups, indexes, relations, and metadata elements added in extensions must have a name that is unique across both the element that is being extended and other extension elements. Therefore, **these artifacts should include a prefix** that minimizes the risk of conflicts across models. In addition, these artifacts should have clear terms and abbreviations so that they can be easily understood. 

+ Include a prefix, term, or abbreviation at the beginning of the name of the metadata node. For example, an approving worker foreign key field is added as part of a table extension, and **WHS** is one of prefixes that are dedicated to other elements in the hosting model. In this case, the field might be named **WHSApprovingWorker**.

## Naming variables and methods added in extension classes

Variables and methods added in extension classes must have a name that is unique across both the type that is being extended and all other extension classes that extend the same type. You should take care to create unique and readable names for variables and methods. When you can't create a unique name, then you should apply a prefix to minimize the risk of conflicts across models. 

+ Create unique and readable names for variables and methods. For example, an approving worker class-level member variable might be named **approvingWorkerForLocalWarehouse** if the area of functionality is related to supporting some local warehouse extension functionality. An **approveWork** method for the same area of functionality might be named **approveWorkForLocalWarehouse**. 
 
+ When you cannot create a unique and readable name, then add a prefix, term, or an abbreviation at the beginning of the member variable or method name. For example, an approving worker class-level member variable might be named **whsApprovingWorker** if **WHS** is one of the prefixes that is used by other elements in the model. An **approveWork** method might be named **whsApproveWork** if **WHS** is a prefix that is used by other elements in the hosting model. 
 
+ Avoid generic names, because the risk is high that multiple extensions could be using the same term or that the base functionality would be enhanced with an identical name in a future release. Some example of names likely to collide are **Approver**, **Delay**, **Group**, **Lookup**, and **Process**.   



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
