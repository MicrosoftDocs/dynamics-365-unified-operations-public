---
# required metadata

title: Service description for Dynamics 365 Finance and Dynamics 365 Supply Chain Management apps
description: This topic provides the service description for Dynamics 365 Finance and Dynamics 365 Supply Chain Management.
author: shellybakke
manager: AnnBe
ms.date: 03/04/2021
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: NotInTOC
ms.search.region: Global
# ms.search.industry:
ms.author: sericks
ms.search.validFrom: 2021-03-31
ms.dyn365.ops.version: 10.0.18
---

# Service description for Dynamics 365 Finance and Dynamics 365 Supply Chain Management apps

[!include[banner](../includes/banner.md)]

## Overview

Microsoft Dynamics 365 Finance and Supply Chain Management is a cloud Enterprise Resource 
Planning (ERP) service for enterprises, built on and for Microsoft Azure. It provides organizations with ERP functionality that supports their unique requirements and helps them adjust to constantly changing business environments, without the hassle of managing infrastructure. Finance and Supply Chain Management brings together a set of ERP, business intelligence, infrastructure, compute, and database services in a single offering that enables organizations to run industry-specific and operational business processes that are extendable with specific solutions from Independent Software Vendors (ISV) (see Microsoft AppSource). Organizations can match their business growth by easily adding users and business processes with a simple, transparent subscription model.  

- [Microsoft AppSource](https://appsource.microsoft.com/partners)
- [Licensing Guide](https://dynamics.microsoft.com/finance-and-operations-to-finance-and-scm/)

The Finance and Supply Chain Management cloud service is comprised of the components illustrated below.

![Illustration showing devices in the Finance and Supply Chain Managemnt environments](media/Devices.png)

## Operating model

The operating model of Finance and Supply Chain Management distinguishes specific roles and responsibilities for Customer, Implementation Partner, and Microsoft throughout the lifecycle of the service. 

Microsoft maintains the Finance and Supply Chain Management service by deploying, actively monitoring, and servicing the Customer’s production tenants.  This includes allocating the required system infrastructure to run the service and proactive communication to Customers about the service’s health. 

![Implementation roles and responsibilities](media/implementation-roles-responsibilities.png)

With the support of their Implementation Partner, Customers determine the configuration of the business application logic in Finance and Supply Chain Management to match their unique business processes. Customers can extend Finance and Supply Chain Management with ISV solutions of their choice, unique customizations, or a combination of these. Customers typically choose one of the following configuration scenarios: 

-	**Solution 1:** Standard Finance and Supply Chain Management configuration (no extension) 
-	**Solution 2:** Finance and Supply Chain Management configuration with Customer-specific extensions 
-	**Solution 3:** Finance and Supply Chain Management configuration with one or more ISV solutions and Customer-specific extensions 

For any of these scenarios, the Customer defines, develops, and tests any modifications using Microsoft Dynamics Lifecycle Services (LCS) and tools. 

![Common configuration scenarios](media/common-configuration-scenarios.png)

## System configuration

Finance and Operations scales with transaction volume and User load. Each Customer implementation of Finance and Operations produces a unique solution due to the following variables: 

-	**Data composition:** A unique set of parameters that control behavior, layout of the organization, structure of master data (such as financial and inventory dimensions), and granularity of transaction tracking. 
-	**Extension and configuration:** Extension mechanisms of Finance and Supply Chain Management with code extensions, ISV solutions, and unique configurations including workflows, integrations, and report configurations. 
-	**Usage patterns:** A unique combination of online and batch usage combined with the ability to integrate with upstream and downstream systems for unified data flow and the ability to differentiate based on the information views used by Customers in their business processes. 

Microsoft configures production tenants sized to handle the transaction volumes and user concurrency. Microsoft is responsible for: 

-	Proper allocation of resources of production tenants, based on the Customer’s profiling information in the LCS Subscription Estimator; 
-	Continually monitoring and diagnosing service availability of production tenants; and 
-	Analyzing and troubleshooting system performance issues with Finance and Operations. 

To ensure that an implementation is configured for high performance, Customers must:

-	Provide accurate usage information for the Finance and Supply Chain Management implementation through the LCS Subscription Estimator; 
- Build and test extensions for performance and scale; and 
-	Test data configurations appropriately for performance. 

## Service operations

Service operations reflect various aspects of provisioning and use of Finance and Supply Chain Management, from onboarding and implementation to updates and monitoring. For each successful implementation of Finance and Supply Chain Management, Microsoft, the Customer, and Implementation Partners or ISVs (when applicable) have specific roles and responsibilities. 

![Service operations](media/service-operations.png)

### Onboarding and implementation

Typical onboarding and implementation events and the expected responsibilities for each party are provided in the following table.

| Request | Expected Microsoft action  | Expected Customer/Implementation Partner action |
|-------------------------|-------------------------|-------------------------|
| Initial offer purchase | LCS project is created after the purchase of the offer. | Go through EA or CSP onboarding process. Partner creates tenant for Customer, if applicable. |
| Add-On purchase | Grant Customer access to Add-On selected during the implementation. | Not applicable. |
| Implementation planning and analysis | Provide relevant tools in LCS, such as Business Process Modeler and interoperability with Visual Studio Online. |Project planning, Visual Studio Team Services, System onboarding and admin account setup.|

For more information about the onboarding process, see [Onboard an implementation project](../imp-lifecycle/onboard.md).


### Tenant and data management 

Typical tenant and data management events for the service and the responsibilities for each party are described in the following table for
production instances.

| Customer's request  | Customer's responsibility  | Microsoft's responsibility  | Microsoft's lead time  |Microsoft's estimated maintenance downtime  |
|-------------------------|-------------------------|-------------------------|-------------------------|-------------------------|
| Deploy a new Production Instance | Request submitted through service request in LCS and available through LCS for self-service deployments.</br></br><ul><li>Accurately complete the sizing questionnaire in the LCS Subscription Estimator before requesting a Production Instance.</li></br><li>Complete all implementation tasks specified in the LCS checklists. | <ul><li>Complete Go live health check from Microsoft Fasttrack Services.</br></li></br><li>Deploy a Production Instance only after Customer has completed all LCS checklists and notify Customer of the provisioned environment through email.</br> | </br>2 business days*</br></blockquote> | </br>N/A</br></blockquote> |
| Copy a Non-Production Instance database to a Production Instance before go-live.<br><br>*(Note: This request is not available if Customer already is live in production)* | Request submitted through service request in LCS and available through LCS for self-service deployments.<br><br><ul><li>Validation and sign-off. | <ul><li>Copy a Non-Production Instance (e.g., Sandbox Tier 2 Add-on) database to a Production Instance as part of the go-live process. | 5 hours* | 1-4 hours|
| Maintenance mode | <ul><li>Put AOS in maintenance mode through LCS.</br></li></br><li>Complete necessary maintenance.</br></li></br><li>Request to put the AOS back into active mode.</br> | N/A | N/A| 2 hours|


Microsoft will provide point in time restoration of Customer's Non-Production Instance databases as described in the following table.

| Customer's request  | Customer's responsibility  | Microsoft's responsibility | Microsoft's lead time  | Microsoft's estimated maintenance downtime  |
|-------------------------|-------------------------|-------------------------|-------------------------|-------------------------|
| New sandbox instance  |Request submitted through service request in LCS and available through LCS for selfservice deployments.</br></br><ul></br><li>Ensure all the instances needed, have been planned and Add-On offers purchased.</li></br><li>Complete all implementation tasks specified in the LCS checklists.</li></br></ul> | <ul></br><li>Ensure instance request is against a base subscription or an AddOn offer.</li></br><li>Deploy the instance and notify the Customer and Implementation Partner.</li></br><li>A sandbox instance is a Tier-1 development or build environment or a Tier-2 (or higher). Tier-2</br>(or higher) environments are multibox environments closer in topology to a production environment. | 2 business days* | N/A|
| Copy golden configuration database from Dev/Test to Sandbox before go-live | <ul></br><li>Validation and sign-off.</br><br><li>Prepare and export the database from a development environment (Tier 1).</br></br><ul></br><li>Trigger the import operation through LCS and update the database to a sandbox environment (Tier 2 or higher). |N/A |N/A | 1-4 hours |
| Copy a Production Instance database to a Non-Production Instance  | Trigger the copy operation through LCS.</br></br><ul></br><li>Post-copy: Delete or obfuscate sensitive data, adjust environment specific application configuration (such as integration endpoints) and enable or add users.</li></br><li>Customer should make these changes by applying a data package.</li></br></ul> | N/A |N/A| 1-4 hours |
| Non-Production Instance database point in time restore |Accept that process cannot be undone.</br>• Trigger the point in time restore operation through Lifecycle Services.</br>| N/A | N/A | 1-8 hours |
| Copy Tier 2 Sandbox database to a Tier 1 Sandbox for troubleshooting and debugging  | Trigger database export operation through LCS on the sandbox environment.</br><ul><li> Import and update the database in Tier 1 environment. | N/A | N/A<| 1-4 hours |


### Data back-up and retention 

Databases are protected by automatic back-ups. Automatic back-ups are
*Databases are protected* retained for 30 days unless Microsoft performs
a rollback. Rollbacks may *by automatic back-ups as* be performed in the
event a failure occurs during any planned maintenance update specified
in **Table 4**.

### Service activity responsibilities 

**Table 3** describes some typical scenarios and activities for the
Service along with the responsibilities of Microsoft, Customer, or both
concerning such activities.

***Table 3.** Activities managed by Microsoft or Customer *

| **Activity ** | **Microsoft ** |
|-------------------------|-------------------------|
| **Provisioning initial tenants ** |  |
| Size projected load in LCS using the Subscription Estimator tool and request specific environment(s) to be provisioned |  |
| Provision all Production Instances and Non-Production Instances | ⚫ |
| Validate the deployed Production Instances and Non-Production Instances |  |
| **Service updates ** |  |
| Microsoft applies service updates to a designated Non-Production and</br>Production Instances | ⚫ |
| Download update from LCS and define, develop, and test the update, and provide code update package back to LCS |  |
| Request extension updates to be applied to the Production Instance |  |
| Create code and data backup for Production Instance before applying any updates | ⚫ |
| In case of any failure, roll back Production instance to code and data backup | ⚫ |
| **Data management** <em>(Backup, restore, and update)</em> |  |
| Backup database | ⚫ |
| Determine HA and disaster recovery plan | ⚫ |
| Monitor Production Instance database performance | ⚫ |
| Tuning the Production Instance database for performance | ⚫ |
| Initiate copy of Production Instance database to Non-Production Instance |  |


| **Activity ** | **Microsoft ** |
|-------------------------|-------------------------|
| **Update infrastructure ** |  |
| Schedule regular infrastructure updates | ⚫ |
| **Scale up and down** <em>(Users, storage, instances)</em> |  |
| Purchase additional users and Non-Production add-ons |  |
| Changes in usage must be updated in the LCS' Subscription Estimator tool |  |
| Report any significant performance issues impacting usage of the Service |  |
| Proactively manage the resources needed for the Service applicable Service | ⚫ |
| Investigate and troubleshoot Incidents | ⚫ |
| **Security** <em>(User access)</em> |  |
| Provide user access to the Service |  |
| Provide LCS project access for managing and operating instances deployed through LCS |  |
| **Monitor Production Instance** |  |
| Monitor Production Instances 24x7 | ⚫ |
| Notify Customer proactively of incidents with the Production Instance | ⚫ |
| **Manage and Monitor Non-Production Instances** |  |
| Manage Non-Production Instances with LCS |  |
| Monitor Non-Production Instances |  |


### Service update strategy and maintenance windows 

Customers must stay current on the latest service updates in accordance
with the [*software lifecycle*
*policy*.](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/migration-upgrade/versions-update-policy)
All versions of Finance and Supply Chain Management will use the new
Microsoft Modern Lifecycle Policy. The Modern Lifecycle covers products
that are serviced and supported continuously.

Service
[*Updates*](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/lifecycle-services/oneversion-overview)
to the Finance and Supply Chain Management application and platform are
handled as follows.

- **Customers that are on version 8.1 and higher:** The application
    > and the platform components are released as a single cumulative
    > update called deployable package for customers to uptake.
    > Microsoft notifies the customer when a new service update is made
    > available. Starting April 2019, Microsoft will update your
    > environments to the latest released update by Microsoft within the
    > maintenance window configured in your LCS project. Unless the
    > service update is paused, the environment will be updated to the
    > latest release. Customers have the option to take the update
    > outside of the scheduled maintenance window. We recommend
    > customers to stay current for a better service experience.

- **Customers that are on version 8.0 and lower:** The application
    > updates are released as granular X++ updates while the platform is
    > released as a cumulative binary update. Microsoft requires each
    > customer to be current on the latest Finance and Supply Chain
    > Management platform update. Starting April 2018, Microsoft will
    > update your environments to the latest release of the platform
    > within the maintenance window configured in your LCS project.
    > Customers can also get the service update via LCS and can apply it
    > to their environments on their own prior to Microsoft initiating
    > the service update.

X++ updates must be applied on a development environment before they
can be deployed on a sandbox, staging, or production environment.
Binary updates can be applied directly on any environment but must be
validated on the Customer's sandbox environment before being promoted
to a production environment. Refer to **Table 4** for more detailed
instructions.

Please note that some service updates may be mandatory and require no
consent. To help protect our Customers and the service, Microsoft may
apply critical security updates directly to a Customer's Finance and
Operations production environment.

*Software lifecycle policy.*

*For more information see the* Finance and Supply Chain Management
**[update
FAQ.](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fdynamics365%2Funified-operations%2Ffin-and-ops%2Fget-started%2Fone-version&data=02%7C01%7Cradhij%40microsoft.com%7Ce4e025be903e43c60cca08d746c30074%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637055675644947045&sdata=6qcz2mjRgRcT44DREigEsse3j8elWcZcxkJlyKRJyKw%3D&reserved=0)
**

### Planned maintenance responsibilities 

Microsoft provides Customers with the types of updates to Finance and
Supply Chain Management set forth in **Table 4.** These updates may
require downtime on the production environment. The downtime window can
be categorized as Microsoft Planned Maintenance (initiated by Microsoft)
or Customer Planned Maintenance (initiated by the Customer). Updates are
scheduled with the Customer via LCS.

The responsibilities of Microsoft, the Implementation Partner, and the
Customer are reflected in **Table 4** for each update type.

***Table 4.** Planned maintenance for updates *

| **Type of update**</br><em>Description</em> |  | **Maintenance window **</br><em>(Microsoft's estimated maintenance downtime)</em> |
|-------------------------|-------------------------|-------------------------|
|  | **Microsoft ** | <blockquote></br>**Customer / Implementation **</br></blockquote></br>**Partner ** |  |
| **Customers that are on version 8.1 and higher ** |  |
| **Service updates**</br><em>Service updates are collections of quality updates and new features for the application and the platform, provided as a deployable package. They are backward compatible</em> | <blockquote></br>Initiate updates to the application within the configured maintenance window.</br></blockquote> | <blockquote></br>Customer must always stay current on the latest version of the application.</br></blockquote> | <blockquote></br>Microsoft initiated maintenance window</br><em>30 minutes – 4 hours*</em></br></blockquote> |
| **Critical update **</br><em>Update that solves a critical issue.</em> | <blockquote></br>Notify Customer of the critical update.</br>Initiate update within the specified timeline.</br></blockquote> | <blockquote></br>Apply the critical update.</br></blockquote> | <blockquote></br>Microsoft initiated maintenance window</br><em>30 minutes – 4 hours</em></br></blockquote> |
| **Extensions **</br><em>Change to the standard business application logic.</em> | <blockquote></br>No action required.</br></blockquote> | <blockquote></br>Validate extensions in</br>Customer's Non-Production Instances and then promote them to Customer's</br>Production Instance.</br></blockquote> | <blockquote></br>Customer initiated maintenance window</br><em>1 – 4 hours</em></br></blockquote> |


| **Type of update**</br><em>Description</em> | **Expected action ** | **Maintenance window **</br><em>Microsoft's estimated maintenance downtime</em> |
|-------------------------|-------------------------|-------------------------|
|  | **Microsoft ** | **Customer/ Implementation **</br>**Partner ** |  |
| **Customers that are on version 8.0 and lower ** |
| **Platform updates** <em>Platform updates are collections of hot fixes and new features for the platform, provided as a deployable package. They are backward compatible. They are also backward compatible with the last major release of the applicable Service.</em> | <blockquote></br>Initiate updates to the platform within the configured maintenance window.</br></blockquote> | <blockquote></br>Customer must always stay current on the latest version of the platform.</br></blockquote> | <blockquote></br>Microsoft initiated maintenance window</br><em>30 minutes – 4 hours** </em></br></blockquote> |
| **Major releases **</br><em>Major releases for the Service include new functionality. The last major update is 8.1.</em> | <blockquote></br>Make the new major release available and publish to LCS.</br></blockquote> | <blockquote></br>Prepare for the upgrade according to the LCS instructions and best practices.</br></blockquote> | <blockquote></br>Customer initiated maintenance window</br><em>5 – 8 hours</em></br></blockquote> |
| **Infrastructure updates** <em>Infrastructure updates are updates made to the underlying infrastructure like OS updates. These are done monthly.</em> | <blockquote></br>Initiate updates within the Microsoft planned maintenance window.</br></blockquote> | <blockquote></br>No action needed.</br></blockquote> | <blockquote></br>Microsoft initiated maintenance window</br><em>1 – 4 hours </em></br></blockquote> |
| **Dynamics 365 for Finance and Supply Chain **</br>**Management **</br><em>IP address whitelisting - </em></br><em>Securing access from </em></br><em>Customer's corpnet to Supply Chain Management.</em> | <blockquote></br>Finance and</br>Operations is an Azure Service and uses Azure IP address range.</br></blockquote> | <blockquote></br>Customers need to whitelist the Azure datacenter ranges for both their Primary and Geo-DR datacenters.</br>Link to doc for IP address ranges for Azure.</br></blockquote> | <blockquote></br>N/A</br><em>N/A</em></br></blockquote> |
| **Security **</br><em>Secure Infrastructure.</em> | <blockquote></br>Microsoft installs</br>Anti-Malware, uses SSL, Rotate secrets, and adheres strictly to SOC/ISO standards.</br></blockquote> | <blockquote></br>Refer to [https://www. microsoft.com/en-us/ trustcenter/security/ dynamics365-security f](https://www.microsoft.com/en-us/trustcenter/security/dynamics365-security)or more details on Security.</br></blockquote> | <blockquote></br>N/A</br><em>N/A</em></br></blockquote> |


| **Type of update**</br><em>Description</em> | **Expected action ** | **Maintenance window **</br><em>Microsoft's estimated maintenance downtime</em> |
|-------------------------|-------------------------|-------------------------|
|  | **Microsoft ** | **Customer/ Implementation **</br>**Partner ** |  |
| **Customers that are on version 8.0 and lower ** |
| **Network Security **</br>**Groups (NSG) **</br><em>With the September LCS release, customers can configure Network Security Group rules to restrict RDP and WinRM access to their Microsoft managed sandbox VMs through LCS. </em> | <blockquote></br>Microsoft disallows Remote Desktop access to Sandbox</br>(Tier 1, Tier 2, Tier 3, Tier 4 &amp; Tier 5) environments over the Internet.</br>For self service deployments, RDP is enabled only for Tier1 sandbox.</br></blockquote> | <blockquote></br>Customers need to whitelist their IP Address ranges via LCS to enable RDP access to their environments in Microsoft managed subscriptions. Refer to [https://docs.microsoft. com/en-us/dynamics365/ unified-operations/ devitpro/deployment/ clouddeploymentoverview#featuresof-thefinance-andoperationsproduction-instance](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/deployment/cloud-deployment-overview#features-of-the-finance-and-operations-production-instance) for more information.</br></blockquote> | <blockquote></br>N/A</br><em>N/A </em></br></blockquote> |
| **ExpressRoute **</br><em>Dedicated connection to </em></br><em>Supply Chain Management.</em> | <blockquote></br>Finance and</br>Operations enabled ExpressRoute over public peering.</br></blockquote> | <blockquote></br>Customers need to work with the Azure ExpressRoute service providers to acquire a dedicated connection to Finance and Supply Chain Management.</br></blockquote> | <blockquote></br>N/A</br><em>N/A</em></br></blockquote> |


\*\*Promoting an update to a Customer's production environment is a
service request to Microsoft that must be initiated from LCS. This is
within the Customer planned maintenance window. Request is planned to be
executed within two business days. Generally, 95% of updates are applied
in less than an hour.

### Microsoft planned maintenance schedule and communication 

Scheduled downtime means periods of downtime related to network,
hardware, or Service maintenance or upgrades. Microsoft will publish
notice or notify Customers at least **five days** prior to the
commencement of such downtime. The default downtime window as listed
below are scheduled on weekends in time windows defined per region to
minimize the impact to the Customers' business.

**Microsoft's Planned Maintenance Schedule. **

- **NAM:** 2 AM to 10 AM

- **EMEA:** 10 PM to 6 AM

- **APAC:** 12 PM to 9 PM

## Security and administrative access 

Administrative access to a Finance and Supply Chain Management
production environment is strictly controlled and logged. Customer Data
is handled in accordance with the Microsoft Online Services Terms.
Customer's tenant administrator can access Production Instances or
Non-Production Instances as described in **Table 5.** Microsoft's
Administrator access is described in **Table 5.**

**Table 5.** Customer's administrative access *Downtime has the meaning
given to it in the
[*SLA*.](https://www.microsoft.com/en-us/licensing/product-licensing/products)
*

*Microsoft Online Services Terms.*

| **Environment type ** | <blockquote></br>**Purpose **</br></blockquote> | <blockquote></br>**Level of Customer access **</br></blockquote> |
|-------------------------|-------------------------|-------------------------|
| **Non-Production Instance - **</br>**Sandbox Tier 1: Developer **</br>**Instance ** | <blockquote></br>Non-Production Instance that Customer can use for development or as build machines or to customize any Service and unit test Customer changes.</br></blockquote> | <blockquote></br>As of platform update 12 for the applicable Service, Customer will not have administrator access to development environment VMs running in the Microsoft subscription. Customer will continue to have full administrative access to the SQL Azure server installed on the environment.</br></blockquote> |
| **Non-Production Instance – **</br>**Sandbox Tier 2: Standard Acceptance Testing Instance (or any Sandbox Tier Add-on) ** | <blockquote></br>Non-Production Instance that Customer can use for user acceptance testing, integration testing, and training of any Service.</br></blockquote> | <blockquote></br>Customer will not have remote desktop access or access to the SQL server associated with the NonProduction Instance. Customer can connect as an administrator to the database.</br></blockquote> |
| **Production Instance ** | <blockquote></br>Use to go-live with any Service.</br></blockquote> | <blockquote></br>All access is only through the Finance and Operations client or through LCS.</br></blockquote> |


**Table 6** details the different levels of access for different
Microsoft administrators.

***Table 6.** Microsoft's administrator access *

| **Administrator ** | <blockquote></br>**Customer data **</br></blockquote> |
|-------------------------|-------------------------|
| **Operations responses team **</br>**<em>{Limited to key personnel only)</em> ** | <blockquote></br>Yes, granted by support ticket. Access is audited and limited to the duration of the support activity.</br></blockquote> |
| **Microsoft Customer Support Services ** | <blockquote></br>No direct access. Customer may use screen sharing to work with support staff to debug issues.</br></blockquote> |
| **Engineering ** | <blockquote></br>No direct access. Operations response team may use screen sharing to work with engineering to debug issues.</br></blockquote> |
| **Others in Microsoft ** | <blockquote></br>No access.</br></blockquote> |


## Monitoring and incident management 

### Monitoring 

Microsoft has invested in an extensive toolset to monitor and diagnose
Customers' production instances. Microsoft monitors Customers'
production environments 24 hours a day, 7 days a week. Customer must
monitor its Production Instances for application configurations and
application errors as described in **Table 7.**

***Table 7.** Monitoring responsibilities *

| **Microsoft's responsibilities ** | <blockquote></br>**Customer's responsibilities **</br></blockquote> |
|-------------------------|-------------------------|
| <ul></br><li>Availability monitoring for the service.</li></br><li>Continuous monitoring and alerts through health metrics and watchdogs for critical components such as AOS, Batch, DIXF, Retail, Management Reporter.</li></br><li>Monitoring for performance degradation caused by infrastructure services (AAD, Azure, SQL etc.).</li></br><li>In the event Microsoft determines that a single process or batch job is causing aberrations, these processes will be thwarted after communication with the Customer.</li></br></ul> | <ul></br><li>Monitor changes to application configurations and extensions that can cause functional and performance issues.</li></br><li>Application errors need to be diagnosed using the monitoring tools.</li></br><li>Diagnose user reported performance aberrations using these tools.</li></br><li>Inform Microsoft in the event that there are expected load on the system beyond projected peak usage.</li></br><li>In the event the applicable Service is unavailable in the Production Instance, Customer can create a "Production down" customer support request using LCS.</li></br></ul> |


### Incident management 

Microsoft responds to and resolves Incidents based on the severity
levels set forth in **Table 8.1** and **Table 8.2.** Microsoft's
Incident severity levels can be changed during initial assessment of the
Incident and as more information about the impact and scope becomes
available. If the Incident is mitigated, then the Incident severity
remains unchanged.

**Table 8.1.** Severity Level Description

| **Classification ** | <blockquote></br>**Description **</br></blockquote> |
|-------------------------|-------------------------|
| **Severity 0** <em>(Sev-0) </em></br>**Catastrophic** | <blockquote></br>• Catastrophic event in which all functions of a service in a region are down or inaccessible.</br>**Note:** Sev-0 Incidents normally start as Sev-1, then get upgraded with management approval based on assessment of impact type/scope.</br></blockquote> |
| **Severity 1** <em>(Sev-1) </em></br>**Critical** | <ul></br><li>Severe outage of a Service caused by confirmed systemic problem, resulting in a broad scope of impact, requiring a Technical Control Bridge and engagement from applicable engineering teams.</li></br><li>Suspected breach of a security or privacy boundary.</li></br></ul> |
| **Severity 2** <em>(Sev-2)</em></br>**Urgent** | <ul></br><li>Service outage with narrow scope of impact (&gt; 25% customers).</li></br><li>Degradation of customer experience caused by confirmed systemic event with broad scope (&gt; 25% customers).</li></br><li>Service outage with limited scope of impact (single organization or subset of users).</li></br></ul> |
| **Severity 3** <em>(Sev-3)</em></br>**Moderate** | <blockquote></br>• Degradation of customer experience caused by confirmed systemic event with narrow scope.</br></blockquote> |
| **Severity 4** <em>(Sev-4) </em></br>**Non-SLA Impacting** | <ul></br><li>Monitoring or Customer reported incidents requiring action to avoid potential service impact.</li></br><li>General maintenance events with no Customer impact.</li></br><li>Standard service change requests.</li></br></ul> |


***Table 8.2.** Incident Scope and Severity Level Impact *

| Incident impact | Entire geo OR &gt; 25% of global footprint | 1 customer OR subset of users belonging to one customer |
|-------------------------|-------------------------|-------------------------|
| Service is unavailable | Sev-1 | Sev-2 |
| Service is usable only through a workaround or critical subset feature is malfunctioning | Sev-2 | Sev-3 |
| Degradation of performance, or non critical subset feature is malfunctioning | Sev-3 | Sev-4 |
| Incidents requiring action to avoid potential impact or service disruption | Sev-3 | Sev-4 |


## Business continuity with high availability and disaster recovery 

Customer's Production Instances include High Availability (HA) and
Disaster Recovery (DR) features.

- **High Availability.** HA functionality provides ways to prevent
    > Downtime caused by the failure of a single node within an Azure
    > datacenter. Each Service's cloud architecture uses Azure
    > availability sets for the compute tier to prevent
    > single-point-of-failure events. HA for databases is supported
    > through Azure SQL (a platform-as-a-service (PaaS) offering from
    > Microsoft).

- **Disaster Recovery.** DR features protect each Service against
    > outages broadly impacting an entire Azure datacenter and include
    > the following:

− Azure SQL active-geo replication for primary database (business
database), with a Recovery Point Objective (RPO) estimate of ≤ 5
seconds.

− Geo-redundant copies of Azure blob storage (containing document
attachments) in other Azure regions.

− Same secondary region for the Azure SQL and Azure blob storage
replications.

The primary data stores are supported for replication. This means that
components for each Service, such Management Reporter and Entity Store,
use transformed data from the primary database, which need to be
generated after the recovery site has been setup and service started.
Customer code artifacts and recovered data stores is used to re-deploy
the site, with a Recovery Time Objective (RTO) of up to 10 hours. This
will enable state replication of the compute nodes along with networking
and other components to set up the secondary site using the recovered
data stores. In the event DR is utilize to recover Customer's Production
Instance, each of Microsoft and Customer will perform the
responsibilities described in **Table 8.1** and **Table 8.2. **

***Table 9.** Responsibilities for Disaster Recovery *

| **Microsoft's responsibilities ** | <blockquote></br>**Customer's responsibilities **</br></blockquote> |
|-------------------------|-------------------------|
| Microsoft provisions a secondary environment in the Azure paired datacenters at the time of deployment of the primary Production Instance.</br>See the business continuity and disaster recovery (BCDR): Azure Paired Regions here [https://docs.microsoft.com/en-us/azure/best-practicesavailability-paired-regions f](https://docs.microsoft.com/en-us/azure/best-practices-availability-paired-regions)or details. | <blockquote></br>None.</br></blockquote> |
| Microsoft enables Geo Redundancy of SQL and Azure Storage at the time of deployment of the primary Production Instance. | <blockquote></br>None.</br></blockquote> |
| Microsoft backs up the VMs regularly using Azure backup. | <blockquote></br>None.</br></blockquote> |
| On outage, Microsoft determines if a failover needs to be executed for Customer and if there will be a data loss. Data loss can be up to 5 sec. For details, see Azure SQL Database Geo-Restore here: [https:// azure.microsoft.com/en-us/blog/azure-sql-database-geo-restore/ ](https://azure.microsoft.com/en-in/blog/azure-sql-database-geo-restore/)</br>In the event of a data loss, Microsoft will send a request to Customer asking for its sign-off on a failover. | <blockquote></br>Customer may need to provide written sign-off to trigger the failover in the event of data loss.</br></blockquote> |
| The applicable Service will be operated in limited mode on failover. Update maintenance cannot be triggered in failover mode. | <blockquote></br>Customer cannot request package deployments or other regular maintenance requests in failover mode.</br></blockquote> |
| Microsoft fails back to the Production Instance in the primary Azure region when the datacenter becomes operational. Normal operations are resumed. | <blockquote></br>Customer may need to sign-off on fail back to the Production Instance in the primary Azure region.</br></blockquote> |


## Application support offerings 

Microsoft offers VL customers three support plans: Premier, Professional
Direct, and the support included in the subscription. The level of
support differs per plan and highlights are provided in the **Table
10.**

***Table 10.** Key VL support service features *

| **Service feature ** | <blockquote></br>**Premier **</br></blockquote> | **Professional direct ** | <blockquote></br>**Subscription **</br></blockquote> |
|-------------------------|-------------------------|-------------------------|-------------------------|
| Unlimited break/fix incidents | <blockquote></br>N/A</br></blockquote> | N/A | <blockquote></br>N/A</br></blockquote> |
| 24x7 support | <blockquote></br>N/A</br></blockquote> | N/A | <blockquote></br>Local business hours</br></blockquote> |
| Fastest response times | <blockquote></br>&lt;1 hour</br></blockquote> | &lt;1 hour | <blockquote></br>Next business day</br></blockquote> |


### Process to engage support 

In case of incidents with Finance and Operations, Customers can submit
support tickets to Microsoft by phone or through LCS. CSS will handle
incidents depending on the Customer's support plan and severity of the
incident as designated by CSS.

## Service Level Agreement 

Microsoft is committed to an availability of 99.9% per month of the
Service. If Microsoft does not achieve and maintain the service level
for the applicable Service described in the SLA, then Customer may be
eligible for a credit towards a portion of its monthly service fees for
the applicable Service. See the "Claims" section of the SLA for details
on how to initiate a service credit.

### Dynamics 365 Finance and Supply Chain Management Service description

**More information about Finance and Supply Chain Management can be
found in the sources published below. **

### Trust Center 

Information on where your Finance and Supply Chain Management data is
stored, plus additional information on privacy, compliance, and security
procedures

### Online Service Terms 

Terms and conditions of Microsoft's online services

### Service Level Agreement 

Service Level Agreement

### Update policies 

Online updates

### Online Services lifecycle support policy 

Support policy

### Licensing guide 

Overview of service licensing

### Customer support 

Details about the three support plans for customers

### Dynamics Lifecycle Services 

Access LCS

**The following table contains the meaning of terms used in this
document. **

**Azure region**

A geographical region where one or more Azure datacenters exist; for
example, US and Europe.

### Business Process Manager (BPM) 

A tool in LCS to help complete a fit-gap analysis for a given
implementation using business process definitions as defined in APQC and
their support within Finance and Operations.

### Cloud Solution Provider (CSP) 

Partners who are part of Microsoft's CSP program and provide Customers
with value-added cloud services, Customer support, one invoice, and
Customer management at scale.

### Customer 

A business entity that consumes Finance and Operations and is
represented by a tenant in Microsoft Office 365.

**Development environment**

Tenant used for developing extensions.

### Downtime 

Any period of time when end users are unable to login or access to their
Active

Tenant, due to a failure in the unexpired Platform or the Service
Infrastructure as Microsoft determines from automated health monitoring
and system logs. Downtime does not include Scheduled Downtime, the
unavailability of Service add-on features, the inability to access the
Service due to your modifications of the Service, or periods where the
Scale Unit capacity is exceeded.

### Implementation Partner 

The partner that Customer choses to customize, configure, implement, and
manage its Finance and Operations solution.

### Microsoft Dynamics Lifecycle Services (LCS) 

Administrative portal for lifecycle management of Finance and Operations
from trial to implementation to post-production management and support.

### Microsoft Online Services Terms (OST) 

The OST contains terms that apply to Customer's use of Online Services.

*Click the links below for more information.*

**Microsoft Customer support (CSS) **

Microsoft's support team dedicated to providing quality service for
Finance and Operations.

### Non-Production Instance 

Any of the following instances of a Service that are used by Customer
for validating extensions and other development tasks:

- **Sandbox Tier 1:** Developer Instance

- **Sandbox Tier 2:** Standard Acceptance Testing Instance

- **Sandbox Tier 3:** Add-on through Sandbox Tier 5 Add-on

### Production Instance 

Instance of Finance and Supply Chain Management used by Customer for
managing its "live" daily transactions.

### Sandbox/staging environment 

Instance of Finance and Supply Chain Management used by Customer for
validating extensions and other development tasks.

### Service 

The core services which are included in Microsoft Dynamics 365 for
Finance and Supply Chain Management; Microsoft Dynamics 365 for Retail;
or both.

### Service Level Agreement for Microsoft Online Services (SLA) 

The SLA applies to Microsoft's Online Services, including Finance and
Supply Chain Management .

### Incident 

An issue with the Finance and Supply Chain Management that Customer
encounters while using the service.

**Update request**

Request raised to Microsoft for specific update.

**User**

A single person consuming Finance and Operations, which is associated
with a Customer's tenant.

33
