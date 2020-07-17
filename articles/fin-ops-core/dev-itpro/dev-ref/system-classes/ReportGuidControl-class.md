---
title: ReportGuidControl class
description: This topic describes the ReportGuidControl class.
author: robinarh
manager: tonyafehr
ms.date: 06/25/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

audience: Developer
ms.reviewer: rhaertle
ms.search.scope: Operations
ms.search.region: Global
ms.author: rhaertle
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Class ReportGuidControl

[!include [banner](../../includes/banner.md)]

```xpp
class ReportGuidControl extends ReportControl
```

The ReportGuidControl class enables you to create, read, update, and delete X++ code and metadata.

## Remarks

## Examples

## Methods

| Method                                                                   | Description                                                                                                                                   |
|--------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| public int alignment(\[int value\])                                      |                                                                                                                                               |
| public int arrayIndex(\[int value\])                                     |                                                                                                                                               |
| public boolean autoDeclaration(\[boolean value\])                        | Determines whether the system can declare a member variable that has the same name as the control.                                            |
| public int backgroundColor(\[int value\])                                | Gets or sets the background color of the control.                                                                                             |
| public int backStyle(\[int value\])                                      | Determines whether the control background can be transparent.                                                                                |
| public int bold(\[int value\])                                           | Gets or sets the weight of font that is used to output text in the control.                                                                   |
| public int bottomMarginAndFrame()                                        |                                                                                                                                               |
| public int bottomMarginMode(\[int value\])                               |                                                                                                                                               |
| public str bottomMarginStr(\[str value\])                                |                                                                                                                                               |
| public Units bottomMarginUnit(\[Units value\])                           |                                                                                                                                               |
| public Real bottomMarginValue(\[Real value\])                            |                                                                                                                                               |
| public int changeLabelCase(\[int value\])                                |                                                                                                                                               |
| public int characterSet(\[int value\])                                   | Gets or sets the character set of the font.                                                                                                   |
| public int colorScheme(\[int value\])                                    | Gets or sets the color scheme of the control.                                                                                                 |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\]) | Gets or sets the configuration key that is assigned to the control.                                                                           |
| public ReportFieldType controlType()                                     |                                                                                                                                               |
| public str cssClass(\[str value\])                                       |                                                                                                                                               |
| public FieldId dataField(\[FieldId value\])                              |                                                                                                                                               |
| public str dataMethod(\[str value\])                                     |                                                                                                                                               |
| public int delete()                                                      |                                                                                                                                               |
| public str effectiveFont()                                               |                                                                                                                                               |
| public ExtendedTypeId extendedDataType(\[ExtendedTypeId value\])         |                                                                                                                                               |
| public str font(\[str value\])                                           | Gets or sets the name of the font for the control to use.                                                                                     |
| public str fontInfoPrinter()                                             |                                                                                                                                               |
| public int fontInfoPrinterAscent()                                       |                                                                                                                                               |
| public int fontInfoPrinterDescent()                                      |                                                                                                                                               |
| public int fontInfoPrinterExtLead()                                      |                                                                                                                                               |
| public int fontInfoPrinterHeight()                                       |                                                                                                                                               |
| public int fontInfoPrinterIntLead()                                      |                                                                                                                                               |
| public str fontInfoScreen()                                              |                                                                                                                                               |
| public int fontInfoScreenAscent()                                        |                                                                                                                                               |
| public int fontInfoScreenDescent()                                       |                                                                                                                                               |
| public int fontInfoScreenExtLead()                                       |                                                                                                                                               |
| public int fontInfoScreenHeight()                                        |                                                                                                                                               |
| public int fontInfoScreenIntLead()                                       |                                                                                                                                               |
| public int fontSize(\[int value\])                                       | Gets or sets the size of the font for the control to use.                                                                                     |
| public int foregroundColor(\[int value\])                                | Gets or sets the text color for the control to use.                                                                                           |
| public int height100mm(\[int heightExclBorder\])                         |                                                                                                                                               |
| public int height100mmInclBorder(\[int heightInclBorder\])               |                                                                                                                                               |
| public int heightMode(\[int value\])                                     | Gets or sets a calculation mode for the height of the control.                                                                                |
| public int heightOfWordWrappedString100mm(str string)                    |                                                                                                                                               |
| public str heightStr(\[str value\])                                      |                                                                                                                                               |
| public Units heightUnit(\[Units value\])                                 |                                                                                                                                               |
| public Real heightValue(\[Real value\])                                  | Gets or sets the height of the control.                                                                                                       |
| public boolean italic(\[boolean value\])                                 |                                                                                                                                               |
| public str label(\[str value\])                                          | Gets or sets the label for a control.                                                                                                         |
| public int labelBold(\[int value\])                                      |                                                                                                                                               |
| public int labelCharacterSet(\[int value\])                              |                                                                                                                                               |
| public str labelCssClass(\[str value\])                                  |                                                                                                                                               |
| public str labelFont(\[str value\])                                      |                                                                                                                                               |
| public int labelFontSize(\[int value\])                                  |                                                                                                                                               |
| public boolean labelItalic(\[boolean value\])                            |                                                                                                                                               |
| public LineType labelLineBelow(\[LineType value\])                       |                                                                                                                                               |
| public LineThickness labelLineThickness(\[LineThickness value\])         |                                                                                                                                               |
| public int labelPosition(\[int value\])                                  |                                                                                                                                               |
| public int labelTabLeader(\[int value\])                                 |                                                                                                                                               |
| public boolean labelUnderline(\[boolean value\])                         |                                                                                                                                               |
| public int labelWidthMode(\[int value\])                                 |                                                                                                                                               |
| public str labelWidthStr(\[str value\])                                  |                                                                                                                                               |
| public Units labelWidthUnit(\[Units value\])                             |                                                                                                                                               |
| public Real labelWidthValue(\[Real value\])                              |                                                                                                                                               |
| public int left100mm(\[int leftExclBorder\])                             |                                                                                                                                               |
| public int left100mmInclBorder(\[int leftInclBorder\])                   |                                                                                                                                               |
| public int leftMarginAnFrame()                                           |                                                                                                                                               |
| public int leftMarginMode(\[int value\])                                 |                                                                                                                                               |
| public str leftMarginStr(\[str value\])                                  |                                                                                                                                               |
| public Units leftMarginUnit(\[Units value\])                             |                                                                                                                                               |
| public Real leftMarginValue(\[Real value\])                              |                                                                                                                                               |
| public int leftMode(\[int value\])                                       |                                                                                                                                               |
| public str leftStr(\[str value\])                                        |                                                                                                                                               |
| public Units leftUnit(\[Units value\])                                   |                                                                                                                                               |
| public Real leftValue(\[Real value\])                                    |                                                                                                                                               |
| public LineType lineAbove(\[LineType value\])                            |                                                                                                                                               |
| public LineType lineBelow(\[LineType value\])                            |                                                                                                                                               |
| public LineType lineLeft(\[LineType value\])                             | Gets or sets the type of line that is used as the left border of a section.                                                                   |
| public LineType lineRight(\[LineType value\])                            |                                                                                                                                               |
| public str menuItemLabel(\[str value\])                                  |                                                                                                                                               |
| public str menuItemName(\[str value\])                                   |                                                                                                                                               |
| public MenuItemType menuItemType(\[MenuItemType value\])                 |                                                                                                                                               |
| public str modelFieldName(\[str value\])                                 |                                                                                                                                               |
| public str name(\[str value\])                                           | Gets or sets the name that is used in the code to identify a form, report, table, query, or other application object. |
| public int numberOfLines(int height100mm)                                |                                                                                                                                               |
| public int position(\[int value\])                                       |                                                                                                                                               |
| public str previewInfo(str string)                                       |                                                                                                                                               |
| public int previewXCompensation100mm(str string)                         |                                                                                                                                               |
| public int right100mm()                                                  |                                                                                                                                               |
| public int right100mmInclBorder()                                        |                                                                                                                                               |
| public int rightMarginAndFrame()                                         |                                                                                                                                               |
| public int rightMarginMode(\[int value\])                                |                                                                                                                                               |
| public str rightMarginStr(\[str value\])                                 |                                                                                                                                               |
| public Units rightMarginUnit(\[Units value\])                            |                                                                                                                                               |
| public Real rightMarginValue(\[Real value\])                             |                                                                                                                                               |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                |                                                                                                                                               |
| public str setHeightGetText(int lines, str string)                       |                                                                                                                                               |
| public boolean showLabel(\[boolean value\])                              |                                                                                                                                               |
| public TableId table(\[TableId value\])                                  | Gets or sets the table ID associated with the object.                                                                                         |
| public LineThickness thickness(\[LineThickness value\])                  |                                                                                                                                               |
| public int top100mm(\[int topExclBorder\])                               |                                                                                                                                               |
| public int top100mmInclBorder(\[int topInclBorder\])                     |                                                                                                                                               |
| public int topMarginAndFrame()                                           |                                                                                                                                               |
| public int topMarginMode(\[int value\])                                  |                                                                                                                                               |
| public str topMarginStr(\[str value\])                                   |                                                                                                                                               |
| public Units topMarginUnit(\[Units value\])                              |                                                                                                                                               |
| public Real topMarginValue(\[Real value\])                               |                                                                                                                                               |
| public int topMode(\[int value\])                                        |                                                                                                                                               |
| public str topStr(\[str value\])                                         |                                                                                                                                               |
| public Units topUnit(\[Units value\])                                    |                                                                                                                                               |
| public Real topValue(\[Real value\])                                     |                                                                                                                                               |
| public boolean underline(\[boolean value\])                              |                                                                                                                                               |
| public boolean visible(\[boolean value\])                                |                                                                                                                                               |
| public str webMenuItemName(\[str value\])                                |                                                                                                                                               |
| public WebMenuItemType webMenuItemType(\[WebMenuItemType value\])        |                                                                                                                                               |
| public str webTarget(\[str value\])                                      |                                                                                                                                               |
| public int width100mm(\[int widthExclBorder\])                           |                                                                                                                                               |
| public int width100mmInclBorder(\[int widthInclBorder\])                 |                                                                                                                                               |
| public int widthMode(\[int value\])                                      | Gets or sets the calculation mode of the width of the control.                                                                                |
| public int widthOfString100mm(str string)                                |                                                                                                                                               |
| public str widthStr(\[str value\])                                       |                                                                                                                                               |
| public Units widthUnit(\[Units value\])                                  |                                                                                                                                               |
| public Real widthValue(\[Real value\])                                   | Gets or sets the width of the control.                                                                                                        |
| public void width(Real value, Units unit)                                | Gets or sets the width of the control.                                                                                                        |
| public void topMargin(Real value, Units unit)                            |                                                                                                                                               |
| public void bottomMargin(Real value, Units unit)                         |                                                                                                                                               |
| public void rightMargin(Real value, Units unit)                          |                                                                                                                                               |
| public void leftMargin(Real value, Units unit)                           |                                                                                                                                               |
| public void show()                                                       |                                                                                                                                               |
| public void hide()                                                       |                                                                                                                                               |
| public void top(Real value, Units unit)                                  |                                                                                                                                               |
| public void left(Real value, Units unit)                                 |                                                                                                                                               |
| public void labelWidth(Real value, Units unit)                           |                                                                                                                                               |
| public void height(Real value, Units unit)                               | Gets or sets the height of the control.                                                                                                       |

## Method alignment

```xpp
public int alignment([int value])
```

### Parameters - alignment

value  

### Return Value - alignment

## Method arrayIndex

```xpp
public int arrayIndex([int value])
```

### Parameters - arrayIndex

value  

### Return Value - arrayIndex

## Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

```xpp
public boolean autoDeclaration([boolean value])
```

### Parameters - autoDeclaration

value  

### Return Value - autoDeclaration

true if the member variable can be declared for this control; otherwise, false.

### Remarks - autoDeclaration

Controls cannot have identical names.

## Method backgroundColor

Gets or sets the background color of the control.

```xpp
public int backgroundColor([int value])
```

### Parameters - backgroundColor

value  

### Return Value - backgroundColor

An integer that contains a packed RGB color.

### Remarks - backgroundColor

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

## Method backStyle

Determines whether the control background can be transparent.

```xpp
public int backStyle([int value])
```

### Parameters - backStyle

value  

### Return Value - backStyle

1 if the control background can be transparent; otherwise, 0.

## Method bold

Gets or sets the weight of font that is used to output text in the control.

```xpp
public int bold([int value])
```

### Parameters - bold

value  

### Return Value - bold

An integer value between zero and nine, inclusive.

### Remarks - bold

The integer that is returned contains the weight of the font as follows:

-   0 Use the default font weight.
-   1 Thin.
-   2 Extra-light.
-   3 Light.
-   4 Normal.
-   5 Medium.
-   6 Semibold.
-   7 Bold.
-   8 Extra-bold.
-   9 Heavy.

## Method bottomMarginAndFrame

```xpp
public int bottomMarginAndFrame()
```

### Return Value - bottomMarginAndFrame

## Method bottomMarginMode

```xpp
public int bottomMarginMode([int value])
```

### Parameters - bottomMarginMode

value  

### Return Value - bottomMarginMode

## Method bottomMarginStr

```xpp
public str bottomMarginStr([str value])
```

### Parameters - bottomMarginStr

value  

### Return Value - bottomMarginStr

## Method bottomMarginUnit

```xpp
public Units bottomMarginUnit([Units value])
```

### Parameters - bottomMarginUnit

value  

### Return Value - bottomMarginUnit

## Method bottomMarginValue

```xpp
public Real bottomMarginValue([Real value])
```

### Parameters - bottomMarginValue

value  

### Return Value - bottomMarginValue

## Method changeLabelCase

```xpp
public int changeLabelCase([int value])
```

### Parameters - changeLabelCase

value  

### Return Value - changeLabelCase

## Method characterSet

Gets or sets the character set of the font.

```xpp
public int characterSet([int value])
```

### Parameters - characterSet

value  

### Return Value - characterSet

An integer value that indicates the character set of the font.

### Remarks - characterSet

The values for the integer that is returned indicate the character set according to the following table:

| Value. | Description.         |
|--------|----------------------|
| 0      | ANSI\_CHARSET        |
| 1      | DEFAULT\_CHARSET     |
| 2      | SYMBOL\_CHARSET      |
| 77     | MAC\_CHARSET         |
| 128    | SHIFTJIS\_CHARSET    |
| 129    | HANGUL\_CHARSET      |
| 134    | GB2312\_CHARSET      |
| 136    | CHINESEBIG5\_CHARSET |
| 161    | GREEK\_CHARSET       |
| 162    | TURKISH\_CHARSET     |
| 163    | VIETNAMESE\_CHARSET  |
| 186    | BALTIC\_CHARSET      |
| 204    | RUSSIAN\_CHARSET     |
| 238    | EASTEUROPE\_CHARSET  |
| 255    | OEM\_CHARSET         |

The value in the following table is for the Korean language edition of Microsoft Windows.

| Value. | Description.   |
|--------|----------------|
| 130    | JOHAB\_CHARSET |

The values in the following table are for the Middle East language edition of Microsoft Windows.

| Value. | Description.    |
|--------|-----------------|
| 177    | HEBREW\_CHARSET |
| 178    | ARABIC\_CHARSET |

The value in the following table is for the Thai language edition of Microsoft Windows.

| Value. | Description.  |
|--------|---------------|
| 222    | THAI\_CHARSET |

The default character set is set to a value, depending on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET. For more information, see the LOGFONT structure on the [MSDN website](https://go.microsoft.com/fwlink/?LinkID=85972).

## Method colorScheme

Gets or sets the color scheme of the control.

```xpp
public int colorScheme([int value])
```

### Parameters - colorScheme

value  

### Return Value - colorScheme

An integer between zero and two, inclusive.

### Remarks - colorScheme

The color scheme is defined according to the following table:

| Value. | Style.                        |
|--------|-------------------------------|
| 0      | Default.                      |
| 1      | The Microsoft Windows palette. |
| 2      | The true-color scheme.        |

## Method configurationKey

Gets or sets the configuration key that is assigned to the control.

```xpp
public ConfigurationKeyId configurationKey([ConfigurationKeyId value])
```

### Parameters - configurationKey

value  

### Return Value - configurationKey

The identifier of the configuration key that is assigned to the control.

### Remarks - configurationKey

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

## Method controlType

```xpp
public ReportFieldType controlType()
```

### Return Value - controlType

## Method cssClass

```xpp
public str cssClass([str value])
```

### Parameters - cssClass

value  

### Return Value - cssClass

## Method dataField

```xpp
public FieldId dataField([FieldId value])
```

### Parameters - dataField

value  

### Return Value - dataField

## Method dataMethod

```xpp
public str dataMethod([str value])
```

### Parameters - dataMethod

value  

### Return Value - dataMethod

## Method delete

```xpp
public int delete()
```

### Return Value - delete

## Method effectiveFont

```xpp
public str effectiveFont()
```

### Return Value - effectiveFont

## Method extendedDataType

```xpp
public ExtendedTypeId extendedDataType([ExtendedTypeId value])
```

### Parameters - extendedDataType

value  

### Return Value - extendedDataType

## Method font

Gets or sets the name of the font for the control to use.

```xpp
public str font([str value])
```

### Parameters - font

value  

### Return Value - font

The name of the font to use, such as Tahoma or Verdana.

## Method fontInfoPrinter

```xpp
public str fontInfoPrinter()
```

### Return Value - fontInfoPrinter

## Method fontInfoPrinterAscent

```xpp
public int fontInfoPrinterAscent()
```

### Return Value - fontInfoPrinterAscent

## Method fontInfoPrinterDescent

```xpp
public int fontInfoPrinterDescent()
```

### Return Value - fontInfoPrinterDescent

## Method fontInfoPrinterExtLead

```xpp
public int fontInfoPrinterExtLead()
```

### Return Value - fontInfoPrinterExtLead

## Method fontInfoPrinterHeight

```xpp
public int fontInfoPrinterHeight()
```

### Return Value - fontInfoPrinterHeight

## Method fontInfoPrinterIntLead

```xpp
public int fontInfoPrinterIntLead()
```

### Return Value - fontInfoPrinterIntLead

## Method fontInfoScreen

```xpp
public str fontInfoScreen()
```

### Return Value - fontInfoScreen

## Method fontInfoScreenAscent

```xpp
public int fontInfoScreenAscent()
```

### Return Value - fontInfoScreenAscent

## Method fontInfoScreenDescent

```xpp
public int fontInfoScreenDescent()
```

### Return Value - fontInfoScreenDescent

## Method fontInfoScreenExtLead

```xpp
public int fontInfoScreenExtLead()
```

### Return Value - fontInfoScreenExtLead

## Method fontInfoScreenHeight

```xpp
public int fontInfoScreenHeight()
```

### Return Value - fontInfoScreenHeight

## Method fontInfoScreenIntLead

```xpp
public int fontInfoScreenIntLead()
```

### Return Value - fontInfoScreenIntLead

## Method fontSize

Gets or sets the size of the font for the control to use.

```xpp
public int fontSize([int value])
```

### Parameters - fontSize

value  

### Return Value - fontSize

The height of the font in points.

## Method foregroundColor

Gets or sets the text color for the control to use.

```xpp
public int foregroundColor([int value])
```

### Parameters - foregroundColor

value  

### Return Value - foregroundColor

An integer that contains a packed RGB color.

### Remarks - foregroundColor

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

## Method height100mm

```xpp
public int height100mm([int heightExclBorder])
```

### Parameters - height100mm

heightExclBorder  

### Return Value - height100mm

## Method height100mmInclBorder

```xpp
public int height100mmInclBorder([int heightInclBorder])
```

### Parameters - height100mmInclBorder

heightInclBorder  

### Return Value - height100mmInclBorder

## Method heightMode

Gets or sets a calculation mode for the height of the control.

```xpp
public int heightMode([int value])
```

### Parameters - heightMode

value  

### Return Value - heightMode

The calculation mode.

### Remarks - heightMode

Calculate the height according to the following table:

| Mode.          | Height Calculation.                                                                       |
|----------------|-------------------------------------------------------------------------------------------|
| Exact.         | The exact height in pixels of the controls is used.                                       |
| Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height. | The layout of the form determines the height of the control.                              |

The height of the control might change when the mode is set to auto or column height.

## Method heightOfWordWrappedString100mm

```xpp
public int heightOfWordWrappedString100mm(str string)
```

### Parameters - heightOfWordWrappedString100mm

string  

### Return Value - heightOfWordWrappedString100mm

## Method heightStr

```xpp
public str heightStr([str value])
```

### Parameters - heightStr

value  

### Return Value - heightStr

## Method heightUnit

```xpp
public Units heightUnit([Units value])
```

### Parameters - heightUnit

value  

### Return Value - heightUnit

## Method heightValue

Gets or sets the height of the control.

```xpp
public Real heightValue([Real value])
```

### Parameters - heightValue

value  

### Return Value - heightValue

The height in pixels.

### Remarks - heightValue

The height of the control is not changed unless the exact height calculation mode is used.

## Method italic

```xpp
public boolean italic([boolean value])
```

### Parameters - italic

value  

### Return Value - italic

## Method label

Gets or sets the label for a control.

```xpp
public str label([str value])
```

### Parameters - label

value  

### Return Value - label

The current value of the label string.

### Remarks - label

The label determines which text is displayed in the control or adjacent to it. The label property value cannot exceed 250 characters.

## Method labelBold

```xpp
public int labelBold([int value])
```

### Parameters - labelBold

value  

### Return Value - labelBold

## Method labelCharacterSet

```xpp
public int labelCharacterSet([int value])
```

### Parameters - labelCharacterSet

value  

### Return Value - labelCharacterSet

## Method labelCssClass

```xpp
public str labelCssClass([str value])
```

### Parameters - labelCssClass

value  

### Return Value - labelCssClass

## Method labelFont

```xpp
public str labelFont([str value])
```

### Parameters - labelFont

value  

### Return Value - labelFont

## Method labelFontSize

```xpp
public int labelFontSize([int value])
```

### Parameters - labelFontSize

value  

### Return Value - labelFontSize

## Method labelItalic

```xpp
public boolean labelItalic([boolean value])
```

### Parameters - labelItalic

value  

### Return Value - labelItalic

## Method labelLineBelow

```xpp
public LineType labelLineBelow([LineType value])
```

### Parameters - labelLineBelow

value  

### Return Value - labelLineBelow

## Method labelLineThickness

```xpp
public LineThickness labelLineThickness([LineThickness value])
```

### Parameters - labelLineThickness

value  

### Return Value - labelLineThickness

## Method labelPosition

```xpp
public int labelPosition([int value])
```

### Parameters - labelPosition

value  

### Return Value - labelPosition

## Method labelTabLeader

```xpp
public int labelTabLeader([int value])
```

### Parameters - labelTabLeader

value  

### Return Value - labelTabLeader

## Method labelUnderline

```xpp
public boolean labelUnderline([boolean value])
```

### Parameters - labelUnderline

value  

### Return Value - labelUnderline

## Method labelWidthMode

```xpp
public int labelWidthMode([int value])
```

### Parameters - labelWidthMode

value  

### Return Value - labelWidthMode

## Method labelWidthStr

```xpp
public str labelWidthStr([str value])
```

### Parameters - labelWidthStr

value  

### Return Value - labelWidthStr

## Method labelWidthUnit

```xpp
public Units labelWidthUnit([Units value])
```

### Parameters - labelWidthUnit

value  

### Return Value - labelWidthUnit

## Method labelWidthValue

```xpp
public Real labelWidthValue([Real value])
```

### Parameters - labelWidthValue

value  

### Return Value - labelWidthValue

## Method left100mm

```xpp
public int left100mm([int leftExclBorder])
```

### Parameters - left100mm

leftExclBorder  

### Return Value - left100mm

## Method left100mmInclBorder

```xpp
public int left100mmInclBorder([int leftInclBorder])
```

### Parameters - left100mmInclBorder

leftInclBorder  

### Return Value - left100mmInclBorder

## Method leftMarginAnFrame

```xpp
public int leftMarginAnFrame()
```

### Return Value - leftMarginAnFrame

## Method leftMarginMode

```xpp
public int leftMarginMode([int value])
```

### Parameters - leftMarginMode

value  

### Return Value - leftMarginMode

## Method leftMarginStr

```xpp
public str leftMarginStr([str value])
```

### Parameters - leftMarginStr

value  

### Return Value - leftMarginStr

## Method leftMarginUnit

```xpp
public Units leftMarginUnit([Units value])
```

### Parameters - leftMarginUnit

value  

### Return Value - leftMarginUnit

## Method leftMarginValue

```xpp
public Real leftMarginValue([Real value])
```

### Parameters - leftMarginValue

value  

### Return Value - leftMarginValue

## Method leftMode

```xpp
public int leftMode([int value])
```

### Parameters - leftMode

value  

### Return Value - leftMode

## Method leftStr

```xpp
public str leftStr([str value])
```

### Parameters - leftStr

value  

### Return Value - leftStr

## Method leftUnit

```xpp
public Units leftUnit([Units value])
```

### Parameters - leftUnit

value  

### Return Value - leftUnit

## Method leftValue

```xpp
public Real leftValue([Real value])
```

### Parameters - leftValue

value  

### Return Value - leftValue

## Method lineAbove

```xpp
public LineType lineAbove([LineType value])
```

### Parameters - lineAbove

value  

### Return Value - lineAbove

## Method lineBelow

```xpp
public LineType lineBelow([LineType value])
```

### Parameters - lineBelow

value  

### Return Value - lineBelow

## Method lineLeft

Gets or sets the type of line that is used as the left border of a section.

```xpp
public LineType lineLeft([LineType value])
```

### Parameters - lineLeft

value  

### Return Value - lineLeft

The type of line that is used as the left border.

## Method lineRight

```xpp
public LineType lineRight([LineType value])
```

### Parameters - lineRight

value  

### Return Value - lineRight

## Method menuItemLabel

```xpp
public str menuItemLabel([str value])
```

### Parameters - menuItemLabel

value  

### Return Value - menuItemLabel

## Method menuItemName

```xpp
public str menuItemName([str value])
```

### Parameters - menuItemName

value  

### Return Value - menuItemName

## Method menuItemType

```xpp
public MenuItemType menuItemType([MenuItemType value])
```

### Parameters - menuItemType

value  

### Return Value - menuItemType

## Method modelFieldName

```xpp
public str modelFieldName([str value])
```

### Parameters - modelFieldName

value  

### Return Value - modelFieldName

## Method name

Gets or sets the name that is used in the code to identify a form, report, table, query, or other application object.

```xpp
public str name([str value])
```

### Parameters - name

value  

### Return Value - name

The name that is used in the code to identify an application object.

### Remarks - name

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

## Method numberOfLines

```xpp
public int numberOfLines(int height100mm)
```

### Parameters - numberOfLines

height100mm  

### Return Value - numberOfLines

## Method position

```xpp
public int position([int value])
```

### Parameters - position

value  

### Return Value - position

## Method previewInfo

```xpp
public str previewInfo(str string)
```

### Parameters - previewInfo

string  

### Return Value - previewInfo

## Method previewXCompensation100mm

```xpp
public int previewXCompensation100mm(str string)
```

### Parameters - previewXCompensation100mm

string  

### Return Value - previewXCompensation100mm

## Method right100mm

```xpp
public int right100mm()
```

### Return Value - right100mm

## Method right100mmInclBorder

```xpp
public int right100mmInclBorder()
```

### Return Value - right100mmInclBorder

## Method rightMarginAndFrame

```xpp
public int rightMarginAndFrame()
```

### Return Value - rightMarginAndFrame

## Method rightMarginMode

```xpp
public int rightMarginMode([int value])
```

### Parameters - rightMarginMode

value  

### Return Value - rightMarginMode

## Method rightMarginStr

```xpp
public str rightMarginStr([str value])
```

### Parameters - rightMarginStr

value  

### Return Value - rightMarginStr

## Method rightMarginUnit

```xpp
public Units rightMarginUnit([Units value])
```

### Parameters - rightMarginUnit

value  

### Return Value - rightMarginUnit

## Method rightMarginValue

```xpp
public Real rightMarginValue([Real value])
```

### Parameters - rightMarginValue

value  

### Return Value - rightMarginValue

## Method securityKey

```xpp
public SecurityKeyId securityKey([SecurityKeyId value])
```

### Parameters - securityKey

value  

### Return Value - securityKey

## Method setHeightGetText

```xpp
public str setHeightGetText(int lines, str string)
```

### Parameters - setHeightGetText

lines  

<!-- -->

string  

### Return Value - setHeightGetText

## Method showLabel

```xpp
public boolean showLabel([boolean value])
```

### Parameters - showLabel

value  

### Return Value - showLabel

## Method table

Gets or sets the table ID associated with the object.

```xpp
public TableId table([TableId value])
```

### Parameters - table

value  

### Return Value - table

The current value of the table ID associated with the object.

## Method thickness

```xpp
public LineThickness thickness([LineThickness value])
```

### Parameters - thickness

value  

### Return Value - thickness

## Method top100mm

```xpp
public int top100mm([int topExclBorder])
```

### Parameters - top100mm

topExclBorder  

### Return Value - top100mm

## Method top100mmInclBorder

```xpp
public int top100mmInclBorder([int topInclBorder])
```

### Parameters - top100mmInclBorder

topInclBorder  

### Return Value - top100mmInclBorder

## Method topMarginAndFrame

```xpp
public int topMarginAndFrame()
```

### Return Value - topMarginAndFrame

## Method topMarginMode

```xpp
public int topMarginMode([int value])
```

### Parameters - topMarginMode

value  

### Return Value - topMarginMode

## Method topMarginStr

```xpp
public str topMarginStr([str value])
```

### Parameters - topMarginStr

value  

### Return Value - topMarginStr

## Method topMarginUnit

```xpp
public Units topMarginUnit([Units value])
```

### Parameters - topMarginUnit

value  

### Return Value - topMarginUnit

## Method topMarginValue

```xpp
public Real topMarginValue([Real value])
```

### Parameters - topMarginValue

value  

### Return Value - topMarginValue

## Method topMode

```xpp
public int topMode([int value])
```

### Parameters - topMode

value  

### Return Value - topMode

## Method topStr

```xpp
public str topStr([str value])
```

### Parameters - topStr

value  

### Return Value - topStr

## Method topUnit

```xpp
public Units topUnit([Units value])
```

### Parameters - topUnit

value  

### Return Value - topUnit

## Method topValue

```xpp
public Real topValue([Real value])
```

### Parameters - topValue

value  

### Return Value - topValue

## Method underline

```xpp
public boolean underline([boolean value])
```

### Parameters - underline

value  

### Return Value - underline

## Method visible

```xpp
public boolean visible([boolean value])
```

### Parameters - visible

value  

### Return Value - visible

## Method webMenuItemName

```xpp
public str webMenuItemName([str value])
```

### Parameters - webMenuItemName

value  

### Return Value - webMenuItemName

## Method webMenuItemType

```xpp
public WebMenuItemType webMenuItemType([WebMenuItemType value])
```

### Parameters - webMenuItemType

value  

### Return Value - webMenuItemType

## Method webTarget

```xpp
public str webTarget([str value])
```

### Parameters - webTarget

value  

### Return Value - webTarget

## Method width100mm

```xpp
public int width100mm([int widthExclBorder])
```

### Parameters - width100mm

widthExclBorder  

### Return Value - width100mm

## Method width100mmInclBorder

```xpp
public int width100mmInclBorder([int widthInclBorder])
```

### Parameters - width100mmInclBorder

widthInclBorder  

### Return Value - width100mmInclBorder

## Method widthMode

Gets or sets the calculation mode of the width of the control.

```xpp
public int widthMode([int value])
```

### Parameters - widthMode

value  

### Return Value - widthMode

An integer value that indicates the current calculation mode.

### Remarks - widthMode

Calculate the width according to the following table:

| Mode.         | Width Calculation.                                                                       |
|---------------|------------------------------------------------------------------------------------------|
| Exact.        | The exact width in pixels of the controls is used.                                       |
| Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width. | The layout of the form determines the width of the control.                              |

The width of the control might change when the mode is set to auto or column width.

## Method widthOfString100mm

```xpp
public int widthOfString100mm(str string)
```

### Parameters - widthOfString100mm

string  

### Return Value - widthOfString100mm

## Method widthStr

```xpp
public str widthStr([str value])
```

### Parameters - widthStr

value  

### Return Value - widthStr

## Method widthUnit

```xpp
public Units widthUnit([Units value])
```

### Parameters - widthUnit

value  

### Return Value - widthUnit

## Method widthValue

Gets or sets the width of the control.

```xpp
public Real widthValue([Real value])
```

### Parameters - widthValue

value  

### Return Value - widthValue

The width in pixels of the control.

### Remarks - widthValue

To change the width of the control, use the exact width calculation mode.

## Method width

Gets or sets the width of the control.

```xpp
public void width(Real value, Units unit)
```

### Parameters - width

value  

<!-- -->

unit  

### Remarks - width

Exact mode is used if the value parameter is omitted. Calculate the width according to the following table:

| Mode.           | Width calculation.                                                                       |
|-----------------|------------------------------------------------------------------------------------------|
| -1 Exact.       | The exact width in pixels of the controls is used.                                       |
| 0 Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width. | The layout of the form determines the width of the control.                              |

The width and width calculation mode can be set separately.

## Method topMargin

```xpp
public void topMargin(Real value, Units unit)
```

### Parameters - topMargin

value  

<!-- -->

unit  

## Method bottomMargin

```xpp
public void bottomMargin(Real value, Units unit)
```

### Parameters - bottomMargin

value  

<!-- -->

unit  

## Method rightMargin

```xpp
public void rightMargin(Real value, Units unit)
```

### Parameters - rightMargin

value  

<!-- -->

unit  

## Method leftMargin

```xpp
public void leftMargin(Real value, Units unit)
```

### Parameters - leftMargin

value  

<!-- -->

unit  

## Method show

```xpp
public void show()
```

## Method hide

```xpp
public void hide()
```

## Method top

```xpp
public void top(Real value, Units unit)
```

### Parameters - top

value  

<!-- -->

unit  

## Method left

```xpp
public void left(Real value, Units unit)
```

### Parameters - left

value  

<!-- -->

unit  

## Method labelWidth

```xpp
public void labelWidth(Real value, Units unit)
```

### Parameters - labelWidth

value  

<!-- -->

unit  

## Method height

Gets or sets the height of the control.

```xpp
public void height(Real value, Units unit)
```

### Parameters - height

value  

<!-- -->

unit  

### Remarks - height

Exact mode is used if the value parameter is omitted. Calculate the height according to the following table:

| Mode.            | Height calculation.                                                                       |
|------------------|-------------------------------------------------------------------------------------------|
| -1 Exact.        | The exact height in pixels of the controls is used.                                       |
| 0 Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height. | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

