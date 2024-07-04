---
title: Trial balance financial reports
description: Learn about the default reports for trial balances, including an outline on building blocks that are associated with these reports.
author: jinniew
ms.author: jiwo
ms.topic: article
ms.date: 06/16/2024
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: LedgerTrialBalanceListPage
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 3b77d6f3-fd07-41a7-9ddb-1b22d1ae33fc
---

# Trial balance financial reports

[!include [banner](../includes/banner.md)]

This article describes the default reports for trial balances. It also describes the building blocks that are associated with these reports and how you can modify the reports to fit your business requirements. 

## Default trial balance reports

Three trial balance reports are available in Financial reporting.

| Default report                                 | What it does                                                                            |
|------------------------------------------------|--------------------------------------------------------------------------------------|
| Detailed trial balance - default               | Provides balance information for all accounts, and includes debit and credit balances, and the net of these, together with the transaction date, voucher, and journal description.                  |
| Summary trial balance – default                | Provides balance information for all accounts, and includes opening and closing balances, and debit and credit balances, together with their net difference.  |
| Summary trial balance year over year – default | Provides balance information for all accounts, and includes opening and closing balances, and debit and credit balances, together with their net difference for the current year and the past year. |

## Building blocks
The trial balance financial reports use the following building blocks.

| Default report                                 | Row definition          | Column definition                              |
|------------------------------------------------|-------------------------|------------------------------------------------|
| Detailed trial balance - default               | Trial balance - default | Detailed trial balance - default               |
| Summary trial balance – default                | Trial balance - default | Summary trial balance - default                |
| Summary trial balance year over year – default | Trial balance - default | Summary trial balance year over year - default |

> [!NOTE] 
> When running the **Trial balance** report in Financial reporting, be sure to select the checkboxes for **Display rows with no amounts** and **Display reports with no active rows** on the **Settings** tab.

### Row definition

The row definition, Trial balance – default, contains a single row that pulls in all main accounts. Therefore, anyone can generate the report without having to make any modifications. When you view the report, you drill into the single row to see details about each account. You can modify the row definition so that it includes more detail. To modify the Trial balance – default row definition so that it includes rows for all accounts, follow these steps.

1.  Click **Edit**, and then click **Insert rows from dimensions**. The **Insert rows from dimensions** command lets you choose the dimensions that you want to have in your row definition. For this row definition, you're going to use **Main account**.
2.  Make sure that **Main account** contains all ampersands (&), and then click **OK**.

The row definition now contains all the main accounts for your default legal entity.

### Column definition

Each trial balance report uses a different column definition. These column definitions contain different types of columns to provide different levels of detail and financial data.

-   **Detailed trial balance – default column types:**
    -   **DESC** – The description from the row definition
    -   **ACCT** – Account codes
    -   **ATTR (3)** – Attributes:
        -   Transaction date
        -   Voucher
        -   Journal description
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

[Dynamics financial reporting blog](https://blogs.msdn.com/b/dynamics_financial_reporting/)





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
