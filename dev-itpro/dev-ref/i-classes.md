---
# required metadata

title: I Classes
description: System API classes that start with the letter I.
author: RobinARH
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: RobinARH
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 52171
ms.assetid: bd6df991-7b90-40f0-b342-025ab000c24c
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# I Classes

[!include[banner](../includes/banner.md)]


System API classes that start with the letter I.

Class IDispatcherProxy
----------------------

    class IDispatcherProxy

### Remarks

### Examples

### Methods

| Method                                         | Description |
|------------------------------------------------|-------------|
| public AnyType invoke(str methodName, VarArg ) |             |
| public void refresh()                          |             |

### Method invoke

    public AnyType invoke(str methodName, VarArg )

#### Parameters

methodName  

<!-- -->

  

#### Return Value

### Method refresh

    public void refresh()

## Class IISApplicationObject
    class IISApplicationObject extends Object

The IISApplicationObject class wraps the Application object that is offered by Internet Information Services (IIS).

### Remarks

There is a one-to-one connection between the methods of the IISApplicationObject class and the methods of the Application object that is offered by IIS. Therefore, for more information about the methods of the IISApplicationObject class, see the Microsoft documentation for IIS. Use of the IISApplicationObject class is valid only when code is run by the Microsoft Dynamics 365 for Operations Internet Connector under IIS.

### Examples

### Methods

| Method                                                 | Description                                                   |
|--------------------------------------------------------|---------------------------------------------------------------|
| public IISVariantDictionary contents()                 |                                                               |
| public ComInterface interface()                        |                                                               |
| public IISVariantDictionary staticObjects()            |                                                               |
| public COMVariant value(str value, \[COMVariant var\]) |                                                               |
| public str valueTxt(str value, \[str var\])            |                                                               |
| public void new()                                      | Initializes a new instance of the IISApplicationObject class. |
| public void finalize()                                 |                                                               |
| public void lock()                                     |                                                               |
| public void unLock()                                   |                                                               |

### Method contents

    public IISVariantDictionary contents()

#### Return Value

### Method interface

    public ComInterface interface()

#### Return Value

### Method staticObjects

    public IISVariantDictionary staticObjects()

#### Return Value

### Method value

    public COMVariant value(str value, [COMVariant var])

#### Parameters

value  

<!-- -->

var  

#### Return Value

### Method valueTxt

    public str valueTxt(str value, [str var])

#### Parameters

value  

<!-- -->

var  

#### Return Value

### Method new

Initializes a new instance of the IISApplicationObject class.

    public void new()

### Method finalize

    public void finalize()

### Method lock

    public void lock()

### Method unLock

    public void unLock()

## Class IISContextObject
    class IISContextObject extends Object

### Remarks

### Examples

### Methods

| Method                                                 | Description                                               |
|--------------------------------------------------------|-----------------------------------------------------------|
| public ComInterface interface()                        |                                                           |
| public boolean isTraceEnabled()                        |                                                           |
| public IISVariantDictionary items()                    |                                                           |
| public int traceMode(int mode)                         |                                                           |
| public COMVariant value(str value, \[COMVariant var\]) |                                                           |
| public str valueTxt(str value, \[str var\])            |                                                           |
| public void traceWrite(str category, str message)      |                                                           |
| public void finalize()                                 |                                                           |
| public void traceWarn(str category, str message)       |                                                           |
| public void new()                                      | Initializes a new instance of the IISContextObject class. |

### Method interface

    public ComInterface interface()

#### Return Value

### Method isTraceEnabled

    public boolean isTraceEnabled()

#### Return Value

### Method items

    public IISVariantDictionary items()

#### Return Value

### Method traceMode

    public int traceMode(int mode)

#### Parameters

mode  

#### Return Value

### Method value

    public COMVariant value(str value, [COMVariant var])

#### Parameters

value  

<!-- -->

var  

#### Return Value

### Method valueTxt

    public str valueTxt(str value, [str var])

#### Parameters

value  

<!-- -->

var  

#### Return Value

### Method traceWrite

    public void traceWrite(str category, str message)

#### Parameters

category  

<!-- -->

message  

### Method finalize

    public void finalize()

### Method traceWarn

    public void traceWarn(str category, str message)

#### Parameters

category  

<!-- -->

message  

### Method new

Initializes a new instance of the IISContextObject class.

    public void new()

## Class IISPostedFile
    class IISPostedFile extends Object

### Remarks

### Examples

### Methods

| Method                                 | Description                                            |
|----------------------------------------|--------------------------------------------------------|
| public int contentLength()             |                                                        |
| public str contentType()               |                                                        |
| public str fileName()                  |                                                        |
| public container read(int countToRead) |                                                        |
| public void finalize()                 |                                                        |
| public void new()                      | Initializes a new instance of the IISPostedFile class. |

### Method contentLength

    public int contentLength()

#### Return Value

### Method contentType

    public str contentType()

#### Return Value

### Method fileName

    public str fileName()

#### Return Value

### Method read

    public container read(int countToRead)

#### Parameters

countToRead  

#### Return Value

### Method finalize

    public void finalize()

### Method new

Initializes a new instance of the IISPostedFile class.

    public void new()

## Class IISReadCookie
    class IISReadCookie extends Object

The IISReadCookie class wraps the ReadCookie object that is offered by Internet Information Services (IIS).

### Remarks

There is a one-to-one connection between the methods of the IISReadCookie class and the methods of the ReadCookie object that is offered by IIS. Therefore, for more information about the methods of the IISReadCookie class, see the Microsoft documentation for IIS. Use of the IISReadCookie class is valid only when code is run by the Microsoft Dynamics 365 for Operations Internet Connector under IIS.

### Examples

### Methods

| Method                           | Description                                     |
|----------------------------------|-------------------------------------------------|
| public int count()               |                                                 |
| public COMEnum2Variant getEnum() |                                                 |
| public boolean hasKeys()         |                                                 |
| public ComInterface interface()  |                                                 |
| public str item(\[str item\])    |                                                 |
| public str key(str key)          |                                                 |
| public void finalize()           |                                                 |
| public void new(COM readCookie)  | Initializes a new instance of the Object class. |

### Method count

    public int count()

#### Return Value

### Method getEnum

    public COMEnum2Variant getEnum()

#### Return Value

### Method hasKeys

    public boolean hasKeys()

#### Return Value

### Method interface

    public ComInterface interface()

#### Return Value

### Method item

    public str item([str item])

#### Parameters

item  

#### Return Value

### Method key

    public str key(str key)

#### Parameters

key  

#### Return Value

### Method finalize

    public void finalize()

### Method new

Initializes a new instance of the Object class.

    public void new(COM readCookie)

#### Parameters

readCookie  

## Class IISRequest
    class IISRequest extends Object

The IISRequest class wraps the Request object that is offered by Internet Information Services (IIS).

### Remarks

There is a one-to-one connection between the methods of the IISRequest class and the methods of the Request object that is offered by IIS. Therefore, for more information about the methods of the IISRequest class, see the Microsoft documentation for IIS. Use of the IISRequest class is valid only when code is run by the Microsoft Dynamics 365 for Operations Internet Connector under IIS.

### Examples

### Methods

| Method                                               | Description                                         |
|------------------------------------------------------|-----------------------------------------------------|
| public COMVariant binaryRead(COMVariant countToRead) |                                                     |
| public IISRequestDictionary clientCertificate()      |                                                     |
| public IISRequestDictionary cookies()                |                                                     |
| public IISPostedFile file(COMVariant index)          |                                                     |
| public int fileCount()                               |                                                     |
| public IISRequestDictionary form()                   |                                                     |
| public ComInterface interface()                      |                                                     |
| public str item(str item)                            |                                                     |
| public IISRequestDictionary queryString()            |                                                     |
| public IISRequestDictionary serverVariables()        |                                                     |
| public int totalBytes()                              |                                                     |
| public void finalize()                               |                                                     |
| public void new()                                    | Initializes a new instance of the IISRequest class. |

### Method binaryRead

    public COMVariant binaryRead(COMVariant countToRead)

#### Parameters

countToRead  

#### Return Value

### Method clientCertificate

    public IISRequestDictionary clientCertificate()

#### Return Value

### Method cookies

    public IISRequestDictionary cookies()

#### Return Value

### Method file

    public IISPostedFile file(COMVariant index)

#### Parameters

index  

#### Return Value

### Method fileCount

    public int fileCount()

#### Return Value

### Method form

    public IISRequestDictionary form()

#### Return Value

### Method interface

    public ComInterface interface()

#### Return Value

### Method item

    public str item(str item)

#### Parameters

item  

#### Return Value

### Method queryString

    public IISRequestDictionary queryString()

#### Return Value

### Method serverVariables

    public IISRequestDictionary serverVariables()

#### Return Value

### Method totalBytes

    public int totalBytes()

#### Return Value

### Method finalize

    public void finalize()

### Method new

Initializes a new instance of the IISRequest class.

    public void new()

## Class IISRequestDictionary
    class IISRequestDictionary extends Object

The IISRequestDictionary class wraps the RequestDictionary object that is offered by Internet Information Services (IIS).

### Remarks

There is a one-to-one relationship between the methods of the IISRequestDictionary class and the methods of the RequestDictionary object that is offered by IIS. Therefore, for more information about the methods of the IISRequestDictionary class, see the Microsoft documentation for IIS. Use of the IISRequestDictionary class is valid only when code is run by the Microsoft Dynamics 365 for Operations Internet Connector under IIS.

### Examples

### Methods

| Method                                              | Description                                     |
|-----------------------------------------------------|-------------------------------------------------|
| public int count()                                  |                                                 |
| public COMEnum2Variant getEnum()                    |                                                 |
| public ComInterface interface()                     |                                                 |
| public COMVariant item(COMVariant item)             |                                                 |
| public IISReadCookie itemReadCookie(\[str item\])   |                                                 |
| public IISStringList itemStringList(\[str item\])   |                                                 |
| public str itemTxt(str item)                        |                                                 |
| public IISWriteCookie itemWriteCookie(\[str item\]) |                                                 |
| public str key(str key)                             |                                                 |
| public void finalize()                              |                                                 |
| public void new(COM requestDictionary)              | Initializes a new instance of the Object class. |

### Method count

    public int count()

#### Return Value

### Method getEnum

    public COMEnum2Variant getEnum()

#### Return Value

### Method interface

    public ComInterface interface()

#### Return Value

### Method item

    public COMVariant item(COMVariant item)

#### Parameters

item  

#### Return Value

### Method itemReadCookie

    public IISReadCookie itemReadCookie([str item])

#### Parameters

item  

#### Return Value

### Method itemStringList

    public IISStringList itemStringList([str item])

#### Parameters

item  

#### Return Value

### Method itemTxt

    public str itemTxt(str item)

#### Parameters

item  

#### Return Value

### Method itemWriteCookie

    public IISWriteCookie itemWriteCookie([str item])

#### Parameters

item  

#### Return Value

### Method key

    public str key(str key)

#### Parameters

key  

#### Return Value

### Method finalize

    public void finalize()

### Method new

Initializes a new instance of the Object class.

    public void new(COM requestDictionary)

#### Parameters

requestDictionary  

## Class IISResponse
    class IISResponse extends Object

The IISResponse class wraps the Response object that is offered by Internet Information Services (IIS).

### Remarks

There is a one-to-one relationship between the methods of the IISResponse class and the methods of the Response object that is offered by IIS. Therefore, for more information about the methods of the IISResponse class, see the Microsoft documentation for IIS. Use of the IISResponse class is valid only when code is run by the Microsoft Dynamics 365 for Operations Internet Connector under IIS.

### Examples

### Methods

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

### Method buffer

    public boolean buffer([boolean isBuffering])

#### Parameters

isBuffering  

#### Return Value

### Method cacheControl

    public str cacheControl([str cacheControl])

#### Parameters

cacheControl  

#### Return Value

### Method cacheWrite

    public boolean cacheWrite([boolean cache])

#### Parameters

cache  

#### Return Value

### Method charSet

    public str charSet([str charSet])

#### Parameters

charSet  

#### Return Value

### Method contentType

    public str contentType([str contentType])

#### Parameters

contentType  

#### Return Value

### Method cookies

    public IISRequestDictionary cookies()

#### Return Value

### Method expires

    public int expires([int expiresMinutes])

#### Parameters

expiresMinutes  

#### Return Value

### Method expiresAbsolute

    public COMVariant expiresAbsolute([COMVariant expires])

#### Parameters

expires  

#### Return Value

### Method interface

    public ComInterface interface()

#### Return Value

### Method isClientConnected

    public boolean isClientConnected()

#### Return Value

### Method status

Gets or sets the status of an object.

    public str status([str status])

#### Parameters

status  

#### Return Value

The current value of the status of the object.

### Method addHeader

    public void addHeader(str headerName, str headerValue)

#### Parameters

headerName  

<!-- -->

headerValue  

### Method writeTxt

    public void writeTxt(str text)

#### Parameters

text  

### Method write

    public void write(COMVariant text)

#### Parameters

text  

### Method clear

    public void clear()

### Method finalize

    public void finalize()

### Method binaryWrite

    public void binaryWrite(COMVariant input)

#### Parameters

input  

### Method appendToLog

    public void appendToLog(str logEntry)

#### Parameters

logEntry  

### Method new

Initializes a new instance of the IISResponse class.

    public void new()

### Method redirect

    public void redirect(str url)

#### Parameters

url  

### Method flush

    public void flush()

### Method pics

    public void pics(str headerValue)

#### Parameters

headerValue  

### Method end

    public void end()

## Class IISServer
    class IISServer extends Object

The IISServer class wraps the Server object that is offered by Internet Information Services (IIS).

### Remarks

There is a one-to-one connection between the methods of the IISServer class and the methods of the Server object that is offered by IIS. Therefore, for more information about the methods of the IISServer class, see the Microsoft documentation for IIS. Use of the IISServer class is valid only when code is run by the Microsoft Dynamics 365 for Operations Internet Connector under IIS.

### Examples

### Methods

| Method                                           | Description                                        |
|--------------------------------------------------|----------------------------------------------------|
| public COM createObject(str progID)              |                                                    |
| public str htmlEncode(str txt)                   |                                                    |
| public ComInterface interface()                  |                                                    |
| public str mapPath(str logicalPath)              |                                                    |
| public int scriptTimeout(\[int timeoutSeconds\]) |                                                    |
| public str urlEncode(str txt)                    |                                                    |
| public str urlPathEncode(str txt)                |                                                    |
| public void execute(str logicalPath)             |                                                    |
| public void transfer(str logicalPath)            |                                                    |
| public void new()                                | Initializes a new instance of the IISServer class. |
| public void finalize()                           |                                                    |

### Method createObject

    public COM createObject(str progID)

#### Parameters

progID  

#### Return Value

### Method htmlEncode

    public str htmlEncode(str txt)

#### Parameters

txt  

#### Return Value

### Method interface

    public ComInterface interface()

#### Return Value

### Method mapPath

    public str mapPath(str logicalPath)

#### Parameters

logicalPath  

#### Return Value

### Method scriptTimeout

    public int scriptTimeout([int timeoutSeconds])

#### Parameters

timeoutSeconds  

#### Return Value

### Method urlEncode

    public str urlEncode(str txt)

#### Parameters

txt  

#### Return Value

### Method urlPathEncode

    public str urlPathEncode(str txt)

#### Parameters

txt  

#### Return Value

### Method execute

    public void execute(str logicalPath)

#### Parameters

logicalPath  

### Method transfer

    public void transfer(str logicalPath)

#### Parameters

logicalPath  

### Method new

Initializes a new instance of the IISServer class.

    public void new()

### Method finalize

    public void finalize()

## Class IISSessionObject
    class IISSessionObject extends Object

The IISSessionObject class wraps the Session object that is offered by Internet Information Services (IIS).

### Remarks

There is a one-to-one connection between the methods of the IISSessionObject class and the methods of the Session object that is offered by IIS. Therefore, for more information about the methods of the IISSessionObject class, see the Microsoft documentation for IIS. Use of the IISSessionObject class is valid only when code is run by the Microsoft Dynamics 365 for Operations Internet Connector under IIS.

### Examples

### Methods

| Method                                                 | Description                                               |
|--------------------------------------------------------|-----------------------------------------------------------|
| public int codePage(\[int codePage\])                  |                                                           |
| public IISVariantDictionary contents()                 |                                                           |
| public str getSessionID()                              |                                                           |
| public ComInterface interface()                        |                                                           |
| public int lcid(\[int lcid\])                          |                                                           |
| public IISVariantDictionary staticObjects()            |                                                           |
| public int timeout(\[int timeout\])                    |                                                           |
| public COMVariant value(str value, \[COMVariant var\]) |                                                           |
| public str valueTxt(str value, \[str var\])            |                                                           |
| public void new()                                      | Initializes a new instance of the IISSessionObject class. |
| public void abandon()                                  |                                                           |
| public void finalize()                                 |                                                           |

### Method codePage

    public int codePage([int codePage])

#### Parameters

codePage  

#### Return Value

### Method contents

    public IISVariantDictionary contents()

#### Return Value

### Method getSessionID

    public str getSessionID()

#### Return Value

### Method interface

    public ComInterface interface()

#### Return Value

### Method lcid

    public int lcid([int lcid])

#### Parameters

lcid  

#### Return Value

### Method staticObjects

    public IISVariantDictionary staticObjects()

#### Return Value

### Method timeout

    public int timeout([int timeout])

#### Parameters

timeout  

#### Return Value

### Method value

    public COMVariant value(str value, [COMVariant var])

#### Parameters

value  

<!-- -->

var  

#### Return Value

### Method valueTxt

    public str valueTxt(str value, [str var])

#### Parameters

value  

<!-- -->

var  

#### Return Value

### Method new

Initializes a new instance of the IISSessionObject class.

    public void new()

### Method abandon

    public void abandon()

### Method finalize

    public void finalize()

## Class IISStringList
    class IISStringList extends Object

The IISStringList class wraps the StringList object that is offered by Internet Information Services (IIS).

### Remarks

There is a one-to-one connection between the methods of the IISStringList class and the methods of the StringList object that is offered by IIS. Therefore, for more information about the methods of the IISStringList class, see the Microsoft documentation for IIS. Use of the IISStringList class is valid only when code is run by the Microsoft Dynamics 365 for Operations Internet Connector under IIS.

### Examples

### Methods

| Method                           | Description                                     |
|----------------------------------|-------------------------------------------------|
| public int count()               |                                                 |
| public COMEnum2Variant getEnum() |                                                 |
| public ComInterface interface()  |                                                 |
| public str item(\[str item\])    |                                                 |
| public void finalize()           |                                                 |
| public void new(COM stringList)  | Initializes a new instance of the Object class. |

### Method count

    public int count()

#### Return Value

### Method getEnum

    public COMEnum2Variant getEnum()

#### Return Value

### Method interface

    public ComInterface interface()

#### Return Value

### Method item

    public str item([str item])

#### Parameters

item  

#### Return Value

### Method finalize

    public void finalize()

### Method new

Initializes a new instance of the Object class.

    public void new(COM stringList)

#### Parameters

stringList  

## Class IISVariantDictionary
    class IISVariantDictionary extends Object

The IISVariantDictionary class wraps the VariantDictionary object that is offered by Internet Information Services (IIS).

### Remarks

There is a one-to-one connection between the methods of the IISVariantDictionary class and the methods of the VariantDictionary object that is offered by IIS. Therefore, for more information about the methods of the IISVariantDictionary class, see the Microsoft documentation for IIS. Use of the IISVariantDictionary class is valid only when code is run by the Microsoft Dynamics 365 for Operations Internet Connector under IIS.

### Examples

### Methods

| Method                                                      | Description                                     |
|-------------------------------------------------------------|-------------------------------------------------|
| public int count()                                          |                                                 |
| public COMEnum2Variant getEnum()                            |                                                 |
| public ComInterface interface()                             |                                                 |
| public COMVariant item(COMVariant item, \[COMVariant var\]) |                                                 |
| public COM itemObj(str item, \[COM var\])                   |                                                 |
| public str itemTxt(str item, \[str var\])                   |                                                 |
| public str key(str key)                                     |                                                 |
| public void finalize()                                      |                                                 |
| public void remove(str key)                                 |                                                 |
| public void removeAll()                                     |                                                 |
| public void new(COM variantDictionary)                      | Initializes a new instance of the Object class. |

### Method count

    public int count()

#### Return Value

### Method getEnum

    public COMEnum2Variant getEnum()

#### Return Value

### Method interface

    public ComInterface interface()

#### Return Value

### Method item

    public COMVariant item(COMVariant item, [COMVariant var])

#### Parameters

item  

<!-- -->

var  

#### Return Value

### Method itemObj

    public COM itemObj(str item, [COM var])

#### Parameters

item  

<!-- -->

var  

#### Return Value

### Method itemTxt

    public str itemTxt(str item, [str var])

#### Parameters

item  

<!-- -->

var  

#### Return Value

### Method key

    public str key(str key)

#### Parameters

key  

#### Return Value

### Method finalize

    public void finalize()

### Method remove

    public void remove(str key)

#### Parameters

key  

### Method removeAll

    public void removeAll()

### Method new

Initializes a new instance of the Object class.

    public void new(COM variantDictionary)

#### Parameters

variantDictionary  

## Class IISViewState
    class IISViewState extends Object

### Remarks

### Examples

### Methods

| Method                                         | Description                                           |
|------------------------------------------------|-------------------------------------------------------|
| public boolean viewStateContains(str key)      |                                                       |
| public str viewStateItem(str key, \[str val\]) |                                                       |
| public void finalize()                         |                                                       |
| public void viewStateDelete(str key)           |                                                       |
| public void new()                              | Initializes a new instance of the IISViewState class. |

### Method viewStateContains

    public boolean viewStateContains(str key)

#### Parameters

key  

#### Return Value

### Method viewStateItem

    public str viewStateItem(str key, [str val])

#### Parameters

key  

<!-- -->

val  

#### Return Value

### Method finalize

    public void finalize()

### Method viewStateDelete

    public void viewStateDelete(str key)

#### Parameters

key  

### Method new

Initializes a new instance of the IISViewState class.

    public void new()

## Class IISWriteCookie
    class IISWriteCookie extends Object

The IISWriteCookie class wraps the WriteCookie object that is offered by Internet Information Services (IIS).

### Remarks

There is a one-to-one connection between the methods of the IISWriteCookie class and the methods of the WriteCookie object that is offered by IIS. Therefore, for more information about the methods of the IISWriteCookie class, see the Microsoft documentation for IIS. Use of the IISWriteCookie class is valid only when code is run by the Microsoft Dynamics 365 for Operations Internet Connector under IIS.

### Examples

### Methods

| Method                                  | Description                                     |
|-----------------------------------------|-------------------------------------------------|
| public COMEnum2Variant getEnum()        |                                                 |
| public boolean hasKeys()                |                                                 |
| public ComInterface interface()         |                                                 |
| public void new(COM writeCookie)        | Initializes a new instance of the Object class. |
| public void secure(boolean secure)      |                                                 |
| public void path(str path)              |                                                 |
| public void finalize()                  |                                                 |
| public void domain(str domain)          |                                                 |
| public void expires(COMVariant expires) |                                                 |
| public void item(str item, str value)   |                                                 |

### Method getEnum

    public COMEnum2Variant getEnum()

#### Return Value

### Method hasKeys

    public boolean hasKeys()

#### Return Value

### Method interface

    public ComInterface interface()

#### Return Value

### Method new

Initializes a new instance of the Object class.

    public void new(COM writeCookie)

#### Parameters

writeCookie  

### Method secure

    public void secure(boolean secure)

#### Parameters

secure  

### Method path

    public void path(str path)

#### Parameters

path  

### Method finalize

    public void finalize()

### Method domain

    public void domain(str domain)

#### Parameters

domain  

### Method expires

    public void expires(COMVariant expires)

#### Parameters

expires  

### Method item

    public void item(str item, str value)

#### Parameters

item  

<!-- -->

value  

## Class Image
    class Image extends BinData

Provides methods for loading, saving, and manipulating images. If you want to manipulate several images at the same time, use the Imagelist Class.

### Remarks

You can construct Image objects from the following file types:

-   Raster (bitmap) formats - .bmp, .gif, .jpg, .png, .tiff, and .exif
-   Vector formats - .emf and .wmf

If you want to work with several images at the same time, use the Imagelist class. You can construct the Image objects from the following file types:

-   Raster, which is a bitmap, formats - .bmp, .gif, .jpg, .png, .tiff, and .exif
-   Vector formats - .emf and .wmf

In Microsoft Dynamics 365 for Operations, the Image class is bound to the client. The class can no longer be run from the server because of the security risks that are associated with file handling.

### Examples

The following example prints the height of Picture.jpg in pixels.

    Image img = new  Image(); 
    img.loadFile(@'C:\MyPictures\Picture.jpg'); 
    print img.height(); 
    pause;

### Methods

| Method                                                                                                      | Description                                                                                                                                   |
|-------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| public int captureScreen(int left, int top, int right, int bottom)                                          | Captures an image from the screen by using the coordinates that are supplied in the parameter list.                                           |
| public int captureWindow(int hWnd)                                                                          | Captures a window as an image, using the handle that is supplied as a parameter.                                                              |
| public int clipboardCopy()                                                                                  | Copies an image to the clipboard.                                                                                                             |
| public int clipboardPaste()                                                                                 | Overwrites an existing image with the content of the system clipboard.                                                                        |
| public int copyImage(Image image)                                                                           | Copies the current image object.                                                                                                              |
| public int createImage(int Width, int Height, int BitsPerPixel)                                             | Creates an empty bitmap image with the width, height, and color depth as specified by the parameters.                                         |
| public int crop(int x, int y, int w, int h)                                                                 | Crops the image.                                                                                                                              |
| public int displayImage(Int64 HDC, \[int Mode\], \[int Xpos\], \[int Ypos\], \[int Width\], \[int Height\]) | Draws an image with the device context specified by the HDC parameter.                                                                        |
| public Int64 exportBitmap()                                                                                 | Gets a handle for the image.                                                                                                                  |
| public int flip(FlipType FlipType)                                                                          | Rotates the image 180 degrees in a vertical or horizontal direction.                                                                          |
| public container getImageDimensionUnits()                                                                   |                                                                                                                                               |
| public int getPixel(int x, int y)                                                                           | Retrieves the ARGB color value of the pixel at the point that is specified by the parameters.                                                 |
| public int height()                                                                                         | Retrieves the height of the image in pixels.                                                                                                  |
| public container imageInfo()                                                                                | Retrieves the width, height, and color depth of the image.                                                                                    |
| public int imageSpotlight(int x, int y, int radius, int smoothing, int intensity)                           | Produces a spotlight effect within the circle that is defined by radius with center coordinates x and y.                                      |
| public int importBitmap(Int64 hBitmap)                                                                      | Clones a bitmap from the image that is specified by the hBitmap parameter.                                                                    |
| public int importFileIcon(str fileName)                                                                     | Creates an icon from the file specified by the fileName parameter by copying the icon that is used for the file.                              |
| public int importIcon(str fileName, int iconIdx)                                                            | Retrieves a handle to an icon from an executable file in Microsoft Dynamics 365 for Operations. The icon is specified by the fileName and iconIdx parameters. |
| public int loadImage(str fileName)                                                                          | Loads an image from the file specified by the fileName parameter.                                                                             |
| public int loadResource(int id)                                                                             | Loads a resource from Ax32.exe.                                                                                                               |
| public int promoteColor(int noOfColorBits)                                                                  | Increases the color depth of the image.                                                                                                       |
| public int reduceColorOctree(int maxColors)                                                                 | Reduces the color depth of an image.                                                                                                          |
| public int removeImage()                                                                                    | Removes the data about an image; the object still exists, but has no data.                                                                    |
| public int resize(int newWidth, int newHeight, InterpolationMode InterpolationMode)                         | Resizes the image to the size that is specified by the newWidth and newHeight parameters.                                                     |
| public int rotate(RotateType RotateType)                                                                    | Rotates the image.                                                                                                                            |
| public int saveImage(str fileName, \[ImageSaveType Type\])                                                  | Saves the image to the specified file name.                                                                                                   |
| public ImageSaveType saveType(\[ImageSaveType Type\])                                                       | Gets or sets the image decoder.                                                                                                               |
| public int setPixel(int x, int y, int pixel)                                                                | Sets the color for the pixel that is specified by the x and y parameters.                                                                     |
| public int transparent(\[boolean Set\], \[int RValue\], \[int GValue\], \[int BValue\])                     | Sets the transparent color for the image.                                                                                                     |
| public int width()                                                                                          | Retrieves the width of the image in pixels.                                                                                                   |
| ::public static int canLoad(str filename)                                                                   | Determines whether an image file exists and can be opened.                                                                                    |
| ::public static container loadExt(int idx)                                                                  | Retrieves a list of the extensions of the file formats that are supported by the Image class.                                                 |
| ::public static int resourceType(int resourceIdx)                                                           | Determines whether a particular resource is a bitmap or an icon.                                                                              |
| ::public static int rgb(int R, int G, int B)                                                                | Converts an RGB value to an ARGB value.                                                                                                       |
| ::public static int validResource(int id)                                                                   | Determines whether the resource specified by the id parameter is valid.                                                                       |
| public void new(\[AnyType image\], \[int width\], \[int height\])                                           | Creates a new image.                                                                                                                          |
| public void displayOrign(int Xpos, int Ypos)                                                                | Enables you to specify an offset (X, Y) from the original origin (0, 0).                                                                      |
| public void finalize()                                                                                      |                                                                                                                                               |

### Method captureScreen

Captures an image from the screen by using the coordinates that are supplied in the parameter list.

    public int captureScreen(int left, int top, int right, int bottom)

#### Parameters

left  
Y coordinate of the lower-right corner of the part of the screen that you want to capture.

<!-- -->

top  
Y coordinate of the lower-right corner of the part of the screen that you want to capture.

<!-- -->

right  
Y coordinate of the lower-right corner of the part of the screen that you want to capture.

<!-- -->

bottom  
Y coordinate of the lower-right corner of the part of the screen that you want to capture.

#### Return Value

0 indicates success. Other values indicate failure.

#### Examples

The following example captures a part of the screen and saves it to a file that is named test.bmp.

    Image img = new Image(); 
    img.captureScreen(0, 0, 100, 100); 
    img.saveFile(@'C:\test.bmp');

### Method captureWindow

Captures a window as an image, using the handle that is supplied as a parameter.

    public int captureWindow(int hWnd)

#### Parameters

hWnd  
The handle to the window that you want to capture which must be supplied as an integer.

#### Return Value

0 indicates success; otherwise, failure.

### Method clipboardCopy

Copies an image to the clipboard.

    public int clipboardCopy()

#### Return Value

0 indicates success; otherwise, failure.

#### Examples

The following example copies the content from a file that is named Test.bmp.

    Image img = new Image(); 
    img.loadFile(@'C:\Test.bmp'); 
    img.clipboardCopy(); 
    // Image can now be pasted into an application.

### Method clipboardPaste

Overwrites an existing image with the content of the system clipboard.

    public int clipboardPaste()

#### Return Value

0 indicates success; otherwise, failure.

#### Remarks

For the method to be used successfully, the clipboard must have content.

#### Examples

The following example creates a new image file by using contents previously copied to the clipboard.

    Image img = new Image();
    // Copy an image to the clipboard before this test 
    img.clipboardPaste(); 
    img.saveFile(@'C:\test.jpg');

### Method copyImage

Copies the current image object.

    public int copyImage(Image image)

#### Parameters

image  
The image to be copied.

#### Return Value

0 indicates success; otherwise, failure.

#### Examples

The following example creates two new images and then overwrites the contents of one image with the contents of the other.

    Image img =  new Image(); 
    Image img2 = new Image(); 
    img.loadFile(@'C:\test.bmp'); 
    img2.loadFile(@'C:\test2.bmp'); 
    img2.copyImage(img); //img2 now the same as img

### Method createImage

Creates an empty bitmap image with the width, height, and color depth as specified by the parameters.

    public int createImage(int Width, int Height, int BitsPerPixel)

#### Parameters

Width  
The color depth of the image. Possible values are 1, 4, 8, 16, 24, and 32.

<!-- -->

Height  
The color depth of the image. Possible values are 1, 4, 8, 16, 24, and 32.

<!-- -->

BitsPerPixel  
The color depth of the image. Possible values are 1, 4, 8, 16, 24, and 32.

#### Return Value

0 indicates success; otherwise, failure.

#### Examples

The following example creates an image with a height and width of 16 pixels, and a color depth of 32 bits per pixel.

    int i;
    int j;
    Image image;
    image.createImage(
        Imagelist::smallIconWidth(),
        Imagelist::smallIconHeight(),
        32);
    for (i=0; i < Imagelist::smallIconWidth(); i++)
    {
        for (j=0; j < Imagelist::smallIconHeight(); j++)
        {
            if (i >= Imagelist::smallIconWidth()-2)
            {
                image.setPixel(i, j, WinAPI::RGB2int(0, 255, 255));
            }
            else
            {
                image.setPixel(i, j, WinAPI::imageTransparentColor());
            }
        }
    }

### Method crop

Crops the image.

    public int crop(int x, int y, int w, int h)

#### Parameters

x  
The height of the region that you want to crop from the point (x, y).

<!-- -->

y  
The height of the region that you want to crop from the point (x, y).

<!-- -->

w  
The height of the region that you want to crop from the point (x, y).

<!-- -->

h  
The height of the region that you want to crop from the point (x, y).

#### Return Value

0 indicates success; otherwise, failure.

### Method displayImage

Draws an image with the device context specified by the HDC parameter.

    public int displayImage(Int64 HDC, [int Mode], [int Xpos], [int Ypos], [int Width], [int Height])

#### Parameters

HDC  
Optional parameter.

<!-- -->

Mode  
Optional parameter.

<!-- -->

Xpos  
Optional parameter.

<!-- -->

Ypos  
Optional parameter.

<!-- -->

Width  
Optional parameter.

<!-- -->

Height  
Optional parameter.

#### Return Value

0 indicates success; otherwise, failure.

### Method exportBitmap

Gets a handle for the image.

    public Int64 exportBitmap()

#### Return Value

An integer that represents the handle for the image.

#### Examples

The following example retrieves the handle for an image and then uses the handle to clone the image.

    { 
        int hdlBitmap; 
        Image img = new Image(); 
        Image img2 = new Image(); 
        img.loadImage(@'C:\MyImage.bmp'); 
        //Set hdlBitmap to handle for MyImage.bmp 
        hdlBitmap = img.exportBitmap(); 
        //Load MyImage.bmp to img2 using image handle 
        if (hdlBitmap) 
        { 
            img2.importBitmap(hdlBitmap); 
        } 
    }

### Method flip

Rotates the image 180 degrees in a vertical or horizontal direction.

    public int flip(FlipType FlipType)

#### Parameters

FlipType  
A FlipType enumeration that determines the way in which the image is flipped.

#### Return Value

0 indicates success; otherwise, failure.

#### Remarks

The possible values for the FlipType parameter are those available in the FlipType system enum:

|     |                    |                                                          |
|-----|--------------------|----------------------------------------------------------|
| 0   | RotateNoneFlipNone | No flip                                                  |
| 1   | RotateNoneFlipX    | Rotates the image 180 degrees in a horizontal direction. |
| 2   | RotateNoneFlipY    | Rotates the image 180 degrees in a vertical direction.   |

### Method getImageDimensionUnits

    public container getImageDimensionUnits()

#### Return Value

### Method getPixel

Retrieves the ARGB color value of the pixel at the point that is specified by the parameters.

    public int getPixel(int x, int y)

#### Parameters

x  
The vertical coordinate of the pixel.

<!-- -->

y  
The vertical coordinate of the pixel.

#### Return Value

An integer that is the ARGB value of the pixel (a 32-bit representation of an RGB color).

### Method height

Retrieves the height of the image in pixels.

    public int height()

#### Return Value

An integer that represents the height of the image in pixels.

#### Examples

The following example prints out the height of the image that is contained in test.bmp.

    Image img = new Image(); 
    img.loadFile(@'C:\test.bmp'); 
    print img.height(); 
    pause;

### Method imageInfo

Retrieves the width, height, and color depth of the image.

    public container imageInfo()

#### Return Value

A container that holds values that specify the width of the image, the height of the image, and the number of bits per pixel.

#### Examples

The following example prints out the width and height of the image test.bmp, and specifies the color depth in bits per pixel.

    Image img = new Image(); 
    container c; 
    img.loadFile(@'C:\Test.bmp'); 
    c = img.imageInfo(); 
    print con2str(c); 
    pause;

### Method imageSpotlight

Produces a spotlight effect within the circle that is defined by radius with center coordinates x and y.

    public int imageSpotlight(int x, int y, int radius, int smoothing, int intensity)

#### Parameters

x  
The intensity of the surrounding pixels. The possible values are between 0 and 100 (%).

<!-- -->

y  
The intensity of the surrounding pixels. The possible values are between 0 and 100 (%).

<!-- -->

radius  
The intensity of the surrounding pixels. The possible values are between 0 and 100 (%).

<!-- -->

smoothing  
The intensity of the surrounding pixels. The possible values are between 0 and 100 (%).

<!-- -->

intensity  
The intensity of the surrounding pixels. The possible values are between 0 and 100 (%).

#### Return Value

0 indicates success; otherwise, failure.

#### Remarks

The pixels within the circle are unchanged, but the other pixels in the image are darkened by reducing their intensity.

### Method importBitmap

Clones a bitmap from the image that is specified by the hBitmap parameter.

    public int importBitmap(Int64 hBitmap)

#### Parameters

hBitmap  
The handle to the image that you clone.

#### Return Value

0 indicates success; otherwise, failure.

#### Examples

The following example retrieves the handle for an image and then uses the importBitmap method to clone the image.

    { 
        int hdlBitmap; 
        Image img = new Image(); 
        Image img2 = new Image(); 
        img.loadImage(@'C:\MyImage.bmp'); 
        //Set hdlBitmap to handle for MyImage.bmp 
        hdlBitmap = img.exportBitmap(); 
        //Load MyImage.bmp to img2 using image handle 
        if (hdlBitmap) 
        { 
            img2.importBitmap(hdlBitmap); 
        } 
    }

### Method importFileIcon

Creates an icon from the file specified by the fileName parameter by copying the icon that is used for the file.

    public int importFileIcon(str fileName)

#### Parameters

fileName  
The name and the path of the file from which you create an icon.

#### Return Value

0 indicates success; otherwise, failure.

#### Examples

The following example copies the icon that is used for the file test.bmp.

    Image img = new Image(); 
    img.importFileIcon(@'C:\test.bmp'); 
    img.clipboardCopy(); 
    // Icon used for test.bmp can now be pasted into an application.

### Method importIcon

Retrieves a handle to an icon from an executable file in Microsoft Dynamics 365 for Operations. The icon is specified by the fileName and iconIdx parameters.

    public int importIcon(str fileName, int iconIdx)

#### Parameters

fileName  
The resource within the specified file.

<!-- -->

iconIdx  
The resource within the specified file.

#### Return Value

0 indicates success; otherwise, failure.

### Method loadImage

Loads an image from the file specified by the fileName parameter.

    public int loadImage(str fileName)

#### Parameters

fileName  
The resource from which you want to load the image.

#### Return Value

0 indicates success; otherwise, failure.

### Method loadResource

Loads a resource from Ax32.exe.

    public int loadResource(int id)

#### Parameters

id  
The ID of the resource that you want to load. Values of resources can be found in the Resources macro.

#### Return Value

0 indicates success; otherwise, failure.

#### Examples

The following example adds two resources to an image list.

    #Resource 
    Image img; 
    ImageList imageList; 
    imageList = new Imagelist( 
        Imagelist::smallIconWidth(), 
        Imagelist::smallIconHeight()); 
    img = new Image(); 
    img.loadResource(#RES_NODE_CLOSED); 
    imageList.add(img); 
    img = new Image(); 
    img.loadResource(#RES_NODE_OPEN); 
    imageList.add(img);

### Method promoteColor

Increases the color depth of the image.

    public int promoteColor(int noOfColorBits)

#### Parameters

noOfColorBits  
The number of bits that you want to promote the image to.

#### Return Value

0 indicates success; otherwise, failure.

#### Remarks

The method promotes:

-   8-bit images to 24 or 32 bits.
-   4-bit images to 8, 24, or 32 bits.
-   1-bit images to 4, 8, 24, or 32 bits.

#### Examples

The following example increases the color depth of an image to 8 bits per pixel, unless it is already 8 or more.

    Image img = new Image(); 
    img.loadFile(@'C:\test.bmp'); 
    if (conpeek(img.imageInfo(),3) <8) 
    { 
        img.promoteColor(8); 
    }

### Method reduceColorOctree

Reduces the color depth of an image.

    public int reduceColorOctree(int maxColors)

#### Parameters

maxColors  
The maximum number of colors.

#### Return Value

0 indicates success; otherwise, failure.

#### Remarks

The method reduces a 24-bit image to 8 bits, or an 8-bit image to 4 bits, unless other instructions are specified in the maxColors parameter. If the maxColors parameter is less than or equal to 16, a 4-bit image is produced. If maxColors is more than 16, an 8-bit image is produced.

### Method removeImage

Removes the data about an image; the object still exists, but has no data.

    public int removeImage()

#### Return Value

0 indicates success; otherwise, failure.

### Method resize

Resizes the image to the size that is specified by the newWidth and newHeight parameters.

    public int resize(int newWidth, int newHeight, InterpolationMode InterpolationMode)

#### Parameters

newWidth  
The resizing method.

<!-- -->

newHeight  
The resizing method.

<!-- -->

InterpolationMode  
The resizing method.

#### Return Value

0 indicates success; otherwise, failure.

#### Remarks

The possible values for the InterpolationMode parameter are those available in the InterpolationMode system enum:

|     |                                      |                                                                                                                                                                        |
|-----|--------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 0   | InterpolationModeDefault             | Specifies the default interpolation mode.                                                                                                                              |
| 1   | InterpolationModeLowQuality          | Specifies a low-quality mode.                                                                                                                                          |
| 2   | InterpolationModeHighQuality         | Specifies a high-quality mode.                                                                                                                                         |
| 3   | InterpolationModeBilinear            | Specifies bilinear interpolation. No pre-filtering is done. This method is not suitable for shrinking an image below 50% of its original size.                         |
| 4   | InterpolationModeBicubic             | Specifies bicubic interpolation. No pre-filtering is done. This method is not suitable for shrinking an image below 25% of its original size.                          |
| 5   | InterpolationModeNearestNeighbor     | Specifies nearest-neighbor interpolation.                                                                                                                              |
| 6   | InterpolationModeHighQualityBilinear | Specifies high-quality, bilinear interpolation. Pre-filtering is performed to ensure high-quality shrinking.                                                           |
| 7   | InterpolationModeHighQualityBicubic  | Specifies high-quality, bicubic interpolation. Pre-filtering is performed to ensure high-quality shrinking. This mode produces the highest quality transformed images. |

### Method rotate

Rotates the image.

    public int rotate(RotateType RotateType)

#### Parameters

RotateType  
The amount to rotate the image by.

#### Return Value

0 indicates success; otherwise, failure.

#### Remarks

The possible values for the RotateType parameter are those available in the RotateType system enum:

|     |                    |                          |
|-----|--------------------|--------------------------|
| 0   | RotateNoneFlipNone | No rotation.             |
| 1   | Rotate90FlipNone   | Rotation by 90 degrees.  |
| 2   | Rotate180FlipNone  | Rotation by 180 degrees. |
| 3   | Rotate270FlipNone  | Rotation by 270 degrees. |

### Method saveImage

Saves the image to the specified file name.

    public int saveImage(str fileName, [ImageSaveType Type])

#### Parameters

fileName  
An ImageSaveType that enables you to specify that the file should be saved as a different format from that specified by the file extension; optional.

<!-- -->

Type  
An ImageSaveType that enables you to specify that the file should be saved as a different format from that specified by the file extension; optional.

#### Return Value

0 if the method was successful.

#### Remarks

The possible values for the Type parameter are those available in the ImageSaveType system enum. For example, you could save test.bmp as a .jpg file.

|     |                |
|-----|----------------|
| 0   | Use\_Extension |
| 1   | BMP            |
| 2   | GIF            |
| 3   | JPG            |
| 4   | PNG            |
| 5   | TIFF           |
| 6   | BMP\_UNCOMP    |
| 7   | TIF\_UNCOMP    |

#### Examples

The following example captures part of the screen to a file, and then loads that image.

    Image img = new Image(); 
    img.captureScreen(0, 0, 100, 100); 
    img.saveImage(@'C:\test.bmp'); 
    img.loadFile(@'C:\test.bmp');

### Method saveType

Gets or sets the image decoder.

    public ImageSaveType saveType([ImageSaveType Type])

#### Parameters

Type  
The type of decoder that you want to set; optional.

#### Return Value

#### Remarks

The possible values for the Type parameter are those available in the ImageSaveType system enum:

|     |                |
|-----|----------------|
| 0   | Use\_Extension |
| 1   | BMP            |
| 2   | GIF            |
| 3   | JPG            |
| 4   | PNG            |
| 5   | TIFF           |
| 6   | BMP\_UNCOMP    |
| 7   | TIF\_UNCOMP    |

### Method setPixel

Sets the color for the pixel that is specified by the x and y parameters.

    public int setPixel(int x, int y, int pixel)

#### Parameters

x  
The ARGB value of the color that you want to use.

<!-- -->

y  
The ARGB value of the color that you want to use.

<!-- -->

pixel  
The ARGB value of the color that you want to use.

#### Return Value

0 indicates success; otherwise, failure.

#### Remarks

To convert an RGB color value to an ARGB value, use the Image::rgb Method.

### Method transparent

Sets the transparent color for the image.

    public int transparent([boolean Set], [int RValue], [int GValue], [int BValue])

#### Parameters

Set  
Blue value of the color that you want to set; optional.

<!-- -->

RValue  
Blue value of the color that you want to set; optional.

<!-- -->

GValue  
Blue value of the color that you want to set; optional.

<!-- -->

BValue  
Blue value of the color that you want to set; optional.

#### Return Value

0 to indicate success; otherwise, failure.

#### Remarks

If any of the input parameters are missing, the color at the point (0,0) in the image is used. If you want to specify a color, this is expressed as an RGB color by using parameters 2 to 4.

### Method width

Retrieves the width of the image in pixels.

    public int width()

#### Return Value

An integer that represents the width of the image in pixels.

#### Examples

The following example prints out the width of the image in the test.bmp file.

    Image img = new Image(); 
    img.loadFile(@'C:\test.bmp'); 
    print img.width(); 
    pause;

### Method canLoad

Determines whether an image file exists and can be opened.

    public static int canLoad(str filename)

#### Parameters

filename  
The name and path of the file to check.

#### Return Value

1 if the image is found and can be opened; otherwise, 0.

### Method loadExt

Retrieves a list of the extensions of the file formats that are supported by the Image class.

    public static container loadExt(int idx)

#### Parameters

idx  

#### Return Value

A container that holds a list of the supported file formats.

### Method resourceType

Determines whether a particular resource is a bitmap or an icon.

    public static int resourceType(int resourceIdx)

#### Parameters

resourceIdx  
The ID of the resource that you want to load.

#### Return Value

0 if the image is a bitmap; 1 if it is an icon.

#### Remarks

The values of resources can be found in the Resources macro.

#### Examples

The following example tests whether resource 3020 is an icon or a bitmap.

    #Resource 
    print Image::resourceType(3020); 
    pause;

### Method rgb

Converts an RGB value to an ARGB value.

    public static int rgb(int R, int G, int B)

#### Parameters

R  
The blue value of the color.

<!-- -->

G  
The blue value of the color.

<!-- -->

B  
The blue value of the color.

#### Return Value

An integer that represents the ARGB value of the color that is specified by the parameters.

### Method validResource

Determines whether the resource specified by the id parameter is valid.

    public static int validResource(int id)

#### Parameters

id  
The ID of the resource that you want to check.

#### Return Value

0 if the ID is valid.

### Method new

Creates a new image.

    public void new([AnyType image], [int width], [int height])

#### Parameters

image  
The height of the image in pixels; optional.

<!-- -->

width  
The height of the image in pixels; optional.

<!-- -->

height  
The height of the image in pixels; optional.

#### Remarks

You do not need to specify any parameters, but it is possible to specify the image contents and size. For the image parameter, you can specify a file name and location, a resource, a particular image in an array, or another Image object.

#### Examples

The following examples illustrate how you can optionally specify the existing content for the new image object.

    Image img1 = new Image(@"C:\MyPicture.jpg", 100, 100); 
    Image img2 = new Image(121,100, 100); // Uses resource 121 in Ax32.exe 
    Image img4 = new Image(img1, 200, 200);

### Method displayOrign

Enables you to specify an offset (X, Y) from the original origin (0, 0).

    public void displayOrign(int Xpos, int Ypos)

#### Parameters

Xpos  
New Y (vertical) coordinate for the origin.

<!-- -->

Ypos  
New Y (vertical) coordinate for the origin.

### Method finalize

    public void finalize()

## Class Imagelist
    class Imagelist extends BinData

The Imagelist class lets you work with a list of images.

### Remarks

To work with a single image, use the Image class.

### Examples

The following example creates an image list and adds the icons in the Shell32.dll file. It then deletes the fourth member of the list.

    Imagelist list = new Imagelist( 
        Imagelist::iconWidth(), 
        Imagelist::iconHeight() ); 
    list.loadIcons('shell32.dll'); 
    print list.count(); 
    list.remove(4); 
    print list.count(); 
    pause;

### Methods

| Method                                                                         | Description                                                                                                                        |
|--------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------|
| public int add(Image image)                                                    | Adds a new image to the image list.                                                                                                |
| public boolean autoResize(\[boolean value\])                                   | Sets the Boolean autoResize flag, which determines whether new images are automatically resized.                                   |
| public int clear()                                                             | Removes all images from the image list.                                                                                            |
| public int count()                                                             | Retrieves the number of images in an image list.                                                                                   |
| public boolean dragBegin(int imageIdx, int hotSpotX, int hotSpotY)             | Begins dragging an image.                                                                                                          |
| public boolean dragEnd()                                                       | Ends a drag operation.                                                                                                             |
| public boolean dragEnter(int hWnd, int x, int y)                               | Locks updates to the specified window during a drag operation and displays the drag image at the specified position in the window. |
| public boolean dragLeave(int hWnd)                                             | Unlocks the specified window and hides the drag image, so that the window to be updated.                                           |
| public boolean dragMove(int x, int y)                                          | Moves the image that is being dragged during a drag-and-drop operation.                                                            |
| public boolean dragShowImage(boolean show)                                     | Shows or hides the image that is being dragged.                                                                                    |
| public int height()                                                            | Retrieves the height, in pixels, of the images in the image list.                                                                  |
| public int loadIcons(str moduleName)                                           | Loads icons from the specified resource into the image list.                                                                       |
| public int remove(int imageIdx)                                                | Removes an image from an image list.                                                                                               |
| public int replace(int imageIdx, Image image)                                  | Replaces an existing image in the list.                                                                                            |
| public boolean setOverlayImage(int imageIdx, int overlayIdx)                   | Adds an image to the list of images to use as overlay masks.                                                                       |
| public int width()                                                             | Retrieves the width, in pixels, of the images in the image list.                                                                   |
| ::public static int iconHeight()                                               | Retrieves the system metrics for the height of a standard icon.                                                                    |
| ::public static int iconWidth()                                                | Retrieves the system metrics for the width of a standard icon.                                                                     |
| ::public static int smallIconHeight()                                          | Retrieves the system metrics for the height of a small icon.                                                                       |
| ::public static int smallIconWidth()                                           | Retrieves the system metrics for the width of a small icon.                                                                        |
| public void maskColor(int Color)                                               | Sets the masking color.                                                                                                            |
| public void draw(int HDC, int imageIdx, int x, int y, \[boolean transparent\]) | Draws an image list item in the specified device context.                                                                          |
| public void finalize()                                                         |                                                                                                                                    |
| public void new(int cx, int cy, \[boolean transparent\])                       | Creates a new empty list to hold images.                                                                                           |

### Method add

Adds a new image to the image list.

    public int add(Image image)

#### Parameters

image  
The new image to add to the list.

#### Return Value

0 if the method is successful.

#### Remarks

You can use the autoResize method to automatically resize images when you add them to the list.

#### Examples

The following example creates a new image list and adds three images to it.

    ImageList list = new Imagelist( 
        Imagelist::smallIconWidth(), 
        Imagelist::smallIconHeight()); 
    list.add(new Image(3104)); 
    list.add(new Image(1097)); 
    list.add(new Image(1200)); 
    // Prints 3 
    print list.count(); 
    pause;

### Method autoResize

Sets the Boolean autoResize flag, which determines whether new images are automatically resized.

    public boolean autoResize([boolean value])

#### Parameters

value  
A Boolean value that determines whether the autoResize flag is set; optional.

#### Return Value

#### Remarks

If the autoResize flag is set to true, any image that you add to the list is automatically resized to the dimensions that were specified when you created the image list.

### Method clear

Removes all images from the image list.

    public int clear()

#### Return Value

0 if the method is successful.

### Method count

Retrieves the number of images in an image list.

    public int count()

#### Return Value

An integer that represents the number of images in the list.

#### Examples

The following example creates an image list, loads icons from the shell.dll file, and then prints the number of images in the list.

    Imagelist list; 
    int       counter; 
    list = new Imagelist( 
       Imagelist::iconWidth(), 
       Imagelist::iconHeight() ); 
    list.loadIcons('shell32.dll'); 
    print list.count(); 
    pause;

### Method dragBegin

Begins dragging an image.

    public boolean dragBegin(int imageIdx, int hotSpotX, int hotSpotY)

#### Parameters

imageIdx  
The Y-coordinate of the drag position, relative to the upper-left corner of the image.

<!-- -->

hotSpotX  
The Y-coordinate of the drag position, relative to the upper-left corner of the image.

<!-- -->

hotSpotY  
The Y-coordinate of the drag position, relative to the upper-left corner of the image.

#### Return Value

1 if the method is successful.

#### Remarks

The rest of the drag operation is specified by the dragEnter, dragMove, dragLeave, and dragEnd methods.

### Method dragEnd

Ends a drag operation.

    public boolean dragEnd()

#### Return Value

1 if the method is successful; otherwise, 0.

#### Remarks

The rest of the drag operation is specified by the dragBegin, dragEnter, dragMove, and dragLeave methods.

### Method dragEnter

Locks updates to the specified window during a drag operation and displays the drag image at the specified position in the window.

    public boolean dragEnter(int hWnd, int x, int y)

#### Parameters

hWnd  
The Y-coordinate at which to display the drag icon, relative to the upper-left corner of the window.

<!-- -->

x  
The Y-coordinate at which to display the drag icon, relative to the upper-left corner of the window.

<!-- -->

y  
The Y-coordinate at which to display the drag icon, relative to the upper-left corner of the window.

#### Return Value

1 if the method is successful; otherwise, 0.

#### Remarks

To start the drag operation, call the dragBegin method. The rest of the drag operation is specified by the dragMove, dragLeave, and dragEnd methods.

### Method dragLeave

Unlocks the specified window and hides the drag image, so that the window to be updated.

    public boolean dragLeave(int hWnd)

#### Parameters

hWnd  
The handle to the window that owns the drag image.

#### Return Value

1 if the method is successful; otherwise, 0.

#### Remarks

The rest of the drag operation is specified by the dragBegin, dragEnter, dragMove, and dragEnd methods.

### Method dragMove

Moves the image that is being dragged during a drag-and-drop operation.

    public boolean dragMove(int x, int y)

#### Parameters

x  
The Y-coordinate at which to display the drag icon, relative to the upper-left corner of the window.

<!-- -->

y  
The Y-coordinate at which to display the drag icon, relative to the upper-left corner of the window.

#### Return Value

1 if the method is successful; otherwise, 0.

#### Remarks

To start the drag operation, call the dragBegin method and then the dragEnter method. The rest of the drag operation is specified by the dragLeave and dragEnd methods.

### Method dragShowImage

Shows or hides the image that is being dragged.

    public boolean dragShowImage(boolean show)

#### Parameters

show  
A value that specifies whether to show the image.

#### Return Value

### Method height

Retrieves the height, in pixels, of the images in the image list.

    public int height()

#### Return Value

An integer that represents the height of the images in pixels.

#### Remarks

The height of the images in the list is set when you instantiate the list.

#### Examples

The following example creates an image list, and sets the height and width of the images to the dimensions that are specified by the iconWidth and iconHeight methods. It then prints the height of images in the list.

    Imagelist list; 
    list = new Imagelist( 
        Imagelist::iconWidth(), 
        Imagelist::iconHeight()); 
    print list.height();   
    pause;

### Method loadIcons

Loads icons from the specified resource into the image list.

    public int loadIcons(str moduleName)

#### Parameters

moduleName  
The name of the file from which to load images.

#### Return Value

0 if the method is successful.

#### Examples

The following example creates a list of images and then loads the images that are contained in the shell32.dll file.

    Imagelist list; 
    list = new Imagelist(Imagelist::iconWidth(),Imagelist::iconHeight()); 
    list.loadIcons('shell32.dll');

### Method remove

Removes an image from an image list.

    public int remove(int imageIdx)

#### Parameters

imageIdx  
The position of the image to remove from the list.

#### Return Value

0 if the method is successful.

#### Examples

The following example creates an image list, adds the icons in shell32.dll file, and then deletes the fourth member of the list.

    Imagelist list = new Imagelist( 
        Imagelist::iconWidth(), 
        Imagelist::iconHeight() ); 
    list.loadIcons('shell32.dll'); 
    print list.count(); 
    list.remove(4); 
    print list.count(); 
    pause;

### Method replace

Replaces an existing image in the list.

    public int replace(int imageIdx, Image image)

#### Parameters

imageIdx  
The image to use to replace the existing image.

<!-- -->

image  
The image to use to replace the existing image.

#### Return Value

0 if the method is successful.

### Method setOverlayImage

Adds an image to the list of images to use as overlay masks.

    public boolean setOverlayImage(int imageIdx, int overlayIdx)

#### Parameters

imageIdx  
The one-based index of the overlay mask.

<!-- -->

overlayIdx  
The one-based index of the overlay mask.

#### Return Value

1 if the method is successful.

#### Examples

The following example creates an image list that has three images and then sets the last image as an overlay mask.

    Imagelist list = new Imagelist( 
        Imagelist::iconWidth(), 
        Imagelist::iconHeight() ); 
    list.add(new Image(824)); // Image 0 
    list.add(new Image(815)); // Image 1 
    list.add(new Image(936)); //Image 2 
    list.setOverlayImage (2,1);

### Method width

Retrieves the width, in pixels, of the images in the image list.

    public int width()

#### Return Value

An integer that represents the width of the images in pixels.

#### Remarks

The width of the images in the list is set when you instantiate the list.

#### Examples

The following example creates an image list that has the standard height and width for icons, and then prints the width of images in the list.

    Imagelist list; 
    list = new Imagelist( 
        Imagelist::iconWidth(), 
        Imagelist::iconHeight()); 
    print list.width();   
    pause;

### Method iconHeight

Retrieves the system metrics for the height of a standard icon.

    public static int iconHeight()

#### Return Value

An integer that represents the height of a standard icon.

#### Examples

The following example creates a list of images, and then sets them to the standard icon width and height.

    ImageList list = new Imagelist( 
        Imagelist::iconWidth(), 
        Imagelist::iconHeight());

### Method iconWidth

Retrieves the system metrics for the width of a standard icon.

    public static int iconWidth()

#### Return Value

An integer that represents the width of a standard icon.

#### Examples

The following example creates a list of images, and then sets them to the standard icon width and height.

    ImageList list = new Imagelist( 
        Imagelist::iconWidth(), 
        Imagelist::iconHeight());

### Method smallIconHeight

Retrieves the system metrics for the height of a small icon.

    public static int smallIconHeight()

#### Return Value

An integer that represents the height of a small icon.

#### Examples

The following example creates an image list that has the standard height and width for small icons, and then prints the height of images in the list.

    Imagelist list = new Imagelist( 
        Imagelist::smallIconWidth(), 
        Imagelist::smallIconHeight()); 
    print list.height();   
    pause;

### Method smallIconWidth

Retrieves the system metrics for the width of a small icon.

    public static int smallIconWidth()

#### Return Value

An integer that represents the width of a small icon.

#### Examples

The following example creates an image list that has the standard height and width for small icons, and then prints the width of images in the list.

    Imagelist list = new Imagelist( 
       Imagelist::smallIconWidth(), 
       Imagelist::smallIconHeight()); 
    print list.width();   
    pause;

### Method maskColor

Sets the masking color.

    public void maskColor(int Color)

#### Parameters

Color  
The color as an ARGB value.

### Method draw

Draws an image list item in the specified device context.

    public void draw(int HDC, int imageIdx, int x, int y, [boolean transparent])

#### Parameters

HDC  
A Boolean value that indicates whether the image is drawn transparently by using the mask, regardless of background color; optional.

<!-- -->

imageIdx  
A Boolean value that indicates whether the image is drawn transparently by using the mask, regardless of background color; optional.

<!-- -->

x  
A Boolean value that indicates whether the image is drawn transparently by using the mask, regardless of background color; optional.

<!-- -->

y  
A Boolean value that indicates whether the image is drawn transparently by using the mask, regardless of background color; optional.

<!-- -->

transparent  
A Boolean value that indicates whether the image is drawn transparently by using the mask, regardless of background color; optional.

### Method finalize

    public void finalize()

### Method new

Creates a new empty list to hold images.

    public void new(int cx, int cy, [boolean transparent])

#### Parameters

cx  

<!-- -->

cy  

<!-- -->

transparent  

#### Remarks

You can use the autoResize method to automatically resize images when you add them to the list.

#### Examples

The following example creates an image list to hold items of the standard icon width and height.

    Imagelist list; 
    list = new Imagelist( 
       Imagelist::iconWidth(), 
       Imagelist::iconHeight());

## Class ImportTableDataInfo
    class ImportTableDataInfo extends Object

### Remarks

### Examples

### Methods

| Method                                                  | Description                                     |
|---------------------------------------------------------|-------------------------------------------------|
| public int addColumnData(str szColName, AnyType colVal) |                                                 |
| public int copyDataRow()                                |                                                 |
| public void new(int usTableId)                          | Initializes a new instance of the Object class. |

### Method addColumnData

    public int addColumnData(str szColName, AnyType colVal)

#### Parameters

szColName  

<!-- -->

colVal  

#### Return Value

### Method copyDataRow

    public int copyDataRow()

#### Return Value

### Method new

Initializes a new instance of the Object class.

    public void new(int usTableId)

#### Parameters

usTableId  

## Class ImportTableSchemaInfo
    class ImportTableSchemaInfo extends Object

### Remarks

### Examples

### Methods

| Method                                                                             | Description                                     |
|------------------------------------------------------------------------------------|-------------------------------------------------|
| public int addColumnInfo(str szColName, Types eColType, int eColRole, int lColOrd) |                                                 |
| public int addColumnMapping(str szRefRecIdColName, str szRefTableIdColName)        |                                                 |
| public int hasEqualityCriteria(boolean fHasEqualityCriteria)                       |                                                 |
| public int shreddedMetadataTable(boolean fIsShreddedMetadataTable)                 |                                                 |
| public void new(int usTableId)                                                     | Initializes a new instance of the Object class. |

### Method addColumnInfo

    public int addColumnInfo(str szColName, Types eColType, int eColRole, int lColOrd)

#### Parameters

szColName  

<!-- -->

eColType  

<!-- -->

eColRole  

<!-- -->

lColOrd  

#### Return Value

### Method addColumnMapping

    public int addColumnMapping(str szRefRecIdColName, str szRefTableIdColName)

#### Parameters

szRefRecIdColName  

<!-- -->

szRefTableIdColName  

#### Return Value

### Method hasEqualityCriteria

    public int hasEqualityCriteria(boolean fHasEqualityCriteria)

#### Parameters

fHasEqualityCriteria  

#### Return Value

### Method shreddedMetadataTable

    public int shreddedMetadataTable(boolean fIsShreddedMetadataTable)

#### Parameters

fIsShreddedMetadataTable  

#### Return Value

### Method new

Initializes a new instance of the Object class.

    public void new(int usTableId)

#### Parameters

usTableId  

## Class InfoPart
    class InfoPart extends TreeNode

### Remarks

### Examples

### Methods

| Method                                   | Description                                                                                                                               |
|------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public str caption(\[str value\])        | Gets or set the caption of the control.                                                                                                   |
| public str changedBy(\[str value\])      | Gets or sets the name of the user who last changed the application object.                                                                |
| public Date changedDate(\[Date value\])  | Gets or sets the date an application object was last changed.                                                                             |
| public str changedTime(\[str value\])    | Gets or sets the time an application object was last changed.                                                                             |
| public str createdBy(\[str value\])      | Gets or sets the name of the user who created the application object.                                                                     |
| public Date creationDate(\[Date value\]) | Gets or sets the date an application object was created.                                                                                  |
| public str creationTime(\[str value\])   |                                                                                                                                           |
| public str name(\[str value\])           | Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics 365 for Operations application object. |
| public Guid origin(\[Guid value\])       |                                                                                                                                           |
| public str query(\[str value\])          |                                                                                                                                           |
| public void new()                        | Initializes a new instance of the InfoPart class.                                                                                         |

### Method caption

Gets or set the caption of the control.

    public str caption([str value])

#### Parameters

value  

#### Return Value

The string that is used as the caption of the control.

### Method changedBy

Gets or sets the name of the user who last changed the application object.

    public str changedBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method changedDate

Gets or sets the date an application object was last changed.

    public Date changedDate([Date value])

#### Parameters

value  

#### Return Value

The date an application object was last changed.

### Method changedTime

Gets or sets the time an application object was last changed.

    public str changedTime([str value])

#### Parameters

value  

#### Return Value

The time an application object was last changed.

### Method createdBy

Gets or sets the name of the user who created the application object.

    public str createdBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method creationDate

Gets or sets the date an application object was created.

    public Date creationDate([Date value])

#### Parameters

value  

#### Return Value

The date an application object was created.

### Method creationTime

    public str creationTime([str value])

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
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

### Method origin

    public Guid origin([Guid value])

#### Parameters

value  

#### Return Value

### Method query

    public str query([str value])

#### Parameters

value  

#### Return Value

### Method new

Initializes a new instance of the InfoPart class.

    public void new()

## Class InfoPartField
    class InfoPartField extends TreeNode

### Remarks

### Examples

### Methods

| Method                                            | Description                                                                                                                               |
|---------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public str dataField(\[str value\])               |                                                                                                                                           |
| public str dataMethod(\[str value\])              |                                                                                                                                           |
| public str dataSource(\[str value\])              | Gets or sets a data source that will be used by the control or the form.                                                                  |
| public str label(\[str value\])                   | Gets or sets the label for a control.                                                                                                     |
| public boolean manualRetrieval(\[boolean value\]) |                                                                                                                                           |
| public str name(\[str value\])                    | Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics 365 for Operations application object. |
| public int style(\[int value\])                   |                                                                                                                                           |
| public void new()                                 | Initializes a new instance of the InfoPartField class.                                                                                    |

### Method dataField

    public str dataField([str value])

#### Parameters

value  

#### Return Value

### Method dataMethod

    public str dataMethod([str value])

#### Parameters

value  

#### Return Value

### Method dataSource

Gets or sets a data source that will be used by the control or the form.

    public str dataSource([str value])

#### Parameters

value  

#### Return Value

The identifier of the data source that will be used.

### Method label

Gets or sets the label for a control.

    public str label([str value])

#### Parameters

value  

#### Return Value

The current value of the label string.

#### Remarks

The label determines which text is displayed in the control or adjacent to it. The label property value cannot exceed 250 characters.

### Method manualRetrieval

    public boolean manualRetrieval([boolean value])

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
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

### Method style

    public int style([int value])

#### Parameters

value  

#### Return Value

### Method new

Initializes a new instance of the InfoPartField class.

    public void new()

## Class InfoPartGroup
    class InfoPartGroup extends TreeNode

### Remarks

### Examples

### Methods

| Method                                                         | Description                                                                                                                                   |
|----------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| public str caption(\[str value\])                              | Gets or sets the caption of the control.                                                                                                      |
| public str dataGroup(\[str value\])                            |                                                                                                                                               |
| public str dataSource(\[str value\])                           | Gets or sets a data source that will be used by the control or the form.                                                                      |
| public int labelPosition(\[int value\])                        |                                                                                                                                               |
| public str name(\[str value\])                                 | Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics 365 for Operations application object. |
| public boolean repeating(\[boolean value\])                    |                                                                                                                                               |
| public int rowCountWhenSmall(\[int value\], \[AutoMode mode\]) |                                                                                                                                               |
| public AutoMode rowCountWhenSmallMode(\[AutoMode mode\])       |                                                                                                                                               |
| public int rowCountWhenSmallValue(\[int value\])               |                                                                                                                                               |
| public boolean showCaption(\[boolean value\])                  |                                                                                                                                               |
| public boolean showLabels(\[boolean value\])                   |                                                                                                                                               |
| public int showWhenPartSize(\[int value\])                     |                                                                                                                                               |
| public boolean verticalSpacing(\[boolean value\])              |                                                                                                                                               |
| public void new()                                              | Initializes a new instance of the InfoPartGroup class.                                                                                        |

### Method caption

Gets or sets the caption of the control.

    public str caption([str value])

#### Parameters

value  

#### Return Value

The string that is used as the caption of the control.

### Method dataGroup

    public str dataGroup([str value])

#### Parameters

value  

#### Return Value

### Method dataSource

Gets or sets a data source that will be used by the control or the form.

    public str dataSource([str value])

#### Parameters

value  

#### Return Value

The identifier of the data source that will be used.

### Method labelPosition

    public int labelPosition([int value])

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

### Method repeating

    public boolean repeating([boolean value])

#### Parameters

value  

#### Return Value

### Method rowCountWhenSmall

    public int rowCountWhenSmall([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method rowCountWhenSmallMode

    public AutoMode rowCountWhenSmallMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method rowCountWhenSmallValue

    public int rowCountWhenSmallValue([int value])

#### Parameters

value  

#### Return Value

### Method showCaption

    public boolean showCaption([boolean value])

#### Parameters

value  

#### Return Value

### Method showLabels

    public boolean showLabels([boolean value])

#### Parameters

value  

#### Return Value

### Method showWhenPartSize

    public int showWhenPartSize([int value])

#### Parameters

value  

#### Return Value

### Method verticalSpacing

    public boolean verticalSpacing([boolean value])

#### Parameters

value  

#### Return Value

### Method new

Initializes a new instance of the InfoPartGroup class.

    public void new()

## Class InfoPartLayout
    class InfoPartLayout extends TreeNode

### Remarks

### Examples

### Methods

| Method                                       | Description                                             |
|----------------------------------------------|---------------------------------------------------------|
| public boolean showMore(\[boolean value\])   |                                                         |
| public str showMoreDataSource(\[str value\]) |                                                         |
| public void new()                            | Initializes a new instance of the InfoPartLayout class. |

### Method showMore

    public boolean showMore([boolean value])

#### Parameters

value  

#### Return Value

### Method showMoreDataSource

    public str showMoreDataSource([str value])

#### Parameters

value  

#### Return Value

### Method new

Initializes a new instance of the InfoPartLayout class.

    public void new()

## Class InitialQueryParameter
    class InitialQueryParameter extends Object

### Remarks

### Examples

### Methods

| Method                                                                                                       | Description                                                    |
|--------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|
| public boolean applyQuery(FormDataSource datasource)                                                         |                                                                |
| public str dataSourceName(\[str dataSourceName\])                                                            |                                                                |
| public str modeledQueryName(\[str modeledQueryName\])                                                        |                                                                |
| public Query query(\[Query query\])                                                                          |                                                                |
| ::public static InitialQueryParameter createByModeledQueryName(str modeledQueryName, \[str dataSourceName\]) |                                                                |
| ::public static InitialQueryParameter createByQuery(Query query, \[str dataSourceName\])                     |                                                                |
| public void finalize()                                                                                       |                                                                |
| public void new()                                                                                            | Initializes a new instance of the InitialQueryParameter class. |

### Method applyQuery

    public boolean applyQuery(FormDataSource datasource)

#### Parameters

datasource  

#### Return Value

### Method dataSourceName

    public str dataSourceName([str dataSourceName])

#### Parameters

dataSourceName  

#### Return Value

### Method modeledQueryName

    public str modeledQueryName([str modeledQueryName])

#### Parameters

modeledQueryName  

#### Return Value

### Method query

    public Query query([Query query])

#### Parameters

query  

#### Return Value

### Method createByModeledQueryName

    public static InitialQueryParameter createByModeledQueryName(str modeledQueryName, [str dataSourceName])

#### Parameters

modeledQueryName  

<!-- -->

dataSourceName  

#### Return Value

### Method createByQuery

    public static InitialQueryParameter createByQuery(Query query, [str dataSourceName])

#### Parameters

query  

<!-- -->

dataSourceName  

#### Return Value

### Method finalize

    public void finalize()

### Method new

Initializes a new instance of the InitialQueryParameter class.

    public void new()

## Class InteropPermission
    class InteropPermission extends CodeAccessPermission

The InteropPermission class controls the ability to call unmanaged and managed code.

### Remarks

The InteropPermission class is designed to check permissions for specific APIs. For a list of all APIs that are protected by permissions, see Secured APIs. Before the protected API is run, you must call the assert method on the same tier (usually the server tier) that the corresponding CodeAccessPermission::demand method is called on. Call a method on the server tier from one of the following methods:

-   A server static method
-   A class instance method that is set to run on the server by using the RunOn class property.

### Examples

The following code example shows a new instance of the InteropPermission class. The assert method is called to declare that the code can then instantiate the DLL class that provides the ability to communicate with a MicrosoftWindows dynamic-link library (DLL).

    server static void main(Args args) 
    { 
        InteropPermission _perm; 
        DLL _dll; 
        _perm = new InteropPermission(InteropKind::DllInterop); 
        _perm.assert(); 
        // Invoke the protected API. 
        _dll = new DLL('cfx2032.dll'); 
        // Optionally, call revertAssert() to limit the scope of assert. 
        CodeAccessPermission::revertAssert(); 
    }

### Methods

| Method                                                 | Description                                                                        |
|--------------------------------------------------------|------------------------------------------------------------------------------------|
| public CodeAccessPermission copy()                     | Creates and returns a copy of the current permission class object.                 |
| public boolean isSubsetOf(CodeAccessPermission target) | Determines whether the current permission is a subset of the specified permission. |
| public void new(InteropKind kind)                      | Creates an new instance of the InteropPermission class.                            |

### Method copy

Creates and returns a copy of the current permission class object.

    public CodeAccessPermission copy()

#### Return Value

A copy of the current permission object.

#### Remarks

You override this method when you derive a class from the CodeAccessPermission class. For more information, see the copy method.

### Method isSubsetOf

Determines whether the current permission is a subset of the specified permission.

    public boolean isSubsetOf(CodeAccessPermission target)

#### Parameters

target  
A CodeAccessPermission class object.

#### Return Value

true if the current permission is a subset of the specified permission; otherwise, false.

#### Remarks

You override this method when you derive a class from the CodeAccessPermission class. For more information, see the isSubsetOf method.

### Method new

Creates an new instance of the InteropPermission class.

    public void new(InteropKind kind)

#### Parameters

kind  
An InteropKind system enumeration value that specifies access to managed or unmanaged code.

#### Examples

The following code example shows a new instance of the InteropPermission class that specifies access to Win32 DLLs.

    server static void main(Args args) 
    { 
        InteropPermission _perm; 
        _perm = new InteropPermission(InteropKind::DllInterop); 
    }

## Class Io
    class Io extends Object

The Io class serves as the base class for the format-specific Io classes, which are used to access external files.

### Remarks

The basic Io class features no actual data I/O but works as base class for the format-specific Io classes. The methods that are common to all Io classes are described here. For format-specific features and behavior of the member functions, refer to the documentation for each of the I/O classes. To support reading and writing of different formats of external files, MorphX features a range of different Io classesfor comma-separated files, for comma-separated 7 bit files, for binary files, and for plain-text files.

### Examples

### Methods

| Method                                       | Description                                                                                                                  |
|----------------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
| public str inFieldDelimiter(\[str value\])   | Determines the delimiter used to separate fields in records accessed by the \*Io classes.                                    |
| public str inRecordDelimiter(\[str value\])  | Determines to the \*Io classes what character or characters to search for to determine whether a full record has been read.  |
| public int inRecordLength(\[int value\])     | Gets or sets the number of characters to read for each record in a file.                                                     |
| public str outFieldDelimiter(\[str value\])  | Gets or sets the sequence of characters that are written to a file that is used to separate the fields of a record.          |
| public str outRecordDelimiter(\[str value\]) | Gets or sets the sequence of characters that is written to the output files, which separate the records in the output files. |
| public container read()                      | Reads the next full record from the Io object.                                                                               |
| public IO\_Status status()                   | Retrieves the status of the last operation performed on the Io object.                                                       |
| public boolean write(VarArg values)          | Writes values of a simple type.                                                                                              |
| public boolean writeExp(container data)      | Writes the content of a container to the file.                                                                               |
| public void finalize()                       | Closes the file and, if data was written, flushes the file buffers to disk.                                                  |
| public void new(str filename, str mode)      | Creates a new instance of the Io class.                                                                                      |

### Method inFieldDelimiter

Determines the delimiter used to separate fields in records accessed by the \*Io classes.

    public str inFieldDelimiter([str value])

#### Parameters

value  

#### Return Value

The delimiter used to separate fields in records accessed by the \*Io classes.

### Method inRecordDelimiter

Determines to the \*Io classes what character or characters to search for to determine whether a full record has been read.

    public str inRecordDelimiter([str value])

#### Parameters

value  

#### Return Value

The character or characters that indicate whether a full record has been read.

#### Remarks

For standard text, the delimiter is a newline character.

### Method inRecordLength

Gets or sets the number of characters to read for each record in a file.

    public int inRecordLength([int value])

#### Parameters

value  

#### Return Value

The number of characters to read for each record in the file.

#### Remarks

For files that have a fixed-length format, use the inRecordLength property to guarantee that no more than the specified number of characters are read for each record. If the record format is overruled by a specified inRecordDelimiter property value , that is the inRecordDelimiter value is met before the fixed length is read, the record is accepted, and no additional data is read. To guarantee that a fixed number of characters are read, set the inRecordDelimiter property value to an empty string. When no inRecordDelimiter property value is found, the inRecordDelimiter property value is the maximum limit of characters to read. Set the inRecordDelimiter property value to zero to disable the record length check.

### Method outFieldDelimiter

Gets or sets the sequence of characters that are written to a file that is used to separate the fields of a record.

    public str outFieldDelimiter([str value])

#### Parameters

value  

#### Return Value

The sequence of characters that are written to a file that is used to separate the fields of a record.

### Method outRecordDelimiter

Gets or sets the sequence of characters that is written to the output files, which separate the records in the output files.

    public str outRecordDelimiter([str value])

#### Parameters

value  

#### Return Value

The sequence of characters that is written to the output files.

#### Remarks

For standard text files, the delimiter is a newline character.

### Method read

Reads the next full record from the Io object.

    public container read()

#### Return Value

A container that holds the next full record from the Io object.

#### Remarks

The definition of the next full record is controlled by the inFieldDelimiter, inRecordDelimiter, and inRecordLength method properties. The record is returned as a container. Each entry in the container equals one field in the record. Each of the specialized Io classes has default settings for inFieldDelimiter, inRecordDelimiter, and inRecordLength enabling input and output of the most common formats. You might have to adjust these to support the wanted format.

#### Examples

This method demonstrates the use of the run method. However, the following example will not compile in a job as it must be run in the context of a class, form, or other object.

    static void Job1(Args _args) 
    { 
        FileIoPermission _perm; 
        AsciiIo myfileio; 
        Container c; 
        _perm = new FileIoPermission("myfile.txt","r"); 
        myfileio = new AsciiIo("myfile.txt","r"); 
        while(myfileio.status()==IO_Status::OK) 
        { 
            c = myfileio.read(); 
            // ...do something with the container 
        } 
    }

### Method status

Retrieves the status of the last operation performed on the Io object.

    public IO_Status status()

#### Return Value

The status of the last operation, as an IO\_Status system enumeration value.

#### Remarks

The range of possible IO\_Status values returned varies among Io Classes.

#### Examples

    static void myExample(Args _args) 
    { 
        Io myIo; 
        //.. create io object and perform some operations 
        if (myIo.status()==IO_Status::OK) 
        { 
            // ...go ahead - last operation was successful 
        } 
    }

### Method write

Writes values of a simple type.

    public boolean write(VarArg values)

#### Parameters

values  
The simple types are string, integer, real, enum, and date.

#### Return Value

true if the write operation succeeds; otherwise false. If the write failed, the status method could be checked for the cause.

#### Remarks

The method accepts a variable number of arguments. Each value specified is put into the output record as a field. The first argument as the first field, the second argument as the second field, and so on. The fields are separated with the field delimiter that is specified in the outFieldDelimiter method. Each record is separated by the outRecordDelimiter method. To write complete containers, use the writeExp method.

### Method writeExp

Writes the content of a container to the file.

    public boolean writeExp(container data)

#### Parameters

data  
The container with data for the record.

#### Return Value

true if the operation succeeded; otherwise false.

#### Remarks

If this method returns false, check the status method for the cause. The entries in the container are treated as fields, and the container is treated as a full record. The field separator is defined in the outFieldDelimiter method. The record separator is defined in the outRecordDelimiter method.

#### Examples

    static void testMethod(Args _args) 
    { 
        FileIOPermission _perm; 
        container c; 
        CommaIo myfile; 
        _perm = new FileIOPermission("myfile.txt","w"); 
        _perm.assert(); 
        myfile = new CommaIo("myfile.txt","w"); 
        // Assign the entries in the container according to record layout. 
        c = [1,"MyText",1.324,"Last field"]; 
        // write this record according to file format (record/field delimiters). 
        myfile.writeExp(c); 
    }

### Method finalize

Closes the file and, if data was written, flushes the file buffers to disk.

    public void finalize()

#### Remarks

The object is typically finalized by leaving the scope, so finalize is typically not called directly. Written output will not be valid before the object is finalized.

### Method new

Creates a new instance of the Io class.

    public void new(str filename, str mode)

#### Parameters

filename  
The mode in which the file should be opened.

<!-- -->

mode  
The mode in which the file should be opened.

#### Remarks

The mode parameter can be one of the following modes:

-   R – read
-   W – write
-   A – append (implies W)
-   T – translate (text)
-   B – binary

A run-time error occurs if the file is accessed with a method that does not correspond to the current opened mode (for example, if an attempt is made to write to a read-mode file). If an attacker can control input to the new method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission. . Ensure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

#### Examples

This example uses the Io class to write to ExampleFile.

    void IoExample() 
    { 
        Io io; 
        container con; 
        FileIoPermission perm; 
        #define.ExampleFile(@"c:\test.txt") 
        #define.ExampleOpenMode("w") 
        // Grants permission to execute the 
        // Io.new method. 
        // Io.new runs under code access security. 
        perm = new FileIoPermission(#ExampleFile, #ExampleOpenMode); 
        if (perm == null) 
        { 
            return; 
        } 
        perm.assert(); 
        io = new Io(#ExampleFile, #ExampleOpenMode); 
        if (io != null) 
        { 
            io.write("Test"); 
        } 
        // Close the code access permission scope. 
        CodeAccessPermission::revertAssert(); 
    }



