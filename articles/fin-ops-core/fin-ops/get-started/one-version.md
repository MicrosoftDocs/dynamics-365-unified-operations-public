---
# required metadata

title: One Version service updates FAQ
description: This article provides clarity about the service updates, processes, and tools that you can use to stay current in a consistent, predictable, and seamless manner.
author: laneswenka
ms.date: 03/02/2023
ms.topic: article
ms.prod: 
ms.technology: 
ms.custom: bap-template
# optional metadata

# ms.search.form:  [Operations AOT form name to tie this article to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: laswenka
ms.search.validFrom: 2018-10-31 
ms.dyn365.ops.version: 8.1
---

# One Version service updates FAQ

[!include[banner](../includes/banner.md)]

This FAQ is intended to provide clarity about the service updates, processes, and tools that you can use to prepare for the change. We will continue to add information to this article as required.

For more information about One Version service updates, see [One Version service updates overview](../../dev-itpro/lifecycle-services/oneversion-overview.md).

### Can the updates be delayed? What is the policy?

Yes, customers can pause, delay, or opt out of an update via the update settings in Microsoft Dynamics Lifecycle Services (LCS) projects, provided that all their sandbox and production environments are no more than three versions behind the latest available update. Customers can choose to pause up to three consecutive updates. Here is an example of a delayed update: 

- The customer is currently on version 10.0.22.
- The customer can pause updates 10.0.23, 10.0.24, and 10.0.25.
- The customer must take the 10.0.26 update when it's available.

For information about how to pause an update, see [Pause service updates through Lifecycle Services (LCS)](../../dev-itpro/lifecycle-services/pause-service-updates.md).

### If the release date is in early April, when will the general availability package become available?

Production updates for a release will be scheduled for the first, second, and third weeks of the month. Depending on the configuration that you set up in LCS, you will receive updates during that specific week. Sandbox updates will always be scheduled the week before the production update. The configuration setup is available in LCS.

As an example, for the April 10.0.25 release, Microsoft performed updates during the weekends of April 1, April 8, or April 15, depending on the configuration that you set up in LCS. Sandbox updates will always be scheduled a week before the update.

Customers can always choose to apply the update at an earlier time or at a time that is more convenient than the suggested times in LCS. If a customer is already on the latest version, the automatic update will be canceled.

## Service updates

### What product versions are affected by service updates?

| Version       | Description |
|---------------|-------------|
| 8.1 and later | All customers on version 8.1 and later will be scheduled for automatic monthly updates. These updates will be combined application and platform updates. You are required to be on an update that is no more than three updates behind the current update. For information about how to pause an update, see [Pause service updates](../../dev-itpro/lifecycle-services/pause-service-updates.md). |

### What do the service updates contain?

For release 8.1 and later, service updates will contain application changes (including financial, reporting, and Commerce changes) and platform changes that are critical improvements to the service. These changes include regulatory updates. New experiences will be configurable. The service updates are backward compatible. There will be a single version that represents the update.

### What is a regulatory update?

A regulatory update is a new feature or an existing feature change that is required by law (usually for a specific country or region). The regulatory update is always required by a specific law enforcement date (LED), and should be enabled by that date or earlier.

### What is the upcoming schedule of updates?

Each year, seven service updates are released. You have the option to apply them when it's convenient for you, or you can let Microsoft automatically apply them, based on the selected maintenance window. You are required to be on an update that is no more than three updates behind the current update.

To view a targeted release schedule, see [Service update availability](public-preview-releases.md).

### Are there any major updates post 8.1?

There are two major updates each year: the April update and the October update. New experiences can be enabled by these updates. Major updates don't require code or data upgrade. Breaking changes will be communicated 12 months in advance, so that customers can plan accordingly. Breaking changes will be introduced only during major updates.

### What does it mean when an update is backward compatible?

Backward compatibility covers binary and functional compatibility. Binary compatibility means that you can apply an update on any runtime environment without having to recompile, reconfigure, or redeploy customizations. It also means that, on a development environment at design time, X++ public and protected application programming interfaces (APIs) and metadata aren't modified or deleted. If Microsoft must break compatibility by removing obsolete APIs, this change will be communicated 12 months in advance and will follow a deprecation schedule. Functional compatibility is about the user experience. All new experiences will be available on an opt-in basis for a 12-month period.

Backward compatibility doesn't include non-X++/metadata APIs. Microsoft reserves the right to update versions of any dependencies that the product uses, and to remove dependencies, without early warning. Microsoft doesn't commit to maintain backwards compatibility of dependent software libraries, unless this commitment is expressly stated. 

For more information about deprecation guidelines, and deprecated methods and metadata elements, see [Deprecation of methods and metadata elements](../../dev-itpro/migration-upgrade/deprecation-deletion-apis.md).

### Can I apply a Platform service update to my existing 8.1 or later environments?

Customers on version 8.1 or later will be able to apply only the 8.1.x or v10.x service updates. Platform-only service updates can't be applied to version 8.1.x or later. 

### Service updates for on-premises deployments

The policy and schedule for service updates are now the same for both cloud deployments and on-premises deployments. For example, the option to delay up to three consecutive updates applies to both types of deployment. The process for applying each of these updates remains slightly different. For more information, see [Apply updates to on-premises deployments](../../dev-itpro/deployment/apply-updates-on-premises.md#update-an-on-premises-deployment).

## Process

### How will Microsoft ensure the quality of releases?

Ensuring the quality of releases is a fundamental principle that is enabled through a series of progressive, rigorous, automated validations, as described in [Service update availability](public-preview-releases.md).

### Can I select the day and time to update?

Customers can configure the day and maintenance time windows in LCS. The service update, which is based on your update settings, will start within 15 minutes. Customers who opt in to receive LCS notifications will receive an email that includes update instructions. Customers will be able to select the designated tier 2/UAT sandbox for the update. Customers will have seven calendar days to do testing and validation.

Customers can optionally apply the update earlier to all environments through LCS. The production-ready deployable package will be made available to all customers via the Action Center in LCS. All additional sandboxes will automatically be updated on the same day as the production environment. For more information, see [Configure service update](../../dev-itpro/lifecycle-services/configure-service-updates.md).

### A service update was applied to the environment. In LCS, what does the number on the tile for this environment represent?

Microsoft will automatically apply the same service update to all customers. Microsoft will continue to service the latest update. The number on the tile for that environment in LCS represents the cumulative number of hotfixes that are available to be applied to your environment. Because Microsoft will automatically apply only the same version to all customers, you will be responsible for applying the cumulative hotfix package if it's required.

### How do I update to the latest version?

Users can update to the latest version by using the tiles on the environment details page in LCS. After the update is released by Microsoft, the tile will show the available update. Customers can choose to apply the update on their own by going through the update experience on their sandbox and production environments. 

### How do I update the production environment to the same version after Microsoft updates the sandbox environment?

When Microsoft updates a sandbox environment, the package that is used for the update is saved in the project's asset library. The name of the package is prefixed by the words "Service Update." Because the package was already applied to the sandbox environment, you can mark it as a Release Candidate. You can then go to the production environment and schedule to apply the package, just as you might schedule the application of any other update.

### What is the expected downtime?

The expected downtime for a successful update is 30 minutes to 1 hour. However, we ask for three hours of downtime in case issues occur while the update is applied. We're actively working to reduce the downtime that is required, and you should expect improvements in the next few months.

### What is the process for deprecation?

Before any feature is removed from the product, the deprecation notice will be announced in the product documentation 12 months before the removal.

For breaking changes that only affect compilation time, but that are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these changes are functional updates that must be made to the compiler.

### Can I delay an update?

Yes, you can pause, delay, or opt out of an update via the update settings in LCS projects, provided that all your sandbox and production environments are no more than three versions behind the latest available update. After this period, an update will be scheduled and automatically applied by Microsoft. The update experience for a delayed update will incur additional downtime.

### Can I delay an update for longer than three consecutive service updates because of seasonal activity or another business reason? 

No. Service updates will automatically be applied to the sandbox. Then, seven days later, the update will be applied to all additional sandbox and production environments, if those environments are more than three service updates old. A customer can pause only up to three consecutive updates in a row. For example, if a customer on version 10.0.22 chooses to pause updates 10.0.23, 10.0.24, and 10.0.25, service update 10.0.26 will automatically be applied first to the sandbox environment and later to all additional sandbox and production environments. 

### What happens to an environment that is running a finance and operations app version that is no longer supported?

For environments that are running a finance and operations app version that is no longer supported, a warning message will appear at the top of the environment details page in LCS.

For all Microsoft-managed environments, and sandbox and production environments in on-premises implementation projects, some LCS functionality might not be available when an environment is running a finance and operations app version that is no longer supported. This functionality includes the ability to complete the following actions:

- Enable maintenance mode.
- Use all capabilities that are provided for moving databases on an environment or across environments.
- Enable firewall access to SQL Server databases.
- Download Regression suite automation tool (RSAT) certificates.
- Regenerate RSAT certificates.

After you apply a service update for a supported version, this functionality will be available in the affected environment.

> [!NOTE]
> In this article, versions are noted in the following ways:
>
> - Version N is the latest version, such as 10.0.25
> - Version N-1 is one version older than N, such as 10.0.24
> - Version N-2 is two versions older than N, such as 10.0.23
> - Version N-3 is three versions older than N, such as 10.0.22
> - Version N-4 is four versions older than N, such as 10.0.21 (In this example, customers on version 10.0.21 **can't** pause updates.)

If you encounter an issue on a version that has reached its end of service (N-4), the support team is not able to take your case. You must update to the latest update and then report the issue if it persists.

### How do the automatic updates affect my Microsoft-managed additional sandbox environments in my LCS implementation project? 

All additional sandbox environments will be updated during the same update window as your production environment, and they will be updated to the same release version that is used for the production update. The update will also apply to additional sandboxes environments that are on versions that are supported in the N-3 lifecycle policy. 

### What if one additional sandbox environment is on N-1 and another is on N-4 (the default sandbox environment and the production environment are on less than version N)? 

All environments will be updated to version N. 

### What if the default sandbox environment is manually updated to the exact same version or higher version than the automatic update version? 

Automatic updates for the production environment and all additional sandbox environments will be updated to the current N version.  
 
The default sandbox environment update will be canceled. 

### What if the default sandbox environment is manually updated to an older version than the automatic update version? 
 
The default sandbox environment, production environment, and all additional sandbox environments will be updated to the current N version.

### What if the production environment is manually updated before the production environment email is sent? 

Automatic updates for the production environment and all additional sandbox environments will be canceled. 

### What if the production environment is manually updated after the production environment email is sent? 

Automatic updates for the production environment will be canceled, but all additional sandbox environments will be updated to version N.

### What if I find an issue during the sandbox update?

If you find an issue when doing validations in a sandbox environment, you can request to skip the update directly through LCS by providing a valid support ticket number and a business justification. 

### What if I find a critical issue during sandbox testing, but I can't pause the production automatic update?

Critical issues should always be submitted to the Support team via LCS as soon as they are identified. The support staff will work with you to fix the critical issue.

### How much time do I have for validation?

You will have seven calendar days for validation after the update is applied to your sandbox environment. If you need more time, you can access the deployable package via the Action Center in LCS and apply it to your environments. In this way, you will get additional time to test the update before a production roll-out.

### What happens when the service update is completed?

After the service update is applied by Microsoft, you will receive a notification that indicates whether the update was successful, or whether it could not be applied. There are several reasons why an update might be unable to be applied:

- **Pending Package Sign-off** – If a package is pending signoff, Microsoft won't apply the service update to production.
- **Deployment Failure** – If there was a deployment failure, the environment will be rolled back to the original state.
 
### If there is a failure, can I reschedule the update to be automatically applied?

You won't actually be able to reschedule the update. However, you can apply the package when it's convenient for you, just as you might schedule the application of any other update.

### Will critical hotfixes be automatically applied to my sandbox/production environment during automatic update?

The service update that will be made generally available and automatically applied to all customers will contain hotfixes and potentially new functionality. If a critical issue is reported after the service update has been applied, customers can pull that cumulative hotfix update from the tile in LCS.

### How will my ISVs stay current?

Service updates to customer environments will be backward compatible, and no action is required by the independent software vendors (ISVs). ISVs develop on the minimum required platform release that their code depends on. Breaking changes will have a 12-month lead time, to enable ISVs to include them and do validation. We recommend that the ISVs be part of our [Partner early access program](https://experience.dynamics.com/insider/), so that they can get early access to the platform bits and validate their solutions against the update before it's made generally available.

### What about new features?

All new features will be available on an opt-in basis for a 12-month period. They won't require any change management until you choose to enable them.

### Are batch jobs suspended during a service update?

Batch jobs are suspended during the maintenance windows and resume when the maintenance is completed.

For information about how to pause an update, see [Pause service updates through Lifecycle Services (LCS)](../../dev-itpro/lifecycle-services/pause-service-updates.md).

## Tools

### How can I get early access to non-released platform updates?

Beginning with version 10.0.26, the preview package for all service updates is made available to all customers through the Shared Asset Library in LCS, under **Software deployable package**. Preview packages can be deployed to development or test environments. They can't be used in production environments. You agree to the program terms at installation. Sign up for access to preview packages (formerly known as the Preview Early Access Program (PEAP)) is no longer required.

To be in the first group of customers to take service updates to production, you can join the [First release program](https://aka.ms/FirstReleaseFnO). While enrolled in First Release, Microsoft will keep your system current with the latest updates. First Release customers are always updated before general availability.

### Is any tooling available to support testing of the latest release?

The [Regression Suite Automation Tool](../../dev-itpro/lifecycle-services/using-task-guides-and-bpm-to-create-user-acceptance-tests.md) is [available now](https://www.microsoft.com/download/details.aspx?id=57357). This tool significantly reduces the time and cost of user acceptance testing (UAT). UAT is typically required before you take a Microsoft application update or apply custom code and configurations to your production environment. It lets functional power users record business tasks by using the Task recorder and convert them into a suite of automated tests, without having to write source code. Test libraries are stored and distributed in LCS by using the Business Process Modeler (BPM) libraries, and they are fully integrated with Azure DevOps for test execution, reporting, and investigation. Test data parameters are decoupled from test steps and stored in Excel data files.

### How can I test and validate that the integrations continue to work?

Data task automation lets you easily repeat many types of data tasks and validate the outcome of each task. You can also use automated testing of data entities by using task outcome validation. For more information, see [Data task automation](../../dev-itpro/data-entities/data-task-automation.md).

### How can I determine what is changed in a service update?

The "What's new or changed" documentation is the primary source for the details of each service update. The [release plans](/business-applications-release-notes/) are the primary source of information for all new features and changes for a future release. Features will also include Help topics on Microsoft Learn as needed.

### If I'm not doing active development/recompilation of my code, how will I learn whether there is a deprecated feature that will affect me? 

Deprecated features will be documented for each release. For more information, see [Removed or Deprecated features](../../dev-itpro/migration-upgrade/deprecated-features.md).

## Preparing for One Version

### How can I log an extensibility request?

Extensibility requests can be logged in LCS. Details are available in the [Extensibility requests](../../dev-itpro/extensibility/extensibility-requests.md) article. Note the following timelines for logging and using the available extensions.

| Date         | Extensibility requests |
|--------------|------------------------|
| January 2019 | All extensibility requests must be logged by January 1, 2019. We ask that ISVs and customers analyze the code and make these requests by that date. We will provide exceptions to stay on 7.3 after April 2019 only if the request has been filed by January 1, 2019. |
| December 2019 | For the requests that were logged by January 1, 2019, extensions will be available on or before December 31, 2019. Customers who use these extensions are required to move to the current version by April 2020. |

### What does end of service mean?

Microsoft won't provide any fixes to issues on versions that have reached their end of service. Microsoft also won't investigate or troubleshoot any issue that you encounter on a version that is older than three service updates. If you encounter an issue on a version that has reached its end of service, you must update to the latest update and then report the issue if it persists.

All environments will continue to be operated by Microsoft. All automatic processes around your environments, such as monitoring or self-healing, will also continue as long as the environment is on a supported version.

### Will individual hotfixes be supported?

Individual hotfixes won't be supported after 8.1. Customers must update to the latest cumulative update available to apply the fix (such as 8.1.1). Critical fixes will also be cumulative and available through the LCS servicing experience.

### Will you notify me about critical hotfixes released for the monthly update that I'm on? 

Customer reported issues are searchable via LCS Issue search. You can sign up to be notified when an open issue is resolved.

## Commerce service updates

### What options are available to help minimize the impact on my Commerce cloud components?

Commerce cloud components will require the same down time as your Dynamics 365 headquarters. In an upcoming release, the Retail Cloud Scale Unit (RCSU) will be available to reduce and further schedule updates to your deployment. For more information about RCSU, see the published release information on our [documentation](/business-applications-release-notes/October18/dynamics365-retail/planned-features) and [release notes](/business-applications-release-notes/?panel=products1#pivot=products) sites.

### Will there be options to take individual hotfixes for my commerce solution components?

All fixes and updates for commerce components will be cumulative.

### What are the maintenance downtime requirements that might affect channel operations?

For retailers that have a business need for redundancy, Modern POS offline capability enables core point of sale (POS) operations to be available for use while disconnected from the internet or while the cloud environment is being updated. Stores that use Commerce Scale Unit will also continue to operate with support for core POS operations during cloud maintenance windows. For more information, see [Online and offline point of sale (POS) operations](../../../commerce/pos-operations.md).

### When will I have to update my in-store components?

To maintain support, all in-instore components must be running released software that is less than one year old. Customers are responsible for updating self-hosted components (such as components that are installed in stores or in privately managed datacenters) and ensuring that the installed versions of those components are actively supported.

### Will there continue to be backward compatibility for the in-store components?

Updates to components that are hosted in the cloud will continue to preserve backward compatibility with component versions that are self-hosted by the retailer for 12 months after the release date for that version. (These components include components that are installed in stores or in privately managed datacenters: Modern POS, Commerce Scale Unit, or Hardware Station.) Self-hosted components don't have to be updated at the same time as cloud-hosted components. They can be updated on a separate cadence, so that there is time to roll updates out to stores.

### What options are available for updating in-store components across my organization?

Customers can choose to manually update self-hosted components at each store, or they can use mass update tools such as Microsoft System Center Configuration Manager and Microsoft Intune.

### What options do I have to slowly enable new functionality across my channels?

Microsoft provides several mechanisms for progressively rolling out and enabling functional enhancements across stores, devices, and users.

- **Screen layout designer** – Most visual elements in POS are configured and centrally managed by an administrative user in the customer organization. Therefore, new POS operations won't automatically appear in POS unless they are explicitly configured for inclusion in corresponding screen layouts. Screen layouts are configured by using Screen layout designer, and can be specific to a store or a POS device. For more information, see [Screen layouts for the point of sale (POS)](../../../commerce/pos-screen-layouts.md).
- **Functionality profiles, POS permissions, Commerce parameters** – Significant elements of functionality in POS are typically configurable by the user. These elements can be configured through functionality profiles, POS permissions, commerce parameters, or other controls that allow for device-level, register-level, store-level, or user-level functionality control in applicable scenarios.
- **Modern POS and Commerce Scale Unit** – Because Modern POS and Commerce Scale Unit are self-hosted by the retailer, topologies that include either of these components enable updates to be rolled out at a separate (and slower) cadence and in a more granular fashion than cloud-only topologies.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
