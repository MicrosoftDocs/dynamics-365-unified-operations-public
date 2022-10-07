---
title: Example scenario – Pack containers with the Warehouse Management mobile app
description: This article provides a scenario that illustrates how to pack containers with the Warehouse Management mobile app.
author: perlynne
ms.author: perlynne
ms.reviewer: kamaybac
ms.search.form: WHSMobileAppFlowStepListPage, WHSMobileAppFlowStepAddDetour,WHSMobileAppFlowStepDetourSelectFields, WHSRFMenuItem, WHSPackProfile, WHSWorker, WHSPack
ms.topic: how-to
ms.date: 10/14/2022
ms.custom: bap-template
---

# Example scenario – Pack containers with the Warehouse Management mobile app

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

This article provides an example scenario that shows how to set up a *Warehouse Management mobile app packing flow* and use it to process a simple outbound sales order by packing a container and closing it using the *Warehouse Management mobile app*. The scenario leverages the [detour](warehouse-app-detours.md) and [data inquiry](warehouse-app-data-inquiry.md) capabilities of the mobile app. For more information about the feature that makes this functionality possible, see also [Pack containers using the Warehouse Management mobile app](warehouse-app-packing-containers.md).

The following illustration shows the packing functionality that this scenario adds to the mobile app.

![Warehouse app packing example scenario.](media/wma-packing-demo.png "Warehouse app packing example scenario")

## Prerequisites

### Turn on the Pack containers using the Warehouse Management mobile app feature and its prerequisites

Before you can pack containers using the Warehouse Management mobile app, you must complete the following procedure to turn on the required features.

1. Go to **System administration \> Workspaces \> Feature management**. (For more information about how to use the **Feature management** workspace, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).)

1. Turn on each of the following features in the following order (all are listed as part of the *Warehouse management* module):
    1. *Multi-level detours for the Warehouse Management mobile app*<br>(See also [Multi-level detours for the Warehouse Management mobile app](warehouse-app-detours.md).)
    1. *Auto-submit detour steps for the Warehouse Management mobile app*<br>(See also [Auto-submit detour steps for the Warehouse Management mobile app](warehouse-app-detours.md).)
    1. *Warehouse management app data inquiry flow*<br>(See also [Query data using Warehouse Management mobile app detours](warehouse-app-data-inquiry.md).)
    1. *Pack containers using the Warehouse Management mobile app*<br>(This is the feature described in this article.)

1. Go to **Warehouse management \> Setup \> Mobile device \> Warehouse app field names** and select **Create default setup** on the Action Pane. This will update the field names in the Warehouse Management mobile app. Repeat this step for each legal entity (company) where you use the Warehouse Management mobile app. For more information, see [Configure fields for the Warehouse Management mobile app](configure-app-field-names-priorities-warehouse.md).

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device steps** and select **Create default setup** on the Action Pane. Repeat this step for each legal entity (company) where you use the Warehouse Management mobile app.

### Use the Warehouse Management mobile app version 2.0.31.0 or newer

To see the newest icons and user experience enhancements related to the mobile app packing process, you must use the Warehouse Management mobile app version 2.0.31.0 or newer.

### Make sample data available

To work through this scenario by using the sample records and values that are specified here, you must be on a system where the standard [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed. Additionally, you must select the **USMF** legal entity before you begin. You can also use this scenario as guidance for using the feature on a production system. However, in that case, you must substitute your own values for each setting that is described here.

The example scenario uses the the demo data associated with the worker/person *Julia Funderburk*.

## Set up a worker to pack containers

For each worker that will use the Warehouse Management mobile app to pack containers, you must set up a *Container packing policy* and *Packing profile ID*, as described in the following procedure.

1. Go to **Warehouse management > Setup > Worker**.
1. Select **Edit** on the Action Pane.
1. Select worker *Julia Funderburk* on the list pane.
1. Expand the **Profile** FastTab and make the following settings:
    - **Container packing policy** - Select *WH62Close*, which will move containers to the *Baydoor* location when they are closed.
    - **Packing profile ID** - Select *WH62*, which won't create warehouse work after a container is closed.
1. Expand the **Default packing station** FastTab and make the following settings:
    - **Site** - Select *6*, which is the site for the warehouse we will use in this scenario.
    - **Warehouse** - Select *62*, which is a warehouse already enabled for the packing process in the demo data.
    - **Location** - Select *Pack*. Note that the Warehouse Management mobile app will always prompt the worker to confirm this value, which can edited if needed. If you don't provide a default packing location, workers will always need to scan or look up the packing location, which you can make possible by using the [data inquiry](warehouse-app-data-inquiry.md) capability.
1. Select **Save** on the Action Pane.

> [!NOTE]
> You can set up the system to automatically print container labels when a new container record is created. For details, see [Print container labels](print-container-labels.md).

## Create a mobile device menu item for packing inventory into containers

Follow these steps to create a mobile device menu item that will allow workers to pack inventory into containers using the mobile app.

1. Go to **Warehouse management > Setup > Mobile device > Mobile device menu items**.
1. Select **New** on the Action Pane to add a new mobile device menu item.
1. Make the following settings for the new menu item:
    - **Menu item name** - Enter *Packing*, which will be the internal name for the new menu item.
    - **Title** - Enter *Packing*, which will be the display name of this menu item in the mobile app.
    - **Mode** - Select *Indirect*.
    - **Activity code** - Select *Pack inventory into containers*.
1. Select **Save** on the Action Pane.

## Create a mobile device menu item for creating containers

Follow these steps to create a mobile device menu item that will allow workers to create containers using the mobile app.

1. Go to **Warehouse management > Setup > Mobile device > Mobile device menu items**.
1. Select **New** on the Action Pane to add a new mobile device menu item.
1. Make the following settings for the new menu item:
    - **Menu item name** - Enter *Create container*.
    - **Title** - Enter *Create container*.
    - **Mode** - Select *Indirect*.
    - **Activity code** - Select *Container creation*.
1. Select **Save** on the Action Pane.

## Create a mobile device menu item for closing containers

Follow these steps to create a mobile device menu item that will allow workers to close containers using the mobile app.

1. Go to **Warehouse management > Setup > Mobile device > Mobile device menu items**.
1. Select **New** on the Action Pane to add a new mobile device menu item.
1. Make the following settings for the new menu item:
    - **Menu item name** - Enter *Close container*.
    - **Title** - Enter *Close container*.
    - **Mode** - Select *Indirect*.
    - **Activity code** - Select *Container closing*.
1. Select **Save** on the Action Pane.

## Add the three new mobile device menu items to the menu

Now that you have created the required new mobile device menu items, you must add them to the mobile device menu, which will make these menu items available to workers. Follow these steps:

1. Go to **Warehouse management > Setup > Mobile device > Mobile device menu**.
1. Select **Edit** on the Action Pane.
1. On the list pane, select *Outbound*.
1. In the **Available menus and menu items** column, select the new *Packing* mobile device menu items
1. Select the new *Packing* mobile device menu items in the **Available menus and menu items** list and select the **Add** button (right arrow) to move it into the **Menu structure** column.
1. Repeat the previous step for the other two new menu items, *Create container* and *Close container*.
1. Select **Save** on the Action Pane.

## Add a detour for creating a container

The setup so far now enables workers to use the mobile aoo to pack items into containers, but they'll need to select the *Create container* and *Close container* processes directly from the menu, so you can still streamline the process further. To make it possible for workers to create a container from within the packing flow, you'll now add a [detour](warehouse-app-detours.md). 

Follow these steps to make it possible to create a new container on the packing flow page that asks workers to scan the container to pack.

1. Go to **Warehouse management \> Setup > Mobile device \> Mobile device steps**.
1. In the **Filter** field, enter *ContainerIdToPack* to open a drop-down list with possible searches, then select *Step ID: "ContainerIdToPack"* from the drop-down list.
1. Select the found record in the grid and then, on the Action Pane, select **Add step configuration** to open a drop-down dialog box. In the drop-down dialog box, set **Menu item** to *Packing* and select **OK**.
1. The details page for the new step configuration opens (called **Packing : ContainerIdToPack**). Expand the **Available detours (menu items)** FastTab and select **Add** on its toolbar.
1. The **Add detour** dialog opens. In the **Available detours** list, find and select *Create container* (which is one of the menu items that you created for this scenario).
1. Select **OK** to close the dialog box and add the selected menu item to the available detours list.
1. Select the new detour, and then select **Select fields to send** on the FastTab toolbar.
1. The **Select fields to send** dialog opens. In the **Send from packing** section, set the following values for the empty row that has already been added there:
    - **Copy from Packing:** *Location*
    - **Paste in Create container:** *Location*
    - **Auto submit:** *Selected* (so the worker doesn't need to confirm the value)
1. In the **Send from packing** section, select **Add** from the toolbar to add one more row and then set the following values for it:
    - **Copy from Packing:** *Shipment*
    - **Paste in Create container:** *Shipment*
    - **Auto submit** *Selected*
1. In the **Bring back from create container** section, set the following values for the empty row that has already been added there:
    - **Copy from Create container:** *Container ID*
    - **Paste in Packing:** *Container ID*
    - **Auto submit:** *Cleared* (you want the worker to confirm this value)
1. In the **Bring back from create container** section, select **Add** from the toolbar to add one more row and then set the following values for it:
    - **Copy from Create container:** *Refresh* (automatically updates the page when returning from the detour)
    - **Paste in Packing:** *Refresh* (triggers the update logic)
    - **Auto submit:** *Selected* (automatically updates the page, for example to update the **Available open containers** field)
   1. Select **OK** to close the dialog box.
1. Close the page.

> [!NOTE]
> Only Warehouse Management mobile app pages that contain the *Refresh* option can be used to trigger an automatic page refresh as part of a detour process. This is why you must include a row both the **Copy from Create container** and **Paste in Packing** fields set to *Refresh* and with **Auto submit** selected.

## Add a detour for closing a container

To make it possible for workers to close a container from within the packing flow, you'll now add another [detour](warehouse-app-detours.md). Follow these steps to make it possible to close a container on the packing flow page that asks workers to scan an item.

1. Go to **Warehouse management \> Setup > Mobile device \> Mobile device steps**.
1. In the **Filter** field, enter *ItemId* to open a drop-down list with possible searches, then select *Step ID: "ItemId"* from the drop-down list.
1. Select the found record in the grid and then, on the Action Pane, select **Add step configuration** to open a drop-down dialog box. In the drop-down dialog box, set **Menu item** to *Packing* and select **OK**.
1. The details page for the new step configuration opens (called **Packing : ItemId**). Expand the **Available detours (menu items)** FastTab and select **Add** on its toolbar.
1. The **Add detour** dialog opens. In the **Available detours** list, find and select *Close container* (which is one of the menu items that you created for this scenario).
1. Select **OK** to close the dialog box and add the selected menu item to the available detours list.
1. Select the new detour, and then select **Select fields to send** on the FastTab toolbar.
1. The **Select fields to send** dialog opens. In the **Send from packing** section, set the following values for the empty row that has already been added there:
    - **Copy from Packing:** *Location*
    - **Paste in Close container:** *Location*
    - **Auto submit** *Cleared* (so the worker has a chance to inspect the location and can choose whether to look up a container ID)
1. In the **Send from packing** section, select **Add** from the toolbar to add one more row and then set the following values for it:
    - **Copy from Packing:** *Shipment*
    - **Paste in Close container:** *Shipment*
    - **Auto submit** *Cleared* (so the worker has a chance to inspect the shipment and can choose whether to look up a container ID)
1. In the **Bring back from create container** section don't add anything because you don't want to pass any values back from this detour.
1. Select **OK** to close the dialog box.
1. Close the page.

## Create the five lookup menu items

The setup so far now enables workers to use the mobile app to pack inventory into containers, but you can still add more lookup logic by using the [data inquiry](warehouse-app-data-inquiry.md) capability as part of the process. Now, you'll add the following look up mobile device menu items:

- **Look up location** - Used to inquire for packing locations from which inventory should get packed.
- **Look up shipment** - Used to inquire for shipments that need to be packed.
- **Look up item** - Used to inquire for item numbers that need to be packed.
- **Look up container type** -  Used to inquire for container types for the container creation process.
- **Look up container** - Used to inquire for containers to close.

The following subsections show how to set up these menu items.

### Create a mobile device menu item to look up a location

Many different lookup capabilities exists to look up packing locations. This section provides an example of how to set up a simple lookup to find locations related to a specific *Location profile*, which will be used to filter locations used for packing operations.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. On the Action Pane, select **New** to add a mobile device menu item.
1. Set the following values for the new item:

    - **Menu item name:** *Look up location*
    - **Title:** *Look up location*
    - **Mode:** *Indirect*

1. On the **General** FastTab, set the following values:

    - **Activity code:** *Data inquiry*
    - **Use process guide:** *Yes* (This value is automatically selected.)
    - **Table name:** *WMSLocation* (You want to look up warehouse locations based on, for example, a location profile ID.)

1. On the Action Pane, select **Edit query** to define a query that is based on the selected base table. In this case, you will use the locations table. Note that you can join to related tables when needed.
1. In the query editor dialog, on the **Range** tab, add the following lines to the grid.

    | Table | Derived table | Field | Criteria |
    |---|---|---|---|
    | Locations | Locations | Warehouse |  |
    | Locations | Locations | Location profile ID | PACK |

    In this query, the **Warehouse** field will be assigned automatically based based on the worker's current warehouse.

    If you want to specify how the list will be sorted, you can set this up on the **Sorting** tab.

1. Select **OK**.
1. In addition to defining the query, you must select which fields will be shown on the cards on the inquiry list page. Therefore, on the Action Pane, select **Field list**.
1. On the **Field list** page, set the following values:
    - **Display field 1:** *wMSLocationId* (This field value will be used as the header for each card.)
    - **Display field 2:** *inventLocationId*
    - **Display field 3:** *LocProfileId*
    - **Display field 4:** *whsDisplayQty()*
    - **Display field 5:** *whsDisplayItemId()*

1. On the Action Pane, select **Save**. Then close the page.

### Create a mobile device menu item to look up a shipment

Many different lookup capabilities exists to look up shipments. This section provides an example of how to set up a simple lookup to find active shipments.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. On the Action Pane, select **New** to add a mobile device menu item.
1. Set the following values for the new item:

    - **Menu item name:** *Look up shipment*
    - **Title:** *Look up shipment*
    - **Mode:** *Indirect*

1. On the **General** FastTab, set the following values:

    - **Activity code:** *Data inquiry*
    - **Use process guide:** *Yes* (This value is automatically selected.)
    - **Table name:** *WHSShipmentTable*

1. On the Action Pane, select **Edit query** to define a query that is based on the selected base table. In this case, you will use the locations table. Note that you can join to related tables when needed.
1. In the query editor, on the **Range** tab, add the following lines to the grid.

    | Table | Derived table | Field | Criteria |
    |---|---|---|---|
    | Shipments | Shipments | Warehouse |  |
    | Shipments | Shipments | Shipment status | Open, Waved, "In process" |

    In this query, the **Warehouse** field will be assigned automatically based based on the worker's current warehouse.

    If you want to specify how the list will be sorted, you can set this up on the **Sorting** tab.

1. Select **OK**.
1. In addition to defining the query, you must select which fields will be shown on the cards on the inquiry list page. Therefore, on the Action Pane, select **Field list**.
1. On the **Field list** page, set the following values:
    - **Display field 1:** *ShipmentId* (This field value will be used as the header for each card.)
    - **Display field 2:** *ShipmentStatus*
    - **Display field 3:** *displayDeliveryName()*
    - **Display field 4:** *displayNumberOfContainers()*
    - **Display field 5:** *displayNumberOfLoadLines()*
    - **Display field 6:** *displayTotalVolume()*
    - **Display field 7:** *displayTotalWeight()*
    - **Display field 8:** *displayShipmentDateTime()*

1. On the Action Pane, select **Save**. Then close the page.

### Create a mobile device menu item to look up an item

Many different lookup capabilities exists to inquire for item information. This section provides an example of how to look up item information based on load lines, though you might instead choose to filter based on a wildcard search. You might also choose to use the [packing work](packing-work.md) feature to look up or join to closed put work lines for work that brings inventory to a packing area.

In this example, a simple lookup will be filtered based on the already captured *Shipment ID* as part of the packing process.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. On the Action Pane, select **New** to add a mobile device menu item.
1. Set the following values for the new item:

    - **Menu item name:** *Look up item*
    - **Title:** *Look up item*
    - **Mode:** *Indirect*

1. On the **General** FastTab, set the following values:

    - **Activity code:** *Data inquiry*
    - **Use process guide:** *Yes* (This value is automatically selected.)
    - **Table name:** *WHSLoadLine*

1. On the Action Pane, select **Edit query** to define a query that is based on the selected base table. In this case, you will use the locations table. Note that you can join to related tables when needed.
1. In the query editor, on the **Range** tab, make sure only the following line is shown in the grid.

    | Table | Derived table | Field | Criteria |
    |---|---|---|---|
    | Load details | Load details | Shipment ID |  |

1. Select **OK**.
1. In addition to defining the query, you must select which fields will be shown on the cards on the inquiry list page. Therefore, on the Action Pane, select **Field list**.
1. On the **Field list** page, set the following values:
    - **Display field 1:** *ItemId* (This field value will be used as the header for each card.)
    - **Display field 2:** *displayItemName()*
    - **Display field 3:** *displayCustName()*
    - **Display field 4:** *displayInventQty()*
    - **Display field 5:** *displayInventUOM()*

1. On the Action Pane, select **Save**. Then close the page.

<!--KFM: Continue here-->

### Create mobile device menu item Look up container type

Many different look up capabilities exists to look up container types. In this example all container types will get included, but it might make sense to filter based on *Container group ID* by joining to *Container group details*. <!--check--> or other entities.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. On the Action Pane, select **New** to add a mobile device menu item.
1. Set the following values for the new item:

    - **Menu item name:** *Look up container type*
    - **Title:** *Look up container type*
    - **Mode:** *Indirect*

1. On the **General** FastTab, set the following values:

    - **Activity code:** *Data inquiry*
    - **Use process guide:** *Yes* (This value is automatically selected.)
    - **Table name:** *WHSContainerType*

1. On the Action Pane, select **Edit query** to define a query that is based on the selected base table (in this case, the container type table. Note that you can join to related tables when needed).
1. In the query editor, on the **Range** tab, add the following lines to the grid.

    | Table | Derived table | Field | Criteria |
    |---|---|---|---|
    | Container type | Container type | Container type code | * |

    The "*" indicates that all container types will get displayed.

1. You must select which fields will be shown on the cards on the inquiry list page. Therefore, on the Action Pane, select **Field list**.
1. On the **Field list** page, set the following values:
    - **Display field 1:** *ContainerTypeCode* (This field value will be used as the header for each card.)
    - **Display field 2:** *Description*
    - **Display field 3:** *MaxVolume*
    - **Display field 4:** *MaxWeight*
    - **Display field 5:** *Height*
    - **Display field 6:** *Length*
    - **Display field 7:** *Width*
    - **Display field 8:** *FlexibleVolumeDimensions*

1. On the Action Pane, select **Save**. Then close the page.

If you want to specify how the list will be sorted, you can set up the sorting on the **Sorting** tab. In this example the *Maximum volume* field could be a candidate.

### Create mobile device menu item Look up container

Many different look up capabilities exists to look up containers. In this example, the new menu item is configured to find active containers on the current packing location related to the current shipment getting packed.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. On the Action Pane, select **New** to add a mobile device menu item.
1. Set the following values for the new item:

    - **Menu item name:** *Look up container*
    - **Title:** *Look up container*
    - **Mode:** *Indirect*

1. On the **General** FastTab, set the following values:

    - **Activity code:** *Data inquiry*
    - **Use process guide:** *Yes* (This value is automatically selected.)
    - **Table name:** *WHSContainerWarehouseLocationView* - By using this view it will be possible to limit the look up to only show containers for a specific packing location related to a specific shipment.

1. On the Action Pane, select **Edit query** to define a query that is based on the selected base table (in this case, the location table. Note that you can join to related tables when needed).
1. In the query editor, on the **Range** tab, add the following lines to the grid.

    | Table | Derived table | Field | Criteria |
    |---|---|---|---|
    | WHSContainerWarehouseLocationView | WHSContainerWarehouseLocationView | Warehouse |  |
    | WHSContainerWarehouseLocationView | WHSContainerWarehouseLocationView | Location |  |
    | WHSContainerWarehouseLocationView | WHSContainerWarehouseLocationView | Shipment ID |  |
    | WHSContainerWarehouseLocationView | WHSContainerWarehouseLocationView | Container status |!Closed |

1. Select **OK**.

In the query, the **Warehouse**, **Location**, and **Shipment ID** fields will automatically get assigned based on following detour setup.
If you want to specify how the list will be sorted, you can set up the sorting on the **Sorting** tab.

1. In addition to defining the query, you must select which fields will be shown on the cards on the inquiry list page. Therefore, on the Action Pane, select **Field list**.
1. On the **Field list** page, set the following values:

    - **Display field 1:** *ContainerId* (This field value will be used as the header for each card.)
    - **Display field 2:** *ContainerStatus*
    - **Display field 3:** *Weight*
    - **Display field 4:** *WeightUOM*
    - **Display field 5:** *ContainerNum*
    - **Display field 6:** *ContainerReleased*
    - **Display field 7:** *ContainerTypeCode*

1. On the Action Pane, select **Save**. Then close the page.

## Add the new mobile device menu items to a menu

Your new mobile device menu items are now ready to be added to the mobile device menu. This task must be completed before the menu items can be used as part of a detour process. In this example, you will create a new submenu and add the new menu items to it.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu**.
1. On the Action Pane, select **New**.
1. Set the following values on the header of the new record:

    - **Name:** *Inquire*
    - **Description:** *Inquire*

1. In the **Available menus and menu items** list, select the first of the five "look up" mobile device menu items that you just created. Then select the right arrow button to move that item into the **Menu structure** list.
1. Repeat the previous step for the other four new menu items.
1. In the list pane on the left, select the **Main** menu.
1. In the **Available menus and menu items** list, scroll down to the **Menus** section, and select your new **Inquire** menu. Then select the right arrow button to move that item into the **Menu structure** list.

## Configure detours in your mobile device steps

To complete the setup, you must now use the detour configuration on the **Mobile device steps** page to add the five new mobile device menu items to existing menu item flows.
In this example you perform the following setup:

- Add **Look up location** into the **Packing - Scan packing location** step
- Add **Look up shipment** into the **Packing - Scan shipment** step
- Add **Look up item** into the **Packing - Scan item** step
- Add **Look up container** into the **Packing - Scan container to pack** step
- Add **Look up container type** into the **Create container - Scan container type** step
- Add **Look up container** into the **Close container - Scan container** step

### Add **Look up location** as detour

1. Go to **Warehouse management \> Setup > Mobile device \> Mobile device steps**.
1. In the **Filter** field, enter *PackingLocationId*. Then select *Step ID: "PackingLocationId"* in the drop-down list.
1. While the record that is found is selected in the grid, select **Add step configuration** on the Action Pane. In the drop-down dialog box that appears, set the **Menu item** field to *Packing*. Then select **OK** to close the dialog box.
1. On the details page for the new step configuration (**Packing : PackingLocationId**), on the **Available detours (menu items)** FastTab, select **Add** on the toolbar.
1. In the **Add detour** dialog box, find and select the **Look up location** menu item that you previously created.
1. Select **OK** to close the dialog box and add the selected menu item to the detours list.
1. Select the new detour, and then select **Select fields to send** on the toolbar.
1. In the **Select fields to send** dialog box, don't add anything to the **Send from Packing** section, because you don't want to pass any values to the detour menu item. However, in the **Bring back from look up location** section, set the following value for the empty row that has already been added there:
    - **Copy from Look up location** *Location*
    - **Paste in Packing** *Location*
    - **Auto submit** *Cleared* - You want to confirm the value
1. Select **OK** to close the dialog box.
1. Close the page.

### Add **Look up shipment** as detour

1. Go to **Warehouse management \> Setup > Mobile device \> Mobile device steps**.
1. In the **Filter** field, enter *ShipmentId*. Then select *Step ID: "ShipmentId"* in the drop-down list.
1. While the record that is found is selected in the grid, select **Add step configuration** on the Action Pane. In the drop-down dialog box that appears, set the **Menu item** field to *Packing*. Then select **OK** to close the dialog box.
1. On the details page for the new step configuration (**Packing : ShipmentId**), on the **Available detours (menu items)** FastTab, select **Add** on the toolbar.
1. In the **Add detour** dialog box, find and select the **Look up shipment** menu item that you previously created.
1. Select **OK** to close the dialog box and add the selected menu item to the detours list.
1. Select the new detour, and then select **Select fields to send** on the toolbar.
1. In the **Select fields to send** dialog box, don't add anything to the **Send from Packing** section, because you don't want to pass any values to the detour menu item. However, 1. In the **Bring back from Look up shipment** section, set the following value for the empty row that has already been added there:
    - **Copy from Look up shipment** *Shipment ID*
    - **Paste in Packing** *Shipment*
    - **Auto submit** *Cleared* - You want to confirm the value
1. Select **OK** to close the dialog box.
1. Close the page.

### Add **Look up item** as detour

1. Go to **Warehouse management \> Setup > Mobile device \> Mobile device steps**.
1. In the **Filter** field, enter *ItemId*. Then select *Step ID: "ItemID"* for the record that is found for the previously created for Menu item name **Packing**
1. On the details page for the new step configuration (**Packing : ItemId**), on the **Available detours (menu items)** FastTab, select **Add** on the toolbar.
1. In the **Add detour** dialog box, find and select the **Look up item** menu item that you previously created.
1. Select **OK** to close the dialog box and add the selected menu item to the detours list.
1. Select the new detour, and then select **Select fields to send** on the toolbar.
1. In the **Select fields to send** dialog box, in the **Send from Packing** section,  set the following value for the empty row that has already been added there:
    - **Copy from Packing** *Shipment*
    - **Paste in Look up item** *Shipment ID*
    - **Auto submit** *Selected* - You don't want to confirm the value in the Warehouse management mobile app
1. In the **Bring back from Look up item** section, set the following value for the empty row that has already been added there:
    - **Copy from Look up item** *Item number*
    - **Paste in Packing** *Item*
    - **Auto submit** *Cleared* - You want to confirm the value
1. Select **OK** to close the dialog box.
1. Close the page.

### Add **Look up container** as detour for packing

1. Go to **Warehouse management \> Setup > Mobile device \> Mobile device steps**.
1. In the **Filter** field, enter *ContainerIdToPack*. Then select *Step ID: "ContainerIdToPack"* in the drop-down list.
1. While the record that is found is selected in the grid, select **Add step configuration** on the Action Pane. In the drop-down dialog box that appears, set the **Menu item** field to *Packing*. Then select **OK** to close the dialog box.
1. On the details page for the new step configuration (**Packing : ContainerIdToPack**), on the **Available detours (menu items)** FastTab, select **Add** on the toolbar.
1. In the **Add detour** dialog box, find and select the **Look up container** menu item that you previously created.
1. Select **OK** to close the dialog box and add the selected menu item to the detours list.
1. Select the new detour, and then select **Select fields to send** on the toolbar.
1. In the **Select fields to send** dialog box, in the **Send from Create container** section,  set the following value for the empty row that has already been added there:
    - **Copy from Packing** *Location*
    - **Paste in Look up container** *Location*
    - **Auto submit** *Selected* - You don't want to confirm the value
1. Add a new record with:
    - **Copy from Packing** *Shipment*
    - **Paste in Look up container** *Shipment ID*
    - **Auto submit** *Cleared* - You want to confirm the value
1. In the **Bring back from Look up container** section, set the following value for the empty row that has already been added there:
    - **Copy from Look up container** *Container ID*
    - **Paste in Packing** *Container ID*
    - **Auto submit** *Cleared* - You want to confirm the value
1. Select **OK** to close the dialog box.
1. Close the page.

### Add **Look up container type** as detour

1. Go to **Warehouse management \> Setup > Mobile device \> Mobile device steps**.
1. In the **Filter** field, enter *ContainerTypeToCreateContainer*. Then select *Step ID: "ContainerTypeToCreateContainer"* in the drop-down list.
1. While the record that is found is selected in the grid, select **Add step configuration** on the Action Pane. In the drop-down dialog box that appears, set the **Menu item** field to *Create container*. Then select **OK** to close the dialog box.
1. On the details page for the new step configuration (**Create container : ContainerTypeToCreateContainer**), on the **Available detours (menu items)** FastTab, select **Add** on the toolbar.
1. In the **Add detour** dialog box, find and select the **Look up container type** menu item that you previously created.
1. Select **OK** to close the dialog box and add the selected menu item to the detours list.
1. Select the new detour, and then select **Select fields to send** on the toolbar.
1. In the **Select fields to send** dialog box, don't add anything to the **Send from Create container** section, because you don't want to pass any values to the detour menu item. However, in the **Bring back from Look up container type** section, set the following value for the empty row that has already been added there:
    - **Copy from Look up container type** *Container type code*
    - **Paste in Create container** *Container type code*
    - **Auto submit** *Cleared* - You want to confirm the value
1. Select **OK** to close the dialog box.
1. Close the page.

### Add **Look up container** as detour for container creation

1. Go to **Warehouse management \> Setup > Mobile device \> Mobile device steps**.
1. In the **Filter** field, enter *ContainerId*. Then select *Step ID: "ContainerId"* in the drop-down list.
1. While the record that is found is selected in the grid, select **Add step configuration** on the Action Pane. In the drop-down dialog box that appears, set the **Menu item** field to *Close container*. Then select **OK** to close the dialog box.
1. On the details page for the new step configuration (**Close container : ContainerId**), on the **Available detours (menu items)** FastTab, select **Add** on the toolbar.
1. In the **Add detour** dialog box, find and select the **Look up container** menu item that you previously created.
1. Select **OK** to close the dialog box and add the selected menu item to the detours list.
1. Select the new detour, and then select **Select fields to send** on the toolbar.
1. In the **Select fields to send** dialog box, in the **Send from Create container** section,  set the following value for the empty row that has already been added there:
    - **Copy from Close container** *Location*
    - **Paste in Look up container** *Location*
    - **Auto submit** *Selected* - You don't want to confirm the value
1. Add a new record with:
    - **Copy from Close container** *Shipment*
    - **Paste in Look up container** *Shipment ID*
    - **Auto submit** *Selected* - You don't want to confirm the value
1. In the **Bring back from Look up container** section, set the following value for the empty row that has already been added there:
    - **Copy from Look up container** *Container ID*
    - **Paste in Close container** *Container ID*
    - **Auto submit** *Cleared* - You want to confirm the value
1. Select **OK** to close the dialog box.
1. Close the page.

## Create a sales order and complete the work

Follow these steps to create a sales order and complete the work of moving the ordered items to the packing area.

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. On the Action Pane, select **New**.
1. In the **Create sales order** dialog box, in the **Customer account** field, select *US-005*.
1. Select **OK** to close the dialog box.
1. The new sales order is opened and includes a single, empty line on the **Sales order lines** FastTab. Set the following values for the new order line:

    - **Item number:** *A0001*
    - **Quantity:** *2*
    - **Site:** *6*
    - **Warehouse:** *62*

1. While the order line is still selected, select **Inventory \> Reservation** on the toolbar of the **Sales order lines** FastTab.
1. On the **Reservation** page, on the Action Pane, select **Reserve lot** to reserve the full quantity of the selected line in the warehouse.
1. Close the **Reservation** page to return to the sales order.
1. On the Action Pane, on the **Warehouse** tab, select **Release to warehouse**. A message shows the shipment and wave IDs for the order.
1. While the order line is still selected, select **Warehouse** \> **Work details** on the toolbar of the **Sales order lines** FastTab. If you use batch processing to run your waves, you might have to wait a short time for the work to be created.
1. On the **Work** page, on the Action Pane, on the **Work** tab, select **Complete work**.
1. On the **Work completion** page, set the **User ID** field to *62*.
1. On the Action Pane, select **Validate work**.
1. When you receive a message that indicates that your work is valid, select **Complete work** to complete the process of picking the inventory items and putting them in the *Pack* location.
1. Make a note of the **Shipment ID** value that is shown for the work in the upper grid.

## Pack the ordered items into a container

The inventory items have now been brought to the packing area and are ready to be packed into containers. Follow these steps to create a new container in the system and pack and close the container.

1. Open the Warehouse Management mobile app and sign in with **User ID** *62*.
1. Open the previously created **Packing** menu item.
1. Confirm the **Packing location** *Pack*.
1. Enter/scan the **Shipment ID*** from previously.
1. Enter/scan **Item** *A0001*.
1. Use the **Create container** detour button to jump to the *Container creation* process.
1. Enter/scan **Container type** *Box-Large*.
1. Confirm the number sequence container ID based on the *Container ID mode* setup. This will create a new container for the shipment and return to the main packing flow.
1. Enter/scan the new **Container ID** to pack the 2 pcs of item A0001 into the container. If you need to update the case quantity, select the **Quantity** and edit the value before confirming the **Container ID**.
1. Use the **Close container** detour button to jump to the *Container closing** process.
1. Enter/scan the **Container ID** to select the container to close.
1. Confirm the system weight for the two items packed into the box. To update the weight manually, select the weight value and modify it before confirming.
1. On the Action Pane, select **Close container**.
1. In the **Close container** dialog box, select **Get system weight** to fill in the default **Gross weight** value.
1. Select **OK** to close the container.

> [!NOTE]
> The different field values getting displayed on the Warehouse Management mobile app pages can get sorted and highlighted by using the [Promoted fields](warehouse-app-promoted-fields.md) capability.

> [!TIP]
> Consider using the [Packing work for packing outbound containers and processing shipments](packing-work.md) as part of the process including adding different kind of [Data inquiry](warehouse-app-data-inquiry.md) menu items for this data.
