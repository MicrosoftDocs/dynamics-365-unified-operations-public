---
# required metadata

title: Calculate tax interest and free-hand interest
description: This topic walks you through calculating tax interest for Poland.
author: ShylaThompson
manager: AnnBe
ms.date: 03/02/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom
ms.search.region: Poland
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1

---

# Poland

[!include[banner](../includes/banner.md)]

In Poland, the tax interest rates are determined by the Ministry of Finance. The vendor calculates the interest if the payment settlement is made after the due date. If the payment period is shorter than 30 days, the vendor can calculate the tax interest from the due date through the payment date. Free-hand interest rates apply when payments are settled between the 31st day after the posting and the due date. 

1. Click Accounts receivable > Periodic > Collections > Interest calculation. 
2. Select the Invoice check box to calculate interest on invoices. 
3. Select the Credit note check box to deduct customer credit notes before the interest calculation. 
4. Select the Payment check box to deduct customer payments before interest calculation. 
5. Select the Interest check box to calculate compound interest on previous interest notes. 
6. In the From date field, select the starting date. The interest calculation will include transactions that are due on or after this date. 
7. In the To date field, select the ending date for the interest calculation. 
8. In the Round-off field, enter the units to round off the interest amount. 
9. In the Use posting profile from field, select the posting profile from the following options: 
  - Account – Use the posting profile from the relevant customer account for each interest note. 
  - Select – Indicate a posting profile in the Posting profile field. 
10. In the Posting profile field, select the customer posting profile for the calculation. 
11. Select the Tax interest check box to calculate the free-hand interest and tax interest. 
12. Click Select to open the Interest job form. 
13. Select the criteria to calculate interest and click OK. 
14. In the Interest calculation form, click OK to calculate the tax interest and free-hand interest and create the interest notes for the customer accounts. 
