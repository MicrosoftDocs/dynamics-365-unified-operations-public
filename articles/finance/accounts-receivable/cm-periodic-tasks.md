---
# required metadata

title: Periodic credit management tasks
description: This topic describes the periodic tasks that are a necessary part of the process of managing credit limits for customers. 
author: JodiChristiansen
ms.date: 09/04/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschloma
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: roschlom
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Periodic credit management tasks

[!include [banner](../includes/banner.md)]

This topic describes the periodic tasks that are a necessary part of the process of managing credit limits for customers.

## Update risk scores

As businesses evolve and circumstances change, the credit risks for a given customer can also change. To help maintain appropriate credit limits for your customers, you must periodically review the criteria for each risk score and update the scores for each customer. You can update the following scores by using the **Update risk scores** page (**Credit and collections \> Periodic tasks \> Credit management \> Update risk scores**). All user-defined calculations are also processed.

- **Average payment days** – This score is the average number of days that a customer takes to pay invoices.
- **Customer since** – This score is the number of years that a customer has been a customer of your organization.
- **In business since** – This score is the number of years that a customer has been in business. It uses the value of the **Business start** field on the **Customers** page.
- **Days sales outstanding** – This score is based on the accounts receivable balance, sales revenue, and number of days for the previous 12-month period.
- **Average balance** – This score is based on the accounts receivable balance for the previous 12-month period.
- **Credit management group**, **Account status**, and **Country** – These scores use information from the customer.

## Update customer balance statistics

You can run the **Update customer balance statistics** process to update the calculation of balance statistics that is shown on the **Balance statistics inquiry** page. This information is used to calculate risk scores and the values that are shown in the credit statistics FactBoxes on the **Customer** page.

When you run the process, it updates customer balance statistics for a single customer. To set up a batch job to run the process for multiple customers, you can use the **Calculate balance statistics** page (**Credit management \> Periodic tasks \> Calculate balance statistics**).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
