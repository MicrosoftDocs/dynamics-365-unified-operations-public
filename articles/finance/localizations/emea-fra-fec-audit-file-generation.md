---
# required metadata

title: Generate an FEC in Dynamics 365 Finance
description: This topic explains how to generate a Fichier des écritures comptables (FEC) audit file in Microsoft Dynamics 365 Finance.
author: liza-golub
ms.date: 05/10/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.author: elgolu
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom:
ms.search.region: France

---

# Generate an FEC in Dynamics 365 Finance

To generate a Fichier des écritures comptables (FEC) audit file, follow these steps.

1. Go to **General Ledger** \> **Periodic tasks** \> **Data export**. 
2. If the Electronic reporting (ER) format isn't set up in the **Format mapping** field on the **General ledger parameters** page, select **FEC audit file (FR)** in the **Format mapping** field on the **Data export** page. Then select **OK**. 
3. If the ER format is set up in the **Format mapping** field on the **General ledger parameters** page, the **Data export** page doesn't appear. You can go directly to the dialog box for the report.
4. On the **Electronic report parameters** page, in the **Period - date from** and **Period - date to** fields, enter the start and end dates of the period.
5. In the **FEC report content composition** field, select one or more of the following output files to generate, and then select **Select**.

    | Name                   | Description | Conditions |
    |------------------------|-------------|------------|
    | FEC Main               | Main FEC file for the period specified | For this part of the report, set the **Period - date from** and **Period - date to** fields. In the **Period - date from** field, if you specify the beginning of the fiscal period, transactions of the **opening** type are included at the beginning of the FEC file. If the specified reporting period isn't a full fiscal year, the number of the period within the related fiscal year is appended to the file name (for example, **123456789FEC20131231\_01**). |
    | Customers balances     | Customer fiscal year opening balances annex | For this part of the report, set the **Period - date from** field. The report is generated for the beginning of the fiscal year as it's related to the date that is specified in the **Period - date from** field. Values in the **JournalCode**, **JournalLib**, **EcritureNum**, **PieceRef**, and **EcritureLib** columns of the report represent values that are collected from general ledger transactions of the **opening** type for the reporting fiscal year. |
    | Vendors balances       | Vendor fiscal year opening balances annex | For this part of the report, set the **Period - date from** field. The report is generated for the beginning of the fiscal year as it's related to the date that is specified in the **Period - date from** field. Values in the **JournalLib**, **EcritureNum**, **PieceRef**, and **EcritureLib** columns of the report represent the values that are collected from the general ledger transactions of the **opening** type for the reporting fiscal year. |
    | Customers transactions | Customer transactions annex for the specified period. | For this part of the report, set the **Period - date from** and **Period - date to** fields. |
    | Vendors transactions   | Vendor transactions annex for the specified period. | For this part of the report, set the **Period - date from** and **Period - date to** fields. |
    | FEC Main Extended      | FEC main file that includes fiscal year opening balance details for customers and vendors. | For this part of the report, set the **Period - date from** and **Period - date to** fields. Make sure that the specified period includes the beginning of a fiscal year. |

6. General ledger transactions that are included in the **FEC Main** and **FEC Main Extended** report types must be filtered by the **Current** posting layer. Only main accounts starting with **1**, **2**, **3**, **4**, **5**, **6**, or **7** must be included to the FEC. Use the **Records to include** field to filter for the records that the report should include. Use the filter to report data that complies with the rules in Livre des procédures fiscales, article A47 A-1, chapter VII: "Le numéro de compte, dont les trois premiers caractères doivent correspondre à des chiffres respectant les normes du plan comptable français."
7. To generate the report in batch mode, on **Run in the background** FastTab, specify the batch parameters.
8. When you've finished specifying all the parameters, select **OK** to generate the report.
