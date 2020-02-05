---
# required metadata

title: Extend Talent with Power Apps and Power Automate
description: This topic describes some examples of extensibility scenarios for Microsoft Dynamics 365 HumanResources and Attract that use Microsoft Power Apps and Microsoft Power Automate.
author: negudava
manager: Annbe
ms.date: 05/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: Dynamics 365 Talent;PowerApps;Flow;Common Data Service
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

# Extend Talent with Power Apps and Power Automate

This topic describes some examples of extensibility scenarios for Microsoft Dynamics 365 Talent that use Microsoft Power Apps and Microsoft Power Automate. You can import the solution package that is associated with each example into your Power Apps environment. You can then use the packages either as guidance or as starting points to implement scenarios that are applicable to your organization.

> [!IMPORTANT]
> If you want to use the templates and app that are described in this topic "as is," be sure to test them to make sure that they cover all the scenarios that are specific to your implementation.


## Prerequisites

- To import packages, users must have the **Environment Maker** permission.
- To export or import apps, users must have a Power Apps Plan 2 license or a Power Apps Plan 2 trial license.

## Power Automate – Form Connect

The **Power Automate – Form Connect** template can be used to read data from Microsoft Forms and store it in a Common Data Service entity.

This template can be extended so that it can be used for other scenarios. Here are some examples:

- Capture candidate assessments.
- Capture results from course questionnaires.
- Compile a library of interview questions for Human resources (HR) administrators.
- Capture a candidate's evaluation of the interview process

In Microsoft Dynamics 365: Attract, forms can appear in Candidate portal, and candidates can fill in details. Forms can also be embedded as activities in a job template.

When a candidate submits a form, Microsoft Power Automate captures the form submission, reads the data, and stores it in the Common Data Service entity.

To download the **Power Automate – Form Connect** template and Custom Entity Structure, go to [Power Automate – Form Connect](https://go.microsoft.com/fwlink/?linkid=2081988) on the Microsoft Download Center.


## Integration with Office 365, PowerAutomate

The **Integration with Office 365** app can be used to extract team information for signed-in users from Microsoft Office 365. It references workers in Talent to extract employee identification types. Managers can check  expiration dates of employee identification types and can send an outlook reminder if the employee identification type is expiring. PowerAutomate is integrated with PowerApp to  send this reminder. Confirmation will be sent back to PowerApp from PowerAutomate when the reminder is sent.  Identification types include driver's license, passport, and other acceptable forms of ID.

You can extend this app for other scenarios. For example, you can use it to show team vacation information, calendar events, and any team-specific events.

To download the **Integration with Office 365, PowerAutomate** app , go to [Integration with Office 365](https://go.microsoft.com/fwlink/?linkid=2081787) on the Microsoft Download Center.

## Power Automate – SQL Connect and execute

The **Power Automate – SQL Connect and execute** template connects to Microsoft SQL Server and enables SQL queries to be run.

Although this template is designed to read and update SQL tables, it can be extended so that it can be used for other scenarios. For example, it can be used to fill a staging table in Common Data Service with records from SQL Server, and to periodically synchronize the staging table by using an incremental push from SQL Server.

Advanced Query is integrated with Flow to enable Data transformation and incremental push.

To download the **Power Automate – SQL Connect and execute** template, go to [Power Automate – SQL Connect and execute](https://go.microsoft.com/fwlink/?linkid=2081789) on the Microsoft Download Center.

## Power Automate – SharePoint Integration

The **Power Automate – SharePoint Integration** template can be used to read data from a Microsoft SharePoint list, compare the list with field values for any Common Data Service entity, and send the results of the comparison as a notification email. 

An organization might have a set of skills that it urgently requires. These skills can be stored in SharePoint as a SharePoint list. When a candidate applies for any job that a set of required skills is listed for, if there is a significant match between the candidate's skill and the skills that are stored in SharePoint, a notification email is sent. In this way, positions that are urgently required are filled faster, because the notifications help recruiters reach out and cross-hire candidates throughout the organization.

This template can be extended so that it can be used for any scenario that involves SharePoint integration.

To download the **Power Automate – SharePoint Integration** template, go to [Power Automate – SharePoint Integration](https://go.microsoft.com/fwlink/?linkid=2082109) on the Microsoft Download Center.

## Referral App
You can use the Referral App to add candidates to a shared talent pool. The referrer can enter **Firstname**, **Lastname**, **Email**, and **Linkedln URL** when submitting a candidate. The candidate source metadata is then populated with the referrer’s information.

You can embed this app in Employee self-service (ESS) for submitting referrals, or you can be use it as a hyperlink in the Corporate Portal and run as a stand-alone app.

To download **Referral App**, go to [Dynamics 365 Talent extensibility solution: Referral App](https://www.microsoft.com/downloads/details.aspx?FamilyID=9a59c9d1-f8a1-4d4d-b768-cfc4f4eb9d0d) on the Microsoft Download Center. You can import this app and customize it to add additional functionality.

## Additional resources

[The Microsoft Power Platform](https://docs.microsoft.com/power-platform/admin/admin-documentation)

[Migrate app between tenants and environments](https://docs.microsoft.com/power-platform/admin/environment-and-tenant-migration)
