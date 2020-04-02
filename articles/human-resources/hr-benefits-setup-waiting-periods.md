---
# required metadata

title: Configure waiting periods
description: In Microsoft Dynamics 365 Human Resources, waiting days establish a milestone to use for benefit plans. 
author: andreabichsel
manager: AnnBe
ms.date: 04/01/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-human-resources
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Configure waiting periods

[!include [banner](includes/preview-feature.md)]

In Microsoft Dynamics 365 Human Resources, waiting days establish a milestone to use for benefit plans. For example, three months from hire date, the first of each month, or six months.   

1. In the **Benefits management** workspace, under **Setup**, select **Waiting periods**.

2. Select **New**.

3. Specify values for the following fields:

   | Field | Description |
   | --- | --- |
   | **Waiting code** | A unique identifier for the waiting period. |
   | **Description** | A description of the waiting period. |
   | **Waiting method** | Select the appropriate waiting method from the drop-down list of values. Options are Net, Current month, Current quarter, Current year, and Current week. |
   | **Months** | Enter the number of months to add to the waiting method to calculate the waiting date. |
   | **Days** | Enter the number of days to add to the waiting method to calculate the waiting date. |
   | **Waiting day** | Select the waiting day to use to calculate the waiting date. |

4. Select **Save**.
