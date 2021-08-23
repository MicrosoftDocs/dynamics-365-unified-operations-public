---
# required metadata

title: Deployment configurations for the local agent
description: This topic explains which deployment configurations can be specified, when deploying the local agent, to indicate a special configuration related to the environment.
author: faix
ms.date: 08/03/2021
ms.topic: article
audience: IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: osfaixat
ms.search.validFrom: 2021-08-03

---

# Deployment configurations for the local agent

This topic explains which deployment configurations can be specified, when deploying the local agent, to indicate a special configuration related to the environment.

There is a section in the localagent-config.json file that is labeled deploymentOptions. This can be modified before installing the local agent.

```json
    ...
    "deploymentOptions": {
				"office365AdfsCompatibility": {
					"value": "false"
				},
				"sqlServerVersion" : {
					"value": "2016"
				},
				...
			},
    ...
```

## Specify the version of Microsoft SQL Server

If your environment has Microsoft SQL Server 2019 installed throughout the different components, change **sqlServerVersion** from the default of 2016, to 2019.

For a list of compatible SQL Server versions, see [Microsoft Dynamics 365 Finance + Operations (on-premises) supported software](./onprem-compatibility.md).

## Specify that AD FS is deployed with Microsoft 365 compatibility

To specify that Active Directory Federation Services (AD FS) is deployed with Microsoft 365 compatibility, change **office365AdfsCompatibility** from **false** to **true**.

For more information, see [AD FS Microsoft 365 compatibility](./onprem-adfscompatibility.md).

## Specify that the SQL Server cluster is deployed in multiple subnets

To specify that the SQL Server cluster is deployed in multiple subnets, change **isMultiSubnetFailoverEnabled** from **false** to **true**.

For more information on this SQL Server configuration, see [SQL Server Multi-Subnet Clustering](/sql/sql-server/failover-clusters/windows/sql-server-multi-subnet-clustering-sql-server).

Support for this feature was introduced in release 10.0.19.
