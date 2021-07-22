---
# required metadata

title: Payment times reporting schema
description: This topic provides information about generating the Payment time reporting schema for Australia. 
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

This topic explains how to set up, create, and generate the Payment times reporting schema (PTRS) required for Australian legal entities.

The Australian government established the PTRS with the goal to improve payment times for Australian small businesses. Under the schema, large businesses and government enterprises must report their small business payment terms and times every six months of an income year. In addition, the legal entity must include payment information on the goods and services procured from small business suppliers under a trade credit arrangement.

## General configuration
Before you generate the report, you must identify the small business vendors and import the necessary electronic configurations.

### Identify small business vendors
Large businesses can use the Small Business Identification (SBI) tool to identify their small business suppliers. The current functionality doesn't include the process of recovering the list of small business suppliers from SBI tool and then updating Dynamics 365 Finance. However, the categorization of these type of suppliers is available in the **Accounts payable** module. Complete the following steps to identify small business suppliers.

1. Select **Accounts payable** > **Vendors** > **All vendors**.  
2. Select a required vendor, and expand or collapse the **Vendor profile** section.
3. Set the **Small vendor** option to **Yes** and then select **Save**.
4. Repeat steps 2 and 3 to identify each small business supplier registered in the legal entity.
5. Close the page.

### Import electronic configurations

In Finance, import the following versions or later of these Electronic reporting (ER) configurations from the Global repository. 

- Statistics on invoices version 40.
- Payment times bill model mapping version 40.10.
- Payment times bill (AU) version 40.20. Excel file and .cvs files are generated and packaged in ZIP file.

For more information about how to import Electronic Reporting configurations, see [Download Electronic reporting configurations from Lifecycle Services](../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

## Statistics on invoices process
Before you generate the Payment times report, run the process **Statistic on invoices** to generate a specific view of the payments history. This process is created for other features and consumed by the Payment time report process to get all invoices partially and fully paid. You can run the process in real time or schedule it to run in the background by using batch processing.

1. Go to **Accounts payable** > **Periodic tasks** > **Statistics on invoices**.
2. Select **Calculate statistics**.
3. Select the from and to dates. These dates represent the period to be reported. 
4. Select a vendor posting profile. Vendor posting profiles let you easily include vendor transactions for all vendors, a group of vendors, or a single vendor on the report that is generated. This option allows you to select multiple vendor posting profiles if required. To select all available vendors, leave the field blank.
5. Optional, select the **Vendor group**. You can use this field to introduce an additional transaction filter, or leave it blank to select all available vendors.
6. Select **OK** to run the process.

![Statistics on invoices form.](media/apac-aus-payment-times-reporting-01.JPG)


> [!NOTE]
> When **Calculates statistics** is executed based on the parameters selected, you can see all invoices fully and partially settled in a specific period of time for all of the selected vendors selected. Non small business vendors payments are also included because this process is used for another feature and the amount of all payments of a legal entity are included in the report . The identification of the small vendor supplier is located in the header section under the **Small business** slicer.

### Payment times report pre-processing and generation
PTRS processing lets you create or update the booking period and prepare the all information and metrics required in the Payment times report. The process compares and calculates the due dates on the invoices to the payment received date for the payments settled to the invoice.

Complete the following steps to process and generate the report.

1. Select **Payment times report**.
2. Select **PTRS processing** to create the related booking period by introducing following dates:
  
  - From date
  - To date
  
3. Select **OK** to confirm.
4. Complete the information required in the right part of the page according to the tax authority guidelines.

   - Entity name and ABN. Both fields are automatically populated from the legal entity information.
   - Information about controlling corporation and head entity.
   - Reporting period.
   - Details of the person who submitted the report.
   - Approver of the report.
   - Entity’s principal governing body.
   - A declaration by a responsible member.
   - Payment period statistics.
   - Invoicing arrangements.
   - Supply change finance arrangement.
   - Notifiable events.
   - Report comments.
   - Submission and approval details.
   
5. Select **PTRS report** to generate the the report and a .csv file to input the payment information into the tax authority portal.

![PTRS form.](media/apac-aus-payment-times-reporting-02.JPG)

After the report is generated, the following statistics are included in both reports:

- **Standard payment periods**: The standard payment period, including the shortest and longest standard payment periods, and other changes that the entity offers to its small business vendor at the beginning of the booking period. The information is gathered in the **Payment period statistics** session. You must manaully add for example, 30 days in the **SPP** field to report what is the most common standard payment period in calendar days.
- **Small business invoices paid**: The proportion, which is determined by total number and total value of small business invoices paid during the booking period for each range of days, is established by tax authorities. Small vendor transactions that are fully settled and paid during the booking period are only included in this statistic. Partial settlement and payment aren't included in this statistic because it isn't possible to determine the related metric, <20, 21-30, 31-60, etc.
- **Small Business procurement**: This metric represents total proportion of all invoice payments during the booking period from small business vendors compared to all invoices paid. 
- **Use of supply chain finance**: If the legal entity offers a different type of arrangements, the legal entity must report the proportion (by value and number) of small business invoices paid under these arrangements during the booking period. In Finance, these are the small business invoice paid with cash discount or payment fee. When a cash discount is defined in the vendor invoice and taken if the invoice is paid within the cash discount date, this transaction is classified as supply chain finance.
		
> [!NOTE]
> The file with a Microsoft Word extension is used for signatures and associated declarations and isn't currently supported.
