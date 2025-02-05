---
title: Custom label layouts and printing
description: Learn how to set up and print custom labels, including prerequisites and an outline on setting up your system to show print buttons for custom labels.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 07/23/2024
ms.custom: 
  - bap-template
ms.reviewer: kamaybac
ms.search.form: WHSLabelLayout, WHSLabelLayoutDataSource
---

# Custom label layouts and printing

[!include [banner](../includes/banner.md)]

This article describes how to create and use *custom labels*, which let users print labels for any type of data that you set up for them. For example, you can print product labels, location labels, customer labels, and more. When one or more custom label layouts are defined, the system automatically shows a **Print** button on the relevant pages.

## Prerequisites

To use custom label layouts, you must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.33 or later. You don't have to use Feature management to enable the feature.

## Set up your system to show a Print button for custom labels

Follow these steps to set up your system to automatically show a **Print** button on pages that handle data that a custom label is available for.

1. Go to **Warehouse management \> Setup \> Warehouse management parameters**.
1. On the **Reports** tab, on the **Custom labels** FastTab, set the **Display custom label print buttons** option to *On all forms*.

## Set up the data source for a custom label

Follow these steps to define the data source that's used for a custom label and then select it in your label layout.

1. Go to **Warehouse management \> Setup \> Document routing \> Label layout data source**.
1. Follow one of these steps:

    - To create a new record, select **New** on the Action Pane to add a row to the grid.
    - To edit an existing record, select **Edit** on the Action Pane, and then select the row for the label that you want to edit.
    - To remove a record, select it in the grid, and then select **Delete** on the Action Pane.

1. If you're creating or editing a record, set the following fields for the new or selected label:

    - **Label layout data source ID** – Enter a name for the data source (for example, *Locations*).
    - **Description** – Enter a short description of the data source (for example, *Locations*).
    - **Label layout type** – Select *Custom label*.
    - **Custom label root table** – Select the table that should be used as the main data source for the label (for example, *WMSLocation* to print labels for locations, *InventTable* to print labels for products, or *CustTable* to print labels for customers).
    - **Join type** – Select the type of joins used when adding related tables. Selecting *Inner join* will only retrieve data if data exists in both joined tables, while selecting *Outer join* will retrieve data from the root table even if there is no data in the related table.

    > [!NOTE]
    > Forms that don't have a data source or use a temporary table as a data source can't use the custom labels (for example, the *Registration* form on the purchase orders uses *TmpInventTransWMS* as a data source, so custom labels can't be printed for that table). Instead, a *Regular* table must be used.

1. On the Action Pane, select **Save**.

1. If you want the custom label to include information from related tables, follow these steps to set up the required joins:

    1. On the Action Pane, select **Edit query**.
    1. A standard query editor dialog box appears. On the **Joins** tab, add the required joins to the required tables.
    1. Select **OK** to apply your settings and close the dialog box.

1. If you want to use parameters specified at printing time, follow these steps to set up the parameters:

    1. On the Action Pane, select **Parameters**.
    1. The **Label layout data source parameters** page opens. Use the Action Pane buttons to add or delete rows as needed. For each parameter, specify the following fields:

        - **Name** – Enter the name of the parameter. This name is used in the label layout to refer to the parameter (for example, *label_quantity*). It can only include letters A-Z (upper and lower case), numbers, and the underscore (_) character.
        - **Data types** – Specify the type of data the parameter can hold. Currently, only *String* is supported, which means that no special number or date formatting will be available in label layouts when replacing the placeholder with the value. Using the *String* value should not pose any issues with whole numbers, such as quantity of labels printed.
        - **Display name** – Enter the name that will be shown to the user on the custom label printing dialog (for example, *Quantity of labels*).
        - **Mandatory** – Specify whether a value must be given for the parameter on the custom label printing dialog.
        - **Default value** – Enter the value that will be initially presented to the user on the custom label printing dialog (for example, *1*).

    1. Close the page.

## Create and manage custom label layouts

Follow these steps to create a custom label layout that uses data from a label layout data source that you've set up.

1. Go to **Warehouse management \> Setup \> Document routing \> Label layout**.
1. At the top of the list pane, set the **Label layout type** field to *Custom Label*.
1. Follow one of these steps:

    - To create a new record, select **New** on the Action Pane.
    - To edit an existing record, select **Edit** on the Action Pane, and then, in the list pane, select the record that you want to edit.
    - To remove a record, select it in the list pane, and then select **Delete** on the Action Pane.

1. If you're creating or editing a record, set the following fields on the header:

    - **Label layout ID** – Enter a name for the layout (for example, *Locations*).
    - **Description** – Enter a short description of the layout (for example, *Locations*).
    - **Label layout data source ID** – Select the data source for the custom label (for example, *Locations*).
    - **Enable label template support** – Set this option to *No* if you're creating a simple label layout. Set it to *Yes* to create more advanced layouts that include `{{Header ... }}`, `{{Row ... }}`, and `{{Footer ... }}` elements. For more information about how to use these elements, see [Enable label template support](print-license-plate-labels-using-label-layouts.md#label-template).
    - **Date, time, and number format** – Select the language to use when date, time, and number values that are shown in the label layout are formatted.

1. On the **Printer text Layout** FastTab, enter your label content code. Here's an example of code for printing a location label. You can copy and paste it for testing.

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
    ^PQ$dsparams.label_quantity$^XZ
    ```

    > [!NOTE]
    > Use `dsparams.parameter-name` to refer to label layout data source parameters.
    >
    > In the above example, when the print dialog is opened, the user will be able to enter the number of labels to be printed in the *Quantity of labels* field.

1. On the Action Pane, select **Save**.

## Print a custom label

Follow these steps to print a custom label.

1. In Supply Chain Management, open the page that's associated with the data source that's used for your custom label. Here are some examples:

    - To print a location label (which uses the *WMSLocation* table), go to **Warehouse management \> Setup \> Warehouse \> Locations**.
    - To print a product label (which uses the *InventTable* table), go to **Product information management \> Products \> Released products**.
    - To print a customer label (which uses the *CustTable* table), go to **Sales and marketing \> Customers \> All customers**.

1. Select one or more records that you want to print a label for.
1. On the Action pane, on the **Options** tab, in the **Custom labels** group, select the print option for the type of label that you're printing (for example, **Print locations**).
1. In the **Print custom labels** dialog box, set the following fields:

    - **Label layout ID** – Select the layout that you want to use (for example, *Locations*).
    - **Printer name** – Select the printer that you want to print from.
    - **Label layout data source parameters** - Specify any parameters defined on the label layout data source (for example, *Quantity of labels*).

1. Select **OK**.

## Related information

- [Document routing label layouts](document-routing-layout-for-license-plates.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
