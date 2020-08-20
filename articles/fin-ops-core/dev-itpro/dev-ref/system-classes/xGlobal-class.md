---
title: xGlobal class
description: This topic describes the xGlobal class.
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

# Class xGlobal

[!include [banner](../../includes/banner.md)]

```xpp
class xGlobal extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                                                                                                                                                                                                                                                                                                                                             | Description                                        |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------|
| ::public static ClientType clientKind()                                                                                                                                                                                                                                                                                                                                                            |                                                    |
| ::public static SelectableDataArea company(TableId tableid, \[SelectableDataArea company\])                                                                                                                                                                                                                                                                                                        |                                                    |
| ::public static str computerName()                                                                                                                                                                                                                                                                                                                                                                 |                                                    |
| ::public static boolean hasClient()                                                                                                                                                                                                                                                                                                                                                                |                                                    |
| ::public static int infologLine()                                                                                                                                                                                                                                                                                                                                                                  | Returns the number of lines in the Infolog buffer. |
| ::public static boolean isAOS()                                                                                                                                                                                                                                                                                                                                                                    |                                                    |
| ::public static boolean isGuest()                                                                                                                                                                                                                                                                                                                                                                  |                                                    |
| ::public static boolean isUserLanguageRTL()                                                                                                                                                                                                                                                                                                                                                        |                                                    |
| ::public static container languageList()                                                                                                                                                                                                                                                                                                                                                           |                                                    |
| ::public static str machineTzDisplayName()                                                                                                                                                                                                                                                                                                                                                         |                                                    |
| ::public static boolean isObjectOnServer(AnyType object)                                                                                                                                                                                                                                                                                                                                           |                                                    |
| ::public static int randomPositiveInt32()                                                                                                                                                                                                                                                                                                                                                          |                                                    |
| ::public static boolean terminalServer()                                                                                                                                                                                                                                                                                                                                                           |                                                    |
| ::public static WorkerSessionType workerSessionType()                                                                                                                                                                                                                                                                                                                                              |                                                    |
| ::public static System.Threading.Tasks.Task runAsync(int runAsClassId, str runAsStaticMethodName, container parms, \[System.Threading.CancellationToken cancellationToken\], \[int callbackClassId\], \[str callbackStaticMethodName\], \[container asyncState\], \[str userId\], \[str company\], \[str language\], \[str partitionKey\], \[System.Threading.Tasks.TaskCreationOptions options\]) |                                                    |
| ::public static System.Threading.Tasks.Task runAsyncWithObjectCallback(int runAsClassId, str runAsStaticMethodName, container parms, Object callbackObject, str callbackStaticMethodName)                                                                                                                                                                                                          |                                                    |
| ::public static void forceFormPreload()                                                                                                                                                                                                                                                                                                                                                            | Forces form preloading to occur immediately.       |
| private void new()                                                                                                                                                                                                                                                                                                                                                                                 | Initializes a new instance of the xGlobal class.   |

## Method clientKind

```xpp
public static ClientType clientKind()
```

### Return Value - clientKind

## Method company

```xpp
public static SelectableDataArea company(TableId tableid, [SelectableDataArea company])
```

### Parameters - company

tableid  

<!-- -->

company  

### Return Value - company

## Method computerName

```xpp
public static str computerName()
```

### Return Value - computerName

## Method hasClient

```xpp
public static boolean hasClient()
```

### Return Value - hasClient

## Method infologLine

Returns the number of lines in the Infolog buffer.

```xpp
public static int infologLine()
```

### Return Value - infologLine

### Remarks - infologLine

This method has similar functionality to the xInfo.line method, but it improves performance and lowers network load when you are executing server-side code. When xInfo.line is run on the server, it makes a call to the client to retrieve the number of lines in the Infolog buffer. The xGlobal::infologLine method retrieves the line count of the server-side Infolog buffer, so that you do not have to call to the client. When the xGlobal::infologLine method is called on the client, it returns the count directly from the Infolog buffer on the client. This method is especially useful when you are writing server-side code that processes exceptions. The number of lines in the Infolog is typically stored before a try/catch block is entered. If an exception occurs, the number of lines that were previously stored is used to determine which messages were logged during the code in the try block. If no exceptions occur, the stored Infolog buffer line count is often unused. By using the xGlobal::infologLine method instead of the xInfo.line method to retrieve the Infolog lines, you avoid a round trip to the client.

## Method isAOS

```xpp
public static boolean isAOS()
```

### Return Value - isAOS

## Method isGuest

```xpp
public static boolean isGuest()
```

### Return Value - isGuest

## Method isUserLanguageRTL

```xpp
public static boolean isUserLanguageRTL()
```

### Return Value - isUserLanguageRTL

## Method languageList

```xpp
public static container languageList()
```

### Return Value - languageList

## Method machineTzDisplayName

```xpp
public static str machineTzDisplayName()
```

### Return Value - machineTzDisplayName

## Method isObjectOnServer

```xpp
public static boolean isObjectOnServer(AnyType object)
```

### Parameters - isObjectOnServer

object  

### Return Value - isObjectOnServer

## Method randomPositiveInt32

```xpp
public static int randomPositiveInt32()
```

### Return Value - randomPositiveInt32

## Method terminalServer

```xpp
public static boolean terminalServer()
```

### Return Value - terminalServer

## Method workerSessionType

```xpp
public static WorkerSessionType workerSessionType()
```

### Return Value - workerSessionType

## Method runAsync

```xpp
public static System.Threading.Tasks.Task runAsync(int runAsClassId, str runAsStaticMethodName, container parms, [System.Threading.CancellationToken cancellationToken], [int callbackClassId], [str callbackStaticMethodName], [container asyncState], [str userId], [str company], [str language], [str partitionKey], [System.Threading.Tasks.TaskCreationOptions options])
```

### Parameters - runAsync

runAsClassId  

<!-- -->

runAsStaticMethodName  

<!-- -->

parms  

<!-- -->

cancellationToken  

<!-- -->

callbackClassId  

<!-- -->

callbackStaticMethodName  

<!-- -->

asyncState  

<!-- -->

userId  

<!-- -->

company  

<!-- -->

language  

<!-- -->

partitionKey  

<!-- -->

options  

### Return Value - runAsync

## Method runAsyncWithObjectCallback

```xpp
public static System.Threading.Tasks.Task runAsyncWithObjectCallback(int runAsClassId, str runAsStaticMethodName, container parms, Object callbackObject, str callbackStaticMethodName)
```

### Parameters - runAsyncWithObjectCallback

runAsClassId  

<!-- -->

runAsStaticMethodName  

<!-- -->

parms  

<!-- -->

callbackObject  

<!-- -->

callbackStaticMethodName  

### Return Value - runAsyncWithObjectCallback

## Method forceFormPreload

Forces form preloading to occur immediately.

```xpp
public static void forceFormPreload()
```

### Remarks - forceFormPreload

Normally, preloading occurs only when the client has gone idle. In scenarios where long-running X++ execution is occurring, this method can be used to force form preloading.

## Method new

Initializes a new instance of the xGlobal class.

```xpp
private void new()
```

