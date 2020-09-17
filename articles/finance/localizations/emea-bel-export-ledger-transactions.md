---
# required metadata

title: Export ledger transactions
description: This topic provides information about how to export ledger account balances to a plain text (ASCII) file in .CED format for Belgium.
author: anasyash
manager: AnnBe
ms.date: 09/17/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: TaxReportExtraFieldsBE
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 273103
ms.search.region: Belgium
# ms.search.industry: 
ms.author: shylaw
ms.dyn365.ops.version: AX 7.0.1
ms.search.validFrom: 2016-05-31

---

# Export ledger transactions

[!include [banner](../includes/banner.md)]

The feature described in this topic is used to export the total balance of each ledger account for a specific period to a plain text (ASCII) file in .CED format. You can then import the generated file into third-party software to create an accounting report according to country/region-specific requirements.

This functionality is available for legal entities that have their primary address in Belgium.

## Prerequisites

### Create posting journals

1. Go to **General ledger** \> **Journal setup** \> **Posting journals**.
2. On the **Journal setup** page, select **Create**. Posting journals and corresponding number sequences are automatically created.

## Export ledger transactions to a plain text file in CED format

1. In [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/V2), in the Shared asset library, download the latest versions of the Electronic reporting (ER) configurations for the following report format:

    - Ledger transaction export format (BE)

    For more information, see [Download Electronic reporting configurations from Lifecycle Services](https://docs.microsoft.com/dynamics365/dev-itpro/analytics/download-electronic-reporting-configuration-lcs).

2. In Dynamics 365 Finance, go to **General ledger** \> **Periodic tasks** \> **Export ledger transactions**.
3. In the **Export ledger transactions to an ASCII file in CED format** dialog box, in the **Format mapping** field, select the **Ledger transaction export format (BE)** format that you just downloaded, and then select **OK**.
4. In the **Electronic report parameters** dialog box, set the following fields.

| **Field**          | **Description**                                                             |
|--------------------|-----------------------------------------------------------------------------|
| From date          | Enter the first day of the reporting period.                                |
| To date            | Enter the last day of the reporting period.                                 |
| Reporting in euros | Set this option to **Yes** if the company uses a currency other than euros. |

5. Select **OK** to generate and download the .txt file.

    For example, you post the following ledger transactions in the DEMF company.

| **Date**        | **Transaction type** | **Main account**          | **Offset account**        | **Amount net** | **VAT amount** | **Sales tax code** |
|-----------------|----------------------|---------------------------|---------------------------|----------------|----------------|--------------------|
| January 1, 2020 | Customer invoice     | 110110 – Bank account USD |                           | 1,000          | 190            | VAT19              |
| January 1, 2020 | Vendor invoice       |                           | 110120 – Bank account CNY | 1,095          | 76.65          | EU7                |
| January 1, 2020 | Customer invoice     | 110115 – Bank account CAD |                           | 800            | 0              | EUS                |

In this case, the file that is generated contains the following data.

![Ledger transactions data](media/1_Export_ledger_transactions.png)

Here is an explanation of the columns in this file:

- The first column shows the ledger account code.
- The second column shows the debit balance on the ledger account.
- The third column shows the credit balance on the ledger account.
- The fourth column shows the name of the ledger account.

> [!NOTE]
> To post ledger transactions for customer invoices, go to **Accounts receivable** \> **Invoices** \> **All free text invoices**. For vendor invoices, go to **Accounts payable** \> **Invoices** \> **Invoice journal**.
