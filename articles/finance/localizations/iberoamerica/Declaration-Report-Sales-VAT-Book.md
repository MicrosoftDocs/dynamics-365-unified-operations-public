---
title: Configure printing for the Declaration Reports Sales VAT Book for Venezuela
description: Learn how to configure printing for the Declaration Reports Sales VAT Book for Venezuela.
author: Cpicon85
ms.date: 05/26/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-cpicon
---

# Configure printing for the Declaration Reports Sales VAT Book for Venezuela

[!INCLUDE[banner](../../includes/banner.md)]

This article explains how to set up and generate the Declaration Reports Sales VAT Book for Venezuela.

The sales VAT book report is the record and accounting document that businesses use to keep a record of their sales transactions. The information on it includes the transaction date, customer information, and tax information details.

## Prerequisites

Before you can generate and print the report, the following prerequisites must be met:

- The legal entity's address must be in Venezuela.
- You must enable both the general Latin American (LATAM) feature and the country/region-specific LATAM feature for Venezuela.
- You must download the specific report configuration from the Microsoft Dataverse configuration repository. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

    You must download the following reports:

    - LTM Tax Report
    - LTM Tax Report mapping
    - Tax report- declaration Sales VAT Venezuela

- You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Additional configuration required for the Declaration Reports Sales VAT Book

- You must create a **tax application code** to use on the report. Learn more in [Tax application for Latin America](ltm-core-tax-application.md).
- You must configure the **tax application code** of each **sales point** that is used in transactions with **Manual**. You must configure the **User-defined field 1 code** with **MANUAL**.
- You must configure the **tax application code** of each **document class type** that is used in transactions with **01 Registro** (Register) for invoices and export invoices, or **02 Complemento** (Complement) for credit and debit notes.
- You must configure the **tax application code** of each **document class** that is used in transactions with **FC** for invoices, **NC** for credit notes, **ND** for debit notes, or **EX** for export invoices.
- As required, you can associate debit notes and credit notes with invoices through a source document. Go to **Accounts payable** \> **Inquiries and reports** \> **Invoice** \> **Invoice journal**. On the FastTab for the desired transaction, select **LATAM** \> **Source Documents**. Then select **New**, and add the required record.

## Configure application-specific parameters

To configure application-specific parameters, follow these steps.

1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**, and select **Reporting configurations**.
1. In the **LTM Tax Report** group, select the **Tax report- declaration Sales VAT Venezuela** format.
1. On the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
1. On the **Application specific parameters** page, on the **Lookups** FastTab, select **Invoices**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification Id (VoucherClassId)** field, select all document classes that are required for customer transactions.
1. On the **Lookups** FastTab, select **Withholding**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification Id (VoucherClassId)** field, select all document classes that are required for withholdings that are incurred from customer payment journals.
1. On the **Lookups** FastTab, select **TaxType**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Tax 1**.
1. In the **Tax code** field, select the tax code that is configured for the additional rate (31%).
1. In the **Lookup result** field, select **Tax 2**.
1. In the **Tax code** field, select the tax code that is configured for the taxable rate (16%).
1. In the **Lookup result** field, select **Tax 3**.
1. In the **Tax code** field, select the tax code that is configured for the reduced rate (8%).
1. In the **Lookup result** field, select **Export**.
1. In the **Tax code** field, select the tax code that is configured for export transactions.
1. In the **Lookup result** field, select **Exempt**.
1. In the **Tax code** field, select the tax code that is configured for exempt or non-taxable goods and services.

> [!NOTE]
> Complete each lookup with **No** or **Not applicable** conditions where you select **Blank** and **Not blank**.

## Generate the Declaration Reports Sales VAT Book

To generate the Declaration Reports Sales VAT Book, follow these steps.

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
1. In the **Format mapping** field, enter or select **Tax report- declaration Sales VAT Venezuela**.
1. Select **OK**.
1. In the **TAX application Id** field, enter the tax application code that was created for this report.
1. In the **From date** and **To date** fields, specify the date range for the report.
1. Select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
