---
title: Configure printing for Venezuelan Purchase VAT book details
description: Learn how to set up and use the Venezuelan Purchase VAT book.
author: Cpicon85
ms.date: 05/05/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-cpicon
---

# Configure printing for Venezuelan Purchase VAT book details

[!INCLUDE[banner](../../includes/banner.md)]

This article explains how to set up the purchase value-added tax (VAT) ledger details report so that it can be printed.

Purchase VAT ledgers are the transaction records that companies use to keep a detailed record of their transactions. For each transaction, these records indicate the vendor information and document details. If applicable, they also indicate the corresponding taxes and withholding taxes, including local and foreign transactions and other mandatory information that is specified by the regulations for Venezuela.

## Prerequisites

Before you can generate the report, the following prerequisites must be met:

- The legal entity's address must be in Venezuela.
- Both the country/region-specific Latin American (LATAM) feature for Venezuela and the general LATAM feature must be enabled.
- You must download the specific report configuration from the Microsoft Dataverse configuration repository. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

    You must download the following formats:

    - LTM Tax Report mapping
    - LTM Tax Report
    - VE compras

- You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
- You must post vendor invoices for the relevant period. Learn more in [Purchase invoice posting for Latin America](ltm-core-purchase-invoice-posting.md).

## Additional configuration required for the Venezuelan Purchase VAT book

- You must create a tax application ID for the report to indicate the different codes for the document classes that represent invoices, credit notes, debit notes, and other documents. Learn more in [Tax application for Latin America](ltm-core-tax-application.md).
- You must configure LATAM withholding tax codes and use the LATAM feature for tax withholdings.
- You must configure a document class as a payment order where the **Source exchange rate** option is set to **Yes**. In this way, the exchange rate of the invoice is used to calculate the withholding taxes. Learn more in [Document classes for Latin America](ltm-core-document-class.md).

## Configure application-specific parameters

Lookups and conditions are designed so that you can select the combination of document classification IDs and sales tax codes that is used in the transactions.

To configure application-specific parameters, follow these steps:

1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**, and select **Reporting configurations**.
1. Select **Purchases Vat Book Details**, and then, on the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
1. On the **Application specific parameters** page, on the **Lookups** FastTab, in the **Name** column, select **TaxType**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select a value.
1. In the **Tax code** field, select a value.
1. Repeat steps 4 through 6 to add as many more tax codes as you need.
1. On the **Lookups** FastTab, in the **Name** column, select **VendorInvoiceIsApplicable**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification Id** field, select an applicable document class.
1. On the **Lookups** FastTab, in the **Name** column, select **VendorCreditNoteIsApplicable**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification Id** field, select a document class that represents a credit note.
1. Repeat the previous steps to add as many more document classes as you need.

> [!NOTE]
> Complete each lookup with **No** or **Not applicable** conditions where you select **Blank** and **Not blank**.

## Generate the Venezuelan Purchase VAT book

To generate the Venezuelan Purchase VAT book, follow these steps:

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
1. In the **Format mapping** field, select **VE compras**.
1. Select **OK**.
1. In the **Tax application Id** field, enter the tax application code that was created for this report.
1. In the **From date** and **To date** fields, specify the date range for the report.
1. Select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
