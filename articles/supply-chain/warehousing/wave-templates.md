---
# required metadata

title: Wave templates
description: This article describes how to set up the criteria that determine whether waves are processed manually or automatically, and the work that is generated for a warehouse when a wave is processed.
author: Mirzaab
ms.date: 03/08/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this article to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac

# ms.tgt_pltfrm: 
# ms.custom: [used by loc for articles migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mirzaab
ms.search.validFrom: 2021-03-08
ms.dyn365.ops.version: 10.0.18
---

# Wave templates

[!include [banner](../includes/banner.md)]

This article describes how to set up the criteria that determine whether waves are processed manually or automatically, and the work that is generated for a warehouse when a wave is processed. You specify the criteria by setting up wave templates and queries that match a wave with released lines in sales orders, production orders, and kanbans.

## Settings for wave templates

When you set up a wave template, you specify the following:

- The **Site** and **Warehouse** that the template will create work for.
- The order in which the templates will be evaluated. The sequence in which the templates are matched to released lines on sales orders, production orders, and kanbans. When a line is released, the system applies the first wave template that the line meets the criteria for. The broader the criteria, the more likely it is for a line to meet the criteria, so you should put the templates with the most specific criteria at the top of the list. Use the **Move up** and **Move down** buttons on the Action Pane to arrange templates in the list.
- The actions taken by each template. The wave **Methods** perform the actions that are created by the template, such creating or distributing work for each type of wave template.
- The wave attributes (filters) that must apply for the wave template to be used.

> [!NOTE]
> If needed, a developer can create additional methods. You can view the full list of methods on the **Wave process methods** page.

Some settings represent strategic decisions for wave processing, as follows:

- If the template is used for shipping items for sales orders and transfer orders, or used for moving items to production for production orders or kanbans.
- If a wave is processed manually or automatically, as follows:

  - **Manual processing** – The line is added to a wave and the inventory is reserved, however, you must select **Process** on the **All waves** list page to create the picking work for the order.
  - **Automatic processing** – You can fully or partially automate wave processing. If you fully-automate wave processing, a wave is created that includes the line from the sales order, production order, or kanban when a sales order, production order, or kanban is created. The items are deducted from on-hand inventory and the picking work is created. If you partially automate wave processing, you can specify values that will trigger wave processing. For example, you can specify a maximum weight for shipments that will trigger wave processing when the total weight of the lines in the wave reaches the value.

- If you assign shipments to an open wave. For example, if you promise customers that an order placed by 12:00 PM will ship within 24 hours, you can set up the wave template to automatically assign order lines to an open wave until 12:00 PM. At that time, the wave is automatically processed.

When a wave is processed, the picking work that is created is based on the work template and the location directive that is specified for the warehouse. The work template specifies how the picking work is created, and the location directive specifies the pick and put locations.

## Create a wave template

To set up a wave template, follow these steps:

1. Go to **Warehouse management** \> **Setup** \> **Waves** \> **Wave templates**.
1. Select **New** to create a new wave template.
1. In the **Wave template type** field, select one of the following options:

    - *Shipping* - Use the wave template for shipping items for sales orders and transfer orders.
    - *Production orders* - Use the wave template to move items for production orders.
    - *Kanban* - Use the wave template to move items for kanban orders.

1. In the **Wave template name** and **Wave template description** fields, enter a name and a description for the wave template.

    > [!NOTE]
    > If more than one template is created for a warehouse, the number in the **Wave template sequence** field indicates the position of the template in the sequence in which the templates are applied when the template’s criteria is met. You can select **Move up** or **Move down** to rearrange the sequence of templates.

1. On the **Warehouse selection** FastTab, set the following fields to specify the warehouse and site where the wave template will apply:

    - **Warehouse selection**  – Select one of the following values:

        - *All* – Use the wave template for all warehouses where a more specific wave template hasn't been assigned.
        - *Warehouse group* – Use the wave template for all warehouses in the warehouse group that's selected in the **Warehouse group** field.
        - *Warehouse* – Use the wave template only for the specific warehouse that's selected in the **Warehouse** field.

    - **Site** and **Warehouse** – If the **Warehouse selection** field is set to *Warehouse*, select the site and warehouse where the wave template applies. If you select the warehouse first, the site will be filled in automatically. If you select the site first, the warehouse list will be filtered so that it shows only warehouses at that site.
    - **Warehouse group** – If the **Warehouse selection** field is set to *Warehouse group*, select the warehouse group where the wave template applies. For more information about how to set up warehouse groups, see [Warehouse groups](warehouse-groups.md).

1. If you want to automate wave processing, make the following settings as needed:

    - **Automate wave creation** - Set this to *Yes* to automatically create a wave when a sales order, production order, or kanban is released to the warehouse.
    - **Assign to open waves** - Set this to *Yes* to automatically assign lines to an open wave when the lines are released. Lines are assigned to waves based on the query filter for the wave template.
    - **Process wave at release to warehouse** - Set this to *Yes* to automatically process the wave and create work when a line is released to the warehouse.
    - **Process wave automatically at threshold** - Set this to *Yes* to automatically process the wave when its values reach the thresholds for weight, shipment, and lines specified in the **Wave thresholds** field group. This setting is only active if *Shipping* is selected in the **Wave template type** field.
    - **Automate wave release** - Set this to *Yes* to automatically release the wave. The picking work is created and made available on mobile devices.
    - **Automate replenishment work release** - Set this to *Yes* to create demand-based replenishment work and release it automatically. You must add the replenishment wave method to the wave template, and create a replenishment template using the *Wave demand* type. Set up a replenishment template on the **Replenishment templates** page. This requires that you add the replenish method to the wave template.
    - **Continue wave processing when work creation fails** - When set to *Yes*, the system will use a blank location if it can't reserve inventory at the location proposed by the location directive (for example, because the inventory is no longer available). When set to *No*, the wave will fail if the system can't reserve the inventory.

1. Set the **Wave thresholds** field group as needed:
    - **Wave weight threshold** - Enter the maximum weight a wave can contain.
    - **Shipment threshold** - Enter the maximum number of shipments that can be included in a wave.
    - **Line threshold** - Enter the maximum number of lines that can be included in a wave.

1. In the **Default values** field group, select the wave attributes to use as additional criteria for the wave template. Wave attributes are useful for assigning additional criteria, such as a specific customer name, to a wave template. You create these attributes on the **Wave attributes** page. 

1. Set **Wave notification policy** to the policy you want to use for generating notifications related to waves that use this template. For an example of a wave notification policy, see [Wave execution notifications](wave-execution-notifications.md).

1. On the **Methods** FastTab, the **Selected methods** pane lists the methods for the selected wave template. The wave methods perform the actions that are created by the template, such creating or distributing work. These actions are also referred to as wave steps. Wave methods are predefined for each type of wave template. You cannot remove the predefined wave methods. However, you can rearrange the order of the methods and add additional methods. For example, if you’re creating a wave template for shipping, you can add methods for replenishment and containerization. Wave containerization can be added to a sequence of wave methods to define the containerization of the lines processed in a wave template. To add an additional method, do the following:

    - Select a method on the **Remaining methods** pane, and then select the **Left** arrow to add it to the **Selected methods** pane.
    - To change the sequence, select a method, and then select **Up** or **Down** arrows.

    > [!NOTE]
    > When you add a method, it’s automatically listed in the appropriate location in the sequence of steps.

1. To set up the query that will match released lines to an appropriate wave, select **Edit query** on the Action Pane.
1. To verify that the wave template settings are valid, select **Validate template**.
