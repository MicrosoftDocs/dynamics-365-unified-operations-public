---
title: Simplified transactional appendix (ATS) printing configuration
description: This article describes how to configure Simplified transactional appendix (ATS) report for printing. 
author: Fhernandez0088
ms.date: 01/09/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe 
---

# Simplified transactional appendix (ATS) printing configuration

[!INCLUDE[banner](../../includes/banner.md)]

This article describes how to configure Simplified transactional appendix (ATS) report for printing. The report is to consolidates information about commercial transactions conducted during the relevant period. It includes vendor, customer, and export customer transactions.

## Prerequisites

Before you complete the steps in this article to generate and print the report, the following prerequisites must be met: 

- The legal entity's address must be in a country/region that's within the LATAM localization. 
- The country/region-specific LATAM feature for Ecuador and the general LATAM feature must be enabled.
- Download the specific report configuration from the **Dataverse** repository. 
[ER download reports](../../global/workspace/gsw-import-er-config-dataverse.md).
- You must configure the Electronic reporting (ER) parameters. For more information, see [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md). 
- You must follow the instructions in the [Ecuadorian refund invoice transactions posting](ltm-Ecuadorian-refund-invoice.md) article to post refund invoices.

## Configure the master field lists

To configure the master field lists, follow these steps.

1. Complete **Master Field List 4** with the required items code and description from **table 10** (Export type) of the ATS Fiscal documentation.
1. Complete **Master Field List 5** with the desired options from **table 7.1** (export tax regime type) of the ATS Fiscal documentation.
1. Complete **Master Field List 6 with the desired options from **table 6** (customs district) of the ATS Fiscal documentation.
1. Complete **Master Field List 7** with the desired options from **table 13** (payment methods) of the ATS Fiscal documentation.
1. Complete **Master Field List 8** with **YES** and **NO** options to indicate if the foreign income is taxed.
1. Complete **Master Field List 9 with the desired options from **table 18** (foreign income type) of the ATS Fiscal documentation.
1. Complete **Master Field List 10** with the desired options from **table 5** (document support codes) of the ATS Fiscal documentation.

For each option from every list, the code desired to be informed must be configured into the Tax Application. For more information, see [Field list configuration for Latin America](ltm-core-field-master-lists.md) article.

### Document classes configurations

- In each document class type used for transactions, Tax application code must be configured based on **table 4** of the ATS Fiscal Document.
- In the tax application of the sales point enter **“F”** (physical transaction) or **“E”** (electronic transaction).
- For refund vendor invoice, type 2 transaction, **details taxpayer** in **General** tab must be set to yes. Into additional data, at least **Country document**, **Based in country/region** and **Taxpayer type** must be required.
- For customer export invoices document classes, **Free Text 1,2** and **3** must also be set to **Required**. Free Text 1 will be used for the document number of the carrier, Free Text 2 for **”Numero de refrendo” ** and the third one for **”Año de refrendo”**.
- In document classes used as tax withholdings configure the “Holder’s bank account mask” field with the invoice format and complete that field in tax withholding transactions (payments and collections) with the invoice complete document number that the tax withholding applies.

### Further configurations.

- In the tax application code of each Tax ID type register created as country document types, it is required to enter the required **Tipo de Identificación del Proveedor** code. This is also applicable for customers.
- In **All vendors > Retail > Vendor Type** select **Own** if vendor is not a related party, select **Third Party** otherwise. For customers this is configured in **All customers > General > Business classification**.
- In the tax application code for the vendor´s **taxpayer type**, it is required to enter the foreign fiscal regime type (table 19 in the ATS fiscal documentation).
- In the tax application code for the vendor´s **Country/region **, it is required to enter the country code according to table 16 from the Ecuador ATS documentation if applicable.
- In the tax application code for the vendor´s **State/province**, it is required to enter the code for the tax haven state/district of the country that the vendor belongs if applicable (table 17 from the Ecuador ATS documentation). This is also applicable for foreign customers; you must enter the code for the tax haven state/district of country that the foreign customer belongs to.
	
> [!NOTE]
> Withholdings will appear in the XML only if the payment journal date is within the selected date range for the report.

## Configure application-specific parameters

Lookups and conditions are designed so that you can select the combination of document classification IDs and sales tax codes that's used in the transactions. Depending on the country/region that you want to configure the report for, the applicable conditions are shown.

1. Open the **Electronic Reporting** workspace and select **Reporting configurations**.
1. Select the **ATS** and then, on the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
1. In the **Lookups names**, select **TaxType**.
1. In the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select an option from the list. 
1. In the **Tax code** field, select a tax code from the list. 
1. Repeat steps 4,5 and 6 as many tax codes as you need.
1. Back to **Lookups names**, select **VendorApplicableInvoices**.
1. In the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**. 
1. In the **Document classification Id** field, select a document class from the list. 
1. Repeat steps 9,10 and 11 as many document classes as you need. Document classes used for type 1 transactions in refund invoice and credit/debit notes must be added in this configuration.
1. Back to **Lookups names**, select ** VendorWithholdings **.
1. In the **Conditions** fast tab, select **Add**.
1. In the **Lookup result** field, select an option from the list. 
1. In the **Document classification Id** field, select a document class that represents practiced tax withholding from the list.
1. Repeat steps 14,15 and 16 as many practiced tax withholdings as you need.
1. Back to **Lookups names**, select ** CustomerApplicableInvoices **.
1. In the **Conditions** fast tab, select **Add**.
1. In the **Lookup result** field, select **Yes**. 
1. In the **Document classification Id** field, select a document class from the list. 
1. Repeat steps 19,20 and 21 as many document classes for customer invoices as you need.
1. Back to **Lookups names**, select **CustomerWithholdings**.
1. In the **Conditions** fast tab, select **Add**.
1. In the **Lookup result** field, select an option from the list. 
1. In the **Document classification Id** field, select a document class that represents a suffered tax withholding from the list.
1. Repeat steps 24,25 and 26 as many document classes for suffered tax withholdings as you need.
1. Back to **Lookups names**, select **VendorRefundsAplicableInvoices**.
1. In the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**. 
1. In the **Document classification Id** field, select a document class from the list. 
1. Repeat steps 29,30 and 31 as many document classes for vendor refund invoices as you need. Document class used for type 2 transaction in refund invoice must be added in this lookup.
To ensure that the report shows the transactions that meet the configured conditions, complete the **Lookup result** field as **Not Applicable** or **No** with **blank** and **non-blank** conditions for each **Condition**.

> [!NOTE]
> ATS is a format that depends on the LTM tax report model. Therefore, it's important that tax codes are registered in transactions. The tax codes and document classes that you select in this report configuration must match the tax codes and document classes that are registered in transactions.

> [!NOTE]
> Cancelled invoices are beyond the scope of this report.

## Generate the ATS report.

To generate the ATS report, follow these steps.

1. Go to **Tax** > **Inquiries and reports** > **LATAM** > **Tax reporting**.
1. In the **Format mapping** field, select **ATS** value. Then select **OK**.
1. In the **Tax application id** field enter the tax application code created for this report.
1. In the **From date** and **To date** fields, enter the date range to include on the report.
1. Select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
