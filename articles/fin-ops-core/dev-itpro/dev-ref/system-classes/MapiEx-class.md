---
title: MapiEx class
description: This topic describes the MapiEx class.
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

# Class MapiEx

[!include [banner](../../includes/banner.md)]

```xpp
class MapiEx extends Object
```

## Remarks

## Examples

## Methods

| Method                                                          | Description                                     |
|-----------------------------------------------------------------|-------------------------------------------------|
| public MapiExAppointment getAppointmentFromEntryId(str entryID) |                                                 |
| public MapiExContact getContactFromEntryId(str entryID)         |                                                 |
| public int getCurrentUser()                                     |                                                 |
| public str getCurrentUserEmail()                                |                                                 |
| public str getCurrentUserEntryId()                              |                                                 |
| public str getCurrentUserName()                                 |                                                 |
| public MapiExMail getMailFromEntryId(str entryID)               |                                                 |
| public MapiExTask getTaskFromEntryId(str entryID)               |                                                 |
| public int logon(str profileName, str password, int flags)      |                                                 |
| public boolean mapiInitialised()                                |                                                 |
| public boolean openMessageStore(str str)                        |                                                 |
| public void finalize()                                          |                                                 |
| public void new()                                               | Initializes a new instance of the MapiEx class. |
| public void logout()                                            |                                                 |

## Method getAppointmentFromEntryId

```xpp
public MapiExAppointment getAppointmentFromEntryId(str entryID)
```

### Parameters - getAppointmentFromEntryId

entryID  

### Return Value - getAppointmentFromEntryId

## Method getContactFromEntryId

```xpp
public MapiExContact getContactFromEntryId(str entryID)
```

### Parameters - getContactFromEntryId

entryID  

### Return Value - getContactFromEntryId

## Method getCurrentUser

```xpp
public int getCurrentUser()
```

### Return Value - getCurrentUser

## Method getCurrentUserEmail

```xpp
public str getCurrentUserEmail()
```

### Return Value - getCurrentUserEmail

## Method getCurrentUserEntryId

```xpp
public str getCurrentUserEntryId()
```

### Return Value - getCurrentUserEntryId

## Method getCurrentUserName

```xpp
public str getCurrentUserName()
```

### Return Value - getCurrentUserName

## Method getMailFromEntryId

```xpp
public MapiExMail getMailFromEntryId(str entryID)
```

### Parameters - getMailFromEntryId

entryID  

### Return Value - getMailFromEntryId

## Method getTaskFromEntryId

```xpp
public MapiExTask getTaskFromEntryId(str entryID)
```

### Parameters - getTaskFromEntryId

entryID  

### Return Value - getTaskFromEntryId

## Method logon

```xpp
public int logon(str profileName, str password, int flags)
```

### Parameters - logon

profileName  

<!-- -->

password  

<!-- -->

flags  

### Return Value - logon

## Method mapiInitialised

```xpp
public boolean mapiInitialised()
```

### Return Value - mapiInitialised

## Method openMessageStore

```xpp
public boolean openMessageStore(str str)
```

### Parameters - openMessageStore

str  

### Return Value - openMessageStore

## Method finalize

```xpp
public void finalize()
```

## Method new

Initializes a new instance of the MapiEx class.

```xpp
public void new()
```

## Method logout

```xpp
public void logout()
```

