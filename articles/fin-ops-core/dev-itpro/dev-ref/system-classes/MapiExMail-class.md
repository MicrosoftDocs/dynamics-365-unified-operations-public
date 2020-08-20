---
title: MapiExMail class
description: This topic describes the MapiExMail class.
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

# Class MapiExMail

[!include [banner](../../includes/banner.md)]

```xpp
class MapiExMail extends MapiExMessage
```

## Remarks

## Examples

## Methods

| Method                                                 | Description                                         |
|--------------------------------------------------------|-----------------------------------------------------|
| public str addRecipient(str email, str name, int type) |                                                     |
| public str entryId()                                   |                                                     |
| public boolean getRecipient(int index)                 |                                                     |
| public int getRecipientCount()                         |                                                     |
| public str getRecipientDisplayName()                   |                                                     |
| public str getRecipientEmailAddress()                  |                                                     |
| public str getRecipientEntryId()                       |                                                     |
| public boolean getRecipients()                         |                                                     |
| public str getRecipientSMTPAddress()                   |                                                     |
| public int getRecipientType()                          |                                                     |
| public str getSenderEmail()                            |                                                     |
| public str getSenderName()                             |                                                     |
| public str removeRecipient(str email, int type)        |                                                     |
| public boolean save()                                  |                                                     |
| public boolean saveMsgToFile(str fileName)             |                                                     |
| public boolean send()                                  |                                                     |
| public boolean setBody(str body)                       |                                                     |
| public void finalize()                                 |                                                     |
| public void close()                                    |                                                     |
| public void new()                                      | Initializes a new instance of the MapiExMail class. |

## Method addRecipient

```xpp
public str addRecipient(str email, str name, int type)
```

### Parameters - addRecipient

email  

<!-- -->

name  

<!-- -->

type  

### Return Value - addRecipient

## Method entryId

```xpp
public str entryId()
```

### Return Value - entryId

## Method getRecipient

```xpp
public boolean getRecipient(int index)
```

### Parameters - getRecipient

index  

### Return Value - getRecipient

## Method getRecipientCount

```xpp
public int getRecipientCount()
```

### Return Value - getRecipientCount

## Method getRecipientDisplayName

```xpp
public str getRecipientDisplayName()
```

### Return Value - getRecipientDisplayName

## Method getRecipientEmailAddress

```xpp
public str getRecipientEmailAddress()
```

### Return Value - getRecipientEmailAddress

## Method getRecipientEntryId

```xpp
public str getRecipientEntryId()
```

### Return Value - getRecipientEntryId

## Method getRecipients

```xpp
public boolean getRecipients()
```

### Return Value - getRecipients

## Method getRecipientSMTPAddress

```xpp
public str getRecipientSMTPAddress()
```

### Return Value - getRecipientSMTPAddress

## Method getRecipientType

```xpp
public int getRecipientType()
```

### Return Value - getRecipientType

## Method getSenderEmail

```xpp
public str getSenderEmail()
```

### Return Value - getSenderEmail

## Method getSenderName

```xpp
public str getSenderName()
```

### Return Value - getSenderName

## Method removeRecipient

```xpp
public str removeRecipient(str email, int type)
```

### Parameters - removeRecipient

email  

<!-- -->

type  

### Return Value - removeRecipient

## Method save

```xpp
public boolean save()
```

### Return Value - save

## Method saveMsgToFile

```xpp
public boolean saveMsgToFile(str fileName)
```

### Parameters - saveMsgToFile

fileName  

### Return Value - saveMsgToFile

## Method send

```xpp
public boolean send()
```

### Return Value - send

## Method setBody

```xpp
public boolean setBody(str body)
```

### Parameters - setBody

body  

### Return Value - setBody

## Method finalize

```xpp
public void finalize()
```

## Method close

```xpp
public void close()
```

## Method new

Initializes a new instance of the MapiExMail class.

```xpp
public void new()
```

