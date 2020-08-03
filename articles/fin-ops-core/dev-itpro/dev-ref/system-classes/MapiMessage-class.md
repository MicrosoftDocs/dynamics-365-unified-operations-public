---
title: MapiMessage class
description: This topic describes the MapiMessage class.
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

# Class MapiMessage

[!include [banner](../../includes/banner.md)]

```xpp
class MapiMessage extends Object
```

The MapiMessage class contains a message that is sent to or received from the MAPI system. The message includes a subject, text, recipient information, and attachment information.

## Remarks

When you send or receive a message, the message is passed to and from the MAPI system as a MapiMessage object.

## Examples

## Methods

| Method                                                        | Description                                                                                             |
|---------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| public str conversationID(\[str conversationId\])             | Gets or sets the string that identifies the conversation thread to which the message belongs.           |
| public str dateReceived(\[Date theDate\])                     | Returns the date when the message was received.                                                         |
| public int flags(\[int flags\])                               | Set or get a bitmask of the message status flags.                                                       |
| public MapiFileDesc getFileNo(int fileNo)                     | Gets a file attachment from a message.                                                                  |
| public MapiRecipDesc getRecipNo(int recipientNo)               | Retrieves information about a message recipient in a MapiRecipDesc object.                              |
| public str messageType(\[str messageType\])                   | Gets or sets the string that indicates that the message is not of the IPM (interpersonal message) type. |
| public int numFiles(\[int numFiles\])                         |                                                                                                         |
| public int numRecips(\[int numRecips\])                       |                                                                                                         |
| public MapiRecipDesc originator(\[MapiRecipDesc originator\]) |                                                                                                         |
| public str subject(\[str subject\])                           |                                                                                                         |
| public str text(\[str text\])                                 |                                                                                                         |
| public void new()                                             | Initializes an instance of the MapiMessage class.                                                       |
| public void finalize()                                        |                                                                                                         |
| public void setRecipNo(int recipNo, MapiRecipDesc recipient)  | Adds a recipient to the message.                                                                        |
| public void setFileNo(int fileNo, MapiFileDesc file)          | Sets a file attachment for the message.                                                                 |

## Method conversationID

Gets or sets the string that identifies the conversation thread to which the message belongs.

```xpp
public str conversationID([str conversationId])
```

### Parameters - conversationID

conversationId  
The ID of the conversation thread; optional.

### Return Value - conversationID

A string that identifies the conversation thread to which the message belongs.

### Remarks - conversationID

Some messaging systems might ignore and not return this member.

## Method dateReceived

Returns the date when the message was received.

```xpp
public str dateReceived([Date theDate])
```

### Parameters - dateReceived

theDate  
The date when the message was received; optional.

### Return Value - dateReceived

A string that indicates the date when the message was received.

### Remarks - dateReceived

The format of the string that is returned is YYYY/MM/DD HH:MM and uses a 24-hour clock.

## Method flags

Set or get a bitmask of the message status flags.

```xpp
public int flags([int flags])
```

### Parameters - flags

flags  
The message status flags; optional.

### Return Value - flags

A bitmask of the message status flags.

### Remarks - flags

The following flags can be set:

-   \#MAPI\_RECEIPT\_REQUESTED � Receipt notification is requested. Client applications set this bit when they send a message.
-   \#MAPI\_SENT � The message has been sent.
-   \#MAPI\_UNREAD � The message has not been read.

## Method getFileNo

Gets a file attachment from a message.

```xpp
public MapiFileDesc getFileNo(int fileNo)
```

### Parameters - getFileNo

fileNo  
The index of the attachment to retrieve. The index starts at 1, and the total number of attachments can be retrieved using the numFiles method.

### Return Value - getFileNo

Returns a MapiFileDesc object that contains information about the attachment.

### Remarks - getFileNo

The attached file is returned in a MapiFileDesc object.

### Examples - getFileNo

```xpp
{ 
    MapiFileDesc attachment; 
    MapiMessage message; 
    // Retrieve message. 
    // ...  
    if (message.NumFiles() >= 1) 
    { 
        attachment = message.GetFileNo(1); 
    } 
}
```

## Method getRecipNo

Retrieves information about a message recipient in a MapiRecipDesc object.

```xpp
public MapiRecipDesc getRecipNo(int recipientNo)
```

### Parameters - getRecipNo

recipientNo  
The number of the recipient to retrieve. The numbering starts at 1, and the total number of recipients can be read by using the numRecips method.

### Return Value - getRecipNo

A MapiRecipDesc object that describes the recipient or nullNothingnullptrunita null reference (Nothing in Visual Basic).

## Method messageType

Gets or sets the string that indicates that the message is not of the IPM (interpersonal message) type.

```xpp
public str messageType([str messageType])
```

### Parameters - messageType

messageType  
The messageType value to set for the message; optional.

### Return Value - messageType

A messagetype string.

### Remarks - messageType

Applications can select message types for messages that are not IPMs. Clients that support only IPMs can ignore the MessageType member when they read messages and set it to empty when they send messages.

## Method numFiles

```xpp
public int numFiles([int numFiles])
```

### Parameters - numFiles

numFiles  

### Return Value - numFiles

## Method numRecips

```xpp
public int numRecips([int numRecips])
```

### Parameters - numRecips

numRecips  

### Return Value - numRecips

## Method originator

```xpp
public MapiRecipDesc originator([MapiRecipDesc originator])
```

### Parameters - originator

originator  

### Return Value - originator

## Method subject

```xpp
public str subject([str subject])
```

### Parameters - subject

subject  

### Return Value - subject

## Method text

```xpp
public str text([str text])
```

### Parameters - text

text  

### Return Value - text

## Method new

Initializes an instance of the MapiMessage class.

```xpp
public void new()
```

## Method finalize

```xpp
public void finalize()
```

## Method setRecipNo

Adds a recipient to the message.

```xpp
public void setRecipNo(int recipNo, MapiRecipDesc recipient)
```

### Parameters - setRecipNo

recipNo  
The MapiRecipDesc object that describes the recipient.

<!-- -->

recipient  
The MapiRecipDesc object that describes the recipient.

### Remarks - setRecipNo

If you have to get a correct MapiRecipDesc object from a name that a user entered, use the resolveName method.

## Method setFileNo

Sets a file attachment for the message.

```xpp
public void setFileNo(int fileNo, MapiFileDesc file)
```

### Parameters - setFileNo

fileNo  
The MapiFileDesc object that describes the attachment.

<!-- -->

file  
The MapiFileDesc object that describes the attachment.

### Remarks - setFileNo

The attachments are numbered from 1. Therefore, the first attachment should be numbered 1. You can call the numFiles method to retrieve the number of attachments.

### Examples - setFileNo

```xpp
{ 
    MapiMessage msg = new MapiMessage(); 
    MapiFileDesc attachment = new MapiFileDesc(); 
    attachment.Path("C:\\files\\info.txt"); 
    msg.SetFileNo(1,attachment); 
}
```

