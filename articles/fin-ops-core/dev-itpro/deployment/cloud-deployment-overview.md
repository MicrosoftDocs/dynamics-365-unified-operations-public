---
# required metadata

title: Cloud deployment overview
description: This topic describes the cloud environment and subscription that you are deploying to, who can perform which tasks, and the data and customizations that you need to manage for Finance and Operations apps. 
author: kfend
manager: AnnBe
ms.date: 03/16/2020
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
ms.author: kfend
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: Platform Update 8

---
# Cloud deployment overview

[!include [banner](../includes/banner.md)]
 
Working with Microsoft to deploy Finance and Operations apps in the cloud requires that you understand the environment and subscription that you are deploying to, who can perform which tasks, and the data and customizations that you need to manage. 
We recommend that you sign up for the Full Microsoft FastTrack for Dynamics 365 to help speed your deployment and implementation - it's a program that provides training and consulting to help you realize business value faster. For more information, see [Microsoft FastTrack](../../fin-ops/get-started/fasttrack-dynamics-365-overview.md). If you choose to use the Essentials FastTrack program instead, you will be using the Implementation Project Methodology in Lifecycle Services (LCS) to help you manage your implementation project. 

## Customer lifecycle, subscriptions, and deployment topologies
Microsoft assumes that all customers will follow a lifecycle similar to the following for all cloud deployments, and therefore need different environment topologies at each phase. 

- Evaluate
- Develop customizations, if needed
- Install and test customizations and partner solutions on a tier-1 sandbox (Development or test environment) 
- Test customizations, partner solutions and data configuration on a tier-2 sandbox environment
- Deploy customizations and data configurations to a production environment with high availability

At some phases of a project, you may have all of the environments live at once. For more information, about the default licenses and tiers that are available, see the [Dynamics 365 Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544&clcid=0x409).

You may hear the terms, Customer, Partner, and Microsoft subscriptions. A *customer or partner subscription* means that the customer or partner brings their own Azure subscription and deploys Finance and Operations apps to it, for evaluation and development purposes only. The customer or partner pays for the resources deployed to their Azure subscription based on the Azure price list. 
A *Microsoft subscription* means that the customer purchases Finance and Operations licenses which will then allow them to deploy environments to an Azure subscription which is managed by Microsoft, therefore, the customer has no separate Azure billing. With each Enterprise offer, three environments are included by default. 

- One Tier-1 sandbox which is a development or build environment.
- One Tier-2 sandbox (multi-box environment) for user acceptance testing (UAT).
- One production environment with High Availability (HA). This environment is managed and operated by Microsoft.

Additional environments may be purchased as add-ons. For information about licensing and what is included in Microsoft Dynamics 365, see the [Microsoft Dynamics 365 Enterprise edition licensing guide](https://go.microsoft.com/fwlink/?LinkId=866544&clcid=0x409).

Here's how the lifecycle maps to the available environments.

| Lifecycle phase               | Environment                               | Subscription                                        |
|-------------------------------|-------------------------------------------|-----------------------------------------------------|
| Evaluation and analysis       | Demo, one-box                             | Customer or partner subscription.                                |
| Customize                     | Dev/build, one-box                        | Microsoft subscription, partner/customer subscription, or local VM
| User acceptance testing (UAT) | Tier-2 sandbox, multi-box environment | Microsoft subscription                              |
| Go live                       | Production, High Availability multi-box environment                    | Microsoft subscription                              |

## Features of a production instance
A production instance has the following capabilities.

## Security and compliance
Finance and Operations is PA-DSS 3.1 certified which means that all communications between components are secured out-of-the-box. 

All Finance and Operations front-end virtual machines in Microsoft Azure are configured during deployment to only accept TLS 1.2. 

> [!IMPORTANT]
> Customers who have administrator access to Microsoft-managed sandboxes, including any add-on sandboxes purchased, must follow these guidelines:
> - By default, automatic Windows update is enabled for all Tier 1 - 5 sandboxes and should NOT be disabled. This ensures that any time that Microsoft pushes security or critical infrastructure updates to your environment, your environment receives the latest set of updates and is updated each month with the operating system fixes that Microsoft releases.  
> -	Admin passwords on these environments should NOT be changed. Environments that have admin passwords changed will be flagged by Microsoft. Microsoft reserves the right to, and will reset the admin password.  
> - Adding new user accounts to any Microsoft managed VM is NOT permitted. Microsoft reserves the right to, and will remove the newly added user accounts without providing notice.

> [!IMPORTANT]
> Finance and Operations is not covered by a FedRAMP ATO at this time. If Finance and Operations is provisioned in the United States, all Customer Data at rest is stored in data centers located in the United States, as described in the [Trust Center](https://www.microsoft.com/trustcenter/privacy/dynamics365-finance-operations). Finance and Operations does not support any other Dynamics 365 US Government or Office 365 GCC compliance attributes (for example, access by U.S. screened personnel, and support for CJIS and IRS 1075).  

## Remote Desktop

### Microsoft managed environments
Customers are now required to complete additional setup to connect to virtual machines (VMs) through Microsoft Remote Desktop (RDP). This additional setup applies to all Microsoft-managed environments, including Tier 1 through Tier 5 sandboxes and add-ons. In order to connect to Tier 1 through Tier 5 sandbox environments, you must explicitly enable access (whitelist) from your organization’s IP address space. This can be done by a Lifecycle Services (LCS) user who has access to the **Environment** page (**Maintain** > **Enable Access**) where they can enter the IP address space that will be used to connect to the virtual machines through Remote Desktop. Access rules are either a single IP address (example: 10.10.10.10) or an IP address range (example: 192.168.1.0/24). You may add multiple entries at once as a semi-colon(;) separated list (example: 10.10.10.10;20.20.20.20;192.168.1.0/24). These entries are used to configure the Azure Network Security Group that is associated with your environment’s virtual network. For more information,  see [Filter network traffic with network security groups](/azure/virtual-network/virtual-networks-nsg).

> [!IMPORTANT]
> Customers need to ensure that RDP endpoints are secured through explicit IP whitelist rules as mentioned above. The IP whitelist rules must adhere to the below conditions to ensure the environments are secure and the Intellectual Property is protected.
> - IP whitelist rules must NOT use star/zero, opening the environment to internet
> - Wide IP address ranges must NOT be used.
> - IP address ranges must restrict to the Customer's CORPNET 
> - If computers outside the customer's CORPNET (e.g. a home office) are used to connect to the Sandbox environment(s), only the specific IP addresses of the computers used to connect to the sandbox environment(s) must be added.
> - Azure Datacenter IP Address ranges must NOT be added
> - Public IP addresses, such as a coffee shop location must NOT be configured.     

> [!WARNING]
> Microsoft will run periodic tests on the Microsoft Managed environments validating that the environments are sufficiently restricted.
> Microsoft reserves the right to and will remove any IP Address whitelist rules that violate the above guidelines, immediately without providing notice.
 
### Partner/Customer managed environments 
By default, Remote Desktop is enabled for all non-Microsoft managed environments. We recommend that customers restrict access to any environments that belong to their subscriptions. This can be done by configuring Network Security Group rules on the environments directly in Azure Portal.

## Windows Remoting (WinRM)
Windows Remoting (WinRM) is disabled on all environments. Although you can enable WinRM on environments that belong to your subscriptions through Azure Portal, we strongly recommend that you do not do this.

> [!WARNING]
> Exceptions to enable WinRM will not be granted for any Microsoft-managed environments. 

## Availability
The guaranteed uptime for Finance and Operations apps is 99.9%. Planned downtime occurs once a month and lasts no longer than eight hours. Because the work completed during the downtime doesn’t always take eight hours, we will always communicate the estimated amount of time that your environments will be down. For more information, see [Get support for Finance and Operations apps or Lifecycle Services (LCS)](../lifecycle-services/lcs-support.md).

### High-availability features
To ensure service availability, all production environments are protected by using default Azure high availability (HA) features. HA functionality provides ways to avoid downtime caused by the failure of a single node within a datacenter, and DR features protect against outages broadly impacting an entire datacenter. Azure availability sets are used to prevent single-point-of-failure events. For more information about Azure availability sets, see [Azure availability sets guidelines for Windows VMs](/azure/virtual-machines/windows/infrastructure-availability-sets-guidelines).
High availability for databases is supported through Azure SQL. For more information, see [Overview of business continuity with Azure SQL Database](/azure/sql-database/sql-database-business-continuity).

### Disaster recovery features
Production environments are configured with Azure disaster recovery support that includes the following:
- Azure SQL active-geo replication for primary databases, with a Recovery Point Estimate (RPO) of < 5 seconds. For more information, see [Overview: Failover groups and active geo-replication](/azure/sql-database/sql-database-geo-replication-overview). 
- Geo-redundant copies of Azure blob storage (containing document attachments) in other Azure regions. For more information, see [Geo-redundant storage](/azure/storage/common/storage-redundancy-grs).
- Same secondary region for the Azure SQL and Azure blog storage replication.  

Only primary data stores are supported by replication. This means that some application components, such as Management Reporter, and Entity store, which use transformed data from the primary database, must be generated after the recovery site has been set up and the service has started. Customer code artifacts and recovered data stores are used to re-deploy the site, with a Recovery Time Objective (RTO) of 10 hours and a Recovery Point Objective of 5 seconds. For more information, see [Azure SQL Database Point in Time Restore](https://azure.microsoft.com/blog/azure-sql-database-point-in-time-restore/).

## Service availability 
Finance and Operations apps can be deployed into different Microsoft Azure datacenters using Dynamics Lifecycle Services (LCS). Azure is generally available in datacenters and geographical locations around the world. With Finance and Operations apps, customers can specify the region or datacenter where their customer data will be stored. Microsoft may replicate data to other regions for data durability, but we will not replicate or move customer data outside the geographical location. For more details, see the [Service description white paper](https://aka.ms/D365-Cloud-Service-Operations).

> [!IMPORTANT]
> Regardless of where customer data is stored, Microsoft does not control or limit the locations from which customers or their end-users may access it.
For more information, see [Where your Finance and Operations data is stored](https://www.microsoft.com/trustcenter/privacy/dynamics365-operations-location).

## Frequently asked questions

### Why does the status display 'Migrating' on my environment in LCS?
To provide the best experience and performance, Microsoft has to perform maintenance operations on your environment. During some of these maintenance operations, your environment status may display 'Migrating'. You will not be able to perform any lifecycle operations, such as package applications, until the status returns to 'Deployed'. There will be no impact to Finance and Operations apps. Users can continue with normal operations without any service interruption. You will receive an email notification before the maintenance operation is initiated.

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

### How do I deploy a demo environment
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
Microsoft managed Tier 1 through Tier 5 sandbox environments require Remote Desktop management endpoints to be restricted to specific IP Address sets (whitelist). Microsoft regularly validates that the environments are sufficiently restricted. Microsoft reserves the right to immediately remove any IP Address whitelist rules that violate the above guidelines without notice. You may not be able to Remote Desktop into your environment for one of these reasons: 
- Your current IP address is not in the whitelist.
- Your IP has changed from the IP address listed in the whitelist. 
- Microsoft deleted the rule containing your IP address from the whitelist because it violated a guideline.

To regain access to the environment, you will need to add the IP address of the computer from which you are connecting. To do this, complete the steps in the section, [Remote Desktop](#remote-desktop) earlier in this document.
