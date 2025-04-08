---
title: SysSetupConfigAttribute attribute
description: Learn about how to use the SysSetupConfigAttribute attribute on classes that implement the SysSetup interface.
author: josaw1
ms.author: najaidee
ms.topic: article
ms.date: 06/03/2022
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2021-10-26
ms.dyn365.ops.version: AX 10.0.0
---

# SysSetupConfigAttribute attribute

X++ classes that implement the `SysSetup` interface are processed as part of database synchronization. Custom X++ classes that implement `SysSetup` are also run as part of database synchronization.

Attributes provide a powerful way to associate metadata, or declarative information, with code such as assemblies, types, methods, and properties. After an attribute is associated with a program entity, it can be queried at runtime by using reflection.

This article describes how to use the new `SysSetupConfigAttribute` attribute that the platform updates for [version 10.0.23 of finance and operations apps](../get-started/whats-new-platform-updates-10-0-23.md) introduce for X++ classes that implement the `SysSetup` interface.

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


## SysSetupScript: Asynchronous implementation

To execute the SysSetup scripts in asynchronous mode, the scripts need to be run as a batch job. This enhances performance and removes unnecessary dependencies by ensuring the scripts run parallel and independent of one another. To achieve this, use the SysSetupWrapper and the SysSetupAsync class that you can extend and consume. This allows DbSync to execute, as needed.

## Considerations when enabling asynchronous mode
When enabling asynchronous mode, consider the following: 

 - This mode does not have any timeouts, but instead operates in the boundaries of batch jobs scoped as high priority jobs.
 - When the class implements the asynchronous mode, not all of the SyssetupTable attributes will be considered. Currently, all scripts are independently functional.
 - If you are writing a new script as asynchronous, ensure that you use smaller workloads that can recover from a point of pause/failure because these batch jobs can be withheld and resumed in the future.
 - The loaddata() does not run inside the ttsbegin; ..., ttscommit; block, so this should be handled in your implementation.

```xpp
class DemoClass extends SysSetupAsync implements SysSetup
{
    // Class code here.
}
```
## Versioning SysSetup classes

SysSetup classes can be versioned and run only once, not on every DBSync execution. For example, whenever there is a change in the version, DBSync runs the X++ class.

As of version 10.0.27, the versioning feature is available for SysSetup classes.

### How does versioning work for SysSetup classes?

A new `_version` parameter of the **Version** type is added to the `SysSetupConfigAttribute` attribute. It accepts values in the format \[Major\].\[Minor\], such as **1.0**, **2.1**, **4.5**, and **10.4**.

DBSync reads the value of the `_version` parameter, and whenever there is a change in the version, the scripts are run. This parameter is optional. The default value is **1.0**. Therefore, if the X++ classes that are onboarded to SysSetup don't have the `_version` parameter, the X++ class will have a default version value of **1.0** when it runs.

> [!NOTE]
> A versioned class (default) will successfully run only once, unless the version number is updated again. For example, a script that has a version value of **1.0** won't be rerun on every DBSync request.

The version value **0.0** is dedicated to the execution of X++ classes on every DBSync execution. Therefore, to run X++ classes on every DBSync operation, you must set the `_version` parameter for the `SysSetupConfigAttribute` attribute to **0.0**.

### Onboarding the X++ class to SysSetup

SysSetup classes should start to use the `_version` parameter in the `SysSetupConfigAttribute` attribute. Otherwise, the default behavior is used when the X++ class runs. In other words, the version value is **1.0**, and the class runs only once per version.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

