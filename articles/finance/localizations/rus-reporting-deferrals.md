---
# required metadata
title: Reporting for deferrals (Russia)
description: This topic provides information about the various reports that are available for deferrals.
author: anasyash
ms.date: 06/28/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata
ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: anasyash
ms.search.validFrom: 2019-06-28
ms.dyn365.ops.version: 10.0.1

---

# Reporting for deferrals (Russia)

[!include [banner](../includes/banner.md)]

## Deferrals listing report

The **Deferrals listing** report shows a list of deferrals together with their current status, such as **Scheduled**, **In process**, or **Closed**. For each deferral, the report also shows the initial amount and the remaining amount. Accountants generate and print this report to analyze the value of current deferral charges.

1. Go to **General ledger** \> **Inquiries and reports** \> **Deferrals** \> **Deferrals listing**.
2. Use the following default parameters in the **Deferrals listing** dialog box to filter the data that appears on the report.

    | Field                                                 | Description |
    |-------------------------------------------------------|-------------|
    | Model number                                          | Select the deferral model number. |
    | Reporting date                                        | Select the date to generate the report for. |
    | Exclude zero turnovers                                | Set this option to **Yes** if deferrals that have a net book value of 0 (zero) should be excluded from the report. |
    | Deferral ID (on the **Records to include** FastTab)   | The deferral code that is included on the report. |
    | Date attached (on the **Records to include** FastTab) | The deferral creation date that is included on the report. |

## Deferrals transaction listing report

The **Deferrals transaction listing** report shows the deferrals transactions for a deferral model. The deferrals transactions are categorized by deferrals group. For each deferrals transaction, the report includes details such as the date, type, description, and amount of the transaction. It also includes the name of the deferral, the status, the initial amount, and the depreciated amount. Accountants periodically generate this report to view a list of the deferrals transactions.

1. Go to **General ledger** \> **Inquires and reports** \> **Deferrals** \> **Deferrals transaction listing**.
2. Use the following default parameters in the **Deferrals transaction listing** dialog box to filter the data that appears on the report.

    | Field                                                     | Description |
    |-----------------------------------------------------------|-------------|
    | Model number                                              | Select the deferral model number. |
    | Reporting date                                            | Select the date to generate the report for. |
    | Exclude zero turnovers                                    | Set this option to **Yes** if deferrals that have a net book value of 0 (zero) should be excluded from the report. |
    | Transaction date (on the **Records to include** Fast Tab) | The date when the transaction is posted. |
    | Deferral ID (on the **Records to include** Fast Tab)      | The identification code of the deferral. |
    | Date attached (on the **Records to include** Fast Tab)    | The date when the deferral is created. |
    | Expense code (on the **Records to include** Fast Tab)     | The expense code of the deferrals. |

## Deferrals balances report

The **Deferrals balances** report shows deferral values such as initial amounts, written-off sums, and retirement deferral amounts. Accountants periodically generate this report to analyze the remaining balance of deferrals for the current period and for future costs.

1. Go to **General ledger** \> **Inquires and reports** \> **Deferrals** \> **Deferrals balances**.
2. Use the following default parameters in the **Deferrals balances** dialog box to filter the data that appears on the report.

    | Field                                                | Description |
    |------------------------------------------------------|-------------|
    | Model number                                         | Select the model number for which the deferrals balance information is included on the report. |
    | Reporting date                                       | Enter the date for which the deferrals balance information is included on the report. |
    | Exclude zero turnovers                               | Set this option to **Yes** if deferrals that have a net book value of 0 (zero) should be excluded from the report. |
    | Deferral ID (on the **Records to include** Fast Tab) | The identification code for the deferral. |

## Factor for deferrals writing off report

The **Factors for deferrals writing off** report shows a list of deferral factors. The deferral factors are grouped by the start date of the period that the report is generated for. The data on this report might include the expense code, the coefficient of the factor, normalized amounts, and base amounts. Accountants generate this report to view a list of deferral factors to calculate depreciation.

1. Go to **General ledger** \> **Inquires and reports** \> **Deferrals** \> **Factors for deferrals writing off**.
2. Use the following default parameters in the **Factors for deferrals writing off** dialog box to filter the data that appears on the report.

    | Field                                                    | Description |
    |----------------------------------------------------------|-------------|
    | Start date (on the **Records to include** Fast Tab)      | The start date of the period that the report is generated for. |
    | Deferrals group (on the **Records to include** Fast Tab) | The identification code of the deferrals group for which the deferral factors are included on the report. |
    | Expense code (on the **Records to include** Fast Tab)    | The expense code of the deferral factors that are included on the report. |


[!INCLUDE[footer-include](../../includes/footer-banner.md)]