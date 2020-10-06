---
title: TextIo class
description: This topic describes the TextIo class.
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

# Class TextIo

[!include [banner](../../includes/banner.md)]

```xpp
class TextIo extends CommaIo
```

The TextIo class provides functionality for reading and writing text files.

## Remarks

TextIO replaces AsciiIO to provide support for non-ANSI code page file I/O. The TextIO constructor has an additional optional parameter to set the code page of the file. The TextIO.new method has an optional argument that specifies the code page of the file. The default value is UTF-16LE (the Microsoft Windows native Unicode representation). It is best to use this in most instances, especially if end-users might edit the file in a text editor outside of the Finance and Operations application. For more information, see TextIo.new. When files are read, TextIO examines the first few bytes of the file for a byte-order mark (BOM) and automatically handles UTF-8, UTF-16LE, and UTF-16BE. If no BOM is found, the file is assumed to be in the ANSI Code Page (ACP) format.

## Examples

## Methods

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

## Method inFieldDelimiter

Gets or sets the character that is used for the field delimiter of an input file represented by a TextIO object.

```xpp
public str inFieldDelimiter([str value])
```

### Parameters - inFieldDelimiter

value  
The character to be used as the field delimiter; optional.

### Return Value - inFieldDelimiter

The character used as the field delimiter.

### Remarks - inFieldDelimiter

To set the field delimiter for an output file, use

### Examples - inFieldDelimiter

The following example sets the field delimiter for an input file to '\\r\\n'.

```xpp
protected void openFile() 
{ 
    #define.delimiter('\r\n') 
    super(); 
    importFile.inFieldDelimiter(#delimiter); 
}
```

## Method inRecordDelimiter

Gets or sets the character that is used for the record delimiter of an input file represented by a TextIO object.

```xpp
public str inRecordDelimiter([str value])
```

### Parameters - inRecordDelimiter

value  
The character to be used as the record delimiter; optional.

### Return Value - inRecordDelimiter

The character used as the record delimiter.

### Remarks - inRecordDelimiter

To set the record delimiter for an output file, use the .

### Examples - inRecordDelimiter

The following example sets the record delimiter to 128.

```xpp
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
```

## Method inRecordLength

Gets or sets the record length for an input file.

```xpp
public int inRecordLength([int value])
```

### Parameters - inRecordLength

value  
The record length for the input file; optional.

### Return Value - inRecordLength

The record length for the input file.

### Remarks - inRecordLength

For files that have a fixed-length format, use the inRecordLength property to ensure that no more than the specified number of characters are read for each record. If the record format is overruled by a specified inRecordDelimiter property value, that is the inRecordDelimiter value is met before the fixed length is read, the record is accepted, and no further data is read. To ensure that a fixed number of characters are read, set the inRecordDelimiter property value to an empty string. When no inRecordDelimiter property value is found, the inRecordDelimiter property value is the maximum limit of characters to read. Set the inRecordDelimiter property value to zero to disable the record length check.

### Examples - inRecordLength

The following example sets the record length to 128.

```xpp
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
```

## Method outFieldDelimiter

Gets or sets the character that is used for the field delimiter of an output file represented by a TextIO object.

```xpp
public str outFieldDelimiter([str value])
```

### Parameters - outFieldDelimiter

value  
The character to be used as the field delimiter; optional.

### Return Value - outFieldDelimiter

The character used as the field delimiter.

### Remarks - outFieldDelimiter

To set the field delimiter for an input file, use the .

### Examples - outFieldDelimiter

The following example sets the field delimiter to ' ' (nothing) for an output file.

```xpp
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
```

## Method outRecordDelimiter

Gets or sets the character that is used for the record delimiter of an output file represented by a TextIO object.

```xpp
public str outRecordDelimiter([str value])
```

### Parameters - outRecordDelimiter

value  
The character to be used as the record delimiter; optional.

### Return Value - outRecordDelimiter

The character used as the record delimiter.

### Remarks - outRecordDelimiter

To set the record delimiter for an input file, use the .

### Examples - outRecordDelimiter

The following example sets the record delimiter for an output file to '\\r\\n'.

```xpp
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
```

## Method read

Reads the next full record from a TextIO object.

```xpp
public container read()
```

### Return Value - read

A container that holds one record.

### Remarks - read

Each entry in the container equals one field in the record. The definition of the next full record is controlled by the inFieldDelimiter, inRecordDelimiter, and inRecordLength properties. These properties have default values that allow input and output of the most common formats. It might be necessary to adjust the properties by using the inFieldDelimiter, inRecordDelimiter, and inRecordLength methods.

### Examples - read

The following example reads a record from a file and uses the conpeek function to extract values from the record.

```xpp
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
```

## Method status

Retrieves the status of the last operation performed on a TextIo object.

```xpp
public IO_Status status()
```

### Return Value - status

The status of the last operation.

### Examples - status

The following example throws an error if a file does not exist or if the last operation on the file did not have a status of the IO\_Status::Ok enumeration value.

```xpp
protected void checkDiskFileStatus() 
{ 
    if (!diskFile || diskFile.status() != IO_Status::Ok) 
    { 
        throw error(strfmt("@SYS76826", diskFileName)); 
    } 
}
```

## Method write

Writes data to a file represented by a TextIO object.

```xpp
public boolean write(VarArg values)
```

### Parameters - write

values  
The values to write to the file. The values can be of different data types.

### Return Value - write

true if the write operation succeeds; otherwise, false.

### Remarks - write

If the write operation fails, can be used to ascertain the cause. The write method accepts a variable number of arguments. Each value is put into the output record as a field. The fields are separated by the field delimiter specified by the . Each record is separated by the delimiter specified by the . To write complete containers, use the .

## Method writeChar

Writes a Unicode character to a file.

```xpp
public boolean writeChar(int int)
```

### Parameters - writeChar

int  

### Return Value - writeChar

true if the write operation succeeds; otherwise, false.

### Remarks - writeChar

If the write operation fails, the TextIO.status method can be used to check for the cause. To write multiple values or to write data of different types to a file, use the TextIO.write method.

## Method writeExp

Writes the contents of a container to a file represented by a TextIO object.

```xpp
public boolean writeExp(container data)
```

### Parameters - writeExp

data  
The container that has data to write to the file.

### Return Value - writeExp

true if the write operation succeeds; otherwise, false.

### Remarks - writeExp

If the write operation fails, the TextIo.status Method can be used to ascertain the cause. Entries in the container are separated by the delimiter set by the outFieldDelimiter method. Containers are separated by the delimiter set by the outRecordDelimiter method.

## Method writeRaw

Reserved.

```xpp
public boolean writeRaw(str data)
```

### Parameters - writeRaw

data  

### Return Value - writeRaw

## Method new

Creates a new instance of the TextIO class.

```xpp
public void new(str filename, str mode, [int codepage])
```

### Parameters - new

filename  
The code page number for the character set to be read from or written to the file. The default value is 1200 (UTF-16LE). This parameter is optional. Following are the most common values: For more information about these options, see [the list](https://go.microsoft.com/fwlink/?LinkID=78282&clcid=0x409). An error is reported if an invalid code page is requested. Notice that a code page is reported as "invalid" if it is not installed on the computer (different code pages may be installed on the client and server). For example, specifying code page 1253 for Greek fails unless the computer's ACP is Greek or Greek language support has been loaded by using Control Panel &gt; Regional Options.

<!-- -->

mode  
The code page number for the character set to be read from or written to the file. The default value is 1200 (UTF-16LE). This parameter is optional. Following are the most common values: For more information about these options, see [the list](https://go.microsoft.com/fwlink/?LinkID=78282&clcid=0x409). An error is reported if an invalid code page is requested. Notice that a code page is reported as "invalid" if it is not installed on the computer (different code pages may be installed on the client and server). For example, specifying code page 1253 for Greek fails unless the computer's ACP is Greek or Greek language support has been loaded by using Control Panel &gt; Regional Options.

<!-- -->

codepage  
The code page number for the character set to be read from or written to the file. The default value is 1200 (UTF-16LE). This parameter is optional. Following are the most common values: For more information about these options, see [the list](https://go.microsoft.com/fwlink/?LinkID=78282&clcid=0x409). An error is reported if an invalid code page is requested. Notice that a code page is reported as "invalid" if it is not installed on the computer (different code pages may be installed on the client and server). For example, specifying code page 1253 for Greek fails unless the computer's ACP is Greek or Greek language support has been loaded by using Control Panel &gt; Regional Options.

### Remarks - new

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
<td>The code page that supports only characters in the user&#39;s current language. The code page is unsuitable for anything that might contain multilingual data or for monolingual data that might be transferred between two systems by using different code pages.</td>
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
<td>Stores Unicode in a byte-stream�friendly way:
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

### Examples - new

The following example creates a TextIO object to access a file that is named filename in read mode by using code page 850 encoding.

```xpp
protected void openFile(str _fileOpen = #io_read) 
{ 
    importFile = new TextIo(filename, _fileOpen, 850); 
    if (! importFile) 
    { 
        throw error(strfmt("@SYS18678", filename)); 
    } 
}
```

## Method finalize

Closes the file and, if data was written, flushes the file buffers to disk.

```xpp
public void finalize()
```

### Remarks - finalize

The TextIO object is usually finalized by leaving the scope. The finalize method is not usually directly called. Output written to the file is not valid until the TextIO object is finalized.

