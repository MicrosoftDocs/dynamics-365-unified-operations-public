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

X++ classes that implement the `SysSetup` interface are processed during database synchronization. Custom X++ classes that implement `SysSetup` are also run as part of database synchronization.

Attributes provide a powerful way to associate metadata, or declarative information, with code such as assemblies, types, methods, and properties. After an attribute is associated with a program entity, it can be queried at runtime by using reflection.

This topic describes how to use the new `SysSetupConfigAttribute` attribute that the platform updates for [version 10.0.23 of Finance and Operations apps](../get-started/whats-new-platform-updates-10-0-23.md) introduce for X++ classes that implement the `SysSetup` interface.

## Usage

The `SysSetupConfigAttribute` attribute must be added for all X++ classes that implement the `SysSetup` interface. It accepts two parameters:

+ **ContinueOnError** – This parameter is of the `bool` type. If execution of the X++ class fails during synchronization, database synchronization will either fail or continue with the next steps, depending on the value of this parameter (`true` or `false`).

    + **true** – Database synchronization will continue with the next steps.
    + **false** – The overall database synchronization operation will fail and can't be resumed until the underlying issue is fixed.

+ **Timeout** – This parameter is of the `int` type, and the range of values is from 1 to 600 seconds. It defines the time range that the database synchronization operation will run the `SysSetup` class during.

In the following code example, the `ContinueOnError` parameter is set to `true`, and the `Timeout` parameter is set to `300`.

```xpp
[SysSetupConfigAttribute(true, 300)]
class DemoClass implements SysSetup
{
    // Class code here.
}
```

## Override attribute parameters

You can override the `SysSetupConfigAttribute` attribute by copying the SysSetuScripts.xml file to the Application Object Server (AOS) installation directory. Typically, the file is found in the AOSService\\PackagesLocalDirectory\\bin folder.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Scripts>
    <Script Name="<Class1>" ContinueOnError="true" Timeout="600"/>
    <Script Name="<Class2>" ContinueOnError="false" Timeout="300"/>
</Scripts>
```

## Review the synchronization status

You can download the log file from Microsoft Dynamics Lifecycle Services (LCS). In the log file, you can find each X++ class that was processed, together with the attribute parameters. The following example shows the log output.

```dos
09/21/2021 17:42:07: SysSetupInstaller: Running Script: NumberSequenceModuleSetup with Timeout 600 seconds.
09/21/2021 17:42:09: SysSetupInstaller: Script: NumberSequenceModuleSetup, Completed Successfully. Time elapsed: 0:00:00:01.5189544
```

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
