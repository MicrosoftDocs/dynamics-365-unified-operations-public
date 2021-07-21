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
4. Select Save .
5. Repeat the above steps for the identification of each small business supplier registered in the legal entity.
6. Close the page.

## Import electronic configurations

In Finance, import the following versions or later of these Electronic reporting (ER) configurations from the Global repository. 

- Statistics on invoices version 40.
- Payment times bill model mapping version 40.10.
- Payment times bill (AU) version 40.20. Excel file and .cvs files are generated and packaged in ZIP file.

For more information about how to download ER configurations, see Download ER configurations from the Global repository.(Download ER configurations from the Global repository of Configuration service - Finance & Operations | Dynamics 365 | Microsoft Docs)


# Statistics on invoices process
Before you generate Payment times report  run the process **Statistic on invoices** to generate an specific view of payments history in a specified period of time. This process has been created for another features and consumed by Payment time report process as well with the aim of getting all invoices partially and fully paid. You can run the process in real time or schedule it to run in the background by using batch processing.

1. Go to **Accounts payable > Periodic tasks > Statistics on invoices**.
2. Press **Calculate statistics** button.
3. Select the from and to dates. These dates represent the period to be reported. 
4. Select the **Vendor posting profile**. Vendor posting profiles let you easily include vendor transactions for all vendors, a group of vendors, or a single vendor on the report that is generated. This option allows you to select multiple vendor posting profiles if required. You can leave in blank to select all available vendors.
5. Optional, select the **Vendor group**. This selection allows you to introduce an additional transaction filter. You can leave in blank to select all available vendors.
6. Select *OK* to run the process.

![Statistics on invoices form.](media/apac-aus-payment-times-reporting-01.JPG)






Note: When **Calculates statistics** is executed based on the parameters selected, you will be able to see all invoices fully and/or partially settled/paid in a specific period of time for all vendors selected before. Non small business vendors payments are also included because this process is used for another features and the amount of all payments of legal entity are also informed in the report . The identification of small vendor supplier is located in the header section under **Small business** slicer.
