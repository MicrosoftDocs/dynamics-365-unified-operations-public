---
# required metadata

title: The Payment times reporting scheme
description: This topic provides information about the generation of Payment time reporting scheme for Australia. The PTRS is a report that large legal entities submit to the Australian tax authority to report on their payment terms and practices to small business suppliers
author: sndray
ms.date: 07/21/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 12641
ms.search.region: Australia
# ms.search.industry: 
ms.author: sndray
ms.search.validFrom: 
ms.dyn365.ops.version:

---

# Payment times reporting schema

This topic explains how to set up, create, and generate the Payment Times Reporting Schema (PTRS) required for Australian legal entities.

The Australian Government established the Payment Times Reporting Scheme with the aims to improve payment times for Australian small businesses. Under the scheme, large businesses and government enterprises need to report their small business payment terms and times each six months of an income year . In addition to this, the legal entity must include payment information on the goods and services procured from small business suppliers under a trade credit arrangement.

# General configuration
Before to start with the generation of this report, complete the following configurations:

## Identification of small business vendor. 
Large businesses required to report can use the Small Business Identification (SBI) tool to identify their small business suppliers. The current functionality doesn't include the process of recovering the list of small business suppliers from SBI tool and update in Dynamics 365, however the categorization of these type of suppliers is available in account payable module. Complete the following steps to identify small business suppliers.

1. Select **Accounts payable > Vendors > All vendors**  and then select a required vendor.
2. Expand or collapse the **Vendor profile** section.
3. Set the **Small vendor** option to  "Yes".
4. Select **Save**.
5. Repeat the above steps for the identification of each small business supplier registered in the legal entity.
6. Close the page.

## Import electronic configurations

In Finance, import the following versions or later of these Electronic reporting (ER) configurations from the Global repository. 

- Statistics on invoices version 40.
- Payment times bill model mapping version 40.10.
- Payment times bill (AU) version 40.20. Excel file and .cvs files are generated and packaged in ZIP file.

For more information about how to import Electronic Reporting configurations, see [Download Electronic reporting configurations from Lifecycle Services](../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

# Statistics on invoices process
Before you generate Payment times report  run the process **Statistic on invoices** to generate an specific view of payments history in a specified period of time. This process has been created for another features and consumed by Payment time report process as well with the aim of getting all invoices partially and fully paid. You can run the process in real time or schedule it to run in the background by using batch processing.

1. Go to **Accounts payable > Periodic tasks > Statistics on invoices**.
2. Press **Calculate statistics** button.
3. Select the from and to dates. These dates represent the period to be reported. 
4. Select the **Vendor posting profile**. Vendor posting profiles let you easily include vendor transactions for all vendors, a group of vendors, or a single vendor on the report that is generated. This option allows you to select multiple vendor posting profiles if required. You can leave in blank to select all available vendors.
5. Optional, select the **Vendor group**. This selection allows you to introduce an additional transaction filter. You can leave in blank to select all available vendors.
6. Select **OK** to run the process.

![Statistics on invoices form.](media/apac-aus-payment-times-reporting-01.JPG)


> [!NOTE]
> When **Calculates statistics** is executed based on the parameters selected, you will be able to see all invoices fully and/or partially settled/paid in a specific period of time for all vendors selected before. Non small business vendors payments are also included because this process is used for another features and the amount of all payments of legal entity are also informed in the report . The identification of small vendor supplier is located in the header section under **Small business** slicer.

## Payment times report pre-processing and generation
The action PTRS processing allows users to create or update the booking period and prepare the all information and metrics required in Payment times report . The process compares and calculates the due dates on the invoices to the payment received date for the payments settled to the invoice. 

Complete the following steps to process and generate the report.
1. Click on **Payment times report** .
2. Click on **PTRS processing** to create the related booking period by introducing following dates
  a. From date
  b. To date
3. Select **OK** to confirm.
4. Complete the information required in the right part of the form  in accordance with the tax authority guideline.
		• Entity name and ABN. Both fields are automatically populated from Legal entity information
		• Information about controlling corporation and head entity
		• Reporting period.
		• Details of the person who submitted the report.
		• Approver of the report.
		• Entity’s principal governing body.
		• A declaration by a responsible member.
		• Payment period statistics.
		• Invoicing arrangements.
		• Supply change finance arrangement.
		• Notifiable events.
		• Report comments.
		• Submission and approval details
5. Select **PTRS report**  to generate the Payment times control report and a .csv file to input the payment information into the tax authority portal.

![PTRS form.](media/apac-aus-payment-times-reporting-02.JPG)

Once the generation of report is executed the following statistics are included in both reports:

- **Standard payment periods**. The standard payment period including the shortest and longest standard payment periods and other changes that the entity offers to its small business vendor at the beginning of the booking period. The information is gathered from the above form in **Payment period statistics** session . The user must introduce manually for example 30 days is the SPP  field to report  what this is the most common standard payment period in calendar days.
- **Small business invoices paid**. The proportion, determined by total number and total value of small business invoices paid during the booking period for each range of days established by tax authorities.  Small vendors transactions fully settled and paid during the booking period are only included in this statistic. Partial settlement and payment are not included in this statistics because is not possible to determine the related metric, <20, 21-30, 31-60, etc.
- **Small Business procurement**. This metric represents total proportion of all invoice payments during the booking period  that was from small business vendors compared to all invoices paid. 
- **Use of supply chain finance**. If the legal entity offer different type of arrangements, the legal entity must report the proportion (by value and number) of small business invoices paid under these arrangements during the booking period. In Dynamics Finance context, these are the small business invoice paid with cash discount or payment fee. When a cash discount is defined in the vendor invoice and taken if the invoice is paid within the cash discount date, then this transaction is classified as supply chain finance.
		
> [!NOTE]
> A word file for signatures and associated declarations is not currently supported.
