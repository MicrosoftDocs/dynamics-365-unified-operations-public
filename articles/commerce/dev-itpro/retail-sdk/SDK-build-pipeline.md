---
# required metadata

title: Set up Commerce SDK build pipeline
description: This topic shows how to set up the Azure DevOps build pipeline for the Retail SDK.
author: mugunthanm 
manager: AnnBe
ms.date: 06/10/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations, Retail 
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: mumani
ms.search.validFrom: 2020-06-10
ms.dyn365.ops.version: 10.0.11
---

# Set up Commerce SDK build pipeline

[!include [banner](../../includes/banner.md)]

This topic shows how to set up the Azure DevOps build pipeline for the Retail SDK, by using the Azure DevOps build agent (a Microsoft-hosted agent). To generate the build for Retail SDK, a dedicated build machine isn't required. The setup works with the Azure DevOps build agent. This topic applies to Retail SDK version 10.0.11 or greater. 

## Prerequisites

The Retail SDK must be added to Azure Repos (Git repository), GitHub, or Azure DevOps. The Retail SDK is available in the service volume drive of the development virtual machine (VM) from Lifecycle Services (LCS). To provision a development VM in LCS, follow the steps in [Deploy and access development environments](../../../fin-ops-core/dev-itpro/dev-tools/access-instances.md).

## Set up a build pipeline in Azure DevOps

1. Sign in to your Azure DevOps organization.
2. Select **Pipeline** and click **New pipeline**.
3. Select your source repo.
4. Click the pipeline and provide a name for your pipeline. For **Agent pool**, choose **Azure Pipelines**. For **Agent Specification**, enter **vs2017-win2016**.

    :::image type="content" source="media/Step1.png" alt-text="Pipeline":::

5. On the **Get sources** tab, select your Retail SDK repo.

    :::image type="content" source="media/Step2.png" alt-text="Get sources":::
    
6. In the **Agent job** panel, provide a display name. For **Agent pool**, select **\<inherit from pipeline\>**.
    
    :::image type="content" source="media/Step3.png" alt-text="Hosted Agent":::

7. Add an MSBuild task. For **Project**, select **RetailSDK\\dirs.proj** or **RetailSDK\\Code\\dirs.proj**. The choice depends on how the Retail SDK is structured. Set **MSBuild Version** to **MSBuild 15.0**. Set **MSBuild Architecture** to **MsBuild x86**.

    :::image type="content" source="media/Step4.png" alt-text="MSBuild task":::

8.	Add a PowerShell task (**Run PowerShell script on Linux, macOS, or Windows**). Provide a name for the task. For **Type**, select **Inline**.

9.	In the **Script** section, copy and paste this script.

    ```Powershell
        # Script to copy the Retail deployable package with Build number.

        Copy-Item "$(Build.SourcesDirectory)\RetailSDK\Packages\RetailDeployablePackage\RetailDeployablePackage.zip" -Destination
        "$(Build.ArtifactStagingDirectory)\RetailDeployablePackage_$(Build.BuildNumber).zip"
    ```

    :::image type="content" source="media/Step5.png" alt-text="MSBuild task":::

10. Add a **Publish Artifact** task. Provide the **Display name** and **Artifact name** (drop name). Set the **Path to publish** to **$(Build.ArtifactStagingDirectory)**.

    :::image type="content" source="media/Step7.png" alt-text="Publish Artifact":::

10.	Save the changes and queue the build.

11.	When the build is complete, you can download the deployable package from the **Published Artifacts**.

    :::image type="content" source="media/Step8.png" alt-text="Download Artifact":::

## Sample YAML script for the pipeline

The following YAML script specifies the pipeline.

```YAML
pool:
  name: Azure Pipelines
  demands: msbuild

steps:
- task: MSBuild@1
  displayName: 'Build solution RetailSDK/Code/dirs.proj'
  inputs:
    solution: RetailSDK/Code/dirs.proj
    msbuildVersion: 15.0

- powershell: |
   # Script to copy the Retail deployable package with Build number.
   
   Copy-Item "$(Build.SourcesDirectory)\RetailSDK\Packages\RetailDeployablePackage\RetailDeployablePackage.zip" -Destination
   "$(Build.ArtifactStagingDirectory)\RetailDeployablePackage_$(Build.BuildNumber).zip"
   
  displayName: 'Copy the Retail deployable package'

- task: PublishBuildArtifacts@1
  displayName: 'Publish Artifact: drop'
```

## Set up an Azure DevOps build pipeline that uses a build machine

If the build machine uses MSBuild with the Azure DevOps pipeline, follow these steps in the build machine to enable it for the Retail SDK, version 10.0.11:

1. Install Visual Studio 2017 on the build machine.
2. Optional, run **msbuild** (version 15.0) from the developer command prompt for Visual Studio 2017 in the build machine. Open the developer command prompt for Visual Studio 2017, navigate to the Retail SDK root folder, and run `msbuild dirs.proj`. Make sure that the **msbuild** command finishes successfully.  
3. In the build machine add an environment variable for **msbuild**, version 15.0. Open **System Properties > Environment Variables > System variables**. Select **Path**, click **New**, and add the path variable for **msbuild**. An example of the path is 
**C:\\Program Files(x86)\\Microsoft Visual Studio\\2017\\Enterprise\\MSBuild\\15.0\\Bin\\**. The path depends on where you installed Visual Studio 2017. To get the path for **msbuild**, open the **Developer Command Prompt for Visual Studio 2017**, and run the command **where msbuild**. 
4. Restart the Azure DevOps build agent in the build machines.
5. In the Azure DevOps pipeline, set the **Agent Pool** to **Default** and change the msbuild version to 15.0 or latest.

## Troubleshooting

If the build from Azure DevOps fails with a NuGet error, check for these issues:

- The Azure pipeline isn't using **msbuild**, version 15.0, for NuGet restore.
- The extension projects haven't been upgraded to use the package reference model.

