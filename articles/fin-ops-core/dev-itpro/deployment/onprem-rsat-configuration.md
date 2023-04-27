---
# required metadata

title: Enable RSAT in Finance + Operations (on-premises) environments
description: This topic explains the steps that are required to configure and enable your environment so that it can be used with the Regression suite automation tool (RSAT).
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
search.app:
  - financeandoperationsonprem-docs
---

# Enable RSAT in Finance + Operations (on-premises) environments

The Regression suite automation tool (RSAT) significantly reduces the time and cost of user acceptance testing (UAT) in Finance + Operations (on-premises). For more information, see [Regression suite automation tool (RSAT)](../perf-test/rsat/rsat-overview.md).

## Generate and deploy the certificate

Before you begin, make sure that you have at least version 2.15.0 of the infrastructure scripts.

1. Go to the file share location that contains your **Infrastructure** folder, and open the **ConfigTemplate.xml** file.
2. In the certificates section, find the certificate of the **RSAT** type, and set the **disabled** option to **false**.
3. Generate the RSAT certificate by running the following command.

    ```powershell
    .\New-SelfSignedCertificates.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    ```

    > [!NOTE]
    > The RSAT certificate must be self-signed, because Active Directory Certificate Services (AD&nbsp;CS) certificates and certificates from a certification authority (CA) can't be used.

4. Export the certificate.

    ```powershell
    .\Export-Certificates.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    ```

5. Export the scripts.

    ```powershell
    .\Export-Scripts.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    ```

6. Rerun the prerequisites script to ensure that the certificate is installed. Perform this step as an administrator.

    ```powershell
    # If remoting, only execute
    # .\Complete-PreReqs-AllVMs.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -ForcePushLBDScripts

    .\Complete-PreReqs.ps1
    ```

## Update the local agent configuration

Before you begin, make sure that you have at least local agent 3.1.0. Otherwise, download the latest version from Microsoft Dynamics Lifecycle Services (LCS).

1. Remove the local agent if it's already provisioned in the Azure Service Fabric cluster.

    ```powershell
    .\LocalAgentCLI.exe Cleanup <path of localagent-config.json>
    ```

2. Open the **localagent-config.json** file.
3. Under **deploymentOptions**, set **rsatEnabled** to **true**. You must also set **rsatCertificateThumbprint** to the thumbprint of the RSAT certificate that was generated. You can check the thumbprint in the **ConfigTemplate.xml** file.
4. Install the local agent.

    ```powershell
    .\LocalAgentCLI.exe Install <path of localagent-config.json>
    ```

## Deploy or service your environment

For new environments that haven't been deployed, see [Deploy your Finance + Operations environment from LCS](.\setup-deploy-on-premises-pu41.md#deploy) for information about how to deploy your environment.

For existing environments, service the environment to apply the changes by deploying a new package or following these steps.

1. In [LCS](https://lcs.dynamics.com), select the **Full Details** link for the environment where you want to apply the RSAT configuration.
2. Select **Maintain**, and then select **Update Settings**. Don't change any settings.
3. Select **Prepare**.

    After the download and preparation are completed, the **Update environment** button appears.

    ![Update environment button.](media/0a9d43044593450f1a828c0dd7698024.png)

4. Select **Update environment** to start to update your environment.

    After the update operation is completed, the environment will be configured to work with RSAT.
