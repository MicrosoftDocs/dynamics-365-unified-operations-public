---
# required metadata

title: Build Automation using Azure DevOps Hosted Agents
description: The topic explains how you can automate building X++ on any agents in Azure DevOps
author: jorisdg
manager: AnnBe
ms.date: 03/05/2020
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
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 26731
ms.assetid:
ms.search.region: Global
# ms.search.industry: 
ms.author: jorisde
ms.search.validFrom: 2020-03-05
ms.dyn365.ops.version: AX 7.0.0

---

# Build Automation using Azure DevOps Hosted Agents

[!include [banner](../includes/banner.md)]

Developers can automate building X++ code and creating deployable packages on any build agent running on Windows, including Azure DevOps hosted agents. This avoids the need for the setup, maintenance and cost of deploying build virtual machines. It also allows developers to reuse existing build agents setup to run other .NET build automation.

> [!NOTE]
> This feature is limited to compiling and packaging. There is no support for X++ unit testing (SysTest), database synchronization or other features requiring the runtime (Application Object Server) or its components.

## Preparations for building X++ code

### Build Projects

To standardize on .NET tools for building X++ on Azure DevOps, **MSBuild** with custom X++ targets are used. This requires the X++ source code repository to contain an X++ project for each package that needs to be built. Optionally, a solution file can be used to group the projects, including C# project dependencies, and provide explicit build ordering. If the repository doesn't already contain one, you can create a project from **Visual Studio**.

> [!NOTE]
> When using an existing X++ project (rnrproj), ensure it was created or opened and saved with Visual Studio tools on Platform Update 27 or higher.

> [!NOTE]
> A package can contain multiple models. However, a package always has to be built in its entirety. As a result, only one project for just one of the models is required to build the whole package. Additionally, the project does not need to, but can, contain any objects.

### NuGet Packages

To build X++ code, the basic developer tools such as the X++ compiler (xppc.exe) are required. Additionally, any referenced packages such as the Application Platform or Application Suite need to be available in a compiled format. To enable this process, the **Shared Asset Library** in **Dynamics Lifecycle Services** (LCS) provides NuGet packages needed to perform an X++ build.

The following packages can be downloaded from the **Shared Asset Library**:
- Microsoft.Dynamics.AX.Platform.CompilerPackage : This package contains the X++ compiler and related tools necessary to perform a build.
- Microsoft.Dynamics.AX.Platform.DevALM.BuildXpp : This package contains the compiled X++ code for the Application Platform and related modules, optimized for building.
- Microsoft.Dynamics.AX.Application.DevALM.BuildXpp : This package contains the compiled X++ code for the Application Suite and related modules, optimized for building.

We recommend downloading these packages from LCS and adding them to an Artifacts feed in the Azure DevOps account where the builds will run. For more information on creating an Artifacts feed and adding NuGet packages, review the Azure DevOps documentation [Getting started with NuGet packages in Azure DevOps](https://docs.microsoft.com/en-us/azure/devops/artifacts/get-started-nuget?view=azure-devops) to learn how to [Create a feed](https://docs.microsoft.com/en-us/azure/devops/artifacts/get-started-nuget?view=azure-devops#create-a-feed) and [publish a NuGet package](https://docs.microsoft.com/en-us/azure/devops/artifacts/get-started-nuget?view=azure-devops#create-and-publish-your-own-nuget-package).

> [!NOTE]
> Free Azure DevOps accounts have limited storage for Artifacts. Consider deleting old and unused versions to free up storage capacity. [Review the Azure DevOps documentation on Azure Artifacts](https://docs.microsoft.com/en-us/azure/devops/artifacts/start-using-azure-artifacts?view=azure-devops#billing-and-free-monthly-usage) for more information.

To identify which packages to use during the build and where to find them, a nuget.config and packages.config file has to be provided during the build. Creating these files and adding them to the source control repository is the recommended way. The files can be stored anywhere in source control, since the path to these files are explicit inputs for the NuGet command.

The nuget.config file provides NuGet with the source feed where the packages can be found. The packages.config file specifies the packages and their versions. To build against a newer version, updating the versions in packages.config is all that is required. Review the Azure DevOps documentation on [restoring NuGet packages in Azure Pipelines](https://docs.microsoft.com/en-us/azure/devops/pipelines/packages/nuget-restore?view=azure-devops) for more information and a sample nuget.config file.

The following example shows a packages.config file for the three main packages needed for a typical X++ build:

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
  <package id="Microsoft.Dynamics.AX.Platform.DevALM.BuildXpp" version="7.0.5644.16778" targetFramework="net40" />
  <package id="Microsoft.Dynamics.AX.Application.DevALM.BuildXpp" version="10.0.464.13" targetFramework="net40" />
  <package id="Microsoft.Dynamics.AX.Platform.CompilerPackage" version="7.0.5644.16778" targetFramework="net40" />
</packages>
```

## Creating the pipeline

Azure DevOps provides pipelines to automate builds. These come in two flavors: YML and Classic. YML pipelines are only available when using Git source control repositories. Team Foundation Version Control (TFVC) repositories can only be built using classic pipelines. Please review the documentation about [Aure Pipelines](https://docs.microsoft.com/en-us/azure/devops/pipelines/get-started/pipelines-get-started?view=azure-devops).

The topics below describe details of the needed steps in a pipeline to build X++ code. A sample pipeline that can be imported into an existing Azure DevOps project can be found on the [Dynamics365-Xpp-Samples-Tools](https://github.com/microsoft/Dynamics365-Xpp-Samples-Tools/tree/master/CI-CD/Pipeline-Samples) GitHub repository.

### Creating a basic build pipeline

A basic pipeline for compiling X++ requires only two steps:
1. Install the NuGet packages
2. Build the solution or projects

To simplify the usage of the extracted NuGet packages, consider using the **NuGet install** option, and specifying the **-ExcludeVersion** [NuGet command line option](https://docs.microsoft.com/en-us/nuget/reference/cli-reference/cli-ref-install#options) so the extracted package paths can be used in the build regardless of the version of the packages. Use the **NuGet Installer** task and set the **Installation type** to **Install**. Specify the path to the packages.config and nuget.config files created earlier.

The following example of NuGet arguments will avoid creating a subfolder for the package versions, and extract the NuGet packages into $(Pipeline.Workspace)\NuGets:

> -ExcludeVersion -OutputDirectory "$(Pipeline.Workspace)\NuGets"

To build X++ using **MSBuild**, several arguments need to be supplied. In the build solution step of a pipeline, these can be specified in the **MSBuild Arguments** field.

| Argument | Description |
| --- | --- | --- |
| /p:BuildTasksDirectory | The path to the extracted compiler tools NuGet, including the subfolders into the DevAlm folder. |
| /p:MetadataDirectory | The path to the X++ source code. |
| /p:FrameworkDirectory | The path to the extracted compiler tools Nuget. |
| /p:ReferenceFolder | A semi-colon separated list of paths containing binaries of X++ packages that are referenced and needed to compile, for example Application Platform and Application Suite. If the code that will be compiled has multiple packages that reference each other, the output directory should be included here as well. |
| /p:ReferencePath | A semi-colon separated list of paths containing any non-X++ binaries that are referenced and needed to compile. It's advised to include the extracted compiler tools location since it may contain needed references. |
| /p:OutputDirectory | The path where the folders and binaries will be created by the compiler. |

The following example of **MSBuild** arguments assumes the NuGets are installed to "$(Pipeline.Workspace)\NuGets", the X++ source code is in $(Build.SourcesDirectory)\Metadata, and the output of the compiler should go into $(Build.BinariesDirectory):

> /p:BuildTasksDirectory="$(Pipeline.Workspace)\NuGets\Microsoft.Dynamics.AX.Platform.CompilerPackage\DevAlm"
 /p:MetadataDirectory="$(Build.SourcesDirectory)\Metadata"
 /p:FrameworkDirectory="$(Pipeline.Workspace)\NuGets\Microsoft.Dynamics.AX.Platform.CompilerPackage"
 /p:ReferenceFolder="$(Pipeline.Workspace)\NuGets\Microsoft.Dynamics.AX.Platform.DevALM.BuildXpp\ref\net40;$(Pipeline.Workspace)\NuGets\Microsoft.Dynamics.AX.Application.DevALM.BuildXpp\ref\net40;$(Build.SourcesDirectory)\Metadata;$(Build.BinariesDirectory)"
 /p:ReferencePath="$(Pipeline.Workspace)\NuGets\Microsoft.Dynamics.AX.Platform.CompilerPackage" /p:OutputDirectory="$(Build.BinariesDirectory)"

In the pipeline samples, these commands are simplified using variables for NuGet package names and paths.

### Creating a full pipeline with packaging

For the pipeline to be completely useful, it should include a versioning and a packaging steps. To add these steps to a pipeline, the [Dynamics 365 Finance and Operations Tools](https://marketplace.visualstudio.com/items?itemName=Dyn365FinOps.dynamics365-finops-tools) extension for Azure DevOps needs to be enabled and installed in the Azure DevOps Account. Review the [Azure DevOps documentation](https://docs.microsoft.com/en-us/azure/devops/marketplace/install-extension?view=azure-devops&tabs=browser) on how to install an extension for an organization.

A full pipeline should at least consist of the following steps:
1. Install the NuGet packages
2. [Update the model versions](pipeline-model-version.md)
3. Build the solution or projects
4. Install NuGet 3.3.0 or earlier on the agent (required for the create deployable package step)
5. [Create the deployable package](pipeline-create-deployable-package.md)
6. Publish the deployable package artifact as the build output

To create the deployable package, NuGet has to be readily available on the build agent. The **NuGet tool installer** task in Azure DevOps needs to be run prior to the step that creates the package.

> [!NOTE]
> Due to semantic versioning features in NuGet versions 3.4 and later, please ensure the task installs version 3.3.0 or lower. Currently, deployable package generation does not support semantic versioning.

### Sample pipeline for X++ developers

A sample pipeline that can be imported into an existing Azure DevOps project can be found on the [Dynamics365-Xpp-Samples-Tools](https://github.com/microsoft/Dynamics365-Xpp-Samples-Tools/tree/master/CI-CD/Pipeline-Samples) GitHub repository.