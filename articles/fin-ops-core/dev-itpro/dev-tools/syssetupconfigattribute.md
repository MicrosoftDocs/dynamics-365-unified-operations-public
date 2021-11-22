---
title: SysSetupConfigAttribute attribute
description: This topic describes how to use the SysSetupConfigAttribute attribute on classes that implement the SysSetup interface.
author: tonyafehr
ms.date: 10/26/2021
ms.topic: article
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: najaidee
ms.search.validFrom: 2021-10-26
ms.dyn365.ops.version: AX 10.0.0
---

# SysSetupConfigAttribute attribute

X++ classes that implement the `SysSetup` interface are processed as part of database synchronization. Custom X++ classes that implement `SysSetup` are also run as part of database synchronization.

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

> [!NOTE]
> If the X++ class does not have the **SysSetupConfigAttribute** attribute, then default values are applied. `ContinueOnError` is **true** and `Timeout` is **120** seconds.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
