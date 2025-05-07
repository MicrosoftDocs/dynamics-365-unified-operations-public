---
title: Configure printing for IGV withholding tax report for Peru
description: Learn how to configure printing for an IGV withholdings tax report for Peru in Microsoft Dynamics 365 Finance.
author: Fhernandez0088
ms.date: 05/07/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Configure printing for IGV withholding tax report for Peru

[!include [banner](../../includes/banner.md)]

This article explains how to configure printing for an Impuesto general a las ventas (IGV) withholdings tax report for Peru in Microsoft Dynamics 365 Finance.

The withholding agent must declare the total amount of withholdings made during the month and make the respective payment using Form 626. If you can't use Form 626, you must generate a text format of Form 626 using this report.

## Prerequisites

Before you can complete the steps in this article to generate the report, the following prerequisites must be met:
- The legal entity's address must be in Peru.
- You must enable both the general LATAM feature and the country/region-specific LATAM feature for Peru.
- You must download the specific report configuration from the Dataverse configuration repository. Learn more in [Import electronic reporting (ER) configurations from Dataverse](/dynamics365/finance/localizations/global/workspace/gsw-import-er-config-dataverse). 
- You must configure the electronic reporting (ER) parameters. Learn more in [Configure the electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
- You must download the following formats:
    - Last twelve months (LTM) Tax Report mapping
    - LTM Tax Report
    - Withholdings (PER) (text)
    - Withholdings (PER) (Excel)

## Additional configuration required for the IGV withholding tax report

- You must create a tax application ID for these reports to indicate different codes of document classes thar represent invoices, credit and debit notes and others. Learn more in [Tax application for Latin America](../ltm-core-tax-application.md).
- You must configure LATAM withholding tax codes and use the LATAM feature for tax withholdings.
- You must configure a document class as a payment order with the source exchange rate option set to **Yes** so that the withholdings taxes are calculated with the exchange rate of the invoice. Learn more in [Document classes for Latin America](/dynamics365/finance/localizations/iberoamerica/ltm-core-document-class).

## Configure application-specific parameters

To configure application-specific parameters, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration** > **Workspaces** and select **Reporting configurations**.
1. In the **LTM Tax report** group, select the desired format.
1. On the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
1. On the **Application specific parameters** page, on the **Lookups** FastTab, select **VendorInvoiceIsApplicable**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification Id (VoucherClassId)** field, select all document classes that should appear in the report.
1. On the **Lookups** FastTab, select **Withholdings**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Withholding**. 
1. In the **Document classification Id (VoucherClassId)** field, select the document classes representing VAT withholdings taxes that should appear in the report. 
To ensure that the report shows the transactions that meet the configured conditions, set all the **Lookup result** fields as **Not Applicable** or **No**, and specify **Blank** and **Non-blank** conditions.

## Generate an IGV withholding report

To generate any IGV withholding report, follow these steps.

1. In Dynamics 365 Finance, go to **Tax** > **Inquiries and reports** > **LATAM** > **Tax reporting**.
1. In the **Format mapping** field, enter or select a value, and then select **OK**.
1. In the **Tax application ID** field, enter the tax application code created for this report.
1. In the **From date** and **To date** fields, set the date range for the report.
1. Select **OK**.

