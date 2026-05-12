---
title: Fixed asset repair statement for Lithuania
description: Learn how to submit repair information for a fixed asset and generate a fixed asset repair report. Repair information must be stored for all fixed assets.
author: EvgenyPopovMBS
ms.author: evgenypopov
ms.topic: concept-article
ms.custom: 
  - bap-template
ms.date: 05/04/2026
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Lithuania
ms.search.validFrom: 2016-11-30
ms.search.form: 
ms.dyn365.ops.version: Version 1611
---

# Fixed asset repair statement for Lithuania

[!include [banner](../../includes/banner.md)]

This article explains how to submit repair information for a fixed asset and generate a fixed asset repair report. You must store repair information for all fixed assets.

## Enter details for a fixed asset repair statement

Enter repair information for the fixed asset on the **Repair fixed assets** page. Provide the following information about the repair.

| Field                   | Value                               |
|-----------------------------|------------------------------------------|
| **Date of repair**          | Date on which you repaired the fixed asset.                        |
| **Description**             | Description of the repair.               |
| **Amount spent for repair** | Cost of the repair. **NOTE:** To calculate the total amount, select the **Totals** button, and then specify the period of calculation. |
| **Document number**         | Number that you assign to the document that you generated for the repair.                                                            |

## Generate the fixed asset repair report

To generate the report, go to **Fixed assets** > **Inquires and Reports** > **Transaction reports** > **Fixed assets repair**, and then specify the following values.

| Field                     | Value                 |
|---------------------------|-----------------------|
| **Book**                      | Select the book for which to generate the fixed asset report.                                                                                                                                                                                                                                                    |
| **From date, To date**        | Enter the start and end dates for the reporting period.                                                                                                                                                                                                                                                          |
| **Show report transactions**  | Select this field to include repair transactions on the report.                                                                                                                                                                                                                                                  |
| **Document number**           | Specify the number that is assigned to the document that was generated for the repair.                                                                                                                                                                                                                           |
| **Print from repair percent** | Enter the percentage of the fixed asset’s acquisition value that can be spent on repairs before the fixed asset must be included on the report. The report includes only those fixed assets for which the ratio of repair costs to acquisition value is higher than the percentage that you enter in this field. |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
