---
title: Planned maintenance window FAQ
description: Access answers to frequently asked questions about the Microsoft planned maintenance windows, including infrastructure updates.
author: angelmarshall
ms.author: johnmichalak
ms.topic: faq
ms.date: 01/20/2026
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
> This article applies to Infrastructure-as-a-Service (IaaS) environments and will be removed soon. For up-to-date information, see [Planned maintenance in self-service environments FAQ](../deployment/plannedmaintenance-selfservice.md).

### What is a planned maintenance window?

A planned maintenance window is the timeframe that Microsoft schedules to apply infrastructure or [service updates](../../fin-ops/get-started/one-version.md) to your cloud service.

### How does a planned maintenance window work?

For planned maintenance on your Tier 2 through Tier 5 sandbox environments and production environments, Microsoft sends a notification to all stakeholders **five business days** before the start of the patching window. The patching window is the period when the environment is patched. It's defined by geographic region. The notification to stakeholders includes details about the maintenance activity. For Microsoft-managed Tier 1 environments, Microsoft doesn't send any notifications before the update.

### When is this planned maintenance window?

To limit the impact on users, Microsoft plans the maintenance window according to the region where environments are deployed. The following list shows the maintenance window for each region. All environments fall into one of these three regions. The times are shown in Coordinated Universal Time (UTC, which is also known as Greenwich Mean Time).

- **NAM:** 2 AM to 10 AM
- **EMEA:** 10 PM to 6 AM
- **APAC:** 12 PM to 9 PM

### Does the maintenance from Microsoft require any uptake?

Most of the maintenance operations require no action on your end. If a critical security update requires uptake, you receive a notification.

### Who gets notified about the upcoming planned maintenance?

The following stakeholders get notified about the upcoming maintenance:

- Project owners
- Organization admins
- Environment admins
- Other people specified in the list during deployment or through the **Notify** button on the environment details page in Microsoft Dynamics Lifecycle Services

### How do I sign up to get notified about the maintenance window?

Partners, independent software vendors (ISVs), and other interested parties who want to get notified about upcoming updates can request to be added to the Lifecycle Services project as a relevant stakeholder (project owner, environment admin, or additional stakeholder).

### Why can't these updates be applied with zero downtime?

Microsoft is continually working to reduce the necessity of downtime for the service, and many regular maintenance tasks don't cause downtime. However, to help guarantee the most predictability, Microsoft can't yet do all patching with zero downtime.

## Microsoft service updates

A separate set of frequently asked questions (FAQ) provides details about service updates that Microsoft does. See [One Version service updates FAQ](../../fin-ops/get-started/one-version.md).

## Infrastructure updates

### How long is the maintenance window?

Most operating system–level updates complete in approximately one hour. However, Microsoft asks for a three-hour window, so that there's time to handle any failures and to bring the system back to a healthy state.

The maintenance window notification email that Microsoft sends you before the start of the update includes the exact downtime for all updates.

### How frequent are the updates?

Microsoft applies operating system–level updates monthly to your Microsoft-managed Tier 2 through Tier 5 sandbox environments and to the production environments. However, Microsoft-managed Tier 1 environments are updated weekly in the maintenance windows defined per region.

### Where can I learn more about what is applied?

For more information about the updates that Microsoft applies, see [Microsoft Security Bulletins](/security-updates/).

### Where can I track progress of the update?

During operating system–level updates, Lifecycle Services doesn't currently indicate that any patching is in progress. However, Microsoft plans to add this functionality.

### What environments are updated?

Microsoft applies operating system–level updates to all Microsoft-managed environments that are included as part of the Microsoft base offer. This update process includes your Tier 1, Tier 2 through Tier 5, and production environments. Microsoft also applies updates to purchased add-ons. However, you or your partner are responsible for updating other environments, such as environments hosted in your subscription (known as Cloud hosted environments).

### What notifications will I receive about upcoming planned maintenance?

You receive a notification email for the scheduled update on your Tier 2 to Tier 5 sandbox environment and production environment, five days before the update is scheduled to occur. This email includes information about the environments that Microsoft updates, the update type, the estimated amount of time that the update takes, and any action that you might have to take. Microsoft doesn't send notifications for Microsoft-managed Tier 1 environments.

### Will I be notified when the update is completed?

If the update completes within the defined maintenance window, you don't receive any notification when the update is completed.

### How do I report an issue that is identified during validation of the updates that were applied to the environment?

To report an issue that you identify during update validation, file a support ticket with Microsoft and append the title with 'Planned Maintenance Window'.

### What happens if the patching fails?

If patching fails during an operating system–level update, the update process skips the specific patch. The process applies the patch in the next update cycle.

### Am I compensated if the update takes longer than the scheduled maintenance window?

If the update takes longer than the scheduled maintenance window, the extra time counts as unplanned downtime and falls under the general service level agreement (SLA).

### How do I reschedule security maintenance activities?

Security maintenance helps ensure a secure environment. Not doing the maintenance could potentially introduce an avoidable security risk.

If there's an absolute business need and you can't move forward with this maintenance during the timeframe listed earlier, you can request to reschedule the current maintenance activity for Tier 2 through Tier 5 sandbox environments and production environments by filing a support ticket with Microsoft. The deadline for filing the support ticket to request a reschedule is included in your notification email. Microsoft doesn't honor any request submitted after that deadline.

Microsoft doesn't offer rescheduling of security maintenance activities on Microsoft-managed Tier 1 environments.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
