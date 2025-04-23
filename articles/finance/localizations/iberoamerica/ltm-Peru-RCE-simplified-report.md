---
title: Configure printing for the simplified annex of the Electronic Purchase Register (RCE) for Peru
description: Learn how to configure for printing the simplified annex of the Electronic Purchase Register (RCE) for Peru in Microsoft Dynamics 365 Finance.
author: Fhernandez0088
ms.date: 04/24/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---
# Configure printing for the simplified annex of the Electronic Purchase Register (RCE) in Peru

[!include [banner](../../includes/banner.md)]

This article explains how to configure for printing the simplified annex of the Electronic Purchase Register (RCE) for Peru in Microsoft Dynamics 365 Finance.

The RCE enables taxpayers to manage their electronic purchase records. The Peruvian fiscal authority Superintendencia Nacional de Aduanas y de Administración Tributaria (SUNAT) generates a monthly proposal designed to serve as a comparative tool, helping taxpayers identify discrepancies in their records.

The simplified version of the RCE includes the 13.5.3 annex. The Excel output version is also included.

## Prerequisites

Before you can generate and print the reports, the following prerequisites must be met:
- The legal entity's address must be in Peru.
- You must enable both the general LATAM feature and the country/region-specific LATAM feature for Peru.
- You must download the specific report configuration from the Dataverse configuration repository. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](https://learn.microsoft.com/dynamics365/finance/localizations/global/workspace/gsw-import-er-config-dataverse).
- You must configure the electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

The simplified annex for RCE is composed of the following formats that you must import:
- Last twelve months (LTM) Tax Report
- LTM Tax Report mapping
- RCE-ANEXO 13.5.3
- PE Simply Purchase Register

## Additional configurations required for RCE

- You must create a SUNAT tax application code to use on the report. Learn more in [Tax application for Latin America](../ltm-core-tax-application.md).
- When configuring document classes for purchase invoices, debit notes, and credit notes, the tax application code must be set according to SUNAT Table 3: Types of Payment Receipts or Documents.
- It's possible to associate invoices, debit notes and credit notes through the source document if needed.
    1. In Dynamics 365 Finance, go to **Accounts payable \> Inquiries and reports \> Invoice \> Invoice journal**.
    1. On the FastTab for the desired transaction, select **LATAM \> Source Documents**.
    1. Select **New**.
    1. Add the required record.
- Set up the tax application code of the **Tax ID types** used with the SUNAT Table 1 codes. Learn more in [Tax ID types for Latin America](https://learn.microsoft.com/dynamics365/finance/localizations/iberoamerica/ltm-core-tax-id-type).
- When you create a person type vendor, the **Phonetic last name** field allows you to add a second last name if required.
- Go to **General ledger \> Currencies \> Currencies** and complete the currency tax application code with the appropriate three-letter code from SUNAT Table 2: Currency Type.

## Configure application-specific parameters in Electronic Reporting for the simplified annex

To configure application-specific parameters, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration** \> **Workspace** \> and select **Reporting configurations**.
1. In the **LTM Tax report** group, for each format mentioned above, go to the **Configurations** tab, in the **Application specific parameters** group select **Setup**.
1. On the **Application specific parameters** page, on the **Lookups** tab, select **VendorIsApplicable**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**
1. In **Document classification Id (VoucherClassId)** field, select all document classes required for vendor transactions.
1. To ensure that the report shows the transactions that meet the configured conditions, set all the **Lookup result** fields to **No**, with **Blank** and **Non-blank** conditions.
1. On the **Lookups** FastTab, select **TaxType**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **IGCDG**.
1. In the **Tax code** field, select the tax code configured for taxed acquisitions exclusively intended for VAT-taxed operations and/or export.
1. On the **Conditions** FastTab, select **Add**, and in the **Lookup result** field, select **ICBP**.
1. In the **Tax code** field, select the tax code configured for the Plastic Bag Consumption Tax.
1. On the **Conditions** FastTab, select **Add**, and in the **Lookup result** field, select **OC**.
1. In the **Tax code** field, select the tax code configured for other concepts, taxes, and charges that don't form part of the taxable base.
1. To ensure that the report shows the transactions that meet the configured conditions, set the **Lookup result** fields to **N/A**, with **Blank** and **Non-blank** conditions.

## Generate a RCE annex report

To generate any RCE annex report, follow these steps.

1. In Dynamics 365 Finance, go to **Tax \> Inquiries and reports \> LATAM \> Tax reporting**.
1. In the **Format mapping** field, enter or select a value.
1. Select **OK**.
1. In the **Tax application ID** field, enter the tax application code created for this report.
1. In the **From date** and **To date** fields, set the date range for the report.
1. Select **OK**.

