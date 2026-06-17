---
title: Deployment configurations for the local agent
description: Learn about which deployment configurations can be specified, when deploying the local agent, to indicate a special configuration related to the environment.
author: faix
ms.author: osfaixat
ms.topic: article
ms.custom: 
  - bap-template
ms.date: 06/17/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2026-06-16
ms.service: dynamics-365-op
---

# Deployment configurations for the local agent

[!include [banner](../includes/banner.md)]

This article explains the deployment configuration options that you can specify when deploying the local agent to support special environment configurations.

You can modify these configuration options in Microsoft Dynamics Lifecycle Services (LCS).

To view or edit the current Local Agent configuration, follow these steps:

1. Sign in to LCS and open your on-premises project.
1. In the navigation pane, select **Project Settings** > **On-premises Connectors**.
1. Select the Local Agent associated with your environment, and then select **Edit**.
1. On the **Configure Agent** tab, select **Enter configuration**.
1. In the **Edit agent configuration** dialog box, select the **Deployment Options** tab.
1. Review or modify the deployment options as needed.

If you made changes, you can follow the steps here to update the Local Agent, see [Update the local agent](../lifecycle-services/update-local-agent.md).

The following deployment configuration options can be specified when deploying the Local Agent.

## Specify the version of Microsoft SQL Server

If your environment uses Microsoft SQL Server 2022, change the **SQL Server version** setting from the default value of **2019** to **2022**.

For a list of supported SQL Server versions, see [Microsoft Dynamics 365 Finance + Operations (on-premises), Microsoft Dynamics 365 Finance, and Microsoft Dynamics 365 Supply Chain Management supported software](./onprem-compatibility.md).

## Specify that AD FS is deployed with Microsoft 365 compatibility

If Active Directory Federation Services (AD FS) is deployed with Microsoft 365 compatibility enabled, select the **Enable AD FS Microsoft 365 compatibility** option.

For more information, see [AD FS Microsoft 365 compatibility](./onprem-adfscompatibility.md).

## Specify that the SQL Server cluster is deployed across multiple subnets

If the SQL Server failover cluster is deployed across multiple subnets, select the **Enable SQL Server multi-subnet failover functionality** option.

For more information about this SQL Server configuration, see [SQL Server Multi-Subnet Clustering](/sql/sql-server/failover-clusters/windows/sql-server-multi-subnet-clustering-sql-server).

## Skip certificate revocation list (CRL) validation

When a client establishes a trusted connection with a server, one of the validation steps is to verify that the server certificate isn't revoked by the issuing certificate authority.

To perform this validation, the client, such as the FinancialReporting service, must retrieve the certificate revocation list (CRL). If the certificate was issued by a public certificate authority, internet access is required to verify that the certificate isn't revoked.

Some on-premises environments don't allow outbound internet connectivity and therefore can't perform this validation.

> [!IMPORTANT]
> Disabling certificate revocation validation prevents this security check from being performed. Any risks associated with disabling this validation are the responsibility of the environment owner. Only enable this option if you fully understand and accept the security implications of disabling certificate revocation validation.

## Configure an environment for the Regression Suite Automation Tool (RSAT)

The Regression Suite Automation Tool (RSAT) helps reduce the time and cost associated with user acceptance testing (UAT) in Finance + Operations (on-premises). For more information, see [Regression suite automation tool (RSAT)](../perf-test/rsat/rsat-overview.md).

To enable RSAT support, select the **Enable RSAT configuration** option. When this option is enabled, the **RSAT certificate thumbprint** field becomes available. Enter the thumbprint of the certificate that RSAT should use.

For information about generating and deploying the required certificate, see [Enable RSAT in Microsoft Dynamics 365 Finance + Operations (on-premises) environments](./onprem-rsat-configuration.md).

### Additional details

For reference, you can locate these settings made in LCS in the following section in the `localagent-config.json` file that is labeled `deploymentOptions`.

```json
...
"deploymentOptions": {
    "office365AdfsCompatibility": {
        "value": "true"
    },
    "sqlServerVersion": {
        "value": "2022"
    },
    "isMultiSubnetFailoverEnabled": {
        "value": "false"
    },
    "skipCRLCheck": {
        "value": "false"
    },
    "rsatEnabled": {
        "value": "false"
    },
    "rsatCertificateThumbprint": {
        "value": ""
    }
},
...
```
