---
title: Independent software vendor (ISV) licensing (on-premises)
description: Learn about the independent software vendor (ISV) licensing feature for on-premises environments, including outlines on generating license files and automated imports.
author: faix
ms.author: osfaixat
ms.date: 03/30/2026
ms.topic: how-to
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2018-03-07
ms.dyn365.ops.version: AX 7.3.0
ms.assetid: 90ae4ae6-f19a-4ea5-8bd9-1d45729b0636
search.app:
  - financeandoperationsonprem-docs
ms.service: dynamics-365-op
---

# Independent software vendor (ISV) licensing (on-premises)

[!include [banner](../includes/banner.md)]

This article explains how to import independent software vendor (ISV) licenses into an on-premises deployment.

> [!IMPORTANT]
> The process described in this article is available only for customers who have on-premises environments that are deployed with Platform update 12 or later.

For general information about the benefits of ISV licensing, information about how to enable licensing for your solution, and other information related to self-signed certificates, see [Independent software vendor (ISV) licensing](isv-licensing.md).

## Generate the license file

1. Collect the tenant name and ID for the customer to issue the license to:

    1. Connect to the instance of Service Fabric Explorer where the environment is hosted.
    1. Go to **Clusters** &gt; **Applications** &gt; **AXSFType** &gt; **fabric:\\AXSF**. On the right page, select the **Details** tab.
    1. In the **Parameters** table, find the values for the **License\_TenantDomainGuid** and **Licence\_TenantId** keys.

1. Generate a license for the customer (tenant ID and name), and sign the license by using the certificate's private key. Pass the following parameters to the AXUtil **genlicense** command to create the license file. The command generates an XML file.

    | Parameter name  | Description |
    |-----------------|-------------|
    | file            | The name of the license file. |
    | licensecode     | The name of the license code from Microsoft Visual Studio. |
    | certificatepath | The path of the certificate's private key. |
    | password        | The password of the certificate's private key. |
    | customer        | The customer's tenant name. |
    | serialnumber    | The customer's tenant ID. |
    | expirationdate  | Optional: The expiration date of the license. |
    | usercount       | Optional: The number that can be required for the custom validation logic. This number can be the number of users, but it isn't limited to users. |

    Here's an example of the command.

    ```Console
    C:\AOSService\PackagesLocalDirectory\Bin\axutil genlicense /file:c:\templicense.txt /certificatepath:c:\tempisvcert.pfx /licensecode:ISVLicenseCode /customer:TAEOfficial.ccsctp.net /serialnumber:4dbfcf74-c5a6-4727-b638-d56e51d1f381 /password:********
    ```

## Automated import

### Prerequisites

- The environment is deployed or serviced with Microsoft Dynamics 365 Finance + Operations (on-premises) version 10.0.31 or later.
- Your deployable package contains the license files that are mentioned in [Independent software vendor (ISV) licensing for production environments](isv-licensing.md#production-environments).

### Import licenses

If your environment and deployable package meet the preceding prerequisites, the licenses are automatically imported when you service your environment. The import license step completes before database synchronization. Therefore, you don't need extra downtime for this operation.

## Manual import

### Prerequisites

Before you import the ISV license file into your on-premises environment, verify that the following prerequisites are met:

- You used the most recent version of the local agent when you deployed the environment.
- You deployed the environment with Platform update 12, and you applied all hotfixes for Platform update 12. This step is mandatory because Microsoft released a fix for an ISV licensing scenario. To get the latest set of hotfixes, use the tiles on the **Environment details** page in Microsoft Dynamics Lifecycle Services.
- Before you import the ISV license, the environment is deployed, and the Application Object Server (AOS) service is running.
- Before you import the ISV license, you apply the ISV solution to the on-premises environment. You can apply the ISV solution to an on-premises environment during the deployment flow. Alternatively, you can use the **Apply updates** flow in Lifecycle Services to apply the ISV solution as a post-deployment step. If you don't apply the ISV solution before you import the license, the customizations aren't enabled.

### Import licenses

Use the following procedure for a sandbox environment or a production environment that you deploy in an on-premises project.

> [!NOTE]
> Importing an ISV license requires downtime. During import, users can't perform business transactions in the environment. When you import the license, make sure that no one is using the system, and that you communicate an official downtime notice to all users.

1. Copy the generated licenses to a folder on one of the machines that runs fabric:/AXSF, and verify that fabric:/AXSF is healthy.
1. Run the **Import-LicensePackage.ps1** script from one of the AOS machines. You can find this script in the latest **Microsoft Dynamics 365 Finance + Operations (on-premises), Deployment scripts** folder on the **Model** tab in the Shared asset library in Lifecycle Services. Pass the following parameters to the script:

    - **LicenseFilesPath** – The path of a folder that contains the license files that you want to import. 
    - **SqlUser** – The same user that you specify in the credentials.json file to run the AOS.
    - **SqlPassword** – The password that you can use to connect to SQL.
    - **EnvironmentConfigPath** – The configuration file for the environment. This file is named config.json and is located under the agent share in a folder that has the format wp\\&lt;environment-name&gt;\\StandaloneSetup.

    After you run the command, it generates log files for each license file that it processes. The names of the log files are in the format {license\_file\_name}.output.log and {license\_file\_name}.error.log. The logs that are generated during database synchronization are located in files that are structured like dbsync.output.log and dbsync.error.log.

    > [!NOTE]
    > As of Infrastructure Scripts 2.17.0, the Import-LicensePackage.ps1 script is deprecated in favor of the automated flow. The script will be removed in a future release.

1. When the script runs successfully, validate that the configuration key is imported and enabled. In the product, the corresponding configuration key is available and enabled on the **License configuration** page. By default, the configuration is enabled. For example, if you add a configuration key named ISVConfigurationKey1, it appears in the list of configuration keys.

When you enable the configuration key, the changes in the ISV solution are visible in the product.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
