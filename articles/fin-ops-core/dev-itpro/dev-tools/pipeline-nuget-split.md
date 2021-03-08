---
# required metadata

title: Update the hosted Azure Pipeline for new NuGets
description: This topic explains how to update an Azure pipeline to use new NuGet packages.
author: jorisdg
manager: AnnBe
ms.date: 03/04/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
# ms.tgt_pltfrm: 
ms.custom:
ms.search.region: Global
# ms.search.industry: 
ms.author: jorisde
ms.search.validFrom: 2020-10-20
ms.dyn365.ops.version: AX 7.0.0

---

# Update the hosted Azure Pipeline for new NuGets

[!include [banner](../includes/banner.md)]

> [!NOTE]
> This documentation does not apply to the legay build pipeline that uses the build virtual machine.

> This documentation applies to pipelines that were set up for versions 10.0.17 or earlier, updating to 10.0.18 or above.

Version 10.0.18 (PU42) introduces a new NuGet package as a result of a package split for the Application Build Reference code. As a result, some changes have to be made to a pipeline created for 10.0.17 or earlier versions.

## Add the new package to packages.config list

The packages.config file used for your build will include three packages already:

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
    <package id="Microsoft.Dynamics.AX.Platform.DevALM.BuildXpp" version="7.0.5934.35741" targetFramework="net40" />
    <package id="Microsoft.Dynamics.AX.Application.DevALM.BuildXpp" version="10.0.761.10019" targetFramework="net40" />
    <package id="Microsoft.Dynamics.AX.Platform.CompilerPackage" version="7.0.5934.35741" targetFramework="net40" />
</packages>
```

A fourth package, **Microsoft.Dynamics.AX.ApplicationSuite.DevALM.BuildXpp** needs to be added to the list. The resulting packages.config file should look like the example below, substituting the version number with the version number in use by your pipeline.

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

The pipeline uses variables to simplify and centralize parameters used in the pipeline tasks. There are already variables for each of the NuGet package names. Add a variable for the name of the new NuGet package.

- On the **Variables** tab of the pipeline, click the **Add** link at the bottom of the list of variables.
- In the name column, type `AppSuitePackage`
- In the value column, type `Microsoft.Dynamics.AX.ApplicationSuite.DevALM.BuildXpp`

## Update the **Build solution** step

The **Build solution** step in the pipeline the path and names to all the NuGet packages are supplied as command line parameters to **MSBuild**. Add the new NuGet package to the semi-colon separated list of **ReferenceFolder** paths.

- If you used the existing template without modifying, the new **MSBuild Arguments** will be:

    `/p:BuildTasksDirectory="$(NugetsPath)\$(ToolsPackage)\DevAlm" /p:MetadataDirectory="$(MetadataPath)" /p:FrameworkDirectory="$(NuGetsPath)\$(ToolsPackage)" /p:ReferenceFolder="$(NuGetsPath)\$(PlatPackage)\ref\net40;$(NuGetsPath)\$(AppPackage)\ref\net40;$(MetadataPath);$(Build.BinariesDirectory);$(NuGetsPath)\$(AppSuitePackage)\ref\net40" /p:ReferencePath="$(NuGetsPath)\$(ToolsPackage)" /p:OutputDirectory="$(Build.BinariesDirectory)"`

- If you've modified the arguments list, find the **ReferenceFolder** property argument and add `$(NuGetsPath)\$(AppSuitePackage)\ref\net40` to the semi-colon separated list. Add a semi-colon to separate this new entry from other paths in the list.

## Replace your existing template entirely

As an alternative to making these changes, or as a way to verify your changes, please review the updated templates in the [Dynamics365-Xpp-Samples-Tools](https://github.com/microsoft/Dynamics365-Xpp-Samples-Tools/tree/master/CI-CD/Pipeline-Samples) GitHub repository.