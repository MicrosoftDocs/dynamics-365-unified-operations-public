---
# required metadata

title: On-premises Disaster Recovery Configuration
description: This document describes how to configure Dynamics 365 for Finance and Operations on-premises for Disaster Recovery (DR) and the process for switching between the primary and secondary datacenters.
author: faix
manager: AnnBe
ms.date: 05/16/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: osfaixat
ms.search.validFrom: 2019-07-31 
ms.dyn365.ops.version: Platform update 37 

---

# On-premises Disaster Recovery Configuration

The term disaster is used here to mean an event that makes the primary datacenter unusable – for example, a connection outage that makes the primary datacenter inaccessible. High Availability configuration isn't covered within this document – for the minimum setup required for High Availability read [System requirements for on-premises deployments](../../fin-ops/get-started/system-requirements-on-prem.md#minimum-infrastructure-requirements)

### Limitations of this document

This document won't go into specific configuration details for disaster recovery of the following components:
  - AD FS
  - File storage
  - SQL server.

### Recommendations

Remember to keep your DR environment updated with the latest Windows Updates. Your environment will have the latest security updates and won't require updates during a disaster event.

Ensure that you're applying new pre-requisites that are specified by Microsoft. Also, keep your Service Fabric Cluster updated and do certificate rotations as required.

Once you've read through this document, write-up the steps that need to be taken by your team. Afterwards, run through the steps multiple times to ensure you don't come across unexpected problems and minimize the potential downtime. 

## Overview

The basic configuration for DR involves deploying a duplicate of the production environment within another datacenter (the secondary datacenter) and replicating databases to that datacenter. If a disaster event takes place, a few manual steps can be executed to bring the environment within the secondary datacenter online.

The diagram below illustrates, at a high level, the required setup:

![Disaster Recovery architecture](media/DRArchitecture.png)


## Environment Configuration

Within LCS, the production environment should be deployed as usual by using the environment slot named **PRODUCTION**. Your DR environment **won't** use an additional environment slot in LCS. It will instead **reuse** the slot for your production environment. 

Dynamics 365 for Finance and Operations [AOS and SQL Server must be colocated](../../fin-ops/get-started/system-requirements-on-prem.md#network-requirements) within the same datacenter.

## Deploying code packages to Production

When code packages are deployed to the production environment, they don't need to be deployed to the DR environment. That environment should be unused and no Service Fabric Services should be deployed.

## Environment deployment settings

The DR environment should have almost the same configuration as the production environment. The table below illustrates the shared and specific settings for DR:

| Environment Settings | DR Environment|
|---------------------------------|----------------|
| **Active Directory Settings**   |                |
| Administrator user              | Same as production|
| ADFS URL                        | Same as production|
| ADFS OpenId Connect client ID for AOS | Same as production|
| ADFS OpenId Connect client ID for Financial Reporting | Same as production|
| **SQL Database Configuration**  |                 |
| SQL server name                 | Same as production |
| AX database name                | Same as production |
| Financial Reporting database name| Same as production |
| **File Share Settings**         |                 |
| File share for document store   | Same as production |
| File share certificate thumbprint | Same as production |
| **SSRS Configuration Settings** |                 |
| IP address of SSRS instance     | Can be different <sup>1</sup> |
| SSRS certificate thumbprint     | Same as production |
| **Configure Service Settings**  |                 |
| DNS host name of Dynamics 365 instance | Can be different <sup>2</sup>|
| AOS service user                | Same as production |
| MR application service user     | Same as production |
| MR process service user         | Same as production |
| MR click-once service user      | Same as production |
| **Application Certificate Settings** |                 |
| Data encryption certificate thumbprint| Same as production |
| Data signing certificate thumbprint | Same as production   |
| Session authentication certificate thumbprint | Same as production |
| SSL certificate thumbprint       | Same as production |
| Management reporter certificate thumbprint | Same as production |

<sup>1</sup> SSRS is referenced by IP. If the exact same machine IP can't be configured in the DR environment, the IP can be different.

<sup>2</sup> This depends on your network configuration, if you've a load balancer that can handle diverting traffic to the other environment then the host name can be the same. If you're unable to do that, then use a different host name. 

## SQL Server Always-On Availability Configuration

The business data database (AXDB) should be replicated to the secondary datacenter, typically using [SQL Server Always-On Availability Groups](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/always-on-availability-groups-sql-server?view=sql-server-2016).

| Database | Replicated |
|----------|------------|
| Business data (AXDB) | Yes |
| Financial Reporting  | Yes |
| BYODB                | Yes |
| OrchestratorData     | Yes |

## Failing over to DR

### Overview

When a disaster event occurs – the primary datacenter may be unavailable – within the
secondary datacenter the following components will be available.

![Deployment settings thumbprint example](media/DRArchitectureSingle.png)

At the initial moment of the disaster event – the DR environment will be empty. The only thing present will be a configured Service Fabric cluster and a SQL Server, which contains all of the replicated production data. 

To bring the DR environment online, you'll have LCS deploy what is currently available in your Production environment into the DR environment.

>[!IMPORTANT]
> Before you continue further, ensure that no Dynamics Service Fabric services are running in your production environment (in case you're only failing due to a partial disaster event).

### Deploy the LocalAgent

Download the LocalAgent installer and configuration file from LCS to your disaster recovery environment. Once you have the configuration file, open it. Ensure that the connectionEndpoint under the serviceFabric section points to the IP or FQDN of a server in the DR environment. After modifying the file, save it locally and deploy the LocalAgent as you normally would.

>[!IMPORTANT]
> Do not make changes to your connector settings in LCS. 

From now on and until your main production environment comes back online, this LocalAgent will process all requests that LCS puts into the Message Queue. That's why its important you ensure no services are running in your production environment. Eventually, when your orchestrator nodes come back up in your primary datacenter, unprovision the LocalAgent from the cluster.  

### Prepare your pre-deployment scripts (optional)

Pre-deployment scripts are necessary when changes to the deployment configuration are required. This script will have to modify the config.json file with the values you specify. It will be the customers' responsibility to come up with this script.

You can find the location of the config.json file by running the following command.

    ```sql
    select Location from DeploymentInstanceArtifact where AssetId='config.json' and DeploymentInstanceId = 'LCSENVIRONMENTID'
    ```

    > [!NOTE]
    > Replace **LCSENVIRONMENTID** with the ID of your environment. You can obtain this ID from the full details page for your environment in LCS. 

In the case that the SSRS node IP is different you'll have to modify the following values:

```json
        "biReporting": {
          "persistentVirtualMachineIPAddressSSRS": {
            "value": "192.168.5.31"
          },
          "reportingServers": {
            "value": "192.168.5.31"
          },
```

If changing the host name, the following modifications will be required:

```json
    "name": "AOS",
      "parameters": {
        "activeDirectory": {
          ...
          "aadValidAudience": {
            "value": "https://ax.contosoen05.com/"
          },
          ...
        "infrastructure": {
          "hostName": {
            "value": "ax.contosoen05.com"
          },
          ...
        }
    ...
    "name": "FinancialReporting",
      "parameters": {
        ...
        "aad": {
         ...
         "cookieDomain": {
            "value": "ax.contosoen05.com"
          },
          "validAudiences": {
            "value": "https://ax.contosoen05.com/"
          },
          ...
```

>[!IMPORTANT]
> If changing the hostname url for your deployment ensure that your AD FS server is configured to accept the new url. For more information check out [Reuse the same AD FS instance for multiple environments](./onprem-reuseadfs.md).

As the fileshare is shared between the production and DR environments, this predeployment script should be disabled. Only enable it when deploying to your Disaster Recovery environment. 

### Ensure reports get deployed

As the database has previously been synchronized successfully, synchronization would normally be skipped. However, we need to synchronize the reports as the SSRS node is empty. Do the actions below according to the Platform update that your environment is in. 

#### Platform Update 37 or later

Run the following command against your business data database (AXDB):

```sql
	UPDATE SF.synclog SET STATE=5 WHERE CODEPACKAGEVERSION in (SELECT TOP(1) CODEPACKAGEVERSION from SF.SYNCLOG ORDER BY CREATIONDATE DESC)
```

#### Platform Update 36 or earlier

Run the following command against your business data database (AXDB):

```sql
    DELETE FROM SF.synclog WHERE CODEPACKAGEVERSION in (SELECT TOP(1) CODEPACKAGEVERSION from SF.SYNCLOG ORDER BY CREATIONDATE DESC)
```

>[!NOTE]
> For Platform update 36 and earlier a full database synchronization will be executed.

### Deploy your environment

If your production environment is on Platform update 36 or earlier. Follow the instructions 

1. In LCS navigate to the environment page for your production environment.

1. Select **Maintain** and then select **Update Settings**.

    ![Apply update settings](media/addf4f1d0c0a86d840a6a412f774e474.png)

1. Don't change any values and select **Prepare**.

1. After downloading is finished and preparation is completed, the Update environment button will be displayed.

    ![Update environment button](media/0a9d43044593450f1a828c0dd7698024.png)

1. Select Update environment to start updating your environment.

1. Once the environment is deployed, the DR environment is ready for use. 

## Using your DR environment

You can use your DR environment as you normally would except that updates or hotfixes shouldn't be applied to the environment. If you must apply updates to your environment, your failback process will differ from the one described below. Failing back under this condition isn't covered in this guide.

## Failing back to your production environment

>[!IMPORTANT]
> At this point no Dynamics Service Fabric services should be running in your production environment. 

Secure a downtime window in which you can switch operation from the DR environment to the Production environment. Once in the downtime window, disable all non-Orchestrator nodes in the DR environment through Service Fabric Explorer. Once all nodes are disabled, failover your SQL Server to the production data center.

Once the failover has happened, start up the AOS, SSRS, and MR nodes in your primary datacenter. Carry out validation tests to ensure your environment is functioning as expected. Once you decide the environment is working as expected, remove the LocalAgent from your Disaster Recovery environment and reinstall it on your Production environment.

Your primary environment will be back to functioning as usual and can once again be serviced.

Clean up your DR environment by manually unprovisioning all Dynamics Service Fabric Service.

