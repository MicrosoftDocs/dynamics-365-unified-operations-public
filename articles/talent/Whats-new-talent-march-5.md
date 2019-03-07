---
# required metadata

title: What's new or changed in Dynamics 365 for Talent (March 5, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 for Talent.
author: Darinkramer
manager: AnnBe
ms.date: 3/5/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
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
# "What's new or changed in Dynamics 365 for Talent (March 5, 2019)"

[!include [banner](includes/banner.md)]

This topic describes features that are either new or changed in Talent

## Changes in Attract

### Extending option sets in Attract

In Attract there are multiple fields that are Option Sets within CDS. We are beginning to introduce the capability to extend the option sets, beginning with the Rejection reason field, Employment type field, and Seniority type field.

[!Important] The job posting to LinkedIn functionality requires the use of the Employment type and Seniority type field in the job details form. The default values in these fields are supported by LinkedIn and are displayed when the job is posted. Therefore, if you are posting jobs to LinkedIn and you modify the existing option set values for these fields, the job will still post, but LinkedIn will not display the custom Employment type and Seniority type values.

## Changes in Onboarding
There are minor bug fixes included with this release.

## Changes Core HR
**Build 8.1.2178**

### Configure workflow to auto-approve or follow workflow when HR or line manager submits or updates time off requests
New workflow conditions have been added to allow for leave requests to be auto-approved if submitted by an employee’s manager or by HR. One way to achieve this auto-approval on a workflow is to enable an automatic action on the workflow approval.

The conditions that have been added are:

•Submitted by
Used to evaluate the system User Id of user who submitted the request to workflow
•Submitted on behalf of 
Used to evaluate if the leave request was submitted on behalf of the worker associated to the request
•Submitted by human resources
Used to evaluate if the system User who submitted the request to workflow is in a Human Resources role
•Submitted by manager
Used to evaluate if the user who submitted the leave request to workflow is a line hierarchy manager of the worker associated to the request


### Enable employee fixed compensation for future position assignments
It is typical that employees join an organization with a future start date. This change enables defining fixed compensation for employees with future position assignments.

### Position Payroll fields blank when requesting an edit to the position
With this change, when requesting changes to existing positions the payroll fields will default with there current values.

### Other misc. bug fixes
Other minor bug fixes are included with this release.

### Upgrade to CDS for Apps
Deadlines to upgrade to CDS for Apps are quickly approaching.   Log into the PowerApps Admin center to determine if your database needs to be upgraded. Click [HERE](https://docs.microsoft.com/en-us/common-data-service/upgradecds/introduction-upgrade-cds) for more information on deadlines and necessary steps to upgrade.

## Coming Soon

###  Advanced compensation security (Fixed and Variable)
In many organizations the compensation and benefits managers may only have access to certain compensation records. They may be for Executives or Regional based employees. With this change HR can manage and maintain the compensation plans for different employee populations in the organization. Fixed and Variable plans can be assigned security roles which will determine the access to the plans and the employee data related to the plans. (Salary, Bonus records…) Only the roles with the given access will be able to process compensation for those employees.

###  Platform Update 24
See additional details for Platform 24 [HERE](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/get-started/whats-new-platform-update-24).
