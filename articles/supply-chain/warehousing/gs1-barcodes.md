---
title: GS1 barcodes and QR codes
description: This topic describes how to set up and GS1 barcodes and QR codes for scanning labels in a warehouse
author: Mirzaab
ms.date: 08/02/2021
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: mirzaab
ms.search.validFrom: 2021-08-02
ms.dyn365.ops.version: 10.0.21
---

# GS1 barcodes and QR codes

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

Warehouse workers often need to complete several steps when using a mobile device scanner to register movements of an item, palette, or container. These tasks can include both scanning barcodes and entering information manually on the mobile device. The barcodes use a company-specific format that you define and manage using Dynamics 365 Supply Chain Management.

GS1 barcode and QR code shipping label formats were developed to provide a global standard for exchanging data between different companies. GS1 formats not only encode the data but provide a method of defining the meaning of the data using a predefined list of *application identifiers*. The standard defines the data format and the various kinds of data that can be encoded using it. Unlike older barcode standards, GS1 codes can have multiple data elements so that a single barcode scan can capture several types of product information, including batch, expiration date, and more.

GS1 support in Supply Chain Management dramatically simplifies the scanning process in warehouses where pallets and containers are labeled using GS1 format codes. Warehouse workers can scan a GS1 barcode to extract all the needed information in a single scan. This reduces the time associated with the task by eliminating the need to do multiple scans and/or manually input information while helping to improve accuracy.

Logistics managers must set up the required list of application identifiers and associate each of them with the proper mobile device menu item(s). The identifiers they can be used throughout different warehouses as a global setting for moving and packing purposes. As a result, the diversity of shipping labels will take a unified form.

Unless otherwise stated, this topic uses the term *barcode* to refer both to barcodes and to QR codes.

## Turn on the GS1 feature

Before you can use this feature, it must be turned on in your system. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Warehouse management*
- **Feature name:** *Scan GS1 barcodes*

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

GS1 formats not only encode the data but provide a method of defining the meaning of the data using a predefined list of *application identifiers*. Logistics managers must set up the required list of application identifiers and associate each of them with the proper mobile device menu item(s). The identifiers can be used throughout different warehouses as a global setting for moving and packing purposes. As a result, the diversity of shipping labels will take a unified form.

The system uses the data, particularly the predefined application identifiers, to establish which rules should be applied for the relevant piece of the scanned information.

Application identifiers signal to the system that the following characters in the scanned barcode will be considered a block of encrypted information. The application identifier setup tells the system how to interpret that barcode and save it as a value in the system.

Logistics managers can use standard international application identifiers and/or come up with their own ones.

### Load the standard application identifiers

To get started quickly, you can load a list of common international application identifiers that you can later extend or alter as needed.

To load the standard application identifiers

1. Go to **Warehouse management \> Setup \> GS1 \> GS1 application identifiers**.
1. Select **Create default setup** from the Action Pane.

> [!WARNING]
> The **Create default setup** command deletes all the currently defined application identifiers and replaces them with the standard list. However, you can customize the list as needed after loading the default setup.

### Set up custom application identifiers

If some or all the application identifiers used by your company are different from the standard ones, you can create your own codes from scratch or customize the standard set as needed.

To set up and customize your GS1 own application identifiers:

1. Go to **Warehouse management \> Setup \> GS1 \> GS1 application identifiers**.
1. Do one of the following:
    - To create a new identifier, select **New** on the Action Pane.
    - To edit existing identifiers, select **Edit** on the Action Pane.
1. Make the following settings for your new or selected identifier:
    - **Application identifier** – Enter the identification code for the identifier. This is typically a two-digit integer, but can be longer. For decimal values, the last digit of the identifier indicates how many decimal places there are (see also the description for **Decimal**, later in this list).
    - **Description** – Enter a short description of the identifier.
    - **Fixed length** – Select this check box if the values scanned using this application identifier have a fixed number of characters. Clear this check box if the values are of variable length (in which case, the end of the value must be indicated in the value using the **Group separator** character established on the **Warehouse management parameters page**).
    - **Length** – Enter the maximum number of characters that may appear in the values scanned using this application identifier. When **Fixed length** is set to *Yes*, then exactly this number of characters is expected.
    - **Type** – Select the type of value scanned using this application identifier (*Numeric*, *Alphanumeric*, or *Date*). For dates, the expected format is YYMMDD (no spaces or hyphens).
    - **Decimal** – Select this check box if the value includes an implied decimal point. When this box is selected, the system will use the last digit in the **Application identifier** to find out how many decimal places there are. For example, if the application identifier is 3205, then the right-most five digits of the value are interpreted as coming after the decimal point.

> [!NOTE]
> The **Group separator** established on the **Warehouse management parameters page** is optional if a value followed by an application identifier has a **Fixed length** or its length is maximized (equal to the **Length** set for the application identifier).

## Establish the generic GS1 setup

The generic GS1 setup establishes a collection of common mappings that match each relevant mobile app input field to the application identifier that controls how values from scanned barcodes should be interpreted and stored in that field. These settings apply to all scans for all mobile device menu items unless overwritten for one or more specific fields by as GS1 policy assigned to a specific menu item. The generic GS1 setup only allows for a single value to be scanned at a time, so if you want to be able to load several field values from a single scan, then you must set up a GS1 policy for the relevant menu items. For more information about GS1 policies, see the next section.

### Load the standard generic GS1 setup

The **GS1 generic setup** page lets you load a standard set of mappings between mobile device fields and standard application identifiers created by the default setup.

To establish the generic GS1 setup, go to **Warehouse management \> Setup \> GS1 \> GS1 generic setup**. Then select **Create default setup** to automatically assign a suitable application identifier to each of the fields typically used by mobile device menu items.

> [!WARNING]
> The **Create default setup** command deletes the entire existing generic GS1 setup (if any) and loads the standard setup.

### Customize the standard generic GS1 setup

To customize generic GS1 setup:

1. Go to **Warehouse management \> Setup \> GS1 \> GS1 generic setup**.
1. Do one of the following:
    - To create a new mapping, select **New** on the Action Pane.
    - To edit existing mapping, select **Edit** on the Action Pane.
1. Make the following settings for your new or selected mapping:
    - **Field** – Select or enter the mobile app input field to which the incoming value should be assigned. This isn't the display name seen by workers, but is instead the key name assigned to the field in the underlying code. The default setup provides a collection of fields that are likely to be useful (with intuitive key names for each field and matching back-end functionality) but you may need to talk to your development partners to find the correct selections for your implementation.
    - **Application identifier** – Select the applicable application identifier, as defined on the **GS1 application identifiers** page. The identifier establishes how the barcode will be interpreted and stored as a value for the named field.
    - **Description** – Shows the description of the selected **Application identifier**.

## Set up GS1 policies that you can assign to mobile device menu items

The GS1 standard is designed to enable workers to load several values after scanning a single barcode just once. To reach this aim, logistics managers must set up GS1 policies that tell the system how to interpret multi-value barcodes. Later, you'll be able to assign policies to mobile device menu items to control how a barcode will be interpreted when a worker scans it while using a given menu item.

When you don't have a GS1 policy assigned, the system is only able to capture a single value, which is applied to the mobile app input selected when the worker takes the scan, as specified by the generic GS1 setup. When a GS1 policy is assigned to the menu item, the system still uses the generic GS1 setup to map the first barcode value to the selected field, but can then capture additional field values as specified by the applicable policy.

### Load the standard specific GS1 policies

To get started quickly, you can load a set of GS1 policies that you can later extend or alter as needed.

To load the standard application identifiers

1. Go to **Warehouse management \> Setup \> GS1 \> GS1 policy**.
1. Select **Create default setup** from the Action Pane.

> [!WARNING]
> The **Create default setup** command deletes all the currently defined policies and replaces them with the standard set of policies. However, you can customize the policies as needed after loading the default setup.

### Set up custom specific GS1 policies

To set up and customize your GS1 policies:

1. Go to **Warehouse management \> Setup \> GS1 \> GS1 policy.**
1. Do one of the following:
    - To create a new policy, select **New** on the Action Pane.
    - To edit an existing policies, select it in the list pane.
1. Make the following settings in the header:
    - **Policy name** – Enter a name for the policy.
    - **Description** – Enter a short description of the policy.
1. In the FastTab below the header, establish match field names to application identifiers as needed for the current policy. Use the buttons in the toolbar to add or remove rows as needed. For each row, make the following settings:
    - **Field** – Select or enter the mobile app input field to which the incoming value should be assigned. This isn't the display name seen by workers, but is instead the key name assigned to the field in the underlying code. The default setup provides a collection of fields that are likely to be useful (with intuitive key names for each field and matching back-end functionality) but you may need to talk to your development partners to find the correct selections for your implementation.
    - **Application identifier** – Select the applicable application identifier, as defined on the **GS1 application identifiers** page. The identifier establishes how the barcode will be interpreted and stored as a value for the named field.
    - **Description** – Shows the description of the selected **Application identifier**.
    - **Sorting** – Each multi-value barcode includes a series of application identifiers, each followed by a value. The applicable GS1 policy identifies which application identifier maps to each database field. However, if you have a barcode that uses the same application identifier more than once, the system will map application identifiers to fields based on the order in which they appear in the code. For rows that share an application identifier with one or more other rows, use this setting to establish the order in which to process the matching rows. The row with the lowest sorting value will be processed first.

> [!NOTE]
> For barcodes that include more than one identical application identifier, you *must* use the **Sorting** field to establish the order of the fields.

## Assign GS1 policies to mobile device menu items

By default, all mobile device menu items will provide input fields where workers can scan a single value according to the generic GS1 setup. For any mobile device menu item where you want to enable workers to scan more than one field value with a single scan, you must assign a GS1 policy by doing the following steps:

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items.**
1. Create or open a menu item.
1. On the **General** FastTab, set the **GS1 policy** field to the policy that applies for this menu item.

## GS1 setup example

This example applies to a system that has its GS1 options set up as follows:.

- The following global settings are established on the **Warehouse management parameters** page:
  - **FNC1 character:** *\]1C*
  - **Group separator:** *~*

- On the **GS1 application identifiers** page, the following application identifiers are relevant for this example:

    | Application identifier | Description | Fixed length | Length | Type | Decimal |
    |---|---|---|---|---|---|
    | 01 | GTIN | Yes | 14 | Numeric | No |
    | 10 | Batch number | No | 20 | Alphanumeric | No |
    | 17 | Expiry date | Yes | 6 | Date | No |
    | 30 | Receiving quantity | No | 8 | Numeric | No |

- On the **GS1 generic setup** page, the following settings established for the generic GS1 policy are relevant for this example:

    | Field | Application identifier | Description |
    |---|---|---|
    | ItemId | 01 | GTIN |

- On the **GS1 policy** page, there is policy with a **Policy name** of *Purchase receiving*. This policy includes the following lines: 

    | Field | Application identifier | Description | Sorting |
    |---|---|---|---|
    | ExpDate | 17 | Expiry date | 0 |
    | InventBatchId | 10 | Batch number | 0 |
    | Qty | 30 | Receiving quantity | 0 |

- One the **Mobile device menu items** page, there is a menu item named *Purchase receiving* with its **GS1 policy** set to *Purchase receiving*.

Now, goods for a purchase order have arrived at the warehouse. The worker proceeds as follows:

1. On the mobile device, the worker selects the **Purchase receiving** menu item.
1. The worker enters the purchase order number.
1. The worker selects the **Item** field and scans the following barcode: \]1C0100000012345678\~3030\~10b1\~17220215.
1. As a result of the settings outlined at the start of this example, the system parses the code as follows:

    | Field key | Application ID | Value | Note |
    |---|---|---|---|
    | ItemId | 01 | 00000012345678 | The worker scanned to the **Item** field, so the first value in the barcode maps to this field and the mapping is taken from the GS1 generic setup. |
    | Qty | 30 | 30 | Because we are capturing several field values with a single scan, this and the remaining mappings are taken from the GS1 policy assigned to the **Purchase receiving** menu item. This is the quantity received. |
    | InventBatchId | 10 | b1 | This is the batch ID. |
    | ExpDate | 17 | 220215 | The date format is YYMMDD, so the expiry date is February 15, 2022 |

1. The receipt is registered and the relevant database values are populated after the single scan.
