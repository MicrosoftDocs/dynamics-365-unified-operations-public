---
# required metadata

title: What's new or changed in Dynamics 365 for Talent (June 11, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 for Talent.
author: Darinkramer
manager: AnnBe
ms.date: 6/11/2019
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
ms.search.validFrom: 2019-06-11
ms.dyn365.ops.version: Talent

---
# "What's new or changed in Dynamics 365 for Talent (June 11, 2019)"

[!include [banner](includes/banner.md)]

This topic describes features that are either new or changed in Dynamics 365 for Talent.

## Changes in Attract

### Search engine optimization for job posts: 

If **Search Engine Optimization** is turned on in **Attract Admin settings**, every time a job gets activated and posted or a job post is updated, we will inform the Google Indexing API to crawl the web page and the job should start appearing in Google and other web search results pages. Similarly, when a job gets unposted, the indexing APIs will be updated so that the unposted jobs do not show up search results. For existing jobs to be picked up, please re-post them to the Talent Careers site. 
**Please note**: there is no defined time frame within which web crawlers will look at job updates to update results on their end.  

## Coming soon in Attract

### Job approvals on home page

Approvals appear in an **Approvals** section on the dashboard. Approvers can review their approvals under **Assigned to you**, which displays the job ID, title, other approvers, and date assigned. Users who submit a job for approval can review their jobs under **Requested by you**, which displays the approvers who still need to approve the submitted job.

## Changes in Onboard
This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Changes in Core HR
Changes described in this section apply to build number 8.1.2337.

### Platform Update 27

For additional details about Platform update 27, see [Preview features in Dynamics 365 for Finance and Operations platform update 27 (June 2019)]
https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/get-started/whats-new-platform-update-27

### Feature management workspace in Talent

The Feature management experience provides a workspace where you can view, enable, disable, and schedule features that have been delivered in each release. By default, new features are turned off. You can use the workspace to turn them on and view the documentation for them.

### Common Data Service entity support for custom fields

In this week's release, the following entities now support custom fields: Issuing agency

### New CDS Entities

In this week's release, the following entity has been added: Task group

## In preview

### In Preview features will only be enabled in "Sandbox" Environments.
 
Read more about how changes are published in the documentation [HERE](https://docs.microsoft.com/en-us/dynamics365/unified-operations/talent/provisioning-talent).

When provisioning a new instance of Talent, you can indicate whether the instance type is **Production** or **Sandbox**, which allows for early testing of new features. All existing Talent instances will be updated to the **Production** instance type. If you want one of your existing instances to be updated to the **Sandbox** instance type, please contact [Support](https://docs.microsoft.com/en-us/dynamics365/unified-operations/talent/talent-support) to initiate the change request.

### Restrict the leave types in time off requests

Organizations can offer many different types of leave to employees. Some of these leave types might not be appropriate for employees to submit time off for and are managed by Human Resources (HR) instead. With this release, you can configure which leave types employees can submit time-off requests for. 

## Coming soon in Core HR

### Ability to view extended reports performance information in manager self service

The ability to view and update performance goals, reviews and journals is key. Direct line managers today are able to assign and update goals. They can issue new reviews and co-manage the process along with employees. Performance journals can be maintained and updated by both parties to help guarantee the performance reviews and process goes smoothly. With this change, managers will now able to view and maintain performance related information for their extended reports the same as they could for their direct reports. A new option will be available to allow for viewing of direct or extended reports performance information.
.
### Print performance reviews
With this change, employees, managers and HR will now be able to print an employee’s performance review.
