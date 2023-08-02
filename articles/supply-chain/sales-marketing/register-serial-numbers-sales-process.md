---
# required metadata

title: Working with serialized items
description: This article explains how you can register serial numbers on packing slips or invoices during the sales process. This functionality is useful if a company wants to capture serial numbers for service and warranty purposes, but doesn't have to maintain serial numbers in inventory from receipt to issue.
author: Henrikan
ms.date: 10/31/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: EcoResTrackingDimensionGroup, InventTrackingRegisterTrans, SalesEditLines, SalesTable, InventSerial
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac


# ms.tgt_pltfrm: 
ms.assetid: 5d39630f-607e-492b-8c1e-790ca53effa0
ms.search.region: Global
ms.search.industry: Distribution
ms.author: henrikan
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Working with serialized items

[!include [banner](../includes/banner.md)]

This article explains how you can register serial numbers on packing slips or invoices during the sales process. This functionality is useful if a company wants to capture serial numbers for service and warranty purposes, but doesn't have to maintain serial numbers in inventory from receipt to issue.

Many companies just want to capture serial numbers for service and warranty purposes, and don't have to maintain serial numbers in inventory from receipt to issue. In these scenarios, you can register the serial numbers on the packing slips or invoices when products are sold. If products are later returned, you can trace each product to an invoice to determine whether you sold the product, and whether the service or warranty obligations are valid.

You must enable serial numbers for the sales process by selecting the **Active in sales process** option on the **Tracking dimension groups** page. The following events then occur in Supply Chain Management:
-   On the **Serial numbers** FastTab, the **Serial number control** option is selected. When this option is selected, you must register one serial number for each item on the packing slip or invoice.
-   All selections on the tracking dimension group for serial numbers are cleared, except the **Blank issue allowed** option. You can select the **Blank issue allowed** option to override the serial number control, and allow products to be packed and invoiced without registering serial numbers.

## When do I register serial numbers during the sales process?
You can register serial numbers either on the packing slip for a sales order or on the invoice. When you prepare an invoice for a serialized item that was shipped together with a packing slip, you can select which serial numbers on the packing slip to invoice. The number of registered serial numbers must not exceed the quantity of items that were shipped. If you're creating a partial invoice, you can select fewer serialized items than were registered on the packing slip. When you print a packing slip or an invoice, the serial numbers that were registered are included.

## Can I enter serial numbers by scanning them, or do I have to type them?
You can either scan or type serial numbers. When you use a scanner, the scan mode determines whether the serial numbers are added to or removed from the list of serial numbers on the invoice or packing slip. If you want to scan serial numbers  by using, for example, a hand-held bar code scanner, configure the scanner to send an Enter or TAB command after the serial number. This command will indicate the end of the data stream. Otherwise, you must press Enter or TAB on the keyboard after you scan each serial number.

## If I enable serial numbers for the sales process, do I have to register all serial numbers for all items?
The setup of the tracking dimension group that is assigned to the product determines whether serial numbers must be registered for all items on a packing slip or invoice. When you enable serial numbers for the sales process, the **Serial number control** option is automatically selected. You must then register one serial number, or register a blank registration for an unreadable number, for each item on the packing slip or invoice. If you don't want to require a serial number for each item, select the **Blank issue allowed** option on the tracking dimension group that is assigned to the item. You can then register fewer serial numbers than the quantity of items that are being shipped. If you register more serial numbers than the quantity of items that are being shipped, you won't be able to post the packing slip or invoice.

## Can I register serial numbers for partial invoices and partial shipments?
You can create partial invoices and packing slips for sales orders, and register only the serial numbers for the items that those invoices and packing slips include. If you want to create a partial invoice, and you have more than one packing slip for the sales order, you can include serial numbers from more than one packing slip. However, there can be only one packing slip that doesn't include all serial numbers. For example, if you have three packing slips, and each packing slip includes two serialized items, you can't create a partial invoice for one item from each packing slip.

## What do I do when a serial number isn't readable?
If a serial number can't be read or scanned, you can create a blank line for the item by clicking **Not readable** on the **Serial numbers** page. If the serial number becomes available later, you can update the invoice or packing slip. For more information, see the next section, “Can I correct or change the serial numbers I have registered for a sales order?”

## Can I correct or change the serial numbers that I have registered for a sales order?
Yes, you can correct serial numbers if the following conditions are met:
-   **Invoices** – You can change the serial numbers for items that you haven't yet invoiced. The packing slip is then also updated. However, if a sales order line was corrected by registering a negative quantity, you can't change serial numbers for the sales order line.
-   **Packing slips** – You can't partially correct a packing slip line that contains serialized items. You must reverse the full quantity for the line. If a packing slip has been canceled or corrected, you don't have to register the reversed serial numbers again when you create a new packing slip for the same serialized items. The numbers that were registered will be used.

## Can I view the serial numbers that were shipped together with a specific packing slip, or that were included on an invoice?
Yes, you can run an inquiry on the packing slip journal line or invoice journal line to view a list of all serial numbers that were included in the document.

## Can I view the serialized items that I have on hand?
No, you can't view the serialized items that you have on hand, because serial numbers aren't registered for items until the items are sold.

## Can I register serial numbers for catchweight items?
No, you can't register serial numbers for catch-weight items during the sales process. Additionally, if a product is set up as a catch-weight item, you can't assign the product to a tracking dimension group that is set up to use serial numbers only during the sales process.

## Can I register serial numbers at the retail POS?

Yes, the retail point of sale (POS) will prompt the user to enter a serial number when the user sells an item that is assigned a tracking dimension group that is set up to use serial numbers only during the sales process.

## What security roles are required in order to register serial numbers during the sales process?
This functionality is available to all roles that can maintain sales packing slips and sales invoices. The following duties let workers correct serial numbers, and register blank entries for serial numbers that can't be read or scanned:
-   Maintain serial number corrections
-   Maintain registration of non-readable serial numbers







[!INCLUDE[footer-include](../../includes/footer-banner.md)]