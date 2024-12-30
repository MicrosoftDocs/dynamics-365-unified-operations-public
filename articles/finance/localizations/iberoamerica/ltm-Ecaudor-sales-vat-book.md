---
title: Configure Ecuador sales VAT book printing
description: The article describes how to set up, use and print the Ecuador Sales VAT book report.
author: Fhernandez0088
ms.date: 12/30/2024
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Configure Ecuador Sales VAT book printing

[!INCLUDE[banner](../../includes/banner.md)]

The article describes how to create and use sales VAT books for Ecuador. The value added tax (VAT) sales report is the record and accounting document used by businesses to keep a record of their sales transactions. Although specific VAT ledger requirements may vary from country/region to country/region, they generally include transaction date, customer information, and tax information details.

## Prerequisites

To print the report, the following prerequisites must be met: 

- Be a legal entity domiciled in a country within the LATAM localization, Ecuador in this case.
- Have both the LATAM country specific function and the general function activated.
- Download the specific report from the global repository. For more information, see [ER download reports](/dynamics365/fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo?context=%2Fdynamics365%2Fcontext%2Ffinance).
- Configure the ER parameters. For more information, see [ER configuration](/dynamics365/fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters).
- You must have sales invoices posted.

## Set up application-specific parameters

Searches and conditions are designed to allow you to select the combination of document classification IDs and sales tax codes that are used in sales transactions. Depending on the country/region for which you want to set up the report, the applicable conditions will be displayed.

To set up application-specific parameters, follow these steps.

1. Open the **Electronic Reporting** work area and select **Report Configurations**.
1. Select the Sales VAT ledger format for Ecuador, and then select **setup** in the **Actions** pane, on the **Configuration** tab, in the **Application-specific parameters** group.
1. Under **Lookup** in the **Name** column, configure **IsApplicable** for the document class required for the sales, the **TaxType** for the taxes involved in sales transactions in Ecuador and, the **Ret** for withholdings applied to sales.
1. On the Quick **Conditions** tab, select **Add** to add conditions to the lookup name we have previously selected.
1. For the lookup name **Isapplicable**, in the **lookup result** field, select **add**, in the lookup result column, indicate whether the document is applicable or not, then in the **Document classification id** column indicates the document class that applies.
1. For the lookup name **Ret**, in the **lookup result** field, select **add**, in the lookup result column, indicate the type of withholding, then in the **Document classification id** column indicate the type of voucher that applies for each withholding.
1. For the lookup name **Taxtype**, in the Search result field, select **add**.in the **lookup result** column indicate the tax type, then in the **Tax code** column, indicate the tax code in each case.

> [!NOTE]
> VAT books are formats that depend on the LTM tax report template. Therefore, it is important that taxes are recorded for the transactions. The codes you select here must match the codes recorded on the transactions.
To ensure that the report shows the transactions that meet the configured conditions, complete the conditions field with blank and non-blank conditions.

## Run VAT books

To run VAT books, follow these steps.

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
1. In the **Format mapping** field, select **EC sales vat book** value.
1. Select **OK**.
1. In the **From** date field, enter a date.
1. In the **To** date field, enter a date.
1. Select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
