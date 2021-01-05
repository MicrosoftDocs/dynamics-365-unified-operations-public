---
# required metadata

title: What's new or changed in Dynamics 365 Talent (June 11, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent.
author: Darinkramer
manager: AnnBe
ms.date: 06/11/2019
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
ms.search.validFrom: 2019-06-11
ms.dyn365.ops.version: Talent

---
# What's new or changed in Dynamics 365 Talent (June 11, 2019)

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent.

## Changes in Attract

### Search engine optimization for job posts

After you turn on **Search Engine Optimization** in the Dynamics 365 Talent: Attract Admin center, Attract informs the Google Indexing application programming interface (API) to crawl the webpage whenever you activate and post a new job or update an existing job. In this way, the job will appear in the search results for Google and other search engines.

Likewise, whenever you unpost a job, Attract informs the Indexing API, so that the unposted job will stop appearing in search results.

> [!NOTE]
> Web crawlers don't have a defined timeframe for crawling webpages or updating search results.

## Coming soon in Attract

### Job approvals appear on the home page

Approvals appear in an **Approvals** section on the dashboard. Approvers can review their approvals under **Assigned to you**, which shows the job ID, the job title, other approvers, and the date when the job was assigned. Users who submit a job for approval can review their jobs under **Requested by you**, which shows the approvers who must still approve the submitted job.

## Changes in Onboard

This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Changes in Core HR

The changes that are described in this section apply to build number 8.1.2337.

### Platform update 27 for Finance and Operations

For more details about Platform update 27 for Finance and Operations, see [Preview features in Dynamics 365 Finance and Operations platform update 27 (June 2019)](https://docs.microsoft.com/dynamics365/unified-operations/fin-and-ops/get-started/whats-new-platform-update-27).

### Feature management workspace in Talent

The **Feature management** workspace in **System administration** lets you view, enable, disable, and schedule features that have been delivered in each release. By default, new features are turned off. You can use the **Feature management** workspace to turn them on and view the documentation for them.

### Common Data Service entity support for custom fields

The Issuing agency entity now supports custom fields.

### New Common Data Service entities

The Task group entity has been added.

## In preview

### Preview features will be enabled only in sandbox environments

For more information about how changes are published, see [Provision Talent](https://docs.microsoft.com/dynamics365/unified-operations/talent/provisioning-talent).

When you provision a new instance of Talent, you can indicate whether the instance type is Production or Sandbox. The Sandbox instance type allows for early testing of new features. All existing Talent instances will be updated to the **Production** instance type. If you want one of your existing instances to be updated to the **Sandbox** instance type, contact [Support](https://docs.microsoft.com/dynamics365/unified-operations/talent/talent-support) to initiate the change request.

### Restrict the leave types in time-off requests

Organizations can offer many types of leave to employees. However, it might not be appropriate for employees to submit time-off requests for some leave types. Those leave types might be managed by Human resources (HR) instead. In this release, you can configure which leave types employees can submit time-off requests for. 

## Coming soon in Core HR

### View extended information about report performance in manager self-service

A new option will let managers view the performance of both their direct reports and their extended reports. Currently, line managers can assign and update performance goals and issue new reviews. In addition, direct managers and their employees can maintain and update performance journals to help guarantee that the performance review process goes smoothly. When this change is implemented, managers will be able to view and maintain performance-related information for their extended reports in addition to their direct reports.

### Print performance reviews

Employees, managers, and HR will be able to print an employee's performance review.
