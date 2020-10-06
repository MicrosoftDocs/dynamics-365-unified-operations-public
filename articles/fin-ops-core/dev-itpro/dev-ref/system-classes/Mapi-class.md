---
title: Mapi class
description: This topic describes the Mapi class.
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

# Class Mapi

[!include [banner](../../includes/banner.md)]

```xpp
class Mapi extends Object
```

The Mapi class enables email to be sent, received, and managed in most major mail systems, such as Microsoft Exchange�based systems, Microsoft Outlook Express, and Lotus CCMail.

## Remarks

Together with the other Mapi classes, MapiMessage, MapiRecipDesc, and MapiFileDesc, this class lets you specify multiple recipients, file attachments, message text, and a subject. The easiest approach is to set up a working mail client on the machine, and make sure that this works correctly order by sending and receiving a few email messages. Flags for the Mapi methods are located in the Mapi macro. You include this macro in code where you use the Mapi classes together with the \#MAPI statement.

## Examples

The following example shows how to send an email message by using this class.

```xpp
static void example() 
{ 
    #Mapi 
    Mapi m = new Mapi(); 
    MapiMessage msg = new MapiMessage(); 
    MapiRecipDesc recip = new MapiRecipDesc(); 
    // Set up the recipient. 
    recip.Name("someone"); 
    recip.RecipClass(#MAPI_TO); 
    msg.setRecipNo(1,recip); 
    // Log on using default profile. 
    m.Logon("","",#MAPI_USE_DEFAULT); 
    // Send the mail, and allow the user to modify the 
    // Subject, Text and Recipients in the Send Mail Dialog. 
    m.SendMail(msg,#MAPI_DIALOG); 
    // Log off. 
    m.Logoff(); 
}
```

## Methods

| Method                                                                         | Description                                                                                          |
|--------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------|
| public int deleteMail(str messageID)                                           | Removes the specified message from the message store.                                                |
| public str findNext(\[str messageType\], \[str seedMessageID\], \[int flags\]) | Finds the first or next message in the message store.                                                |
| public int logoff()                                                            | Lets you log off the mail system.                                                                    |
| public int logon(str profileName, str password, int flags)                     | Logs on to the mail system by using the specified profile and password.                              |
| public MapiMessage readMail(str messageID, \[int flags\])                      | Retrieves a message from the message store.                                                          |
| public MapiRecipDesc resolveName(str mame, int flags)                          | Transforms the message recipient's name, as entered by a user, to an unambiguous address list entry. |
| public int saveMail(MapiMessage message, int flags, str messageId)             | Saves a message to the message store.                                                                |
| public int sendMail(MapiMessage message, \[int flags\])                        | Sends a message to the specified recipients.                                                         |
| public int status()                                                            | Retrieves the status of the last Mapi operation.                                                     |
| public void new()                                                              | Initializes an instance of the Mapi class.                                                           |
| public void finalize()                                                         |                                                                                                      |

## Method deleteMail

Removes the specified message from the message store.

```xpp
public int deleteMail(str messageID)
```

### Parameters - deleteMail

messageID  
The unique message ID for the message to delete.

### Return Value - deleteMail

The status \#SUCCESS\_SUCCES or an error code, which can be found in the \#MAPI macro.

### Remarks - deleteMail

The message ID can be retrieved by using the findNext method.

## Method findNext

Finds the first or next message in the message store.

```xpp
public str findNext([str messageType], [str seedMessageID], [int flags])
```

### Parameters - findNext

messageType  
Flags that indicate first in, first out (FIFO) or unread; optional. This parameter has two possible values:

<!-- -->

seedMessageID  
Flags that indicate first in, first out (FIFO) or unread; optional. This parameter has two possible values:

<!-- -->

flags  
Flags that indicate first in, first out (FIFO) or unread; optional. This parameter has two possible values:

### Return Value - findNext

The message ID of the message that is found; an empty string if no message is found.

### Remarks - findNext

Call this method to find the first message, and then issue subsequent calls to obtain the following messages. Use the status method to check for Mapi errors after you call this method.

## Method logoff

Lets you log off the mail system.

```xpp
public int logoff()
```

### Return Value - logoff

The status \#SUCCESS\_SUCCESS or an error code, which can be found in the \#MAPI macro.

## Method logon

Logs on to the mail system by using the specified profile and password.

```xpp
public int logon(str profileName, str password, int flags)
```

### Parameters - logon

profileName  
A list of flags. The valid flags are as follows:

<!-- -->

password  
A list of flags. The valid flags are as follows:

<!-- -->

flags  
A list of flags. The valid flags are as follows:

### Return Value - logon

The status \#SUCCESS\_SUCCESS if the logon succeeded; otherwise, an error code, which can be found in the \#MAPI macro.

### Remarks - logon

An easy and common way to log on is to specify the \#MAPI\_USE\_DEFAULT flag, which logs on by using the default profile.

## Method readMail

Retrieves a message from the message store.

```xpp
public MapiMessage readMail(str messageID, [int flags])
```

### Parameters - readMail

messageID  
A list of flags; optional. The valid flags are as follows:

<!-- -->

flags  
A list of flags; optional. The valid flags are as follows:

### Return Value - readMail

The MapiMessage object that is retrieved or nullNothingnullptrunita null reference (Nothing in Visual Basic).

## Method resolveName

Transforms the message recipient's name, as entered by a user, to an unambiguous address list entry.

```xpp
public MapiRecipDesc resolveName(str mame, int flags)
```

### Parameters - resolveName

mame  
A list of flags. The valid flags are as follows:

<!-- -->

flags  
A list of flags. The valid flags are as follows:

### Return Value - resolveName

A MapiRecipDesc class object that has an unambiguous address list entry.

## Method saveMail

Saves a message to the message store.

```xpp
public int saveMail(MapiMessage message, int flags, str messageId)
```

### Parameters - saveMail

message  
The unique ID of the message to retrieve.

<!-- -->

flags  
The unique ID of the message to retrieve.

<!-- -->

messageId  
The unique ID of the message to retrieve.

### Return Value - saveMail

The status \#SUCCESS\_SUCCESS or an error code from the \#MAPI macro.

## Method sendMail

Sends a message to the specified recipients.

```xpp
public int sendMail(MapiMessage message, [int flags])
```

### Parameters - sendMail

message  
A list of flags; optional. The valid flags are as follows:

<!-- -->

flags  
A list of flags; optional. The valid flags are as follows:

### Return Value - sendMail

The status \#SUCCESS\_SUCCESS or an error code from the \#MAPI macro.

## Method status

Retrieves the status of the last Mapi operation.

```xpp
public int status()
```

### Return Value - status

The status code of the last Mapi operation.

### Remarks - status

The status codes can be found in the \#MAPI macro.

## Method new

Initializes an instance of the Mapi class.

```xpp
public void new()
```

## Method finalize

```xpp
public void finalize()
```

