---
title: SysSetupConfigAttribute attribute
description: This topic describes how to use the SysSetupConfigAttribute attribute on classes that implement the SysSetup interface. 
author: robinarh
ms.date: 10/26/2021
ms.topic: article
audience: Developer
ms.reviewer: rhaertle
ms.search.region: Global
ms.author: najaidee
ms.search.validFrom: 2021-10-26
ms.dyn365.ops.version: AX 10.0.0
---

# SysSetupConfigAttribute attribute

X++ classes that implement the `SysSetup` interface are processed during database synchronization. Custom X++ classes that implement `SysSetup` are also executed as a part of database synchronization. A new attribute is introduced in the platform updates for [version 10.0.23 of Finance and Operations apps](../get-started/whats-new-platform-updates-10-0-23.md).

Attributes provide a powerful method of associating metadata, or declarative information, with code, for example, assemblies, types, methods, and properties. After an attribute is associated with a program entity, the attribute can be queried at run time by using reflection.

## Usage

The `SysSetupConfigAttribute` attribute must be added for all the X++ classes that implement the `SysSetup` interface. This attribute accepts 2 parameters:

+ `ContinueOnError` – This parameter is of type `bool` (`true` or `false`). If the class fails during synchronization then based on this parameter value, the database synchronization will either fail or continue with the successive steps.

    + If the parameter is set to `true`, database synchronization will continue with the next steps upon failure of the X++ class execution.  
    + If the parameter is set to `false`, the overall database synchronization operation will fail and the underlying issue must be fixed before the database synchronization operation is resumed.

+ Timeout – This parameter is of type `int`, and the range is from 1 to 600 seconds. The database synchronization operation will execute the `SysSetup` class within the time range provided.  

In the following code example, `ContinueOnError` is set to `true` and `Timeout` is set to 300.

```xpp
[SysSetupConfigAttribute(true, 300)]
class DemoClass implements SysSetup
{
    // Class code here.
}
```

## Override attribute parameters

The `SysSetupConfigAttribute` attribute of can be overridden by copying the `SysSetuScripts.xml` file to the AOS install directory. The file is typically found in the `AOSService\PackagesLocalDirectory\bin` folder.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Scripts>
    <Script Name="<Class1>" ContinueOnError="true" Timeout="600"/>
    <Script Name="<Class2>" ContinueOnError="false" Timeout="300"/>
</Scripts>
```

## Synchronization status

You can download the log file from Lifecycle Services. You can find each X++ class processed along with the attribute parameters. The following example shows the log output.

```dos
09/21/2021 17:42:07: SysSetupInstaller: Running Script: NumberSequenceModuleSetup with Timeout 600 seconds.
09/21/2021 17:42:09: SysSetupInstaller: Script: NumberSequenceModuleSetup, Completed Successfully. Time elapsed: 0:00:00:01.5189544
```

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]