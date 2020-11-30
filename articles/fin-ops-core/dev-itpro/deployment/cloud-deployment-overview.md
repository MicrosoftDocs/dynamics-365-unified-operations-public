---
# required metadata

title: Cloud deployment overview
description: This topic describes the cloud environment and subscription that you are deploying to, who can perform which tasks, and the data and customizations that you need to manage for Finance and Operations apps. 
author: LaneSwenka
manager: AnnBe
ms.date: 11/30/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 60373
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: laswenka
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: Platform Update 8

---
# Cloud deployment overview

[!include [banner](../includes/banner.md)]
 
Working with Microsoft to deploy Finance and Operations apps in the cloud requires that you understand the environment and subscription that you are deploying to, who can perform which tasks, and the data and customizations that you need to manage. 
We recommend that you sign up for the Full Microsoft FastTrack for Dynamics 365 to help speed your deployment and implementation - it's a program that provides training and consulting to help you realize business value faster. For more information, see [Microsoft FastTrack](../../fin-ops/get-started/fasttrack-dynamics-365-overview.md). If you choose to use the Essentials FastTrack program instead, you will be using the Implementation Project Methodology in Lifecycle Services (LCS) to help you manage your implementation project. 

## Customer lifecycle, subscriptions, and environment types
Microsoft assumes that all customers will follow a lifecycle similar to the following for all cloud deployments, and therefore need different environment topologies at each phase. 

- Evaluate
- Develop customizations, if needed.
- Curate a "golden configuration" environment that contains only module configurations without master or transactional data.  This is to be the baseline for your data migration testing and eventual go live.
- Install and test customizations and partner solutions on a tier-1 sandbox (Development or test environment). 
- Test customizations, partner solutions and data configuration on a tier-2 sandbox environment.
- Deploy customizations and data configurations to a production environment with high availability.

At some phases of a project, you may have all of the environments live at once. For more information, about the default licenses and tiers that are available, see the [Dynamics 365 Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544&clcid=0x409).

You may notice the terms cloud hosted or Microsoft subscriptions. A *cloud hosted subscription* means that the customer or partner brings their own Azure subscription and deploys Finance and Operations apps to it, for evaluation and development purposes only. The customer or partner pays for the resources deployed to their Azure subscription based on the Azure price list. A *Microsoft subscription* means that the customer purchases Finance and Operations licenses, which will then allow them to deploy environments to an Azure subscription which is managed by Microsoft, therefore, the customer has no separate Azure billing. 

With each Enterprise offer, three environments are included by default:
- One Tier 2 sandbox (multi-box environment) for user acceptance testing (UAT).
- One production environment with high availability (HA). 

Additional environments may be purchased as add-ons. For information about licensing and what is included in Microsoft Dynamics 365, see the [Dynamics 365 Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544&clcid=0x409).

Here's how the lifecycle maps to the available environments.  If you already have environments deployed in your Lifecycle Services project, you can find the Environment Type and Environment Sub type on each environment's details page.

| Lifecycle phase      | Environment tier         | Subscription            | Environment types                 | Environment sub-type 
|-------------------------------|---------------------------------|--------------------------------------|---------------------------------------------|---------------------------------------------|
| Evaluation and analysis       | Tier 1 Sandbox | Cloud hosted | Customer Managed | Demo
| Customize                     | Tier 1 Sandbox | Cloud hosted or VHD | Customer Managed | Develop
| Golden configuration          | Tier 1 Sandbox | Cloud hosted | Customer Managed | Develop
| User acceptance testing (UAT) | Tiers 2-5 Sandbox | Microsoft                 | Microsoft Managed or Self-service | Not applicable
| Go live                       | Production | Microsoft                    | Microsoft Managed or Self-service | Not applicable     

*Tiers 2-5 can be purchased to increase performance of the environment.  The higher the tier, the more compute and database capacity is reserved for your use.*
*For more information about Self-service environment types, check out the [Self-service deployment overview](infrastructure-stack.md).*

### Environment lifecycle operations
Users with the Environment Administrator or Project Owner roles in Lifecycle Services can perform various lifecycle operations on their environments.  These operations often involve downtime on the environment until the task is finished.  Each of these operations are located under or next to the **Maintain** button on each environment details page.

| Lifecycle operation | Description | Learn more
|---------------------|-------------|------------|
| Apply software | Install Microsoft updates, ISV solutions, or your own customization packages. | [Apply updates to cloud environments](apply-deployable-package-system.md)
| Enable access | Allow list your IP for Remote Desktop or database access | See the [Remote Desktop](cloud-deployment-overview.md#remote-desktop) section later in this topic
| Restart services | Ability to restart components of your environment | [Restart environment services](../lifecycle-services/restart-environment-services.md)
| Move database | Full data lifecycle management | [Database movement operations](../database/dbmovement-operations.md)
| Maintenance mode | Ability to change configuration with only admin access | [Maintenance mode](../sysadmin/maintenance-mode.md)
| Upgrade | Upgrade code and data from 7.x to the latest version | [Process for moving to the latest update](../migration-upgrade/upgrade-latest-update.md)
| Deallocate | Ability to turn off an environment not being used, or to troubleshoot a failed action | Not applicable
| Start | Ability to turn on an environment for use | Not applicable
| Delete | Ability to delete an environment previously deallocated | Not applicable


## Security and compliance
Finance and Operations is PA-DSS 3.1 certified which means that all communications between components are secured out-of-the-box. 

All Finance and Operations front-end virtual machines in Microsoft Azure are configured during deployment to only accept TLS 1.2. 

> [!IMPORTANT]
> Customers who have administrator access to Microsoft-managed sandboxes, including any add-on sandboxes purchased, must follow these guidelines:
> - By default, automatic Windows update is enabled for all Tier 1 - 5 sandboxes and should NOT be disabled. This ensures that any time that Microsoft pushes security or critical infrastructure updates to your environment, your environment receives the latest set of updates and is updated each month with the operating system fixes that Microsoft releases.  
> -	Admin passwords on these environments should NOT be changed. Environments that have admin passwords changed will be flagged by Microsoft. Microsoft reserves the right to, and will reset the admin password.  
> - Adding new user accounts to any Microsoft managed VM is NOT permitted. Microsoft reserves the right to, and will remove the newly added user accounts without providing notice.

> Finance and Operations is not covered by a FedRAMP ATO at this time. If Finance and Operations is provisioned in the United States, all customer data at rest is stored in data centers located in the United States, as described in [International availability of Dynamics 365](https://www.microsoft.com/trustcenter/privacy/dynamics365-finance-operations). Finance and Operations does not support any other Dynamics 365 US Government or Microsoft 365 GCC compliance attributes (for example, access by US screened personnel, and support for CJIS and IRS 1075). 

## Remote Desktop

### Microsoft-managed environments

> [!WARNING]
> Microsoft will be removing the use of Remote Desktop by customers and partners.  Each environment will first have administrator access removed, but still allow non-administrator access to the virtual machines. After this, all access will be removed. For each step of this phased removal, an email notification will be sent to the Notification list setup for each environment. All Remote Desktop access will be removed by November 2020.

Customers are required to complete additional setup to connect to virtual machines (VMs) through Microsoft Remote Desktop (RDP). This additional setup applies to all Microsoft-managed environments, including Tier 1 through Tier 5 sandboxes and add-ons. In order to connect to Tier 1 through Tier 5 sandbox environments, you must explicitly enable access (safe list) from your organization’s IP address space. This can be done by a Lifecycle Services (LCS) user who has access to the **Environment** page (**Maintain** > **Enable Access**) where they can enter the IP address space that will be used to connect to the virtual machines through Remote Desktop. Access rules are either a single IP address (example: 10.10.10.10) or an IP address range (example: 192.168.1.0/24). You may add multiple entries at once as a semi-colon(;) separated list (example: 10.10.10.10;20.20.20.20;192.168.1.0/24). These entries are used to configure the Azure Network Security Group that is associated with your environment’s virtual network. For more information, see [Security rules](https://docs.microsoft.com/azure/virtual-network/security-overview#security-rules).

> [!IMPORTANT]
> Customers need to ensure that RDP endpoints are secured through explicit IP safe list rules as mentioned above. The IP safe list rules must adhere to the following conditions.
> - IP safe list rules must NOT use asterisk/zero.
> - Wide IP address ranges must NOT be used.
> - IP address ranges must restrict to the customer's CORPNET. 
> - If computers outside the customer's CORPNET (such as a home office) are used to connect to sandbox environments, only the specific IP addresses of the computers used to connect to the sandbox environments must be added.
> - Azure Datacenter IP address ranges must NOT be added.
> - Public IP addresses, such as a coffee shop location, must NOT be added.     
> - IP safe list rules should be removed when not in use. Periodic review of environment IP safe list rules is recommended.

> Microsoft will run periodic tests on the Microsoft Managed environments validating that the environments are sufficiently restricted.
> Microsoft reserves the right to and will remove any IP Address safe list rules that violate the above guidelines, immediately without providing notice.
 
### Partner/Customer managed environments 
By default, Remote Desktop is enabled for all non-Microsoft managed environments. We recommend that customers restrict access to any environments that belong to their subscriptions. This can be done by configuring Network Security Group rules on the environments directly in Azure Portal.

## Windows Remoting (WinRM)
Windows Remoting (WinRM) is disabled on all environments. Although you can enable WinRM on environments that belong to your subscriptions through Azure Portal, we strongly recommend that you do not do this.

> [!WARNING]
> Exceptions to enable WinRM will not be granted for any Microsoft-managed environments. 

## Availability
The guaranteed uptime for Finance and Operations apps is 99.9%. Planned downtime occurs once a month and lasts no longer than eight hours. Because the work completed during the downtime doesn’t always take eight hours, we will always communicate the estimated amount of time that your environments will be down. For more information, see [Get support for Finance and Operations apps or Lifecycle Services (LCS)](../lifecycle-services/lcs-support.md).

### High-availability features
To ensure service availability, all production environments are protected by using default Azure high availability (HA) features. HA functionality provides ways to avoid downtime caused by the failure of a single node within a datacenter, and DR features protect against outages broadly impacting an entire datacenter. Azure availability sets are used to prevent single-point-of-failure events. For more information about Azure availability sets, see [Use availability zones to protect from datacenter level failures](https://docs.microsoft.com/azure/virtual-machines/windows/manage-availability#use-availability-zones-to-protect-from-datacenter-level-failures).
High availability for databases is supported through Azure SQL. For more information, see [Overview of business continuity with Azure SQL Database](https://docs.microsoft.com/azure/azure-sql/database/business-continuity-high-availability-disaster-recover-hadr-overview).

### Disaster recovery features
Production environments are configured with Azure disaster recovery support that includes the following:
- Azure SQL active-geo replication for primary databases, with a Recovery Point Estimate (RPO) of < 5 seconds. For more information, see [Compare geo-replication with failover groups](https://docs.microsoft.com/azure/azure-sql/database/business-continuity-high-availability-disaster-recover-hadr-overview#compare-geo-replication-with-failover-groups). 
- Geo-redundant copies of Azure blob storage (containing document attachments) in other Azure regions. For more information, see [Azure Storage redundancy](https://docs.microsoft.com/azure/storage/common/storage-redundancy).
- Same secondary region for the Azure SQL and Azure blog storage replication.  

Only primary data stores are supported by replication. This means that some application components, such as Management Reporter, and Entity store, which use transformed data from the primary database, must be generated after the recovery site has been set up and the service has started. Customer code artifacts and recovered data stores are used to re-deploy the site, with a Recovery Time Objective (RTO) of 10 hours and a Recovery Point Objective of 5 seconds. For more information, see [Azure SQL Database Point in Time Restore](https://azure.microsoft.com/blog/azure-sql-database-point-in-time-restore/).

## Service availability in Azure Regions
Finance and Operations apps can be deployed into a subset of Microsoft Azure datacenters using Dynamics Lifecycle Services (LCS). Azure is generally available in datacenters and geographical locations around the world. With Finance and Operations apps, customers can specify the region or datacenter where their customer data will be stored. Microsoft may replicate data to other regions for data durability, but we will not replicate or move customer data outside the geographical location. For more details, see the [Service description white paper](https://aka.ms/D365-Cloud-Service-Operations).

> [!IMPORTANT]
> Regardless of where customer data is stored, Microsoft does not control or limit the locations from which customers or their end-users may access it.
For more information, see [International availability of Dynamics 365](https://www.microsoft.com/trustcenter/privacy/dynamics365-operations-location).

### Upcoming changes to region availability
Dynamics 365 solutions consist of a collection of multiple services. Looking across Dynamics 365 applications, the Power Platform and the Azure services that they both depend on, the required matrix of services is quite large and growing. We have locked on a strategy of selecting a subset of data center regions across the globe to simplify ensuring that we have availability of the full portfolio of required services. Our plan is to optimize to have minimal latency between the component services of a solution and as a result, we are focused on having the full portfolio of services available in each of the designated data centers.

Additionally, the Finance and Operations architecture is being enhanced to build on self-service for greater elasticity, stronger reliability, and more seamless maintenance. Customers gain material efficiency by having deeper self-service deployments in fewer data centers. This transition also benefits from selecting a subset of Azure regions. To that effect, the regional availability of Finance and Operations apps will now be <strong>limited to East US, West US, and Central US in North America </strong> for all new projects. For a list of the latest supported regions, see [International availability of Dynamics 365](https://www.microsoft.com/trustcenter/privacy/dynamics365-operations-location).

Support for East US2, West US2, West Central US, North Central US, and South Central US will continue to be available for projects and environments that currently have their data stored in those regions on Microsoft-managed environments. 

> [!Note]
> Microsoft will work with customers to move them to an appropriate data center beginning October 19, 2020. This will happen in a phased approach. Select customers will receive advance notification before we migrate them to a supported region.

If there are other customer workloads that are not part of the Dynamics 365 or Power Platform family that also require proximity to the Dynamics 365 and Power Platform services, Microsoft will work with customers to coordinate a plan for the overall migration. For more information, see [Cloud deployment overview: Frequently asked questions](cloud-deployment-overview.md#frequently-asked-questions).

## Frequently asked questions

### Why does the status display 'Maintenance' on my environment in LCS?
To provide the best experience and performance, Microsoft performs maintenance operations on your environment. During some of these maintenance operations, your environment status may display one of the following statuses:

- Preparing for maintenance
- Prepared for maintenance
- Maintenance in progress

While your environment is in this state and until the status returns to 'Deployed', you will not be able to perform any lifecycle operations, such as package applications. There will be no impact to Finance and Operations apps. Users can continue with normal operations without any service interruption. You will receive an email notification before any maintenance operation puts your environment in this state.

### How do I connect to the SQL database on my Sandbox environment?
Follow these steps to connect to the SQL Database in your Tier 2+ Sandbox environments.

> [!IMPORTANT]
> You will not be able to connect to the Production database directly.

1. Remote Desktop into one of the AOS VMs belonging to the Tier 2+ environment with a database that you want to connect to.
2. Open SQL Server Management Studio.
3. Use these steps to get the connection details:
    1. Go to the **Environment Details** page in **Lifecycle Services portal**.
    2. Get the SQL Server, Database Name, and AXDBAdmin credentials from the **Database Accounts** section.
4. In the **Connect to SQL Server** dialog box, complete the following steps:
    1. Enter (ServerName).database.windows.net, where (ServerName) is the name of your database server obtained from LCS.
    2. Select SQL Server Authentication for **Authentication**.
    3. Use axdbadmin for **Login**.
    4. Enter the password obtained from LCS for axdbadmin.
    5. Select **Options**.
    6. Enter the name of the database obtained from LCS in the **Connect to database** drop-down list.
    7. Select **Connect**.

### How do I access a development instance?
For information about how to access development instances, configure on-premises development VMs, and find configurations settings for developers and administrators, see [Deploy and access development environments](../dev-tools/access-instances.md).

### How do I deploy a demo environment?
A demo environment includes only Microsoft demo data. You can use a demo environment to explore default features and functionality. For more information, see [Deploy a demo environment](deploy-demo-environment.md).

### How do I move my customizations between environments?
To move customizations from a development to a sandbox or production environment, see [Create deployable packages of models](../deployment/create-apply-deployable-package.md)

### Can I bring my own domain name?
You can bring your own domain name if it is running Azure Active Directory (AAD), and the administrator of your AAD instance has enabled the Finance and Operations apps within their AAD. This is usually done through the office email, after you buy a license. When you click the link to accept the offer, AAD is set up for you.

### Can I add guest AAD accounts as users?
You can add guest AAD accounts if you have correctly configured them within Azure Active Directory, and enabled the Finance and Operations apps within your AAD. 

### Why am I no longer able to see the Private AOS machines in one or more of my Tier 2 through Tier 5 Sandbox environments?
The Private AOS VMs were part of your environment configuration as they were needed to secure communication between the AOS and BI machines in the past. With recent updates, all communication between AOS and BI machines are secure directly and no longer need the intermediary Private AOS machines. Therefore, we are in the process of rolling out removing the Private AOS machines. As we are removing the machines in batches, you may notice that only some of your environments have the Private AOS machines removed. This change will not impact functionality or security in any way and will be transparent to you.

### Why am I no longer able to Remote Desktop into one or more of my Tier 1 through Tier 5 Microsoft managed Sandbox environments?
Microsoft managed Tier 1 through Tier 5 sandbox environments require Remote Desktop management endpoints to be restricted to specific IP Address sets (safe list). Microsoft regularly validates that the environments are sufficiently restricted. Microsoft reserves the right to immediately remove any IP Address safe list rules that violate the above guidelines without notice. You may not be able to Remote Desktop into your environment for one of these reasons: 

- Your current IP address is not in the safe list.
- Your IP has changed from the IP address listed in the safe list. 
- Microsoft deleted the rule containing your IP address from the safe list because it violated a guideline.

To regain access to the environment, you will need to add the IP address of the computer from which you are connecting to. To do this, complete the steps [Remote Desktop](#remote-desktop) section earlier in this topic.

### When will the availability of reduced regions go into effect for new onboarding?
Beginning August 1, 2020, new projects for Finance and Operations will be onboarded to the following regions:

- East US
- West US
- Central US

### My environments are currently in the regions that will be deprecated. How will this change affect me?
We will deprecate support for the following regions only for new projects that will be onboarded on or after August 1, 2020:

-	East US2
-	West US2
-	West Central US
-	North Central US
-	South Central US

This will not affect any environments that have their data stored in the deprecated regions before August 2020. In the near future there is a transition plan to move customers in the deprecated regions into the reduced regions.

### I'm unable to redeploy an environment after deleting it, the environment slot is missing. 
This is due to the license expiring, which means that you no longer have the minimum required licenses to obtain an environment slot.  Please review your [subscription status](https://docs.microsoft.com/dynamics365/fin-ops-core/fin-ops/get-started/subscription-overview#how-can-i-find-the-subscription-status) and then reactivate the expired license to enable the redeployment.


