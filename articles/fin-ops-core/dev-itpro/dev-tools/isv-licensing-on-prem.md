---
title: Independent software vendor (ISV) licensing (on-premises)
description: This article describes the independent software vendor (ISV) licensing feature for on-premises environments.
author: faix
ms.date: 09/16/2022
ms.topic: article
ms.prod: dynamics-365
audience: Developer
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: osfaixat
ms.search.validFrom: 2018-03-07
ms.dyn365.ops.version: AX 7.3.0
ms.assetid: 90ae4ae6-f19a-4ea5-8bd9-1d45729b0636
ms.service: 
search.app:
  - financeandoperationsonprem-docs
---

# Independent software vendor (ISV) licensing (on-premises)

[!include [banner](../includes/banner.md)]

This article explains how to import independent software vendor (ISV) licenses into an on-premises deployment.

> [!IMPORTANT]
> The process that is described in this article is available only for customers who have on-premises environments that are deployed with Platform update 12 or later.

For general information about the benefits of ISV licensing, information about how to enable licensing for your solution, and other information that is related to self-signed certificates, see [Independent software vendor (ISV) licensing](isv-licensing.md).

## Generate the license file

1. Collect the tenant name and ID for the customer to issue the license to:

    1. Connect to the instance of Service Fabric Explorer where the environment is hosted.
    2. Go to **Clusters** &gt; **Applications** &gt; **AXSFType** &gt; **fabric:\\AXSF**, and then, on the right page, select the **Details** tab.
    3. In the **Parameters** table, find the values for the **License\_TenantDomainGuid** and **Licence\_TenantId** keys.

1. Generate a license for the customer (tenant ID and name), and sign the license by using the certificate's private key. The following parameters must be passed to the AXUtil **genlicense** command to create the license file. The command will generate an XML file.

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

    Here is an example of the command.

    ```Console
    C:\AOSService\PackagesLocalDirectory\Bin\axutil genlicense /file:c:\templicense.txt /certificatepath:c:\tempisvcert.pfx /licensecode:ISVLicenseCode /customer:TAEOfficial.ccsctp.net /serialnumber:4dbfcf74-c5a6-4727-b638-d56e51d1f381 /password:********
    ```

## Automated import

### Prerequisites

- The environment is deployed or will be serviced with Microsoft Dynamics 365 Finance + Operations (on-premises) version 10.0.31 or later.
- Your deployable package contains the license files that are mentioned in [Independent software vendor (ISV) licensing for production environments](isv-licensing.md#production-environments).

### Import licenses

If your environment and deployable package meet the preceding prerequisites, the licenses will automatically be imported when you service your environment. The import license step will be completed before database synchronization. Therefore, additional downtime will no longer be required for this operation.

## Manual import

### Prerequisites

Before you import the ISV license file into your on-premises environment, verify that the following prerequisites are met:

- The most recent version of the local agent was used when the environment was deployed.
- The environment is deployed with Platform update 12, and all hotfixes for Platform update 12 are applied. This step is mandatory because Microsoft has released a fix for an ISV licensing scenario. To get the latest set of hotfixes, use the tiles on the **Environment details** page in Microsoft Dynamics Lifecycle Services.
- Before you import the ISV license, the environment must be deployed, and the Application Object Server (AOS) service must be running.
- Before you import the ISV license, the ISV solution must be applied to the on-premises environment. The ISV solution can be applied to an on-premises environment during the deployment flow. Alternatively, you can use the **Apply updates** flow in Lifecycle Services to apply the ISV solution as a post-deployment step. If the ISV solution isn't applied before you import the license, the customizations won't be enabled.

### Import licenses

The following procedure can be used for a sandbox environment or a production environment that is deployed in an on-premises project.

> [!NOTE]
> Because import of an ISV license requires downtime, no business transactions can be performed in the environment during import. When you do the import, make sure that no one is using the system, and that an official downtime notice has been communicated to all the users.

1. Copy the licenses that are generated to a folder on one of the machines that is running fabric:/AXSF, and verify that fabric:/AXSF is healthy.
1. Run the **Import-LicensePackage.ps1** script from one of the AOS machines. You can find this script in the latest **Microsoft Dynamics 365 Finance + Operations (on-premises), Deployment scripts** folder on the **Model** tab in the Shared asset library in Lifecycle Services. You must pass the following parameters to the script:

    - **LicenseFilesPath** – The path of a folder that contains the license files that must be imported. 
    - **SqlUser** – The same user who is specified in the credentials.json file to run the AOS.
    - **SqlPassword** – The password that can be used to connect to SQL.
    - **EnvironmentConfigPath** – The configuration file for the environment. This file is named config.json and is located under the agent share in a folder that has the format wp\\&lt;environment-name&gt;\\StandaloneSetup.

    After the command is run, log files are generated for each license file that is processed. The names of the log files are in the format {license\_file\_name}.output.log and {license\_file\_name}.error.log. The logs that are generated during database synchronization are located in files that are structured like dbsync.output.log and dbsync.error.log.

    > [!NOTE]
    > As of Infrastructure Scripts 2.17.0, the Import-LicensePackage.ps1 script is deprecated in favor of the automated flow. The script will be removed in a future release.

1. When the script has been run successfully, validate that the configuration key has been imported and enabled. In the product, the corresponding configuration key will be available and enabled on the **License configuration** page. By default, the configuration is enabled. For example, if you added a configuration key that is named ISVConfigurationKey1, it will appear in the list of configuration keys.

When the configuration key is enabled, the changes in the ISV solution will be visible in the product.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
