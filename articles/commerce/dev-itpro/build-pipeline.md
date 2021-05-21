---
title: Setup build pipeline for Commerce SDK to generate the Cloud scale unit and Self-service deployable packages (new independent extension model) .
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

This topic applies to Retail SDK version 10.0.19 and later, the steps documented here will not work if you are using the previous version of Retail SDK from the LCS Dev VM, this applicable if you are using the new independent extension model (consuming the packages from the public feed) and using the independent packaging and extension model.

## Set up a build pipeline in Azure DevOps to generate Cloud Scale Unit extension package:

1. Sign in to your Azure DevOps organization.
2. Select Pipeline and click New pipeline.
3. Select your extension code source repo.
4. Select Existing Azure Pipelines YAML file.
5. Select/Get the YAML file from /Pipeline/YAML_Files/build-pipeline.yml files [The YAML file are published in the Dynamics365Commerce.ScaleUnit GitHub repo](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/blob/release/9.29/Pipeline/YAML_Files/build-pipeline.yml)

The YAML files refers few other script from the [Dynamics365Commerce.ScaleUnit repo](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit), please include all those scripts in your repo, if you are cloning the samples repo then all the scripts are already included.

All the reference scripts are available in the [Dynamics365Commerce.ScaleUnit GitHub repo.](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/tree/release/9.29/Pipeline/PowerShellScripts)

7. Click Continue.
8. The YAML file has script to build the entire solution and upload the output CloudScaleUnitExtensionPackage.zip package to build Published Artifacts drop location.

>
> Note: The YAML file looks for a solution file in the repo and build the solution and look for output CloudScaleUnitExtensionPackage.zip, so please make sure your extension and packaging projects are linked to a solution, you can refer the samples in [Dynamics365Commerce.ScaleUnit GitHub Repo](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/tree/release/9.29) on how to model your extension projects.

9. Save the changes and queue the build.
10. When the build is complete, you can download the CloudScaleUnitExtensionPackage.zip package from the Published Artifacts.


## Setup a Release pipeline:

It’s a best practice to setup separate pipeline for build and release, you can create a separate release pipeline and use the LCS Upload Asset task to upload the CloudScaleUnitExtensionPackage.zip to LCS Asset library, you can also add the task part of our build pipeline to upload to LCS instead of separate release pipeline.

**Follow the below steps to setup the release pipeline to upload the CloudScaleUnitExtensionPackage.zip package to Lifecycle service Assets folder:**

1. Click Releases in the Azure DevOps and click New pipeline and Select Empty job in the template.
2. Provide a name for your Release pipeline, by default it will be App Pipelines > New release pipeline.
3. In the Pipeline, Click on the + Add an artifact, in the Add  artifact dialog, select your Project, then select the build pipeline you created in the Setup build pipeline section.
4. You can click the Thunder bolt/Trigger icon in the Artifact you created in the previous step and enable continuous deployment trigger and choose your branch etc., this step is optional, the Release pipeline provides different options for how/when you want to trigger the release.
5. Click Save to save your pipeline, it may ask for a folder name, provide any folder name.
6. Click the Stages and rename the Stage 1 to Upload Assets to LCS and Click the 1 Job.
7. In the Tasks, click the Agent job. In the Add tasks, search for Dynamics Lifecycle Services (LCS) Asset Upload and click Add.

Follow the Steps mentioned in the [Upload assets to LCS by using Azure pipelines.](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/dev-tools/pipeline-asset-upload) doc to Setup the Upload task.

**In the LCS Asset Upload task select:**

- **Type of asset** -  CloudScaleUnitExtensionPackage.
- **File to Upload** - $(System.DefaultWorkingDirectory)/_ScaleUnit-CI/drop/ScaleUnitPackage_$(Release.Artifacts._ScaleUnit-CI.BuildNumber).zip
- **LCS Asset Name** - ScaleUnitPackage_$(Release.Artifacts._ScaleUnit-CI.BuildNumber). The Asset name can be changed according to your naming guidelines. 

8. Once the Tasks configuration completed, click Save to save the release pipeline.
9. Click the Pipelines tab, select your pipeline and click Create release and in the Create a new release dialog, select the Scale unit artifact and Click Create, this will manually trigger the Release.

To automate the release pipeline, configure continuous build follow the [Release pipelines](https://docs.microsoft.com/en-us/azure/devops/pipelines/release/?view=azure-devops) documentation for more information.

## Set up a build pipeline in Azure DevOps to generate Retail self-service packages:

The below steps guide on how you can generate the Retail Modern POS, hardware Station and Cloud Scale unit (self-hosted) installers:

1. Sign in to your Azure DevOps organization.
2. Select Pipeline and click New pipeline.
3. Select your source repo.
4. Select Existing Azure Pipelines YAML file.
5. Select the YAML file available in /Pipeline/YAML_Files/build-pipeline.yml files, the YAML file are published in the [Dynamics365Commerce.InStore GitHub repo]( https://github.com/microsoft/Dynamics365Commerce.InStore/blob/release/9.29/Pipeline/YAML_Files/build-pipeline.yml)

The YAML files refers few other script from the [Dynamics365Commerce.InStore repo](https://github.com/microsoft/Dynamics365Commerce.InStore), please include those scripts in your repo, if you are cloning the samples repo then all the scripts are already included.

All the reference scripts are available in the [Dynamics365Commerce.ScaleUnit GitHub repo.](https://github.com/microsoft/Dynamics365Commerce.InStore/tree/release/9.29/Pipeline/PowerShellScripts)

7. Click Continue.
8. The YAML file has steps to sign the Modern POS and Hardware station installer using a certificate, the script will look for a certificate file in the Azure key Vault and use that for signing. To read the certificate from Azure key Vault you need to provide application id, secret, Certificate name and Timestamp server details (signing the certificate with timestamp). 

Refer [How to set and retrieve a certificate from Azure Key Vault using the Azure portal](https://docs.microsoft.com/en-us/azure/key-vault/certificates/quick-create-portal) for more information.

To read the Azure key Vault and timestamp server details in the pipeline, create the below variables in your build pipeline by clicking the Variables tab and provide values for the variables, you can choose the variables type to Secret if you want to secure it.
  
- ApplicationId
- AzureKeyVaultURI
- CertificateName
- SecretValue
- Timestamp
 
 For the timestamp, you can choose any timestamp provider. Ex: http://timestamp.digicert.com
 
If you are not storing your certificate in Azure, you can use other options like Secure task or some other Azure DevOps pipeline supported options to sign the installers. If you don’t want to sign the installers you can remove the sign step from the YAML file, search for task: PowerShell@2 in the YAMl file and remove it.

9. The YAML file has script to build the entire solution and upload the output HardwareStation.Installer.exe and ModernPos.Installer.exe package to build Published Artifacts drop location.

>
> Note: The YAML file looks for a solution file in the repo and build the solution and look for output HardwareStation.Installer.exe and ModernPos.Installer.exe, so please make sure your extension and packaging projects are linked to a solution, you can refer the samples in [Dynamics365Commerce.InStore GitHub repo]( https://github.com/microsoft/Dynamics365Commerce.InStore/tree/release/9.29) on how to model your extension projects.

10. Save the changes and queue the build.
11. When the build is complete, you can download the CloudScaleUnitExtensionPackage.zip package from the Published Artifacts.


## Setup a Release pipeline:

Its best practice to setup separate pipeline for build and release, you can create a separate release pipeline and use the LCS Upload Asset task to upload the HardwareStation.Installer.exe and ModernPos.Installer.exe to LCS Asset library, you can also add the task part of our build pipeline to upload instead of separate release pipeline.

Follow the below steps to setup the release pipeline to upload the HardwareStation.Installer.exe and ModernPos.Installer.exe to Lifecycle service Assets folder:

1. Click Releases in the Azure DevOps and click New pipeline and Select Empty job in the template.
2. Provide a name for your Release pipeline, by default it will be App Pipelines > New release pipeline.
3. In the Pipeline, Click on the + Add an artifact, in the Add  artifact dialog, select your repo Project, then select the build pipeline you created in the setup build pipeline section.
4. You can click the Thunder bolt icon in the Artifact you created in the previous step and enable continuous deployment trigger and choose your branch etc., this step is optional, the Release pipeline provides different options for how/when you want to release the package.
5. Click Save to Save your pipeline, it may ask for a folder name, provide any folder name.
6. Click the Stages and rename the Stage 1 to Upload Assets to LCS and Click the 1 Job.
7. In the Tasks, click the Agent job. In the Add tasks, search for Dynamics Lifecycle Services (LCS) Asset Upload and click Add.

Follow the Steps mentioned in the [Upload assets to LCS by using Azure pipelines.](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/dev-tools/pipeline-asset-upload) doc to fully Setup the Upload task.


**In the LCS Asset Upload task select:**

- **Type of asset** -  Retail Self-Service Package
- **File to Upload** - $(System.DefaultWorkingDirectory)/_CommerceSDK-Signing-EXE/drop/Installer_$(Release.Artifacts._CommerceSDK-Signing-EXE.BuildNumber).exe
- **LCS Asset Name** - Installer_$(Release.Artifacts._CommerceSDK-Signing-EXE.BuildNumber).

8. Once the Tasks configuration completed, click Save to save the release pipeline.
9. Click the Pipelines tab, select your pipeline and click Create release and in the Create a new release dialog, select the artifact and Click Create, this will manually trigger the Release.

To automate the release pipeline, configure continuous build follow the [Release pipelines](https://docs.microsoft.com/en-us/azure/devops/pipelines/release/?view=azure-devops) documentation for more information.
