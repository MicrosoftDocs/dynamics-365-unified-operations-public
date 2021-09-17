---
title: GS1 bar codes and QR codes
description: This topic describes how to set up GS1 bar codes and QR codes so that labels can be scanned in a warehouse.
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

# GS1 bar codes and QR codes

[!include [banner](../includes/banner.md)]

Warehouse workers often have to complete several tasks when they use a mobile device scanner to register movements of an item, palette, or container. These tasks can include both scanning bar codes and manually entering information on the mobile device. The bar codes use a company-specific format that you define and manage by using Microsoft Dynamics 365 Supply Chain Management.

GS1 bar code and QR code formats for shipping labels were developed to provide a global standard for the exchange of data between companies. GS1 formats not only encode the data but also let you use a predefined list of *application identifiers* to define the meaning of the data. The GS1 standard defines the data format and the various kinds of data that it can be used to encode. Unlike older bar codes, GS1 bar codes can have multiple data elements. Therefore, a single bar code scan can capture several types of product information, such as the batch and the expiration date.

GS1 support in Supply Chain Management dramatically simplifies the scanning process in warehouses where pallets and containers are labeled by using codes in GS1 format. Warehouse workers can extract all the required information through a single scan of a GS1 bar code. By eliminating the need to do multiple scans and/or manually enter information, GS1 bar codes help reduce the time that is associated with tasks. At the same time, they also help improve accuracy.

Logistics managers must set up the required list of application identifiers and associate each of them with the appropriate mobile device menu items. The application identifiers can then be used across warehouses as a global setting for moving and packing purposes. Therefore, all shipping labels will take a unified form.

Unless otherwise stated, this topic uses the term *bar code* to refer to both bar codes and QR codes.

## Turn on the GS1 feature

Before you can use this feature, it must be turned on in your system. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Warehouse management*
- **Feature name:** *Scan GS1 barcodes*

## Set up global GS1 options

The **Warehouse management parameters** page provides a few settings that establish global GS1 options.

To set up global GS1 options, follow these steps.

1. Go to **Warehouse management \> Setup \> Warehouse management parameters**.
1. On the **Bar codes** FastTab, set the following fields:

    - **FNC1 Character** – Specify characters that should be interpreted as a prefix when a bar code is parsed.
    - **Datamatrix character** – Specify characters that should be interpreted as a prefix when a datamatrix is parsed.
    - **QR code character** – Specify characters that should be interpreted as a prefix when a QR code is parsed.
    - **Group separator** – Specify the character that identifies separate parts of a bar code or QR code.
    - **Maximum length of identifier** – Specify the maximum number of characters that is permitted for the application identifier.

> [!NOTE]
> Prefixes tell the system that a bar code is encrypted according to the GS1 standard. Up to three prefixes (**FNC1 Character**, **Datamatrix character**, and **QR code character**) can be used simultaneously and for various purposes.

## GS1 application identifiers

GS1 formats not only encode the data but also let you use a predefined list of application identifiers to define the meaning of the data. Logistics managers must set up the required list of application identifiers and associate each of them with the appropriate mobile device menu items. The identifiers can then be used across warehouses as a global setting for moving and packing purposes. Therefore, all shipping labels will take a unified form.

The system uses the data, especially the predefined application identifiers, to establish the rules that should be applied to the relevant piece of scanned information.

Each application identifier signals to the system that subsequent characters in the scanned bar code should be considered a block of encrypted information. The setup of the application identifiers defines how the system should interpret a bar code and save it as a value in the system.

Logistics managers can use standard international application identifiers and/or create their own.

### Load the standard application identifiers

To get started quickly, you can load a list of common international application identifiers. You can then extend or edit the list later, as you require.

To load the standard application identifiers, follow these steps.

1. Go to **Warehouse management \> Setup \> GS1 \> GS1 application identifiers**.
1. On the Action Pane, select **Create default setup**.

> [!WARNING]
> The **Create default setup** command deletes all currently defined application identifiers and replaces them with the standard list. However, after you load the default setup, you can customize the list as you require.

### Set up custom application identifiers

If some or all application identifiers that your company uses differ from the standard set, you can create your own codes from scratch or customize the standard set as you require.

To set up and customize your GS1 own application identifiers, follow these steps.

1. Go to **Warehouse management \> Setup \> GS1 \> GS1 application identifiers**.
1. Follow one of these steps:

    - To create a new identifier: On the Action Pane, select **New**.
    - To edit an existing identifier: Select the identifier, and then, on the Action Pane, select **Edit**.

1. Set the following fields for the new or selected identifier:

    - **Application identifier** – Enter the identification code for the application identifier. Typically, this code is a two-digit integer, but it can be longer. For decimal values, the last digit indicates the number of decimal places. For more information, see the description of the **Decimal** checkbox later in this list.
    - **Description** – Enter a short description of the identifier.
    - **Fixed length** – Select this checkbox if values that are scanned by using this application identifier have a fixed number of characters. Clear this checkbox if the length of values is variable. In this case, you must indicate the end of the value by using the group separator character that you specified on the **Warehouse management parameters** page.
    - **Length** – Enter the maximum number of characters that can appear in the values that are scanned by using this application identifier. If the **Fixed length** checkbox is selected, exactly this number of characters is expected.
    - **Type** – Select the type of value that is scanned by using this application identifier (*Numeric*, *Alphanumeric*, or *Date*). For dates, the expected format is YYMMDD (without spaces or hyphens).
    - **Decimal** – Select this checkbox if the value includes an implied decimal point. If this box is selected, the system will use the last digit of the application identifier to determine the number of decimal places. For example, if the application identifier is *3205*, the right-most five digits of the value will be interpreted as coming after the decimal point.

> [!NOTE]
> The group separator that is specified on the **Warehouse management parameters** page is optional if a value that is followed by an application identifier has a fixed length, or if its length is maximized (that is, if the length equals the **Length** value that is set for the application identifier).

## Establish the generic GS1 setup

The generic GS1 setup establishes a collection of common mappings. These mappings match each relevant input field in the mobile app to the application identifier that controls how values from scanned bar codes should be interpreted and stored in that field. By default, these settings apply to all scans for all mobile device menu items. However, they can be overwritten for one or more specific fields by a GS1 policy that is assigned to a specific menu item.

The generic GS1 setup allows only one value to be scanned at a time. Therefore, if you want to load multiple field values from a single scan, you must set up a GS1 policy for the relevant menu items.

For more information about GS1 policies, see the next section.

### Load the standard generic GS1 setup

The **GS1 generic setup** page lets you load a standard set of mappings between mobile device fields and standard application identifiers that are created by the default setup.

To establish the generic GS1 setup, go to **Warehouse management \> Setup \> GS1 \> GS1 generic setup**. Then select **Create default setup** to automatically assign a suitable application identifier to each field that is typically used by mobile device menu items.

> [!WARNING]
> If any generic GS1 setup already exists, the **Create default setup** command completely deletes it and loads the standard setup.

### Customize the standard generic GS1 setup

To customize the generic GS1 setup, follow these steps.

1. Go to **Warehouse management \> Setup \> GS1 \> GS1 generic setup**.
1. Follow one of these steps:

    - To create a new mapping: On the Action Pane, select **New**.
    - To edit an existing mapping: Select the mapping, and then, on the Action Pane, select **Edit**.

1. Set the following fields for the new or selected mapping:

    - **Field** – Select or enter the mobile app input field that the incoming value should be assigned to. The value isn't the display name that workers see. Instead, it's the key name that is assigned to the field in the underlying code. The default setup provides a collection of fields that are likely to be useful, and includes intuitive key names for each field and matching programmed functionality. However, you might have to talk to your development partners to find the correct selections for your implementation.
    - **Application identifier** – Select the applicable application identifier, as defined on the **GS1 application identifiers** page. The identifier establishes how the bar code will be interpreted and stored as a value for the named field. After you select an application identifier, the **Description** field shows the description of it.

## Set up GS1 policies that you can assign to mobile device menu items

The purpose of the GS1 standard is to enable workers to load several values when they scan a single bar code one time. To achieve this purpose, logistics managers must set up GS1 policies that tell the system how to interpret multi-value bar codes. Later, you can assign policies to mobile device menu items to control how a bar code will be interpreted when workers scan it while they are using a specific menu item.

If no GS1 policy is assigned to a menu item, the system can capture only a single value. This value is applied to the mobile app input that is selected when the worker takes the scan, as specified by the generic GS1 setup. If a GS1 policy is assigned to the menu item, the system still uses the generic GS1 setup to map the first bar code value to the selected field. However, it can then capture additional field values, as specified by the applicable policy.

### Load the standard specific GS1 policies

To get started quickly, you can load a set of GS1 policies. You can then extend or edit the policies later, as you require.

To load the standard application identifiers, follow these steps.

1. Go to **Warehouse management \> Setup \> GS1 \> GS1 policy**.
1. On the Action Pane, select **Create default setup**.

> [!WARNING]
> The **Create default setup** command deletes all currently defined policies and replaces them with the standard set of policies. However, after the default setup is loaded, you can customize the policies as you require.

### Set up custom specific GS1 policies

To set up and customize your GS1 policies, follow these steps.

1. Go to **Warehouse management \> Setup \> GS1 \> GS1 policy**.
1. Follow one of these steps:

    - To create a new policy: On the Action Pane, select **New**.
    - To edit an existing policy: Select the policy in the list pane.

1. On the header of the new or selected policy, set the following fields:

    - **Policy name** – Enter a name for the policy.
    - **Description** – Enter a short description of the policy.

1. On the FastTab below the header, map field names to application identifiers as required for the current policy. Use the buttons on the toolbar to add or remove rows as you require. For each row, set the following fields:

    - **Field** – Select or enter the mobile app input field that the incoming value should be assigned to. The value isn't the display name that workers see. Instead, it's the key name that is assigned to the field in the underlying code. The default setup provides a collection of fields that are likely to be useful, and includes intuitive key names for each field and matching programmed functionality. However, you might have to talk to your development partners to find the correct selections for your implementation.
    - **Application identifier** – Select the applicable application identifier, as defined on the **GS1 application identifiers** page. The identifier establishes how the bar code will be interpreted and stored as a value for the named field. After you select an application identifier, the **Description** field shows the description of it.
    - **Sorting** – Each multi-value bar code includes a series of application identifiers, each of which is followed by a value. The applicable GS1 policy identifies which application identifier is mapped to each database field. However, if a bar code uses the same application identifier more than once, the system uses the order in which application identifiers appear in the code to map them to fields. For rows that share an application identifier with one or more other rows, use this field to establish the order that the matching rows are processed in. The row that has the lowest sorting value will be processed first.

> [!NOTE]
> For bar codes that include more than one identical application identifier, you *must* use the **Sorting** field to establish the order of the fields.

## Assign GS1 policies to mobile device menu items

By default, all mobile device menu items provide input fields where workers can scan a single value, according to the generic GS1 setup. If you want workers to be able to scan more than one field value in a single scan for any mobile device menu item, you must assign a GS1 policy by following these steps.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. Create or open a menu item.
1. On the **General** FastTab, set the **GS1 policy** field to the policy that applies to the menu item.

## GS1 setup example

This example applies to a system where the GS1 options are set up in the following way:

- On the **Warehouse management parameters** page, the following global settings are established:

  - **FNC1 character:** *\]C1*
  - **Group separator:** *\~*

- On the **GS1 application identifiers** page, the following application identifiers are relevant to this example.

    | Application identifier | Description | Fixed length | Length | Type | Decimal |
    |---|---|---|---|---|---|
    | 01 | GTIN | Selected | 14 | Numeric | Cleared |
    | 10 | Batch number | Cleared | 20 | Alphanumeric | Cleared |
    | 17 | Expiry date | Selected | 6 | Date | Cleared |
    | 30 | Receiving quantity | Cleared | 8 | Numeric | Cleared |

- On the **GS1 generic setup** page, the following settings for the generic GS1 policy are relevant to this example.

    | Field | Application identifier | Description |
    |---|---|---|
    | ItemId | 01 | GTIN |

- On the **GS1 policy** page, there is policy where the **Policy name** field is set to *Purchase receiving*. This policy includes the following lines.

    | Field | Application identifier | Description | Sorting |
    |---|---|---|---|
    | ExpDate | 17 | Expiry date | 0 |
    | InventBatchId | 10 | Batch number | 0 |
    | Qty | 30 | Receiving quantity | 0 |

- On the **Mobile device menu items** page, there is a menu item that is named *Purchase receiving*. Its **GS1 policy** field is set to *Purchase receiving*.

After goods for a purchase order arrive at the warehouse, the worker follows these steps.

1. On the mobile device, select the **Purchase receiving** menu item.
1. Enter the purchase order number.
1. Select the **Item** field, and scan the following bar code: *\]C10100000012345678\~3030\~10b1\~17220215*.

Because of the settings that are established for this example, the system parses the scanned bar code in the following way.

| Field key | Application ID | Value | Note |
|---|---|---|---|
| ItemId | 01 | 00000012345678 | Because the worker scanned to the **Item** field, the first value in the bar code is mapped to that field. The mapping is taken from the GS1 generic setup. |
| Qty | 30 | 30 | Because several field values are being captured in a single scan, this mapping and all remaining mappings are taken from the GS1 policy that is assigned to the **Purchase receiving** menu item. This value is the quantity that was received. |
| InventBatchId | 10 | b1 | This value is the batch ID. |
| ExpDate | 17 | 220215 | The date format is YYMMDD. Therefore, the expiry date is February 15, 2022. |

The receipt is then registered, and the relevant database values are entered after the single scan.
