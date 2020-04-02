---
# required metadata

title: Document routing layout for license plate labels
description: Describes how to use formatting methods to print values on labels.
author: perlynne
manager: tfehr
ms.date: 04/01/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: perlynne
ms.search.validFrom: 2012-04-01
ms.dyn365.ops.version: Release 10.0.11
---

# Document routing layout for license plate labels

[!include [banner](../includes/banner.md)]

The layout and data printed for license plate labels is defined by the document routing layout. You configure the printing trigger points when setting up mobile device menu items and work templates.

In a typical scenario, warehouse receiving clerks print license plate labels right after they record the content of a pallet arriving in the receiving area. The physical label is then applied to the pallet and used for validation as part of the following put-away process and future outbound picking operations.

You can print highly complex labels provided the printing device can understand the text being sent. For example, a Zebra Programming Language (ZPL) layout with a barcode might look like this:

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

The text `$LicensePlateId$` will be replaced with a data value as part of the label printing process.

You can see the values to be printed by going to **Warehouse management \> Inquiries and reports \> License plate labels**.

You can use any of several common label generation tools to help with the text format for the label layout (including many that support the `$FieldName$` format). In addition, Supply Chain Management also uses special formatting logic as part of the document routing layout field mapping.

## Custom number formats

You can customize the formatting of your printed numerical field values using codes with the following format:

```dos
$FieldName:FormatString$
```

Where:

- `FieldName` is the data field (such as `Qty`)
- `FormatString` defines how the data must be printed.

Here are two examples of how to customize the work quantity (Qty) field:

- To always show four digits (with zero place holders), use `$Qty:0000$`. So, for example, if the quantity is 10, then the label will show "0010".
- To always show two decimal places, use `$Qty:0.00$`.  So, for example, if the quantity is 10, then the label will show "10.00".

For a complete list of available number format strings, see [Custom numeric format strings](https://docs.microsoft.com/dotnet/standard/base-types/custom-numeric-format-strings).

## Custom string formats

You can remove the first characters of a string using the following field and format code:

```dos
$FieldName:#..$
```

Where `#` specifies the number of characters to skip. So, for example, to print an SSCC license plate number that doesn't includes the first two characters, you would use `$LicensePlateId:2..$`. In this case, the license plate number "0011111111111222221" would print as "11111111111222221".

## Custom date/time formats

Here is an example of how to control the format used for printings dates:

```dos
$PrintedDate:dd-MM-yyyy$
```

In this example, the date "April 30, 2020" would print as "30-04-2020".

For a complete list of available date/time formats, see [Custom date and time format strings](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings).

## Print individual lines from multiline data

Use the following format to print an individual line from a data field that contains multiple lines (with line breaks):

```dos
$FieldName[#]$
```

Where `#` is the line number that you want to print (starting with 1).

For example, suppose your system includes a field named `AdditionalAddress`, which stores a multiline address such as:

Contoso Inc.  
123 Street Name  
Some City, Some State

You can print this, one line at a time, using the following codes:

| Code | Prints as |
| --- | --- |
| `$AdditionalAddress[1]$` | Contoso Inc. |
| `$AdditionalAddress[2]$` | 123 Street Name  |
| `$AdditionalAddress[3]$` | Some City, Some State |

## Print and format from a display method

Use the following format to print from a display method:

```dos
$DisplayMethod()$
```

You can combine this with other types of formatting described previously in this topic.

For example, if you have a display method called `DisplayListOfItemsNumbers()` and would like to print the first item number of this method, you could use the following code:

```dos
$DisplayListOfItemsNumbers()[1]$
```

## More information about printing labels

For more information about how to set up and print labels, see [Enable license plate label printing](tasks/license-plate-label-printing.md).
