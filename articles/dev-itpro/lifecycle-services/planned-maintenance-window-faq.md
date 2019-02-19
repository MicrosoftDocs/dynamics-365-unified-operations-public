---
# required metadata

title: Planned maintenance window FAQ
description: This topic provides answers to frequently asked questions about the Microsoft planned maintenance windows.
author: robadawy
manager: AnnBe
ms.date: 03/13/2018
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
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 6154
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: robadawy
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Planned maintenance window FAQ
[!include [banner](../includes/banner.md)]

### What is a planned maintenance window?
A planned maintenance window is the timeframe that Microsoft has scheduled to apply critical updates to your cloud service.

### How does a planned maintenance window work?
For all planned maintenance, Microsoft will send a notification to all stakeholders **five days** before the patching window begins. The patching window, which is when the environment is patched, is defined by geographic region. Details on the maintenance activity will be included in the notification sent to stakeholders.

### When is this planned maintenance window taken?
To limit the impact on users, the maintenance window is planned according to the region where environments are deployed. The following list shows the maintenance window for each region. All environments fall in one of these three regions. The times are shown in Coordinated Universal Time (UTC, which is also known as Greenwich Mean Time).
- NAM: 2 AM to 10 AM
- EMEA: 10 PM to 6 AM
- APAC: 12 PM to 9 PM

### Will the maintenance from Microsoft require any uptake?
Most of the maintenance operations require no action from your end. If there is a critical security update that requires uptake, you will be notified.

### Who will be notified about the upcoming planned maintenance?
The following stakeholders will be notified about the upcoming maintenance:
- Project owners
- Organization admins
- Environment admins
- Other people who are specified in the list during deployment or through the Notify button on the Environment details page. 

### How do I sign up to be notified about the maintenance window?
If partners, independent software vendors (ISVs), and other interested parties want to be notified about upcoming updates, they can request to be added to the LCS project as a relevant stakeholder (project owner, environment admin, or additional stakeholder).

### Why can’t these updates be applied in zero downtime?
We are continually working to reduce the necessity of downtime for the service, and many regular maintenance tasks don’t incur downtime. To help guarantee the most predictability, we can’t yet perform all patching in zero downtime.

## Microsoft service updates 
We have a seperate FAQ that has details around service updates done by Microsoft. To learn more see the [One Version service updates FAQ](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/get-started/one-version).  

## Operating system-level updates 

### How long is the maintenance window?
Most Operating system–level updates are completed in approximately one hour. However, we ask for a three hour window to handle failures and to bring the system back to a health state. 

The exact downtime for all updates will be included in the maintenance window notification email that is sent to you before the start of the update.

### Where can I learn more about what is applied?
For more information about the updates that will be applied, see [Microsoft Security Bulletins](https://technet.microsoft.com/en-us/security/bulletins.aspx).  

### Where can I track progress of the update?
At this time, during operation system-level updates, LCS does not indicate that any patching is in progress. We are planning to add this functionality sometime in the future.

### What environments are updated?
Operating system–level updates are applied on all Tier-2 sandbox environments that are included as part of the Microsoft base offer. They are also applied on add-ons that have been purchased. However, other environments such as Tier-1 sandbox and demo environments, are the responsibility of the customer or partner.

### What notifications will I receive about upcoming planned maintenance?
You will receive an email notification five days before the update is scheduled to occur. This notification will include information about the environments that will be updated, the update type, the estimated amount of time that the update will take, and any action that you may have to take.

### Will I be notified when the update is completed?
If your update is completed within the defined maintenance window, you won’t receive any notification when the update is completed. 

### How do I report an issue that is identified during validation of the updates that were applied to the environment?
To report an issue that is identified during update validation, file a support ticket with Microsoft and append the title with ‘Planned Maintenance Window’.

### What happens if the patching fails?
If the patching fails during an operating system–level update, the specific patch is skipped and will be applied in the next update cycle.

### Will I be compensated if the update takes longer than the scheduled maintenance window?
If the update takes longer than the scheduled maintenance window, the extra time is considered unplanned downtime and is subject to the general service level agreement (SLA).

### Can I reschedule the planned maintenance?
We do not offer an option to reschedule a planned maintenance. However, you can select to be excluded from the maintenance cycle for the current month. 

### How do I opt out of the current maintenance cycle?
To opt out of the current maintenance cycle, file a support ticket with Microsoft. Your environment will be excluded from the maintenance cycle for the current month. However, your environment will be updated the next month.





