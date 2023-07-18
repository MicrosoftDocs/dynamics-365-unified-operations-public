---
title: Dynamic printer selection
description: This article explains how to set up your system to dynamically select a printer when printing license plate labels and container labels
author: adesypri
ms.author: adesypri
ms.reviewer: kamaybac
ms.search.form: WHSLicensePlateLabel, WHSWorkUserdefaultLabelPrinterTable, WHSLocationDefaultLabelPrinter, WHSLabelLayout, WHSDocumentRoutingLayout, WHSPrinterStockType, WHSSysCorpNetPrinters
ms.topic: how-to
ms.date: 07/31/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Dynamic printer selection

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!-- KFM: Preview until 10.0.36 GA -->

This article explains how to set up your system to dynamically select a printer when printing [license plate labels](print-license-plate-labels-using-label-layouts.md) and [container labels](print-container-labels.md).

When a worker requests a print when using dynamic printer selection, the system selects a printer based on the current work user, warehouse, location, and/or zone. The warehouse manager can set up default printers for each work user, warehouse, location, and/or zone.

## Basic printing and label layout setup

Before you can set up dynamic printing selection, you must configure your printers and labels in the system, as summarized in the following subsections.

### <a name="stock-type"></a>Set up printer stock types

A *printer stock type* typically describes the paper type (such as size) a specific printer uses. It's also used to specify the paper type that a specific label layout will be printed to.

> [!IMPORTANT]
> To use dynamic printer selection, you *must* set up a printer stock type for each relevant printer. You must also set up a printer stock type for each label layout that you want to use for dynamic printing selection.

Follow these steps to set up your printer stock types:

1. Go to **Warehouse management \> Setup \> Document routing \> Printer stock types** and create or select a stock type.
1. Make the following settings for the new or selected stock type:
    - **Printer stock type** – Enter a name for the printer stock type (for example *A1*).
    - **Description** – Enter a short description of the printer stock type.
1. Continue working until you have all the stock types that you need.
1. On the Action pane, select **Save**.

### Set up the printer stock type of a label printer

Follow these steps to set the printer stock type of a label printer:

1. Go to **Warehouse management \> Setup \> Document routing \> Label printers** and create or select a printer.
1. For your new or selected printer, set the **Printer stock type** field to the relevant printer stock type, such as one of those set up in the previous section. For more information about the other settings here, see [Set up a printer](label-printing-using-external-label-service.md#label-printers).
1. Continue working until you have all the stock types that you need.
1. On the Action pane, select **Save**.

### Set a label layout, including the printer stock type

Follow these steps to set the printer stock type for a label layout:

1. Go to **Warehouse management \> Setup \> Document routing \> Label layout**.
1. At the top of the list pane, set the **Label layout type** field to *License Plate Label*.
1. Create or select a label layout.
1. Set the **Printer stock type** field to the printer stock type you set up earlier in this article. For more information about the other settings here, see [License plate label layouts and printing](print-license-plate-labels-using-label-layouts.md).
1. On the Action Pane, select **Save**.

### Configure the license plate label routing

Follow these steps to configure the license plate label routing:

1. Go to **Warehouse management \> Setup \> Document routing \> Document routing**.
1. Set up license plate label routing as usual (as described in [Set up license plate label routing](print-license-plate-labels-using-label-layouts.md#routing)). However, be sure to include just one row on the **Document routing printers** FastTab, configured with the following settings:
    - **Name** – Leave blank.
    - **Label layout ID** – Select the label layout that you set up in the previous section.

    > [!NOTE]
    > If row exists here that has a **Name** specified, then that printer will be used and the dynamic printing selection won't be considered.

1. On the Action Pane, select **Save**.

## Set up default label printers for specific workers and locations

Once your printers and label layouts are set up, you can set up default label printers for specific workers and locations. These settings establish the printer that the system will choose (based on the current worker and/or location) when you use dynamic printer selection (see also [How the system selects a printer](#resolve-printer)).

Follow these steps to set up default label printers for each worker and/or location:

1. Go to **Warehouse management \> Document routing \> Default label printers**.
1. Open the **Locations** tab. The grid on this page shows the default label printers assigned to each location. For flows where the system knows the location a worker is in when requesting a print the printers set here take priority (provided the worker hasn't manually overridden the default printer selection). Use the toolbar buttons to add or remove rows as needed. Make the following settings for each row:
    - **Printer stock type** – Select the printer stock type for which the row applies.
    - **Warehouse** – Select the warehouse that includes the location.
    - **Location scope type** – Set to *Location* to identify a specific location. Set to *Zone* to specify a zone that includes multiple locations.
    - **Location scope** – Select the location or zone for which the row applies (depending on the **Location scope type** setting).
    - **Printer name** – Select the default printer to use for the location or zone specified for this row.
1. Open the **Users** tab. The grid on this page shows the default label printers assigned to each worker in each warehouse. Use the toolbar buttons to add or remove rows as needed. Make the following settings for each row:
    - **Printer stock type** – Select the printer stock type for which the row applies.
    - **User ID** – Select the user ID of the worker for which the row applies.
    - **Warehouse** – Select the warehouse for which the row applies. You can set up multiple rows for users that work in more than one warehouse. Leave this blank to set the default printer to use for a worker when no other more specific row applies. The system will choose the printer that is most specific to the warehouse where the user is signed in when requesting a print.
    - **Printer name** – Select the default printer to use for the worker, warehouse, and stock type combination specified for this row.
1. On the Action Pane, select **Save**.

## Create a menu item to allow workers to override the default printer

You can set up the Warehouse Management mobile app to allow workers to override the default printer assigned to them by using their mobile device to scan a new printer name. To do so, create a new mobile device menu item, set the **Mode** to *Indirect*, and set the **Activity code** to *Override label printer*.

## <a name="resolve-printer"></a>How the system selects a printer

While executing a print job, the system uses the following sequence to identify which printer to use:

1. If the current worker has manually overridden the printer, and the selected printer uses the printer stock type of the layout currently being printed, then it will use that printer (skip the rest of this list).
1. If no overriding printer exists, then the system checks the default printer setup.
    1. If a default label printer with the required stock type is set up for the location or zone specified in the current flow (for example, when printing a container label from the packing station) then that printer will be used.
    1. Otherwise, the system uses the default label printer with the required stock type set up for the current user and warehouse.
1. If no override or default printer is found, then no label will be printed.

## Additional resources

- [License plate label layouts and printing](print-license-plate-labels-using-label-layouts.md)
- [Container label layouts and printing](print-container-labels.md)
- [Document routing label layouts](document-routing-layout-for-license-plates.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
