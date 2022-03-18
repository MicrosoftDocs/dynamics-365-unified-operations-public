---
# required metadata

title: Document routing layout for license plate labels
description: This topic describes how to use formatting methods to print values on labels.
author: perlynne
ms.date: 04/01/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: WHSLicensePlateLabel, WHSLicensePlateLabelBuildConfig, WHSLicensePlateLabel, WHSDocumentRoutingLayout
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: perlynne
ms.search.validFrom: 2012-04-01
ms.dyn365.ops.version: 10.0.10
---

# Document routing layout for license plate labels

[!include [banner](../includes/banner.md)]


The document routing layout defines the layout of license plate labels, and the data that is printed on them. You configure the printing trigger points when you set up mobile device menu items and work templates.

In a typical scenario, warehouse receiving clerks print license plate labels immediately after they record the contents of pallets that arrive in the receiving area. The physical labels are applied to the pallets. They can then be used for validation as part of the put-away process that follows and future outbound picking operations.

You can print highly complex labels, provided that the printing device can interpret the text that is sent to it. For example, a Zebra Programming Language (ZPL) layout that includes a bar code might resemble the following example.

```dos
^XA~TA000~JSN^LT0^MNW^MTD^PON^PMN^LH0,0^JMA^PR2,2~SD15^JUS^LRN^CI0^XZ
^XA
^MMT
^PW320
^LL0160
^LS0
^FT20,58^A0N,28,28^FH\^FDLabel:^FS
^FT20,81^AAN,18,10^FH\^FD$LicensePlateId$^FS
^BY1,3,17^FT20,106^BCN,,Y,N,N,A
^FD$LicensePlateId$^FS
^PQ1,,,Y^XZ
```

As part of the label printing process, the text `$LicensePlateId$` in this example will be replaced with a data value.

To see the values that will be printed, go to **Warehouse management \> Inquiries and reports \> License plate labels**.

Several widely available label generation tools can help you format the text for the label layout. Many of these tools support the `$FieldName$` format. In addition, Microsoft Dynamics 365 Supply Chain Management uses special formatting logic as part of the field mapping for the document routing layout.

## Turn on this feature for your system

If your system doesn't already include the features described in this topic, go to [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) and turn on the *Enhanced license plate label layouts* feature. (As of Supply Chain Management version 10.0.21, this feature is turned on by default. As of Supply Chain Management 10.0.25, this feature is mandatory and can't be turned off.)

## Custom number formats

You can customize the formatting of numerical field values that are printed by using codes that have the following format.

```dos
$FieldName:FormatString$
```

Here is an explanation of this format:

- `FieldName` is the name of the data field (such as **Qty**).
- `FormatString` defines how the data must be printed.

The following examples show how you can customize the work quantity (**Qty**) field:

- To always show four digits (by using zeros as placeholders), use `$Qty:0000$`. For example, if the quantity is 10, the label will show "0010."
- To always show two decimal places, use `$Qty:0.00$`. For example, if the quantity is 10, the label will show "10.00."

For a complete list of the available number format strings, see [Custom numeric format strings](/dotnet/standard/base-types/custom-numeric-format-strings).

## Custom string formats

You can remove the first characters of a string by using the following field and format code.

```dos
$FieldName:#..$
```

Here, `#` specifies the number of characters to skip. For example, to print a Serial Shipping Container Code (SSCC) license plate number that doesn't include the first two characters, use `$LicensePlateId:2..$`. In this case, the license plate number 0011111111111222221 will be printed as "11111111111222221."

## Custom date/time formats

The following example shows how you can control the format that is used to print dates.

```dos
$PrintedDate:dd-MM-yyyy$
```

In this example, the date April 30, 2020, will be printed as "30-04-2020."

For a complete list of the available date/time formats, see [Custom date and time format strings](/dotnet/standard/base-types/custom-date-and-time-format-strings).

## Print individual lines from multiline data

If a data field contains multiple lines (that is, lines that are separated by line breaks), you can print an individual line by using the following format.

```dos
$FieldName[#]$
```

Here, `#` is the line number that you want to print. (Use 1 for the first line.)

For example, your system has an `AdditionalAddress` field that stores the following multiline address:

Contoso Inc.  
123 Street Name  
Some City, Some State

You can print this address, one line at a time, by using the following codes.

| Code | Text that is printed |
|---|---|
| `$AdditionalAddress[1]$` | Contoso Inc. |
| `$AdditionalAddress[2]$` | 123 Street Name |
| `$AdditionalAddress[3]$` | Some City, Some State |

## Print and format from a display method

You can print from a display method by using the following format.

```dos
$DisplayMethod()$
```

You can combine this format with other types that were described earlier in this topic. For example, you have a display method that is named `DisplayListOfItemsNumbers()`, and you want to print the first item number of this method. In this case, you can use the following code.

```dos
$DisplayListOfItemsNumbers()[1]$
```

## More information about how to print labels

For more information about how to set up and print labels, see [Enable license plate label printing](tasks/license-plate-label-printing.md).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]