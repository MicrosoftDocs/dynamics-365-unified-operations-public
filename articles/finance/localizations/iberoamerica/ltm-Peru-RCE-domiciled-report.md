---
title: Configure printing for the Electronic Purchase Register (RCE) for purchases domiciled in Peru
description: Learn about the required configuration for printing the Electronic Purchase Register (RCE) for purchases domiciled in Peru
author: Fhernandez0088
ms.date: 04/21/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---
# Configure printing for the Electronic Purchase Register (RCE) for purchases domiciled in Peru
This article provides a guide on how to set up and generate the various annexes (reports) for the **Electronic Purchase Register (RCE)** for purchases domiciled in Peru.
The **Electronic Purchase Register (RCE)** enables taxpayers to manage their electronic purchase records. The Peruvian fiscal authority, SUNAT, generates a monthly proposal designed to serve as a comparative tool, helping taxpayers identify discrepancies in their records.
The Electronic Purchase Register (RCE) for purchases domiciled in Peru includes annexes 8, 11, 12.8.4 and 13.5.1
The excel output version of the 13.5.1 annex is also included.

## Prerequisites
Before you can generate and print the reports, the following prerequisites must be met:
* The legal entity's address must be in Peru.
* Both the general LATAM feature and the country/region-specific LATAM feature for Peru must be enabled.
* You must download the specific report configuration from the Dataverse configuration repository. 
Learn more in [Import Electronic reporting (ER) configurations from Dataverse](https://learn.microsoft.com/dynamics365/finance/localizations/global/workspace/gsw-import-er-config-dataverse).
* You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

The RCE for domiciled purchases is composed by the following formats that you must import:
* LTM Tax Report
* LTM Tax Report mapping
* RCE-ANEXO 8
* RCE-ANEXO 11
* RCE-ANEXO 12.8.4
* RCE-ANEXO 13.5.1

## Additional configurations required for RCE:
* You must create a tax application code as SUNAT to use on the report. See [Tax application for Latin America](../ltm-core-tax-application.md).
* When configuring document classes for purchase invoices, debit notes, credit notes and DUA-DSI declaration (customs legal requirements), the tax application code must be set according to Table 3: Types of Payment Receipts or Documents from SUNAT.
* If the DAM-DSI (customs legal requirements) emission year is required for a transaction, **Concept 1** from the document class must be enabled.
* If the DAM-DSI (customs legal requirements) code from Table 4 of SUNAT is required for the transaction, use **Concept 2** field from the document class.
* It is possible to associate invoices, debit notes, credit notes and DUA-DSI declaration through Source Document if needed. Go to **Accounts payable > Inquiries and reports > Invoice > Invoice journal**. Over the desired transaction, go into de **Fast Tab** select **LATAM > Source Documents** and click **New**, add the required record.
* Set up the tax application code of the **Tax ID types** used with the table 1 codes of SUNAT. [Tax ID types for Latin America](https://learn.microsoft.com/dynamics365/finance/localizations/iberoamerica/ltm-core-tax-id-type)
* When creating a person type vendor, the **Phonetic last name** field allows you to add a second last name if required.
* Go to **General ledger > Currencies > Currencies** and complete the currency tax application code with the appropriate three-letter code from SUNAT Table 2: Currency Type.

## Configure application-specific parameters in Electronic Reporting for purchases domiciled in Peru.
1. Go to **Organization administration** > **Workspace** > and select **Reporting configurations**.
2. In the LTM Tax report group for each format mentioned above, go to the **Configurations** tab, in the **Application specific parameters** group select **Setup**.
3. On the **Application specific parameters** page, on the **Lookups** tab, select **VendorIsApplicable**.
4. In the **Conditions** FastTab, select **Add**.
5. In the **Lookup result** field, select **Yes**
6. In **Document classification Id (VoucherClassId)** field select all document classes required for vendor transactions.
7. To ensure that the report shows the transactions that meet the configured conditions, complete the **Lookup result** fields as **No** with **Blank** and **Non-blank** conditions.
8. Back to **Lookups** tab, select **TaxType**.
9. In the **Conditions** FastTab, select **Add**.
10. In the **Lookup result** field, select **IGCDG**.
11. In **Tax code** field select the General Purchase Tax code configured for taxed acquisitions exclusively intended for vat taxed operations and/or export
12. In the **Conditions** FastTab, select **Add** and in the **Lookup result** field, select **IGCDGNG**.
13. In **Tax code** field select the General Purchase Tax code configured for acquisitions intended for vat taxed operations and/or export and non-taxable operations.
14. In the **Conditions** FastTab, select **Add** and in the **Lookup result** field, select **IGCDNG**.
15. In Tax code select the General Purchase Tax code configured for taxed acquisitions not intended for vat taxed operations and/or export.
16. In the **Conditions** FastTab, select **Add** and in the **Lookup result** field, select **ICBP**.
17. In Tax code select the tax code configured for Plastic Bag Consumption Tax.
18. In the **Conditions** FastTab, select **Add** and in the **Lookup result** field, select **IMB**.
19. In Tax code select the tax code configured for transactions subject to Law benefit 31053.
20. In the **Conditions** FastTab, select **Add** and in the **Lookup result** field, select **ISC**.
21. In Tax code select the tax code configured for The Selective Consumption Tax.
22. In the **Conditions** FastTab, select **Add** and in the **Lookup result** field, select **OC**.
23. In Tax code select the tax code configured for other concepts, taxes, and charges that do not form part of the taxable base.
22. In the **Conditions** FastTab, select **Add** and in the **Lookup result** field, select **VANG**.
23. In Tax code select the tax code configured for non-taxed acquisitions.
24. To ensure that the report shows the transactions that meet the configured conditions, complete the **Lookup result** fields as **N/A** with **Blank** and **Non-blank** conditions.

## Run RCE report:
To generate any **RCE** annex report mentioned above, follow these steps.
1. Go to **Tax > Inquiries and reports > LATAM > Tax reporting**.
2. In the Format mapping field, enter or select a value. Then select **OK**.
3.  In the **TAX application Id** field, specify the tax application code created for this report.
4. In the **From date** and **To date** fields, select the date range for the report.
5. Select **OK**.

