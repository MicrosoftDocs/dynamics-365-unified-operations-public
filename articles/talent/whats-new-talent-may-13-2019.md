---
# required metadata

title: What's new or changed in Dynamics 365 for Talent (May 13, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 for Talent.
author: Darinkramer
manager: AnnBe
ms.date: 5/13/2019
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
ms.search.validFrom: 2019-05-13
ms.dyn365.ops.version: Talent

---
# "What's new or changed in Dynamics 365 for Talent (May 13, 2019)"

[!include [banner](includes/banner.md)]

This topic describes features that are either new or changed in Dynamics 365 for Talent.

## Coming soon in Attract

### Job approvals on home page

Approvals will appear in an Approvals section on the dashboard. Approvers will see a section called 'Assigned to you' which will include the job ID, title, other approvers, and date assigned. Those that have submitted a job for approval will be able to see a section called 'Requested by you' which will show which individuals still need to approve the job that was submitted.

## Changes in Onboard

This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Changes in Core HR

Changes described in this section apply to build number 8.1.2297.

### Indicate instance type when provisioning Talent

When provisioning a new instance of Talent, you will be able to indicate whether the instance type is **Production** or **Sandbox**, allowing for early testing of new features. All existing Talent instances will be updated to the Production instance type. If you want one of your existing instances to be updated to the Sandbox instance type, please contact Support to initiate the change request.

### Common Data Service entity support for custom fields

In this week's release, the following CDS entities now support custom fields: Employment, Benefit calc frequency, Benefit calc rate, Work calendar holiday and Identification type.

### Common Data Service integration page

With this release a new option is availble in **System Administration > Links > Integrations > Common Data Service configuration**. The Common Data Service configuration is a form that allows an administrator or data management administrator some flexibility and insights with the Common Data Service (CDS). The form allows to do things like enable/disable the CDS integration with the Talent instance and allows the administrator to see the sync details between the Talent instance and the CDS.

### Importing performance data with final employee rating (316710)

In this release you are now able to import historical employee rating data. The FinalEmployeeRatingId field will now allow writes.

### Worker Address cannot be created in CDS and synced to Talent (317555)

This change now allows for address data which has been created in CDS to sync to Talent.

## In preview

### New page to validate position hierarchy data

Human resources (HR) and administrators can now validate the managerial hierarchy for any circular references that might have inadvertently been imported. You can access this new page from **Organizational administration > Links > Positions > Position hierarchy validation**.

### Specify reason codes on leave types

Organizations might require additional information about time-off requests. You can now specify reason codes for leave types and let employees select a reason code on their time-off requests.

### Require reason codes for specific leave types on time-off requests

Organizations might require reason codes for specific leave types when employees submit time-off requests. This requirement might exist because of company policy or regulatory requirements. You can now specify which leave types require a reason code, and you can require that employees provide a reason code for the leave type on their time-off requests.

### Provide a leave and absence transaction list for HR

The ability to track employee time off and understand how time off is calculated not only helps HR answer employee questions, but also helps ensure accurate time-off awards for employees. HR now has a new view into the transactions (grants, accruals, adjustments, and requests), so that HR staff can view the reasons behind balances.
