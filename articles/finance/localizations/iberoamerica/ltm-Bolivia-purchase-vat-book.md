---
title: Configure printing for Purchase Vat Books for Bolivia
description: Learn about the required configuration for printing a Purchase Vat Book report for Bolivia. 
author: Fhernandez0088
ms.date: 01/27/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Configure printing for Purchase Vat Books for Bolivia

This article explains how to set up and use purchase VAT tax books for Bolivia.

Value-added tax (VAT) books refer to the records and accounting documents that businesses use to keep track of their transactions for VAT purposes. Although the specific requirements for VAT books can vary from one country/region to another, they generally include the date of the transaction, the customer/vendor information, and the tax information details.

## Prerequisites

Before you complete the steps in this article to generate and print the report, the following prerequisites must be met:

- The legal entity's address must be in Bolivia.
- Both the country/region-specific LATAM feature for Bolivia and the general LATAM feature must be enabled.
- You must download the relevant report (**BO Sales VAT Book**) from the Global repository. Learn more in [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).
- You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
- You must create a tax application to use on the report. Learn more in [Tax application for Latin America](../ltm-core-tax-application.md).
- Complete the tax application code field in the document classes used in this report with "DUI" or "DIM" when required as specified by the regulation.

## Configure application-specific parameters

Lookups and conditions are designed so that you can select the combination of document classes IDs and sales tax codes that are used in transactions.

To configure application-specific parameters, follow these steps.

1. Open the **Electronic reporting** workspace, and select **Reporting configurations**.
1. Select **BO Purchase VAT Book**, and then, on the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group select **Setup**.
1. On the **Application specific parameters** page, on the **Lookups** tab, select **VendorInvoicesIsApplicable**.
1. On the **Conditions** tab, select **Add**.
1. To add every document class that the report shows, in the **Lookup result** field, select **Yes**.
1. On the **Lookups** tab, select **TaxType**.
1. On the **Conditions** tab, select **Add**.
1. In the **Lookup result** field, select each tax type that should be used on the report.
1. In the **Tax type** column, add the tax codes that are used in transactions.

> [!NOTE]
> VAT books are formats that depend on the **LTM Tax Report** model. Therefore, it's important that taxes are registered for transactions. The codes that you select here must match the codes that are registered in the transactions. Complete each lookup with conditions **No** or **Not applicable** selecting **Blank** and **Not blank**.

> [!NOTE]
> This VAT book will only consider VAT, and not other type of taxes.

1. Repeat steps 6 through 9 for every other VAT column on the report.

## Run BO Purchase VAT Book format

To generate the **BO Purchase VAT Book** report, follow these steps.

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
1. In the **Format mapping** field, select **BO Purchase VAT Book**.
1. Select **OK**.
1. In the **TAX application Id** field, specify the tax application code created for this report.
1. In the **From date** and **To date** fields, specify the date range to include on the report.
1. Select **OK**.
