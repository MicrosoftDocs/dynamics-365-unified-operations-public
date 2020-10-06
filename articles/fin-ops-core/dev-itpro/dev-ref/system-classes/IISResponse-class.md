---
title: IISResponse class
description: This topic describes the IISResponse class.
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

# Class IISResponse

[!include [banner](../../includes/banner.md)]

```xpp
class IISResponse extends Object
```

The IISResponse class wraps the Response object that is offered by Internet Information Services (IIS).

## Remarks

There is a one-to-one relationship between the methods of the IISResponse class and the methods of the Response object that is offered by IIS. Therefore, for more information about the methods of the IISResponse class, see the Microsoft documentation for IIS. Use of the IISResponse class is valid only when code is run by the Internet Connector under IIS.

## Examples

## Methods

| Method                                                    | Description                                          |
|-----------------------------------------------------------|------------------------------------------------------|
| public boolean buffer(\[boolean isBuffering\])            |                                                      |
| public str cacheControl(\[str cacheControl\])             |                                                      |
| public boolean cacheWrite(\[boolean cache\])              |                                                      |
| public str charSet(\[str charSet\])                       |                                                      |
| public str contentType(\[str contentType\])               |                                                      |
| public IISRequestDictionary cookies()                     |                                                      |
| public int expires(\[int expiresMinutes\])                |                                                      |
| public COMVariant expiresAbsolute(\[COMVariant expires\]) |                                                      |
| public ComInterface interface()                           |                                                      |
| public boolean isClientConnected()                        |                                                      |
| public str status(\[str status\])                         | Gets or sets the status of an object.                |
| public void addHeader(str headerName, str headerValue)    |                                                      |
| public void writeTxt(str text)                            |                                                      |
| public void write(COMVariant text)                        |                                                      |
| public void clear()                                       |                                                      |
| public void finalize()                                    |                                                      |
| public void binaryWrite(COMVariant input)                 |                                                      |
| public void appendToLog(str logEntry)                     |                                                      |
| public void new()                                         | Initializes a new instance of the IISResponse class. |
| public void redirect(str url)                             |                                                      |
| public void flush()                                       |                                                      |
| public void pics(str headerValue)                         |                                                      |
| public void end()                                         |                                                      |

## Method buffer

```xpp
public boolean buffer([boolean isBuffering])
```

### Parameters - buffer

isBuffering  

### Return Value - buffer

## Method cacheControl

```xpp
public str cacheControl([str cacheControl])
```

### Parameters - cacheControl

cacheControl  

### Return Value - cacheControl

## Method cacheWrite

```xpp
public boolean cacheWrite([boolean cache])
```

### Parameters - cacheWrite

cache  

### Return Value - cacheWrite

## Method charSet

```xpp
public str charSet([str charSet])
```

### Parameters - charSet

charSet  

### Return Value - charSet

## Method contentType

```xpp
public str contentType([str contentType])
```

### Parameters - contentType

contentType  

### Return Value - contentType

## Method cookies

```xpp
public IISRequestDictionary cookies()
```

### Return Value - cookies

## Method expires

```xpp
public int expires([int expiresMinutes])
```

### Parameters - expires

expiresMinutes  

### Return Value - expires

## Method expiresAbsolute

```xpp
public COMVariant expiresAbsolute([COMVariant expires])
```

### Parameters - expiresAbsolute

expires  

### Return Value - expiresAbsolute

## Method interface

```xpp
public ComInterface interface()
```

### Return Value - interface

## Method isClientConnected

```xpp
public boolean isClientConnected()
```

### Return Value - isClientConnected

## Method status

Gets or sets the status of an object.

```xpp
public str status([str status])
```

### Parameters - status

status  

### Return Value - status

The current value of the status of the object.

## Method addHeader

```xpp
public void addHeader(str headerName, str headerValue)
```

### Parameters - addHeader

headerName  

<!-- -->

headerValue  

## Method writeTxt

```xpp
public void writeTxt(str text)
```

### Parameters - writeTxt

text  

## Method write

```xpp
public void write(COMVariant text)
```

### Parameters - write

text  

## Method clear

```xpp
public void clear()
```

## Method finalize

```xpp
public void finalize()
```

## Method binaryWrite

```xpp
public void binaryWrite(COMVariant input)
```

### Parameters - binaryWrite

input  

## Method appendToLog

```xpp
public void appendToLog(str logEntry)
```

### Parameters - appendToLog

logEntry  

## Method new

Initializes a new instance of the IISResponse class.

```xpp
public void new()
```

## Method redirect

```xpp
public void redirect(str url)
```

### Parameters - redirect

url  

## Method flush

```xpp
public void flush()
```

## Method pics

```xpp
public void pics(str headerValue)
```

### Parameters - pics

headerValue  

## Method end

```xpp
public void end()
```

