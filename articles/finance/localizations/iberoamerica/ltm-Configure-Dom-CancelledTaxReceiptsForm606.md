---
title: Configure printing for Cancelled Tax Receipts Submission Form 608
description: Learn about the required configuration for printing Cancelled Tax Receipts Submission Form 608 for the Dominican Republic.
author: Cpicon85
ms.date: 04/09/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-cpicon
---

# Configure printing for Cancelled Tax Receipts Submission Form 608

[!INCLUDE[banner](../../includes/banner.md)]

This article explains how to configure Cancelled Tax Receipts Submission Form 608 so that it can be printed as a report (**Format 608 DO**). You can use this report for details of canceled tax receipts.

## Prerequisites

Before you can generate the **Format 608 DO** report, the following prerequisites must be met:

- The legal entity's address must be in the Dominican Republic.
- Both the country/region-specific LATAM feature for the Dominican Republic and the general LATAM feature must be enabled.
- You must download the specific report configuration from the Microsoft Dataverse configuration repository. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).
- You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](/dynamics365/fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters).

## Other required configuration for the Format 608 DO report

- You must create a tax application to use on the report. The tax application ID must be set to **F608**. Learn more in [Tax application for Latin America](../ltm-core-tax-application.md).
- You must create and configure a document class for cancellation purposes. In the document, in the **Tax application** option, in the **Letter code** field, add the letter **A**. Learn more in [Document classes for Latin America]( ltm-core-document-class.md).
- Configure master field list 7 to add and classify the type of cancellation for your sales. You can add the corresponding code in the **Tax application** option. Learn more in [Field list configuration for Latin America](ltm-core-field-master-lists.md).
- In the document class for sales cancellation, in the **Additional data** section, you must configure field list 7 as required.

## Configure application-specific parameters

To configure application-specific parameters, follow these steps.

1. Go to **Organization administration** \> **Workspace**, and select **Reporting configurations**.
1. In the **LTM Tax** report, select **Format 608 DO**. Then, on the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
1. On the **Application specific parameters** page, on the **Lookups** tab, select **DocumentsVoided**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification Id** (**VoucherClassId**) field, select the internal document classes that represent **DocumentsVoided**.

> [!NOTE]
> To ensure that the report shows the transactions that meet the configured conditions, complete the **Lookup result** fields as **Not Applicable** or **No**, with **blank** and **non-blank** conditions.

## Run the Format 608 DO report

To generate the **Format 608 DO** report, follow these steps.

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
1. In the **Format mapping** field, enter or select a value.
1. Select **OK**.
1. In the **TAX application ID** field, specify the tax application code that you created for this report.
1. In the **From date** field, enter a date.
1. In the **To date** field, enter a date.
1. Select **OK**.

You can generate an Excel file by doing the same configuration in **Format 608 (Excel)DO**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
