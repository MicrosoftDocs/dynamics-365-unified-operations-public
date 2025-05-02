---
title: Configure printing for the Electronic Sales and Income Registry (RVIE) report for Peru
description: Learn about the required configuration for printing the Electronic Sales and Income Registry (RVIE) report in Peru
author: Fhernandez0088
ms.date: 05/02/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---
# Configure printing for the Electronic Sales and Income Registry (RVIE) report for Peru
This article provides a guide on how to set up and generate the Electronic Sales and Income Registry (RVIE) in Peru.
The **Electronic Sales and Income Registry (RVIE)** in Peru is a record of sales and income.
These reports are used to modify the proposed by SUNAT.
The Electronic Sales and Income Registry (RVIE) includes annexes 2, 3 and 5
The excel output version of the 5th annex is also included.

## Prerequisites
Before you can generate and print the reports, the following prerequisites must be met:
* The legal entity's address must be in Peru.
* Both the general LATAM feature and the country/region-specific LATAM feature for Peru must be enabled.
* You must download the specific report configuration from the Dataverse configuration repository. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/global/workspace/gsw-import-er-config-dataverse).
* You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

RVIE is composed by the following formats that must be imported:
* LTM Tax Report mapping
* LTM Tax Report
* RVIE-ANEXO 2
* RVIE-ANEXO 3
* RVIE-ANEXO 5
* PE Sales Vat

## Additional configurations required for RVIE:
* You must create a tax application code as SUNAT to use on the report. See [Tax application for Latin America](../ltm-core-tax-application.md).
* When configuring document classes for purchase invoices, debit notes and credit notes the tax application code must be set according to Table 3: Types of Payment Receipts or Documents from SUNAT.
* It is possible to associate debit notes and credit notes with invoices through Source Document if needed. Go to Accounts payable > Inquiries and reports > Invoice > Invoice journal. Over the desired transaction, go into de **Fast Tab** select ¨**LATAM > Source Documents** and click **New**, add the desired record.
* Set up the tax application code of the **Tax ID types** used with the table 1 codes of SUNAT. Learn more in [Tax ID types for Latin America](https://learn.microsoft.com/dynamics365/finance/localizations/iberoamerica/ltm-core-tax-id-type).
* When creating a person type customer, the **Phonetic last name** field allows you to add a second last name if required.
* Go to **General ledger > Currencies > Currencies** and complete the currency tax application code with the appropriate three-letter code from SUNAT Table 2: Currency Type.

## Configure application-specific parameters in Electronic Sales and Income Registry (RVIE)
1. Go to **Organization administration** > **Workspace** > and select **Reporting configurations**.
2. In the LTM Tax report group for each format mentioned above, go to the **Configurations** tab, in the **Application specific parameters** group select **Setup**.
3. In the **Application specific parameters** page, on the **Lookups** tab, select **CustomerInvoiceIsApplicable**.
4. In the **Conditions** FastTab, select **Add**.
5. In the **Lookup result** field, select **Yes**
6. In **Document classification Id (VoucherClassId)** field select all document classes required for customer transactions.
7. To ensure that the report shows the transactions that meet the configured conditions, complete the **Lookup result** fields as **No** with **Blank** and **Non-blank** conditions.
8. Back to **Lookups** tab, select **TaxType**.
9. In the **Conditions** FastTab, select **Add**.
10. In the **Lookup result** field, select **IGV / IPM**.
11. In **Tax code** field select the “General Sales Tax or Municipal Promotion Tax” code.
12. In the **Conditions** FastTab, select **Add** and in the **Lookup result** field, select **BIA**.
13. In **Tax code** field select the tax code configured for “Taxable base”
14. In the **Conditions** FastTab, select **Add** and in the **Lookup result** field, select **ME**.
15. In **Tax code** field select the Tax code configured for “Exempt amount”
16. In the **Conditions** FastTab, select **Add** and in the **Lookup result** field, select **MI**.
17. In **Tax code** field select the tax code configured for “Non-taxable amount”
18. In the **Conditions** FastTab, select **Add** and in the **Lookup result** field, select **OT**.
19. In **Tax code** field select the tax code configured for “Other taxes”.
20. In the **Conditions** FastTab, select **Add** and in the **Lookup result** field, select **IVAP**.
21. In **Tax code** field select the tax code configured for “Tax on sales of polished rice”.
22. In the **Conditions** FastTab, select **Add** and in the **Lookup result** field, select **ISC**.
23. In **Tax code** field select the tax code configured for “Selective Consumption Tax”.
24. In the **Conditions** FastTab, select **Add** and in the **Lookup result** field, select **ICPB**.
25. In **Tax code** field select the tax code configured for “Tax on consumption of plastic bottles”
26. In the **Conditions** FastTab, select **Add** and in the **Lookup result** field, select **VFE**.
27. In **Tax code** field select the tax code configured for “Invoiced export value”
28. To ensure that the report shows the transactions that meet the configured conditions, complete the **Lookup result** fields as **NotApplicable** with **Blank** and **Non-blank** conditions.

## Run RVIE report:
To generate any **RVIE** annex report mentioned above, follow these steps.
1. Go to **Tax > Inquiries and reports > LATAM > Tax reporting**.
2. In the Format mapping field, enter or select a value. Then select **OK**.
3.  In the **TAX application Id** field, specify the tax application code created for this report.
4. In the **From** date and **To** date fields, select the date range for the report.
5. Select **OK**.

