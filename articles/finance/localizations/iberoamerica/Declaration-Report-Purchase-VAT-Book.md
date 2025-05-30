---
title: Configure Venezuela Purchase VAT book details printing
description: The article describes how to set up and use Venezuela Purchase VAT book 
author: Cpicon85
ms.date: 05/05/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-Cpicon85
---

# Configure Venezuela Purchase VAT book  

[!INCLUDE[banner](../../includes/banner.md)]

This article explains how to set up the purchase VAT ledger detail report so that it can be printed. 

Purchase VAT ledgers are the transaction records that companies use to keep a detailed record of their transactions. For each transaction, these records indicate the vendor information and document details. If applicable, they also indicate the corresponding taxes and withholding taxes, including local and foreign transactions and other mandatory information specified by the regulations in this case for Venezuela.

## Prerequisites

Before you complete the steps in this article to generate the report, the following prerequisites must be met:

- The legal entity's address must be in Venezuela.
- Both the country/region-specific Venezuela feature and the general LATAM feature must be enabled.
- You must download the specific report configuration from the Dataverse configuration repository. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](gsw-import-er-config-dataverse.md). 
- You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](electronic-reporting-er-configure-parameters.md).
- You must post vendor invoices for the relevant period. Learn more in [Purchase invoice posting for Latin America](ltm-core-purchase-invoice-posting.md)


You must download the following formats:
* LTM Tax Report mapping
* LTM Tax Report
* VE compras

## Aditional configurations required for Venezuela Purchase VAT book  
- You must create a tax application id for these reports to indicate different codes of document classes thar represent invoices, credit and debit notes and others. See [Tax application for Latin America](../ltm-core-tax-application.md).
- You must configure LATAM withholding tax codes and use the LATAM feature for tax withholdings.
- You must configure a document class as a payment order with the source exchange rate option set to **Yes** so that the withholdings taxes are calculated with the exchange rate of the invoice. Learn more in [Document classes for Latin America](ltm-core-document-class.md).

## Configure application-specific parameters

Lookups and conditions are designed so that you can select the combination of document classification IDs and sales tax codes that is used in the transactions.

To configure application-specific parameters, follow these steps.

1. Go to **Organization administration** > **Workspace** > and select **Reporting configurations**.
1. Open the **Electronic Reporting workspace** , and select **Reporting configurations**.
1. Select **Purchases Vat Book Details**, and then, on the Action Pane, on the **Configurations tab**, in the **Application specific parameters** group, select **Setup.**
1. On the **Lookups** FastTab, in the **Name** column, select **TaxType**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select a value.
1. In the **Tax code** field, select a value.
1. Repeat steps 5 and 6 to add as many tax codes as you need.
1. On the **Lookups** FastTab, in the **Name** column, select **VendorInvoiceIsApplicable**
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification Id** field, select an applicable document class.
1. On the **Lookups** FastTab, in the **Name** column, select **VendorCreditNoteIsApplicable**.
1. On the ** Conditions FastTab**, select **Add**.
1. In the **Lookup result** field, select **yes**.
1. In the **Document classification Id** field, select a document class that represent a Credit note.
1. Repeat previous steps to add as many document classes as you need.

> [!NOTE]
> Complete each lookup with **No** or **Not applicable** conditions where you select **Blank** and **Not blank**.

## Run VAT books:

To generate puechase VAT book for Venezuela, follow these steps.

1. Go to **Tax** > **Inquiries and reports** > **LATAM** > **Tax reporting**.
1. In the Format mapping field,select **VE compras** value.
1. Select **OK**.
1. In the **Tax application id** field, enter the tax application code that was created for this report.
1. In the **From date** and **To date** fields, specify the date range for the report.
1. Select **OK**.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
