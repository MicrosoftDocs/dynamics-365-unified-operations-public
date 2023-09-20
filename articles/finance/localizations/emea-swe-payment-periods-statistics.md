---
title: Reporting statistics of vendor payment periods
description: This article explains how to set up and generate the Statistics of vendor payment periods required in Sweden.
author: AdamTrukawka
ms.date: 09/20/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: APAC
ms.author: atrukawk
ms.search.validFrom: 2023-09-12
ms.dyn365.ops.version: 
ms.search.form: 
---

# Reporting statistics of vendor payment periods

This article explains how to set up and generate Statistics of vendor payment periods required in Sweden.

Starting March 1, 2022, a new regulation has been implemented in Sweden that mandates large companies (more than 249 employees) report their payment terms with subcontractors to the Swedish Companies Registration Office (SCRO) (Bolagsverket). This initiative is designed to counteract the trend of extending payment terms and aims to foster growth among smaller Swedish companies by creating the best possible conditions for them to develop and grow.

The information that these companies are required to report includes: 

   - Average agreed payment term
   - Average actual payment term
   - Percentage of invoices paid after the agreed term
   
Payment terms must be reported separately for subcontractors of different sizes: those with 0 – 9 employees, 10 – 49 employees, and 50 – 249 employees. If a company uses reverse factoring, that information must be reported separately. If reverse factoring is used for all three size categories of subcontractors, an additional nine items must be reported.

Large companies must report payment terms statistics for the period starting July 1 of the previous year through June 30 of the current year. The company must then submit the information by the end of September. For more information, contact the Swedish Companies Registration Office or visit their e-service portal at [www.bolagsverket.se](https://www.bolagsverket.se).

## General Configuration
Before you generate the report, complete the following setup. 

### Import electronic configurations
In Dynamics 365 Finance, import the following components of Electronic reporting (ER) configurations from the Global repository. Make sure you select the most recent version:

   - Vendor size category model
   - Vendor size category import format
   - Vendor size category model mapping to destination

Compare imported configurations on the **Reporting configurations** page in the Electronic Reporting workspace.


For more information about how to import ER configurations, see [Download Electronic reporting configurations from Lifecycle Services](../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md)

### Create a reporting period and import SCRO vendor size definition data

The size definition for Swedish based companies is published every year by the Swedish Companies Registration Office (Bolagsverket) in the e-service. The SCRO also publishes a file with all small companies under 250 employees that are in scope for the vendor payment periods reporting. To configure the **Statistics of vendor payment periods** report in Finance, access the SCRO e-service using your company's registered business credentials and download the published file.

The downloaded file from SCRO (Bolagsverket) e-service must be imported into Finance. 

1. Go to **Accounts Payable** > **Periodic Tasks** > **Statistics of vendor payment periods**.
2. On the **Statistics of vendor payment periods** page, select **New** to create a new reporting period and enter the reporting period dates. 
3. Select **SCRO data** to open the **Vendor size category** page.
4. On the **Vendor Size Category** page, select **Import SCRO Data**. Two dialog pages will open.
5. On the first dialog page, select the **Vendor size category import format** that you imported earlier and select **OK**.
6. On the next dialog page, browse to and select the file you downloaded from the SCRO. The system imports the file to temporary storage and begins processing the data from the file. The processing runs a search for vendors created in a legal entity and matches those with the data provided in the SCRO data file. The matching process is based on Swedish company official identification number or tax registration number, whichever matches first. Make sure all vendors have at least one of those numbers filled.

> [!NOTE]
> Processing and matching the vendors size category can take a significant amount of time depending on number of vendor records in a legal entity. Therefore, you may choose batch processing for this task. To enable batch mode for this task, you must enable the feature **Run ER import of manually uploaded documents in batch**. Go to the **Feature management** workspace, locate the feature in the list, and select **Enable**. 


The SCRO data file is provided as a CSV file in the Bolagsverket e-service. Most antivirus services may interrupt during the time the file is being downloaded, saved, or processed. To be assured that the file has downloaded completely and isn't corrupted, verify the size of file with information provided by SCRO. In the 2023 reporting period, the file size was approximately 92MB. If there is any issue with importing and matching the file, search for vendor at the Bolagsverket e-service. Then, manually add the record for your vendor and their size category in the **Vendor Size Category** form.

## Calculate vendor payment statistics

After the vendors size category classification of your vendors have been configured, run the calculation of statistics. 

Statistics related to payment delays are based on the rule that calculates the number of days a payment is delayed for each vendor invoice transaction. The calculation formula subtracts the invoice date from the payment date and rounds the result down to the nearest integer. For example, if an invoice is issued on January 1 and paid on January 15, the delay is 14. If an invoice date is January 1 and paid on January 31, the delay is 30. 

To calculate payment terms, the **Payment due date** on the transaction invoice is used. The calculation formula subtracts the invoice date from the payment due date and rounds the result to the nearest integer. For example, if an invoice date is January 1 and payment due date is January 11, the actual payment term days are 10.

The report considers invoices paid after the agreed payment term if the payment date is later than the payment due date. The latest delayed payment date of the invoice is taken for statistics when an invoice is paid multiple times.

The percentage of invoices paid after the agreed payment term is calculated and includes all invoices paid in the reporting period. 

1.	Go to **Accounts Payable** > **Periodic Tasks** > **Statistics of vendor payment periods** to run the calculation of statistics. 
2.	Select **Calculate Statistics**. The system opens a dialog form starting process of calculating statistics of payment delays. 
3. If your company transacts frequently with many small companies resulting with large number of transactions, you can filter vendors by **Posting profile** or **Vendor group** to create a smaller report. You can use the filters to prepare a separate report for groups of vendors that are paid using reverse factoring services. You can also run the processing in batch.
4. Select **OK**. 

The system calculates all of the data required for reporting. You may verify the calculations in the provided data for the form for each vendor size category. On the **Vendor invoices** page, navigate through each transaction included in the statistics calculation. For each transaction, you can view the settlement, original documents, and payments by selecting **View Settlements**. 

   > [!NOTE]
   > On the **Vendor invoices** page, there are fields you can add to the page by selecting the page customization options. You may also choose to export data from the page to Microsoft Excel for further analysis. 

## Reporting to the Swedish Companies Registration Office
At this time, the Swedish Companies Registration Office requires that you file the report by manually entering information in the Bolagsverket e-service. Therefore, navigate to the reporting area in the e-service and fill in the required statistics in the office forms online.
