---
# required metadata

title: One Version service updates FAQ
description: This topic provides clarity on service updates, processes, and tools that you can use to stay current in a consistent, predictable, and seamless manner.
author: ShellyBakke
ms.date: 04/21/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: smiller
ms.search.validFrom: 2018-10-31 
ms.dyn365.ops.version: 8.1
---

# One Version service updates FAQ

[!include[banner](../includes/banner.md)]

In July 2018 we announced a [change to the way we deliver Dynamics 365 updates](https://cloudblogs.microsoft.com/dynamics365/2018/07/06/modernizing-the-way-we-update-dynamics-365/) that will help you stay current in a consistent, predictable, and seamless manner. In June 2019, based on customer feedback we announced [New flexible service updates being made available](https://cloudblogs.microsoft.com/dynamics365/bdm/2019/06/03/new-flexible-service-updates-for-dynamics-365-for-finance-and-operations/). This FAQ is intended to provide clarity on the service updates, processes, and tools you can use to prepare for it. We'll continue to add additional information to this topic as needed.

For more information about One Version service updates, see [One Version service updates overview](../../dev-itpro/lifecycle-services/oneversion-overview.md).

### Can the update be delayed? What is the policy?
Yes, the customer can pause, delay, or opt-out of an update via Update Settings in Lifecycle Services projects provided that all of their sandbox and production environments are no more than three versions behind the latest available update.  A customer can choose to pause up to three consecutive updates. The following is an example of a delayed update: 

- The customer is currently on version 10.0.22.
- The customer can pause updates 10.0.23, 10.0.24, and 10.0.25.
- The customer must take the 10.0.26 update when it is available.

To pause an update, refer to [Pause service updates through Lifecycle Services (LCS)](../../dev-itpro/lifecycle-services/pause-service-updates.md).
  
### With a release date in early April, when will the general availability package be made available?
Production updates for a monthly release will be scheduled for the first, second, and third weeks in of the month. Depending on the configuration that you set up in Lifecycle Services (LCS), you'll receive updates during that specific week.
 
For the April 10.0 release, Microsoft will perform updates during the weekends of April 6, April 13, or April 20 based on the configuration that you set up in LCS. Sandbox updates will always be scheduled a week before the update. The configuration setup is available in LCS.

Customers can always choose to apply the update at an earlier time, or if there's a more convenient time than the suggested times in Lifecycle Services. If the customer is on the latest version the auto update will be canceled.

## Service updates

### What product versions are impacted by service updates?

| Version       | Description |
|---------------|-------------|
| 8.1 and later | All customers on version 8.1 and later will be scheduled for automatic monthly updates. These updates will be combined application and platform updates. You are required to be on an update that's no more than three updates behind the current update. To pause an update, refer to [Pause service updates](../../dev-itpro/lifecycle-services/pause-service-updates.md). |

### What does the service update contain?

For release 8.1 and later, service updates will contain application (including financial, reporting, and Commerce) and platform changes that are critical improvements to the service including regulatory updates. New experiences will be configurable. The service updates are backward compatible. There will be a single version representing this update.

### What is a regulatory update?

A regulatory update is a new feature or an existing feature change required by law (usually for a specific country/region). The regulatory update is always required by a specific law enforcement date (LED) and should be enabled by this date or earlier.

### What's the upcoming schedule of updates?

Service updates are available. You have the option to apply the update when it's convenient for you, or let Microsoft auto-apply the service updates based on the selected maintenance window. You are required to be on an update that's no more than three updates behind the current update.

To see a targeted release schedule, see [Service update availability](public-preview-releases.md).

### Are there any major updates post 8.1?

There are two major updates each year: the April update and the October update. New experiences can be enabled with these updates. Major updates won't require code or data upgrade. Breaking changes will be communicated 12 months in advance such that customers can plan accordingly. Such a change will only be introduced during a major update.

### What does it mean when an update is backward compatible?

Backward compatibility covers binary and functional compatibility. Binary compatibility means that you can apply an update on any runtime environment without needing to recompile, reconfigure, or redeploy customizations. This also means that on a development environment at design time, X++ public and protected APIs and metadata aren't modified or deleted. If Microsoft needs to break compatibility by removing obsolete APIs, it will be communicated 12 months in advance and follow a deprecation schedule. Functional compatibility is about user experience, all new experiences will be opt-in for a 12-month period.

Backward compatibility doesn't include non-X++/metadata APIs. Microsoft reserves the right to update versions of any dependencies the product uses, as well as remove dependencies without early warning. Microsoft doesn't commit to maintain backwards compatibility of dependent software libraries unless expressly stated. 

For more information on deprecation guidelines and deprecated methods and metadata elements, see [Deprecation of methods and metadata elements](../../dev-itpro/migration-upgrade/deprecation-deletion-apis.md).

### Can I apply a Platform service update to my existing 8.1 or later environments?

Customers on version 8.1 or later will only be able to apply the 8.1.x or v10.x service updates. Platform only service updates cannot be applied to version 8.1.x or later. 

### Will Platform updates be able to be scheduled and delay/pause by customers?

Yes, customers who are on version 7.3 are able to schedule platform updates directly in Lifecycle Services. A delay/pause experience is also available.

### Service updates for on-premises deployments

The policy and schedule for service updates are now the same for both cloud and on-premises deployments. This includes, for example, the option to delay applying up to three consecutive updates. How to apply each of these updates remains slightly different. For more information, see [Apply updates to on-premises deployments](../../dev-itpro/deployment/apply-updates-on-premises.md#update-an-on-premises-deployment).

## Process

### How will Microsoft ensure quality of releases?

Ensuring quality of the release is a fundamental principle that's enabled through a series of progressive, rigorous, automated validations as described in [Service update availability](public-preview-releases.md).

### Can I select the day and time to update?

Customers can configure the day and maintenance time windows in LCS. The service update, which is based on your update settings, will start within 15 minutes. Email will be sent to customers who opt in to receive LCS notifications with instructions included on how to update. Customers will be able to select the designated tier 2/UAT sandbox for the update. Customers will have 7 calendar days for testing and validation.

Customers can optionally choose to apply the update earlier to all environments through LCS. The production-ready, deployable package will be made available to all customers via the Action Center in Lifecycle Services. All additional sandboxes will be auto updated on the same day as the production environment. For more information, see [Configure service update](../../dev-itpro/lifecycle-services/configure-service-updates.md).


### A service update was applied to the environment, when looking at the tile in Lifecycle Services for this environment what does the number on the tile represent?

The same service update will be auto applied to all customers by Microsoft. Microsoft will continue to service the latest update. The tile in LCS for that environment represents the cumulative number of hotfixes that are available to be applied to your environment. Because Microsoft will only auto apply the same version to all customers, you'll be responsible for apply the cumulative hotfix package if it's required.

### How do I update to the latest version?

Users can update to the latest version using the tiles on the Environment details page in LCS. After the update is released by Microsoft, the tile will show the update available. Customers can choose to apply the update on their own by going through the update experience on their sandbox and production environments. 

### How do I update the production environment to the same version after Microsoft updates the sandbox environment?

When Microsoft updates a sandbox environment, the package that is used for the update is saved in the project's asset library. The name of the package is prefixed by the words "Service Update." Because the package was already applied to the sandbox environment, you can mark this package as a Release Candidate. You can then go to the production environment and schedule to apply the package, just as you might schedule to apply any other update.

### What is the expected downtime?

The expected downtime for a successful update is 30 minutes to 1 hour. However, we ask for three hours of downtime in case issues occur while the update is applied. We're actively working to reduce the downtime that is required, and you should expect improvements in the next few months.

### What's the process for deprecation?

Before any feature is removed from the product, the deprecation notice will be announced in the product documentation 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

### Can I delay an update?

Yes, you can pause, delay, or opt-out of an update via Update Settings in Lifecycle Services projects provided that all of your sandbox and production environments are no more than three versions behind the latest available update. After this period, an update will be scheduled and auto-applied by Microsoft. The update experience for a delayed update will incur additional downtime.

### Can I delay an update for longer than three consecutive service updates due to seasonal activity or other business reason? 

No, service updates will be automatically applied to the sandbox, then 7 days later the update will be applied to all additional sandbox and production environments if the environments are more than three service updates old. A customer can only pause up to three consecutive updates in a row. For example, if a customer on version 10.0.22 chooses to pause updates 10.0.23, 10.0.24, and 10.0.25 then service update 10.0.26 will be auto applied to the sandbox and later followed by all additional sandbox and production environments. 

### What happens to an environment that is running a Finance and Operations version that is no longer supported?
Environments that are running a Finance and Operations version that is no longer supported display a warning message at the top of the environment details page in LCS.

For all Microsoft-managed environments, as well as sandbox and production environments in on-premises implementation projects, some Lifecycle Services (LCS) functionality may not be available when an environment is running a Finance and Operations version that is no longer supported. The LCS functionality that may not be available includes the ability to do the following:

- Enable maintenance mode
- Use all capabilities provided for moving databases on an environment or across environments
- Enable firewall access to SQL Server databases
- Download RSAT certificates
- Regenerate RSAT certificates

After you apply a service update for a supported version, this functionality will be available in the affected environment.

> [!NOTE]
> In this topic, versions are noted in the following ways:
>
> - Version N is the latest version, for example: 10.0.25
> - Version N-1 is one version older than N, for example: 10.0.24
> - Version N-2 is two versions older than N, for example: 10.0.23
> - Version N-3 is three versions older than N, for example: 10.0.22
> - Version N-4 is four versions older than N, for example: 10.0.22  (Customers on version 10.0.22 **can't** pause updates in this example.)

### How do the automatic updates affect my Microsoft-managed additional sandbox environments in my LCS implementation project? 

All additional sandbox environments will be updated during the same update window as your production environment, and they will be updated to the same release version that is used for the production update. The update will also apply to additional sandboxes environments that are on versions that are supported in the N-3 lifecycle policy. 

### What if one additional sandbox environment is on N-1 and another is on N-4 (the default sandbox environment and the production environment are on less than version N)? 

All environments will be updated to version N. 

### What if the default sandbox environment is manually updated before the default sandbox environment email is sent? 

Automatic updates for the default sandbox environment, production environment, and all additional sandbox environments will be canceled.

### What if the default sandbox environment is manually updated after the default sandbox email is sent? 

Automatic updates for the default sandbox environment, production environment, and all additional sandbox environments will be canceled. 

### What if the production environment is manually updated before the production environment email is sent? 

Automatic updates for the production environment and all additional sandbox environments will be canceled. 

### What if the production environment is manually updated after the production environment email is sent? 

Automatic updates for the production environment will be canceled, but all additional sandbox environments will be updated to version N.

### What if I find an issue during the sandbox update?

If you find an issue when doing validations in a sandbox environment, you can request to skip the update through LCS directly by providing a valid support ticket number and a business justification. 

### What if I find a critical issue during sandbox testing and I'm not able to pause the Production auto update?

Critical issues should always be submitted to the support team via Lifecycle Services as soon as they're identified. The support staff will work with you on the resolution to the critical issue.

### How much time do I get for validation?

You'll get 7 calendar days for validation after the update is applied to your sandbox environment. If you need more time, you can access the deployable package via the action center in Lifecycle Service and apply to your environments. This will provide you with additional time to test the update prior to a production roll-out.

### What happens when the service update is complete?

After the service update is applied by Microsoft, you'll receive a notification that indicates whether the update was successful or whether it could not be applied. There are several reasons why an update might be unable to be applied:

- **Pending Package Sign-off** – If a package is pending signoff, Microsoft won't apply the service update to production.
- **Deployment Failure** – If there was a deployment failure, the environment will be rolled-back to the original state.
 
### If there's a failure, can I reschedule the update to be automatically applied?

You won't be able to reschedule the update per se, but you may apply the package when it's convenient for you, just as you might schedule to apply any other update.

### Will critical hotfixes be automatically applied to my sandbox/production environment during auto-update?

The service update that will be made generally available, and auto applied to all customers will contain hotfixes and potentially new functionality. If a critical issue is reported after the service update has been applied, customers can pull that cumulative hotfix update from the tile in Lifecycle Services.

### How will my ISVs stay current?

Service updates to customer environments will be backward compatible and no action is required by the Independent software vendors (ISVs). ISVs develop on the minimum required platform release that their code depends on. Breaking changes will have a 12-month lead time to enable ISVs to include and validate. We recommend that the ISVs be part of our [Partner early access program](https://experience.dynamics.com/insider/), so that they can get early access to the platform bits and validate their solutions against the update before it's made generally available.

### What about new features?

All new features will be opt-in for a 12-month period and won't require any change management until you choose to enable the feature.

### Are batch jobs suspended during a service update?

Batch jobs are suspended during the maintenance windows and resume when the maintenance is completed.

To pause an update, refer to [Pause service updates through Lifecycle Services (LCS)](../../dev-itpro/lifecycle-services/pause-service-updates.md).

## Tools

### How can I get early access to non-released platform updates?

You can join the [First release program](https://experience.dynamics.com/insider/), where Microsoft will keep your system always current with the latest updates. If you're not already a member of the Dynamics 365 Insider Program, you'll need to:

1. Sign up for the Insider Program using this URL: https://experience.dynamics.com
2. Accept the terms and conditions to become a Dynamics 365 Insider.
3. After your application has been approved (approximately 24 hours) you can then sign back into the Insider Portal to find the different preview programs available for you to join. 
4. Preview Early Access Program (PEAP) and First Release: The program requires that you accept additional terms and conditions to join. Please look for these programs within the Dynamics 365 Insider Program after your nomination has been accepted.

### Is there tooling available to support testing the latest release?

The [Regression Suite Automation Tool](../../dev-itpro/lifecycle-services/using-task-guides-and-bpm-to-create-user-acceptance-tests.md) is [available now](https://www.microsoft.com/download/details.aspx?id=57357). This tool significantly reduces the time and cost of user acceptance testing. User acceptance testing is typically required before taking a Microsoft application update or applying custom code and configurations to your production environment. It enables functional power users to record business tasks using the Task recorder and convert them into a suite of automated tests without the need to write source code. Test libraries are stored and distributed in Lifecycle Services using the Business Process Modeler (BPM) libraries and fully integrated with Azure DevOps for test execution, reporting, and investigation. Test data parameters are decoupled from test steps and stored in Excel data files.

### How can I test and validate that the integrations continue to work?

Data task automation lets you easily repeat many types of data tasks and validate the outcome of each task. You can also use automated testing of data entities by using task outcome validation. For more information, see the [Data task automation](../../dev-itpro/data-entities/data-task-automation.md) topic.

### How can I determine what's changed in a service update?

The What's new or Changed documentation is the primary source for the details contained in each service update. The [Release plans](/business-applications-release-notes/) are the primary source of information for all new features and changes for a future release. Features will also include help topics in docs.microsoft.com as needed. 

### How will I know whether there's a deprecated feature that will affect me if I'm not doing active development/recompilation of my code? 

Deprecated features will be documented with each release. For more information, see [Removed or Deprecated features](../../dev-itpro/migration-upgrade/deprecated-features.md).

## Preparing for One Version

### How can I log an extensibility request?

Extensibility requests can be logged in LCS. Details are available in the [Extensibility requests](../../dev-itpro/extensibility/extensibility-requests.md) topic. Please note the following timelines to log and use the available extensions.

| Date         | Extensibility requests |
|--------------|------------------------|
| January 2019 | All extensibility requests must be logged by January 1, 2019. ISVs and customers are requested to analyze the code and make these requests by this time. We won't provide exceptions to stay on 7.3 after April 2019, if the request hasn't been filed by January 1, 2019. |
| December 2019 | Extensions will be available on/before December 31, 2019 for the requests logged by January 1, 2019. Customers using these extensions are required to move to current version by April 2020. |

### What does end of service mean?

Microsoft won't provide any fixes to issues on versions that have reached end of service. Microsoft will also not investigate or troubleshoot any issue that you may encounter on a version that's older than three service updates. If you encounter an issue on a version that has reached end of service, you'll be required to update to the latest update and report the issue if it persists.

All environments will continue to be operated by Microsoft. All automatic processes around your environments, such as monitoring or self-healing, will also continue as long as the environment is on a supported version.

### Will individual hotfixes be supported?

Individual hotfixes won't be supported after 8.1. Customers must update to the latest cumulative update available to apply the fix (such as 8.1.1). Critical fixes will also be cumulative and available through the LCS servicing experience.

### Will you notify me about critical hotfixes released for the monthly update that I'm on? 

Customer reported issues are searchable via Lifecycle Services Issue Search. You can sign up to be notified when an open issue is resolved.

## Commerce service updates

### What options are available to minimize impact to my Commerce cloud components?

Commerce cloud components will require the same down time as your Dynamics 365 headquarters. In an upcoming release, the Retail Cloud Scale Unit (RCSU) will be available to reduce and further schedule updates to your deployment. Please refer to our published release information on our [documentation](/business-applications-release-notes/October18/dynamics365-retail/planned-features) and [release notes](/business-applications-release-notes/?panel=products1#pivot=products) sites for additional details on RCSU.

### Will there be options to take individual hotfixes for my commerce solution components?

All fixes and updates for commerce components will be cumulative.

### What are the maintenance downtime requirements that may impact channel operations?

For retailers with a business need for redundancy, Modern POS offline capability allows core POS operations to be available for use while disconnected from the internet or while the cloud environment is being updated. Stores operating with Commerce Scale Unit will also continue to operate with support for core POS operations during cloud maintenance windows. For more information, see [Online and offline point of sale (POS) operations](../../../commerce/pos-operations.md).

### When will I need to update my in-store components?

All in-instore components must be running released software that is less than one year old in order to maintain support. Customers are responsible for updating self-hosted components (such as components installed in stores or in privately managed datacenters) and ensuring that the installed versions of these components are actively supported.

### Will there continue to be backward compatibility for the in-store components?

Updates to components that are hosted in the cloud will continue to preserve backward compatibility with component versions that are self-hosted by the retailer for 12 months after the release date for that version. (These components include components that are installed in stores or in privately managed datacenters: Modern Point of Sale, Commerce Scale Unit, or Hardware Station.) Self-hosted components don't have to be updated at the same time as cloud-hosted components. They can be updated on a separate cadence, so that there is time to roll updates out to stores.

### What options are available for updating in-store components across my organization?

Customers can choose to update self-hosted components manually at each store or use mass update tools such as Microsoft System Center Configuration Manager, Microsoft Intune, etc.

### What options do I have to slowly enable new functionality across my channels?

Microsoft provides several mechanisms to progressively roll-out and enable functional enhancements across stores, devices, and users.

- **Screen layout designer** – Most visual elements in POS are configured and centrally managed by an administrative user in the customer organization. This means that new POS operations won't automatically be displayed on POS unless explicitly configured for inclusion in corresponding screen layouts. Screen layouts are configured using Screen layout designer and can be specific to a store or POS device. For more information, see [Screen layouts for the point of sale (POS)](../../../commerce/pos-screen-layouts.md).
- **Functionality profiles, POS permissions, Commerce parameters** – Significant elements of functionality in POS are typically configurable by the user. This can be configured through functionality profiles, POS permissions, commerce parameters, or other controls which allow for device, register, store, or user-level functionality control in applicable scenarios.
- **Modern Point of Sale and Commerce Scale Unit** – Because Modern Point of Sale and Commerce Scale Unit are self-hosted by the retailer, topologies which include either of these components enable roll out of updates at a separate (and slower) cadence, and in a more granular fashion than with cloud-only topologies.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
