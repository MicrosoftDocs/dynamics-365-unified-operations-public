---
# required metadata

title: Extend Talent with Power Apps and Power Automate
description: This article describes some examples of extensibility scenarios for Microsoft Dynamics 365 Talent - Attract that use Microsoft Power Apps and Microsoft Power Automate.
author: negudava
manager: Annbe
ms.date: 02/06/2020
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
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Talent October 2018 update

---

# Extend Talent with Power Apps and Power Automate

This article describes some examples of extensibility scenarios for Microsoft Dynamics 365 Talent: Attract that use Microsoft Power Apps and Microsoft Power Automate. You can import the solution package that is associated with each example into your Power Apps environment. You can then use the packages either as guidance or as starting points to implement scenarios that are applicable to your organization.

> [!IMPORTANT]
> If you want to use the templates and app that are described in this article "as is," be sure to test them to make sure that they cover all the scenarios that are specific to your implementation.


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

In Microsoft Dynamics 365: Attract, you can use forms in the candidate portal, where candidates fill in details. You can also embed forms as activities in a job template.

When a candidate submits a form, Microsoft Power Automate captures the form submission, reads the data, and stores it in the Common Data Service entity.

To download the **Power Automate – Form Connect** template and Custom Entity Structure, go to [Power Automate – Form Connect](https://go.microsoft.com/fwlink/?linkid=2081988) on the Microsoft Download Center.

## Power Automate – SharePoint Integration

The **Power Automate – SharePoint Integration** template can be used to read data from a Microsoft SharePoint list, compare the list with field values for any Common Data Service entity, and send the results of the comparison as a notification email. 

An organization might have a set of skills that it urgently requires. These skills can be stored in SharePoint as a SharePoint list. When a candidate applies for any job that a set of required skills is listed for, if there is a significant match between the candidate's skill and the skills that are stored in SharePoint, a notification email is sent. This helps fill positions that are urgently required faster, because the notifications help recruiters cross-hire candidates throughout the organization.

This template can be extended so that it can be used for any scenario that involves SharePoint integration.

To download the **Power Automate – SharePoint Integration** template, go to [Power Automate – SharePoint Integration](https://go.microsoft.com/fwlink/?linkid=2082109) on the Microsoft Download Center.

## Referral App

You can use the Referral App to add candidates to a shared talent pool. The referrer can enter **Firstname**, **Lastname**, **Email**, and **LinkedIn URL** when submitting a candidate. The candidate source metadata is then populated with the referrer’s information.

You can embed this app in Employee self service for submitting referrals, or you can use it as a hyperlink in the corporate portal and run it as a stand-alone app.

To download **Referral App**, go to [Dynamics 365 Talent extensibility solution: Referral App](https://www.microsoft.com/download/details.aspx?id=58497) on the Microsoft Download Center. You can import this app and customize it to add additional functionality.

## Additional resources

[The Microsoft Power Platform](https://docs.microsoft.com/power-platform/admin/admin-documentation)</br>
[Migrate app between tenants and environments](https://docs.microsoft.com/power-platform/admin/environment-and-tenant-migration)
