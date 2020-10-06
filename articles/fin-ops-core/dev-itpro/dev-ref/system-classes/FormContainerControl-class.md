---
title: FormContainerControl class
description: This topic describes the FormContainerControl class.
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

# Class FormContainerControl

[!include [banner](../../includes/banner.md)]

```xpp
class FormContainerControl extends FormControl
```

## Remarks

## Examples

## Methods

| Method                                                                                                              | Description |
|---------------------------------------------------------------------------------------------------------------------|-------------|
| public FormControl addControl(FormControlType controlType, str controlName, \[FormControl insertAfter\])            |             |
| public FormControl addControlEx(str controlClass, str controlName, \[FormControl insertAfter\])                     |             |
| public FormControl addDataField(int dataSourceId, FieldId fieldId, \[FormControl insertAfter\], \[int arrayIndex\]) |             |
| public boolean alignChild(\[boolean value\])                                                                        |             |
| public boolean alignChildren(\[boolean value\])                                                                     |             |
| public boolean alignControl(\[boolean value\])                                                                      |             |
| public boolean allowEdit(\[boolean value\])                                                                         |             |
| public boolean allowSysSetup()                                                                                      |             |
| public int allowUserSetup(\[int value\])                                                                            |             |
| public int arrangeGuide(\[int value\])                                                                              |             |
| public int arrangeMethod(\[int value\])                                                                             |             |
| public int arrangeWhen(\[int value\])                                                                               |             |
| public boolean autoDataGroup(\[boolean value\])                                                                     |             |
| public boolean autoDeclaration(\[boolean value\])                                                                   |             |
| public int beginDrag(int x, int y)                                                                                  |             |
| public int bottomMargin(\[int value\], \[AutoMode mode\])                                                           |             |
| public AutoMode bottomMarginMode(\[AutoMode mode\])                                                                 |             |
| public int bottomMarginValue(\[int value\])                                                                         |             |
| public container calcControlSize(int chars, int lines)                                                              |             |
| public boolean canAddDataField(int dataSourceId, FieldId fieldId, \[int arrayIndex\])                               |             |
| public boolean canContain(FormControl control)                                                                      |             |
| public int columns(\[int value\], \[ColumnsMode mode\])                                                             |             |
| public ColumnsMode columnsMode(\[ColumnsMode mode\])                                                                |             |
| public int columnspace(\[int value\], \[AutoMode mode\])                                                            |             |
| public AutoMode columnspaceMode(\[AutoMode mode\])                                                                  |             |
| public int columnspaceValue(\[int value\])                                                                          |             |
| public int columnsValue(\[int value\])                                                                              |             |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                            |             |
| public List configurationKeyEx()                                                                                    |             |
| public boolean contains(FormControl control)                                                                        |             |
| public int controlCount()                                                                                           |             |
| public FormControl controlNum(int controlNo)                                                                        |             |
| public str countryRegionCodes(\[str value\])                                                                        |             |
| public str dataRelationPath(\[str value\])                                                                          |             |
| public int displayTarget(\[int value\])                                                                             |             |
| public int dragDrop(\[int value\])                                                                                  |             |
| public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)                                   |             |
| public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)                                       |             |
| public str dragText()                                                                                               |             |
| public boolean enabled(\[boolean value\])                                                                           |             |
| public boolean hasChanged(\[boolean val\])                                                                          |             |
| public boolean hasUserSetting()                                                                                     |             |
| public int height(int value, \[int mode\])                                                                          |             |
| public int heightMode(\[int value\])                                                                                |             |
| public int heightValue(\[int value\])                                                                               |             |
| public str helpField()                                                                                              |             |
| public str helpText(\[str value\])                                                                                  |             |
| public boolean hideIfEmpty(\[boolean value\])                                                                       |             |
| public str hierarchyParent(\[str value\])                                                                           |             |
| public int hWnd()                                                                                                   |             |
| public boolean isContainer()                                                                                        |             |
| public boolean isDisplayed()                                                                                        |             |
| public boolean isRestricted()                                                                                       |             |
| public boolean isUserSetupEnabled(int neededSetupRights)                                                            |             |
| public boolean isVisible()                                                                                          |             |
| public boolean isVisibleOnClient()                                                                                  |             |
| public int left(int value, \[int mode\])                                                                            |             |
| public int leftMargin(\[int value\], \[AutoMode mode\])                                                             |             |
| public AutoMode leftMarginMode(\[AutoMode mode\])                                                                   |             |
| public int leftMarginValue(\[int value\])                                                                           |             |
| public int leftMode(\[int value\])                                                                                  |             |
| public int leftValue(\[int value\])                                                                                 |             |
| public boolean markAsUserAdd(\[boolean value\])                                                                     |             |
| public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)                                     |             |
| public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)                                         |             |
| public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)                                         |             |
| public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)                                           |             |
| public int moveControl(int controlId, \[int insertAfterId\])                                                        |             |
| public str name(\[str value\])                                                                                      |             |
| public int neededPermission(\[int value\])                                                                          |             |
| public container SysObsoleteAttribute()                                                                             |             |
| public FormControl parentControl()                                                                                  |             |
| public int rightMargin(\[int value\], \[AutoMode mode\])                                                            |             |
| public AutoMode rightMarginMode(\[AutoMode mode\])                                                                  |             |
| public int rightMarginValue(\[int value\])                                                                          |             |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                           |             |
| public int showContextMenu(int menuHandle)                                                                          |             |
| public boolean skip(\[boolean value\])                                                                              |             |
| public str toolTip()                                                                                                |             |
| public int top(int value, \[int mode\])                                                                             |             |
| public int topMargin(\[int value\], \[AutoMode mode\])                                                              |             |
| public AutoMode topMarginMode(\[AutoMode mode\])                                                                    |             |
| public int topMarginValue(\[int value\])                                                                            |             |
| public int topMode(\[int value\])                                                                                   |             |
| public int topValue(\[int value\])                                                                                  |             |
| public int type(\[int value\])                                                                                      |             |
| public boolean SysObsoleteAttribute(container data)                                                                 |             |
| public int userData(\[int value\])                                                                                  |             |
| public int userDataItem(\[int value\])                                                                              |             |
| public int userDataItems(\[int value\])                                                                             |             |
| public int userDisable(\[int value\])                                                                               |             |
| public int userHeight(\[int value\])                                                                                |             |
| public int userHide(\[int value\])                                                                                  |             |
| public int userOrgContainer(\[int value\])                                                                          |             |
| public int userOrgSibling(\[int value\])                                                                            |             |
| public str userPromptText(\[str value\])                                                                            |             |
| public int userSecurityLevel(\[int value\])                                                                         |             |
| public int userSkip(\[int value\])                                                                                  |             |
| public int userWidth(\[int value\])                                                                                 |             |
| public boolean useUserLayout(\[boolean value\])                                                                     |             |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                        |             |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                              |             |
| public int verticalSpacingValue(\[int value\])                                                                      |             |
| public boolean visible(\[boolean value\])                                                                           |             |
| public int width(int value, \[int mode\])                                                                           |             |
| public int widthMode(\[int value\])                                                                                 |             |
| public int widthValue(\[int value\])                                                                                |             |
| public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)                                               |             |
| public void inputSearch(str searchStr)                                                                              |             |
| public void prefColumnSize(int width, int height)                                                                   |             |
| public void gotFocus()                                                                                              |             |
| public void lostFocus()                                                                                             |             |
| public void mouseLeave()                                                                                            |             |
| public void setFocus()                                                                                              |             |
| public void copy()                                                                                                  |             |
| private void OnGotFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                         |             |
| public void displayControl()                                                                                        |             |
| public void paste()                                                                                                 |             |
| public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)                                           |             |
| private void OnLostFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                        |             |
| public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)                                       |             |
| public void resetUserSetting()                                                                                      |             |
| public void endDrag()                                                                                               |             |
| public void arrange()                                                                                               |             |
| public void dragLeave()                                                                                             |             |
| public void cut()                                                                                                   |             |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\])         |             |
| public void context()                                                                                               |             |

## Method addControl

```xpp
public FormControl addControl(FormControlType controlType, str controlName, [FormControl insertAfter])
```

### Parameters - addControl

controlType  

<!-- -->

controlName  

<!-- -->

insertAfter  

### Return Value - addControl

## Method addControlEx

```xpp
public FormControl addControlEx(str controlClass, str controlName, [FormControl insertAfter])
```

### Parameters - addControlEx

controlClass  

<!-- -->

controlName  

<!-- -->

insertAfter  

### Return Value - addControlEx

## Method addDataField

```xpp
public FormControl addDataField(int dataSourceId, FieldId fieldId, [FormControl insertAfter], [int arrayIndex])
```

### Parameters - addDataField

dataSourceId  

<!-- -->

fieldId  

<!-- -->

insertAfter  

<!-- -->

arrayIndex  

### Return Value - addDataField

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

## Method alignControl

```xpp
public boolean alignControl([boolean value])
```

### Parameters - alignControl

value  

### Return Value - alignControl

## Method allowEdit

```xpp
public boolean allowEdit([boolean value])
```

### Parameters - allowEdit

value  

### Return Value - allowEdit

## Method allowSysSetup

```xpp
public boolean allowSysSetup()
```

### Return Value - allowSysSetup

## Method allowUserSetup

```xpp
public int allowUserSetup([int value])
```

### Parameters - allowUserSetup

value  

### Return Value - allowUserSetup

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

## Method autoDataGroup

```xpp
public boolean autoDataGroup([boolean value])
```

### Parameters - autoDataGroup

value  

### Return Value - autoDataGroup

## Method autoDeclaration

```xpp
public boolean autoDeclaration([boolean value])
```

### Parameters - autoDeclaration

value  

### Return Value - autoDeclaration

## Method beginDrag

```xpp
public int beginDrag(int x, int y)
```

### Parameters - beginDrag

x  

<!-- -->

y  

### Return Value - beginDrag

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

## Method calcControlSize

```xpp
public container calcControlSize(int chars, int lines)
```

### Parameters - calcControlSize

chars  

<!-- -->

lines  

### Return Value - calcControlSize

## Method canAddDataField

```xpp
public boolean canAddDataField(int dataSourceId, FieldId fieldId, [int arrayIndex])
```

### Parameters - canAddDataField

dataSourceId  

<!-- -->

fieldId  

<!-- -->

arrayIndex  

### Return Value - canAddDataField

## Method canContain

```xpp
public boolean canContain(FormControl control)
```

### Parameters - canContain

control  

### Return Value - canContain

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

## Method configurationKey

```xpp
public ConfigurationKeyId configurationKey([ConfigurationKeyId value])
```

### Parameters - configurationKey

value  

### Return Value - configurationKey

## Method configurationKeyEx

```xpp
public List configurationKeyEx()
```

### Return Value - configurationKeyEx

## Method contains

```xpp
public boolean contains(FormControl control)
```

### Parameters - contains

control  

### Return Value - contains

## Method controlCount

```xpp
public int controlCount()
```

### Return Value - controlCount

## Method controlNum

```xpp
public FormControl controlNum(int controlNo)
```

### Parameters - controlNum

controlNo  

### Return Value - controlNum

## Method countryRegionCodes

```xpp
public str countryRegionCodes([str value])
```

### Parameters - countryRegionCodes

value  

### Return Value - countryRegionCodes

## Method dataRelationPath

```xpp
public str dataRelationPath([str value])
```

### Parameters - dataRelationPath

value  

### Return Value - dataRelationPath

## Method displayTarget

```xpp
public int displayTarget([int value])
```

### Parameters - displayTarget

value  

### Return Value - displayTarget

## Method dragDrop

```xpp
public int dragDrop([int value])
```

### Parameters - dragDrop

value  

### Return Value - dragDrop

## Method dragOver

```xpp
public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)
```

### Parameters - dragOver

dragSource  

<!-- -->

dragMode  

<!-- -->

x  

<!-- -->

y  

### Return Value - dragOver

## Method dragOverEx

```xpp
public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)
```

### Parameters - dragOverEx

dragSource  

<!-- -->

dragMode  

<!-- -->

x  

<!-- -->

y  

### Return Value - dragOverEx

## Method dragText

```xpp
public str dragText()
```

### Return Value - dragText

## Method enabled

```xpp
public boolean enabled([boolean value])
```

### Parameters - enabled

value  

### Return Value - enabled

## Method hasChanged

```xpp
public boolean hasChanged([boolean val])
```

### Parameters - hasChanged

val  

### Return Value - hasChanged

## Method hasUserSetting

```xpp
public boolean hasUserSetting()
```

### Return Value - hasUserSetting

## Method height

```xpp
public int height(int value, [int mode])
```

### Parameters - height

value  

<!-- -->

mode  

### Return Value - height

## Method heightMode

```xpp
public int heightMode([int value])
```

### Parameters - heightMode

value  

### Return Value - heightMode

## Method heightValue

```xpp
public int heightValue([int value])
```

### Parameters - heightValue

value  

### Return Value - heightValue

## Method helpField

```xpp
public str helpField()
```

### Return Value - helpField

## Method helpText

```xpp
public str helpText([str value])
```

### Parameters - helpText

value  

### Return Value - helpText

## Method hideIfEmpty

```xpp
public boolean hideIfEmpty([boolean value])
```

### Parameters - hideIfEmpty

value  

### Return Value - hideIfEmpty

## Method hierarchyParent

```xpp
public str hierarchyParent([str value])
```

### Parameters - hierarchyParent

value  

### Return Value - hierarchyParent

## Method hWnd

```xpp
public int hWnd()
```

### Return Value - hWnd

## Method isContainer

```xpp
public boolean isContainer()
```

### Return Value - isContainer

## Method isDisplayed

```xpp
public boolean isDisplayed()
```

### Return Value - isDisplayed

## Method isRestricted

```xpp
public boolean isRestricted()
```

### Return Value - isRestricted

## Method isUserSetupEnabled

```xpp
public boolean isUserSetupEnabled(int neededSetupRights)
```

### Parameters - isUserSetupEnabled

neededSetupRights  

### Return Value - isUserSetupEnabled

## Method isVisible

```xpp
public boolean isVisible()
```

### Return Value - isVisible

## Method isVisibleOnClient

```xpp
public boolean isVisibleOnClient()
```

### Return Value - isVisibleOnClient

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

## Method markAsUserAdd

```xpp
public boolean markAsUserAdd([boolean value])
```

### Parameters - markAsUserAdd

value  

### Return Value - markAsUserAdd

## Method mouseDblClick

```xpp
public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)
```

### Parameters - mouseDblClick

x  

<!-- -->

y  

<!-- -->

button  

<!-- -->

Ctrl  

<!-- -->

Shift  

### Return Value - mouseDblClick

## Method mouseDown

```xpp
public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)
```

### Parameters - mouseDown

x  

<!-- -->

y  

<!-- -->

button  

<!-- -->

Ctrl  

<!-- -->

Shift  

### Return Value - mouseDown

## Method mouseMove

```xpp
public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)
```

### Parameters - mouseMove

x  

<!-- -->

y  

<!-- -->

button  

<!-- -->

Ctrl  

<!-- -->

Shift  

### Return Value - mouseMove

## Method mouseUp

```xpp
public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)
```

### Parameters - mouseUp

x  

<!-- -->

y  

<!-- -->

button  

<!-- -->

Ctrl  

<!-- -->

Shift  

### Return Value - mouseUp

## Method moveControl

```xpp
public int moveControl(int controlId, [int insertAfterId])
```

### Parameters - moveControl

controlId  

<!-- -->

insertAfterId  

### Return Value - moveControl

## Method name

```xpp
public str name([str value])
```

### Parameters - name

value  

### Return Value - name

## Method neededPermission

```xpp
public int neededPermission([int value])
```

### Parameters - neededPermission

value  

### Return Value - neededPermission

## Method SysObsoleteAttribute

```xpp
public container SysObsoleteAttribute()
```

### Return Value - SysObsoleteAttribute

## Method parentControl

```xpp
public FormControl parentControl()
```

### Return Value - parentControl

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

## Method securityKey

```xpp
public SecurityKeyId securityKey([SecurityKeyId value])
```

### Parameters - securityKey

value  

### Return Value - securityKey

## Method showContextMenu

```xpp
public int showContextMenu(int menuHandle)
```

### Parameters - showContextMenu

menuHandle  

### Return Value - showContextMenu

## Method skip

```xpp
public boolean skip([boolean value])
```

### Parameters - skip

value  

### Return Value - skip

## Method toolTip

```xpp
public str toolTip()
```

### Return Value - toolTip

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

## Method type

```xpp
public int type([int value])
```

### Parameters - type

value  

### Return Value - type

## Method SysObsoleteAttribute

```xpp
public boolean SysObsoleteAttribute(container data)
```

### Parameters - SysObsoleteAttribute

data  

### Return Value - SysObsoleteAttribute

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

## Method userDisable

```xpp
public int userDisable([int value])
```

### Parameters - userDisable

value  

### Return Value - userDisable

## Method userHeight

```xpp
public int userHeight([int value])
```

### Parameters - userHeight

value  

### Return Value - userHeight

## Method userHide

```xpp
public int userHide([int value])
```

### Parameters - userHide

value  

### Return Value - userHide

## Method userOrgContainer

```xpp
public int userOrgContainer([int value])
```

### Parameters - userOrgContainer

value  

### Return Value - userOrgContainer

## Method userOrgSibling

```xpp
public int userOrgSibling([int value])
```

### Parameters - userOrgSibling

value  

### Return Value - userOrgSibling

## Method userPromptText

```xpp
public str userPromptText([str value])
```

### Parameters - userPromptText

value  

### Return Value - userPromptText

## Method userSecurityLevel

```xpp
public int userSecurityLevel([int value])
```

### Parameters - userSecurityLevel

value  

### Return Value - userSecurityLevel

## Method userSkip

```xpp
public int userSkip([int value])
```

### Parameters - userSkip

value  

### Return Value - userSkip

## Method userWidth

```xpp
public int userWidth([int value])
```

### Parameters - userWidth

value  

### Return Value - userWidth

## Method useUserLayout

```xpp
public boolean useUserLayout([boolean value])
```

### Parameters - useUserLayout

value  

### Return Value - useUserLayout

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

## Method visible

```xpp
public boolean visible([boolean value])
```

### Parameters - visible

value  

### Return Value - visible

## Method width

```xpp
public int width(int value, [int mode])
```

### Parameters - width

value  

<!-- -->

mode  

### Return Value - width

## Method widthMode

```xpp
public int widthMode([int value])
```

### Parameters - widthMode

value  

### Return Value - widthMode

## Method widthValue

```xpp
public int widthValue([int value])
```

### Parameters - widthValue

value  

### Return Value - widthValue

## Method dropEx

```xpp
public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)
```

### Parameters - dropEx

dragSource  

<!-- -->

dragMode  

<!-- -->

x  

<!-- -->

y  

## Method inputSearch

```xpp
public void inputSearch(str searchStr)
```

### Parameters - inputSearch

searchStr  

## Method prefColumnSize

```xpp
public void prefColumnSize(int width, int height)
```

### Parameters - prefColumnSize

width  

<!-- -->

height  

## Method gotFocus

```xpp
public void gotFocus()
```

## Method lostFocus

```xpp
public void lostFocus()
```

## Method mouseLeave

```xpp
public void mouseLeave()
```

## Method setFocus

```xpp
public void setFocus()
```

## Method copy

```xpp
public void copy()
```

## Method OnGotFocus

```xpp
private void OnGotFocus([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnGotFocus

sender  

<!-- -->

e  

## Method displayControl

```xpp
public void displayControl()
```

## Method paste

```xpp
public void paste()
```

## Method drop

```xpp
public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)
```

### Parameters - drop

dragSource  

<!-- -->

dragMode  

<!-- -->

x  

<!-- -->

y  

## Method OnLostFocus

```xpp
private void OnLostFocus([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnLostFocus

sender  

<!-- -->

e  

## Method mouseEnter

```xpp
public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)
```

### Parameters - mouseEnter

x  

<!-- -->

y  

<!-- -->

button  

<!-- -->

Ctrl  

<!-- -->

Shift  

## Method resetUserSetting

```xpp
public void resetUserSetting()
```

## Method endDrag

```xpp
public void endDrag()
```

## Method arrange

```xpp
public void arrange()
```

## Method dragLeave

```xpp
public void dragLeave()
```

## Method cut

```xpp
public void cut()
```

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

## Method context

```xpp
public void context()
```

