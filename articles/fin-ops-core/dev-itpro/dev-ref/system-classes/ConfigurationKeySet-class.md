---
title: ConfigurationKeySet class
description: This topic describes the ConfigurationKeySet class.
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

# Class ConfigurationKeySet

[!include [banner](../../includes/banner.md)]

```xpp
class ConfigurationKeySet extends Object
```

The ConfigurationKeySet class enables working with a tree of configuration keys.

## Remarks

When a new ConfigurationKeySet is created, a tree of configuration keys is created, where all keys are set by default to "enabled". The cnt method is used to loop through all configuration keys and count them. The cntID method is used to retrieve the IDs of the configuration keys. In situations in which a configuration key has been deleted and the key IDs are ID1, ID2, ID5, and so on, this method will distinguish the number of configuration keys compared to their IDs. When a new ConfigurationKeySet is created, all configuration keys are enabled. The system will then call the loadSystemSetup method, which scans the SysConfig table where the configuration types are stored. It loops through the configuration key setup and identifies what is enabled. Next, the enabled method is called. Every time a configuration key is disabled, all sub-configuration keys are also automatically disabled. In a situation in which a top node is enabled and one of the sub-nodes is disabled, the kernel will remember which configuration key sub-nodes were previously disabled whenever a top node is disabled.

## Examples

## Methods

| Method                                                                            | Description                                                                                                             |
|-----------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| public int cnt()                                                                  | Retrieves the number of configuration keys that are defined in the Application Object Tree (AOT). |
| public ConfigurationKeyId cnt2Id(int cnt)                                         | Retrieves the ID of the *n*th configuration key.                                                                        |
| public boolean enabled(ConfigurationKeyId configurationKeyId, \[boolean enable\]) | Determines whether to enable or disable the object.                                                                     |
| public container pack()                                                           | Serializes the current instance of the ConfigurationKeySet class.                                                       |
| public boolean touchedByUser(ConfigurationKeyId configurationKeyId)               |                                                                                                                         |
| public void new(\[container container\])                                          | Initializes a new instance of the Object class.                                                                         |
| public void loadSystemSetup()                                                     |                                                                                                                         |

## Method cnt

Retrieves the number of configuration keys that are defined in the Application Object Tree (AOT).

```xpp
public int cnt()
```

### Return Value - cnt

The number of configuration keys that are defined in the AOT.

## Method cnt2Id

Retrieves the ID of the *n*th configuration key.

```xpp
public ConfigurationKeyId cnt2Id(int cnt)
```

### Parameters - cnt2Id

cnt  
The index of the configuration key, which must be between 1 and the number of configuration keys.

### Return Value - cnt2Id

The ID of the specified configuration key.

### Remarks - cnt2Id

To find the number of configuration keys, use the cnt method. In general, the index and ID will differ, because not all the IDs are used.

### Examples - cnt2Id

```xpp
ConfigurationKeySet configKeySet = new ConfigurationKeySet(); 
DictConfigurationKey dictConfigurationKey; 
int i; 
```

```xpp
configKeySet.loadSystemSetup(); 
for (i=1; i<= configKeySet.cnt(); i++) 
{ 
    setPrefix('Disabled configurationkeys'); 
    if (!configKeySet.enabled( configKeySet.cnt2Id(i) )) 
    { 
        dictConfigurationKey =  
            new DictConfigurationKey(configKeySet.cnt2id(i)); 
        info (dictConfigurationKey.name()); 
    } 
}
```

## Method enabled

Determines whether to enable or disable the object.

```xpp
public boolean enabled(ConfigurationKeyId configurationKeyId, [boolean enable])
```

### Parameters - enabled

configurationKeyId  
The value to which to set the state of the configuration key; optional.

<!-- -->

enable  
The value to which to set the state of the configuration key; optional.

### Return Value - enabled

true if the object is enabled; otherwise, false.

### Remarks - enabled

The enabled property allows controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

### Examples - enabled

This example demonstrates the use of the ConfigurationKeySet.enabled method.

```xpp
static void testConfigKey(Args _args) 
{ 
    ConfigurationKeySet configKey = new ConfigurationKeySet(); 
```

```xpp
    configKey.loadSystemSetup(); 
```

```xpp
    // Set the enable value to false. 
    configKey.enabled(configurationkeynum(RouteApprove), false); 
    SysDictConfigurationKey::save(configKey.pack()); 
    SysSecurity::reload(true); 
    print isConfigurationkeyEnabled(configurationkeynum(RouteApprove)); 
```

```xpp
    // Set the enable value to true. 
    configKey.enabled(configurationkeynum(RouteApprove), true); 
    //Save the configuration key setup. 
    SysDictConfigurationKey::save(configKey.pack()); 
    SysSecurity::reload(true); 
```

```xpp
    print isConfigurationkeyEnabled(configurationkeynum(RouteApprove)); 
```

```xpp
    pause; 
}
```

## Method pack

Serializes the current instance of the ConfigurationKeySet class.

```xpp
public container pack()
```

### Return Value - pack

A container that contains the current instance of the ConfigurationKeySet class.

## Method touchedByUser

```xpp
public boolean touchedByUser(ConfigurationKeyId configurationKeyId)
```

### Parameters - touchedByUser

configurationKeyId  

### Return Value - touchedByUser

## Method new

Initializes a new instance of the Object class.

```xpp
public void new([container container])
```

### Parameters - new

container  

## Method loadSystemSetup

```xpp
public void loadSystemSetup()
```

