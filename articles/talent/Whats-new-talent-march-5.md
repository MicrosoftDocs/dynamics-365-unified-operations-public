---
# required metadata

title: What's new or changed in Dynamics 365 Talent (March 5, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent.
author: Darinkramer
manager: AnnBe
ms.date: 03/05/2019
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
ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2019-03-05
ms.dyn365.ops.version: Talent

---
# What's new or changed in Dynamics 365 Talent (March 5, 2019)

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

This topic describes features that are either new or changed in Talent.

## Changes in Attract

### Extending option sets in Attract

In Attract, there are multiple fields that are option sets within the Common Data Service. New capabilities have been introduced to extend the option sets, beginning with the **Rejection** reason field, **Employment type** field, and **Seniority type** field.

> [!IMPORTANT]
> The job posting to LinkedIn functionality requires the use of the **Employment type** and **Seniority type** fields on the **Job details** page. The default values in these fields are supported by LinkedIn and are displayed when the job is posted. If you are posting jobs to LinkedIn and you modify the existing option set values for these fields, the job will still post, but LinkedIn will not display the custom **Employment type** and **Seniority type** values.

## Changes in Onboarding

### Private preview for Onboard teams
You can now easily share and collaborate on templates across your entire organization. For more information, see [Share best practices across your organization using Onboard Teams](https://docs.microsoft.com/business-applications-release-notes/April19/dynamics365-talent/onboard/share-best-practices-teams).

### Private preview for assignee placeholders
You can enrich your templates by assigning activities to roles instead of individuals. Roles are then assigned to individuals at the time of guide creation. For more information, see [Streamline guide administration by assigning activities to roles](https://docs.microsoft.com/business-applications-release-notes/April19/dynamics365-talent/onboard/assign-activities-roles).

## Changes in Core HR
**Build 8.1.2178**

### Configure workflow to auto-approve or follow workflow when an HR or line manager submits or updates time off requests
New workflow conditions have been added to allow for leave requests to be automatically approved if submitted by an employee’s manager or by HR. One way to achieve this auto-approval on a workflow is to enable an automatic action on the workflow approval.

The conditions that have been added include:

- Submitted by - Used to evaluate the system user ID of the user who submitted the request to workflow.
- Submitted on behalf of - Used to evaluate if the leave request was submitted on behalf of the worker associated to the request.
- Submitted by human resources - Used to evaluate if the system user who submitted the request to workflow is in a Human Resources role.
- Submitted by manager - Used to evaluate if the user who submitted the leave request to workflow is a line hierarchy manager of the worker associated to the request.

### Enable employee fixed compensation for future position assignments
It is typical for employees to join an organization with a future start date. This change enables defining fixed compensation for employees with future position assignments.

### Position Payroll fields are blank when editing the position
With this change, when requesting changes to existing positions, the payroll fields will now default to the current values.

### Other miscellaneous bug fixes
Other minor bug fixes are included with this release.

### Upgrade to Common Data Service
Deadlines to upgrade to Common Data Service are quickly approaching. Sign in to the Power Apps Admin center to determine if your database needs to be upgraded. For more information about deadlines and necessary steps to upgrade, see [Upgrade to Common Data Service](https://docs.microsoft.com/common-data-service/upgradecds/introduction-upgrade-cds).

## Coming soon

###  Advanced compensation security (fixed and variable)
In many organizations, compensation and benefits managers can only access certain compensation records, such as records for executives or regional-based employees. With this change, you can manage and maintain the compensation plans for different employee populations in the organization. Fixed and variable plans can be assigned security roles, which will determine the access to the plans and the employee data related to the plans, such as salary or bonus records. Only the roles with the given access will be able to process compensation for those employees.

###  Platform update 24 for Finance and Operations
For additional details about Platform update 24 for Finance and Operations, see [What's new or changed in Finance and Operations platform update 24 (March 2019)](https://docs.microsoft.com/dynamics365/unified-operations/fin-and-ops/get-started/whats-new-platform-update-24).
