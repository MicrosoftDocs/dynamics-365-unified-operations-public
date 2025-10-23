---
title: Deployment configurations for the local agent
description: Learn about which deployment configurations can be specified, when deploying the local agent, to indicate a special configuration related to the environment.
author: faix
ms.author: osfaixat
ms.topic: article
ms.custom: 
  - bap-template
ms.date: 09/15/2025
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2021-08-03
ms.service: dynamics-365-op
---

# Deployment configurations for the local agent

This article explains which deployment configurations can be specified, when deploying the local agent, to indicate a special configuration related to the environment.

There's a section in the localagent-config.json file that is labeled deploymentOptions. This can be modified before installing the local agent.

```json
...
"deploymentOptions": {
    "office365AdfsCompatibility": {
        "value": "false"
    },
    "sqlServerVersion": {
        "value": "2016"
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

## Specify the version of Microsoft SQL Server

If your environment has Microsoft SQL Server 2019 installed throughout the different components, change **sqlServerVersion** from the default of 2016, to 2019.

For a list of compatible SQL Server versions, see [Microsoft Dynamics 365 Finance + Operations (on-premises), Microsoft Dynamics 365 Finance, and Microsoft Dynamics 365 Supply Chain Management supported software](./onprem-compatibility.md).

## Specify that AD FS is deployed with Microsoft 365 compatibility

To specify that Active Directory Federation Services (AD FS) is deployed with Microsoft 365 compatibility, change **office365AdfsCompatibility** from **false** to **true**.

For more information, see [AD FS Microsoft 365 compatibility](./onprem-adfscompatibility.md).

## Specify that the SQL Server cluster is deployed in multiple subnets

To specify that the SQL Server cluster is deployed in multiple subnets, change **isMultiSubnetFailoverEnabled** from **false** to **true**.

For more information on this SQL Server configuration, see [SQL Server Multi-Subnet Clustering](/sql/sql-server/failover-clusters/windows/sql-server-multi-subnet-clustering-sql-server).

Support for this feature was introduced in release 10.0.19.

## Specify that checking the certificate revocation list of a certificate should be skipped

As part of establishing a trusted connection between a client and a server, one of the checks that is carried out is checking that the certificate provided by the server hasn't been revoked by the issuing authority.

This requires that a client, such as the FinancialReporting service, retrieve the certificate revocation list. If the certificate has been issued by a public certificate authority, then the client would need access to the internet in order to verify that the certificate hasn't been revoked.

Some on-premises environments aren't allowed to connect to the internet. As such, they may not be able to perform this check. It's possible to disable this check by updating **skipCRLCheck** from **false** to **true**.

Support for this option was introduced in version 10.0.21. Additionally, at least local agent 2.7.1 is required to use this option.

> [!IMPORTANT]
> When you disable the certificate revocation list of a certificate, the security check isn't performed. You bear the risk of disabling it. You should only enable this deployment option if you are fully aware of the security implications of disabling this check.

## Specify that an environment should be configured to work with the Regression suite automation tool

The Regression suite automation tool (RSAT) significantly reduces the time and cost of user acceptance testing (UAT) in Finance + Operations (on-premises). For more information, see [Regression suite automation tool (RSAT)](../perf-test/rsat/rsat-overview.md).

To enable this deployment option, change the value of **rsatEnabled** from **false** to **true**. Additionally, set **rsatCertificateThumbprint** to the thumbprint of the certificate that you want to use for RSAT.

For more information about how to generate and deploy the certificate, see [Enable RSAT in Microsoft Dynamics 365 Finance + Operations (on-premises) environments](./onprem-rsat-configuration.md).

Support for this option was introduced in version 10.0.28. Additionally, at least local agent 3.1.0 is required to use this option.
