---
# required metadata

title: Prorate employee contribution amounts
description: This article describes how to prorate employee contribution amounts.
author: twheeloc
ms.date: 01/23/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: HcmJob, HcmPosition, OMOperatingUnit, HcmPersonnelManagementWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.custom: 87933
ms.assetid: eb5dcacb-a5fe-451d-b30a-7ef14da65d81
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Human Resources

---

# Prorate employee contribution amounts

The employee contribution amounts for Savings and FSA benefit plans can be prorated based on the number of pay periods in the benefit period.

To enable proration, follow these steps.

1. Make sure that a start date and end date are specified for the benefit period.
2. In the period configuration, if the previous period is specified, make sure that there's no gap or overlap between the benefit periods.
3. In the benefit plans configuration, make sure that the **Prorate contribution** option is selected.
4. Make sure that pay periods are defined for the payment frequency that's specified in the employee profile. Pay periods are defined on the **Pay cycle dates** tab in the **Payment frequency** configuration under **Setup**.

The maximum annual contribution amount is prorated in the available pay periods for the employee. The maximum amount that's allowed per pay period is the maximum annual amount, minus the amount that has been contributed so far, divided by the remaining pay periods.
