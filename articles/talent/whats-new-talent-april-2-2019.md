---
# required metadata

title: What's new or changed in Dynamics 365 for Talent (April 2, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 for Talent.
author: Darinkramer
manager: AnnBe
ms.date: 4/2/2019
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
ms.search.validFrom: 2019-04-02
ms.dyn365.ops.version: Talent

---
# "What's new or changed in Dynamics 365 for Talent (April 2, 2019)"

[!include [banner](includes/banner.md)]

This topic describes features that are either new or changed in Dynamics 365 for Talent.

## Changes in Attract

### Approval emails in Attract
Visibility into the approval process has been improved with the introduction of approval email functionality. Emails will be sent to the approvers when a requester submits the job for approval, when the job is either rejected or approved, or if an approver has not acted upon the approval request within 24 hours. The approval email content can be customized with the introduction of approval email templates.

### Application and profile attachments
We have reworked the Documents tab on applications and talent pool profiles to show both the document name as well as the type.

## Changes in Onboard
This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Coming soon (Attract and Onboard)

### LCS (Life cycle services) report a problem integration
Report a problem issues logged by end users in Attract and Onboard will automatically create Support Issues in the corresponding customer’s LCS project.  Customer admins will then be able to triage those issues and submit them to Microsoft if applicable.  This is consistent with how end user support issues are logged in Core HR.  

## Changes in Core HR
Changes described in this section apply to build number 8.1.2216.

### Platform 25 Update
For more information about Platform update 25 click [HERE:](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/get-started/whats-new-platform-25)

###  Advanced compensation security (fixed and variable)
In many organizations, the compensation and benefits managers might only have access to certain compensation records. These could be for executives or regional employees. With this change, HR can manage and maintain the compensation plans for different employee groups in the organization. You can assign security roles to fixed and variable plans that determine access to the plans and the employee data related to the plans, such as salary or bonus records. Only the roles with the access granted can process compensation for those employees.

### Upgrade to CDS for Apps
Deadlines to upgrade to CDS for Apps are quickly approaching.   Log into the PowerApps Admin center to determine if your database needs to be upgraded. Click [HERE](https://docs.microsoft.com/en-us/common-data-service/upgradecds/introduction-upgrade-cds) for more information on deadlines and necessary steps to upgrade.

## In preview

### Allow reason codes to be specified on leave types
Organizations may need additional information related to time off requests. To get this information, employees need to include a reason code on their time off requests. With this release you can now specify the reason codes associated with a given leave type and enable employees to select a reason code on their time off requests.

### Configure reason codes to be required when submitting time off for certain leave types
Organizations may require reason codes to be set on specific leave types when employees submit time off. This may be required based on a regulatory requirement in their country or a company policy. This release provides the ability for HR to specify which leave types require a reason code and this will be enforced when employees submit time off requests where the leave requires a reason code.

## Coming soon

### Duplicate employee check: Interface changes
With this change, duplicates are detected as you enter name fields, and a status displays the number of duplicates found. You can select the provided link to open a new page to evaluate whether to use the detected match. The duplicates form doesn't automatically open, to avoid interrupting data entry.

###  Email support for alerts
With Platform update 25, users can create alert rules that automatically dispatch email notifications to contacts when triggered by an event. 
