---
title: FormObjectSetNotifyEvents class
description: This topic describes the FormObjectSetNotifyEvents class.
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

# Class FormObjectSetNotifyEvents

[!include [banner](../../includes/banner.md)]

```xpp
class FormObjectSetNotifyEvents extends FormObjectSetNotify
```

## Remarks

## Examples

## Methods

| Method                                                                                                                                                                               | Description                                                        |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------|
| public boolean onLeave(FormObjectSet sender)                                                                                                                                         |                                                                    |
| public int onRequestCacheSize(FormObjectSet sender)                                                                                                                                  |                                                                    |
| public void new()                                                                                                                                                                    | Initializes a new instance of the FormObjectSetNotifyEvents class. |
| public void onRuntimeMetadataChanged(FormObjectSet sender, str changedDatasourceName, str referencedDatasourceName, FieldId changedFieldId, DataSourceMetadataChangeType changeType) |                                                                    |
| public void onRefresh(FormObjectSet sender)                                                                                                                                          |                                                                    |
| public void finalize()                                                                                                                                                               |                                                                    |
| public void addEventDelegate(FormObjectSetEventType eventType, ManagedEventDelegate eventDelegate)                                                                                   |                                                                    |
| public void onCurrentChanged(FormObjectSet sender, int position)                                                                                                                     |                                                                    |
| public void removeEventDelegate(FormObjectSetEventType eventType, ManagedEventDelegate eventDelegate)                                                                                |                                                                    |
| public void onMarkingChanged(FormObjectSet sender, Array ids)                                                                                                                        |                                                                    |
| public void onPagingParametersChanged(FormObjectSet sender, boolean pagingEnabled, int startRowIndex, int pageSize)                                                                  |                                                                    |
| public void onCacheChanged(FormObjectSet sender, NotifyCacheChangeType cacheChangeType)                                                                                              |                                                                    |
| public void onActive(FormObjectSet sender)                                                                                                                                           |                                                                    |

## Method onLeave

```xpp
public boolean onLeave(FormObjectSet sender)
```

### Parameters - onLeave

sender  

### Return Value - onLeave

## Method onRequestCacheSize

```xpp
public int onRequestCacheSize(FormObjectSet sender)
```

### Parameters - onRequestCacheSize

sender  

### Return Value - onRequestCacheSize

## Method new

Initializes a new instance of the FormObjectSetNotifyEvents class.

```xpp
public void new()
```

## Method onRuntimeMetadataChanged

```xpp
public void onRuntimeMetadataChanged(FormObjectSet sender, str changedDatasourceName, str referencedDatasourceName, FieldId changedFieldId, DataSourceMetadataChangeType changeType)
```

### Parameters - onRuntimeMetadataChanged

sender  

<!-- -->

changedDatasourceName  

<!-- -->

referencedDatasourceName  

<!-- -->

changedFieldId  

<!-- -->

changeType  

## Method onRefresh

```xpp
public void onRefresh(FormObjectSet sender)
```

### Parameters - onRefresh

sender  

## Method finalize

```xpp
public void finalize()
```

## Method addEventDelegate

```xpp
public void addEventDelegate(FormObjectSetEventType eventType, ManagedEventDelegate eventDelegate)
```

### Parameters - addEventDelegate

eventType  

<!-- -->

eventDelegate  

## Method onCurrentChanged

```xpp
public void onCurrentChanged(FormObjectSet sender, int position)
```

### Parameters - onCurrentChanged

sender  

<!-- -->

position  

## Method removeEventDelegate

```xpp
public void removeEventDelegate(FormObjectSetEventType eventType, ManagedEventDelegate eventDelegate)
```

### Parameters - removeEventDelegate

eventType  

<!-- -->

eventDelegate  

## Method onMarkingChanged

```xpp
public void onMarkingChanged(FormObjectSet sender, Array ids)
```

### Parameters - onMarkingChanged

sender  

<!-- -->

ids  

## Method onPagingParametersChanged

```xpp
public void onPagingParametersChanged(FormObjectSet sender, boolean pagingEnabled, int startRowIndex, int pageSize)
```

### Parameters - onPagingParametersChanged

sender  

<!-- -->

pagingEnabled  

<!-- -->

startRowIndex  

<!-- -->

pageSize  

## Method onCacheChanged

```xpp
public void onCacheChanged(FormObjectSet sender, NotifyCacheChangeType cacheChangeType)
```

### Parameters - onCacheChanged

sender  

<!-- -->

cacheChangeType  

## Method onActive

```xpp
public void onActive(FormObjectSet sender)
```

### Parameters - onActive

sender  

