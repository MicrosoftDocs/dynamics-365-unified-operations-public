--- 
title: Create a released product for a single company
description: Learn how to create a single released product in the context of a single legal unit, including a step-by-step process for creating released products. 
author: sgmsft
ms.author: shwgarg
ms.topic: how-to
ms.date: 5/27/2026
ms.custom: 
ms.reviewer: kamaybac    
ms.search.form: EcoResProductDetailsExtended, EcoResProductCreate, UnitOfMeasureLookup, DimensionLookup
---

# Create a released product for a single company

[!include [banner](../../includes/banner.md)]

This procedure shows how to create a single released product for a single legal unit. When you create the released product, it's available only in that legal unit. You can perform this task for demo data company USMF. A product designer usually performs the task.

## Create a released product

1. Go to **Released products**.
1. Select **New**.
1. In the **Product number** field, enter a value.

    If the **Product number** field isn't automatically filled in, enter a unique product number. Perform this step only if you haven't set up any number sequence for product numbers.
1. In the **Product name** field, enter a value.

     The **Product name** defaults to the search name. If needed, select a different search name.  
1. In the **Item model group** field, select the dropdown button to open the lookup.

    The item model groups contain settings that determine how items are controlled and handled on item receipts and issues. The settings also determine how the consumption of items is calculated.  
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the Item group field, click the drop-down button to open the lookup.

    Use item groups to manage inventory by dividing inventory items into groups based on item characteristics. For example, to manage how information is posted to main accounts, create a series of different item groups that are associated with specific main accounts. This process lets you track the inventory value of items at different stages.  
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the **Storage dimension group** field, select the dropdown button to open the lookup.

    The storage dimensions help you control how items are stored and taken from inventory. For example, a storage dimension can be Site and Warehouse.  
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the **Tracking dimension group** field, select the dropdown button to open the lookup.

    The tracking dimension group determines which tracking dimensions you can add to a product. For example, the batch number and serial number are used to track inventory items.  
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the **Inventory unit** field, select the dropdown button to open the lookup.

    The inventory unit determines how the product is quantified when it's stored in inventory.  
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the **Purchase unit** field, select the dropdown button to open the lookup.

    The purchase unit determines how the product is quantified when it's purchased from a vendor.  
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the **Sales unit** field, select the dropdown button to open the lookup.
    The sales unit determines how the product is quantified when it's sold to a customer.  
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the **BOM unit** field, select the dropdown button to open the lookup.

    The BOM unit determines how the product is quantified when including it in a bill of materials (BOM).  
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the **Item sales tax group** field, select the dropdown button to open the lookup.

    The item sales tax group in the **Sales taxation group** determines how sales tax is calculated for each item.  
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the **Item sales tax group** field, select the dropdown button to open the lookup.

    The item sales tax group in the **Purchase taxation group** determines how purchase tax is calculated for each item.  
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. Click OK.

## Add product characteristics

1. Expand or collapse the **Manage inventory** section.
1. In the **Net weight** field, enter a number.
1. In the **Tare weight** field, enter a number.
1. In the **Gross depth** field, enter a number.
1. In the **Gross width** field, enter a number.
1. In the **Gross height** field, enter a number.
1. In the **Volume** field, enter a number.

## Add financial dimensions

1. Expand or collapse the **Financial dimensions** section.
1. In the **BusinessUnit** field, select the dropdown button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the **CostCenter** field, select the dropdown button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the **Department** field, select the dropdown button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the **ItemGroup** field, select the dropdown button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
