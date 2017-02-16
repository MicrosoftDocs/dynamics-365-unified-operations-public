---
# required metadata

title: B Classes
description: System API classes that start with the letter B.
author: RobinARH
manager: AnnBe
ms.date: 2016-02-18 20 - 20 - 46
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: a:2:{s:4:"name";s:22:"Robin Reynolds-Haertle";s:2:"id";s:0:"";}
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 50951
ms.assetid: a10ee8be-9a6c-49ac-ad0d-13c02f937cf2
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.dyn365.ops.intro: Feb-16
ms.dyn365.ops.version: AX 7.0.0

---

# B Classes

System API classes that start with the letter B.

Class Binary
------------

    class Binary extends Object

### Remarks

### Examples

### Methods

| Method                                                                   | Description                                     |
|--------------------------------------------------------------------------|-------------------------------------------------|
| public int byte(int offset, \[int value\])                               |                                                 |
| public Real double(int offset, \[Real value\])                           |                                                 |
| public int dWord(int offset, \[int value\])                              |                                                 |
| public container getContainer()                                          |                                                 |
| public CLRObject getMemoryStream()                                       |                                                 |
| public Int64 qWord(int offset, \[Int64 value\])                          |                                                 |
| public str string(int offset, \[str value\])                             |                                                 |
| public int strLenBytes(int offset)                                       |                                                 |
| public int word(int offset, \[int value\])                               |                                                 |
| public str wString(int offset, \[str value\])                            |                                                 |
| ::public static Binary constructFromContainer(container data)            |                                                 |
| ::public static Binary constructFromMemoryStream(CLRObject memoryStream) |                                                 |
| public void attach(Int64 bufPtr, int bufSize)                            |                                                 |
| public void finalize()                                                   |                                                 |
| public void appendSubString(\[str string\])                              |                                                 |
| public void setBinaryValue(int offset, Binary value)                     |                                                 |
| public void new(AnyType buffersizeOrString, \[boolean wideString\])      | Initializes a new instance of the Object class. |

### Method byte

    public int byte(int offset, [int value])

#### Parameters

offset  

<!-- -->

value  

#### Return Value

### Method double

    public Real double(int offset, [Real value])

#### Parameters

offset  

<!-- -->

value  

#### Return Value

### Method dWord

    public int dWord(int offset, [int value])

#### Parameters

offset  

<!-- -->

value  

#### Return Value

### Method getContainer

    public container getContainer()

#### Return Value

### Method getMemoryStream

    public CLRObject getMemoryStream()

#### Return Value

### Method qWord

    public Int64 qWord(int offset, [Int64 value])

#### Parameters

offset  

<!-- -->

value  

#### Return Value

### Method string

    public str string(int offset, [str value])

#### Parameters

offset  

<!-- -->

value  

#### Return Value

### Method strLenBytes

    public int strLenBytes(int offset)

#### Parameters

offset  

#### Return Value

### Method word

    public int word(int offset, [int value])

#### Parameters

offset  

<!-- -->

value  

#### Return Value

### Method wString

    public str wString(int offset, [str value])

#### Parameters

offset  

<!-- -->

value  

#### Return Value

### Method constructFromContainer

    public static Binary constructFromContainer(container data)

#### Parameters

data  

#### Return Value

### Method constructFromMemoryStream

    public static Binary constructFromMemoryStream(CLRObject memoryStream)

#### Parameters

memoryStream  

#### Return Value

### Method attach

    public void attach(Int64 bufPtr, int bufSize)

#### Parameters

bufPtr  

<!-- -->

bufSize  

### Method finalize

    public void finalize()

### Method appendSubString

    public void appendSubString([str string])

#### Parameters

string  

### Method setBinaryValue

    public void setBinaryValue(int offset, Binary value)

#### Parameters

offset  

<!-- -->

value  

### Method new

Initializes a new instance of the Object class.

    public void new(AnyType buffersizeOrString, [boolean wideString])

#### Parameters

buffersizeOrString  

<!-- -->

wideString  

## Class BinaryIo
    class BinaryIo extends Io

### Remarks

### Examples

### Methods

| Method                                  | Description                                                                     |
|-----------------------------------------|---------------------------------------------------------------------------------|
| public container read()                 | Reads the next full record from the Io object.                                  |
| public IO\_Status status()              | Retrieves the status of the last operation that was performed on the Io object. |
| public boolean write(VarArg values)     | Writes values of a simple type.                                                 |
| public boolean writeExp(container data) | Writes the content of a container to a file.                                    |
| public void new(str filename, str mode) | Creates an instance of the BinaryIo class.                                      |
| public void finalize()                  | Closes the file and, if data was written, flushes the file buffers to disk.     |

### Method read

Reads the next full record from the Io object.

    public container read()

#### Return Value

A container that holds the next full record from the Io object.

#### Remarks

The definition of the next full record is controlled by the inFieldDelimiter, inRecordDelimiter, and inRecordLength method properties. The record is returned as a container. Each entry in the container equals one field in the record. Every specialized Io class has default settings for the inFieldDelimiter, inRecordDelimiter, and inRecordLength properties. These default settings enable input and output of the most common formats. You might have to adjust these settings to support the format that you want to use.

### Method status

Retrieves the status of the last operation that was performed on the Io object.

    public IO_Status status()

#### Return Value

The status of the last operation as an IO\_Status system enumeration value.

#### Remarks

The range of possible IO\_Status values that are returned varies, depending on the Io class.

### Method write

Writes values of a simple type.

    public boolean write(VarArg values)

#### Parameters

values  
The simple type. The simple types are string, integer, real, enum, and date.

#### Return Value

true if the write operation succeeds; otherwise, false. If the write operation is unsuccessful, you can check the status method for the cause.

#### Remarks

This method accepts a variable number of arguments. Each value that is specified is put into the output record as a field. The first argument is the first field, the second argument is the second field, and so on. The fields are separated by the field delimiter that is specified in the outFieldDelimiter method. Each record is separated by the record delimiter that is specified in the outRecordDelimiter method. To write complete containers, use the writeExp method.

### Method writeExp

Writes the content of a container to a file.

    public boolean writeExp(container data)

#### Parameters

data  
The container that holds data for the record.

#### Return Value

true if the operation is successful; otherwise, false.

#### Remarks

If this method returns false, check the status method for the cause. The entries in the container are treated as fields, and the container is treated as a full record. The field separator is defined in the outFieldDelimiter method. The record separator is defined in the outRecordDelimiter method.

### Method new

Creates an instance of the BinaryIo class.

    public void new(str filename, str mode)

#### Parameters

filename  
The mode to use to create the instance of the BinaryIo class.

<!-- -->

mode  
The mode to use to create the instance of the BinaryIo class.

#### Remarks

If an attacker can control input to the new method, a security risk exists. Therefore, this method runs under class. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

#### Examples

This example uses the BinaryIo class to read data from the ExampleFile text file.

    static void BinaryIoExampleW2(Args _args)
    {     
        #define.ExampleFile(@"D:\Writers\GeneMi\_Junk\TestW.BinaryIo")
        #define.ExampleOpenModeW("w")
        #define.ExampleOpenModeR("r")
        BinaryIo binaryIoObject;
        container con1;
        str sConRecs;
        FileIoPermission perm;

        // Set the code access permission to help protect the use of
        // the BinaryIo.new method.
        perm = new FileIoPermission(#ExampleFile, #ExampleOpenModeW);
        if (perm == null)
        {
            return;
        }
        perm.assert();
             
        // Overwrites the file if it already exists; restarts it as empty.
        binaryIoObject = new BinaryIo(#ExampleFile, #ExampleOpenModeW);
        if (binaryIoObject != null)
        {
            info("w binaryIoObject is NOT null, Good.");
            binaryIoObject.write("hello world");
            binaryIoObject.write("goodbye solar system");
        }
        else
        {
            warning("w binaryIoObject is NULL, Bad.");
        }

        binaryIoObject.finalize();
        binaryIoObject = null;
        // Close the file, w?
        // BinaryIo instance can only read files in that
        // are in the exact same esoteric format that BinaryIo
        // writes files to.
        // binaryIoObject = new BinaryIo(#ExampleFile, #ExampleOpenModeR);
        if (binaryIoObject != null)
        {
             info("r binaryIoObject is NOT null, Good.");
             while (true)
            {
                con1 = binaryIoObject.read();
                if (con1 == conNull())
                {
                    info("r, no more records.");
                    break;
                }
                sConRecs = con2Str(con1);
                info(sConRecs);
            }
        }
        else
        {
             warning("r binaryIoObject is NULL, Bad.");
        }
        binaryIoObject.finalize();
        binaryIoObject = null;
        WINAPI::deleteFile(#ExampleFile);
         // Clean up after the job.
        CodeAccessPermission::revertAssert();
     }
    /*** Output copied from Infolog:Message (11:22:16 am)w binaryIoObject is NOT null, Good.r binaryIoObject is NOT null, Good.hello worldgoodbye solar systemr, no more records.***/

### Method finalize

Closes the file and, if data was written, flushes the file buffers to disk.

    public void finalize()

#### Remarks

Typically, you finalize the object by leaving the scope. Therefore, the finalize method is not usually called directly. Written output is not valid until the object is finalized.

## Class BinData
    class BinData extends Object

### Remarks

### Examples

### Methods

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

### Method appendToFile

    public boolean appendToFile(str filename)

#### Parameters

filename  

#### Return Value

### Method ascii85Encode

    public str ascii85Encode()

#### Return Value

### Method base64Encode

    public str base64Encode()

#### Return Value

### Method compressLZ77

    public int compressLZ77(int windowBits)

#### Parameters

windowBits  

#### Return Value

### Method copyData

    public boolean copyData(BinData data, [int offset], [int length])

#### Parameters

data  

<!-- -->

offset  

<!-- -->

length  

#### Return Value

### Method decompressLZ77

    public int decompressLZ77()

#### Return Value

### Method getAsciiData

    public str getAsciiData()

#### Return Value

### Method getData

    public container getData()

#### Return Value

### Method getStrData

    public str getStrData()

#### Return Value

### Method getVariant

    public COMVariant getVariant()

#### Return Value

### Method loadFile

    public boolean loadFile(str filename, [int offset], [int length])

#### Parameters

filename  

<!-- -->

offset  

<!-- -->

length  

#### Return Value

#### Remarks

If an attacker can control input to the loadFile method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

### Method saveFile

    public boolean saveFile(str filename)

#### Parameters

filename  

#### Return Value

#### Remarks

If an attacker can control input to the saveFile method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

### Method size

    public int size()

#### Return Value

### Method dataToString

    public static str dataToString(container data)

#### Parameters

data  

#### Return Value

### Method loadFromAscii85

    public static container loadFromAscii85(str ascii85EncodedString)

#### Parameters

ascii85EncodedString  

#### Return Value

### Method loadFromBase64

    public static container loadFromBase64(str base64EncodedString)

#### Parameters

base64EncodedString  

#### Return Value

### Method stringToData

    public static container stringToData(str string)

#### Parameters

string  

#### Return Value

### Method setStrData

    public void setStrData(str data)

#### Parameters

data  

### Method setVariant

    public void setVariant(COMVariant data)

#### Parameters

data  

### Method appendData

    public void appendData(BinData binData)

#### Parameters

binData  

### Method new

Initializes an instance of the BinData class.

    public void new()

### Method setBinaryData

    public void setBinaryData(Binary binary)

#### Parameters

binary  

### Method setAsciiData

    public void setAsciiData(str data, [int codePage])

#### Parameters

data  

<!-- -->

codePage  

### Method setData

    public void setData(container data)

#### Parameters

data  

### Method finalize

    public void finalize()

