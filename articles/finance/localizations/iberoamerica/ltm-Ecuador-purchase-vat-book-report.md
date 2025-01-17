---
title: Configure Ecuadorian purchase VAT book details printing
description: Learn how to configure the Ecuadorian purchase VAT book details report for printing.
author: Fhernandez0088
ms.date: 01/17/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Configure Ecuadorian purchase VAT book details printing

[!INCLUDE[banner](../../includes/banner.md)]

This article explains how to configure the purchase value-added tax (VAT) book details report so that it can be printed. Purchases VAT books are the transaction records that companies use to keep a detailed record of their operations. For each transaction, these records indicate the vendor information and document details. If applicable, they also indicate the corresponding taxes and tax withholdings, including local and foreign transactions and other mandatory information that the regulations specify.

## Prerequisites

Before you complete the steps in this article to generate and print the report, the following prerequisites must be met:

- The legal entity's address must be in Ecuador.
- Both the country/region-specific Ecuador feature and the general LATAM feature must be enabled.
- You must download the relevant report from the Global repository. Learn more in [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).
- You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
- You must post vendor invoices for the relevant period. Learn more in [Purchase invoice posting for Latin America](/dynamics365/finance/localizations/iberoamerica/ltm-core-purchase-invoice-posting).
- You must post vendor payments with or without withholding taxes. For more information see [Use the LATAM extension in vendor payments journals](ltm-latam-in-vendor-payment.md) article.
- You must configure LATAM withholding tax codes and set tax application code for each withholding tax code as specified by the regulation. See [Tax application for Latin America](ltm-core-tax-application.md)

## Additional configuration required for Ecuadorian Purchases VAT book details report:

- You must create and use a **Tax Application** code for this report. See [Tax application for Latin America](ltm-core-tax-application.md) article.
- Configure master field list 10 in purchase invoice document classes with the **Support code** as specified by the regulation. See [Field list configuration for Latin America](ltm-core-field-master-lists.md) article.
- You must configure the **Tax application code** of the vendor **Tax Id type** with the **Vendor identification type code** as specified by the regulation. See [Tax ID types for Latin America](ltm-core-tax-id-type.md)
- You must configure the **Tax application code** of the **Document class type** with the **Document type code** as specified by the regulation. See [Document class type for Latin America](ltm-core-document-class-type.md)
-You must configure the **Vendor type** field in the **Retail** section of the **Vendor** configuration with **Own** to indicate no relation, and with **3rd party** to indicate a related part.
- A vendor payment will be considered locally or abroad according to the country address configured in the vendor main address.
- You must configure the **Tax application code** of the vendor **Taxpayer type** with the **Foreign tax regime code** as specified by the regulation. See [Taxpayer types for Latin America](iberoamerica/ltm-core-taxpayer-type.md)

## Configure application-specific parameters

Lookups and conditions are designed so that you can select the combination of document classification IDs and sales tax codes that is used in the transactions. Depending on the country/region that you want to configure the report for, the applicable conditions are shown.

To configure application-specific parameters, follow these steps.

1. Open the **Electronic Reporting** workspace, and select **Reporting configurations**.
1. Select **Purchases Vat Book Details**, and then, on the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
1. On the **Lookups** FastTab, in the **Name** column, select **TaxType**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select a value.
1. In the **Tax code** field, select a value.
1. Repeat steps 5 and 6 to add as many more tax codes as you need.
1. On the **Lookups** FastTab, in the **Name** column, select **VendorApplicableInvoices**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification Id** field, select an applicable document class.
1. Repeat steps 10 and 11 to add as many more document classes as you need.
1. On the **Lookups** FastTab, in the **Name** column, select **WithholdingGroup**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select a withholding tax category.
1. In the **Document classification Id** field, select a document class that represent a withholding tax.
1. Repeat steps 15 and 16 to add as many more withholding document classes as you need.

> [!NOTE]
> Purchase VAT book details are formats that depend on the **LTM Tax Report** model. Therefore, it's important that taxes and document classes are registered for transactions. The tax codes and document classes that you select here must match the codes and document classes that are registered in the transactions. To ensure that the report shows the transactions that meet the configured conditions, complete the **Lookup result** fields as **Not Applicable** or **No** with blank and non-blank conditions.

## Run the purchase VAT book details report

To generate the purchase VAT book details report, follow these steps.

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
1. In the **Format mapping** field, select **EC Purchases VAT Book details**.
1. Select **OK**.
2. In the **Tax application Id** field, enter the tax application code you created for this report.
1. In the **From date** and **To date** fields, enter the date range to include on the report.
1. Select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
