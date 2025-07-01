---
title: Configure printing for Goods and Services Purchases Submission Form 606
description: Learn about the required configuration for printing Goods and Services Purchases Submission Form 606 for the Dominican Republic.
author: Cpicon85
ms.date: 04/14/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-cpicon
---

# Configure printing for Goods and Services Purchases Submission Form 606

[!INCLUDE[banner](../../includes/banner.md)]

This article explains how to configure Goods and Services Purchase Submission Form (606) so that it can be printed as a report (**Format 606 DO**). Purchase transaction records that companies use to keep a detailed record of their operations indicate vendor information and document details. As applicable, they also indicate any corresponding taxes and tax withholdings, including local and foreign transactions and other mandatory information that the regulations specify.

## Prerequisites

Before you can generate the **Format 606 DO** report, the following prerequisites must be met:

- The legal entity's address must be in the Dominican Republic.
- Both the country/region-specific LATAM feature for the Dominican Republic and the general LATAM feature must be enabled.
- You must download the specific report configuration from the Microsoft Dataverse configuration repository. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).
- You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](/dynamics365/fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters).

## Other required configuration for the Format 606 DO report

- You must create a tax application to use on the report. The tax application ID must be set to **F606**. Learn more in [Tax application for Latin America](../ltm-core-tax-application.md).
- You must configure the master field list. First configure field list 2 for the type of goods and services that are purchased, together with the corresponding code. Then configure field list 3 for the method of payment together with the corresponding code in the tax application code. Learn more in [Field list configuration for Latin America](ltm-core-field-master-lists.md).
- You must create two sales tax codes to use for Tax on Transfers of Industrialized Goods and Services (ITBIS), including ITBIS 18% (for goods) and ITBIS 0% (for services). Create one sales tax code for purchases and another for services. Remember to use one code for ITBIS that is taken to cost and another for ITBIS that is subject to proportionality.
- After you create sales tax codes, you must follow these steps.

    1. Go to **Tax** \> **Indirect tax** \> **Sales tax** \> **Sales tax codes**.
    1. Select a sales tax.
    1. On the Action Pane, select **Tax application**.
    1. In the **Tax application ID** field, verify that **F606** is entered.
    1. In the **Income tax code** field, enter **C** for ITBIS that is taken to cost or **P** for ITBIS that is subject to proportionality.

- You must configure LATAM withholding tax codes and set the tax application code for income withholding and ITBIS withholding if you need it.
- In the document class for purchase transactions (invoices, debit notes, or credit notes), in the **Additional data** section, in the field list, you must configure field list 2 and field list 3 as required.
- You must create a special document class for foreign service payments as a purchase document. To configure the country identification number of the foreign vendor, on the **Address setup** page, on the **Country/region** tab, select **LATAM** \> **Country per Taxpayer Type identification**. You must have a tax ID type that is configured as the **Not foreign** document type. You must complete the country identification number with the number of the legal entity. When you use this document, the report doesn't show income withholdings that are made to the foreign vendor.

## Configure application-specific parameters

To configure application-specific parameters, follow these steps.

1. Go to **Organization administration** \> **Workspace**, and select **Reporting configurations**.
1. In the **LTM Tax** report, select **Format 606 DO**. Then, on the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
1. On the **Application specific parameters** page, on the **Lookups** tab, select **VendorApplicableInvoices**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification Id** (**VoucherClassId**) field, select all document classes that are received from vendors, including the special document class for foreign service payments.
1. On the **Lookups** tab, select **Withholdings**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Income**.
1. In the **Document classification Id** (**VoucherClassId**) field, select all document classes for each income withholding.
1. In the **Lookup result** field, select **ITBIS**.
1. In the **Document classification Id** (**VoucherClassId**) field, select all document classes for each ITBIS withholding.
1. On the **Lookups** tab, select **TaxType**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Products**.
1. In the **Tax Code** field, select all sales tax codes that were created for products.
1. In the **Lookup result** field, select **Services**.
1. In the **Tax Code** field, select all sales tax codes that were created for services.

> [!NOTE]
> To ensure that the report shows the transactions that meet the configured conditions, complete the **Lookup result** fields as **Not Applicable** or **No**, with **blank** and **non-blank** conditions.

## Run the Format 606 DO report

To generate the **Format 606 DO** report, follow these steps.

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
1. In the **Format mapping** field, enter or select a value.
1. Select **OK**.
1. In the **TAX application ID** field, specify the tax application code that you created for this report.
1. In the **From date** field, enter a date.
1. In the **To date** field, enter a date.
1. Select **OK**.

You can generate an Excel file by doing the same configuration in **Format 606 (Excel)DO**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
