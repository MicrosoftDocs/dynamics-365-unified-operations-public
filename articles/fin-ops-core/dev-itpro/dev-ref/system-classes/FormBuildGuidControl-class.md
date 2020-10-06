---
title: FormBuildGuidControl class
description: This topic describes the FormBuildGuidControl class.
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

# Class FormBuildGuidControl

[!include [banner](../../includes/banner.md)]

```xpp
class FormBuildGuidControl extends FormBuildControl
```

The FormBuildGuidControl class lets you create, read, update, and delete X++ code and metadata.

## Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

## Examples

## Methods

| Method                                                                                                      | Description                                                                                                                             |
|-------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| public boolean alignControl(\[boolean value\])                                                              | Determines whether to align the control.                                                                                                |
| public int alignment(\[int value\])                                                                         |                                                                                                                                         |
| public boolean allowEdit(\[boolean value\])                                                                 | Determines whether the user can change the contents of the control.                                                                     |
| public int arrayIndex(\[int value\])                                                                        |                                                                                                                                         |
| public boolean autoDeclaration(\[boolean value\])                                                           | Determines whether the system can declare a member variable that has the same name as the control.                                      |
| public int backgroundColor(\[int value\])                                                                   | Gets or sets the background color of the control.                                                                                       |
| public int backStyle(\[int value\])                                                                         | Determines whether the control background can be transparent.                                                                          |
| public int bold(\[int value\])                                                                              | Gets or sets the weight of font that is used to output text in the control.                                                             |
| public int border(\[int value\])                                                                            | Gets or sets the style of the borderline of the control.                                                                                |
| public int cacheDataMethod(\[int value\])                                                                   |                                                                                                                                         |
| public int characterSet(\[int value\])                                                                      | Gets or sets the character set of the font.                                                                                             |
| public int colorScheme(\[int value\])                                                                       | Gets or sets the color scheme of the control.                                                                                           |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                    | Gets or sets the configuration key that is assigned to the control.                                                                     |
| public int containerId()                                                                                    | Retrieves the ID of the parent container for the control.                                                                               |
| public str countryRegionCodes(\[str value\])                                                                |                                                                                                                                         |
| public FieldId countryRegionContextField(\[FieldId value\])                                                 |                                                                                                                                         |
| public FieldId dataField(\[FieldId value\])                                                                 |                                                                                                                                         |
| public str dataMethod(\[str value\])                                                                        |                                                                                                                                         |
| public str dataRelationPath(\[str value\])                                                                  |                                                                                                                                         |
| public int dataSource(\[AnyType value\])                                                                    | Gets or sets a data source that will be used by the control or the form.                                                                |
| public int direction(\[int value\])                                                                         |                                                                                                                                         |
| public int displayHeight(\[int value\], \[AutoMode mode\])                                                  |                                                                                                                                         |
| public AutoMode displayHeightMode(\[AutoMode mode\])                                                        |                                                                                                                                         |
| public int displayHeightValue(\[int value\])                                                                |                                                                                                                                         |
| public int displayLength(\[int value\], \[AutoMode mode\])                                                  |                                                                                                                                         |
| public AutoMode displayLengthMode(\[AutoMode mode\])                                                        |                                                                                                                                         |
| public int displayLengthValue(\[int value\])                                                                |                                                                                                                                         |
| public int displayTarget(\[int value\])                                                                     |                                                                                                                                         |
| public int dragDrop(\[int value\])                                                                          | Determines whether to enable or disable drag-and-drop operations for the control.                                                       |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether to enable or disable the object.                                                                                     |
| public ExtendedTypeId extendedDataType(\[ExtendedTypeId value\])                                            |                                                                                                                                         |
| public int fastTabSummary(\[int value\])                                                                    |                                                                                                                                         |
| public str font(\[str value\])                                                                              | Gets or sets the name of the font for the control to use.                                                                               |
| public int fontSize(\[int value\])                                                                          | Gets or sets the size of the font for the control to use.                                                                               |
| public int foregroundColor(\[int value\])                                                                   | Gets or sets the text color for the control to use.                                                                                     |
| public int height(int value, \[int mode\])                                                                  | Gets or sets the height of the control.                                                                                                 |
| public int heightMode(\[int value\])                                                                        | Gets or sets a calculation mode for the height of the control.                                                                          |
| public int heightValue(\[int value\])                                                                       | Gets or sets the height of the control.                                                                                                 |
| public str helpText(\[str value\])                                                                          | Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.                                |
| public str hierarchyParent(\[str value\])                                                                   |                                                                                                                                         |
| public int id()                                                                                             | Retrieves the ID of the control.                                                                                                        |
| public int iMEMode(\[int value\])                                                                           |                                                                                                                                         |
| public boolean isContainer()                                                                                | Retrieves a value that indicates whether the control is a container control.                                                            |
| public boolean italic(\[boolean value\])                                                                    |                                                                                                                                         |
| public str label(\[str value\])                                                                             | Gets or sets the label for a control.                                                                                                   |
| public int labelAlignment(\[int value\])                                                                    |                                                                                                                                         |
| public int labelBold(\[int value\])                                                                         |                                                                                                                                         |
| public int labelCharacterSet(\[int value\])                                                                 |                                                                                                                                         |
| public str labelFont(\[str value\])                                                                         |                                                                                                                                         |
| public int labelFontSize(\[int value\])                                                                     |                                                                                                                                         |
| public int labelForegroundColor(\[int value\])                                                              |                                                                                                                                         |
| public int labelGuide(\[int value\])                                                                        |                                                                                                                                         |
| public int labelHeight(int value, \[int mode\])                                                             |                                                                                                                                         |
| public int labelHeightMode(\[int value\])                                                                   |                                                                                                                                         |
| public int labelHeightValue(\[int value\])                                                                  |                                                                                                                                         |
| public boolean labelItalic(\[boolean value\])                                                               |                                                                                                                                         |
| public int labelPosition(\[int value\])                                                                     |                                                                                                                                         |
| public boolean labelUnderline(\[boolean value\])                                                            |                                                                                                                                         |
| public int labelWidth(int value, \[int mode\])                                                              |                                                                                                                                         |
| public int labelWidthMode(\[int value\])                                                                    |                                                                                                                                         |
| public int labelWidthValue(\[int value\])                                                                   |                                                                                                                                         |
| public int left(int value, \[int mode\])                                                                    |                                                                                                                                         |
| public int leftMode(\[int value\])                                                                          |                                                                                                                                         |
| public int leftValue(\[int value\])                                                                         |                                                                                                                                         |
| public int limitText(\[int value\], \[AutoMode mode\])                                                      |                                                                                                                                         |
| public AutoMode limitTextMode(\[AutoMode mode\])                                                            |                                                                                                                                         |
| public int limitTextValue(\[int value\])                                                                    |                                                                                                                                         |
| public int lookupButton(\[int value\])                                                                      |                                                                                                                                         |
| public boolean mandatory(\[boolean value\])                                                                 |                                                                                                                                         |
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in code to identify a form, report, table, query, or other application object. |
| public int neededPermission(\[int value\])                                                                  |                                                                                                                                         |
| public int promptrect(\[int value\])                                                                        |                                                                                                                                         |
| public boolean replaceOnLookup(\[boolean value\])                                                           |                                                                                                                                         |
| public int searchAfterInput(\[int value\])                                                                  |                                                                                                                                         |
| public int searchMode(\[int value\])                                                                        |                                                                                                                                         |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                   |                                                                                                                                         |
| public boolean showLabel(\[boolean value\])                                                                 |                                                                                                                                         |
| public boolean skip(\[boolean value\])                                                                      | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.         |
| public int style(\[int value\])                                                                             |                                                                                                                                         |
| public int top(int value, \[int mode\])                                                                     |                                                                                                                                         |
| public int topMode(\[int value\])                                                                           |                                                                                                                                         |
| public int topValue(\[int value\])                                                                          |                                                                                                                                         |
| public int type(\[int value\])                                                                              |                                                                                                                                         |
| public boolean underline(\[boolean value\])                                                                 | Sets or returns the underline property for the text in the control.                                                                     |
| public int userData(\[int value\])                                                                          |                                                                                                                                         |
| public int userDataItem(\[int value\])                                                                      |                                                                                                                                         |
| public int userDataItems(\[int value\])                                                                     |                                                                                                                                         |
| public Guid value(\[Guid value\])                                                                           |                                                                                                                                         |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                |                                                                                                                                         |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                      |                                                                                                                                         |
| public int verticalSpacingValue(\[int value\])                                                              |                                                                                                                                         |
| public int viewEditMode(\[int value\])                                                                      |                                                                                                                                         |
| public boolean visible(\[boolean value\])                                                                   |                                                                                                                                         |
| public int width(int value, \[int mode\])                                                                   | Gets or sets the width of the control.                                                                                                  |
| public int widthMode(\[int value\])                                                                         | Gets or sets the calculation mode of the width of the control.                                                                          |
| public int widthValue(\[int value\])                                                                        | Gets or sets the width of the control.                                                                                                  |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                         |

## Method alignControl

Determines whether to align the control.

```xpp
public boolean alignControl([boolean value])
```

### Parameters - alignControl

value  

### Return Value - alignControl

true if the control should be aligned; otherwise, false.

### Remarks - alignControl

The upper-left corner of the control is aligned according to the longest label.

## Method alignment

```xpp
public int alignment([int value])
```

### Parameters - alignment

value  

### Return Value - alignment

## Method allowEdit

Determines whether the user can change the contents of the control.

```xpp
public boolean allowEdit([boolean value])
```

### Parameters - allowEdit

value  

### Return Value - allowEdit

true if the control can be edited; otherwise, false.

### Remarks - allowEdit

When this property is set on a container control, modifications are disabled or enabled for all controls in the container.

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

## Method border

Gets or sets the style of the borderline of the control.

```xpp
public int border([int value])
```

### Parameters - border

value  

### Return Value - border

An integer between zero and four, inclusive.

### Remarks - border

The integer that is returned contains the style of the borderline of the control as follows:

| Value. | Description. |
|--------|--------------|
| 0      | Auto.        |
| 1      | 3D.          |
| 2      | Single line. |
| 3      | Flat.        |
| 4      | None.        |

## Method cacheDataMethod

```xpp
public int cacheDataMethod([int value])
```

### Parameters - cacheDataMethod

value  

### Return Value - cacheDataMethod

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

| Value. | Style.                         |
|--------|--------------------------------|
| 0      | Default.                       |
| 1      | The Microsoft Windows palette. |
| 2      | The true-color scheme.         |

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

## Method containerId

Retrieves the ID of the parent container for the control.

```xpp
public int containerId()
```

### Return Value - containerId

The ID of the parent container.

## Method countryRegionCodes

```xpp
public str countryRegionCodes([str value])
```

### Parameters - countryRegionCodes

value  

### Return Value - countryRegionCodes

## Method countryRegionContextField

```xpp
public FieldId countryRegionContextField([FieldId value])
```

### Parameters - countryRegionContextField

value  

### Return Value - countryRegionContextField

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

## Method dataRelationPath

```xpp
public str dataRelationPath([str value])
```

### Parameters - dataRelationPath

value  

### Return Value - dataRelationPath

## Method dataSource

Gets or sets a data source that will be used by the control or the form.

```xpp
public int dataSource([AnyType value])
```

### Parameters - dataSource

value  

### Return Value - dataSource

The identifier of the data source that will be used.

## Method direction

```xpp
public int direction([int value])
```

### Parameters - direction

value  

### Return Value - direction

## Method displayHeight

```xpp
public int displayHeight([int value], [AutoMode mode])
```

### Parameters - displayHeight

value  

<!-- -->

mode  

### Return Value - displayHeight

## Method displayHeightMode

```xpp
public AutoMode displayHeightMode([AutoMode mode])
```

### Parameters - displayHeightMode

mode  

### Return Value - displayHeightMode

## Method displayHeightValue

```xpp
public int displayHeightValue([int value])
```

### Parameters - displayHeightValue

value  

### Return Value - displayHeightValue

## Method displayLength

```xpp
public int displayLength([int value], [AutoMode mode])
```

### Parameters - displayLength

value  

<!-- -->

mode  

### Return Value - displayLength

## Method displayLengthMode

```xpp
public AutoMode displayLengthMode([AutoMode mode])
```

### Parameters - displayLengthMode

mode  

### Return Value - displayLengthMode

## Method displayLengthValue

```xpp
public int displayLengthValue([int value])
```

### Parameters - displayLengthValue

value  

### Return Value - displayLengthValue

## Method displayTarget

```xpp
public int displayTarget([int value])
```

### Parameters - displayTarget

value  

### Return Value - displayTarget

## Method dragDrop

Determines whether to enable or disable drag-and-drop operations for the control.

```xpp
public int dragDrop([int value])
```

### Parameters - dragDrop

value  

### Return Value - dragDrop

1 if drag-and-drop operations are enabled; otherwise, false.

## Method enabled

Determines whether to enable or disable the object.

```xpp
public boolean enabled([boolean value])
```

### Parameters - enabled

value  

### Return Value - enabled

true if the object is enabled; otherwise, false.

### Remarks - enabled

The enabled property allows for controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

## Method extendedDataType

```xpp
public ExtendedTypeId extendedDataType([ExtendedTypeId value])
```

### Parameters - extendedDataType

value  

### Return Value - extendedDataType

## Method fastTabSummary

```xpp
public int fastTabSummary([int value])
```

### Parameters - fastTabSummary

value  

### Return Value - fastTabSummary

## Method font

Gets or sets the name of the font for the control to use.

```xpp
public str font([str value])
```

### Parameters - font

value  

### Return Value - font

The name of the font to use, such as Tahoma or Verdana.

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

## Method height

Gets or sets the height of the control.

```xpp
public int height(int value, [int mode])
```

### Parameters - height

value  

<!-- -->

mode  

### Return Value - height

The height of the control in pixels.

### Remarks - height

Exact mode is used if the value parameter is omitted. Calculate the height according to the following table:

| Mode.            | Height calculation.                                                                       |
|------------------|-------------------------------------------------------------------------------------------|
| -1 Exact.        | The exact height in pixels of the controls is used.                                       |
| 0 Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height. | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

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

## Method heightValue

Gets or sets the height of the control.

```xpp
public int heightValue([int value])
```

### Parameters - heightValue

value  

### Return Value - heightValue

The height in pixels.

### Remarks - heightValue

The height of the control is not changed unless the exact height calculation mode is used.

## Method helpText

Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.

```xpp
public str helpText([str value])
```

### Parameters - helpText

value  

### Return Value - helpText

The string to be displayed at the bottom of the screen.

### Remarks - helpText

Set the HelpText property for an object by using the property sheet. The help text must not exceed 250 characters.

## Method hierarchyParent

```xpp
public str hierarchyParent([str value])
```

### Parameters - hierarchyParent

value  

### Return Value - hierarchyParent

## Method id

Retrieves the ID of the control.

```xpp
public int id()
```

### Return Value - id

The ID of the control.

## Method iMEMode

```xpp
public int iMEMode([int value])
```

### Parameters - iMEMode

value  

### Return Value - iMEMode

## Method isContainer

Retrieves a value that indicates whether the control is a container control.

```xpp
public boolean isContainer()
```

### Return Value - isContainer

A Boolean value that indicates whether the control is a container control.

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

## Method labelAlignment

```xpp
public int labelAlignment([int value])
```

### Parameters - labelAlignment

value  

### Return Value - labelAlignment

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

## Method labelForegroundColor

```xpp
public int labelForegroundColor([int value])
```

### Parameters - labelForegroundColor

value  

### Return Value - labelForegroundColor

## Method labelGuide

```xpp
public int labelGuide([int value])
```

### Parameters - labelGuide

value  

### Return Value - labelGuide

## Method labelHeight

```xpp
public int labelHeight(int value, [int mode])
```

### Parameters - labelHeight

value  

<!-- -->

mode  

### Return Value - labelHeight

## Method labelHeightMode

```xpp
public int labelHeightMode([int value])
```

### Parameters - labelHeightMode

value  

### Return Value - labelHeightMode

## Method labelHeightValue

```xpp
public int labelHeightValue([int value])
```

### Parameters - labelHeightValue

value  

### Return Value - labelHeightValue

## Method labelItalic

```xpp
public boolean labelItalic([boolean value])
```

### Parameters - labelItalic

value  

### Return Value - labelItalic

## Method labelPosition

```xpp
public int labelPosition([int value])
```

### Parameters - labelPosition

value  

### Return Value - labelPosition

## Method labelUnderline

```xpp
public boolean labelUnderline([boolean value])
```

### Parameters - labelUnderline

value  

### Return Value - labelUnderline

## Method labelWidth

```xpp
public int labelWidth(int value, [int mode])
```

### Parameters - labelWidth

value  

<!-- -->

mode  

### Return Value - labelWidth

## Method labelWidthMode

```xpp
public int labelWidthMode([int value])
```

### Parameters - labelWidthMode

value  

### Return Value - labelWidthMode

## Method labelWidthValue

```xpp
public int labelWidthValue([int value])
```

### Parameters - labelWidthValue

value  

### Return Value - labelWidthValue

## Method left

```xpp
public int left(int value, [int mode])
```

### Parameters - left

value  

<!-- -->

mode  

### Return Value - left

## Method leftMode

```xpp
public int leftMode([int value])
```

### Parameters - leftMode

value  

### Return Value - leftMode

## Method leftValue

```xpp
public int leftValue([int value])
```

### Parameters - leftValue

value  

### Return Value - leftValue

## Method limitText

```xpp
public int limitText([int value], [AutoMode mode])
```

### Parameters - limitText

value  

<!-- -->

mode  

### Return Value - limitText

## Method limitTextMode

```xpp
public AutoMode limitTextMode([AutoMode mode])
```

### Parameters - limitTextMode

mode  

### Return Value - limitTextMode

## Method limitTextValue

```xpp
public int limitTextValue([int value])
```

### Parameters - limitTextValue

value  

### Return Value - limitTextValue

## Method lookupButton

```xpp
public int lookupButton([int value])
```

### Parameters - lookupButton

value  

### Return Value - lookupButton

## Method mandatory

```xpp
public boolean mandatory([boolean value])
```

### Parameters - mandatory

value  

### Return Value - mandatory

## Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other application object.

```xpp
public str name([str value])
```

### Parameters - name

value  
The name to assign to the control.

### Return Value - name

The name that is used in code to identify an application object.

### Remarks - name

The name property value of an object must meet the following criteria to avoid code conflicts:

-   It must start with a letter.
-   It cannot exceed 250 characters.
-   It can include numbers and underscore (\_) characters.
-   It cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, or classes.

## Method neededPermission

```xpp
public int neededPermission([int value])
```

### Parameters - neededPermission

value  

### Return Value - neededPermission

## Method promptrect

```xpp
public int promptrect([int value])
```

### Parameters - promptrect

value  

### Return Value - promptrect

## Method replaceOnLookup

```xpp
public boolean replaceOnLookup([boolean value])
```

### Parameters - replaceOnLookup

value  

### Return Value - replaceOnLookup

## Method searchAfterInput

```xpp
public int searchAfterInput([int value])
```

### Parameters - searchAfterInput

value  

### Return Value - searchAfterInput

## Method searchMode

```xpp
public int searchMode([int value])
```

### Parameters - searchMode

value  

### Return Value - searchMode

## Method securityKey

```xpp
public SecurityKeyId securityKey([SecurityKeyId value])
```

### Parameters - securityKey

value  

### Return Value - securityKey

## Method showLabel

```xpp
public boolean showLabel([boolean value])
```

### Parameters - showLabel

value  

### Return Value - showLabel

## Method skip

Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.

```xpp
public boolean skip([boolean value])
```

### Parameters - skip

value  
The value to assign to the skip property of the control.

### Return Value - skip

true if the control is skipped when the user presses the TAB key to move to the control; otherwise, false.

## Method style

```xpp
public int style([int value])
```

### Parameters - style

value  

### Return Value - style

## Method top

```xpp
public int top(int value, [int mode])
```

### Parameters - top

value  

<!-- -->

mode  

### Return Value - top

## Method topMode

```xpp
public int topMode([int value])
```

### Parameters - topMode

value  

### Return Value - topMode

## Method topValue

```xpp
public int topValue([int value])
```

### Parameters - topValue

value  

### Return Value - topValue

## Method type

```xpp
public int type([int value])
```

### Parameters - type

value  

### Return Value - type

## Method underline

Sets or returns the underline property for the text in the control.

```xpp
public boolean underline([boolean value])
```

### Parameters - underline

value  
The value to assign to the underline property of the control.

### Return Value - underline

true if the text in the control is underlined; otherwise, false.

## Method userData

```xpp
public int userData([int value])
```

### Parameters - userData

value  

### Return Value - userData

## Method userDataItem

```xpp
public int userDataItem([int value])
```

### Parameters - userDataItem

value  

### Return Value - userDataItem

## Method userDataItems

```xpp
public int userDataItems([int value])
```

### Parameters - userDataItems

value  

### Return Value - userDataItems

## Method value

```xpp
public Guid value([Guid value])
```

### Parameters - value

value  

### Return Value - value

## Method verticalSpacing

```xpp
public int verticalSpacing([int value], [AutoMode mode])
```

### Parameters - verticalSpacing

value  

<!-- -->

mode  

### Return Value - verticalSpacing

## Method verticalSpacingMode

```xpp
public AutoMode verticalSpacingMode([AutoMode mode])
```

### Parameters - verticalSpacingMode

mode  

### Return Value - verticalSpacingMode

## Method verticalSpacingValue

```xpp
public int verticalSpacingValue([int value])
```

### Parameters - verticalSpacingValue

value  

### Return Value - verticalSpacingValue

## Method viewEditMode

```xpp
public int viewEditMode([int value])
```

### Parameters - viewEditMode

value  

### Return Value - viewEditMode

## Method visible

```xpp
public boolean visible([boolean value])
```

### Parameters - visible

value  

### Return Value - visible

## Method width

Gets or sets the width of the control.

```xpp
public int width(int value, [int mode])
```

### Parameters - width

value  

<!-- -->

mode  

### Return Value - width

The width of the control in pixels.

### Remarks - width

Exact mode is used if the value parameter is omitted. Calculate the width according to the following table:

| Mode.           | Width calculation.                                                                       |
|-----------------|------------------------------------------------------------------------------------------|
| -1 Exact.       | The exact width in pixels of the controls is used.                                       |
| 0 Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width. | The layout of the form determines the width of the control.                              |

The width and width calculation mode can be set separately.

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

## Method widthValue

Gets or sets the width of the control.

```xpp
public int widthValue([int value])
```

### Parameters - widthValue

value  

### Return Value - widthValue

The width in pixels of the control.

### Remarks - widthValue

To change the width of the control, use the exact width calculation mode.

## Method registerOverrideMethod

```xpp
public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])
```

### Parameters - registerOverrideMethod

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

