---
title: Set up and generate the Annual Declaration of Transactions with Third Parties (DAOT) sales report for Peru
description: Learn how to set up and generate the Annual Declaration of Transactions with Third Parties (DAOT) sales report for Peru in Microsoft Dynamics 365 Finance.
author: Fhernandez0088
ms.date: 04/17/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Set up and generate the Annual Declaration of Transactions with Third Parties (DAOT) sales report for Peru

[!include [banner](../../includes/banner.md)]

This article explains how to set up and generate the Annual Declaration of Transactions with Third Parties (DAOT) sales report for Peru in Microsoft Dynamics 365 Finance.

The DAOT is an informative declaration that companies must submit to the National Superintendency of Customs and Tax Administration (SUNAT), the fiscal authority in Peru. This declaration includes detailed information about transactions with vendors and customers that exceed specific value thresholds.

This article is focused exclusively on the *sales report*. Learn about the purchases report in [Set up and generate the Annual Declaration of Transactions with Third Parties (DAOT) purchases report for Peru](ltm-peru-daot-purchase-report.md).

## Prerequisites

Before you can generate the report, the following prerequisites must be met:

- The legal entity's address must be in Peru.
- You must enable both the general Latin American (LATAM) feature and the country/region-specific LATAM feature for Peru.
- You must download the specific report configuration from the Dataverse configuration repository. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

    The following formats constitute the DAOT sales report:

    - File export DAOT Sales
    - DAOT sales (Excel)

- You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Additional configuration required for the DAOT

- You must create a SUNAT *tax application code* to use on the reports. Learn more in [Tax application for Latin America](ltm-core-tax-application.md).
- Set up the tax application code of all the *taxpayer types* that are used with the SUNAT "table 2" codes. Learn more in [Taxpayer types for Latin America](ltm-core-taxpayer-type.md).
- Set up the tax application code of all the *tax ID types* that are used with the SUNAT "table 1" codes. Learn more in [Tax ID types for Latin America](ltm-core-tax-id-type.md).
- When you create a customer of the person type, you can add a second last name in the phonetic last name field as required.

## Configure application-specific parameters for the DAOT sales report and the Excel-based format

To configure application-specific parameters, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration** \> **Workspaces** \> **Electronic reporting**, and select **Reporting configurations**.
1. In the last twelve months (LTM) tax report and for each format that is listed in the [Prerequisites](#prerequisites) section, on the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
1. On the **Application specific parameters** page, on the **Lookups** FastTab, select **CustomerApplicableInvoices**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification Id (VoucherClassId)** field, select all document classes that are required for customer transactions.
1. To ensure that the report shows the transactions that meet the configured conditions, set the **Lookup result** fields to **No**, and specify both **Blank** and **Non-blank** conditions.
1. On the **Lookups** FastTab, select **TaxType**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **VAT**.
1. In the **Tax code** field, select the tax code that is configured for General Sales Tax.
1. To ensure that the report shows the transactions that meet the configured conditions, set the **Lookup result** fields to **N/A**, and specify both **Blank** and **Non-blank** conditions.

## Generate the DAOT sales report

To generate the DAOT sales report in any of the previously mentioned formats, follow these steps.

1. In Dynamics 365 Finance, go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
1. In the **Format mapping** field, enter or select one of the previously mentioned formats, and then select **OK**.
1. In the **TAX application Id** field, enter the tax application code that was created for this report.
1. In the **From date** and **To date** fields, specify the date range for the report.
1. Select **OK**.
