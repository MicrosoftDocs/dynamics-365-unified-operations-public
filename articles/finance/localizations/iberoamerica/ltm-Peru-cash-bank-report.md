---
title: Configure printing for Cash And Banks Ledger reports for Peru
description: Learn about the required configuration for printing the Cash and Banks Ledger reports Peru. 
author: Fhernandez0088
ms.date: 02/05/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Configure printing for Cash And Banks Ledger reports for Peru

This article explains how to set up and generate Cash and Banks Ledger formats for Peru:
Cash and Bank Ledger F1.1 for cash transactions.
Cash and Bank Ledger F1.2 for bank transactions.
 
In these books, all the information from the movement of cash and cash equivalents (Banks) must be recorded monthly, in order to keep an updated control of the company's financial transactions.

## Prerequisites
Before you complete the steps in this article to generate the report, the following prerequisites must be met:
- The legal entity's address must be in Peru.
- Both the country/region-specific LATAM feature for Peru and the general LATAM feature must be enabled.
- You must download the specific report configuration from the Dataverse configuration repository. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](https://learn.microsoft.com/dynamics365/finance/localizations/global/workspace/gsw-import-er-config-dataverse). 
- You must download the following reports from the Dataverse:
    * Ledger Accounting LATAM
    * Cash and Bank Ledger F1.1 for cash transactions
    * Cash and Bank Ledger F1.2 for bank transactions    

- You must configure the Electronic reporting (ER) parameters for each report. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
- You must configure **SSRS Reports/Services reference** for each format following these steps:
  * In the Report/Service Id field, enter an Id for each report.
  * In the Report/Service name field, enter a name for each report.
  * In the Report/Service type field, select an ER configuration.
  * In the Model mapping name field, select Ledger Accounting LTM.
  * In the Data model definition field, select GeneralLedger.
  * In the Format mapping field, select Cash and Bank Ledger F1.2 or Cash and Bank Ledger F1.1.
  * In the list of report/service types, enable Taxes report and General ledger.
  * In the list of Parameters add **TaxApplicationId** to the **Name** column, and the tax application code created in the **Value** column
Learn more in [SSRS Reports/Services references configuration for Latin America]( https://learn.microsoft.com/dynamics365/finance/localizations/iberoamerica/ltm-ssrsreport-services)
## Additional configurations required for Cash And Banks Ledger Format 1.2:
- You must create a tax application to use with this format. See [Tax application for Latin America](../ltm-core-tax-application.md).
- Enter the payment method codes in the tax application section of the document classes used as such. [Document classes for Latin Americahttps://learn.microsoft.com/dynamics365/finance/localizations/iberoamerica/ltm-core-document-class)

## Configure application-specific parameters for both formats
To configure application-specific parameters, follow these steps.
1. Go to **Organization administration** > **Workspace** > and select **Reporting configurations**.
2. On the left section select the format to be configured.
2. Go to the **Configurations** tab, in the **Application specific parameters** group select **Setup**.
3. On the **Application specific parameters** page, on the **Lookups** tab, select **IsApplicable**.
4. In the **Conditions** FastTab, select **Add**.
5. In the **Lookup result** field, select **Yes**
6. In Document classification Id (VoucherClassId) field select all document classes that represent bank transactions and should appear in the **Cash and Bank Ledger F 1.2** report or select all document classes that represent cash movements and should appear in the **Cash and Bank Ledger F 1.1** report.

To ensure that the report shows the transactions that meet the configured conditions, complete the **Lookup result** fields as **Not Applicable** or **No** with **blank** and **non-blank** conditions.

## Run Cash and Bank Ledger F 1.2 report or Cash and Bank Ledger F 1.1

To generate the reports follow these steps.
1. Go to **General ledger>inquiries and reports>LATAM>General ledger**.
2. Select the Report Id field with the Report Id created for each report.
3. In the **From date** and **To date** fields, specify the date range to include in the report.
4. Select **YES** in the following options Include current layer, Include operation layer, Include tax layer, Print Customer/Vendor.
5. Select **OK**.


