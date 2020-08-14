---
title: xSession class
description: This topic describes the xSession class.
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

# Class xSession

[!include [banner](../../includes/banner.md)]

```xpp
class xSession extends Object
```

Gets information about sessions.

## Remarks

To get information about the current session, create a new xSession session without parameters. The only way to get information about all active sessions (AOS only) is to traverse from session ID 1 to xSession.maxSessionId. The IDs are not an unbroken list, but will never exceed the maximum number of sessions as specified in the maxSessionId method.

## Examples

The following example creates a new xSession object, and then uses it to find the name of the server for the current session.

```xpp
xSession xSession; 
xSession = new xSession();   
// Prints the name of server for the current session. 
print xSession.AOSName();
```

## Methods

| Method                                                                            | Description                                                                                                                    |
|-----------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------|
| public str AOSName()                                                              | Retrieves the name of the Application Object Server (AOS) that is responsible for servicing the session.                       |
| public str clientComputerName()                                                   | Retrieves the network name of the client computer that is responsible for servicing the session.                               |
| public ClientType clientKind()                                                    | Retrieves the type of the client that is responsible for servicing the session.                                                |
| public str databaseSpid()                                                         | Retrieves a comma-separated list of active connection IDs.                                                                     |
| public str documentationLanguage()                                                | Retrieves the language ID of the documentation that is shown for the session.                                                  |
| public str interfaceLanguage()                                                    | Retrieves the ID for the language that is used on menus and dialogs for the session.                                           |
| public boolean isWorkerThread()                                                   | Determines whether the session is a worker thread.                                                                             |
| public Date loginDate()                                                           | Retrieves the date on which the user of the session logged on.                                                                 |
| public DateTime loginDateTime()                                                   |                                                                                                                                |
| public TimeOfDay loginTime()                                                      | Retrieves the time at which the user of the session logged on.                                                                 |
| public int masterSessionId()                                                      | Retrieves the master session ID for the session that the xSession object covers.                                               |
| public int serverId()                                                             |                                                                                                                                |
| public int sessionId()                                                            | Retrieves the session ID of the session that the xSession object covers.                                                       |
| public boolean terminate(\[Date loginDate\], \[TimeOfDay loginTime\])             | Terminates the session ID that the object was instantiated with.                                                               |
| public UserId userId()                                                            | Retrieves the user ID that this session is logged on with.                                                                     |
| ::public static int currentRetryCount()                                           | Counts the number of times a try block has been retried after a deadlock, an update conflict, or another exception.            |
| ::public static Uncheck currentUnCheck()                                          |                                                                                                                                |
| ::public static str getDbSchema()                                                 | Retrieves the schema part of the database object name for the session.                                                         |
| ::public static COM getIISObject(IISObject object)                                | Instantiates and returns a COM object for an IIS object.                                                                       |
| ::public static boolean getSysTraceActive()                                       | Enables you to determine whether system tracing is turned on for the session.                                                  |
| ::public static str getXRefAssembyTempFolder()                                    |                                                                                                                                |
| ::public static boolean isCLRSession()                                            |                                                                                                                                |
| ::public static boolean isUserPreferredTzSameAsLocalMachine()                     |                                                                                                                                |
| ::public static int lastDuplicateKeyViolatingTable()                              |                                                                                                                                |
| ::public static int lastUpdateConflictingTable()                                  | Retrieves an instance of the table that most recently had an update conflict.                                                  |
| ::public static int maxSessionId()                                                | Retrieves the maximum number of sessions that are permitted by the current license codes.                                      |
| ::public static int numSession()                                                  | Retrieves the current number of registered sessions.                                                                           |
| public PreferredLocale preferredLocale()                                          |                                                                                                                                |
| ::public static int pseudoBandwidth(\[int bandwidth\])                            | Determines whether bandwidth simulation is turned on for the session, and enables bandwidth simulation to be turned on or off. |
| ::public static int pseudoLatency(\[int latency\])                                | Determines whether latency simulation is turned on for the session, and enables latency simulation to be turned on or off.     |
| ::public static int pseudoSimMode(\[int simMode\])                                | Determines whether delay simulation is turned on for the session, and enables delay simulation to be turned on or off.         |
| ::public static int systemSessionId()                                             | Retrieves the system session ID for the session that the xSession object covers.                                               |
| ::public static container xppCallStack()                                          | Retrieves the current call stack.                                                                                              |
| ::public static void removeAOC()                                                  | Removes the Application Object Server client-side cache (AOC) for the current session.                                         |
| ::public static void updateAOC()                                                  | Updates the Application Object Server client-side cache (AOC) for the current session.                                         |
| ::public static void setAutoUpdateRecVersion(boolean autoUpdateRecVersion)        |                                                                                                                                |
| ::public static void setSysTraceActive(boolean nValue)                            | Switches system tracing on or off.                                                                                             |
| ::private static void clientSetAutoUpdateRecVersion(boolean autoUpdateRecVersion) |                                                                                                                                |
| ::private static void serverSetAutoUpdateRecVersion(boolean autoUpdateRecVersion) |                                                                                                                                |
| public void new(\[int sessionId\], \[boolean checkSession\])                      | Instantiates the xSession object, either for current session or for the session ID passed in as a parameter.                   |
| ::public static void reloadTableCollectionOnClient()                              |                                                                                                                                |

## Method AOSName

Retrieves the name of the Application Object Server (AOS) that is responsible for servicing the session.

```xpp
public str AOSName()
```

### Return Value - AOSName

A string that indicates the name of the AOS.

### Remarks - AOSName

For non�AOS connected clients, this method returns an empty string.

### Examples - AOSName

The following example prints the name of the AOS that is running the current session.

```xpp
xSession xSession; 
xSession = new xSession(); 
// Prints the name of server for the current session. 
print xSession.AOSName();
```

## Method clientComputerName

Retrieves the network name of the client computer that is responsible for servicing the session.

```xpp
public str clientComputerName()
```

### Return Value - clientComputerName

A string that indicates the name of the client computer.

### Examples - clientComputerName

The following example prints the name of the client that is running the current session.

```xpp
{ 
    xSession xSession; 
    xSession = new xSession(); 
    print xSession.clientComputerName(); 
    pause; 
}
```

## Method clientKind

Retrieves the type of the client that is responsible for servicing the session.

```xpp
public ClientType clientKind()
```

### Return Value - clientKind

The type of the client.

### Remarks - clientKind

The possible values are those in the ClientType system enumeration:

-   COMObject
-   Client
-   Server
-   WorkerThread

### Examples - clientKind

The following example prints the type of the client that is running the current session.

```xpp
{ 
    xSession xSession; 
    xSession = new xSession(); 
    print xSession.clientKind(); 
    pause; 
}
```

## Method databaseSpid

Retrieves a comma-separated list of active connection IDs.

```xpp
public str databaseSpid()
```

### Return Value - databaseSpid

A comma-separated list of active connection IDs.

### Remarks - databaseSpid

This method is used to populate the Online users form (SysUsersOnline). To retrieve the number of active connections, use xSession::numSession.

## Method documentationLanguage

Retrieves the language ID of the documentation that is shown for the session.

```xpp
public str documentationLanguage()
```

### Return Value - documentationLanguage

A string that contains the ID of the language that is used for the documentation in the session.

### Remarks - documentationLanguage

For example, this method returns "en-us" if the language is set to US English. The documentation language can be selected separately and is not necessarily identical to the language used in menus and dialogs. To retrieve the language ID for menus and dialogs, use xSession.interfaceLanguage. xInfo.documentationLanguage enables you to set the documentation language.

## Method interfaceLanguage

Retrieves the ID for the language that is used on menus and dialogs for the session.

```xpp
public str interfaceLanguage()
```

### Return Value - interfaceLanguage

A string that contains the ID of the language used on menus and dialogs in the session.

### Remarks - interfaceLanguage

For example, this method returns "en-us" if the language is set to US English. The documentation language can be selected separately and is not necessarily identical to the language used in menus and dialogs. To retrieve the language ID for documentation, use .

## Method isWorkerThread

Determines whether the session is a worker thread.

```xpp
public boolean isWorkerThread()
```

### Return Value - isWorkerThread

true if the session is a worker thread; otherwise, false.

### Remarks - isWorkerThread

A worker thread is an instance of the Thread class, which creates a new instance without UI. If this method is called inside such a session, it will return true.

## Method loginDate

Retrieves the date on which the user of the session logged on.

```xpp
public Date loginDate()
```

### Return Value - loginDate

The date that the user of the session logged on.

## Method loginDateTime

```xpp
public DateTime loginDateTime()
```

### Return Value - loginDateTime

## Method loginTime

Retrieves the time at which the user of the session logged on.

```xpp
public TimeOfDay loginTime()
```

### Return Value - loginTime

The time that the user of the session logged on.

## Method masterSessionId

Retrieves the master session ID for the session that the xSession object covers.

```xpp
public int masterSessionId()
```

### Return Value - masterSessionId

An integer that represents the session ID.

### Remarks - masterSessionId

Some sessions have a master session ID, such as a COM session or a worker thread session.

### Examples - masterSessionId

The following example creates an xSession object by using the normal session ID (or the master session ID, if there is one).

```xpp
static xSession getThisSession() 
{ 
    xSession xSession = new xSession(sessionid()); 
    if (xSession.masterSessionId()) 
    { 
        xSession = new xSession(xSession.masterSessionId()); 
    } 
    return xSession; 
}
```

## Method serverId

```xpp
public int serverId()
```

### Return Value - serverId

## Method sessionId

Retrieves the session ID of the session that the xSession object covers.

```xpp
public int sessionId()
```

### Return Value - sessionId

An integer that represents the session ID.

## Method terminate

Terminates the session ID that the object was instantiated with.

```xpp
public boolean terminate([Date loginDate], [TimeOfDay loginTime])
```

### Parameters - terminate

loginDate  
The time that the user of the session logged on; optional.

<!-- -->

loginTime  
The time that the user of the session logged on; optional.

### Return Value - terminate

false if the user is not authorized to perform this function; otherwise, true.

### Remarks - terminate

This API has a built-in authorization check that is invoked at run time. An exception is thrown if calls to the terminate method are made by users who do not have access to the development security key (SysDevelopment). The optional parameters allow you to put a timestamp on the session to ensure that it is the session you intend to terminate. The same session ID could be used at two different times. The terminate method is used in the Online users form to allow administrators to terminate sessions. An administrator might decide to terminate a session because it has stopped responding, is consuming a lot of resources, or its license needs to be freed for another user.

### Examples - terminate

The following example confirms whether the user has permission to terminate the session. If so, the session is terminated.

```xpp
server static public void Main(Args _args) 
{ 
    Session session; 
    session = new Session(); 
    if (session) 
    { 
        session.terminate(); 
    } 
}
```

## Method userId

Retrieves the user ID that this session is logged on with.

```xpp
public UserId userId()
```

### Return Value - userId

The ID for the user of the session.

### Examples - userId

The following example determines whether a particular user is online.

```xpp
server static boolean isUserOnline(userId userId) 
{ 
    xSession    session; 
    int counter; 
    int maxSessions = Info::licensedUsersTotal(); 
    if (!userId) 
    { 
        return false; 
    } 
    for(counter = 1; counter < maxSessions;counter++) 
    { 
        session = new xSession(counter, true); 
        if(session && session.userId() == userId) 
        { 
            return true; 
        } 
    } 
    return false; 
}
```

## Method currentRetryCount

Counts the number of times a try block has been retried after a deadlock, an update conflict, or another exception.

```xpp
public static int currentRetryCount()
```

### Return Value - currentRetryCount

The number of times that the try block has been retried.

### Examples - currentRetryCount

The following example uses the currentRetryCount method to test how many times that a transaction has been retried to determine the exception handling for a CUD transaction.

```xpp
catch (Exception::UpdateConflict) 
    { 
        if (appl.ttsLevel() == 0) 
        { 
            if (xSession::currentRetryCount() >= #RetryNum) 
            { 
                throw Exception::UpdateConflictNotRecovered; 
            } 
            else 
            { 
                retry; 
            } 
        } 
        else 
        { 
            throw Exception::UpdateConflict; 
        } 
    }
```

## Method currentUnCheck

```xpp
public static Uncheck currentUnCheck()
```

### Return Value - currentUnCheck

## Method getDbSchema

Retrieves the schema part of the database object name for the session.

```xpp
public static str getDbSchema()
```

### Return Value - getDbSchema

Returns the schema part of the database object name.

## Method getIISObject

Instantiates and returns a COM object for an IIS object.

```xpp
public static COM getIISObject(IISObject object)
```

### Parameters - getIISObject

object  
The IIS object that you want to create a COM object for.

### Return Value - getIISObject

A COM object.

### Remarks - getIISObject

The IIS object can be one of the possible values supplied by the IISObject system enumeration:

-   ApplicationObject
-   Request
-   Response
-   Server
-   SessionObject

## Method getSysTraceActive

Enables you to determine whether system tracing is turned on for the session.

```xpp
public static boolean getSysTraceActive()
```

### Return Value - getSysTraceActive

true if system tracing is active; otherwise, false.

### Remarks - getSysTraceActive

To turn on system tracing, use xSession::setSysTraceActive.

### Examples - getSysTraceActive

The following example uses the getSysTraceActive method to determine the original setting for system tracing and to reset the setting after tracing is temporarily set to false.

```xpp
server static void main(Args a) 
{ 
    SysDataImport sysDataImport; 
    boolean       sysTraceActive = xSession::getSysTraceActive(); 
    sysDataImport = SysDataImport::newTmpFilename(''); 
    sysDataImport.addTmpExpImpTable( 
        tablenum(SysTraceTableSQL), 
        false); 
    sysDataImport.addTmpExpImpTable( 
        tablenum(SysTraceTableSQLExecPlan), 
        false); 
    sysDataImport.addTmpExpImpTable( 
        tablenum(SysTraceTableSQLTabRef), 
        false); 
    xSession::setSysTraceActive(FALSE); 
    if (sysDataImport.prompt()) 
        sysDataImport.run(); 
    xSession::setSysTraceActive(sysTraceActive); 
}
```

## Method getXRefAssembyTempFolder

```xpp
public static str getXRefAssembyTempFolder()
```

### Return Value - getXRefAssembyTempFolder

## Method isCLRSession

```xpp
public static boolean isCLRSession()
```

### Return Value - isCLRSession

## Method isUserPreferredTzSameAsLocalMachine

```xpp
public static boolean isUserPreferredTzSameAsLocalMachine()
```

### Return Value - isUserPreferredTzSameAsLocalMachine

## Method lastDuplicateKeyViolatingTable

```xpp
public static int lastDuplicateKeyViolatingTable()
```

### Return Value - lastDuplicateKeyViolatingTable

## Method lastUpdateConflictingTable

Retrieves an instance of the table that most recently had an update conflict.

```xpp
public static int lastUpdateConflictingTable()
```

### Return Value - lastUpdateConflictingTable

An instance of the table that most recently had an update conflict.

### Examples - lastUpdateConflictingTable

The following example demonstrates the general use of the lastUpdateConflictingTable method�it enables you to abort or retry transactions according to which table has an update conflict.

```xpp
try 
{ 
    // ... 
    table1.update(); 
    // ... 
    table2.update(); 
} 
catch(Exception::UpdateConflict) 
{ 
    if(xSession::lastUpdateConflictingTable() == table1) 
    { 
        ttsabort; 
    } 
    else if(xSession::lastUpdateConflictingTable() == table2) 
    { 
        // Compensate here. 
        // ... 
        retry; 
    } 
}
```

## Method maxSessionId

Retrieves the maximum number of sessions that are permitted by the current license codes.

```xpp
public static int maxSessionId()
```

### Return Value - maxSessionId

An integer that indicates the maximum number of sessions that are permitted by the current license code.

## Method numSession

Retrieves the current number of registered sessions.

```xpp
public static int numSession()
```

### Return Value - numSession

An integer that indicates the number of currently registered sessions.

## Method preferredLocale

```xpp
public PreferredLocale preferredLocale()
```

### Return Value - preferredLocale

## Method pseudoBandwidth

Determines whether bandwidth simulation is turned on for the session, and enables bandwidth simulation to be turned on or off.

```xpp
public static int pseudoBandwidth([int bandwidth])
```

### Parameters - pseudoBandwidth

bandwidth  
Turns bandwidth simulation on or off. Set to zero to turn simulation off. Other values turn simulation on.

### Return Value - pseudoBandwidth

An integer that indicates whether bandwidth simulation is turned on. If the return value is zero, there is no bandwidth simulation.

### Remarks - pseudoBandwidth

You can run pseudo simulations of remote connections from the System monitoring tool:

-   On the toolbar, select Tools, point to Development tools, point to System monitoring, and then click the Remote connection tab.

## Method pseudoLatency

Determines whether latency simulation is turned on for the session, and enables latency simulation to be turned on or off.

```xpp
public static int pseudoLatency([int latency])
```

### Parameters - pseudoLatency

latency  
Turns latency simulation on or off. Set to zero to turn simulation off. Other values turn simulation on.

### Return Value - pseudoLatency

An integer that indicates whether latency simulation is turned on. If the return value is zero, there is no latency simulation.

### Remarks - pseudoLatency

You can run pseudo simulations of remote connections from the System monitoring tool:

-   On the toolbar, select Tools, point to Development tools, point to System monitoring, and then click the Remote connection tab

## Method pseudoSimMode

Determines whether delay simulation is turned on for the session, and enables delay simulation to be turned on or off.

```xpp
public static int pseudoSimMode([int simMode])
```

### Parameters - pseudoSimMode

simMode  
Turns delay simulation on or off. Set to zero to turn simulation off. Set to 1 to simulate delays for application calls. Set to 2 to simulate delays for all calls.

### Return Value - pseudoSimMode

An integer that indicates whether delay simulation is turned on. If the return value is zero, there is no delay simulation. If the return value is 1, delays are simulated only for application-controlled calls. If the return value is 2, delays are simulated for all calls.

### Remarks - pseudoSimMode

You can run pseudo simulations of remote connections from the System monitoring tool:

-   On the toolbar, select Tools, point to Development tools, point to System monitoring, and then click the Remote connection tab

## Method systemSessionId

Retrieves the system session ID for the session that the xSession object covers.

```xpp
public static int systemSessionId()
```

### Return Value - systemSessionId

An integer that represents the session ID.

### Remarks - systemSessionId

Some sessions, such as a COM session or a worker thread session, have a parent system session.

## Method xppCallStack

Retrieves the current call stack.

```xpp
public static container xppCallStack()
```

### Return Value - xppCallStack

A container that holds the contents of the current call stack.

## Method removeAOC

Removes the Application Object Server client-side cache (AOC) for the current session.

```xpp
public static void removeAOC()
```

## Method updateAOC

Updates the Application Object Server client-side cache (AOC) for the current session.

```xpp
public static void updateAOC()
```

### Remarks - updateAOC

AOC is a client-side cache that consists of metadata that is loaded by the client, and then saved to disk when the client is closed. It is saved under the user�s local settings folder. The file has an .auc filename extension and is saved in a user's Local Settings folder. When the client is started, it reads from the cache, and then deletes the cache from the disk.

## Method setAutoUpdateRecVersion

```xpp
public static void setAutoUpdateRecVersion(boolean autoUpdateRecVersion)
```

### Parameters - setAutoUpdateRecVersion

autoUpdateRecVersion  

## Method setSysTraceActive

Switches system tracing on or off.

```xpp
public static void setSysTraceActive(boolean nValue)
```

### Parameters - setSysTraceActive

nValue  
A Boolean value that determines whether tracing should be switched on or off. Set to true to switch tracing on.

### Examples - setSysTraceActive

The following example uses the setSysTraceActive method to turn system tracing off when data is imported.

```xpp
server static void main(Args a) 
{ 
    SysDataImport sysDataImport; 
    boolean       sysTraceActive = xSession::getSysTraceActive(); 
    sysDataImport = SysDataImport::newTmpFilename(''); 
    sysDataImport.addTmpExpImpTable( 
        tablenum(SysTraceTableSQL), 
        false); 
    sysDataImport.addTmpExpImpTable( 
        tablenum(SysTraceTableSQLExecPlan), 
        false); 
    sysDataImport.addTmpExpImpTable( 
        tablenum(SysTraceTableSQLTabRef), 
        false); 
    xSession::setSysTraceActive(FALSE); 
    if (sysDataImport.prompt()) 
        sysDataImport.run(); 
    xSession::setSysTraceActive(sysTraceActive); 
}
```

## Method clientSetAutoUpdateRecVersion

```xpp
private static void clientSetAutoUpdateRecVersion(boolean autoUpdateRecVersion)
```

### Parameters - clientSetAutoUpdateRecVersion

autoUpdateRecVersion  

## Method serverSetAutoUpdateRecVersion

```xpp
private static void serverSetAutoUpdateRecVersion(boolean autoUpdateRecVersion)
```

### Parameters - serverSetAutoUpdateRecVersion

autoUpdateRecVersion  

## Method new

Instantiates the xSession object, either for current session or for the session ID passed in as a parameter.

```xpp
public void new([int sessionId], [boolean checkSession])
```

### Parameters - new

sessionId  
A boolean flag that, if set to true, checks to determine whether the session specified by the \_SessionId parameter exists. The operation that checks whether a session exists might use a lot of system resources. This parameter is therefore set to false by default.

<!-- -->

checkSession  
A boolean flag that, if set to true, checks to determine whether the session specified by the \_SessionId parameter exists. The operation that checks whether a session exists might use a lot of system resources. This parameter is therefore set to false by default.

### Examples - new

The following example returns a count of all the active sessions.

```xpp
server static Integer getAllOnlineUserCount() 
{ 
    int      counter; 
    int      num = 0; 
    int      maxSessions = Info::licensedUsersTotal(); 
    xSession session; 
    UserInfo userInfo; 
    for(counter = 1; counter < maxSessions;counter++) 
    { 
        session = new xSession(counter, true); 
        if(session && session.userId()) 
        { 
            select firstonly userInfo 
                where userInfo.Id == session.userId(); 
            if (userInfo) 
                num++; 
        } 
    } 
    return num; 
}
```

## Method reloadTableCollectionOnClient

```xpp
public static void reloadTableCollectionOnClient()
```

