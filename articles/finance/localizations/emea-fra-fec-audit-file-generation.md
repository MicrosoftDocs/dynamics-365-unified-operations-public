---
# required metadata

title: Generate FEC from Dynamics 365 Finance
description: This topic explains how to generate the FEC audit file in Dynamics 365 Finance.
author: liza-golub
ms.date: 05/03/2021
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

# Generate FEC in Dynamics 365 Finance

1. To generate FEC, go to **General Ledger** > **Periodic tasks** > **Data export** to open the **Data export** page. 
2. If the Electronic reporting format isn't set up in the **Format mapping** field on the **General ledger parameters**, select **FEC audit file (FR)** in the **Format mapping** field on the **Data export** page, and then select **OK**. 
3. If the Electronic reporting format isn't set up in the **Format mapping** field on the **General ledger parameters** page, you won't see the **Data export** page. You can go directly to the dialog page of the report.
4. On the **Electronic report parameters** page, in the **Period - date from** and **Period - date to** fields, enter the start and end dates for the period.
5. Mark one or more output files to be generated in **FEC report content composition** parameter, and then select **Select**.

    | **Name**               | **Description**                                                                       | **Conditions**                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    |------------------------|---------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | FEC Main               | Main FEC file for the period specified                                                | For this part of the report, specify values in the **Period - date from** and **Period - date to** fields. In the **Period - date from** field, if you specify the beginning of the fiscal period, **opening** type transactions are included in the beginning of the FEC file. If the specified reporting period isn't a full fiscal year, the name of the file includes the number of the period within the related fiscal year at the end. For example, **123456789FEC20131231_01**. |
    | Customers balances     | Customers fiscal year opening balances annex                                          | For this part of the report, specify a value in the **Period - date from**field. The report is generated for the beginning of the fiscal year as it relates to the date specified in the **Period - date from** field. Values in the **JournalCode**, **JournalLib**, **EcritureNum**, **PieceRef**, and **EcritureLib** columns of the report represent values collected from the **opening** type of general ledger transactions for the reporting fiscal year.                                          |
    | Vendors balances       | Vendors fiscal year opening balances annex                                            | For this part of the report, specify a value in the **Period - date from** field. The report is generated for the beginning of the fiscal year as it relates to the date specified in the **Period - date from** field. Values in the **JournalLib**, **EcritureNum**, **PieceRef**, and **EcritureLib** columns of the report represent the values collected from the **opening** type of general ledger transactions for the reporting fiscal year.                                                       |
    | Customers transactions | Customers transactions annex for the specified period.                           | For this part of the report, specify values in the **Period - date from** and **Period - date to** fields.                                                                                                                                                                                                                                                                                                                                                                    |
    | Vendors transactions   | Vendors transactions annex for the specified period.                                   | For this part of the report, specify values in the **Period - date from** and **Period - date to** fields.                                                                                                                                                                                                                                                                                                                                                                    |
    | FEC Main Extended      | EC main file including fiscal year opening balance details for customers and vendors. | For this part of the report, specify values in the **Period - date from** and **Period - date to** fields. Make sure that the specified period includes the beginning of a fiscal year.                                                                                                                                                                                                                                                                                       |

6. General ledger transactions that are included in the report types, **FEC Main** and **FEC Main Extended** are filtered by the **Current** posting layer. Use the filter to specify the records to be included in the report by using the **Records to include** field. Use the filter to report data that complies with the rules of “Livre des procédures fiscales A 47 A 1 chapitre VII (Le numéro de compte, dont les trois premiers caractères doivent correspondre à des chiffres respectant les normes du plan comptable français).
7. On **Run in the background** FastTab, specify the batch parameters to generate the report in batch.
8. When all of the parameters are defined, select **OK** to generate the report.
