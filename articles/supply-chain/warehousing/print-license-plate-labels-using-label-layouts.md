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

- **Document routing label layouts** – These layouts provide basic layout capabilities.
- **Label layouts** – These layouts let you build more advanced layouts. Your layouts can have repeating structures and include header, body, and footer elements. You can print information from the related tables and define custom date, time, and number formats.

This article describes how to create and use *label layouts* for license plate labels. For more information about *document routing label layouts*, see [Document routing label layouts](document-routing-layout-for-license-plates.md).

## Enable license plate label layouts

To enable license plate label layouts, you must set up the following elements (as described later in this article):

- **[Warehouse management parameters](#parameters)** – Define whether to use document routing label layouts or label layouts.
- **[License plate label layout](#lp-label-layout)** – Define the label layout to use for the license plate labels.
- **[License plate label routing](#routing)** – Define which Zebra Programming Language (ZPL) layouts should be printed to which network printer and under which conditions.

## <a name="parameters"></a>Set up warehouse management parameters

Follow these steps to set up warehouse parameters for license plate label printing.

1. Go to **Warehouse management \> Setup \> Warehouse management parameters**.
1. On the **General** tab, on the **License plates** FastTab, set the **Use label layouts for license plate labels** option to *Yes* to use label layouts for your license plates (as described in this article). Set it to *No* to use [document routing label layouts](document-routing-layout-for-license-plates.md) instead.

## <a name="lp-label-layout"></a>Create a license plate label layout

The label layout controls what information is printed on the label and how it's laid out. Here, you enter the ZPL code that's sent to the printer. Typically, you'll copy this code from a label designer program.

As the system generates a label, it can replace field and method names that are used in the label layout with actual values. You can easily find text that will be replaced by looking for dollar signs (`$`) in the code.

### Create a basic label layout

Follow these steps to create a license plate label layout.

1. Go to **Warehouse management \> Setup \> Document routing \> Label layout**.
1. At the top of the list pane, set the **Label layout type** field to *License Plate Label*.
1. On the Action Pane, select **New** to create a label.
1. Set the following fields for the new label:

    - **Label layout ID** – Enter a name for the layout (for example, *License plate*).
    - **Description** – Enter a short description of the layout (for example, *License plate*).
    - **Label layout data source ID** – Leave this field blank if you'll use only license plate data. If you must include data from other tables, select a label layout data source that has the required joins. For more information about how to set up and use a label layout data source, see the next section in this article.
    - **Enable label template support** – Leave this option set to *No* for now. (When it's set to *Yes*, you can add header, row, and footer elements to your layout, as described later in this article.)
    - **Date, time, and number format** – Select the language to use when date, time, and number values that are shown in the label layout are formatted.

1. On the **Printer text Layout** FastTab, enter your label code. Here's an example of code that you can copy and paste for testing.

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
    > 1. If the **Tables** list is shown, select the table. (The **Tables** list is shown only when a value is selected in the **Label layout data source ID** field.)
    > 1. Depending on the type of item that you want to add, select either the **Fields** tab or the **Methods** tab, and then select the name of the field or method to add.
    > 1. Select **Insert at end of text** to add the field or method to the end of the code.
    > 1. As you require, move the new field or method to the place in the code where you want to use it.

1. On the Action Pane, select **Save**.

### Set up and use a label layout data source

In the label layout in the preceding example, only the license plate ID (`$LicensePlateId$`) is used, and this value is available directly in the license plate table. If you want to include related information (such as that order number that's related to a license plate), and the required layout label data source doesn't already exist, follow these steps to create it and then select it in your label layout.

1. Go to **Warehouse management \> Setup \> Document routing \> Label layout data source**.
1. On the Action Pane, select **New**.
1. Set the following fields for the new label layout data source:

    - **Label layout data source ID** – Enter a name for the data source (for example, *LPPlusPurchOrder*).
    - **Description** – Enter a short description of the data source (for example, *License plate + Purchase order*).
    - **Label layout type** – Select *License plate label*.

1. On the Action Pane, select **Save**.
1. On the Action Pane, select **Edit query**.
1. A standard query editor dialog box appears. On the **Joins** tab, add joins to the required tables. (For example, if you want your label to show the order number, you might make a join to the purchase order table.)
1. Go to **Warehouse management \> Setup \> Document routing \> Label layout**.
1. Create or select a label layout, and then, in the **Label layout data source ID** field, select the record that you just created.
1. You can now add the new field values to the print layout code. Be sure to reference the correct *table.field-names* values in the ZPL code. The additional tables will include a number as a suffix (*\_\#*).

> [!CAUTION]
> On the **Label layout data source** page, be careful about removing a table from the query for an existing record. You might remove field and/or method names that are already used in existing label layouts.

### <a name="label-template"></a>Enable label template support

Label templates let you design labels that have more advanced layouts, which can include header, row, and footer elements. Follow these steps to format a label that includes label template elements.

1. Go to **Warehouse management \> Setup \> Document routing \> Label layout**.
1. At the top of the list pane, set the **Label layout type** field to *License Plate Label*.
1. Follow one of these steps:

    - To create a new layout, select **New** on the Action Pane.
    - To edit an existing layout, select the layout on the list pane, and then select **Edit** on the Action Pane.

1. In the **Label layout data source ID** field, select a data source. (A data source is required to enable label template support. However, if you need only license plate data, you can select a very simple data source where no joins are defined.)
1. Set the **Enable label template support** option to *Yes*.
1. Use the `{{Header ... }}`, `{{Row ... }}`, and `{{Footer ... }}` elements in your code. The following example shows a label that includes all these elements. It prints data about items that are put in a license plate.

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
1. At the top of the list pane, set the **Work order type** field to *Purchase orders*.
1. On the Action Pane, select **New** to create a routing record.
1. On the header of the new routing record, set the following fields:

    - **Sequence number** – Enter an integer to define the order that the routing record should be evaluated in. Each routing must have a unique sequence number. The system evaluates routings in order of ascending sequence numbers and uses the first routing that criteria are met for.
    - **Name** – Enter a name for the routing record. For example, enter *License plate*.

1. On the **Overview** FastTab, use the following fields to define the criteria that are used to select the label routing:

    - **Warehouse** – Specify the warehouse where the routing should be used.
    - **Mobile device user ID** – Specify the user ID that the routing should be used for. To use the routing for any worker, leave this field blank.
    - **Account number** – Specify the vendor account that the routing should be used for. To use the routing for any vendor, leave this field blank.
    - **Carrier** – Specify the carrier that the routing should be used for. To use the routing for any carrier, leave this field blank.
    - **Work template** – Specify the work template that the routing should be used for. To use the routing for any work template, leave this field blank.
    - **From zone ID** and **To zone ID** - Specify the range of zones that the routing should be used for. To use the routing for any zone, leave these fields blank.
    - **Run query** – To add custom selection criteria to a routing record, set this option to *Yes*, and then select **Edit query** on the Action Pane. A standard query editor dialog box appears, where you can add more selection criteria.

1. On the **Document routing printers** FastTab, assign the printer and label layout that should be used when the criteria for the routing record are met. Select **New** on the toolbar to add a line to the grid. Then set the following fields for the new line:

    - **Name** – Select an appropriate ZPL printer. For more information, see [Install the Document Routing Agent to enable network printing](../../fin-ops-core/dev-itpro/analytics/install-document-routing-agent.md).
    > [!NOTE]
    > Leave this field blank if you want to use [dynamic printing selection](dynamic-printing-selection.md).
    - **Label layout ID** – Select the label layout to use. The example label layout ID value that was suggested earlier in this article was *License plate*.

## Automatically print labels when purchase orders are received by using the mobile app

If you want a license plate label to be printed automatically each time that a new purchase order is received, configure mobile device menu items as described in the following procedure.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. Follow one of these steps:

    - To create a new menu item, select **New** on the Action Pane.
    - To edit an existing menu item, select it in the list pane, and then select **Edit** on the Action Pane.

1. Set the following fields for the new or selected menu item:

    - **Menu item name** – Enter an internal name for the new menu item. For example, enter *Mixed*.
    - **Title** – Enter the item name as it should appear in the Warehouse Management mobile app. For example, enter *Mixed LP Receiving*.
    - **Mode** – Select *Work*.
    - **Work creation process** – Select *Mixed license plate receiving*.
    - **Print label** – Set this option to *Yes*.

1. Close the page.

If you created a new mobile device menu item, you must add it to the mobile device menu, as shown in the following example. In this example, you'll add it to the existing **Inbound** mobile device menu.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu**.
1. On the Action Pane, select **Edit**.
1. In the list pane, select the **Inbound** menu.
1. In the **Available menus and menu items** column, select the mobile device menu item that you created (for example, *Mixed*).
1. Select the **Add** button (right arrow) to move the menu item into the **Menu structure** column.
1. Close the page.

## Run a scenario to print license plate labels

If you want to experiment with printing license plate labels, you can set up a scenario for doing mixed license plate receiving through the Warehouse Management mobile app. For more information, see [Mixed license plate receiving](mixed-license-plate-receiving.md). Follow the instructions there, and confirm that the scenario that's described in this article is supported.

## Additional resources

- [Document routing label layouts](document-routing-layout-for-license-plates.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
