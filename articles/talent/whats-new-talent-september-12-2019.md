---
# required metadata

title: What's new or changed in Dynamics 365 for Talent (September 10, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 for Talent.
author: Darinkramer
manager: AnnBe
ms.date: 9/10/2019
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
ms.search.validFrom: 2019-09-10
ms.dyn365.ops.version: Talent

---
# What's new or changed in Dynamics 365 for Talent (September 10, 2019)

This topic describes features that are either new or changed in Dynamics 365 for Talent.

## Changes in Attract

### Candidate e-mail login

Candidates can now use any e-mail address to create an account and login to a Talent career site to apply for jobs and look up their application status. This is in addition to already being able to log on to the Talent career site using their social accounts or their organization credentials.

### Job activation and posting

We have made a few changes to job activation and posting. You need to activate jobs before posting them to the Talent career site or to any external job boards, including LinkedIn or Broadbean.

## Changes in Onboard

This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Changes in Core HR

Changes described in this section apply to build number 8.1.2482. The numbers in parentheses in some headings refer to support numbers in Microsoft Dynamics Lifecycle Services (LCS).

### You can enable preview features in Sandbox and Trial environments

When you provision a new instance of Talent, you can specify whether the instance type is Production or Sandbox. Instances of the Sandbox type allow for early testing of new features. If you want one of your existing instances to be updated to the Sandbox instance type, contact Support to initiate the change request.

For more information about how changes are published, see [Provision Talent](./provisioning-talent.md).

### Platform update 29

For more details about Platform update 29, see [Preview features in Dynamics 365 for Finance and Operations platform update 29 (October 2019)](https://docs.microsoft.com/dynamics365/unified-operations/fin-and-ops/get-started/whats-new-platform-update-29).

### New job base entity available in data management framework (347202)

With this release, a new Base Job entity is available for importing/exporting data. 

### Worker advanced security policy incorrectly displays positions in Position Hierarchy (354868)

With this release, positions no longer display open with a "blank" worker when users have restricted access.

### Job form close box won't close form in certain situations (342467)

This release includes a change that allows the Job form to close in all scenarios.

### New case on employee record is locked for Human Resources manager role (337111)

With this change, the case management form is no longer locked when accessing it from the employee form.

### Employment end date always defaults to 23:59:59 (351492)

With this change, you can change the employment date to a time other than 23:59:59 when manually ending an employment.

### Unable to set up expiration date on an earning code through Data management (336604)

In this release, you can set up earning codes that expire through the **PayrollWorkerPositionEarningCodeEntity** entity.

### Employee development analytic report doesn't display data (348737)

In this week's release, the analytics for employee skills has been updated to provide accurate reporting.

### Terms of employment date/time don't default to beginning of day (349101)

With this change, the start date/time now defaults to beginning of day and the end date/time defaults to end of day.

### Changing the employment end date on Worker action form displays an error (354092) 

This change corrects an issue when modifying the employment end date as part of the worker action.

### Applying onboarding checklists across companies (338433)

This release now provides the ability to apply checklists for employees that are employed in legal entities other than the signed-in legal entity.

## In preview

### Streamlined employee entry and navigation

This functionality is now available in sandbox environments. To turn this feature on, navigate to **System administration > Links > Setup > System parameters > Preview features**. Select **Enhanced worker form and navigation**. This will enable these changes for all users. You can turn this option off at any time.

For more information, see [Streamlined employee entry and navigation](./streamlined-employee-entry.md).
