---
# required metadata

title: E Classes
description: System API classes that start with the letter E.
author: RobinARH
manager: AnnBe
ms.date: 04/04/2017
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
ms.custom: 68633
ms.assetid: c7fea535-c44d-4e78-96b2-77e180076ac9
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# E Classes

[!include[banner](../includes/banner.md)]


System API classes that start with the letter E.

Class Editor
------------

    class Editor extends Object

### Remarks

### Examples

### Methods

| Method                                                                          | Description                                     |
|---------------------------------------------------------------------------------|-------------------------------------------------|
| public int columnNo()                                                           |                                                 |
| public str currentLine()                                                        |                                                 |
| public int currentLineNo()                                                      |                                                 |
| public str getLine()                                                            |                                                 |
| public int gotoCol(int ColumnNo)                                                |                                                 |
| public int lineNo()                                                             |                                                 |
| public MarkMode markMode()                                                      |                                                 |
| public boolean matchCase(\[boolean UseMatchCase\])                              |                                                 |
| public boolean moreLines()                                                      |                                                 |
| public boolean moreSelectedLines()                                              |                                                 |
| public str path()                                                               |                                                 |
| public boolean regexp(\[boolean UseRegExp\])                                    |                                                 |
| public boolean replace(str SearchString, str ReplaceString, boolean ReplaceAll) |                                                 |
| public boolean search(str SearchString)                                         |                                                 |
| public str searchString()                                                       |                                                 |
| public int selectionEndCol()                                                    |                                                 |
| public int selectionEndLine()                                                   |                                                 |
| public int selectionStartCol()                                                  |                                                 |
| public int selectionStartLine()                                                 |                                                 |
| ::public static Editor open(str documentPath)                                   |                                                 |
| public void gotoLine(int LineNo)                                                |                                                 |
| public void closeApplicationObjectDialog()                                      |                                                 |
| public void mark(int line, int col)                                             |                                                 |
| public void executeScript(str scriptName)                                       |                                                 |
| public void nextLine()                                                          |                                                 |
| public void firstSelectedLine()                                                 |                                                 |
| private void new()                                                              | Initializes a new instance of the Editor class. |
| public void unmark()                                                            |                                                 |
| public void insertString(str InsString)                                         |                                                 |
| public void close()                                                             |                                                 |
| public void nextSelectedLine()                                                  |                                                 |
| public void closeSearchDialog()                                                 |                                                 |
| public void deleteLines(\[int noOfLines\])                                      |                                                 |
| public void insertLines(str InsString)                                          |                                                 |
| public void firstLine()                                                         |                                                 |
| public void deleteChars(\[int noOfChars\])                                      |                                                 |

### Method columnNo

    public int columnNo()

#### Return Value

### Method currentLine

    public str currentLine()

#### Return Value

### Method currentLineNo

    public int currentLineNo()

#### Return Value

### Method getLine

    public str getLine()

#### Return Value

### Method gotoCol

    public int gotoCol(int ColumnNo)

#### Parameters

ColumnNo  

#### Return Value

### Method lineNo

    public int lineNo()

#### Return Value

### Method markMode

    public MarkMode markMode()

#### Return Value

### Method matchCase

    public boolean matchCase([boolean UseMatchCase])

#### Parameters

UseMatchCase  

#### Return Value

### Method moreLines

    public boolean moreLines()

#### Return Value

### Method moreSelectedLines

    public boolean moreSelectedLines()

#### Return Value

### Method path

    public str path()

#### Return Value

### Method regexp

    public boolean regexp([boolean UseRegExp])

#### Parameters

UseRegExp  

#### Return Value

### Method replace

    public boolean replace(str SearchString, str ReplaceString, boolean ReplaceAll)

#### Parameters

SearchString  

<!-- -->

ReplaceString  

<!-- -->

ReplaceAll  

#### Return Value

### Method search

    public boolean search(str SearchString)

#### Parameters

SearchString  

#### Return Value

### Method searchString

    public str searchString()

#### Return Value

### Method selectionEndCol

    public int selectionEndCol()

#### Return Value

### Method selectionEndLine

    public int selectionEndLine()

#### Return Value

### Method selectionStartCol

    public int selectionStartCol()

#### Return Value

### Method selectionStartLine

    public int selectionStartLine()

#### Return Value

### Method open

    public static Editor open(str documentPath)

#### Parameters

documentPath  

#### Return Value

### Method gotoLine

    public void gotoLine(int LineNo)

#### Parameters

LineNo  

### Method closeApplicationObjectDialog

    public void closeApplicationObjectDialog()

### Method mark

    public void mark(int line, int col)

#### Parameters

line  

<!-- -->

col  

### Method executeScript

    public void executeScript(str scriptName)

#### Parameters

scriptName  

### Method nextLine

    public void nextLine()

### Method firstSelectedLine

    public void firstSelectedLine()

### Method new

Initializes a new instance of the Editor class.

    private void new()

### Method unmark

    public void unmark()

### Method insertString

    public void insertString(str InsString)

#### Parameters

InsString  

### Method close

    public void close()

### Method nextSelectedLine

    public void nextSelectedLine()

### Method closeSearchDialog

    public void closeSearchDialog()

### Method deleteLines

    public void deleteLines([int noOfLines])

#### Parameters

noOfLines  

### Method insertLines

    public void insertLines(str InsString)

#### Parameters

InsString  

### Method firstLine

    public void firstLine()

### Method deleteChars

    public void deleteChars([int noOfChars])

#### Parameters

noOfChars  

## Class Enumerator
    class Enumerator extends Object

### Remarks

### Examples

### Methods

| Method                        | Description                                          |
|-------------------------------|------------------------------------------------------|
| public AnyType current()      |                                                      |
| public str definitionString() |                                                      |
| public boolean moveNext()     |                                                      |
| public str toString()         | Returns a string that represents the current object. |
| public void reset()           |                                                      |

### Method current

    public AnyType current()

#### Return Value

### Method definitionString

    public str definitionString()

#### Return Value

### Method moveNext

    public boolean moveNext()

#### Return Value

### Method toString

Returns a string that represents the current object.

    public str toString()

#### Return Value

A string that represents the current object.

#### Remarks

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type. For example, an instance of the SysMethodInfo class returns the method name and type of the method, such as instance or static.

### Method reset

    public void reset()

## Class ExecutePermission
    class ExecutePermission extends CodeAccessPermission

The ExecutePermission class controls the execution of X++ code.

### Remarks

This class is designed to check permissions for specific APIs. For a list of all APIs that are protected by permissions, see Secured APIs. Before the protected API is executed, you must call the assert method on the same tier (which is usually the server tier) that the corresponding CodeAccessPermission::demand method is called on. Call a method on the server tier from one of the following methods:

-   A server static method
-   A class instance method that is set to run on the server by using the RunOn class property

### Examples

The following code example shows a new instance of the ExecutePermission class. The assert method is called to declare that the code can then call the Thread.new method to create a new thread.

    server static void main(Args args) 
    { 
        Thread _t; 
        ExecutePermission _perm; 
        _perm = new ExecutePermission(); 
        if (!_perm) 
        { 
            return; 
        } 
        _perm.assert(); 
        // Invoke the protected API. 
         _t = new Thread(); 
        // Call member methods. 
        if (_t) 
        { 
            _t.removeOnComplete(true); 
            _t.run(classnum(SysCodeProfiler), identifierstr(transferFile)); 
        } 
        // Optionally, call revertAssert() to limit scope of assert. 
        CodeAccessPermission::revertAssert(); 
    }

### Methods

| Method                                                 | Description                                                                      |
|--------------------------------------------------------|----------------------------------------------------------------------------------|
| public CodeAccessPermission copy()                     | Creates and returns a copy of the current permission class object.               |
| public boolean isSubsetOf(CodeAccessPermission target) | Determines whether a current permission is a subset of the specified permission. |
| public void new()                                      | Initializes a new instance of the ExecutePermission class.                       |

### Method copy

Creates and returns a copy of the current permission class object.

    public CodeAccessPermission copy()

#### Return Value

A copy of the current permission object.

#### Remarks

You override this method when you derive a class from the CodeAccessPermission class.

### Method isSubsetOf

Determines whether a current permission is a subset of the specified permission.

    public boolean isSubsetOf(CodeAccessPermission target)

#### Parameters

target  
A CodeAccessPermission class object.

#### Return Value

true if a current permission is a subset of the specified permission; otherwise, false.

#### Remarks

You override this method when you derive a class from the CodeAccessPermission class.

### Method new

Initializes a new instance of the ExecutePermission class. End.

    public void new()


