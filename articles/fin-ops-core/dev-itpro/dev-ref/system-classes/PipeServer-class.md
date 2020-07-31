---
title: PipeServer class
description: This topic describes the PipeServer class.
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

# Class PipeServer

[!include [banner](../../includes/banner.md)]

```xpp
class PipeServer extends Object
```

The PipeServer class supports the server side of a named pipe connection.

## Remarks

A named pipe is created when a PipeServer object is created by using the PipeServer.new method. The pipe that is created has read access and is in message mode. The name of the pipe is automatically prefixed with \\\\.\\pipe\\Dynamics. The current session SID is postfixed to the name. The support that is provided for pipe connections on the server is restricted for the following security reasons:

-   The pipe is supported only for the current logon session on the computer that the session was created on.
-   The user who creates the pipe is the only person who can communicate with that pipe.

## Examples

## Methods

| Method                                              | Description                                                                  |
|-----------------------------------------------------|------------------------------------------------------------------------------|
| public boolean blockingMode(\[boolean block\])      |                                                                              |
| public boolean connect()                            | Waits for a client to connect to the named pipe.                             |
| public boolean disconnect()                         | Disconnects the server end of the named pipe instance from a client process. |
| public int errorCode()                              |                                                                              |
| public str read()                                   | Reads data from the named pipe, as written by a pipe client.                 |
| public void new(str pipename, \[boolean blocking\]) | Creates a new instance of the PipeServer class.                              |

## Method blockingMode

```xpp
public boolean blockingMode([boolean block])
```

### Parameters - blockingMode

block  

### Return Value - blockingMode

## Method connect

Waits for a client to connect to the named pipe.

```xpp
public boolean connect()
```

### Return Value - connect

true if the method succeeds; otherwise, false.

### Remarks - connect

If you do not want to block the current thread if it is waiting for a client to connect, avoid using the PipeServer.connect method, and poll by using the PipeServer.read method instead.

## Method disconnect

Disconnects the server end of the named pipe instance from a client process.

```xpp
public boolean disconnect()
```

### Return Value - disconnect

true if the method succeeds; otherwise, false.

## Method errorCode

```xpp
public int errorCode()
```

### Return Value - errorCode

## Method read

Reads data from the named pipe, as written by a pipe client.

```xpp
public str read()
```

### Return Value - read

The data that is read from the pipe, if any data is read.

### Remarks - read

Data might not be available when this method is called, perhaps because no client has connected to the named pipe. If you want to wait for a client to connect, use the connect method. However, if you do not want to block the current thread that is waiting for a client to connect, poll by using the read method.

## Method new

Creates a new instance of the PipeServer class.

```xpp
public void new(str pipename, [boolean blocking])
```

### Parameters - new

pipename  
A Boolean flag that indicates whether blocking behavior should be used. Non-blocking mode is supported for compatibility with Microsoft LAN Manager version 2.0 and should not be used to achieve asynchronous I/O with named pipes. Instead, a polling technique should be used. See the read method.

<!-- -->

blocking  
A Boolean flag that indicates whether blocking behavior should be used. Non-blocking mode is supported for compatibility with Microsoft LAN Manager version 2.0 and should not be used to achieve asynchronous I/O with named pipes. Instead, a polling technique should be used. See the read method.

### Remarks - new

Some restrictions apply. See the example in the general description of the PipeServer class.

