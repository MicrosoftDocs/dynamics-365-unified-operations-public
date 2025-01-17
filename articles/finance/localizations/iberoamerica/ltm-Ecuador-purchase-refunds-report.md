---
title: Configure Ecuadorian purchase refunds printing
description: Learn how to configure the Ecuadorian purchase refunds report for printing.
author: Fhernandez0088
ms.date: 12/30/2024
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Configure Ecuadorian purchase refunds printing

[!INCLUDE[banner](../../includes/banner.md)]

The article explains how to configure the Ecuadorian purchase refunds report so that it can be printed. This report provides information about purchase refund transactions, which are used when there are intermediaries in the purchases.

In a purchase refund transaction, there are three parties: a vendor, an intermediary, and a beneficiary. The vendor issues the invoice in the name of the intermediary, and the intermediary is the party that pays the vendor. However, the expenses and the value-added tax (VAT) credit correspond to the beneficiary. Because the intermediary must comply with a refund request process, the beneficiary reimburses the intermediary for the expense.

## Prerequisites

Before you can generate and print the report, the following prerequisites must be met:

- The legal entity's address must be in a country/region that is within the LATAM localization.
- Both the country/region-specific LATAM feature and the general LATAM feature must be enabled.
- You must download the relevant report from the Global repository. Learn more in [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).
- You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
- You must post vendor invoices for the relevant period. Learn more in [Purchase invoice posting for Latin America](/dynamics365/finance/localizations/iberoamerica/ltm-core-purchase-invoice-posting).
- You must post vendor payments. Learn more in [Use the LATAM extension in vendor payments journals](/dynamics365/finance/localizations/iberoamerica/ltm-latam-in-vendor-payment).
- You must post refund invoices. Learn more in [Ecuadorian refund invoice transactions posting](ltm-Ecuadorian-refund-invoice.md).

## Additional configuration required for Ecuadorian Purchases refunds report:

- You must create and use a **Tax Application** code for this report. Learn more in [Tax application for Latin America](https://learn.microsoft.com/dynamics365/finance/localizations/iberoamerica/ltm-core-tax-application).
- You must configure the **Vendor identification ID type code** in the **Tax application** of the vendor **Tax Id type** as specified by the regulation. Learn more in [Document classes for Latin America](https://learn.microsoft.com/dynamics365/finance/localizations/iberoamerica/ltm-core-document-class)
- You must configure the **Document type code** in the **Tax application** field of the **Document class types** used in transactions as specified by the regulation. Learn more in [Document class type for Latin America](https://learn.microsoft.com/dynamics365/finance/localizations/iberoamerica/ltm-core-document-class-type).

## Configure application-specific parameters

Lookups and conditions are designed so that you can select the combination of document classification IDs and sales tax codes that is used in the transactions. Depending on the country/region that you want to configure the report for, the applicable conditions are shown.

To configure application-specific parameters, follow these steps.

1. Open the **Electronic Reporting** workspace, and select **Reporting configurations**.
1. Select the **EC Purchases Refund** format, and then, on the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
1. On the **Lookups** FastTab, in the **Name** column, select **TaxType**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select a value.
1. In the **Tax code** field, select a value.
1. Repeat steps 5 and 6 to add as many more tax codes as you need.
1. On the **Lookups** FastTab, in the **Name** column, select **VendorApplicableInvoices**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification Id** field, select a value (add all document classes involved in refund transactions except for the used in balance transactions).
1. Repeat steps 10 and 11 to add as many more document classes as you need.
1. On the **Lookups** FastTab, in the **Name** column, select **ApplicableWithholdings**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select a value.
1. In the **Document classification Id** field, select a value.
1. Repeat steps 15 and 16 to add as many more withholding document classes as you need.

> [!NOTE]
> Purchase refunds are formats that depend on the **LTM Tax Report** model. Therefore, it's important that taxes and document classes are registered for transactions. The tax codes and document classes that you select here must match the codes and document classes that are registered in the transactions. To ensure that the report shows the transactions that meet the configured conditions, complete each **Lookup result** field as **Not Applicable** or **No** with blank and non-blank conditions.

## Run the purchase refunds report

To generate the purchase refunds report, follow these steps.

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
1. In the **Format mapping** field, select **EC Purchases Refund **.
1. Select **OK**.
3. In the parameters section, complete the **Tax application Id** field with the **Tax application** code created for this report.
1. In the **From date** and **To date** fields, enter the date range to include on the report.
1. Select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
