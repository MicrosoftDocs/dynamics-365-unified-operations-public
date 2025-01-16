---
title: Configure Ecuadorian sales VAT book printing
description: Learn how to configure the Ecuadorian sales VAT book report for printing.
author: Fhernandez0088
ms.date: 12/30/2024
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Configure Ecuadorian sales VAT book printing
	
[!INCLUDE[banner](../../includes/banner.md)]

This article explains how to configure the Ecuadorian sales value-added tax (VAT) book report so that it can be printed. The sales VAT book report is the record and accounting document that businesses use to keep a record of their sales transactions. Although the specific VAT ledger requirements might vary from one country/region to another, they typically include the transaction date, customer information, and tax information details.

## Prerequisites

Before you can generate and print the report, the following prerequisites must be met:

- The legal entity's address must be in a country/region that is within the LATAM localization (in this case, Ecuador).
- Both the country/region-specific LATAM feature and the general LATAM feature must be enabled.
- You must download the relevant report from the Global repository. Learn more in [Download ER configurations from the Global repository of Configuration service](/dynamics365/fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo?context=%2Fdynamics365%2Fcontext%2Ffinance).
- You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
- You must post sales invoices.
* You must configure the **Tax applications** of the **Sales points** used in transactions with an **F** for physical documents and **E** for electronic documents. See [Tax application for Latin America](https://learn.microsoft.com/dynamics365/finance/localizations/iberoamerica/ltm-core-tax-application) and [Sales point prefixes for Latin America](https://learn.microsoft.com/dynamics365/finance/localizations/iberoamerica/ltm-core-sales-point-prefixes) articles.

## Set up application-specific parameters

Lookups and conditions are designed so that you can select the combination of document classification IDs and sales tax codes that is used in sales transactions. In this case lookups and conditions for the Ecaudor ATS will be shown.

To set up application-specific parameters, follow these steps.

1. Open the **Electronic Reporting** workspace, and select **Report Configurations**.
1. Select the **EC sales vat book** format and then, on the Action Pane, on the **Configuration** tab, in the **Application specific parameters** group, select **Setup**.
1. On the **Lookups** FastTab, in the **Name** column, select **IsApplicable** to configure this lookup for the document class that is required for the sales transactions.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** column, specify whether the document is applicable.
1. In the **Document classification id** column, specify the document class that applies.
1. On the **Lookups** FastTab, in the **Name** column, select **Ret** to configure this lookup for withholdings that are applied to sales transactions.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** column, specify the type of withholding.
1. In the **Document classification id** column, specify the docuement class that applies to each withholding.
1. On the **Lookups** FastTab, in the **Name** column, select **TaxType** to configure this lookup for the taxes that are involved in sales transactions in Ecuador.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** column, specify the tax type.
1. In the **Tax code** column, specify the tax code for each case.

> [!NOTE]
> **EC sales vat book** is a format that depends on the **LTM Tax Report** model. Therefore, it's important that taxes are recorded for the transactions. The codes that you select here must match the codes that are recorded on the transactions. To ensure that the report shows the transactions that meet the configured conditions, complete the conditions with blank and non-blank conditions.

## Run the Euador sales VAT book

To generate the sales VAT book report, follow these steps.

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
1. In the **Format mapping** field, select **EC sales vat book**.
1. Select **OK**.
1. Complete the **Tax application id** field with the **Tax application** code created for this report.
1. In the **From date** and **To date** fields, enter the date range to include on the report.
1. Select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
