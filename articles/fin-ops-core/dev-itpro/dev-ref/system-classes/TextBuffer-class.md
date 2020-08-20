---
title: TextBuffer class
description: This topic describes the TextBuffer class.
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

# Class TextBuffer

[!include [banner](../../includes/banner.md)]

```xpp
class TextBuffer extends Object
```

The TextBuffer class manages arbitrary text file content, and generates and manipulates text.

## Remarks

This class features various string operations, a simple clipboard, and a file interface.

## Examples

```xpp
static void example() 
{ 
    FileIoPermission _perm = new FileIoPermission("myfile.txt",'r'); 
    TextBuffer txtb = new TextBuffer(); 
    _perm.assert(); 
    txtb.fromFile("myfile.txt"); // Read text from file 
    txtb.toClipboard(); // Copy it to the clipboard 
}
```

## Methods

| Method                                                                 | Description                                                                                           |
|------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
| public boolean accept(str searchText)                                  |                                                                                                       |
| public int decryptOld(int cryptKey)                                    |                                                                                                       |
| public boolean find(str searchText, \[int start\])                     | Searches the TextBuffer object for any occurrence of a string expression.                             |
| public boolean fromClipboard()                                         | Replaces the content of the TextBuffer object with the content of the clipboard.                      |
| public boolean fromFile(str filename, \[int encoding\])                | Replaces the content of a TextBuffer object with the content of the specified file.                   |
| public str getText()                                                   | Retrieves the current content of the TextBuffer object.                                               |
| public int getValue()                                                  |                                                                                                       |
| public boolean ignoreCase(\[boolean ignoreCase\])                      |                                                                                                       |
| public boolean isNext(str searchText)                                  |                                                                                                       |
| public int matchLen()                                                  | Returns the string length of the first match in the TextBuffer object.                                |
| public int matchPos()                                                  | Returns the character position of the first occurrence of the search string in the TextBuffer object. |
| public str nextToken(\[boolean includeWholeLine\], \[str stopAtChar\]) |                                                                                                       |
| public int numLines()                                                  | Retrieves the number of lines in the TextBuffer object.                                               |
| public boolean regularExpressions(\[boolean useRegularExpressions\])   |                                                                                                       |
| public int size()                                                      |                                                                                                       |
| public str subStr(int start, int length)                               | Retrieves part of the content of the TextBuffer object (a substring).                                 |
| public boolean toFile(str filename, \[int encoding\])                  | Saves the content of the TextBuffer object to a file.                                                 |
| public str token()                                                     |                                                                                                       |
| public str toString()                                                  | Returns a string that represents the current object.                                                  |
| ::public static int strHashKey(str sourceString)                       |                                                                                                       |
| public void new()                                                      | Initializes a new instance of the TextBuffer class.                                                   |
| public void removeChar(str charList)                                   |                                                                                                       |
| public void toClipboard()                                              | Copies the content of a TextBuffer object to the clipboard.                                           |
| public void insert(str insertString, int position)                     |                                                                                                       |
| public void setText(str string)                                        | Sets the content of the TextBuffer object to the specified string, overwriting any existing content.  |
| public void appendText(str string)                                     | Appends a string to the content of the TextBuffer object.                                             |
| public void replace(str findString, str replaceString)                 |                                                                                                       |
| public void delete(int start, int length)                              |                                                                                                       |

## Method accept

```xpp
public boolean accept(str searchText)
```

### Parameters - accept

searchText  

### Return Value - accept

## Method decryptOld

```xpp
public int decryptOld(int cryptKey)
```

### Parameters - decryptOld

cryptKey  

### Return Value - decryptOld

## Method find

Searches the TextBuffer object for any occurrence of a string expression.

```xpp
public boolean find(str searchText, [int start])
```

### Parameters - find

searchText  
A numeric expression that sets the starting position for each search; optional. If this parameter is omitted, the search starts at the first character position.

<!-- -->

start  
A numeric expression that sets the starting position for each search; optional. If this parameter is omitted, the search starts at the first character position.

### Return Value - find

true if searchText is found; otherwise, false.

### Remarks - find

This method performs a textual, case-insensitive comparison by using regular expressions. For more information, see the match function. Case-insensitivity can be turned off by using the ignoreCase method. Regular expressions can be turned off by using the regularExpressions method.

### Examples - find

The following example searches the TextBuffer object for all occurrences of a specified string and prints the position at which the match is found.

```xpp
int pos; 
TextBuffer textBuffer; 
textBuffer = new TextBuffer(); 
textBuffer.setText("ABC DEF GHI JKL MNO ABC ABC"); 
pos = 0; 
while (textBuffer.find("ABC",pos)) 
{ 
    print "String found at position: ", textBuffer.matchPos(); 
    pause; 
    pos = textBuffer.matchPos()+1; 
}
```

## Method fromClipboard

Replaces the content of the TextBuffer object with the content of the clipboard.

```xpp
public boolean fromClipboard()
```

### Return Value - fromClipboard

true if the replacement was successful; otherwise, false.

### Examples - fromClipboard

```xpp
{ 
    TextBuffer txtb = new textBuffer(); 
    FileIoPermission perm; 
    #define.ExampleFile(@"c:\test.txt") 
    #define.ExampleOpenMode("w") 
    // Set code access permission to help protect the use of 
    // TextBuffer.tofile 
    perm = new FileIoPermission(#ExampleFile, #ExampleOpenMode); 
    perm.assert(); 
    if ( txtb.fromClipboard() ) 
    { 
        // Got text from clipboard - save it to file 
        txtb.toFile(#ExampleFile); 
    } 
    // Close the code access permission scope. 
    CodeAccessPermission::revertAssert(); 
}
```

## Method fromFile

Replaces the content of a TextBuffer object with the content of the specified file.

```xpp
public boolean fromFile(str filename, [int encoding])
```

### Parameters - fromFile

filename  
The encoding option to use; optional.

<!-- -->

encoding  
The encoding option to use; optional.

### Return Value - fromFile

true if the file operation was successful; otherwise, false.

### Remarks - fromFile

The following are possible values for the encoding parameter that are supplied by the FileEncoding system enumeration:

-   ACP
-   UTF8
-   UTF16BE
-   UTF16LE
-   GB18030
-   AUTO

If the file operation is unsuccessful, the TextBuffer object remains unchanged. If an attacker can control input to the fromFile method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission from the ExecutePermission class. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

## Method getText

Retrieves the current content of the TextBuffer object.

```xpp
public str getText()
```

### Return Value - getText

A string that contains the content of TextBuffer object.

### Remarks - getText

The TextBuffer can contain new lines, which are then present in the returned string.

## Method getValue

```xpp
public int getValue()
```

### Return Value - getValue

## Method ignoreCase

```xpp
public boolean ignoreCase([boolean ignoreCase])
```

### Parameters - ignoreCase

ignoreCase  

### Return Value - ignoreCase

## Method isNext

```xpp
public boolean isNext(str searchText)
```

### Parameters - isNext

searchText  

### Return Value - isNext

## Method matchLen

Returns the string length of the first match in the TextBuffer object.

```xpp
public int matchLen()
```

### Return Value - matchLen

The length of the match that is found; 0 (zero) if no match is found.

### Remarks - matchLen

This method is used as part of a text search (see the find method).

## Method matchPos

Returns the character position of the first occurrence of the search string in the TextBuffer object.

```xpp
public int matchPos()
```

### Return Value - matchPos

The position at which the match is found; 0 (zero) if no match is found.

### Remarks - matchPos

This method is used as part of a text search (see the find method).

## Method nextToken

```xpp
public str nextToken([boolean includeWholeLine], [str stopAtChar])
```

### Parameters - nextToken

includeWholeLine  

<!-- -->

stopAtChar  

### Return Value - nextToken

## Method numLines

Retrieves the number of lines in the TextBuffer object.

```xpp
public int numLines()
```

### Return Value - numLines

The number of lines in the content.

### Remarks - numLines

Lines are separated by newlines ('\\n').

### Examples - numLines

```xpp
{ 
    TextBuffer txtb = new TextBuffer(); 
    if (txtb.fromClipboard()) 
    { 
        print "Clipboard contains ",txtb.numLines()," lines."; 
    } 
}
```

## Method regularExpressions

```xpp
public boolean regularExpressions([boolean useRegularExpressions])
```

### Parameters - regularExpressions

useRegularExpressions  

### Return Value - regularExpressions

## Method size

```xpp
public int size()
```

### Return Value - size

## Method subStr

Retrieves part of the content of the TextBuffer object (a substring).

```xpp
public str subStr(int start, int length)
```

### Parameters - subStr

start  
The length of the desired substring.

<!-- -->

length  
The length of the desired substring.

### Return Value - subStr

A string that contains the specified part of the TextBuffer object content.

### Remarks - subStr

When you specify the start position for substring, use 1 for the first character in the content, 2 for the second character, and so on.

### Examples - subStr

```xpp
{ 
    TextBuffer txtb = new TextBuffer(); 
    str mystr; 
    if (txtb.fromClipboard()) 
    { 
        mystr = txtb.subStr(10,15);  
        // 15 long substring starting at position 10. 
    } 
}
```

## Method toFile

Saves the content of the TextBuffer object to a file.

```xpp
public boolean toFile(str filename, [int encoding])
```

### Parameters - toFile

filename  

<!-- -->

encoding  

### Return Value - toFile

true if the operation is successful; otherwise, false.

### Remarks - toFile

If the specified file already exists, it is overwritten without confirmation. If an attacker can control input to the toFile method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission from the ExecutePermission class. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

## Method token

```xpp
public str token()
```

### Return Value - token

## Method toString

Returns a string that represents the current object.

```xpp
public str toString()
```

### Return Value - toString

A string that represents the current object.

### Remarks - toString

The default implementation returns the class name of the object. The method can be overridden in a derived class so that it returns values that are meaningful for that type. For example, an instance of the SysMethodInfo class returns the method name and type of the method, such as instance or static.

## Method strHashKey

```xpp
public static int strHashKey(str sourceString)
```

### Parameters - strHashKey

sourceString  

### Return Value - strHashKey

## Method new

Initializes a new instance of the TextBuffer class.

```xpp
public void new()
```

## Method removeChar

```xpp
public void removeChar(str charList)
```

### Parameters - removeChar

charList  

## Method toClipboard

Copies the content of a TextBuffer object to the clipboard.

```xpp
public void toClipboard()
```

## Method insert

```xpp
public void insert(str insertString, int position)
```

### Parameters - insert

insertString  

<!-- -->

position  

## Method setText

Sets the content of the TextBuffer object to the specified string, overwriting any existing content.

```xpp
public void setText(str string)
```

### Parameters - setText

string  
A string that contains the new text for the TextBuffer object.

### Remarks - setText

If the TextBuffer object contains any content, it is overwritten by the new content.

### Examples - setText

```xpp
{ 
    TextBuffer txtb = new TextBuffer(); 
    txtb.setText("This is the first text."); 
    // Now txtb contains exactly that text. 
}
```

## Method appendText

Appends a string to the content of the TextBuffer object.

```xpp
public void appendText(str string)
```

### Parameters - appendText

string  
The string to append.

### Examples - appendText

```xpp
{ 
    TextBuffer txtb = new TextBuffer(); 
    txtb.setText("[One]"); 
    txtb.appendText("[Another]"); 
    print txtb.getText(); // Will print "[One][Another]" 
}
```

## Method replace

```xpp
public void replace(str findString, str replaceString)
```

### Parameters - replace

findString  

<!-- -->

replaceString  

## Method delete

```xpp
public void delete(int start, int length)
```

### Parameters - delete

start  

<!-- -->

length  

