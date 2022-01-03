---
title: SysSetupConfigAttribute attribute
description: This topic describes how to use the SysSetupConfigAttribute attribute on classes that implement the SysSetup interface.
author: tonyafehr
ms.date: 01/03/2022
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


# SysSetupScript: Asynchronous implementation

To execute the SysSetup scripts in asynchronous mode, which executes the script as a batch job. This would enhance the performance and remove unnecessary dependencies by making sure these can run parallelly and independent of one another. To achieve this, we have a SysSetupWrapper. SysSetupAsync class that you could extend and consume. This would allow DbSync to recognize and execute, as necessary.

## Points to be considered when enabling as asynchronous mode

 - They don’t have any timeouts, but they operate in the boundaries of batch jobs scope as high priority jobs.
 - There is no further meaning to SysssetupTable Attribute once they are scheduled as batch jobs. However, as far as we have seen all scripts are independently functional today.
 - If you are writing a new script as asynchronous, please ensure to operate on smaller workloads which can recover from point of pause / failure as batch jobs can be withheld and resumed in future.
 - The loaddata() is not running inside this ttsbegin; ..., ttscommit; block. so this should be handled in your implementation.

```xpp
class DemoClass extends SysSetupAsync implements SysSetup
{
    // Class code here.
}
```

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
