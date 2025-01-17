---
title: Printing configuration for Sales Vat Book Bolivia
description: This topic provides information about the required configuration for printing a Sales Vat Book for Bolivia. 
author: Fhernandez0088
ms.date: 01/17/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Printing configuration for Sales Vat Book Bolivia

This article describes how to set up and use Sales VAT tax books for Bolivia.

Value-added tax (VAT) books refer to the records and accounting documents that businesses use to keep track of their transactions for VAT purposes. Although the specific requirements for VAT books can vary from one country/region to another, they generally include the date of the transaction, the customer/vendor information, and the tax information details.

## Prerequisites

Before you complete the steps in this article to generate and print the report, the following prerequisites must be met:

- The legal entity's address must be in country/region Bolivia.
- The country/region-specific LATAM feature for Bolivia and the general LATAM feature must be enabled.
- You must download the relevant report from the Global repository (BO Sales VAT Book). Learn more in [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).
- You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

-There must be a **Tax application** created to be used in this report, see [Configure Tax application for Latin America]( /ltm-core-tax-application.md).
-Configure the **Tax application** of **Document classes** used to annul posted fiscal documents with the **Tax application** created and complete the **Letter code** field with an “A”. Learn more in [Document classes for Latin America](https://learn.microsoft.com/dynamics365/finance/localizations/iberoamerica/ltm-core-document-class).

## Configure application-specific parameters

Lookups and conditions are designed so that you can select the combination of document classes IDs and sales tax codes that are used in transactions.

1. Open the **Electronic reporting** workspace and select **Reporting configurations**.
2. Select the BO Sales VAT Book, and then, on the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
3. On the **Application specific parameters** page, in the **Lookups** tab select **CustomerInvoicesIsApplicable** and on the **Conditions** tab, select **Add**.
4. In the **Lookup result** field, select **Yes** to add every Document class that this report will show.
5. On the **Application specific parameters** page, in the **Lookups** tab select **TaxType** and on the **Conditions** tab, select **Add**.
6. In the **Lookup result** field, select each tax type to be used in the report and in the **Tax type** column add the tax codes used in transactions.

> [!NOTE]
> VAT books are formats that depend on the LTM tax report model. Therefore, it's important that taxes are registered for transactions. The codes that you select here must match the codes that are registered in the transactions.

7. Repeat steps 5 and 6 for each report VAT column.

## Run BO Sales VAT Book format

Follow these steps to generate the **BO Sales VAT Book**.

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
2. In the **Format mapping** field, enter or select a value. Then select **OK**.
3. Complete the **TAX application Id** field with the tax application code used in the document classes used to annul fiscal documents.
4. In the **From date** and **To date** fields, enter the date range to include in the report.
5. Select **OK**.
