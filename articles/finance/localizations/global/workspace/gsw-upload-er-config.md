---
title: Globalization features
description: This article explains the features of Globalization Studio workspace
author: filatovm
ms.author: filatovm
ms.topic: conceptual 
ms.date: 01/29/2023
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak

---

# Upload ER configurations and Globalization features as a Dataverse solution

You can use Dataverse solutions for Application Lifecycle Management (ALM) scenarios – moving ER configurations to other environments, sharing them with other tenants via AppSource, etc.

You can also export and import specific versions as afile using export and import buttons on the form (existing functionality).

## Pre-requisites

- Install PowerShell 7 [Installing PowerShell on Windows - PowerShell | Microsoft Learn](https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell-on-windows?view=powershell-7.3)
- Install [Microsoft Power Platform CLI - Power Platform | Microsoft Learn](https://learn.microsoft.com/en-us/power-platform/developer/cli/introduction)

Get Generate-GlobalizationDataverseSolution.ps1 script from LCS Shared Asset Library, \<\<Asset type:, Asset name:\>\>

## Step 1: Export your artefacts

- Create new folder, e.g. C:\DvArtifactsSrc
- Export ER configurations .xml files (if any) and G. Features .json files (if any) to that folder.
  - **Do not** include Microsoft configurations.

## Step 2: Create Dataverse solution

- Create new solution in Dataverse [Create a solution in Power Apps - Power Apps | Microsoft Learn](https://learn.microsoft.com/en-us/power-apps/maker/data-platform/create-solution) and export it [Export solutions - Power Apps | Microsoft Learn](https://learn.microsoft.com/en-us/power-apps/maker/data-platform/export-solutions)
- Extract it with [pac solution unpack](https://learn.microsoft.com/en-us/power-platform/developer/cli/reference/solution#pac-solution-unpack) command, e.g.

pac solution unpack --zipfile C:\SampleEmptySolution.zip --folder C:\SampleSolutionUnpacked

## Step 3: Run script

Run Generate-GlobalizationDataverseSolution.ps1 script in PowerShell 7 specifying:

- working folder as DvArtifactsSrcFolder parameter
- solution folder as SolutionFolder parameter
- ConfigurationsIndexRowName parameter: indicates name of Dataverse table record with index file for configurations. Use only alphanumeric characters and whitespaces. Note that if you change later that name then corresponding row in Dataverse table will have different GUID and index files will be duplicated. If you don't have any ER configurations you can omit this parameter.
 Example:

"Contoso Electronic Reporting Configurations Index"

- FeaturesIndexRowName parameter: indicates name of Dataverse table record with index file for features. Use only alphanumeric characters and whitespaces. Note that if you change later that name then corresponding row in Dataverse table will have different GUID and index files will be duplicated. If you don't have any G. Features you can omit this parameter.
 Example:

"Contoso Globalization Features Index"

**Full PowerShell 7 command line example:**

pwsh -ExecutionPolicy RemoteSigned -File C:\Generate-GlobalizationDataverseSolution.ps1 -DvArtifactsSrcFolder C:\DvArtifactsSrc -SolutionFolder C:\SampleSolutionUnpacked -configurationsIndexRowName "Contoso Electronic Reporting Configurations Index" -featuresIndexRowName "Contoso Globalization Features Index"

## Step 4: Pack solution

- Pack solution with [pac solution pack](https://learn.microsoft.com/en-us/power-platform/developer/cli/reference/solution#pac-solution-pack) command, e.g.

  - pac solution pack --zipfile C:\SampleSolutionWithContents.zip --folder C:\SampleSolutionUnpacked --packagetype Both

- Check size of generated .zip file. If it exceeds 90 megabytes you need to split your source files into multiple Dataverse solutions.

## Step 5: Import solution to Dataverse

- Import it back to Dataverse

  - [Import solutions - Power Apps | Microsoft Learn](https://learn.microsoft.com/en-us/power-apps/maker/data-platform/import-update-export-solutions)
  - You can also use [pac solution import](https://learn.microsoft.com/en-us/power-platform/developer/cli/reference/solution#pac-solution-import) command
    - Note that after importing solution to Dataverse there is no way to remove it together with content. You can remove solution, but all inserted tables records will remain, they need to be cleaned up manually.
- [Publish your app on AppSource - Power Platform | Microsoft Learn](https://learn.microsoft.com/en-us/power-platform/developer/appsource/publish-app)
