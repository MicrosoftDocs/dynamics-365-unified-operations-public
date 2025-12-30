---
title: Configure printing for Goods and Services sales Submission Form 607
description: Learn about the required configuration for printing Goods and Services sales Submission Form 607 for the Dominican Republic.
author: Cpicon85
ms.date: 04/14/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-cpicon
---

# Configure printing for Goods and Services sales Submission Form 607

[!INCLUDE[banner](../../includes/banner.md)]

This article explains how to configure the Goods and Services Sales Submission Form (607) so it can be printed as the **Format 607 DO** report. Sales transaction records that companies use to keep a detailed record of their operations indicate customer information and document details. As applicable, they also indicate any corresponding taxes and tax withholdings.

## Prerequisites

Before you can generate the **Format 607 DO** report, the following prerequisites must be met:

- The legal entity's address must be in the Dominican Republic.
- Both the country/region-specific LATAM feature for the Dominican Republic and the general LATAM feature must be enabled.
- You must download the specific report configuration from the Microsoft Dataverse configuration repository. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).
- You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](/dynamics365/fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters).

## Other required configuration for the Format 607 DO report

- You must create a tax application to use on the report. The tax application ID must be set to **F607**. Learn more in [Tax application for Latin America](../ltm-core-tax-application.md).
- You must configure master field list 1 to add and classify the type of income for your sales. You can add the corresponding code in the **Tax application** option. Learn more in [Field list configuration for Latin America](ltm-core-field-master-lists.md).
- You must create sales tax codes that will be used for Tax on Transfers of Industrialized Goods and Services (ITBIS), including ITBIS 18% (for goods) and ITBIS 0% (for services).
- You must create and configure one document class payment medium for each type, such as cash and bank transfer. Learn more in [Document classes for Latin America](ltm-core-document-class.md). Then, in the **Tax application** option, you must configure the payment medium with one item from the following list.

    | Document class payment | Code |
    |---|---|
    | Cash | E |
    | Check, bank transfer, deposit | D |
    | Debit or credit card | C |
    | Bonds or Gift Certificates | B |
    | Swap | P |
    | Other forms of sales | O |

- In the document class for sales transactions (invoices, debit notes, or credit notes), in the **Additional data** section, in the field list, you must configure field 1 as required.

## Configure application-specific parameters

To configure application-specific parameters, follow these steps:

1. Go to **Organization administration** \> **Workspace**, and select **Reporting configurations**.
1. In the **LTM Tax** report, select **Format 607 DO**. Then, on the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
1. On the **Application specific parameters** page, on the **Lookups** tab, select **CustomerApplicableInvoices**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification Id** (**VoucherClassId**) field, select all document classes that represent sales (invoices, debits, and credit notes).
1. On the **Lookups** tab, select **Withholdings**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Income**.
1. In the **Document classification Id** (**VoucherClassId**) field, select all document classes for each income withholding.
1. In the **Lookup result** field, select **ITBIS**.
1. In the **Document classification Id** (**VoucherClassId**) field, select all document classes for each Tax on Transfers of Industrialized Goods and Services (ITBIS) withholding.
1. On the **Lookups** tab, select **TaxType**.
1. In the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **ITBIS**.
1. In the **Tax Code** field, select all sales tax codes that were created for ITBIS.
1. Repeat steps 15 and 16 for each column of the report.

> [!NOTE]
> To ensure that the report shows the transactions that meet the configured conditions, complete the **Lookup result** fields as **Not Applicable** or **No**, with **blank** and **non-blank** conditions.

## Run the Format 607 DO report

To generate the **Format 607 DO** report, follow these steps:

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
1. In the **Format mapping** field, enter or select a value.
1. Select **OK**.
1. In the **TAX application ID** field, specify the tax application code that you created for this report.
1. In the **From date** field, enter a date.
1. In the **To date** field, enter a date.
1. Select **OK**.

You can generate an Excel file by doing the same configuration in **Format 607 (Excel)DO**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
