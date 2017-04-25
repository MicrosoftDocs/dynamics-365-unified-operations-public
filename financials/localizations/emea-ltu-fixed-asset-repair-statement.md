---
# required metadata

title: Fixed asset repair statement for Lithuania
description: This topic explains how to submit repair information for a fixed asset and generate a fixed asset repair report. Repair information must be stored for all fixed assets. 
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
ms.custom: 262724
ms.assetid: 59259905-5dc3-4e15-9a04-ab38bb58a37b
ms.search.region: Lithuania
# ms.search.industry: 
ms.author: epopov
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Fixed asset repair statement for Lithuania

[!include[banner](../includes/banner.md)]


This topic explains how to submit repair information for a fixed asset and generate a fixed asset repair report. Repair information must be stored for all fixed assets. 

Enter details for a fixed asset repair statement
------------------------------------------------

You can enter repair information for the fixed asset on the **Repair fixed assets** page. Provide the following information about the repair.

|                             |                                                                                                                                       |
|-----------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
| **Field**                   | **Value**                                                                                                                             |
| **Date of repair**          | Date on which the fixed asset was repaired.                                                                                           |
| **Description**             | Description of the repair.                                                                                                            |
| **Amount spent for repair** | Cost of the repair. **Note:** To calculate the total amount, click the **Totals** button, and then specify the period of calculation. |
| **Document number**         | Number that is assigned to the document that was generated for the repair.                                                            |

 

## Generate the fixed asset repair report
To generate the report, go to **Fixed assets** **&gt; Inquires and** **Reports** &gt; **Transaction reports** &gt; **Fixed assets repair**, and then specify the following values.

|                               |                                                                                                                                                                                                                                                                                                                  |
|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Field**                     | **Value**                                                                                                                                                                                                                                                                                                        |
| **Book**                      | Select the book for which to generate the fixed asset report.                                                                                                                                                                                                                                                    |
| **From date, To date**        | Enter the start and end dates for the reporting period.                                                                                                                                                                                                                                                          |
| **Show report transactions**  | Select this field to include repair transactions on the report.                                                                                                                                                                                                                                                  |
| **Document number**           | Specify the number that is assigned to the document that was generated for the repair.                                                                                                                                                                                                                           |
| **Print from repair percent** | Enter the percentage of the fixed asset’s acquisition value that can be spent on repairs before the fixed asset must be included on the report. The report includes only those fixed assets for which the ratio of repair costs to acquisition value is higher than the percentage that you enter in this field. |

 



