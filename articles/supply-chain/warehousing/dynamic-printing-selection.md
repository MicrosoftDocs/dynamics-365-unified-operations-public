---
# required metadata

title: Dynamic printing selection
description: This article describes how to setup the system to dynamically select printers for workers and locations
author: AlexandraDesypri
ms.author: adesypri
ms.date: 28/06/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: WHSLicensePlateLabel, WHSWorkUserdefaultLabelPrinterTable, WHSLocationDefaultLabelPrinter, WHSLabelLayout, WHSDocumentRoutingLayout, WHSPrinterStockType, WHSSysCorpNetPrinters
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for articles migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: perlynne
ms.search.validFrom: 2012-04-01
ms.dyn365.ops.version: 10.0.10
---

# Dynamic printing selection

[!include [banner](../includes/banner.md)]

This article explains how to set up your system to dynamically select a printer, when printing [license plate labels](print-license-plate-labels-using-label-layouts.md) and [container labels](print-container-labels.md).

The printer is selected based on the configuration of the work user that is executing the printing work, or the current location or zone. The warehouse manager can set up default printers for each work user, for specific or across warehouses, and for each location or zone.

# Example scenario: How to set up dynamic printing selection for a specific work user

In this example we will run through the configuration of dynamic printing selection for a specific work user, when printing license plate labels.

## Set up printer stock types

A printer stock type typically describes the paper type a specific printer uses. It is also used to specify the paper type that a specific label layout will be printed to.

Go to **Warehouse management \> Document routing \> Printer stock type** and create a new printer stock type. In the **Printer stock type** field enter a name for the printer stock type (for example _A1_)

### Set up the printer stock type of a label printer

Follow these steps to set the printer stock type of a label printer:

1. Go to **Warehouse management \> Document routing \> Label printer** and create or select a printer.
1. Set the **Printer stock type** field to the printer stock type created in the previous step.

### Set up the printer stock type of a label layout

1. Go to **Warehouse management \> Document routing \> Label layout**.
1. At the top of the list pane, set the **Label layout type** field to _License Plate Label_.
1. Create or select a label layout.
1. Set the **Printer stock type field** to the printer stock type previously created.

## Configure the license plate label routing

You can follow the setup as described in [License plate label layouts and printing](print-license-plate-labels-using-label-layouts.md#set-up-license-plate-label-routing).

When setting up license plate label routing, on the **Document routing printers** FastTab, set the following:

1. Set the **Label layout ID** to that of the label layout configured in the previous step.
1. Leave the **Name** blank.

    > [!NOTE]
    > If the **Name** it is specified, then this printer will be used, and the dynamic printing selection will not be considered.

## Set up default label printers

This setup allows the warehouse manager to control which printer prints specific label layouts, for specific work users and locations.

1. Go to **Warehouse management \> Document routing \> Default label printer** .
1. Select **Users** on the side pane.
1. On the new record created, set the following:
    - Set the **Printer stock type** to the printer stock type previously created.
    - Set the **User ID** to a work user id.
    - Leave the **Warehouse** field blank. This specifies that the setup will be applied across warehouses for the specified work user. You can add a configuration for each warehouse.
    - Set the **Printer name** to the printer configured earlier.

Once you have completed this step, whenever the specific user is printing license plate labels that have the specified printer stock type, the specified printer will be used. 

## Override the default setup

The default label printer setup for a specific work user can be overridden, using the mobile device to scan a new printer name.

Create a new mobile device menu item and set the **Mode** to _Indirect._ Set the **Activity code** to _Override label printer_.

Using this menu item, the user can scan the name of the printer that they want to use. The scanned printer will override the default label printer setup, for its specific printer stock type.

## Printer selection process

While executing the printing job, the system will first check if the work user that is executing it has overridden the printer with the printer stock type of the layout currently being printed. If so, then the overriding printer will be used. Otherwise, the system will then look into the default setup. First, any default label printer setup for the current location/zone will be considered, if one is specified in the flow (for example printing a container label in the packing station) and finally, any default label printer setup for the current user will be considered.

## Additional resources

- [License plate label layouts and printing](print-license-plate-labels-using-label-layouts.md)
- [Container label layouts and printing](print-container-labels.md)
- [Document routing label layouts](document-routing-layout-for-license-plates.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]