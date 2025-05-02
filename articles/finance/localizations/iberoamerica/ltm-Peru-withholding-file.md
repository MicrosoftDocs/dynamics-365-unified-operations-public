---
title: Configure printing for IGV withholding tax report for Peru
description: Learn about the required configuration for printing IGV withholdings tax report, Form 626 for Peru. 
author: Fhernandez0088
ms.date: 02/05/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Configure printing for IGV withholding tax report for Peru

This article explains how to set up and generate IGV withholding tax report (Form 626) in txt format for Peru.

The Withholding Agent must declare the total amount of withholdings made during the month and make the respective payment using Virtual Form No. 626. If, for reasons beyond your control, you cannot use this form, you must generate the txt format of 626 - IGV Withholdings using this report.

## Prerequisites
Before you complete the steps in this article to generate the report, the following prerequisites must be met:
- The legal entity's address must be in Peru.
- Both the country/region-specific LATAM feature for Peru and the general LATAM feature must be enabled.
- You must download the specific report configuration from the Dataverse configuration repository. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](https://learn.microsoft.com/dynamics365/finance/localizations/global/workspace/gsw-import-er-config-dataverse). 
- You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
You must download the following formats:
* LTM Tax Report mapping
* LTM Tax Report
* Withholdings (PER) txt
* Withholdings (PER) excel

## Aditional configurations required for IGV withholding tax report, form 626:
- You must create a tax application id for these reports to indicate different codes of document classes thar represent invoices, credit and debit notes and others. See [Tax application for Latin America](../ltm-core-tax-application.md).
- You must configure LATAM withholding tax codes and use the LATAM feature for tax withholdings.
- You must configure a document class as a payment order with the source exchange rate option set to **Yes** so that the withholdings taxes are calculated with the exchange rate of the invoice. Learn more in [Document classes for Latin America](https://learn.microsoft.com/dynamics365/finance/localizations/iberoamerica/ltm-core-document-class).

## Configure application-specific parameters
To configure application-specific parameters, follow these steps.
1. Go to **Organization administration** > **Workspace** > and select **Reporting configurations**.
2. In the LTM Tax report select the desired format, and then, on the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group select **Setup**.
3. On the **Application specific parameters** page, on the **Lookups** tab, select **VendorInvoiceIsApplicable**.
4. In the **Conditions** FastTab, select **Add**.
5. In the **Lookup result** field, select **Yes**
6. In Document classification Id (VoucherClassId) select all document classes that should appear in the report
7. Back to **Lookups** tab, select **Withholdings**.
8. In the **Conditions** FastTab, select **Add**.
9. In the **Lookup result** field, select **Withholding** 
10. In Document classification Id (VoucherClassId) select the document classes that represent VAT withholdings taxes that should appear in the report. 
To ensure that the report shows the transactions that meet the configured conditions, complete the **Lookup result** fields as **Not Applicable** or **No** with **blank** and **non-blank** conditions

## Run IGV withholding reports:
To generate any IGV withholding report mentioned above, follow these steps.
1. Go to **Tax > Inquiries and reports > LATAM > Tax reporting**.
2. In the Format mapping field, enter or select a value. Then select **OK**.
3.  In the **TAX application Id** field, specify the tax application code created for this report.
4. In the **From** date and **To** date fields, select the date range for the report.
5. Select **OK**.

