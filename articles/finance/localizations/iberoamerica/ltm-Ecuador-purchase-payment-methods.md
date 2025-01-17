---
title: Configure Ecuadorian purchase payment methods printing 
description: Learn how to configure the Ecuadorian purchase payment methods report for printing.
author: Fhernandez0088
ms.date: 12/30/2024
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Configure Ecuadorian purchase payment methods printing

[!INCLUDE[banner](../../includes/banner.md)]

This article explains how to configure the Ecuadorian purchase payment methods report so that it can be printed. This report shows the purchase code, its payments, and the transactions amount.

## Prerequisites

Before you can generate and print the report, the following prerequisites must be met:

- The legal entity's address must be in a country/region that is within the LATAM localization.
- Both the country/region-specific LATAM feature and the general LATAM feature must be enabled.
- You must download the relevant report from the Global repository. Learn more in [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).
- You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
- You must post vendor invoices for the relevant period. Learn more in [Purchase invoice posting for Latin America](ltm-core-purchase-invoice-posting.md).
- You must post vendor payments. Learn more in [Use the LATAM extension in vendor payments journals](ltm-latam-in-vendor-payment.md).

## Additional configuration required for Ecuadorian Purchases payment methods report:

- You must create and use a **Tax Application** code for this report. See [Tax application for Latin America](https://learn.microsoft.com/dynamics365/finance/localizations/iberoamerica/ltm-core-tax-application) article.
- You must configure **Payment method** as specified by the regulation in the field master list 7. For more information, see [Field list configuration for Latin America] (https://learn.microsoft.com/en-us/dynamics365/finance/localizations/iberoamerica/ltm-core-field-master-lists)
- You must configure the **Payment method code** in the field master list 7 of the document class used as specified by the regulation. Learn more in [Field list configuration for Latin America](https://learn.microsoft.com/dynamics365/finance/localizations/iberoamerica/ltm-core-field-master-lists) article.

## Configure application-specific parameters

Lookups and conditions are designed so that you can select the combination of document classification IDs and sales tax codes that is used in the transactions. Depending on the country/region that you want to configure the report for, the applicable conditions are shown.

To configure application-specific parameters, follow these steps.

1. Open the **Electronic Reporting** workspace, and select **Reporting configurations**.
1. Select the **EC Purchases Payment Methods** format, and then, on the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
1. On the **Lookups** FastTab, in the **Name** column, select **IsApplicable**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document Classification Id** field, select a document class that represents vendor tax withholdings.
1. Repeat steps 5 and 6 to add as many more **Lookups result** fields as you need.
 
> [!NOTE]
> **EC Purchases Payment Methods** is a format that depends on the **LTM Tax Report** model. Therefore, it's important that document classes are registered for the transactions. The document classes that you select here must match the document classes that are registered in the transactions. To ensure that the report shows the transactions that meet the configured conditions, complete the **Lookup result** field as **Not Applicable** or **No** with blank and non-blank conditions.

## Run the purchase payment methods report

To generate the purchase payment methods report, follow these steps.

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
1. In the **Format mapping** field, select **EC Purchases Payment Methods**.
1. Select **OK**.
3. In **Parameters**, complete the **Tax application Id** code created for this report.
1. In the **From date** and **To date** fields, enter the date range to include on the report.
1. Select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
