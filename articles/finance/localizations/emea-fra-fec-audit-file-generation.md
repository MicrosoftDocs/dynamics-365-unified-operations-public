---
# required metadata

title: How to generate FEC from Dynamics 365 Finance
description: This topic describes how to generate FEC in Dynamics 365 Finance.
author: liza-golub
ms.date: 28/04/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom:
ms.search.region: France

---

# How to generate FEC in Dynamics 365 Finance

To generate FEC, go to **General Ledger** \> **Periodic tasks** \> **Data
export** to open the **Data export** page. If Electronic reporting format is not
set up in **General ledger parameters**, in the **Format mapping** field, you
must select **FEC audit file (FR)** in the **Format mapping** field on the
**Data export** page and click **OK**. If Electronic reporting format is not set
up in **General ledger parameters**, in the **Format mapping** field, you will
not see the **Data export** page and you can go directly to the dialog page of
the report.

On the **Electronic report parameters** page, enter start and end dates for the
period in the **Period - date from** and **Period - date to** fields.

Mark one or several output files to be generated in **FEC report content
composition** parameter and click **Select**.

| **Name**               | **Description**                                                                       | **Conditions**                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|------------------------|---------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| FEC Main               | Main FEC file for the period specified                                                | For this type of the report you must specify **Period - date from** and **Period - date to** values. If in the **Period - date from** you specify the beginning of the fiscal period, transactions of ‘opening’ type will be included in the beginning of the FEC file. If specified reporting period is not a full fiscal year, the name of the file will include the number of the period within the related fiscal year at the end. Example: 123456789FEC20131231_01 |
| Customers balances     | Customers fiscal year opening balances annex                                          | For this type of the report you must specify **Period - date from** value. Report will be generated for the beginning of the fiscal year related to the date specified in the **Period - date from** field. Values for JournalCode, JournalLib, EcritureNum, PieceRef, EcritureLib columns of the report will represent values collected from the general ledger transactions of ‘opening’ type for the reporting fiscal year.                                          |
| Vendors balances       | Vendors fiscal year opening balances annex                                            | For this type of the report you must specify **Period - date from** value. Report will be generated for the beginning of the fiscal year related to the date specified in the **Period - date from** field. Values for JournalLib, EcritureNum, PieceRef, EcritureLib columns of the report will represent values collected from the general ledger transactions of ‘opening’ type for the reporting fiscal year.                                                       |
| Customers transactions | Customers transactions annex for the period specified                                 | For this type of the report you must specify **Period - date from** and **Period - date to** values.                                                                                                                                                                                                                                                                                                                                                                    |
| Vendors transactions   | Vendors transactions annex for the period specified                                   | For this type of the report you must specify **Period - date from** and **Period - date to** values.                                                                                                                                                                                                                                                                                                                                                                    |
| FEC Main Extended      | EC main file including fiscal year opening balances details for customers and vendors | For this type of the report you must specify **Period - date from** and **Period - date to** values. Make sure that the period specified includes the beginning of a fiscal year.                                                                                                                                                                                                                                                                                       |

General ledger transaction included into the report type of “FEC Main” and “FEC
Main Extended” are filtered by the “Current” posting layer. You can additionally
specify filters for the records to be included to the report by using **Records
to include**. Make sure that you specify filter to report data compliant with
the rules of “Livre des procédures fiscales A 47 A 1 chapitre VII (Le numéro de
compte, dont les trois premiers caractères doivent correspondre à des chiffres
respectant les normes du plan comptable français).

Specify batch parameters on **Run in the background** fast tab to generate the
report in batch.

Select OK when all the necessary parameters of the report are defined, to run
the report generation.
