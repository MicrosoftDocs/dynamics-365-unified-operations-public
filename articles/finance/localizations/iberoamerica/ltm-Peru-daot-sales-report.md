---
title: Configure printing for Annual Declaration of Transactions with Third Parties (DAOT) sales report for Peru
description: Learn about the required configuration for printing an Annual Declaration of Transactions with Third Parties (DAOT) sales report for Peru
author: Fhernandez0088
ms.date: 04/16/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---
# Configure printing for Annual Declaration of Transactions with Third Parties (DAOT) sales report for Peru
This article provides a guide on how to set up and generate the Annual Declaration of Transactions with Third Parties (DAOT) sales report for Peru.
The Annual Declaration of Transactions with Third Parties (DAOT) is an informative declaration that companies must submit to SUNAT (fiscal authority in Peru). This declaration includes detailed information about transactions with vendors and customers that exceed certain value thresholds.
In this article, we will focus exclusively on the sales report.

## Prerequisites
Before you complete the steps to generate the report, the following prerequisites must be met:
* The legal entity's address must be in Peru.
* Both the general LATAM feature and the country/region-specific LATAM feature for Peru must be enabled.
* You must download the specific report configuration from the Dataverse configuration repository. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](https://learn.microsoft.com/dynamics365/finance/localizations/global/workspace/gsw-import-er-config-dataverse).
The following formats constitute the DAOT sales:
* File export DAOT Sales
* DAOT sales (Excel)

* You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Aditional configurations required for DAOT:
* You must create tax application code as SUNAT to use on the reports. See [Tax application for Latin America](../ltm-core-tax-application.md).
* Set up the tax application code of all the **Taxpayer type** used with the table 2 codes of SUNAT. [Taxpayer types for Latin America]( https://learn.microsoft.com/dynamics365/finance/localizations/iberoamerica/ltm-core-taxpayer-type)
* Set up the tax application code of all the **Tax ID types** used with the table 1 codes of SUNAT. [Tax ID types for Latin America]( https://learn.microsoft.com/dynamics365/finance/localizations/iberoamerica/ltm-core-tax-id-type).
* When creating a person type customer, the phonetic last name field allows you to add a second last name if required.

## Configure application-specific parameters for DAOT Sales and the excel-based format.
To configure application-specific parameters, follow these steps.
1. Go to **Organization administration** > **Workspace** > and select **Reporting configurations**.
2. In the LTM Tax report and for each format mentioned above, on the **Configurations** tab, in the **Application specific parameters** group select **Setup**.
3. On the **Application specific parameters** page, on the **Lookups** tab, select **CustomerApplicableInvoices**.
4. In the **Conditions** FastTab, select **Add**.
5. In the **Lookup result** field, select **Yes**
6. In **Document classification Id (VoucherClassId)** field select all document classes required for customer transactions.
7. To ensure that the report shows the transactions that meet the configured conditions, complete the **Lookup result** fields as **No** with **Blank** and **Non-blank** conditions.
8. Back to **Lookups** tab, select **TaxType**.
9. In the **Conditions** FastTab, select **Add**.
10. In the **Lookup result** field, select **VAT**.
11. In **Tax code** field select the tax code configured for General Sales Tax
12. To ensure that the report shows the transactions that meet the configured conditions, complete the **Lookup result** fields as **N/A** with **Blank** and **Non-blank** conditions.

## Run DAOT report:
To generate any ** DAOT ** format report mentioned above, follow these steps.
1. Go to **Tax > Inquiries and reports > LATAM > Tax reporting**.
2. In the Format mapping field, enter or select any format mentioned above. Then select **OK**.
3.  In the **TAX application Id** field, specify the tax application code created for this report.
4. In the From date and To date fields, select the date range for the report.
5. Select **OK**.

