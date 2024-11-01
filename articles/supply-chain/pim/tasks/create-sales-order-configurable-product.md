--- 
title: Create a sales order for a configurable product
description: Learn how to apply a configuration template to a product on a sales order, including a step-by-step process for creating sales orders.
author: sgmsft
ms.author: shwgarg
ms.topic: how-to
ms.date: 08/29/2018
ms.custom: 
ms.reviewer: kamaybac 
ms.search.form: DefaultDashboard, SalesOrderProcessingWorkspace, SalesCreateOrder, SalesTable, PCRuntimeConfigurator, PCTemplateConfigurationSelection    
---

# Create a sales order for a configurable product

[!include [banner](../../includes/banner.md)]

This procedure shows how to apply a configuration template to a product on a sales order. This example uses the D0006 speaker model in the USMF demo data company. Typically, a sales order processor uses this procedure.

## Create a sales order

1. Go to **Sales and marketing \> Workspaces \> Sales order processing and inquiry**.
1. Select **New**.
1. Select **Sales order**.
1. In the **Customer account** field, select *US-001*. 
1. Select **OK**.
1. In the **Item number** field, select *D0006*.
    * For this task, you must select a configurable product.  
1. Select **Product and supply**.
1. Select **Configure line**.
    * Note that the price has changed, based on the configuration that was selected, and that the **Include cable** field is now set to *True*.  
    * Note the default price and the settings that are selected for the cable.  
1. Select **Load template**.
    * This example shows how you can apply a template to select a predefined configuration. If you're using this procedure as a task guide and want to see the other attribute values that are available, you must select the **Unlock** button.  
1. Select **OK**.
1. Select **OK**.
1. Expand the **Line details** section.
1. Select the **Product** tab.
    * The configuration of the item is now listed under the product dimensions.  
1. Close the page.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]