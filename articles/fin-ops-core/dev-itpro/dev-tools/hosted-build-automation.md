---
title: Build automation that uses Microsoft-hosted agents and Azure Pipelines
description: Learn about how you can automate the process of building X++ on any agents in Microsoft Azure DevOps, including prerequisites.
author: dedmond83
ms.author: josaw
ms.topic: article
ms.date: 11/22/2024
ms.reviewer: twheeloc
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2020-03-05
ms.dyn365.ops.version: AX 7.0.0
---

# Build automation that uses Microsoft-hosted agents and Azure Pipelines

[!include [banner](../includes/banner.md)]

In Microsoft Azure DevOps, you can automate the process of building X++ code and creating deployable packages on any Windows build agent. These agents include [Microsoft-hosted agents](/azure/devops/pipelines/agents/hosted). This approach helps you avoid the setup, maintenance, and cost of deploying build virtual machines (VMs). It also lets you reuse the existing setup of build agents to run other .NET build automation.

> [!NOTE]
> This feature is limited to compilation and packaging. There is no support for X++ unit testing (SysTest), database synchronization, or other features that require the runtime (Application Object Server \[AOS\]) or its components.

## Prerequisites for building X++ code

### Build projects

To use .NET tools to build X++ in Azure DevOps, the Microsoft Build Engine (MSBuild) and custom X++ targets are used. Your X++ source code repository must contain an X++ project for each package that you have to build. 

You can optionally use a solution file to group the projects, including C# project dependencies, and provide an explicit build order. If the repository doesn't already contain a project, you can create a project in Visual Studio.

Ensure that a descriptor folder exists and checked in the descriptor file for each model to your model metadata folder in Azure DevOps.

> [!NOTE]
> When you use an existing X++ project (rnrproj), make sure that you used Visual Studio tools to create it, or to open and save it.
>
> Although a package can contain multiple models, it must always be built in its entirety. Therefore, only one project for just one of the models is required to build the whole package. Additionally, although the project doesn't have to contain any objects, it can contain them.

### NuGet packages

NuGet packages are used for the Azure DevOps build pipelines. They include the tools that are required to build X++ code, such as the X++ compiler (xppc.exe), the Application Platform and Application Suite modules, and other modules. 

The following NuGet packages are available in the Shared asset library in Microsoft Dynamics 365 Lifecycle Services:

- **Microsoft.Dynamics.AX.Platform.CompilerPackage** 

    - This package contains the X++ compiler and related tools that are required to do a build.
    - The name of the package is typically **PUXX/10.X.XX – Compiler Tools**.

- **Microsoft.Dynamics.AX.Platform.DevALM.BuildXpp** 

    - This package contains the compiled X++ code for the Application Platform module and related modules. This code is optimized for building.
    - The name of the package is typically **PUXX/10.X.XX – Platform Build Reference**.

- **Microsoft.Dynamics.AX.Application1.DevALM.BuildXpp**

    - This package contains the compiled X++ code for the Application module and related modules. This code is optimized for building.
    - The name of the package is typically **PUXX/10.X.XX – Application 1 Build Reference**.

- **Microsoft.Dynamics.AX.Application2.DevALM.BuildXpp** 

    - This package contains the compiled X++ code for the Application module and related modules. This code is optimized for building.
    - The name of the package is typically **PUXX/10.X.XX – Application 2 Build Reference**.

- **Microsoft.Dynamics.AX.ApplicationSuite.DevALM.BuildXpp**

    - This package contains the compiled X++ code for the Application Suite module. This code is optimized for building.
    - The name of the package is typically **PUXX/10.X.XX – Application Suite Build Reference**.

> [!NOTE]
> Lifecycle Services contains six NuGet packages per release. The package that is named **PUXX/10.X.XX – application build reference** is the combined version of **PUXX/10.X.XX – Application 1 Build Reference** and **PUXX/10.X.XX – Application 2 Build Reference**. It isn't needed. The split packages are smaller and can be used instead of the single package.

> [!IMPORTANT]
> The NuGet packages contain version details about the platform and application code that are included. Ensure that you download a version that is later than or equal to the version of your Dynamics 365 finance and operations environment. Hotfix packages are released to correspond to quality updates.

#### Install NuGet packages

Follow these steps to complete the NuGet package installation.

1. Create a feed. Learn more in [Create a feed](/azure/devops/artifacts/get-started-nuget#create-a-feed).
2. Connect to the feed. In the **Project setup** section, select the **Copy** button to copy the nuget.config XML to the clipboard. Learn more in [Connect to a feed](/azure/devops/artifacts/get-started-nuget#connect-to-a-feed).
3. In Notepad, create a new file, paste the XML that you copied in the previous step, and save the file as **nuget.config**.
4. In your Azure DevOps project, go to your code repository for Dynamics 365 finance and operations apps.
5. Upload the **nuget.config** file that you created in the previous step to your repository. The nuget.config file can be stored anywhere in source control, because the path is defined in variables in the build pipeline. However, we recommend a simple location, such as **Trunk/Main/Projects**.
6. Download [NuGet](https://www.nuget.org/downloads). Save it to the folder where the NuGet packages that you previously downloaded from Lifecycle Services are located.
7. Publish each Dynamics 365 NuGet package by using the command for project-scoped feeds in [Publish packages](/azure/devops/artifacts/get-started-nuget#publish-packages). For example, the command for the compiler package resembles this code.

    ```PowerShell
    nuget.exe push -Source https://pkgs.dev.azure.com/<orgname>/<projectname>/_packaging/<feedname>/nuget/v3/index.json -ApiKey AZ Microsoft.Dynamics.AX.Platform.CompilerPackage.nupkg
    ```

8. Confirm that the packages were published by verifying that the five NuGet packages are in your Azure DevOps project artifacts.

> [!NOTE]
> Free Azure DevOps organizations have limited storage for Azure Artifacts. Consider deleting old and unused versions to free up storage capacity. Learn more in [Sign up for Azure Artifacts](/azure/devops/artifacts/start-using-azure-artifacts#billing-and-free-monthly-usage).

#### Use NuGet packages in a build pipeline

In a build pipeline, two files are used to identify the packages and specify where they can be found. One of the files is a nuget.config file, and the other is a packages.config file. The paths of these files are explicit inputs for the NuGet command and can be defined in the variable section of the build pipeline.

The nuget.config file gives NuGet the source feed where the packages can be found. You created it in the [Install NuGet packages](#install-nuget-packages) section of this article.

The packages.config file specifies the packages and their versions. To build against a newer version, update the versions in the packages.config file. The package.config file is manually created.

The following example shows a packages.config file that contains the main packages that are required for a typical X++ build.

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
    <package id="Microsoft.Dynamics.AX.Platform.DevALM.BuildXpp" version="7.0.7279.40" targetFramework="net40" />
    <package id="Microsoft.Dynamics.AX.Application1.DevALM.BuildXpp" version="10.0.1935.21" targetFramework="net40" />
    <package id="Microsoft.Dynamics.AX.Application2.DevALM.BuildXpp" version="10.0.1935.21" targetFramework="net40" />
    <package id="Microsoft.Dynamics.AX.ApplicationSuite.DevALM.BuildXpp" version="10.0.1935.21" targetFramework="net40" />
    <package id="Microsoft.Dynamics.AX.Platform.CompilerPackage" version="7.0.7279.40" targetFramework="net40" />
</packages>
```

Follow these steps to create a packages.config so that you can use NuGet packages in a build pipeline.

1. Copy the preceding XML.
2. In Notepad, create a new file, and paste the XML that you copied in the previous step. Replace the example version numbers with the actual versions of your NuGet packages.
3. Save the file as **packages.config**.
4. In your Azure DevOps project, go to your code repository for finance and operations apps.
5. Upload the **packages.config** file to your Azure DevOps repository. The packages.config file can be stored anywhere in source control, because the path is defined in variables in the build pipeline. However, for the sake of simplicity, we recommend that you use the same location that you used for the nuget.config file (for example, **Trunk/Main/Projects**).

## Creating the pipeline

Azure DevOps provides pipelines that can be used to automate builds. There are two types of pipelines: YML and Classic. YML pipelines are available only when you use Git source control repositories. Classic pipelines must be used to build Team Foundation Version Control (TFVC) repositories. Learn more in [YAML vs Classic Pipelines](/azure/devops/pipelines/get-started/pipelines-get-started).

This section describes the steps that are required in a pipeline to build X++ code.

### Create a basic build pipeline from a template (preferred method)

Follow these steps to create a build pipeline.

1. Download the **xpp-classic-ci.json** file from the [Dynamics365-Xpp-Samples-Tools](https://github.com/microsoft/Dynamics365-Xpp-Samples-Tools/tree/master/CI-CD/Pipeline-Samples) GitHub repository.
2. In Azure DevOps, select **Pipelines**.
3. Select the three vertical dots, and then select **Import a pipeline** on the menu. Browse to the .json file that you downloaded in the previous step, and import it.

    > [!NOTE]
    > To use Classic pipelines, in Azure DevOps, go to **Organization settings** \> **Pipelines** \> **Settings**, and confirm that both the following settings are disabled (turned off):
    >
    > - Disable creation of classic build pipelines
    > - Disable creation of classic release pipelines

4. The imported pipeline is automatically opened. In the pipeline settings, name your pipeline, set the agent pool, and set the agent specification to **windows-latest**.
5. Select **Get sources**, and set the source to TFVC. The **Workspace mappings** section is opened.
6. Select the ellipsis (**&hellip;**) button next to the **Server path** field, and then select the folder that contains the metadata and projects folders. For example, the folder might be **\$/\<*RepoName*\>/Trunk/Main**.
7. On the **Variables** tab, confirm that **NugetConfigPath** points to the location of the in your Dynamics 365 finance and operations repository. For example, the location might be **\$(Build.SourcesDirectory)\\Projects**.
8. In the **Build solution** task, set your Visual Studio solution to Visual Studio 2022 or the latest version.
9. Save the pipeline.

### Manually create a basic build pipeline

A basic pipeline for compiling X++ and creating a deployable package requires several steps. The pipeline should include a versioning step and a packaging step.

Before you can add the necessary steps to a pipeline to create a deployable package for finance and operations apps, the [Dynamics 365 finance and operations Tools](https://marketplace.visualstudio.com/items?itemName=Dyn365FinOps.dynamics365-finops-tools) extension for Azure DevOps must be enabled and installed in the Azure DevOps organization. Learn how to install an extension for an organization in the [Azure DevOps documentation](/azure/devops/marketplace/install-extension).

The following six tasks must be added to the pipeline agent job:

1. [Install the NuGet packages](#installnuget)
2. [Update the model versions](#updatemodel).
3. [Build the solution or projects](#buildsolutions).
4. [Install NuGet 3.3.0 or earlier on the agent](#installnuget3)
5. [Create the deployable package](#createpackage)
6. [Publish the deployable package](#publishpackage)

#### <a name="installnuget"></a>Task 1. Install the NuGet packages

To install the NuGet packages, you can use the NuGet task and change it to a custom command in the task properties. The custom command should resemble this code.

```dos
install -Noninteractive $(NugetConfigsPath)\packages.config -ConfigFile $(NugetConfigsPath)\nuget.config -Verbosity Detailed -ExcludeVersion -OutputDirectory "$(NugetsPath)" 
```

> [!NOTE]
> To simplify the use of the extracted NuGet packages, consider using the **NuGet install** option and specifying the **-ExcludeVersion** [NuGet command-line option](/nuget/reference/cli-reference/cli-ref-install#options). The extracted package paths can be used in the build, regardless of the version of the packages.
>
> The NuGetInstaller\@0 version of the task has been deprecated, Microsoft recommends that you use the NuGetCommand\@2 version of the task.

#### <a name="updatemodel"></a>Task 2. Update the model versions

Follow the steps here to install and configure the [Update the model versions](pipeline-model-version.md) task.

#### <a name="buildsolutions"></a>Task 3. Build the solution or projects

The Visual Studio build task lets you select the Visual Studio version that is used to build the solution or projects. Before you can use the task, the MSBuild arguments in the task must be populated.

The following table describes the variables that are used in the MSBuild arguments.

| Argument | Description |
| --- | --- |
| /p:BuildTasksDirectory | The path of the extracted Compiler Tools NuGet package, including the subfolders in the DevAlm folder. |
| /p:MetadataDirectory | The path of the X++ source code. |
| /p:FrameworkDirectory | The path of the extracted Compiler Tools NuGet package. |
| /p:ReferenceFolder | A semicolon-separated list of paths that contain binaries of X++ packages that are referenced and required for compilation (for example, Application Platform and Application Suite). If the code that will be compiled has multiple packages that reference each other, the output directory should also be included here. |
| /p:ReferencePath | A semicolon-separated list of paths that contain any non-X++ binaries that are referenced and required for compilation. You should include the location of the extracted Compiler Tools NuGet package, because it might contain required references. |
| /p:OutputDirectory | The path where the compiler will create folders and binaries. |

The following example shows a value that can be used for the MSBuild arguments.

```dos
/p:BuildTasksDirectory="$(Pipeline.Workspace)\NuGets\Microsoft.Dynamics.AX.Platform.CompilerPackage\DevAlm"
/p:MetadataDirectory="$(Build.SourcesDirectory)\Metadata"
/p:FrameworkDirectory="$(Pipeline.Workspace)\NuGets\Microsoft.Dynamics.AX.Platform.CompilerPackage"
/p:ReferenceFolder="$(Pipeline.Workspace)\NuGets\Microsoft.Dynamics.AX.Platform.DevALM.BuildXpp\ref\net40;$(Pipeline.Workspace)\NuGets\Microsoft.Dynamics.AX.Application1.DevALM.BuildXpp\ref\net40;$(Pipeline.Workspace)\NuGets\Microsoft.Dynamics.AX.Application2.DevALM.BuildXpp\ref\net40;$(Pipeline.Workspace)\NuGets\Microsoft.Dynamics.AX.ApplicationSuite.DevALM.BuildXpp\ref\net40;$(Build.SourcesDirectory)\Metadata;$(Build.BinariesDirectory)"
/p:ReferencePath="$(Pipeline.Workspace)\NuGets\Microsoft.Dynamics.AX.Platform.CompilerPackage" /p:OutputDirectory="$(Build.BinariesDirectory)"
```

The preceding example of MSBuild arguments assumes that the NuGet packages are installed in **\$(Pipeline.Workspace)\\NuGets**, the X++ source code is in **\$(Build.SourcesDirectory)\\Metadata**, and the output of the compiler should go in **\$(Build.BinariesDirectory)**.

In the pipeline samples, variables for NuGet package names and paths are used to simplify these commands.

#### <a name="installnuget3"></a>Task 4. Install NuGet 3.3.0 or earlier on the agent

This step is required for the step that creates the deployable package. The deployable package can be created only if NuGet is readily available on the build agent. Therefore, the **NuGet tool installer** task in Azure DevOps must be run before the step that creates the deployable package.

> [!NOTE]
> Because of semantic versioning features in NuGet version 3.4 and later, make sure that the task installs version 3.3.0 or earlier. Currently, deployable package generation doesn't support semantic versioning.

#### <a name="createpackage"></a>Task 5. Create the deployable package

Follow the instructions in [Create deployable packages in Azure Pipelines](pipeline-create-deployable-package.md).

> [!NOTE]
> If your source code repository includes binary packages from third parties such as independent software vendors (ISVs), explicitly add those packages to the packaging step. Learn more in [Create deployable packages in Azure Pipelines](pipeline-create-deployable-package.md).

#### <a name="publishpackage"></a>Task 6. Publish the deployable package

Add the **Publish build artifacts** task to your build pipeline.

### Sample pipeline for X++ developers

In the [Dynamics365-Xpp-Samples-Tools](https://github.com/microsoft/Dynamics365-Xpp-Samples-Tools/tree/master/CI-CD/Pipeline-Samples) GitHub repository, you can find a sample pipeline that can be imported into an existing Azure DevOps project.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
