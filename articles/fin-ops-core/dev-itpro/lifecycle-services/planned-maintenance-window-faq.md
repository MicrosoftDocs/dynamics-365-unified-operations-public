---
title: Planned maintenance window FAQ
description: Access answers to frequently asked questions about the Microsoft planned maintenance windows, including infrastructure updates.
author: angelmarshall
ms.author: tsmarsha
ms.topic: article
ms.date: 02/25/2022
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form:
ms.dyn365.ops.version: AX 7.0.0
---

# Planned maintenance window FAQ
[!include [banner](../includes/banner.md)]

> [!IMPORTANT]
> This article is applicable to Infrastructure-as-a-Service (IaaS) environments and will be removed soon. For up-to-date information, see [Planned maintenance in self-service environments FAQ](../deployment/plannedmaintenance-selfservice.md).

### What is a planned maintenance window?
A planned maintenance window is the timeframe that Microsoft has scheduled to apply infrastructure or [service updates](../../fin-ops/get-started/one-version.md) to your cloud service.

### How does a planned maintenance window work?
For planned maintenance scheduled on your Tier 2 through Tier 5 sandbox environments and production environments, Microsoft will send a notification to all stakeholders **five business days** before the start of the patching window. The patching window is the period when the environment is patched. It's defined by geographic region. Details about the maintenance activity will be included in the notification that is sent to stakeholders. For Microsoft-managed Tier 1 environments, we will not send any notifications before the update. 

### When is this planned maintenance window taken?
To limit the impact on users, the maintenance window is planned according to the region where environments are deployed. The following list shows the maintenance window for each region. All environments fall into one of these three regions. The times are shown in Coordinated Universal Time (UTC, which is also known as Greenwich Mean Time).

- **NAM:** 2 AM to 10 AM
- **EMEA:** 10 PM to 6 AM
- **APAC:** 12 PM to 9 PM

### Will the maintenance from Microsoft require any uptake?
Most of the maintenance operations require no action on your end. If there is a critical security update that requires uptake, you will be notified.

### Who will be notified about the upcoming planned maintenance?
The following stakeholders will be notified about the upcoming maintenance:

- Project owners
- Organization admins
- Environment admins
- Other people who are specified in the list during deployment or through the **Notify** button on the environment details page in Microsoft Dynamics Lifecycle Services (LCS)

### How do I sign up to be notified about the maintenance window?
Any partner, independent software vendor (ISV), and other interested party who wants to be notified about upcoming updates can request to be added to the LCS project as a relevant stakeholder (project owner, environment admin, or additional stakeholder).

### Why can't these updates be applied in zero downtime?
Microsoft is continually working to reduce the necessity of downtime for the service, and many regular maintenance tasks don't incur downtime. However, to help guarantee the most predictability, Microsoft can't yet do all patching in zero downtime.

## Microsoft service updates 
A separate set of frequently asked questions (FAQ) provides details about service updates that are done by Microsoft. See [One Version service updates FAQ](../../fin-ops/get-started/one-version.md).

## Infrastructure updates 

### How long is the maintenance window?
Most operating system–level updates are completed in approximately one hour. However, Microsoft asks for a three-hour window, so that there is time to handle any failures and to bring the system back to a healthy state. 

The exact downtime for all updates will be included in the maintenance window notification email that is sent to you before the start of the update.

### How frequent are the updates?
Operating system–level updates are applied monthly to your Microsoft-managed Tier 2 through Tier 5 sandbox environments and to the production environments. However, Microsoft-managed Tier 1 environments are updated weekly in the maintenance windows defined per region.

### Where can I learn more about what is applied?
For more information about the updates that will be applied, see [Microsoft Security Bulletins](/security-updates/).

### Where can I track progress of the update?
During operating system–level updates, LCS doesn't currently indicate that any patching is in progress. However, Microsoft plans to add this functionality at some point.

### What environments are updated?
Operating system–level updates are applied to all Microsoft-managed environments that are included as part of the Microsoft base offer. This includes your Tier 1, Tier 2 through Tier 5, and Production environments. They are also applied to add-ons that have been purchased. However, other environments, such as environments hosted in your subscription (known as Cloud hosted environments), are the responsibility of the customer or partner.

### What notifications will I receive about upcoming planned maintenance?
You will receive a notification email for the scheduled update on your Tier 2 to Tier 5 sandbox environment and production environment, five days before the update is scheduled to occur. This email will include information about the environments that will be updated, the update type, the estimated amount of time that the update will take, and any action that you might have to take. We do not send notifications for Microsoft-managed Tier 1 environments. 

### Will I be notified when the update is completed?
If your update is completed within the defined maintenance window, you won't receive any notification when the update is completed. 

### How do I report an issue that is identified during validation of the updates that were applied to the environment?
To report an issue that is identified during update validation, file a support ticket with Microsoft and append the title with 'Planned Maintenance Window'.

### What happens if the patching fails?
If the patching fails during an operating system–level update, the specific patch is skipped and will be applied in the next update cycle.

### Will I be compensated if the update takes longer than the scheduled maintenance window?
If the update takes longer than the scheduled maintenance window, the extra time is considered unplanned downtime and is subject to the general service level agreement (SLA).

### How do I reschedule security maintenance activities?
Security maintenance helps ensure a secure environment, and not doing the maintenance could potentially introduce an avoidable security risk. 

If there is an absolute business need and you are unable to move forward with this maintenance during the timeframe listed above, you can request to reschedule the current maintenance activity for Tier 2 through Tier 5 sandbox environments and production environments by filing a support ticket with Microsoft. The deadline for filing the support ticket to request a reschedule will be included in your notification email. Any request submitted after that deadline will not be honored. 

We do not offer rescheduling of security maintenance activities on Microsoft-managed Tier 1 environments.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
