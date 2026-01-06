---
title: Configure printing for Cash and Banks Ledger reports for Peru
description: Learn how to configure printing for Cash and Banks Ledger reports for Peru in Microsoft Dynamics 365 Finance.
author: Fhernandez0088
ms.date: 05/07/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Configure printing for Cash and Banks Ledger reports for Peru

[!include [banner](../../includes/banner.md)]

This article explains how to configure printing for Cash and Banks Ledger reports for Peru in Microsoft Dynamics 365 Finance.

The following procedures guide you through the process of setting up and generating the following Cash and Banks Ledger formats for Peru:

- Cash and Bank Ledger F1.1 for cash transactions
- Cash and Bank Ledger F1.2 for bank transactions

All the information from the movement of cash and cash equivalents (banks) must be recorded in these books monthly to maintain control of the company's financial transactions.

## Prerequisites

Before you can generate and print Cash and Banks Ledger reports, the following prerequisites must be met:

- The legal entity's address must be in Peru.
- You must enable both the general LATAM feature and the country/region-specific LATAM feature for Peru.
- You must download the specific report configuration from the Dataverse configuration repository. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).
- You must download the following reports from the Dataverse:

    - Ledger Accounting LATAM
    - Cash and Bank Ledger F1.1 for cash transactions
    - Cash and Bank Ledger F1.2 for bank transactions

- You must configure the Electronic reporting (ER) parameters for each report. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
- You must configure the SQL Server Reporting Services (SSRS) Reports/Services reference for each format by following these steps:

    1. In the **Report/Service ID** field, enter an ID for each report.
    1. In the **Report/Service name** field, enter a name for each report.
    1. In the **Report/Service type** field, select an ER configuration.
    1. In the **Model mapping name** field, select **Ledger Accounting LTM**.
    1. In the **Data model definition** field, select **GeneralLedger**.
    1. In the **Format mapping** field, select **Cash and Bank Ledger F1.2** or **Cash and Bank Ledger F1.1**.
    1. In the list of report/service types, enable **Taxes report and General ledger**.
    1. In the list of parameters, add **TaxApplicationId** in the **Name** column and the tax application code in the **Value** column.

    Learn more in [SSRS Reports/Services references configuration for Latin America](ltm-ssrsreport-services.md).

## Additional configuration required for Cash and Banks Ledger Format 1.2

- You must create a tax application to use with this format. Learn more in [Tax application for Latin America](ltm-core-tax-application.md).
- Enter the payment method codes in the tax application section of the document classes that you use. Learn more in [Document classes for Latin America](ltm-core-document-class.md).

## Configure application-specific parameters for both formats

To configure application-specific parameters for both the Cash and Bank Ledger F1.1 format and the Cash and Bank Ledger F1.2 format, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** \> **Workspace**, and select **Reporting configurations**.
1. In the left pane, select the format to configure.
1. On the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
1. On the **Application specific parameters** page, on the **Lookups** FastTab, select **IsApplicable**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification ID (VoucherClassId)** field, select all document classes that represent bank transactions and that should appear on the **Cash and Bank Ledger F 1.2** report. Alternatively, select all document classes that represent cash movements and that should appear on the **Cash and Bank Ledger F 1.1** report.
1. To ensure that the report shows the transactions that meet the configured conditions, set all the **Lookup result** fields as **Not Applicable** or **No**, and specify **Blank** and **Non-blank** conditions.

## Generate reports for both formats

To generate reports for both the Cash and Bank Ledger F1.1 format and the Cash and Bank Ledger F1.2 format, follow these steps:

1. In Finance, go to **General ledger** \> **Inquiries and reports** \> **LATAM** \> **General ledger**.
1. For each report format, in the **Report ID** field, select the report ID that was created.
1. In the **From date** and **To date** fields, set the date range for the report.
1. Set the **Include current layer**, **Include operation layer**, **Include tax layer**, and **Print Customer/Vendor** options to **Yes**.
1. Select **OK**.
