---
# required metadata

title: What's new or changed in Dynamics 365 Talent (October 1, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent.
author: Darinkramer
manager: AnnBe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
# ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2019-10-01
ms.dyn365.ops.version: Talent

---
# What's new or changed in Dynamics 365 Talent (October 1, 2019)

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

This topic describes features that are either new or changed in Dynamics 365 Talent.

## Changes in Attract

This release includes minor bug fixes for Dynamics 365 Talent: Attract.

## Changes in Onboard

This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Changes in Core HR

Changes described in this section apply to build number 8.1.2509. The numbers in parentheses in some headings refer to support numbers in Microsoft Dynamics Lifecycle Services (LCS).

### Streamlined employee entry and navigation

This functionality is now available in all environments. To turn this feature on, navigate to **System administration > Links > Setup > System parameters > Preview features**. Select **Enhanced worker form and navigation**. This enables these changes for all users. You can turn this option off at any time.

For more information, see [Streamlined employee entry and navigation](./streamlined-employee-entry.md). To watch a video of these changes, see [Dynamics 365 for Talent 2019 release wave 2 overview](https://aka.ms/ROGT19RW2ROV).

### You can enable preview features in Sandbox and Trial environments

When you provision a new instance of Talent, you can specify whether the instance type is Production or Sandbox. Instances of the Sandbox type allow for early trial of new features. If you want one of your existing instances to be updated to the Sandbox instance type, contact Support to initiate the change request.

For more information about how changes are published, see [Provision Talent](./provisioning-talent.md).

### Compensation date defaults to a different date than the position assignment (337694)

With this change, the compensation start date defaults to the position assignment start date.

### Not able to end compensation along with its position assignment (328993)

With this change, you can end compensation when you end the position assignment by using **End assignment** in the **Worker position assignments** page with personnel actions turned on.

### Bank account validation requires routing and account numbers in all locations (340403)

With this week's changes, a new configuration option has been added to disable **Routing number** and **Account number** required validation. 

### Attachments are not enabled in MSS performance journals for performance feedback (341794)

With this week's release, attachments are enabled for feedback items in the performance journal page.

### Leave request details don't sync from Common Data Service to Talent (369608)

With these changes, leave request details that are updated in Common Data Service will sync back to Talent.

### Job description doesn't display for the job in the Skill gap analysis page (369398)

In this week's build, the description will display when selecting the job in the **Skill gap analysis** page.

## Coming soon

### Print performance reviews

Employees, managers, and HR professionals will be able to print an employee's performance review.
