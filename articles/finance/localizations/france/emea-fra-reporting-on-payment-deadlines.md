---
title: Reporting on payment deadlines for customer and vendor invoices for France using Microsoft Dynamics 365 Finance.
description: Learn how to configure and generate reports on payment deadlines for customer and vendor invoices for legal entities in France using Microsoft Dynamics 365 Finance.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.date: 07/01/2025
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
ms.search.region: France
---

# Reporting on payment deadlines for customer and vendor invoices for France

[!include [banner](../../includes/banner.md)]

This article explains how to configure and generate reports on payment deadlines for customer and vendor invoices for legal entities in France using Microsoft Dynamics 365 Finance.

In France, legal entities are required to report on payment practices as part of their annual management report, in accordance with the French Commercial Code. 
This regulation aims to increase transparency and reduce late payments in commercial transactions. 
Companies must disclose the number and total value of invoices paid late, both to suppliers and by customers, and provide a breakdown by delay intervals. 

In Dynamics 365 Finance users can generate the following reports in Excel format.

- Invoices received with late payment during the financial year.
- Invoices received which have not been paid by the closing date of the financial year in which the term expired.
- Invoices issued with late payment during the financial year.
- Invoices issued which have not been paid by the closing date of the financial year in which the term expired.

## Prepare your environment to report on payment deadlines for customer and vendor invoices for France

To use the **Reporting on payment deadlines for customer and vendor invoices** for France in Dynamics 365 Finance, you need to import the following Electronic reporting (ER) configurations.

| ER configuration name                                       | Configuration type | Description |
|-------------------------------------------------------------|--------------------|-------------|
| Statistics on invoices                                      | Model              | Common reporting model designed to provide a view of payment practices, particularly in relation to late payments and outstanding invoices. |
| Statistics on invoices model mapping                        | Model mapping      | This model mapping defines how data sources within Microsoft Dynamics 365 Finance are connected to the reporting model used for analyzing payment practices.|
| AP Invoices delayed in payment | Format (exporting) | Invoices received with late payment during the financial year. |
| AP Overdue invoices | Format (exporting) | Invoices received which have not been paid by the closing date of the financial year in which the term expired.|
| AR Invoices delayed in payment | Format (exporting) | Invoices issued with late payment during the financial year.|
| AR Overdue invoices | Format (exporting) | Invoices issued which have not been paid by the closing date of the financial year in which the term expired. |

Learn more about how to import ER configurations in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

Import the most recent versions of the configurations. The version description usually includes the number of the Knowledge Base (KB) article that explains the changes that were introduced in the configuration version.

> [!NOTE]
> After you import all the ER configurations from the preceding table, set the **Default for model mapping** option to **Yes** for the **Statistics on invoices model mapping** configuration.

## Generate the report

To generate the report, follow these steps.

1. Go to **General ledger** > **Inquiries and reports** > **Statistics** > **Statistics on invoices report**.
1. In the **Statistics on invoices** dialog box, in the **Format mapping** field, select one of the ER formats.
  
    - AP Invoices delayed in payment
    - AR Overdue invoices
    - AR Invoices delayed in payment
    - AR Overdue invoices
1. In the **Electronic report parameters** dialog box, set the following fields.

    | Field                         | Description |
    |-------------------------------|-------------|
    | **From date** and **To date** | Specify the start and end dates of the reporting period. |
    | **Vendor posting profile** or  **Customer posting profile**  | To generate a report for only a specific vendor or customer profile, select the profile. |
    | **Print document details**    | Set the option to **Yes** to export details of invoice and payment documents to the report. |

5. Select **OK** to generate the report.
6. On the **Run in the background** FastTab, use the **Batch processing** checkbox to specify the mode that report generation runs in:

    - To run report generation in a batch, select the **Batch processing** checkbox. Then specify the batch parameters.
    - To run report generation in interactive mode, clear the **Batch processing** checkbox. 
