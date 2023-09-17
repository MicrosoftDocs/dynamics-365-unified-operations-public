---
title: Withholding tax for Italy
description: This article explains how to configure up Italy-specific settings for withholding tax and Italian withholding tax reports.
author: AdamTrukawka
ms.date: 04/10/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Italy
ms.author: atrukawk
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611
ms.custom: 272733
ms.assetid: a5628f89-2ebb-4df2-a8a5-522649fb66da
---

# Withholding tax for Italy

[!include [banner](../includes/banner.md)]

This article explains how to configure up Italy-specific settings for withholding tax and Italian withholding tax reports.

For Italy, there is a country/region-specific legal requirement that a buyer withhold a tax amount from some types of vendor payments, such as payments to self-employed vendors. The company must then remit the tax to the tax authority. Withholding tax is a tax that is withheld from the payment amount for vendor invoices. This article describes Italy-specific settings for withholding tax and the following Italian reports: **Withholding tax - certification**, **Withholding tax - monthly**, and **Withholding tax - yearly**. Set up withholding tax codes at **Tax** &gt; **Indirect taxes** &gt; **Withholding tax** &gt; **Withholding tax codes**. Define standard settings on the **General** and **Calculation** FastTabs. On the **Italian reporting** FastTab, define the following settings.

|Field group|Field|Description|
|------------|----------------|----------------|
|Entry type   |Withholding tax reason code|Select the reference that is used when a payment is made to the tax authorities.|
|Entry type   |Source|Specify whether to summarize the posted tax by source (source withholding tax or withholding tax in advance). This field is used on the **Withholding tax - certification** and **Withholding tax - yearly** reports.|
|Entry type   |May be reported by recipient|Specify whether to summarize the posted tax by recipient (the recipient can or can't report income). This field is used on the **Withholding tax - certification** and **Withholding tax - yearly** reports.|
|Yearly declaration (770)|Service type|Enter the code for the service type. The code is used as a classification on the yearly tax declaration.|
|Yearly declaration (770)|770 form|Enter the code for the section of the yearly tax declaration that the tax must be included in.|

On the **Action Pane**, click **Values**, and set up values for the withholding tax code.

| Field            | Description                                                                                  |
|------------------|----------------------------------------------------------------------------------------------|
| From date        | Enter the first date that the withholding tax value percentage is valid.                     |
| To date          | Enter the last date that the withholding tax value percentage is valid.                      |
| Minimum limit    | Enter the minimum base for the calculation of the withholding tax.                           |
| Maximum limit    | Enter the maximum base for the calculation of the withholding tax.                           |
| Value            | Enter the withholding tax percentage value.                                                  |
| Non deductible % | Enter the percentage to reduce the amount base by before calculation of the withholding tax. |

On the Action Pane, click **Limits**, and set up limits for the withholding tax amount.

| Field                   | Description                                                                                                            |
|-------------------------|------------------------------------------------------------------------------------------------------------------------|
| From date               | Enter the first date that the withholding tax limits apply. The posting date determines which limit interval is used.  |
| To date                 | Enter the last date that the withholding tax limits apply. The posting date determines which limit interval is used.   |
| Minimum withholding tax | Enter the minimum withholding tax amount that can be posted for any transaction for the selected withholding tax code. |
| Maximum withholding tax | Enter the maximum withholding tax amount that can be posted for any transaction for the selected withholding tax code. |

Set up withholding tax groups at **Tax** &gt; **Indirect taxes** &gt; **Withholding tax** &gt; **Withholding tax groups**. Define the code and name for a withholding tax group, and assign a withholding tax code to the group. Find more information, see [Set up withholding tax](../general-ledger/tasks/set-up-withholding-tax.md). Set up a vendor account for the calculation of withholding tax at **Accounts payable** &gt; **Vendors** &gt; **All vendors**. Define the following settings.


|         FastTab         |              Field               |                                Description                                |
|-------------------------|----------------------------------|---------------------------------------------------------------------------|
|  Invoice and delivery   |    Calculate withholding tax     |   Set this option to <strong>Yes</strong> to calculate withholding tax.   |
|  Invoice and delivery   |        Withholding tax g         |                           Withholding tax group                           |
|  Invoice and delivery   |           Fiscal code            |                          Enter the fiscal code.                           |
| Purchasing demographics | Residence foreign country/region |                        Select the country/region.                         |
| Purchasing demographics |           Birth place            |                         Enter the place of birth.                         |
|         General         |   Birthday - Day, Month, Year    | Enter the date of birth for a vendor of the <strong>Person</strong> type. |

To run the Italy-specific reports about withholding tax, go to **Tax** &gt; **Inquiries and reports** &gt; **Withholding tax reports**:

-   **Withholding tax - certification** - This report is used to print an Italian certification report in the withholding tax currency. The report is intended to be sent to the vendor. It includes withholding tax data for the specified period. The report certifies to the vendor that tax amounts were withheld during the report period.
-   **Withholding tax - monthly** - This report is used to print, for each vendor account, details of the withholding tax amounts for all invoices that were paid during a month: the withholding tax reason code, total amount, base excluded amount, not taxable amount by treaty, not taxable amount, taxable base, and withholding tax amount. If the user selects to print details in the dialog box, the report shows amount details by document date and invoice number.
-   **Withholding tax - yearly** - This report is used to print, for each vendor account, the resulting withholding tax amounts. These amounts are grouped by withholding tax code and details are included by invoice. Depending on the **Source** and **May be reported by recipient** settings on the withholding tax code, the report also shows total amounts: total amounts that the recipient can or can't report, and total amounts of source withholding tax or withholding tax in advance.







[!INCLUDE[footer-include](../../includes/footer-banner.md)]
