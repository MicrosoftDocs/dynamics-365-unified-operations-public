---
title: Configure printing for Relationship purchases Book reports for Venezuela
description: Learn how to configure printing for Relationship purchases Book reports for Venezuela. 
author: Cpicon85
ms.date: 02/05/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-cpicon
---

# Configure printing for Relationship purchases Book reports for Venezuela

[!INCLUDE[banner](../../includes/banner.md)]

This article explains how to set up and generate the Relationship purchases Book reports for Venezuela.

The Declaration Reports Relationship purchases Book in Venezuela is a document that details all purchase transactions for formal taxpayers that replace the purchase ledger according to the normative. This report must keep a monthly chronological record of transactions. It must include details such as the date of the transaction, the number of invoices, debit notes, or credit notes for the domestic or foreign purchase of goods and receipt of services, the name of each vendor, the tax identification number, and the total value of domestic purchases of goods and services that were received.

## Prerequisites

Before you can generate the report, the following prerequisites must be met:

- The legal entity's address must be in Venezuela.
- You must enable both the general Latin American (LATAM) feature and the country/region-specific LATAM feature for Venezuela.
- You must download the specific report configuration from the Microsoft Dataverse configuration repository. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

    You must download the following reports:

    - LTM Tax Report mapping
    - LTM Tax Report
    - Declaration Reports Relationship purchases Book VE

- You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Additional configuration required for Relationship purchases Book reports

- You must create a tax application ID. Learn more in [Tax application for Latin America](ltm-core-tax-application.md).
- You must configure withholdings with a negative percentage in sales tax codes.

## Configure application-specific parameters

To configure application-specific parameters, follow these steps.

1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**, and select **Reporting configurations**.
1. In the **LTM Tax Report** group, select the **Declaration Reports Relationship purchases Book VE** format.
1. On the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
1. On the **Application specific parameters** page, on the **Lookups** FastTab, select **TaxType**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select different value-added tax (VAT) rates, and exempt and different withholding rates.
1. On the **Lookups** FastTab, select **InvoiceIsApplicable**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification Id (VoucherClassId)** field, select all document classes that should appear on the report.

> [!NOTE]
> Complete each lookup with **No** or **Not applicable** conditions where you select **Blank** and **Not blank**.

## Generate Relationship purchases Book reports

To generate Relationship purchases Book reports, follow these steps.

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
1. In the **Format mapping** field, enter or select the value that represents these reports.
1. Select **OK**.
1. In the **TAX application Id** field, enter the tax application code that was created for these reports.
1. In the **From date** and **To date** fields, select the date range for the reports.
1. Select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
