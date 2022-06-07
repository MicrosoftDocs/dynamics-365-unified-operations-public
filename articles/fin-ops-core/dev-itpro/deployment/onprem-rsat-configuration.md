---
# required metadata

title: Enabling RSAT in Microsoft Dynamics 365 Finance + Operations (on-premises) environments
description: This topic explains the steps that need to be taken in order to configure and enable your environment so that it can be used with RSAT.
author: faix
ms.date: 03/06/2022
ms.topic: article
ms.prod: dynamics-365 
ms.service:
audience: IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: osfaixat
ms.search.validFrom: 2022-06-03

---

# Enabling RSAT in Microsoft Dynamics 365 Finance + Operations (on-premises) environments

The Regression suite automation tool (RSAT) significantly reduces the time and cost of user acceptance testing (UAT) of Finance and Operations apps. For more information see [Regression suite automation tool (RSAT)](../perf-test/rsat/rsat-overview.md)

## Generating and deploying the certificate

1. Ensure that you have at least version 2.15.0 of the Infrastructure Scripts.
1. Navigate to the fileshare location that contains your **Infrastructure** folder and open the **ConfigTemplate.xml** file.
1. In the certificates section, find the certificate of type **RSAT** and set the **disabled** to **false**
1. Generate the RSAT certificate by running the following command:
    ```powershell
        .\New-SelfSignedCertificates.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    ```

    > [!NOTE]
    > The RSAT certificate must be self-signed. It is not possible to use ADCS certificates or certificates from a certificate authority.

1. Export the certificate:
    ```powershell
        .\Export-Certificates.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    ```

1. Export the scripts:
    ```powershell
        .\Export-Scripts.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    ```

1. Rerun the prerequisites script to ensure the certificate gets installed . Perform this step as an administrator.

    ```powershell
    # If remoting, only execute
    # .\Complete-PreReqs-AllVMs.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -ForcePushLBDScripts

    .\Complete-PreReqs.ps1
    ```

## Update the local agent configuration

1. Ensure you have at least local agent 3.1.0, otherwise download the latest version from LCS.

1. Remove the local agent if it provisioned in the Service Fabric cluster already.
    ```powershell
    .\LocalAgentCLI.exe Cleanup <path of localagent-config.json>
    ```
1. Open the **localagent-config.json** and under deploymentOptions set **rsatEnabled** to **true**. You also need to set the **rsatCertificateThumbprint** to the thumbprint of the generated RSAT certificate. You can check the thumbprint in the **ConfigTemplate.xml**.

1. Install the local agent.
    ```powershell
    .\LocalAgentCLI.exe Install <path of localagent-config.json>
    ```

## Deploy or service your environment

1. For new environments that have not been deployed yet, follow [Deploy your Finance + Operations environment from LCS](.\setup-deploy-on-premises-pu41.md#deploy) to deploy your environment.

1. For existing environments, you need to service the environment to apply the changes. This can be done by deploying a new package or by following the instructions below.

    1. In [LCS](https://lcs.dynamics.com), select the **Full Details** link for the environment where you want to apply the RSAT configuration.

    1. Select **Maintain**, and then select **Update Settings**. Do not change any settings.

    1. Select **Prepare**.

        After the download and preparation are completed, the **Update environment** button appears.

	    ![Update environment button.](media/0a9d43044593450f1a828c0dd7698024.png)

    1. Select **Update environment** to start to update your environment.

        After the update operation is finished, the environment will be configured to work with RSAT.
