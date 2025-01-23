---
title: Configure printing for Sales Vat Books for Bolivia
description: Learn about the required configuration for printing a Sales Vat Book report for Bolivia.
author: Fhernandez0088
ms.date: 01/17/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Configure printing for Sales Vat Books for Bolivia

This article explains how to set up and use sales VAT tax books for Bolivia.

Value-added tax (VAT) books refer to the records and accounting documents that businesses use to keep track of their transactions for VAT purposes. Although the specific requirements for VAT books can vary from one country/region to another, they generally include the date of the transaction, customer/vendor information, and tax information details.

## Prerequisites

Before you can generate and print the report, the following prerequisites must be met:

- The legal entity's address must be in Bolivia.
- Both the country/region-specific LATAM feature for Bolivia and the general LATAM feature must be enabled.
- You must download the relevant report (**BO Sales VAT Book**) from the Global repository. Learn more in [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).
- You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
- You must create a tax application to use on the report. Learn more in [Tax application for Latin America](../ltm-core-tax-application.md).
- You must configure the tax application of document classes that are used to annul posted fiscal documents by using the tax application that you created. Set the **Letter code** field to **A**. Learn more in [Document classes for Latin America](ltm-core-document-class.md).

## Configure application-specific parameters

Lookups and conditions are designed so that you can select the combination of document classes IDs and sales tax codes that is used in transactions.

To configure application-specific parameters, follow these steps.

1. Open the **Electronic reporting** workspace, and select **Reporting configurations**.
1. Select **BO Sales VAT Book**, and then, on the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group select **Setup**.
1. On the **Application specific parameters** page, on the **Lookups** tab, select **CustomerInvoicesIsApplicable**.
1. On the **Conditions** tab, select **Add**.
1. To add every document class that the report shows, in the **Lookup result** field, select **Yes**.
1. On the **Lookups** tab, select **TaxType**.
1. On the **Conditions** tab, select **Add**.
1. In the **Lookup result** field, select each tax type that should be used on the report.
1. In the **Tax type** column, add the tax codes that are used in transactions.

    > [!NOTE]
    > VAT books are formats that depend on the **LTM Tax Report** model. Therefore, it's important that taxes are registered for transactions. The codes that you select here must match the codes that are registered in the transactions.

1. Repeat steps 6 through 9 for every other VAT column on the report.

## Run the BO Sales VAT Book format

To generate the **BO Sales VAT Book** report, follow these steps.

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
1. In the **Format mapping** field, enter or select a value.
1. Select **OK**.
1. In the **TAX application Id** field, specify the tax application code that is used in the document classes that are used to annual fiscal documents.
1. In the **From date** and **To date** fields, specify the date range to include on the report.
1. Select **OK**.
