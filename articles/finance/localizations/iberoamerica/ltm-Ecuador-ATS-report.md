---
title: Configure Simplified transactional appendix (ATS) printing
description: Learn how to configure the Simplified transactional appendix (ATS) report for printing.
author: Fhernandez0088
ms.date: 01/09/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe 
---

# Configure Simplified transactional appendix (ATS) printing

[!INCLUDE[banner](../../includes/banner.md)]

This article explains how to configure the **Simplified transactional appendix** (**ATS**) report for printing. The report is used to consolidate information about commercial transactions that were conducted during the relevant period. It includes vendor, customer, and export customer transactions.

## Prerequisites

Before you can generate and print the **ATS** report, the following prerequisites must be met:

- The legal entity's address must be in a country/region that is within the LATAM localization.
- Both the country/region-specific LATAM feature for Ecuador and the general LATAM feature must be enabled.
- You must download the relevant report configuration from the Dataverse repository. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).
- You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
- You must post refund invoices by following the instructions in [Ecuadorian refund invoice transactions posting](ltm-Ecuadorian-refund-invoice.md).

## Configure the master field lists

To configure the master field lists, follow these steps.

1. Complete **Master Field List 4** with the required items code and description from **table 10** (export type) of the ATS Fiscal documentation.
1. Complete **Master Field List 5** with the desired options from **table 7.1** (export tax regime type) of the ATS Fiscal documentation.
1. Complete **Master Field List 6** with the desired options from **table 6** (customs district) of the ATS Fiscal documentation.
1. Complete **Master Field List 7** with the desired options from **table 13** (payment methods) of the ATS Fiscal documentation.
1. Complete **Master Field List 8** with **YES** and **NO** options to indicate whether foreign income is taxed.
1. Complete **Master Field List 9** with the desired options from **table 18** (foreign income type) of the ATS Fiscal documentation.
1. Complete **Master Field List 10** with the desired options from **table 5** (document support codes) of the ATS Fiscal documentation.

For each option in every list, the code that you want to be entered must be configured in the tax application. Learn more in [Field list configuration for Latin America](ltm-core-field-master-lists.md).

### Configure document classes

- In each document class type that is used for transactions, a tax application code must be configured based on **table 4** of the ATS Fiscal documentation.
- In the tax application of the sales point, enter **"F"** (physical transaction) or **"E"** (electronic transaction).
- For a type 2 transaction on a refund vendor invoice, the **Details taxpayer** option in the **General** section must be set to **Yes**. In the **Additional data** section, at least the **Country document**, **Based in country/region**, and **Taxpayer type** fields must be set to **Required**.
- For customer export invoices document classes, the **Free Text 1**, **Free Text 2**, and **Free Text 3** fields must also be set to **Required**. The **Free Text 1** field is used for the document number of the carrier, the **Free Text 2** field is used for **"Numero de refrendo"**, and the **Free Text 3** field is used for **"Año de refrendo"**.
- In document classes that are used as tax withholdings, configure the **Holder's bank account mask** field with the invoice format, and complete that field in tax withholding transactions (payments and collections) with the complete document number that the tax withholding applies for invoices.

### Other configuration

- In the tax application code of each tax ID type register that is created as a country document type, you must enter the required **Tipo de Identificación del Proveedor** code. This requirement is also applicable for customers.
- At **All vendors** \> **Retail** \> **Vendor Type**, select **Own** if the vendor is *not* a related party. Otherwise, select **Third Party**. For customers, this setting is configured at **All customers** \> **General** \> **Business classification**.
- In the tax application code for the vendor's taxpayer type, you must enter the foreign fiscal regime type (**table 19** of the ATS Fiscal documentation).
- In the tax application code for the vendor's country/region, you must enter the country code (**table 16** of the ATS Fiscal documentation), if applicable.
- In the tax application code for the vendor's state/province, you must enter the code for the tax haven state/district of the country/region that the vendor belongs to (**table 17** of the ATS Fiscal documentation), if applicable. This requirement is also applicable for foreign customers. In that case, you must enter the code for the tax haven state/district of country/region that the foreign customer belongs to.
	
> [!NOTE]
> Withholdings appear in the XML only if the payment journal date is within the selected date range for the report.

## Configure application-specific parameters

Lookups and conditions are designed so that you can select the combination of document classification IDs and sales tax codes that is used in the transactions. Depending on the country/region that you want to configure the report for, the applicable conditions are shown.

1. Open the **Electronic Reporting** workspace, and select **Reporting configurations**.
1. Select **ATS**, and then, on the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
1. On the **Lookups** FastTab, in the **Name** column, select **TaxType**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select a value.
1. In the **Tax code** field, select a tax code.
1. Repeat steps 4 through 6 to add as many more tax codes as you need.
1. On the **Lookups** FastTab, in the **Name** column, select **VendorApplicableInvoices**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification Id** field, select a document class.
1. Repeat steps 9 through 11 to add as many more document classes as you need. Document classes that are used for type 1 transactions on refund invoice and credit/debit notes must be added in this lookup.
1. On the **Lookups** FastTab, in the **Name** column, select **VendorWithholdings**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select a value.
1. In the **Document classification Id** field, select a document class that represents practiced tax withholding.
1. Repeat steps 14 through 16 to add as many more practiced tax withholdings as you need.
1. On the **Lookups** FastTab, in the **Name** column, select **CustomerApplicableInvoices**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification Id** field, select a document class.
1. Repeat steps 19 through 21 to add as many more document classes for customer invoices as you need.
1. On the **Lookups** FastTab, in the **Name** column, select **CustomerWithholdings**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select a value.
1. In the **Document classification Id** field, select a document class that represents a suffered tax withholding.
1. Repeat steps 24 through 26 to add as many more document classes for suffered tax withholdings as you need.
1. On the **Lookups** FastTab, in the **Name** column, select **VendorRefundsAplicableInvoices**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification Id** field, select a document class.
1. Repeat steps 29 through 31 to add as many more document classes for vendor refund invoices as you need. Document classes that are used for type 2 transactions on refund invoices must be added in this lookup.
1. To ensure that the report shows the transactions that meet the configured conditions, complete the **Lookup result** field as **Not Applicable** or **No** with blank and non-blank conditions for each condition.

> [!NOTE]
> **ATS** is a format that depends on the **LTM Tax Report** model. Therefore, it's important that tax codes are registered in transactions. The tax codes and document classes that you select in this report configuration must match the tax codes and document classes that are registered in transactions.
>
> Canceled invoices are beyond the scope of this report.

## Generate the ATS report

To generate the **ATS** report, follow these steps.

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
1. In the **Format mapping** field, select **ATS**.
1. Select **OK**.
1. In the **Tax application id** field, enter the tax application code that was created for this report.
1. In the **From date** and **To date** fields, enter the date range to include on the report.
1. Select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
