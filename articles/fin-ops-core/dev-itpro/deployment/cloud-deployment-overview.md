---
title: Cloud deployment overview
description: Learn about the cloud environment and subscription, who can perform which tasks, and the data and customizations that you need to manage.
author: LaneSwenka
ms.author: laswenka
ms.topic: overview
ms.custom: 
  - bap-template
ms.date: 04/02/2026
ms.reviewer: johnmichalak
ms.collection: get-started
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form:
ms.dyn365.ops.version: Platform Update 8
---

# Cloud deployment overview

[!include [banner](../includes/banner.md)]

To work with Microsoft to deploy finance and operations apps in the cloud, you need to understand the environment and subscription that you're deploying to, who can perform which tasks, and the data and customizations that you need to manage.
Sign up for the Full Microsoft FastTrack for Dynamics 365 to help speed your deployment and implementation. This program provides training and consulting to help you realize business value faster. For more information, see [Microsoft FastTrack](/dynamics365/fasttrack/). If you choose to use the Essentials FastTrack program instead, use the Implementation Project Methodology in Microsoft Dynamics 365 Lifecycle Services to help you manage your implementation project.

## Customer lifecycle, subscriptions, and environment types

Microsoft assumes that all customers follow a lifecycle similar to the following for all cloud deployments, and therefore need different environment topologies at each phase.

- Evaluate
- Develop customizations, if needed.
- Curate a "golden configuration" environment that contains only module configurations without master or transactional data. This environment serves as the baseline for your data migration testing and eventual go live.
- Install and test customizations and partner solutions on a tier-1 sandbox (Development or test environment).
- Test customizations, partner solutions, and data configuration on a tier-2 sandbox environment.
- Deploy customizations and data configurations to a production environment with high availability.

At some phases of a project, you might have all of the environments live at once. For more information about the default licenses and tiers that are available, see the [Dynamics 365 Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544&clcid=0x409).

You might notice the terms cloud hosted or Microsoft subscriptions. A *cloud hosted subscription* means that the customer or partner brings their own Azure subscription and deploys finance and operations apps to it, for evaluation and development purposes only. The customer or partner pays for the resources deployed to their Azure subscription based on the Azure price list. A *Microsoft subscription* means that the customer purchases finance and operations licenses, which then allow them to deploy environments to an Azure subscription that Microsoft manages. Therefore, the customer has no separate Azure billing.

Each Enterprise offer includes two environments by default:

- One Tier 2 sandbox (multibox environment) for user acceptance testing (UAT).
- One production environment with high availability (HA).

You can purchase additional environments as add-ons. For information about licensing and what is included in Microsoft Dynamics 365, see the [Dynamics 365 Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544&clcid=0x409).

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
> Starting in November 2020, Microsoft no longer manages tier 1 sandbox environments. For demo, build, and develop purposes, you can deploy the tier 1 environments on a customer's Azure subscription directly from Lifecycle Services.

### Environment lifecycle operations

Users with the Environment Administrator or Project Owner roles in Lifecycle Services can perform various lifecycle operations on their environments.  These operations often involve downtime on the environment until the task finishes.  You can find each of these operations under or next to the **Maintain** button on each environment details page.

| Lifecycle operation | Description | Learn more
|---------------------|-------------|------------|
| Apply software | Install Microsoft updates, ISV solutions, or your own customization packages. | [Apply updates to cloud environments](apply-deployable-package-system.md)
| Enable access | Allow list your IP for Remote Desktop or database access. | See the [Remote Desktop](cloud-deployment-overview.md#remote-desktop) section later in this article.
| Restart services | Restart components of your environment. | [Restart environment services](../lifecycle-services/restart-environment-services.md)
| Move database | Full data lifecycle management. | [Database movement operations](../database/dbmovement-operations.md)
| Maintenance mode | Change configuration with only admin access. | [Maintenance mode](../sysadmin/maintenance-mode.md)
| Upgrade | Upgrade code and data from 7.x to the latest version. | [Process for moving to the latest update](../migration-upgrade/upgrade-latest-update.md)
| Deallocate | Turn off an environment that isn't being used, or to troubleshoot a failed action. | Not applicable
| Start | Turn on an environment for use. | Not applicable
| Delete | Delete an environment that you previously deallocated. | Not applicable

## Security and compliance

Finance and operations apps are PA-DSS 3.1 certified, which means that all communications between components are secured automatically.

All finance and operations front-end virtual machines in Microsoft Azure are configured during deployment to accept only TLS 1.2.

> [!IMPORTANT]
> Customers who have administrator access to Microsoft-managed sandboxes, including any add-on sandboxes purchased, must follow these guidelines:
>
> - By default, automatic Windows update is enabled for all Tier 1 - 5 sandboxes and you shouldn't disable it. This setting ensures that any time Microsoft pushes security or critical infrastructure updates to your environment, your environment receives the latest set of updates and is updated each month with the operating system fixes that Microsoft releases.  
> - Don't change admin passwords on these environments. Microsoft flags environments when admin passwords are changed. Microsoft reserves the right to reset the admin password, and it will do so.  
> - Don't add new user accounts to any Microsoft-managed VM. Microsoft reserves the right to remove the newly added user accounts without providing notice.
>
> Finance and operations isn't covered by a FedRAMP ATO at this time. If you provision finance and operations in the United States, all customer data at rest is stored in data centers located in the United States. Finance and operations doesn't support any other Dynamics 365 US Government or Microsoft 365 GCC compliance attributes (for example, access by US screened personnel, and support for CJIS and IRS 1075).

## Remote Desktop

### Microsoft-managed environments

> [!WARNING]
> Microsoft is removing the use of Remote Desktop by customers and partners.  Each environment first loses administrator access but still allows non-administrator access to the virtual machines. After this step, all access is removed. For each step of this phased removal, an email notification is sent to the notification list set up for each environment. Microsoft removes all Remote Desktop access by November 2020.

To connect to virtual machines (VMs) through Microsoft Remote Desktop (RDP), you need to complete additional setup. This setup applies to all Microsoft-managed environments, including Tier 1 through Tier 5 sandboxes and add-ons. To connect to Tier 1 through Tier 5 sandbox environments, you must explicitly enable access (allow list) from your organization's IP address space. A Lifecycle Services user with access to the **Environment** page (**Maintain** > **Enable Access**) can enter the IP address space that you use to connect to the virtual machines through Remote Desktop. Access rules are either a single IP address (example: 10.10.10.10) or an IP address range (example: 192.168.1.0/24). You can add multiple entries at once as a semicolon (;) separated list (example: 10.10.10.10;20.20.20.20;192.168.1.0/24). These entries configure the Azure Network Security Group that is associated with your environment's virtual network. For more information, see [Security rules](/azure/virtual-network/security-overview#security-rules).

> [!IMPORTANT]
> You need to ensure that RDP endpoints are secured through explicit IP allow list rules as mentioned earlier. The IP allow list rules must adhere to the following conditions.
>
> - Don't use asterisk or zero in IP allow list rules.
> - Don't use wide IP address ranges.
> - Restrict IP address ranges to your organization's CORPNET.
> - If you use computers outside your organization's CORPNET (such as a home office) to connect to sandbox environments, add only the specific IP addresses of the computers used to connect to the sandbox environments.
> - Don't add Azure Datacenter IP address ranges.
> - Don't add public IP addresses, such as a coffee shop location.
> - Remove IP allow list rules when not in use. Periodic review of environment IP allow list rules is recommended.
>
> Microsoft runs periodic tests on the Microsoft-managed environments to validate that the environments are sufficiently restricted.
> Microsoft reserves the right to remove any IP address allow list rules that violate the preceding guidelines, immediately and without providing notice.

### Customer-managed/Tier-1 environments

By default, Remote Desktop is enabled for all environments that aren't managed by Microsoft. Restrict access to any environments that belong to your subscriptions. You can restrict access by configuring Network Security Group rules on the environments directly in Azure portal.

## Windows Remoting (WinRM)

Windows Remoting (WinRM) is disabled on all environments. Although you can enable WinRM on environments that belong to your subscriptions through the Azure portal, don't enable it.

> [!WARNING]
> Microsoft doesn't grant exceptions to enable WinRM for any Microsoft-managed environments.

## Availability

The guaranteed uptime for finance and operations apps is 99.9%. Planned downtime occurs once a month and lasts no longer than eight hours. Because the work completed during the downtime doesn't always take eight hours, the estimated amount of time that your environments are down is always communicated. For more information, see [Get support for finance and operations apps or Lifecycle Services](../lifecycle-services/lcs-support.md).

### High-availability features

To ensure service availability, all production environments use default Azure high availability (HA) features. HA functionality provides ways to avoid downtime caused by the failure of a single node within a datacenter, and DR features protect against outages that broadly impact an entire datacenter. Azure availability sets prevent single-point-of-failure events. For more information about Azure availability sets, see [Use availability zones to protect from datacenter level failures](/azure/virtual-machines/windows/manage-availability#use-availability-zones-to-protect-from-datacenter-level-failures).
High availability for databases is supported through Azure SQL. For more information, see [Overview of business continuity with Azure SQL Database](/azure/azure-sql/database/business-continuity-high-availability-disaster-recover-hadr-overview).

#### Database backup retention

For Microsoft-managed or self-service Tiers 2-5 environments, Azure SQL takes automated backups every few minutes. You can restore these backups by using Lifecycle Services point-in-time restore capability up to 14 days in the past. For production type environments, you can restore backups up to 28 days in the past. For Tier 1 or customer-managed environments, database backups aren't automatic and need to be taken manually as often as required.

### Disaster recovery features

Production environments are configured with Azure disaster recovery support that includes the following features:

- Azure SQL active-geo replication is configured for the finance and operations database of the production environment. For more information about SQL replication, see [Compare geo-replication with failover groups](/azure/azure-sql/database/business-continuity-high-availability-disaster-recover-hadr-overview#compare-geo-replication-with-failover-groups).
- Geo-redundant copies of Azure blob storage (containing document attachments) in other Azure regions. For more information, see [Azure Storage redundancy](/azure/storage/common/storage-redundancy).
- Same secondary region for the Azure SQL and Azure blob storage replication.  

Only primary data stores are supported by replication. The Financial reporting services and Entity store database use transformed data from the primary database and must be generated after the recovery site is set up and the finance and operations service starts.

## Service availability in Azure regions

You can deploy finance and operations apps to a subset of Microsoft Azure datacenters by using Dynamics Lifecycle Services. Azure is generally available in datacenters and geographical locations around the world. By using finance and operations apps, you can specify the region or datacenter where you want to store your customer data. Microsoft might replicate data to other regions for data durability, but it doesn't replicate or move customer data outside the geographical location. For more details, see [Service description for finance and operations apps](../../fin-ops/get-started/service-description.md).

> [!IMPORTANT]
> Regardless of where customer data is stored, Microsoft doesn't control or limit the locations from which customers or their end-users can access it. For more information, see the following articles:
>
> - [Dynamics 365 Finance, Supply Chain Management, and Commerce in local geographies](deployment-options-geo.md)
> - [Dynamics 365 Finance, Supply Chain Management, and Commerce in US Government Community Cloud (GCC)](../../fin-ops/deployment/us-gcc-deployment.md)
> - [Dynamics 365 Finance, Supply Chain Management, and Commerce operated by 21Vianet in China](../../fin-ops/deployment/china-local-deployment.md)

## Frequently asked questions

### Why does the status display 'Maintenance' on my environment in Lifecycle Services?

To provide the best experience and performance, Microsoft performs maintenance operations on your environment. During some of these maintenance operations, your environment status might display one of the following statuses:

- Preparing for maintenance
- Prepared for maintenance
- Maintenance in progress

While your environment is in this state and until the status returns to 'Deployed', you can't perform any lifecycle operations, such as package applications. There's no impact to finance and operations apps. Users can continue with normal operations without any service interruption. You receive an email notification before any maintenance operation puts your environment in this state.

### How do I connect to the SQL database on my sandbox environment?

To connect to the SQL database in your sandbox environment, follow the steps in [Enable just-in-time access](../database/database-just-in-time-JIT-access.md).

### How do I access a development instance?

For information about how to access development instances, configure on-premises development VMs, and find configuration settings for developers and administrators, see [Deploy and access development environments](../dev-tools/access-instances.md).

### How do I deploy a demo environment?

A demo environment includes only Microsoft demo data. Use a demo environment to explore default features and functionality. For more information, see [Deploy a demo environment](deploy-demo-environment.md).

### How do I move my customizations between environments?

To move customizations from a development environment to a sandbox or production environment, see [Create deployable packages of models](../deployment/create-apply-deployable-package.md).

### Can I bring my own domain name?

You can bring your own domain name if it's running Microsoft Entra ID, and the administrator of your Microsoft Entra instance enables the finance and operations apps within their Microsoft Entra ID. This configuration is usually done through the office email, after you buy a license. When you click the link to accept the offer, Microsoft Entra ID is set up for you.

### Can I add guest Microsoft Entra accounts as users?

You can add guest Microsoft Entra accounts if you correctly configure them within Microsoft Entra and enable the finance and operations apps within your Microsoft Entra.

### Why am I no longer able to see the Private AOS machines in one or more of my Tier 2 through Tier 5 sandbox environments?

The Private AOS VMs were part of your environment configuration as they secured communication between the AOS and BI machines. With recent updates, all communication between AOS and BI machines is secure directly and no longer needs the intermediary Private AOS machines. Therefore, Microsoft is in the process of rolling out removal of the Private AOS machines. As the removal process rolls out in batches, you might notice that only some of your environments have the Private AOS machines removed. This change doesn't impact functionality or security in any way and is transparent to you.

### Why can't I use Remote Desktop to connect to one or more of my Tier 1 through Tier 5 Microsoft-managed sandbox environments?

Microsoft-managed Tier 1 through Tier 5 sandbox environments require Remote Desktop management endpoints to be restricted to specific IP address sets (allow list). Microsoft regularly validates that the environments are sufficiently restricted. Microsoft reserves the right to remove any IP address allow list rules that violate the preceding guidelines without notice. You might not be able to use Remote Desktop to connect to your environment for one of these reasons:

- Your current IP address isn't in the allow list.
- Your IP address changed from the IP address listed in the allow list.
- Microsoft deleted the rule containing your IP address from the allow list because it violated a guideline.

To regain access to the environment, add the IP address of the computer you're connecting from. To do this, complete the steps in the [Remote Desktop](#remote-desktop) section earlier in this article.

### When does the availability of reduced regions go into effect for new onboarding?

Starting August 1, 2020, onboard new projects for finance and operations to the following regions:

- East US
- West US
- Central US

    > [!IMPORTANT]
    > Central US is no longer an option for self-service migrations starting April 1, 2021.

- East US2
- West US2
- West Central US
- North Central US
- South Central US

This change doesn't affect any environments that store their data in the deprecated regions before August 2020. In the near future, there's a transition plan to move customers in the deprecated regions into the reduced regions.

### I can't redeploy an environment after deleting it because the environment slot is missing

This issue happens when your license expires. You no longer have the minimum required licenses to get an environment slot. Review your [subscription status](../../fin-ops/get-started/subscription-overview.md#how-can-i-find-the-subscription-status) and reactivate the expired license to enable the redeployment.

### What does it mean when some deployment regions options are marked as **Data resident region**

If you select a region that isn't **Data resident**, you see a warning that the selected region for environment deployment isn't the same as where Lifecycle Services stores the project data.

For example, when you use the global Lifecycle Services endpoint, the project data is stored in the United States. The available regions that show Data Resident include:
- brazilsouth
- uscentral
- useast
- uswest

> [!NOTE]
> Brazil South is only included in this list due to business and disaster recovery scenarios. Environments deployed to Brazil South might fail over to US Central in the event of a disaster. Environments deployed in US regions only fail over to other US regions in the event of a disaster.

For information about migrating Lifecycle Services project data to a different geography, see [Project migration manager](../lifecycle-services/project-migration-manager.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
