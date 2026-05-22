---
title: SysSetupConfigAttribute attribute
description: Learn about how to use the SysSetupConfigAttribute attribute on classes that implement the SysSetup interface.
author: josaw1
ms.author: najaidee
ms.topic: article
ms.date: 03/30/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2021-10-26
ms.dyn365.ops.version: AX 10.0.0
---

# SysSetupConfigAttribute attribute

The system processes X++ classes that implement the `SysSetup` interface as part of database synchronization. Custom X++ classes that implement `SysSetup` also run as part of database synchronization.

Attributes provide a way to associate metadata, or declarative information, with code such as assemblies, types, methods, and properties. After you associate an attribute with a program entity, you can query it at runtime by using reflection.

This article describes how to use the new `SysSetupConfigAttribute` attribute that the platform updates for [version 10.0.23 of finance and operations apps](../get-started/whats-new-platform-updates-10-0-23.md) introduce for X++ classes that implement the `SysSetup` interface.

## Usage

Add the `SysSetupConfigAttribute` attribute to all X++ classes that implement the `SysSetup` interface. It accepts two parameters:

- **ContinueOnError** – This parameter is a `bool` type. If execution of the X++ class fails during synchronization, database synchronization either fails or continues with the next steps, depending on the value of this parameter (`true` or `false`).

  - **true** – Database synchronization continues with the next steps.
  - **false** – The overall database synchronization operation fails and can't resume until the underlying issue is fixed.

- **Timeout** – This parameter is an `int` type, and the range of values is from 1 to 600 seconds. It defines the time range that the database synchronization operation runs the `SysSetup` class during.

In the following code example, the `ContinueOnError` parameter is set to `true`, and the `Timeout` parameter is set to `300`.

```xpp
[SysSetupConfigAttribute(true, 300)]
class DemoClass implements SysSetup
{
    // Class code here.
}
```

> [!NOTE]
> If the X++ class doesn't have the **SysSetupConfigAttribute** attribute, default values apply. `ContinueOnError` is **true** and `Timeout` is **120** seconds.

## SysSetupScript: Asynchronous implementation

To execute the SysSetup scripts in asynchronous mode, run the scripts as a batch job. This approach enhances performance and removes unnecessary dependencies by ensuring the scripts run parallel and independent of one another. To achieve this approach, use the SysSetupWrapper and the SysSetupAsync classes that you can extend and consume. This approach allows DbSync to execute, as needed.

## Considerations when enabling asynchronous mode

When you enable asynchronous mode, consider the following points:

- This mode doesn't use any timeouts. Instead, it operates within the boundaries of batch jobs scoped as high priority jobs.
- When the class implements the asynchronous mode, the system doesn't consider all of the `SyssetupTable` attributes. Currently, all scripts are independently functional.
- If you're writing a new script as asynchronous, use smaller workloads that can recover from a point of pause or failure because these batch jobs can be withheld and resumed in the future.
- The `loaddata()` method doesn't run inside the `ttsbegin; ...`, `ttscommit;` block, so you should handle this behavior in your implementation.

```xpp
class DemoClass extends SysSetupAsync implements SysSetup
{
    // Class code here.
}
```

## Versioning SysSetup classes

You can version SysSetup classes so that they run only once, not on every DBSync execution. For example, DBSync runs the X++ class whenever there's a change in the version.

As of version 10.0.27, the versioning feature is available for SysSetup classes.

### How does versioning work for SysSetup classes?

The system adds a new `_version` parameter of the **Version** type to the `SysSetupConfigAttribute` attribute. It accepts values in the format \[Major\].\[Minor\], such as **1.0**, **2.1**, **4.5**, and **10.4**.

DBSync reads the value of the `_version` parameter, and whenever there's a change in the version, it runs the scripts. This parameter is optional. The default value is **1.0**. Therefore, if the X++ classes that you onboard to SysSetup don't have the `_version` parameter, the X++ class has a default version value of **1.0** when it runs.

> [!NOTE]
> A versioned class (default) runs successfully only once, unless you update the version number. For example, a script that has a version value of **1.0** isn't rerun on every DBSync request.

The version value **0.0** is dedicated to the execution of X++ classes on every DBSync execution. Therefore, to run X++ classes on every DBSync operation, set the `_version` parameter for the `SysSetupConfigAttribute` attribute to **0.0**.

### Onboard the X++ class to SysSetup

SysSetup classes should use the `_version` parameter in the `SysSetupConfigAttribute` attribute. Otherwise, the default behavior applies when the X++ class runs. In other words, the version value is **1.0**, and the class runs only once per version.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
