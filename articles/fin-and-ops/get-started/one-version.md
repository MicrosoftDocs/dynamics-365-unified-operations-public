---
# required metadata

title: One Version service updates FAQ
description: This topic is intended to provide clarity on service updates, processes, and tools that you can use to stay current in a consistent, predictable, and seamless manner.
author: meeramahabala
manager: AnnBe
ms.date: 10/25/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: meeram
ms.search.validFrom: 2018-10-31 
ms.dyn365.ops.version: 8.1
---

# One Version service updates FAQ
[!include[banner](../includes/banner.md)]

In July 2018 we announced a [change to the way we deliver Dynamics 365 updates](https://cloudblogs.microsoft.com/dynamics365/2018/07/06/modernizing-the-way-we-update-dynamics-365/) that will help you stay current in a consistent, predictable, and seamless manner. This FAQ is intended to provide clarity on the Finance and Operations service updates, processes, and tools you can use to prepare for it. We will continue to add additional information to this topic as needed.

## Service updates

### What product versions are impacted by service updates?
| Version | Description |
|---------|-------|
| 8.1 and later | All customers on 8.1 and later will be scheduled for updates monthly with a combined application and platform update starting November 2018.  You will be required to have an update that's no older than 3 months.                   |
| 8.0           | Customers on 8.0 will receive a monthly platform and financial reporting update. You will be required to have an update that's no older than 3 months. The 8.0 lifecycle ends in April 2019. We encourage customers on 8.0 to update to 8.1 by December 1, 2018. This process is like a regular package update. For detailed documentation, see the [Update environments from version 8.0 to 8.1](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/migration-upgrade/appupdate-80-81) topic.  | 
| 7.x           | Customers on 7.x will receive a monthly platform and financial reporting update. You will be required to have an update that's no older than 3 months.  You are required to upgrade to 8.1 before April 2019 (unless extensions are not available, the only overlayered version in market will be version 7.3). Starting April 2019, the service will be updated to version 10.0. |

### What does the update contain?
For 8.1 and later, service updates will contain application (including financial, reporting, and Retail) and platform changes that are critical improvements to the service including regulatory updates. New experiences will be opt-in. The service updates are backward compatible. There will be a single version representing this update.

### What is a regulatory update?
A regulatory update is a new feature or an existing feature change required by law (usually for a specific country/region). The regulatory update is always required by a specific law enforcement date (LED) and should be enabled by this date or earlier.

### What's the upcoming schedule of updates?
Service updates will be available each month starting in November 2018. Microsoft will apply the updates monthly, based on the selected maintenance window. You are required to have an update no older than 3 months.

### Are there any major updates post 8.1?
There will be 2 major updates in April and October where new experiences will be enabled. Major updates will not require code or data upgrade. Breaking changes will be communicated 12 months in advance such that customers can plan accordingly. Such a change will only be introduced during a major update. The 10.0 release, which will be available in April 2019, will also be an update and not an upgrade.

### What does it mean when an update is backward compatible?
Backward compatibility covers binary and functional compatibility. Binary compatibility means that you can apply an update on any runtime environment without needing to recompile, reconfigure, or redeploy customizations. This means that on a development environment at design time, X++ public and protected APIs and metadata are not modified or deleted. If Microsoft needs to break compatibility by removing obsolete APIs, it will be communicated 12 months in advance and follow a deprecation schedule. Design-time compatibility does not include non X++/metadata APIs. Functional compatibility is about user experience. All new experiences will be opt-in.

### Do these updates apply to on-premises?
Refer to the [Software lifecycle policy and on-premises releases](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/migration-upgrade/on-prem-version-update-policy?toc=/fin-and-ops/toc.json) topic for the specific expiration dates of the version that you are on. The process of the updates outlined in this topic only apply to the cloud service. 

## Process

### Can I select the day and time to update?
Customers can configure the day and maintenance time windows in Lifecycle Services (LCS). Email will be sent to those individuals who opt in to receive LCS notifications with instructions included on how to update. Customers will be able to select the designated tier 2/UAT sandbox for the update. Customers will have 5 business days for testing and validation. Customers can optionally choose to apply the update earlier to all environments through Lifecycle Services and even earlier through early access programs. Customers are responsible for deploying the update to any additional sandbox or developer/build (tier 1) environments.

### How do I update to the latest version?
Users can update to the latest version using the tiles on the Environment details page in LCS. After the update is released by Microsoft, the tile will show the latest update. Customers can choose to apply the update on their own by going through the update experience on their sandbox and production environments. Documentation will also be made available on docs.microsoft.com.

### What is the expected downtime?
The expected downtime for a successful update is 30 minutes to 1 hour. However, we ask for three hours of downtime in case issues occur while the update is applied. We are actively working to reduce the downtime that is required, and you should expect improvements in the next few months.

### What's the process for deprecation?
Deprecation will be announced by a notice 12 months prior to the deprecation. The functionality will only be deprecated during a major update.

### Can I delay an update?
You can pause an update up to 3 months by way of LCS configuration. After this period, an update will be scheduled and monthly updates resumed. The update experience for a delayed update will incur additional downtime.

### What if I find an issue during the sandbox update?
If you find an issue when doing validations in a sandbox environment, you can request to skip the update through LCS directly by providing a valid support ticket number and a business justification. The request will be reviewed by Microsoft and if approved you will be left out of that month's update.

### How much time do I get for validation?
You will get five (5) days for validation once the update is applied to your sandbox environment. If you need more time, you can sign up for an early access automatic update to one of your sandbox environments. This will provide you with additional time to test the update prior to a production roll out. More information about this program will be available shortly.

### Will rollback be supported after an update is applied?
Rollback will be supported in the coming months.

### How will my ISVs stay current?
Service updates to customer environments will be backward compatible and no action is required by the Independent software vendors (ISVs). ISVs develop on the minimum required platform release that their code depends on. Breaking changes will have a 12-month lead time to enable ISVs to include and validate. We recommend that the ISVs be part of our [Partner early access program](https://experience.dynamics.com/insider/), so that they can get early access to the platform bits and validate their solutions against the update before it's made generally available.

### What about new features?
All new features will be opt-in for a 12-month period and will not require any change management until you choose to enable the feature.

### Are batch jobs suspended during a service update?
Batch jobs are suspended during the maintenance windows and resume when the maintenance is completed.

## Tools

### How can I get early access to non-released platform updates?
You can join the [First release program](https://experience.dynamics.com/insider/), where Microsoft will keep your system always current with the latest updates.

### Is there tooling available to support testing the latest release?
The [Regression Suite Automation Tool](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/lifecycle-services/using-task-guides-and-bpm-to-create-user-acceptance-tests) for Finance and Operations is [available now](https://www.microsoft.com/en-us/download/details.aspx?id=57357). This tool significantly reduces the time and cost of user acceptance testing. User acceptance testing is typically required before taking a Microsoft application update or applying custom code and configurations to your Dynamics 365 for Finance and Operations production environment. It enables functional power users to record business tasks using the Finance and Operations Task recorder and convert them into a suite of automated tests without the need to write source code. Test libraries are stored and distributed in Lifecycle Services using the Business Process Modeler (BPM) libraries and fully integrated with Azure DevOps for test execution, reporting, and investigation. Test data parameters are decoupled from test steps and stored in Excel data files.

Data task automation lets you easily repeat many types of data tasks and validate the outcome of each task. You can also use automated testing of data entities by using task outcome validation. For more information, see the [Data task automation](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/data-entities/data-task-automation) topic.

### How can I determine what's changed in a service update?
The [Release notes](https://docs.microsoft.com/en-us/business-applications-release-notes/) are the primary source of information for all new features and changes for a release. Features will also include help topics in docs.microsoft.com as needed. An impact analysis tool will be available in LCS to help you better understand the impact to the features that you use.

## Preparing for One Version

### How can I log an extensibility request?
Extensibility requests can be logged in LCS. Details are available in the [Extensibility requests](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/extensibility/extensibility-requests) topic. Please note the following timelines to log and use the available extensions.

| Date | Extensibility requests |
|----------|---------------------------------------------------------------------------------------------------------|
| January 2019 | All extensibility requests must be logged by January 1, 2019. ISVs and customers are requested to analyze the code and make these requests by this time. We will not provide exceptions to stay on 7.3 after April 2020, if the request has not been filed by January 1, 2019. |
| December 2019 | Extensions will be available on/ before December 31, 2019 for the requests logged by January 1, 2019. Customers using these extensions are required to move to current version by April 2020.    |

### What does end of service mean?
To service any issues that you have, you will need to take the latest update at that time. We will not be providing any individual hotfix. Microsoft will be unable to troubleshoot performance issues on older updates.

After 8.1 you will be required to be on the latest version supported (such as 8.1.1) within 3 months of the release date. Please see the [Lifecycle policy](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/migration-upgrade/versions-update-policy) for details.

### Will individual hotfixes be supported?
Individual hotfixes will not be supported after 8.1. Customers must update to the latest cumulative update available to apply the fix (such as 8.1.1). Critical fixes will also be cumulative and available through the LCS servicing experience.

### How can I upgrade to 8.x?
Refer to the [Process for moving to the latest update of Finance and Operations](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/migration-upgrade/upgrade-latest-update#scenario-3-upgrade-to-the-latest-application-release-1) topic to learn how to upgrade to the latest application. Updating from [8.0 to 8.1](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/migration-upgrade/appupdate-80-81) will not require any data upgrade and will be a self-serve update with much reduced downtime.

## How Retail functionality is impacted 

### What components of my solution will be impacted by One Version monthly updates?

All cloud components including Retail Server and Cloud POS will be updated at the same cadence as your Retail headquarters.

### What options are available to minimize impact to my Retail cloud components?

Retail cloud components will require the same down time as your Retail headquarters. In an upcoming release, the Retail Store Scale Unit (RSSU) will be available to reduce and further schedule updates to your deployment. Please refer to our published release information on our [documentation](https://docs.microsoft.com/en-us/business-applications-release-notes/October18/dynamics365-retail/planned-features) and [release notes](https://docs.microsoft.com/en-us/business-applications-release-notes/#pivot=products&panel=products1) sites for additional details on RSSU.

### Will there be options to take individual hotfixes for my retail solution components?

All fixes and updates for retail components will be cumulative.

### What are the maintenance downtime requirements that may impact channel operations?

For retailers with a business need for redundancy, Modern POS offline capability allows core retail POS operations to be available for use while disconnected from the internet or while the cloud environment is being updated. Stores operating with Retail Store Scale Unit will also continue to operate with support for core POS operations during cloud maintenance windows. For more information, see [Online and offline point of sale (POS) operations](../retail/pos-operations/md).

### When will I need to update my in-store components?

All in-instore components must be running released software that is less than one year old in order to maintain support. Customers are responsible for updating self-hosted components (i.e. components installed in stores or in privately managed datacenters) and ensuring that the installed versions of these components are actively supported.

### Will there continue to be backwards compatibility for the in-store retail components?

Updates to components hosted in the cloud will continue to preserve backwards compatibility with component versions self-hosted by the Retailer (i.e. components installed in stores or in privately managed datacenters - Modern Point of Sale, Retail Store Scale Unit, Hardware Station) for 12 months after the release date for that version. Self-hosted components do not need to be updated at the same time as cloud-hosted components and can be updated on a separate cadence allowing time to roll-out updates to stores.

### What options are available for updating in-store components across my organization?

Customers may choose to update self-hosted components manually at each store or employ use of mass update tools such as Microsoft System Center Configuration Manager, Microsoft Intune, etc.

### What options do I have to slowly enable new functionality across my retail channels?

Microsoft provides several mechanisms to progressively roll-out and enable functional enhancements across stores, devices, and users.

1.  **Screen layout designer**: Most visual elements at POS are configured and centrally managed by an administrative user in the customer organization. This means that new POS operations will not automatically be displayed on POS unless explicitly configured for inclusion in corresponding screen layouts. Screen layouts are configured using Screen layout designer and can be specific to a store or POS device. For more inforamation, see [Screen layouts for the point of sale (POS)]../retail/pos-screen-layouts.md).

2.  **Functionality profiles, POS permissions, Retail parameters**: Significant elements of functionality at POS are typically configurable by the user. This can be configured through functionality profiles, POS permissions, retail parameters, or other controls which allow for device, register, store, or user level functionality control in applicable scenarios.

**Modern Point of Sale and Retail Store Scale Unit:** Since Modern Point of Sale and Retail Store Scale Unit are self-hosted by the retailer, topologies which include either of these components enable roll out of updates at a separate (and slower) cadence, and in a more granular fashion than with cloud-only topologies.


