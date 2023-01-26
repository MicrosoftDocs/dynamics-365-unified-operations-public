---
# required metadata

title: Prorate employee contributions amount 
description: This article describes how to prorate the employee contributions amount.  
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

# Prorate employee contributions

The employee contribution amounts for Savings and FSA Benefit plans can be prorated based on the number of pay periods available in the benefit period.

To enable proration:

1. The **Benefit period** must have a specified **Start** and **End date**.
2. If, in the **Period configuration**, the previous period is specified, there must be no gap or overlap between the **Benefit periods**.
3. The **Prorate contribution** option in the **Benefit plans configuration** is selected.
4. The pay periods must be defined for the payment frequency specified in the employee profile. The pay periods are defined under **Pay cycle dates** tab in **Payment
frequency** configuration under **Setup**.

The maximum annual contribution amount is prorated in the available pay periods for the employee. The maximum amount allowed per pay period is the maximum annual amount, minus the amount contributed thus far, divided by the remaining pay periods.
