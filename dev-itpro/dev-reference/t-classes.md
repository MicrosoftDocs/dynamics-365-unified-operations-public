---
# required metadata

title: T Classes
description: System API classes that start with the letter T.
author: RobinARH
manager: AnnBe
ms.date: 2016-02-24 01 - 03 - 12
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
ms.custom: 51774
ms.assetid: c83d7228-86a5-404b-a978-7f6d316b7b7e
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# T Classes

System API classes that start with the letter T.

Class TableExtension
--------------------

    class TableExtension extends Object

### Remarks

### Examples

### Methods

| Method                                                    | Description                                             |
|-----------------------------------------------------------|---------------------------------------------------------|
| public void new()                                         | Initializes a new instance of the TableExtension class. |
| public void modifiedField(Common record, FieldId fieldId) |                                                         |
| public void defaultRow(Common record)                     |                                                         |
| public void defaultField(Common record, FieldId fieldId)  |                                                         |

### Method new

Initializes a new instance of the TableExtension class.

    public void new()

### Method modifiedField

    public void modifiedField(Common record, FieldId fieldId)

#### Parameters

record  

<!-- -->

fieldId  

### Method defaultRow

    public void defaultRow(Common record)

#### Parameters

record  

### Method defaultField

    public void defaultField(Common record, FieldId fieldId)

#### Parameters

record  

<!-- -->

fieldId  

## Class TextBuffer
    class TextBuffer extends Object

The TextBuffer class manages arbitrary text file content, and generates and manipulates text.

### Remarks

This class features various string operations, a simple clipboard, and a file interface.

### Examples

    static void example() 
    { 
        FileIoPermission _perm = new FileIoPermission("myfile.txt",'r'); 
        TextBuffer txtb = new TextBuffer(); 
        _perm.assert(); 
        txtb.fromFile("myfile.txt"); // Read text from file 
        txtb.toClipboard(); // Copy it to the clipboard 
    }

### Methods

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

### Method accept

    public boolean accept(str searchText)

#### Parameters

searchText  

#### Return Value

### Method decryptOld

    public int decryptOld(int cryptKey)

#### Parameters

cryptKey  

#### Return Value

### Method find

Searches the TextBuffer object for any occurrence of a string expression.

    public boolean find(str searchText, [int start])

#### Parameters

searchText  
A numeric expression that sets the starting position for each search; optional. If this parameter is omitted, the search starts at the first character position.

<!-- -->

start  
A numeric expression that sets the starting position for each search; optional. If this parameter is omitted, the search starts at the first character position.

#### Return Value

true if searchText is found; otherwise, false.

#### Remarks

This method performs a textual, case-insensitive comparison by using regular expressions. For more information, see the match function. Case-insensitivity can be turned off by using the ignoreCase method. Regular expressions can be turned off by using the regularExpressions method.

#### Examples

The following example searches the TextBuffer object for all occurrences of a specified string and prints the position at which the match is found.

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

### Method fromClipboard

Replaces the content of the TextBuffer object with the content of the clipboard.

    public boolean fromClipboard()

#### Return Value

true if the replacement was successful; otherwise, false.

#### Examples

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

### Method fromFile

Replaces the content of a TextBuffer object with the content of the specified file.

    public boolean fromFile(str filename, [int encoding])

#### Parameters

filename  
The encoding option to use; optional.

<!-- -->

encoding  
The encoding option to use; optional.

#### Return Value

true if the file operation was successful; otherwise, false.

#### Remarks

The following are possible values for the encoding parameter that are supplied by the FileEncoding system enumeration:

-   ACP
-   UTF8
-   UTF16BE
-   UTF16LE
-   GB18030
-   AUTO

If the file operation is unsuccessful, the TextBuffer object remains unchanged. If an attacker can control input to the fromFile method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission from the ExecutePermission class. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

### Method getText

Retrieves the current content of the TextBuffer object.

    public str getText()

#### Return Value

A string that contains the content of TextBuffer object.

#### Remarks

The TextBuffer can contain new lines, which are then present in the returned string.

### Method getValue

    public int getValue()

#### Return Value

### Method ignoreCase

    public boolean ignoreCase([boolean ignoreCase])

#### Parameters

ignoreCase  

#### Return Value

### Method isNext

    public boolean isNext(str searchText)

#### Parameters

searchText  

#### Return Value

### Method matchLen

Returns the string length of the first match in the TextBuffer object.

    public int matchLen()

#### Return Value

The length of the match that is found; 0 (zero) if no match is found.

#### Remarks

This method is used as part of a text search (see the find method).

### Method matchPos

Returns the character position of the first occurrence of the search string in the TextBuffer object.

    public int matchPos()

#### Return Value

The position at which the match is found; 0 (zero) if no match is found.

#### Remarks

This method is used as part of a text search (see the find method).

### Method nextToken

    public str nextToken([boolean includeWholeLine], [str stopAtChar])

#### Parameters

includeWholeLine  

<!-- -->

stopAtChar  

#### Return Value

### Method numLines

Retrieves the number of lines in the TextBuffer object.

    public int numLines()

#### Return Value

The number of lines in the content.

#### Remarks

Lines are separated by newlines ('\\n').

#### Examples

    { 
        TextBuffer txtb = new TextBuffer(); 
        if (txtb.fromClipboard()) 
        { 
            print "Clipboard contains ",txtb.numLines()," lines."; 
        } 
    }

### Method regularExpressions

    public boolean regularExpressions([boolean useRegularExpressions])

#### Parameters

useRegularExpressions  

#### Return Value

### Method size

    public int size()

#### Return Value

### Method subStr

Retrieves part of the content of the TextBuffer object (a substring).

    public str subStr(int start, int length)

#### Parameters

start  
The length of the desired substring.

<!-- -->

length  
The length of the desired substring.

#### Return Value

A string that contains the specified part of the TextBuffer object content.

#### Remarks

When you specify the start position for substring, use 1 for the first character in the content, 2 for the second character, and so on.

#### Examples

    { 
        TextBuffer txtb = new TextBuffer(); 
        str mystr; 
        if (txtb.fromClipboard()) 
        { 
            mystr = txtb.subStr(10,15);  
            // 15 long substring starting at position 10. 
        } 
    }

### Method toFile

Saves the content of the TextBuffer object to a file.

    public boolean toFile(str filename, [int encoding])

#### Parameters

filename  

<!-- -->

encoding  

#### Return Value

true if the operation is successful; otherwise, false.

#### Remarks

If the specified file already exists, it is overwritten without confirmation. If an attacker can control input to the toFile method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission from the ExecutePermission class. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

### Method token

    public str token()

#### Return Value

### Method toString

Returns a string that represents the current object.

    public str toString()

#### Return Value

A string that represents the current object.

#### Remarks

The default implementation returns the class name of the object. The method can be overridden in a derived class so that it returns values that are meaningful for that type. For example, an instance of the SysMethodInfo class returns the method name and type of the method, such as instance or static.

### Method strHashKey

    public static int strHashKey(str sourceString)

#### Parameters

sourceString  

#### Return Value

### Method new

Initializes a new instance of the TextBuffer class.

    public void new()

### Method removeChar

    public void removeChar(str charList)

#### Parameters

charList  

### Method toClipboard

Copies the content of a TextBuffer object to the clipboard.

    public void toClipboard()

### Method insert

    public void insert(str insertString, int position)

#### Parameters

insertString  

<!-- -->

position  

### Method setText

Sets the content of the TextBuffer object to the specified string, overwriting any existing content.

    public void setText(str string)

#### Parameters

string  
A string that contains the new text for the TextBuffer object.

#### Remarks

If the TextBuffer object contains any content, it is overwritten by the new content.

#### Examples

    { 
        TextBuffer txtb = new TextBuffer(); 
        txtb.setText("This is the first text."); 
        // Now txtb contains exactly that text. 
    }

### Method appendText

Appends a string to the content of the TextBuffer object.

    public void appendText(str string)

#### Parameters

string  
The string to append.

#### Examples

    { 
        TextBuffer txtb = new TextBuffer(); 
        txtb.setText("[One]"); 
        txtb.appendText("[Another]"); 
        print txtb.getText(); // Will print "[One][Another]" 
    }

### Method replace

    public void replace(str findString, str replaceString)

#### Parameters

findString  

<!-- -->

replaceString  

### Method delete

    public void delete(int start, int length)

#### Parameters

start  

<!-- -->

length  

## Class TextIo
    class TextIo extends CommaIo

The TextIo class provides functionality for reading and writing text files.

### Remarks

TextIO replaces AsciiIO to provide support for non-ANSI code page file I/O. The TextIO constructor has an additional optional parameter to set the code page of the file. The TextIO.new method has an optional argument that specifies the code page of the file. The default value is UTF-16LE (the Microsoft Windows native Unicode representation). It is best to use this in most instances, especially if end-users might edit the file in a text editor outside Microsoft Dynamics AX. For more information, see TextIo.new. When files are read, TextIO examines the first few bytes of the file for a byte-order mark (BOM) and automatically handles UTF-8, UTF-16LE, and UTF-16BE. If no BOM is found, the file is assumed to be in the ANSI Code Page (ACP) format.

### Examples

### Methods

| Method                                                    | Description                                                                                                        |
|-----------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------|
| public str inFieldDelimiter(\[str value\])                | Gets or sets the character that is used for the field delimiter of an input file represented by a TextIO object.   |
| public str inRecordDelimiter(\[str value\])               | Gets or sets the character that is used for the record delimiter of an input file represented by a TextIO object.  |
| public int inRecordLength(\[int value\])                  | Gets or sets the record length for an input file.                                                                  |
| public str outFieldDelimiter(\[str value\])               | Gets or sets the character that is used for the field delimiter of an output file represented by a TextIO object.  |
| public str outRecordDelimiter(\[str value\])              | Gets or sets the character that is used for the record delimiter of an output file represented by a TextIO object. |
| public container read()                                   | Reads the next full record from a TextIO object.                                                                   |
| public IO\_Status status()                                | Retrieves the status of the last operation performed on a TextIo object.                                           |
| public boolean write(VarArg values)                       | Writes data to a file represented by a TextIO object.                                                              |
| public boolean writeChar(int int)                         | Writes a Unicode character to a file.                                                                              |
| public boolean writeExp(container data)                   | Writes the contents of a container to a file represented by a TextIO object.                                       |
| public boolean writeRaw(str data)                         | Reserved.                                                                                                          |
| public void new(str filename, str mode, \[int codepage\]) | Creates a new instance of the TextIO class.                                                                        |
| public void finalize()                                    | Closes the file and, if data was written, flushes the file buffers to disk.                                        |

### Method inFieldDelimiter

Gets or sets the character that is used for the field delimiter of an input file represented by a TextIO object.

    public str inFieldDelimiter([str value])

#### Parameters

value  
The character to be used as the field delimiter; optional.

#### Return Value

The character used as the field delimiter.

#### Remarks

To set the field delimiter for an output file, use

#### Examples

The following example sets the field delimiter for an input file to '\\r\\n'.

    protected void openFile() 
    { 
        #define.delimiter('\r\n') 
        super(); 
        importFile.inFieldDelimiter(#delimiter); 
    }

### Method inRecordDelimiter

Gets or sets the character that is used for the record delimiter of an input file represented by a TextIO object.

    public str inRecordDelimiter([str value])

#### Parameters

value  
The character to be used as the record delimiter; optional.

#### Return Value

The character used as the record delimiter.

#### Remarks

To set the record delimiter for an output file, use the .

#### Examples

The following example sets the record delimiter to 128.

    boolean openFile() 
    { 
        boolean ret = false; 
        int     recordLength = 128; 
        int     numOflastCharacter = 255; 
        textFile = new TextIo(filename, 'r'); 
        if (textFile) 
        { 
            if (textFile.status()) 
            { 
                throw error("@SYS52680"); 
            } 
            textFile.inFieldDelimiter(num2char(numOflastCharacter)); 
            textFile.inRecordDelimiter(num2char(numOflastCharacter)); 
            textFile.inRecordLength(recordLength); 
            ret = true; 
        } 
        return ret; 
    }

### Method inRecordLength

Gets or sets the record length for an input file.

    public int inRecordLength([int value])

#### Parameters

value  
The record length for the input file; optional.

#### Return Value

The record length for the input file.

#### Remarks

For files that have a fixed-length format, use the inRecordLength property to ensure that no more than the specified number of characters are read for each record.If the record format is overruled by a specified inRecordDelimiter property value, that is the inRecordDelimiter value is met before the fixed length is read, the record is accepted, and no further data is read. To ensure that a fixed number of characters are read, set the inRecordDelimiter property value to an empty string. When no inRecordDelimiter property value is found, the inRecordDelimiter property value is the maximum limit of characters to read. Set the inRecordDelimiter property value to zero to disable the record length check.

#### Examples

The following example sets the record length to 128.

    boolean openFile() 
    { 
        boolean ret = false; 
        int     recordLength = 128; 
        int     numOflastCharacter = 255; 
        textFile = new TextIo(filename, 'r'); 
        if (textFile) 
        { 
            if (textFile.status()) 
            { 
                throw error("@SYS52680"); 
            } 
            textFile.inFieldDelimiter(num2char(numOflastCharacter)); 
            textFile.inRecordDelimiter(num2char(numOflastCharacter)); 
            textFile.inRecordLength(recordLength); 
            ret = true; 
        } 
        return ret; 
    }

### Method outFieldDelimiter

Gets or sets the character that is used for the field delimiter of an output file represented by a TextIO object.

    public str outFieldDelimiter([str value])

#### Parameters

value  
The character to be used as the field delimiter; optional.

#### Return Value

The character used as the field delimiter.

#### Remarks

To set the field delimiter for an input file, use the .

#### Examples

The following example sets the field delimiter to ' ' (nothing) for an output file.

    void defineFile() 
    { 
        diskFile = new TextIo(diskFileName,'W'); 
        if (!diskFile) 
        { 
            throw error("@SYS26757"); 
        } 
        diskFile.outRecordDelimiter('\r\n'); 
        diskFile.outFieldDelimiter(''); 
    }

### Method outRecordDelimiter

Gets or sets the character that is used for the record delimiter of an output file represented by a TextIO object.

    public str outRecordDelimiter([str value])

#### Parameters

value  
The character to be used as the record delimiter; optional.

#### Return Value

The character used as the record delimiter.

#### Remarks

To set the record delimiter for an input file, use the .

#### Examples

The following example sets the record delimiter for an output file to '\\r\\n'.

    void defineFile() 
    { 
        diskFile = new TextIo(diskFileName,'W'); 
        if (!diskFile) 
        { 
            throw error("@SYS26757"); 
        } 
        diskFile.outRecordDelimiter('\r\n'); 
        diskFile.outFieldDelimiter(''); 
    }

### Method read

Reads the next full record from a TextIO object.

    public container read()

#### Return Value

A container that holds one record.

#### Remarks

Each entry in the container equals one field in the record. The definition of the next full record is controlled by the inFieldDelimiter, inRecordDelimiter, and inRecordLength properties. These properties have default values that allow input and output of the most common formats. It might be necessary to adjust the properties by using the inFieldDelimiter, inRecordDelimiter, and inRecordLength methods.

#### Examples

The following example reads a record from a file and uses the conpeek function to extract values from the record.

    public void run() 
    { 
        container         fileRecord; 
        IntrastatToProdCom intrastatToProdCom; 
        if (filename) 
        { 
            this.initializeFile(); 
            fileRecord = prodComFile.read(); 
            ttsbegin; 
            while (fileRecord) 
            { 
                intrastatToProdCom.IntrastatItemCodeID = conpeek(fileRecord, 1); 
                intrastatToProdCom.InventProdComCodeID = conpeek (fileRecord, 2); 
                intrastatToProdCom.ValidFromYear = conpeek (fileRecord, 3); 
                intrastatToProdCom.ValidTillYear = conpeek (fileRecord, 4); 
                intrastatToProdCom.insert(); 
                filerecord = prodComFile.read(); 
            } 
            ttscommit; 
        } 
    }

### Method status

Retrieves the status of the last operation performed on a TextIo object.

    public IO_Status status()

#### Return Value

The status of the last operation.

#### Examples

The following example throws an error if a file does not exist or if the last operation on the file did not have a status of the IO\_Status::Ok enumeration value.

    protected void checkDiskFileStatus() 
    { 
        if (!diskFile || diskFile.status() != IO_Status::Ok) 
        { 
            throw error(strfmt("@SYS76826", diskFileName)); 
        } 
    }

### Method write

Writes data to a file represented by a TextIO object.

    public boolean write(VarArg values)

#### Parameters

values  
The values to write to the file. The values can be of different data types.

#### Return Value

true if the write operation succeeds; otherwise, false.

#### Remarks

If the write operation fails, can be used to ascertain the cause. The write method accepts a variable number of arguments. Each value is put into the output record as a field. The fields are separated by the field delimiter specified by the . Each record is separated by the delimiter specified by the . To write complete containers, use the .

### Method writeChar

Writes a Unicode character to a file.

    public boolean writeChar(int int)

#### Parameters

int  

#### Return Value

true if the write operation succeeds; otherwise, false.

#### Remarks

If the write operation fails, the TextIO.status method can be used to check for the cause. To write multiple values or to write data of different types to a file, use the TextIO.write method.

### Method writeExp

Writes the contents of a container to a file represented by a TextIO object.

    public boolean writeExp(container data)

#### Parameters

data  
The container that has data to write to the file.

#### Return Value

true if the write operation succeeds; otherwise, false.

#### Remarks

If the write operation fails, the TextIo.status Method can be used to ascertain the cause. Entries in the container are separated by the delimiter set by the outFieldDelimiter method. Containers are separated by the delimiter set by the outRecordDelimiter method.

### Method writeRaw

Reserved.

    public boolean writeRaw(str data)

#### Parameters

data  

#### Return Value

### Method new

Creates a new instance of the TextIO class.

    public void new(str filename, str mode, [int codepage])

#### Parameters

filename  
The code page number for the character set to be read from or written to the file. The default value is 1200 (UTF-16LE). This parameter is optional. Following are the most common values: For more information about these options, see the list of http://go.microsoft.com/fwlink/?LinkID=78282&clcid=0x409. An error is reported if an invalid code page is requested. Notice that a code page is reported as "invalid" if it is not installed on the computer (different code pages may be installed on the client and server). For example, specifying code page 1253 for Greek fails unless the computer's ACP is Greek or Greek language support has been loaded by using Control Panel &gt; Regional Options.

<!-- -->

mode  
The code page number for the character set to be read from or written to the file. The default value is 1200 (UTF-16LE). This parameter is optional. Following are the most common values: For more information about these options, see the list of http://go.microsoft.com/fwlink/?LinkID=78282&clcid=0x409. An error is reported if an invalid code page is requested. Notice that a code page is reported as "invalid" if it is not installed on the computer (different code pages may be installed on the client and server). For example, specifying code page 1253 for Greek fails unless the computer's ACP is Greek or Greek language support has been loaded by using Control Panel &gt; Regional Options.

<!-- -->

codepage  
The code page number for the character set to be read from or written to the file. The default value is 1200 (UTF-16LE). This parameter is optional. Following are the most common values: For more information about these options, see the list of http://go.microsoft.com/fwlink/?LinkID=78282&clcid=0x409. An error is reported if an invalid code page is requested. Notice that a code page is reported as "invalid" if it is not installed on the computer (different code pages may be installed on the client and server). For example, specifying code page 1253 for Greek fails unless the computer's ACP is Greek or Greek language support has been loaded by using Control Panel &gt; Regional Options.

#### Remarks

A run-time error occurs if the file is accessed with a method that does not correspond to the current opened mode (for example, you try to write to a read-mode file). If an attacker can control input to the new method, a security risk exists. This method runs under Code Access Security. Calls to this method on the server require permission from the FileIoPermission class. Ensure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method. The following table describes some of the more common code pages that might be specified for the \_codePage parameter.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<tbody>
<tr class="odd">
<td>0</td>
<td>ANSI code page (ACP)</td>
<td>The code page that supports only characters in the user's current language. The code page is unsuitable for anything that might contain multilingual data or for monolingual data that might be transferred between two systems by using different code pages.</td>
</tr>
<tr class="even">
<td>437</td>
<td>OEM code page 437</td>
<td>The IBM PC or MS-DOS code page 437. It is often abbreviated as CP437 and also called DOS-US or OEM-US.</td>
</tr>
<tr class="odd">
<td>850</td>
<td>Code page 850</td>
<td>A code page that was used in Western Europe running on operating systems, such as MS-DOS.</td>
</tr>
<tr class="even">
<td>1200</td>
<td>UTF-16LE</td>
<td>The native Unicode representation on Microsoft Windows x86 systems. Almost all characters are stored as 16 bit. Some Chinese characters require 32 bit. An identifying byte-order mark is written, examined, and then discarded when the rest of the character is read.</td>
</tr>
<tr class="odd">
<td>1201</td>
<td>UTF-16BE</td>
<td>The same as UTF-16LE but byte-swapped. Used for compatibility with some non-x86 systems, which store bytes from left-to-right instead of low-order to high-order. An identifying byte-order mark is written first, examined, and then discarded when the rest of the character is read.</td>
</tr>
<tr class="even">
<td>65001</td>
<td>UTF-8</td>
<td>Stores Unicode in a byte-stream–friendly way:
<ul>
<li>ASCII characters are 1 byte</li>
<li>European alphabets (including basic diacritics) are 2 bytes per character</li>
<li>Chinese, Japanese, and Korean require 3 bytes per character</li>
</ul>
This code page is a good choice when a file contains a very high percentage of ASCII, relatively few other characters, and it is important to save space. For example, .xpo files are stored in UTF-8. UTF-8 files begin with a 3-byte byte-order mark sequence, which is the first item written. It is examined, and then discarded when the rest of the character is read.</td>
</tr>
<tr class="odd">
<td>54936</td>
<td>GB-18030</td>
<td>Stores data in the GB-18030 character representation that is required by the Chinese government. No byte-order mark is written. These files cannot be distinguished from those written in code page 20936 (GB-2312, which is the ACP for Simplified Chinese systems) unless the file contains characters outside the repertoire of GB-2312.</td>
</tr>
</tbody>
</table>

#### Examples

The following example creates a TextIO object to access a file that is named filename in read mode by using code page 850 encoding.

    protected void openFile(str _fileOpen = #io_read) 
    { 
        importFile = new TextIo(filename, _fileOpen, 850); 
        if (! importFile) 
        { 
            throw error(strfmt("@SYS18678", filename)); 
        } 
    }

### Method finalize

Closes the file and, if data was written, flushes the file buffers to disk.

    public void finalize()

#### Remarks

The TextIO object is usually finalized by leaving the scope. The finalize method is not usually directly called. Output written to the file is not valid until the TextIO object is finalized.

## Class TileReference
    class TileReference extends TreeNode

### Remarks

### Examples

### Methods

| Method                                              | Description |
|-----------------------------------------------------|-------------|
| public str tile()                                   |             |
| public int copyCallerQuery()                        |             |
| public int formViewOption()                         |             |
| public int openMode()                               |             |
| public str parameters()                             |             |
| public boolean isFound()                            |             |
| public ConfigurationKeyId configurationKeyId()      |             |
| public ConfigurationKeyId countryConfigurationKey() |             |
| public str countryRegionCodes()                     |             |
| public str helpText()                               |             |
| public int imageLocation()                          |             |
| public str kpiName()                                |             |
| public MenuItemType menuItemType()                  |             |
| public str menuItemName()                           |             |
| public str normalImage()                            |             |
| public int size()                                   |             |
| public int tileType()                               |             |
| public int tileDisplay()                            |             |
| public int buttonDisplay()                          |             |
| public str url()                                    |             |
| public str label()                                  |             |
| public int refreshFrequency()                       |             |
| public int applyFilter()                            |             |
| public int allowUserCacheRefresh()                  |             |
| public str query()                                  |             |
| public boolean visible(\[boolean value\])           |             |

### Method tile

    public str tile()

#### Return Value

### Method copyCallerQuery

    public int copyCallerQuery()

#### Return Value

### Method formViewOption

    public int formViewOption()

#### Return Value

### Method openMode

    public int openMode()

#### Return Value

### Method parameters

    public str parameters()

#### Return Value

### Method isFound

    public boolean isFound()

#### Return Value

### Method configurationKeyId

    public ConfigurationKeyId configurationKeyId()

#### Return Value

### Method countryConfigurationKey

    public ConfigurationKeyId countryConfigurationKey()

#### Return Value

### Method countryRegionCodes

    public str countryRegionCodes()

#### Return Value

### Method helpText

    public str helpText()

#### Return Value

### Method imageLocation

    public int imageLocation()

#### Return Value

### Method kpiName

    public str kpiName()

#### Return Value

### Method menuItemType

    public MenuItemType menuItemType()

#### Return Value

### Method menuItemName

    public str menuItemName()

#### Return Value

### Method normalImage

    public str normalImage()

#### Return Value

### Method size

    public int size()

#### Return Value

### Method tileType

    public int tileType()

#### Return Value

### Method tileDisplay

    public int tileDisplay()

#### Return Value

### Method buttonDisplay

    public int buttonDisplay()

#### Return Value

### Method url

    public str url()

#### Return Value

### Method label

    public str label()

#### Return Value

### Method refreshFrequency

    public int refreshFrequency()

#### Return Value

### Method applyFilter

    public int applyFilter()

#### Return Value

### Method allowUserCacheRefresh

    public int allowUserCacheRefresh()

#### Return Value

### Method query

    public str query()

#### Return Value

### Method visible

    public boolean visible([boolean value])

#### Parameters

value  

#### Return Value

## Class TreeNode
    class TreeNode extends Object

The TreeNode class retrieves and represents any node in the Application Object Tree (AOT).

### Remarks

This class, and the classes that extend it, enable you to create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before calling this API or APIs that are derived from this class. The TreeNode class can be used to get a handle to any node in the AOT. The TreeNode class is a generic class in that it can be a reference to any type of node in the AOT. In addition to providing access to some of the functions on the shortcut menu of the AOT, this class also contains methods that are used to maneuver in the tree. The TreeNodeTraverser class is also useful in navigating in the AOT. The TreeNode::findNode and TreeNode::rootNode methods return a treeNode object from which you can maneuver to any other node.

### Examples

### Methods

| Method                                                                                                                                              | Description                                                                                                                                                          |
|-----------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public TreeNode SysObsoleteAttribute(UtilElementName name)                                                                                          |                                                                                                                                                                      |
| public TreeNode SysObsoleteAttribute(str name, Types type)                                                                                          |                                                                                                                                                                      |
| public TreeNode SysObsoleteAttribute()                                                                                                              |                                                                                                                                                                      |
| public TreeNode SysObsoleteAttribute(int nodetype)                                                                                                  |                                                                                                                                                                      |
| public boolean AOTAllowEdit()                                                                                                                       |                                                                                                                                                                      |
| public int AOTbitmapId()                                                                                                                            | Returns the resource ID of the bitmap of the tree node.                                                                                                              |
| public int AOTchildNodeCount()                                                                                                                      | Counts the number of child nodes that a given tree node has.                                                                                                         |
| public boolean SysObsoleteAttribute(\[int flag\], \[boolean forceNoXRef\], \[boolean fastMode\])                                                    |                                                                                                                                                                      |
| public boolean AOTDrop(TreeNode sourcenode, \[TreeNode after\])                                                                                     | Creates a copy of a specified tree node as a child to the TreeNode object.                                                                                           |
| public TreeNode AOTDuplicate()                                                                                                                      |                                                                                                                                                                      |
| public TreeNode AOTfindChild(str name, \[int nodeType\])                                                                                            | Finds the specified child node of this node.                                                                                                                         |
| public TreeNode AOTfirstChild()                                                                                                                     | Retrieves the first child of the tree node.                                                                                                                          |
| public TreeNode AOTfirstChildEx(\[boolean loadFullNode\])                                                                                           |                                                                                                                                                                      |
| public int AOTgetExecutableLineCount()                                                                                                              | Returns the number of executable lines of code for this node.                                                                                                        |
| public Set AOTgetExecutableLines()                                                                                                                  | Returns the executable lines of code for this node.                                                                                                                  |
| public int AOTGetModel()                                                                                                                            |                                                                                                                                                                      |
| public str AOTgetProperties(\[boolean includeInvisible\], \[boolean includeReadOnly\], \[boolean includeNonExportable\])                            | Returns a string containing the properties of the tree node.                                                                                                         |
| public Struct AOTgetPropertiesExt(\[str filter\])                                                                                                   |                                                                                                                                                                      |
| public AnyType AOTgetProperty(str name)                                                                                                             |                                                                                                                                                                      |
| public str AOTgetSource()                                                                                                                           | Returns the source code of this node.                                                                                                                                |
| public boolean AOTIncludeInCompare()                                                                                                                |                                                                                                                                                                      |
| public boolean AOTIsDirty()                                                                                                                         |                                                                                                                                                                      |
| public boolean AOTIsOld()                                                                                                                           | Indicates whether this node is from a file found in the old model store.                                                                                             |
| public boolean AOTIsPersisted()                                                                                                                     | Indicates whether this node has been persisted in the model store.                                                                                                   |
| public boolean AOTIsProxyNode()                                                                                                                     |                                                                                                                                                                      |
| public TreeNodeIterator AOTiterator()                                                                                                               | Returns an object which can be used to iterate the child nodes of the tree node.                                                                                     |
| public KernelHelpType AOTKernelHelpType()                                                                                                           |                                                                                                                                                                      |
| public UtilEntryLevel AOTLayer()                                                                                                                    | Returns the layer of the tree node.                                                                                                                                  |
| public Set AOTLayers(\[boolean old\])                                                                                                               | Returns a collection of the layers the tree node is defined in.                                                                                                      |
| public str AOTname()                                                                                                                                | Returns the value of the name property of the node.                                                                                                                  |
| public int AOTnewWindow()                                                                                                                           | Opens a new AOT tree window with the tree node as the root.                                                                                                          |
| public TreeNode AOTnextSibling()                                                                                                                    | Returns the next node on the same level as the tree node.                                                                                                            |
| public boolean AOTObjectNode()                                                                                                                      | Indicates whether the node is an application object.                                                                                                                 |
| public int AOToverlayBitmapId()                                                                                                                     | Returns the resource ID of the overlay in the AOT associated with this node.                                                                                         |
| public TreeNode AOTparent()                                                                                                                         | Returns the parent node of the tree node.                                                                                                                            |
| public TreeNode AOTprevious()                                                                                                                       | Returns the previous sibling of this tree node.                                                                                                                      |
| public boolean SysObsoleteAttribute(str name)                                                                                                       |                                                                                                                                                                      |
| public str AOTtoolTip()                                                                                                                             | Returns the tool tip associated with the tree node.                                                                                                                  |
| public str AOTToString()                                                                                                                            |                                                                                                                                                                      |
| public str AOTtypeStr()                                                                                                                             | Returns the internal string code for the element type used in XPO files.                                                                                             |
| public UtilFileType AOTUtilFileType()                                                                                                               | Retrieves the value of the UtilFileType enumeration type for the TreeNode object. The UtilFileType indicates which kind of file the application object is stored in. |
| public int applObjectId()                                                                                                                           | Returns the application object ID, if applicable.                                                                                                                    |
| public int applObjectLayerMask()                                                                                                                    | Returns a bitmask that specifies which layers contain this element.                                                                                                  |
| public int applObjectOldLayerMask()                                                                                                                 | Returns a bitmask that specifies which layers contain this element in the baseline model store.                                                                      |
| public TreeNode getNodeInLayer(UtilEntryLevel layer, \[boolean old\])                                                                               | Retrieves a version of the tree node from a specified layer.                                                                                                         |
| public Int64 hashKey()                                                                                                                              |                                                                                                                                                                      |
| public TreeNode makeCopy()                                                                                                                          |                                                                                                                                                                      |
| public str newObjectName(\[str oldName\])                                                                                                           | Returns a string that contains the name of the new element.                                                                                                          |
| public str toString()                                                                                                                               | Returns a string that represents the current object.                                                                                                                 |
| public str treeNodeName()                                                                                                                           | Returns the name of the tree node.                                                                                                                                   |
| public str treeNodePath()                                                                                                                           | Returns the unique path to the tree node within the Application Object Tree (AOT).                                                                                   |
| public TreeNodeType treeNodeType()                                                                                                                  | Retrieves an instance of a TreeNodeType class that provides reflection information for the tree node.                                                                |
| public int updateNodePermissions(boolean throwExceptions)                                                                                           |                                                                                                                                                                      |
| public UtilElements utilElement()                                                                                                                   | Returns a UtilElements record that is related to the node.                                                                                                           |
| public UtilIdElements utilIdElement()                                                                                                               | Returns a UtilIdElements record that is related to the node.                                                                                                         |
| public boolean validateNameCharacters(str name)                                                                                                     |                                                                                                                                                                      |
| ::public static TreeNode findNode(str path)                                                                                                         | Returns a specified node in the Application Object Tree (AOT).                                                                                                       |
| ::public static str generateObjectName(str template)                                                                                                |                                                                                                                                                                      |
| ::public static int getMaximumNodeNameLength(int modelElementTypeId)                                                                                |                                                                                                                                                                      |
| ::public static boolean isNodeReferenceValid(TreeNode treeNode)                                                                                     |                                                                                                                                                                      |
| ::public static boolean isValidObjectName(str name)                                                                                                 | Determines whether the string passed as an argument can be used as a name for a node in the Application Object Tree (AOT).                                           |
| ::public static TreeNode rootNode()                                                                                                                 | Returns the root node of the AOT.                                                                                                                                    |
| public void SysObsoleteAttribute()                                                                                                                  |                                                                                                                                                                      |
| public void treeNodeRelease()                                                                                                                       | Releases the tree node explicitly.                                                                                                                                   |
| public void SysObsoleteAttribute(str name, xRefKind xrefKind, int lineNumber, int columNumber, \[XRefReference xrefRef\], \[ClassId parentTypeId\]) |                                                                                                                                                                      |
| public void AOTrun()                                                                                                                                | Compiles this node and its subtree in the Application Object Tree (AOT).                                                                                             |
| public void SysObsoleteAttribute()                                                                                                                  |                                                                                                                                                                      |
| public void AOTrefresh()                                                                                                                            | Refreshes the node with the latest changes to the .aod file.                                                                                                         |
| public void SysObsoleteAttribute(Struct struct1)                                                                                                    |                                                                                                                                                                      |
| public void SysObsoleteAttribute(str properties)                                                                                                    |                                                                                                                                                                      |
| public void AOTconfigure()                                                                                                                          |                                                                                                                                                                      |
| public void AOTload()                                                                                                                               | Ensures that the object is loaded.                                                                                                                                   |
| public void treeNodeExport(str filename, \[int flag\])                                                                                              | Exports this node and its subtree from the Application Object Tree (AOT).                                                                                            |
| public void SysObsoleteAttribute(str source, \[boolean isStatic\])                                                                                  |                                                                                                                                                                      |
| public void AOTendXref()                                                                                                                            |                                                                                                                                                                      |
| public void AOTmessageLine(str text, int linenumber)                                                                                                | Writes text to the Application Object Tree (AOT) Message window.                                                                                                     |
| public void SysObsoleteAttribute(str name, AnyType value)                                                                                           |                                                                                                                                                                      |
| public void AOTrestore(\[boolean forceReload\])                                                                                                     | Reloads this node from the disk, if applicable.                                                                                                                      |
| public void AOTregenerate()                                                                                                                         |                                                                                                                                                                      |
| public void AOTmakeXref(\[int flag\], \[boolean xRefAll\])                                                                                          | Compiles this node and its subtree in the AOT, updating the cross-reference system.                                                                                  |
| public void AOTedit(\[int Line\], \[int Column\])                                                                                                   | Opens the appropriate editor for this node.                                                                                                                          |
| public void AOTshowProperties()                                                                                                                     | Opens the property sheet (if not already open) and shows the properties for this node.                                                                               |
| public void AOTinsert(TreeNode parent, \[TreeNode after\], \[boolean doNotDuplicate\])                                                              | Inserts a node among the subnodes of this node.                                                                                                                      |
| public void new()                                                                                                                                   | Initializes a new instance of the TreeNode class.                                                                                                                    |
| public void AOTMove(TreeNode parent, \[TreeNode after\])                                                                                            |                                                                                                                                                                      |
| public void SysObsoleteAttribute(int modelId)                                                                                                       |                                                                                                                                                                      |

### Method SysObsoleteAttribute

    public TreeNode SysObsoleteAttribute(UtilElementName name)

#### Parameters

name  

#### Return Value

### Method SysObsoleteAttribute

    public TreeNode SysObsoleteAttribute(str name, Types type)

#### Parameters

name  

<!-- -->

type  

#### Return Value

### Method SysObsoleteAttribute

    public TreeNode SysObsoleteAttribute()

#### Return Value

### Method SysObsoleteAttribute

    public TreeNode SysObsoleteAttribute(int nodetype)

#### Parameters

nodetype  

#### Return Value

### Method AOTAllowEdit

    public boolean AOTAllowEdit()

#### Return Value

### Method AOTbitmapId

Returns the resource ID of the bitmap of the tree node.

    public int AOTbitmapId()

#### Return Value

The resource ID of the bitmap of the tree node.

#### Examples

The following example prints the resource ID of the Extended Data Types node in the Application Object Tree (AOT).

    #AOT 
    static void myJobAOTbitmapId(Args _args) 
    { 
        treeNode treeNode = TreeNode::findNode(#ExtendedDataTypesPath); 
        print treeNode.AOTbitmapId(); 
        pause; 
    }

This job will print the integer 895. If you run the Tutorial resources form, you can see the bitmap and verify that it is the same as the one that is used for Extended Data Types in the AOT.

### Method AOTchildNodeCount

Counts the number of child nodes that a given tree node has.

    public int AOTchildNodeCount()

#### Return Value

An integer that indicates the number of child nodes for the tree node.

#### Examples

The following example prints the number of child nodes that appear under the Menu Items node in the Application Object Tree (AOT).

    #AOT 
    static void myJobAOTchildNodeCount(Args _args) 
    { 
        treeNode treeNode = TreeNode::findNode(#MenuItemsPath); 
        print "Number of nodes below Menu Items: ", treeNode.AOTchildNodeCount(); 
        pause; 
    }

### Method SysObsoleteAttribute

    public boolean SysObsoleteAttribute([int flag], [boolean forceNoXRef], [boolean fastMode])

#### Parameters

flag  

<!-- -->

forceNoXRef  

<!-- -->

fastMode  

#### Return Value

### Method AOTDrop

Creates a copy of a specified tree node as a child to the TreeNode object.

    public boolean AOTDrop(TreeNode sourcenode, [TreeNode after])

#### Parameters

sourcenode  
The child node of the tree node that the source should be inserted after; optional.

<!-- -->

after  
The child node of the tree node that the source should be inserted after; optional.

#### Return Value

true if the drop operation was successful; otherwise, false.

#### Examples

The following example creates the tabPage:CopyOfContainers tree node as the last node underTab:Tab in the tutorial\_Form\_Controls form.

    #AOT 
    static void myJobAOTDrop(Args _args) 
    { 
        treeNode treeNodeTab; 
        treeNode treeNodeTabPageContainers; 
        treeNodeTab = TreeNode::findNode(#FormsPath + '\\' +  
            formStr(tutorial_form_controls)+ '\\Designs\\Design\\[Tab:Tab]'); 
        treeNodeTabPageContainers = TreeNode::findNode(#FormsPath + '\\' +  
            formStr(tutorial_form_controls)+  
            '\\Designs\\Design\\[Tab:Tab]\\[TabPage:Containers]'); 
        if (treeNodeTab && treeNodeTabPageContainers) 
        { 
            // Drop the TabPage:Containers node on the Tab:Tab node. 
            print treeNodeTab.AOTDrop(treeNodeTabPageContainers); 
        } 
        else 
        { 
            print "Could not find treeNodeTab or treeNodeTabPageContainers"; 
        } 
        pause; 
    }

### Method AOTDuplicate

    public TreeNode AOTDuplicate()

#### Return Value

### Method AOTfindChild

Finds the specified child node of this node.

    public TreeNode AOTfindChild(str name, [int nodeType])

#### Parameters

name  

<!-- -->

nodeType  

#### Return Value

The specified TreeNode.

### Method AOTfirstChild

Retrieves the first child of the tree node.

    public TreeNode AOTfirstChild()

#### Return Value

The first child node of the tree node.

### Method AOTfirstChildEx

    public TreeNode AOTfirstChildEx([boolean loadFullNode])

#### Parameters

loadFullNode  

#### Return Value

### Method AOTgetExecutableLineCount

Returns the number of executable lines of code for this node.

    public int AOTgetExecutableLineCount()

#### Return Value

The number of executable lines of code for this node if any; otherwise, zero.

#### Remarks

This function calls a method which is overridden by nodes which have source code.

### Method AOTgetExecutableLines

Returns the executable lines of code for this node.

    public Set AOTgetExecutableLines()

#### Return Value

A Set object containing the executable lines of code for this node if any; otherwise, nullNothingnullptrunita null reference (Nothing in Visual Basic).

#### Remarks

This function calls a method which is overridden by nodes which have source code.

### Method AOTGetModel

    public int AOTGetModel()

#### Return Value

### Method AOTgetProperties

Returns a string containing the properties of the tree node.

    public str AOTgetProperties([boolean includeInvisible], [boolean includeReadOnly], [boolean includeNonExportable])

#### Parameters

includeInvisible  

<!-- -->

includeReadOnly  

<!-- -->

includeNonExportable  

#### Return Value

A string containing the properties of the tree node.

#### Examples

The following example provides a list of temporary tables in Microsoft Dynamics AX.

    { 
        #aot 
        #properties 
        TreeNode        tn = TreeNode::findNode(#TablesPath); 
        str             tableName; 
        str             temporaryProperty; 
        tn = tn.AOTfirstChild(); 
        while (tn) 
        { 
            tableName = findProperty(tn.AOTgetProperties(), #PropertyName); 
            temporaryProperty = findProperty( 
                tn.AOTgetProperties(), 
                #PropertyTemporary); 
            info (strfmt( 
                'Table %1 has the temporary property specified as %2', 
                tableName, temporaryProperty)); 
            tn = tn.AOTnextSibling(); 
        } 
    }

### Method AOTgetPropertiesExt

    public Struct AOTgetPropertiesExt([str filter])

#### Parameters

filter  

#### Return Value

### Method AOTgetProperty

    public AnyType AOTgetProperty(str name)

#### Parameters

name  

#### Return Value

### Method AOTgetSource

Returns the source code of this node.

    public str AOTgetSource()

#### Return Value

The string that contains source code if any; otherwise, nullNothingnullptrunita null reference (Nothing in Visual Basic).

#### Remarks

This function is overridden by nodes which have source code.

### Method AOTIncludeInCompare

    public boolean AOTIncludeInCompare()

#### Return Value

### Method AOTIsDirty

    public boolean AOTIsDirty()

#### Return Value

### Method AOTIsOld

Indicates whether this node is from a file found in the old model store.

    public boolean AOTIsOld()

#### Return Value

true if this node is from the old model store; otherwise false.

### Method AOTIsPersisted

Indicates whether this node has been persisted in the model store.

    public boolean AOTIsPersisted()

#### Return Value

true if this node has been persisted; otherwise false.

#### Remarks

This method throws an exception if the method is not supported for the tree node. Use the TreeNode.TreeNodeType().isModelElement() method to determine if the method is supported.

### Method AOTIsProxyNode

    public boolean AOTIsProxyNode()

#### Return Value

### Method AOTiterator

Returns an object which can be used to iterate the child nodes of the tree node.

    public TreeNodeIterator AOTiterator()

#### Return Value

The TreeNodeIterator object used to iterate the children of the tree node.

### Method AOTKernelHelpType

    public KernelHelpType AOTKernelHelpType()

#### Return Value

### Method AOTLayer

Returns the layer of the tree node.

    public UtilEntryLevel AOTLayer()

#### Return Value

The layer that this node resides in.

#### Remarks

This method throws an exception if the method is not supported for the tree node. Use the TreeNode.TreeNodeType().isLayerAware() method to determine if the method is supported.

### Method AOTLayers

Returns a collection of the layers the tree node is defined in.

    public Set AOTLayers([boolean old])

#### Parameters

old  
A Boolean value that indicates whether to return the layers of the tree node definitions from the old model store; optional.

#### Return Value

A Set object with the layers.

#### Remarks

This method throws an exception if the method is not supported for the tree node. Use the TreeNode.TreeNodeType().isLayerAware() method to determine if the method is supported.

### Method AOTname

Returns the value of the name property of the node.

    public str AOTname()

#### Return Value

The string that contains the value of the name property

#### Remarks

In most cases, this yields the same result as the method TreeNodeName.

#### Examples

The following example prints out the name of the first child of the tree node.

    static void Job(Args _args) 
    { 
        treeNode t = infolog.findNode('\\Reports\\AssetAcquisition\\Designs\\ReportDesign1\\AutoDesignSpecs'); 
        t = t.AOTfirstChild(); 
        print "treeNodeName: " + t.treeNodeName(); 
        print "AOTName:" + t.AOTName(); 
        pause; 
    }

### Method AOTnewWindow

Opens a new AOT tree window with the tree node as the root.

    public int AOTnewWindow()

#### Return Value

### Method AOTnextSibling

Returns the next node on the same level as the tree node.

    public TreeNode AOTnextSibling()

#### Return Value

The next node on the same level as the current tree node.

### Method AOTObjectNode

Indicates whether the node is an application object.

    public boolean AOTObjectNode()

#### Return Value

true if the node is an application object; otherwise false.

#### Remarks

A form or report is an application object. A control on a form, or any other subpart, is not.

### Method AOToverlayBitmapId

Returns the resource ID of the overlay in the AOT associated with this node.

    public int AOToverlayBitmapId()

#### Return Value

The resource ID of the overlay in the AOT associated with this node.

### Method AOTparent

Returns the parent node of the tree node.

    public TreeNode AOTparent()

#### Return Value

The parent node of the tree node.

### Method AOTprevious

Returns the previous sibling of this tree node.

    public TreeNode AOTprevious()

#### Return Value

The previous tree node relative to this one on the same level.

### Method SysObsoleteAttribute

    public boolean SysObsoleteAttribute(str name)

#### Parameters

name  

#### Return Value

### Method AOTtoolTip

Returns the tool tip associated with the tree node.

    public str AOTtoolTip()

#### Return Value

The string that contains the tool tip.

### Method AOTToString

    public str AOTToString()

#### Return Value

### Method AOTtypeStr

Returns the internal string code for the element type used in XPO files.

    public str AOTtypeStr()

#### Return Value

The string that contains the tree node type.

### Method AOTUtilFileType

Retrieves the value of the UtilFileType enumeration type for the TreeNode object. The UtilFileType indicates which kind of file the application object is stored in.

    public UtilFileType AOTUtilFileType()

#### Return Value

The value of the UtilFileType enumeration for the tree node. The possible values are in the following list. UtilFileType::Application means that the element is stored in the .aod file (form, report, query, table, and so on). UtilFileType::ApplicationCodeDocumentationmeans that the element is stored in the .add file. UtilFileType::ApplicationHelp means that the element is stored in the .ahd file. UtilFileType::KernelHelp means that the element is stored in the .akh file.

#### Examples

The following example finds a TreeNode object of each UtilFileType, and then prints the path of the UtilFileType to the Infolog.

    static void myJob(Args _args) 
    { 
        treeNode tn; 
        tn = treeNode::findNode("\\Forms"); 
        tn = tn.AOTfirstChild(); 
        info(strfmt( 
             "Path: %1 \nUtilFileType: %2", 
             tn.treeNodePath(), 
             tn.AOTUtilFileType())); 
        tn = treeNode::findNode("\\System Documentation"); 
        tn = tn.AOTfirstChild(); 
        tn = tn.AOTfirstChild(); 
        info(strfmt( 
             "Path: %1 \nUtilFileType: %2", 
             tn.treeNodePath(), 
             tn.AOTUtilFileType())); 
        tn = treeNode::findNode("\\Application Developer Documentation"); 
        tn = tn.AOTfirstChild(); 
        tn = tn.AOTfirstChild(); 
        info(strfmt( 
            "Path: %1 \nUtilFileType: %2", 
            tn.treeNodePath(), 
            tn.AOTUtilFileType())); 
        tn = treeNode::findNode("\\Application Documentation"); 
        tn = tn.AOTfirstChild(); 
        tn = tn.AOTfirstChild(); 
        info(strfmt( 
            "Path: %1 \nUtilFileType: %2", 
            tn.treeNodePath(), 
            tn.AOTUtilFileType())); 
    }

### Method applObjectId

Returns the application object ID, if applicable.

    public int applObjectId()

#### Return Value

The ID of the application object.

### Method applObjectLayerMask

Returns a bitmask that specifies which layers contain this element.

    public int applObjectLayerMask()

#### Return Value

A bitmask that specifies which layers contain this element.

### Method applObjectOldLayerMask

Returns a bitmask that specifies which layers contain this element in the baseline model store.

    public int applObjectOldLayerMask()

#### Return Value

A bitmask that specifies which layers contain this element.

### Method getNodeInLayer

Retrieves a version of the tree node from a specified layer.

    public TreeNode getNodeInLayer(UtilEntryLevel layer, [boolean old])

#### Parameters

layer  
The value specifying whether or not the node should be retrieved from the layer file in the old model store; optional.

<!-- -->

old  
The value specifying whether or not the node should be retrieved from the layer file in the old model store; optional.

#### Return Value

The new TreeNode.

#### Remarks

This method throws an exception if the method is not supported for the tree node. Use the TreeNode.TreeNodeType().isGetNodeInLayerSupported method to determine if the method is supported.

### Method hashKey

    public Int64 hashKey()

#### Return Value

### Method makeCopy

    public TreeNode makeCopy()

#### Return Value

### Method newObjectName

Returns a string that contains the name of the new element.

    public str newObjectName([str oldName])

#### Parameters

oldName  
The new name of the node; optional. If no argument is passed, the new node name is determined by the child node type.

#### Return Value

The string that contains the name of the new element.

#### Remarks

If no argument is passed, the new node name is determined by the child node type. For example, if the TreeNode has forms as children, calling this method without an argument will return "Form1". If the tree node has several child node types, the method returns the string "object".

#### Examples

The following call to Treenode.newObjectName returns "object" because the data dictionary node has children that represent several object types.

    { 
        TreeNode t; 
        str s; 
        t = TreeNode::findNode("\Data dictionary"); 
        s = t.newObjectName(); 
        print s; 
        pause; 
    }

### Method toString

Returns a string that represents the current object.

    public str toString()

#### Return Value

A string that represents the current object.

#### Remarks

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type.For example, an instance of the class returns the method name and type of the method, such as instance or static.

### Method treeNodeName

Returns the name of the tree node.

    public str treeNodeName()

#### Return Value

The string that contains the name of the tree node.

### Method treeNodePath

Returns the unique path to the tree node within the Application Object Tree (AOT).

    public str treeNodePath()

#### Return Value

Returns the unique path of the tree node in the AOT.

#### Examples

The following example finds a TreeNode object of each UtilFileType and prints the path of the UtilFileType to the Infolog.

    static void myJob(Args _args) 
    { 
        treeNode tn; 
        tn = treeNode::findNode("\\Forms"); 
        tn = tn.AOTfirstChild(); 
        info(strfmt( 
             "Path: %1 \nUtilFileType: %2", 
             tn.treeNodePath(), 
             tn.AOTUtilFileType())); 
        tn = treeNode::findNode("\\System Documentation"); 
        tn = tn.AOTfirstChild(); 
        tn = tn.AOTfirstChild(); 
        info(strfmt( 
             "Path: %1 \nUtilFileType: %2", 
             tn.treeNodePath(), 
             tn.AOTUtilFileType())); 
        tn = treeNode::findNode("\\Application Developer Documentation"); 
        tn = tn.AOTfirstChild(); 
        tn = tn.AOTfirstChild(); 
        info(strfmt( 
            "Path: %1 \nUtilFileType: %2", 
            tn.treeNodePath(), 
            tn.AOTUtilFileType())); 
        tn = treeNode::findNode("\\Application Documentation"); 
        tn = tn.AOTfirstChild(); 
        tn = tn.AOTfirstChild(); 
        info(strfmt( 
            "Path: %1 \nUtilFileType: %2", 
            tn.treeNodePath(), 
            tn.AOTUtilFileType())); 
    }

### Method treeNodeType

Retrieves an instance of a TreeNodeType class that provides reflection information for the tree node.

    public TreeNodeType treeNodeType()

#### Return Value

An instance of a TreeNodeType class.

### Method updateNodePermissions

    public int updateNodePermissions(boolean throwExceptions)

#### Parameters

throwExceptions  

#### Return Value

### Method utilElement

Returns a UtilElements record that is related to the node.

    public UtilElements utilElement()

#### Return Value

The UtilElements record that is related to the node.

#### Remarks

This method throws an exception if the method is not supported for the tree node.

### Method utilIdElement

Returns a UtilIdElements record that is related to the node.

    public UtilIdElements utilIdElement()

#### Return Value

The UtilIdElements record that is related to the node.

#### Remarks

This method throws an exception if the method is not supported for the tree node.

### Method validateNameCharacters

    public boolean validateNameCharacters(str name)

#### Parameters

name  

#### Return Value

### Method findNode

Returns a specified node in the Application Object Tree (AOT).

    public static TreeNode findNode(str path)

#### Parameters

path  
A string that indicates the path that is used in the search.

#### Return Value

The requested TreeNode object or nullNothingnullptrunita null reference (Nothing in Visual Basic) if no node with the specified path exists.

#### Remarks

Another way of getting a TreeNode object is by using the Info.getNode method. An important difference between the two methods is that the Info.getNode method will give you a node that is detached from the AOT, whereas the findNode method will return the node in the AOT. This means that the node that is returned by the Info.getNode method will not have a parent node, whereas the one returned by the findNode method will have a parent node.

#### Examples

The following example retrieves the name of the tree node that is found the TreeNode::findNode method is called. This example checks whether the user has the required security key before it calls the TreeNode.findNode method.

    server static public void Main(Args _args) 
    { 
        TreeNode tn; 
        str name; 
        tn = TreeNode::findNode(@"\Classes"); 
        if (tn) 
        { 
            name = tn.treeNodeName(); 
        } 
    }

### Method generateObjectName

    public static str generateObjectName(str template)

#### Parameters

template  

#### Return Value

### Method getMaximumNodeNameLength

    public static int getMaximumNodeNameLength(int modelElementTypeId)

#### Parameters

modelElementTypeId  

#### Return Value

### Method isNodeReferenceValid

    public static boolean isNodeReferenceValid(TreeNode treeNode)

#### Parameters

treeNode  

#### Return Value

### Method isValidObjectName

Determines whether the string passed as an argument can be used as a name for a node in the Application Object Tree (AOT).

    public static boolean isValidObjectName(str name)

#### Parameters

name  
The string that contains the tree node name to validate.

#### Return Value

true if each condition is met; otherwise false.

#### Remarks

A candidate name must meet the following conditions:

-   The first character must be a letter.
-   It can only contain letters, numbers or an underscore.
-   It must not evaluate to a token.

This method does not check if an element of the same name already exists. It only validates that the argument is a valid name for an AOT object. Duplicate names may not exist within classes, tables, extended data types, or enums.

#### Examples

The following example gives examples of valid and invalid arguments.

    boolean validName; 
    validName = TreeNode::isValidObjectName('ValidName'); //true 
    validName = TreeNode::isValidObjectName('Name with spaces'); //false 
    validName = TreeNode::isValidObjectName('4StartsWithDigit'); //false 
    validName = TreeNode::isValidObjectName('Illegal;Character'); //false 
    validName = TreeNode::isValidObjectName('if'); // false (token name)

### Method rootNode

Returns the root node of the AOT.

    public static TreeNode rootNode()

#### Return Value

The root node of the AOT.

#### Remarks

The method provides similar functionality to the rootNode method.

### Method SysObsoleteAttribute

    public void SysObsoleteAttribute()

### Method treeNodeRelease

Releases the tree node explicitly.

    public void treeNodeRelease()

#### Remarks

Usually you do not have to explicitly unload objects, because the garbage collector will do it automatically. However, because tree nodes are ordinarily linked to the AOT, they are not garbage-collected. If you run this method on many tree nodes in the same execution, it can be demanding on resources. You should unload the tree nodes as you go along to give the garbage collector a chance to remove them. Make sure to remove all references to the tree node and its subnodes before you call this method. Use the TreeNode.TreeNodeType().isConsumingMemory method to determine if you need to call this method.

### Method SysObsoleteAttribute

    public void SysObsoleteAttribute(str name, xRefKind xrefKind, int lineNumber, int columNumber, [XRefReference xrefRef], [ClassId parentTypeId])

#### Parameters

name  

<!-- -->

xrefKind  

<!-- -->

lineNumber  

<!-- -->

columNumber  

<!-- -->

xrefRef  

<!-- -->

parentTypeId  

### Method AOTrun

Compiles this node and its subtree in the Application Object Tree (AOT).

    public void AOTrun()

### Method SysObsoleteAttribute

    public void SysObsoleteAttribute()

### Method AOTrefresh

Refreshes the node with the latest changes to the .aod file.

    public void AOTrefresh()

### Method SysObsoleteAttribute

    public void SysObsoleteAttribute(Struct struct1)

#### Parameters

struct1  

### Method SysObsoleteAttribute

    public void SysObsoleteAttribute(str properties)

#### Parameters

properties  

### Method AOTconfigure

    public void AOTconfigure()

### Method AOTload

Ensures that the object is loaded.

    public void AOTload()

### Method treeNodeExport

Exports this node and its subtree from the Application Object Tree (AOT).

    public void treeNodeExport(str filename, [int flag])

#### Parameters

filename  

<!-- -->

flag  

#### Remarks

If an attacker can control input to this method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission from the . Ensure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

#### Examples

This example uses the treeNodeExport method to export the ExampleClass class to an .xpo file.

    void TreeNodeExample() 
    { 
        TreeNode treeNode; 
        TreeNode childNode; 
        FileIoPermission perm; 
        #define.ExportFile(@"c:\TreeNodeExportExampleClass.xpo") 
        #define.ExportMode("w") 
        perm = new FileIoPermission(#ExportFile, #ExportMode); 
        if (perm == null) 
        { 
            return; 
        } 
        perm.assert(); 
        treeNode = TreeNode::findNode(@"\Classes"); 
        if (treeNode != null) 
        { 
            childNode = treeNode.AOTfindChild(@"ExampleClass"); 
            // BP deviation documented. 
            childNode.treeNodeExport(#ExportFile); 
        } 
        CodeAccessPermission::revertAssert(); 
    }

### Method SysObsoleteAttribute

    public void SysObsoleteAttribute(str source, [boolean isStatic])

#### Parameters

source  

<!-- -->

isStatic  

### Method AOTendXref

    public void AOTendXref()

### Method AOTmessageLine

Writes text to the Application Object Tree (AOT) Message window.

    public void AOTmessageLine(str text, int linenumber)

#### Parameters

text  
An integer that is ignored. It does not currently direct the written text to a specific line number in the output Message window.

<!-- -->

linenumber  
An integer that is ignored. It does not currently direct the written text to a specific line number in the output Message window.

#### Remarks

This method is intended to be used to output text so that when the user later double-clicks that line of text in the message window, some action will happen regarding this node.

#### Examples

The following example executes the AOTmessageLine method on a Form object, because Form inherits this method from TreeNode.

    static void JobAOTmessageLineDemo(Args _args) 
    { 
        Form f = new Form('testAOTMessageLine'); 
        // 
        f.AOTmessageLine('test message 1a',1); 
        f.AOTmessageLine('test message 2a',2); 
        f.AOTmessageLine('test message 3a',3); 
        f.AOTmessageLine('test message 1b',1); 
        f.AOTmessageLine('test message 2b',2); 
        f.AOTmessageLine('test message 3b',3); 
        f.AOTmessageLine('test message 2c',2); 
        // 
        /******* 
        Actual Output in the Message window 
        (the 7 identical lines): 
        test message 2c 
        test message 2c 
        test message 2c 
        test message 2c 
        test message 2c 
        test message 2c 
        test message 2c 
        *******/ 
    }

### Method SysObsoleteAttribute

    public void SysObsoleteAttribute(str name, AnyType value)

#### Parameters

name  

<!-- -->

value  

### Method AOTrestore

Reloads this node from the disk, if applicable.

    public void AOTrestore([boolean forceReload])

#### Parameters

forceReload  

### Method AOTregenerate

    public void AOTregenerate()

### Method AOTmakeXref

Compiles this node and its subtree in the AOT, updating the cross-reference system.

    public void AOTmakeXref([int flag], [boolean xRefAll])

#### Parameters

flag  

<!-- -->

xRefAll  

#### Remarks

This method can be called at any:

-   list node (such as AOT, Tables, Forms, Project roots, and groups)
-   Application Object (such as a Table or Form)
-   methods branch
-   method

### Method AOTedit

Opens the appropriate editor for this node.

    public void AOTedit([int Line], [int Column])

#### Parameters

Line  
The column of the cursor position; optional.

<!-- -->

Column  
The column of the cursor position; optional.

#### Remarks

If the node is a method, the code editor will open. If the node is a documentation object, the Help editor will open.

#### Examples

The following code example opens the X++ editor, shows the class declaration of the class Tax, and positions the pointer at line 6, column 8.

    #AOT 
    static void myJobAOTEdit(Args _args) 
    { 
        treeNode treeNode; 
        treeNode = TreeNode::findNode(#ClassesPath + '\\' + classStr(Tax)+ '\\ClassDeclaration'); 
        if (treeNode) 
        { 
            treeNode.AOTedit(6,8); 
        } 
        else 
        { 
            print "Could not find treeNode"; 
        } 
        pause; 
    }

### Method AOTshowProperties

Opens the property sheet (if not already open) and shows the properties for this node.

    public void AOTshowProperties()

### Method AOTinsert

Inserts a node among the subnodes of this node.

    public void AOTinsert(TreeNode parent, [TreeNode after], [boolean doNotDuplicate])

#### Parameters

parent  

<!-- -->

after  

<!-- -->

doNotDuplicate  

### Method new

Initializes a new instance of the TreeNode class.

    public void new()

### Method AOTMove

    public void AOTMove(TreeNode parent, [TreeNode after])

#### Parameters

parent  

<!-- -->

after  

### Method SysObsoleteAttribute

    public void SysObsoleteAttribute(int modelId)

#### Parameters

modelId  

## Class TreeNodeIterator
    class TreeNodeIterator extends Object

The TreeNodeIterator class traverses the child nodes of a tree node.

### Remarks

### Examples

The following example prints the names of all child nodes of the root node.

    static void example()  
    { 
        treeNode myTreeNode; 
        xInfo xi = new xInfo(); 
        void printChildNames (treeNode t) 
        { 
            treeNode child; 
            treenodeIterator it; 
            it = t.AOTiterator(); 
            child = it.next(); 
            while (child) 
            { 
                print child.treeNodeName(); 
                child = it.next(); 
            } 
        } 
        myTreeNode = xi.rootNode(); 
        printChildNames(myTreeNode); 
        pause; 
    }

### Methods

| Method                 | Description                                                                                            |
|------------------------|--------------------------------------------------------------------------------------------------------|
| public TreeNode next() | Retrieves the next element in the list of child nodes.                                                 |
| public void reset()    | Resets the iterator so that the next call to the next method returns the first child node in the list. |

### Method next

Retrieves the next element in the list of child nodes.

    public TreeNode next()

#### Return Value

The next child node in the tree.

### Method reset

Resets the iterator so that the next call to the next method returns the first child node in the list.

    public void reset()

## Class TreeNodeType
    class TreeNodeType extends Object

The TreeNodeType class retrieves information about types of TreeNode classes.

### Remarks

This class enable you to reflect on a TreeNode class instance. The reflection information is not specific to an instance of a TreeNode class. All TreeNode instances with the same NodeType share the same TreeNodeType. The TreeNode.TreeNodeType method return a treeNodeType object with the reflection informantion.

### Examples

### Methods

| Method                                     | Description                                                                                            |
|--------------------------------------------|--------------------------------------------------------------------------------------------------------|
| public int id()                            | Returns the type's ID.                                                                                 |
| public boolean isConsumingMemory()         | Indicates whether instances of this node type are consuming memory that needs to be manually released. |
| public boolean isGetNodeInLayerSupported() | Indicates whether instances of this node type support the TreeNode.GetNodeInLayer method.              |
| public boolean isLayerAware()              | Indicates whether instances of this node type are decorated with layers in the AOT.                    |
| public boolean isModelElement()            | Indicates whether instances of this node type are model-elements.                                      |
| public boolean isRootElement()             | Indicates whether instances of this node type are root-elements.                                       |
| public boolean isUtilElement()             | Indicates whether instances of this node type are util-elements.                                       |
| public boolean isVCSControllableElement()  |                                                                                                        |
| private void new()                         | Initializes a new instance of the TreeNodeType class.                                                  |

### Method id

Returns the type's ID.

    public int id()

#### Return Value

The ID of the TreeNodeType.

### Method isConsumingMemory

Indicates whether instances of this node type are consuming memory that needs to be manually released.

    public boolean isConsumingMemory()

#### Return Value

true if tree nodes of this type are consumes memory; otherwise, false.

#### Remarks

After working with TreeNode instances of this type it is important to call the TreeNode.TreeNodeRelease method to release any consumed memory. Failure to do this will result in out-of-memory exceptions. Do not call the TreeNode.TreeNodeRelease method before all instances of TreeNode classes in the composition hierarchy has been garbage collected. For example, do not call the TreeNode.TreeNodeRelease() method on MyClass, if you still have a TreeNode instance of MyClass.myMethod.

### Method isGetNodeInLayerSupported

Indicates whether instances of this node type support the TreeNode.GetNodeInLayer method.

    public boolean isGetNodeInLayerSupported()

#### Return Value

true if tree nodes of this type support the TreeNode.GetNodeInLayer method; otherwise, false.

### Method isLayerAware

Indicates whether instances of this node type are decorated with layers in the AOT.

    public boolean isLayerAware()

#### Return Value

true if tree nodes of this type are decorated with layers; otherwise, false.

#### Remarks

Tree nodes of this type support the AOTLayer and AOTLayers methods.

### Method isModelElement

Indicates whether instances of this node type are model-elements.

    public boolean isModelElement()

#### Return Value

true if tree nodes of this type are model-elements; otherwise, false.

#### Remarks

A model-element is a tree node that is (or can be) persisted in the model store. For each model-element tree node one record can be found in the ModelElements table in the model store. Model-elements are visually decorated with the name of the Model they are contained by in the AOT.

### Method isRootElement

Indicates whether instances of this node type are root-elements.

    public boolean isRootElement()

#### Return Value

true if tree nodes of this type are root-elements; otherwise, false.

#### Remarks

A root-element is the root in a composition hierarchy of tree nodes. A root-element never has a model-element parent. Examples include MyTable, MyClass, MyForm.

### Method isUtilElement

Indicates whether instances of this node type are util-elements.

    public boolean isUtilElement()

#### Return Value

true if tree nodes of this type are util-elements; otherwise, false.

#### Remarks

An util-element is a tree node that can be accessed via the UtilElements and UtilIdElements views. Util-elements are a subset of model-elements.

### Method isVCSControllableElement

    public boolean isVCSControllableElement()

#### Return Value

### Method new

Initializes a new instance of the TreeNodeType class.

    private void new()

