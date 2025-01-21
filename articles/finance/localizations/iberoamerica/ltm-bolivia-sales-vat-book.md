---
title: Configure for Sales Vat Books for Bolivia
description: This topic provides information about the required configuration for printing a Sales Vat Book for Bolivia. 
author: Fhernandez0088
ms.date: 01/17/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Configure for Sales Vat Books for Bolivia

This article describes how to set up and use Sales VAT tax books for Bolivia.

Value-added tax (VAT) books refer to the records and accounting documents that businesses use to keep track of their transactions for VAT purposes. Although the specific requirements for VAT books can vary from one country/region to another, they generally include the date of the transaction, the customer/vendor information, and the tax information details.

## Prerequisites

Before you complete the steps in this article to generate and print the report, the following prerequisites must be met:

- The legal entity's address must be in country/region Bolivia.
- The country/region-specific LATAM feature for Bolivia and the general LATAM feature must be enabled.
- You must download the relevant report from the Global repository (BO Sales VAT Book). For more information, see [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).
- You must configure the Electronic reporting (ER) parameters. For more information, see [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
-There must be a **Tax application** created to be used in this report. For more information, see [Configure Tax application for Latin America]( /ltm-core-tax-application.md).
-Configure the **Tax application** of **Document classes** used to annul posted fiscal documents with the **Tax application** created and complete the **Letter code** field with an “A”. For more information, see [Document classes for Latin America](https://learn.microsoft.com/dynamics365/finance/localizations/iberoamerica/ltm-core-document-class).

## Configure application-specific parameters

Lookups and conditions are designed so that you can select the combination of document classes IDs and sales tax codes that are used in transactions.

To configure application-specific parameters, follow these steps.

1. Open the **Electronic reporting** workspace and select **Reporting configurations**.
1. Select the **BO Sales VAT Book**, select the Action Pane, select the **Configurations** tab, in the **Application specific parameters** group select **Setup**.
1. On the **Application specific parameters** page, in the **Lookups** tab select **CustomerInvoicesIsApplicable**, select the **Conditions** tab, and select **Add**.
1. To add every document class that this report shows, in the **Lookup result** field, select **Yes**.
1. On the **Application specific parameters** page, in the **Lookups** tab. select **TaxType**. On the **Conditions** tab, select **Add**.
1. In the **Lookup result** field, select each tax type to be used in the report and in the **Tax type** column add the tax codes used in transactions.

   > [!NOTE]
   > VAT books are formats that depend on the LTM tax report model. Therefore, it's important that taxes are registered for transactions. The codes that you select here must match the codes that are registered in the transactions.

1. Repeat steps five and six for each report VAT column.

## Run BO Sales VAT Book format

To generate the **BO Sales VAT Book**, follow these steps.

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
1. In the **Format mapping** field, enter or select a value, and select **OK**.
1. Complete the **TAX application Id** field with the tax application code used in the document classes used for annual fiscal documents.
1. To  enter the date range to include in the report, select the **From date** and **To date**.
1. Select **OK**.
