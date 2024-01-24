---
title: Upload ER configurations and Globalization features as a Dataverse solution (preview)
description: This article explains how to upload ER configurations and globalization features as a Dataverse solution (preview)
author: filatovm
ms.author: filatovm
ms.topic: conceptual 
ms.date: 01/29/2023
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak

---

# Upload ER configurations and Globalization features as a Dataverse solution (preview)

[!INCLUDE[banner](../../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
[!INCLUDE[banner](../../../includes/rsc-to-gsw-banner.md)]

You can use Dataverse solutions for Application Lifecycle Management (ALM) scenarios – moving ER configurations to other environments, sharing them with other tenants via AppSource, etc.

You can also export and import specific versions as a file using export and import buttons on the form (existing functionality).

## Pre-requisites

- Install PowerShell 7 [Installing PowerShell on Windows - PowerShell | Microsoft Learn](/powershell/scripting/install/installing-powershell-on-windows)
- Install [Microsoft Power Platform CLI - Power Platform | Microsoft Learn](/power-platform/developer/cli/introduction)

Get Generate-GlobalizationDataverseSolution.ps1 script from LCS Shared Asset Library, \<\<Asset type:, Asset name:\>\>

## Step 1: Export your artifacts

To export your artifacts, follow these steps.

1. Create new folder. For example, C:\DvArtifactsSrc.
1. Export any ER configurations .xml files, and any globalization features .json files to that folder.
   > [!IMPORTANT]
   > **Do not** include Microsoft configurations.

## Step 2: Create a Dataverse solution

To create a Dataverse solution, follow these steps.

1. Create new solution in Dataverse. For more information, see [Create a solution in Power Apps - Power Apps | Microsoft Learn](/power-apps/maker/data-platform/create-solution), and export it [Export solutions - Power Apps | Microsoft Learn](/power-apps/maker/data-platform/export-solutions).
1. Extract the new solution with the **pac solution unpack** command. For example:
   
   ``` command
   pac solution unpack --zipfile C:\SampleEmptySolution.zip --folder C:\SampleSolutionUnpacked
   ```
   For more information, see [pac solution unpack](/power-platform/developer/cli/reference/solution#pac-solution-unpack).

## Step 3: Run script

Run the Generate-GlobalizationDataverseSolution.ps1 script in PowerShell 7 specifying the following parameters:

- Working folder as DvArtifactsSrcFolder parameter.
- Solution folder as SolutionFolder parameter.
- ConfigurationsIndexRowName parameter: indicates name of Dataverse table record with index file for configurations. Use only alphanumeric characters and whitespaces. Note that if you change later that name then corresponding row in Dataverse table will have different GUID and index files will be duplicated. If you don't have any ER configurations you can omit this parameter. For example:

  ``` command
  Contoso Electronic Reporting Configurations Index
  ``` 
- FeaturesIndexRowName parameter: indicates name of Dataverse table record with index file for features. Use only alphanumeric characters and whitespaces. Note that if you change later that name then corresponding row in Dataverse table will have different GUID and index files will be duplicated. If you don't have any G. Features you can omit this parameter. For example:
   
  ``` command
  Contoso Globalization Features Index
  ```

**Full PowerShell 7 command line example:**

``` command
pwsh -ExecutionPolicy RemoteSigned -File C:\Generate-GlobalizationDataverseSolution.ps1 -DvArtifactsSrcFolder C:\DvArtifactsSrc -SolutionFolder C:\SampleSolutionUnpacked -configurationsIndexRowName "Contoso Electronic Reporting Configurations Index" -featuresIndexRowName "Contoso Globalization Features Index"
```

## Step 4: Pack the solution

Pack the solution with the **pac solition unpack** command. For example:

``` command
pac solution pack --zipfile C:\SampleSolutionWithContents.zip --folder C:\SampleSolutionUnpacked --packagetype Both
```

> [!NOTE]
> Check size of generated .zip file. If it exceeds 90 megabytes you need to split your source files into multiple Dataverse solutions.

For more information, see [pac solution unpack](/power-platform/developer/cli/reference/solution#pac-solution-unpack).

## Step 5: Import the solution to Dataverse

Import the solition back to Dataverse.

- [Import solutions - Power Apps | Microsoft Learn](/power-apps/maker/data-platform/import-update-export-solutions).
- You can also use [pac solution import](/power-platform/developer/cli/reference/solution#pac-solution-import) command.
  > [!NOTE]
  > After importing the solution to Dataverse, there is no way to remove it together with content. You can remove the solution, but all inserted tables records will remain, they need to be cleaned up manually.
- [Publish your app on AppSource - Power Platform | Microsoft Learn](/power-platform/developer/appsource/publish-app).

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
