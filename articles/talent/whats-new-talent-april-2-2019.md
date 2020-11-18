---
# required metadata

title: What's new or changed in Dynamics 365 Talent (April 2, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent.
author: Darinkramer
manager: AnnBe
ms.date: 04/02/2019
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
ms.search.validFrom: 2019-04-02
ms.dyn365.ops.version: Talent

---
# What's new or changed in Dynamics 365 Talent (April 2, 2019)

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

This topic describes features that are either new or changed in Dynamics 365 Talent.

## Changes in Attract

### Approval emails in Attract
New approval emails improve visibility into the approval process. Emails are sent to approvers when one of the following scenarios occur:

- A requestor submits a job for approval.
- A job is either rejected or approved.
- An approver hasn't acted on an approval request within 24 hours.

You can customize the content of approval emails with new templates.

### Application and profile attachments
Improvements to the **Documents** tab on applications and talent pool profiles now display both the document name and the type.

## Changes in Onboard
This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Coming soon (Attract and Onboard)

### Lifecycle Services (LCS) integration with report a problem
In Attract and Onboard, problems logged by end users through the report a problem feature now automatically create support issues in the customer's LCS project. Admins can then triage the issues and submit them to Microsoft when needed. This is consistent with how Core HR handles end user support issues.

## Changes in Core HR
Changes described in this section apply to build number 8.1.2216.

### Platform update 25 for Finance and Operations
For more information about Platform update 25 for Finance and Operations, see [Preview features in Dynamics 365 for Finance and Operations platform update 25 (April 2019)](https://docs.microsoft.com/dynamics365/unified-operations/fin-and-ops/get-started/whats-new-platform-25).

###  Advanced compensation security (fixed and variable)
In many organizations, compensation and benefits managers might only have access to certain compensation records. These might include records for executives or regional employees. This change allows HR to manage and maintain compensation plans for different employee groups in the organization. You can assign security roles to fixed and variable plans. These security roles determine access to plans and related employee data, such as salary or bonus records, so that only those roles can process compensation for the employee groups.

### Upgrade to Common Data Service
Deadlines to upgrade to Common Data Service are rapidly approaching. Sign in to the Microsoft Power Apps Admin center to determine if your database needs to be upgraded. For more information about deadlines and necessary steps to upgrade, see [Upgrade to Common Data Service](https://docs.microsoft.com/common-data-service/upgradecds/introduction-upgrade-cds).

## In preview

### Allow reason codes to be specified on leave types
Organizations might need additional information about time-off requests. You can now specify reason codes for leave types and enable employees to select a reason code on their time-off requests.

### Require reason codes for certain leave types on time-off requests
Organizations might require reason codes for specific leave types when employees submit time-off. This might be due to company policy or regulatory requirements. You can now specify which leave types require a reason code, and you can require employees to provide a reason code for the leave type on their time-off requests.

## Coming soon

### Improvements to the user interface for duplicate employee check
With this change, duplicates are detected as you enter name fields, and a status displays the number of duplicates found. You can select the provided link to open a new page to evaluate whether to use the detected match. To avoid interrupting data entry, the duplicates form doesn't automatically open.

###  Email support for alerts
With Platform update 25 for Finance and Operations, users can create alert rules that automatically send email notifications to contacts when triggered by an event. 
