---
title: Set up a build pipeline for the independent-packaging SDK
description: This article explains how to set up a build pipeline for the Retail software development kit (SDK) so that you can generate the Cloud Scale Unit and self-service deployable packages for extension code.
author: josaw1
ms.date: 05/17/2021
ms.topic: article
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2020-05-17
ms.dyn365.ops.version: AX 10.0.19
---

# Set up a build pipeline for the independent-packaging SDK

[!include [banner](../../includes/banner.md)]

This article explains how to set up a build pipeline for the Retail software development kit (SDK) so that you can generate the Cloud Scale Unit and self-service deployable packages for extension code (by using the new independent extension model).

This article applies to version 10.0.19 and later of the Retail SDK. The steps that are described in this article won't work if you're using the previous version of the Retail SDK from the developer virtual machine (VM) in Microsoft Dynamics Lifecycle Services (LCS). The information in this article is applicable if you're using the new independent extension model (that is, if you're consuming the packages from the public feed), and the independent packaging and extension model.

## Set up a build pipeline in Azure DevOps to generate a Cloud Scale Unit extension package

1. Sign in to your Microsoft Azure DevOps organization.
2. Select **Pipeline**, and then select **New pipeline**.
3. Select the source repository (repo) for your extension code.
4. Select **Existing Azure Pipelines YAML file**.
5. Select or get the [build-pipeline.yml file](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/blob/release/9.29/Pipeline/YAML_Files/build-pipeline.yml) from the [Dynamics365Commerce.ScaleUnit](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/tree/release/9.29) GitHub repo.

    > [!NOTE]
    > The YAML file refers to some scripts in the [Pipeline/PowerShellScripts directory in the Dynamics365Commerce.ScaleUnit GitHub repo](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/tree/release/9.29/Pipeline/PowerShellScripts). Be sure to include all those scripts in your repo. If you clone the samples repo, all the scripts are already included.

6. Select **Continue**.

    Scripts in the YAML file build the whole solution and upload the output (the CloudScaleUnitExtensionPackage.zip package) to the **Published Artifacts** drop location for the build.

    > [!NOTE]
    > The YAML file looks for a solution file in the repo, builds the solution, and then looks for the CloudScaleUnitExtensionPackage.zip package. Therefore, make sure that your extension and packaging projects are linked to a solution. For information about how to model your extension projects, see the samples in the [Dynamics365Commerce.ScaleUnit GitHub repo](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/tree/release/9.29).

7. Save your changes, and add the build to the queue.
8. When the build is completed, you can download the **ScaleUnitPackage_(Build.BuildNumber).zip** package from **Published Artifacts**.

## Set up a release pipeline for the Cloud Scale Unit extension package

As a best practice, you should set up separate build and release pipelines. If you create a separate release pipeline, you can use the **Upload Asset** task in LCS to upload the CloudScaleUnitExtensionPackage.zip package to the Asset library. If you want to upload to LCS instead of to a separate release pipeline, you can add the task as part of your build pipeline.

Follow these steps to set up the release pipeline to upload the CloudScaleUnitExtensionPackage.zip package to the Asset library in LCS.

1. In Azure DevOps, select **Releases**, select **New pipeline**, and then select **Empty job in the template**.
2. Enter a name for the new release pipeline. The default name is **App Pipelines \> New release pipeline**.
3. In the pipeline, select **Add an artifact**.
4. In the **Add artifact** dialog box, select your project, and then select the build pipeline that you created in the previous section.
5. Optional: In the artifact that you just created, you can select the **Trigger** button (lightning bolt symbol), enable a continuous deployment trigger, and then select your branch, and so on.

    > [!NOTE]
    > The release pipeline also offers other options that let you specify how and when the release is triggered.

6. Select **Save** to save your pipeline. If you're prompted for a folder name, enter any folder name.
7. Select **Stages**, rename stage 1 **Upload Assets to LCS**, and then select **1 Job**.
8. In **Tasks**, select **Agent job**.
9. In **Add tasks**, search for **Dynamics Lifecycle Services (LCS) Asset Upload**, and select **Add**.
10. Set up the upload task by following the steps in [Upload assets by using Azure Pipelines](../../fin-ops-core/dev-itpro/dev-tools/pipeline-asset-upload.md). In the task, set the following values:

    - **Type of asset:** CloudScaleUnitExtensionPackage
    - **File to Upload:** $(System.DefaultWorkingDirectory)/\_ScaleUnit-CI/drop/ScaleUnitPackage\_$(Release.Artifacts.\_ScaleUnit-CI.BuildNumber).zip
    - **LCS Asset Name:** ScaleUnitPackage\_$(Release.Artifacts.\_ScaleUnit-CI.BuildNumber)

        > [!NOTE]
        > You can change the asset name according to your naming guidelines.

11. After you've finished configuring tasks, select **Save** to save the release pipeline.
12. On the **Pipelines** tab, select your pipeline, and then select **Create release**.
13. In the **Create a new release** dialog box, select the Cloud Scale Unit artifact, and then select **Create** to manually trigger the release.

To automate the release pipeline, configure continuous build. For more information, see the [Release pipelines](/azure/devops/pipelines/release) documentation.

## Set up a build pipeline in Azure DevOps to generate Retail self-service packages

Follow these steps to generate the Retail Modern POS, Hardware Station, and Cloud Scale Unit (self-hosted) installers.

1. Sign in to your Azure DevOps organization.
2. Select **Pipeline**, and then select **New pipeline**.
3. Select your source repo.
4. Select **Existing Azure Pipelines YAML file**.
5. Select the [YAML file (build-pipeline.yml) from the Pipeline/YAML\_Files directory in the Dynamics365Commerce.InStore GitHub repo](https://github.com/microsoft/Dynamics365Commerce.InStore/blob/release/9.29/Pipeline/YAML_Files/build-pipeline.yml).

    > [!NOTE]
    > The YAML file refers to some scripts in the [Pipeline/PowerShellScripts directory in the Dynamics365Commerce.InStore GitHub repo](https://github.com/microsoft/Dynamics365Commerce.InStore/tree/release/9.29/Pipeline/PowerShellScripts). Be sure to include all those scripts in your repo. If you clone the samples repo, all the scripts are already included.

6. Select **Continue**.

    The YAML file has steps to sign the Modern POS and Hardware Station installers by using a certificate. The script will look for a certificate file in Azure Key Vault and use that certificate file for signing. To read the certificate from Azure Key Vault, you must provide the application ID, secret, certificate name, and timestamp server details (for signing the certificate by using a timestamp). For more information, see [Set and retrieve a certificate from Azure Key Vault using the Azure portal](/azure/key-vault/certificates/quick-create-portal).

    To view the details of the key vault and the timestamp server in the pipeline, create the following variables on the **Variables** tab in your build pipeline, and provide values for them. To help secure the variables, you can select **Secret** as the variable type.

    - ApplicationId
    - AzureKeyVaultURI
    - CertificateName
    - SecretValue
    - Timestamp

        You can specify any timestamp provider as the value of this variable, such as `http://timestamp.digicert.com`.

    If you aren't storing your certificate in Azure, you can sign the installers by using the **Secure task** option or other options that Azure Pipelines supports.

    If you don't want to sign the installers, you can remove the signing step from the YAML file. In the YAML file, search for the **PowerShell\@2** task, and remove it.

    Scripts in the YAML file build the whole solution and upload the output (the HardwareStation.Installer.exe and ModernPos.Installer.exe packages) to the **Published Artifacts** drop location for the build.

    > [!NOTE]
    > The YAML file looks for a solution file in the repo, builds the solution, and then looks for the HardwareStation.Installer.exe and ModernPos.Installer.exe packages. Therefore, make sure that your extension and packaging projects are linked to a solution. For information about how to model your extension projects, see the samples in the [Dynamics365Commerce.InStore GitHub repo](https://github.com/microsoft/Dynamics365Commerce.InStore/tree/release/9.29).

7. Save your changes, and add the build to the queue.
8. When the build is completed, you can download the **HardwareStation.Installer.exe** and **ModernPos.Installer.exe** packages from **Published Artifacts**.

## Set up a release pipeline for Retail self-service packages

As a best practice, you should set up separate build and release pipeline. If you create a separate release pipeline, you can use the **Upload Asset** task in LCS to upload the HardwareStation.Installer.exe and ModernPos.Installer.exe packages to the Asset library. If you want to upload to LCS instead of to a separate release pipeline, you can add the task as part of your build pipeline.

Follow these steps to set up the release pipeline to upload the HardwareStation.Installer.exe and ModernPos.Installer.exe packages to the Asset library in LCS.

1. In Azure DevOps, select **Releases**, select **New pipeline**, and then select **Empty job in the template**.
2. Enter a name for the new release pipeline. The default name is **App Pipelines \> New release pipeline**.
3. In the pipeline, select **Add an artifact**.
4. In the **Add artifact** dialog box, select your repo project, and then select the build pipeline that you created in the previous section.
5. Optional: In the artifact that you just created, you can select the **Trigger** button (lightning bolt symbol), enable a continuous deployment trigger, and then select your branch, and so on.

    > [!NOTE]
    > The release pipeline also offers other options that let you specify how and when the release is triggered.

6. Select **Save** to save your pipeline. If you're prompted for a folder name, enter any folder name.
7. Select **Stages**, rename stage 1 **Upload Assets to LCS**, and then select **1 Job**.
8. In **Tasks**, select **Agent job**.
9. In **Add tasks**, search for **Dynamics Lifecycle Services (LCS) Asset Upload**, and select **Add**.
10. Fully set up the upload task by following the steps in [Upload assets by using Azure Pipelines](../../fin-ops-core/dev-itpro/dev-tools/pipeline-asset-upload.md). In the task, set the following values:

    - **Type of asset:** Retail Self-Service Package
    - **File to Upload:** $(System.DefaultWorkingDirectory)/\_CommerceSDK-Signing-EXE/drop/Installer\_$(Release.Artifacts.\_CommerceSDK-Signing-EXE.BuildNumber).exe
    - **LCS Asset Name:** Installer\_$(Release.Artifacts.\_CommerceSDK-Signing-EXE.BuildNumber)

11. After you've finished configuring tasks, select **Save** to save the release pipeline.
12. On the **Pipelines** tab, select your pipeline, and then select **Create release**.
13. In the **Create a new release** dialog box, select the artifact, and then select **Create** to manually trigger the release.

To automate the release pipeline, configure continuous build. For more information, see the [Release pipelines](/azure/devops/pipelines/release) documentation.
