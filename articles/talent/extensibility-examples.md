---
# required metadata

title: Extend Talent by using PowerApps and Microsoft Flow - Example scenarios
description: This topic describes some examples of extensibility scenarios for Microsoft Dynamics 365 for Talent that use Microsoft PowerApps and Microsoft Flow.
author: negudava
manager: Annbe
ms.date: 05/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: Dynamics 365 for Talent;PowerApps;Flow;Common Data Service
# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Talent;Core;Experience Apps
# ms.tgt_pltfrm: 
ms.custom:
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: negudava
ms.search.validFrom: 2019-03-04
ms.dyn365.ops.version: Talent October 2018 update

---

# Extend Talent by using PowerApps and Microsoft Flow - Example scenarios

This topic describes some examples of extensibility scenarios for Microsoft Dynamics 365 for Talent that use Microsoft PowerApps and Microsoft Flow. You can import the solution package that is associated with each example into your PowerApps environment. You can then use the packages either as guidance or as starting points to implement scenarios that are applicable to your organization.

> [!IMPORTANT]
> If you want to use the templates and app that are described in this topic "as is," be sure to test them to make sure that they cover all the scenarios that are specific to your implementation.


## Prerequisites

- To import packages, users must have the **Environment Maker** permission.
- To export or import apps, users must have a PowerApps Plan 2 license or a PowerApps Plan 2 trial license.

## Flow – Form Connect

The **Flow – Form Connect** template can be used to read data from Microsoft Forms and store it in a Common Data Service entity.

This template can be extended so that it can be used for other scenarios. Here are some examples:

- Capture candidate assessments.
- Capture results from course questionnaires.
- Compile a library of interview questions for Human resources (HR) administrators.
- Capture a candidate's evaluation of the interview process

In Microsoft Dynamics 365: Attract, forms can appear in Candidate portal, and candidates can fill in details. Forms can also be embedded as activities in a job template.

When a candidate submits a form, Microsoft Flow captures the form submission, reads the data, and stores it in the Common Data Service entity.

To download the **Flow – Form Connect** template and Custom Entity Structure, go to [Flow – Form Connect](https://go.microsoft.com/fwlink/?linkid=2081988) on the Microsoft Download Center.

## Initiate and Extract Parameters Passed to Powerapps

The **Initiate and Extract Parameters Passed to Powerapps** template can be used as a starting point for any PowerApps scenario that is specific to Attract. It includes all the default parameters that are passed by Attract, such as **Job Application**, **Candidate ID**, and **JobID**.

This template can be used to retrieve a candidate assessment form, so that a hiring manager can view the assessment that a candidate filled in.

Apps that are created by using PowerApps can be embedded into the job template in Attract.

To download the **Initiate and Extract Parameters Passed to Powerapps** template and Custom Entity Structure, go to [Initiate and Extract Parameters Passed to Powerapps](https://go.microsoft.com/fwlink/?linkid=2081991) on the Microsoft Download Center.

## Integration with Office 365

The **Integration with Office 365** app can be used to extract team information for signed-in users from Microsoft Office 365. It references workers in Talent to extract clock-in and clock-out details and exception recordings. Clock-in and Clock-out details are stored in custom Common Data Service entities. The assumption is that these details are filled in from third-party systems via integration.

This app can be extended so that it can be used for other scenarios. For example, it can be used to show team vacation information, calendar events, and any team-specific events.

To download the **Integration with Office 365** app and Custome Entity Structure, go to [Integration with Office 365](https://go.microsoft.com/fwlink/?linkid=2081787) on the Microsoft Download Center.

## Flow – Email Notification

The **Flow – Email Notification** template can be used for email notification scenarios. It can be used to trigger notification emails to candidates that the hiring team rejects during any stage of the recruiting process.

This template can be extended to track changes to the candidate stage throughout the recruiting process, and to send notifications to the hiring team and candidate.

In general, for entities that are stored in Common Data Service, flows can be set up to send notifications for events that occur in Core HR, Attract, or Dynamics 365 Talent: Onboard.

To download the **Flow – Email Notification** template, go to [Flow – Email Notification](https://go.microsoft.com/fwlink/?linkid=2082103) on the Microsoft Download Center.

## Flow – SQL Connect and execute

The **Flow – SQL Connect and execute** template connects to Microsoft SQL Server and enables SQL queries to be run.

Although this template is designed to read and update SQL tables, it can be extended so that it can be used for other scenarios. For example, it can be used to fill a staging table in Common Data Service with records from SQL Server, and to periodically synchronize the staging table by using an incremental push from SQL Server.

To download the **Flow – SQL Connect and execute** template, go to [Flow – SQL Connect and execute](https://go.microsoft.com/fwlink/?linkid=2081789) on the Microsoft Download Center.

## Flow – SharePoint Integration

The **Flow – SharePoint Integration** template can be used to read data from a Microsoft SharePoint list, compare the list with field values for any Common Data Service entity, and send the results of the comparison as a notification email. 

An organization might have a set of skills that it urgently requires. These skills can be stored in SharePoint as a SharePoint list. When a candidate applies for any job that a set of required skills is listed for, if there is a significant match between the candidate's skill and the skills that are stored in SharePoint, a notification email is sent. In this way, positions that are urgently required are filled faster, because the notifications help recruiters reach out and cross-hire candidates throughout the organization.

This template can be extended so that it can be used for any scenario that involves SharePoint integration.

To download the **Flow – SharePoint Integration** template, go to [Flow – SharePoint Integration](https://go.microsoft.com/fwlink/?linkid=2082109) on the Microsoft Download Center.

## Admin console to manage talent pools

When you enable integration with LinkedIn, Attract automatically createas a LinkedIn talent pool. When a recruiter exchanges InMail with a recruit through LinkedIn, Attract creates a profile for the recruit, and the recruit becomes a member of the LinkedIn talent pool. This PowerApps app is useful for reorganizing candidates in talent pools based on skill.

Run this PowerApps app as an admin console to perform the following tasks:

- List candidates in a talent pool
- Add and remove candidates from a talent pool
- Move candidates from one talent pool to another
- Determine whether candidates are already part of a talent pool before moving them
- Check the skills of candidates before moving them to other talent pools

This PowerApps app uses many-to-many relationships, so you can use it as a template for other scenarios where you need to extract records that have many-to-many relationships.

To download the **Admin console to manage talent pools** template,  go to [Admin console to manage talent pools](https://www.microsoft.com/downloads/details.aspx?FamilyID=780a5eee-0e2a-4159-9a83-009f9ccdc469) on the Microsoft Download Center.

## Additional resources

[The Microsoft Power Platform](https://docs.microsoft.com/power-platform/admin/admin-documentation)

[Migrate app between tenants and environments](https://docs.microsoft.com/en-us/power-platform/admin/environment-and-tenant-migration)
