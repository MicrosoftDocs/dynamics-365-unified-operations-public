---
title: Update the hosted Azure Pipeline for new NuGet packages
description: Learn about how to update an Azure pipeline to use new NuGet packages, including outlines on how to add pipeline variables and updating build solutionss steps.
author: josaw1
ms.author: josaw
ms.topic: article
ms.date: 03/04/2021
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2020-10-20
ms.dyn365.ops.version: AX 7.0.0
---

# Update the hosted Azure Pipeline for new NuGet packages

[!include [banner](../includes/banner.md)]

> [!NOTE]
> This article applies to pipelines that were set up for versions 10.0.17 or earlier. This does not apply to the legacy build pipeline that uses the build virtual machine.

Platform updates for [version 10.0.18](../get-started/whats-new-platform-updates-10-0-18.md) introduce a new NuGet package. The new package is a result of a package split for the Application Build Reference code. As a result, you have to make changes to pipelines created for 10.0.17 or earlier versions.

## Add the new package to packages.config list

The **packages.config** file used for your build already includes three packages:

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
    <package id="Microsoft.Dynamics.AX.Platform.DevALM.BuildXpp" version="7.0.5934.35741" targetFramework="net40" />
    <package id="Microsoft.Dynamics.AX.Application.DevALM.BuildXpp" version="10.0.761.10019" targetFramework="net40" />
    <package id="Microsoft.Dynamics.AX.Platform.CompilerPackage" version="7.0.5934.35741" targetFramework="net40" />
</packages>
```

You need to add a fourth package to the list, **Microsoft.Dynamics.AX.ApplicationSuite.DevALM.BuildXpp**. The resulting **packages.config** file should look like the following example, replacing the version number with the version number that your pipeline uses.

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
    <package id="Microsoft.Dynamics.AX.Platform.DevALM.BuildXpp" version="7.0.5968.16973" targetFramework="net40" />
    <package id="Microsoft.Dynamics.AX.Application.DevALM.BuildXpp" version="10.0.793.16" targetFramework="net40" />
    <package id="Microsoft.Dynamics.AX.ApplicationSuite.DevALM.BuildXpp" version="10.0.793.16" targetFramework="net40" />
    <package id="Microsoft.Dynamics.AX.Platform.CompilerPackage" version="7.0.5968.16973" targetFramework="net40" />
</packages>
```

## Add a pipeline variable

The pipeline uses variables to simplify and centralize parameters used in the pipeline tasks. There are already variables for each of the NuGet package names. To add a variable for the name of the new NuGet package, do the following:

1. On the **Variables** tab of the pipeline, select the **Add** link at the bottom of the list of variables.
2. In the **Name** column, type `AppSuitePackage`.
3. In the **Value** column, type `Microsoft.Dynamics.AX.ApplicationSuite.DevALM.BuildXpp`.

## Update the **Build solution** step

In the **Build solution** step in the pipeline, the path and names to all the NuGet packages are supplied as command-line parameters to **MSBuild**. To add the new NuGet package to the semi-colon separated list of **ReferenceFolder** paths, do either of the following:

- If you used the existing template without modifying it, the new **MSBuild Arguments** will be:

    `/p:BuildTasksDirectory="$(NugetsPath)\$(ToolsPackage)\DevAlm" /p:MetadataDirectory="$(MetadataPath)" /p:FrameworkDirectory="$(NuGetsPath)\$(ToolsPackage)" /p:ReferenceFolder="$(NuGetsPath)\$(PlatPackage)\ref\net40;$(NuGetsPath)\$(AppPackage)\ref\net40;$(MetadataPath);$(Build.BinariesDirectory);$(NuGetsPath)\$(AppSuitePackage)\ref\net40" /p:ReferencePath="$(NuGetsPath)\$(ToolsPackage)" /p:OutputDirectory="$(Build.BinariesDirectory)"`

- If you've modified the arguments list, find the **ReferenceFolder** property argument and add `$(NuGetsPath)\$(AppSuitePackage)\ref\net40` to the semi-colon separated list. Add a semi-colon to separate this new entry from other paths in the list.

## Use the updated templates on GitHub as an alternative

As an alternative to making these changes, or as a way to verify your changes, review the updated templates in the [Dynamics365-Xpp-Samples-Tools](https://github.com/microsoft/Dynamics365-Xpp-Samples-Tools/tree/master/CI-CD/Pipeline-Samples) GitHub repository.
