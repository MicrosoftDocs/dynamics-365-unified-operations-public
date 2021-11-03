---
title: Set up a build pipeline for a fiscal integration sample
description: This topic explains how to set up build and release pipelines for a fiscal integration sample so that you can generate and release the Cloud Scale Unit and self-service deployable packages for the sample code.
author: Sergio1C
ms.date: 11/03/2021
ms.topic: article
audience: Developer
ms.reviewer: josaw
ms.search.region: global
ms.author: v-seskry
ms.search.industry: Retail
ms.search.validFrom:
ms.dyn365.ops.version:
---

# Set up a build pipeline for a fiscal integration sample

[!include[banner](../includes/banner.md)]

This topic explains how to set up build and release pipelines for a [fiscal integration sample](fiscal-integration-for-retail-channel.md#fiscal-registration-process-and-fiscal-integration-samples-for-fiscal-devices) from the Retail software development kit (SDK) so that you can generate and release the Cloud Scale Unit and self-service deployable packages for this fiscal integration sample extension code (by using the [new independent packaging and extension model](../dev-itpro/build-pipeline.md)).

> [!NOTE]
> The steps that are described in this topic won't work if you're using the previous version of the Retail SDK from the developer virtual machine (VM) in Microsoft Dynamics Lifecycle Services (LCS). For the steps that are required to deploy a fiscal integration sample from the Retail SDK from the developer VM in LCS, see the corresponding fiscal integration sample documentation.

## Set up a build pipeline in Azure DevOps to generate Cloud Scale Unit extension packages and Retail Self-service packages

1. Sign in to your Microsoft Azure DevOps organization.
2. Select **Pipeline**, and then select **New pipeline**.
3. Select the source repository (repo) for fiscal integration solutions: [Dynamics365Commerce.Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions).
4. Select **Existing Azure Pipelines YAML file**.
5. Select or get an appropriate YAML file from the **Pipeline\\YAML_Files** folder of the [Dynamics365Commerce.Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions) repo. See the readme.md file of the fiscal integration solution or the public documentation for the fiscal integration sample for more information on how to find a template YAML file for the sample.
6. Select **Continue**.

    The YAML file has steps to sign the Scale Unit, Modern POS, and Hardware Station extension installers by using a certificate. The script will look for a certificate file in Azure Key Vault and use that certificate file for signing. To read the certificate from Azure Key Vault, you must provide the application ID, secret, certificate name, and timestamp server details (for signing the certificate by using a timestamp). For more information, see [Set and retrieve a certificate from Azure Key Vault using the Azure portal](/azure/key-vault/certificates/quick-create-portal).

    To view the details of the key vault and the timestamp server in the pipeline, create the following variables on the **Variables** tab in your build pipeline, and provide values for them. To help secure the variables, you can select **Secret** as the variable type.

    - ApplicationId
    - AzureKeyVaultURI
    - CertificateName
    - SecretValue
    - Timestamp

        You can specify any timestamp provider as the value of this variable, such as `http://timestamp.digicert.com`.

    If you aren't storing your certificate in Azure, you can sign the installers by using the **Secure task** option or other options that Azure Pipelines supports.

    If you don't want to sign the installers, you can remove the signing step from the YAML file. In the YAML file, search for the **PowerShell\@2** task, and remove it.

    Scripts in the YAML file build the whole solution and upload the output files (the CloudScaleUnitExtensionPackage.zip and Retail self-service extension packages: HardwareStation.\*.Installer.exe, ScaleUnit.\*.Installer.exe, ModernPOS.\*.Installer.exe) to the **Published Artifacts** drop location for the build.

    > [!NOTE]
    > A fiscal integration sample may not include extensions of some components. Therefore, depending on the sample, some of the output files may be omitted.

7. Save your changes, and add the build to the queue.
8. When the build is completed, you can download the packages from **Published Artifacts**:

    - Cloud scale unit package:
        - ScaleUnitPackage_$(BuildNumber).zip

    - Retail self-service extension packages:
         - HardwareStation.\*.Installer_$(BuildNumber).exe
         - ScaleUnit.\*.Installer_$(BuildNumber).exe
         - ModernPOS.\*.Installer_$(BuildNumber).exe
         
         where the asterisk (**\***) stands for the name of the fiscal integration solution.

## Set up a release pipeline for the Cloud Scale Unit extension package

Follow the steps described in [Set up a release pipeline for the Cloud Scale Unit extension package](../dev-itpro/build-pipeline.md#set-up-a-release-pipeline-for-the-cloud-scale-unit-extension-package) to set up a release pipeline for the Cloud Scale Unit extension package for the fiscal integration sample.

## Set up a release pipeline for Retail self-service packages

Follow the steps described in [Set up a release pipeline for Retail self-service packages](../../commerce/dev-itpro/build-pipeline.md#set-up-a-release-pipeline-for-retail-self-service-packages) to set up a release pipeline for Retail self-service packages for the fiscal integration sample.
