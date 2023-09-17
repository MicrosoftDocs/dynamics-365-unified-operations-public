--- 
# required metadata 
 
title: Configure wave processing example
description: This article provides an example of how to set up the criteria that determine what work is generated for a warehouse when a wave is processed, and whether waves are processed manually or automatically.
author: Mirzaab
ms.date: 03/17/2021
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: WHSWaveTemplateTable, InventLocationIdLookup, WHSParameters, ProdParameters, whswavetablecreatenew, WHSWaveTable, WHSWaveAttributes, WHSKanbanWaveTable, WHSWaveTableListPage, WHSKanbanWaveTableListPage
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: mirzaab
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Configure wave processing example

[!include [banner](../../includes/banner.md)]

This article provides an example of how to set up the criteria that determine what work is generated for a warehouse when a wave is processed, and whether waves are processed manually or automatically. You specify the criteria by setting up wave templates and queries that match a wave with released lines in sales orders, production orders, or kanban orders.

## Enable sample data

To work through this scenario using the sample records and values specified here, you must use a system where the standard [demo data](../../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed. You must also select the **USMF** legal entity before you begin.

## Example scenario: configure wave processing

This example scenario walks through many of the diverse settings that affect how waves are created, populated, processed, and released.

1. Go to **Warehouse management > Setup > Waves > Wave templates**.
1. Select **New**.
1. In the **Wave template name** field, type a value. When you set up a wave template, you specify the sequence in which the templates will be matched to released lines on sales orders, production orders, or kanbans. When a line is released to the warehouse or to production, it uses the first wave template that it meets the criteria for. We recommend that you put templates with the most specific criteria at the top of the list. The broader the criteria, the more likely it is for a line to meet the criteria, and this could lead to lines being assigned to the wrong wave.  
1. In the **Wave template description** field, type a value.
1. In the **Site** field, enter or select a value. If you're using USMF, you can select site 2.  
1. In the **Warehouse** field, enter or select a value. If you're using USMF, you can select warehouse 24.  
1. Set the **Automate wave creation** field to **Yes**. Select this option to automatically create a wave when a sales order, production order, or kanban is released to the warehouse.  
1. Set the **Process wave at release to warehouse** option to **Yes**. Select this option to automatically process the wave and create work when a line is released to the warehouse.  
1. Set the **Automate wave release option** to **Yes**. Select this option to automatically release the wave. The picking work is created and made available on mobile devices.  
1. Set the **Assign to open waves option** to **Yes**. Lines are assigned to waves based on the query filter for the wave template.  
1. Set the **Process wave automatically at threshold option** to **Yes**. Select this option to automatically process the wave when its values reach the thresholds for weight, shipment, and lines specified in the **Wave thresholds** field group. This option is available only if **Shipping** is selected in the **Wave template type** field.  
1. Set the **Automate replenishment work release option** to **Yes**. Select this option to create demand-based replenishment work and release it automatically. You must add the replenishment wave method to the wave template, and create a replenishment template using the **Wave demand** type.  
1. Use settings in the **Default values** filed group to assign wave attributes. Wave attributes act as filters, to restrict the kind of items that can use the wave. For example, you could specify an item group.  
1. Expand the **Methods** section and set the actions taken by the wave template. Wave template methods allow you to control the sequence of activities that each wave is going through when it's processed. For example, you might have a method for wave replenishment. When you add a method, it's automatically listed in the appropriate location in the sequence of steps. If you've set the **Automate replenishment work release** option to **Yes**, you need to add the replenish method here.  
1. Select **Save**.
1. Close the page.
1. Go to **Warehouse management > Setup > Warehouse management parameters**.
1. Expand the **Wave processing** section.
1. In the **Wave processing batch group** field, enter or select a value.
1. Set the **Process waves in batch option** to **Yes**.
1. In the **Wait for lock (ms)** field, enter a number. Enter the time, in milliseconds, that an allocation step will wait for a system resource that is locked by another allocation step. When this time is exceeded, the wave is not processed and an error message is displayed.  
1. Select **Save**.
1. Close the page.
1. Go to **Production control > Setup > Production control parameters**.
1. In the **Release to warehouse** field, select an option.

    For sales orders and kanban orders, inventory must be reserved before the order is released to the warehouse. Otherwise, the items or allocation lines cannot be processed in a wave. For production orders, you also have the option of choosing **Allow partial reservation**. For example, this is useful if you have the materials that you need to start production, and can wait until the additional materials become available to finish the process. If you select this option, you must manually repeat the release to warehouse process when the additional materials become available.
1. Close the page.

## Additional resources

- [Wave creation and processing](../wave-processing.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
