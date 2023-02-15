---
title: Custom label layouts and printing
description: This article describes how to set up and print custom labels using label layouts.
author: GalynaFedorova
ms.author: gfedorova
ms.reviewer: kamaybac
ms.search.form: WHSLabelLayout, WHSLabelLayoutDataSource
ms.topic: how-to
ms.date: 02/12/2023
ms.custom: bap-template
---

# Custom label layouts and printing

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]
<!-- KFM: Preview until 10.0.33 GA -->

This article describes how to create and use *custom labels*, which let users print labels for any type of data that you set up for them, including (but not limited to) product labels, location labels, customer labels, and more, depending on your business requirements. When you have one or more custom label layouts defined, the system will automatically show a **Print** button on the relevant pages.

## Prerequisites

To use custom label layouts, you must be running Supply Chain Management 10.0.33 or newer. No feature management is necessary to enable the feature.

## Set your system to display print buttons for custom labels

Follow these steps to set your system to automatically show a **Print** button on pages dealing with data for which a custom label is available.

1. Go to **Warehouse management \> Setup \> Warehouse management parameters**.
1. Open the **Reports** tab.
1. On the **Custom labels** FastTab, set the **Display custom label print buttons** option to *On all forms*.

## Set up the data source for a custom label

Follow these steps to define the data source to use for a custom label and then select it in your label layout.

1. Go to **Warehouse management \> Setup \> Document routing \> Label layout data source**.
1. Do one of the following steps:
    - To create a new record, select **New** on the Action Pane to add a new row to the grid.
    - To edit an existing record, select **Edit** on the Action Pane and then select the row for the label you want to edit.
    - To remove a record, select it in the grid and then select **Delete** on the Action Pane.
1. Make the following settings for your new or selected label:
    - **Label layout data source ID** – Enter a name for the data source (for example, *Locations*).
    - **Description** – Enter a short description of the data source (for example, *Locations*).
    - **Label layout type** – Select *Custom label*.
    - **Custom label root table** – Select the table that will be used as the main data source for the label (for example, *WMSLocation* to print labels for locations, *InventTable* for products, or *CustTable* for customers).
1. If you'd like your custom label to include information from related tables, then set up the required joins. To set up a join, follow these steps:
    1. On  the Action Pane, select **Edit query**.
    1. A standard query editor dialog box appears. Open the **Joins** tab and add the required joins to the required tables.
    1. Select **OK** to apply your settings and close the dialog.
1. On the Action Pane, select **Save**.

## Create and manage custom label layouts

Follow these steps to create a custom label layout that uses data from a label layout data source that you have set up.

1. Go to **Warehouse management \> Setup \> Document routing \> Label layout**.
1. At the top of the list pane, set the **Label layout type** field to *Custom Label*.
1. Do one of the following steps:
    - To create a new record, select **New** on the Action Pane.
    - To edit an existing record, select **Edit** on the Action Pane and then select the record you want to edit on the list pane.
    - To remove a record, select it on the list pane and then select **Delete** on the Action Pane.
1. In the header of your new or selected record, make the following settings:
    - **Label layout ID** – Enter a name for the layout (for example, *Locations*).
    - **Description** – Enter a short description of the layout (for example, *Locations*).
    - **Label layout data source ID** – Select the data source for the custom label (for example, *Locations*).
    - **Enable label template support** – Set to *No* if you're creating a simple label layout. Set to *Yes* to create more advanced layouts that include `{{Header ... }}`, `{{Row ... }}`, and `{{Footer ... }}` elements; for more information about how to use these elements, see [Enable label template support](print-license-plate-labels-using-label-layouts.md#label-template).
    - **Date, time, and number format** – Select the language to use when date, time, and number values that are shown in the label layout are formatted.

1. On the **Printer text Layout** FastTab, enter your label content code. Here's an example of code for printing a location label, which you could copy and paste for testing:

    ``` ZPL
    CT~~CD,~CC^~CT~
    ^XA~TA000~JSN^LT0^MNM,0^MTT^PON^PMN^LH0,0^JMA^PR8,8~SD15^JUS^LRN^CI27^PA0,1,1,0^XZ
    ^XA
    ^MMT
    ^PW831
    ^LL609
    ^LS0
    ^FT40,59^A0N,28,28^FH\^CI28^FDLocation^FS^CI27
    ^FT19,148^A0N,42,43^FH\^CI28^FDLocationID: ^FS^CI27
    ^FT230,148^A0N,42,43^FH\^CI28^FD$WMSLocation_1.wMSLocationId$ ^FS^CI27
    ^BY3,3,180^FT116,525^BCN,,Y,N
    ^FH\^FD^FS
    ^PQ1,0,1,Y^XZ
    ```

1. On the Action Pane, select **Save**.

## Print a custom label

Follow these steps to print a custom label.

1. In Supply Chain Management, open the page associated with the data source used on your custom label. For example:
    - To print a location label (which uses the *WMSLocation* table), go to **Warehouse management \> Setup \> Warehouse \> Locations**.
    - To print a product label (which uses the *InventTable* table), go to **Product information management \> Products \> Released products**.
    - To print a customer label (which uses the *CustTable* table), go to **Sales and marketing \> Customers \> All customers**.
1. Select one or more records you want to print a label for.
1. On the Action pane, open the **Options** tab. Then, in the **Custom labels** group, select the print option for the type of label you are printing (for example, **Print locations**).
1. The **Print custom labels** dialog opens. Make the following settings:
    - **Label layout ID** – Select the layout you want to use (for example, *Locations*).
    - **Printer name** – Select the printer that you want to print from.
1. Select **OK**.

## Additional resources

- [Document routing label layouts](document-routing-layout-for-license-plates.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
