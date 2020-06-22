---
title: xResourceNode class
description: This topic describes the xResourceNode class.
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

# Class xResourceNode

[!include [banner](../../includes/banner.md)]

```xpp
class xResourceNode extends TreeNode
```

## Remarks

## Examples

## Methods

| Method                                                                   | Description |
|--------------------------------------------------------------------------|-------------|
| public BinData AOTGetData()                                              |             |
| public Image AOTGetImage()                                               |             |
| public str changedBy(\[str value\])                                      |             |
| public Date changedDate(\[Date value\])                                  |             |
| public str changedTime(\[str value\])                                    |             |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\]) |             |
| public str createdBy(\[str value\])                                      |             |
| public Date creationDate(\[Date value\])                                 |             |
| public str creationTime(\[str value\])                                   |             |
| public str filename(\[str value\])                                       |             |
| public str helpText(\[str value\])                                       |             |
| public str label(\[str value\])                                          |             |
| public str name(\[str value\])                                           |             |
| public Guid origin(\[Guid value\])                                       |             |
| ::public static Image AOTCreateImage(str imageName)                      |             |
| public void AOTSetData(BinData data)                                     |             |
| public void AOTSetImage(Image image)                                     |             |

## Method AOTGetData

```xpp
public BinData AOTGetData()
```

### Return Value - AOTGetData

## Method AOTGetImage

```xpp
public Image AOTGetImage()
```

### Return Value - AOTGetImage

## Method changedBy

```xpp
public str changedBy([str value])
```

### Parameters - changedBy

value  

### Return Value - changedBy

## Method changedDate

```xpp
public Date changedDate([Date value])
```

### Parameters - changedDate

value  

### Return Value - changedDate

## Method changedTime

```xpp
public str changedTime([str value])
```

### Parameters - changedTime

value  

### Return Value - changedTime

## Method configurationKey

```xpp
public ConfigurationKeyId configurationKey([ConfigurationKeyId value])
```

### Parameters - configurationKey

value  

### Return Value - configurationKey

## Method createdBy

```xpp
public str createdBy([str value])
```

### Parameters - createdBy

value  

### Return Value - createdBy

## Method creationDate

```xpp
public Date creationDate([Date value])
```

### Parameters - creationDate

value  

### Return Value - creationDate

## Method creationTime

```xpp
public str creationTime([str value])
```

### Parameters - creationTime

value  

### Return Value - creationTime

## Method filename

```xpp
public str filename([str value])
```

### Parameters - filename

value  

### Return Value - filename

## Method helpText

```xpp
public str helpText([str value])
```

### Parameters - helpText

value  

### Return Value - helpText

## Method label

```xpp
public str label([str value])
```

### Parameters - label

value  

### Return Value - label

## Method name

```xpp
public str name([str value])
```

### Parameters - name

value  

### Return Value - name

## Method origin

```xpp
public Guid origin([Guid value])
```

### Parameters - origin

value  

### Return Value - origin

## Method AOTCreateImage

```xpp
public static Image AOTCreateImage(str imageName)
```

### Parameters - AOTCreateImage

imageName  

### Return Value - AOTCreateImage

## Method AOTSetData

```xpp
public void AOTSetData(BinData data)
```

### Parameters - AOTSetData

data  

## Method AOTSetImage

```xpp
public void AOTSetImage(Image image)
```

### Parameters - AOTSetImage

image  

