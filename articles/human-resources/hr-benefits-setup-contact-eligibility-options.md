---
# required metadata

title: Configure personal contact eligibility options
description: Configure eligibility options for personal contacts in Microsoft Dynamics 365 Human Resources. Personal contacts can be beneficiaries or dependents.
author: andreabichsel
manager: AnnBe
ms.date: 02/03/2020
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

# Configure personal contact eligibility options

[!include [banner](includes/preview-feature.md)]

This article shows you how to configure types of personal contacts to use in benefits in Microsoft Dynamics 365 Human Resources. Personal contacts can be beneficiaries or dependents. 

1. In the **Benefits management** workspace, under **Setup**, select **Personal contact eligibility options**.

2. Select **New**.

3. Specify values for the following fields:

   | Field | Description |
   | --- | --- |
   | **Eligibility option** | A unique eligibility option name or code to identify the eligibility option. |
   | **Description** | A brief description of the eligibility option. |
   | **Contact eligibility code** | The system code that best describes the personal eligibility option. You can choose from: <ul><li>Relationship</li><li>Student</li><li>Overage dependent</li><li>Over-aged disabled dependent</li></ul> |
   | **Status** | The status of the eligibility option. If the status for an eligibility option is set to inactive, then you can’t select that personal contact eligibility option for personal contacts. |
   | **Relationship** | Specifies the relationship between the personal contact and the employee. This field is only active if the contact eligibility code is set to Relationship. |
   | **Age** | The maximum age of an eligible personal contact for the benefit plan. This field is only active if you select a relationship. This age is compared with the calculated age of the personal contact. Calculated age is: (Coverage date – personal contact birth date / 365). This number is always an integer. |

4. Select **Save**. 
