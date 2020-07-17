---
title: BinData class
description: This topic describes the BinData class.
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

# Class BinData

[!include [banner](../../includes/banner.md)]

```xpp
class BinData extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                | Description                                   |
|-----------------------------------------------------------------------|-----------------------------------------------|
| public boolean appendToFile(str filename)                             |                                               |
| public str ascii85Encode()                                            |                                               |
| public str base64Encode()                                             |                                               |
| public int compressLZ77(int windowBits)                               |                                               |
| public boolean copyData(BinData data, \[int offset\], \[int length\]) |                                               |
| public int decompressLZ77()                                           |                                               |
| public str getAsciiData()                                             |                                               |
| public container getData()                                            |                                               |
| public str getStrData()                                               |                                               |
| public COMVariant getVariant()                                        |                                               |
| public boolean loadFile(str filename, \[int offset\], \[int length\]) |                                               |
| public boolean saveFile(str filename)                                 |                                               |
| public int size()                                                     |                                               |
| ::public static str dataToString(container data)                      |                                               |
| ::public static container loadFromAscii85(str ascii85EncodedString)   |                                               |
| ::public static container loadFromBase64(str base64EncodedString)     |                                               |
| ::public static container stringToData(str string)                    |                                               |
| public void setStrData(str data)                                      |                                               |
| public void setVariant(COMVariant data)                               |                                               |
| public void appendData(BinData binData)                               |                                               |
| public void new()                                                     | Initializes an instance of the BinData class. |
| public void setBinaryData(Binary binary)                              |                                               |
| public void setAsciiData(str data, \[int codePage\])                  |                                               |
| public void setData(container data)                                   |                                               |
| public void finalize()                                                |                                               |

## Method appendToFile

```xpp
public boolean appendToFile(str filename)
```

### Parameters - appendToFile

filename  

### Return Value - appendToFile

## Method ascii85Encode

```xpp
public str ascii85Encode()
```

### Return Value - ascii85Encode

## Method base64Encode

```xpp
public str base64Encode()
```

### Return Value - base64Encode

## Method compressLZ77

```xpp
public int compressLZ77(int windowBits)
```

### Parameters - compressLZ77

windowBits  

### Return Value - compressLZ77

## Method copyData

```xpp
public boolean copyData(BinData data, [int offset], [int length])
```

### Parameters - copyData

data  

<!-- -->

offset  

<!-- -->

length  

### Return Value - copyData

## Method decompressLZ77

```xpp
public int decompressLZ77()
```

### Return Value - decompressLZ77

## Method getAsciiData

```xpp
public str getAsciiData()
```

### Return Value - getAsciiData

## Method getData

```xpp
public container getData()
```

### Return Value - getData

## Method getStrData

```xpp
public str getStrData()
```

### Return Value - getStrData

## Method getVariant

```xpp
public COMVariant getVariant()
```

### Return Value - getVariant

## Method loadFile

```xpp
public boolean loadFile(str filename, [int offset], [int length])
```

### Parameters - loadFile

filename  

<!-- -->

offset  

<!-- -->

length  

### Return Value - loadFile

### Remarks - loadFile

If an attacker can control input to the loadFile method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

## Method saveFile

```xpp
public boolean saveFile(str filename)
```

### Parameters - saveFile

filename  

### Return Value - saveFile

### Remarks - saveFile

If an attacker can control input to the saveFile method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

## Method size

```xpp
public int size()
```

### Return Value - size

## Method dataToString

```xpp
public static str dataToString(container data)
```

### Parameters - dataToString

data  

### Return Value - dataToString

## Method loadFromAscii85

```xpp
public static container loadFromAscii85(str ascii85EncodedString)
```

### Parameters - loadFromAscii85

ascii85EncodedString  

### Return Value - loadFromAscii85

## Method loadFromBase64

```xpp
public static container loadFromBase64(str base64EncodedString)
```

### Parameters - loadFromBase64

base64EncodedString  

### Return Value - loadFromBase64

## Method stringToData

```xpp
public static container stringToData(str string)
```

### Parameters - stringToData

string  

### Return Value - stringToData

## Method setStrData

```xpp
public void setStrData(str data)
```

### Parameters - setStrData

data  

## Method setVariant

```xpp
public void setVariant(COMVariant data)
```

### Parameters - setVariant

data  

## Method appendData

```xpp
public void appendData(BinData binData)
```

### Parameters - appendData

binData  

## Method new

Initializes an instance of the BinData class.

```xpp
public void new()
```

## Method setBinaryData

```xpp
public void setBinaryData(Binary binary)
```

### Parameters - setBinaryData

binary  

## Method setAsciiData

```xpp
public void setAsciiData(str data, [int codePage])
```

### Parameters - setAsciiData

data  

<!-- -->

codePage  

## Method setData

```xpp
public void setData(container data)
```

### Parameters - setData

data  

## Method finalize

```xpp
public void finalize()
```


