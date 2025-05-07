---
title: Configure printing for the simplified Electronic Sales and Income Registry (RVIE) report for Peru
description: Learn how to configure printing for the simplified Electronic Sales and Income Registry (RVIE) report for Peru in Microsoft Dynamics 365 Finance.
author: Fhernandez0088
ms.date: 05/07/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---
# Configure printing for the Electronic Sales and Income Registry (RVIE) report simplified version for Peru

[!include [banner](../../includes/banner.md)]

This article explains how to configure printing for the simplified Electronic Sales and Income Registry (RVIE) report for Peru in Microsoft Dynamics 365 Finance.

The simplified RVIE report in Peru is a record of sales and income. These reports are used to modify proposed reports by the National Superintendency of Customs and Tax Administration (SUNAT). The simplified RVIE report includes the 5.2 annex and its Excel output version.

## Prerequisites

Before you can generate and print simplified RVIE reports, the following prerequisites must be met:
- The legal entity's address must be in Peru.
- You must enable both the general LATAM feature and the country/region-specific LATAM feature for Peru.
- You must download the specific report configuration from the Dataverse configuration repository. Learn more in [Import electronic reporting (ER) configurations from Dataverse](/dynamics365/finance/localizations/global/workspace/gsw-import-er-config-dataverse).
- You must configure the electronic reporting (ER) parameters. Learn more in [Configure the electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

RVIE is composed by the following formats that you must import:
- Last twelve months (LTM) Tax Report mapping
- LTM Tax Report
- REG Vtas E Ing Simplicado (txt)
- PE Simplified Sales Register (Excel)

## Additional configurations required for RVIE

- You must create a SUNAT tax application code to use on the report. Learn more in [Tax application for Latin America](../ltm-core-tax-application.md).
- When you configure document classes for purchase invoices, debit notes, and credit notes, the tax application code must be set according to SUNAT table 3, "Types of Payment Receipts or Documents."
- You can associate debit notes and credit notes with invoices through the source document as required.

    1. In Dynamics 365 Finance, go to **Accounts payable** > **Inquiries and reports** > **Invoice** > **Invoice journal**.
    1. On the FastTab for the desired transaction, select **LATAM** \> **Source Documents**.
    1. Select **New**.
    1. Add the required record.

- Set up the tax application code of the tax ID types that are used with the codes from SUNAT table 1. Learn more in [Tax ID types for Latin America](/dynamics365/finance/localizations/iberoamerica/ltm-core-tax-id-type).
- When you create a person of the **Person** type, you can use the **Phonetic last name** field to add a second last name as required.
- Go to **General ledger** > **Currencies** > **Currencies** and complete the currency tax application code with the appropriate three-letter code from SUNAT table 2, "Currency Type."

## Configure application-specific parameters in a simplified RVIE report

To configure application-specific parameters in a simplified RVIE report, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration** > **Workspaces** and select **Reporting configurations**.
1. In the **LTM Tax report** group, for each format that is listed in the [Prerequisites](#prerequisites) section, on the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
1. On the **Application specific parameters** page, on the **Lookups** FastTab, select **CustomerInvoiceIsApplicable**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**
1. In **Document classification Id (VoucherClassId)** field, select all document classes required for customer transactions.
1. To ensure that the report shows the transactions that meet the configured conditions, set all the **Lookup result** fields as **No**, and specify **Blank** and **Non-blank** conditions.
1. On to **Lookups** FastTab, select **TaxType**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **IGV / IPM**.
1. In **Tax code** field, select **General Sales Tax or Municipal Promotion Tax**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **BIA**.
1. In the **Tax code** field, select the tax code configured for "Taxable base".
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **OT**.
1. In the **Tax code** field, select the tax code configured for "Other taxes".
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **ICPB**.
1. In the **Tax code** field, select the tax code configured for "Tax on consumption of plastic bottles".
1. To ensure that the report shows the transactions that meet the configured conditions, set all the **Lookup result** fields to **NotApplicable**, and specify **Blank** and **Non-blank** conditions.

## Generate a RVIE report

To generate any RVIE annex report, follow these steps.

1. In Dynamics 365 Finance, go to **Tax** > **Inquiries and reports** > **LATAM** > **Tax reporting**.
1. In the **Format mapping** field, enter or select a value, and then select **OK**.
1. In the **Tax application ID** field, enter the tax application code created for this report.
1. In the **From date** and **To date** fields, set the date range for the report.
1. Select **OK**.
