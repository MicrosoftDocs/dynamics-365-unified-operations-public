---
# required metadata

title: Extend with Power Apps and Power Automate
description: 
author: andreabichsel
manager: AnnBe
ms.date: 02/01/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-human-resources
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2020-02-01
ms.dyn365.ops.version: Human Resources April 2020 update

---

# Extend with Power Apps and Power Automate

This article describes some examples of extensibility scenarios for Microsoft Dynamics Human Resources that use Microsoft Power Apps and Microsoft Power Automate. You can import the solution package that is associated with each example into your Power Apps environment. You can then use the packages either as guidance or as starting points to implement scenarios that are applicable to your organization.

> [!IMPORTANT]
> If you want to use the templates and app that are described in this article as is, be sure to test them to make sure that they cover all the scenarios that are specific to your implementation.

## Prerequisites

- To import packages, users must have the **Environment Maker** permission.
- To export or import apps, users must have a Power Apps Plan 2 license or a Power Apps Plan 2 trial license.

## Power Automate – Form Connect template

You can use the **Power Automate – Form Connect** template to read data from Microsoft Forms and store it in a Common Data Service entity.

You can also extned this template so you can use it for other scenarios, for example:

- Capture candidate assessments
- Capture results from course questionnaires
- Compile a library of interview questions for human resources administrators
- Capture a candidate's evaluation of the interview process

When a candidate submits a form, Microsoft Power Automate captures the form submission, reads the data, and stores it in the Common Data Service entity.

Download the **Power Automate – Form Connect** template and Custom Entity Structure at [Power Automate – Form Connect](https://go.microsoft.com/fwlink/?linkid=2081988) on the Microsoft Download Center.

## Integration with Office 365 app

You can use the **Integration with Office 365** app to extract team information for users signed in to Microsoft Office 365. It references workers in Human Resources to extract clock-in and clock-out details and exception recordings. Clock-in and clock-out details are stored in custom Common Data Service entities. These details are generally supplied by third-party systems via integration.

You can extend this app to use it in other scenarios. For example, you can use it to show team vacation information, calendar events, and any team-specific events.

Download the **Integration with Office 365** app and Custom Entity Structure at [Integration with Office 365](https://go.microsoft.com/fwlink/?linkid=2081787) on the Microsoft Download Center.

## Power Automate – Email Notification template

You can use the **Power Automate – Email Notification** template for email notification scenarios. Use it to send notification emails to candidates that the hiring team rejects during any stage of the recruiting process.

You can use this template to track changes to the candidate stage throughout the recruiting process, and to send notifications to the hiring team and candidate.

In general, for entities that are stored in Common Data Service, you can set up flows to send notifications for events that occur in Human Resources.

Download the **Power Automate – Email Notification** template at [Power Automate – Email Notification](https://go.microsoft.com/fwlink/?linkid=2082103) on the Microsoft Download Center.

## Power Automate – SQL Connect and execute template

The **Power Automate – SQL Connect and execute** template connects to Microsoft SQL Server and enables running SQL queries.

Although this template is designed to read and update SQL tables, you can extend it for other scenarios. For example, you can use it to fill a staging table in Common Data Service with records from SQL Server, and to periodically synchronize the staging table by using an incremental push from SQL Server.

Download the **Power Automate – SQL Connect and execute** template at [Power Automate – SQL Connect and execute](https://go.microsoft.com/fwlink/?linkid=2081789) on the Microsoft Download Center.

## Power Automate – SharePoint Integration template

You can use the **Power Automate – SharePoint Integration** template to read data from a Microsoft SharePoint list, compare the list with field values for any Common Data Service entity, and send the results of the comparison as a notification email. 

An organization might have a set of skills that it urgently requires, stored as a SharePoint list. When a candidate applies for any job that a set of required skills is listed for, if there is a significant match between the candidate's skill and the skills that are stored in SharePoint, a notification email is sent. In this way, positions that are urgently required are filled faster, because the notifications help recruiters reach out and cross-hire candidates throughout the organization.

You can extend this template for any scenario that involves SharePoint integration.

Download the **Power Automate – SharePoint Integration** template at [Power Automate – SharePoint Integration](https://go.microsoft.com/fwlink/?linkid=2082109) on the Microsoft Download Center.

## See also

- [The Microsoft Power Platform](https://docs.microsoft.com/power-platform/admin/admin-documentation)
- [Migrate app between tenants and environments](https://docs.microsoft.com/power-platform/admin/environment-and-tenant-migration)


