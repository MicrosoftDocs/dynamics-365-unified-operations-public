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
# "What's new or changed in Dynamics 365 for Talent (September 10, 2019)"

[!include [banner](includes/banner.md)]

This topic describes features that are either new or changed in Dynamics 365 for Talent.

## Changes in Attract

### Candidate e-mail login experience

Candidates can now use any e-mail address to create an account and login to Talent career site to apply for jobs and look up their application status. This is in addition to a candidate already being able to log on to the Talent career site using their social accounts or their organization credentials.

### Job activation and posting experience

We have made few changes to the job activation and posting experiences. Jobs needs to be activated before they can be posted to the Talent career site or to any of the external job boards including LinkedIn or Broadbean.

## Changes in Onboard
This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Changes in Core HR
Changes described in this section apply to build number 8.1.2482.

### Reminder - Preview features can be enabled in Sandbox and Trial environments

When you provision a new instance of Talent, you can specify whether the instance type is Production or Sandbox. Instances of the Sandbox type allow for early testing of new features. If you want one of your existing instances to be updated to the Sandbox instance type, contact Support to initiate the change request.

For more information about how changes are published, see [Provision Talent](./provisioning-talent.md).

### Platform update 29

For more details about Platform update 29, see [Preview features in Dynamics 365 for Finance and Operations platform update 29 (October 2019)](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/get-started/whats-new-platform-update-29).

### New job base entity available in data management framework (347202)

With this release a new Base Job entity is available for importing/exporting data. 

### Worker advanced security policy incorrectly displaying positions in Position Hieararchy (354868)

With this release, positions no longer display open with a "blank" worker when users have restricted access.

### Job form close box won't close form in certain situations (342467)

This release includes a change that allows for the Job form to be closed in all scenarios.

### New case on employee record is locked for HR manager role (337111)

With this change, the case management form is no longer locked when accessing from the employee form.

### Employment end date always defaults to 23:59:59 (351492)

With this change, the employment date can be changed to a time other than 23:59:59 when manually ending an employment.

### TUnable to set up expiring date on the earning code through Data management (336604)

In this release, you are able to set up earning codes that expire through the "PayrollWorkerPositionEarningCodeEntity" entity.

### Employee development analytic report not displaying data (348737)

In this week's release, the analytics for employee skills has been updated to provide accurate reporting.

### Terms of employment date/time not defaulting to beginning of day (349101)

With this change, the start date/time will now default to the beginning of day and the end date/time will default to end of day.

### Changing the employment end date on Worker action form displays an error (354092) 

This changes corrects an issue when modifying the employment end date as part of the worker action.

### Applying onboarding checklists across companies (338433)

This release now provides the ability to apply checklists for employees that are employed in legal entities other than the logged in legal entity.

## In preview

### Streamlined employee entry and navigation

This functionality is now available in sandbox environments. To turn this feature on, navigate to **System administration > Links > Setup > System parameters > Preview features**. Select **Enhanced worker form and navigation**. This will enable these changes for all users. You can turn this option off at any time.

For more information, see [Streamlined employee entry and navigation](./streamlined-employee-entry.md).
