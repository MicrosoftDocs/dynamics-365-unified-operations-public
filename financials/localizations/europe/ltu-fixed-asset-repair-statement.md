---
# required metadata

title: Fixed asset repair statement for Lithuania | Microsoft Docs
description: This topic explains how to submit repair information for a fixed asset and generate a fixed asset repair report. Repair information must be stored for all fixed assets. 
author: ShylaThompson
manager: AnnBe
ms.date: 2016-12-12 22:45:40
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: 81
ms.suite: Released- Dynamics 365 for Operations version 1611
# ms.tgt_pltfrm: 
ms.custom: 262724
ms.assetid: 26de01d2-2570-48b2-9f31-79f55437cd28
ms.region: Lithuania
# ms.industry: 
ms.author: epopov

---

# Fixed asset repair statement for Lithuania

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

 

