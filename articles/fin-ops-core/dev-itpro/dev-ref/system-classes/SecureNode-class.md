---
title: SecureNode class
description: This topic describes the SecureNode class.
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

# Class SecureNode

[!include [banner](../../includes/banner.md)]

```xpp
class SecureNode extends TreeNode
```

The SecureNode class lets you create, read, update, and delete X++ code and metadata.

## Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

## Examples

## Methods

| Method                                                                          | Description                                                             |
|---------------------------------------------------------------------------------|-------------------------------------------------------------------------|
| public boolean checkAccessRights()                                              |                                                                         |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])        | Gets or sets the configuration key that is assigned to the control.     |
| public ConfigurationKeyId countryConfigurationkey(\[ConfigurationKeyId value\]) |                                                                         |
| public boolean extendedDataSecurity(\[boolean value\])                          |                                                                         |
| public boolean isWeb()                                                          |                                                                         |
| public int neededAccessLevel(\[int value\])                                     | Gets or sets the neededAccessLevel property for the MenuFunction class. |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                       |                                                                         |
| public ConfigurationKeyId webConfigurationkey(\[ConfigurationKeyId value\])     |                                                                         |

## Method checkAccessRights

```xpp
public boolean checkAccessRights()
```

### Return Value - checkAccessRights

## Method configurationKey

Gets or sets the configuration key that is assigned to the control.

```xpp
public ConfigurationKeyId configurationKey([ConfigurationKeyId value])
```

### Parameters - configurationKey

value  

### Return Value - configurationKey

The identifier of the configuration key that is assigned to the control.

### Remarks - configurationKey

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

## Method countryConfigurationkey

```xpp
public ConfigurationKeyId countryConfigurationkey([ConfigurationKeyId value])
```

### Parameters - countryConfigurationkey

value  

### Return Value - countryConfigurationkey

## Method extendedDataSecurity

```xpp
public boolean extendedDataSecurity([boolean value])
```

### Parameters - extendedDataSecurity

value  

### Return Value - extendedDataSecurity

## Method isWeb

```xpp
public boolean isWeb()
```

### Return Value - isWeb

## Method neededAccessLevel

Gets or sets the neededAccessLevel property for the MenuFunction class.

```xpp
public int neededAccessLevel([int value])
```

### Parameters - neededAccessLevel

value  

### Return Value - neededAccessLevel

The current value of the neededAccessLevel property.

### Remarks - neededAccessLevel

The possible values for the AccessType system enumeration value are as follows:

-   AccessType::NoAccess.
-   AccessType::View.
-   AccessType::Edit.
-   AccessType::Add.
-   AccessType::Delete.

## Method securityKey

```xpp
public SecurityKeyId securityKey([SecurityKeyId value])
```

### Parameters - securityKey

value  

### Return Value - securityKey

## Method webConfigurationkey

```xpp
public ConfigurationKeyId webConfigurationkey([ConfigurationKeyId value])
```

### Parameters - webConfigurationkey

value  

### Return Value - webConfigurationkey

