---
title: Set up a build pipeline for a fiscal integration sample
description: This article explains how to set up build and release pipelines for a fiscal integration sample from the Microsoft Dynamics 365 Commerce Retail software development kit (SDK) so that you can generate and release the Cloud Scale Unit and self-service deployable packages for the sample code.
author: josaw1
ms.date: 12/21/2021
ms.topic: article
audience: Developer
ms.reviewer: josaw
ms.search.region: global
ms.author: josaw
ms.search.validFrom: 
---

# Set up a build pipeline for a fiscal integration sample

[!include[banner](../includes/banner.md)]

This article explains how to set up build and release pipelines for a [fiscal integration sample](fiscal-integration-for-retail-channel.md#fiscal-registration-process-and-fiscal-integration-samples-for-fiscal-devices-and-services) from the Microsoft Dynamics 365 Commerce Retail software development kit (SDK). In this way, you can use the [independent packaging and extension model](../dev-itpro/build-pipeline.md) to generate and release the Cloud Scale Unit and self-service deployable packages for the sample code.

> [!NOTE]
> The steps that are described in this article won't work if you're using the previous version of the Retail SDK from the developer virtual machine (VM) in Microsoft Dynamics Lifecycle Services (LCS). For the steps that are required to deploy a fiscal integration sample if you're using the Retail SDK from the developer VM in LCS, see the corresponding fiscal integration sample documentation.

## Set up a build pipeline in Azure DevOps to generate Cloud Scale Unit extension packages and Retail self-service packages

1. Sign in to your Azure DevOps organization.
1. Select **Pipeline**, and then select **New pipeline**.
1. Select the source repository (repo) for fiscal integration solutions, [Dynamics365Commerce.Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions).
1. Select **Existing Azure Pipelines YAML file**.
1. Select or get an appropriate YAML file from the **Pipeline\\YAML_Files** folder of the [Dynamics365Commerce.Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions) repo. For more information about how to find a template YAML file for the sample, see the readme.md file of the fiscal integration solution or the public documentation for the fiscal integration sample.
1. Select **Continue**.

    The YAML file has steps for using a certificate to sign the Scale Unit, Modern POS, and Hardware Station extension installers. The script will look for a certificate file in Azure Key Vault and then use the certificate for signing. To read the certificate from Azure Key Vault, you must provide the application ID, secret, and certificate name. To sign the certificate by using a timestamp, you must also provide the timestamp server details. For more information, see [Set and retrieve a certificate from Azure Key Vault using the Azure portal](/azure/key-vault/certificates/quick-create-portal).

    To view the details of the key vault and the timestamp server in the pipeline, create the following variables on the **Variables** tab in your build pipeline, and provide values for them. To help secure the variables, you can select **Secret** as the variable type.

    - **ApplicationId**
    - **AzureKeyVaultURI**
    - **CertificateName**
    - **SecretValue**
    - **Timestamp** – As the value of this variable, you can specify any timestamp provider, such as `http://timestamp.digicert.com`.

    If you aren't storing your certificate in Azure, you can sign the installers by using the **Secure task** option or other options that Azure Pipelines supports.

    If you don't want to sign the installers, you can remove the signing step from the YAML file. In the YAML file, search for the **PowerShell\@2** task, and remove it.

    Scripts in the YAML file build the whole solution and upload the output files to the **Published Artifacts** drop location for the build. The output files are CloudScaleUnitExtensionPackage.zip and the following Retail self-service extension packages: HardwareStation.\*.Installer.exe, ScaleUnit.\*.Installer.exe, and ModernPOS.\*.Installer.exe.

    > [!NOTE]
    > In the names of the Retail self-service extension packages, the asterisk (\*) represents the name of the fiscal integration solution.
    >
    > Depending on the fiscal integration sample, extensions of some Commerce components may be not needed. Therefore, some of the output files might be omitted.

1. Save your changes, and add the build to the queue.
1. When the build is completed, you can download the packages from **Published Artifacts**:

    - **Cloud scale unit package:**

        - ScaleUnitPackage_$(BuildNumber).zip

    - **Retail self-service extension packages:**

        - HardwareStation.\*.Installer_$(BuildNumber).exe
        - ScaleUnit.\*.Installer_$(BuildNumber).exe
        - ModernPOS.\*.Installer_$(BuildNumber).exe

        In these package names, the asterisk (**\***) represents the name of the fiscal integration solution.

## Set up a release pipeline for the Cloud Scale Unit extension package

To set up a release pipeline for the Cloud Scale Unit extension package for the fiscal integration sample, follow the steps in [Set up a release pipeline for the Cloud Scale Unit extension package](../dev-itpro/build-pipeline.md#set-up-a-release-pipeline-for-the-cloud-scale-unit-extension-package).

## Set up a release pipeline for Retail self-service packages

To set up a release pipeline for Retail self-service packages for the fiscal integration sample, follow the steps in [Set up a release pipeline for Commerce self-service packages](../../commerce/dev-itpro/build-pipeline.md#set-up-a-release-pipeline-for-commerce-self-service-packages).
