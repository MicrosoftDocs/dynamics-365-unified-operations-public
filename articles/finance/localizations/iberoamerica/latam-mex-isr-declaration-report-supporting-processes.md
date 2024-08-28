---
title: ISR declaration report and supporting processes for Mexico
description: In Mexico, all individuals or corporations must file a monthly Impuesto sobre la renta (ISR) declaration report, with an outline on generating this report.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: conceptual
ms.custom: 
  - bap-template
ms.date: 07/11/2024
ms.reviewer: johnmichalak
ms.search.region: Mexico
ms.search.validFrom: 2016-02-28
ms.search.form: ISRConcept_MX, ISRConceptMainAccount_MX, ISRRateTable_MX
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: bcc395db-7c00-4151-9340-e83415cb0882
---

# ISR declaration report and supporting processes for Mexico

[!include [banner](../../includes/banner.md)]

In Mexico, all individuals or corporations must file a monthly Impuesto sobre la renta (ISR) declaration report. This article provides information about generating this report.

You must present the IRS declaration report for each month on or before the seventeenth day of the following month. The report displays detailed calculations of provisional income tax payments, and is based on the following factors:

-   ISR concept categories linked to one or more ledger accounts
-   ISR annual rate table
-   ISR utility ratio

For example, provisional ISR payments for January 2014 are paid and presented in February 2014, the payments for February are paid and presented in March, and so on. Taxpayers must use the calendar year to file income tax. At the end of the year, taxpayers must also present the annual declaration, which shows the final calculation of income tax.

## Prerequisites
Before you generate the ISR report, configure the concept category and define the ISR rates that should be applied in the report. The ISR report is based on general journal transactions.

### Concepts

You must create concepts to identify the different sections of the report, and then attach one or more main accounts for each concept. You can attach a range or specific main accounts, depending on the structure of your chart of accounts. When a main account is attached, you can select **Debits** to use the debit amount only, **Credit** to use the credit amount only, or **Both**. The ISR report shows the value, based on the concept that you configured. **Example**

| &nbsp;        | &nbsp;                                                   |
|---------------|----------------------------------------------------------|
| **Revenue**   | Main Accounts 4010001, 401002, 4010003, 4100001, 4100002 |
| **Inventory** | Main Accounts 1155001, 1155002, 1155003                  |

### ISR rate table

You can create or update the ISR rates that are used to calculate the provisional ISR payment amount. In general, this table is available on the government site. You identify the year and month, and then the minimum and maximum amounts, the fixed amount, and the ISR rate. In the ISR payment report, the rate percentage is used to multiply the derived value after the minimum amount is deducted from the resulting fiscal amount. **Example**

| Minimum amount | Maximum amount | Fixed amount | Rate percentage to apply over the minimum amount |
|----------------|----------------|--------------|--------------------------------------------------|
| 0.00           | 496.07         | 0.00         | 1.92                                             |
| 496.08         | 4,210.41       | 9.52         | 6.4                                              |
| 4,210.42       | 7,399.42       | 247.23       | 10.88                                            |
| 7,399.43       | 8,601.50       | 594.24       | 16                                               |
| 8,601.51       | 10,298.35      | 786.55       | 17.92                                            |

If the fiscal utility amount that is obtained during the calculation process is between 7,399.43 and 8,601.50, the rate that must be applied is 16 percent.

## Generating the provisional ISR payment report
You can generate a detailed ISR report, or the report can summarize each main account that has the debit and credit indicators. To generate the report, click **Tax** &gt; **Declarations** &gt; **Sales tax** &gt; **ISR reports**. When you generate the ISR report, you must specify information in the following fields:

-   **Month** and **Year**
-   **Utility ratio**: Enter the value to use as part of the ISR tax calculation for the period. In the ISR report, this ratio will be multiplied by the value of the **Revenue category** concept.
-   **Type of report**: Select one of the following values:
    -   **Details**: The values are grouped by concept category and the main accounts that are linked to each category. Each record on the report shows the main account, the account name of the main account, voucher numbers, the period that the report is generated for, the posting type of the transactions, and the value of the transactions. The report also indicates whether the transactions are debits or credits. All the amount fields on the report are shown in the company currency
    -   **Summary**: The values are grouped by concept category, and the aggregate value of each concept category is calculated. This report shows the minimum amount, the fixed amount, the utility ratio, and the ISR rates. All the amount fields on the report are shown in the company currency.






[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
