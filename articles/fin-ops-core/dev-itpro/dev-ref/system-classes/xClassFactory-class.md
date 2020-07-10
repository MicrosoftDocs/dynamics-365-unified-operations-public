---
title: xClassFactory class
description: This topic describes the xClassFactory class.
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

# Class xClassFactory

[!include [banner](../../includes/banner.md)]

```xpp
class xClassFactory extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                                                                                               | Description                                            |
|------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------|
| public xFormRun createAutoReportForm(xArgs args)                                                                                                     |                                                        |
| public xFormRun createLabelForm(xArgs args)                                                                                                          |                                                        |
| public xFormRun createRecInfoForm(xArgs args)                                                                                                        |                                                        |
| public ReportViewer createReportViewer(PrintJobHeader jobsCursor, PrintJobPages pagesCursor, \[ReportRun reportRun\])                                |                                                        |
| public xFormRun createSetupForm(xArgs args)                                                                                                          |                                                        |
| public ReportOutputUser createViewer(PrintJobHeader jobsCursor, PrintJobPages pagesCursor, ReportOutputUserType viewerType, \[ReportRun reportRun\]) |                                                        |
| public Object createWebPageEditor()                                                                                                                  |                                                        |
| public xFormRun formRunClass(xArgs args)                                                                                                             |                                                        |
| public container lastValueGet(SelectableDataArea company, UserId user, UtilElementType utilType, UtilElementName name, \[str design\])               |                                                        |
| public QueryRun queryRunClass(xArgs args)                                                                                                            |                                                        |
| public ReportRun reportRunClass(xArgs args)                                                                                                          |                                                        |
| public Object startAOTWizard(TreeNode parent)                                                                                                        |                                                        |
| public void projectDeleted(str projectName)                                                                                                          |                                                        |
| public void lastValueDelete(SelectableDataArea company, UserId user, UtilElementType utilType, UtilElementName name, \[str design\])                 |                                                        |
| public void lastValuePut(container value, SelectableDataArea company, UserId user, UtilElementType utilType, UtilElementName name, \[str design\])   |                                                        |
| public void drillDown(OutputField outputField, MenuItemType menuItemType, str menuItemName)                                                          |                                                        |
| public void new()                                                                                                                                    | Initializes a new instance of the xClassFactory class. |

## Method createAutoReportForm

```xpp
public xFormRun createAutoReportForm(xArgs args)
```

### Parameters - createAutoReportForm

args  

### Return Value - createAutoReportForm

## Method createLabelForm

```xpp
public xFormRun createLabelForm(xArgs args)
```

### Parameters - createLabelForm

args  

### Return Value - createLabelForm

## Method createRecInfoForm

```xpp
public xFormRun createRecInfoForm(xArgs args)
```

### Parameters - createRecInfoForm

args  

### Return Value - createRecInfoForm

## Method createReportViewer

```xpp
public ReportViewer createReportViewer(PrintJobHeader jobsCursor, PrintJobPages pagesCursor, [ReportRun reportRun])
```

### Parameters - createReportViewer

jobsCursor  

<!-- -->

pagesCursor  

<!-- -->

reportRun  

### Return Value - createReportViewer

## Method createSetupForm

```xpp
public xFormRun createSetupForm(xArgs args)
```

### Parameters - createSetupForm

args  

### Return Value - createSetupForm

## Method createViewer

```xpp
public ReportOutputUser createViewer(PrintJobHeader jobsCursor, PrintJobPages pagesCursor, ReportOutputUserType viewerType, [ReportRun reportRun])
```

### Parameters - createViewer

jobsCursor  

<!-- -->

pagesCursor  

<!-- -->

viewerType  

<!-- -->

reportRun  

### Return Value - createViewer

## Method createWebPageEditor

```xpp
public Object createWebPageEditor()
```

### Return Value - createWebPageEditor

## Method formRunClass

```xpp
public xFormRun formRunClass(xArgs args)
```

### Parameters - formRunClass

args  

### Return Value - formRunClass

## Method lastValueGet

```xpp
public container lastValueGet(SelectableDataArea company, UserId user, UtilElementType utilType, UtilElementName name, [str design])
```

### Parameters - lastValueGet

company  

<!-- -->

user  

<!-- -->

utilType  

<!-- -->

name  

<!-- -->

design  

### Return Value - lastValueGet

## Method queryRunClass

```xpp
public QueryRun queryRunClass(xArgs args)
```

### Parameters - queryRunClass

args  

### Return Value - queryRunClass

## Method reportRunClass

```xpp
public ReportRun reportRunClass(xArgs args)
```

### Parameters - reportRunClass

args  

### Return Value - reportRunClass

## Method startAOTWizard

```xpp
public Object startAOTWizard(TreeNode parent)
```

### Parameters - startAOTWizard

parent  

### Return Value - startAOTWizard

## Method projectDeleted

```xpp
public void projectDeleted(str projectName)
```

### Parameters - projectDeleted

projectName  

## Method lastValueDelete

```xpp
public void lastValueDelete(SelectableDataArea company, UserId user, UtilElementType utilType, UtilElementName name, [str design])
```

### Parameters - lastValueDelete

company  

<!-- -->

user  

<!-- -->

utilType  

<!-- -->

name  

<!-- -->

design  

## Method lastValuePut

```xpp
public void lastValuePut(container value, SelectableDataArea company, UserId user, UtilElementType utilType, UtilElementName name, [str design])
```

### Parameters - lastValuePut

value  

<!-- -->

company  

<!-- -->

user  

<!-- -->

utilType  

<!-- -->

name  

<!-- -->

design  

## Method drillDown

```xpp
public void drillDown(OutputField outputField, MenuItemType menuItemType, str menuItemName)
```

### Parameters - drillDown

outputField  

<!-- -->

menuItemType  

<!-- -->

menuItemName  

## Method new

Initializes a new instance of the xClassFactory class.

```xpp
public void new()
```

