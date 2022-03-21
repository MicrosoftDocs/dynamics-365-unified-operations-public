---
title: GS1 bar code scanning
description: This topic describes how to set up GS1 bar codes and QR codes so that labels can be scanned in a warehouse.
author: Mirzaab
ms.date: 03/21/2022
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: mirzaab
ms.search.validFrom: 2021-08-02
ms.dyn365.ops.version: 10.0.25
---

# GS1 bar code scanning

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]
<!-- Preview until 10.0.25 GA -->

Warehouse workers often have to complete several tasks when they use a mobile device scanner to register movements of an item, palette, or container. These tasks can include both scanning bar codes and manually entering information on the mobile device. The bar codes use a company-specific format that you define and manage by using Microsoft Dynamics 365 Supply Chain Management.

GS1 bar codes (linear, such as GS1-128 and 2D, such as GS1 DataMatrix and GS1 QR code) for shipping labels were developed to provide a global standard for the exchange of data between companies. GS1 bar codes not only encode the data but also let you use a predefined list of *application identifiers* to define the meaning of the data. The GS1 standard defines the data format and the various kinds of data that it can be used to encode. Unlike older bar codes, GS1 bar codes can have multiple data elements. Therefore, a single bar code scan can capture several types of product information, such as the batch and the expiration date.

GS1 support in Supply Chain Management dramatically simplifies the scanning process in warehouses where pallets and containers are labeled by using bar codes in GS1 format. Warehouse workers can extract all the required information through a single scan of a GS1 bar code. By eliminating the need to do multiple scans and/or manually enter information, GS1 bar codes help reduce the time that is associated with tasks. At the same time, they also help improve accuracy.

Logistics managers must set up the required list of application identifiers and associate each of them with the appropriate mobile device menu items. The application identifiers can then be used across warehouses as a global setting for moving and packing purposes. Therefore, all shipping labels will take a unified form.

Unless otherwise stated, this topic uses the term *bar code* to refer to both linear (1D) bar codes and 2D bar codes.

## GS1 bar code format

GS1 General Specifications specify which symbologies can be used for GS1 bar codes and how to encode the data in the bar code. This section provides a short introduction to the topic. For full details, refer to the full document [GS1 General Specifications](https://www.gs1.org/docs/barcodes/GS1_General_Specifications.pdf) published by GS1. This document changes on a regular schedule, and the information on this page is up to date with GS1 General Specifications release 22.0.

The symbologies (bar code formats) that are used by GS1 bar codes are:

* Linear or 1D bar codes: GS1-128 and GS1 DataBar
* 2D bar codes: GS1 DataMatrix, GS1 QR Code and GS1 Dotcode

Notice that there are special mentions of GS1 in GS1-128, which is a special case of the ordinary Code-128 linear bar code, GS1 DataMatrix and GS1 QR Code. The difference between the GS1 version and the non-GS1 version is the presence of a special character (FNC1) as the first character in the bar code data. The presence of this FNC1 character is an indication that the data in the bar code should be formatted using GS1 specification.

The data in the bar code itself is composed of multiple data elements, all of them identified by an Application Identifier (AI) at the start of the field. Usually, the data is also represented under the bar code in a human readable format with the AI shown in parenthesis, for example: (01) 09521101530001 (17) 210119 (10) AB-123. This bar code contains three elements:

* AI 01 - the GS1 Global Trade Item Number (GTIN) of the item
* AI 17 - expiration date
* AI 10 - the batch number

Elements might have a predefined length or non-predefined (variable) length of data. There is a fixed list of Application Identifiers that have predefined lengths, with the reset of them having variable length, with the maximum length and format of data specified by GS1 AI list. For example, AI 01 has a predefined length of 16 characters (2 for the AI and 14 for the GTIN), AI 17 has a predefined length of 8 characters (again, 2 for the AI and 6 for the date), while AI 10 has a format of 2 numbers for the AI and up to 20 alphanumeric characters.

When putting together elements, if a new element follows a variable length element, a separator character must be used. This can either be the special FNC1 character or the character GS (non-printable character with ASCII code 29). After the last element, the separator should not be used. Likewise, the separator should not be used after elements with predefined length, but the presence of a separator is not a critical error.

If we take a look at the bar code data from the previous example of a bar code with AIs 01, 17 and 10, the data in a Code-128, QR Code or DataMatrix symbol would be encoded as `<FNC1>**01**09521101530001**17**210119**10**AB-123` (AIs highlighted). It is best practice to place the elements without predefined lengths at the end, as this removes the need for additional GS character, however the bar code could also have a different order of elements, where the separator is mandatory: `<FNC1>**01**09521101530001**10**AB-123<GS>**17**210119`.

### Dates and decimal numbers

Dates are always represented as YYMMDD, with the century of the year determined by GS1 specifications. Dates can only represent dates from 49 years in the past to 50 years in the future from the current year.

Some data elements contain decimal numbers, for example AIs 3100, 3101 ... 3105 represent a net weight in kilograms. These AIs have a predefined length of 10, so there are 6 numbers available for the quantity. The position of the decimal number is specified by the last number of the AI, so this family of AIs can also be represented as "310n". GS1 standard specifies that there must always be at least one number to the left of the decimal number, so in this case, the maximum number of decimal places allowed is 5.

An example of a string "123456" with different AIs:

* **3100**123456 -> 123456 (integer number)
* **3101**123456 -> 12345.6
* **3102**123456 -> 1234.56
* **3103**123456 -> 123.456
* **3104**123456 -> 12.3456
* **3105**123456 -> 1.23456

## How GS1 bar code scanning works with the Warehouse Mobile Application and Supply Chain Management

In order to scan GS1 bar codes, the warehouse worker uses a scanner built into or connected to a mobile device they use to execute their warehouse work. The scanner needs to transmit the scanned bar code to the WMA as keyboard events. This mode of operation is also known as a "keyboard wedge" or "wedge". The mobile application will then send the received text as-is to the SCM system. Upon receiving any input data, the system first checks whether the data begins with one of the configured prefixes which indicates to the system that the data is actually a GS1 bar code (see the Set up global GS1 options section for further details). If so, the system will use a GS1 parser to parse the scanned data and extract individual data elements according to their Application Identifiers. After the data has been parsed, either the current input field or multiple fields will be populated by the scanned data.

### Configuration of bar code scanner hardware and software

In order for Supply Chain Management to properly recognize and decode GS1 bar codes, the hardware scanner or supporting software should be configured to:

* add a prefix to the scanned bar codes that can be used by the system to recognize a GS1 bar code, and
* to convert the non-printable ASCII GS character (ASCII code 29 or hexadecimal 1D) to a printable character (for example, a tilde ~)

While you can choose to add any prefix to the scanned bar code, one option is to add an ISO/IEC 15424 symbology identifier, also known as AIM identifier. This is a three character identifier which starts with `]`, then one character identifying the symbology used and a number as a further modifier. For example, the AIM identifier `]C1` specifies a Code 128 bar code (because of the character `C`), with the modifier `1` specifying that there is a FNC1 character in the first position of the data. On the other hand, `]C0` is a Code 128 bar code with any other character as the first character of the data.

The five symbology identifiers that correspond to GS1 bar codes with AI elements are:

* `]C1` - Code 128 (`C`) with FNC1 in first position (`1`), also known as GS1-128
* `]e0` - GS1 DataBar
* `]d2` - DataMatrix (`d`) with ECC 200 and FNC1 in first position (`2`), also known as GS1 DataMatrix
* `]Q3` - QR Code (`Q`) Model 2 symbol with FNC1 in first position (`3`), also known as GS1 QR Code
* `]J1` - GS1 DotCode

If you choose to use these identifiers. then, in order to be compatible with non-GS1 bar codes, the scanners or scanning software should be configured to remove any identifiers that do not correspond to the GS1 identifiers. For example, scanning a "normal" Code 39 bar code would result in a prefix `]A0` being added. Since the system will not understand this prefix as one of the GS1 prefixes, it will interpret it as a data with unexpected results.

> [!NOTE]
> For convenience, the Warehouse Mobile Application (from version 2.0.17.0 onwards) will remove any AIM prefixes not listed above. This is to support cases where the customer is only able to configure the scanner to add the AIM prefix, but not to remove the unwanted ones.

### Single field scanning and multiple field scanning support

After the data has been parsed from the bar code, it will be fed into the mobile device flow's controls. There are two different methods for this that will be processed in turn:

1. *Single field scanning* (controlled by the GS1 generic setup, see [Establish the generic GS1 setup] later in the document) This method only fills the field where the bar code was scanned into. For example, if you scan the bar code `<FNC1>**01**09521101530001**17**210119**10**AB-123` when positioned in the item field, the GTIN `09521101530001` from the bar code would be filled into the current field. If instead you scan the same bar code when positioned in the Batch ID field, the batch number `AB-123` from the bar code would be filled in. This mode only requires the GS1 generic setup to be configured and works in general on all fields in all flows. If a bar code contains multiple elements, then it is still necessary to scan the bar code multiple times, as only one piece of the bar code will be filled into the mobile device flow at a time.
2. *Multiple field scanning* (controlled by GS1 policies linked to menu items, see [Set up GS1 policies that you can assign to mobile device menu items]) This method fills multiple fields when scanning one bar code by pushing additional data into the mobile device flow state. If the policy is configured to push the AI 01 into the control ItemId and AI 10 into the field InventBatchId, then scanning the bar code `<FNC1>**01**09521101530001**17**210119**10**AB-123` would push data for both variables at the same time. This would result in the system not prompting for the item and/or batch number in the flow.

> [!WARNING]
> The default GS1 policies have been tested to work without unexpected behavior, but customizing GS1 policies linked to menu items can lead to unexpected behavior of mobile device flows, as the flow might not expect some data to be available at a particular point of time.

## Turn on the GS1 feature

Before you can use this feature, it must be turned on in your system. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on. In the **Feature management** workspace, the feature is listed in the following way:

* **Module:** *Warehouse management*
* **Feature name:** *Scan GS1 bar codes*

## Turn on the Enhanced GS1 Parser feature

In addition to the *Scan GS1 bar codes*, administrators can turn on the feature *Enhanced GS1 Parser*. This feature enables the use of an improved implementation of the GS1 bar code parser, which has the following improvements:

* Follows the GS1 General Specification algorithm for symbol data parsing and validates that the data in the symbol is valid as per GS1 General Specifications.
* Does not require the setup of "maximum length of AI" and uses longest prefix matching from configured AIs.
* Easier configuration of decimal AIs by using "n" in the configuration to match any number, for example using configuration AI 310n instead of separate 3101, 3102, 3103... AIs.
* Solves the issue of incorrectly encoded data to be interpreted as field data.
* Comes as a separate class that can be reused in other contexts and enables the use of an extensibility point to manipulate scanned data before filling the flow fields.

## Set up global GS1 options

The **Warehouse management parameters** page provides a few settings that establish global GS1 options.

To set up global GS1 options, follow these steps.

1. Go to **Warehouse management \> Setup \> Warehouse management parameters**.
1. On the **Bar codes** FastTab, set the following fields:

    * **FNC1 Character**, **Datamatrix character**, **QR code character** - Specify characters that should be interpreted as a prefix for a GS1 bar code.
    * **Group separator** – Specify the character that replaces the ASCII Group Separator character.
    * **Maximum length of identifier** – Specify the maximum number of characters that is permitted for the application identifier. Not needed if **Enhanced GS1 Parser** feature is enabled.

> [!NOTE]
> Prefixes tell the system that a bar code is encoded according to the GS1 standard. Up to three prefixes (**FNC1 Character**, **Datamatrix character**, and **QR code character**) can be used simultaneously and for various purposes.

## GS1 Application Identifiers

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

    * To create a new identifier: On the Action Pane, select **New**.
    * To edit an existing identifier: Select the identifier, and then, on the Action Pane, select **Edit**.

1. Set the following fields for the new or selected identifier:

    * **Application identifier** – Enter the identification code for the application identifier. Typically, this code is a two-digit integer, but it can be longer. For decimal values, the last digit indicates the number of decimal places. For more information, see the description of the **Decimal** checkbox later in this list. If the **Enhanced GS1 Parser** feature is enabled, then you can create a single application identifier for all decimal place variants by putting the letter *n* as the last character in the application identifier.
    * **Description** – Enter a short description of the identifier.
    * **Fixed length** – Select this checkbox if values that are scanned by using this application identifier have a fixed number of characters. Clear this checkbox if the length of values is variable. In this case, you must indicate the end of the value by using the group separator character that you specified on the **Warehouse management parameters** page.
    * **Length** – Enter the maximum number of characters that can appear in the values that are scanned by using this application identifier. If the **Fixed length** checkbox is selected, exactly this number of characters is expected.
    * **Type** – Select the type of value that is scanned by using this application identifier (*Numeric*, *Alphanumeric*, or *Date*). Refer also to [Dates and decimal numbers](#dates-and-decimal-numbers) for more information on how dates and numbers are represented in bar code data.
    * **Decimal** – Select this checkbox if the value includes an implied decimal point. If this box is selected, the system will use the last digit of the application identifier to determine the number of decimal places. Refer also to [Dates and decimal numbers](#dates-and-decimal-numbers) for more information on how dates and numbers are represented in bar code data.

> [!WARNING]
> While the system will allow setting the **Fixed length** checkbox for any application identifier, it should only be used for the subset of application identifiers that have a predefined length as per GS1 General Specifications. The enhanced GS1 parser already contains the list of all application identifiers with predefined lengths.

> [!NOTE]
> The group separator that is specified on the **Warehouse management parameters** page is optional if a value that is followed by an application identifier has a fixed length.

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

    * To create a new mapping: On the Action Pane, select **New**.
    * To edit an existing mapping: Select the mapping, and then, on the Action Pane, select **Edit**.

1. Set the following fields for the new or selected mapping:

    * **Field** – Select or enter the mobile app input field that the incoming value should be assigned to. The value isn't the display name that workers see. Instead, it's the key name that is assigned to the field in the underlying code. The default setup provides a collection of fields that are likely to be useful, and includes intuitive key names for each field and matching programmed functionality. However, you might have to talk to your development partners to find the correct selections for your implementation.
    * **Application identifier** – Select the applicable application identifier, as defined on the **GS1 application identifiers** page. The identifier establishes how the bar code will be interpreted and stored as a value for the named field. After you select an application identifier, the **Description** field shows the description of it.

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

> [!WARNING]
> It is not guaranteed that any given GS1 policy will work with the mobile flow used. When configuring custom GS1 policies, customer is required to test the mobile device flow with different pieces of information scanned at different points in the flow to see whether the flow behaves as expected.

To set up and customize your GS1 policies, follow these steps.

1. Go to **Warehouse management \> Setup \> GS1 \> GS1 policy**.
1. Follow one of these steps:

    * To create a new policy: On the Action Pane, select **New**.
    * To edit an existing policy: Select the policy in the list pane.

1. On the header of the new or selected policy, set the following fields:

    * **Policy name** – Enter a name for the policy.
    * **Description** – Enter a short description of the policy.

1. On the FastTab below the header, map field names to application identifiers as required for the current policy. Use the buttons on the toolbar to add or remove rows as you require. For each row, set the following fields:

    * **Field** – Select or enter the mobile app input field that the incoming value should be assigned to. The value isn't the display name that workers see. Instead, it's the key name that is assigned to the field in the underlying code. The default setup provides a collection of fields that are likely to be useful, and includes intuitive key names for each field and matching programmed functionality. However, you might have to talk to your development partners to find the correct selections for your implementation.
    * **Application identifier** – Select the applicable application identifier, as defined on the **GS1 application identifiers** page. The identifier establishes how the bar code will be interpreted and stored as a value for the named field. After you select an application identifier, the **Description** field shows the description of it.
    * **Sorting** – Each multi-value bar code includes a series of application identifiers, each of which is followed by a value. The applicable GS1 policy identifies which application identifier is mapped to each database field. However, if a bar code uses the same application identifier more than once, the system uses the order in which application identifiers appear in the code to map them to fields. For rows that share an application identifier with one or more other rows, use this field to establish the order that the matching rows are processed in. The row that has the lowest sorting value will be processed first.

> [!NOTE]
> For bar codes that include more than one identical application identifier, you *must* use the **Sorting** field to establish the order of the fields.

## Assign GS1 policies to mobile device menu items

By default, all mobile device menu items provide input fields where workers can scan a single value, according to the generic GS1 setup. If you want workers to be able to scan more than one field value in a single scan for any mobile device menu item, you must assign a GS1 policy by following these steps.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. Create or open a menu item.
1. On the **General** FastTab, set the **GS1 policy** field to the policy that applies to the menu item.

## GS1 setup example

This example applies to a system where the GS1 options are set up in the following way:

* On the **Warehouse management parameters** page, the following global settings are established:

  * **FNC1 character:** *\]C1*
  * **Group separator:** *\~*

* On the **GS1 application identifiers** page, the following application identifiers are relevant to this example.

    | Application identifier | Description | Fixed length | Length | Type | Decimal |
    |---|---|---|---|---|---|
    | 01 | GTIN | Selected | 14 | Numeric | Cleared |
    | 10 | Batch number | Cleared | 20 | Alphanumeric | Cleared |
    | 17 | Expiry date | Selected | 6 | Date | Cleared |
    | 30 | Receiving quantity | Cleared | 8 | Numeric | Cleared |

* On the **GS1 generic setup** page, the following settings for the generic GS1 policy are relevant to this example.

    | Field | Application identifier | Description |
    |---|---|---|
    | ItemId | 01 | GTIN |

* On the **GS1 policy** page, there is policy where the **Policy name** field is set to *Purchase receiving*. This policy includes the following lines.

    | Field | Application identifier | Description | Sorting |
    |---|---|---|---|
    | ExpDate | 17 | Expiry date | 0 |
    | InventBatchId | 10 | Batch number | 0 |
    | Qty | 30 | Receiving quantity | 0 |

* On the **Mobile device menu items** page, there is a menu item that is named *Purchase receiving*. Its **GS1 policy** field is set to *Purchase receiving*.

After goods for a purchase order arrive at the warehouse, the worker follows these steps.

1. On the mobile device, select the **Purchase receiving** menu item.
2. Enter the purchase order number.
3. Select the **Item** field, and scan the following bar code: *\]C10100000012345678\~3030\~10b1\~17220215*.

Because of the settings that are established for this example, the system parses the scanned bar code in the following way.

| Field key | Application ID | Value | Note |
|---|---|---|---|
| ItemId | 01 | 00000012345678 | Because the worker scanned to the **Item** field, the first value in the bar code is mapped to that field. The mapping is taken from the GS1 generic setup. |
| Qty | 30 | 30 | Because several field values are being captured in a single scan, this mapping and all remaining mappings are taken from the GS1 policy that is assigned to the **Purchase receiving** menu item. This value is the quantity that was received. |
| InventBatchId | 10 | b1 | This value is the batch ID. |
| ExpDate | 17 | 220215 | The date format is YYMMDD. Therefore, the expiry date is February 15, 2022. |

The receipt is then registered, and the relevant database values are entered after the single scan.
