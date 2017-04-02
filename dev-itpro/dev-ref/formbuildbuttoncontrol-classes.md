---
# required metadata

title: F Classes - FormBuildButtonControl to FormBuildFastTabSummarySeparator
description: System API classes that start with the letter F.
author: RobinARH
manager: AnnBe
ms date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: RobinARH
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 58741
ms.assetid: 9af62525-aa36-4d6f-b138-c9002a4b21e2
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# F Classes - FormBuildButtonControl to FormBuildFastTabSummarySeparator

System API classes that start with the letter F.

Class FormBuildButtonControl
----------------------------

    class FormBuildButtonControl extends FormBuildControl

The FormBuildButtonControl class lets you create, read, update, and delete X++ code and metadata.

### Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                                                                                      | Description                                                                                                                             |
|-------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| public int acquireFocus(\[int value\])                                                                      |                                                                                                                                         |
| public boolean alignControl(\[boolean value\])                                                              | Determines whether to align the control.                                                                                                |
| public int alignment(\[int value\])                                                                         |                                                                                                                                         |
| public boolean allowEdit(\[boolean value\])                                                                 | Determines whether the user can change the contents of the control.                                                                     |
| public boolean autoDeclaration(\[boolean value\])                                                           | Determines whether the system can declare a member variable that has the same name as the control.                                      |
| public boolean autoRefreshData(\[boolean value\])                                                           |                                                                                                                                         |
| public int backgroundColor(\[int value\])                                                                   | Gets or sets the background color of the control.                                                                                       |
| public int backStyle(\[int value\])                                                                         | Determines whether the control background can be transparent.                                                                           |
| public boolean big(\[boolean value\])                                                                       |                                                                                                                                         |
| public int bold(\[int value\])                                                                              | Gets or sets the weight of font used to output text in the control.                                                                     |
| public int border(\[int value\])                                                                            | Gets or sets the style of the borderline of the control.                                                                                |
| public int buttonDisplay(\[int value\])                                                                     | Gets or sets the appearance of the button control.                                                                                      |
| public int characterSet(\[int value\])                                                                      | Gets or sets the character set of the font.                                                                                             |
| public int colorScheme(\[int value\])                                                                       | Gets or sets the color scheme of the control.                                                                                           |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                    | Gets or sets the configuration key that is assigned to the control.                                                                     |
| public int containerId()                                                                                    | Retrieves the ID of the parent container for the control.                                                                               |
| public str countryRegionCodes(\[str value\])                                                                |                                                                                                                                         |
| public str dataRelationPath(\[str value\])                                                                  |                                                                                                                                         |
| public boolean defaultButton(\[boolean value\])                                                             | Determines whether the button should be the default button on the form.                                                                 |
| public str disabledImage(\[str value\])                                                                     | Gets or sets the disabled image of the button.                                                                                          |
| public int disabledImageLocation(\[int value\])                                                             |                                                                                                                                         |
| public int disabledResource(\[int value\])                                                                  | Gets or sets the resource ID of the image to use as the disabled button image.                                                          |
| public int displayTarget(\[int value\])                                                                     |                                                                                                                                         |
| public int dragDrop(\[int value\])                                                                          | Determines whether to enable or disable drag-and-drop operations for the control.                                                       |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether to enable or disable the object.                                                                                     |
| public str font(\[str value\])                                                                              | Gets or sets the name of the font for the control to use.                                                                               |
| public int fontSize(\[int value\])                                                                          | Gets or sets the size of the font for the control to use.                                                                               |
| public boolean forcedToOverflow(\[boolean value\])                                                          |                                                                                                                                         |
| public int foregroundColor(\[int value\])                                                                   | Gets or sets the text color for the control to use.                                                                                     |
| public int height(int value, \[int mode\])                                                                  | Gets or sets the height of the control.                                                                                                 |
| public int heightMode(\[int value\])                                                                        | Gets or sets a calculation mode for the height of the control.                                                                          |
| public int heightValue(\[int value\])                                                                       | Gets or sets the height of the control.                                                                                                 |
| public str helpText(\[str value\])                                                                          | Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.                                |
| public str hierarchyParent(\[str value\])                                                                   |                                                                                                                                         |
| public int id()                                                                                             | Retrieves the ID of the control.                                                                                                        |
| public int imageLocation(\[int value\])                                                                     |                                                                                                                                         |
| public boolean isContainer()                                                                                | Retrieves a value that indicates whether the control is a container control.                                                            |
| public boolean italic(\[boolean value\])                                                                    |                                                                                                                                         |
| public str keyTip(\[str value\])                                                                            |                                                                                                                                         |
| public int left(int value, \[int mode\])                                                                    |                                                                                                                                         |
| public int leftMode(\[int value\])                                                                          |                                                                                                                                         |
| public int leftValue(\[int value\])                                                                         |                                                                                                                                         |
| public int multiSelect(\[int value\])                                                                       |                                                                                                                                         |
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics 365 for Operations application object. |
| public int neededPermission(\[int value\])                                                                  |                                                                                                                                         |
| public int needsRecord(\[int value\])                                                                       |                                                                                                                                         |
| public str normalImage(\[str value\])                                                                       |                                                                                                                                         |
| public int normalResource(\[int value\])                                                                    |                                                                                                                                         |
| public boolean primary(\[boolean value\])                                                                   |                                                                                                                                         |
| public boolean saveRecord(\[boolean value\])                                                                |                                                                                                                                         |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                   |                                                                                                                                         |
| public int shortkey(\[int value\])                                                                          |                                                                                                                                         |
| public boolean showShortCut(\[boolean value\])                                                              |                                                                                                                                         |
| public boolean skip(\[boolean value\])                                                                      | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.         |
| public int style(\[int value\])                                                                             |                                                                                                                                         |
| public str text(\[str value\])                                                                              |                                                                                                                                         |
| public int toggleButton(\[int value\])                                                                      |                                                                                                                                         |
| public int toggleValue(\[int value\])                                                                       |                                                                                                                                         |
| public int top(int value, \[int mode\])                                                                     |                                                                                                                                         |
| public int topMode(\[int value\])                                                                           |                                                                                                                                         |
| public int topValue(\[int value\])                                                                          |                                                                                                                                         |
| public int type(\[int value\])                                                                              |                                                                                                                                         |
| public boolean underline(\[boolean value\])                                                                 | Sets or returns the underline property for the text in the control.                                                                     |
| public int userData(\[int value\])                                                                          |                                                                                                                                         |
| public int userDataItem(\[int value\])                                                                      |                                                                                                                                         |
| public int userDataItems(\[int value\])                                                                     |                                                                                                                                         |
| public boolean value(\[boolean value\])                                                                     |                                                                                                                                         |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                |                                                                                                                                         |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                      |                                                                                                                                         |
| public int verticalSpacingValue(\[int value\])                                                              |                                                                                                                                         |
| public boolean visible(\[boolean value\])                                                                   |                                                                                                                                         |
| public int width(int value, \[int mode\])                                                                   | Gets or sets the width of the control.                                                                                                  |
| public int widthMode(\[int value\])                                                                         | Gets or sets the calculation mode of the width of the control.                                                                          |
| public int widthValue(\[int value\])                                                                        | Gets or sets the width of the control.                                                                                                  |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                         |

### Method acquireFocus

    public int acquireFocus([int value])

#### Parameters

value  

#### Return Value

### Method alignControl

Determines whether to align the control.

    public boolean alignControl([boolean value])

#### Parameters

value  

#### Return Value

true if the control should be aligned; otherwise, false.

#### Remarks

The upper-left corner of the control is aligned according to the longest label.

### Method alignment

    public int alignment([int value])

#### Parameters

value  

#### Return Value

### Method allowEdit

Determines whether the user can change the contents of the control.

    public boolean allowEdit([boolean value])

#### Parameters

value  

#### Return Value

true if the control can be edited; otherwise, false.

#### Remarks

When this property is set on a container control, modifications are disabled or enabled for all controls within the container.

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method autoRefreshData

    public boolean autoRefreshData([boolean value])

#### Parameters

value  

#### Return Value

### Method backgroundColor

Gets or sets the background color of the control.

    public int backgroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method backStyle

Determines whether the control background can be transparent.

    public int backStyle([int value])

#### Parameters

value  

#### Return Value

1 if the control background can be transparent; otherwise, 0.

### Method big

    public boolean big([boolean value])

#### Parameters

value  

#### Return Value

### Method bold

Gets or sets the weight of font used to output text in the control.

    public int bold([int value])

#### Parameters

value  

#### Return Value

An integer value between zero and nine, inclusive.

#### Remarks

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

### Method border

Gets or sets the style of the borderline of the control.

    public int border([int value])

#### Parameters

value  

#### Return Value

An integer between zero and four, inclusive.

#### Remarks

The integer that is returned contains the style of the borderline of the control as follows:

| Value. | Description. |
|--------|--------------|
| 0      | Auto.        |
| 1      | 3D.          |
| 2      | Single line. |
| 3      | Flat.        |
| 4      | None.        |

### Method buttonDisplay

Gets or sets the appearance of the button control.

    public int buttonDisplay([int value])

#### Parameters

value  

#### Return Value

An integer between zero and five, inclusive.

#### Remarks

The value of the property defines whether the text, the image, or both should be displayed on the button. This property also controls relative positions of text and image if both are displayed. The integer value that is returned contains the appearance of the button control as follows:

| Value. | Description.                                                     |
|--------|------------------------------------------------------------------|
| 0      | Text only.                                                       |
| 1      | Image Only.                                                      |
| 2      | Text and image; the image is displayed below the text.           |
| 3      | Text and image; the image is displayed above the text.           |
| 4      | Text and image; the image is displayed to the left of the text.  |
| 5      | Text and image; the image is displayed to the right of the text. |

### Method characterSet

Gets or sets the character set of the font.

    public int characterSet([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the character set of the font.

#### Remarks

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

The default character set is set to a value based on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET. For more information, see the LOGFONT structure on the MSDN Web site, http://go.microsoft.com/fwlink/?LinkID=85972.

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  

#### Return Value

An integer between zero and two, inclusive.

#### Remarks

The color scheme is defined according to the following table:

| Value. | Style.                         |
|--------|--------------------------------|
| 0      | Default.                       |
| 1      | The Microsoft Windows palette. |
| 2      | The true-color scheme.         |

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method containerId

Retrieves the ID of the parent container for the control.

    public int containerId()

#### Return Value

The ID of the parent container.

### Method countryRegionCodes

    public str countryRegionCodes([str value])

#### Parameters

value  

#### Return Value

### Method dataRelationPath

    public str dataRelationPath([str value])

#### Parameters

value  

#### Return Value

### Method defaultButton

Determines whether the button should be the default button on the form.

    public boolean defaultButton([boolean value])

#### Parameters

value  

#### Return Value

true if the button should be the default button; otherwise, false.

### Method disabledImage

Gets or sets the disabled image of the button.

    public str disabledImage([str value])

#### Parameters

value  

#### Return Value

The full name of an image file. The system supports all of the GDI-supported image formats.

#### Remarks

This property has precedence over the disabledResource property . It is used if both of these properties are set.

### Method disabledImageLocation

    public int disabledImageLocation([int value])

#### Parameters

value  

#### Return Value

### Method disabledResource

Gets or sets the resource ID of the image to use as the disabled button image.

    public int disabledResource([int value])

#### Parameters

value  

#### Return Value

The resource ID of the image to use as the disabled button image. Both icon and bitmap images are supported.

### Method displayTarget

    public int displayTarget([int value])

#### Parameters

value  

#### Return Value

### Method dragDrop

Determines whether to enable or disable drag-and-drop operations for the control.

    public int dragDrop([int value])

#### Parameters

value  

#### Return Value

1 if drag-and-drop operations are enabled; otherwise, false.

### Method enabled

Determines whether to enable or disable the object.

    public boolean enabled([boolean value])

#### Parameters

value  

#### Return Value

true if the object is enabled; otherwise, false.

#### Remarks

The enabled property allows controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

### Method font

Gets or sets the name of the font for the control to use.

    public str font([str value])

#### Parameters

value  

#### Return Value

The name of the font to use, such as Tahoma or Verdana.

### Method fontSize

Gets or sets the size of the font for the control to use.

    public int fontSize([int value])

#### Parameters

value  

#### Return Value

The height of the font in points.

### Method forcedToOverflow

    public boolean forcedToOverflow([boolean value])

#### Parameters

value  

#### Return Value

### Method foregroundColor

Gets or sets the text color for the control to use.

    public int foregroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method height

Gets or sets the height of the control.

    public int height(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

The height of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the height according to the following table:

| Mode.            | Height calculation.                                                                       |
|------------------|-------------------------------------------------------------------------------------------|
| -1 Exact.        | The exact height in pixels of the controls is used.                                       |
| 0 Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height. | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

### Method heightMode

Gets or sets a calculation mode for the height of the control.

    public int heightMode([int value])

#### Parameters

value  

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table:

| Mode.          | Height Calculation.                                                                       |
|----------------|-------------------------------------------------------------------------------------------|
| Exact.         | The exact height in pixels of the controls is used.                                       |
| Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height. | The layout of the form determines the height of the control.                              |

The height of the control might change when the mode is set to auto or column height.

### Method heightValue

Gets or sets the height of the control.

    public int heightValue([int value])

#### Parameters

value  

#### Return Value

The height in pixels.

#### Remarks

The height of the control is not changed unless the exact height calculation mode is used.

### Method helpText

Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property sheet. The help text must not exceed 250 characters.

### Method hierarchyParent

    public str hierarchyParent([str value])

#### Parameters

value  

#### Return Value

### Method id

Retrieves the ID of the control.

    public int id()

#### Return Value

The ID of the control.

### Method imageLocation

    public int imageLocation([int value])

#### Parameters

value  

#### Return Value

### Method isContainer

Retrieves a value that indicates whether the control is a container control.

    public boolean isContainer()

#### Return Value

A Boolean value that indicates whether the control is a container control.

### Method italic

    public boolean italic([boolean value])

#### Parameters

value  

#### Return Value

### Method keyTip

    public str keyTip([str value])

#### Parameters

value  

#### Return Value

### Method left

    public int left(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method leftMode

    public int leftMode([int value])

#### Parameters

value  

#### Return Value

### Method leftValue

    public int leftValue([int value])

#### Parameters

value  

#### Return Value

### Method multiSelect

    public int multiSelect([int value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics 365 for Operations application object.

    public str name([str value])

#### Parameters

value  
The name to assign to the control.

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   It must start with a letter.
-   It cannot exceed 250 characters.
-   It can include numbers and underscore (\_) characters.
-   It cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, or classes.

### Method neededPermission

    public int neededPermission([int value])

#### Parameters

value  

#### Return Value

### Method needsRecord

    public int needsRecord([int value])

#### Parameters

value  

#### Return Value

### Method normalImage

    public str normalImage([str value])

#### Parameters

value  

#### Return Value

### Method normalResource

    public int normalResource([int value])

#### Parameters

value  

#### Return Value

### Method primary

    public boolean primary([boolean value])

#### Parameters

value  

#### Return Value

### Method saveRecord

    public boolean saveRecord([boolean value])

#### Parameters

value  

#### Return Value

### Method securityKey

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  

#### Return Value

### Method shortkey

    public int shortkey([int value])

#### Parameters

value  

#### Return Value

### Method showShortCut

    public boolean showShortCut([boolean value])

#### Parameters

value  

#### Return Value

### Method skip

Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.

    public boolean skip([boolean value])

#### Parameters

value  
The value to assign to the skip property of the control.

#### Return Value

true if the control is skipped when the user presses the TAB key to move to the control; otherwise, false.

### Method style

    public int style([int value])

#### Parameters

value  

#### Return Value

### Method text

    public str text([str value])

#### Parameters

value  

#### Return Value

### Method toggleButton

    public int toggleButton([int value])

#### Parameters

value  

#### Return Value

### Method toggleValue

    public int toggleValue([int value])

#### Parameters

value  

#### Return Value

### Method top

    public int top(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method topMode

    public int topMode([int value])

#### Parameters

value  

#### Return Value

### Method topValue

    public int topValue([int value])

#### Parameters

value  

#### Return Value

### Method type

    public int type([int value])

#### Parameters

value  

#### Return Value

### Method underline

Sets or returns the underline property for the text in the control.

    public boolean underline([boolean value])

#### Parameters

value  
The value to assign to the underline property of the control.

#### Return Value

true if the text in the control is underlined; otherwise, false.

### Method userData

    public int userData([int value])

#### Parameters

value  

#### Return Value

### Method userDataItem

    public int userDataItem([int value])

#### Parameters

value  

#### Return Value

### Method userDataItems

    public int userDataItems([int value])

#### Parameters

value  

#### Return Value

### Method value

    public boolean value([boolean value])

#### Parameters

value  

#### Return Value

### Method verticalSpacing

    public int verticalSpacing([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method verticalSpacingMode

    public AutoMode verticalSpacingMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method verticalSpacingValue

    public int verticalSpacingValue([int value])

#### Parameters

value  

#### Return Value

### Method visible

    public boolean visible([boolean value])

#### Parameters

value  

#### Return Value

### Method width

Gets or sets the width of the control.

    public int width(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

The width of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the width according to the following table:

| Mode.           | Width calculation.                                                                       |
|-----------------|------------------------------------------------------------------------------------------|
| -1 Exact.       | The exact width in pixels of the controls is used.                                       |
| 0 Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width. | The layout of the form determines the width of the control.                              |

The width and width calculation mode can be set separately.

### Method widthMode

Gets or sets the calculation mode of the width of the control.

    public int widthMode([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table:

| Mode.         | Width Calculation.                                                                       |
|---------------|------------------------------------------------------------------------------------------|
| Exact.        | The exact width in pixels of the controls is used.                                       |
| Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width. | The layout of the form determines the width of the control.                              |

The width of the control might change when the mode is set to auto or column width.

### Method widthValue

Gets or sets the width of the control.

    public int widthValue([int value])

#### Parameters

value  

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

## Class FormBuildButtonGroupControl
    class FormBuildButtonGroupControl extends FormBuildControl

The FormBuildButtonGroupControl class lets you create, read, update, and delete X++ code and metadata.

### Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                                                                                      | Description                                                                                                                             |
|-------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| public boolean alignChild(\[boolean value\])                                                                |                                                                                                                                         |
| public boolean alignChildren(\[boolean value\])                                                             |                                                                                                                                         |
| public boolean alignControl(\[boolean value\])                                                              | Determines whether to align the control.                                                                                                |
| public boolean allowEdit(\[boolean value\])                                                                 | Determines whether the user can change the contents of the control.                                                                     |
| public int allowUserSetup(\[int value\])                                                                    |                                                                                                                                         |
| public int arrangeGuide(\[int value\])                                                                      |                                                                                                                                         |
| public int arrangeMethod(\[int value\])                                                                     |                                                                                                                                         |
| public int arrangeWhen(\[int value\])                                                                       |                                                                                                                                         |
| public boolean autoDeclaration(\[boolean value\])                                                           | Determines whether the system can declare a member variable that has the same name as the control.                                      |
| public int backgroundColor(\[int value\])                                                                   | Gets or sets the background color of the control.                                                                                       |
| public int backStyle(\[int value\])                                                                         | Determiness whether the control background can be transparent.                                                                          |
| public int bold(\[int value\])                                                                              | Gets or sets the weight of font used to output text in the control.                                                                     |
| public int bottomMargin(\[int value\], \[AutoMode mode\])                                                   |                                                                                                                                         |
| public AutoMode bottomMarginMode(\[AutoMode mode\])                                                         |                                                                                                                                         |
| public int bottomMarginValue(\[int value\])                                                                 |                                                                                                                                         |
| public str caption(\[str value\])                                                                           | Gets or set the caption of the control.                                                                                                 |
| public int characterSet(\[int value\])                                                                      | Gets or sets the character set of the font.                                                                                             |
| public int colorScheme(\[int value\])                                                                       | Gets or sets the color scheme of the control.                                                                                           |
| public int columns(\[int value\], \[ColumnsMode mode\])                                                     |                                                                                                                                         |
| public ColumnsMode columnsMode(\[ColumnsMode mode\])                                                        |                                                                                                                                         |
| public int columnspace(\[int value\], \[AutoMode mode\])                                                    |                                                                                                                                         |
| public AutoMode columnspaceMode(\[AutoMode mode\])                                                          |                                                                                                                                         |
| public int columnspaceValue(\[int value\])                                                                  |                                                                                                                                         |
| public int columnsValue(\[int value\])                                                                      |                                                                                                                                         |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                    | Gets or sets the configuration key that is assigned to the control.                                                                     |
| public int containerId()                                                                                    | Retrieves the ID of the parent container for the control.                                                                               |
| public str countryRegionCodes(\[str value\])                                                                |                                                                                                                                         |
| public FieldId countryRegionContextField(\[FieldId value\])                                                 |                                                                                                                                         |
| public str dataRelationPath(\[str value\])                                                                  |                                                                                                                                         |
| public int dataSource(\[AnyType value\])                                                                    | Gets or sets a data source to be used by the control or the form.                                                                       |
| public int displayTarget(\[int value\])                                                                     |                                                                                                                                         |
| public int dragDrop(\[int value\])                                                                          | Determines whether to enable or disable drag-and-drop operations for the control.                                                       |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether to enable or disable the object.                                                                                     |
| public str font(\[str value\])                                                                              | Gets or sets the name of the font for the control to use.                                                                               |
| public int fontSize(\[int value\])                                                                          | Gets or sets the size of the font for the control to use.                                                                               |
| public int framePosition(\[int value\])                                                                     |                                                                                                                                         |
| public int frameType(\[int value\])                                                                         |                                                                                                                                         |
| public int height(int value, \[int mode\])                                                                  | Gets or sets the height of the control.                                                                                                 |
| public int heightMode(\[int value\])                                                                        | Gets or sets a calculation mode for the height of the control.                                                                          |
| public int heightValue(\[int value\])                                                                       | Gets or sets the height of the control.                                                                                                 |
| public str helpText(\[str value\])                                                                          | Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.                                |
| public boolean hideIfEmpty(\[boolean value\])                                                               |                                                                                                                                         |
| public str hierarchyParent(\[str value\])                                                                   |                                                                                                                                         |
| public int id()                                                                                             | Retrieves the ID of the control.                                                                                                        |
| public boolean isContainer()                                                                                | Retrieves a value that indicates whether the control is a container control.                                                            |
| public boolean italic(\[boolean value\])                                                                    |                                                                                                                                         |
| public str keyTip(\[str value\])                                                                            |                                                                                                                                         |
| public int left(int value, \[int mode\])                                                                    |                                                                                                                                         |
| public int leftMargin(\[int value\], \[AutoMode mode\])                                                     |                                                                                                                                         |
| public AutoMode leftMarginMode(\[AutoMode mode\])                                                           |                                                                                                                                         |
| public int leftMarginValue(\[int value\])                                                                   |                                                                                                                                         |
| public int leftMode(\[int value\])                                                                          |                                                                                                                                         |
| public int leftValue(\[int value\])                                                                         |                                                                                                                                         |
| public int moveControl(int controlId, \[int insertAfterControlId\])                                         | Moves a specified control to the control.                                                                                               |
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics 365 for Operations application object. |
| public int neededPermission(\[int value\])                                                                  |                                                                                                                                         |
| public int rightMargin(\[int value\], \[AutoMode mode\])                                                    |                                                                                                                                         |
| public AutoMode rightMarginMode(\[AutoMode mode\])                                                          |                                                                                                                                         |
| public int rightMarginValue(\[int value\])                                                                  |                                                                                                                                         |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                   |                                                                                                                                         |
| public boolean sizeHeight(\[boolean value\])                                                                |                                                                                                                                         |
| public boolean sizeWidth(\[boolean value\])                                                                 |                                                                                                                                         |
| public boolean skip(\[boolean value\])                                                                      | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.         |
| public int style(\[int value\])                                                                             |                                                                                                                                         |
| public int top(int value, \[int mode\])                                                                     |                                                                                                                                         |
| public int topMargin(\[int value\], \[AutoMode mode\])                                                      |                                                                                                                                         |
| public AutoMode topMarginMode(\[AutoMode mode\])                                                            |                                                                                                                                         |
| public int topMarginValue(\[int value\])                                                                    |                                                                                                                                         |
| public int topMode(\[int value\])                                                                           |                                                                                                                                         |
| public int topValue(\[int value\])                                                                          |                                                                                                                                         |
| public int type(\[int value\])                                                                              |                                                                                                                                         |
| public boolean underline(\[boolean value\])                                                                 | Sets or returns the underline property for the text in the control.                                                                     |
| public int userData(\[int value\])                                                                          |                                                                                                                                         |
| public int userDataItem(\[int value\])                                                                      |                                                                                                                                         |
| public int userDataItems(\[int value\])                                                                     |                                                                                                                                         |
| public boolean useUserLayout(\[boolean value\])                                                             |                                                                                                                                         |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                |                                                                                                                                         |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                      |                                                                                                                                         |
| public int verticalSpacingValue(\[int value\])                                                              |                                                                                                                                         |
| public boolean visible(\[boolean value\])                                                                   |                                                                                                                                         |
| public int width(int value, \[int mode\])                                                                   | Gets or sets the width of the control.                                                                                                  |
| public int widthMode(\[int value\])                                                                         | Gets or sets the calculation mode of the width of the control.                                                                          |
| public int widthValue(\[int value\])                                                                        | Gets or sets the width of the control.                                                                                                  |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                         |

### Method alignChild

    public boolean alignChild([boolean value])

#### Parameters

value  

#### Return Value

### Method alignChildren

    public boolean alignChildren([boolean value])

#### Parameters

value  

#### Return Value

### Method alignControl

Determines whether to align the control.

    public boolean alignControl([boolean value])

#### Parameters

value  

#### Return Value

true if the control should be aligned; otherwise, false.

#### Remarks

The upper-left corner of the control is aligned according to the longest label.

### Method allowEdit

Determines whether the user can change the contents of the control.

    public boolean allowEdit([boolean value])

#### Parameters

value  

#### Return Value

true if the control can be edited; otherwise, false.

#### Remarks

When this property is set on a container control, modifications are disabled or enabled for all controls within the container.

### Method allowUserSetup

    public int allowUserSetup([int value])

#### Parameters

value  

#### Return Value

### Method arrangeGuide

    public int arrangeGuide([int value])

#### Parameters

value  

#### Return Value

### Method arrangeMethod

    public int arrangeMethod([int value])

#### Parameters

value  

#### Return Value

### Method arrangeWhen

    public int arrangeWhen([int value])

#### Parameters

value  

#### Return Value

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method backgroundColor

Gets or sets the background color of the control.

    public int backgroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method backStyle

Determiness whether the control background can be transparent.

    public int backStyle([int value])

#### Parameters

value  

#### Return Value

1 if the control background can be transparent; otherwise, 0.

### Method bold

Gets or sets the weight of font used to output text in the control.

    public int bold([int value])

#### Parameters

value  

#### Return Value

An integer value between zero and nine, inclusive.

#### Remarks

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

### Method bottomMargin

    public int bottomMargin([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method bottomMarginMode

    public AutoMode bottomMarginMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method bottomMarginValue

    public int bottomMarginValue([int value])

#### Parameters

value  

#### Return Value

### Method caption

Gets or set the caption of the control.

    public str caption([str value])

#### Parameters

value  

#### Return Value

The string that is used as the caption of the control.

### Method characterSet

Gets or sets the character set of the font.

    public int characterSet([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the character set of the font.

#### Remarks

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

The default character set is set to a value based on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET.For more information, see the LOGFONT structure on the MSDN Web site, http://go.microsoft.com/fwlink/?LinkID=85972.

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  

#### Return Value

An integer between zero and two, inclusive.

#### Remarks

The color scheme is defined according to the following table:

| Value. | Style.                         |
|--------|--------------------------------|
| 0      | Default.                       |
| 1      | The Microsoft Windows palette. |
| 2      | The true-color scheme.         |

### Method columns

    public int columns([int value], [ColumnsMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method columnsMode

    public ColumnsMode columnsMode([ColumnsMode mode])

#### Parameters

mode  

#### Return Value

### Method columnspace

    public int columnspace([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method columnspaceMode

    public AutoMode columnspaceMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method columnspaceValue

    public int columnspaceValue([int value])

#### Parameters

value  

#### Return Value

### Method columnsValue

    public int columnsValue([int value])

#### Parameters

value  

#### Return Value

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method containerId

Retrieves the ID of the parent container for the control.

    public int containerId()

#### Return Value

The ID of the parent container.

### Method countryRegionCodes

    public str countryRegionCodes([str value])

#### Parameters

value  

#### Return Value

### Method countryRegionContextField

    public FieldId countryRegionContextField([FieldId value])

#### Parameters

value  

#### Return Value

### Method dataRelationPath

    public str dataRelationPath([str value])

#### Parameters

value  

#### Return Value

### Method dataSource

Gets or sets a data source to be used by the control or the form.

    public int dataSource([AnyType value])

#### Parameters

value  

#### Return Value

The identifier of the data source to be used.

### Method displayTarget

    public int displayTarget([int value])

#### Parameters

value  

#### Return Value

### Method dragDrop

Determines whether to enable or disable drag-and-drop operations for the control.

    public int dragDrop([int value])

#### Parameters

value  

#### Return Value

1 if drag-and-drop operations are enabled; otherwise, false.

### Method enabled

Determines whether to enable or disable the object.

    public boolean enabled([boolean value])

#### Parameters

value  

#### Return Value

true if the object is enabled; otherwise, false.

#### Remarks

The enabled property allows controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

### Method font

Gets or sets the name of the font for the control to use.

    public str font([str value])

#### Parameters

value  

#### Return Value

The name of the font to use, such as Tahoma or Verdana.

### Method fontSize

Gets or sets the size of the font for the control to use.

    public int fontSize([int value])

#### Parameters

value  

#### Return Value

The height of the font in points.

### Method framePosition

    public int framePosition([int value])

#### Parameters

value  

#### Return Value

### Method frameType

    public int frameType([int value])

#### Parameters

value  

#### Return Value

### Method height

Gets or sets the height of the control.

    public int height(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

The height of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the height according to the following table:

| Mode.            | Height calculation.                                                                       |
|------------------|-------------------------------------------------------------------------------------------|
| -1 Exact.        | The exact height in pixels of the controls is used.                                       |
| 0 Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height. | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

### Method heightMode

Gets or sets a calculation mode for the height of the control.

    public int heightMode([int value])

#### Parameters

value  

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table:

| Mode.          | Height Calculation.                                                                       |
|----------------|-------------------------------------------------------------------------------------------|
| Exact.         | The exact height in pixels of the controls is used.                                       |
| Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height. | The layout of the form determines the height of the control.                              |

The height of the control might change when the mode is set to auto or column height.

### Method heightValue

Gets or sets the height of the control.

    public int heightValue([int value])

#### Parameters

value  

#### Return Value

The height in pixels.

#### Remarks

The height of the control is not changed unless the exact height calculation mode is used.

### Method helpText

Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property sheet. The help text must not exceed 250 characters.

### Method hideIfEmpty

    public boolean hideIfEmpty([boolean value])

#### Parameters

value  

#### Return Value

### Method hierarchyParent

    public str hierarchyParent([str value])

#### Parameters

value  

#### Return Value

### Method id

Retrieves the ID of the control.

    public int id()

#### Return Value

The ID of the control.

### Method isContainer

Retrieves a value that indicates whether the control is a container control.

    public boolean isContainer()

#### Return Value

A Boolean value that indicates whether the control is a container control.

### Method italic

    public boolean italic([boolean value])

#### Parameters

value  

#### Return Value

### Method keyTip

    public str keyTip([str value])

#### Parameters

value  

#### Return Value

### Method left

    public int left(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method leftMargin

    public int leftMargin([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method leftMarginMode

    public AutoMode leftMarginMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method leftMarginValue

    public int leftMarginValue([int value])

#### Parameters

value  

#### Return Value

### Method leftMode

    public int leftMode([int value])

#### Parameters

value  

#### Return Value

### Method leftValue

    public int leftValue([int value])

#### Parameters

value  

#### Return Value

### Method moveControl

Moves a specified control to the control.

    public int moveControl(int controlId, [int insertAfterControlId])

#### Parameters

controlId  

<!-- -->

insertAfterControlId  

#### Return Value

1 if the control was moved successfully; otherwise, 0.

#### Remarks

In general, if the specified control can be contained in the control and can be moved from the container that it is currently in, this method should succeed. However, in some cases, such as for the reference group control instance, controls cannot be moved.

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics 365 for Operations application object.

    public str name([str value])

#### Parameters

value  
The name to assign to the control.

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   It must start with a letter.
-   It cannot exceed 250 characters.
-   It can include numbers and underscore (\_) characters.
-   It cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, or classes.

### Method neededPermission

    public int neededPermission([int value])

#### Parameters

value  

#### Return Value

### Method rightMargin

    public int rightMargin([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method rightMarginMode

    public AutoMode rightMarginMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method rightMarginValue

    public int rightMarginValue([int value])

#### Parameters

value  

#### Return Value

### Method securityKey

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  

#### Return Value

### Method sizeHeight

    public boolean sizeHeight([boolean value])

#### Parameters

value  

#### Return Value

### Method sizeWidth

    public boolean sizeWidth([boolean value])

#### Parameters

value  

#### Return Value

### Method skip

Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.

    public boolean skip([boolean value])

#### Parameters

value  
The value to assign to the skip property of the control.

#### Return Value

true if the control is skipped when the user presses the TAB key to move to the control; otherwise, false.

### Method style

    public int style([int value])

#### Parameters

value  

#### Return Value

### Method top

    public int top(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method topMargin

    public int topMargin([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method topMarginMode

    public AutoMode topMarginMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method topMarginValue

    public int topMarginValue([int value])

#### Parameters

value  

#### Return Value

### Method topMode

    public int topMode([int value])

#### Parameters

value  

#### Return Value

### Method topValue

    public int topValue([int value])

#### Parameters

value  

#### Return Value

### Method type

    public int type([int value])

#### Parameters

value  

#### Return Value

### Method underline

Sets or returns the underline property for the text in the control.

    public boolean underline([boolean value])

#### Parameters

value  
The value to assign to the underline property of the control.

#### Return Value

true if the text in the control is underlined; otherwise, false.

### Method userData

    public int userData([int value])

#### Parameters

value  

#### Return Value

### Method userDataItem

    public int userDataItem([int value])

#### Parameters

value  

#### Return Value

### Method userDataItems

    public int userDataItems([int value])

#### Parameters

value  

#### Return Value

### Method useUserLayout

    public boolean useUserLayout([boolean value])

#### Parameters

value  

#### Return Value

### Method verticalSpacing

    public int verticalSpacing([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method verticalSpacingMode

    public AutoMode verticalSpacingMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method verticalSpacingValue

    public int verticalSpacingValue([int value])

#### Parameters

value  

#### Return Value

### Method visible

    public boolean visible([boolean value])

#### Parameters

value  

#### Return Value

### Method width

Gets or sets the width of the control.

    public int width(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

The width of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted.Calculate the width according to the following table:

| Mode.           | Width calculation.                                                                       |
|-----------------|------------------------------------------------------------------------------------------|
| -1 Exact.       | The exact width in pixels of the controls is used.                                       |
| 0 Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width. | The layout of the form determines the width of the control.                              |

The width and width calculation mode can be set separately.

### Method widthMode

Gets or sets the calculation mode of the width of the control.

    public int widthMode([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table:

| Mode.         | Width Calculation.                                                                       |
|---------------|------------------------------------------------------------------------------------------|
| Exact.        | The exact width in pixels of the controls is used.                                       |
| Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width. | The layout of the form determines the width of the control.                              |

The width of the control might change when the mode is set to auto or column width.

### Method widthValue

Gets or sets the width of the control.

    public int widthValue([int value])

#### Parameters

value  

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

## Class FormBuildButtonSeparatorControl
    class FormBuildButtonSeparatorControl extends FormBuildControl

The FormBuildButtonSeparatorControl class lets you create, read, update, and delete X++ code and metadata.

### Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                                                                                      | Description                                                                                                                                   |
|-------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| public boolean alignControl(\[boolean value\])                                                              | Determines whether to align the control.                                                                                                      |
| public boolean allowEdit(\[boolean value\])                                                                 | Determines whether the user can change the contents of the control.                                                                           |
| public boolean autoDeclaration(\[boolean value\])                                                           | Determines whether the system can declare a member variable that has the same name as the control.                                            |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                    | Gets or sets the configuration key that is assigned to the control.                                                                           |
| public int containerId()                                                                                    | Retrieves the ID of the parent container for the control.                                                                                     |
| public str countryRegionCodes(\[str value\])                                                                |                                                                                                                                               |
| public str dataRelationPath(\[str value\])                                                                  |                                                                                                                                               |
| public int displayTarget(\[int value\])                                                                     |                                                                                                                                               |
| public int dragDrop(\[int value\])                                                                          | Determines whether to enable or disable drag-and-drop operations for the control.                                                             |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether to enable or disable the object.                                                                                           |
| public int height(int value, \[int mode\])                                                                  | Gets or sets the height of the control.                                                                                                       |
| public int heightMode(\[int value\])                                                                        | Gets or sets a calculation mode for the height of the control.                                                                                |
| public int heightValue(\[int value\])                                                                       | Gets or sets the height of the control.                                                                                                       |
| public str helpText(\[str value\])                                                                          | Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.                                      |
| public str hierarchyParent(\[str value\])                                                                   |                                                                                                                                               |
| public int id()                                                                                             | Retrieves the ID of the control.                                                                                                              |
| public boolean isContainer()                                                                                | Retrieves a value that indicates whether the control is a container control.                                                                  |
| public int left(int value, \[int mode\])                                                                    |                                                                                                                                               |
| public int leftMode(\[int value\])                                                                          |                                                                                                                                               |
| public int leftValue(\[int value\])                                                                         |                                                                                                                                               |
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics 365 for Operations application object. |
| public int neededPermission(\[int value\])                                                                  |                                                                                                                                               |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                   |                                                                                                                                               |
| public boolean skip(\[boolean value\])                                                                      |                                                                                                                                               |
| public str text(\[str value\])                                                                              |                                                                                                                                               |
| public int top(int value, \[int mode\])                                                                     |                                                                                                                                               |
| public int topMode(\[int value\])                                                                           |                                                                                                                                               |
| public int topValue(\[int value\])                                                                          |                                                                                                                                               |
| public int type(\[int value\])                                                                              |                                                                                                                                               |
| public int userData(\[int value\])                                                                          |                                                                                                                                               |
| public int userDataItem(\[int value\])                                                                      |                                                                                                                                               |
| public int userDataItems(\[int value\])                                                                     |                                                                                                                                               |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                |                                                                                                                                               |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                      |                                                                                                                                               |
| public int verticalSpacingValue(\[int value\])                                                              |                                                                                                                                               |
| public boolean visible(\[boolean value\])                                                                   |                                                                                                                                               |
| public int width(int value, \[int mode\])                                                                   | Gets or sets the width of the control.                                                                                                        |
| public int widthMode(\[int value\])                                                                         | Gets or sets the calculation mode of the width of the control.                                                                                |
| public int widthValue(\[int value\])                                                                        | Gets or sets the width of the control.                                                                                                        |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                               |

### Method alignControl

Determines whether to align the control.

    public boolean alignControl([boolean value])

#### Parameters

value  

#### Return Value

true if the control should be aligned; otherwise, false.

#### Remarks

The upper-left corner of the control is aligned according to the longest label.

### Method allowEdit

Determines whether the user can change the contents of the control.

    public boolean allowEdit([boolean value])

#### Parameters

value  

#### Return Value

true if the control can be edited; otherwise, false.

#### Remarks

When this property is set on a container control, modifications are disabled or enabled for all controls in the container.

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method containerId

Retrieves the ID of the parent container for the control.

    public int containerId()

#### Return Value

The ID of the parent container.

### Method countryRegionCodes

    public str countryRegionCodes([str value])

#### Parameters

value  

#### Return Value

### Method dataRelationPath

    public str dataRelationPath([str value])

#### Parameters

value  

#### Return Value

### Method displayTarget

    public int displayTarget([int value])

#### Parameters

value  

#### Return Value

### Method dragDrop

Determines whether to enable or disable drag-and-drop operations for the control.

    public int dragDrop([int value])

#### Parameters

value  

#### Return Value

1 if drag-and-drop operations are enabled; otherwise, false.

### Method enabled

Determines whether to enable or disable the object.

    public boolean enabled([boolean value])

#### Parameters

value  

#### Return Value

true if the object is enabled; otherwise, false.

#### Remarks

The enabled property allows for controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

### Method height

Gets or sets the height of the control.

    public int height(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

The height of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the height according to the following table:

| Mode.            | Height calculation.                                                                       |
|------------------|-------------------------------------------------------------------------------------------|
| -1 Exact.        | The exact height in pixels of the controls is used.                                       |
| 0 Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height. | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

### Method heightMode

Gets or sets a calculation mode for the height of the control.

    public int heightMode([int value])

#### Parameters

value  

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table:

| Mode.          | Height Calculation.                                                                       |
|----------------|-------------------------------------------------------------------------------------------|
| Exact.         | The exact height in pixels of the controls is used.                                       |
| Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height. | The layout of the form determines the height of the control.                              |

The height of the control might change when the mode is set to auto or column height.

### Method heightValue

Gets or sets the height of the control.

    public int heightValue([int value])

#### Parameters

value  

#### Return Value

The height in pixels.

#### Remarks

The height of the control is not changed unless the exact height calculation mode is used.

### Method helpText

Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property dialog box.The help text must not exceed 250 characters.

### Method hierarchyParent

    public str hierarchyParent([str value])

#### Parameters

value  

#### Return Value

### Method id

Retrieves the ID of the control.

    public int id()

#### Return Value

The ID of the control.

### Method isContainer

Retrieves a value that indicates whether the control is a container control.

    public boolean isContainer()

#### Return Value

A Boolean value that indicates whether the control is a container control.

### Method left

    public int left(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method leftMode

    public int leftMode([int value])

#### Parameters

value  

#### Return Value

### Method leftValue

    public int leftValue([int value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics 365 for Operations application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in the code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

### Method neededPermission

    public int neededPermission([int value])

#### Parameters

value  

#### Return Value

### Method securityKey

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  

#### Return Value

### Method skip

    public boolean skip([boolean value])

#### Parameters

value  

#### Return Value

### Method text

    public str text([str value])

#### Parameters

value  

#### Return Value

### Method top

    public int top(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method topMode

    public int topMode([int value])

#### Parameters

value  

#### Return Value

### Method topValue

    public int topValue([int value])

#### Parameters

value  

#### Return Value

### Method type

    public int type([int value])

#### Parameters

value  

#### Return Value

### Method userData

    public int userData([int value])

#### Parameters

value  

#### Return Value

### Method userDataItem

    public int userDataItem([int value])

#### Parameters

value  

#### Return Value

### Method userDataItems

    public int userDataItems([int value])

#### Parameters

value  

#### Return Value

### Method verticalSpacing

    public int verticalSpacing([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method verticalSpacingMode

    public AutoMode verticalSpacingMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method verticalSpacingValue

    public int verticalSpacingValue([int value])

#### Parameters

value  

#### Return Value

### Method visible

    public boolean visible([boolean value])

#### Parameters

value  

#### Return Value

### Method width

Gets or sets the width of the control.

    public int width(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

The width of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted.Calculate the width according to the following table:

| Mode.           | Width calculation.                                                                       |
|-----------------|------------------------------------------------------------------------------------------|
| -1 Exact.       | The exact width in pixels of the controls is used.                                       |
| 0 Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width. | The layout of the form determines the width of the control.                              |

The width and width calculation mode can be set separately.

### Method widthMode

Gets or sets the calculation mode of the width of the control.

    public int widthMode([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table:

| Mode.         | Width Calculation.                                                                       |
|---------------|------------------------------------------------------------------------------------------|
| Exact.        | The exact width in pixels of the controls is used.                                       |
| Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width. | The layout of the form determines the width of the control.                              |

The width of the control might change when the mode is set to auto or column width.

### Method widthValue

Gets or sets the width of the control.

    public int widthValue([int value])

#### Parameters

value  

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

## Class FormBuildCheckBoxControl
    class FormBuildCheckBoxControl extends FormBuildControl

The FormBuildCheckBoxControl class lets you create, read, update, and delete X++ code and metadata.

### Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                                                                                      | Description                                                                                                                             |
|-------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| public boolean alignControl(\[boolean value\])                                                              | Determines whether to align the control.                                                                                                |
| public boolean allowEdit(\[boolean value\])                                                                 | Determines whether the user can change the contents of the control.                                                                     |
| public boolean autoDeclaration(\[boolean value\])                                                           | Determines whether the system can declare a member variable that has the same name as the control.                                      |
| public int backgroundColor(\[int value\])                                                                   | Gets or sets the background color of the control.                                                                                       |
| public int backStyle(\[int value\])                                                                         | Determines whether the control background can be transparent.                                                                           |
| public int cacheDataMethod(\[int value\])                                                                   |                                                                                                                                         |
| public int colorScheme(\[int value\])                                                                       | Gets or sets the color scheme of the control.                                                                                           |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                    | Gets or sets the configuration key that is assigned to the control.                                                                     |
| public int containerId()                                                                                    | Retrieves the ID of the parent container for the control.                                                                               |
| public str countryRegionCodes(\[str value\])                                                                |                                                                                                                                         |
| public FieldId countryRegionContextField(\[FieldId value\])                                                 |                                                                                                                                         |
| public FieldId dataField(\[FieldId value\])                                                                 |                                                                                                                                         |
| public str dataMethod(\[str value\])                                                                        |                                                                                                                                         |
| public str dataRelationPath(\[str value\])                                                                  |                                                                                                                                         |
| public int dataSource(\[AnyType value\])                                                                    | Gets or sets a data source that is used by the control or the form.                                                                     |
| public int displayTarget(\[int value\])                                                                     |                                                                                                                                         |
| public int dragDrop(\[int value\])                                                                          | Determines whether to enable or disable drag-and-drop operations for the control.                                                       |
| public boolean drawFocusRect(\[boolean value\])                                                             |                                                                                                                                         |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether to enable or disable the object.                                                                                     |
| public int foregroundColor(\[int value\])                                                                   | Gets or sets the text color for the control to use.                                                                                     |
| public int height(int value, \[int mode\])                                                                  | Gets or sets the height of the control.                                                                                                 |
| public int heightMode(\[int value\])                                                                        | Gets or sets a calculation mode for the height of the control.                                                                          |
| public int heightValue(\[int value\])                                                                       | Gets or sets the height of the control.                                                                                                 |
| public str helpText(\[str value\])                                                                          | Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.                                |
| public str hierarchyParent(\[str value\])                                                                   |                                                                                                                                         |
| public int id()                                                                                             | Retrieves the ID of the control.                                                                                                        |
| public boolean isContainer()                                                                                | Retrieves a value that indicates whether the control is a container control.                                                            |
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
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics 365 for Operations application object. |
| public int neededPermission(\[int value\])                                                                  |                                                                                                                                         |
| public boolean optionalRecordControl(\[boolean value\])                                                     |                                                                                                                                         |
| public int promptrect(\[int value\])                                                                        |                                                                                                                                         |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                   |                                                                                                                                         |
| public boolean showLabel(\[boolean value\])                                                                 |                                                                                                                                         |
| public boolean skip(\[boolean value\])                                                                      | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.         |
| public int style(\[int value\])                                                                             |                                                                                                                                         |
| public int top(int value, \[int mode\])                                                                     |                                                                                                                                         |
| public int topMode(\[int value\])                                                                           |                                                                                                                                         |
| public int topValue(\[int value\])                                                                          |                                                                                                                                         |
| public int type(\[int value\])                                                                              |                                                                                                                                         |
| public int userData(\[int value\])                                                                          |                                                                                                                                         |
| public int userDataItem(\[int value\])                                                                      |                                                                                                                                         |
| public int userDataItems(\[int value\])                                                                     |                                                                                                                                         |
| public int value(\[int value\])                                                                             |                                                                                                                                         |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                |                                                                                                                                         |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                      |                                                                                                                                         |
| public int verticalSpacingValue(\[int value\])                                                              |                                                                                                                                         |
| public int viewEditMode(\[int value\])                                                                      |                                                                                                                                         |
| public boolean visible(\[boolean value\])                                                                   |                                                                                                                                         |
| public int width(int value, \[int mode\])                                                                   | Gets or sets the width of the control.                                                                                                  |
| public int widthMode(\[int value\])                                                                         | Gets or sets the calculation mode of the width of the control.                                                                          |
| public int widthValue(\[int value\])                                                                        | Gets or sets the width of the control.                                                                                                  |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                         |

### Method alignControl

Determines whether to align the control.

    public boolean alignControl([boolean value])

#### Parameters

value  

#### Return Value

true if the control should be aligned; otherwise, false.

#### Remarks

The upper-left corner of the control is aligned according to the longest label.

### Method allowEdit

Determines whether the user can change the contents of the control.

    public boolean allowEdit([boolean value])

#### Parameters

value  

#### Return Value

true if the control can be edited; otherwise, false.

#### Remarks

When this property is set on a container control, modifications are disabled or enabled for all controls in the container.

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method backgroundColor

Gets or sets the background color of the control.

    public int backgroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method backStyle

Determines whether the control background can be transparent.

    public int backStyle([int value])

#### Parameters

value  

#### Return Value

1 if the control background can be transparent; otherwise, 0.

### Method cacheDataMethod

    public int cacheDataMethod([int value])

#### Parameters

value  

#### Return Value

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  

#### Return Value

An integer between zero and two, inclusive.

#### Remarks

The color scheme is defined according to the following table:

| Value. | Style.                        |
|--------|-------------------------------|
| 0      | Default.                      |
| 1      | The MicrosoftWindows palette. |
| 2      | The true-color scheme.        |

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method containerId

Retrieves the ID of the parent container for the control.

    public int containerId()

#### Return Value

The ID of the parent container.

### Method countryRegionCodes

    public str countryRegionCodes([str value])

#### Parameters

value  

#### Return Value

### Method countryRegionContextField

    public FieldId countryRegionContextField([FieldId value])

#### Parameters

value  

#### Return Value

### Method dataField

    public FieldId dataField([FieldId value])

#### Parameters

value  

#### Return Value

### Method dataMethod

    public str dataMethod([str value])

#### Parameters

value  

#### Return Value

### Method dataRelationPath

    public str dataRelationPath([str value])

#### Parameters

value  

#### Return Value

### Method dataSource

Gets or sets a data source that is used by the control or the form.

    public int dataSource([AnyType value])

#### Parameters

value  

#### Return Value

The identifier of the data source to use.

### Method displayTarget

    public int displayTarget([int value])

#### Parameters

value  

#### Return Value

### Method dragDrop

Determines whether to enable or disable drag-and-drop operations for the control.

    public int dragDrop([int value])

#### Parameters

value  

#### Return Value

1 if drag-and-drop operations are enabled; otherwise, false.

### Method drawFocusRect

    public boolean drawFocusRect([boolean value])

#### Parameters

value  

#### Return Value

### Method enabled

Determines whether to enable or disable the object.

    public boolean enabled([boolean value])

#### Parameters

value  

#### Return Value

true if the object is enabled; otherwise, false.

#### Remarks

The enabled property allows for controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

### Method foregroundColor

Gets or sets the text color for the control to use.

    public int foregroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method height

Gets or sets the height of the control.

    public int height(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

The height of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted.Calculate the height according to the following table:

| Mode.            | Height calculation.                                                                       |
|------------------|-------------------------------------------------------------------------------------------|
| -1 Exact.        | The exact height in pixels of the controls is used.                                       |
| 0 Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height. | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

### Method heightMode

Gets or sets a calculation mode for the height of the control.

    public int heightMode([int value])

#### Parameters

value  

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table:

| Mode.          | Height Calculation.                                                                       |
|----------------|-------------------------------------------------------------------------------------------|
| Exact.         | The exact height in pixels of the controls is used.                                       |
| Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height. | The layout of the form determines the height of the control.                              |

The height of the control might change when the mode is set to auto or column height.

### Method heightValue

Gets or sets the height of the control.

    public int heightValue([int value])

#### Parameters

value  

#### Return Value

The height in pixels.

#### Remarks

The height of the control is not changed unless the exact height calculation mode is used.

### Method helpText

Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property sheet. The help text must not exceed 250 characters.

### Method hierarchyParent

    public str hierarchyParent([str value])

#### Parameters

value  

#### Return Value

### Method id

Retrieves the ID of the control.

    public int id()

#### Return Value

The ID of the control.

### Method isContainer

Retrieves a value that indicates whether the control is a container control.

    public boolean isContainer()

#### Return Value

A Boolean value that indicates whether the control is a container control.

### Method label

Gets or sets the label for a control.

    public str label([str value])

#### Parameters

value  

#### Return Value

The current value of the label string.

#### Remarks

The label determines which text is displayed in the control or adjacent to it. The label property value cannot exceed 250 characters.

### Method labelAlignment

    public int labelAlignment([int value])

#### Parameters

value  

#### Return Value

### Method labelBold

    public int labelBold([int value])

#### Parameters

value  

#### Return Value

### Method labelCharacterSet

    public int labelCharacterSet([int value])

#### Parameters

value  

#### Return Value

### Method labelFont

    public str labelFont([str value])

#### Parameters

value  

#### Return Value

### Method labelFontSize

    public int labelFontSize([int value])

#### Parameters

value  

#### Return Value

### Method labelForegroundColor

    public int labelForegroundColor([int value])

#### Parameters

value  

#### Return Value

### Method labelGuide

    public int labelGuide([int value])

#### Parameters

value  

#### Return Value

### Method labelHeight

    public int labelHeight(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method labelHeightMode

    public int labelHeightMode([int value])

#### Parameters

value  

#### Return Value

### Method labelHeightValue

    public int labelHeightValue([int value])

#### Parameters

value  

#### Return Value

### Method labelItalic

    public boolean labelItalic([boolean value])

#### Parameters

value  

#### Return Value

### Method labelPosition

    public int labelPosition([int value])

#### Parameters

value  

#### Return Value

### Method labelUnderline

    public boolean labelUnderline([boolean value])

#### Parameters

value  

#### Return Value

### Method labelWidth

    public int labelWidth(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method labelWidthMode

    public int labelWidthMode([int value])

#### Parameters

value  

#### Return Value

### Method labelWidthValue

    public int labelWidthValue([int value])

#### Parameters

value  

#### Return Value

### Method left

    public int left(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method leftMode

    public int leftMode([int value])

#### Parameters

value  

#### Return Value

### Method leftValue

    public int leftValue([int value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics 365 for Operations application object.

    public str name([str value])

#### Parameters

value  
The name to assign to the control.

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   It must start with a letter.
-   It cannot exceed 250 characters.
-   It can include numbers and underscore (\_) characters.
-   It cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, or classes.

### Method neededPermission

    public int neededPermission([int value])

#### Parameters

value  

#### Return Value

### Method optionalRecordControl

    public boolean optionalRecordControl([boolean value])

#### Parameters

value  

#### Return Value

### Method promptrect

    public int promptrect([int value])

#### Parameters

value  

#### Return Value

### Method securityKey

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  

#### Return Value

### Method showLabel

    public boolean showLabel([boolean value])

#### Parameters

value  

#### Return Value

### Method skip

Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.

    public boolean skip([boolean value])

#### Parameters

value  
The value to assign to the skip property of the control.

#### Return Value

true if the control is skipped when the user presses the TAB key to move to the control; otherwise, false.

### Method style

    public int style([int value])

#### Parameters

value  

#### Return Value

### Method top

    public int top(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method topMode

    public int topMode([int value])

#### Parameters

value  

#### Return Value

### Method topValue

    public int topValue([int value])

#### Parameters

value  

#### Return Value

### Method type

    public int type([int value])

#### Parameters

value  

#### Return Value

### Method userData

    public int userData([int value])

#### Parameters

value  

#### Return Value

### Method userDataItem

    public int userDataItem([int value])

#### Parameters

value  

#### Return Value

### Method userDataItems

    public int userDataItems([int value])

#### Parameters

value  

#### Return Value

### Method value

    public int value([int value])

#### Parameters

value  

#### Return Value

### Method verticalSpacing

    public int verticalSpacing([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method verticalSpacingMode

    public AutoMode verticalSpacingMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method verticalSpacingValue

    public int verticalSpacingValue([int value])

#### Parameters

value  

#### Return Value

### Method viewEditMode

    public int viewEditMode([int value])

#### Parameters

value  

#### Return Value

### Method visible

    public boolean visible([boolean value])

#### Parameters

value  

#### Return Value

### Method width

Gets or sets the width of the control.

    public int width(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

The width of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the width according to the following table:

| Mode.           | Width calculation.                                                                       |
|-----------------|------------------------------------------------------------------------------------------|
| -1 Exact.       | The exact width in pixels of the controls is used.                                       |
| 0 Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width. | The layout of the form determines the width of the control.                              |

The width and width calculation mode can be set separately.

### Method widthMode

Gets or sets the calculation mode of the width of the control.

    public int widthMode([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table:

| Mode.         | Width Calculation.                                                                       |
|---------------|------------------------------------------------------------------------------------------|
| Exact.        | The exact width in pixels of the controls is used.                                       |
| Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width. | The layout of the form determines the width of the control.                              |

The width of the control might change when the mode is set to auto or column width.

### Method widthValue

Gets or sets the width of the control.

    public int widthValue([int value])

#### Parameters

value  

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

## Class FormBuildComboBoxControl
    class FormBuildComboBoxControl extends FormBuildControl

The FormBuildComboBoxControl class lets you create, read, update, and delete X++ code and metadata.

### Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                                                                                      | Description                                                                                                                                   |
|-------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| public boolean alignControl(\[boolean value\])                                                              | Determines whether to align the control.                                                                                                      |
| public boolean allowEdit(\[boolean value\])                                                                 | Determines whether the user can change the contents of the control.                                                                           |
| public boolean appendNew(\[boolean value\])                                                                 |                                                                                                                                               |
| public int arrayIndex(\[int value\])                                                                        |                                                                                                                                               |
| public boolean autoDeclaration(\[boolean value\])                                                           | Determines whether the system can declare a member variable that has the same name as the control.                                            |
| public int backgroundColor(\[int value\])                                                                   | Gets or sets the background color of the control.                                                                                             |
| public int backStyle(\[int value\])                                                                         | Determiness whether the control background can be transparent.                                                                                |
| public int bold(\[int value\])                                                                              | Gets or sets the weight of font that is used to output text in the control.                                                                   |
| public int border(\[int value\])                                                                            | Gets or sets the style of the borderline of the control.                                                                                      |
| public int cacheDataMethod(\[int value\])                                                                   |                                                                                                                                               |
| public int characterSet(\[int value\])                                                                      | Gets or sets the character set of the font.                                                                                                   |
| public int colorScheme(\[int value\])                                                                       | Gets or sets the color scheme of the control.                                                                                                 |
| public int comboType(\[int value\])                                                                         |                                                                                                                                               |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                    | Gets or sets the configuration key that is assigned to the control.                                                                           |
| public int containerId()                                                                                    | Retrieves the ID of the parent container for the control.                                                                                     |
| public str countryRegionCodes(\[str value\])                                                                |                                                                                                                                               |
| public FieldId countryRegionContextField(\[FieldId value\])                                                 |                                                                                                                                               |
| public FieldId dataField(\[FieldId value\])                                                                 |                                                                                                                                               |
| public str dataMethod(\[str value\])                                                                        |                                                                                                                                               |
| public str dataRelationPath(\[str value\])                                                                  |                                                                                                                                               |
| public int dataSource(\[AnyType value\])                                                                    | Gets or sets a data source that will be used by the control or the form.                                                                      |
| public int displayLength(\[int value\], \[AutoMode mode\])                                                  |                                                                                                                                               |
| public AutoMode displayLengthMode(\[AutoMode mode\])                                                        |                                                                                                                                               |
| public int displayLengthValue(\[int value\])                                                                |                                                                                                                                               |
| public int displayTarget(\[int value\])                                                                     |                                                                                                                                               |
| public int dragDrop(\[int value\])                                                                          | Determines whether to enable or disable drag-and-drop operations for the control.                                                             |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether to enable or disable the object.                                                                                           |
| public EnumId enumType(\[EnumId value\])                                                                    |                                                                                                                                               |
| public ExtendedTypeId extendedDataType(\[ExtendedTypeId value\])                                            |                                                                                                                                               |
| public int fastTabSummary(\[int value\])                                                                    |                                                                                                                                               |
| public str font(\[str value\])                                                                              | Gets or sets the name of the font for the control to use.                                                                                     |
| public int fontSize(\[int value\])                                                                          | Gets or sets the size of the font for the control to use.                                                                                     |
| public int foregroundColor(\[int value\])                                                                   | Gets or sets the text color for the control to use.                                                                                           |
| public int height(int value, \[int mode\])                                                                  | Gets or sets the height of the control.                                                                                                       |
| public int heightMode(\[int value\])                                                                        | Gets or sets a calculation mode for the height of the control.                                                                                |
| public int heightValue(\[int value\])                                                                       | Gets or sets the height of the control.                                                                                                       |
| public str helpText(\[str value\])                                                                          | Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.                                      |
| public boolean hideFirstEntry(\[boolean value\])                                                            |                                                                                                                                               |
| public str hierarchyParent(\[str value\])                                                                   |                                                                                                                                               |
| public int id()                                                                                             | Retrieves the ID of the control.                                                                                                              |
| public boolean isContainer()                                                                                | Retrieves a value that indicates whether the control is a container control.                                                                  |
| public boolean italic(\[boolean value\])                                                                    |                                                                                                                                               |
| public int item(\[int value\])                                                                              |                                                                                                                                               |
| public int items(\[int value\])                                                                             |                                                                                                                                               |
| public str label(\[str value\])                                                                             | Gets or sets the label for a control.                                                                                                         |
| public int labelAlignment(\[int value\])                                                                    |                                                                                                                                               |
| public int labelBold(\[int value\])                                                                         |                                                                                                                                               |
| public int labelCharacterSet(\[int value\])                                                                 |                                                                                                                                               |
| public str labelFont(\[str value\])                                                                         |                                                                                                                                               |
| public int labelFontSize(\[int value\])                                                                     |                                                                                                                                               |
| public int labelForegroundColor(\[int value\])                                                              |                                                                                                                                               |
| public int labelGuide(\[int value\])                                                                        |                                                                                                                                               |
| public int labelHeight(int value, \[int mode\])                                                             |                                                                                                                                               |
| public int labelHeightMode(\[int value\])                                                                   |                                                                                                                                               |
| public int labelHeightValue(\[int value\])                                                                  |                                                                                                                                               |
| public boolean labelItalic(\[boolean value\])                                                               |                                                                                                                                               |
| public int labelPosition(\[int value\])                                                                     |                                                                                                                                               |
| public boolean labelUnderline(\[boolean value\])                                                            |                                                                                                                                               |
| public int labelWidth(int value, \[int mode\])                                                              |                                                                                                                                               |
| public int labelWidthMode(\[int value\])                                                                    |                                                                                                                                               |
| public int labelWidthValue(\[int value\])                                                                   |                                                                                                                                               |
| public int left(int value, \[int mode\])                                                                    |                                                                                                                                               |
| public int leftMode(\[int value\])                                                                          |                                                                                                                                               |
| public int leftValue(\[int value\])                                                                         |                                                                                                                                               |
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics 365 for Operations application object. |
| public int neededPermission(\[int value\])                                                                  |                                                                                                                                               |
| public int promptrect(\[int value\])                                                                        |                                                                                                                                               |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                   |                                                                                                                                               |
| public int selection(\[int value\])                                                                         |                                                                                                                                               |
| public boolean showLabel(\[boolean value\])                                                                 |                                                                                                                                               |
| public boolean skip(\[boolean value\])                                                                      | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.               |
| public str text(\[str value\])                                                                              |                                                                                                                                               |
| public int top(int value, \[int mode\])                                                                     |                                                                                                                                               |
| public int topMode(\[int value\])                                                                           |                                                                                                                                               |
| public int topValue(\[int value\])                                                                          |                                                                                                                                               |
| public int type(\[int value\])                                                                              |                                                                                                                                               |
| public boolean underline(\[boolean value\])                                                                 | Sets or returns the underline property for the text in the control.                                                                           |
| public int userData(\[int value\])                                                                          |                                                                                                                                               |
| public int userDataItem(\[int value\])                                                                      |                                                                                                                                               |
| public int userDataItems(\[int value\])                                                                     |                                                                                                                                               |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                |                                                                                                                                               |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                      |                                                                                                                                               |
| public int verticalSpacingValue(\[int value\])                                                              |                                                                                                                                               |
| public int viewEditMode(\[int value\])                                                                      |                                                                                                                                               |
| public boolean visible(\[boolean value\])                                                                   |                                                                                                                                               |
| public int width(int value, \[int mode\])                                                                   | Gets or sets the width of the control.                                                                                                        |
| public int widthMode(\[int value\])                                                                         | Gets or sets the calculation mode of the width of the control.                                                                                |
| public int widthValue(\[int value\])                                                                        | Gets or sets the width of the control.                                                                                                        |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                               |

### Method alignControl

Determines whether to align the control.

    public boolean alignControl([boolean value])

#### Parameters

value  

#### Return Value

true if the control should be aligned; otherwise, false.

#### Remarks

The upper-left corner of the control is aligned according to the longest label.

### Method allowEdit

Determines whether the user can change the contents of the control.

    public boolean allowEdit([boolean value])

#### Parameters

value  

#### Return Value

true if the control can be edited; otherwise, false.

#### Remarks

When this property is set on a container control, modifications are disabled or enabled for all controls in the container.

### Method appendNew

    public boolean appendNew([boolean value])

#### Parameters

value  

#### Return Value

### Method arrayIndex

    public int arrayIndex([int value])

#### Parameters

value  

#### Return Value

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method backgroundColor

Gets or sets the background color of the control.

    public int backgroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method backStyle

Determiness whether the control background can be transparent.

    public int backStyle([int value])

#### Parameters

value  

#### Return Value

1 if the control background can be transparent; otherwise, 0.

### Method bold

Gets or sets the weight of font that is used to output text in the control.

    public int bold([int value])

#### Parameters

value  

#### Return Value

An integer value between zero and nine, inclusive.

#### Remarks

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

### Method border

Gets or sets the style of the borderline of the control.

    public int border([int value])

#### Parameters

value  

#### Return Value

An integer between zero and four, inclusive.

#### Remarks

The integer that is returned contains the style of the borderline of the control as follows:

| Value. | Description. |
|--------|--------------|
| 0      | Auto.        |
| 1      | 3D.          |
| 2      | Single line. |
| 3      | Flat.        |
| 4      | None.        |

### Method cacheDataMethod

    public int cacheDataMethod([int value])

#### Parameters

value  

#### Return Value

### Method characterSet

Gets or sets the character set of the font.

    public int characterSet([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the character set of the font.

#### Remarks

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

The value in the following table is for the Korean language edition of MicrosoftWindows.

| Value. | Description.   |
|--------|----------------|
| 130    | JOHAB\_CHARSET |

The values in the following table are for the Middle East language edition of MicrosoftWindows.

| Value. | Description.    |
|--------|-----------------|
| 177    | HEBREW\_CHARSET |
| 178    | ARABIC\_CHARSET |

The value in the following table is for the Thai language edition of MicrosoftWindows.

| Value. | Description.  |
|--------|---------------|
| 222    | THAI\_CHARSET |

The default character set is set to a value, depending on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET.For more information, see the LOGFONT structure on the MSDN Web site, http://go.microsoft.com/fwlink/?LinkID=85972.

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  

#### Return Value

An integer between zero and two, inclusive.

#### Remarks

The color scheme is defined according to the following table:

| Value. | Style.                        |
|--------|-------------------------------|
| 0      | Default.                      |
| 1      | The MicrosoftWindows palette. |
| 2      | The true-color scheme.        |

### Method comboType

    public int comboType([int value])

#### Parameters

value  

#### Return Value

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method containerId

Retrieves the ID of the parent container for the control.

    public int containerId()

#### Return Value

The ID of the parent container.

### Method countryRegionCodes

    public str countryRegionCodes([str value])

#### Parameters

value  

#### Return Value

### Method countryRegionContextField

    public FieldId countryRegionContextField([FieldId value])

#### Parameters

value  

#### Return Value

### Method dataField

    public FieldId dataField([FieldId value])

#### Parameters

value  

#### Return Value

### Method dataMethod

    public str dataMethod([str value])

#### Parameters

value  

#### Return Value

### Method dataRelationPath

    public str dataRelationPath([str value])

#### Parameters

value  

#### Return Value

### Method dataSource

Gets or sets a data source that will be used by the control or the form.

    public int dataSource([AnyType value])

#### Parameters

value  

#### Return Value

The identifier of the data source that will be used.

### Method displayLength

    public int displayLength([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method displayLengthMode

    public AutoMode displayLengthMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method displayLengthValue

    public int displayLengthValue([int value])

#### Parameters

value  

#### Return Value

### Method displayTarget

    public int displayTarget([int value])

#### Parameters

value  

#### Return Value

### Method dragDrop

Determines whether to enable or disable drag-and-drop operations for the control.

    public int dragDrop([int value])

#### Parameters

value  

#### Return Value

1 if drag-and-drop operations are enabled; otherwise, false.

### Method enabled

Determines whether to enable or disable the object.

    public boolean enabled([boolean value])

#### Parameters

value  

#### Return Value

true if the object is enabled; otherwise, false.

#### Remarks

The enabled property allows for controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

### Method enumType

    public EnumId enumType([EnumId value])

#### Parameters

value  

#### Return Value

### Method extendedDataType

    public ExtendedTypeId extendedDataType([ExtendedTypeId value])

#### Parameters

value  

#### Return Value

### Method fastTabSummary

    public int fastTabSummary([int value])

#### Parameters

value  

#### Return Value

### Method font

Gets or sets the name of the font for the control to use.

    public str font([str value])

#### Parameters

value  

#### Return Value

The name of the font to use, such as Tahoma or Verdana.

### Method fontSize

Gets or sets the size of the font for the control to use.

    public int fontSize([int value])

#### Parameters

value  

#### Return Value

The height of the font in points.

### Method foregroundColor

Gets or sets the text color for the control to use.

    public int foregroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method height

Gets or sets the height of the control.

    public int height(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

The height of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the height according to the following table:

| Mode.            | Height calculation.                                                                       |
|------------------|-------------------------------------------------------------------------------------------|
| -1 Exact.        | The exact height in pixels of the controls is used.                                       |
| 0 Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height. | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

### Method heightMode

Gets or sets a calculation mode for the height of the control.

    public int heightMode([int value])

#### Parameters

value  

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table:

| Mode.          | Height Calculation.                                                                       |
|----------------|-------------------------------------------------------------------------------------------|
| Exact.         | The exact height in pixels of the controls is used.                                       |
| Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height. | The layout of the form determines the height of the control.                              |

The height of the control might change when the mode is set to auto or column height.

### Method heightValue

Gets or sets the height of the control.

    public int heightValue([int value])

#### Parameters

value  

#### Return Value

The height in pixels.

#### Remarks

The height of the control is not changed unless the exact height calculation mode is used.

### Method helpText

Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property dialogue box. The help text must not exceed 250 characters.

### Method hideFirstEntry

    public boolean hideFirstEntry([boolean value])

#### Parameters

value  

#### Return Value

### Method hierarchyParent

    public str hierarchyParent([str value])

#### Parameters

value  

#### Return Value

### Method id

Retrieves the ID of the control.

    public int id()

#### Return Value

The ID of the control.

### Method isContainer

Retrieves a value that indicates whether the control is a container control.

    public boolean isContainer()

#### Return Value

A Boolean value that indicates whether the control is a container control.

### Method italic

    public boolean italic([boolean value])

#### Parameters

value  

#### Return Value

### Method item

    public int item([int value])

#### Parameters

value  

#### Return Value

### Method items

    public int items([int value])

#### Parameters

value  

#### Return Value

### Method label

Gets or sets the label for a control.

    public str label([str value])

#### Parameters

value  

#### Return Value

The current value of the label string.

#### Remarks

The label determines which text is displayed in the control or adjacent to it.The label property value cannot exceed 250 characters.

### Method labelAlignment

    public int labelAlignment([int value])

#### Parameters

value  

#### Return Value

### Method labelBold

    public int labelBold([int value])

#### Parameters

value  

#### Return Value

### Method labelCharacterSet

    public int labelCharacterSet([int value])

#### Parameters

value  

#### Return Value

### Method labelFont

    public str labelFont([str value])

#### Parameters

value  

#### Return Value

### Method labelFontSize

    public int labelFontSize([int value])

#### Parameters

value  

#### Return Value

### Method labelForegroundColor

    public int labelForegroundColor([int value])

#### Parameters

value  

#### Return Value

### Method labelGuide

    public int labelGuide([int value])

#### Parameters

value  

#### Return Value

### Method labelHeight

    public int labelHeight(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method labelHeightMode

    public int labelHeightMode([int value])

#### Parameters

value  

#### Return Value

### Method labelHeightValue

    public int labelHeightValue([int value])

#### Parameters

value  

#### Return Value

### Method labelItalic

    public boolean labelItalic([boolean value])

#### Parameters

value  

#### Return Value

### Method labelPosition

    public int labelPosition([int value])

#### Parameters

value  

#### Return Value

### Method labelUnderline

    public boolean labelUnderline([boolean value])

#### Parameters

value  

#### Return Value

### Method labelWidth

    public int labelWidth(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method labelWidthMode

    public int labelWidthMode([int value])

#### Parameters

value  

#### Return Value

### Method labelWidthValue

    public int labelWidthValue([int value])

#### Parameters

value  

#### Return Value

### Method left

    public int left(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method leftMode

    public int leftMode([int value])

#### Parameters

value  

#### Return Value

### Method leftValue

    public int leftValue([int value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics 365 for Operations application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in the code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enumeration types, classes, and so on.

### Method neededPermission

    public int neededPermission([int value])

#### Parameters

value  

#### Return Value

### Method promptrect

    public int promptrect([int value])

#### Parameters

value  

#### Return Value

### Method securityKey

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  

#### Return Value

### Method selection

    public int selection([int value])

#### Parameters

value  

#### Return Value

### Method showLabel

    public boolean showLabel([boolean value])

#### Parameters

value  

#### Return Value

### Method skip

Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.

    public boolean skip([boolean value])

#### Parameters

value  
The value to assign to the skip property of the control.

#### Return Value

true if the control is skipped when the user presses the TAB key to move to the control; otherwise, false.

### Method text

    public str text([str value])

#### Parameters

value  

#### Return Value

### Method top

    public int top(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method topMode

    public int topMode([int value])

#### Parameters

value  

#### Return Value

### Method topValue

    public int topValue([int value])

#### Parameters

value  

#### Return Value

### Method type

    public int type([int value])

#### Parameters

value  

#### Return Value

### Method underline

Sets or returns the underline property for the text in the control.

    public boolean underline([boolean value])

#### Parameters

value  
The value to assign to the underline property of the control.

#### Return Value

true if the text in the control is underlined; otherwise, false.

### Method userData

    public int userData([int value])

#### Parameters

value  

#### Return Value

### Method userDataItem

    public int userDataItem([int value])

#### Parameters

value  

#### Return Value

### Method userDataItems

    public int userDataItems([int value])

#### Parameters

value  

#### Return Value

### Method verticalSpacing

    public int verticalSpacing([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method verticalSpacingMode

    public AutoMode verticalSpacingMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method verticalSpacingValue

    public int verticalSpacingValue([int value])

#### Parameters

value  

#### Return Value

### Method viewEditMode

    public int viewEditMode([int value])

#### Parameters

value  

#### Return Value

### Method visible

    public boolean visible([boolean value])

#### Parameters

value  

#### Return Value

### Method width

Gets or sets the width of the control.

    public int width(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

The width of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the width according to the following table:

| Mode.           | Width calculation.                                                                       |
|-----------------|------------------------------------------------------------------------------------------|
| -1 Exact.       | The exact width in pixels of the controls is used.                                       |
| 0 Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width. | The layout of the form determines the width of the control.                              |

The width and width calculation mode can be set separately.

### Method widthMode

Gets or sets the calculation mode of the width of the control.

    public int widthMode([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table:

| Mode.         | Width Calculation.                                                                       |
|---------------|------------------------------------------------------------------------------------------|
| Exact.        | The exact width in pixels of the controls is used.                                       |
| Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width. | The layout of the form determines the width of the control.                              |

The width of the control might change when the mode is set to auto or column width.

### Method widthValue

Gets or sets the width of the control.

    public int widthValue([int value])

#### Parameters

value  

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

## Class FormBuildCommandButtonControl
    class FormBuildCommandButtonControl extends FormBuildControl

The FormBuildCommandButtonControl class lets you create, read, update, and delete X++ code and metadata.

### Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                                                                                      | Description                                                                                                                             |
|-------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| public boolean alignControl(\[boolean value\])                                                              | Determines whether to align the control.                                                                                                |
| public int alignment(\[int value\])                                                                         |                                                                                                                                         |
| public boolean allowEdit(\[boolean value\])                                                                 | Determines whether the user can change the contents of the control.                                                                     |
| public boolean autoDeclaration(\[boolean value\])                                                           | Determines whether the system can declare a member variable that has the same name as the control.                                      |
| public boolean autoRefreshData(\[boolean value\])                                                           |                                                                                                                                         |
| public int backgroundColor(\[int value\])                                                                   | Gets or sets the background color of the control.                                                                                       |
| public int backStyle(\[int value\])                                                                         | Determiness whether the control background can be transparent.                                                                          |
| public boolean big(\[boolean value\])                                                                       |                                                                                                                                         |
| public int bold(\[int value\])                                                                              | Gets or sets the weight of font used to output text in the control.                                                                     |
| public int border(\[int value\])                                                                            | Gets or sets the style of the borderline of the control.                                                                                |
| public int buttonDisplay(\[int value\])                                                                     | Gets or sets the appearance of the button control.                                                                                      |
| public str caption(\[str value\])                                                                           | Gets or set the caption of the control.                                                                                                 |
| public int characterSet(\[int value\])                                                                      | Gets or sets the character set of the font.                                                                                             |
| public int colorScheme(\[int value\])                                                                       | Gets or sets the color scheme of the control.                                                                                           |
| public int command(\[int value\])                                                                           |                                                                                                                                         |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                    | Gets or sets the configuration key that is assigned to the control.                                                                     |
| public int containerId()                                                                                    | Retrieves the ID of the parent container for the control.                                                                               |
| public str countryRegionCodes(\[str value\])                                                                |                                                                                                                                         |
| public str dataRelationPath(\[str value\])                                                                  |                                                                                                                                         |
| public boolean defaultButton(\[boolean value\])                                                             | Determines whether the button should be the default button on the form.                                                                 |
| public str disabledImage(\[str value\])                                                                     | Gets or sets the disabled image of the button.                                                                                          |
| public int disabledImageLocation(\[int value\])                                                             |                                                                                                                                         |
| public int disabledResource(\[int value\])                                                                  | Gets or sets the resource ID of the image to use as the disabled button image.                                                          |
| public int displayTarget(\[int value\])                                                                     |                                                                                                                                         |
| public int dragDrop(\[int value\])                                                                          | Determines whether to enable or disable drag-and-drop operations for the control.                                                       |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether to enable or disable the object.                                                                                     |
| public str font(\[str value\])                                                                              | Gets or sets the name of the font for the control to use.                                                                               |
| public int fontSize(\[int value\])                                                                          | Gets or sets the size of the font for the control to use.                                                                               |
| public boolean forcedToOverflow(\[boolean value\])                                                          |                                                                                                                                         |
| public int foregroundColor(\[int value\])                                                                   | Gets or sets the text color for the control to use.                                                                                     |
| public int height(int value, \[int mode\])                                                                  | Gets or sets the height of the control.                                                                                                 |
| public int heightMode(\[int value\])                                                                        | Gets or sets a calculation mode for the height of the control.                                                                          |
| public int heightValue(\[int value\])                                                                       | Gets or sets the height of the control.                                                                                                 |
| public str helpText(\[str value\])                                                                          | Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.                                |
| public str hierarchyParent(\[str value\])                                                                   |                                                                                                                                         |
| public int id()                                                                                             | Retrieves the ID of the control.                                                                                                        |
| public int imageLocation(\[int value\])                                                                     |                                                                                                                                         |
| public boolean isContainer()                                                                                | Retrieves a value that indicates whether the control is a container control.                                                            |
| public boolean italic(\[boolean value\])                                                                    |                                                                                                                                         |
| public str keyTip(\[str value\])                                                                            |                                                                                                                                         |
| public int left(int value, \[int mode\])                                                                    |                                                                                                                                         |
| public int leftMode(\[int value\])                                                                          |                                                                                                                                         |
| public int leftValue(\[int value\])                                                                         |                                                                                                                                         |
| public int multiSelect(\[int value\])                                                                       |                                                                                                                                         |
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics 365 for Operations application object. |
| public int neededPermission(\[int value\])                                                                  |                                                                                                                                         |
| public int needsRecord(\[int value\])                                                                       |                                                                                                                                         |
| public str normalImage(\[str value\])                                                                       |                                                                                                                                         |
| public int normalResource(\[int value\])                                                                    |                                                                                                                                         |
| public str parameters(\[str value\])                                                                        |                                                                                                                                         |
| public boolean primary(\[boolean value\])                                                                   |                                                                                                                                         |
| public boolean saveRecord(\[boolean value\])                                                                |                                                                                                                                         |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                   |                                                                                                                                         |
| public int shortkey(\[int value\])                                                                          |                                                                                                                                         |
| public boolean showShortCut(\[boolean value\])                                                              |                                                                                                                                         |
| public boolean skip(\[boolean value\])                                                                      | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.         |
| public int style(\[int value\])                                                                             |                                                                                                                                         |
| public str text(\[str value\])                                                                              |                                                                                                                                         |
| public int toggleButton(\[int value\])                                                                      |                                                                                                                                         |
| public int toggleValue(\[int value\])                                                                       |                                                                                                                                         |
| public int top(int value, \[int mode\])                                                                     |                                                                                                                                         |
| public int topMode(\[int value\])                                                                           |                                                                                                                                         |
| public int topValue(\[int value\])                                                                          |                                                                                                                                         |
| public int type(\[int value\])                                                                              |                                                                                                                                         |
| public boolean underline(\[boolean value\])                                                                 | Sets or returns the underline property for the text in the control.                                                                     |
| public int userData(\[int value\])                                                                          |                                                                                                                                         |
| public int userDataItem(\[int value\])                                                                      |                                                                                                                                         |
| public int userDataItems(\[int value\])                                                                     |                                                                                                                                         |
| public boolean value(\[boolean value\])                                                                     |                                                                                                                                         |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                |                                                                                                                                         |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                      |                                                                                                                                         |
| public int verticalSpacingValue(\[int value\])                                                              |                                                                                                                                         |
| public boolean visible(\[boolean value\])                                                                   |                                                                                                                                         |
| public int width(int value, \[int mode\])                                                                   | Gets or sets the width of the control.                                                                                                  |
| public int widthMode(\[int value\])                                                                         | Gets or sets the calculation mode of the width of the control.                                                                          |
| public int widthValue(\[int value\])                                                                        | Gets or sets the width of the control.                                                                                                  |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                         |

### Method alignControl

Determines whether to align the control.

    public boolean alignControl([boolean value])

#### Parameters

value  

#### Return Value

true if the control should be aligned; otherwise, false.

#### Remarks

The upper-left corner of the control is aligned according to the longest label.

### Method alignment

    public int alignment([int value])

#### Parameters

value  

#### Return Value

### Method allowEdit

Determines whether the user can change the contents of the control.

    public boolean allowEdit([boolean value])

#### Parameters

value  

#### Return Value

true if the control can be edited; otherwise, false.

#### Remarks

When this property is set on a container control, modifications are disabled or enabled for all controls within the container.

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method autoRefreshData

    public boolean autoRefreshData([boolean value])

#### Parameters

value  

#### Return Value

### Method backgroundColor

Gets or sets the background color of the control.

    public int backgroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method backStyle

Determiness whether the control background can be transparent.

    public int backStyle([int value])

#### Parameters

value  

#### Return Value

1 if the control background can be transparent; otherwise, 0.

### Method big

    public boolean big([boolean value])

#### Parameters

value  

#### Return Value

### Method bold

Gets or sets the weight of font used to output text in the control.

    public int bold([int value])

#### Parameters

value  

#### Return Value

An integer value between zero and nine, inclusive.

#### Remarks

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

### Method border

Gets or sets the style of the borderline of the control.

    public int border([int value])

#### Parameters

value  

#### Return Value

An integer between zero and four, inclusive.

#### Remarks

The integer that is returned contains the style of the borderline of the control as follows:

| Value. | Description. |
|--------|--------------|
| 0      | Auto.        |
| 1      | 3D.          |
| 2      | Single line. |
| 3      | Flat.        |
| 4      | None.        |

### Method buttonDisplay

Gets or sets the appearance of the button control.

    public int buttonDisplay([int value])

#### Parameters

value  

#### Return Value

An integer between zero and five, inclusive.

#### Remarks

The value of the property defines whether the text, the image, or both should be displayed on the button. This property also controls relative positions of text and image if both are displayed.The integer value that is returned contains the appearace of the button control as follows:

| Value. | Description.                                                     |
|--------|------------------------------------------------------------------|
| 0      | Text only.                                                       |
| 1      | Image Only.                                                      |
| 2      | Text and image; the image is displayed below the text.           |
| 3      | Text and image; the image is displayed above the text.           |
| 4      | Text and image; the image is displayed to the left of the text.  |
| 5      | Text and image; the image is displayed to the right of the text. |

### Method caption

Gets or set the caption of the control.

    public str caption([str value])

#### Parameters

value  

#### Return Value

The string that is used as the caption of the control.

### Method characterSet

Gets or sets the character set of the font.

    public int characterSet([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the character set of the font.

#### Remarks

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

The default character set is set to a value based on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET.For more information, see the LOGFONT structure on the MSDN Web site, http://go.microsoft.com/fwlink/?LinkID=85972.

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  

#### Return Value

An integer between zero and two, inclusive.

#### Remarks

The color scheme is defined according to the following table:

| Value. | Style.                         |
|--------|--------------------------------|
| 0      | Default.                       |
| 1      | The Microsoft Windows palette. |
| 2      | The true-color scheme.         |

### Method command

    public int command([int value])

#### Parameters

value  

#### Return Value

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method containerId

Retrieves the ID of the parent container for the control.

    public int containerId()

#### Return Value

The ID of the parent container.

### Method countryRegionCodes

    public str countryRegionCodes([str value])

#### Parameters

value  

#### Return Value

### Method dataRelationPath

    public str dataRelationPath([str value])

#### Parameters

value  

#### Return Value

### Method defaultButton

Determines whether the button should be the default button on the form.

    public boolean defaultButton([boolean value])

#### Parameters

value  

#### Return Value

true if the button should be the default button; otherwise, false.

### Method disabledImage

Gets or sets the disabled image of the button.

    public str disabledImage([str value])

#### Parameters

value  

#### Return Value

The full name of an image file. The system supports all of the GDI-supported image formats.

#### Remarks

This property has precedence over the disabledResource property. It is used if both of these properties are set.

### Method disabledImageLocation

    public int disabledImageLocation([int value])

#### Parameters

value  

#### Return Value

### Method disabledResource

Gets or sets the resource ID of the image to use as the disabled button image.

    public int disabledResource([int value])

#### Parameters

value  

#### Return Value

The resource ID of the image to use as the disabled button image. Both icon and bitmap images are supported.

### Method displayTarget

    public int displayTarget([int value])

#### Parameters

value  

#### Return Value

### Method dragDrop

Determines whether to enable or disable drag-and-drop operations for the control.

    public int dragDrop([int value])

#### Parameters

value  

#### Return Value

1 if drag-and-drop operations are enabled; otherwise, false.

### Method enabled

Determines whether to enable or disable the object.

    public boolean enabled([boolean value])

#### Parameters

value  

#### Return Value

true if the object is enabled; otherwise, false.

#### Remarks

The enabled property allows controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

### Method font

Gets or sets the name of the font for the control to use.

    public str font([str value])

#### Parameters

value  

#### Return Value

The name of the font to use, such as Tahoma or Verdana.

### Method fontSize

Gets or sets the size of the font for the control to use.

    public int fontSize([int value])

#### Parameters

value  

#### Return Value

The height of the font in points.

### Method forcedToOverflow

    public boolean forcedToOverflow([boolean value])

#### Parameters

value  

#### Return Value

### Method foregroundColor

Gets or sets the text color for the control to use.

    public int foregroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method height

Gets or sets the height of the control.

    public int height(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

The height of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the height according to the following table:

| Mode.            | Height calculation.                                                                       |
|------------------|-------------------------------------------------------------------------------------------|
| -1 Exact.        | The exact height in pixels of the controls is used.                                       |
| 0 Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height. | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

### Method heightMode

Gets or sets a calculation mode for the height of the control.

    public int heightMode([int value])

#### Parameters

value  

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table:

| Mode.          | Height Calculation.                                                                       |
|----------------|-------------------------------------------------------------------------------------------|
| Exact.         | The exact height in pixels of the controls is used.                                       |
| Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height. | The layout of the form determines the height of the control.                              |

The height of the control might change when the mode is set to auto or column height.

### Method heightValue

Gets or sets the height of the control.

    public int heightValue([int value])

#### Parameters

value  

#### Return Value

The height in pixels.

#### Remarks

The height of the control is not changed unless the exact height calculation mode is used.

### Method helpText

Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property sheet. The help text must not exceed 250 characters.

### Method hierarchyParent

    public str hierarchyParent([str value])

#### Parameters

value  

#### Return Value

### Method id

Retrieves the ID of the control.

    public int id()

#### Return Value

The ID of the control.

### Method imageLocation

    public int imageLocation([int value])

#### Parameters

value  

#### Return Value

### Method isContainer

Retrieves a value that indicates whether the control is a container control.

    public boolean isContainer()

#### Return Value

A Boolean value that indicates whether the control is a container control.

### Method italic

    public boolean italic([boolean value])

#### Parameters

value  

#### Return Value

### Method keyTip

    public str keyTip([str value])

#### Parameters

value  

#### Return Value

### Method left

    public int left(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method leftMode

    public int leftMode([int value])

#### Parameters

value  

#### Return Value

### Method leftValue

    public int leftValue([int value])

#### Parameters

value  

#### Return Value

### Method multiSelect

    public int multiSelect([int value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics 365 for Operations application object.

    public str name([str value])

#### Parameters

value  
The name to assign to the control.

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   It must start with a letter.
-   It cannot exceed 250 characters.
-   It can include numbers and underscore (\_) characters.
-   It cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, or classes.

### Method neededPermission

    public int neededPermission([int value])

#### Parameters

value  

#### Return Value

### Method needsRecord

    public int needsRecord([int value])

#### Parameters

value  

#### Return Value

### Method normalImage

    public str normalImage([str value])

#### Parameters

value  

#### Return Value

### Method normalResource

    public int normalResource([int value])

#### Parameters

value  

#### Return Value

### Method parameters

    public str parameters([str value])

#### Parameters

value  

#### Return Value

### Method primary

    public boolean primary([boolean value])

#### Parameters

value  

#### Return Value

### Method saveRecord

    public boolean saveRecord([boolean value])

#### Parameters

value  

#### Return Value

### Method securityKey

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  

#### Return Value

### Method shortkey

    public int shortkey([int value])

#### Parameters

value  

#### Return Value

### Method showShortCut

    public boolean showShortCut([boolean value])

#### Parameters

value  

#### Return Value

### Method skip

Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.

    public boolean skip([boolean value])

#### Parameters

value  
The value to assign to the skip property of the control.

#### Return Value

true if the control is skipped when the user presses the TAB key to move to the control; otherwise, false.

### Method style

    public int style([int value])

#### Parameters

value  

#### Return Value

### Method text

    public str text([str value])

#### Parameters

value  

#### Return Value

### Method toggleButton

    public int toggleButton([int value])

#### Parameters

value  

#### Return Value

### Method toggleValue

    public int toggleValue([int value])

#### Parameters

value  

#### Return Value

### Method top

    public int top(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method topMode

    public int topMode([int value])

#### Parameters

value  

#### Return Value

### Method topValue

    public int topValue([int value])

#### Parameters

value  

#### Return Value

### Method type

    public int type([int value])

#### Parameters

value  

#### Return Value

### Method underline

Sets or returns the underline property for the text in the control.

    public boolean underline([boolean value])

#### Parameters

value  
The value to assign to the underline property of the control.

#### Return Value

true if the text in the control is underlined; otherwise, false.

### Method userData

    public int userData([int value])

#### Parameters

value  

#### Return Value

### Method userDataItem

    public int userDataItem([int value])

#### Parameters

value  

#### Return Value

### Method userDataItems

    public int userDataItems([int value])

#### Parameters

value  

#### Return Value

### Method value

    public boolean value([boolean value])

#### Parameters

value  

#### Return Value

### Method verticalSpacing

    public int verticalSpacing([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method verticalSpacingMode

    public AutoMode verticalSpacingMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method verticalSpacingValue

    public int verticalSpacingValue([int value])

#### Parameters

value  

#### Return Value

### Method visible

    public boolean visible([boolean value])

#### Parameters

value  

#### Return Value

### Method width

Gets or sets the width of the control.

    public int width(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

The width of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the width according to the following table:

| Mode.           | Width calculation.                                                                       |
|-----------------|------------------------------------------------------------------------------------------|
| -1 Exact.       | The exact width in pixels of the controls is used.                                       |
| 0 Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width. | The layout of the form determines the width of the control.                              |

The width and width calculation mode can be set separately.

### Method widthMode

Gets or sets the calculation mode of the width of the control.

    public int widthMode([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table:

| Mode.         | Width Calculation.                                                                       |
|---------------|------------------------------------------------------------------------------------------|
| Exact.        | The exact width in pixels of the controls is used.                                       |
| Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width. | The layout of the form determines the width of the control.                              |

The width of the control might change when the mode is set to auto or column width.

### Method widthValue

Gets or sets the width of the control.

    public int widthValue([int value])

#### Parameters

value  

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

## Class FormBuildContainerControl
    class FormBuildContainerControl extends FormBuildControl

### Remarks

### Examples

### Methods

| Method                                                                                                      | Description |
|-------------------------------------------------------------------------------------------------------------|-------------|
| public boolean alignControl(\[boolean value\])                                                              |             |
| public boolean allowEdit(\[boolean value\])                                                                 |             |
| public boolean autoDeclaration(\[boolean value\])                                                           |             |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                    |             |
| public int containerId()                                                                                    |             |
| public str countryRegionCodes(\[str value\])                                                                |             |
| public str dataRelationPath(\[str value\])                                                                  |             |
| public int displayTarget(\[int value\])                                                                     |             |
| public int dragDrop(\[int value\])                                                                          |             |
| public boolean enabled(\[boolean value\])                                                                   |             |
| public int height(int value, \[int mode\])                                                                  |             |
| public int heightMode(\[int value\])                                                                        |             |
| public int heightValue(\[int value\])                                                                       |             |
| public str helpText(\[str value\])                                                                          |             |
| public str hierarchyParent(\[str value\])                                                                   |             |
| public int id()                                                                                             |             |
| public boolean isContainer()                                                                                |             |
| public int left(int value, \[int mode\])                                                                    |             |
| public int leftMode(\[int value\])                                                                          |             |
| public int leftValue(\[int value\])                                                                         |             |
| public int moveControl(int controlId, \[int insertAfterControlId\])                                         |             |
| public str name(\[str value\])                                                                              |             |
| public int neededPermission(\[int value\])                                                                  |             |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                   |             |
| public boolean skip(\[boolean value\])                                                                      |             |
| public int top(int value, \[int mode\])                                                                     |             |
| public int topMode(\[int value\])                                                                           |             |
| public int topValue(\[int value\])                                                                          |             |
| public int type(\[int value\])                                                                              |             |
| public int userData(\[int value\])                                                                          |             |
| public int userDataItem(\[int value\])                                                                      |             |
| public int userDataItems(\[int value\])                                                                     |             |
| public boolean useUserLayout(\[boolean value\])                                                             |             |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                |             |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                      |             |
| public int verticalSpacingValue(\[int value\])                                                              |             |
| public boolean visible(\[boolean value\])                                                                   |             |
| public int width(int value, \[int mode\])                                                                   |             |
| public int widthMode(\[int value\])                                                                         |             |
| public int widthValue(\[int value\])                                                                        |             |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |             |

### Method alignControl

    public boolean alignControl([boolean value])

#### Parameters

value  

#### Return Value

### Method allowEdit

    public boolean allowEdit([boolean value])

#### Parameters

value  

#### Return Value

### Method autoDeclaration

    public boolean autoDeclaration([boolean value])

#### Parameters

value  

#### Return Value

### Method configurationKey

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

### Method containerId

    public int containerId()

#### Return Value

### Method countryRegionCodes

    public str countryRegionCodes([str value])

#### Parameters

value  

#### Return Value

### Method dataRelationPath

    public str dataRelationPath([str value])

#### Parameters

value  

#### Return Value

### Method displayTarget

    public int displayTarget([int value])

#### Parameters

value  

#### Return Value

### Method dragDrop

    public int dragDrop([int value])

#### Parameters

value  

#### Return Value

### Method enabled

    public boolean enabled([boolean value])

#### Parameters

value  

#### Return Value

### Method height

    public int height(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method heightMode

    public int heightMode([int value])

#### Parameters

value  

#### Return Value

### Method heightValue

    public int heightValue([int value])

#### Parameters

value  

#### Return Value

### Method helpText

    public str helpText([str value])

#### Parameters

value  

#### Return Value

### Method hierarchyParent

    public str hierarchyParent([str value])

#### Parameters

value  

#### Return Value

### Method id

    public int id()

#### Return Value

### Method isContainer

    public boolean isContainer()

#### Return Value

### Method left

    public int left(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method leftMode

    public int leftMode([int value])

#### Parameters

value  

#### Return Value

### Method leftValue

    public int leftValue([int value])

#### Parameters

value  

#### Return Value

### Method moveControl

    public int moveControl(int controlId, [int insertAfterControlId])

#### Parameters

controlId  

<!-- -->

insertAfterControlId  

#### Return Value

### Method name

    public str name([str value])

#### Parameters

value  

#### Return Value

### Method neededPermission

    public int neededPermission([int value])

#### Parameters

value  

#### Return Value

### Method securityKey

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  

#### Return Value

### Method skip

    public boolean skip([boolean value])

#### Parameters

value  

#### Return Value

### Method top

    public int top(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method topMode

    public int topMode([int value])

#### Parameters

value  

#### Return Value

### Method topValue

    public int topValue([int value])

#### Parameters

value  

#### Return Value

### Method type

    public int type([int value])

#### Parameters

value  

#### Return Value

### Method userData

    public int userData([int value])

#### Parameters

value  

#### Return Value

### Method userDataItem

    public int userDataItem([int value])

#### Parameters

value  

#### Return Value

### Method userDataItems

    public int userDataItems([int value])

#### Parameters

value  

#### Return Value

### Method useUserLayout

    public boolean useUserLayout([boolean value])

#### Parameters

value  

#### Return Value

### Method verticalSpacing

    public int verticalSpacing([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method verticalSpacingMode

    public AutoMode verticalSpacingMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method verticalSpacingValue

    public int verticalSpacingValue([int value])

#### Parameters

value  

#### Return Value

### Method visible

    public boolean visible([boolean value])

#### Parameters

value  

#### Return Value

### Method width

    public int width(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method widthMode

    public int widthMode([int value])

#### Parameters

value  

#### Return Value

### Method widthValue

    public int widthValue([int value])

#### Parameters

value  

#### Return Value

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

## Class FormBuildControl
    class FormBuildControl extends Object

The FormBuildControl class lets you create, read, update, and delete X++ code and metadata.

### Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                                                                                                                    | Description                                                                                                                                        |
|-------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| public FormBuildControl addControl(FormControlType controlType, str controlName, \[FormBuildControl insertAfter\], \[boolean pushFront\]) | Adds a control to the control, based on the specified control type.                                                                                |
| public FormBuildControl addControlEx(str controlClass, str controlName, \[FormBuildControl insertAfter\], \[boolean pushFront\])          |                                                                                                                                                    |
| public FormBuildControl addDataField(int dataSourceId, FieldId fieldId, \[int arrayIndex\])                                               | Adds a control to the control, based on the specified data field information.                                                                      |
| public boolean allowEdit(\[boolean value\])                                                                                               |                                                                                                                                                    |
| public boolean autoDeclaration(\[boolean value\])                                                                                         |                                                                                                                                                    |
| public boolean canAddDataField(int dataSourceId, FieldId fieldId, \[int arrayIndex\])                                                     | Retrieves a value that indicates whether the specified data field can be added as a child control to the control.                                  |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                                                  |                                                                                                                                                    |
| public int containerId()                                                                                                                  | Retrieves the ID of the parent container for the control.                                                                                          |
| public int controlCount()                                                                                                                 | Retrieves the number of controls that are contained in the control.                                                                                |
| public FormBuildControl controlNum(int controlNo)                                                                                         | Retrieves a contained control by using the specified index.                                                                                        |
| public str countryRegionCodes(\[str value\])                                                                                              |                                                                                                                                                    |
| public boolean editAutoPostback(\[boolean value\])                                                                                        |                                                                                                                                                    |
| public boolean enabled(\[boolean value\])                                                                                                 |                                                                                                                                                    |
| public str helpText(\[str value\])                                                                                                        |                                                                                                                                                    |
| public str extendedStyle(\[str value\])                                                                                                   |                                                                                                                                                    |
| public int height(int value, \[int mode\])                                                                                                |                                                                                                                                                    |
| public int heightMode(\[int value\])                                                                                                      |                                                                                                                                                    |
| public int heightValue(\[int value\])                                                                                                     |                                                                                                                                                    |
| public str GetXppILImplementation()                                                                                                       |                                                                                                                                                    |
| public boolean hasUserSetting()                                                                                                           | Indicates whether the control has custom user settings.                                                                                            |
| public int id()                                                                                                                           | Retrieves the ID of the control.                                                                                                                   |
| public boolean isContainer()                                                                                                              | Retrieves a value that indicates whether the control is a container control.                                                                       |
| public boolean markAsUserAdd(\[boolean value\])                                                                                           | Marks or unmarks the control as a user-added control.                                                                                              |
| public int moveControl(int controlId, \[int insertAfterId\])                                                                              | Moves a specified control to the control.                                                                                                          |
| public str name(\[str value\])                                                                                                            |                                                                                                                                                    |
| public int neededPermission(\[int value\])                                                                                                |                                                                                                                                                    |
| public container SysObsoleteAttribute()                                                                                                   |                                                                                                                                                    |
| public str previewPartRef(\[str value\])                                                                                                  |                                                                                                                                                    |
| public boolean skip(\[boolean value\])                                                                                                    |                                                                                                                                                    |
| public boolean SysObsoleteAttribute(container data)                                                                                       |                                                                                                                                                    |
| public int userDisable(\[int value\])                                                                                                     | Gets or sets the value that indicates whether the control is disabled for the user.                                                                |
| public int userHeight(\[int value\])                                                                                                      | Gets or sets the custom user height for the control.                                                                                               |
| public int userHide(\[int value\])                                                                                                        | Gets or sets the value that indicates whether the control is hidden from the user.                                                                 |
| public int userOrgContainer(\[int value\])                                                                                                | Gets or sets the organization container for the control.                                                                                           |
| public int userOrgSibling(\[int value\])                                                                                                  | Gets or sets the organization sibling for the control.                                                                                             |
| public str userPromptText(\[str value\])                                                                                                  | Gets or sets the user label text for the control.                                                                                                  |
| public int userSecurityLevel(\[int value\])                                                                                               | Gets or sets the user security level for the control.                                                                                              |
| public int userSkip(\[int value\])                                                                                                        | Sets or returns the value that indicates whether the form control is skipped when the user press the TAB key to navigate the controls on the form. |
| public int userWidth(\[int value\])                                                                                                       | Sets or returns the width of the control in pixels.                                                                                                |
| public boolean visible(\[boolean value\])                                                                                                 |                                                                                                                                                    |
| public int width(int value, \[int mode\])                                                                                                 |                                                                                                                                                    |
| public int widthMode(\[int value\])                                                                                                       |                                                                                                                                                    |
| public int widthValue(\[int value\])                                                                                                      |                                                                                                                                                    |
| public void RegisterXppILImplementation(str className)                                                                                    |                                                                                                                                                    |
| public void new(FormContainer container)                                                                                                  |                                                                                                                                                    |
| public void resetUserSetting()                                                                                                            | Resets the user settings for the control.                                                                                                          |

### Method addControl

Adds a control to the control, based on the specified control type.

    public FormBuildControl addControl(FormControlType controlType, str controlName, [FormBuildControl insertAfter], [boolean pushFront])

#### Parameters

controlType  
The string value to set the name of the new control to.

<!-- -->

controlName  
The string value to set the name of the new control to.

<!-- -->

insertAfter  

<!-- -->

pushFront  

#### Return Value

A FormBuildControl object that represents the newly added control.

### Method addControlEx

    public FormBuildControl addControlEx(str controlClass, str controlName, [FormBuildControl insertAfter], [boolean pushFront])

#### Parameters

controlClass  

<!-- -->

controlName  

<!-- -->

insertAfter  

<!-- -->

pushFront  

#### Return Value

### Method addDataField

Adds a control to the control, based on the specified data field information.

    public FormBuildControl addDataField(int dataSourceId, FieldId fieldId, [int arrayIndex])

#### Parameters

dataSourceId  
An integer value that indicates the index of the data field type; optional.

<!-- -->

fieldId  
An integer value that indicates the index of the data field type; optional.

<!-- -->

arrayIndex  
An integer value that indicates the index of the data field type; optional.

#### Return Value

A FormBuildControl object that represents the newly added control.

#### Remarks

The type of control that should be added is determined automatically, based on the specified data field information. The arrayIndex parameter has a default value of 1 when a value is not specified, so that the first index is assumed.

### Method allowEdit

    public boolean allowEdit([boolean value])

#### Parameters

value  

#### Return Value

### Method autoDeclaration

    public boolean autoDeclaration([boolean value])

#### Parameters

value  

#### Return Value

### Method canAddDataField

Retrieves a value that indicates whether the specified data field can be added as a child control to the control.

    public boolean canAddDataField(int dataSourceId, FieldId fieldId, [int arrayIndex])

#### Parameters

dataSourceId  
An integer value that indicates the index of the data field type; optional.

<!-- -->

fieldId  
An integer value that indicates the index of the data field type; optional.

<!-- -->

arrayIndex  
An integer value that indicates the index of the data field type; optional.

#### Return Value

A Boolean value that indicates whether the specified data field can be added as a child control to the control.

### Method configurationKey

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

### Method containerId

Retrieves the ID of the parent container for the control.

    public int containerId()

#### Return Value

The ID of the parent container.

### Method controlCount

Retrieves the number of controls that are contained in the control.

    public int controlCount()

#### Return Value

An integer value that indicates the number of controls that are contained in the control if it is a container control; otherwise, 0.

### Method controlNum

Retrieves a contained control by using the specified index.

    public FormBuildControl controlNum(int controlNo)

#### Parameters

controlNo  
An integer value that indicates the index of the child control to retrieve.

#### Return Value

A FormBuildControl object that represents the child control that has the specified index if this is a container control; otherwise, nullNothingnullptrunita null reference (Nothing in Visual Basic).

#### Remarks

If the specified controlNo parameter is out of range, an exception is raised.

### Method countryRegionCodes

    public str countryRegionCodes([str value])

#### Parameters

value  

#### Return Value

### Method editAutoPostback

    public boolean editAutoPostback([boolean value])

#### Parameters

value  

#### Return Value

### Method enabled

    public boolean enabled([boolean value])

#### Parameters

value  

#### Return Value

### Method helpText

    public str helpText([str value])

#### Parameters

value  

#### Return Value

### Method extendedStyle

    public str extendedStyle([str value])

#### Parameters

value  

#### Return Value

### Method height

    public int height(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method heightMode

    public int heightMode([int value])

#### Parameters

value  

#### Return Value

### Method heightValue

    public int heightValue([int value])

#### Parameters

value  

#### Return Value

### Method GetXppILImplementation

    public str GetXppILImplementation()

#### Return Value

### Method hasUserSetting

Indicates whether the control has custom user settings.

    public boolean hasUserSetting()

#### Return Value

A Boolean value that indicates whether the control has custom user settings.

### Method id

Retrieves the ID of the control.

    public int id()

#### Return Value

The ID of the control.

### Method isContainer

Retrieves a value that indicates whether the control is a container control.

    public boolean isContainer()

#### Return Value

A Boolean value that indicates whether the control is a container control.

### Method markAsUserAdd

Marks or unmarks the control as a user-added control.

    public boolean markAsUserAdd([boolean value])

#### Parameters

value  
A Boolean value that indicates whether to mark the control as a user-added control.

#### Return Value

A Boolean value that indicates whether the control was marked as a user-added control.

### Method moveControl

Moves a specified control to the control.

    public int moveControl(int controlId, [int insertAfterId])

#### Parameters

controlId  
An integer value that indicates the ID of the control to insert the control after; optional.

<!-- -->

insertAfterId  
An integer value that indicates the ID of the control to insert the control after; optional.

#### Return Value

1 if the control was moved successfully; otherwise, 0.

#### Remarks

In general, if the specified control can be contained in the control and can be moved from the container that it is currently in, this method should succeed. However, in some cases, such as for the reference group control instance, controls cannot be moved.

### Method name

    public str name([str value])

#### Parameters

value  

#### Return Value

### Method neededPermission

    public int neededPermission([int value])

#### Parameters

value  

#### Return Value

### Method SysObsoleteAttribute

    public container SysObsoleteAttribute()

#### Return Value

### Method previewPartRef

    public str previewPartRef([str value])

#### Parameters

value  

#### Return Value

### Method skip

    public boolean skip([boolean value])

#### Parameters

value  

#### Return Value

### Method SysObsoleteAttribute

    public boolean SysObsoleteAttribute(container data)

#### Parameters

data  

#### Return Value

### Method userDisable

Gets or sets the value that indicates whether the control is disabled for the user.

    public int userDisable([int value])

#### Parameters

value  
The value that indicates whether the control is disabled for the user; optional.

#### Return Value

1 if the control is disabled for the user; otherwise, 0.

### Method userHeight

Gets or sets the custom user height for the control.

    public int userHeight([int value])

#### Parameters

value  
The user height for the control; optional.

#### Return Value

The custom user height for the control.

### Method userHide

Gets or sets the value that indicates whether the control is hidden from the user.

    public int userHide([int value])

#### Parameters

value  
The value that indicates whether the control is hidden from the user; optional.

#### Return Value

1 if the control is hidden from the user; otherwise, 0.

#### Remarks

The user specifies whether a control is hidden by right-clicking the control when it is viewable or right-clicking another control when the original control is hidden. The right-click opens a menu that can be used to hide or display the control. This method lets you programmatically determine and set the value.

### Method userOrgContainer

Gets or sets the organization container for the control.

    public int userOrgContainer([int value])

#### Parameters

value  
The organization container to set for the control; optional.

#### Return Value

The organization container for the control.

### Method userOrgSibling

Gets or sets the organization sibling for the control.

    public int userOrgSibling([int value])

#### Parameters

value  
The organization sibling to set for the control; optional.

#### Return Value

The organization sibling for the control.

### Method userPromptText

Gets or sets the user label text for the control.

    public str userPromptText([str value])

#### Parameters

value  
The user label text to set for the control; optional.

#### Return Value

The user label text for the control.

### Method userSecurityLevel

Gets or sets the user security level for the control.

    public int userSecurityLevel([int value])

#### Parameters

value  
The user security level to set for the control; optional.

#### Return Value

The user security level for the control.

### Method userSkip

Sets or returns the value that indicates whether the form control is skipped when the user press the TAB key to navigate the controls on the form.

    public int userSkip([int value])

#### Parameters

value  
The value to assign to the userSkip property; optional. The value is 1 if the user setting to skip the control is in effect; otherwise, it is 0.

#### Return Value

1 if the user setting to skip the control is in effect; otherwise, 0.

### Method userWidth

Sets or returns the width of the control in pixels.

    public int userWidth([int value])

#### Parameters

value  
The number of pixels to use as the width of the control; optional.

#### Return Value

The number of pixels that the user specified as the width of the control; 0 (zero) if the user did not specify a character width.

#### Remarks

The userWidth method returns the width in pixels, based on six times the number of characters. For example, if the user has specified 30 characters as the width of the control, the return value is 6 \* 30 = 180. To specify the width of the control in characters, users can right-click the control to open the setup form where the character specification is made.

### Method visible

    public boolean visible([boolean value])

#### Parameters

value  

#### Return Value

### Method width

    public int width(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method widthMode

    public int widthMode([int value])

#### Parameters

value  

#### Return Value

### Method widthValue

    public int widthValue([int value])

#### Parameters

value  

#### Return Value

### Method RegisterXppILImplementation

    public void RegisterXppILImplementation(str className)

#### Parameters

className  

### Method new

    public void new(FormContainer container)

#### Parameters

container  

### Method resetUserSetting

Resets the user settings for the control.

    public void resetUserSetting()

## Class FormBuildDataSource
    class FormBuildDataSource extends FormBuildObjectSet

The FormBuildDataSource class lets you create, read, update, and delete X++ code and metadata.

### Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                                                            | Description                                                                                                               |
|-----------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------|
| public FormBuildDataSource addReferenceDataSource(str name, \[str joinRelation\]) |                                                                                                                           |
| public boolean allowCheck(\[boolean value\])                                      |                                                                                                                           |
| public boolean allowCreate(\[boolean value\])                                     |                                                                                                                           |
| public boolean allowDeferredLoad(\[boolean value\])                               |                                                                                                                           |
| public boolean allowDelete(\[boolean value\])                                     |                                                                                                                           |
| public boolean allowEdit(\[boolean value\])                                       | Determines whether the user can change the contents of the control.                                                       |
| public boolean autoNotify(\[boolean value\])                                      |                                                                                                                           |
| public boolean autoQuery(\[boolean value\])                                       |                                                                                                                           |
| public boolean autoSearch(\[boolean value\])                                      |                                                                                                                           |
| public FormBuildDataSource baseDataSource()                                       |                                                                                                                           |
| public str company(\[str value\])                                                 |                                                                                                                           |
| public FieldId counterField(\[FieldId value\])                                    |                                                                                                                           |
| public boolean crossCompanyAutoQuery(\[boolean value\])                           |                                                                                                                           |
| public boolean delayActive(\[boolean value\])                                     |                                                                                                                           |
| public int extends(\[AnyType value\])                                             |                                                                                                                           |
| public str GetXppILImplementation()                                               |                                                                                                                           |
| public IndexId index(\[IndexId value\])                                           |                                                                                                                           |
| public boolean insertAtEnd(\[boolean value\])                                     |                                                                                                                           |
| public boolean insertIfEmpty(\[boolean value\])                                   |                                                                                                                           |
| public boolean isBaseDataSource()                                                 |                                                                                                                           |
| public boolean isInheritanceDataSource()                                          |                                                                                                                           |
| public boolean isMasterDataSource()                                               |                                                                                                                           |
| public str joinRelation(\[str value\])                                            |                                                                                                                           |
| public int joinSource(\[AnyType value\])                                          |                                                                                                                           |
| public int linkType(\[int value\])                                                |                                                                                                                           |
| public FormBuildDataSource masterDataSource()                                     |                                                                                                                           |
| public int maxAccessRight(\[int value\])                                          |                                                                                                                           |
| public int maxRecordsToLoad(\[int value\])                                        |                                                                                                                           |
| public str name(\[str value\])                                                    | Gets or sets the name that is used in code to identify a form, report, rable, query, or another MSDAX application object. |
| public boolean onlyFetchActive(\[boolean value\])                                 |                                                                                                                           |
| public int optionalRecordMode(\[int value\])                                      |                                                                                                                           |
| public int startPosition(\[int value\])                                           |                                                                                                                           |
| public TableId table(\[TableId value\])                                           | Gets or sets the table ID associated with the object.                                                                     |
| public int validTimeStateAutoQuery(\[int value\])                                 |                                                                                                                           |
| public int validTimeStateUpdate(\[int value\])                                    |                                                                                                                           |
| public void RegisterXppDataFieldILImplementation(str fieldName, str className)    |                                                                                                                           |
| public void RegisterXppILImplementation(str className)                            |                                                                                                                           |
| public void SetDataLinkType(QueryDataLinkType linkType, str parentDataSource)     |                                                                                                                           |

### Method addReferenceDataSource

    public FormBuildDataSource addReferenceDataSource(str name, [str joinRelation])

#### Parameters

name  

<!-- -->

joinRelation  

#### Return Value

### Method allowCheck

    public boolean allowCheck([boolean value])

#### Parameters

value  

#### Return Value

### Method allowCreate

    public boolean allowCreate([boolean value])

#### Parameters

value  

#### Return Value

### Method allowDeferredLoad

    public boolean allowDeferredLoad([boolean value])

#### Parameters

value  

#### Return Value

### Method allowDelete

    public boolean allowDelete([boolean value])

#### Parameters

value  

#### Return Value

### Method allowEdit

Determines whether the user can change the contents of the control.

    public boolean allowEdit([boolean value])

#### Parameters

value  

#### Return Value

true if the control can be edited; otherwise, false.

#### Remarks

When this property is set on a container control, modifications are disabled or enabled for all controls in the container.

### Method autoNotify

    public boolean autoNotify([boolean value])

#### Parameters

value  

#### Return Value

### Method autoQuery

    public boolean autoQuery([boolean value])

#### Parameters

value  

#### Return Value

### Method autoSearch

    public boolean autoSearch([boolean value])

#### Parameters

value  

#### Return Value

### Method baseDataSource

    public FormBuildDataSource baseDataSource()

#### Return Value

### Method company

    public str company([str value])

#### Parameters

value  

#### Return Value

### Method counterField

    public FieldId counterField([FieldId value])

#### Parameters

value  

#### Return Value

### Method crossCompanyAutoQuery

    public boolean crossCompanyAutoQuery([boolean value])

#### Parameters

value  

#### Return Value

### Method delayActive

    public boolean delayActive([boolean value])

#### Parameters

value  

#### Return Value

### Method extends

    public int extends([AnyType value])

#### Parameters

value  

#### Return Value

### Method GetXppILImplementation

    public str GetXppILImplementation()

#### Return Value

### Method index

    public IndexId index([IndexId value])

#### Parameters

value  

#### Return Value

### Method insertAtEnd

    public boolean insertAtEnd([boolean value])

#### Parameters

value  

#### Return Value

### Method insertIfEmpty

    public boolean insertIfEmpty([boolean value])

#### Parameters

value  

#### Return Value

### Method isBaseDataSource

    public boolean isBaseDataSource()

#### Return Value

### Method isInheritanceDataSource

    public boolean isInheritanceDataSource()

#### Return Value

### Method isMasterDataSource

    public boolean isMasterDataSource()

#### Return Value

### Method joinRelation

    public str joinRelation([str value])

#### Parameters

value  

#### Return Value

### Method joinSource

    public int joinSource([AnyType value])

#### Parameters

value  

#### Return Value

### Method linkType

    public int linkType([int value])

#### Parameters

value  

#### Return Value

### Method masterDataSource

    public FormBuildDataSource masterDataSource()

#### Return Value

### Method maxAccessRight

    public int maxAccessRight([int value])

#### Parameters

value  

#### Return Value

### Method maxRecordsToLoad

    public int maxRecordsToLoad([int value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, rable, query, or another MSDAX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

### Method onlyFetchActive

    public boolean onlyFetchActive([boolean value])

#### Parameters

value  

#### Return Value

### Method optionalRecordMode

    public int optionalRecordMode([int value])

#### Parameters

value  

#### Return Value

### Method startPosition

    public int startPosition([int value])

#### Parameters

value  

#### Return Value

### Method table

Gets or sets the table ID associated with the object.

    public TableId table([TableId value])

#### Parameters

value  

#### Return Value

The current value of the table ID associated with the object.

### Method validTimeStateAutoQuery

    public int validTimeStateAutoQuery([int value])

#### Parameters

value  

#### Return Value

### Method validTimeStateUpdate

    public int validTimeStateUpdate([int value])

#### Parameters

value  

#### Return Value

### Method RegisterXppDataFieldILImplementation

    public void RegisterXppDataFieldILImplementation(str fieldName, str className)

#### Parameters

fieldName  

<!-- -->

className  

### Method RegisterXppILImplementation

    public void RegisterXppILImplementation(str className)

#### Parameters

className  

### Method SetDataLinkType

    public void SetDataLinkType(QueryDataLinkType linkType, str parentDataSource)

#### Parameters

linkType  

<!-- -->

parentDataSource  

## Class FormBuildDateControl
    class FormBuildDateControl extends FormBuildControl

The FormBuildDateControl class lets you create, read, update, and delete X++ code and metadata.

### Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                                                                                      | Description                                                                                                                                   |
|-------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| public boolean alignControl(\[boolean value\])                                                              | Determines whether to align the control.                                                                                                      |
| public int alignment(\[int value\])                                                                         |                                                                                                                                               |
| public boolean allowEdit(\[boolean value\])                                                                 | Determines whether the user can change the contents of the control.                                                                           |
| public int arrayIndex(\[int value\])                                                                        |                                                                                                                                               |
| public boolean autoDeclaration(\[boolean value\])                                                           | Determines whether the system can declare a member variable that has the same name as the control.                                            |
| public int backgroundColor(\[int value\])                                                                   | Gets or sets the background color of the control.                                                                                             |
| public int backStyle(\[int value\])                                                                         | Determines whether the control background can be transparent.                                                                                 |
| public int bold(\[int value\])                                                                              | Gets or sets the weight of font that was used to output text in the control.                                                                  |
| public int border(\[int value\])                                                                            | Gets or sets the style of the borderline of the control.                                                                                      |
| public int cacheDataMethod(\[int value\])                                                                   |                                                                                                                                               |
| public int characterSet(\[int value\])                                                                      | Gets or sets the character set of the font.                                                                                                   |
| public int colorScheme(\[int value\])                                                                       | Gets or sets the color scheme of the control.                                                                                                 |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                    | Gets or sets the configuration key that is assigned to the control.                                                                           |
| public int containerId()                                                                                    | Retrieves the ID of the parent container for the control.                                                                                     |
| public str countryRegionCodes(\[str value\])                                                                |                                                                                                                                               |
| public FieldId countryRegionContextField(\[FieldId value\])                                                 |                                                                                                                                               |
| public FieldId dataField(\[FieldId value\])                                                                 |                                                                                                                                               |
| public str dataMethod(\[str value\])                                                                        |                                                                                                                                               |
| public str dataRelationPath(\[str value\])                                                                  |                                                                                                                                               |
| public int dataSource(\[AnyType value\])                                                                    | Gets or sets a data source that will be used by the control or the form.                                                                      |
| public int dateDay(\[int value\])                                                                           |                                                                                                                                               |
| public int dateFormat(\[int value\])                                                                        |                                                                                                                                               |
| public int dateMonth(\[int value\])                                                                         |                                                                                                                                               |
| public int dateSeparator(\[int value\])                                                                     |                                                                                                                                               |
| public Date dateValue(\[Date value\])                                                                       |                                                                                                                                               |
| public int dateYear(\[int value\])                                                                          |                                                                                                                                               |
| public int direction(\[int value\])                                                                         |                                                                                                                                               |
| public int displayHeight(\[int value\], \[AutoMode mode\])                                                  |                                                                                                                                               |
| public AutoMode displayHeightMode(\[AutoMode mode\])                                                        |                                                                                                                                               |
| public int displayHeightValue(\[int value\])                                                                |                                                                                                                                               |
| public int displayLength(\[int value\], \[AutoMode mode\])                                                  |                                                                                                                                               |
| public AutoMode displayLengthMode(\[AutoMode mode\])                                                        |                                                                                                                                               |
| public int displayLengthValue(\[int value\])                                                                |                                                                                                                                               |
| public int displayTarget(\[int value\])                                                                     |                                                                                                                                               |
| public int dragDrop(\[int value\])                                                                          | Determines whether to enable or disable drag-and-drop operations for the control.                                                             |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether to enable or disable the object.                                                                                           |
| public ExtendedTypeId extendedDataType(\[ExtendedTypeId value\])                                            |                                                                                                                                               |
| public int fastTabSummary(\[int value\])                                                                    |                                                                                                                                               |
| public str font(\[str value\])                                                                              | Gets or sets the name of the font for the control to use.                                                                                     |
| public int fontSize(\[int value\])                                                                          | Gets or sets the size of the font for the control to use.                                                                                     |
| public int foregroundColor(\[int value\])                                                                   | Gets or sets the text color for the control to use.                                                                                           |
| public int height(int value, \[int mode\])                                                                  | Gets or sets the height of the control.                                                                                                       |
| public int heightMode(\[int value\])                                                                        | Gets or sets a calculation mode for the height of the control.                                                                                |
| public int heightValue(\[int value\])                                                                       | Gets or sets the height of the control.                                                                                                       |
| public str helpText(\[str value\])                                                                          | Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.                                      |
| public str hierarchyParent(\[str value\])                                                                   |                                                                                                                                               |
| public int id()                                                                                             | Retrieves the ID of the control.                                                                                                              |
| public int iMEMode(\[int value\])                                                                           |                                                                                                                                               |
| public boolean isContainer()                                                                                | Retrieves a value that indicates whether the control is a container control.                                                                  |
| public boolean italic(\[boolean value\])                                                                    |                                                                                                                                               |
| public str label(\[str value\])                                                                             | Gets or sets the label for a control.                                                                                                         |
| public int labelAlignment(\[int value\])                                                                    |                                                                                                                                               |
| public int labelBold(\[int value\])                                                                         |                                                                                                                                               |
| public int labelCharacterSet(\[int value\])                                                                 |                                                                                                                                               |
| public str labelFont(\[str value\])                                                                         |                                                                                                                                               |
| public int labelFontSize(\[int value\])                                                                     |                                                                                                                                               |
| public int labelForegroundColor(\[int value\])                                                              |                                                                                                                                               |
| public int labelGuide(\[int value\])                                                                        |                                                                                                                                               |
| public int labelHeight(int value, \[int mode\])                                                             |                                                                                                                                               |
| public int labelHeightMode(\[int value\])                                                                   |                                                                                                                                               |
| public int labelHeightValue(\[int value\])                                                                  |                                                                                                                                               |
| public boolean labelItalic(\[boolean value\])                                                               |                                                                                                                                               |
| public int labelPosition(\[int value\])                                                                     |                                                                                                                                               |
| public boolean labelUnderline(\[boolean value\])                                                            |                                                                                                                                               |
| public int labelWidth(int value, \[int mode\])                                                              |                                                                                                                                               |
| public int labelWidthMode(\[int value\])                                                                    |                                                                                                                                               |
| public int labelWidthValue(\[int value\])                                                                   |                                                                                                                                               |
| public int left(int value, \[int mode\])                                                                    |                                                                                                                                               |
| public int leftMode(\[int value\])                                                                          |                                                                                                                                               |
| public int leftValue(\[int value\])                                                                         |                                                                                                                                               |
| public int limitText(\[int value\], \[AutoMode mode\])                                                      |                                                                                                                                               |
| public AutoMode limitTextMode(\[AutoMode mode\])                                                            |                                                                                                                                               |
| public int limitTextValue(\[int value\])                                                                    |                                                                                                                                               |
| public int lookupButton(\[int value\])                                                                      |                                                                                                                                               |
| public boolean mandatory(\[boolean value\])                                                                 |                                                                                                                                               |
| public str maxDateLabel(\[str value\])                                                                      |                                                                                                                                               |
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics 365 for Operations application object. |
| public int neededPermission(\[int value\])                                                                  |                                                                                                                                               |
| public int promptrect(\[int value\])                                                                        |                                                                                                                                               |
| public boolean replaceOnLookup(\[boolean value\])                                                           |                                                                                                                                               |
| public int searchAfterInput(\[int value\])                                                                  |                                                                                                                                               |
| public int searchMode(\[int value\])                                                                        |                                                                                                                                               |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                   |                                                                                                                                               |
| public boolean showLabel(\[boolean value\])                                                                 |                                                                                                                                               |
| public boolean skip(\[boolean value\])                                                                      | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.               |
| public int style(\[int value\])                                                                             |                                                                                                                                               |
| public int top(int value, \[int mode\])                                                                     |                                                                                                                                               |
| public int topMode(\[int value\])                                                                           |                                                                                                                                               |
| public int topValue(\[int value\])                                                                          |                                                                                                                                               |
| public int type(\[int value\])                                                                              |                                                                                                                                               |
| public boolean underline(\[boolean value\])                                                                 | Sets or returns the underline property for the text in the control.                                                                           |
| public int userData(\[int value\])                                                                          |                                                                                                                                               |
| public int userDataItem(\[int value\])                                                                      |                                                                                                                                               |
| public int userDataItems(\[int value\])                                                                     |                                                                                                                                               |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                |                                                                                                                                               |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                      |                                                                                                                                               |
| public int verticalSpacingValue(\[int value\])                                                              |                                                                                                                                               |
| public int viewEditMode(\[int value\])                                                                      |                                                                                                                                               |
| public boolean visible(\[boolean value\])                                                                   |                                                                                                                                               |
| public int width(int value, \[int mode\])                                                                   | Gets or sets the width of the control.                                                                                                        |
| public int widthMode(\[int value\])                                                                         | Gets or sets the calculation mode of the width of the control.                                                                                |
| public int widthValue(\[int value\])                                                                        | Gets or sets the width of the control.                                                                                                        |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                               |

### Method alignControl

Determines whether to align the control.

    public boolean alignControl([boolean value])

#### Parameters

value  

#### Return Value

true if the control should be aligned; otherwise, false.

#### Remarks

The upper-left corner of the control is aligned according to the longest label.

### Method alignment

    public int alignment([int value])

#### Parameters

value  

#### Return Value

### Method allowEdit

Determines whether the user can change the contents of the control.

    public boolean allowEdit([boolean value])

#### Parameters

value  

#### Return Value

true if the control can be edited; otherwise, false.

#### Remarks

When this property is set on a container control, modifications are disabled or enabled for all controls in the container.

### Method arrayIndex

    public int arrayIndex([int value])

#### Parameters

value  

#### Return Value

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method backgroundColor

Gets or sets the background color of the control.

    public int backgroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method backStyle

Determines whether the control background can be transparent.

    public int backStyle([int value])

#### Parameters

value  

#### Return Value

1 if the control background can be transparent; otherwise, 0.

### Method bold

Gets or sets the weight of font that was used to output text in the control.

    public int bold([int value])

#### Parameters

value  

#### Return Value

An integer value between zero and nine, inclusive.

#### Remarks

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

### Method border

Gets or sets the style of the borderline of the control.

    public int border([int value])

#### Parameters

value  

#### Return Value

An integer between zero and four, inclusive.

#### Remarks

The integer that is returned contains the style of the borderline of the control as follows:

| Value. | Description. |
|--------|--------------|
| 0      | Auto.        |
| 1      | 3D.          |
| 2      | Single line. |
| 3      | Flat.        |
| 4      | None.        |

### Method cacheDataMethod

    public int cacheDataMethod([int value])

#### Parameters

value  

#### Return Value

### Method characterSet

Gets or sets the character set of the font.

    public int characterSet([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the character set of the font.

#### Remarks

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

The default character set is set to a value that is based on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET. For more information, see the LOGFONT structure on the MSDN Web site, http://go.microsoft.com/fwlink/?LinkID=85972.

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  

#### Return Value

An integer between zero and two, inclusive.

#### Remarks

The color scheme is defined according to the following table:

| Value. | Style.                         |
|--------|--------------------------------|
| 0      | Default.                       |
| 1      | The Microsoft Windows palette. |
| 2      | The true-color scheme.         |

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method containerId

Retrieves the ID of the parent container for the control.

    public int containerId()

#### Return Value

The ID of the parent container.

### Method countryRegionCodes

    public str countryRegionCodes([str value])

#### Parameters

value  

#### Return Value

### Method countryRegionContextField

    public FieldId countryRegionContextField([FieldId value])

#### Parameters

value  

#### Return Value

### Method dataField

    public FieldId dataField([FieldId value])

#### Parameters

value  

#### Return Value

### Method dataMethod

    public str dataMethod([str value])

#### Parameters

value  

#### Return Value

### Method dataRelationPath

    public str dataRelationPath([str value])

#### Parameters

value  

#### Return Value

### Method dataSource

Gets or sets a data source that will be used by the control or the form.

    public int dataSource([AnyType value])

#### Parameters

value  

#### Return Value

The identifier of the data source that will be used.

### Method dateDay

    public int dateDay([int value])

#### Parameters

value  

#### Return Value

### Method dateFormat

    public int dateFormat([int value])

#### Parameters

value  

#### Return Value

### Method dateMonth

    public int dateMonth([int value])

#### Parameters

value  

#### Return Value

### Method dateSeparator

    public int dateSeparator([int value])

#### Parameters

value  

#### Return Value

### Method dateValue

    public Date dateValue([Date value])

#### Parameters

value  

#### Return Value

### Method dateYear

    public int dateYear([int value])

#### Parameters

value  

#### Return Value

### Method direction

    public int direction([int value])

#### Parameters

value  

#### Return Value

### Method displayHeight

    public int displayHeight([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method displayHeightMode

    public AutoMode displayHeightMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method displayHeightValue

    public int displayHeightValue([int value])

#### Parameters

value  

#### Return Value

### Method displayLength

    public int displayLength([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method displayLengthMode

    public AutoMode displayLengthMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method displayLengthValue

    public int displayLengthValue([int value])

#### Parameters

value  

#### Return Value

### Method displayTarget

    public int displayTarget([int value])

#### Parameters

value  

#### Return Value

### Method dragDrop

Determines whether to enable or disable drag-and-drop operations for the control.

    public int dragDrop([int value])

#### Parameters

value  

#### Return Value

1 if drag-and-drop operations are enabled; otherwise, false.

### Method enabled

Determines whether to enable or disable the object.

    public boolean enabled([boolean value])

#### Parameters

value  

#### Return Value

true if the object is enabled; otherwise, false.

#### Remarks

The enabled property allows for controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

### Method extendedDataType

    public ExtendedTypeId extendedDataType([ExtendedTypeId value])

#### Parameters

value  

#### Return Value

### Method fastTabSummary

    public int fastTabSummary([int value])

#### Parameters

value  

#### Return Value

### Method font

Gets or sets the name of the font for the control to use.

    public str font([str value])

#### Parameters

value  

#### Return Value

The name of the font to use, such as Tahoma or Verdana.

### Method fontSize

Gets or sets the size of the font for the control to use.

    public int fontSize([int value])

#### Parameters

value  

#### Return Value

The height of the font in points.

### Method foregroundColor

Gets or sets the text color for the control to use.

    public int foregroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method height

Gets or sets the height of the control.

    public int height(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

The height of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the height according to the following table:

| Mode.            | Height calculation.                                                                       |
|------------------|-------------------------------------------------------------------------------------------|
| -1 Exact.        | The exact height in pixels of the controls is used.                                       |
| 0 Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height. | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

### Method heightMode

Gets or sets a calculation mode for the height of the control.

    public int heightMode([int value])

#### Parameters

value  

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table:

| Mode.          | Height Calculation.                                                                       |
|----------------|-------------------------------------------------------------------------------------------|
| Exact.         | The exact height in pixels of the controls is used.                                       |
| Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height. | The layout of the form determines the height of the control.                              |

The height of the control might change when the mode is set to auto or column height.

### Method heightValue

Gets or sets the height of the control.

    public int heightValue([int value])

#### Parameters

value  

#### Return Value

The height in pixels.

#### Remarks

The height of the control is not changed unless the exact height calculation mode is used.

### Method helpText

Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property sheet. The help text must not exceed 250 characters.

### Method hierarchyParent

    public str hierarchyParent([str value])

#### Parameters

value  

#### Return Value

### Method id

Retrieves the ID of the control.

    public int id()

#### Return Value

The ID of the control.

### Method iMEMode

    public int iMEMode([int value])

#### Parameters

value  

#### Return Value

### Method isContainer

Retrieves a value that indicates whether the control is a container control.

    public boolean isContainer()

#### Return Value

A Boolean value that indicates whether the control is a container control.

### Method italic

    public boolean italic([boolean value])

#### Parameters

value  

#### Return Value

### Method label

Gets or sets the label for a control.

    public str label([str value])

#### Parameters

value  

#### Return Value

The current value of the label string.

#### Remarks

The label determines which text is displayed in the control or adjacent to it. The label property value cannot exceed 250 characters.

### Method labelAlignment

    public int labelAlignment([int value])

#### Parameters

value  

#### Return Value

### Method labelBold

    public int labelBold([int value])

#### Parameters

value  

#### Return Value

### Method labelCharacterSet

    public int labelCharacterSet([int value])

#### Parameters

value  

#### Return Value

### Method labelFont

    public str labelFont([str value])

#### Parameters

value  

#### Return Value

### Method labelFontSize

    public int labelFontSize([int value])

#### Parameters

value  

#### Return Value

### Method labelForegroundColor

    public int labelForegroundColor([int value])

#### Parameters

value  

#### Return Value

### Method labelGuide

    public int labelGuide([int value])

#### Parameters

value  

#### Return Value

### Method labelHeight

    public int labelHeight(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method labelHeightMode

    public int labelHeightMode([int value])

#### Parameters

value  

#### Return Value

### Method labelHeightValue

    public int labelHeightValue([int value])

#### Parameters

value  

#### Return Value

### Method labelItalic

    public boolean labelItalic([boolean value])

#### Parameters

value  

#### Return Value

### Method labelPosition

    public int labelPosition([int value])

#### Parameters

value  

#### Return Value

### Method labelUnderline

    public boolean labelUnderline([boolean value])

#### Parameters

value  

#### Return Value

### Method labelWidth

    public int labelWidth(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method labelWidthMode

    public int labelWidthMode([int value])

#### Parameters

value  

#### Return Value

### Method labelWidthValue

    public int labelWidthValue([int value])

#### Parameters

value  

#### Return Value

### Method left

    public int left(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method leftMode

    public int leftMode([int value])

#### Parameters

value  

#### Return Value

### Method leftValue

    public int leftValue([int value])

#### Parameters

value  

#### Return Value

### Method limitText

    public int limitText([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method limitTextMode

    public AutoMode limitTextMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method limitTextValue

    public int limitTextValue([int value])

#### Parameters

value  

#### Return Value

### Method lookupButton

    public int lookupButton([int value])

#### Parameters

value  

#### Return Value

### Method mandatory

    public boolean mandatory([boolean value])

#### Parameters

value  

#### Return Value

### Method maxDateLabel

    public str maxDateLabel([str value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics 365 for Operations application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in the code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enumeration types, classes, and so on.

### Method neededPermission

    public int neededPermission([int value])

#### Parameters

value  

#### Return Value

### Method promptrect

    public int promptrect([int value])

#### Parameters

value  

#### Return Value

### Method replaceOnLookup

    public boolean replaceOnLookup([boolean value])

#### Parameters

value  

#### Return Value

### Method searchAfterInput

    public int searchAfterInput([int value])

#### Parameters

value  

#### Return Value

### Method searchMode

    public int searchMode([int value])

#### Parameters

value  

#### Return Value

### Method securityKey

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  

#### Return Value

### Method showLabel

    public boolean showLabel([boolean value])

#### Parameters

value  

#### Return Value

### Method skip

Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.

    public boolean skip([boolean value])

#### Parameters

value  
The value to assign to the skip property of the control.

#### Return Value

true if the control is skipped when the user presses the TAB key to move to the control; otherwise, false.

### Method style

    public int style([int value])

#### Parameters

value  

#### Return Value

### Method top

    public int top(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method topMode

    public int topMode([int value])

#### Parameters

value  

#### Return Value

### Method topValue

    public int topValue([int value])

#### Parameters

value  

#### Return Value

### Method type

    public int type([int value])

#### Parameters

value  

#### Return Value

### Method underline

Sets or returns the underline property for the text in the control.

    public boolean underline([boolean value])

#### Parameters

value  
The value to assign to the underline property of the control.

#### Return Value

true if the text in the control is underlined; otherwise, false.

### Method userData

    public int userData([int value])

#### Parameters

value  

#### Return Value

### Method userDataItem

    public int userDataItem([int value])

#### Parameters

value  

#### Return Value

### Method userDataItems

    public int userDataItems([int value])

#### Parameters

value  

#### Return Value

### Method verticalSpacing

    public int verticalSpacing([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method verticalSpacingMode

    public AutoMode verticalSpacingMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method verticalSpacingValue

    public int verticalSpacingValue([int value])

#### Parameters

value  

#### Return Value

### Method viewEditMode

    public int viewEditMode([int value])

#### Parameters

value  

#### Return Value

### Method visible

    public boolean visible([boolean value])

#### Parameters

value  

#### Return Value

### Method width

Gets or sets the width of the control.

    public int width(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

The width of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the width according to the following table:

| Mode.           | Width calculation.                                                                       |
|-----------------|------------------------------------------------------------------------------------------|
| -1 Exact.       | The exact width in pixels of the controls is used.                                       |
| 0 Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width. | The layout of the form determines the width of the control.                              |

The width and width calculation mode can be set separately.

### Method widthMode

Gets or sets the calculation mode of the width of the control.

    public int widthMode([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table:

| Mode.         | Width Calculation.                                                                       |
|---------------|------------------------------------------------------------------------------------------|
| Exact.        | The exact width in pixels of the controls is used.                                       |
| Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width. | The layout of the form determines the width of the control.                              |

The width of the control might change when the mode is set to auto or column width.

### Method widthValue

Gets or sets the width of the control.

    public int widthValue([int value])

#### Parameters

value  

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

## Class FormBuildDateTimeControl
    class FormBuildDateTimeControl extends FormBuildControl

### Remarks

### Examples

### Methods

| Method                                                                                                      | Description                                                                                                                               |
|-------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public boolean alignControl(\[boolean value\])                                                              | Determines whether to align the control.                                                                                                  |
| public int alignment(\[int value\])                                                                         |                                                                                                                                           |
| public boolean allowEdit(\[boolean value\])                                                                 | Determines whether the user can change the contents of the control.                                                                       |
| public int arrayIndex(\[int value\])                                                                        |                                                                                                                                           |
| public boolean autoDeclaration(\[boolean value\])                                                           | Determines whether the system can declare a member variable that has the same name as the control.                                        |
| public int backgroundColor(\[int value\])                                                                   | Gets or sets the background color of the control.                                                                                         |
| public int backStyle(\[int value\])                                                                         | Determines whether the control background can be transparent.                                                                             |
| public int bold(\[int value\])                                                                              | Gets or sets the weight of font that is used to output text in the control.                                                               |
| public int border(\[int value\])                                                                            | Gets or sets the style of the borderline of the control.                                                                                  |
| public int cacheDataMethod(\[int value\])                                                                   |                                                                                                                                           |
| public int characterSet(\[int value\])                                                                      | Gets or sets the character set of the font.                                                                                               |
| public int colorScheme(\[int value\])                                                                       | Gets or sets the color scheme of the control.                                                                                             |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                    | Gets or sets the configuration key that is assigned to the control.                                                                       |
| public int containerId()                                                                                    | Retrieves the ID of the parent container for the control.                                                                                 |
| public str countryRegionCodes(\[str value\])                                                                |                                                                                                                                           |
| public FieldId countryRegionContextField(\[FieldId value\])                                                 |                                                                                                                                           |
| public FieldId dataField(\[FieldId value\])                                                                 |                                                                                                                                           |
| public str dataMethod(\[str value\])                                                                        |                                                                                                                                           |
| public str dataRelationPath(\[str value\])                                                                  |                                                                                                                                           |
| public int dataSource(\[AnyType value\])                                                                    | Gets or sets a data source that will be used by the control or the form.                                                                  |
| public int dateDay(\[int value\])                                                                           |                                                                                                                                           |
| public int dateFormat(\[int value\])                                                                        |                                                                                                                                           |
| public int dateMonth(\[int value\])                                                                         |                                                                                                                                           |
| public int dateSeparator(\[int value\])                                                                     |                                                                                                                                           |
| public DateTime dateTimeValue(\[DateTime value\])                                                           |                                                                                                                                           |
| public int dateYear(\[int value\])                                                                          |                                                                                                                                           |
| public int displayOption(\[int value\])                                                                     |                                                                                                                                           |
| public int displayTarget(\[int value\])                                                                     |                                                                                                                                           |
| public int dragDrop(\[int value\])                                                                          | Determines whether to enable or disable drag-and-drop operations for the control.                                                         |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether to enable or disable the object.                                                                                       |
| public ExtendedTypeId extendedDataType(\[ExtendedTypeId value\])                                            |                                                                                                                                           |
| public int fastTabSummary(\[int value\])                                                                    |                                                                                                                                           |
| public str font(\[str value\])                                                                              | Gets or sets the name of the font for the control to use.                                                                                 |
| public int fontSize(\[int value\])                                                                          | Gets or sets the size of the font for the control to use.                                                                                 |
| public int foregroundColor(\[int value\])                                                                   | Gets or sets the text color for the control to use.                                                                                       |
| public int height(int value, \[int mode\])                                                                  | Gets or sets the height of the control.                                                                                                   |
| public int heightMode(\[int value\])                                                                        | Gets or sets a calculation mode for the height of the control.                                                                            |
| public int heightValue(\[int value\])                                                                       | Gets or sets the height of the control.                                                                                                   |
| public str helpText(\[str value\])                                                                          | Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.                                  |
| public str hierarchyParent(\[str value\])                                                                   |                                                                                                                                           |
| public int id()                                                                                             | Retrieves the ID of the control.                                                                                                          |
| public boolean isContainer()                                                                                | Retrieves a value that indicates whether the control is a container control.                                                              |
| public boolean italic(\[boolean value\])                                                                    |                                                                                                                                           |
| public str label(\[str value\])                                                                             | Gets or sets the label for a control.                                                                                                     |
| public int labelAlignment(\[int value\])                                                                    |                                                                                                                                           |
| public int labelBold(\[int value\])                                                                         |                                                                                                                                           |
| public int labelCharacterSet(\[int value\])                                                                 |                                                                                                                                           |
| public str labelFont(\[str value\])                                                                         |                                                                                                                                           |
| public int labelFontSize(\[int value\])                                                                     |                                                                                                                                           |
| public int labelForegroundColor(\[int value\])                                                              |                                                                                                                                           |
| public int labelGuide(\[int value\])                                                                        |                                                                                                                                           |
| public int labelHeight(int value, \[int mode\])                                                             |                                                                                                                                           |
| public int labelHeightMode(\[int value\])                                                                   |                                                                                                                                           |
| public int labelHeightValue(\[int value\])                                                                  |                                                                                                                                           |
| public boolean labelItalic(\[boolean value\])                                                               |                                                                                                                                           |
| public int labelPosition(\[int value\])                                                                     |                                                                                                                                           |
| public boolean labelUnderline(\[boolean value\])                                                            |                                                                                                                                           |
| public int labelWidth(int value, \[int mode\])                                                              |                                                                                                                                           |
| public int labelWidthMode(\[int value\])                                                                    |                                                                                                                                           |
| public int labelWidthValue(\[int value\])                                                                   |                                                                                                                                           |
| public int left(int value, \[int mode\])                                                                    |                                                                                                                                           |
| public int leftMode(\[int value\])                                                                          |                                                                                                                                           |
| public int leftValue(\[int value\])                                                                         |                                                                                                                                           |
| public int limitText(\[int value\], \[AutoMode mode\])                                                      |                                                                                                                                           |
| public AutoMode limitTextMode(\[AutoMode mode\])                                                            |                                                                                                                                           |
| public int limitTextValue(\[int value\])                                                                    |                                                                                                                                           |
| public int lookupButton(\[int value\])                                                                      |                                                                                                                                           |
| public boolean mandatory(\[boolean value\])                                                                 |                                                                                                                                           |
| public str maxDateLabel(\[str value\])                                                                      |                                                                                                                                           |
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics 365 for Operations application object. |
| public int neededPermission(\[int value\])                                                                  |                                                                                                                                           |
| public int promptrect(\[int value\])                                                                        |                                                                                                                                           |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                   |                                                                                                                                           |
| public boolean showLabel(\[boolean value\])                                                                 |                                                                                                                                           |
| public boolean skip(\[boolean value\])                                                                      |                                                                                                                                           |
| public int timeFormat(\[int value\])                                                                        |                                                                                                                                           |
| public int timeHours(\[int value\])                                                                         |                                                                                                                                           |
| public int timeMinute(\[int value\])                                                                        |                                                                                                                                           |
| public int timeSeconds(\[int value\])                                                                       |                                                                                                                                           |
| public int timeSeparator(\[int value\])                                                                     |                                                                                                                                           |
| public int timeZoneIndicator(\[int value\])                                                                 |                                                                                                                                           |
| public int timezonePreference(\[int value\])                                                                |                                                                                                                                           |
| public int top(int value, \[int mode\])                                                                     |                                                                                                                                           |
| public int topMode(\[int value\])                                                                           |                                                                                                                                           |
| public int topValue(\[int value\])                                                                          |                                                                                                                                           |
| public int type(\[int value\])                                                                              |                                                                                                                                           |
| public boolean underline(\[boolean value\])                                                                 |                                                                                                                                           |
| public int userData(\[int value\])                                                                          |                                                                                                                                           |
| public int userDataItem(\[int value\])                                                                      |                                                                                                                                           |
| public int userDataItems(\[int value\])                                                                     |                                                                                                                                           |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                |                                                                                                                                           |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                      |                                                                                                                                           |
| public int verticalSpacingValue(\[int value\])                                                              |                                                                                                                                           |
| public int viewEditMode(\[int value\])                                                                      |                                                                                                                                           |
| public boolean visible(\[boolean value\])                                                                   |                                                                                                                                           |
| public int width(int value, \[int mode\])                                                                   | Gets or sets the width of the control.                                                                                                    |
| public int widthMode(\[int value\])                                                                         | Gets or sets the calculation mode of the width of the control.                                                                            |
| public int widthValue(\[int value\])                                                                        | Gets or sets the width of the control.                                                                                                    |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                           |

### Method alignControl

Determines whether to align the control.

    public boolean alignControl([boolean value])

#### Parameters

value  

#### Return Value

true if the control should be aligned; otherwise, false.

#### Remarks

The upper-left corner of the control is aligned according to the longest label.

### Method alignment

    public int alignment([int value])

#### Parameters

value  

#### Return Value

### Method allowEdit

Determines whether the user can change the contents of the control.

    public boolean allowEdit([boolean value])

#### Parameters

value  

#### Return Value

true if the control can be edited; otherwise, false.

#### Remarks

When this property is set on a container control, modifications are disabled or enabled for all controls in the container.

### Method arrayIndex

    public int arrayIndex([int value])

#### Parameters

value  

#### Return Value

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method backgroundColor

Gets or sets the background color of the control.

    public int backgroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method backStyle

Determines whether the control background can be transparent.

    public int backStyle([int value])

#### Parameters

value  

#### Return Value

1 if the control background can be transparent; otherwise, 0.

### Method bold

Gets or sets the weight of font that is used to output text in the control.

    public int bold([int value])

#### Parameters

value  

#### Return Value

An integer value between zero and nine, inclusive.

#### Remarks

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

### Method border

Gets or sets the style of the borderline of the control.

    public int border([int value])

#### Parameters

value  

#### Return Value

An integer between zero and four, inclusive.

#### Remarks

The integer that is returned contains the style of the borderline of the control as follows:

| Value. | Description. |
|--------|--------------|
| 0      | Auto.        |
| 1      | 3D.          |
| 2      | Single line. |
| 3      | Flat.        |
| 4      | None.        |

### Method cacheDataMethod

    public int cacheDataMethod([int value])

#### Parameters

value  

#### Return Value

### Method characterSet

Gets or sets the character set of the font.

    public int characterSet([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the character set of the font.

#### Remarks

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

The value in the following table is for the Korean language edition of MicrosoftWindows.

| Value. | Description.   |
|--------|----------------|
| 130    | JOHAB\_CHARSET |

The values in the following table are for the Middle East language edition of MicrosoftWindows.

| Value. | Description.    |
|--------|-----------------|
| 177    | HEBREW\_CHARSET |
| 178    | ARABIC\_CHARSET |

The value in the following table is for the Thai language edition of MicrosoftWindows.

| Value. | Description.  |
|--------|---------------|
| 222    | THAI\_CHARSET |

The default character set is set to a value, depending on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET. For more information, see the LOGFONT structure on the MSDN Web site, http://go.microsoft.com/fwlink/?LinkID=85972.

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  

#### Return Value

An integer between zero and two, inclusive.

#### Remarks

The color scheme is defined according to the following table:

| Value. | Style.                        |
|--------|-------------------------------|
| 0      | Default.                      |
| 1      | The MicrosoftWindows palette. |
| 2      | The true-color scheme.        |

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method containerId

Retrieves the ID of the parent container for the control.

    public int containerId()

#### Return Value

The ID of the parent container.

### Method countryRegionCodes

    public str countryRegionCodes([str value])

#### Parameters

value  

#### Return Value

### Method countryRegionContextField

    public FieldId countryRegionContextField([FieldId value])

#### Parameters

value  

#### Return Value

### Method dataField

    public FieldId dataField([FieldId value])

#### Parameters

value  

#### Return Value

### Method dataMethod

    public str dataMethod([str value])

#### Parameters

value  

#### Return Value

### Method dataRelationPath

    public str dataRelationPath([str value])

#### Parameters

value  

#### Return Value

### Method dataSource

Gets or sets a data source that will be used by the control or the form.

    public int dataSource([AnyType value])

#### Parameters

value  

#### Return Value

The identifier of the data source that will be used.

### Method dateDay

    public int dateDay([int value])

#### Parameters

value  

#### Return Value

### Method dateFormat

    public int dateFormat([int value])

#### Parameters

value  

#### Return Value

### Method dateMonth

    public int dateMonth([int value])

#### Parameters

value  

#### Return Value

### Method dateSeparator

    public int dateSeparator([int value])

#### Parameters

value  

#### Return Value

### Method dateTimeValue

    public DateTime dateTimeValue([DateTime value])

#### Parameters

value  

#### Return Value

### Method dateYear

    public int dateYear([int value])

#### Parameters

value  

#### Return Value

### Method displayOption

    public int displayOption([int value])

#### Parameters

value  

#### Return Value

### Method displayTarget

    public int displayTarget([int value])

#### Parameters

value  

#### Return Value

### Method dragDrop

Determines whether to enable or disable drag-and-drop operations for the control.

    public int dragDrop([int value])

#### Parameters

value  

#### Return Value

1 if drag-and-drop operations are enabled; otherwise, false.

### Method enabled

Determines whether to enable or disable the object.

    public boolean enabled([boolean value])

#### Parameters

value  

#### Return Value

true if the object is enabled; otherwise, false.

#### Remarks

The enabled property allows for controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

### Method extendedDataType

    public ExtendedTypeId extendedDataType([ExtendedTypeId value])

#### Parameters

value  

#### Return Value

### Method fastTabSummary

    public int fastTabSummary([int value])

#### Parameters

value  

#### Return Value

### Method font

Gets or sets the name of the font for the control to use.

    public str font([str value])

#### Parameters

value  

#### Return Value

The name of the font to use, such as Tahoma or Verdana.

### Method fontSize

Gets or sets the size of the font for the control to use.

    public int fontSize([int value])

#### Parameters

value  

#### Return Value

The height of the font in points.

### Method foregroundColor

Gets or sets the text color for the control to use.

    public int foregroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method height

Gets or sets the height of the control.

    public int height(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

The height of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the height according to the following table:

| Mode.            | Height calculation.                                                                       |
|------------------|-------------------------------------------------------------------------------------------|
| -1 Exact.        | The exact height in pixels of the controls is used.                                       |
| 0 Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height. | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

### Method heightMode

Gets or sets a calculation mode for the height of the control.

    public int heightMode([int value])

#### Parameters

value  

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table:

| Mode.          | Height Calculation.                                                                       |
|----------------|-------------------------------------------------------------------------------------------|
| Exact.         | The exact height in pixels of the controls is used.                                       |
| Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height. | The layout of the form determines the height of the control.                              |

The height of the control might change when the mode is set to auto or column height.

### Method heightValue

Gets or sets the height of the control.

    public int heightValue([int value])

#### Parameters

value  

#### Return Value

The height in pixels.

#### Remarks

The height of the control is not changed unless the exact height calculation mode is used.

### Method helpText

Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property dialog box. The help text must not exceed 250 characters.

### Method hierarchyParent

    public str hierarchyParent([str value])

#### Parameters

value  

#### Return Value

### Method id

Retrieves the ID of the control.

    public int id()

#### Return Value

The ID of the control.

### Method isContainer

Retrieves a value that indicates whether the control is a container control.

    public boolean isContainer()

#### Return Value

A Boolean value that indicates whether the control is a container control.

### Method italic

    public boolean italic([boolean value])

#### Parameters

value  

#### Return Value

### Method label

Gets or sets the label for a control.

    public str label([str value])

#### Parameters

value  

#### Return Value

The current value of the label string.

#### Remarks

The label determines which text is displayed in the control or adjacent to it. The label property value cannot exceed 250 characters.

### Method labelAlignment

    public int labelAlignment([int value])

#### Parameters

value  

#### Return Value

### Method labelBold

    public int labelBold([int value])

#### Parameters

value  

#### Return Value

### Method labelCharacterSet

    public int labelCharacterSet([int value])

#### Parameters

value  

#### Return Value

### Method labelFont

    public str labelFont([str value])

#### Parameters

value  

#### Return Value

### Method labelFontSize

    public int labelFontSize([int value])

#### Parameters

value  

#### Return Value

### Method labelForegroundColor

    public int labelForegroundColor([int value])

#### Parameters

value  

#### Return Value

### Method labelGuide

    public int labelGuide([int value])

#### Parameters

value  

#### Return Value

### Method labelHeight

    public int labelHeight(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method labelHeightMode

    public int labelHeightMode([int value])

#### Parameters

value  

#### Return Value

### Method labelHeightValue

    public int labelHeightValue([int value])

#### Parameters

value  

#### Return Value

### Method labelItalic

    public boolean labelItalic([boolean value])

#### Parameters

value  

#### Return Value

### Method labelPosition

    public int labelPosition([int value])

#### Parameters

value  

#### Return Value

### Method labelUnderline

    public boolean labelUnderline([boolean value])

#### Parameters

value  

#### Return Value

### Method labelWidth

    public int labelWidth(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method labelWidthMode

    public int labelWidthMode([int value])

#### Parameters

value  

#### Return Value

### Method labelWidthValue

    public int labelWidthValue([int value])

#### Parameters

value  

#### Return Value

### Method left

    public int left(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method leftMode

    public int leftMode([int value])

#### Parameters

value  

#### Return Value

### Method leftValue

    public int leftValue([int value])

#### Parameters

value  

#### Return Value

### Method limitText

    public int limitText([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method limitTextMode

    public AutoMode limitTextMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method limitTextValue

    public int limitTextValue([int value])

#### Parameters

value  

#### Return Value

### Method lookupButton

    public int lookupButton([int value])

#### Parameters

value  

#### Return Value

### Method mandatory

    public boolean mandatory([boolean value])

#### Parameters

value  

#### Return Value

### Method maxDateLabel

    public str maxDateLabel([str value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics 365 for Operations application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enumerations, classes, and so on.

### Method neededPermission

    public int neededPermission([int value])

#### Parameters

value  

#### Return Value

### Method promptrect

    public int promptrect([int value])

#### Parameters

value  

#### Return Value

### Method securityKey

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  

#### Return Value

### Method showLabel

    public boolean showLabel([boolean value])

#### Parameters

value  

#### Return Value

### Method skip

    public boolean skip([boolean value])

#### Parameters

value  

#### Return Value

### Method timeFormat

    public int timeFormat([int value])

#### Parameters

value  

#### Return Value

### Method timeHours

    public int timeHours([int value])

#### Parameters

value  

#### Return Value

### Method timeMinute

    public int timeMinute([int value])

#### Parameters

value  

#### Return Value

### Method timeSeconds

    public int timeSeconds([int value])

#### Parameters

value  

#### Return Value

### Method timeSeparator

    public int timeSeparator([int value])

#### Parameters

value  

#### Return Value

### Method timeZoneIndicator

    public int timeZoneIndicator([int value])

#### Parameters

value  

#### Return Value

### Method timezonePreference

    public int timezonePreference([int value])

#### Parameters

value  

#### Return Value

### Method top

    public int top(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method topMode

    public int topMode([int value])

#### Parameters

value  

#### Return Value

### Method topValue

    public int topValue([int value])

#### Parameters

value  

#### Return Value

### Method type

    public int type([int value])

#### Parameters

value  

#### Return Value

### Method underline

    public boolean underline([boolean value])

#### Parameters

value  

#### Return Value

### Method userData

    public int userData([int value])

#### Parameters

value  

#### Return Value

### Method userDataItem

    public int userDataItem([int value])

#### Parameters

value  

#### Return Value

### Method userDataItems

    public int userDataItems([int value])

#### Parameters

value  

#### Return Value

### Method verticalSpacing

    public int verticalSpacing([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method verticalSpacingMode

    public AutoMode verticalSpacingMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method verticalSpacingValue

    public int verticalSpacingValue([int value])

#### Parameters

value  

#### Return Value

### Method viewEditMode

    public int viewEditMode([int value])

#### Parameters

value  

#### Return Value

### Method visible

    public boolean visible([boolean value])

#### Parameters

value  

#### Return Value

### Method width

Gets or sets the width of the control.

    public int width(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

The width of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the width according to the following table:

| Mode.           | Width calculation.                                                                       |
|-----------------|------------------------------------------------------------------------------------------|
| -1 Exact.       | The exact width in pixels of the controls is used.                                       |
| 0 Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width. | The layout of the form determines the width of the control.                              |

The width and width calculation mode can be set separately.

### Method widthMode

Gets or sets the calculation mode of the width of the control.

    public int widthMode([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table:

| Mode.         | Width Calculation.                                                                       |
|---------------|------------------------------------------------------------------------------------------|
| Exact.        | The exact width in pixels of the controls is used.                                       |
| Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width. | The layout of the form determines the width of the control.                              |

The width of the control might change when the mode is set to auto or column width.

### Method widthValue

Gets or sets the width of the control.

    public int widthValue([int value])

#### Parameters

value  

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

## Class FormBuildDesign
    class FormBuildDesign extends Object

The FormBuildDesign class modifies a form design.

### Remarks

This class lets you create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

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

### Method addControl

    public Object addControl(FormControlType controlType, str controlName, [FormBuildControl insertAfter], [boolean pushFront])

#### Parameters

controlType  

<!-- -->

controlName  

<!-- -->

insertAfter  

<!-- -->

pushFront  

#### Return Value

### Method addControlEx

    public Object addControlEx(str controlClass, str controlName, [FormBuildControl insertAfter], [boolean pushFront])

#### Parameters

controlClass  

<!-- -->

controlName  

<!-- -->

insertAfter  

<!-- -->

pushFront  

#### Return Value

### Method alignChild

    public boolean alignChild([boolean value])

#### Parameters

value  

#### Return Value

### Method alignChildren

    public boolean alignChildren([boolean value])

#### Parameters

value  

#### Return Value

### Method allowDocking

    public boolean allowDocking([boolean value])

#### Parameters

value  

#### Return Value

### Method allowFormCompanyChange

    public boolean allowFormCompanyChange([boolean value])

#### Parameters

value  

#### Return Value

### Method allowImplicitParent

    public boolean allowImplicitParent([boolean value])

#### Parameters

value  

#### Return Value

### Method allowUserSetup

    public int allowUserSetup([int value])

#### Parameters

value  

#### Return Value

### Method alwaysOnTop

    public boolean alwaysOnTop([boolean value])

#### Parameters

value  

#### Return Value

### Method arrangeGuide

    public int arrangeGuide([int value])

#### Parameters

value  

#### Return Value

### Method arrangeMethod

    public int arrangeMethod([int value])

#### Parameters

value  

#### Return Value

### Method arrangeWhen

    public int arrangeWhen([int value])

#### Parameters

value  

#### Return Value

### Method backgroundColor

Gets or sets the background color of the control.

    public int backgroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method bold

Gets or sets the weight of font that is used to output text in the control.

    public int bold([int value])

#### Parameters

value  

#### Return Value

An integer value between zero and nine, inclusive.

#### Remarks

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

### Method bottomMargin

    public int bottomMargin([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method bottomMarginMode

    public AutoMode bottomMarginMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method bottomMarginValue

    public int bottomMarginValue([int value])

#### Parameters

value  

#### Return Value

### Method caption

Gets or set the caption of the control.

    public str caption([str value])

#### Parameters

value  

#### Return Value

The string that is used as the caption of the control.

### Method characterSet

Gets or sets the character set of the font.

    public int characterSet([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the character set of the font.

#### Remarks

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

The value in the following table is for the Korean language edition of MicrosoftWindows.

| Value. | Description.   |
|--------|----------------|
| 130    | JOHAB\_CHARSET |

The values in the following table are for the Middle East language edition of MicrosoftWindows.

| Value. | Description.    |
|--------|-----------------|
| 177    | HEBREW\_CHARSET |
| 178    | ARABIC\_CHARSET |

The value in the following table is for the Thai language edition of MicrosoftWindows.

| Value. | Description.  |
|--------|---------------|
| 222    | THAI\_CHARSET |

The default character set is set to a value that is based on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET.For more information, see the LOGFONT structure on the MSDN Web site, http://go.microsoft.com/fwlink/?LinkID=85972.

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  

#### Return Value

An integer between zero and two, inclusive.

#### Remarks

The color scheme is defined according to the following table:

| Value. | Style.                        |
|--------|-------------------------------|
| 0      | Default.                      |
| 1      | The MicrosoftWindows palette. |
| 2      | The true-color scheme.        |

### Method columns

    public int columns([int value], [ColumnsMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method columnsMode

    public ColumnsMode columnsMode([ColumnsMode mode])

#### Parameters

mode  

#### Return Value

### Method columnspace

    public int columnspace([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method columnspaceMode

    public AutoMode columnspaceMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method columnspaceValue

    public int columnspaceValue([int value])

#### Parameters

value  

#### Return Value

### Method columnsValue

    public int columnsValue([int value])

#### Parameters

value  

#### Return Value

### Method control

    public Object control(AnyType control)

#### Parameters

control  

#### Return Value

### Method controlCount

    public int controlCount()

#### Return Value

### Method controlNum

    public FormBuildControl controlNum(int controlNo)

#### Parameters

controlNo  

#### Return Value

### Method cssClass

    public str cssClass([str value])

#### Parameters

value  

#### Return Value

### Method dataSource

Gets or sets a data source that should be used by the control or the form.

    public int dataSource([AnyType value])

#### Parameters

value  

#### Return Value

The identifier of the data source that will be used.

### Method defaultAction

    public str defaultAction([str value])

#### Parameters

value  

#### Return Value

### Method font

Gets or sets the name of the font for the control to use.

    public str font([str value])

#### Parameters

value  

#### Return Value

The name of the font to use, such as Tahoma or Verdana.

### Method fontSize

Gets or sets the size of the font for the control to use.

    public int fontSize([int value])

#### Parameters

value  

#### Return Value

The height of the font in points.

### Method frame

    public int frame([int value])

#### Parameters

value  

#### Return Value

### Method height

Gets or sets the height of the control.

    public int height(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

The height of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the height according to the following table:

| Mode.            | Height calculation.                                                                       |
|------------------|-------------------------------------------------------------------------------------------|
| -1 Exact.        | The exact height in pixels of the controls is used.                                       |
| 0 Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height. | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

### Method heightMode

Gets or sets a calculation mode for the height of the control.

    public int heightMode([int value])

#### Parameters

value  

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table:

| Mode.          | Height Calculation.                                                                       |
|----------------|-------------------------------------------------------------------------------------------|
| Exact.         | The exact height in pixels of the controls is used.                                       |
| Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height. | The layout of the form determines the height of the control.                              |

The height of the control might change when the mode is set to auto or column height.

### Method heightValue

Gets or sets the height of the control.

    public int heightValue([int value])

#### Parameters

value  

#### Return Value

The height in pixels.

#### Remarks

The height of the control is not changed unless the exact height calculation mode is used.

### Method hideIfEmpty

    public boolean hideIfEmpty([boolean value])

#### Parameters

value  

#### Return Value

### Method hideToolbar

    public boolean hideToolbar([boolean value])

#### Parameters

value  

#### Return Value

### Method imagemode

    public int imagemode([int value])

#### Parameters

value  

#### Return Value

### Method imageName

    public str imageName([str value])

#### Parameters

value  

#### Return Value

### Method imageResource

    public int imageResource([int value])

#### Parameters

value  

#### Return Value

### Method italic

    public boolean italic([boolean value])

#### Parameters

value  

#### Return Value

### Method labelBold

    public int labelBold([int value])

#### Parameters

value  

#### Return Value

### Method labelCharacterSet

    public int labelCharacterSet([int value])

#### Parameters

value  

#### Return Value

### Method labelFont

    public str labelFont([str value])

#### Parameters

value  

#### Return Value

### Method labelFontSize

    public int labelFontSize([int value])

#### Parameters

value  

#### Return Value

### Method labelItalic

    public boolean labelItalic([boolean value])

#### Parameters

value  

#### Return Value

### Method labelUnderline

    public boolean labelUnderline([boolean value])

#### Parameters

value  

#### Return Value

### Method left

    public int left(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method leftMargin

    public int leftMargin([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method leftMarginMode

    public AutoMode leftMarginMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method leftMarginValue

    public int leftMarginValue([int value])

#### Parameters

value  

#### Return Value

### Method leftMode

    public int leftMode([int value])

#### Parameters

value  

#### Return Value

### Method leftValue

    public int leftValue([int value])

#### Parameters

value  

#### Return Value

### Method localWebMenu

    public str localWebMenu([str value])

#### Parameters

value  

#### Return Value

### Method maximizeBox

    public boolean maximizeBox([boolean value])

#### Parameters

value  

#### Return Value

### Method minimizeBox

    public boolean minimizeBox([boolean value])

#### Parameters

value  

#### Return Value

### Method mode

    public int mode([int value])

#### Parameters

value  

#### Return Value

### Method moveControl

    public int moveControl(int controlId, [int insertAfterControlId])

#### Parameters

controlId  

<!-- -->

insertAfterControlId  

#### Return Value

### Method newRecordAction

    public str newRecordAction([str value])

#### Parameters

value  

#### Return Value

### Method rightMargin

    public int rightMargin([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method rightMarginMode

    public AutoMode rightMarginMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method rightMarginValue

    public int rightMarginValue([int value])

#### Parameters

value  

#### Return Value

### Method saveSize

    public boolean saveSize([boolean value])

#### Parameters

value  

#### Return Value

### Method scrollbars

    public int scrollbars([int value])

#### Parameters

value  

#### Return Value

### Method setCompany

    public boolean setCompany([boolean value])

#### Parameters

value  

#### Return Value

### Method showDeleteButton

    public int showDeleteButton([int value])

#### Parameters

value  

#### Return Value

### Method showNewButton

    public int showNewButton([int value])

#### Parameters

value  

#### Return Value

### Method showWebHelp

    public int showWebHelp([int value])

#### Parameters

value  

#### Return Value

### Method statusBarStyle

    public int statusBarStyle([int value])

#### Parameters

value  

#### Return Value

### Method style

    public int style([int value])

#### Parameters

value  

#### Return Value

### Method submitMethod

    public int submitMethod([int value])

#### Parameters

value  

#### Return Value

### Method supportReload

    public boolean supportReload([boolean value])

#### Parameters

value  

#### Return Value

### Method titleDatasource

    public int titleDatasource([AnyType value])

#### Parameters

value  

#### Return Value

### Method top

    public int top(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method topMargin

    public int topMargin([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method topMarginMode

    public AutoMode topMarginMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method topMarginValue

    public int topMarginValue([int value])

#### Parameters

value  

#### Return Value

### Method topMode

    public int topMode([int value])

#### Parameters

value  

#### Return Value

### Method topValue

    public int topValue([int value])

#### Parameters

value  

#### Return Value

### Method underline

    public boolean underline([boolean value])

#### Parameters

value  

#### Return Value

### Method useCaptionFromMenuItem

    public int useCaptionFromMenuItem([int value])

#### Parameters

value  

#### Return Value

### Method viewEditMode

    public int viewEditMode([int value])

#### Parameters

value  

#### Return Value

### Method visible

    public boolean visible([boolean value])

#### Parameters

value  

#### Return Value

### Method width

Gets or sets the width of the control.

    public int width(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

The width of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted.Calculate the width according to the following table:

| Mode.           | Width calculation.                                                                       |
|-----------------|------------------------------------------------------------------------------------------|
| -1 Exact.       | The exact width in pixels of the controls is used.                                       |
| 0 Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width. | The layout of the form determines the width of the control.                              |

The width and width calculation mode can be set separately.

### Method widthMode

Gets or sets the calculation mode of the width of the control.

    public int widthMode([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table:

| Mode.         | Width Calculation.                                                                       |
|---------------|------------------------------------------------------------------------------------------|
| Exact.        | The exact width in pixels of the controls is used.                                       |
| Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width. | The layout of the form determines the width of the control.                              |

The width of the control might change when the mode is set to auto or column width.

### Method widthValue

Gets or sets the width of the control.

    public int widthValue([int value])

#### Parameters

value  

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method windowResize

    public int windowResize([int value])

#### Parameters

value  

#### Return Value

### Method windowType

    public int windowType([int value])

#### Parameters

value  

#### Return Value

### Method workflowDatasource

    public int workflowDatasource([AnyType value])

#### Parameters

value  

#### Return Value

### Method workflowEnabled

    public boolean workflowEnabled([boolean value])

#### Parameters

value  

#### Return Value

### Method workflowType

    public str workflowType([str value])

#### Parameters

value  

#### Return Value

### Method dialogSize

    public int dialogSize([int value])

#### Parameters

value  

#### Return Value

## Class FormBuildDropDialogButtonControl
    class FormBuildDropDialogButtonControl extends FormBuildControl

### Remarks

### Examples

### Methods

| Method                                                                                                      | Description                                                                                                                               |
|-------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public boolean alignControl(\[boolean value\])                                                              | Determines whether to align the control.                                                                                                  |
| public int alignment(\[int value\])                                                                         |                                                                                                                                           |
| public boolean allowEdit(\[boolean value\])                                                                 | Determines whether the user can change the contents of the control.                                                                       |
| public boolean autoDeclaration(\[boolean value\])                                                           | Determines whether the system can declare a member variable that has the same name as the control.                                        |
| public boolean autoRefreshData(\[boolean value\])                                                           |                                                                                                                                           |
| public int backgroundColor(\[int value\])                                                                   | Gets or sets the background color of the control.                                                                                         |
| public int backStyle(\[int value\])                                                                         | Determines whether the control background can be transparent.                                                                             |
| public boolean big(\[boolean value\])                                                                       |                                                                                                                                           |
| public int bold(\[int value\])                                                                              | Gets or sets the weight of font that is used to output text in the control.                                                               |
| public int border(\[int value\])                                                                            | Gets or sets the style of the borderline of the control.                                                                                  |
| public int buttonDisplay(\[int value\])                                                                     | Gets or sets the appearance of the button control.                                                                                        |
| public str caption(\[str value\])                                                                           | Gets or set the caption of the control.                                                                                                   |
| public int characterSet(\[int value\])                                                                      | Gets or sets the character set of the font.                                                                                               |
| public int colorScheme(\[int value\])                                                                       | Gets or sets the color scheme of the control.                                                                                             |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                    | Gets or sets the configuration key that is assigned to the control.                                                                       |
| public int containerId()                                                                                    | Retrieves the ID of the parent container for the control.                                                                                 |
| public int copyCallerQuery(\[int value\])                                                                   |                                                                                                                                           |
| public str countryRegionCodes(\[str value\])                                                                |                                                                                                                                           |
| public FieldId countryRegionContextField(\[FieldId value\])                                                 |                                                                                                                                           |
| public str dataRelationPath(\[str value\])                                                                  |                                                                                                                                           |
| public int dataSource(\[AnyType value\])                                                                    | Gets or sets a data source that will be used by the control or the form.                                                                  |
| public boolean defaultButton(\[boolean value\])                                                             | Determines whether the button should be the default button on the form.                                                                   |
| public str disabledImage(\[str value\])                                                                     | Gets or sets the disabled image of the button.                                                                                            |
| public int disabledImageLocation(\[int value\])                                                             |                                                                                                                                           |
| public int disabledResource(\[int value\])                                                                  | Gets or sets the resource ID of the image to use as the disabled button image.                                                            |
| public int displayTarget(\[int value\])                                                                     |                                                                                                                                           |
| public int dragDrop(\[int value\])                                                                          | Determines whether to enable or disable drag-and-drop operations for the control.                                                         |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether to enable or disable the object.                                                                                       |
| public str font(\[str value\])                                                                              | Gets or sets the name of the font for the control to use.                                                                                 |
| public int fontSize(\[int value\])                                                                          | Gets or sets the size of the font for the control to use.                                                                                 |
| public boolean forcedToOverflow(\[boolean value\])                                                          |                                                                                                                                           |
| public int foregroundColor(\[int value\])                                                                   | Gets or sets the text color for the control to use.                                                                                       |
| public int formViewOption(\[int value\])                                                                    |                                                                                                                                           |
| public int height(int value, \[int mode\])                                                                  | Gets or sets the height of the control.                                                                                                   |
| public int heightMode(\[int value\])                                                                        | Gets or sets a calculation mode for the height of the control.                                                                            |
| public int heightValue(\[int value\])                                                                       | Gets or sets the height of the control.                                                                                                   |
| public str helpText(\[str value\])                                                                          | Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.                                  |
| public str hierarchyParent(\[str value\])                                                                   |                                                                                                                                           |
| public int id()                                                                                             | Retrieves the ID of the control.                                                                                                          |
| public int imageLocation(\[int value\])                                                                     |                                                                                                                                           |
| public boolean isContainer()                                                                                | Retrieves a value that indicates whether the control is a container control.                                                              |
| public boolean italic(\[boolean value\])                                                                    |                                                                                                                                           |
| public str keyTip(\[str value\])                                                                            |                                                                                                                                           |
| public int left(int value, \[int mode\])                                                                    |                                                                                                                                           |
| public int leftMode(\[int value\])                                                                          |                                                                                                                                           |
| public int leftValue(\[int value\])                                                                         |                                                                                                                                           |
| public str menuItemName(\[str value\])                                                                      |                                                                                                                                           |
| public int multiSelect(\[int value\])                                                                       |                                                                                                                                           |
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics 365 for Operations application object. |
| public int neededPermission(\[int value\])                                                                  |                                                                                                                                           |
| public int needsRecord(\[int value\])                                                                       |                                                                                                                                           |
| public str normalImage(\[str value\])                                                                       |                                                                                                                                           |
| public int normalResource(\[int value\])                                                                    |                                                                                                                                           |
| public int openMode(\[int value\])                                                                          |                                                                                                                                           |
| public str parameters(\[str value\])                                                                        | Gets or sets the list of parameters that are passed to objects that are run by the MenuFunction class.                                    |
| public boolean primary(\[boolean value\])                                                                   |                                                                                                                                           |
| public boolean saveRecord(\[boolean value\])                                                                |                                                                                                                                           |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                   |                                                                                                                                           |
| public boolean sendExternalContext(\[boolean value\])                                                       |                                                                                                                                           |
| public int shortkey(\[int value\])                                                                          |                                                                                                                                           |
| public boolean showShortCut(\[boolean value\])                                                              |                                                                                                                                           |
| public boolean skip(\[boolean value\])                                                                      |                                                                                                                                           |
| public int style(\[int value\])                                                                             |                                                                                                                                           |
| public str text(\[str value\])                                                                              |                                                                                                                                           |
| public int top(int value, \[int mode\])                                                                     |                                                                                                                                           |
| public int topMode(\[int value\])                                                                           |                                                                                                                                           |
| public int topValue(\[int value\])                                                                          |                                                                                                                                           |
| public int type(\[int value\])                                                                              |                                                                                                                                           |
| public boolean underline(\[boolean value\])                                                                 |                                                                                                                                           |
| public int userData(\[int value\])                                                                          |                                                                                                                                           |
| public int userDataItem(\[int value\])                                                                      |                                                                                                                                           |
| public int userDataItems(\[int value\])                                                                     |                                                                                                                                           |
| public boolean value(\[boolean value\])                                                                     |                                                                                                                                           |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                |                                                                                                                                           |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                      |                                                                                                                                           |
| public int verticalSpacingValue(\[int value\])                                                              |                                                                                                                                           |
| public boolean visible(\[boolean value\])                                                                   |                                                                                                                                           |
| public int width(int value, \[int mode\])                                                                   | Gets or sets the width of the control.                                                                                                    |
| public int widthMode(\[int value\])                                                                         | Gets or sets the calculation mode of the width of the control.                                                                            |
| public int widthValue(\[int value\])                                                                        | Gets or sets the width of the control.                                                                                                    |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                           |

### Method alignControl

Determines whether to align the control.

    public boolean alignControl([boolean value])

#### Parameters

value  

#### Return Value

true if the control should be aligned; otherwise, false.

#### Remarks

The upper-left corner of the control is aligned according to the longest label.

### Method alignment

    public int alignment([int value])

#### Parameters

value  

#### Return Value

### Method allowEdit

Determines whether the user can change the contents of the control.

    public boolean allowEdit([boolean value])

#### Parameters

value  

#### Return Value

true if the control can be edited; otherwise, false.

#### Remarks

When this property is set on a container control, modifications are disabled or enabled for all controls in the container.

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method autoRefreshData

    public boolean autoRefreshData([boolean value])

#### Parameters

value  

#### Return Value

### Method backgroundColor

Gets or sets the background color of the control.

    public int backgroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method backStyle

Determines whether the control background can be transparent.

    public int backStyle([int value])

#### Parameters

value  

#### Return Value

1 if the control background can be transparent; otherwise, 0.

### Method big

    public boolean big([boolean value])

#### Parameters

value  

#### Return Value

### Method bold

Gets or sets the weight of font that is used to output text in the control.

    public int bold([int value])

#### Parameters

value  

#### Return Value

An integer value between zero and nine, inclusive.

#### Remarks

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

### Method border

Gets or sets the style of the borderline of the control.

    public int border([int value])

#### Parameters

value  

#### Return Value

An integer between zero and four, inclusive.

#### Remarks

The integer that is returned contains the style of the borderline of the control as follows:

| Value. | Description. |
|--------|--------------|
| 0      | Auto.        |
| 1      | 3D.          |
| 2      | Single line. |
| 3      | Flat.        |
| 4      | None.        |

### Method buttonDisplay

Gets or sets the appearance of the button control.

    public int buttonDisplay([int value])

#### Parameters

value  

#### Return Value

An integer between zero and five, inclusive.

#### Remarks

The value of the property defines whether the text, the image, or both should be displayed on the button. This property also controls relative positions of text and image if both are displayed. The integer value that is returned contains the appearance of the button control as follows:

| Value. | Description.                                                     |
|--------|------------------------------------------------------------------|
| 0      | Text only.                                                       |
| 1      | Image Only.                                                      |
| 2      | Text and image; the image is displayed below the text.           |
| 3      | Text and image; the image is displayed above the text.           |
| 4      | Text and image; the image is displayed to the left of the text.  |
| 5      | Text and image; the image is displayed to the right of the text. |

### Method caption

Gets or set the caption of the control.

    public str caption([str value])

#### Parameters

value  

#### Return Value

The string that is used as the caption of the control.

### Method characterSet

Gets or sets the character set of the font.

    public int characterSet([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the character set of the font.

#### Remarks

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

The default character set is set to a value that is based on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET. For more information, see the LOGFONT structure on the MSDN Web site, http://go.microsoft.com/fwlink/?LinkID=85972.

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  

#### Return Value

An integer between zero and two, inclusive.

#### Remarks

The color scheme is defined according to the following table:

| Value. | Style.                         |
|--------|--------------------------------|
| 0      | Default.                       |
| 1      | The Microsoft Windows palette. |
| 2      | The true-color scheme.         |

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method containerId

Retrieves the ID of the parent container for the control.

    public int containerId()

#### Return Value

The ID of the parent container.

### Method copyCallerQuery

    public int copyCallerQuery([int value])

#### Parameters

value  

#### Return Value

### Method countryRegionCodes

    public str countryRegionCodes([str value])

#### Parameters

value  

#### Return Value

### Method countryRegionContextField

    public FieldId countryRegionContextField([FieldId value])

#### Parameters

value  

#### Return Value

### Method dataRelationPath

    public str dataRelationPath([str value])

#### Parameters

value  

#### Return Value

### Method dataSource

Gets or sets a data source that will be used by the control or the form.

    public int dataSource([AnyType value])

#### Parameters

value  

#### Return Value

The identifier of the data source that will be used.

### Method defaultButton

Determines whether the button should be the default button on the form.

    public boolean defaultButton([boolean value])

#### Parameters

value  

#### Return Value

true if the button should be the default button; otherwise, false.

### Method disabledImage

Gets or sets the disabled image of the button.

    public str disabledImage([str value])

#### Parameters

value  

#### Return Value

The full name of an image file. The system supports all of the GDI-supported image formats.

#### Remarks

This property has precedence over the disabledResourceproperty . It is used if both of these properties are set.

### Method disabledImageLocation

    public int disabledImageLocation([int value])

#### Parameters

value  

#### Return Value

### Method disabledResource

Gets or sets the resource ID of the image to use as the disabled button image.

    public int disabledResource([int value])

#### Parameters

value  

#### Return Value

The resource ID of the image to use as the disabled button image. Both icon and bitmap images are supported.

### Method displayTarget

    public int displayTarget([int value])

#### Parameters

value  

#### Return Value

### Method dragDrop

Determines whether to enable or disable drag-and-drop operations for the control.

    public int dragDrop([int value])

#### Parameters

value  

#### Return Value

1 if drag-and-drop operations are enabled; otherwise, false.

### Method enabled

Determines whether to enable or disable the object.

    public boolean enabled([boolean value])

#### Parameters

value  

#### Return Value

true if the object is enabled; otherwise, false.

#### Remarks

The enabled property enables controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

### Method font

Gets or sets the name of the font for the control to use.

    public str font([str value])

#### Parameters

value  

#### Return Value

The name of the font to use, such as Tahoma or Verdana.

### Method fontSize

Gets or sets the size of the font for the control to use.

    public int fontSize([int value])

#### Parameters

value  

#### Return Value

The height of the font in points.

### Method forcedToOverflow

    public boolean forcedToOverflow([boolean value])

#### Parameters

value  

#### Return Value

### Method foregroundColor

Gets or sets the text color for the control to use.

    public int foregroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method formViewOption

    public int formViewOption([int value])

#### Parameters

value  

#### Return Value

### Method height

Gets or sets the height of the control.

    public int height(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

The height of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the height according to the following table:

| Mode.            | Height calculation.                                                                       |
|------------------|-------------------------------------------------------------------------------------------|
| -1 Exact.        | The exact height in pixels of the controls is used.                                       |
| 0 Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height. | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

### Method heightMode

Gets or sets a calculation mode for the height of the control.

    public int heightMode([int value])

#### Parameters

value  

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table:

| Mode.          | Height Calculation.                                                                       |
|----------------|-------------------------------------------------------------------------------------------|
| Exact.         | The exact height in pixels of the controls is used.                                       |
| Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height. | The layout of the form determines the height of the control.                              |

The height of the control might change when the mode is set to auto or column height.

### Method heightValue

Gets or sets the height of the control.

    public int heightValue([int value])

#### Parameters

value  

#### Return Value

The height in pixels.

#### Remarks

The height of the control is not changed unless the exact height calculation mode is used.

### Method helpText

Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property sheet. The help text must not exceed 250 characters.

### Method hierarchyParent

    public str hierarchyParent([str value])

#### Parameters

value  

#### Return Value

### Method id

Retrieves the ID of the control.

    public int id()

#### Return Value

The ID of the control.

### Method imageLocation

    public int imageLocation([int value])

#### Parameters

value  

#### Return Value

### Method isContainer

Retrieves a value that indicates whether the control is a container control.

    public boolean isContainer()

#### Return Value

A Boolean value that indicates whether the control is a container control.

### Method italic

    public boolean italic([boolean value])

#### Parameters

value  

#### Return Value

### Method keyTip

    public str keyTip([str value])

#### Parameters

value  

#### Return Value

### Method left

    public int left(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method leftMode

    public int leftMode([int value])

#### Parameters

value  

#### Return Value

### Method leftValue

    public int leftValue([int value])

#### Parameters

value  

#### Return Value

### Method menuItemName

    public str menuItemName([str value])

#### Parameters

value  

#### Return Value

### Method multiSelect

    public int multiSelect([int value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics 365 for Operations application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   It must start with a letter.
-   It cannot exceed 250 characters.
-   It can include numbers and underscore (\_) characters.
-   It cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enumerations, or classes.

### Method neededPermission

    public int neededPermission([int value])

#### Parameters

value  

#### Return Value

### Method needsRecord

    public int needsRecord([int value])

#### Parameters

value  

#### Return Value

### Method normalImage

    public str normalImage([str value])

#### Parameters

value  

#### Return Value

### Method normalResource

    public int normalResource([int value])

#### Parameters

value  

#### Return Value

### Method openMode

    public int openMode([int value])

#### Parameters

value  

#### Return Value

### Method parameters

Gets or sets the list of parameters that are passed to objects that are run by the MenuFunction class.

    public str parameters([str value])

#### Parameters

value  

#### Return Value

The list of parameters that are passed to the object.

#### Remarks

The parameters string format is Parameter1=Value1, Parameter2=Value2, and so on. If ignore is passed, unrecognized parameters.

### Method primary

    public boolean primary([boolean value])

#### Parameters

value  

#### Return Value

### Method saveRecord

    public boolean saveRecord([boolean value])

#### Parameters

value  

#### Return Value

### Method securityKey

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  

#### Return Value

### Method sendExternalContext

    public boolean sendExternalContext([boolean value])

#### Parameters

value  

#### Return Value

### Method shortkey

    public int shortkey([int value])

#### Parameters

value  

#### Return Value

### Method showShortCut

    public boolean showShortCut([boolean value])

#### Parameters

value  

#### Return Value

### Method skip

    public boolean skip([boolean value])

#### Parameters

value  

#### Return Value

### Method style

    public int style([int value])

#### Parameters

value  

#### Return Value

### Method text

    public str text([str value])

#### Parameters

value  

#### Return Value

### Method top

    public int top(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method topMode

    public int topMode([int value])

#### Parameters

value  

#### Return Value

### Method topValue

    public int topValue([int value])

#### Parameters

value  

#### Return Value

### Method type

    public int type([int value])

#### Parameters

value  

#### Return Value

### Method underline

    public boolean underline([boolean value])

#### Parameters

value  

#### Return Value

### Method userData

    public int userData([int value])

#### Parameters

value  

#### Return Value

### Method userDataItem

    public int userDataItem([int value])

#### Parameters

value  

#### Return Value

### Method userDataItems

    public int userDataItems([int value])

#### Parameters

value  

#### Return Value

### Method value

    public boolean value([boolean value])

#### Parameters

value  

#### Return Value

### Method verticalSpacing

    public int verticalSpacing([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method verticalSpacingMode

    public AutoMode verticalSpacingMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method verticalSpacingValue

    public int verticalSpacingValue([int value])

#### Parameters

value  

#### Return Value

### Method visible

    public boolean visible([boolean value])

#### Parameters

value  

#### Return Value

### Method width

Gets or sets the width of the control.

    public int width(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

The width of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the width according to the following table:

| Mode.           | Width calculation.                                                                       |
|-----------------|------------------------------------------------------------------------------------------|
| -1 Exact.       | The exact width in pixels of the controls is used.                                       |
| 0 Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width. | The layout of the form determines the width of the control.                              |

The width and width calculation mode can be set separately.

### Method widthMode

Gets or sets the calculation mode of the width of the control.

    public int widthMode([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table:

| Mode.         | Width Calculation.                                                                       |
|---------------|------------------------------------------------------------------------------------------|
| Exact.        | The exact width in pixels of the controls is used.                                       |
| Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width. | The layout of the form determines the width of the control.                              |

The width of the control might change when the mode is set to auto or column width.

### Method widthValue

Gets or sets the width of the control.

    public int widthValue([int value])

#### Parameters

value  

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

## Class FormBuildFastTabHeaderControl
    class FormBuildFastTabHeaderControl extends FormBuildControl

### Remarks

### Examples

### Methods

| Method                                                                                                      | Description                                                                                                                               |
|-------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public boolean alignChild(\[boolean value\])                                                                |                                                                                                                                           |
| public boolean alignChildren(\[boolean value\])                                                             |                                                                                                                                           |
| public boolean alignControl(\[boolean value\])                                                              | Determines whether to align the control.                                                                                                  |
| public boolean allowEdit(\[boolean value\])                                                                 | Determines whether the user can change the contents of the control.                                                                       |
| public int allowUserSetup(\[int value\])                                                                    |                                                                                                                                           |
| public int arrangeGuide(\[int value\])                                                                      |                                                                                                                                           |
| public int arrangeMethod(\[int value\])                                                                     |                                                                                                                                           |
| public int arrangeWhen(\[int value\])                                                                       |                                                                                                                                           |
| public boolean autoDeclaration(\[boolean value\])                                                           | Determines whether the system can declare a member variable that has the same name as the control.                                        |
| public int backgroundColor(\[int value\])                                                                   | Gets or sets the background color of the control.                                                                                         |
| public int backStyle(\[int value\])                                                                         | Determiness whether the control background can be transparent.                                                                            |
| public int bold(\[int value\])                                                                              | Gets or sets the weight of font used to output text in the control.                                                                       |
| public int bottomMargin(\[int value\], \[AutoMode mode\])                                                   |                                                                                                                                           |
| public AutoMode bottomMarginMode(\[AutoMode mode\])                                                         |                                                                                                                                           |
| public int bottomMarginValue(\[int value\])                                                                 |                                                                                                                                           |
| public str caption(\[str value\])                                                                           | Gets or set the caption of the control.                                                                                                   |
| public int characterSet(\[int value\])                                                                      | Gets or sets the character set of the font.                                                                                               |
| public int colorScheme(\[int value\])                                                                       | Gets or sets the color scheme of the control.                                                                                             |
| public int columns(\[int value\], \[ColumnsMode mode\])                                                     |                                                                                                                                           |
| public ColumnsMode columnsMode(\[ColumnsMode mode\])                                                        |                                                                                                                                           |
| public int columnspace(\[int value\], \[AutoMode mode\])                                                    |                                                                                                                                           |
| public AutoMode columnspaceMode(\[AutoMode mode\])                                                          |                                                                                                                                           |
| public int columnspaceValue(\[int value\])                                                                  |                                                                                                                                           |
| public int columnsValue(\[int value\])                                                                      |                                                                                                                                           |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                    | Gets or sets the configuration key that is assigned to the control.                                                                       |
| public int containerId()                                                                                    | Retrieves the ID of the parent container for the control.                                                                                 |
| public str countryRegionCodes(\[str value\])                                                                |                                                                                                                                           |
| public FieldId countryRegionContextField(\[FieldId value\])                                                 |                                                                                                                                           |
| public str dataRelationPath(\[str value\])                                                                  |                                                                                                                                           |
| public int dataSource(\[AnyType value\])                                                                    | Gets or sets a data source to be used by the control or the form.                                                                         |
| public int displayTarget(\[int value\])                                                                     |                                                                                                                                           |
| public int dragDrop(\[int value\])                                                                          | Determines whether to enable or disable drag-and-drop operations for the control.                                                         |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether to enable or disable the object.                                                                                       |
| public str font(\[str value\])                                                                              | Gets or sets the name of the font for the control to use.                                                                                 |
| public int fontSize(\[int value\])                                                                          | Gets or sets the size of the font for the control to use.                                                                                 |
| public int height(int value, \[int mode\])                                                                  | Gets or sets the height of the control.                                                                                                   |
| public int heightMode(\[int value\])                                                                        | Gets or sets a calculation mode for the height of the control.                                                                            |
| public int heightValue(\[int value\])                                                                       | Gets or sets the height of the control.                                                                                                   |
| public str helpText(\[str value\])                                                                          | Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.                                  |
| public boolean hideIfEmpty(\[boolean value\])                                                               |                                                                                                                                           |
| public str hierarchyParent(\[str value\])                                                                   |                                                                                                                                           |
| public int id()                                                                                             | Retrieves the ID of the control.                                                                                                          |
| public boolean isContainer()                                                                                | Retrieves a value that indicates whether the control is a container control.                                                              |
| public boolean italic(\[boolean value\])                                                                    |                                                                                                                                           |
| public int left(int value, \[int mode\])                                                                    |                                                                                                                                           |
| public int leftMargin(\[int value\], \[AutoMode mode\])                                                     |                                                                                                                                           |
| public AutoMode leftMarginMode(\[AutoMode mode\])                                                           |                                                                                                                                           |
| public int leftMarginValue(\[int value\])                                                                   |                                                                                                                                           |
| public int leftMode(\[int value\])                                                                          |                                                                                                                                           |
| public int leftValue(\[int value\])                                                                         |                                                                                                                                           |
| public int moveControl(int controlId, \[int insertAfterControlId\])                                         | Moves a specified control to the control.                                                                                                 |
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics 365 for Operations application object. |
| public int neededPermission(\[int value\])                                                                  |                                                                                                                                           |
| public int rightMargin(\[int value\], \[AutoMode mode\])                                                    |                                                                                                                                           |
| public AutoMode rightMarginMode(\[AutoMode mode\])                                                          |                                                                                                                                           |
| public int rightMarginValue(\[int value\])                                                                  |                                                                                                                                           |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                   |                                                                                                                                           |
| public boolean skip(\[boolean value\])                                                                      |                                                                                                                                           |
| public int top(int value, \[int mode\])                                                                     |                                                                                                                                           |
| public int topMargin(\[int value\], \[AutoMode mode\])                                                      |                                                                                                                                           |
| public AutoMode topMarginMode(\[AutoMode mode\])                                                            |                                                                                                                                           |
| public int topMarginValue(\[int value\])                                                                    |                                                                                                                                           |
| public int topMode(\[int value\])                                                                           |                                                                                                                                           |
| public int topValue(\[int value\])                                                                          |                                                                                                                                           |
| public int type(\[int value\])                                                                              |                                                                                                                                           |
| public boolean underline(\[boolean value\])                                                                 |                                                                                                                                           |
| public int userData(\[int value\])                                                                          |                                                                                                                                           |
| public int userDataItem(\[int value\])                                                                      |                                                                                                                                           |
| public int userDataItems(\[int value\])                                                                     |                                                                                                                                           |
| public boolean useUserLayout(\[boolean value\])                                                             |                                                                                                                                           |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                |                                                                                                                                           |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                      |                                                                                                                                           |
| public int verticalSpacingValue(\[int value\])                                                              |                                                                                                                                           |
| public boolean visible(\[boolean value\])                                                                   |                                                                                                                                           |
| public int width(int value, \[int mode\])                                                                   | Gets or sets the width of the control.                                                                                                    |
| public int widthMode(\[int value\])                                                                         | Gets or sets the calculation mode of the width of the control.                                                                            |
| public int widthValue(\[int value\])                                                                        | Gets or sets the width of the control.                                                                                                    |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                           |

### Method alignChild

    public boolean alignChild([boolean value])

#### Parameters

value  

#### Return Value

### Method alignChildren

    public boolean alignChildren([boolean value])

#### Parameters

value  

#### Return Value

### Method alignControl

Determines whether to align the control.

    public boolean alignControl([boolean value])

#### Parameters

value  

#### Return Value

true if the control should be aligned; otherwise, false.

#### Remarks

The upper-left corner of the control is aligned according to the longest label.

### Method allowEdit

Determines whether the user can change the contents of the control.

    public boolean allowEdit([boolean value])

#### Parameters

value  

#### Return Value

true if the control can be edited; otherwise, false.

#### Remarks

When this property is set on a container control, modifications are disabled or enabled for all controls within the container.

### Method allowUserSetup

    public int allowUserSetup([int value])

#### Parameters

value  

#### Return Value

### Method arrangeGuide

    public int arrangeGuide([int value])

#### Parameters

value  

#### Return Value

### Method arrangeMethod

    public int arrangeMethod([int value])

#### Parameters

value  

#### Return Value

### Method arrangeWhen

    public int arrangeWhen([int value])

#### Parameters

value  

#### Return Value

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method backgroundColor

Gets or sets the background color of the control.

    public int backgroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method backStyle

Determiness whether the control background can be transparent.

    public int backStyle([int value])

#### Parameters

value  

#### Return Value

1 if the control background can be transparent; otherwise, 0.

### Method bold

Gets or sets the weight of font used to output text in the control.

    public int bold([int value])

#### Parameters

value  

#### Return Value

An integer value between zero and nine, inclusive.

#### Remarks

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

### Method bottomMargin

    public int bottomMargin([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method bottomMarginMode

    public AutoMode bottomMarginMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method bottomMarginValue

    public int bottomMarginValue([int value])

#### Parameters

value  

#### Return Value

### Method caption

Gets or set the caption of the control.

    public str caption([str value])

#### Parameters

value  

#### Return Value

The string that is used as the caption of the control.

### Method characterSet

Gets or sets the character set of the font.

    public int characterSet([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the character set of the font.

#### Remarks

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

The default character set is set to a value based on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET. For more information, see the LOGFONT structure on the MSDN Web site, http://go.microsoft.com/fwlink/?LinkID=85972.

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  

#### Return Value

An integer between zero and two, inclusive.

#### Remarks

The color scheme is defined according to the following table:

| Value. | Style.                         |
|--------|--------------------------------|
| 0      | Default.                       |
| 1      | The Microsoft Windows palette. |
| 2      | The true-color scheme.         |

### Method columns

    public int columns([int value], [ColumnsMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method columnsMode

    public ColumnsMode columnsMode([ColumnsMode mode])

#### Parameters

mode  

#### Return Value

### Method columnspace

    public int columnspace([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method columnspaceMode

    public AutoMode columnspaceMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method columnspaceValue

    public int columnspaceValue([int value])

#### Parameters

value  

#### Return Value

### Method columnsValue

    public int columnsValue([int value])

#### Parameters

value  

#### Return Value

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method containerId

Retrieves the ID of the parent container for the control.

    public int containerId()

#### Return Value

The ID of the parent container.

### Method countryRegionCodes

    public str countryRegionCodes([str value])

#### Parameters

value  

#### Return Value

### Method countryRegionContextField

    public FieldId countryRegionContextField([FieldId value])

#### Parameters

value  

#### Return Value

### Method dataRelationPath

    public str dataRelationPath([str value])

#### Parameters

value  

#### Return Value

### Method dataSource

Gets or sets a data source to be used by the control or the form.

    public int dataSource([AnyType value])

#### Parameters

value  

#### Return Value

The identifier of the data source to be used.

### Method displayTarget

    public int displayTarget([int value])

#### Parameters

value  

#### Return Value

### Method dragDrop

Determines whether to enable or disable drag-and-drop operations for the control.

    public int dragDrop([int value])

#### Parameters

value  

#### Return Value

1 if drag-and-drop operations are enabled; otherwise, false.

### Method enabled

Determines whether to enable or disable the object.

    public boolean enabled([boolean value])

#### Parameters

value  

#### Return Value

true if the object is enabled; otherwise, false.

#### Remarks

The enabled property allows controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

### Method font

Gets or sets the name of the font for the control to use.

    public str font([str value])

#### Parameters

value  

#### Return Value

The name of the font to use, such as Tahoma or Verdana.

### Method fontSize

Gets or sets the size of the font for the control to use.

    public int fontSize([int value])

#### Parameters

value  

#### Return Value

The height of the font in points.

### Method height

Gets or sets the height of the control.

    public int height(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

The height of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the height according to the following table:

| Mode.            | Height calculation.                                                                       |
|------------------|-------------------------------------------------------------------------------------------|
| -1 Exact.        | The exact height in pixels of the controls is used.                                       |
| 0 Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height. | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

### Method heightMode

Gets or sets a calculation mode for the height of the control.

    public int heightMode([int value])

#### Parameters

value  

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table:

| Mode.          | Height Calculation.                                                                       |
|----------------|-------------------------------------------------------------------------------------------|
| Exact.         | The exact height in pixels of the controls is used.                                       |
| Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height. | The layout of the form determines the height of the control.                              |

The height of the control might change when the mode is set to auto or column height.

### Method heightValue

Gets or sets the height of the control.

    public int heightValue([int value])

#### Parameters

value  

#### Return Value

The height in pixels.

#### Remarks

The height of the control is not changed unless the exact height calculation mode is used.

### Method helpText

Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property sheet.The help text must not exceed 250 characters.

### Method hideIfEmpty

    public boolean hideIfEmpty([boolean value])

#### Parameters

value  

#### Return Value

### Method hierarchyParent

    public str hierarchyParent([str value])

#### Parameters

value  

#### Return Value

### Method id

Retrieves the ID of the control.

    public int id()

#### Return Value

The ID of the control.

### Method isContainer

Retrieves a value that indicates whether the control is a container control.

    public boolean isContainer()

#### Return Value

A Boolean value that indicates whether the control is a container control.

### Method italic

    public boolean italic([boolean value])

#### Parameters

value  

#### Return Value

### Method left

    public int left(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method leftMargin

    public int leftMargin([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method leftMarginMode

    public AutoMode leftMarginMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method leftMarginValue

    public int leftMarginValue([int value])

#### Parameters

value  

#### Return Value

### Method leftMode

    public int leftMode([int value])

#### Parameters

value  

#### Return Value

### Method leftValue

    public int leftValue([int value])

#### Parameters

value  

#### Return Value

### Method moveControl

Moves a specified control to the control.

    public int moveControl(int controlId, [int insertAfterControlId])

#### Parameters

controlId  

<!-- -->

insertAfterControlId  

#### Return Value

1 if the control was moved successfully; otherwise, 0.

#### Remarks

In general, if the specified control can be contained in the control and can be moved from the container that it is currently in, this method should succeed. However, in some cases, such as for the reference group control instance, controls cannot be moved.

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics 365 for Operations application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   It must start with a letter.
-   It cannot exceed 250 characters.
-   It can include numbers and underscore (\_) characters.
-   It cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enumerations, or classes.

### Method neededPermission

    public int neededPermission([int value])

#### Parameters

value  

#### Return Value

### Method rightMargin

    public int rightMargin([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method rightMarginMode

    public AutoMode rightMarginMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method rightMarginValue

    public int rightMarginValue([int value])

#### Parameters

value  

#### Return Value

### Method securityKey

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  

#### Return Value

### Method skip

    public boolean skip([boolean value])

#### Parameters

value  

#### Return Value

### Method top

    public int top(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method topMargin

    public int topMargin([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method topMarginMode

    public AutoMode topMarginMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method topMarginValue

    public int topMarginValue([int value])

#### Parameters

value  

#### Return Value

### Method topMode

    public int topMode([int value])

#### Parameters

value  

#### Return Value

### Method topValue

    public int topValue([int value])

#### Parameters

value  

#### Return Value

### Method type

    public int type([int value])

#### Parameters

value  

#### Return Value

### Method underline

    public boolean underline([boolean value])

#### Parameters

value  

#### Return Value

### Method userData

    public int userData([int value])

#### Parameters

value  

#### Return Value

### Method userDataItem

    public int userDataItem([int value])

#### Parameters

value  

#### Return Value

### Method userDataItems

    public int userDataItems([int value])

#### Parameters

value  

#### Return Value

### Method useUserLayout

    public boolean useUserLayout([boolean value])

#### Parameters

value  

#### Return Value

### Method verticalSpacing

    public int verticalSpacing([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method verticalSpacingMode

    public AutoMode verticalSpacingMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method verticalSpacingValue

    public int verticalSpacingValue([int value])

#### Parameters

value  

#### Return Value

### Method visible

    public boolean visible([boolean value])

#### Parameters

value  

#### Return Value

### Method width

Gets or sets the width of the control.

    public int width(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

The width of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the width according to the following table:

| Mode.           | Width calculation.                                                                       |
|-----------------|------------------------------------------------------------------------------------------|
| -1 Exact.       | The exact width in pixels of the controls is used.                                       |
| 0 Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width. | The layout of the form determines the width of the control.                              |

The width and width calculation mode can be set separately.

### Method widthMode

Gets or sets the calculation mode of the width of the control.

    public int widthMode([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table:

| Mode.         | Width Calculation.                                                                       |
|---------------|------------------------------------------------------------------------------------------|
| Exact.        | The exact width in pixels of the controls is used.                                       |
| Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width. | The layout of the form determines the width of the control.                              |

The width of the control might change when the mode is set to auto or column width.

### Method widthValue

Gets or sets the width of the control.

    public int widthValue([int value])

#### Parameters

value  

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

## Class FormBuildFastTabSummarySeparator
    class FormBuildFastTabSummarySeparator extends FormBuildControl

### Remarks

### Examples

### Methods

| Method                                                                                                      | Description                                                                                                                               |
|-------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public boolean alignControl(\[boolean value\])                                                              | Determines whether to align the control.                                                                                                  |
| public boolean allowEdit(\[boolean value\])                                                                 | Determines whether the user can change the contents of the control.                                                                       |
| public boolean autoDeclaration(\[boolean value\])                                                           | Determines whether the system can declare a member variable that has the same name as the control.                                        |
| public int backgroundColor(\[int value\])                                                                   | Gets or sets the background color of the control.                                                                                         |
| public int backStyle(\[int value\])                                                                         | Determiness whether the control background can be transparent.                                                                            |
| public int bold(\[int value\])                                                                              | Gets or sets the weight of font that is used to output text in the control.                                                               |
| public int characterSet(\[int value\])                                                                      | Gets or sets the character set of the font.                                                                                               |
| public int colorScheme(\[int value\])                                                                       | Gets or sets the color scheme of the control.                                                                                             |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                    | Gets or sets the configuration key that is assigned to the control.                                                                       |
| public int containerId()                                                                                    | Retrieves the ID of the parent container for the control.                                                                                 |
| public str countryRegionCodes(\[str value\])                                                                |                                                                                                                                           |
| public str dataRelationPath(\[str value\])                                                                  |                                                                                                                                           |
| public int displayTarget(\[int value\])                                                                     |                                                                                                                                           |
| public int dragDrop(\[int value\])                                                                          | Determines whether to enable or disable drag-and-drop operations for the control.                                                         |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether to enable or disable the object.                                                                                       |
| public str font(\[str value\])                                                                              | Gets or sets the name of the font for the control to use.                                                                                 |
| public int fontSize(\[int value\])                                                                          | Gets or sets the size of the font for the control to use.                                                                                 |
| public int height(int value, \[int mode\])                                                                  | Gets or sets the height of the control.                                                                                                   |
| public int heightMode(\[int value\])                                                                        | Gets or sets a calculation mode for the height of the control.                                                                            |
| public int heightValue(\[int value\])                                                                       | Gets or sets the height of the control.                                                                                                   |
| public str helpText(\[str value\])                                                                          | Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.                                  |
| public str hierarchyParent(\[str value\])                                                                   |                                                                                                                                           |
| public int id()                                                                                             | Retrieves the ID of the control.                                                                                                          |
| public boolean isContainer()                                                                                | Retrieves a value that indicates whether the control is a container control.                                                              |
| public boolean italic(\[boolean value\])                                                                    |                                                                                                                                           |
| public int left(int value, \[int mode\])                                                                    |                                                                                                                                           |
| public int leftMode(\[int value\])                                                                          |                                                                                                                                           |
| public int leftValue(\[int value\])                                                                         |                                                                                                                                           |
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics 365 for Operations application object. |
| public int neededPermission(\[int value\])                                                                  |                                                                                                                                           |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                   |                                                                                                                                           |
| public boolean skip(\[boolean value\])                                                                      |                                                                                                                                           |
| public int top(int value, \[int mode\])                                                                     |                                                                                                                                           |
| public int topMode(\[int value\])                                                                           |                                                                                                                                           |
| public int topValue(\[int value\])                                                                          |                                                                                                                                           |
| public int type(\[int value\])                                                                              |                                                                                                                                           |
| public boolean underline(\[boolean value\])                                                                 |                                                                                                                                           |
| public int userData(\[int value\])                                                                          |                                                                                                                                           |
| public int userDataItem(\[int value\])                                                                      |                                                                                                                                           |
| public int userDataItems(\[int value\])                                                                     |                                                                                                                                           |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                |                                                                                                                                           |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                      |                                                                                                                                           |
| public int verticalSpacingValue(\[int value\])                                                              |                                                                                                                                           |
| public boolean visible(\[boolean value\])                                                                   |                                                                                                                                           |
| public int width(int value, \[int mode\])                                                                   | Gets or sets the width of the control.                                                                                                    |
| public int widthMode(\[int value\])                                                                         | Gets or sets the calculation mode of the width of the control.                                                                            |
| public int widthValue(\[int value\])                                                                        | Gets or sets the width of the control.                                                                                                    |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                           |

### Method alignControl

Determines whether to align the control.

    public boolean alignControl([boolean value])

#### Parameters

value  

#### Return Value

true if the control should be aligned; otherwise, false.

#### Remarks

The upper-left corner of the control is aligned according to the longest label.

### Method allowEdit

Determines whether the user can change the contents of the control.

    public boolean allowEdit([boolean value])

#### Parameters

value  

#### Return Value

true if the control can be edited; otherwise, false.

#### Remarks

When this property is set on a container control, modifications are disabled or enabled for all controls in the container.

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method backgroundColor

Gets or sets the background color of the control.

    public int backgroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method backStyle

Determiness whether the control background can be transparent.

    public int backStyle([int value])

#### Parameters

value  

#### Return Value

1 if the control background can be transparent; otherwise, 0.

### Method bold

Gets or sets the weight of font that is used to output text in the control.

    public int bold([int value])

#### Parameters

value  

#### Return Value

An integer value between zero and nine, inclusive.

#### Remarks

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

### Method characterSet

Gets or sets the character set of the font.

    public int characterSet([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the character set of the font.

#### Remarks

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

The value in the following table is for the Korean language edition of MicrosoftWindows.

| Value. | Description.   |
|--------|----------------|
| 130    | JOHAB\_CHARSET |

The values in the following table are for the Middle East language edition of MicrosoftWindows.

| Value. | Description.    |
|--------|-----------------|
| 177    | HEBREW\_CHARSET |
| 178    | ARABIC\_CHARSET |

The value in the following table is for the Thai language edition of MicrosoftWindows.

| Value. | Description.  |
|--------|---------------|
| 222    | THAI\_CHARSET |

The default character set is set to a value that is based on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET. For more information, see the LOGFONT structure on the MSDN Web site, http://go.microsoft.com/fwlink/?LinkID=85972.

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  

#### Return Value

An integer between zero and two, inclusive.

#### Remarks

The color scheme is defined according to the following table:

| Value. | Style.                         |
|--------|--------------------------------|
| 0      | Default.                       |
| 1      | The Microsoft Windows palette. |
| 2      | The true-color scheme.         |

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method containerId

Retrieves the ID of the parent container for the control.

    public int containerId()

#### Return Value

The ID of the parent container.

### Method countryRegionCodes

    public str countryRegionCodes([str value])

#### Parameters

value  

#### Return Value

### Method dataRelationPath

    public str dataRelationPath([str value])

#### Parameters

value  

#### Return Value

### Method displayTarget

    public int displayTarget([int value])

#### Parameters

value  

#### Return Value

### Method dragDrop

Determines whether to enable or disable drag-and-drop operations for the control.

    public int dragDrop([int value])

#### Parameters

value  

#### Return Value

1 if drag-and-drop operations are enabled; otherwise, false.

### Method enabled

Determines whether to enable or disable the object.

    public boolean enabled([boolean value])

#### Parameters

value  

#### Return Value

true if the object is enabled; otherwise, false.

#### Remarks

The enabled property allows controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

### Method font

Gets or sets the name of the font for the control to use.

    public str font([str value])

#### Parameters

value  

#### Return Value

The name of the font to use, such as Tahoma or Verdana.

### Method fontSize

Gets or sets the size of the font for the control to use.

    public int fontSize([int value])

#### Parameters

value  

#### Return Value

The height of the font in points.

### Method height

Gets or sets the height of the control.

    public int height(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

The height of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted.Calculate the height according to the following table:

| Mode.            | Height calculation.                                                                       |
|------------------|-------------------------------------------------------------------------------------------|
| -1 Exact.        | The exact height in pixels of the controls is used.                                       |
| 0 Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height. | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

### Method heightMode

Gets or sets a calculation mode for the height of the control.

    public int heightMode([int value])

#### Parameters

value  

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table:

| Mode.          | Height Calculation.                                                                       |
|----------------|-------------------------------------------------------------------------------------------|
| Exact.         | The exact height in pixels of the controls is used.                                       |
| Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height. | The layout of the form determines the height of the control.                              |

The height of the control might change when the mode is set to auto or column height.

### Method heightValue

Gets or sets the height of the control.

    public int heightValue([int value])

#### Parameters

value  

#### Return Value

The height in pixels.

#### Remarks

The height of the control is not changed unless the exact height calculation mode is used.

### Method helpText

Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property sheet.The help text must not exceed 250 characters.

### Method hierarchyParent

    public str hierarchyParent([str value])

#### Parameters

value  

#### Return Value

### Method id

Retrieves the ID of the control.

    public int id()

#### Return Value

The ID of the control.

### Method isContainer

Retrieves a value that indicates whether the control is a container control.

    public boolean isContainer()

#### Return Value

A Boolean value that indicates whether the control is a container control.

### Method italic

    public boolean italic([boolean value])

#### Parameters

value  

#### Return Value

### Method left

    public int left(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method leftMode

    public int leftMode([int value])

#### Parameters

value  

#### Return Value

### Method leftValue

    public int leftValue([int value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics 365 for Operations application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   It must start with a letter.
-   It cannot exceed 250 characters.
-   It can include numbers and underscore (\_) characters.
-   It cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enumerations, or classes.

### Method neededPermission

    public int neededPermission([int value])

#### Parameters

value  

#### Return Value

### Method securityKey

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  

#### Return Value

### Method skip

    public boolean skip([boolean value])

#### Parameters

value  

#### Return Value

### Method top

    public int top(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method topMode

    public int topMode([int value])

#### Parameters

value  

#### Return Value

### Method topValue

    public int topValue([int value])

#### Parameters

value  

#### Return Value

### Method type

    public int type([int value])

#### Parameters

value  

#### Return Value

### Method underline

    public boolean underline([boolean value])

#### Parameters

value  

#### Return Value

### Method userData

    public int userData([int value])

#### Parameters

value  

#### Return Value

### Method userDataItem

    public int userDataItem([int value])

#### Parameters

value  

#### Return Value

### Method userDataItems

    public int userDataItems([int value])

#### Parameters

value  

#### Return Value

### Method verticalSpacing

    public int verticalSpacing([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method verticalSpacingMode

    public AutoMode verticalSpacingMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method verticalSpacingValue

    public int verticalSpacingValue([int value])

#### Parameters

value  

#### Return Value

### Method visible

    public boolean visible([boolean value])

#### Parameters

value  

#### Return Value

### Method width

Gets or sets the width of the control.

    public int width(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

The width of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted.Calculate the width according to the following table:

| Mode.           | Width calculation.                                                                       |
|-----------------|------------------------------------------------------------------------------------------|
| -1 Exact.       | The exact width in pixels of the controls is used.                                       |
| 0 Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width. | The layout of the form determines the width of the control.                              |

The width and width calculation mode can be set separately.

### Method widthMode

Gets or sets the calculation mode of the width of the control.

    public int widthMode([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table:

| Mode.         | Width Calculation.                                                                       |
|---------------|------------------------------------------------------------------------------------------|
| Exact.        | The exact width in pixels of the controls is used.                                       |
| Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width. | The layout of the form determines the width of the control.                              |

The width of the control might change when the mode is set to auto or column width.

### Method widthValue

Gets or sets the width of the control.

    public int widthValue([int value])

#### Parameters

value  

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  



