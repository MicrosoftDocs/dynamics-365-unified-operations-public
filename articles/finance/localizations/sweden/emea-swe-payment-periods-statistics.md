---
title: Report statistics of vendor payment periods
description: Learn how to set up and generate the statistics of vendor payment periods that are required in Sweden with an outline on calculating vendor payment statistics.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: article
ms.date: 09/20/2023
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: APAC
ms.search.validFrom: 2023-09-12
ms.search.form: 
ms.dyn365.ops.version: 
---

# Report statistics of vendor payment periods

This article explains how to set up and generate the statistics of vendor payment periods that are required in Sweden.

As of March 1, 2022, a new regulation that was implemented in Sweden mandates that large companies must report their payment terms with subcontractors to the Swedish Companies Registration Office (SCRO) (Bolagsverket). (Large companies are defined as those that have 250 or more employees.) This regulation is designed to counteract the trend of extending payment terms. Its purpose is to foster growth among smaller Swedish companies by creating the best possible conditions for them to develop and grow.

Here is some of the information that large companies are required to report:

- Average agreed payment term
- Average actual payment term
- Percentage of invoices that are paid after the agreed payment term

Payment terms must be reported separately for subcontractors of different sizes:

- Subcontractors that have 0–9 employees
- Subcontractors that have 10–49 employees
- Subcontractors that have 50–249 employees

If a company uses reverse factoring, that information must be reported separately. If reverse factoring is used for subcontractors that belong to all three size categories, nine additional items must be reported.

Large companies must report payment term statistics for the period that extends from July 1 of the previous year through June 30 of the current year. They must then submit the information by the end of September. For more information, contact SCRO, or visit its e-service portal at [www.bolagsverket.se](https://www.bolagsverket.se).

## General configuration

Before you generate the report, complete the following setup.

### Import Electronic reporting configurations

In Microsoft Dynamics 365 Finance, import the following components of Electronic reporting (ER) configurations from the Global repository. Make sure that you select the most recent version.

- Vendor size category model
- Vendor size category import format
- Vendor size category model mapping to destination

Compare imported configurations on the **Reporting configurations** page in the **Electronic Reporting** workspace.

For more information about how to import ER configurations, see [Download Electronic reporting configurations from Lifecycle Services](../../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

### Create a reporting period and import SCRO vendor size definition data

Every year, SCRO (Bolagsverket) publishes the size definition for Swedish-based companies in the e-service. SCRO also publishes a file that shows all small companies that have fewer than 250 employees, but that are in scope for vendor payment periods reporting.

To configure the **Statistics of vendor payment periods** report in Finance, access the SCRO e-service by using your company's registered business credentials, and download the published file. You must then import the downloaded file into Finance.

1. In Finance, go to **Accounts payable** \> **Periodic tasks** \> **Statistics of vendor payment periods**.
2. On the **Statistics of vendor payment periods** page, select **New** to create a reporting period, and enter the reporting period dates.
3. Select **SCRO data**.
4. On the **Vendor Size Category** page, select **Import SCRO Data**.
5. In the dialog box that appears, select the **Vendor size category import format** component that you imported earlier, and then select **OK**.
6. In the next dialog box that appears, browse to and select the data file that you downloaded from SCRO. The system imports the file into temporary storage and starts to process the data from it.

    The processing runs a search for vendors that were created in a legal entity. It then matches those vendors with the data that's provided in the SCRO data file. The matching process is based on either the Swedish company official identification number or the tax registration number, whichever is matched first. Make sure that at least one of those numbers is filled in for ever vendor.

> [!NOTE]
> Processing and matching of the vendor size category can take a significant amount of time, depending on the number of vendor records in a legal entity. Therefore, you might want to use batch processing for this task. To enable batch mode for this task, you must enable the **Run ER import of manually uploaded documents in batch** feature. Open the **Feature management** workspace, find the feature in the list, and select **Enable**.

The SCRO data file is provided as a comma-separated values (CSV) file in the SCRO e-service. Most antivirus services might interrupt while the file is being downloaded, saved, or processed. To ensure that the file is completely downloaded and isn't corrupted, verify the file size against the information that SCRO provides. In the 2023 reporting period, the file size was approximately 92 megabytes (MB). If you have any issues importing and matching the file, search for the vendor in the SCRO e-service. Then, on the **Vendor Size Category** page in Finance, manually add a record for the vendor and its size category.

## Calculate vendor payment statistics

After you've configured the vendor size category classification of your vendors, run the calculation of statistics.

Statistics that are related to payment delays are based on the rule that calculates the number of days that a payment is delayed for each vendor invoice transaction. The calculation formula subtracts the invoice date from the payment date and rounds the result down to the nearest integer. For example, if an invoice is issued on January 1 and paid on January 15, the delay is 14. If an invoice is issued on January 1 and paid on January 31, the delay is 30.

To calculate payment terms, the payment due date on the transaction invoice is used. The calculation formula subtracts the invoice date from the payment due date and rounds the result to the nearest integer. For example, if the invoice date of an invoice is January 1, and the payment due date is January 11, the actual payment term days are 10.

The report considers invoices that are paid after the agreed payment term if the payment date is later than the payment due date. If an invoice is paid multiple times, the latest delayed payment date of the invoice is used for statistics.

The percentage of invoices that are paid after the agreed payment term is calculated and includes all invoices that are paid during the reporting period.

1.	Go to **Accounts payable** \> **Periodic tasks** \> **Statistics of vendor payment periods** to run the calculation of statistics.
2.	Select **Calculate Statistics**. The system starts the process of calculating statistics of payment delays.
3. If your company often transacts with many small companies, so that the result is a large number of transactions, you can filter vendors by **Posting profile** or **Vendor group** value to create a smaller report. You can use the filters to prepare a separate report for groups of vendors that are paid by using reverse factoring services. You can also run the processing in batch mode.
4. Select **OK**.

The system calculates all the data that's required for reporting. You can verify the calculations in the provided data for the page for each vendor size category. On the **Vendor invoices** page, go through each transaction that's included in the statistics calculation. For each transaction, you can view the settlement, original documents, and payments by selecting **View Settlements**.

> [!NOTE]
> There are other fields that you can add to the **Vendor invoices** page by using the page customization options. You can also export data from this page to Excel for further analysis.

## Report statistics to SCRO

Currently, SCRO (Bolagsverket) requires that you file the report by manually entering information in the SCRO e-service. In the e-service, go to the reporting area, and fill in the required statistics in the online forms.
