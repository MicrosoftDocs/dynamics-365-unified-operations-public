---
title: FormAutoLookupFactory class
description: This topic describes the FormAutoLookupFactory class.
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

# Class FormAutoLookupFactory

[!include [banner](../../includes/banner.md)]

```xpp
class FormAutoLookupFactory extends FieldBinding
```

## Remarks

## Examples

## Methods

| Method                                                                                                                                                                              | Description                                                    |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|
| ::public static xFormRun buildLookupFormByField(FormControl controlHostingLookup, FieldBinding fieldBinding)                                                                        |                                                                |
| ::public static xFormRun buildLookupFromCustomForm(FormControl controlHostingLookup, Form customLookupForm, FieldBinding fieldBinding, \[xArgs customArgs\], \[Query customQuery\]) |                                                                |
| ::public static xFormRun buildReferenceLookupFromCustomForm(FormReferenceControl referenceControlHostingLookup, Form customLookupForm, \[xArgs customArgs\], \[Query customQuery\]) |                                                                |
| ::public static void createLookupForClientsideControl(xFormRun parentForm, str targetId, str controlName, int tableId, int fieldId, str controlValue, boolean isInFilterMode)       |                                                                |
| ::public static void performFormLookup(xFormRun lookupForm, \[boolean blockUntilLookupClosed\], \[FormControl controlHostingLookup\])                                               |                                                                |
| private void new()                                                                                                                                                                  | Initializes a new instance of the FormAutoLookupFactory class. |

## Method buildLookupFormByField

```xpp
public static xFormRun buildLookupFormByField(FormControl controlHostingLookup, FieldBinding fieldBinding)
```

### Parameters - buildLookupFormByField

controlHostingLookup  

<!-- -->

fieldBinding  

### Return Value - buildLookupFormByField

## Method buildLookupFromCustomForm

```xpp
public static xFormRun buildLookupFromCustomForm(FormControl controlHostingLookup, Form customLookupForm, FieldBinding fieldBinding, [xArgs customArgs], [Query customQuery])
```

### Parameters - buildLookupFromCustomForm

controlHostingLookup  

<!-- -->

customLookupForm  

<!-- -->

fieldBinding  

<!-- -->

customArgs  

<!-- -->

customQuery  

### Return Value - buildLookupFromCustomForm

## Method buildReferenceLookupFromCustomForm

```xpp
public static xFormRun buildReferenceLookupFromCustomForm(FormReferenceControl referenceControlHostingLookup, Form customLookupForm, [xArgs customArgs], [Query customQuery])
```

### Parameters - buildReferenceLookupFromCustomForm

referenceControlHostingLookup  

<!-- -->

customLookupForm  

<!-- -->

customArgs  

<!-- -->

customQuery  

### Return Value - buildReferenceLookupFromCustomForm

## Method createLookupForClientsideControl

```xpp
public static void createLookupForClientsideControl(xFormRun parentForm, str targetId, str controlName, int tableId, int fieldId, str controlValue, boolean isInFilterMode)
```

### Parameters - createLookupForClientsideControl

parentForm  

<!-- -->

targetId  

<!-- -->

controlName  

<!-- -->

tableId  

<!-- -->

fieldId  

<!-- -->

controlValue  

<!-- -->

isInFilterMode  

## Method performFormLookup

```xpp
public static void performFormLookup(xFormRun lookupForm, [boolean blockUntilLookupClosed], [FormControl controlHostingLookup])
```

### Parameters - performFormLookup

lookupForm  

<!-- -->

blockUntilLookupClosed  

<!-- -->

controlHostingLookup  

## Method new

Initializes a new instance of the FormAutoLookupFactory class.

```xpp
private void new()
```

