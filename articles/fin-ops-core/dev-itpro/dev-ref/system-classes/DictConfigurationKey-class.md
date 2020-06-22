---
title: DictConfigurationKey class
description: This topic describes the DictConfigurationKey class.
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

# Class DictConfigurationKey

[!include [banner](../../includes/banner.md)]

```xpp
class DictConfigurationKey extends Object
```

The DictConfigurationKey class provides information about a configuration key.

## Remarks

For an example that uses the DictConfigurationKey class, see the new method.

## Examples

## Methods

| Method                                                                     | Description                                                               |
|----------------------------------------------------------------------------|---------------------------------------------------------------------------|
| public boolean enabled()                                                   | Returns a value that indicates whether the configuration key is enabled.  |
| public ConfigurationKeyId id()                                             | Returns the ID of the configuration key.                                  |
| public str label()                                                         | Returns the label for a configuration key.                                |
| public str labelId()                                                       |                                                                           |
| public LicenseCodeId licenseCode()                                         | Returns the license code ID for the configuration key.                    |
| public str name()                                                          | Returns the name of the configuration key.                                |
| public ConfigurationKeyId parentConfigurationKeyId()                       | Returns the ID of the parent configuration key for the configuration key. |
| ::public static boolean enabledById(ConfigurationKeyId configurationKeyId) |                                                                           |
| public boolean permanentlyDisabled()                                       |                                                                           |
| public void new(ConfigurationKeyId configurationKeyId)                     | Initializes a new instance of the Object class.                           |

## Method enabled

Returns a value that indicates whether the configuration key is enabled.

```xpp
public boolean enabled()
```

### Return Value - enabled

true if the configuration key is enabled; otherwise, false.

### Remarks - enabled

For an example that uses this method, see the new method.

## Method id

Returns the ID of the configuration key.

```xpp
public ConfigurationKeyId id()
```

### Return Value - id

The ID of the configuration key.

## Method label

Returns the label for a configuration key.

```xpp
public str label()
```

### Return Value - label

The label for the configuration key; an empty string if the configuration key does not have a label value.

## Method labelId

```xpp
public str labelId()
```

### Return Value - labelId

## Method licenseCode

Returns the license code ID for the configuration key.

```xpp
public LicenseCodeId licenseCode()
```

### Return Value - licenseCode

The license code ID for the configuration key; 0 (zero) if the configuration key has no license code.

## Method name

Returns the name of the configuration key.

```xpp
public str name()
```

### Return Value - name

The name of the configuration key.

### Remarks - name

For an example that uses this method, see the new method.

## Method parentConfigurationKeyId

Returns the ID of the parent configuration key for the configuration key.

```xpp
public ConfigurationKeyId parentConfigurationKeyId()
```

### Return Value - parentConfigurationKeyId

The ID of the parent configuration key; 0 (zero) if the configuration key has no parent configuration key.

## Method enabledById

```xpp
public static boolean enabledById(ConfigurationKeyId configurationKeyId)
```

### Parameters - enabledById

configurationKeyId  

### Return Value - enabledById

## Method permanentlyDisabled

```xpp
public boolean permanentlyDisabled()
```

### Return Value - permanentlyDisabled

## Method new

Initializes a new instance of the Object class.

```xpp
public void new(ConfigurationKeyId configurationKeyId)
```

### Parameters - new

configurationKeyId  
The ID of the configuration key that is used to create the instance of the DictConfigurationKey class.

### Examples - new

The following example shows how to create a new instance of the DictConfigurationKey class during an enumeration of configuration keys.

```xpp
ConfigurationKeySet configKeySet; 
DictConfigurationKey dictConfigKey; 
str strOutput; 
int i; 
configKeySet = new ConfigurationKeySet(); 
configKeySet.loadSystemSetup(); 
// Output the configuration key names and their enable state. 
for (i=1; i <= configKeySet.cnt(); i++) 
{ 
    dictConfigKey = new DictConfigurationKey(configKeySet.cnt2Id(i)); 
    strOutput = dictConfigKey.enabled() ? "enabled" : "disabled"; 
    strOutput += " " + dictConfigKey.name(); 
    print strOutput; 
}
```

