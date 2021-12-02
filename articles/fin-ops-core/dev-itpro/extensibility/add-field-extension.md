---
title: Add fields to tables through extension
description: This topic describes how to use a table extension to add a field to a table.
author: ivanv-microsoft
ms.date: 06/20/2017
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
ms.author: ivanv
ms.search.validFrom: 2017-06-01
ms.dyn365.ops.version: Platform update 4

---

# Add fields to tables through extension

[!include [banner](../includes/banner.md)]

To add a new field to an existing table, you must first create a table extension. For example, to add a field that holds the radius of the released product, you must create an extension for the InventTable table in your model, as shown in the following illustration.

![Create an extension.](media/TableNewField01.jpg) 

You can now add the field to the extension, just as you would add a field to a table in your model. You can use two methods:

+ In the designer, right-click the **Fields** node, select **New**, and then select the type of field to add.
+ Drag an existing Extended Data Type or Base Enumeration from your project onto the **Fields** node.

When you've finished, you can modify the properties of the new field. In the following illustration, only the **Label** property was modified.

![Modify properties of the new field.](media/TableNewField02.jpg)

You can now optionally add the new field either to one of the existing field groups or to a new field group that you create. In the following illustration, the **Radius** field was added to the **PhysicalDimensions** field group.

![Add the new field to a field group.](media/TableNewField03.jpg)

After compilation and synchronization of the database, you can see and edit the new field in the user interface.

![New field in the user interface.](media/TableNewField04.jpg)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]