---
# required metadata

title: Periodic credit management tasks
description: This topic describes period tasks that are a necessary component of managing credit limits for your cutomers. 
author: mikefalkner
manager: AnnBe
ms.date: 09/04/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschloma
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mfalkner
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Periodic credit management tasks

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic describes periodic tasks that are a necessary component of managing credit limits for your cutomers. 

## Update risk scores

As you process invoices, the risk for a customer can change. You must periodically review the criteria for each risk score and update the scores for each customer. You can use the Update risk scores page (**Credit and collections > Periodic tasks > Update risk scores**) to update the following scores:

- **Average payment days** is the average number of days that it takes a customer to pay their invoices. 
- **Customer since** is the number of years that a customer has been a customer of your organization.
- **In business since** is the number of years that a customer has been in business using the **Business start** value on the **Customers** page. 
- **Days sales outstanding** is based on the accounts receivables balance, sales revenue, and number of days for the previous 12 month period.
- **Average balance** is based on the accounts receivables balance for the previous 12 month period.
- **Average balance** is based on the accounts receivables balance for the previous 12 month period.
- **Credit management group**, **Account status** and **Country** used information from the customer. 

In addition, all user defined calculations are processed.

## Update Customer Balance Statistics

You can run the **Update customer balance statistics** process to update the balance statistics calculation that is viewed on the balance statistics inquiry form. This information is used in the calculations for risk scores and the values shown on the credit statistics fact boxes found on the customer form.

You can run this process and set up a periodic batch job using the **Calculate balance statistics** page (**Credit management > Periodic tasks > Calculate balance statistics**).
