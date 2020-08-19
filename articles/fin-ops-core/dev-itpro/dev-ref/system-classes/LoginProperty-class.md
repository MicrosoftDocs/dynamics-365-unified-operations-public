---
title: LoginProperty class
description: This topic describes the LoginProperty class.
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

# Class LoginProperty

[!include [banner](../../includes/banner.md)]

```xpp
class LoginProperty extends Object
```

The LoginProperty class enables logon information to be passed to an instance of the OdbcConnection class.

## Remarks

## Examples

## Methods

| Method                                                | Description                                                                                                                                                                                            |
|-------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public str getDatabase()                              | Retrieves the name of the database, as stored in the LoginProperty class.                                                                                                                              |
| public str getDSN()                                   | Retrieves the data source name (DSN) that is stored in the LoginProperty class.                                                                                                                        |
| public str getOciServiceName()                        | Retrieves the Oracle service name that is stored in the LoginProperty class.                                                                                                                           |
| public str getOther()                                 | Retrieves the additional logon parameters that are stored in the LoginProperty class.                                                                                                                  |
| public str getServer()                                | Retrieves the server name that is stored in the LoginProperty class.                                                                                                                                   |
| public str getTcpIpPort()                             | Retrieves the TCP/IP port that is stored in the LoginProperty class.                                                                                                                                   |
| public boolean getUsePredefinedService()              | Returns whether the loginProperty class is set to use a predefined Oracle service instead of specifying the server and database information on the loginProperty class.                                |
| public void setTcpIpPort(str tcpipPort)               | Specifies which TCP/IP port is used to connect to Oracle.                                                                                                                                              |
| public void setDatabase(str database)                 | Sets the name of the database to log on to.                                                                                                                                                            |
| public void setDSN(str datasourceName)                | Sets the DSN that is used to access the data source.                                                                                                                                                   |
| public void new()                                     | Initializes a new instance of the LoginProperty class.                                                                                                                                                 |
| public void setOciServiceName(str ociServiceName)     | Specifies an Oracle service name.                                                                                                                                                                      |
| public void setOther(str otherOdbcParameters)         | Sets additional nonstandard logon parameters that are stored in the LoginProperty class.                                                                                                               |
| public void setServer(str serverName)                 | Sets the name of the server on which the database resides.                                                                                                                                             |
| public void setUsePredefinedService(boolean newValue) | Specifies whether to use a predefined Oracle service (created by using Oracle network configuration tools) for the connection information, or whether it will be specified in the loginProperty class. |

## Method getDatabase

Retrieves the name of the database, as stored in the LoginProperty class.

```xpp
public str getDatabase()
```

### Return Value - getDatabase

The name of the database.

## Method getDSN

Retrieves the data source name (DSN) that is stored in the LoginProperty class.

```xpp
public str getDSN()
```

### Return Value - getDSN

The DSN.

## Method getOciServiceName

Retrieves the Oracle service name that is stored in the LoginProperty class.

```xpp
public str getOciServiceName()
```

### Return Value - getOciServiceName

The Oracle service name.

## Method getOther

Retrieves the additional logon parameters that are stored in the LoginProperty class.

```xpp
public str getOther()
```

### Return Value - getOther

The additional logon parameters as a string.

## Method getServer

Retrieves the server name that is stored in the LoginProperty class.

```xpp
public str getServer()
```

### Return Value - getServer

The name of the server.

## Method getTcpIpPort

Retrieves the TCP/IP port that is stored in the LoginProperty class.

```xpp
public str getTcpIpPort()
```

### Return Value - getTcpIpPort

The TCP/IP port.

## Method getUsePredefinedService

Returns whether the loginProperty class is set to use a predefined Oracle service instead of specifying the server and database information on the loginProperty class.

```xpp
public boolean getUsePredefinedService()
```

### Return Value - getUsePredefinedService

true if a predefined Oracle service is used to connect; otherwise, false.

## Method setTcpIpPort

Specifies which TCP/IP port is used to connect to Oracle.

```xpp
public void setTcpIpPort(str tcpipPort)
```

### Parameters - setTcpIpPort

tcpipPort  
The TCP/IP port to use.

### Remarks - setTcpIpPort

The default port is 1521.

## Method setDatabase

Sets the name of the database to log on to.

```xpp
public void setDatabase(str database)
```

### Parameters - setDatabase

database  
The name of the database.

## Method setDSN

Sets the DSN that is used to access the data source.

```xpp
public void setDSN(str datasourceName)
```

### Parameters - setDSN

datasourceName  
The name of the data source.

## Method new

Initializes a new instance of the LoginProperty class.

```xpp
public void new()
```

## Method setOciServiceName

Specifies an Oracle service name.

```xpp
public void setOciServiceName(str ociServiceName)
```

### Parameters - setOciServiceName

ociServiceName  
The name of the service.

### Remarks - setOciServiceName

This method is used when the loginProperty class is not set to use a predefined Oracle service.

## Method setOther

Sets additional nonstandard logon parameters that are stored in the LoginProperty class.

```xpp
public void setOther(str otherOdbcParameters)
```

### Parameters - setOther

otherOdbcParameters  
The additional ODBC-formatted parameters.

### Remarks - setOther

This method should be used only if the data source that you want to use requires some additional, nonstandard parameters. The parameters must be applied in the standard ODBC format: &lt;parm1&gt;=&lt;value1&gt;;&lt;parm2&gt;=&lt;value2&gt;,... For example: MODE=1;PATCH=32

## Method setServer

Sets the name of the server on which the database resides.

```xpp
public void setServer(str serverName)
```

### Parameters - setServer

serverName  
The name of the server where the database is located.

## Method setUsePredefinedService

Specifies whether to use a predefined Oracle service (created by using Oracle network configuration tools) for the connection information, or whether it will be specified in the loginProperty class.

```xpp
public void setUsePredefinedService(boolean newValue)
```

### Parameters - setUsePredefinedService

newValue  
A Boolean value that indicates whether to use a predefined Oracle service.

### Remarks - setUsePredefinedService

By default, a predefined service is not used.


