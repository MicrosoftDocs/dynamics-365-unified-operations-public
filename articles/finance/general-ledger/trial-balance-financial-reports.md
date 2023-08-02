---
# required metadata

title: Trial balance financial reports
description: This article describes the default reports for trial balances. It also describes the building blocks that are associated with these reports and how you can modify the reports to fit your business requirements. 
author: jinniew
ms.date: 05/26/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LedgerTrialBalanceListPage 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.assetid: 3b77d6f3-fd07-41a7-9ddb-1b22d1ae33fc
ms.search.region: Global
# ms.search.industry: 
ms.author: jiwo
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Trial balance financial reports

[!include [banner](../includes/banner.md)]

This article describes the default reports for trial balances. It also describes the building blocks that are associated with these reports and how you can modify the reports to fit your business requirements. 

## Default trial balance reports

Three trial balance reports are available in Financial reporting.

| Default report                                 | What it does                                                                            |
|------------------------------------------------|--------------------------------------------------------------------------------------|
| Detailed Trial Balance - Default               | Provides balance information for all accounts, and includes debit and credit balances, and the net of these, together with the transaction date, voucher, and journal description.                  |
| Summary Trial Balance – Default                | Provides balance information for all accounts, and includes opening and closing balances, and debit and credit balances, together with their net difference.                                        |
| Summary Trial Balance Year Over Year – Default | Provides balance information for all accounts, and includes opening and closing balances, and debit and credit balances, together with their net difference for the current year and the past year. |

## Building blocks
The trial balance financial reports use the following building blocks.

| Default report                                 | Row definition          | Column definition                              |
|------------------------------------------------|-------------------------|------------------------------------------------|
| Detailed Trial Balance - Default               | Trial Balance - Default | Detailed Trial Balance - Default               |
| Summary Trial Balance – Default                | Trial Balance - Default | Summary Trial Balance - Default                |
| Summary Trial Balance Year Over Year – Default | Trial Balance - Default | Summary Trial Balance Year Over Year - Default |

> [!NOTE] 
> When running the **Trial Balance** report in Financial reporting, be sure to select the check boxes for **Display rows with no amounts** and **Display reports with no active rows** on the **Settings** tab.

### Row definition

The row definition, Trial Balance – Default, contains a single row that pulls in all main accounts. Therefore, anyone can generate the report without having to make any modifications. When you view the report, you drill into the single row to see details about each account. You can modify the row definition so that it includes more detail. To modify the Trial Balance – Default row definition so that it includes rows for all accounts, follow these steps.

1.  Click **Edit**, and then click **Insert rows from dimensions**. The **Insert rows from dimensions** command lets you choose the dimensions that you want to have in your row definition. For this row definition, you're going to use **Main account**.
2.  Make sure that **Main account** contains all ampersands (&), and then click **OK**.

The row definition now contains all the main accounts for your default legal entity.

### Column definition

Each trial balance report uses a different column definition. These column definitions contain different types of columns to provide different levels of detail and financial data.

-   **Detailed Trial Balance – Default column types:**
    -   **DESC** – The description from the row definition
    -   **ACCT** – Account codes
    -   **ATTR (3)** – Attributes:
        -   Transaction Date
        -   Voucher
        -   Journal Description
    -   **FD** – Financial data that contains only debits
    -   **FD** – Financial data that contains only credits
    -   **CALC** – The net difference
-   **Summary Trial Balance – Default columns types:**
    -   **ACCT** – Account codes
    -   **DESC** – The description from the row definition
    -   **ATTR** – An attribute:
        -   Voucher
    -   **FD** – The beginning balance financial data
    -   **FD** – Financial data that contains only debits
    -   **FD** – Financial data that contains only credits
    -   **CALC** – The net difference
    -   **CALC** – The closing balance
-   **Summary Trial Balance Year Over Year – Default:**
    -   **ACCT** – Account codes
    -   **DESC** – The description from the row definition
    -   **ATTR** – An attribute
        -   Voucher
    -   **FD** – The beginning balance financial data for the current year
    -   **FD** – Financial data that contains only debits for the current year
    -   **FD** – Financial data that contains only credits for the current year
    -   **CALC** – The net difference
    -   **CALC** – The closing balance
    -   **FD** – Financial data that contains only debits for the last year
    -   **FD** – Financial data that contains only credits for the last year

## Additional resources

[Financial reporting overview](financial-reporting-getting-started.md)

[View financial reports](view-financial-reports.md)

[Dynamics Financial Reporting Blog](https://blogs.msdn.com/b/dynamics_financial_reporting/)





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
