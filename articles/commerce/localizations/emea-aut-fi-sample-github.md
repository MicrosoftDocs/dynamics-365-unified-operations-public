---

# required metadata

title: Deployment guidelines for the fiscal integration sample for Austria from GitHub
description: This topic provides guidance about how to deploy the fiscal integration sample for Austria from GitHub
author: josaw
ms.date: 10/28/2021
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang:
ms.reviewer: josaw
# ms.tgt_pltfrm:
# ms.custom:
ms.search.region: Austria
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2019-3-1
ms.dyn365.ops.version: 10.0.1

---

# Deploying the fiscal integration sample for Austria from GitHub

This 

The sample's code can be found in repository [microsoft/Dynamics365Commerce.Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions).

This sample consists of extensions for the CRT, Hardware station, and POS. To run this sample, you must beforehand install the sealed version of Commerce Scale Unit, Hardware station and POS. After installing these retail components, you should build the EFR solution and run installers for each component. We recommend that you use an unmodified solution files from this repository to make the changes that are described in this topic. We also recommend that you use a source control system, such as Azure DevOps, where no files have been changed yet.

## Development environment

Follow these steps to set up a development environment so that you can test and extend the sample.

The CRT extension components are included in the EFR solution from Fiscal Integration folder. To complete the following procedures, open the EFR solution, **Efr.sln**, under **Dynamics365Commerce.Solutions\\FiscalIntegration\\Efr**.

### Install Commerce runtime extensions

1. Find the **EFR** solution and build it.

2. Build the CRT extension installer:

    - **Commerce Scale Unit:** In the **Efr\\ScaleUnit\\ScaleUnit.EFR.Installer\\bin\\Debug\\net461** folder, find the **ScaleUnit.EFR.Installer** installer.
    - **Local CRT on Modern POS:** In the **Efr\\ModernPOS\\ModernPOS.EFR.Installer\\bin\\Debug\\net461** folder, find the **ModernPOS.EFR.Installer** installer.

3. Start the extension installer from command line as follows:

    - **Commerce Scale Unit:**

    ```Console
    ScaleUnit.EFR.Installer.exe install --verbosity 0
    ```

    - **Local CRT on Modern POS:**

    ```Console
    ModernPOS.EFR.Installer.exe install --verbosity 0
    ```

### Install Hardware station extensions

The Hardware station extension components are included in the EFR solution from Fiscal Integration folder. To complete the following procedures, open the EFR solution, **EFR.sln**, under **Dynamics365Commerce.Solutions\\FiscalIntegration\\Efr**.

#### EFRSample component

1. Find the **EFR** solution and build it.

2. In the **Efr\\HardwareStation\\HardwareStation.EFR.Installer\\bin\\Debug\\net461** folder, find the **HardwareStation.EFR.Installer** installer.

3. Start the extension installer from command line as follows:

    ```Console
    HardwareStation.EFR.Installer.exe install --verbosity 0
    ```

## Production environment

The previous procedure enables the extensions that are components of the fiscal registration service integration sample. In addition, you must follow these steps to create deployable packages that contain Commerce components, and to apply those packages in a production environment.

### Commerce Cloud Scale Unit (CSU) package

The steps to generate Commerce Cloud Scale Unit (CSU) package are following:

1. Clone or download the [microsoft/Dynamics365Commerce.Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions).

Select the correct release branch version according to your SDK/application release. Detailed steps to clone can be in [Download Retail SDK samples and reference packages from GitHub and NuGet](../dev-itpro/retail-sdk/sdk-github.md).

2. Build the project **ScaleUnit.EFR** under **Dynamics365Commerce.Solutions\\FiscalIntegration\\Efr\\ScaleUnit**. This project will generate the **CloudScaleUnitExtensionPackage.zip** output package in the project bin output folder. CloudScaleUnitExtensionPackage.zip package can be uploaded to LCS and deployed to CSU.

Select the correct version of the **Microsoft.Dynamics.Commerce.Sdk.ScaleUnit** NuGet version in the NuGet package manager in Visual Studio according to your SDK/application version.

To upload the created **CloudScaleUnitExtensionPackage.zip** package to LCS see [Deploy the package to CSU](../dev-itpro/retail-sdk/retail-sdk-packaging.md#deploy-the-package-to-csu).

### Commerce Scale Unit (self-hosted) components

1. Download the Commerce Scale Unit, Hardware station, Modern POS component installers and install each one as prerequisites. For more information about sealed self-service installers, see [Mass deployment of sealed Commerce self-service components](../dev-itpro/Enhanced-Mass-Deployment.md).

2. Start the extension installer from command line

- For **Commerce Scale Unit:** under **Dynamics365Commerce.Solutions\\FiscalIntegration\\Efr\\ScaleUnit\\ScaleUnit.EFR.Installer\\bin\\Debug\\net461** path

    ```Console
    ScaleUnit.EFR.Installer.exe install --verbosity 0
    ```

- For **Local CRT on Modern POS:** under **Dynamics365Commerce.Solutions\\FiscalIntegration\\Efr\\ModernPOS\\ModernPOS.EFR.Installer\\bin\\Debug\\net461** path

    ```Console
    ModernPOS.EFR.Installer.exe install --verbosity 0
    ```

- For **Hardware station** under **Dynamics365Commerce.Solutions\\FiscalIntegration\\Efr\\HardwareStation\\HardwareStation.EFR.Installer\\bin\\Debug\\net461** path

    ```Console
    HardwareStation.EFR.Installer.exe install --verbosity 0
    ```
