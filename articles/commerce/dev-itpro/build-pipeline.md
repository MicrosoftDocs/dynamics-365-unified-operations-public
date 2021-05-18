---
title: Setup build pipeline for Commerce SDK to generate the Cloud scale unit and Self-service deployable packages.
description: This topic explains how to set up build pipeline for the commerce SDK to generate the deployable package for the extension code.
author: mugunthanm
ms.date: 05/17/2021
ms.topic: article
audience: Developer
ms.reviewer: rhaertle
ms.search.region: Global
ms.author: mumani
ms.search.validFrom: 05-17-2020
ms.dyn365.ops.version: AX 10.0.19
---

# Setup build pipeline for Commerce SDK

[!include [banner](../../../includes/banner.md)]

This topic applies to the Retail SDK version 10.0.19 and later, the steps documented here will not work if you are using the legacy Retail SDK from the LCS Dev VM, this applicable if you are using the new independent extension model (consuming the packages from the public feed) and using the indepednet packaging and extension model.

## Set up a build pipeline in Azure DevOps to generate Cloud Scale Unit extension package:

1. Sign in to your Azure DevOps organization.
2. Select Pipeline and click New pipeline.
3. Select your source repo.
4. Select Existing Azure Pipelines YAML file.
5. Select the YAML file available in /Pipeline/YAML_Files/build-pipeline.yml files [The YAML file are published in the Commerce ScaleUnit GitHub Repos](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/blob/release/9.29/Pipeline/YAML_Files/build-pipeline.yml)
6. Click Continue.
7. The YAML file has script to build the entire solution and upload the output CloudScaleUnitExtensionPackage.zip package to build Published Artifacts drop location.

>
> Note: The YAML file looks for a solution file in the repo and build the solution and look for output CloudScaleUnitExtensionPackage.zip, so please make sure your extension and packaging projects are linked to a solution, you can refer the samples in [ScaleUnit GitHub Repos](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/tree/release/9.29) on how you can model your extension projects.

## Setup a Release pipeline:

Follow the steps mentioned in the below docs to setup the release pipeline if you want to upload the CloudScaleUnitExtensionPackage.zip package to Lifecycle service Assets folder. 

- [Release pipelines.](https://docs.microsoft.com/en-us/azure/devops/pipelines/release/?view=azure-devops)
- [Upload assets by using Azure pipelines.](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/dev-tools/pipeline-asset-upload)

**In the LCS Asset Upload task choose:**

- **Type of asset** -  CloudScaleUnitExtensionPackage.
- **File to Upload** - $(System.DefaultWorkingDirectory)/_ScaleUnit-CI/drop/ScaleUnitPackage_$(Release.Artifacts._ScaleUnit-CI.BuildNumber).zip
- **LCS Asset Name** - ScaleUnitPackage_$(Release.Artifacts._ScaleUnit-CI.BuildNumber). The Asset name can be changed according to your naming guidelines. 

## Set up a build pipeline in Azure DevOps to generate  Retail self-service package:

The below steps guide on how you can generate the Retail Modern POS, hardware Station and Cloud Scale unit (self-hosted) installers:

1. Sign in to your Azure DevOps organization.
2. Select Pipeline and click New pipeline.
3. Select your source repo.
4. Select Existing Azure Pipelines YAML file.
5. Select the YAML file available in /Pipeline/YAML_Files/build-pipeline.yml files, the YAML file are published in the Commerce [Dynamics365Commerce.InStore GitHub Repos]( https://github.com/microsoft/Dynamics365Commerce.InStore/blob/release/9.29/Pipeline/YAML_Files/build-pipeline.yml)
6. Click Continue.
7. The YAML file has script to build the entire solution and upload the output CloudScaleUnitExtensionPackage.zip package to build Published Artifacts drop location.

>
> Note: The YAML file looks for a solution file in the repo and build the solution and look for output CloudScaleUnitExtensionPackage.zip, so please make sure your extension and packaging projects are linked to a solution, you can refer the samples in [Dynamics365Commerce.InStore GitHub Repos]( https://github.com/microsoft/Dynamics365Commerce.InStore/tree/release/9.29) on how you can model your extension projects.

## Setup a Release pipeline:

Follow the steps mentioned in the below docs to setup the release pipeline if you want to upload the CloudScaleUnitExtensionPackage.zip package to Lifecycle service Assets folder. 

- [Release pipelines.](https://docs.microsoft.com/en-us/azure/devops/pipelines/release/?view=azure-devops)
- [Upload assets by using Azure pipelines.](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/dev-tools/pipeline-asset-upload)

**In the LCS Asset Upload task choose:**

- **Type of asset** -  Retail Self-Service Package
- **File to Upload** - $(System.DefaultWorkingDirectory)/_CommerceSDK-Signing-EXE/drop/Installer_$(Release.Artifacts._CommerceSDK-Signing-EXE.BuildNumber).exe
- **LCS Asset Name** - Installer_$(Release.Artifacts._CommerceSDK-Signing-EXE.BuildNumber). 


