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
ms.reviewer: anbichse
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
# What's new or changed in Dynamics 365 for Talent (June 11, 2019)

[!include [banner](includes/banner.md)]

This topic describes features that are either new or changed in Dynamics 365 for Talent.

## Changes in Attract

### Search engine optimization for job posts

When you turn on **Search Engine Optimization** in the Attract Admin center, Attract informs Google's Indexing API to crawl the webpage when you activate and post a new job or update an existing one, so the job will appear in the search results for Google and other search engines.

Likewise, when you unpost a job, Attract will update the Indexing API so the unposted job will stop appearing in search results.

> [!NOTE]
> Web crawlers don't have a set timeframe for crawling web pages or updating search results.

## Coming soon in Attract

### Job approvals appear on Home page

Approvals appear in an **Approvals** section on the dashboard. Approvers can review their approvals under **Assigned to you**, which displays the job ID, title, other approvers, and date assigned. Users who submit a job for approval can review their jobs under **Requested by you**, which displays the approvers who still need to approve the submitted job.

## Changes in Onboard
This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Changes in Core HR
Changes described in this section apply to build number 8.1.2337.

### Platform Update 27

For additional details about Platform update 27, see [Preview features in Dynamics 365 for Finance and Operations platform update 27 (June 2019)](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/get-started/whats-new-platform-update-27).

### Feature management workspace in Talent

The **Feature management** tab in **System administration** lets you view, enable, disable, and schedule features that have been delivered in each release. By default, new features are turned off. You can use the **Feature management** tab to turn them on and view the documentation for them.

### Common Data Service entity support for custom fields

The following entities now support custom fields: Issuing agency.

### New Common Data Service entities

The following entity has been added: Task group.

## In preview

### Preview features will only be enabled in Sandbox environments
 
Read more about how changes are published in the documentation in [Provision Talent](https://docs.microsoft.com/en-us/dynamics365/unified-operations/talent/provisioning-talent).

When provisioning a new instance of Talent, you can indicate whether the instance type is **Production** or **Sandbox**, which allows early testing of new features. All existing Talent instances will be updated to the **Production** instance type. If you want one of your existing instances to be updated to the **Sandbox** instance type, please contact [Support](https://docs.microsoft.com/en-us/dynamics365/unified-operations/talent/talent-support) to initiate the change request.

### Restrict the leave types in time-off requests

Organizations can offer many different types of leave to employees. However, it might not be appropriate for employees to submit time-off requests for some leave types. Those leave types might be managed by HR instead. In this release, you can configure which leave types employees can submit time-off requests for. 

## Coming soon in Core HR

### View extended reports performance information in manager self-service

A new option will let managers view the performance of both their direct reports and their extended reports. Currently, line managers can assign and update performance goals and issue new reviews, which their employees co-manage. In addition, direct managers and their employees can maintain and update performance journals to help guarantee that the performance review process goes smoothly. When this change is implemented, managers will be able to view and maintain performance-related information for their extended reports in addition to their direct reports.

### Print performance reviews

Employees, managers, and HR will be able to print an employee's performance review.
