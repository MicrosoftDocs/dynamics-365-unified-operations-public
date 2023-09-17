---
# required metadata

title: Service description for finance and operations apps
description: This article provides the service description for finance and operations apps.
author: tomhig
ms.date: 04/27/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: whigginb
ms.search.validFrom: 2021-09-03

---

# Service description for finance and operations apps

[!include[banner](../includes/banner.md)]

Finance and operations apps are enterprise resource planning (ERP) software as a service (SaaS) offerings that are built on and for [Microsoft Azure](https://azure.microsoft.com/overview/what-is-azure/). The finance and operations service provides organizations with ERP functionality that supports their unique requirements and helps them adjust to constantly changing business environments, without requiring that they manage infrastructure. Finance and operations apps can include one or more of the following solution areas:

- [Dynamics 365 Finance](/dynamics365/finance/)
- [Dynamics 365 Human Resources](/dynamics365/human-resources/)
- [Dynamics 365 Supply Chain Management](/dynamics365/supply-chain/)
- [Dynamics 365 Commerce](/dynamics365/commerce/)
- [Dynamics 365 Project Operations](/dynamics365/project-operations/)

Together with [business intelligence](/power-bi/fundamentals/power-bi-service-overview), [infrastructure](https://azure.microsoft.com/global-infrastructure/), [compute](/azure/service-fabric/service-fabric-overview), and [database services](https://devblogs.microsoft.com/azure-sql/running-1m-databases-on-azure-sql-for-a-large-saas-provider-microsoft-dynamics-365-and-power-platform/), these apps enable organizations to run industry-specific and operational business processes. Supported by their implementation partner, customers determine the configuration of the business application logic that best suits their unique business processes. Functionality and business processes can be augmented or extended through one or a combination of the following solutions:

- Built in [personalization experience](personalize-user-experience.md)
- [Microsoft Power Platform](../../dev-itpro/power-platform/overview.md) tools
- [Visual Studio](https://visualstudio.microsoft.com)–based [finance and operations software development kit (SDK)](../../dev-itpro/dev-tools/developer-home-page.md) and [Azure DevOps build automation](../../dev-itpro/dev-tools/developer-home-page.md#build-automation-using-azure)
- Independent software vendor (ISV) solutions from [AppSource](https://appsource.microsoft.com/partners)

Based on requirements, customers choose their solution approach. They work with their implementation partner to define, develop, and test their solution by using the tools and best practices that are provided in [Microsoft Dynamics Lifecycle Services (LCS)](../../dev-itpro/lifecycle-services/lcs.md). There are four common scenarios:

- Standard finance and operations apps "out of the box" configuration (no extensions)
- Finance and operations apps configuration that includes one or more ISV solutions
- Finance and operations apps configuration that includes one or more customer-specific extensions
- Finance and operations apps configuration that includes a combination of customer-specific extensions and one or more ISV solutions

Organizations can match their business growth by easily adding users and business processes through a simple, transparent subscription model. For more information, see the [Dynamics 365 Licensing Guide](https://www.microsoft.com/licensing/docs/view/Microsoft-Dynamics-365).

## Operating model

The operating model of finance and operations apps defines specific roles and responsibilities for the customer, implementation partner, and Microsoft throughout the lifecycle of the service. For more information, see [Cloud operations and servicing](../../dev-itpro/lifecycle-services/cloud-operations-servicing.md).

### Customer activities

Customers work with their partner and [Microsoft FastTrack](/dynamics365/fasttrack/) following the [Dynamics 365 Implementation Guide](https://community.dynamics.com/365/dynamics-365-fasttrack/p/dynamics365implementationguide), the [Success by Design](/dynamics365/fasttrack/success-by-design-overview) framework, and the tools and best practice templates provided in [Lifecycle Services](../../dev-itpro/lifecycle-services/lcs.md) to implement their solution. Common activities include:

- User identity and security management
- Define, develop, and operate business processes
- Define, develop, test, and operate extensions
- Monitor and manage non-production deployments
- Manage application updates and validate extensions
- Manage ISV solutions and 3rd party integrations

### Microsoft responsibilities

Microsoft manages the finance and operations service by deploying, actively monitoring, and servicing customer sandbox and production environments in the Microsoft SaaS subscription. This management includes allocating the required system infrastructure to run the service and proactively communicate with customers about the service's health. Responsibilities include:

**Infrastructure management**
- Security and isolation
- Operating systems and virtualization
- Servers, storage, and networking
- Data center power, networking, cooling

**Application platform management**
- 24/7 application monitoring and notifications
- Diagnostics, platform updates, patches, service updates
- Application routing, load balancing, site replication
- Environment provisioning and management
- Database management, high availability (HA)/disaster recovery (DR), scale, operations
- Compute deployment, scale up, scale down

## System configuration

Finance and operations apps scale according to the transaction volume and user load. Each customer implementation produces a unique solution that consists of the following elements:

- **Data composition** – A unique set of parameters that control behavior, the layout of the organization, the structure of master data (such as financial and inventory dimensions), and the granularity of transaction tracking.
- **Extension and configuration** – Extension mechanisms that use code extensions, ISV solutions, and unique configurations that include workflows, integrations, and report configurations.
- **Usage patterns** – A unique combination of online and batch usage, together with the ability to integrate with upstream and downstream systems for unified data flow and the ability to differentiate based on the information views that customers use in their business processes.

Microsoft configures customer production environments that are sized to handle the transaction volumes and user concurrency. Microsoft is responsible for the following tasks:

- Correctly allocating the resources of production environments, based on the customer's profiling information in the [LCS Subscription estimator](../../dev-itpro/lifecycle-services/subscription-estimator.md)
- Continually monitoring and diagnosing the service availability of production environments
- Analyzing and troubleshooting system performance issues with finance and operations apps

To ensure that an implementation is configured for high performance, customers must complete these tasks:

- Provide accurate usage information about the finance and operations implementation in the [LCS Subscription estimator](../../dev-itpro/lifecycle-services/subscription-estimator.md).
- Build and test extensions for performance and scale.
- Appropriately test data configurations for performance.
- Ensure scalability by doing [performance testing](https://community.dynamics.com/365/b/techtalks/posts/performance-testing-approach-april-30-2018) before go-live.

## Onboarding and implementation

The following table shows typical onboarding and implementation events.

| Request | Expected Microsoft action | Expected customer/implementation partner action |
|---|---|---|
| Initial offer purchase | An LCS project is created after the purchase of the offer, based on an event that is triggered by the customer. | Go through the Enterprise Agreement (EA) or Cloud Solution Provider (CSP) [commercial process](before-you-buy.md). The partner creates a tenant for the customer, if applicable. |
| Add-on purchase | Grant the customer access to the add-on that is selected during implementation. | Not applicable |
| Implementation planning and analysis | Provide relevant tools in LCS, such as [Business process modeler (BPM)](../../dev-itpro/lifecycle-services/bpm-overview.md) and [interoperability with Azure DevOps](../../dev-itpro/lifecycle-services/synchronize-bpm-vsts.md). | Do project planning, set up Azure DevOps, complete system onboarding, and set up admin accounts. |

For more information, see [Onboarding an implementation project](../imp-lifecycle/onboard.md).

## Globalization

Finance and operations apps are served from several Azure regions around the world. Finance and operations apps provide functionality to support different countries/regions and native languages. For more information, see [Localization and regulatory features](../../dev-itpro/lcs-solutions/country-region.md#localization-and-regulatory-features).

### Country/region-specific considerations

- Customers in regulated industry or commercial organizations that do business with entities in France that require local data residency should review [Finance and operations in France](../../dev-itpro/deployment/france-local-deployment.md).
- Customers that have operations in China should review [Azure China Playbook](/azure/china/) and [Finance and operations operated by 21Vianet in China](../../dev-itpro/deployment/china-local-deployment.md).
- Customers that have operations in Russia should review the [Russian personal data localization law](/business-applications-release-notes/october18/dynamics365-finance-operations/russian-regulations-on-prem#when-will-the-cloud-deployment-option-of-dynamics-365-for-finance-and-operations-be-generally-available-for-russia).

### Privacy laws and regulations

For finance and operations apps, Microsoft acts as a processor. As a data processor, finance and operations provides processes and features that help customers comply with privacy obligations as a data controller. For more information, see [Privacy overview](../../dev-itpro/privacy/privacy-guide.md).

## Environment and data management

This section describes some typical environment and data management events that occur in the service.

### Environment and data management events for production instances

LCS provides [self-service tools](../../dev-itpro/deployment/infrastructure-stack.md) and [database movement operations](../../dev-itpro/database/dbmovement-operations.md) that are used to perform environment and data management tasks. Here are some examples:

**Event:** [Requesting a production instance](../imp-lifecycle/go-live-faq.md#when-can-i-configure-and-request-my-production-environment)

- Complete the [Go-live readiness review](../imp-lifecycle/prepare-go-live.md), and submit it to the [Microsoft FastTrack](/dynamics365/fasttrack/) team.
- Complete the [LCS Subscription estimator](../../dev-itpro/lifecycle-services/subscription-estimator.md) before you request a production instance.
- Complete all the implementation tasks that are specified in the [LCS methodology](../../dev-itpro/lifecycle-services/create-methodology.md).

**Event:** [Copying a sandbox database to a production instance](../../dev-itpro/database/dbmovement-scenario-goldenconfig.md)

- Performed for a mock go-live or an actual go-live cutover.

**Event:** [Maintenance mode](../../dev-itpro/sysadmin/maintenance-mode.md)

1. Turn on maintenance mode in LCS.
2. Complete the required maintenance.
3. Turn off maintenance mode in LCS.

### Environment and data management events for non-production instances

LCS provides [self-service provisioning](../../dev-itpro/deployment/infrastructure-stack.md) and [database movement operations](../../dev-itpro/database/dbmovement-operations.md) that are used to perform environment and data management tasks. Here are some examples:

**Event:** [Deploying a new sandbox instance](../../dev-itpro/deployment/deployenvironment-newinfrastructure.md)

- Make sure that all required instances have been [planned](../imp-lifecycle/environment-planning.md), and that the applicable add-on offers have been purchased.
- Run the deployment process in LCS.
- Complete all tasks that are specified in the LCS checklists.
    
>[!NOTE]
>A development sandbox environment is a virtual machine (VM) that is [deployed to the customer's Azure subscription](../../dev-itpro/dev-tools/access-instances.md) and managed by the customer.

**Event:** [Copying a golden configuration database from sandbox to production](../../dev-itpro/database/dbmovement-scenario-goldenconfig.md)

- Performed for a mock go-live or an actual go-live cutover.

**Event:** [Restoring a production point-in-time backup to a non-production instance](../../dev-itpro/database/database-pitr-prod-sandbox.md)

- Run the [Refresh database](../../dev-itpro/database/database-refresh.md) option in LCS.
- Post-copy: Delete or obfuscate sensitive data via scripts, adjust environment-specific application configurations (such as integration endpoints), and enable or add users. Note that these changes are made by applying a [data package](../../dev-itpro/data-entities/data-entities-data-packages.md#import-a-data-package).

**Event:** [Non-production instance database point-in-time restore](../../dev-itpro/database/database-point-in-time-restore.md)

- Accept that the process cannot be undone.
- Run the point-in-time restore operation in LCS.

**Event:** Copying a Tier 2 sandbox database to a development sandbox for troubleshooting and [debugging](../../dev-itpro/database/dbmovement-scenario-debugdiag.md)

- Run the database export operation in LCS on the Tier 2 sandbox environment.
- Import and update the database in the development environment.

## Data backup and retention

Databases for finance and operations environments in the SaaS subscription are protected by automatic backups. For production environments, automatic backups are retained for 28 days, unless Microsoft does a rollback. For sandbox (Tier 2+) environments, they are retained for seven days. A rollback of the production environment can be done if a failure occurs during any planned maintenance update.

For more information about automatic backups, see [Automated backups - Azure SQL Database & SQL Managed Instance](/azure/azure-sql/database/automated-backups-overview?tabs=single-database).

## Service activity responsibilities

The following table describes some typical scenarios and activities for the service. It also indicates whether Microsoft, the customer, or both Microsoft and the customer are responsibly for the activities.

| Activity | Responsibility of Microsoft | Responsibility of the customer |
|---|---|---|
| **Provisioning initial tenants** | | |
| Size the projected load in LCS by using the Subscription estimator tool, and request that specific environments be provisioned. | | X |
| Provision all production instances and non-production instances. | X | |
| Validate the deployed production instances and non-production instances. | | X |
| **Service updates** | |
| Apply service updates to designated non-production and production instances. | X | |
| Manually apply service updates from LCS to sandbox instances. Define, develop, test the update, and provide the code update package back to LCS. | | X |
| Request and schedule extension updates be applied to the production instance. | | X |
| Create a code and data backup for the production instance before any updates are applied. | X | |
| In the event of any failure, roll back the production instance to the code and data backup. | X | |
| **Data management (backup, restore, and update)** | | |
| Back up the database. | X | |
| Determine high availability and a disaster recovery plan. | X | |
| Monitor performance of the production instance database. | X | |
| Tune the production instance database for performance. | X | |
| Perform production instance database point-in-time refresh to a non-production instance. | | X |
| **Updating the infrastructure** | | |
| Schedule regular infrastructure updates. | X | |
| **Scaling up and down (users, storage, and instances)** | | |
| Purchase additional users and non-production add-ons. | | X |
| Update usage changes in the LCS Subscription estimator tool. | | X |
| Report any significant performance issues that affect use of the service. | | X |
| Proactively manage the resources that are required for the applicable service. | X | |
| Investigate and troubleshoot incidents. | X | |
| **Security (user access)** | | |
| Provide user access to the service. | | X |
| Provide LCS project access for the management and operation of instances that were deployed through LCS. | | X |
| **Monitoring production instances** | | |
| Monitor production instances 24/7. | X | |
| Proactively notify the customer about incidents that involve the production instance. | X | |
| **Managing and monitoring non-production instances** | | |
| Manage non-production instances by using LCS. | | X |
| Monitor non-production instances. | | X |

## Service update strategy

In accordance with the [software lifecycle policy](../../dev-itpro/migration-upgrade/versions-update-policy.md), finance and operations apps follow the Microsoft [Modern Lifecycle Policy](../../dev-itpro/migration-upgrade/versions-update-policy.md#modern-lifecycle-policy), which covers products that are continuously serviced and supported. 

Microsoft releases eight service updates to finance and operations apps every year on the following months:

- January
- February
- April
- May
- July
- August
- October
- November

>[!NOTE]
>April and October are major feature release waves. Customers may pause an individual service update for up to three consecutive update cycles.

For more information, review the following topics:

- [One Version service updates overview](../../dev-itpro/lifecycle-services/oneversion-overview.md)
- [Configure service updates through LCS](../../dev-itpro/lifecycle-services/configure-service-updates.md)
- [Pause service updates through LCS](../../dev-itpro/lifecycle-services/pause-service-updates.md)
- [Get notified about service updates through LCS](../../dev-itpro/lifecycle-services/notifications-service-updates.md)
- [Regression testing tools to validate service updates](../../dev-itpro/perf-test/rsat/rsat-overview.md)
- [Dynamics 365 roadmap and release waves](https://dynamics.microsoft.com/roadmap/overview/)

## Security and administrative access

Administrative access to a finance and operations production environment is strictly controlled and logged. Customer data is handled in accordance with the [Microsoft Online Services Terms](https://www.microsoft.com/licensing/terms/productoffering). 

### Customer administrative access

The customer's tenant administrator can access production instances or non-production instances, as described in the following table:

| Environment type | Purpose | Level of customer access |
|---|---|---|
| **Non-production**<br>Tier 1 sandbox | A non-production environment that customers deploy for development, demonstration, or training purposes. | A Tier 1 sandbox (also referred to as a cloud-hosted environment) is a customer-managed VM that is deployed to the customer's Azure subscription from LCS. Because it is a VM in the customer's Azure subscription, the customer has full administrative access to the environment via Remote Desktop. |
| **Non-production**<br>Tier 2 (or higher) sandbox | A non-production environment that customers deploy for user acceptance testing, integration testing, training, staging, or any other pre-production scenario. | Tier 2 and higher sandboxes are deployed to the finance and operations SaaS subscription. Access to Azure SQL databases that are associated with the non-production environment is granted via [just-in-time access](../../dev-itpro/database/database-just-in-time-jit-access.md). Remote Desktop access isn't available. |
| **Production** | A production environment is deployed when the project is [ready for initial go-live](../imp-lifecycle/environment-planning.md#production-system-readiness). | Production environments are deployed to the SaaS subscription. All access is through the browser, service endpoints, or LCS. |

### Microsoft administrative access

The following table shows the different levels of access for different Microsoft administrators:

| Administrator | Customer data |
|---|---|
| Operations responses team<br>(Limited to key personnel only) | Access is granted through a support ticket. Access is audited and limited to the duration of the support activity. |
| Microsoft Customer Support Services (CSS) | No direct access. Customer can use screen sharing to work with support staff to debug issues. |
| Engineering | No direct access. The Operations response team can use screen sharing to work with engineering to debug issues. |
| Others in Microsoft | No access. |

## Monitoring

Microsoft has invested in an extensive toolset to monitor and diagnose customers' production instances. Microsoft monitors customers' production environments 24 hours a day, 7 days a week. For more information, see [Production support and monitoring](../imp-lifecycle/production-support-monitoring.md).

| Microsoft responsibilities | Customer responsibilities |
|---|---|
| <ul><li>Monitor availability of the service.</li><li>Continuously monitor and alert through health metrics and watchdogs for critical components such as Application Object Server (AOS), Batch, Data Import/Export Framework (DIXF), Commerce, and Management Reporter.</li><li>Monitor for performance degradation that is caused by infrastructure services (such as Azure Active Directory \[Azure AD\] and Azure SQL).</li><li>If Microsoft determines that a single process or batch job is causing aberrations, that process or job will be terminated after communication with the customer.</li></ul> | <ul><li>Monitor changes to application configurations and extensions that can cause functional and performance issues.</li><li>Application errors must be diagnosed by using the monitoring tools. Use these tools to diagnose user-reported performance aberrations.</li><li>Inform Microsoft if there is expected load on the system beyond projected peak usage.</li><li>If the applicable service is unavailable in the production instance, the customer can use LCS to report a [production outage](../../dev-itpro/lifecycle-services/report-production-outage.md).</li></ul> |

By submitting support requests online, via LCS, customers enable Microsoft to deliver fast and deep technical expertise in the most effective and efficient manner. Although a phone option is available, it should only be used  if the online option is not available. For more information, see [Phone support options](/power-platform/admin/support-overview?toc=%2Fdynamics365%2Ffin-ops-core%2Fdev-itpro%2Ftoc.json&bc=%2Fdynamics365%2Fbreadcrumb%2Ftoc.json#is-there-a-phone-number-i-can-call-to-contact-support).

## Incident management

Microsoft responds to and fixes incidents based on severity levels. Microsoft's incident severity levels can be changed during initial assessment of the incident, and as more information about the impact and scope becomes available. If the incident is mitigated, the incident severity remains unchanged.

For more information about severity levels, see [this severity table](/power-platform/admin/support-overview#what-is-initial-response-time-and-how-quickly-can-i-expect-to-hear-back-from-someone-after-submitting-my-support-request).

## Business continuity through high availability and disaster recovery 

Microsoft provides business continuity and disaster recovery for production instances of finance and operations apps in the event of Azure region–wide outages. For more information, including service Recovery Time Objective (RTO) and Recovery Point Objective (RPO), see [Business continuity and disaster recovery](../../dev-itpro/sysadmin/business-continuity-disaster-recovery.md).

- **High availability** – HA functionality provides ways to prevent downtime that is caused by the failure of a single node in an Azure datacenter. Each service's cloud architecture uses Azure availability sets for the compute tier to prevent single-point-of-failure events. HA for databases is provided through [Azure SQL HA features](/azure/azure-sql/database/high-availability-sla).
- **Disaster recovery** – [Azure disaster recovery features](/azure/best-practices-availability-paired-regions) protect each service against outages that broadly affect an entire Azure datacenter. Here are some of these features:

    - Azure SQL active-geo replication for the primary database (business database).
    - Geo-redundant copies of Azure Blob Storage (which contains document attachments) in other Azure regions.
    - Secondary region for the Azure SQL and Azure Blob Storage replications.

If disaster recovery is used to recover the customer's production instance, Microsoft and the customer will meet their [incident management](service-description.md#incident-management) responsibilities.

Microsoft's Disaster Recovery plans and procedures are examined regularly through System and Organization Controls (SOC) audits. These compliance audits attest to the technical and procedural process of Microsoft's DR, including Dynamics 365 finance and operations apps. [SOC compliance](/compliance/regulatory/offering-soc-2) audit reports and all other Compliance Reports are available on [Microsoft Trust Center Compliance Offerings](/compliance/regulatory/offering-home).

## Finance and operations support offerings

Technical support is available in markets where finance and operations services are offered. [Support experiences](../../dev-itpro/lifecycle-services/lcs-support.md) are provided in LCS or finance and operations apps. Here are some examples:

- [Issue search](../../dev-itpro/lifecycle-services/issue-search-lcs.md) in LCS
- [Integrated technical support](../../dev-itpro/lifecycle-services/support-experience.md) in finance and operations apps
- [Cloud-powered support](../../dev-itpro/lifecycle-services/cloud-powered-support-lcs.md) in LCS

Microsoft offers finance and operations customers three support plans: Premier, Professional Direct, and the support that is included in the subscription. The level of support differs per plan. The following table shows a comparison of the three plans.

| Support feature | Premier | Professional Direct | Subscription |
|---|---|---|---|
| Unlimited break/fix incident submission | Yes | Yes | Yes |
| 24/7 access via LCS | Yes | Yes | Yes |
| Incident response time | Less than one hour | Less than one hour | Next business day |
| Advisory hours | Pools are acquired per agreement. | No | No |
| Dedicated support account manager | Yes | No | No |
| Dedicated support engineer | Engaged under a separate agreement | No | No |

For more information, see [Support overview](/power-platform/admin/support-overview).

### Process to engage support

In the event of incidents that involve finance and operations apps, customers submit support tickets to Microsoft through LCS. CSS handles the incidents, based on the customer's support plan and the severity of the incident as designated by CSS.

### Service level agreement

Microsoft is committed to an availability rate of 99.9 percent per month of the service. If Microsoft doesn't achieve and maintain the service level for the applicable service as described in the service level agreement (SLA), the customer might be eligible for a credit toward a portion of its monthly service fees for that service. For information about how to initiate a service credit, see the "Claims" section of the [SLA](https://www.microsoft.com/licensing/docs/view/Service-Level-Agreements-SLA-for-Online-Services).

## Important resources

- **[Trust Center](https://www.microsoft.com/trust-center)** – Get information about where your finance and operations data is stored, plus additional information about privacy, compliance, and security procedures.
- **[Licensing terms and documentation](https://www.microsoftvolumelicensing.com/)** – Quickly access licensing terms, conditions, and supplemental information that is relevant to the use of products and services that are licensed through Microsoft volume licensing programs.
- **[Licensing terms](https://www.microsoft.com/licensing/product-licensing/)** – The resources on this page define the terms and conditions for the software and online services products that you purchase through Microsoft commercial licensing programs.
- **[Microsoft Lifecycle Policy](/lifecycle/)** – This page provides consistent and predictable guidelines for the availability of support throughout the life of a product.
- **[Licensing guide](https://www.microsoft.com/licensing/docs/view/Microsoft-Dynamics-365)** – Use this guide to learn more about how to license Dynamics 365.
- **[Customer support](https://dynamics.microsoft.com/support/)** – Get industry-leading support for your Dynamics 365 apps.
- **[Dynamics Lifecycle Services](https://lcs.dynamics.com/)** – Manage your application lifecycle, and move towards predictable, repeatable, high-quality implementations.
- **[Dynamics 365 Implementation Guide](https://aka.ms/D365ImplementationGuideFlip)** - The Dynamics 365 Implementation Guide documents time-tested Success by Design principles and provides prescriptive guidance to architect, build, test, and deploy Dynamics 365 solutions.

## Definitions

### [Azure region](/azure/availability-zones/az-overview#regions)

A geographical region where one or more Azure datacenters exist. Examples include US and Europe.

### [Business process modeler (BPM)](../../dev-itpro/lifecycle-services/bpm-overview.md)

A tool in LCS that helps complete a fit-gap analysis for a given implementation by using business process definitions from American Productivity & Quality Center (APQC) that are supported in finance and operations apps.

### Cloud solution provider

A partner that is part of the Microsoft Cloud Solution Provider (CSP) program, and that provides customers with value-added cloud services, support, one invoice, and customer management at scale.

### Customer

A business entity that consumes finance and operations apps and is represented by a tenant in Office 365.

### Development environment

A non-production sandbox environment that is used to develop extensions. Customers deploy this environment to their own Azure subscription from LCS. This environment can also be used for demonstration, training, or other testing tasks. It's also known as a [Tier 1 sandbox](../imp-lifecycle/environment-planning.md#tier-1-vs-tier-2-and-higher).

### Downtime

Any period when users can't sign in or access their active tenant because of a failure in the unexpired platform or the service infrastructure, as Microsoft determines from automated health monitoring and system logs. Downtime doesn't include scheduled downtime, the unavailability of service add-on features, the inability to access the service because of your modifications to the service, or periods where the scale unit capacity is exceeded.

### Implementation partner

The partner that the customer selects to customize, configure, implement, and manage its finance and operations solutions.

### Incident

An issue that customers encounter while they use the finance and operations service, and that they submit a ticket for via LCS.

### Microsoft Customer Support Services (CSS)

The Microsoft global support team that is dedicated to providing quality service for finance and operations apps.

### Microsoft Dynamics Lifecycle Services (LCS)

The administrative portal for lifecycle management of finance and operations apps from trial, to implementation, to post-production management and support. For more information, see [Lifecycle Services Resources](../../dev-itpro/lifecycle-services/lcs.md).

### Non-production instance

Any of the following instances of a service that the customer uses to validate extensions and perform other development tasks:

- **Sandbox Tier 1** – Developer instance (customer-hosted)
- **Sandbox Tier 2** – Standard Acceptance Testing instance
- **Sandbox Tiers 3–5** – Add-on sandboxes

For more information about Tiers 2 through 5, see [Selecting the correct Tier-2 or higher environment](../imp-lifecycle/environment-planning.md#selecting-the-correct-tier-2-or-higher-environment).

### Production instance

A finance and operations environment that the customer uses to manage its "live" daily transactions and business processes.

### Sandbox environment

A non-production environment that the customer uses for demonstration, training, user acceptance testing, validation of extensions, and other testing tasks.

### Service

Any of the core services that are included in finance and operations apps.

### Service level agreement (SLA) for Microsoft online services

The SLA applies to Microsoft online services. For more information, see [Service Level Agreements](https://www.microsoft.com/licensing/docs/view/Service-Level-Agreements-SLA-for-Online-Services).

### Service update

Microsoft services finance and operations environments on consistent basis through service updates. Customers set their own service update calendar, based on their business needs. For more information, see [One Version service updates](../../dev-itpro/lifecycle-services/oneversion-overview.md).

### [Success by Design](/dynamics365/fasttrack/success-by-design-overview)

The framework that systematically guides an implementation through a series of assessments at critical stages to ensure optimal architecture, security, performance, and user experience for a Dynamics 365 solution.

### User

A single person who uses finance and operations environments, and who is associated with a customer's tenant.

