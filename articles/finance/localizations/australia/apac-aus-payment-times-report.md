---
title: Payment times reporting schema
description: Learn how to set up, create, and generate the Payment times reporting schema for Australia, including outlines on configuration and statistics on invoices.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/11/2024
ms.reviewer: johnmichalak
ms.search.region: Australia

---

# Payment times reporting schema

[!include [banner](../../includes/banner.md)]

This article explains how to set up, create, and generate the Payment times reporting schema (PTRS) that is required for Australian legal entities.

The Australian government established the PTRS to help improve payment times for Australian small businesses. Under the schema, large businesses and government enterprises must report their small business payment terms and times every six months during an income year. In addition, legal entities must include payment information about the goods and services that they procured from small business suppliers under a trade credit arrangement.

## General configuration

Before you generate the report, you must identify vendors as small business suppliers and import the required electronic configurations.

### Identify small business suppliers

Large businesses can use the Small Business Identification (SBI) tool to identify their small business suppliers. The current functionality doesn't include the process of recovering the list of small business suppliers from the SBI tool and then updating Microsoft Dynamics 365 Finance. However, the categorization of this type of suppliers is available in the **Accounts payable** module.

Follow these steps to identify small business suppliers.

1. Go to **Accounts payable** \> **Vendors** \> **All vendors**.
2. Select the required vendor, and then, in the **Vendor profile** section, set the **Small vendor** option to **Yes**.
3. Select **Save**.
4. Repeat steps 2 and 3 to identify each small business supplier that is registered in the legal entity.
5. Close the page.

### Import electronic configurations

In Finance, import the following versions or later of these Electronic reporting (ER) configurations from the Global repository:

| ER configuration name | Type | Description |
|-----------------------|------|-------------|
| Statistics on invoices | Model | Generic model for invoice and payment statistics. |
| Payment times bill model mapping | Model mapping | Model mapping for invoice and payment times statistics. |
| Payment times - PTRS 2024 (AU) | Format (Excel) | Payment Times Reporting Scheme for Australia for reporting periods starting from July 1, 2024. |
| Payment times bill (AU) | Format (Excel, CSV) | Payment Times Reporting Scheme for Australia for reporting periods before July 1, 2024. |

For more information about how to import ER configurations, see [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

## Statistics on invoices process

This section outlines the reporting process for Australia’s Payment Times Reporting Scheme, applicable to reporting periods starting July 1, 2024.

Before you generate the **Payment times** report, run the **Statistics on invoices** process to generate a specific view of the payments history. This process is created for other features and consumed by the **Payment times** report process to get all invoices that have been fully and partially paid. You can run the process in real time, or you can schedule it to run in the background through batch processing.

1. Go to **Accounts payable** \> **Periodic tasks** \> **Statistics on invoices**.
2. Select **Calculate statistics**.
3. Select the **From** and **To** dates. These dates represent the period that should be reported.
4. Optionally, select one or more vendor posting profiles. Vendor posting profiles let you easily include vendor transactions for all vendors, a group of vendors, or a single vendor on the report that is generated. To select all available vendors, leave the field blank. These settings apply only to the reporting legal entity. Starting from the July 1, 2024 reporting period, your organization may be required by the Australian Payment Times Reporting Regulator to consolidate data from multiple legal entities into a single reporting entity. For further details, refer to the official guidance materials published by the Australian Government.
5. Optionally, select the vendor group. The **Vendor group** field lets you introduce an additional transaction filter. To select all available vendors, leave the field blank.
6. Optionally, to consolidate data from multiple legal entities into a single reporting entity, expand the **Cross company** FastTab select the relevant legal entities, along with the appropriate **Posting profile** and **Vendor group** for each.

![Statistics on invoices page](../media/apac-aus-ptrs-calculate-statistics-dialog.png)

7. Select **OK** to run the process.

> [!NOTE]
> When the **Calculate statistics** command is run based on the selected parameters, it selects all invoices that were fully and partially settled during a specific period for all the selected vendors. Payments for vendors that aren't small business suppliers are also included. The report includes the amount of all payments for the selected legal entities and the current (reporting) legal entity. The identification of the small vendor supplier can be found in the header section under the **Small business** slicer.

![Statistics on invoices page](../media/apac-aus-ptrs-statistics-page.png)

> [!NOTE]
> The **Cross company** FastTab, along with the option to consolidate data from multiple legal entities into a single reporting entity, is available for reporting periods starting July 1, 2024.

### Payment times report pre-processing and generation

This section outlines the reporting process for Australia’s Payment Times Reporting Scheme, applicable to reporting periods starting July 1, 2024.

PTRS processing lets you create or update the booking period, and prepare all the information and metrics that are required on the **Payment times** report. The processing takes into account the payment terms that are specified for invoices and **Purchase agreements**.

Follow these steps to process and generate the report.

1. On the **Statistics on invoices** page, select **Payment times report**.
2. Select **PTRS processing**, and create the related booking period by specifying the **From** and **To** dates.
3. Optionally, mark the **Recalculate dataset** checkbox to recalculated the **Dataset** for the selected period.
4. Optionally, expand the Run in the background FastTab and configure the batch parameters to process the dataset in the background.
5. Select **OK**.

As a result, the dataset for the PTRS is generated. To see the dataset with all the necessary information for PTRS, click the **Dataset** button on the Action pane of the **Payment times report** page.
   
Review the generated dataset and PTRS data. Some of the prepared information can be edited. If any dataset fields that impact the main PTRS report have been modified, you may need to recalculate the PTRS data.
To do this, run the PTRS processing again for the same period without selecting **Recalculate dataset**. This will update only the PTRS data without altering the dataset itself.

Select **PTRS report** to generate the report in Excel format that is used to enter the payment information in the tax authority portal.

After the report is generated, the following statistics are included on both reports:

- **Standard payment periods** – The standard payment period, including the shortest and longest standard payment periods, and other changes that the entity offers to its small business suppliers at the beginning of the booking period. The information is gathered in the **Payment period statistics** session. For example, to report the most common standard payment period in calendar days, you must manually specify 30 days in the **SPP** field.
- **Small business invoices paid** – The proportion, which is established by tax authorities. It's determined by the total number and total value of small business invoices that are paid during the booking period for each range of days. This statistic includes only small vendor transactions that are fully settled and paid during the booking period. It doesn't include partial settlements and payments, because the related metric (for example, **<20**, **21-30**, and **31-60**) can't be determined.
- **Small Business procurement** – The total proportion of all invoice payments from small business suppliers during the booking period to all invoices that were paid.
- **Use of supply chain finance** – If the legal entity offers a different type of arrangements, it must report the proportion (by value and number) of small business invoices that were paid under those arrangements during the booking period. In Finance, these invoices are the paid small business invoices that have a cash discount or a payment fee. When a cash discount is defined on the vendor invoice and taken if the invoice is paid by the cash discount date, this transaction is classified as supply chain finance.
		
> [!NOTE]
> The file that has a Word file name extension is used for signatures and associated declarations. It isn't currently supported.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
