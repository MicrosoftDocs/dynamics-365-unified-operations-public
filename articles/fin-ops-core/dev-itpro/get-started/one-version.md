---
# required metadata

title: One Version service updates FAQ
description: This article provides clarity about the service updates, processes, and tools that you can use to stay current in a consistent, predictable, and seamless manner.
author: josaw1
ms.date: 09/29/2023
ms.topic: article
ms.prod: 
ms.technology: 
ms.custom: bap-template
# optional metadata

# ms.search.form:  [Operations AOT form name to tie this article to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: josaw
ms.search.validFrom: 2018-10-31 
ms.dyn365.ops.version: 8.1
---

# One Version service updates FAQ

[!include[banner](../includes/banner.md)]

This FAQ is intended to provide clarity about the service updates, processes, and tools that you can use to prepare for the change. We continue to add information to this article as required.

For more information about One Version service updates, see [One Version service updates overview](../../dev-itpro/lifecycle-services/oneversion-overview.md).

> [!IMPORTANT]
> There's an important change coming to the service update release schedule. The number of service updates released annually is being reduced from seven to four. This change impacts the preview availability, general availability (self-update), and end of service dates for version 10.0.38, and goes into full effect beginning with version 10.0.39 (the “April” 2024 release).

### What's changing with the new release cadence?

The following changes are being implemented.
-	Service updates are only released in February (December self-update), April, July, and October. The May, August, and November releases are no longer available for self-update or auto-update.
-	The lifecycle of each release is substantially extended to 404 – 414 days.
-	The preview period is extended. Every release now includes one scheduled update to the preview build.
-	The [First release program](https://aka.ms/FirstReleaseFnO)’s auto-update and feedback phase is extended by two weeks. 
-	The servicing window of every release is substantially extended to 186 - 214 days with improved overlap between releases.
-	The number of consecutive pauses allowed is reduced from three to one. With the release durations extended, the same minimum two annual service updates is maintained.

### Is the change from three to one maximum pauses already in effect?

No. The transition from three to one maximum pauses will be completed by April 2024. The enforcement of one maximum pause goes into effect on February 19, 2024, after all scheduled auto-updates for 10.0.38 are completed.

The following table illustrates allowed pauses by month based on your installed version until the transition is completed. For more information about pausing service updates, refer to [Pause service updates through Lifecycle Services (LCS)](../../dev-itpro/lifecycle-services/pause-service-updates.md).

![Allowed pauses by month.](../media/OneVersion-FAQs-Max-Pause-Transition.png)

### Does the new release schedule impact when I can schedule auto-updates?

No. There is no change to how auto-updates are scheduled in Lifecycle Services and when those auto-updates occur. The only change is what service updates are being released each year. For information about how to pause an update, refer to [Pause service updates through Lifecycle Services (LCS)](../../dev-itpro/lifecycle-services/pause-service-updates.md).

### When does the new service update release cadence take effect?

Version 10.0.38 (the “February” release) is revised to act as a transition release. 10.0.39 (the “April” release) is be the first service update released under the new cadence.

### Is the published 10.0.38 schedule impacted by the new service update release cadence?

Yes. To act as a transition release, some release milestones for 10.0.38 were adjusted to align with the new release cadence.
-	Preview availability was pushed out by two weeks from October 13 to October 27, 2023.
-	An update to the preview was added, and will be released on November 3, 2023.
-	Customers participating in the [First release program](https://aka.ms/FirstReleaseFnO) will receive their auto-updates a month earlier, in December 2023.
-	General availability for self-update will occur a month earlier, on December 22, 2023.
-	There is no change to the general availability broadcast (auto-update) dates.
-	The servicing window is extended from April 12 to Aug 9, 2024.

### Can the updates be delayed? What's the policy?

Yes, customers can pause, delay, or opt out of an update by using the update settings in Lifecycle Services projects. Beginning with the April 2024 auto-update, customers can choose to pause one update. Prior to April 2024, the number of pauses available to a customer depends on their release version relative to the latest version. See [Is the change from three to one maximum pauses already in effect?](#Is-the-change-from-three-to-one-maximum-pauses-already-in-effect) for details.

For information about how to pause an update, refer to [Pause service updates through Lifecycle Services (LCS)](../../dev-itpro/lifecycle-services/pause-service-updates.md).

### How does the timing for general availability of a release work?

The release package is made generally available to all customers for self-update prior to auto-updates. The timing of the package release for self-update relative to the production auto-updates varies. To determine self-update and auto-update timing for upcoming releases, use the [Targeted release schedule (dates subject to change)](public-preview-releases.md#targeted-release-schedule-dates-subject-to-change).

Production auto-updates for a release are scheduled for the first, second, and third weeks of the month. The configuration setup is available in Lifecycle Services. You receive updates during the selected week based on the configuration that you set up in Lifecycle Services. Sandbox updates are always scheduled the week before the production update.

As an example, for the 10.0.39 ("April") release, Microsoft will make the release generally available to all customers for self-update by the general availability public date of March 15, 2024. Customers who have enabled auto-updates through Lifecycle Services will receive production updates beginning two weeks after the general availability public date, during the weekends of April 5, April 12, or April 19, depending on the configuration in Lifecycle Services. Sandbox updates are always scheduled a week before the update.

Customers can always choose to apply the update at an earlier time or at a time that is more convenient than the suggested times in Lifecycle Services. If a customer is already on the latest version, the automatic update is canceled.


## Service updates

### What product versions are affected by service updates?

| Version       | Description |
|---------------|-------------|
| 10 | All customers are scheduled for automatic service updates. The updates are combined application and platform updates. Beginning in February 2024, you can only pause one update before being required to take the next update. For information about how to pause an update, see [Pause service updates](../../dev-itpro/lifecycle-services/pause-service-updates.md). |

### What do the service updates contain?

Service updates contain application and platform changes that are critical to the service, including regulatory updates. Service updates are backward compatible and new experiences are configurable. The update is represented by a single version.

> [!NOTE]
> Add-in components, Power Apps, and Dataverse are updated independently of the finance and operations apps service update package and process.

### What is a regulatory update?

A regulatory update is a new feature or an existing feature change required by law, usually for a specific country or region. A regulatory update is always required by a specific law enforcement date (LED) and should be enabled by that date or earlier.

### How can I determine what's changed in a service update?

The "What's new or changed" documentation is the primary source for the details of each service update. The release plans are the primary source of information for new features and changes for a future release. Features are also documented on Microsoft Learn as needed. 

### What is the upcoming schedule of updates?

Each year, four service updates are released. You have the option to apply them when convenient for you, or you can let Microsoft automatically apply them, based on the selected maintenance window. You're required to use an update that's no more than one update behind the current update.

To view the targeted release schedule for upcoming releases, see [Service update availability](public-preview-releases.md).

### Are there any major differences between the updates?

There are two major updates each year: the April update and the October update. New experiences can be enabled in these updates. Major updates don't require code or data upgrade. Breaking changes are communicated 12 months in advance so that customers can plan accordingly. Breaking changes are introduced only during major updates.

### What does it mean that an update is backward compatible?

Backward compatibility covers binary and functional compatibility. Binary compatibility means that you can apply an update on any runtime environment without having to recompile, reconfigure, or redeploy customizations. It also means that, on a development environment at design time, X++ public and protected application programming interfaces (APIs) and metadata aren't modified or deleted. If Microsoft must break compatibility by removing obsolete APIs, the change is communicated 12 months in advance and follows a deprecation schedule. Functional compatibility refers to the user experience. All new experiences are available on an opt-in basis for a 12-month period.

Backward compatibility doesn't include non-X++/metadata APIs. Microsoft reserves the right to update versions of any dependencies that the product uses, and to remove dependencies, without early warning. Microsoft doesn't commit to maintain backwards compatibility of dependent software libraries unless this commitment is expressly stated.

For more information about deprecation guidelines, and deprecated methods and metadata elements, see [Deprecation of methods and metadata elements](../../dev-itpro/migration-upgrade/deprecation-deletion-apis.md).

### What's the process for deprecation?

The deprecation notice is announced in the product documentation 12 months before Microsoft removes a feature from the app.

For breaking changes that only affect compilation time, but that are binary compatible with sandbox and production environments, the deprecation time is less than 12 months. Typically, these changes are functional updates that must be made to the compiler. 

### If I'm not doing active development/recompilation of my code, how will I learn whether there is a deprecated feature that will affect me? 

Deprecated features are documented for each release. For more information, see [Removed or Deprecated features](../../dev-itpro/migration-upgrade/deprecated-features.md).

### Can I update just the platform? Similarly, can I update just the application?

No. Only combined application plus platform update packages are released for both service updates and quality updates. 

### Service updates for on-premises deployments

The policy and schedule for service updates are the same for both cloud deployments and on-premises deployments. For example, the option to delay one service update applies to both types of deployment. The process for applying each of these updates remains slightly different, however. For more information, see [Apply updates to on-premises deployments](../../dev-itpro/deployment/apply-updates-on-premises.md#update-an-on-premises-deployment).

## Process

### How does Microsoft ensure the quality of releases?

Ensuring the quality of releases is a fundamental principle that is enabled through a series of progressive, rigorous, automated validations, as described in [Service update availability](public-preview-releases.md).

### Can I select the day and time to update?

You can configure the day and maintenance time windows in Lifecycle Services. The service update, which is based on your update settings, starts within 15 minutes. If you opt in to receive Lifecycle Services notifications, you'll receive an email that includes update instructions. You'll be able to select the designated tier 2/UAT sandbox for the update. You'll have seven calendar days to do testing and validation before the production environment is updated. All additional sandboxes are automatically updated on the same day as the production environment. For more information, see [Configure service update](../../dev-itpro/lifecycle-services/configure-service-updates.md).

You can optionally apply the update earlier to all environments through Lifecycle Services. The production-ready deployable package is available to all customers via the Action Center in Lifecycle Services by the generally available (self-update) date. See [Service update availability](public-preview-releases.md) for the targeted release schedule of upcoming releases.

### A service update was applied to the environment. In Lifecycle Services, what does the number on the tile for this environment represent?

Microsoft automatically applies the same service update to all customers. Microsoft continues to service the update until the end of service date for that release is reached. In Lifecycle Services, the available updates tile for the environment represents the cumulative quality update package that is available to be applied to your environment. There are two numbers on the tile. The top number is the release version and the bottom number is the build number of the latest quality update package. The build number is always higher than the number of the service update that was applied to your environment, either through self-update or auto-update. Because Microsoft automatically applies the same version to all customers, you're responsible for applying the cumulative hotfix package if it's required.

> [!NOTE]
> If your environment version is earlier than the latest release version, a tile appears under **Available updates** to inform you to apply the latest service update using self-update.

### How do I update to the latest version?

You can self-update to the latest version by using the tile on the **Environment details** page. After an update is released by Microsoft, the tile shows the available update. You can choose to apply the update by going through the update experience on your sandbox and production environments. For more details, see [Apply updates to cloud environments](../../dev-itpro/deployment/apply-deployable-package-system.md) and [Apply updates to on-premises deployments](../../dev-itpro/deployment/apply-updates-on-premises.md). 

### How do I update the production environment to the same version after Microsoft updates the sandbox environment?

When Microsoft updates a sandbox environment, the package that's used for the update is saved in the project's asset library. The name of the package is prefixed by the words "Service Update." Because the package was already applied to the sandbox environment, you can mark it as a release candidate. You can then go to the production environment and schedule to apply the package, just as you might schedule any other update.

### What is the expected downtime during an auto-update?

The expected downtime for a successful update is approximately 15 minutes. However, Microsoft asks for three hours of downtime in case issues occur while the update is applied.

### Can I delay an update?

Yes, you can pause, delay, or opt out of an update using the update settings in Lifecycle Services projects, provided that all your sandbox and production environments aren't more than one version behind the latest available update. After this period, Microsoft schedules and automatically applies an update. The update experience for a delayed update incurs additional downtime.

### Can I delay an update for longer than the one permitted skipped service update because of seasonal activity or other business reasons?

No. Once your environment version is more than one version older than the latest, Microsoft automatically applies the latest service update to the default Tier-2 sandbox. Seven days later, the update is applied to all additional sandbox and production environments that are also more than one version older than latest. You can pause only one update before you must take the next service update, which in effect, requires a minimum of two service updates annually. For example, if a customer is running version 10.0.39 and chooses to pause update 10.0.40, service update 10.0.41 will automatically be applied first to the Tier-2 sandbox environment and later to all additional sandbox and production environments.

### What does it mean for a release to be “in service”?

A release is a service update version that has been made available to customers. A release is “in service” from the day it's made available to customers for production use to its end of service date. See the targeted release schedule in the [Service update availability](public-preview-releases.md) article for release milestones by release.

A release in post-update servicing reaches its end of service date about one month after auto-updates complete for the latest version. This gives customers who opted to pause time to complete their required update before the servicing window for their version is closed. You can see this illustrated in the following figure, which visualizes the staggered release rollout and servicing model.

![Staggered release rollout servicing model.](../media/OneVersion-FAQsa-Staggered-Release-Rollout-Servicing-Model.png)

![Staggered release rollout servicing model legend.](../media/OneVersion-FAQs-Staggered-Release-Rollout-Servicing-Model-legend.png)


> [!IMPORTANT]
> The support team at Microsoft can't take cases for issues reported from versions that are at end of service. You must first update to the latest service update and then apply the latest quality update. If the issue still persists, then you can report it.    

### What happens to an environment that is running a finance and operations app version that's no longer supported?

For environments that are running a finance and operations app version that is no longer supported, a warning message appears at the top of the environment details page in Lifecycle Services.

For all Microsoft-managed environments, and sandbox and production environments in on-premises implementation projects, some Lifecycle Services functionality might not be available when an environment is running a finance and operations app version that is no longer supported. This functionality includes the ability to complete the following actions:

- Enable maintenance mode.
- Use all capabilities that are provided for moving databases on an environment or across environments.
- Enable firewall access to SQL Server databases.
- Download Regression suite automation tool (RSAT) certificates.
- Regenerate RSAT certificates.

After you apply a service update for a supported version, this functionality is available in the affected environment.

### How do the automatic updates affect my Microsoft-managed additional sandbox environments in my Lifecycle Services implementation project? 

All additional sandbox environments are updated during the same update window as your production environment, and are updated to the same release version that is used for the production update. The update is also applied to additional sandbox environments that are on versions that haven't reached end of service.

### What happens during an update when my additional sandboxes are on different versions from that of default sandbox and production, which are scheduled to receive the latest service update?       

All environments are updated to the current version being used for auto-updates.

### What if the default sandbox environment is manually updated to the exact same version or newer version than the automatic update version? 

Automatic updates for the production environment and all additional sandbox environments are updated to the current version being used for auto-updates.
 
The default sandbox environment update are canceled. 

### What if the default sandbox environment is manually updated to an older version than the automatic update version? 
 
The default sandbox environment, production environment, and all additional sandbox environments are updated to the current version being used for auto-updates.

### What if the production environment is manually updated _before_ the production environment email is sent? 

Automatic updates for the production environment and all additional sandbox environments are canceled. 

### What if the production environment is manually updated _after_ the production environment email is sent? 

Automatic updates for the production environment are canceled, but all additional sandbox environments are updated to the current version being used for auto-updates.

### What if I find an issue during the sandbox update?

If you find an issue when doing validations in a sandbox environment, you can request to skip the update directly through LCS by providing a valid support ticket number and a business justification. See [Pause service updates through Lifecycle Services (LCS)](../../dev-itpro/lifecycle-services/pause-service-updates.md). 

### What if I find a critical issue during sandbox testing, but I can't pause the production automatic update?

Critical issues should always be submitted to the Support team via LCS as soon as they are identified. The support staff will work with you to fix the critical issue.

### How much time do I have for validation?

You have seven calendar days for validation after the update is applied to your sandbox environment. If you need more time, you can access the deployable package via the Action Center in LCS and apply it to your environments. In this way, you'll get additional time to test the update before a production roll-out.

### What happens when the service update is completed?

After the service update is applied by Microsoft, you'll receive a notification that indicates whether the update was successful or whether it couldn't be applied. Reasons why an update may not be applied are:

- **Pending Package Sign-off** – If a package is pending signoff, Microsoft won't apply the service update to production.
- **Deployment Failure** – If there was a deployment failure, the environment is rolled back to the original state.
 
### If there's a failure, can I reschedule the update to be automatically applied?

No. You won't be able to reschedule the update. However, you can apply the package when it's convenient, just as you might schedule any other update.

### Will critical hotfixes be automatically applied to my sandbox/production environment during automatic update?

The service update that's generally available to all customers for self-update and auto-update contains hotfixes and new functionality. If a critical issue is reported and fixed after the service update was applied, you can pull the latest cumulative quality update from the tile in Lifecycle Services.

### How do my ISVs stay current?

Service updates to customer environments are backward compatible, and no action is required by the independent software vendors (ISVs). ISVs develop on the minimum required platform release that their code depends on. Breaking changes have a 12-month lead time so ISVs can include them and do validation. Microsoft recommends that the ISVs take advantage of the preview release for each service update so that they can get early access to the platform code and validate their solutions against the update before it's made generally available. There is a [Preview Early Access](https://www.yammer.com/dynamicsaxfeedbackprograms/#/threads/inGroup?type=in_group&feedId=12792233) Yammer group that Microsoft encourages both ISVs and customers to join. The Yammer group provides a forum to receive preview and release-related announcements and to collaborate with others in the finance and operations apps community.


### What about new features?

All new features are available on an opt-in basis for a 12-month period. They won't require any change management until you choose to enable them.

### Are batch jobs suspended during a service update?

Batch jobs are suspended during the maintenance windows and resume when the maintenance is completed.

For information about how to pause an update, see [Pause service updates through Lifecycle Services (LCS)](../../dev-itpro/lifecycle-services/pause-service-updates.md).

## Tools

### How can I get early access to updates that weren't released?

Beginning with version 10.0.26, the preview package for all service updates is made available to all customers through the Shared Asset Library in Lifecycle Services, under **Software deployable package**. Preview packages can be deployed to development or test environments. They can't be used in production environments. You agree to the program terms at installation. Sign up for access to preview packages (formerly known as the Preview Early Access Program (PEAP)) is no longer required.

To be in the first group of customers to take service updates to production, you can join the [First release program](https://aka.ms/FirstReleaseFnO). While enrolled in First Release, Microsoft keeps your system current with the latest updates. First Release customers receive updates to all sandbox and production environments and are always updated before general availability.

### Is any tooling available to support testing of the latest release?

The [Regression Suite Automation Tool](../../dev-itpro/lifecycle-services/using-task-guides-and-bpm-to-create-user-acceptance-tests.md) is [available now](https://www.microsoft.com/download/details.aspx?id=57357). This tool significantly reduces the time and cost of user acceptance testing (UAT). UAT is typically required before you take a Microsoft application update or apply custom code and configurations to your production environment. It lets functional power users record business tasks by using the Task recorder and convert them into a suite of automated tests, without having to write source code. Test libraries are stored and distributed in LCS by using the Business Process Modeler (BPM) libraries, and they are fully integrated with Azure DevOps for test execution, reporting, and investigation. Test data parameters are decoupled from test steps and stored in Excel data files.

### How can I test and validate that the integrations continue to work?

Data task automation lets you easily repeat many types of data tasks and validate the outcome of each task. You can also use automated testing of data entities by using task outcome validation. For more information, see [Data task automation](../../dev-itpro/data-entities/data-task-automation.md).

## Preparing for One Version

### How can I log an extensibility request?

Extensibility requests can be logged in LCS. Details are available in the [Extensibility requests](../../dev-itpro/extensibility/extensibility-requests.md) article. 

### What does "end of service" mean?

Microsoft won't provide any fixes for issues on versions that reached their end of service. If you encounter an issue on a version that reached its end of service, you must apply the latest update and then report the issue if it persists. See [Service update availability](public-preview-releases.md) for end of service dates by version.

All environments continue to be operated by Microsoft. All automatic processes around your environments, such as monitoring or self-healing, also continue as- is for supported versions.

### Are individual hotfixes supported?

Individual hotfixes aren't supported after version 8.1. To apply a fix, you must update to the latest cumulative update available. Critical fixes are also applied via cumulative update and are available through the Lifecycle Services servicing experience.

### Will you notify me about critical hotfixes released for the monthly update that I'm on? 

Customer reported issues are searchable in Lifecycle Services Issue search. You can sign up to be notified when an open issue is resolved. A summary list of customer reported issues is published to Lifecycle Services Issue search for every preview and general availability release. You can find the list by title search using the pattern “Version 10.0.xx of Finance and Operations apps”.

## Commerce service updates

### What options are available to help minimize the impact on my Commerce cloud components?

Commerce cloud components require the same down time as your Dynamics 365 headquarters. In an upcoming release, the Retail Cloud Scale Unit (RCSU) will be available to reduce and further schedule updates to your deployment. For more information about RCSU, see the published release information on our [documentation](/business-applications-release-notes/October18/dynamics365-retail/planned-features) and [release notes](/business-applications-release-notes/?panel=products1#pivot=products) sites.

### Will there be options to take individual hotfixes for my commerce solution components?

All fixes and updates for commerce components are cumulative.

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
