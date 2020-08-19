---
title: Label class
description: This topic describes the Label class.
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

# Class Label

[!include [banner](../../includes/banner.md)]


```xpp
class Label extends Object
```

The Label class manages label IDs and label files.

## Remarks

The SysLabel class extends the Label class.

## Examples

## Methods

| Method                                                                | Description                                                                                         |
|-----------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
| public LabelBulkEditor bulkEditor(str module)                         | Creates an instance of the LabelBulkEditor class.                                                   |
| public boolean createLabelFile(str module, str language)              | Creates a label file for a specified label ID.                                                      |
| public boolean delete(str label)                                      | Deletes a specified label.                                                                          |
| public boolean exists(str label)                                      | Indicates whether a specified label ID exists.                                                      |
| public str extractComment(str label)                                  | Returns a comment that is associated with a specified label ID.                                     |
| public str extractString(str label)                                   | Returns the text that is associated with a specified label ID.                                      |
| public str getFirstLabelFile()                                        | Returns the first label file ID record.                                                             |
| public Date getLabelFileCreatedDate(str labelFile, str language)      | Returns the date that a specified label file was created.                                           |
| public int getLabelFileCreatedTime(str labelFile, str language)       | Returns the time that a specified label file was created.                                           |
| public Date getLabelFileModificationDate(str labelFile, str language) | Returns the date that a specified label file was modified.                                          |
| public int getLabelFileModificationTime(str labelFile, str language)  | Returns the time that a specified label file was modified.                                          |
| public str getNextLabelFile()                                         | Returns the next label file ID record.                                                              |
| public str insert(str text, str comment, str module)                  | Creates a label ID for a specified text string.                                                     |
| public int labelId(str label)                                         | Returns the number that is included in a specified label ID.                                        |
| public int maxLabelId(str module)                                     | Returns the ID for the last label in the specified label file.                                      |
| public boolean modify(str label, str text, \[str comment\])           | Modifies the text and comment that are associated with a specified label.                           |
| public str moduleId(str label)                                        | Returns the label file ID for a specified label ID.                                                 |
| public boolean moreLabelFiles()                                       | Indicates whether there are additional label files.                                                 |
| public str name(str module, int labelId)                              | Returns a label ID, based on a specified label file ID and label ID number.                         |
| public str searchFirst(str searchString)                              | Returns the first label ID that is found for a specified search term.                               |
| public str searchNext()                                               | Returns the next label ID that is found for a search term that is passed to the searchFirst method. |
| ::public static boolean flush(str labelFileId, str language)          | Flushes the label file buffers to disk.                                                             |
| public void new(\[str language\])                                     | Creates a new instance of the Label class.                                                          |
| public void finalize()                                                | Closes the current label file.                                                                      |

## Method bulkEditor

Creates an instance of the LabelBulkEditor class.

```xpp
public LabelBulkEditor bulkEditor(str module)
```

### Parameters - bulkEditor

module  
A string data type that specifies a three-letter label file ID.

### Return Value - bulkEditor

An instance of the LabelBulkEditor class.

### Remarks - bulkEditor

The LabelBulkEditor class is used to quickly modify a label file. This method returns nullNothingnullptrunita null reference (Nothing in Visual Basic) when it is invoked from the client tier.

## Method createLabelFile

Creates a label file for a specified label ID.

```xpp
public boolean createLabelFile(str module, str language)
```

### Parameters - createLabelFile

module  
A string data type that specifies a language by using a language prefix.

<!-- -->

language  
A string data type that specifies a language by using a language prefix.

### Return Value - createLabelFile

true if a file is created; otherwise, false.

### Remarks - createLabelFile

The label file is created after the file buffers are flushed to disk, which occurs when the server closes.

## Method delete

Deletes a specified label.

```xpp
public boolean delete(str label)
```

### Parameters - delete

label  
A string that specifies the label ID. The string must include the at sign (@) followed by a label file ID and a number.

### Return Value - delete

true if the label ID is deleted; otherwise, false.

## Method exists

Indicates whether a specified label ID exists.

```xpp
public boolean exists(str label)
```

### Parameters - exists

label  
The output of the literalStr function from a label ID string that includes the at sign (@).

### Return Value - exists

true if the label ID exists; otherwise, false.

### Remarks - exists

The format of the label parameter value must resemble literalStr("@SYS24359").

## Method extractComment

Returns a comment that is associated with a specified label ID.

```xpp
public str extractComment(str label)
```

### Parameters - extractComment

label  
A string that specifies the label ID. The string must include the at sign (@) followed by a label file ID and a number.

### Return Value - extractComment

A string value that indicates the comment that is associated with the specified label ID.

### Remarks - extractComment

If you specify a label ID that does not exist, this method returns the specified ID as a string. If you do not include the @ in the label parameter value, the method returns the label ID.

## Method extractString

Returns the text that is associated with a specified label ID.

```xpp
public str extractString(str label)
```

### Parameters - extractString

label  
A string data type that specifies a label ID. The string must include the at sign (@) followed by a label file ID and a number.

### Return Value - extractString

A string data type value that indicates the text that is associated with the specified label ID.

### Remarks - extractString

If you specify a label ID that does not exist, the method returns the specified ID as a string. If you do not include the @ in the label parameter value, the method returns the label ID.

## Method getFirstLabelFile

Returns the first label file ID record.

```xpp
public str getFirstLabelFile()
```

### Return Value - getFirstLabelFile

A string data type value that indicates the label file ID.

### Remarks - getFirstLabelFile

A label file ID is a three-letter identifier for a label file.

## Method getLabelFileCreatedDate

Returns the date that a specified label file was created.

```xpp
public Date getLabelFileCreatedDate(str labelFile, str language)
```

### Parameters - getLabelFileCreatedDate

labelFile  
A string data type that specifies a language by using a language prefix.

<!-- -->

language  
A string data type that specifies a language by using a language prefix.

### Return Value - getLabelFileCreatedDate

A Date data type value that indicates when a label file is created.

### Remarks - getLabelFileCreatedDate

You can use the date2str function to convert the date to a text string.

## Method getLabelFileCreatedTime

Returns the time that a specified label file was created.

```xpp
public int getLabelFileCreatedTime(str labelFile, str language)
```

### Parameters - getLabelFileCreatedTime

labelFile  
A string data type that specifies a language by using a language prefix.

<!-- -->

language  
A string data type that specifies a language by using a language prefix.

### Return Value - getLabelFileCreatedTime

An integer data type value that indicates the time that a label file is created.

### Remarks - getLabelFileCreatedTime

For more information, see How to: Create a Label File. You can use the time2str function to convert the integer to a text string.

## Method getLabelFileModificationDate

Returns the date that a specified label file was modified.

```xpp
public Date getLabelFileModificationDate(str labelFile, str language)
```

### Parameters - getLabelFileModificationDate

labelFile  
A string data type that specifies a language by using a language prefix.

<!-- -->

language  
A string data type that specifies a language by using a language prefix.

### Return Value - getLabelFileModificationDate

A Date data type value that indicates when a label file was modified.

### Remarks - getLabelFileModificationDate

You can use the date2str function to convert the date to a text string.

## Method getLabelFileModificationTime

Returns the time that a specified label file was modified.

```xpp
public int getLabelFileModificationTime(str labelFile, str language)
```

### Parameters - getLabelFileModificationTime

labelFile  
A string data type that specifies a language by using a language prefix.

<!-- -->

language  
A string data type that specifies a language by using a language prefix.

### Return Value - getLabelFileModificationTime

An integer value that indicates the time that a label file was modified.

### Remarks - getLabelFileModificationTime

You can use the time2str function to convert the integer to a text string.

## Method getNextLabelFile

Returns the next label file ID record.

```xpp
public str getNextLabelFile()
```

### Return Value - getNextLabelFile

A string data type value that indicates the label file ID.

### Remarks - getNextLabelFile

A label file ID is a three-letter identifier for a label file.

## Method insert

Creates a label ID for a specified text string.

```xpp
public str insert(str text, str comment, str module)
```

### Parameters - insert

text  
A string data type that specifies a three-letter label file ID.

<!-- -->

comment  
A string data type that specifies a three-letter label file ID.

<!-- -->

module  
A string data type that specifies a three-letter label file ID.

### Return Value - insert

A string data type value for the label ID that is created.

### Remarks - insert

This operation allocates a new label ID across all languages.

## Method labelId

Returns the number that is included in a specified label ID.

```xpp
public int labelId(str label)
```

### Parameters - labelId

label  
A string data type that specifies the label ID. The string must include the at sign (@) followed by a label file ID and a number.

### Return Value - labelId

An integer data type value that indicates the number that is included in a label ID.

### Remarks - labelId

You must call the searchFirst or searchNext method, and then pass the return value as a parameter to this method.

## Method maxLabelId

Returns the ID for the last label in the specified label file.

```xpp
public int maxLabelId(str module)
```

### Parameters - maxLabelId

module  
A string that specifies a three-letter label file ID.

### Return Value - maxLabelId

An integer that indicates the maximum label ID for the specified label file.

## Method modify

Modifies the text and comment that are associated with a specified label.

```xpp
public boolean modify(str label, str text, [str comment])
```

### Parameters - modify

label  
A string that specifies the comment that is associated with a label ID.

<!-- -->

text  
A string that specifies the comment that is associated with a label ID.

<!-- -->

comment  
A string that specifies the comment that is associated with a label ID.

### Return Value - modify

true if the label ID is modified; otherwise, false.

## Method moduleId

Returns the label file ID for a specified label ID.

```xpp
public str moduleId(str label)
```

### Parameters - moduleId

label  
A string that specifies the label ID. The string must include the at sign (@) followed by a label file ID and a number.

### Return Value - moduleId

A string that indicates the label file ID for a specified label ID.

### Remarks - moduleId

You need to call the searchFirst or searchNext method, and then pass the return value as a parameter to the labelId method.

## Method moreLabelFiles

Indicates whether there are additional label files.

```xpp
public boolean moreLabelFiles()
```

### Return Value - moreLabelFiles

true if there are additional label files; otherwise, false.

## Method name

Returns a label ID, based on a specified label file ID and label ID number.

```xpp
public str name(str module, int labelId)
```

### Parameters - name

module  
An integer that specifies the numeric part of a label ID.

<!-- -->

labelId  
An integer that specifies the numeric part of a label ID.

### Return Value - name

A string value that indicates the label ID.

## Method searchFirst

Returns the first label ID that is found for a specified search term.

```xpp
public str searchFirst(str searchString)
```

### Parameters - searchFirst

searchString  
A string that specifies the search term.

### Return Value - searchFirst

A string value that indicates the label ID.

## Method searchNext

Returns the next label ID that is found for a search term that is passed to the searchFirst method.

```xpp
public str searchNext()
```

### Return Value - searchNext

A string value that indicates the label ID.

### Remarks - searchNext

You must call the searchFirst method before you call this method. Otherwise, this method returns a random label ID.

## Method flush

Flushes the label file buffers to disk.

```xpp
public static boolean flush(str labelFileId, str language)
```

### Parameters - flush

labelFileId  
A string that specifies a language by using a language prefix.

<!-- -->

language  
A string that specifies a language by using a language prefix.

### Return Value - flush

## Method new

Creates a new instance of the Label class.

```xpp
public void new([str language])
```

### Parameters - new

language  
A string that specifies a language by using a language prefix.

## Method finalize

Closes the current label file.

```xpp
public void finalize()
```

