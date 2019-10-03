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

This topic describes period tasks that are a necessary component of managing credit limits for your cutomers. As you process invoices, the risk for a customer can change. You must periodically review the criteria for each risk score and update the scores for each customer. You can use the Update risk scores page (**Credit and collections > Periodic tasks > Update risk scores**) to update the following scores.

### Payment days

The Payment days criteria is one of the scoring group criteria that must be calculated periodically. The process calculates the number of days that it takes a customer to pay their invoices. This value is then used in the scoring group to calculate a score for this criteria for each customer.

### Years in business

Years in business is one of the scoring group criteria that must be calculated periodically. The process calculates the number of years that a customer has been in business using the **Business start** value on the **Customers** page. This value is then used in the scoring group to calculate a score for this criteria for each customer.

### Customer since

The value on the **Customer since** field is one of the scoring group criteria that must be calculated periodically. The process calculates the number of years that a customer has been your organization's customer using the **Customer since** value in the 
**Customers** page. This value is then used in the scoring group to calculate a score for this criteria for each customer.

### Update Customer Balance Statistics

You can run the **Update customer balance statistics** process to update the balance statistics calculation that viewed on the balance statistics inquiry form. You can run this process and set up a periodic batch job using the **Calculate balance statistics** page (**Credit management > Periodic tasks > Calculate balance statistics**.
