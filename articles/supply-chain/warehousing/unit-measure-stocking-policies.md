---
# required metadata

title: Unit of measure and stocking policies
description: This article describes how default units, unit sequences, and unit conversions are used in warehouse processes.
author: perlynne
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: EcoResProductDetails, EcoResProductDetailsExtended, EcoResStorageDimensionGroup, InventItemOrderSetup, UnitOfMeasureConversion, WHSRFMenuItem, WHSUOMSeqGroupTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: 4b5ca875-9a06-416d-9ac0-cc3ab8f7338e
ms.search.region: Global
# ms.search.industry: 
ms.author: perlynne
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Unit of measure and stocking policies

[!include [banner](../includes/banner.md)]

This article describes how default units, unit sequences, and unit conversions are used in warehouse processes.

Unit sequence groups define the sequence of units that can be used in warehouse operations. They are created on the **Unit sequence groups** page. The sequence shows the relationship of the various units. For example, you store pallets that contain boxes that contain individual pieces of items. In this case, you must provide the three different units and the logical order of the layers. Unit sequence groups let you define the policies for the grouping of license plates, and the default units that should be used for various warehouse processes. This article applies to both the warehouse management processes (WMS) available in the Warehouse management module and the more basic warehousing solution that is available in the Inventory management module.

## Unit sequence groups for released products
If you want to use released products in warehouse work processes, a unit sequence group must be assigned to them. If you validate a product that is associated with a Storage dimension group, and the **Use warehouse management processes** option for the Storage dimension group is set to **Yes**, you receive an error message if a unit sequence group ID isn't defined for the product. If the unit sequence group that you use contains multiple lines (and therefore multiple units), you must set up a unit conversion between the units. You complete this setup on the **Unit conversions** page. The smallest unit in a sequence group that you associate with a released product must match the inventory unit that is defined for the corresponding product. The inventory unit is the unit that is used for base calculations of the on-hand inventory. You can also set up unit of measure conversions for product variants of product masters by using the **Enable unit of measure conversions** option.

## License plate grouping
You can specify whether receipts of less than or more than a specific unit should be grouped into one license plate or divided into a license plate for each unit. To set up this behavior, use the **License plate grouping** option on the **Line details** tab of the **Unit sequence groups** page. If you want to use the license plate grouping when you process work by using a mobile device, the **License plate grouping** option must be selected on the **Mobile device** menu item. For example, you're using a mobile device to register an item that is associated with a unit sequence group that has two lines. The first line is for Pieces, and the **License plate grouping** option is set to **Yes**. The second line is for the Pallet unit, and the **License plate grouping** option is set to **No**. In this case, the system can automatically guide the split and creation of license plates per 100 pieces.

## Units for cycle counting
To define which units should be used as part of the cycle counting processes, select the **Use unit for cycle counting** option on the **Unit sequence groups** page. You can select a maximum of four units in the sequence group. If you select more than four units, the additional units won't be shown on the mobile device.

## Default units for mobile device receiving processes
To set the default units that should be used for receiving processes on mobile devices, enable the **Default unit for purchase and transfer** and **Default unit for production** options on the **Unit sequence groups** page. For example, you can specify that, by default, the system should use Pallet quantities when purchase order on-hand inventory is received by using a mobile device, but that the stock-keeping unit should be Pieces. To get the conversion for the number of pieces that each pallet contains, you must define a unit conversion, such as 100 Pcs = 1 PL.

## Default order settings
As part of the creation of released products, you must select default units for purchases, sales, and inventory to process the various orders. You can set the default units and quantities for the various source documents by using the **Default order settings** and **Site specific order settings** pages. You can access these pages from the **Released products** page.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]