---
# required metadata

title: VAT statements details for Italy
description: This topic explains how to set up a VAT statement for legal entities in Italy. 
author: ShylaThompson
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 81
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 269664
ms.assetid: af07d122-5694-4de6-96bf-7bf5478b0175
ms.search.region: Italy
# ms.search.industry: 
ms.author: sndray
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# VAT statements details for Italy

This topic explains how to set up a VAT statement for legal entities in Italy. 

Set up customer/vendor tax information for tax reports
------------------------------------------------------

To generate the sales tax report, the customer and vendor must be configured with the fiscal information for Italy. On the **Customers** page, select the fields in the following table.

#### Invoice and delivery

| **Field**             | **Description**                                        |
|-----------------------|--------------------------------------------------------|
| **Tax exempt number** | Enter the tax exempt number for VAT declaration.       |
| **Fiscal code**       | Enter the fiscal code for this customer.               |
| **Sales tax Group**   | Select a sales tax group to be used for this customer. |

On the **Vendors** page, select the fields in the following table.

#### Invoice and delivery

| **Field**             | **Description**                                      |
|-----------------------|------------------------------------------------------|
| **Tax exempt number** | Enter the tax exempt number for VAT declaration.     |
| **Fiscal code**       | Enter the fiscal code for this vendor.               |
| **Sales tax Group**   | Select a sales tax group to be used for this vendor. |

## Set up a company fiscal code and tax registration number
To generate reports, the company fiscal code and registration number should be set up on the **Legal entity** page. On the **Legal entity** page, select the fields in the following table.

#### Registration numbers

| **Field**        | **Description**                                                    |
|------------------|--------------------------------------------------------------------|
| **Fiscal Code**  | Enter the fiscal code from the legal entity registration in Italy. |
| **Legal Nature** | Enter the legal structure of the company.                          |
| **CUC**          | Enter the CUC code.                                                |

#### Tax registration

| **Field**               | **Description**                                                 |
|-------------------------|-----------------------------------------------------------------|
| Tax registration number | Enter the tax registration number for the legal entity in Italy |

#### Set up parameters for Italian sales tax book

On the **Sales tax** page, create sales tax books to be reported to the Italian government after the settlement period is past.

| **Field**                     | **Description**                                 |
|-------------------------------|-------------------------------------------------|
| **Sales tax book type**       | Enter the movement direction. (Sales/Purchase)  |
| **Sales tax book**            | Enter the identifier of the sales tax book.     |
| **Name**                      | Enter the name of the sales tax book.           |
| **Sales tax book type**       | Enter the movement direction. (Sales/Purchase)  |
| **Settlement period**         | The period for this tax book.                   |
| **Closed to**                 | Select the transaction date.                    |
| **EU sales**                  | The amount sold to the European Union.          |
| **ATECOFIN**                  | The tax code for sales tax reporting.           |
| **Print summary and payment** | Select to print the summary and payment report. |

## Yearly tax communication report
After the year end, generate the report for each settlement period. The transmission is mandatory as required by the Italian fiscal authority via a website. On the **Yearly tax communication** page, it is possible to create or view a report.

#### Overview

| **Field**                | **Description**                                                                               |
|--------------------------|-----------------------------------------------------------------------------------------------|
| **Tax communication ID** | Enter the identification number of the Yearly tax communication report.                       |
| **Years**                | Enter the year of the tax communication.                                                      |
| **ATECOFIN Code**        | Enter the tax code that is associated with the classification of possible company activities. |
| **Exported**             | Indicates that the .ivc file is exported.                                                     |

#### General

| **Field**                | **Description**                                                                               |
|--------------------------|-----------------------------------------------------------------------------------------------|
| **Tax communication ID** | Enter the identification number of the Yearly tax communication report.                       |
| **Years**                | Enter the year of the tax communication.                                                      |
| **ATECOFIN Code**        | Enter the tax code that is associated with the classification of possible company activities. |
| **Exported**             | Indicates that the file was exported.                                                         |
| **Date of export**       | The date when the .ivc file was exported.                                                     |
| **Export file name**     | The name of the .ivc file.                                                                    |

## VAT summary report
For VAT reporting, Italy has specific information to be reported and formatted. In the **Sales tax authorities** page, on **Tax setup**, configure the Italian authority.

| **Field**                                 | **Description**                                                                                |
|-------------------------------------------|------------------------------------------------------------------------------------------------|
| **Report layout**                         | Select the Italian report to enable Italian fields.                                            |
| **Print blank page with no transactions** | Select to print blank pages when no transactions are present.                                  |
| **Separate summary register**             | Select this check box to use a separate value added tax (VAT) book to number summary sections. |
| **Account gain**                          | Gain due to rounding.                                                                          |
| **Account loss**                          | Loss due to rounding.                                                                          |

## Sales tax settlement periods
Per Italian legislation, rules apply to settlement periods. For example, after the settlement period is closed, no change is allowed. You are required to report if the settlement refers to the last period on the fiscal year. View the settlement period status and report if it refers to a year closing. On the **Sales tax settlement period** page &gt; **Period Intervals** tab, select the following fields.

| **Field**       | **Description**                                                                                   |
|-----------------|---------------------------------------------------------------------------------------------------|
| **Closed**      | Indicates if the Italian sales tax book for the period has been updated and automatically closed. |
| **Last period** | Select this option if the period is the last period in a sales tax year.                          |



