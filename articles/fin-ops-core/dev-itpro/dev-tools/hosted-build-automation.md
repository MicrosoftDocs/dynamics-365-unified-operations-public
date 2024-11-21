---
title: Build automation that uses Microsoft-hosted agents and Azure Pipelines
description: Learn about how you can automate the process of building X++ on any agents in Microsoft Azure DevOps, including prerequisites.
author: josaw1
ms.author: josaw
ms.topic: article
ms.date: 09/29/2023
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2020-03-05
ms.dyn365.ops.version: AX 7.0.0
---

# Build automation that uses Microsoft-hosted agents and Azure Pipelines

[!include [banner](../includes/banner.md)]

Within Azure DevOps you can automate the process of building X++ code and creating deployable packages on any Microsoft Windows build agent. These agents include [Microsoft-hosted agents](/azure/devops/pipelines/agents/hosted). This approach helps you avoid the setup, maintenance, and cost of deploying build virtual machines (VMs). It also lets you reuse the existing setup of build agents to run other .NET build automation.

> [!NOTE]
> This feature is limited to compilation and packaging. There is no support for X++ unit testing (SysTest), database synchronization, or other features that require the runtime (Application Object Server \[AOS\]) or its components.

## Prerequisites for building X++ code

### Build projects

To use .NET tools for building X++ in Azure DevOps, the Microsoft Build Engine (MSBuild) and custom X++ targets are used. Your X++ source code repository must contain an X++ project for each package that you have to build. 

You can optionally use a solution file to group the projects, including C# project dependencies, and provide an explicit build order. If the repository doesn't already contain a project, you can create a project in Visual Studio.

Also ensure that you have a Descriptor folder and checked in the descriptor file for each model to your model Metadata folder in Azure DevOps.

> [!NOTE]
> When you use an existing X++ project (rnrproj), make sure that you created it, or opened and saved it, by using Visual Studio tools.
>
> Although a package can contain multiple models, it must always be built in its entirety. Therefore, only one project for just one of the models is required to build the whole package. Additionally, although the project doesn't have to contain any objects, it can contain them.

### NuGet packages

NuGet packages are used for the Azure DevOps build pipelines and include the required tools to build X++ code, such as the X++ compiler (xppc.exe), Application Platform, Application Suite, and other models. 

The following NuGet packages are available in the Shared asset library in Microsoft Dynamics Lifecycle Services (LCS):
- **Microsoft.Dynamics.AX.Platform.CompilerPackage** 
   - This package contains the X++ compiler and related tools that are required to do a build.
   - The name of the package is typically **PUXX/10.X.XX – Compiler Tools**
- **Microsoft.Dynamics.AX.Platform.DevALM.BuildXpp** 
   - This package contains the compiled X++ code for the Application Platform and related modules. This code is optimized for building.
   - The name of the package is typically **PUXX/10.X.XX – Platform Build Reference**
- **Microsoft.Dynamics.AX.Application1.DevALM.BuildXpp**
   - This package contains the compiled X++ code for the Application and related modules. This code is optimized for building.
   - The name of the package is typically **PUXX/10.X.XX – Application 1 Build Reference**

- **Microsoft.Dynamics.AX.Application2.DevALM.BuildXpp** 
   - This package contains the compiled X++ code for the Application and related modules. This code is optimized for building.
   - The name of the package is typically **PUXX/10.X.XX – Application 2 Build Reference**
- **Microsoft.Dynamics.AX.ApplicationSuite.DevALM.BuildXpp**
   - This package contains the compiled X++ code for the Application Suite module. This code is optimized for building.
   - The name of the package is typically **PUXX/10.X.XX – Application Suite Build Reference**
> [!NOTE]
> LCS contains six NuGet packages per release. However, the package name PUXX/10.X.XX – Application Build Reference, that is the combined version of Application 1 Build Reference and Application 2 Build Reference, is not needed.  The split packages are smaller and can be used in place of the single package.

> [!IMPORTANT]
> The NuGet packages contain version details about which platform and application code are included.  Ensure the version you download is greater than or equal to the version of your D365 Finance and Operations environment. Hotfix packages are released to correspond with quality updates.

#### NuGet package installation
Follow these steps to complete the NuGet package installation:
1. Create a feed as per the section in this document [Create a feed](/azure/devops/artifacts/get-started-nuget#create-a-feed)
2. Connect to the feed  as per the section in this document [Connect to a feed](/azure/devops/artifacts/get-started-nuget#connect-to-a-feed)
3. From the step above, copy the nuget.config XML, which is in the Project setup pane, to Notepad and save the file as nuget.config.
4. Within your Azure DevOps project, navigate to your code repository for D365 Finance and Operations.  Upload the nuget.config file, created in the step above, to your repository. The nuget.config can be stored anywhere in source control since the path is defined in variables within the build pipeline. To simply the location, we recommend a simple location, for example, Trunk / Main / Projects.
5. Download [NuGet]( https://www.nuget.org/downloads) and save it to the same folder where the NuGet packages that were previously downloaded from LCS are located.
6. Publish each of the D365 NuGet packages using the command for Project-scoped feeds from this document [Publish packages](/azure/devops/artifacts/get-started-nuget#publish-packages). For example, for the compiler package the command would look similar to this:
```PowerShell
nuget.exe push -Source https://pkgs.dev.azure.com/<orgname>/<projectname>/_packaging/<feedname>/nuget/v3/index.json -ApiKey AZ Microsoft.Dynamics.AX.Platform.CompilerPackage.nupkg
```
7. Confirm the publish worked by verifying that the five NuGet packages are in your DevOps project Artifacts.
> [!NOTE]
> Free Azure DevOps organizations have limited storage for Azure Artifacts. Consider deleting old and unused versions to free up storage capacity. For more information, see [Sign up for Azure Artifacts](/azure/devops/artifacts/start-using-azure-artifacts#billing-and-free-monthly-usage).

#### Utilizing NuGet packages in a build pipeline
There are two files which are used during a build pipeline to identify which packages should be and where they can be found. The two files are a nuget.config file and a packages.config. The paths of these files are explicit inputs for the NuGet command and can be defined within the variable section of the build pipeline. 

The nuget.config was created using the steps in the NuGet package installation section. The nuget.config file provides NuGet with the source feed where the packages can be found. 

The packages.config file specifies the packages and their versions. To build against a newer version, you just have to update the versions in the packages.config file. The package.config is created manually.

The following example shows a **packages.config** file containing the main packages that are required for a typical X++ build. You must substitute the listed version with the actual versions of your NuGet packages.
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
Copy the XML from above and paste the contents into Notepad.  Save the file as packages.config. Within your Azure DevOps project, navigate to your code repository for D365 Finance and Operations.  Upload the packages.config file, to your Azure DevOps repository. The packages.config can be stored anywhere in source control since the path is defined in variables within the build pipeline. To simply the location, we recommend it is in the same location as the nuget.config file, for example, Trunk / Main / Projects.
## Creating the pipeline

Azure DevOps provides pipelines that can be used to automate builds. There are two types of pipelines: YML and Classic. YML pipelines are available only when you use Git source control repositories. Classic pipelines must be used to build Team Foundation Version Control (TFVC) repositories. For more information, see [Azure Pipelines](/azure/devops/pipelines/get-started/pipelines-get-started).

This section describes the steps that are required in a pipeline to build X++ code. 
### Creating a basic build pipeline from template (preferred)
Use the following steps to create a build pipeline:
1. Download xpp-classic-ci.json file found [here]( https://github.com/microsoft/Dynamics365-Xpp-Samples-Tools/tree/master/CI-CD/Pipeline-Samples)
2. Within Azure DevOps, select Pipelines, choose Import a pipeline (available from the 3 dots menu), and browse to the json that was downloaded in the step above and import that.
> [!NOTE]
> To utilize classic pipelines you must go into Azure DevOps go to Organization settings. Navigate to Pipelines > Settings. Ensure the following two settings are disabled (Off):
> - Disable creation of classic build pipelines
> - Disable creation of classic release pipelines
3. The imported pipeline automatically opens. Under the pipeline settings, name your pipeline, set the Agent pool, and set the Agent Specification to windows-latest.
4. Click on Get sources and set the source to be TFVC. This opens the Workspace mappings section. For the Server path, click on the ellipses button and choose the folder that contains the Metadata and Projects folders. For example, $/<RepoName>/Trunk/Main.
5. Click on the Variables tab and confirm the NugetConfigPath points to the location of the in your D365 Finance and Operations repository. For example, $(Build.SourcesDirectory)\Projects.
6. In the Build solution task, set your Visual Studio solution to Visual Studio 2022 or to Latest.
7. Save the pipeline.
### Creating a basic build pipeline manually

A basic pipeline for compiling X++ and creating a deployable package requires several steps.  The pipeline should include a versioning step and a packaging step. 
Before you can add the necessary steps to a pipeline to create a deployable package for D365 Dynamics and operations, the [Dynamics 365 finance and operations Tools](https://marketplace.visualstudio.com/items?itemName=Dyn365FinOps.dynamics365-finops-tools) extension for Azure DevOps must be enabled and installed in the Azure DevOps organization. For information about how to install an extension for an organization, see the [Azure DevOps documentation](/azure/devops/marketplace/install-extension).
The following lists the six tasks that need to be added to the pipeline agent job.
1. [Install the NuGet packages](#installnuget)
2. [Update the model versions](#updatemodel).
3. [Build the solution or projects](#buildsolutions).
4. [Install NuGet 3.3.0 or earlier on the agent](#installnuget3)
5. [Create the deployable package ](#createpackage)
6. [Publish the deployable package](#publishpackage)
#### <a name=”installnuget”></a>Task 1. Install the NuGet packages 
You can use the NuGet task and change to a custom command in the task properties to install the NuGet packages. The custom command should look like this:
```dos
install -Noninteractive $(NugetConfigsPath)\packages.config -ConfigFile $(NugetConfigsPath)\nuget.config -Verbosity Detailed -ExcludeVersion -OutputDirectory "$(NugetsPath)" 
```
> [!NOTE]
> To simplify use of the extracted NuGet packages, consider using the **NuGet install** option and specifying the **-ExcludeVersion** [NuGet command-line option](/nuget/reference/cli-reference/cli-ref-install#options). In that way, the extracted package paths can be used in the build, regardless of the version of the packages.

> [!NOTE]
> Because the NuGetInstaller@0 version of the task has been deprecated, Microsoft recommends that you use the NuGetCommand@2 version of the task instead.

#### <a name=”updatemodel”></a> Task 2. Update the model versions
Follow the steps here to install and configure the  [Update the model versions](pipeline-model-version.md) task.
#### <a name=”buildsolutions”></a> Task 3. Build the solution or projects
 The Visual Studio build task allows you to select the Visual Studio version to use for building the solution or projects. To use the task, the MSBuild arguments within the task must be populated.  
The following variables are used in the MSBuild arguments:
| Argument | Description |
| --- | --- |
| /p:BuildTasksDirectory | The path of the extracted Compiler Tools NuGet package, including the subfolders in the DevAlm folder. |
| /p:MetadataDirectory | The path of the X++ source code. |
| /p:FrameworkDirectory | The path of the extracted Compiler Tools NuGet package. |
| /p:ReferenceFolder | A semicolon-separated list of paths that contain binaries of X++ packages that are referenced and required for compilation (for example, Application Platform and Application Suite). If the code that will be compiled has multiple packages that reference each other, the output directory should also be included here. |
| /p:ReferencePath | A semicolon-separated list of paths that contain any non-X++ binaries that are referenced and required for compilation. You should include the location of the extracted Compiler Tools NuGet package, because it might contain required references. |
| /p:OutputDirectory | The path where the compiler will create folders and binaries. |

The following is an example of what could be used in the MSBuild arguments value:
```dos
/p:BuildTasksDirectory="$(Pipeline.Workspace)\NuGets\Microsoft.Dynamics.AX.Platform.CompilerPackage\DevAlm"
/p:MetadataDirectory="$(Build.SourcesDirectory)\Metadata"
/p:FrameworkDirectory="$(Pipeline.Workspace)\NuGets\Microsoft.Dynamics.AX.Platform.CompilerPackage"
/p:ReferenceFolder="$(Pipeline.Workspace)\NuGets\Microsoft.Dynamics.AX.Platform.DevALM.BuildXpp\ref\net40;$(Pipeline.Workspace)\NuGets\Microsoft.Dynamics.AX.Application1.DevALM.BuildXpp\ref\net40;$(Pipeline.Workspace)\NuGets\Microsoft.Dynamics.AX.Application2.DevALM.BuildXpp\ref\net40;$(Pipeline.Workspace)\NuGets\Microsoft.Dynamics.AX.ApplicationSuite.DevALM.BuildXpp\ref\net40;$(Build.SourcesDirectory)\Metadata;$(Build.BinariesDirectory)"
/p:ReferencePath="$(Pipeline.Workspace)\NuGets\Microsoft.Dynamics.AX.Platform.CompilerPackage" /p:OutputDirectory="$(Build.BinariesDirectory)"
```
The above example of MSBuild arguments assumes that the NuGet packages are installed in **$(Pipeline.Workspace)\\NuGets**, the X++ source code is in **$(Build.SourcesDirectory)\\Metadata**, and the output of the compiler should go in **$(Build.BinariesDirectory)**.
In the pipeline samples, variables for NuGet package names and paths are used to simplify these commands.
#### <a name=”installnuget3”></a>Task 4. Install NuGet 3.3.0 or earlier on the agent. 
This step is required for the step that creates the deployable package. For the deployable package to be created, NuGet must be readily available on the build agent. Therefore, this **NuGet tool installer** task in Azure DevOps must be run before the step that creates the deployable package.
> [!NOTE]
> Because of semantic versioning features in NuGet version 3.4 and later, make sure that the task installs version 3.3.0 or earlier. Currently, deployable package generation doesn't support semantic versioning.

#### <a name=”createpackage”></a>Task 5. Create the deployable package
Follow the details in this link [Create the deployable package](pipeline-create-deployable-package.md).
> [!NOTE]
> If your source code repository includes binary packages from third parties like ISVs, you have to explicitly add those to the packaging step. For more information, see [Create deployable packages in Azure Pipelines](pipeline-create-deployable-package.md).

#### <a name=”publishpackage”></a>Task 6. Publish the deployable package 
Add the Publish build artifacts task to your build pipeline.

### Sample pipeline for X++ developers

In the [Dynamics365-Xpp-Samples-Tools](https://github.com/microsoft/Dynamics365-Xpp-Samples-Tools/tree/master/CI-CD/Pipeline-Samples) GitHub repository, you can find a sample pipeline that can be imported into an existing Azure DevOps project.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]


