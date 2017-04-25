---
# required metadata

title: Split periods in periodic journals
description: Periodic journals are sometimes called recurring journals because the amount, text, and other information are repeated each time that the journal is posted. When you create the journal, you specify the period interval for the recurrence, such as days or months. You also specify the number of periods for which the journal will be posted.
author: ShylaThompson
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 81
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 261354
ms.assetid: 76c0d7bf-f795-4d42-9a86-a9f36989962c
ms.search.region: Czech Republic, Estonia, Hungary, Latvia, Lithuania, Poland
# ms.search.industry: 
ms.author: v-elgolu
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Split periods in periodic journals

[!include[banner](../includes/banner.md)]


Periodic journals are sometimes called recurring journals because the amount, text, and other information are repeated each time that the journal is posted. When you create the journal, you specify the period interval for the recurrence, such as days or months. You also specify the number of periods for which the journal will be posted.

To repeatedly retrieve and post transaction lines, you can use the **Periodic journals** page. For legal entities in Czech Republic, Estonia, Hungary, Latvia, Lithuania, Poland, and Russia, the **Periodic journals** page is extended by the split for periods functionality. <!---For more information, see [Create and process a periodic journal](http://ax.help.dynamics.com/en/wiki/create-and-process-a-periodic-journal/).-->

### Example: Split for periods in periodic journals

An insurance company offers your organization a discount for prepaying the insurance policy for an entire year. The payment is posted to an asset account such as prepaid insurance. You then amortize your monthly insurance expense throughout the year by creating a periodic journal that contains a credit to the prepaid insurance account and a debit to an insurance expense account. In this case, you can use the split for periods functionality. Click the **Split for periods** button on the Action Pane on the **Periodic journal** **lines** page, and then specify the following fields.

|                       |                                                                                                                                                                                                             |
|-----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Field**             | **Description**                                                                                                                                                                                             |
| **Start date**        | Select the date for the first periodic journal line.                                                                                                                                                        |
| **Number of periods** | Enter the number of periods across which to split the journal line. This value determines how many new transactions are generated. The transaction amount is distributed evenly among the new transactions. |
| **Unit**              | Select the unit of measure for the period.                                                                                                                                                                  |
| **Period interval**   | Determine an interval between posting periods.                                                                                                                                                              |

For example, to generate quarterly postings, enter **4** in the **Number of periods** field, select **Months** in the **Unit** field, and enter **3** in the **Period interval** field. The system generates four journal lines, each for one fourth of the journal line amount that you entered, at 3-month intervals. Similar functionality is also available for the general journal. When viewing general journal lines, select **Period journal** &gt; **Save journal**.



