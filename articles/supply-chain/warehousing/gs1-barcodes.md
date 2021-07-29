---
title: GS1 barcodes and QR codes
description: This topic describes how to set up and GS1 barcodes and QR codes for scanning labels in a warehouse
author: XXXX
ms.date: MM/DD/YYYY
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: XXXX
ms.search.validFrom: YYYY-MM-DD
ms.dyn365.ops.version: 10.0.18
---

# GS1 barcodes and QR codes

[!include [banner](../includes/banner.md)]

Warehouse workers often need to complete several steps when using a mobile device scanner to register movements of an item, palette, or container. These tasks can include both scanning barcodes and entering information manually on the mobile device. The barcodes use a company-specific format that you define and manage using Dynamics 365 Supply Chain Management.

GS1 barcode and QR code shipping label formats were developed to provide a global standard for exchanging data between different companies. GS1 formats not only encode the data but provide a method of defining the meaning of the data using a predefined list of *application identifiers*. The standard defines the data format and the various kinds of data that can be encoded using it. Unlike older barcode standards, GS1 codes can have multiple data elements so that a single code scan can capture several types of product information, including batch, expiration date, and more.

GS1 support in Supply Chain Management dramatically simplifies the scanning process in warehouses where pallets and containers are labeled using GS1 format codes. Warehouse workers can scan a GS1 code to extract all the needed information in a single scan. This reduces the time associated with the task by eliminating the need to do multiple scans and/or manually input information while helping to improve accuracy.

Logistics managers must set up the required list of application identifiers and associate each of them with the proper mobile device menu item(s). The identifiers they can be used throughout different warehouses as a global setting for moving and packing purposes. As a result, the diversity of shipping labels will take a unified form.

## Set up global GS1 options

The **Warehouse management parameters** page provides a few settings for establishing global GS1 options.

To set up your global GS1 options:

1. Go to **Warehouse management \> Setup \> Warehouse management parameters.**
1. Expand the **Bar codes** FastTab and make the following settings:
    - **FNC1 Character** – Specify characters that should be interpreted as a prefix when parsing a barcode.
    - **Datamatrix character** – Specify characters that should be interpreted as a prefix when parsing datamatrix.
    - **QR code character** – Specify characters that should be interpreted as a prefix when parsing a QR code.
    - **Group separator** – Specify the character used to identify separate parts of a barcode or QR code.
    - **Maximum length of identifier** – Specify the maximum number of characters permitted for the application identifier.

> [!NOTE]
> Prefixes point out to the system that a barcode is encrypted as GS1 standard. Up to three prefixes (**FNC1 Character**, **Datamatrix character**, and/or **QR code character**) can be used simultaneously and for various purposes.

## GS1 application identifiers

GS1 formats not only encode the data but provide a method of defining the meaning of the data using a predefined list of *application identifiers*. Logistics managers must set up the required list of application identifiers and associate each of them with the proper mobile device menu item(s). The identifiers they can be used throughout different warehouses as a global setting for moving and packing purposes. As a result, the diversity of shipping labels will take a unified form.

The system uses the data, particularly the predefined application identifiers, to guide which rule should be applied for the relevant piece of the scanned information.

Application identifiers signal to the system that the following characters in the scanned code will be considered a block of encrypted information.

Logistics managers can use standard international application identifiers or come up with their own ones.

### Load the standard application identifiers

The **Create default setup** button on the menu can help Logistics managers create a list of common international application identifiers that can be extended or altered.

**WARNING**: The **Create default setup** command deletes all the currently defined application identifiers and replaces them with the standard list. However, you can customize the list as needed after loading the default setup.

To load the standard application identifiers

1. Go to **Warehouse management \> Setup \> GS1 \> GS1 application identifiers**.
1. Select **Create default setup** from the Action Pane.

### Custom application identifiers

If some or all the application identifiers used by your company are different from the standard ones, you can create your own codes from scratch or customize the standard set as needed.

To set up and customize your GS1 own application identifiers:

1. Go to **Warehouse management \> Setup \> GS1 \> GS1 application identifiers.**
1. There is the **GS1 application identifiers** grid that contains the following fields:
    - **Application identifier** – Identifies which rules to apply when scanning a GS1 barcode.
    - **Description** – Enter a short description of the identifier.
    - **Fixed length** – Specify whether the value of this application identifier has a fixed number of characters.
    - **Length** – Enter the maximum number of characters in the value.
    - **Type** – Select the type of value (*Numeric*, *Alphanumeric*, or*Date*).
    - **Decimal** – Value decimal for numeric type.

> [!NOTE]
> The **Group separator** established on the **Warehouse management parameters page** may not be used if a value followed by an application identifier has a **Fixed length** or its length is maximized (equal to the **Length** set for the application identifier).

## Use GS1 policies to assign application identifiers to mobile device fields

The GS1 standard is designed to enable workers to load several values after scanning a single code just once. To reach this aim, logistics managers must assign an application identifier to each relevant field used by the mobile device. The assigned application identifiers let the system know how to parse and recognize the scanned information. As a result, the mobile device gets fields automatically populated with the decrypted barcode data.

### Load the generic GS1 polity setup

The **Generic GS1 setup** page lets you load a standard set of mappings between mobile device fields and standard application identifiers. It establishes the global rules for all mobile device menu items fields.

To establish the generic GS1 setup, go to **Warehouse management \> Setup \> GS1 \> GS1 generic setup**. Then select **Create default setup** to automatically assign a suitable application identifier to each of the mobile device menu items that are currently in use.

> [!WARNING]
> The **Create default setup** command deletes the entire existing GS1 setup (if any) and loads the standard setup.

### Customize your GS1 policy

If some or all the mobile device files and/or application identifiers used by your company are different from the standard ones, you can create your own mappings from scratch or customize the standard set as needed.

To set up and customize your GS1 policy:

1. Go to **Warehouse management \> Setup \> GS1 \> GS1 policy.**
1. The page contains a grid with the following fields:
    - **Field** – Specify the actual field from a Supply Chain Management table whose value could be set when scanning
    - **Application identifier** – Select the applicable application identifier defined on the **GS1 application identifiers** page.
    - **Description** – Enter a description for the row.
    - **Sorting** – For rows that share an application identifier with one or more other rows, use this setting to establish the order in which to process the matching rows. The row with the lowest sorting value will be processed first.

> [!NOTE]
> For barcodes and QR codes that include more than one identical application identifier, you must use the **Sorting** field to establish the order of the fields.

## Assign GS1 policies to mobile device menu items

For each mobile device menu item that will be used to scan a GS1 code, you must assign a GS1 policy by doing the following steps:

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items.**
1. Create or open a menu item.
1. On the **General** FastTab, set the **GS1 policy** field to the policy that applies for this menu item.

## GS1 setup example

This example applies to a system that has its GS1 options set up as follows:.

- On the **Warehouse management parameters** page, **FNC1 character** = *\]1C* 
- On the **GS1 policy** page, there is policy with **Policy name** = *Purchase receiving*. This policy includes the following lines:
  - **Field** = *ExpDate*, **Application identifier** = *17*, **Description** = *Expiry date*, **Sorting** = *0*
  - **Field** = *InventBatchId*, **Application identifier** = *10*, **Description** = *BatchNum*, **Sorting** = *0*
  - **Field** = *Qty*, **Application identifier** = *30*, **Description** = *Receiving quantity*, **Sorting** = *0*
- One the **Mobile device menu items** page, there is a menu item named *Purchase receiving* with its**GS1 policy** set to *Purchase receiving*.

Now, goods for a purchase order have arrived at the warehouse. The arriving item has GTIN = 0000012345678, and the received quantity (30) is greater than that specified in the purchase order (10), but over receiving is allowed.

The worker proceeds as follows:

1. On the mobile device, select the **Purchase receiving** menu item.
1. Select the purchase order number.
1. Select the **Item** field and scan the following barcode: \]1C0100000012345678\~3030\~10b1\~17220215
1. The item (0000012345678), its dimensions, and its quantity (30) are all automatically populated after the single scan.
