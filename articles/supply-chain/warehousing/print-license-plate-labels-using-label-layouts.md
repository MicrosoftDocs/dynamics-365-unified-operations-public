---
title: License plate label layouts and printing
description: This article describes how to set up and print license plate labels using label layouts.
author: GalynaFedorova
ms.author: gfedorova
ms.reviewer: kamaybac
ms.search.form: WHSLabelLayout, WHSLabelLayoutDataSource, WHSDocumentRouting
ms.topic: how-to
ms.date: 01/17/2022
ms.custom: bap-template
---

# License plate label layouts and printing

[!include [banner](../includes/banner.md)]

Labels layouts are used to control what information is printed on a label and how it's laid out. There are two ways to define a license plate label layout:

- **Document routing label layout** – Provide basic layout capabilities. For details, see [Document routing label layouts](document-routing-layout-for-license-plates.md) and [Enable license plate label printing](tasks/license-plate-label-printing.md).
- **Label layouts** – Let you build more advanced layouts. Your layouts can have repeating structures and include header, body, and footer elements. You can print information from the related tables and define custom date, time, and number formats.

This article describes how to create and use label layouts for license plate labels.

## Enable license plate label layout

To enable license plate label layout, you must set up each of the following (as described later in this article):

- **[Warehouse management parameters](#parameters)** – Define whether to use document routing label layouts or label layouts.
- **[License plate label layout](#lp-label-layout)** – Define label layout to be used for the license plate labels.
- **[License plate label routing](#routing)** – Define which ZPL layouts should be printed to which network printer and under which conditions.

## <a name="parameters"></a>Set up warehouse management parameters

To set up warehouse parameters for license plate label printing, follow these steps:

1. Go to **Warehouse management \> Setup \> Warehouse management parameters**.
1. On the **License plates** FastTab, make the following setting:
    - **Use label layouts for license plate labels** – Choose whether the system should use label layouts instead of document routing label layouts.  Set this option to *Yes* to use label layout feature for license plate labels.

## <a name="lp-label-layout"></a>Create a license plate label layout

The label layout controls what information is printed on the label and how it's laid out. Here, you enter the ZPL code that is sent to the printer. Typically, you'll copy this code from a label designer program.

As the system generates a label, it can replace field and method names that are used in the label layout with actual values. You can easily find text that will be replaced by looking for dollar signs (`$`) in the code.

### Create a basic label layout

Follow these steps to create a license plate label layout.

1. Go to **Warehouse management \> Setup \> Document routing \> Label layout**.
1. At the top of the list pane, set the **Label layout type** field to *License Plate Label*.
1. On the Action Pane, select **New** to create a label.
1. Set the following values for the new label:
    - **Label layout ID** – Enter a name for the layout (for example, *License plate*).
    - **Description** – Enter a short description of the layout (for example, *License plate*).
    - **Label layout data source ID** – Leave this field blank if you'll only license plate data. If you need to include data from other tables, then select a label layout data source with the required joins. For more information about how to set up and use a label layout data source, see the next section in this article.
    - **Enable label template support** – Leave this option set to *No* for now. (When it's set to *Yes*, you can add header, row, and footer elements to your layout, as described later in this article.)
    - **Date, time, and number format** – Select the language to use when formatting date, time, and number values that are shown in a label layout.
1. On the **Printer text Layout** FastTab, copy and paste the following example of a ZPL license plate label (or enter your own code).

    ``` ZPL
    CT~~CD,~CC^~CT~
    ^XA~TA000~JSN^LT0^MNM,0^MTT^PON^PMN^LH0,0^JMA^PR8,8~SD15^JUS^LRN^CI27^PA0,1,1,0^XZ
    ^XA
    ^MMT
    ^PW831
    ^LL609
    ^LS0
    ^FT19,59^A0N,28,28^FH\^CI28^FDLicense plate label^FS^CI27
    ^FT19,148^A0N,42,43^FH\^CI28^FDItem: ^FS^CI27
    ^FT128,148^A0N,42,43^FH\^CI28^FD$ItemId$ ^FS^CI27
    ^BY3,3,180^FT116,525^BCN,,Y,N
    ^FH\^FD$LicensePlateId$^FS
    ^FT19,206^A0N,42,43^FH\^CI28^FDQty:^FS^CI27
    ^FT128,206^A0N,42,43^FH\^CI28^FD$Qty$^FS^CI27
    ^PQ1,0,1,Y^XZ
    ```

    > [!NOTE]
    > While you're customizing the label code on the **Printer text layout** FastTab, you can add valid field and method names by following these steps:
    >
    > 1. In the **Tables** list (if shown), select the table. (The **Tables** list is only shown when a **Label layout data source ID** is selected.)
    > 1. Depending on the type of item that you want to add, select either the **Fields** tab or the **Methods** tab, and then select the name of the field or method to add.
    > 1. Select **Insert at end of text** to add the field or method to the end of the code.
    > 1. As you require, move the new field or method to the place in the code where you want to use it.

1. Select **Save** on the Action Pane.

### Set up and use a label layout data source

In the label layout shown in the preceding example, only the license plate ID (`$LicensePlateId$`) bar code will be printed. If you want to include related information (such as order number that is related to a license plate), and the required layout label data source doesn't already exist, follow these steps to create it:

1. Go to **Warehouse management \> Setup \> Document routing \> Label layout data source**.
1. On the Action Pane, select **New**.
1. Set the following values for the new label layout data source:
    - **Label layout data source ID** – Enter a name for the data source (for example, *LPPlusPurchOrder*).
    - **Description** – Enter a short description for the data source (for example, *License plate + Purchase order*).
    - **Label layout type** – Select *License plate label*.
1. On the Action Pane, select **Save**.
1. On the Action Pane, select **Edit query**.
1. A standard query editor dialog box appears. On the **Joins** tab, add joins to the required tables. (For example, you might make a join to the purchase order table if you want your label to show the order number.)
1. Go to **Warehouse management \> Setup \> Document routing \> Label layout**.
1. Create or select a label layout, and then, in the **Label layout data source ID** field, select the record that you just created.
1. You can now add the new field values to the print layout code. Be sure to reference the correct *table.field-names* values in the ZPL code. The additional tables will include a number (*\_\#*) as a suffix.

> [!CAUTION]
> On the **Label layout data source** page, be careful about removing a table from the query for an existing record. You might remove field and/or method names that are already used in existing label layouts.

### Enable label template support

If you want to create more advanced label layouts, you can benefit from using some of the widely available label generation tools that are described in [Document routing label layouts](document-routing-layout-for-license-plates.md).

To format a label by using header, row, and footer elements, follow these steps:

1. Go to **Warehouse management \> Setup \> Document routing \> Label layout**.
1. At the top of the list pane, set the **Label layout type** field to *License Plate Label*.
1. Do one of the following steps:
    - To create a new layout, select **New** on the Action Pane.
    - To edit an existing layout, select the layout on the list pane and then select **Edit** on the Action Pane.
1. Select a **Label layout data source ID**. (A data source is required in order to enable label template support, but you could select a very simple one with no joins defined if you only need license plate data.)
1. Set **Enable label template support** to *Yes*.
1. Use the `{{Header ... }}`, `{{Row ... }}`, and `{{Footer ... }}` elements in your code. The following example shows a label that includes all these elements. It prints data about items that are placed in a license plate.

    ``` ZPL
    {{LabelStart
    ^FX ... ZPL commands that will be printed on every label ...
    CT~~CD,~CC^~CT~
    ^XA
    ~TA000
    ~JSN
    ^LT0
    ^MNM,0
    ^MTT
    ^PON
    ^PMN
    ^LH0,0
    ^JMA
    ^PR8,8
    ~SD15
    ^JUS
    ^LRN
    ^CI27
    ^PA0,1,1,0
    ^XZ
    ^XA
    ^MMT
    ^PW831
    ^LL609
    ^LS0
    }}
    {{Header
    ^FT31,59^A0N,28,28^FH\^CI28^FDLicense plate label with work lines^FS^CI27
    ^BY3,3,180^FT116,300^BCN,,Y,N
    ^FH\^FD$WHSLicensePlateLabel.LicensePlateId$^FS
    }}
    {{Row Table=WHsWorkLine_1 StartY=400 IncY=68 RowsPerLabel=5
    ^FT19,$position.YPos$^A0N,42,43^FH\^CI28^FDLine:^FS^CI27
    ^FT128,$position.YPos$^A0N,42,43^FH\^CI28^FD$WHSWorkLine_1.ItemID$^FS^CI27
    ^FT250,$position.YPos$^A0N,42,43^FH\^CI28^FD$WHSWorkLine_1.QtyWork$^FS^CI27
    }}
    {{LabelEnd
    ^PQ1,0,1,Y
    ^XZ
    }}
    ```

> [!NOTE]
> Because of the `RowsPerLabel=5` attribute, this example will loop over license plate lines and split out a label for each set of five license plate lines. If you change the attribute to `RowsPerLabel=1`, a label will be generated for each line.
>
> This example will print one copy of each label. If you require more copies (for example, one copy for each side of the license plate), set the `n` value for the `\^PQn` section in the footer to the required number of copies. For example, to print two copies of each label, specify `\^PQ2`.

## <a name="routing"></a>Set up license plate label routing

To specify the license plate label layouts that are used and where they're printed, you must define a document routing record, as described in the following procedure.

1. Go to **Warehouse management \> Setup \> Document routing \> Document routing**.
1. In the **Work order type** field at the top of the list pane, select *Purchase orders* option.
1. On the Action Pane, select **New** to create a routing record.
1. On the header of the new routing record, set the following fields:

    - **Sequence number** – Enter an integer to define the order that the routing record should be evaluated in. Each routing must have a unique sequence number. The system evaluates routings in order of ascending sequence numbers and uses the first routing that criteria are met for.
    - **Name** – Enter a name for the routing record. For example, enter *License plate*.

1. On the **Overview** FastTab, use the following fields to define the criteria that are used to select the label routing:

    - **Warehouse** – Specify the warehouse where the routing should be used.
    - **Mobile device user ID** – Specify the user ID that the routing should be used for. To use the routing for any worker, leave this blank.
    - **Account number** – Specify the vendor account that the routing should be used for. To use the routing for any vendor, leave this blank.
    - **Carrier** – Specify the carrier that the routing should be used for. To use the routing for any carrier, leave this blank.
    - **Work template** – Specify the work template that the routing should be used for. To use the routing for any work templates, leave this blank.
    - **From zone, To zone** - Specify the zone range from that the routing should be used for. To use the routing for any zone, leave this blank
    - **Run query** – To add custom selection criteria to a routing record, set this option to *Yes*, and then select **Edit query** on the Action Pane. A standard query editor dialog box appears, where you can add more selection criteria.

1. On the **Document routing printers** FastTab, assign the printer and label layout that should be used when the criteria for the routing record are met. Select **New** on the toolbar to add a line to the grid. Then set the following fields for the new line:
    - **Name** – Select an appropriate ZPL printer. For more information, see [Install the Document Routing Agent to enable network printing](../../fin-ops-core/dev-itpro/analytics/install-document-routing-agent.md).
    - **Label layout ID** – Select the label layout to use. The example label layout ID value that was suggested earlier in this article was *License plate*.

## Print labels automatically when purchase orders are received using the mobile app

If you want a license plate label to be printed automatically each time a new purchase order is received, configure mobile device menu items as described in the following procedure.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. Do one of the following steps:
    - To create a new menu item, select **New** on the Action Pane.
    - To edit an existing menu item, select it on the list pane and then select **Edit** on the Action Pane.
1. Set the following values for the new or selected menu item:
    - **Menu item name** – Enter an internal name for the new menu item. For example, enter *Mixed*.
    - **Title** – Enter the item name as it should appear in the Warehouse Management mobile app. For example, enter *Mixed LP Receiving*.
    - **Mode** – Select *Work*.
    - **Work creation process:** – Select *Mixed license plate receiving*.
    - **Print label** –  Set this option to *Yes*.
1. Close the page.

If you created a new mobile device menu item, then you must add it to the mobile device menu, as shown in the following example. In this example, you'll add it to the existing **Inbound** mobile device menu.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu**.
1. On the Action Pane, select **Edit**.
1. In the list pane, select the **Inbound** menu.
1. In the **Available menus and menu items** column, select the mobile device menu item that you created (for example, *Mixed*).
1. Select the **Add** button (right arrow) to move the menu item into the **Menu structure** column.
1. Close the page.

## Run a scenario to print license plate labels

If you'd like to experiment with printing license plate labels, you could set up a scenario for doing mixed license plate receiving with the Warehouse Management mobile app. For details, see [Mixed license plate receiving](mixed-license-plate-receiving.md). Follow the instructions there, and confirm that the scenario that is described in this article is supported.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
