---
title: Statistics on payment practices report
description: Learn how to generate the Statistics on payment practices report for the United Kingdom in Microsoft Dynamics 365 Finance.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 12/18/2025
ms.reviewer: johnmichalak
ms.search.region: United Kingdom
ms.search.validFrom: 2020-12-02
---

# Statistics on payment practices report

[!include [banner](../../includes/banner.md)]

This article explains how to generate the Statistics on payment practices report for the United Kingdom in Microsoft Dynamics 365 Finance.

In the scope of reporting requirements, businesses in the United Kingdom (UK) must prepare and publish, for each reporting period in the financial year, information about their payment practices and performance as they relate to qualifying contracts. The information for each reporting period must reflect the policies and practices that the business applied during that period, and the business's performance for that period.

The business must publish the report on a web-based service that the government provides or that the government authorizes. The business must publish the report within 30 days of the end of the reporting period.

> [!NOTE]
> Starting in 2025, under the Reporting on Payment Practices and Performance (Amendment) Regulations 2024, which the UK Secretary of State issued under powers in the Small Business, Enterprise and Employment Act 2015, companies in scope are required to report both the total number of payments made in the reporting period and the percentage of payments made late due to disputes.
> This requirement is supported in the following versions of Dynamics 365 Finance:
> 
> - 10.0.46 and higher
> - 10.0.45 from build 10.0.2345.106
> - 10.0.44 from build 10.0.2263.170
> - 10.0.43 from build 	10.0.2177.213
>
> The regulatory update also requires the following or higher versions of ER configurations:
> - Statistics on invoices – version 67
> - Statistics on invoices model mapping – version 67.44
> - Statistics on payment practices (UK) – version 67.18
>
> For more information about importing ER configurations, see [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

## Report format

In the scope of the report, you find narrative descriptions of reporting practices. The report also contains the following three statistics:

- During the reporting period, the average number of days that passed between the date when invoices were received and the date when payments were made (in other words, the average number of days that was taken to make payments).
- Of the payments that you made during the reporting period, the percentage that were made in 30 days or less, in 31 to 60 days, and in 61 days or more.
- Of the payments that were due during the reporting period, the percentage that weren't paid according to the agreed-on terms.

In Dynamics 365 Finance, you export the Statistics on payment practices report to Microsoft Excel and it has two tabs:

- **Payments\_made** – This tab contains the first two types of statistics from the previous list. It contains the details per vendor account. The detailed view also contains details of each payment made during a reporting period.
- **Payments\_due** – This tab contains the third type of statistics from the previous list. It contains the details per vendor account. The detailed view also contains details of each invoice that was due during a reporting period.

## Set up Statistics on payment practices report in Dynamics 365 Finance

In Finance, import the following ER configurations from the Global repository.

| ER configuration name                | Configuration type |
|--------------------------------------|--------------------|
| Statistics on invoices               | Model              |
| Statistics on invoices model mapping | Model mapping      |
| Statistics on payment practices (UK) | Format (exporting) |

For more information about importing ER configurations, see [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

Import the most recent versions of the configurations. The version description usually includes the number of the Microsoft Knowledge Base (KB) article that explains the changes that were introduced in the configuration version.

> [!NOTE]
> After you import all the ER configurations from the preceding table, set the **Default for model mapping** option to **Yes** for the **Statistics on invoices model mapping** configuration.

## Post documents and define the date when you receive the invoice

Before you generate the report, post and settle the appropriate invoices and payments. You can't export payments that aren't settled to the **Payments\_made** tab, because there's no information about the invoices that the payments are intended to pay. Additionally, the number of days that it takes to make payments can't be calculated.

You can specify the date when you receive the purchase invoice and then use this date to calculate the number of days that it takes to make payments. Set the **Receive document date** field in the following places:

- When you create and post the new vendor invoice, set the **Receive document date** field in the **Invoice dates** section on the **Vendor invoice header** tab of the **Vendor invoice** page. By default, the value of the **Invoice date** field is used.
- When you create the vendor invoice journal line, you can set the **Receive document date** field on the **General** tab.
- After the vendor invoice is posted but before it's fully settled, you can also set the **Receive document date** field on the **General** tab of the **Vendor transactions** page.

## Define payments made late due to disputes

To define payments made late due to disputes in Dynamics 365 Finance, use the [Financial tags](../../general-ledger/financial-tag.md). 

Set up **Financial tags segment delimiter** in **General ledger parameters** and create and activate new **Financial tag** that you use to mark transactions related to payments made late due to disputes.

Use the created **Financial tag** for payments made late due to disputes.

## Generate the report

To generate the report, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts payable** \> **Inquiries and reports** \> **Statistics** \> **Report on payment deadlines**.
1. In the **Report on payment deadlines** dialog, in the **Format mapping** field, select **Statistics on payment practices (UK)**.
1. In the **Electronic report parameters** dialog, set the following fields.

    | Field                         | Description |
    |-------------------------------|-------------|
    | **Date criteria**             | Select one of the following options: **Invoice accounting date**, **Invoice date**, or **Invoice receive date**. Depending on the option that you select, the number of days that was taken to make payments is calculated by using the payment date and the corresponding type of date that you select in the dialog: **Transaction date**, **Invoice date**, or **Receive document date**. |
    | **From date** and **To date** | Specify the start and end dates of the reporting period. |
    | **Vendor posting profile**    | To generate a report for only a specific vendor profile, select the profile. |
    | **Print document details**    | Set the option to **Yes** to export details of invoice and payment documents to the report. |
    | **Financial tag**             | Select the **Financial tag** that is used for payments made late due to disputes. |

1. Select **OK** to generate the report.
1. Review the report: **Payments made** tab and **Payments due** tab.

   > [!NOTE]
   > This tab contains all invoices that are either due, paid before the due date, and overdue. Only overdue invoices are visible by default. Excel rows with invoices paid before the due date are hidden. To view all invoices, unhide the Excel rows.

## Publish the reporting about payment practices

After you generate the Statistics on payment practices (UK) report in Excel, use the report data to prepare the final report about payment practices for publication.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
