---
# required metadata

title: What's new or changed in Dynamics 365 for Talent (May 6, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 for Talent.
author: Darinkramer
manager: AnnBe
ms.date: 5/6/2019
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
ms.search.validFrom: 2019-05-06
ms.dyn365.ops.version: Talent

---
# "What's new or changed in Dynamics 365 for Talent (May 6, 2019)"

[!include [banner](includes/banner.md)]

This topic describes features that are either new or changed in Dynamics 365 for Talent.

## Changes in Attract

### Select optional documents upon offer creation

Upon offer package template selection, offer creator will be prompted to select the applicable optional documents from that package template. Offer creators will be able to add other optional documents while the offer preparation is in progress. 

## Changes in Onboard
This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Changes in Core HR
Changes described in this section apply to build number 8.1.2282.

### Platform update PU26

For additional details about Platform update 26, see [Preview features in Dynamics 365 for Finance and Operations platform update 26 (May 2019)](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/get-started/whats-new-platform-update-26). 

### Common Data Service entity support for custom fields

In this week's release, the following entities now support custom fields: Benefit calc frequency, Benefit calc rate, Benefit type, Work calendar, Work calendar holiday, Pay cycle and Worker identification types.

### Leave mass enrollment, changing the tier basis to "Seniority date" doesn't refresh the initial accrual rate (318526)

In this release, when you mass enrolling employees and you change the tier bases on the form, the initial accrual will now reflect the tier bases that was selected.  

### Workflow showing duplicate place holders (313636)

Changes have been made in this release to eliminate any duplication of placeholders when workflow notifications are sent.

### Dimension fields are not updated when using "Open in Excel" (176261)

With this releases, you can now update financial dimension using “Open in Excel” option from the Worker form. 

### Worker Address created in CDS is not synced to Talent (317555)

With this change, addresses created in CDS will be updated in Talent Core HR.


## In preview

### New page to validate Position Hierarchy data

HR and administrators can now validate the managerial hierarchy for any circular references that may have inadvertently been imported. This new page can be accessed form Organizational administration>Links>Positions>Position hierarchy validation.

### Allow reason codes to be specified on leave types

Organizations might require additional information about time-off requests. You can now specify reason codes for leave types and let employees select a reason code on their time-off requests.

### Require reason codes for specific leave types on time-off requests

Organizations might require reason codes for specific leave types when employees submit time-off requests. This requirement might exist because of company policy or regulatory requirements. You can now specify which leave types require a reason code, and you can require that employees provide a reason code for the leave type on their time-off requests.

### Provide a leave and absence transaction list for HR

The ability to track employee time off and understand how time off is calculated not only helps Human resources (HR) answer employee questions, but also helps guarantee accurate time-off awards for employees. HR now has a new view into the transactions (grants, accruals, adjustments, and requests), so that HR staff can view the reasons behind balances.

## Coming soon

### Indicate instance type when provisioning Talent

When provisioning a new instance of Talent, you will be able to indicate if the instance type is Production or Sandbox, allowing for early testing of new features.   All existing Talent instances will be updated to the type of Production. If you would like one of your existing instances to be updated to Sandbox please contact CSS and they will initiate the change request.
