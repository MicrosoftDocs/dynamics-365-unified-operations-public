---
title: Configure printing for the IGV withholding tax report for Peru
description: Learn how to configure printing for the General Sales Tax (IGV) withholding tax report for Peru in Microsoft Dynamics 365 Finance.
author: Fhernandez0088
ms.date: 05/07/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Configure printing for the IGV withholding tax report for Peru

[!include [banner](../../includes/banner.md)]

This article explains how to configure printing for the General Sales Tax (IGV) withholding tax report for Peru in Microsoft Dynamics 365 Finance.

The withholding agent must declare the total amount of withholdings that were made during the month, and they must use Form 626 to make the appropriate payment. If you can't use Form 626, you must use an IGV withholding tax report to generate a text format of Form 626.

## Prerequisites

Before you can generate and print IGV withholding tax reports, the following prerequisites must be met:

- The legal entity's address must be in Peru.
- You must enable both the general LATAM feature and the country/region-specific LATAM feature for Peru.
- You must download the specific report configuration from the Dataverse configuration repository. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).
- You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
- You must download the following formats:

    - :::no-loc text="Tax Report mapping":::
    - :::no-loc text="LTM Tax Report":::
    - :::no-loc text="Withholdings (PER) (text)":::
    - :::no-loc text="Withholdings (PER) (Excel)":::

## Additional configuration required for the IGV withholding tax report

- You must create a tax application ID for the report to indicate the different codes of document classes that represent invoices, credit and debit notes, and other documents. Learn more in [Tax application for Latin America](ltm-core-tax-application.md).
- You must configure LATAM withholding tax codes and use the LATAM feature for tax withholdings.
- You must configure a document class as a payment order where the **Source exchange rate** option is set to **Yes**. In this way, the exchange rate of the invoice is used to calculate the withholding taxes. Learn more in [Document classes for Latin America](ltm-core-document-class.md).

## Configure application-specific parameters

To configure application-specific parameters, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** \> **Workspaces**, and select **Reporting configurations**.
1. In the **LTM Tax report** group, select the desired format.
1. On the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
1. On the **Application specific parameters** page, on the **Lookups** FastTab, select **VendorInvoiceIsApplicable**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification Id (VoucherClassId)** field, select all document classes that should appear on the report.
1. On the **Lookups** FastTab, select **Withholdings**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Withholding**.
1. In the **Document classification Id (VoucherClassId)** field, select the document classes that represent value-added tax (VAT) withholding taxes that should appear on the report.
1. To ensure that the report shows the transactions that meet the configured conditions, set all the **Lookup result** fields as **Not Applicable** or **No**, and specify **Blank** and **Non-blank** conditions.

## Generate an IGV withholding tax report

To generate an IGV withholding tax report, follow these steps:

1. In Finance, go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
1. In the **Format mapping** field, enter or select a value.
1. Select **OK**.
1. In the **Tax application ID** field, enter the tax application code that was created for this report.
1. In the **From date** and **To date** fields, set the date range for the report.
1. Select **OK**.
