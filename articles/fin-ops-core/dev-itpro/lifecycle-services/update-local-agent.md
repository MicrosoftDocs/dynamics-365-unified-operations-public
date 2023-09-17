---
# required metadata

title: Update the local agent
description: This article explains how to update the local agent.
author: faix
ms.date: 08/15/2023
ms.topic: article
ms.prod: dynamics-365
ms.service:
ms.technology:

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: johnmichalak
# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: osfaixat
ms.search.validFrom: 2017-12-05
ms.dyn365.ops.version: 7.3
search.app:
  - financeandoperationsonprem-docs
---
# Update the local agent

[!include [banner](../includes/banner.md)]

This article explains how to update the local agent. The latest version of the local agent is version 3.2.3, which was released in August 2023.

> [!IMPORTANT]
> Do not update the local agent during a servicing operation, even if the preparation phase has completed. 

| Local agent version | Capability | Release Date | Expiration date |
|---------------------|------------|--------------|-----------------|
| 3.2.3               | This version fixes a few bugs and removes the need for manually updating the config.json after a certificate rotation.| August 2023 | Not applicable |
| 3.2.2               | This version fixes a bug with the local agent not able to clean up the workspace directory due to the directory containing files with long paths. | June 2023 | Not applicable |
| 3.2.1               | This version fixes some bugs with the local agent not being able to download artifacts correctly from Azure Storage. Upgrades the Azure Storage libraries. | June 2023 | Not applicable |
| 3.2.0               | This version upgrades the Service Fabric SDK, upgrades the Azure Storage libraries, introduces file hash validation | March 2023 | Not applicable |
| 3.1.0               | This version upgrades the Service Fabric SDK and adds a new deployment option. |June 2022 | Not applicable |
| 3.0.0               | This version includes support for Edge Scale Unit Application Lifecycle Management. | November 2021 | June 30, 2023 |
| 2.7.2               | This version includes a fix for deploying older application versions. | October 2021 | June 30, 2023 |
| 2.7.1               | This version introduces a new deployment option and fixes a bug with a deployment option. | October 2021 | June 30, 2023 |
| 2.7.0               | Enables deploying or updating to 10.0.21 and later versions. Additionally, this version enables deploying on environments with Microsoft SQL Server 2019 and some bug fixes. | August 2021 | June 30, 2023 |
| 2.6.0               | This version upgrades the Service Fabric SDK, fixes a bug with refresh state, and increases the application provisioning timeout. | October 2020 | June 30, 2023 |
| 2.5.0               | This version updates dependencies and fixes a cleanup bug. | May 2020 | June 30, 2023 |
| 2.4.0               | This version fixes a deployment issue and upgrades the runtime of the local agent. | December 2019 | April 30, 2023 |
| 2.3.1               | This version fixes orchestration service crashes that may occur during cleanup on some environments.<br><br>Deploying version 10.0.5 with Platform update 29 or earlier requires the use of predeployment scripts for automatic updating of FinancialReportingDeployer.exe.config. For more information, see [Troubleshoot on-premises deployments](../../dev-itpro/deployment/troubleshoot-on-prem.md#FREntityFramework). | September 2019 | April 30, 2023 |
| 2.3.0               | This version adds support for pre and post-deployment scripts. | August 2019 | April 30, 2023 |
| 2.2.0               | This version fixes locked DLLs during cleanup and enables prerequisites for supporting Active Directory Federation Services (AD FS) that also is used for Microsoft 365. | July 2019 | January 31, 2023 |
| 2.1.2               | This version contains updated Azure dependencies for improved download stability and logic to correctly evaluate if files are downloaded. This update fixes an issue where files are fully downloaded, but the logic would still consider them missing a few bytes and therefore fail the download. | July 2019 | January 31, 2023 |
| 2.1.1               | This version fixes an issue that occurs when the download fails and the Microsoft Dynamics Lifecycle Services **Maintain** button isn't available. Other changes include updates to Azure storage libraries to improve communication with Azure storage and enable TLS 1.2. | February 2019 | January 31, 2023 |
| 2.1.0               | This version enables two-phased servicing where **Preparation** and **Update** are two separate steps. | June 2018 | January 31, 2023 |
| 2.0.0               | This version enables servicing flows and deploys Platform update 12. | January 2018 | January 31, 2023 |
| 1.1.0               | This version enables the [Reconfigure feature](../../dev-itpro/lifecycle-services/reconfigure-environment.md) for successful deployments, enables multi-model package deployments, and deploys Platform update 8 and 11. | December 2017 | January 31, 2023 |
| 1.0.0               | This version enables the [Reconfigure feature](../../dev-itpro/lifecycle-services/reconfigure-environment.md) for failed deployments. | October 2017 | January 31, 2023 |
| Null                | This initial version deploys Platform update 8. | July 2017 | January 31, 2023 |

## What's new in local agent 3.2.3
- This version fixes a bug where the topology.xml was being cached and not updated from Lifecycle Services.
- Removes the need to update the config.json after a certificate rotation.
- Enforces an encrypted communication between the local agent and the SQL database.

## What's new in local agent 3.2.2
- This version fixes a bug with the local agent not able to clean up the workspace directory due to the directory containing files with long paths.

## What's new in local agent 3.2.1
- This version fixes some bugs with the local agent not being able to download artifacts correctly from Azure Storage.
- Upgrades the Azure Storage libraries.
- Adds logging for 7zip operations.

## What's new in local agent 3.2.0
- Local agent 3.2.0 uptakes a new Service Fabric Explorer SDK and runtime.
- This release also upgrades the Azure Storage libraries to the latest version. The checkpointing functionality is no longer available, however there's now automated retry functionality that can be customized. We'll consider bringing back checkpoints once the Azure Storage libraries support it again.
- Artifact management logic has been improved, and downloading existing artifacts again should no longer take place.
- Filehash validation has been added to ensure artifacts in the artifact store match exactly what is in the Lifecycle Services artifact store.
- The MSAL libraries are now used to authenticate with Microsoft Azure Active Directory (Azure AD).
- Detection of the local agent being deprecated with clear messaging in Service Fabric Explorer.

> [!IMPORTANT]
> This release is only compatible with 8.2+ Service Fabric clusters.
> This release requires that a new local agent configuration file be downloaded from Lifecycle Services.

## What's new in local agent 3.1.0

- Local agent 3.1.0 uptakes a new Service Fabric SDK and runtime.
- This release introduces a new deployment option to [specify that an environment should be configured to work with the Regression suite automation tool (RSAT)](../../dev-itpro/deployment/onprem-localagent-options.md#specify-that-an-environment-should-be-configured-to-work-with-the-regression-suite-automation-tool).

> [!IMPORTANT]
> This release is only compatible with 8.1+ Service Fabric clusters.

## What's new in local agent 3.0.0

- Local agent 3.0.0 includes support for managing the lifecycle of Edge Scale Units through the Scale Unit Management portal. For more information, see [Distributed Hybrid Topology](../../../supply-chain/cloud-edge/cloud-edge-landing-page.md).
- This release requires the .NET Framework version 4.8 to uptake the newest changes from Lifecycle Services.

## What's new in local agent 2.7.2

- Local agent 2.7.2 fixes an issue where environments on older versions of the application would fail to deploy.

## What's new in local agent 2.7.1

- Local agent 2.7.1 introduces a new deployment option to [Specify that checking the Certificate Revocation List of a certificate should be skipped](../../dev-itpro/deployment/onprem-localagent-options.md#specify-that-checking-the-certificate-revocation-list-of-a-certificate-should-be-skipped).
- This release addresses a bug where the **office365AdfsCompatibility** deploymentOption wasn't being correctly set.

## What's new in local agent 2.7.0

- Local agent 2.7.0 is a prerequisite to deploy or update to 10.0.21 and later releases. 
- This release introduces the possibility of specifying a limited set of deployment options for environment-specific deployment options. Most notably, this release allows you to deploy on environments with Microsoft SQL Server 2019. For all possible configurations, see [Local agent deployment configurations](../../dev-itpro/deployment/onprem-localagent-options.md).
- Additionally, this release addresses an issue where the gMSA account that the local agent executes under loses permission to the private key for some certificates.
- The LBDTelemetry-Agent application can start correctly even if the Event Viewer is open. 

> [!IMPORTANT]
> This release **must be used** to deploy or update to 10.0.21 and later releases.
> This release requires that a new local agent configuration file be downloaded from Lifecycle Services. If you encounter issues, refer to [Troubleshoot on-premises deployments](../../dev-itpro/deployment/troubleshoot-on-prem.md). 

## What's new in local agent 2.6.0

- Local agent 2.6.0 uptakes a new Service Fabric SDK and runtime.
- This release fixes a bug where, if refresh state is triggered when the environment is stuck in the Downloading phase, the environment would automatically move to a deployed state without updating the environment. In this situation, the refresh state marks the Downloading phase as failed.
- The timeout for provisioning an application has been increased.

> [!IMPORTANT]
> This release is only compatible with 7.x Service Fabric clusters.

## What's new in local agent 2.5.0

- Local agent 2.5.0 uptakes new versions of various dependencies. The main changes are Service Fabric and Entity Framework.
- This release also fixes a bug where, if cleanup fails without cleaning up any services, subsequent reattempts always fail during cleanup.

## What's new in local agent 2.4.0

- Local agent 2.4.0 now requires the .NET Framework version 4.7.2 to uptake the newest changes from Lifecycle Services. To meet the newest requirements, be sure to run the latest infrastructure scripts that are available in Lifecycle Services.
- This release also fixes an issue where the deployment of the AXService would fail in slower environments due to a hard-coded timeout.

## What's new in local agent 2.3.0

- Local agent 2.3.0 enables the execution of custom [pre- and post- deployment scripts](../../dev-itpro/lifecycle-services/pre-post-scripts.md).
- It fixes the problem introduced in 2.2.0 with deploying older platform updates.
- This release removes the monitoring agent and introduces a new service called LBDTelemetry, that is used to install the ETWManifests.

> [!IMPORTANT]
> This release requires that a new local agent configuration file be downloaded from Lifecycle Services. Refer to the [Troubleshoot on-premises deployments](../../dev-itpro/deployment/troubleshoot-on-prem.md) article if you encounter problems. 

## What's new in local agent 2.1.0
- Local agent 2.1.0 enables the two-phased servicing where **Environment preparation** and **Environment update** are two distinct steps and explicit actions. This reduces the total downtime customers must take when applying updates to their on-premises environments by preparing upfront and allowing users to use the environment during preparation and then communicating the downtime when the actual update environment action is triggered.

## What's new in local agent 2.0.0
- Local agent 2.0.0 can deploy Platform update 12.
- It enables the [Reconfigure feature](../../dev-itpro/lifecycle-services/reconfigure-environment.md) until the first deployment of Platform update 12 succeeds.
- It disables the [Reconfigure feature](../../dev-itpro/lifecycle-services/reconfigure-environment.md) on the first successful deployment of Platform update 12. After deployment succeeds, you can use the regular update experience to update the environment.

> [!NOTE]
> Local agent 2.0.0 **cannot** deploy Platform update 8 and Platform update 11. You must have version 1.1.0 to deploy those platform updates.

## Download the latest local agent and configuration from Lifecycle Services

> [!NOTE]
> If you require an older version of the local agent for your current deployments, download it from the Asset library in Lifecycle Services. To download Local agent version 1.1.0, go to **Shared Asset Library > Model** and click on Dynamics 365 Finance and Operations (on-premises) - Local agent v1.1.0**.
>
> You must have version 2.0.0 or later to deploy Platform update 12 and complete update flows.

1. In Lifecycle Services, select **Project settings** > **On-prem connectors**.
2. Select the connector to your environment, and then select **Edit**.
3. On the menu on the left side of the page, select **Setup host infrastructure**, and then select **Download agent installer**.

    You must now verify that the zip file that is downloaded and unblocked.

4. Go to the zip file, right-click it, and then select **Properties**.
5. In the **Properties** dialog box, select **Unblock**, and then select **Apply**.
6. On the **Configure agent** tab, select **Download configurations** to download the localagent-config.json configuration file.

## Update the local agent

### Clean up the existing local agent

1. Fine the folder that you previously installed the local agent from.
1. In a PowerShell window, navigate to that folder, and run the following command.

    ```Console
    LocalAgentCLI.exe Cleanup <path of localagent-config.json>
    ```

    > [!NOTE]
    > You must use the current agent's binaries to clean up the agent. If you don't have the current agent's binaries, you can delete the local agent application from Service Fabric Explorer.

1. Select any key to exit the cleanup operation.
1. Verify that the local agent has been successfully cleaned up by looking in Service Fabric Explorer and making sure that there are no apps in the **Deployed Applications** section in the **Orchestrator** nodes.

### Install the new local agent

1. Copy the zip file and the localagent-config.json file that you previously downloaded into the file share where you placed your **infrastructure** folder (for example, \\\\LBDFFILE01\\Install)).
1. Unzip the agent installer to \\\\LBDFFILE01\\Install\LocalAgent.
1. Copy the localagent-config.json file to \\\\LBDFFILE01\\Install\LocalAgent.
1. In a PowerShell window, navigate to \\\\LBDFFILE01\\Install\LocalAgent, and run the following command.

    ```Console
    LocalAgentCLI.exe Install <path of localagent-config.json>
    ```

1. After the local agent is successfully installed, go back to your on-premises connector in Lifecycle Services.
1. On the **Validate setup** tab, select **Message agent** to test Lifecycle Services connectivity to your new local agent.

## Local agent expiration dates

After the date when a local agent becomes expired, it can no longer communicate with Lifecycle Services. Therefore, you have to update your local agent to a supported version. Going forward, we plan to support only a few versions of the local agent at a time. The two most recently released versions won't receive an expiration date until a new version has been released. At that point, the oldest version that doesn't have an expiration date will receive an expiration date. The expiration date will be set a few months into the future, so that customers have time to upgrade to a newer version.

> [!NOTE]
> A released local agent version will be supported for at least six months.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

