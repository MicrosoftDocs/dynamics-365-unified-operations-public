---
title: Configure Colombian sales VAT book printing
description: Learn how to configure the Colombian sales VAT book report for printing.
author: Fhernandez0088
ms.date: 04/14/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Configure Colombian sales VAT book printing

[!INCLUDE[banner](../../includes/banner.md)]

This article explains how to configure the Colombian sales value-added tax (VAT) book report so that it can be printed. The sales VAT book report is the record and accounting document that businesses use to keep a record of their sales transactions. Although the specific VAT ledger requirements might vary from one country/region to another, they typically include the transaction date, customer information, and tax information details.

## Prerequisites

Before you can generate and print the report, the following prerequisites must be met:

- The legal entity's address must be in a country/region that is within the LATAM localization (in this case, Colombia).
- Both the country/region-specific LATAM feature for Colombia and the general LATAM feature must be enabled.
- You must download the relevant report from the Dataverse repository. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).
- You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
- You must post sales invoices, credit notes, and debit notes.

## Set up application-specific parameters

Lookups and conditions are designed so that you can select the combination of document classification IDs and sales tax codes that is used in sales transactions.

To set up application-specific parameters, follow these steps.

1. Open the **Electronic Reporting** workspace, and select **Report Configurations**.
1. Select the **CO Ventas** format, and then, on the Action Pane, on the **Configuration** tab, in the **Application specific parameters** group, select **Setup**.
1. On the **Lookups** FastTab, in the **Name** column, select **Applicable Customer Invoices**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** column, specify whether the document is applicable.
1. In the **Document classification id** column, add the document classes that are included on this report as sales invoices.
1. On the **Lookups** FastTab, in the **Name** column, select **CustomerCreditNoteIsApplicable**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** column, specify whether the document is applicable.
1. In the **Document classification id** column, add the document classes that are included on this report as sales credit notes.
1. On the **Lookups** FastTab, in the **Name** column, select **TaxType**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** column, specify the tax type.
1. In the **Tax code** column, specify the tax code for each case.

> [!NOTE]
> The **CO Ventas** format depends on the **LTM Tax Report** model. Therefore, it's important that taxes are recorded for the transactions. The codes that you select here must match the codes that are recorded on the transactions. To ensure that the report shows the transactions that meet the configured conditions, complete the conditions with blank and non-blank conditions.

## Run the Columbian sales VAT book

To generate the sales VAT book report, follow these steps.

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
1. In the **Format mapping** field, select **CO Ventas**.
1. Select **OK**.
1. In the **From date** and **To date** fields, enter the date range to include on the report.
1. Select **OK**.

> [!NOTE]
> The **CO Ventas** format shows the transactions in the company currency.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
