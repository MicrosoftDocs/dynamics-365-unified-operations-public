---
# required metadata

title: Prorate employee contribution amounts
description: This article describes how to prorate employee contribution amounts.
author: ramagadu
ms.date: 09/24/2026
ms.topic: how-to
# optional metadata

ms.search.form: HcmJob, HcmPosition, OMOperatingUnit, HcmPersonnelManagementWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: eb5dcacb-a5fe-451d-b30a-7ef14da65d81
ms.search.region: Global
# ms.search.industry: 
ms.author: ramagadu
ms.reviewer: twheeloc
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Human Resources

---

# Prorate employee contribution amounts

[!INCLUDE [banner](../includes/banner.md)]

The employee contribution amounts for Savings and FSA benefit plans can be prorated based on the number of pay periods in the benefit period.

To enable proration, follow these steps:

1. Specify a start date and end date for the benefit period.
2. In the period configuration, if the previous period is specified, make sure that there's no gap or overlap between the benefit periods.
1. In the benefit plans configuration, select the **Prorate contribution** option.
4. Make sure that pay periods are defined for the payment frequency that's specified in the employee profile. Pay periods are defined on the **Pay cycle dates** tab in the **Payment frequency** configuration under **Setup**.

The maximum annual contribution amount is prorated in the available pay periods for the employee. The maximum amount that's allowed per pay period is the maximum annual amount, minus the amount that has been contributed so far, divided by the remaining pay periods.

If the **Enable ongoing benefit contribution changes** feature is turned on and an employee's contribution is changed during the year, the proration rules in this article validate the new contribution amount for plans that prorate contributions. For more information, see [Change HSA and savings plan contributions during the year](hr-benefits-change-contributions.md).
