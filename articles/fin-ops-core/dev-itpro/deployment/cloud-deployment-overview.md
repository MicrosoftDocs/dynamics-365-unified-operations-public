---
# required metadata

title: Cloud deployment overview
description: This article describes the cloud environment and subscription, who can perform which tasks, and the data and customizations that you need to manage.
author: LaneSwenka
ms.date: 02/08/2023
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: laswenka
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: Platform Update 8

---
# Cloud deployment overview

[!include [banner](../includes/banner.md)]
 
Working with Microsoft to deploy finance and operations apps in the cloud requires that you understand the environment and subscription that you're deploying to, who can perform which tasks, and the data and customizations that you need to manage. 
We recommend that you sign up for the Full Microsoft FastTrack for Dynamics 365 to help speed your deployment and implementation - it's a program that provides training and consulting to help you realize business value faster. For more information, see [Microsoft FastTrack](/dynamics365/fasttrack/). If you choose to use the Essentials FastTrack program instead, you'll be using the Implementation Project Methodology in Microsoft Dynamics 365 Lifecycle Services to help you manage your implementation project. 

## Customer lifecycle, subscriptions, and environment types
Microsoft assumes that all customers will follow a lifecycle similar to the following for all cloud deployments, and therefore need different environment topologies at each phase. 

- Evaluate
- Develop customizations, if needed.
- Curate a "golden configuration" environment that contains only module configurations without master or transactional data.  This is to be the baseline for your data migration testing and eventual go live.
- Install and test customizations and partner solutions on a tier-1 sandbox (Development or test environment). 
- Test customizations, partner solutions and data configuration on a tier-2 sandbox environment.
- Deploy customizations and data configurations to a production environment with high availability.

At some phases of a project, you may have all of the environments live at once. For more information, about the default licenses and tiers that are available, see the [Dynamics 365 Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544&clcid=0x409).

You may notice the terms cloud hosted or Microsoft subscriptions. A *cloud hosted subscription* means that the customer or partner brings their own Azure subscription and deploys finance and operations apps to it, for evaluation and development purposes only. The customer or partner pays for the resources deployed to their Azure subscription based on the Azure price list. A *Microsoft subscription* means that the customer purchases finance and operations licenses, which will then allow them to deploy environments to an Azure subscription which is managed by Microsoft, therefore, the customer has no separate Azure billing. 

With each Enterprise offer, two environments are included by default:
- One Tier 2 sandbox (multi-box environment) for user acceptance testing (UAT).
- One production environment with high availability (HA). 

Additional environments may be purchased as add-ons. For information about licensing and what is included in Microsoft Dynamics 365, see the [Dynamics 365 Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544&clcid=0x409).

Here's how the lifecycle maps to the available environments.  If you already have environments deployed in your Lifecycle Services project, you can find the Environment Type and Environment Sub type on each environment's details page.

| Lifecycle phase      | Environment tier         | Subscription            | Environment types                 | Environment sub-type 
|-------------------------------|---------------------------------|--------------------------------------|---------------------------------------------|---------------------------------------------|
| Evaluation and analysis       | Tier 1 sandbox | Cloud hosted | Customer-managed | Demo
| Customize                     | Tier 1 sandbox | Cloud hosted or VHD | Customer-managed | Develop
| Golden configuration          | Tier 1 sandbox | Cloud hosted | Customer-managed | Develop
| User acceptance testing (UAT) | Tiers 2-5 sandbox | Microsoft                 | Microsoft-managed or self-service | Not applicable
| Go live                       | Production | Microsoft                    | Microsoft-managed or self-service | Not applicable     

*Tiers 2-5 can be purchased to increase performance of the environment.  The higher the tier, the more compute and database capacity is reserved for your use.*
*For more information about Self-service environment types, see [Self-service deployment overview](infrastructure-stack.md).*

> [!IMPORTANT]
> Tier 1 sandbox environments are no longer Microsoft-managed starting in November 2020. For demo, build, and develop purposes the Tier 1 environments can be deployed on a customer's Azure subscription directly from Lifecycle Services.

### Environment lifecycle operations
Users with the Environment Administrator or Project Owner roles in Lifecycle Services can perform various lifecycle operations on their environments.  These operations often involve downtime on the environment until the task is finished.  Each of these operations is located under or next to the **Maintain** button on each environment details page.

| Lifecycle operation | Description | Learn more
|---------------------|-------------|------------|
| Apply software | Install Microsoft updates, ISV solutions, or your own customization packages. | [Apply updates to cloud environments](apply-deployable-package-system.md)
| Enable access | Allow list your IP for Remote Desktop or database access | See the [Remote Desktop](cloud-deployment-overview.md#remote-desktop) section later in this article
| Restart services | Ability to restart components of your environment | [Restart environment services](../lifecycle-services/restart-environment-services.md)
| Move database | Full data lifecycle management | [Database movement operations](../database/dbmovement-operations.md)
| Maintenance mode | Ability to change configuration with only admin access | [Maintenance mode](../sysadmin/maintenance-mode.md)
| Upgrade | Upgrade code and data from 7.x to the latest version | [Process for moving to the latest update](../migration-upgrade/upgrade-latest-update.md)
| Deallocate | Ability to turn off an environment not being used, or to troubleshoot a failed action | Not applicable
| Start | Ability to turn on an environment for use | Not applicable
| Delete | Ability to delete an environment previously deallocated | Not applicable


## Security and compliance
Finance and operations apps are PA-DSS 3.1 certified which means that all communications between components are secured out-of-the-box. 

All finance and operations front-end virtual machines in Microsoft Azure are configured during deployment to only accept TLS 1.2. 

> [!IMPORTANT]
> Customers who have administrator access to Microsoft-managed sandboxes, including any add-on sandboxes purchased, must follow these guidelines:
> - By default, automatic Windows update is enabled for all Tier 1 - 5 sandboxes and should NOT be disabled. This ensures that any time that Microsoft pushes security or critical infrastructure updates to your environment, your environment receives the latest set of updates and is updated each month with the operating system fixes that Microsoft releases.  
> -	Admin passwords on these environments should NOT be changed. Environments that have admin passwords changed will be flagged by Microsoft. Microsoft reserves the right to reset the admin password, and will do so.  
> - Adding new user accounts to any Microsoft-managed VM ISN'T permitted. Microsoft reserves the right to do this, and will remove the newly added user accounts without providing notice.
>
> finance and operations isn't covered by a FedRAMP ATO at this time. If finance and operations is provisioned in the United States, all customer data at rest is stored in data centers located in the United States. Finance and operations does not support any other Dynamics 365 US Government or Microsoft 365 GCC compliance attributes (for example, access by US screened personnel, and support for CJIS and IRS 1075). 

## Remote Desktop

### Microsoft-managed environments

> [!WARNING]
> Microsoft will be removing the use of Remote Desktop by customers and partners.  Each environment will first have administrator access removed, but still allow non-administrator access to the virtual machines. After this, all access will be removed. For each step of this phased removal, an email notification will be sent to the Notification list setup for each environment. All Remote Desktop access will be removed by November 2020.

Customers are required to complete additional setup to connect to virtual machines (VMs) through Microsoft Remote Desktop (RDP). This additional setup applies to all Microsoft-managed environments, including Tier 1 through Tier 5 sandboxes and add-ons. In order to connect to Tier 1 through Tier 5 sandbox environments, you must explicitly enable access (safe list) from your organization's IP address space. This can be done by a Lifecycle Services user who has access to the **Environment** page (**Maintain** > **Enable Access**) where they can enter the IP address space that will be used to connect to the virtual machines through Remote Desktop. Access rules are either a single IP address (example: 10.10.10.10) or an IP address range (example: 192.168.1.0/24). You may add multiple entries at once as a semicolon (;) separated list (example: 10.10.10.10;20.20.20.20;192.168.1.0/24). These entries are used to configure the Azure Network Security Group that is associated with your environment's virtual network. For more information, see [Security rules](/azure/virtual-network/security-overview#security-rules).

> [!IMPORTANT]
> Customers need to ensure that RDP endpoints are secured through explicit IP safe list rules as mentioned above. The IP safe list rules must adhere to the following conditions.
> - IP safe list rules must NOT use asterisk/zero.
> - Wide IP address ranges must NOT be used.
> - IP address ranges must restrict to the customer's CORPNET. 
> - If computers outside the customer's CORPNET (such as a home office) are used to connect to sandbox environments, only the specific IP addresses of the computers used to connect to the sandbox environments must be added.
> - Azure Datacenter IP address ranges must NOT be added.
> - Public IP addresses, such as a coffee shop location, must NOT be added.     
> - IP safe list rules should be removed when not in use. Periodic review of environment IP safe list rules is recommended.
>
> Microsoft will run periodic tests on the Microsoft-managed environments validating that the environments are sufficiently restricted.
> Microsoft reserves the right to and will remove any IP Address safe list rules that violate the above guidelines, immediately without providing notice.
 
### Customer-managed/Tier-1 environments 
By default, Remote Desktop is enabled for all environments that aren't managed by Microsoft. We recommend that customers restrict access to any environments that belong to their subscriptions. This can be done by configuring Network Security Group rules on the environments directly in Azure Portal.

## Windows Remoting (WinRM)
Windows Remoting (WinRM) is disabled on all environments. Although you can enable WinRM on environments that belong to your subscriptions through Azure Portal, we strongly recommend that you don't do this.

> [!WARNING]
> Exceptions to enable WinRM will not be granted for any Microsoft-managed environments. 

## Availability
The guaranteed uptime for finance and operations apps is 99.9%. Planned downtime occurs once a month and lasts no longer than eight hours. Because the work completed during the downtime doesn't always take eight hours, we'll always communicate the estimated amount of time that your environments will be down. For more information, see [Get support for finance and operations apps or Lifecycle Services](../lifecycle-services/lcs-support.md).

### High-availability features
To ensure service availability, all production environments are protected by using default Azure high availability (HA) features. HA functionality provides ways to avoid downtime caused by the failure of a single node within a datacenter, and DR features protect against outages broadly impacting an entire datacenter. Azure availability sets are used to prevent single-point-of-failure events. For more information about Azure availability sets, see [Use availability zones to protect from datacenter level failures](/azure/virtual-machines/windows/manage-availability#use-availability-zones-to-protect-from-datacenter-level-failures).
High availability for databases is supported through Azure SQL. For more information, see [Overview of business continuity with Azure SQL Database](/azure/azure-sql/database/business-continuity-high-availability-disaster-recover-hadr-overview).

#### Database backup retention
Databases for Microsoft-managed or Self-service Tiers 2-5 environments have automated backups taken by Azure SQL every few minutes. These backups can be restored by using Lifecycle Services point-in-time restore capability up to 14 days in the past. For production type environments, backups can be restored up to 28 days in the past. For Tier 1 or customer-managed environments, database backups aren't automatic and need to be taken manually as often as required.

### Disaster recovery features
Production environments are configured with Azure disaster recovery support that includes the following:
- Azure SQL active-geo replication is configured for the finance and operations database of the production environment. For more information about SQL replication, see [Compare geo-replication with failover groups](/azure/azure-sql/database/business-continuity-high-availability-disaster-recover-hadr-overview#compare-geo-replication-with-failover-groups). 
- Geo-redundant copies of Azure blob storage (containing document attachments) in other Azure regions. For more information, see [Azure Storage redundancy](/azure/storage/common/storage-redundancy).
- Same secondary region for the Azure SQL and Azure blog storage replication.  

Only primary data stores are supported by replication. The Financial reporting services and Entity store database use transformed data from the primary database and must be generated after the recovery site has been set up and the finance and operations service has started. 

## Service availability in Azure regions
Finance and operations apps can be deployed into a subset of Microsoft Azure datacenters using Dynamics Lifecycle Services. Azure is generally available in datacenters and geographical locations around the world. With finance and operations apps, customers can specify the region or datacenter where their customer data will be stored. Microsoft may replicate data to other regions for data durability, but we'll not replicate or move customer data outside the geographical location. For more details, see [Service description for finance and operations apps](../../fin-ops/get-started/service-description.md).

> [!IMPORTANT]
> Regardless of where customer data is stored, Microsoft does not control or limit the locations from which customers or their end-users may access it. For more information, see the following articles:
>
> - [Dynamics 365 Finance, Supply Chain Management, and Commerce in local geographies](deployment-options-geo.md)
> - [Dynamics 365 Finance, Supply Chain Management, and Commerce in US Government Community Cloud (GCC)](us-gcc-deployment.md)
> - [Dynamics 365 Finance, Supply Chain Management, and Commerce operated by 21Vianet in China](china-local-deployment.md)

## Frequently asked questions

### Why does the status display 'Maintenance' on my environment in Lifecycle Services?
To provide the best experience and performance, Microsoft performs maintenance operations on your environment. During some of these maintenance operations, your environment status may display one of the following statuses:

- Preparing for maintenance
- Prepared for maintenance
- Maintenance in progress

While your environment is in this state and until the status returns to 'Deployed', you'll not be able to perform any lifecycle operations, such as package applications. There will be no impact to finance and operations apps. Users can continue with normal operations without any service interruption. You'll receive an email notification before any maintenance operation puts your environment in this state.

### How do I connect to the SQL database on my sandbox environment?
To connect to the SQL database in your sandbox environment, follow the steps in [Enable just-in-time access](../database/database-just-in-time-JIT-access.md).

### How do I access a development instance?
For information about how to access development instances, configure on-premises development VMs, and find configurations settings for developers and administrators, see [Deploy and access development environments](../dev-tools/access-instances.md).

### How do I deploy a demo environment?
A demo environment includes only Microsoft demo data. You can use a demo environment to explore default features and functionality. For more information, see [Deploy a demo environment](deploy-demo-environment.md).

### How do I move my customizations between environments?
To move customizations from a development to a sandbox or production environment, see [Create deployable packages of models](../deployment/create-apply-deployable-package.md)

### Can I bring my own domain name?
You can bring your own domain name if it's running Azure Active Directory (Azure AD), and the administrator of your Azure AD instance has enabled the finance and operations apps within their Azure AD. This is usually done through the office email, after you buy a license. When you click the link to accept the offer, Azure AD is set up for you.

### Can I add guest Azure AD accounts as users?
You can add guest Azure AD accounts if you've correctly configured them within Azure AD and enabled the finance and operations apps within your Azure AD. 

### Why am I no longer able to see the Private AOS machines in one or more of my Tier 2 through Tier 5 sandbox environments?
The Private AOS VMs were part of your environment configuration as they were needed to secure communication between the AOS and BI machines in the past. With recent updates, all communication between AOS and BI machines is secure directly and no longer need the intermediary Private AOS machines. Therefore, we're in the process of rolling out removing the Private AOS machines. As we're removing the machines in batches, you may notice that only some of your environments have the Private AOS machines removed. This change won't impact functionality or security in any way and will be transparent to you.

### Why am I no longer able to Remote Desktop into one or more of my Tier 1 through Tier 5 Microsoft-managed sandbox environments?
Microsoft-managed Tier 1 through Tier 5 sandbox environments require Remote Desktop management endpoints to be restricted to specific IP Address sets (safe list). Microsoft regularly validates that the environments are sufficiently restricted. Microsoft reserves the right to immediately remove any IP Address safe list rules that violate the above guidelines without notice. You may not be able to Remote Desktop into your environment for one of these reasons: 

- Your current IP address is not in the safe list.
- Your IP has changed from the IP address listed in the safe list. 
- Microsoft deleted the rule containing your IP address from the safe list because it violated a guideline.

To regain access to the environment, you'll need to add the IP address of the computer from which you're connecting to. To do this, complete the steps [Remote Desktop](#remote-desktop) section earlier in this article.

### When will the availability of reduced regions go into effect for new onboarding?
Beginning August 1, 2020, new projects for finance and operations will be onboarded to the following regions:

- East US
- West US
- Central US

    > [!IMPORTANT]
    > Central US is no longer an option for Self Service migrations beginning April 1, 2021.

-	East US2
-	West US2
-	West Central US
-	North Central US
-	South Central US

This won't affect any environments that have their data stored in the deprecated regions before August 2020. In the near future there is a transition plan to move customers in the deprecated regions into the reduced regions.

### I'm unable to redeploy an environment after deleting it, the environment slot is missing. 
This is due to the license expiring, which means that you no longer have the minimum required licenses to obtain an environment slot.  Please review your [subscription status](../../fin-ops/get-started/subscription-overview.md#how-can-i-find-the-subscription-status) and then reactivate the expired license to enable the redeployment.

### What does it mean when some deployment regions options are marked as **Data resident region**
If you select a region which isn't **Data resident** you'll see a warning calling out the selected region for environment deployment isn't the same as where Lifecycle Services is storing the project data. 

For example, when using the global Lifecycle Services endpoint, the project data is stored in the United States.  The available regions that show Data Resident include:
* brazilsouth
* uscentral
* useast
* uswest

> [!Note]
> Brazil south is only included in this list due to business and disaster recovery scenarios.  Environments deployed to Brazil South may fail over to US Central in the event of a disaster.  Environments deployed in US regions will only failover to other US regions in the event of a disaster.

For information about migrating Lifecycle Services project data to a different geography, see [Project migration manager](../lifecycle-services/project-migration-manager.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

