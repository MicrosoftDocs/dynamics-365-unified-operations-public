---
# required metadata

title: H Classes
description: System API classes that start with the letter H.
author: RobinARH
manager: AnnBe
ms date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: RobinARH
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 52591
ms.assetid: c27e2044-28c2-432a-b15f-a41d26a83a52
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# H Classes

System API classes that start with the letter H.

Class HeapCheck
---------------

    class HeapCheck extends Object

### Remarks

### Examples

### Methods

| Method                                                                                      | Description                                     |
|---------------------------------------------------------------------------------------------|-------------------------------------------------|
| public int accessCnt()                                                                      |                                                 |
| public int addRefCnt()                                                                      |                                                 |
| public Int64 blocksAllocated(\[int pool\])                                                  |                                                 |
| public int breakCount(\[int count\])                                                        |                                                 |
| public Int64 bytesAllocated(\[int pool\])                                                   |                                                 |
| public Int64 ceiling(int pool, \[int ceiling\])                                             |                                                 |
| public int context(\[int context\])                                                         |                                                 |
| public int count(\[int count\])                                                             |                                                 |
| public int countObjects(int classId)                                                        |                                                 |
| public container createAContainer()                                                         |                                                 |
| public int csCallCnt()                                                                      |                                                 |
| public int csSweepCnt()                                                                     |                                                 |
| public container dataByContext(\[int poolNo\], \[int context\])                             |                                                 |
| public int dumpCursors()                                                                    |                                                 |
| public int dumpObjects()                                                                    |                                                 |
| public int filename(\[str filename\])                                                       |                                                 |
| public int fixedBlockSize(int pool, \[int blockSize\])                                      |                                                 |
| public int floor(int pool, \[int floor\])                                                   |                                                 |
| public int freeRefCnt()                                                                     |                                                 |
| public int getRuntimeBugcheckFlags()                                                        |                                                 |
| public Common getUnfreedCursor()                                                            |                                                 |
| public Common getUnfreedObject()                                                            |                                                 |
| public boolean include(int objectNo, \[boolean include\])                                   |                                                 |
| public boolean moreUnfreedCursors()                                                         |                                                 |
| public boolean moreUnfreedObjects()                                                         |                                                 |
| public int objectContext(int objNo, \[int context\])                                        |                                                 |
| public int pageSize(int pool, \[int pageSize\])                                             |                                                 |
| public int poolCount()                                                                      |                                                 |
| public str poolName(int poolNo)                                                             |                                                 |
| public int smallBlockSize(int pool, \[int blockSize\])                                      |                                                 |
| public int sweepCnt()                                                                       |                                                 |
| public int testBlocks(\[int arg1\])                                                         |                                                 |
| public str unfreedObjectClass()                                                             |                                                 |
| public boolean unfreedObjectClient()                                                        |                                                 |
| public boolean unfreedObjectFinalized()                                                     |                                                 |
| public int unfreedObjectHandle()                                                            |                                                 |
| public int unfreedObjectIdent()                                                             |                                                 |
| public int unfreedObjectUseCount()                                                          |                                                 |
| public str version()                                                                        |                                                 |
| public void checkHeap(str Description, \[int context\], \[int pool\], \[boolean detailed\]) |                                                 |
| public void shrinkPool(\[int poolNo\])                                                      |                                                 |
| public void postCompactingMessage()                                                         |                                                 |
| public void checkHeapDif(str Description, \[int context\], \[int pool\])                    |                                                 |
| public void clearHeapContext()                                                              |                                                 |
| public void writeString(str text)                                                           |                                                 |
| public void firstUnfreedCursor()                                                            |                                                 |
| public void dumpDGMLGraph()                                                                 |                                                 |
| public void firstUnfreedObject()                                                            |                                                 |
| public void setHeapContext(str description)                                                 |                                                 |
| public void new(\[str Filename\])                                                           | Initializes a new instance of the Object class. |
| public void nextUnfreedObject()                                                             |                                                 |
| public void checkHeapStop()                                                                 |                                                 |
| public void nextUnfreedCursor()                                                             |                                                 |
| public void setRuntimeBugcheckFlags(int flags)                                              |                                                 |
| public void checkHeapStart()                                                                |                                                 |

### Method accessCnt

    public int accessCnt()

#### Return Value

### Method addRefCnt

    public int addRefCnt()

#### Return Value

### Method blocksAllocated

    public Int64 blocksAllocated([int pool])

#### Parameters

pool  

#### Return Value

### Method breakCount

    public int breakCount([int count])

#### Parameters

count  

#### Return Value

### Method bytesAllocated

    public Int64 bytesAllocated([int pool])

#### Parameters

pool  

#### Return Value

### Method ceiling

    public Int64 ceiling(int pool, [int ceiling])

#### Parameters

pool  

<!-- -->

ceiling  

#### Return Value

### Method context

    public int context([int context])

#### Parameters

context  

#### Return Value

### Method count

    public int count([int count])

#### Parameters

count  

#### Return Value

### Method countObjects

    public int countObjects(int classId)

#### Parameters

classId  

#### Return Value

### Method createAContainer

    public container createAContainer()

#### Return Value

### Method csCallCnt

    public int csCallCnt()

#### Return Value

### Method csSweepCnt

    public int csSweepCnt()

#### Return Value

### Method dataByContext

    public container dataByContext([int poolNo], [int context])

#### Parameters

poolNo  

<!-- -->

context  

#### Return Value

### Method dumpCursors

    public int dumpCursors()

#### Return Value

### Method dumpObjects

    public int dumpObjects()

#### Return Value

### Method filename

    public int filename([str filename])

#### Parameters

filename  

#### Return Value

### Method fixedBlockSize

    public int fixedBlockSize(int pool, [int blockSize])

#### Parameters

pool  

<!-- -->

blockSize  

#### Return Value

### Method floor

    public int floor(int pool, [int floor])

#### Parameters

pool  

<!-- -->

floor  

#### Return Value

### Method freeRefCnt

    public int freeRefCnt()

#### Return Value

### Method getRuntimeBugcheckFlags

    public int getRuntimeBugcheckFlags()

#### Return Value

### Method getUnfreedCursor

    public Common getUnfreedCursor()

#### Return Value

### Method getUnfreedObject

    public Common getUnfreedObject()

#### Return Value

### Method include

    public boolean include(int objectNo, [boolean include])

#### Parameters

objectNo  

<!-- -->

include  

#### Return Value

### Method moreUnfreedCursors

    public boolean moreUnfreedCursors()

#### Return Value

### Method moreUnfreedObjects

    public boolean moreUnfreedObjects()

#### Return Value

### Method objectContext

    public int objectContext(int objNo, [int context])

#### Parameters

objNo  

<!-- -->

context  

#### Return Value

### Method pageSize

    public int pageSize(int pool, [int pageSize])

#### Parameters

pool  

<!-- -->

pageSize  

#### Return Value

### Method poolCount

    public int poolCount()

#### Return Value

### Method poolName

    public str poolName(int poolNo)

#### Parameters

poolNo  

#### Return Value

### Method smallBlockSize

    public int smallBlockSize(int pool, [int blockSize])

#### Parameters

pool  

<!-- -->

blockSize  

#### Return Value

### Method sweepCnt

    public int sweepCnt()

#### Return Value

### Method testBlocks

    public int testBlocks([int arg1])

#### Parameters

arg1  

#### Return Value

### Method unfreedObjectClass

    public str unfreedObjectClass()

#### Return Value

### Method unfreedObjectClient

    public boolean unfreedObjectClient()

#### Return Value

### Method unfreedObjectFinalized

    public boolean unfreedObjectFinalized()

#### Return Value

### Method unfreedObjectHandle

    public int unfreedObjectHandle()

#### Return Value

### Method unfreedObjectIdent

    public int unfreedObjectIdent()

#### Return Value

### Method unfreedObjectUseCount

    public int unfreedObjectUseCount()

#### Return Value

### Method version

    public str version()

#### Return Value

### Method checkHeap

    public void checkHeap(str Description, [int context], [int pool], [boolean detailed])

#### Parameters

Description  

<!-- -->

context  

<!-- -->

pool  

<!-- -->

detailed  

### Method shrinkPool

    public void shrinkPool([int poolNo])

#### Parameters

poolNo  

### Method postCompactingMessage

    public void postCompactingMessage()

### Method checkHeapDif

    public void checkHeapDif(str Description, [int context], [int pool])

#### Parameters

Description  

<!-- -->

context  

<!-- -->

pool  

### Method clearHeapContext

    public void clearHeapContext()

### Method writeString

    public void writeString(str text)

#### Parameters

text  

### Method firstUnfreedCursor

    public void firstUnfreedCursor()

### Method dumpDGMLGraph

    public void dumpDGMLGraph()

### Method firstUnfreedObject

    public void firstUnfreedObject()

### Method setHeapContext

    public void setHeapContext(str description)

#### Parameters

description  

### Method new

Initializes a new instance of the Object class.

    public void new([str Filename])

#### Parameters

Filename  

### Method nextUnfreedObject

    public void nextUnfreedObject()

### Method checkHeapStop

    public void checkHeapStop()

### Method nextUnfreedCursor

    public void nextUnfreedCursor()

### Method setRuntimeBugcheckFlags

    public void setRuntimeBugcheckFlags(int flags)

#### Parameters

flags  

### Method checkHeapStart

    public void checkHeapStart()

## Class HelpDocSetNode
    class HelpDocSetNode extends TreeNode

### Remarks

### Examples

### Methods

| Method                                                     | Description                                                                |
|------------------------------------------------------------|----------------------------------------------------------------------------|
| public boolean addToApplicationHelpMenu(\[boolean value\]) |                                                                            |
| public boolean addToDeveloperHelpMenu(\[boolean value\])   |                                                                            |
| public str changedBy(\[str value\])                        | Gets or sets the name of the user who last changed the application object. |
| public Date changedDate(\[Date value\])                    | Gets or sets the date an application object was last changed.              |
| public str changedTime(\[str value\])                      | Gets or sets the time an application object was last changed.              |
| public int contentLocation(\[int value\])                  |                                                                            |
| public str createdBy(\[str value\])                        | Gets or sets the name of the user who created the application object.      |
| public Date creationDate(\[Date value\])                   | Gets or sets the date an application object was created.                   |
| public str creationTime(\[str value\])                     |                                                                            |
| public boolean developerDocumentSet(\[boolean value\])     |                                                                            |
| public str documentSetDescription(\[str value\])           |                                                                            |
| public str documentSetName(\[str value\])                  |                                                                            |
| public str helpProviderClass(\[str value\])                |                                                                            |
| public Guid origin(\[Guid value\])                         |                                                                            |
| public boolean userDocumentSet(\[boolean value\])          |                                                                            |
| public void new(str DocSetName)                            | Initializes a new instance of the TreeNode class.                          |

### Method addToApplicationHelpMenu

    public boolean addToApplicationHelpMenu([boolean value])

#### Parameters

value  

#### Return Value

### Method addToDeveloperHelpMenu

    public boolean addToDeveloperHelpMenu([boolean value])

#### Parameters

value  

#### Return Value

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

### Method contentLocation

    public int contentLocation([int value])

#### Parameters

value  

#### Return Value

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

### Method developerDocumentSet

    public boolean developerDocumentSet([boolean value])

#### Parameters

value  

#### Return Value

### Method documentSetDescription

    public str documentSetDescription([str value])

#### Parameters

value  

#### Return Value

### Method documentSetName

    public str documentSetName([str value])

#### Parameters

value  

#### Return Value

### Method helpProviderClass

    public str helpProviderClass([str value])

#### Parameters

value  

#### Return Value

### Method origin

    public Guid origin([Guid value])

#### Parameters

value  

#### Return Value

### Method userDocumentSet

    public boolean userDocumentSet([boolean value])

#### Parameters

value  

#### Return Value

### Method new

Initializes a new instance of the TreeNode class.

    public void new(str DocSetName)

#### Parameters

DocSetName  

## Class HelpDocumentManager
    class HelpDocumentManager extends Object

### Remarks

### Examples

### Methods

| Method                                                                                                              | Description                                                  |
|---------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------|
| public void new()                                                                                                   | Initializes a new instance of the HelpDocumentManager class. |
| ::public static void showHelpTopic(\[str topic\], \[str documentSet\], \[str contentLanguage\], \[str uiLanguage\]) |                                                              |
| public void finalize()                                                                                              |                                                              |

### Method new

Initializes a new instance of the HelpDocumentManager class.

    public void new()

### Method showHelpTopic

    public static void showHelpTopic([str topic], [str documentSet], [str contentLanguage], [str uiLanguage])

#### Parameters

topic  

<!-- -->

documentSet  

<!-- -->

contentLanguage  

<!-- -->

uiLanguage  

### Method finalize

    public void finalize()

## Class HtmlFont
    class HtmlFont extends Object

### Remarks

### Examples

### Methods

| Method                                                                                                    | Description                                     |
|-----------------------------------------------------------------------------------------------------------|-------------------------------------------------|
| public int backColor(\[int value\])                                                                       |                                                 |
| public str fontName(\[str value\])                                                                        |                                                 |
| public int pointSize(\[int value\])                                                                       |                                                 |
| public int style(\[int value\])                                                                           |                                                 |
| public int textColor(\[int value\])                                                                       |                                                 |
| public void new(\[str TypeFace\], \[int PointSize\], \[int Style\], \[int TextColor\], \[int BackColor\]) | Initializes a new instance of the Object class. |
| public void finalize()                                                                                    |                                                 |

### Method backColor

    public int backColor([int value])

#### Parameters

value  

#### Return Value

### Method fontName

    public str fontName([str value])

#### Parameters

value  

#### Return Value

### Method pointSize

    public int pointSize([int value])

#### Parameters

value  

#### Return Value

### Method style

    public int style([int value])

#### Parameters

value  

#### Return Value

### Method textColor

    public int textColor([int value])

#### Parameters

value  

#### Return Value

### Method new

Initializes a new instance of the Object class.

    public void new([str TypeFace], [int PointSize], [int Style], [int TextColor], [int BackColor])

#### Parameters

TypeFace  

<!-- -->

PointSize  

<!-- -->

Style  

<!-- -->

TextColor  

<!-- -->

BackColor  

### Method finalize

    public void finalize()

