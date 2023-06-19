---
title: Build automation that uses Microsoft-hosted agents and Azure Pipelines
description: The article explains how you can automate the process of building X++ on any agents in Microsoft Azure DevOps.
author: gianugo
ms.date: 03/05/2020
ms.topic: article
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: gianura
ms.search.validFrom: 2020-03-05
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 
---

# Build automation that uses Microsoft-hosted agents and Azure Pipelines

[!include [banner](../includes/banner.md)]

You can automate the process of building X++ code and creating deployable packages on any build agent that run on Microsoft Windows. These agents include [Microsoft-hosted agents](/azure/devops/pipelines/agents/hosted). This approach helps you avoid the setup, maintenance, and cost of deploying build virtual machines (VMs). It also lets you reuse the existing setup of build agents to run other .NET build automation.

> [!NOTE]
> This feature is limited to compilation and packaging. There is no support for X++ unit testing (SysTest), database synchronization, or other features that require the runtime (Application Object Server \[AOS\]) or its components.

## Prerequisites for building X++ code

### Build projects

To use .NET tools for building X++ in Azure DevOps, the Microsoft Build Engine (MSBuild) and custom X++ targets are used. Your X++ source code repository must contain an X++ project for each package that you have to build. You can optionally use a solution file to group the projects, including C# project dependencies, and provide an explicit build order. If the repository doesn't already contain a project, you can create a project in Visual Studio.

> [!NOTE]
> When you use an existing X++ project (rnrproj), make sure that you created it, or opened and saved it, by using Visual Studio tools on Platform update 27 or later.
>
> Although a package can contain multiple models, it must always be built in its entirety. Therefore, only one project for just one of the models is required to build the whole package. Additionally, although the project doesn't have to contain any objects, it can contain them.

### NuGet packages

To build X++ code, the basic developer tools such as the X++ compiler (xppc.exe) are required. Additionally, any referenced packages, such as the Application Platform or Application Suite, must be available in a compiled format. To enable this process, the Shared asset library in Microsoft Dynamics Lifecycle Services (LCS) provides NuGet packages that are required to do an X++ build.

The following packages can be downloaded from the Shared asset library:

- **Microsoft.Dynamics.AX.Platform.CompilerPackage** – This package contains the X++ compiler and related tools that are required to do a build.
- **Microsoft.Dynamics.AX.Platform.DevALM.BuildXpp** – This package contains the compiled X++ code for the Application Platform and related modules. This code is optimized for building.
- **Microsoft.Dynamics.AX.Application.DevALM.BuildXpp** – This package contains the compiled X++ code for the Application and related modules. This code is optimized for building.

Starting from version 10.0.18, the Application Suite package has been split into two packages and there is an additional package to download from the Shared asset library.

- **Microsoft.Dynamics.AX.ApplicationSuite.DevALM.BuildXpp** - This package contains the compiled X++ code for the Application Suite module. This code is optimized for building.

Download these packages from LCS, and add them to an Azure Artifacts feed in the Azure DevOps organization where the builds will run. For more information about how to create an Azure Artifacts feed and add NuGet packages, see these topics:

- [Get started with NuGet packages in Azure DevOps Services and TFS](/azure/devops/artifacts/get-started-nuget)
- [Create a feed](/azure/devops/artifacts/get-started-nuget#create-a-feed)
- [Create and publish your own NuGet package](/azure/devops/artifacts/get-started-nuget#create-and-publish-your-own-nuget-package)

> [!NOTE]
> Free Azure DevOps organizations have limited storage for Azure Artifacts. Consider deleting old and unused versions to free up storage capacity. For more information, see [Sign up for Azure Artifacts](/azure/devops/artifacts/start-using-azure-artifacts#billing-and-free-monthly-usage).

To identify which packages should be used during the build, and where they can be found, you must provide a nuget.config file and a packages.config file during the build. We recommend that you create these files and add them to the source control repository. The files can be stored anywhere in source control, because the paths of these files are explicit inputs for the NuGet command.

The nuget.config file provides NuGet with the source feed where the packages can be found. The packages.config file specifies the packages and their versions. To build against a newer version, you just have to update the versions in the packages.config file. For more information, including a sample nuget.config file, see [Restore Package Management NuGet packages in Azure Pipelines](/azure/devops/pipelines/packages/nuget-restore).

The following example shows a **packages.config** file for the three main packages that are required for a typical X++ build. You must substitute the listed version with the actual versions of your NuGet packages.

+ For version 10.0.17 or earlier, use the following packages.config layout:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <packages>
        <package id="Microsoft.Dynamics.AX.Platform.DevALM.BuildXpp" version="7.0.5644.16778" targetFramework="net40" />
        <package id="Microsoft.Dynamics.AX.Application.DevALM.BuildXpp" version="10.0.464.13" targetFramework="net40" />
        <package id="Microsoft.Dynamics.AX.Platform.CompilerPackage" version="7.0.5644.16778" targetFramework="net40" />
    </packages>
    ```

+ For version 10.0.18 or later, use the following packages.config layout:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <packages>
        <package id="Microsoft.Dynamics.AX.Platform.DevALM.BuildXpp" version="7.0.5968.16973" targetFramework="net40" />
        <package id="Microsoft.Dynamics.AX.Application.DevALM.BuildXpp" version="10.0.793.16" targetFramework="net40" />
        <package id="Microsoft.Dynamics.AX.ApplicationSuite.DevALM.BuildXpp" version="10.0.793.16" targetFramework="net40" />
        <package id="Microsoft.Dynamics.AX.Platform.CompilerPackage" version="7.0.5968.16973" targetFramework="net40" />
    </packages>
    ```

## Creating the pipeline

Azure DevOps provides pipelines that can be used to automate builds. There are two types of pipelines: YML and Classic. YML pipelines are available only when you use Git source control repositories. Classic pipelines must be used to build Team Foundation Version Control (TFVC) repositories. For more information, see [Azure Pipelines](/azure/devops/pipelines/get-started/pipelines-get-started).

This section describes the steps that are required in a pipeline to build X++ code. In the [Dynamics365-Xpp-Samples-Tools](https://github.com/microsoft/Dynamics365-Xpp-Samples-Tools/tree/master/CI-CD/Pipeline-Samples) GitHub repository, you can find a sample pipeline that can be imported into an existing Azure DevOps project.

### Creating a basic build pipeline

A basic pipeline for compiling X++ requires only two steps:

1. Install the NuGet packages.
2. Build the solution or projects.

To simplify use of the extracted NuGet packages, consider using the **NuGet install** option and specifying the **-ExcludeVersion** [NuGet command-line option](/nuget/reference/cli-reference/cli-ref-install#options). In that way, the extracted package paths can be used in the build, regardless of the version of the packages. Use the **NuGet Installer** task, and set the **Installation type** field to **Install**. Finally, specify the path of the packages.config and nuget.config files that you created earlier.

The following example of NuGet arguments will prevent a subfolder from being created for the package versions and will extract the NuGet packages into **$(Pipeline.Workspace)\\NuGets**.

`-ExcludeVersion -OutputDirectory "$(Pipeline.Workspace)\NuGets"`

To build X++ by using MSBuild, you must supply several arguments. In the pipeline step that builds the solution, you can specify these arguments in the **MSBuild Arguments** field.

| Argument | Description |
| --- | --- |
| /p:BuildTasksDirectory | The path of the extracted Compiler Tools NuGet package, including the subfolders in the DevAlm folder. |
| /p:MetadataDirectory | The path of the X++ source code. |
| /p:FrameworkDirectory | The path of the extracted Compiler Tools NuGet package. |
| /p:ReferenceFolder | A semicolon-separated list of paths that contain binaries of X++ packages that are referenced and required for compilation (for example, Application Platform and Application Suite). If the code that will be compiled has multiple packages that reference each other, the output directory should also be included here. |
| /p:ReferencePath | A semicolon-separated list of paths that contain any non-X++ binaries that are referenced and required for compilation. You should include the location of the extracted Compiler Tools NuGet package, because it might contain required references. |
| /p:OutputDirectory | The path where the compiler will create folders and binaries. |

The following example of MSBuild arguments assumes that the NuGet packages are installed in **$(Pipeline.Workspace)\\NuGets**, the X++ source code is in **$(Build.SourcesDirectory)\\Metadata**, and the output of the compiler should go in **$(Build.BinariesDirectory)**.

+ For version 10.0.17 or earlier, use the following arguments:

    ```dos
    /p:BuildTasksDirectory="$(Pipeline.Workspace)\NuGets\Microsoft.Dynamics.AX.Platform.CompilerPackage\DevAlm"
    /p:MetadataDirectory="$(Build.SourcesDirectory)\Metadata"
    /p:FrameworkDirectory="$(Pipeline.Workspace)\NuGets\Microsoft.Dynamics.AX.Platform.CompilerPackage"
    /p:ReferenceFolder="$(Pipeline.Workspace)\NuGets\Microsoft.Dynamics.AX.Platform.DevALM.BuildXpp\ref\net40;$(Pipeline.Workspace)\NuGets\Microsoft.Dynamics.AX.Application.DevALM.BuildXpp\ref\net40;$(Build.SourcesDirectory)\Metadata;$(Build.BinariesDirectory)"
    /p:ReferencePath="$(Pipeline.Workspace)\NuGets\Microsoft.Dynamics.AX.Platform.CompilerPackage" /p:OutputDirectory="$(Build.BinariesDirectory)"
    ```
    
+ For version 10.0.18 or newer, use the following arguments:

    ```dos
    /p:BuildTasksDirectory="$(Pipeline.Workspace)\NuGets\Microsoft.Dynamics.AX.Platform.CompilerPackage\DevAlm"
    /p:MetadataDirectory="$(Build.SourcesDirectory)\Metadata"
    /p:FrameworkDirectory="$(Pipeline.Workspace)\NuGets\Microsoft.Dynamics.AX.Platform.CompilerPackage"
    /p:ReferenceFolder="$(Pipeline.Workspace)\NuGets\Microsoft.Dynamics.AX.Platform.DevALM.BuildXpp\ref\net40;$(Pipeline.Workspace)\NuGets\Microsoft.Dynamics.AX.Application.DevALM.BuildXpp\ref\net40;$(Pipeline.Workspace)\NuGets\Microsoft.Dynamics.AX.ApplicationSuite.DevALM.BuildXpp\ref\net40;$(Build.SourcesDirectory)\Metadata;$(Build.BinariesDirectory)"
    /p:ReferencePath="$(Pipeline.Workspace)\NuGets\Microsoft.Dynamics.AX.Platform.CompilerPackage" /p:OutputDirectory="$(Build.BinariesDirectory)"
    ```

In the pipeline samples, variables for NuGet package names and paths are used to simplify these commands.

### Creating a full pipeline that includes packaging

To be useful, the pipeline should include a versioning step and a packaging step. Before you can add these steps to a pipeline, the [Dynamics 365 finance and operations Tools](https://marketplace.visualstudio.com/items?itemName=Dyn365FinOps.dynamics365-finops-tools) extension for Azure DevOps must be enabled and installed in the Azure DevOps organization. For information about how to install an extension for an organization, see the [Azure DevOps documentation](/azure/devops/marketplace/install-extension).

A full pipeline should consist of at least the following steps:

1. Install the NuGet packages.
2. [Update the model versions](pipeline-model-version.md).
3. Build the solution or projects.
4. Install NuGet 3.3.0 or earlier on the agent. (This step is required for the step that creates the deployable package.)
5. [Create the deployable package](pipeline-create-deployable-package.md).
6. Publish the deployable package artifact as the build output.

For the deployable package to be created, NuGet must be readily available on the build agent. Therefore, the **NuGet tool installer** task in Azure DevOps must be run before the step that creates the package.

> [!NOTE]
> If your source code repository includes binary packages from third parties like ISVs, you have to explicitly add those to the packaging step. For more information, see [Create deployable packages in Azure Pipelines](pipeline-create-deployable-package.md).

> [!NOTE]
> Because of semantic versioning features in NuGet version 3.4 and later, make sure that the task installs version 3.3.0 or earlier. Currently, deployable package generation doesn't support semantic versioning.

### Sample pipeline for X++ developers

In the [Dynamics365-Xpp-Samples-Tools](https://github.com/microsoft/Dynamics365-Xpp-Samples-Tools/tree/master/CI-CD/Pipeline-Samples) GitHub repository, you can find a sample pipeline that can be imported into an existing Azure DevOps project.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]


