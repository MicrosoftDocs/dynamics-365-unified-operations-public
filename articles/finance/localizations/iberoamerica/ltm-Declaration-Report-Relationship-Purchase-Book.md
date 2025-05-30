---
title: Configure printing for Relationship purchases Book reports for Venezuela
description: Learn about the required configuration for printing Relationship purchases Book reports for Venezuela. 
author: Cpicon85
ms.date: 02/05/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-cpicon
---

# Configure printing for Relationship purchases Book reports for Venezuela

[!INCLUDE[banner](../../includes/banner.md)]

This article provides a guide on how to set up and generate the Relationship purchases Book reports for Venezuela.
The Declaration Reports Relationship purchases book in Venezuela is a document that details all purchase transactions for Formal taxpayers replacing the purchase ledger according the normative. This report must keep a monthly chronological record of transactions and include details such as the date of the transaction, number of invoices, debit notes, or credit notes for the domestic or foreign purchase of goods and receipt of services, name of each vendor, Tax identification number and total value of domestic purchases of goods and services received.

## Prerequisites
Before you complete the steps in this article to generate the report, the following prerequisites must be met:
- The legal entity's address must be in Venezuela.
- You must enable both the general Latin American (LATAM) feature and the country/region-specific LATAM feature for Venezuela.
- You must download the specific report configuration from the Dataverse configuration repository. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](gsw-import-er-config-dataverse.md). 
- You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](electronic-reporting-er-configure-parameters.md).

You must download the following reports:
* LTM Tax Report mapping
* LTM Tax Report
* Declaration Reports Relationship purchases Book VE 

## Additional configurations required for Relationship purchases Book reports:
- You must create a tax application Id. Learn more in [Tax application for Latin America](ltm-core-tax-application.md).
- You must configure withholdings in sales tax code with a negative percentage.

## Configure application-specific parameters 
To configure application-specific parameters, follow these steps.
1. Go to **Organization administration** > **Workspace** > and select **Reporting configurations**.
1. Into the LTM Tax report select the **Declaration Reports Relationship purchases Book VE** format. 
1. Go to the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
1. On the **Application specific parameters** page, on the **Lookups** tab, select **TaxType**.
1. In the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select different VAT rates, exempt and differents withholding rates.
1. On the **Application specific parameters** page, on the **Lookups** tab, select **InvoiceIsApplicable**.
1. In the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes** 
1. In Document classification Id (VoucherClassId) select all document classes that should be appear in this report.  

> [!NOTE]
> Complete each lookup with **No** or **Not applicable** conditions where you select **Blank** and **Not blank**.

## Run Relationship purchases Book reports:
To generate Relationship purchases Book reports, follow these steps.
1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
1. In the Format mapping field, enter or select the value that represent this report. Then select **OK**.
1. In the **TAX application Id** field, enter the tax application code that was created for this report.
1. In the **From** date and **To** date fields, select the date range for the report.
1. Select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
