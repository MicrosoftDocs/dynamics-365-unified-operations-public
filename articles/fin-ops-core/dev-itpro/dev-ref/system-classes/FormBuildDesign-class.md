---
title: FormBuildDesign class
description: This topic describes the FormBuildDesign class.
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

# Class FormBuildDesign

[!include [banner](../../includes/banner.md)]

```xpp
class FormBuildDesign extends Object
```

The FormBuildDesign class modifies a form design.

## Remarks

This class lets you create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

## Examples

## Methods

| Method                                                                                                                          | Description                                                                 |
|---------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------|
| public Object addControl(FormControlType controlType, str controlName, \[FormBuildControl insertAfter\], \[boolean pushFront\]) |                                                                             |
| public Object addControlEx(str controlClass, str controlName, \[FormBuildControl insertAfter\], \[boolean pushFront\])          |                                                                             |
| public boolean alignChild(\[boolean value\])                                                                                    |                                                                             |
| public boolean alignChildren(\[boolean value\])                                                                                 |                                                                             |
| public boolean allowDocking(\[boolean value\])                                                                                  |                                                                             |
| public boolean allowFormCompanyChange(\[boolean value\])                                                                        |                                                                             |
| public boolean allowImplicitParent(\[boolean value\])                                                                           |                                                                             |
| public int allowUserSetup(\[int value\])                                                                                        |                                                                             |
| public boolean alwaysOnTop(\[boolean value\])                                                                                   |                                                                             |
| public int arrangeGuide(\[int value\])                                                                                          |                                                                             |
| public int arrangeMethod(\[int value\])                                                                                         |                                                                             |
| public int arrangeWhen(\[int value\])                                                                                           |                                                                             |
| public int backgroundColor(\[int value\])                                                                                       | Gets or sets the background color of the control.                           |
| public int bold(\[int value\])                                                                                                  | Gets or sets the weight of font that is used to output text in the control. |
| public int bottomMargin(\[int value\], \[AutoMode mode\])                                                                       |                                                                             |
| public AutoMode bottomMarginMode(\[AutoMode mode\])                                                                             |                                                                             |
| public int bottomMarginValue(\[int value\])                                                                                     |                                                                             |
| public str caption(\[str value\])                                                                                               | Gets or set the caption of the control.                                     |
| public int characterSet(\[int value\])                                                                                          | Gets or sets the character set of the font.                                 |
| public int colorScheme(\[int value\])                                                                                           | Gets or sets the color scheme of the control.                               |
| public int columns(\[int value\], \[ColumnsMode mode\])                                                                         |                                                                             |
| public ColumnsMode columnsMode(\[ColumnsMode mode\])                                                                            |                                                                             |
| public int columnspace(\[int value\], \[AutoMode mode\])                                                                        |                                                                             |
| public AutoMode columnspaceMode(\[AutoMode mode\])                                                                              |                                                                             |
| public int columnspaceValue(\[int value\])                                                                                      |                                                                             |
| public int columnsValue(\[int value\])                                                                                          |                                                                             |
| public Object control(AnyType control)                                                                                          |                                                                             |
| public int controlCount()                                                                                                       |                                                                             |
| public FormBuildControl controlNum(int controlNo)                                                                               |                                                                             |
| public str cssClass(\[str value\])                                                                                              |                                                                             |
| public int dataSource(\[AnyType value\])                                                                                        | Gets or sets a data source that should be used by the control or the form.  |
| public str defaultAction(\[str value\])                                                                                         |                                                                             |
| public str font(\[str value\])                                                                                                  | Gets or sets the name of the font for the control to use.                   |
| public int fontSize(\[int value\])                                                                                              | Gets or sets the size of the font for the control to use.                   |
| public int frame(\[int value\])                                                                                                 |                                                                             |
| public int height(int value, \[int mode\])                                                                                      | Gets or sets the height of the control.                                     |
| public int heightMode(\[int value\])                                                                                            | Gets or sets a calculation mode for the height of the control.              |
| public int heightValue(\[int value\])                                                                                           | Gets or sets the height of the control.                                     |
| public boolean hideIfEmpty(\[boolean value\])                                                                                   |                                                                             |
| public boolean hideToolbar(\[boolean value\])                                                                                   |                                                                             |
| public int imagemode(\[int value\])                                                                                             |                                                                             |
| public str imageName(\[str value\])                                                                                             |                                                                             |
| public int imageResource(\[int value\])                                                                                         |                                                                             |
| public boolean italic(\[boolean value\])                                                                                        |                                                                             |
| public int labelBold(\[int value\])                                                                                             |                                                                             |
| public int labelCharacterSet(\[int value\])                                                                                     |                                                                             |
| public str labelFont(\[str value\])                                                                                             |                                                                             |
| public int labelFontSize(\[int value\])                                                                                         |                                                                             |
| public boolean labelItalic(\[boolean value\])                                                                                   |                                                                             |
| public boolean labelUnderline(\[boolean value\])                                                                                |                                                                             |
| public int left(int value, \[int mode\])                                                                                        |                                                                             |
| public int leftMargin(\[int value\], \[AutoMode mode\])                                                                         |                                                                             |
| public AutoMode leftMarginMode(\[AutoMode mode\])                                                                               |                                                                             |
| public int leftMarginValue(\[int value\])                                                                                       |                                                                             |
| public int leftMode(\[int value\])                                                                                              |                                                                             |
| public int leftValue(\[int value\])                                                                                             |                                                                             |
| public str localWebMenu(\[str value\])                                                                                          |                                                                             |
| public boolean maximizeBox(\[boolean value\])                                                                                   |                                                                             |
| public boolean minimizeBox(\[boolean value\])                                                                                   |                                                                             |
| public int mode(\[int value\])                                                                                                  |                                                                             |
| public int moveControl(int controlId, \[int insertAfterControlId\])                                                             |                                                                             |
| public str newRecordAction(\[str value\])                                                                                       |                                                                             |
| public int rightMargin(\[int value\], \[AutoMode mode\])                                                                        |                                                                             |
| public AutoMode rightMarginMode(\[AutoMode mode\])                                                                              |                                                                             |
| public int rightMarginValue(\[int value\])                                                                                      |                                                                             |
| public boolean saveSize(\[boolean value\])                                                                                      |                                                                             |
| public int scrollbars(\[int value\])                                                                                            |                                                                             |
| public boolean setCompany(\[boolean value\])                                                                                    |                                                                             |
| public int showDeleteButton(\[int value\])                                                                                      |                                                                             |
| public int showNewButton(\[int value\])                                                                                         |                                                                             |
| public int showWebHelp(\[int value\])                                                                                           |                                                                             |
| public int statusBarStyle(\[int value\])                                                                                        |                                                                             |
| public int style(\[int value\])                                                                                                 |                                                                             |
| public int submitMethod(\[int value\])                                                                                          |                                                                             |
| public boolean supportReload(\[boolean value\])                                                                                 |                                                                             |
| public int titleDatasource(\[AnyType value\])                                                                                   |                                                                             |
| public int top(int value, \[int mode\])                                                                                         |                                                                             |
| public int topMargin(\[int value\], \[AutoMode mode\])                                                                          |                                                                             |
| public AutoMode topMarginMode(\[AutoMode mode\])                                                                                |                                                                             |
| public int topMarginValue(\[int value\])                                                                                        |                                                                             |
| public int topMode(\[int value\])                                                                                               |                                                                             |
| public int topValue(\[int value\])                                                                                              |                                                                             |
| public boolean underline(\[boolean value\])                                                                                     |                                                                             |
| public int useCaptionFromMenuItem(\[int value\])                                                                                |                                                                             |
| public int viewEditMode(\[int value\])                                                                                          |                                                                             |
| public boolean visible(\[boolean value\])                                                                                       |                                                                             |
| public int width(int value, \[int mode\])                                                                                       | Gets or sets the width of the control.                                      |
| public int widthMode(\[int value\])                                                                                             | Gets or sets the calculation mode of the width of the control.              |
| public int widthValue(\[int value\])                                                                                            | Gets or sets the width of the control.                                      |
| public int windowResize(\[int value\])                                                                                          |                                                                             |
| public int windowType(\[int value\])                                                                                            |                                                                             |
| public int workflowDatasource(\[AnyType value\])                                                                                |                                                                             |
| public boolean workflowEnabled(\[boolean value\])                                                                               |                                                                             |
| public str workflowType(\[str value\])                                                                                          |                                                                             |
| public int dialogSize(\[int value\])                                                                                            |                                                                             |

## Method addControl

```xpp
public Object addControl(FormControlType controlType, str controlName, [FormBuildControl insertAfter], [boolean pushFront])
```

### Parameters - addControl

controlType  

<!-- -->

controlName  

<!-- -->

insertAfter  

<!-- -->

pushFront  

### Return Value - addControl

## Method addControlEx

```xpp
public Object addControlEx(str controlClass, str controlName, [FormBuildControl insertAfter], [boolean pushFront])
```

### Parameters - addControlEx

controlClass  

<!-- -->

controlName  

<!-- -->

insertAfter  

<!-- -->

pushFront  

### Return Value - addControlEx

## Method alignChild

```xpp
public boolean alignChild([boolean value])
```

### Parameters - alignChild

value  

### Return Value - alignChild

## Method alignChildren

```xpp
public boolean alignChildren([boolean value])
```

### Parameters - alignChildren

value  

### Return Value - alignChildren

## Method allowDocking

```xpp
public boolean allowDocking([boolean value])
```

### Parameters - allowDocking

value  

### Return Value - allowDocking

## Method allowFormCompanyChange

```xpp
public boolean allowFormCompanyChange([boolean value])
```

### Parameters - allowFormCompanyChange

value  

### Return Value - allowFormCompanyChange

## Method allowImplicitParent

```xpp
public boolean allowImplicitParent([boolean value])
```

### Parameters - allowImplicitParent

value  

### Return Value - allowImplicitParent

## Method allowUserSetup

```xpp
public int allowUserSetup([int value])
```

### Parameters - allowUserSetup

value  

### Return Value - allowUserSetup

## Method alwaysOnTop

```xpp
public boolean alwaysOnTop([boolean value])
```

### Parameters - alwaysOnTop

value  

### Return Value - alwaysOnTop

## Method arrangeGuide

```xpp
public int arrangeGuide([int value])
```

### Parameters - arrangeGuide

value  

### Return Value - arrangeGuide

## Method arrangeMethod

```xpp
public int arrangeMethod([int value])
```

### Parameters - arrangeMethod

value  

### Return Value - arrangeMethod

## Method arrangeWhen

```xpp
public int arrangeWhen([int value])
```

### Parameters - arrangeWhen

value  

### Return Value - arrangeWhen

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

## Method bottomMargin

```xpp
public int bottomMargin([int value], [AutoMode mode])
```

### Parameters - bottomMargin

value  

<!-- -->

mode  

### Return Value - bottomMargin

## Method bottomMarginMode

```xpp
public AutoMode bottomMarginMode([AutoMode mode])
```

### Parameters - bottomMarginMode

mode  

### Return Value - bottomMarginMode

## Method bottomMarginValue

```xpp
public int bottomMarginValue([int value])
```

### Parameters - bottomMarginValue

value  

### Return Value - bottomMarginValue

## Method caption

Gets or set the caption of the control.

```xpp
public str caption([str value])
```

### Parameters - caption

value  

### Return Value - caption

The string that is used as the caption of the control.

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

The default character set is set to a value that is based on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET. For more information, see the LOGFONT structure on the [MSDN website](https://go.microsoft.com/fwlink/?LinkID=85972).

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

## Method columns

```xpp
public int columns([int value], [ColumnsMode mode])
```

### Parameters - columns

value  

<!-- -->

mode  

### Return Value - columns

## Method columnsMode

```xpp
public ColumnsMode columnsMode([ColumnsMode mode])
```

### Parameters - columnsMode

mode  

### Return Value - columnsMode

## Method columnspace

```xpp
public int columnspace([int value], [AutoMode mode])
```

### Parameters - columnspace

value  

<!-- -->

mode  

### Return Value - columnspace

## Method columnspaceMode

```xpp
public AutoMode columnspaceMode([AutoMode mode])
```

### Parameters - columnspaceMode

mode  

### Return Value - columnspaceMode

## Method columnspaceValue

```xpp
public int columnspaceValue([int value])
```

### Parameters - columnspaceValue

value  

### Return Value - columnspaceValue

## Method columnsValue

```xpp
public int columnsValue([int value])
```

### Parameters - columnsValue

value  

### Return Value - columnsValue

## Method control

```xpp
public Object control(AnyType control)
```

### Parameters - control

control  

### Return Value - control

## Method controlCount

```xpp
public int controlCount()
```

### Return Value - controlCount

## Method controlNum

```xpp
public FormBuildControl controlNum(int controlNo)
```

### Parameters - controlNum

controlNo  

### Return Value - controlNum

## Method cssClass

```xpp
public str cssClass([str value])
```

### Parameters - cssClass

value  

### Return Value - cssClass

## Method dataSource

Gets or sets a data source that should be used by the control or the form.

```xpp
public int dataSource([AnyType value])
```

### Parameters - dataSource

value  

### Return Value - dataSource

The identifier of the data source that will be used.

## Method defaultAction

```xpp
public str defaultAction([str value])
```

### Parameters - defaultAction

value  

### Return Value - defaultAction

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

## Method frame

```xpp
public int frame([int value])
```

### Parameters - frame

value  

### Return Value - frame

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

## Method hideIfEmpty

```xpp
public boolean hideIfEmpty([boolean value])
```

### Parameters - hideIfEmpty

value  

### Return Value - hideIfEmpty

## Method hideToolbar

```xpp
public boolean hideToolbar([boolean value])
```

### Parameters - hideToolbar

value  

### Return Value - hideToolbar

## Method imagemode

```xpp
public int imagemode([int value])
```

### Parameters - imagemode

value  

### Return Value - imagemode

## Method imageName

```xpp
public str imageName([str value])
```

### Parameters - imageName

value  

### Return Value - imageName

## Method imageResource

```xpp
public int imageResource([int value])
```

### Parameters - imageResource

value  

### Return Value - imageResource

## Method italic

```xpp
public boolean italic([boolean value])
```

### Parameters - italic

value  

### Return Value - italic

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

## Method labelItalic

```xpp
public boolean labelItalic([boolean value])
```

### Parameters - labelItalic

value  

### Return Value - labelItalic

## Method labelUnderline

```xpp
public boolean labelUnderline([boolean value])
```

### Parameters - labelUnderline

value  

### Return Value - labelUnderline

## Method left

```xpp
public int left(int value, [int mode])
```

### Parameters - left

value  

<!-- -->

mode  

### Return Value - left

## Method leftMargin

```xpp
public int leftMargin([int value], [AutoMode mode])
```

### Parameters - leftMargin

value  

<!-- -->

mode  

### Return Value - leftMargin

## Method leftMarginMode

```xpp
public AutoMode leftMarginMode([AutoMode mode])
```

### Parameters - leftMarginMode

mode  

### Return Value - leftMarginMode

## Method leftMarginValue

```xpp
public int leftMarginValue([int value])
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

## Method leftValue

```xpp
public int leftValue([int value])
```

### Parameters - leftValue

value  

### Return Value - leftValue

## Method localWebMenu

```xpp
public str localWebMenu([str value])
```

### Parameters - localWebMenu

value  

### Return Value - localWebMenu

## Method maximizeBox

```xpp
public boolean maximizeBox([boolean value])
```

### Parameters - maximizeBox

value  

### Return Value - maximizeBox

## Method minimizeBox

```xpp
public boolean minimizeBox([boolean value])
```

### Parameters - minimizeBox

value  

### Return Value - minimizeBox

## Method mode

```xpp
public int mode([int value])
```

### Parameters - mode

value  

### Return Value - mode

## Method moveControl

```xpp
public int moveControl(int controlId, [int insertAfterControlId])
```

### Parameters - moveControl

controlId  

<!-- -->

insertAfterControlId  

### Return Value - moveControl

## Method newRecordAction

```xpp
public str newRecordAction([str value])
```

### Parameters - newRecordAction

value  

### Return Value - newRecordAction

## Method rightMargin

```xpp
public int rightMargin([int value], [AutoMode mode])
```

### Parameters - rightMargin

value  

<!-- -->

mode  

### Return Value - rightMargin

## Method rightMarginMode

```xpp
public AutoMode rightMarginMode([AutoMode mode])
```

### Parameters - rightMarginMode

mode  

### Return Value - rightMarginMode

## Method rightMarginValue

```xpp
public int rightMarginValue([int value])
```

### Parameters - rightMarginValue

value  

### Return Value - rightMarginValue

## Method saveSize

```xpp
public boolean saveSize([boolean value])
```

### Parameters - saveSize

value  

### Return Value - saveSize

## Method scrollbars

```xpp
public int scrollbars([int value])
```

### Parameters - scrollbars

value  

### Return Value - scrollbars

## Method setCompany

```xpp
public boolean setCompany([boolean value])
```

### Parameters - setCompany

value  

### Return Value - setCompany

## Method showDeleteButton

```xpp
public int showDeleteButton([int value])
```

### Parameters - showDeleteButton

value  

### Return Value - showDeleteButton

## Method showNewButton

```xpp
public int showNewButton([int value])
```

### Parameters - showNewButton

value  

### Return Value - showNewButton

## Method showWebHelp

```xpp
public int showWebHelp([int value])
```

### Parameters - showWebHelp

value  

### Return Value - showWebHelp

## Method statusBarStyle

```xpp
public int statusBarStyle([int value])
```

### Parameters - statusBarStyle

value  

### Return Value - statusBarStyle

## Method style

```xpp
public int style([int value])
```

### Parameters - style

value  

### Return Value - style

## Method submitMethod

```xpp
public int submitMethod([int value])
```

### Parameters - submitMethod

value  

### Return Value - submitMethod

## Method supportReload

```xpp
public boolean supportReload([boolean value])
```

### Parameters - supportReload

value  

### Return Value - supportReload

## Method titleDatasource

```xpp
public int titleDatasource([AnyType value])
```

### Parameters - titleDatasource

value  

### Return Value - titleDatasource

## Method top

```xpp
public int top(int value, [int mode])
```

### Parameters - top

value  

<!-- -->

mode  

### Return Value - top

## Method topMargin

```xpp
public int topMargin([int value], [AutoMode mode])
```

### Parameters - topMargin

value  

<!-- -->

mode  

### Return Value - topMargin

## Method topMarginMode

```xpp
public AutoMode topMarginMode([AutoMode mode])
```

### Parameters - topMarginMode

mode  

### Return Value - topMarginMode

## Method topMarginValue

```xpp
public int topMarginValue([int value])
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

## Method topValue

```xpp
public int topValue([int value])
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

## Method useCaptionFromMenuItem

```xpp
public int useCaptionFromMenuItem([int value])
```

### Parameters - useCaptionFromMenuItem

value  

### Return Value - useCaptionFromMenuItem

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

## Method windowResize

```xpp
public int windowResize([int value])
```

### Parameters - windowResize

value  

### Return Value - windowResize

## Method windowType

```xpp
public int windowType([int value])
```

### Parameters - windowType

value  

### Return Value - windowType

## Method workflowDatasource

```xpp
public int workflowDatasource([AnyType value])
```

### Parameters - workflowDatasource

value  

### Return Value - workflowDatasource

## Method workflowEnabled

```xpp
public boolean workflowEnabled([boolean value])
```

### Parameters - workflowEnabled

value  

### Return Value - workflowEnabled

## Method workflowType

```xpp
public str workflowType([str value])
```

### Parameters - workflowType

value  

### Return Value - workflowType

## Method dialogSize

```xpp
public int dialogSize([int value])
```

### Parameters - dialogSize

value  

### Return Value - dialogSize

