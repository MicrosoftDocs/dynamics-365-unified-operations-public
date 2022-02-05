---
# required metadata

title: Set up payment frequencies
description: Microsoft Dynamics 365 Human Resources uses payment frequencies to calculate the annual benefit salary, determine the benefit premium amount an employee pays each pay period, and how often providers are paid.
author: twheeloc
ms.date: 08/24/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: BenefitWorkspace, HcmBenefitSummaryPart
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Set up payment frequencies


[!INCLUDE [PEAP](../includes/peap-2.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

Microsoft Dynamics 365 Human Resources uses payment frequencies to calculate the annual benefit salary, determine the benefit premium amount an employee pays each pay period, and how often providers are paid.

Benefit payment frequencies use conversion factors to convert benefit payment periods between monthly, semi-monthly, biweekly, weekly, and daily payment frequencies. This allows companies to define the interdependence between the payment frequencies within a benefit plan.

The conversion factors fields identify the conversion factor from the payment frequency to the standard payment periods and allow the system to do calculations between payment frequencies. The conversion factor amount also determines the benefit premium amount that an employee should pay each pay frequency.

1. In the **Benefits management** workspace, under **Setup**, select **Payment frequencies**.

2. Select **New**.

3. Specify values for the following fields:

   | Field | Description |
   | --- | --- |
   | **Payment frequency** | A unique payment frequency name. |
   | **Description** | A description of the payment frequency. |
   | **Period** | The appropriate period that best matches the benefit provider’s and employee’s payment frequency. The period list is composed of the standard payment periods. |
   | **Number of pay periods** | The number of pay periods that represents how often the benefit provider or employees are paid. This amount will be used to calculate the employee‘s annual benefit salary amount. |
   | **Annual conversion factor** | The annual conversion factor for the payment frequency. For example, the annual conversion factor for the monthly pay frequency is: </br></br>(12 monthly payments / 1 year) = 12 |
   | **Semiannual conversion factor** | The semiannual conversion factor for the payment frequency. For example, the semiannual conversion factor for the monthly pay frequency is: </br></br>(12 monthly payments / 2 times a year) = 6 |
   | **Quarterly conversion factor** | The quarterly conversion factor for the payment frequency. For example, the quarterly conversion factor for the monthly pay frequency is: </br></br>(12 monthly payments / 4 quarters) = 3 |
   | **Monthly conversion factor** | The monthly conversion factor for the payment frequency. For example, the monthly conversion factor for the monthly pay frequency is: </br></br>(12 monthly payments / 12 months) = 1 |
   | **Semimonthly conversion factor** | The semimonthly conversion factor for the payment frequency. For example, the semimonthly conversion factor for the monthly pay frequency is: </br></br>(12 monthly payments / 24 (2x a month)) = 0.5 | 
   | **Biweekly conversion factor** | The annual conversion factor for the payment frequency. For example, the annual conversion factor for the monthly pay frequency is: </br></br>(12 monthly payments / 26 weeks) = 0.461538 |
   | **Weekly conversion factor** | The annual conversion factor for the payment frequency. For example, the annual conversion factor for the monthly pay frequency is: </br></br>(12 monthly payments / 52 weeks) = 0.230769 |
   | **Daily conversion factor** | The annual conversion factor for the payment frequency. For example, the annual conversion factor for the monthly pay frequency is: </br></br>(12 monthly payments / 365 days) = 0.032877 |
   | **Hourly conversion factor** | The annual conversion factor for the payment frequency. For example, the annual conversion factor for the monthly pay frequency is: </br></br>(12 monthly payments / 2080 hours) = 0.005769

4. Select **Save**. 


[!INCLUDE[footer-include](../includes/footer-banner.md)]
