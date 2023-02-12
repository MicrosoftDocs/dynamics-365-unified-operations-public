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

This feature introduces a new Custom label layout type that allows you to build layouts for any data sources. New Print button will be displayed automatically when layout exists for corresponding source. Users can print labels for any data including but not limited to Product labels, Location labels, Customer labels. 

This article describes how to create and use *Custom labels* for locations, but it can be used for any other data source depends on the business requirements. 

## Set up warehouse management parameters

Follow these steps to set up warehouse parameters for custom label printing.

1. Go to **Warehouse management \> Setup \> Warehouse management parameters**.
1. On the **Reports** tab, on the **Custom labels** FastTab, set the **Display custom label print buttons** option to *On all forms*.

## Set up and use a custom label layout data source

Follow these steps to define the data source that will be used for the label and then select it in your label layout.

1. Go to **Warehouse management \> Setup \> Document routing \> Label layout data source**.
1. On the Action Pane, select **New**.
1. Set the following fields for the new label layout data source:

    - **Label layout data source ID** – Enter a name for the data source (for example, *Locations*).
    - **Description** – Enter a short description of the data source (for example, *Locations*).
    - **Label layout type** – Select *Custom label*.
    - **Custom label root table** – Select the table that will be used as main data source (for example, *WMSLocation* to print labels for locations, *InventTable* - for products, *CustTable* - for customers). 

## Create a custom label layout

Follow these steps to create a label layout for the locations.

1. Go to **Warehouse management \> Setup \> Document routing \> Label layout**.
1. At the top of the list pane, set the **Label layout type** field to *Custom Label*.
1. On the Action Pane, select **New** to create a label.
1. Set the following fields for the new label:

    - **Label layout ID** – Enter a name for the layout (for example, *Locations*).
    - **Description** – Enter a short description of the layout (for example, *Locations*).
    - **Label layout data source ID** – Select the data source for the custom label (for example, *Locations*). 
    - **Enable label template support** – Leave this option set to *No* for now. 
    - **Date, time, and number format** – Select the language to use when date, time, and number values that are shown in the label layout are formatted.

1. On the **Printer text Layout** FastTab, paste the following example of a ZPL location label (or enter your own code).

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

## Print custom label

Follow these steps to print the label from the data source defined on the layout.

1. Go to **Warehouse management \> Setup \> Warehouse \> Locations**.
1. On the Action pane, select **Options**.
1. Select **Print Locations** in the **Custom labels** section.
1. Set the following fields to print the label:

    - **Label layout ID** – Select a name for the layout (for example, *Locations*).
    - **Printer name** – Select the printer that will be used for label printing .
1. Seelct **OK**.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
