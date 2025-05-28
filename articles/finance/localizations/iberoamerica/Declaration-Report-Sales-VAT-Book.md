---
title: Configure the Declaration Reports Sales VAT Book for Venezuela
description: Configure printing for the Declaration Reports Sales VAT Book for Venezuela
author: Cpicon85
ms.date: 05/26/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-Cpicon85
---

# Configure printing for the Declaration Reports Sales VAT Book for Venezuela

This article provides a guide on how to set up and generate the Declaration Reports Sales VAT Book for Venezuela.
The sales VAT book report is the record and accounting document that businesses use to keep a record of their sales transactions including transaction date, customer information and tax information details.

## Prerequisites
Before you can generate and print the report, the following prerequisites must be met:
* The legal entity's address must be in Venezuela.
* You must enable both the general Latin American (LATAM) feature and the country/region-specific LATAM feature for Venezuela.
* You must download the specific report configuration from the Dataverse configuration repository. 
Learn more in [Import Electronic reporting (ER) configurations from Dataverse]( gsw-import-er-config-dataverse.mp).
* You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](electronic-reporting-er-configure-parameters.md).

You must download the following reports:
* LTM Tax Report
* LTM Tax Report mapping
* Tax report- declaration Sales VAT Venezuela

## Additional configuration required for the Declaration Reports Sales VAT Book:
- You must create a **tax application code** to use on this report. Learn more in [Tax application for Latin America](ltm-core-tax-application.md).
- You must configure the **Tax application code** of each **Sales Point** used in transactions with **Manual**. You must configure the **User-defined field 1 code** with **MANUAL**
- You must configure the **Tax application code** of each **Document class type** used in transactions with **01 Registro** (Register) for invoices and export invoices or **02 Complemento** (Complement) for credit and debit notes.
- You must configure the **Tax application code** of each **Document class** used in transactions with **FC** for invoices, **NC** for credit notes, **ND** for debit notes and **EX** for export invoices.
- You must configure the **Tax application code** of each **Document class** used in transactions with **FC** for invoices, **NC** for credit notes, **ND** for debit notes and **EX** for export invoices.
* It is possible to associate debit notes and credit notes with invoices through Source Document if needed. Go to **Accounts payable > Inquiries and reports > Invoice > Invoice journal**. Over the desired transaction, go into de **Fast Tab** select **LATAM > Source Documents** and click **New**, add the required record.


## Configure application-specific parameters
To configure application-specific parameters, follow these steps:
1. Go to **Organization administration** > **Workspace** > and select **Reporting configurations**.
1. Into the LTM Tax report group, select the **Tax report- declaration Sales VAT Venezuela** format.
1. Go to the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
1. On the **Application specific parameters** page, on the **Lookups** tab, select **Invoices**.
1. In the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**
1. In **Document classification Id (VoucherClassId)** field select all document classes required for customer transactions.
1. Back to **Lookups** tab, select **Withholding**.
1. In the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**
1. In **Document classification Id (VoucherClassId)** field select all document classes required for withholdings suffered from customer payment journals
1. Back to **Lookups** tab, select **TaxType**.
1. In the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Tax 1**.
1. In **Tax code** field select the tax code configured for the additional rate (31%)
1. In the **Lookup result** field, select **Tax 2**.
1. In **Tax code** field select the tax code configured for the taxable rate (16%)
1. In the **Lookup result** field, select **Tax 3**.
1. In **Tax code** field select the tax code configured for the reduced rate (8%)
1. In the **Lookup result** field, select **Export**.
1. In **Tax code** field select the tax code configured for export transactions
1. In the **Lookup result** field, select **Exempt**.
1. In **Tax code** field select the tax code configured for exempt or non-taxable goods and services
> [!NOTE]
>Complete each lookup with **No** or **Not applicable** conditions where you select **Blank** and **Not blank**.

## Run Declaration Reports Sales VAT Book

To generate the Declaration Reports Sales VAT Book follow these steps.
1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
2. In the **Format mapping** field, enter or select **Tax report- declaration Sales VAT Venezuela**, and then select **OK**.
3.  In the **TAX application Id** field, enter the tax application code that was created for this report.
4. In the **From date** and **To date** fields, specify the date range for the report.
5. Select **OK**.
