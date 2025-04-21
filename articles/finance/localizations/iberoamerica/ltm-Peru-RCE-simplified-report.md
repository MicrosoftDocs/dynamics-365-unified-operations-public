---
title: Configure printing for the simplified annex of the Electronic Purchase Register (RCE) for Peru
description: Learn about the required configuration for printing the simplified annex of the Electronic Purchase Register (RCE) for Peru
author: Fhernandez0088
ms.date: 04/21/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---
# Configure printing for the simplified annex of the Electronic Purchase Register (RCE) in Peru
This article provides a guide on how to set up and issue the simplified annex of the **Electronic Purchase Register (RCE)** in Peru.
The **Electronic Purchase Register (RCE)** enables taxpayers to manage their electronic purchase records. The Peruvian fiscal authority, SUNAT, generates a monthly proposal designed to serve as a comparative tool, helping taxpayers identify discrepancies in their records.
The simplified version of the Electronic Purchase Register (RCE) is composed by the 13.5.3 annex.
The excel output version is also included.

## Prerequisites
Before you can generate and print the reports, the following prerequisites must be met:
* The legal entity's address must be in Peru.
* Both the general LATAM feature and the country/region-specific LATAM feature for Peru must be enabled.
* You must download the specific report configuration from the Dataverse configuration repository. 
Learn more in [Import Electronic reporting (ER) configurations from Dataverse](https://learn.microsoft.com/dynamics365/finance/localizations/global/workspace/gsw-import-er-config-dataverse).
* You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

The simplified annex for RCE is composed by the following formats that you must import:
* LTM Tax Report
* LTM Tax Report mapping
* RCE-ANEXO 13.5.3
* PE Simply Purchase Register

## Additional configurations required for RCE:
* You must create a tax application code as SUNAT to use on the report. See [Tax application for Latin America](../ltm-core-tax-application.md).
* When configuring document classes for purchase invoices, debit notes and credit notes, the tax application code must be set according to Table 3: Types of Payment Receipts or Documents from SUNAT.
* It is possible to associate invoices, debit notes and credit notes through Source Document if needed. Go to **Accounts payable > Inquiries and reports > Invoice > Invoice journal**. Over the desired transaction, go into de **Fast Tab** select **LATAM > Source Documents** and click **New**, add the required record.
* Set up the tax application code of the **Tax ID types** used with the table 1 codes of SUNAT. [Tax ID types for Latin America]( https://learn.microsoft.com/dynamics365/finance/localizations/iberoamerica/ltm-core-tax-id-type)
* When creating a person type vendor, the **Phonetic last name** field allows you to add a second last name if required.
* Go to **General ledger > Currencies > Currencies** and complete the currency tax application code with the appropriate three-letter code from SUNAT Table 2: Currency Type.

## Configure application-specific parameters in Electronic Reporting for the simplified annex.
To configure application-specific parameters, follow these steps.
1. Go to **Organization administration** > **Workspace** > and select **Reporting configurations**.
2. In the LTM Tax report group for each format mentioned above, go to the **Configurations** tab, in the **Application specific parameters** group select **Setup**.
3. On the **Application specific parameters** page, in the **Lookups** tab, select **VendorIsApplicable**.
4. In the **Conditions** FastTab, select **Add**.
5. In the **Lookup result** field, select **Yes**
6. In **Document classification Id (VoucherClassId)** field select all document classes required for vendor transactions.
7. To ensure that the report shows the transactions that meet the configured conditions, complete the **Lookup result** fields as **No** with **Blank** and **Non-blank** conditions.
8. Back to **Lookups** tab, select **TaxType**.
9. In the **Conditions** FastTab, select **Add**.
10. In the **Lookup result** field, select **IGCDG**.
11. In Tax code select the tax code configured for taxed acquisitions exclusively intended for vat taxed operations and/or export.
12. In the **Conditions** FastTab, select **Add** and in the **Lookup result** field, select **ICBP**.
13. In Tax code select the tax code configured for Plastic Bag Consumption Tax.
14. In the **Conditions** FastTab, select **Add** and in the **Lookup result** field, select **OC**.
15. In Tax code select the tax code configured for other concepts, taxes, and charges that do not form part of the taxable base.
16. To ensure that the report shows the transactions that meet the configured conditions, complete the **Lookup result** fields as **N/A** with **Blank** and **Non-blank** conditions.

## Run RCE report:
To generate any **RCE** annex report, follow these steps.
1. Go to **Tax > Inquiries and reports > LATAM > Tax reporting**.
2. In the Format mapping field, enter or select a value. Then select **OK**.
3.  In the **TAX application Id** field, specify the tax application code created for this report.
4. In the **From date** and **To date** fields, select the date range for the report.
5. Select **OK**.

