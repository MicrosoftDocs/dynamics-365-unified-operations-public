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
<!-- KFM: FM needed?-->

This article explains how to set up your system to dynamically select a printer when printing [license plate labels](print-license-plate-labels-using-label-layouts.md) and [container labels](print-container-labels.md).

When a worker requests a print when using dynamic printer selection, the system selects a printer based on the current work user, warehouse, location, and/or zone. The warehouse manager can set up default printers for each work user, warehouse, location, and/or zone.

## Basic printing and label layout setup

Before you can set up dynamic printing selection, you must configure your printers and labels in the system, as summarized in the following subsections.

### <a name="stock-type"></a>Set up printer stock types

<!--KFM: Are stock types new for this feature? Is there something special about them here? -->

A *printer stock type* typically describes the paper type a specific printer uses. It is also used to specify the paper type that a specific label layout will be printed to.

Follow these steps to set up your e printer stock types:

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

Once your printers and label layouts are set up, you can set up default label printers for specific workers and locations.

Follow these steps to set up a default label printer for a specific worker and/or location:

1. Go to **Warehouse management \> Document routing \> Default label printers**.
1. Open the **Users** tab. The grid on this page shows the default label printers assigned to each worker in each warehouse. Use the toolbar buttons to add or remove rows as needed. Make the following settings for each row:
    - **Printer stock type** – Select the printer stock type for which the row applies. <!-- KFM: Might we have multiple rows, each for a different stock type? -->
    - **User ID** – Select the user ID of the worker for which the row applies.
    - **Warehouse** – Select the warehouse for which the row applies. You can set up multiple rows for users that work in more than one warehouse. Leave this blank to set the default printer to use for a worker when no other default applies. The system will choose the printer that is most specific to the warehouse where the user is currently located when requesting a print. <!-- KFM: Please confirm this -->
    - **Printer name** – Select the default printer to use for the worker, warehouse, and stock type combination specified for this row. <!-- KFM: Must match the selected stock type? -->
1. On the Action Pane, select **Save**.

<!-- KFM: What about the **Locations** tab? Is that part of this feature?  -->

## Create a menu item to allow workers to override the default printer

You can set up the Warehouse Management mobile app to allow workers to override the default printer assigned to them by using their mobile device to scan a new printer name. To do so, create a new mobile device menu item, set the **Mode** to *Indirect*, and set the **Activity code** to *Override label printer*.

## How the system selects a printer

While executing a print job, the system uses the following sequence to identify which printer to use:

1. If the current worker has overridden the printer with the printer stock type of the layout currently being printed, then it will use that printer (skip the rest of this list).
1. If no overriding printer exists, then the system checks the default printer setup.
    1. If a default label printer is set up for the current location or zone, and is specified in the flow (for example, when printing a container label from the packing station) then that printer will be used.
    1. If no printer has yet been found, then the system will use the default label printer set up for the current user. <!-- KFM: What if there still isn't a printer for the current user? -->

## Additional resources

- [License plate label layouts and printing](print-license-plate-labels-using-label-layouts.md)
- [Container label layouts and printing](print-container-labels.md)
- [Document routing label layouts](document-routing-layout-for-license-plates.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
