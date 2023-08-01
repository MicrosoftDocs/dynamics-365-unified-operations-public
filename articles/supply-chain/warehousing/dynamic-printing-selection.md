---
title: Dynamic printer selection
description: This article explains how to set up your system to dynamically select a printer when license plate labels and container labels are printed.
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

This article explains how to set up your system to dynamically select a printer when [license plate labels](print-license-plate-labels-using-label-layouts.md) and [container labels](print-container-labels.md) are printed.

When dynamic printer selection is used, and a worker requests printing, the system selects a printer based on the current work user, warehouse, location, and/or zone. The warehouse manager can set up default printers for each work user, warehouse, location, and/or zone.

## Basic printing and label layout setup

Before you can set up dynamic printer selection, you must configure your printers and labels in the system, as summarized in the following subsections.

### <a name="stock-type"></a>Set up printer stock types

A *printer stock type* typically describes the type of paper (for example, the size) that a specific printer uses. It's also used to specify the type of paper that a specific label layout should be printed to.

> [!IMPORTANT]
> To use dynamic printer selection, you *must* set up a printer stock type for each relevant printer. You must also set up a printer stock type for each label layout that you want to use for dynamic printer selection.

Follow these steps to set up printer stock types.

1. Go to **Warehouse management \> Setup \> Document routing \> Printer stock types**.
1. Create or select a stock type.
1. For the new or selected stock type, set the following fields:

    - **Printer stock type** – Enter a name for the printer stock type (for example, *A1*).
    - **Description** – Enter a short description of the printer stock type.

1. Repeat steps 2 and 3 until you've set up all the stock types that you need.
1. On the Action Pane, select **Save**.

### Set the printer stock type for a label printer

Follow these steps to set the printer stock type for a label printer.

1. Go to **Warehouse management \> Setup \> Document routing \> Label printers**.
1. Create or select a printer.
1. For the new or selected printer, set the **Printer stock type** field to the relevant printer stock type. (For example, select one of the stock types that you set up in the previous section.) For information about the other settings that are available for a label printer, see [Set up a printer](label-printing-using-external-label-service.md#label-printers).
1. Repeat steps 2 and 3 until you've set up all the stock types that you need.
1. On the Action Pane, select **Save**.

### Set up a label layout, including the printer stock type

Follow these steps to set the printer stock type for a label layout.

1. Go to **Warehouse management \> Setup \> Document routing \> Label layout**.
1. At the top of the list pane, set the **Label layout type** field to *License Plate Label*.
1. Create or select a label layout.
1. For the new or selected label layout, set the **Printer stock type** field to a printer stock type that you set up earlier in this article. For information about the other settings that are available for a label layout, see [License plate label layouts and printing](print-license-plate-labels-using-label-layouts.md).
1. On the Action Pane, select **Save**.

### Configure the license plate label routing

Follow these steps to configure the license plate label routing.

1. Go to **Warehouse management \> Setup \> Document routing \> Document routing**.
1. Set up license plate label routing as described in [Set up license plate label routing](print-license-plate-labels-using-label-layouts.md#routing). However, on the **Document routing printers** FastTab, include only one row, and configure it in the following way:

    - **Name** – Leave this field blank.
    - **Label layout ID** – Select the label layout that you set up in the previous section.

    > [!NOTE]
    > If the **Document routing printers** FastTab includes a row where the printer name is specified (that is, the **Name** field isn't blank), dynamic printer selection won't be used. Instead, the specified printer will be used.

1. On the Action Pane, select **Save**.

## Set up default label printers for specific workers and locations

After your printers and label layouts are set up, you can set up default label printers for specific workers and locations. The settings define the printer that the system selects for the current worker and/or location when you use dynamic printer selection. For more information, see the [How the system selects a printer](#resolve-printer) section later in this article.

Follow these steps to set up default label printers for each worker and/or location.

1. Go to **Warehouse management \> Document routing \> Default label printers**.
1. On the **Locations** tab, the grid shows the default label printers that are assigned to each location. For flows where the system can determine the location of a worker who requests printing, the printers that are set in this grid have priority (provided that the worker hasn't manually overridden the default printer selection). Use the toolbar buttons to add or remove rows as required. For each row, set the following fields:

    - **Printer stock type** – Select the printer stock type that the row applies to.
    - **Warehouse** – Select the warehouse that includes the location.
    - **Location scope type** – Select *Location* if the row applies to one specific location. Select *Zone* if the row applies to a zone that includes multiple locations.
    - **Location scope** – Depending on the **Location scope type** value, select either the location or the zone that the row applies to.
    - **Printer name** – Select the default printer to use for the location or zone that the row applies to.

1. On the **Users** tab, the grid shows the default label printers that are assigned to each worker in each warehouse. Use the toolbar buttons to add or remove rows as required. For each row, set the following fields:

    - **Printer stock type** – Select the printer stock type that the row applies to.
    - **User ID** – Select the user ID of the worker that the row applies to.
    - **Warehouse** – Select the warehouse that the row applies to. You can set up multiple rows for workers who work in more than one warehouse. Leave this field blank to set the default printer that's used for a worker if no other, more specific row applies. When the worker requests printing, the system will select the printer that's most specific to the warehouse where the worker is signed in.
    - **Printer name** – Select the default printer to use for the combination of a worker, warehouse, and stock type on the row.

1. On the Action Pane, select **Save**.

## Create a menu item that lets workers override their default printer

You can set up the Warehouse Management mobile app to let workers override the default printer that's assigned to them. Workers can then use their mobile device to scan a new printer name.

Create a new mobile device menu item, set the **Mode** field to *Indirect*, and set the **Activity code** field to *Override label printer*.

## <a name="resolve-printer"></a>How the system selects a printer

When a print job is run, the system uses the following sequence to identify which printer to use:

1. If the current worker has manually overridden the printer, and the selected printer uses the printer stock type of the layout that's currently being printed, the system uses that printer (and then skips the remaining steps in this sequence).
1. If no printer override exists, the system checks the default printer setup.

    1. If a default label printer that uses the required stock type is set up for the location or zone that's specified in the current flow (for example, when a container label is printed from the packing station), the system uses that printer.
    1. Otherwise, the system uses the default label printer that uses the required stock type and that's set up for the current user and warehouse.

1. If no override or default printer is found, no label is printed.

## Additional resources

- [License plate label layouts and printing](print-license-plate-labels-using-label-layouts.md)
- [Container label layouts and printing](print-container-labels.md)
- [Document routing label layouts](document-routing-layout-for-license-plates.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
