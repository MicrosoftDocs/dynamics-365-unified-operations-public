---
# required metadata

title: Integrate the Retail SDK with the continuous build system (VSTS) | Microsoft Docs
description: The LCS-integrated experience supports both code upgrades and new projects. The Retail SDK is a self-contained MSBuild-based build system. Many customizers want to make productive changes in both Microsoft Dynamics 365 for Operations and Retail components. This article outlines the manual steps for merging both build systems. 
author: MargoC
manager: AnnBe
ms.date: 2016-04-12 22:07:22
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: 61
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 80861
ms.assetid: f3e3e905-268c-45ba-8c30-7abb6d49f15c
ms.region: Global
# ms.industry: 
ms.author: margoc

---

# Integrate the Retail SDK with the continuous build system (VSTS)

The LCS-integrated experience supports both code upgrades and new projects. The Retail SDK is a self-contained MSBuild-based build system. Many customizers want to make productive changes in both Microsoft Dynamics 365 for Operations and Retail components. This article outlines the manual steps for merging both build systems. 

Enable the build system
-----------------------

To get started, you must follow all the steps to get a full Dynamics 365 for Operations continuous build system up and running. For information, see [Developer topology deployment with continuous build and test automation](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/perf-test/developer-topology-deployment-with-continuous-build-and-test-automation). After deployment, you create the build definition and build steps. Build at least one time, so that you become familiar with it and are sure that you can build without errors. Then move to the next step.

## Prepare the Retail SDK
### Getting the Retail SDK

If you don't already have the Retail software development kit (SDK) in the same Microsoft Visual Studio Team Services (VSTS) project, add it now. You will find the Retail SDK in any developer or build topology. Follow the branching documentation in the **Retail Sdk Handbook.pdf** file, which is in the Documents folder for the Retail SDK. We recommend that you create your Retail SDK mirror and your Retail SDK customization branch at this time. After your Retail SDK customization branch is ready, and it has been submitted in the same VSTS project as Dynamics 365 for Operations, you can start.

### Get the build target working

You must make some changes in a few filesto get the correct build targeting to work. (These changes will be made in a future release of the Retail SDK.)

#### 1. Add a Clean target

Add a correct Clean target at the end of these four project files:

-   Packages\\CloudPos\\Sdk.CloudPosSetup.proj
-   Packages\\RetailDeployablePackage\\Sdk.RetailDeployablePackageSetup.proj
-   Packages\\RetailSelfService\\Sdk.RetailSelfServiceSetup.proj
-   Packages\\RetailServer\\Sdk.RetailServerSetup.proj

In an XML editor of your choice, update the Rebuild and Clean MSBuild targets as shown here.

    <Target Name="Rebuild">
    <CallTarget Targets="Clean" />
    <CallTarget Targets="Build" />
    </Target>
    <Target Name="Clean">
    <RemoveDir Directories="$(OutputPath)content.folder" />
    <Delete Files="$(OutputPath)content.zip" />
    </Target>
    </Project>

All four project files require the same changes.

#### 2. Change the CopyTypeScriptLibraries target

Change the CopyTypeScriptLibraries target in these four project files:

-   OnlineStore\\Ecommerce.Sdk.Controls\\Platform.Ecommerce.Sdk.Controls.csproj
-   POS\\App\\Pos.App.jsproj
-   POS\\ViewModels\\Pos.ViewModels.csproj
-   POS\\Web\\Pos.Web.csproj

<!-- -->

    <Target Name="CopyTypeScriptLibraries" BeforeTargets="PreComputeCompileTypeScript;">
        <Copy SourceFiles="%(TypeScriptLibraries.Identity)" DestinationFiles="$(TypeScriptLibrariesOutDir)%(TypeScriptLibraries.FileName)%(TypeScriptLibraries.Extension)" SkipUnchangedFiles="true" Condition="Exists('%(TypeScriptLibraries.Identity)')" />
    </Target>

Make this change in all four files. When you've finished, submit these eight file changes to VSTS.

### Add two Windows PowerShell scripts to the Retail SDK that will be used for build tasks

You need to add two scripts that the build can use to do its work. (These scripts will be added automatically in a future release of the Retail SDK.) In the Retail Sdk\\Buildtools folder, add a file that has the following content file. Name this file **Copy-RetailBinaries.ps1**.

    Param(
        [Parameter(Mandatory=$true, HelpMessage="The path to the build metadata.")]
        [string]$BuildMetadataPath
    )
    function Copy-FileWithCheck($fromFilePath, $toFilePath)
    {
        if (!(Test-Path -Path $fromFilePath))
        {
            throw "Could not find $fromFilePath"
        }
        $toDirectoryPath = Split-Path -Path $toFilePath -Parent
        if (!(Test-Path -Path $toDirectoryPath))
        {
            New-Item $toDirectoryPath -Type container -force
        }
        Write-Host "Copying $fromFilePath to $toFilePath..."
        Copy-Item -Path $fromFilePath -Destination $toFilePath -Force
    }
    [int]$ExitCode = 0
    try
    {
        Write-Host "Copying Retail binaries to: $BuildMetadataPath"
        if ([String]::IsNullOrEmpty($BuildMetadataPath))
        {
            throw "No valid path is specified in BuildMetadataPath parameter."
        }
        $scriptRootPath = $PSScriptRoot
        $retailSdkSourcePath = Split-Path $scriptRootPath -Parent
        $retailSdkReferencesPath = Join-Path -Path $retailSdkSourcePath -ChildPath 'References'
        # add your own file copies here...
            $fileName = 'Contoso.Commerce.Runtime.Services.PricingEngine.dll'
            Copy-FileWithCheck -fromFilePath (Join-Path -Path $retailSdkReferencesPath -ChildPath $fileName) `
                               -toFilePath (Join-Path -Path $BuildMetadataPath -ChildPath "ApplicationSuite\bin\$fileName")
        Write-Host "Copying of Retail packages complete."
    }
    catch [System.Exception]
    {
        Write-Host "- Exception thrown at $($_.InvocationInfo.ScriptName):$($_.InvocationInfo.ScriptLineNumber): $($_.InvocationInfo.Line.Trim())$([Environment]::NewLine)$($_.Exception.ToString())"
        Write-Error "Error copying Retail packages: $($_)"
        $ExitCode = -1
    }
    Write-Host "Script completed with exit code: $ExitCode"
    Exit $ExitCode

In the same folder, add a file that has the following content. Name this file **Copy-RetailPackages.ps1**.

    Param(
        [Parameter(Mandatory=$true, HelpMessage="The path where to produce the deployable packages.")]
        [string]$BuildPackagePath,
        [Parameter(Mandatory=$false, HelpMessage="The build number to use in the package names.")]
        [string]$BuildVersion = "1.0.0.0"
    )
    function Copy-FileWithCheck($fromFilePath, $toFilePath)
    {
        if (!(Test-Path -Path $fromFilePath))
        {
            throw "Could not find $fromFilePath"
        }
            $toDirectoryPath = Split-Path -Path $toFilePath -Parent
        if (!(Test-Path -Path $toDirectoryPath))
        {
            New-Item $toDirectoryPath -Type container -force
        }
        Write-Host "Copying $fromFilePath to $toFilePath..."
        Copy-Item -Path $fromFilePath -Destination $toFilePath -Force
    }
    [int]$ExitCode = 0
    try
    {
        Write-Host "Copying Retail packages to: $BuildPackagePath"
        if ([String]::IsNullOrEmpty($BuildPackagePath))
        {
            throw "No valid path is specified in BuildPackagePath parameter."
        }
        $scriptRootPath = $PSScriptRoot
        $retailSdkSourcePath = Split-Path $scriptRootPath -Parent
        New-Item $BuildPackagePath -Type container -force
        # RetailServer package
            Copy-FileWithCheck -fromFilePath (Join-Path -Path $retailSdkSourcePath -ChildPath 'Packages\RetailServer\content.zip') `
                               -toFilePath (Join-Path -Path $BuildPackagePath -ChildPath "RetailServer_$BuildVersion.zip")
        # CloudPOS package
            Copy-FileWithCheck -fromFilePath (Join-Path -Path $retailSdkSourcePath -ChildPath 'Packages\CloudPOS\content.zip') `
                               -toFilePath (Join-Path -Path $BuildPackagePath -ChildPath "CloudPOS_$BuildVersion.zip")
        # RetailSelfService package (includes ModernPOS, ModernPOSOffline, HardwareStation packages)
            Copy-FileWithCheck -fromFilePath (Join-Path -Path $retailSdkSourcePath -ChildPath 'Packages\RetailSelfService\content.zip') `
                               -toFilePath (Join-Path -Path $BuildPackagePath -ChildPath "RetailSelfService_$BuildVersion.zip")
        Write-Host "Copying of Retail packages complete."
    }
    catch [System.Exception]
    {
        Write-Host "- Exception thrown at $($_.InvocationInfo.ScriptName):$($_.InvocationInfo.ScriptLineNumber): $($_.InvocationInfo.Line.Trim())$([Environment]::NewLine)$($_.Exception.ToString())"
        Write-Error "Error copying Retail packages: $($_)"
        $ExitCode = -1
    }
    Write-Host "Script completed with exit code: $ExitCode"
    Exit $ExitCode

When you've finished, submit both files to VSTS.

## Add a repository mapping for the Retail SDK
Edit the build definition so that it includes the location of the Retail SDK. (In other words, add a map.) [![Adding a repository mapping for the Retail SDK](./media/build-map-addition.png)](./media/build-map-addition.png)

## Add a new build step to build the Retail SDK
Add a new step at the beginning of the build pipeline, as shown in the following screen shot. [![Adding a new build step to build the Retail SDK](./media/new-build-step-1024x527.png)](./media/new-build-step.png)

## Add a copy step for binaries from the Retail SDK to the Dynamics 365 for Operations build
This build step enables Microsoft to copy the latest built Retail binaries to the Dynamics 365 for Operations bin folder, if Microsoft shares files/binaries. Make sure that you complete this step immediately after you add a build step for the Retail SDK, as described in the previous section. [![Adding a copy step for binaries from the Retail SDK to the Dynamics AX build](./media/binary-drop-to-ax.png)](./media/binary-drop-to-ax.png)

## Add a copy step for all Retail packages
Make sure that this step occurs after the “PowerShell: Generate packages” step (see image below). Here are the arguments.

    -BuildPackagePath "$(Agent.BuildDirectory)\Packages" -BuildVersion "$(Build.BuildNumber)"

[![Adding a copy step for all Retail packages](./media/package-drop-1024x473.png)](./media/package-drop.png)

## Optional: Referencing a Retail DLL from Dynamics 365 for Operations
You must complete this task only if you must add built Retail binaries to the Dynamics 365 for Operations package. In this case, you must follow these three steps:

1.  Use a normal AXReference in your Dynamics 365 for Operations project.
2.  Add the corresponding AXReference folder and the XML file inside it to VSTS.
3.  Update the Copy-RetailBinaries.ps1 file with the appropriate file commands to get the binary file from the Retail SDK to the Dynamics 365 for Operations bin folder. The Microsoft Windows PowerShell file includes a sample that copies the PricingEngine.dll file into the ApplicationSuite bin folder. Depending on the modules that you're building, the files and folders must be changed so that they are in a different location.


