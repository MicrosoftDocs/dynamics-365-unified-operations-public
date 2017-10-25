---
# required metadata

title: Planned maintenance window FAQ
description: This topic provides answers to frequently asked questions about the Microsoft planned maintenance windows.
author: robadawy
manager: AnnBe
ms.date: 09/19/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 6154
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: robadawy
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---
# What is a planned maintenance window?
A planned maintenance window is the timeframe that Microsoft has scheduled to apply critical updates to your cloud service.

### How does a planned maintenance window work?
For all planned updates, Microsoft will send a notification to all stakeholders five days before the patching window begins. The patching window, which is when the environment is patched or the update is applied, is defined by geographic region.

During a platform update, Microsoft Dynamics Lifecycle Services (LCS) will reflect the state of your environment at all times and provide email updates about the process. The History section on the Environment pane shows the updates that have been completed,

At this time, during operation system-level updates, LCS does not indicate that any patching is in progress. We are planning to add this functionality sometime in the future.

### When is this planned maintenance window taken?
To limit the impact on users, the maintenance window is planned according to the region where environments are deployed. The following list shows the maintenance window for each region. The times are shown in Coordinated Universal Time (UTC, which is also known as Greenwich Mean Time).
- NAM: 2 AM to 10 AM
- SAM: 12 AM to 8 AM
- EMEA: 6 PM to 2 AM
- CAN: 2 AM to 10 AM
- APAC: 12 PM to 9 PM

### What updates are applied in the planned maintenance window?
During the planned maintenance window, operating system–level updates, and critical security and reliability platform updates are applied.

### How long is the maintenance window?
Operating system–level updates are completed in approximately one hour.

Platform updates are typically completed in one to three hours. In rare instances, a platform update can take up to eight hours to be completed.

The exact downtime for all updates will be included in the maintenance window notification email that is sent to you before the start of the update.

### What environments are updated as a part of the planned maintenance?
Platform updates are applied on the Tier-2 sandbox environment that is included in the Microsoft base offer. After validating that the environments are patched successfully, Microsoft will apply this update in the production environment within five days.

Operating system–level updates are applied on all Tier-2 sandbox environments that are included as part of the Microsoft base offer. They are also applied on add-ons that have been purchased.

Note that all other environments, such as Tier-1 sandbox and demo environments, are the responsibility of the customer or partner.

### What notifications will I receive about upcoming planned maintenance?
You will receive an email notification five days before the update is scheduled to occur. This notification will include information about the environments that will be updated, the update type, the estimated amount of time that the update will take, and any action that you may have to take.

In the future, we are planning to enable more notification types:
- Email notification – Five days before the planned maintenance window an email reminder will be sent. Additional emails will be sent in the days leading up to the maintenance (T-5, T-3, T-1 day),
- LCS notification – In LCS, in the Environment details, you can select Upcoming updates to see an entry for the upcoming maintenance window. In addition, 24 hrs before the maintenance window, there will be a message bar on the environment as a reminder.
- Product based notification – In Finance and Operations, a notification will be sent two hours prior to a planned system downtime informing users that the system will be unavailable in the planned downtime window.

### Who will be notified about the upcoming planned maintenance?
The following stakeholders will be notified about the upcoming maintenance:
- Project owners
- Organization admins
- Environment admins
- Other people who are specified in the list during deployment or through the Notify button on the Environment details pane

### What validation requirements do I have to complete?
When a platform update is applied, you don’t have to complete any validations. Microsoft is responsible for making sure that the updates are backward compatible and forward compatible. However, if you prefer, you can complete functional validations, because Microsoft doesn’t do those validations after updates are applied. We recommend that you automate functional validations to reduce the validation effort.

### What validations does Microsoft do for changes that will be applied during the update?
Before the update is applied, Microsoft runs validations to make sure that there is no impact on components outside the platform, such as Management reporter or Retail. Microsoft also makes sure that the changes are backward compatible and forward compatible.

After the update is applied, Microsoft validates that it was successful, and that the environment is running as expected. As part of this validation, Microsoft runs some basic verification tests to make sure that Microsoft Dynamics 365 for Finance and Operations can be used to complete transactions.

### How do I reschedule the planned maintenance?
You can reschedule planned maintenance by filing a support ticket with Microsoft to request a change in the schedule.

We plan to add this option into LCS so that you can reschedule an update directly through LCS.

### How do I report an issue that is identified during validation of the updates that were applied to the environment?
To report an issue that is identified during update validation, file a support ticket with Microsoft and append the title with ‘Planned Maintenance Window’.

### What happens if the patching fails?
If the patching of a platform update fails or takes longer than the specified maintenance window, a notification will be posted on the Service health dashboard. This issue is considered the highest priority, and the product team becomes involved to address it. However, if there is no quick fix, Microsoft will roll back the update so that the environment can be brought back to a healthy state as soon as possible.

If the patching fails during an operating system–level update, the specific patch is skipped and will be applied in the next update cycle.

### Will I be notified when the update is completed?
If your update is completed within the defined maintenance window, you won’t receive any notification when the update is completed. However, the History page in LCS will be updated to show that the update has been completed.

We are planning to add the ability to notify customers when the downtime window is completed.

### Will I be compensated if the update takes longer than the scheduled maintenance window?
If the update takes longer than the scheduled maintenance window, the extra time is considered unplanned downtime and is subject to the general service level agreement (SLA).

### Who is responsible for managing non-production environments?
Other than the Tier-2 sandbox environment that is included in the Microsoft base offer, customers and partners are responsible for patching non-production environments. You can get the same update that was applied by Microsoft from the Global asset library in LCS. The package name, details, and date information will be included in the email notification.

Customers and partners are responsible for applying operating system–level updates on all Tier-1 environments.

### Will the update from Microsoft require any uptake?
Most of the updates require no uptake from you. If there is a critical security update that requires uptake, you will be notified.

### How do I sign up to be notified about the maintenance window?
If partners, independent software vendors (ISVs), and other interested parties want to be notified about upcoming updates, they have two options:

- Check the Service health.
- Ask to be added to the LCS project as a relevant stakeholder (project owner, environment admin, or additional stakeholder).

### Why can’t these updates be applied in zero downtime?
We are continually working to reduce the necessity of downtime for the service, and many regular maintenance tasks don’t incur downtime. To help guarantee the most predictability, we can’t yet perform all patching in zero downtime.

### How can I update my environments with the package from Microsoft?
Every platform update package from Microsoft is available on the Deployable package tab in the Global asset library. The package name, details, and date information are also included in the email notification that is sent from Microsoft.

You can apply an operating system–level update by turning on Windows Updates on Tier-1 environments. All other environments are updated by Microsoft.

### Because patching of the production environment doesn’t occur until five days after patching of the sandbox environment for a platform update, how do I make sure that all the environments are in the same state and have the same version?
Microsoft applies the update on the Tier-2 sandbox (pre-production) environment. If that update is successful, Microsoft then applies it on the production environment. Notifications for production environment updates are sent five days before the update.

If you don’t want a five-day difference in versions between the Tier-2 sandbox and production environments, you can update your production environment by submitting a service request to the Dynamics Services Engineering (DSE) team to apply the package through the regular production update flow. (The package is available in the Global asset library.)

Even if there is a difference in versions between the sandbox and production environments, you can still use the product. However, you can’t move packages to the production environment or complete true validations until the sandbox and production environments have the same version.

### Is there a way to roll back a package that Microsoft applied?
Currently, there is no way for you to roll back a package that Microsoft applied.

### How are batch jobs handled as part of this maintenance?
Batch jobs are suspended during the maintenance windows and resume when the maintenance is completed.

### Where can I check that the update was completed successfully?
You can verify that the update was completed successfully on the History page in LCS. There, you will see an entry for Microsoft planned maintenance window – Completion.

### Where can I see which updates are included in the package that is being applied?
The Description column in the Global asset library shows what is included in the package.

