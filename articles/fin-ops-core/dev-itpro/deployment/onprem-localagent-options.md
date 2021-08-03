---
# required metadata

title: Deployment configurations for the local agent
description: This topic explains which deployment configurations can be specified when deploying the local agent to indicate a special configuration related to the environment. 
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

This topic explains which deployment configurations can be specified when deploying the local agent to indicate a special configuration related to the environment.

There will be a section in the localagent-config.json file that is labeled deploymentOptions that can be modified prior to installing the local agent.

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

## Specifying the version of Microsoft SQL Server

Change **sqlServerVersion** from the default of 2016, to 2019 if your environment has Microsoft SQL Server 2019 installed throughout the different components.

For a list of compatible SQL Server versions, see [Microsoft Dynamics 365 Finance + Operations (on-premises) supported software](./onprem-compatibility.md).

## Specifying AD FS is deployed with Microsoft 365 compatibility

Change **office365AdfsCompatibility** from **false** to **true**.

For more information, see [AD FS Microsoft 365 compatibility](./onprem-adfscompatibility.md).

## Specifying that the SQL Server cluster is deployed in multiple subnets

Change **isMultiSubnetFailoverEnabled** from **false** to **true**.

For more information on this SQL Server configuration, see [SQL Server Multi-Subnet Clustering](/sql/sql-server/failover-clusters/windows/sql-server-multi-subnet-clustering-sql-server).

Support for this feature was introduced in 10.0.19.
