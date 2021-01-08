---
# required metadata

title: What's new or changed in Dynamics 365 Talent (May 6, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent.
author: Darinkramer
manager: AnnBe
ms.date: 05/06/2019
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
# ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2019-05-06
ms.dyn365.ops.version: Talent

---
# What's new or changed in Dynamics 365 Talent (May 6, 2019)

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

This topic describes features that are either new or changed in Dynamics 365 Talent.

## Changes in Attract

### Select optional documents upon offer creation

When you select an offer package template, Attract now prompts you to select the applicable, optional documents from that package template. You can add other optional documents while preparing the offer.

## Changes in Onboard

This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Changes in Core HR

Changes described in this section apply to build number 8.1.2282. The numbers in parentheses in some headings refer to support numbers in Microsoft Dynamics Lifecycle Services (LCS).

### Platform update 26 for Finance and Operations

For additional details about Platform update 26 for Finance and Operations, see [Preview features in Dynamics 365 Finance and Operations platform update 26 (May 2019)](https://docs.microsoft.com/dynamics365/unified-operations/fin-and-ops/get-started/whats-new-platform-update-26). 

### Common Data Service entity support for custom fields

In this week's release, the following entities now support custom fields: Benefit calc frequency, Benefit calc rate, Benefit type, Work calendar, Work calendar holiday, Pay cycle, and Worker identification types.

### Leave mass enrollment, changing the tier basis to "Seniority date" doesn't refresh the initial accrual rate (318526)

When you mass enroll employees and change the tier basis, the initial accrual now reflects the tier basis that you selected.

### Workflow showing duplicate place holders (313636)

Changes in this release eliminate duplication of placeholders when workflow notifications are sent.

### Dimension fields aren't updated when using "Open in Excel" (176261)

With this release, you can now update financial dimension using **Open in Excel** from the **Worker** page. 

### Worker address created in Common Data Service isn't synced to Talent (317555)

With this change, addresses created in Common Data Service are updated in Talent: Core HR.


## In preview

### New page to validate position hierarchy data

Human resources (HR) and administrators can now validate the managerial hierarchy for any circular references that might have inadvertently been imported. You can access this new page from **Organizational administration > Links > Positions > Position hierarchy validation**.

### Specify reason codes on leave types

Organizations might require additional information about time-off requests. You can now specify reason codes for leave types and let employees select a reason code on their time-off requests.

### Require reason codes for specific leave types on time-off requests

Organizations might require reason codes for specific leave types when employees submit time-off requests. This requirement might exist because of company policy or regulatory requirements. You can now specify which leave types require a reason code, and you can require that employees provide a reason code for the leave type on their time-off requests.

### Provide a leave and absence transaction list for HR

The ability to track employee time off and understand how time off is calculated not only helps HR answer employee questions, but also helps ensure accurate time-off awards for employees. HR now has a new view into the transactions (grants, accruals, adjustments, and requests), so that HR staff can view the reasons behind balances.

## Coming soon

### Indicate instance type when provisioning Talent

When provisioning a new instance of Talent, you will be able to indicate whether the instance type is **Production** or **Sandbox**, allowing for early testing of new features. All existing Talent instances will be updated to the Production instance type. If you want one of your existing instances to be updated to the Sandbox instance type, please contact Support to initiate the change request.
