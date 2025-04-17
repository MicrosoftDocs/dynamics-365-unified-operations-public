---
title: Configure printing for Annual Declaration of Transactions with Third Parties (DAOT) purchases report for Peru
description: Learn how to set up and generate the Annual Declaration of Transactions with Third Parties (DAOT) purchases report for Peru in Microsoft Dynamics 365 Finance.
author: Fhernandez0088
ms.date: 04/17/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Configure printing for Annual Declaration of Transactions with Third Parties (DAOT) purchases report for Peru

[!include [banner](../../includes/banner.md)]

This article explains how to set up and generate the Annual Declaration of Transactions with Third Parties (DAOT) purchases report for Peru in Microsoft Dynamics 365 Finance.

The DAOT is an informative declaration that companies must submit to Superintendencia Nacional de Aduanas y de Administración Tributaria (SUNAT), the fiscal authority in Peru. This declaration includes detailed information about transactions with vendors and customers that exceed certain value thresholds.
In this article, we will focus exclusively on the purchases report.

## Prerequisites

Before you complete the steps to generate the report, the following prerequisites must be met:
- The legal entity's address must be in Peru.
- You must enable both the general LATAM feature and the country/region-specific LATAM feature for Peru.
- You must download the specific report configuration from the Dataverse configuration repository. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](/dynamics365/finance/localizations/global/workspace/gsw-import-er-config-dataverse).
- The following formats constitute the DAOT:
    - File export DAOT purchases
    - DAOT purchases (Excel)
- You must configure the electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Aditional configurations required for DAOT

- You must create a SUNAT tax application code to use on the reports. Learn more in [Tax application for Latin America](../ltm-core-tax-application.md).
- Set up the tax application code of all the *taxpayer types* used with the SUNAT "table 2" codes. Learn more in [Taxpayer types for Latin America](/dynamics365/finance/localizations/iberoamerica/ltm-core-taxpayer-type).
- Set up the tax application code of all the tax ID types used with the SUNAT "table 1" codes. Learn more in [Tax ID types for Latin America](/dynamics365/finance/localizations/iberoamerica/ltm-core-tax-id-type).
- When creating a person type vendor, the phonetic last name field allows you to add a second last name if required.

## Configure application-specific parameters for DAOT purchases and the Excel-based format

To configure application-specific parameters, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration** \> **Workspace** and select **Reporting configurations**.
1. In the last twelve months (LTM) tax report and for each format mentioned above, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
1. On the **Application specific parameters** page, on the **Lookups** tab, select **VendorApplicableInvoices**.
1. In the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**
1. In the **Document classification Id (VoucherClassId)** field, select all document classes required for vendor transactions.
1. To ensure that the report shows the transactions that meet the configured conditions, set the **Lookup result** fields to **No**, with both **Blank** and **Non-blank** conditions.
1. On to **Lookups** FastTab, select **TaxType**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **VAT**.
1. In the **Tax code** field, select the tax code configured for General Purchase Tax.
1. To ensure that the report shows the transactions that meet the configured conditions, set the **Lookup result** fields to **N/A**, with both **Blank** and **Non-blank** conditions.

## Generate DAOT report

To generate any DAOT format report mentioned above, follow these steps.

1. In Dynamics 365 Finance, go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
1. In the **Format mapping** field, enter or select any format mentioned above, and then select **OK**.
1. In the **TAX application Id** field, enter the tax application code created for this report.
1. In the **From date** and **To date** fields, specify the date range for the report.
1. Select **OK**.

