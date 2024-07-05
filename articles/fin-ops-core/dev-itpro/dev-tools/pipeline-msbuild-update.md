---
title: Update a legacy pipeline in Azure Pipelines
description: Learn about how to update a legacy pipeline in Azure Pipelines to use a newer version of Visual Studio, including a table that outlines property values for task names.
author: josaw1
ms.author: josaw
ms.topic: article
ms.date: 09/23/2020
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2020-10-20
ms.dyn365.ops.version: AX 7.0.0
---

# Update a legacy pipeline in Azure Pipelines

[!include [banner](../includes/banner.md)]

> [!NOTE]
> This documentation does not apply to the [new build pipeline](hosted-build-automation.md), even if you run it on the build virtual machine.

An **Azure Pipelines** pipeline explicitly specifies the versions of **Visual Studio** tools such as **MSBuild** and **VS Test**. To continue supporting newer versions of these products, new virtual machines will be deployed with newer versions of **Visual Studio** pre-installed. Any existing pipelines need to be manually updated to use the newer version.

## Determine if your pipeline needs to be updated

Build and development virtual machines deployed with version 10.0.13 through version 10.0.20 include **Visual Studio 2017**. Those deployed with version 10.0.21 and later include **Visual Studio 2019**. Support for [Visual Studio 2015 was deprecated](../get-started/removed-deprecated-features-platform-updates.md#platform-updates-for-version-10011-of-finance-and-operations-apps) in April 2021 and support for [Visual Studio 2017 was deprecated](/lifecycle/products/visual-studio-2017) in April 2022. If your build virtual machine does not include **Visual Studio 2019** you must plan to deploy a new build virtual machine with version 10.0.21 or later, or consider using the new [hosted build pipeline](hosted-build-automation.md).

If your build virtual machine has Visual Studio 2019 installed, you can use the newer versions of **MSBuild** and **VS Test**. If your pipeline was created by a virtual machine deployment prior to version 10.0.21, you will have to manually update the pipeline.

Finally, you can check your build pipeline on the **Build the solution** step. The **MSBuild Version** property indicates the version of **Visual Studio** in use.

| MSBuild version | Visual Studio version |
|---|---|
| MSBuild 14.0 | Visual Studio 2015 |
| MSBuild 15.0 | Visual Studio 2017 |
| MSBuild 16.0 | Visual Studio 2019 |

## Updating the Azure Pipelines pipeline

> [!NOTE]
> To update an **Azure Pipelines** pipeline to use **Visual Studio 2019**, ensure your build virtual machine has been updated to version 10.0.21 or later.

The following four properties, in three tasks in the pipeline, need to be updated.

| Task name | Task property | Old value | New value|
| --- | --- | --- | ---|
| Build the solution | MSBuild Version | MSBuild 14.0/15.0 | MSBuild 16.0 |
| Database Sync | MSBuild Version | MSBuild 14.0/15.0 | MSBuild 16.0 |
| Execute Tests | Test platform version | Visual Studio 2015/2017 | Visual Studio 2019 |
| Execute Tests | Other console options | `/Platform:X64 /InIsolation /UseVsixExtensions:true` | `/Platform:X64 /InIsolation /TestAdapterPath:"$(VsixExtensionFolder)"` |



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
