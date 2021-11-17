---
# required metadata

title: Deployment guidelines for cash registers for Norway
description: This topic provides guidance about how to enable the cash register functionality for the Microsoft Dynamics 365 Commerce localization for Norway.
author: 
manager: 
ms.date: 
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Norway
ms.search.industry: Retail
ms.author: 
ms.search.validFrom: 
ms.dyn365.ops.version: 

---
# Deployment guidelines for cash registers for Norway

[!include [banner](../includes/banner.md)]

This topic provides guidance about how to enable the cash register functionality for the Microsoft Dynamics 365 Commerce localization for Norway. The localization consists of several extensions of components. These extensions let you perform actions such as printing custom fields on receipts, registering additional audit events, sales transactions, and payment transactions in Point of Sale (POS), digitally signing sales transactions, and printing X and Z reports in local formats. For more information about the localization for Norway, see [Cash register functionality for Norway](./emea-nor-cash-registers.md). For more information about how to configure Commerce for Norway, see [Set up Commerce for Norway](./emea-nor-cash-registers.md#setting-up-commerce-for-Norway).

> [!NOTE]
> This version of the Commerce cash register functionality for Norway is based on the [fiscal integration framework](./fiscal-integration-for-retail-channel.md). For information about the legacy digital signing sample for Norway, see [Deployment guidelines for cash registers for Norway (legacy)](./emea-nor-loc-deployment-guidelines.md). For guidelines about how to enable the fiscal integration functionality for Norway in existing environments that use the legacy digital signing sample, see [Migrate from legacy Commerce functionality for Norway](./emea-nor-fi-migration.md).

## Configure channel components

> [!WARNING]
> Because of limitations of the [new independent packaging and extension model](../dev-itpro/build-pipeline.md), it can't currently be used for this fiscal integration sample. You must use the previous version of the Retail SDK on a developer VM in LCS. See [Deployment guidelines for cash registers for Norway (legacy)](emea-nor-loc-deployment-guidelines.md) for more details.
>
> Supporting the new independent packaging and extension model for fiscal integration samples is planned for later versions.

### Development environment

Follow these steps to set up a development environment so that you can test and extend the sample:

1. Clone or download the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions) repository. Select a correct release branch version according to your SDK/application version. For more details, see [Download Retail SDK samples and reference packages from GitHub and NuGet](../dev-itpro/retail-sdk/sdk-github.md).
2. Open the SequentialSignatureNorway solution at **Dynamics365Commerce.Solutions\\FiscalIntegration\\SequentialSignatureNorway\\SequentialSignatureNorway.sln**, and build it.
3. Install Commerce runtime extensions:
    - Find the CRT extension installer:
        - **Commerce Scale Unit:** In the **SequentialSignatureNorway\\ScaleUnit\\ScaleUnit.SequentialSignNorway.Installer\\bin\\Debug\\net461** folder, find the **ScaleUnit.SequentialSignNorway.Installer** installer.
        - **Local CRT on Modern POS:** In the **SequentialSignatureNorway\\ModernPOS\\ModernPos.SequentialSignNorway.Installer\\bin\\Debug\\net461** folder, find the **ModernPos.SequentialSignNorway.Installer** installer.
    - Start the CRT extension installer from command line as follows:
        - **Commerce Scale Unit:**
        ```Console
        ScaleUnit.SequentialSignNorway.Installer.exe install --verbosity 0
        ```
        - **Local CRT on Modern POS:**
        ```Console
        ModernPOS.SequentialSignNorway.Installer.exe install --verbosity 0
        ```

### Production environment

Follow the steps described in [Set up a build pipeline for a fiscal integration sample](fiscal-integration-sample-build-pipeline.md) to generate and release the Cloud Scale Unit and self-service deployable packages for the fiscal integration sample. The template YAML file **SequentialSignatureNorway build-pipeline.yaml** can be found in the **Pipeline\\YAML_Files** folder of the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions) repository.

> [!WARNING]
> After you complete the preceding steps, your previous customizations of the digital signing functionality will stop working.

## Enable the digital signature in offline mode for Modern POS

To enable the digital signature in offline mode for Modern POS, you must follow these steps after you activate Modern POS on a new device.

1. Sign in to POS.
1. On the **Database connection status** page, ensure that the offline database is fully synchronized. When the value of the **Pending downloads** field is **0** (zero), the database is fully synchronized.
1. Sign out of POS.
1. Wait for the offline database to be fully synchronized.
1. Sign in to POS.
1. On the **Database connection status** page, ensure that the offline database is fully synchronized. When the value of the **Pending transactions in offline database** field is **0** (zero), the database is fully synchronized.
1. Restart Modern POS.
