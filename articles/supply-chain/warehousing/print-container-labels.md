---
title: Print container labels
description: This article describes how to set up and print container labels.
author: perlynne
ms.author: perlynne
ms.reviewer: kamaybac
ms.search.form: WHSContainerLabelRouting, WHSLabelLayout, WHSLabelLayoutDataSource, SysCorpNetPrinterList, WHSDocumentRouting, WHSPackProfile, WHSContainerTable, WHSRFMenuItem
ms.topic: how-to
ms.date: 10/14/2022
ms.custom: bap-template
---

# Print container labels

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

Container labels provide information about a container and the related shipment data. A typical scenario that could include this type of label is when a worker is [creating and packing containers using the Warehouse Management mobile app](warehouse-app-packing-containers.md), where the worker could print a container label with a barcode of the container ID and apply it to the physical container.

As with [*license plate labels*](document-routing-layout-for-license-plates.md), *container labels* use the Zebra Programming Language (ZPL) to create label layouts.

## Turn on the container label printing functionality

*Container label* functionality is part of the *Pack containers using the Warehouse Management mobile app* feature (see also [Packing containers with the Warehouse Management mobile app](warehouse-app-packing-containers.md)). To use this functionality, it must be turned on in your system. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Warehouse management*
- **Feature name:** *Pack containers using the Warehouse Management mobile app*

## Example scenario: Print container labels while creating a container using the Warehouse Management mobile app

This example scenario shows how you can set up your system to print container labels when a worker creates a container using the Warehouse Management mobile app. This scenario builds on the information provided in [Packing containers with the Warehouse Management mobile app](warehouse-app-packing-containers.md), which provides more details about the full process of Packing containers with the Warehouse Management mobile app.

### Make sample data available

To work through this scenario using the sample records and values that are specified here, you must be on a system where the standard [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed. Additionally, you must select the *USMF* legal entity before you begin.

You can also use this scenario as guidance for using the feature on a production system. However, in that case, you must substitute your own values for each setting that is described here.

### Create a container label layout

The label layout controls what information is printed on the label and how it's laid out. Here, you enter the ZPL code that is sent to the printer (you would typically copy this code from a label designer program).

As the system generates a label, it can replace field and method names used in the label layout with actual values. You can easily see the text that will get replaced by looking for the `$` character in the code.

Follow these steps to create a container label layout:

1. Go to **Warehouse management \> Setup \> Document routing \> Label layout**.
1. At the top of the list pane, set **Label layout type** to *Container label*.
1. Select **New** on the Action Pane to create a new label.
1. Make the following settings for you new label:
    - **Label layout ID** – Enter *Container*.
    - **Description** – Enter *Container ID barcode*.
    - **Label layout data source ID** – Leave blank (only container data will be used).
    - **Enable label template support** – Leave set to *No* for now (when set you *Yes*, you'll be able to add header, row, and footer elements to your layout, as described later in this article).
    - **Date, time, and number format** – Leave blank (used to set formats of the *date*, *time*, and *number* values shown in a label layout, as described later in this article).
1. Expand the **Printer text Layout** FastTab and copy the following ZPL container label example and paste the text into the large field there:

    ``` plaintext
    CT~~CD,~CC^~CT~
    ^XA~TA000~JSN^LT0^MNW^MTT^PON^PMN^LH0,0^JMA^PR8,8~SD15^JUS^LRN^CI0^XZ
    ^XA
    ^MMT
    ^PW812
    ^LL0609
    ^LS0
    ^BY3,3,262^FT658,186^BAI,,Y,N
    ^FD$WHSContainerTable.ContainerId$^FS
    ^FT660,457^A0I,39,38^FH\^FDContainer ID^FS
    ^FT660,515^A0I,39,38^FH\^FDShipment: $WHSContainerTable.ShipmentId$^FS
    ^PQ1,0,1,Y^XZ
    ```

1. Close the page.

> [!NOTE]
> While customizing your label code on the **Printer text layout** FastTab, you can add valid field and method names by doing the following steps:
> 
> 1. Select the table in the **Tables** list.
> 1. Depending on which type of item you want to add, select either the **Fields** or **Methods** tab and then select the name of the field or method you want to add.
> 1. Select the **Insert at end of text** button to add your field or method at the end of the code.
> 1. If necessary, move the new field or method to the location within the code where you want to use it.
>
> In the label layout shown in this example, only the container ID (`$WHSContainerTable.ContainerId$`) barcode will be printed. If you want to include additional related information (such as the delivery name related to a shipment), do the following steps (unless the required layout label data source already exists):
>
> 1. Go to **Warehouse \> Setup \> Document routing \> Label layout data source** and create a label layout data source that includes a join to the `Shipment` table.
> 1. Select **New** on the Action Pane.
> 1. For the new record, specify a **Label layout data source ID**, **Description**, and **Label layout type**.
> 1. Select **Save** on the Action Pane.
> 1. Select **Edit query** in the Action Pane.
> 1. The standard query editor dialog opens.  Open the **Joins** tab and add a join to the needed table(s).
> 1. Go back to the **Label layout** page and select the new record in the **Label layout data source ID** page for a new or existing layout.
> 1. Now you can add the new field values to  your print layout code. Be sure to reference the correct *table.field-names* in your ZPL text. The additional tables will include a number (*_#*) as a suffix.
>
> When working on the **Label layout data source** page, be careful when removing a table from the query for an existing record because you might risk removing field and/or method names already used in existing label layouts.

#### Enable label template support

When making more advanced label layouts, you can benefit from using some of the widely available label generation tools described in [Document routing label layout](document-routing-layout-for-license-plates.md).

To format a label using header, row, and footer elements, go to the **Label layout** page, select or create a layout, and set **Enable label template support** to *Yes* for your new or selected layout. Then use the elements `{{Header ... }}`, `{{Row ... }}`, and `{{Footer ... }}` in your code. The following code shows an example of a label that includes each of these elements. It prints data about items packed in a container.

``` plaintext
{{Header
^FX ... ZPL commands which will get printed on every label ...
CT~~CD,~CC^~CT~
^XA
~TA000
~JSN
^LT0
^MNW
^MTT
^PON
^PMN
^LH0,0
^JMA
^PR6,6
~SD15
^JUS
^LRN
^CI27
^PA0,1,1,0
^XZ
^XA
^MMT
^PW1276
^LL900
^LS0
^FT80,150^A0N,58,58^FH\^CI28^FDShipment: $WHSContainerTable.ShipmentId$^FS^CI27
^FT80,250^A0N,33,33^FH\^CI28^FDItem^FS^CI27
^FT579,250^A0N,33,33^FH\^CI28^FDQuantity^FS^CI27
^FT720,250^A0N,33,33^FH\^CI28^FDUnit^FS^CI27
}}
^FX ... This section goes on the first label only...
^FT85,51^A0N,17,18^FH\^CI28^FDFIRST CONTAINER LABEL^FS^CI27
{{Row Table=WHSContainerLine_1 RowsPerLabel=10 StartY=300 IncY=50
^FX... ZPL commands to format the row using *$position.YPos$* to position the location of the text fields ...
^FT80,$position.YPos$^A0N,33,33^FH\^CI28^FD$WHSContainerLine_1.ItemId$^FS^CI27
^FT579,$position.YPos$^A0N,33,33^FH\^CI28^FD$WHSContainerLine_1.Qty$^FS^CI27
^FT720,$position.YPos$^A0N,33,33^FH\^CI28^FD$WHSContainerLine_1.UnitId$^FS^CI27
}}
^FX ... This part goes on the last label only ... 
^FT100,750^A0N,17,18^FH\^CI28^FDLast container label^FS^CI27
{{Footer
^FX ... Here goes the ZPL commands that closes every label ...
^FT600,750^A0N,58,58^FH\^CI28^FDLabel: $position.labelNumber$/$position.labelCount$^FS^CI27
^XZ
}}
```

> [!NOTE]
> This setup will loop over container lines and split out a label for each set of 10 container lines (because of the `RowsPerLabel=10` attribute). If you changed this to `RowsPerLabel=1`, you would generate a label for each line.
>  
> This setup will print one copy of each label. If you require more copies (for example, one copy for each side of the container), set the `n` value for the `\^PQn` section in the footer to the required number of copies. For example, to print two copies of each label, specify `\^PQ2`. <!--KFM: @per Let's add a `\^PQn` section in the sample code so we can see where it goes. -->

#### Specify the date, time, and number format

To set the formats of the *date*, *time*, and *number* values shown in a label layout, go to the **Label layout** page, select or create a layout, and set **Date, time, and number format** to the language whose formats you want to use.

### Set up container label routing

To define which container label layouts to use and where to print them, you must define a **Container label routing** record, as described in the following procedure.

1. Go to **Warehouse management \> Setup \> Document routing \> Container label routing**.
1. Select **New** on the Action Pane to create a new routing record.
1. Make the following settings in the header of you new routing record:
    - **Sequence number** – Enter an integer to establish the order in which this routing record should be evaluated. Each routing must have a unique sequence number. The system evaluates routings in ascending order according to their sequence number and will use the first one whose criteria are met. If you're using demo data, enter  *1*.
    - **Name** –  Enter a name for the routing record, for example *Container packing*.
1. Expand the **Overview** FastTab and use the settings here to establish the criteria by which the current label routing should be selected. The following fields are available:
    - **Warehouse** – Specify the warehouse where this routing should be used. If you're using demo data, enter *62*.
    - **Location** – Specify the location where this routing should be used. If you're using demo data, assume the target printer is physically placed at the packing location, so select *Pack*.
    - **Worker** – Specify the worker for whom this routing should be used. Leave this blank to use this routing for any worker.
    - **Mobile device user ID** – Specify the user ID for whom this routing should be used. Leave this blank to use this routing for any user.
    - **Container type** – Specify the container type for which this routing should be used.
    - **Account number** – Specify the customer account for whom this routing should be used. Leave this blank to use this routing for any customer.
    - **Carrier** –  Specify the shipping carrier for whom this routing should be used. Leave this blank to use this routing for any carrier.
    - **Run query** – To add custom selection criteria to a routing record, set **Run query** to *Yes* and then select **Edit query** on the Action Pane. This opens a standard query editor dialog where you can add more selection criteria.

    > [!NOTE]
    > When printing a container label from the Warehouse Management mobile app, the current user's warehouse, location, worker ID, and user ID are passed as possible filter values for selecting the printer and layout. Other values will be found based on the selected shipment.

1. Expand the **Container label routing printer** FastTab. Use the settings here to assign the printer and label layout to use when the criteria for this routing record are met. Select **New** on the toolbar to add a new line to the grid. Make the following settings for the new line.
    - **Name** – Select an appropriate ZPL printer. See also [Install the Document Routing Agent to enable network printing](../../fin-ops-core/dev-itpro/analytics/install-document-routing-agent.md).
    - **Label layout ID** – Select the label layout to use. The example label layout ID value suggested earlier in this scenario was *Container*.

### Set container labels to be printed automatically a new container is created

To set the system to print a container label automatically each time a new container is created, configure each packing profile as needed, as described in the following procedure.

1. Go to **Warehouse management \> Setup \> Packing \> Packing profiles**.
1. Select **Edit** on the Action Pane.
1. Select the profile for which you want to print container labels automatically. If you're working with sample data, select the row with **Packing profile ID** *WHS62*.
1. Select the **Print container label at container creation** checkbox for the selected row.
1. Close the page.

> [!NOTE]
> The **Container ID mode** for the **Packing profile ID** *WH62* is set to *Auto*, which means that the [number sequence](../../fin-ops-core/fin-ops/organization-administration/number-sequence-overview.md) defined for **Reference** *Container ID* will be used as part of the container creation process.

### Create a new mobile device menu item for printing container labels

To enable workers to print a container label manually, you must create a new mobile device menu item for the Warehouse Management mobile app.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**
1. Select **New** on the Action Pane to add a new mobile device menu item
1. Make the following settings for the new menu item:
    - **Menu item name** – Enter an internal name for the new menu item, for example *Print container label*.
    - **Title** – Enter the item name as it should be displayed in the Warehouse Management mobile app, for example *Print container label*.
    - **Mode** – Select *Indirect*.
    - **Activity code** – Select *Print container label*.
1. Close the page.

### Add the new mobile device menu item to the menu

Now that you've created the mobile device menu item you're ready to add it to the mobile device menu. In this example, you'll add it to the existing **Outbound** mobile device menu.

1. Open **Warehouse management \> Setup \> Mobile device \> Mobile device menu**.
1. Select **Edit** on the Action Pane.
1. Select the *Outbound* menu on the list pane.
1. In the **Available menus and menu items** column, select the new mobile device menu item that you created, for example *Print container label*.
1. Select the **Add** button (right-arrow) to move this menu item into the **Menu structure** column.
1. Close the page

### Run a scenario to print container labels

For an example of how to print bar codes manually, follow the instructions given in [Packing containers with the Warehouse Management mobile app](warehouse-app-packing-containers.md) and confirm that the scenario describe in this article is also supported.

Here are a few suggestions for how to customize and fine-tune this scenario to reduce the number of steps workers must perform when printing container labels.

- You can [query data using Warehouse Management mobile app detours](warehouse-app-data-inquiry.md) to look up a container ID instead of asking the worker to enter it manually.
- When a worker selects the **Print container label** mobile device menu item from the **Outbound** menu, the application automatically submits the current **User ID** and the **Warehouse** values. If the worker wants to specify a **Location**, they can choose to do so within the app.
- If you'd like the **Location** value to be assigned automatically when a worker selects **Print container label** from the **Pack inventory into containers** menu item, then you could set up a [detour]( warehouse-app-detours.md).

## Additional resources

- [Pack containers for shipment](packing-containers.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
