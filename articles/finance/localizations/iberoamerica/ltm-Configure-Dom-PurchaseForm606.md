---
title: Configure printing for Goods and Services Purchases Submission Form 606
description: Learn about the required configuration for printing a Purchase Bank Book report for Bolivia. Dominican Republic
author: Cpicon85
ms.date: 03/04/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-Cpicon85
---

# Configure printing for Goods and Services Purchases 606 report of Dominican Republic.

This article explains how to configure Goods and Services Purchase Submission Form (606) so that it can be printed. Purchase transactions records that companies use to keep a detailed record of their operations. For each transaction, these records indicate the vendor information and document details. If applicable, they also indicate the corresponding taxes and tax withholdings, including local and foreign transactions and other mandatory information that the regulations specify.

## Prerequisites
Before you complete the steps in this article to generate the report, the following prerequisites must be met:
- The legal entity's address must be in Dominican Republic.
- Both the country/region-specific LATAM feature for Dominican Republic and the general LATAM feature must be enabled.
- You must download the specific report configuration from the Dataverse configuration repository. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](gsw-import-er-config-dataverse.md). 
- You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](electronic-reporting-er-configure-parameters.md).

## Aditional configurations required for Goods and Services Purchase Submission Form (606) report:
- You must create tax application as F606 to use on the report. See [Tax application for Latin America](../ltm-core-tax-application.md).
- Configure master field list: master list 2 for Type of Goods and Services Purchased with its respective code in reference code as specified by the regulation and You must configure fields master list 3 for Method of Payment with its respective code in tax application code 
and fields master list 2 for Type of Goods and Services Purchased with its respective code in reference code as specified by the regulation. See [Field list configuration for Latin America](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/iberoamerica/ltm-core-field-master-lists).
- You must create the same sales tax codes, one for purchases and one for services that will be used for Tax on Transfers of Industrialized Goods and Services (ITBIS), including ITBIS 18% and ITBIS 0% (goods and services respectively) . Also remember to use a code , and for each of these you must create the same sales tax code, one general, one for ITBIS taken to cost and one for ITBIS subject to proportionality.
- You must configure the tax application code of the sales tax code for purchase of goods without Income tax code if ITBIS is to advance, with Income tax code C for ITBIS taken to cost and with Income tax code P for ITBIS subject to proportionality.repetido
- Go to Tax> indirect tax  > sales tax > sales tax codes.
Select a sales tax 
On the Action Pane, select Tax application.
In the Tax application ID field, verify that F606 is entered.
In the Income tax code field, enter C You must configure the tax application code of the sales tax code for services without Income tax code if ITBIS is to advance, with Income tax code C for ITBIS taken to cost and with Income tax codeor  P for ITBIS subject to proportionality.
- You must configure LATAM withtholding tax codes and set tax application code for income withholding tax code as specified by the regulation. See [Set up withholding tax] (https://learn.microsoft.com/en-us/dynamics365/finance/general-ledger/tasks/set-up-withholding-tax)
- You must configure in documentthe document class of purchase transactions (invoices, debit notes or credit notes) in additional data section field 2 and field 3 as required. 
- You must create a special document class for foreign service payments as a purchase document. To configure the country identification number of thefor a foreign vendor, go to **Address setup** > **country/region** > **latam** > **Country per taxpayer type identification**. You will need a **Tax Id Type** configurated as Not foreign document type and complete the country identification number with the number of the legal entity. When you use this document, income withholdings made to foreign vendor will not be shown in this report.  

## Configure application-specific parameters
To configure application-specific parameters, follow these steps.
1. Go to **Organization administration** > **Workspace** > and select **Reporting configurations**.
2. In the LTM Tax report select **Format 606 DO**, and then, on the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group select **Setup**.
3. On the **Application specific parameters** page, on the **Lookups** tab, select **VendorApplicableInvoices**.
4. In the **Conditions** FastTab, select **Add**.
5. In the **Lookup result** field, select **Yes**
6. In Document classification Id (VoucherClassId) select all document classes received from vendors including special document class for foreign service payments
7. Back to **Lookups** tab, select **Withholdings**.
8. In the **Conditions** FastTab, select **Add**.
9. In the **Lookup result** field, select **Income** 
10. In Document classification Id (VoucherClassId) select all document classes for each of income withholdings. 
11. In the **Lookup result** field, select **ITBIS**
12. In Document classification Id (VoucherClassId) select all document classes for each of ITBIS withholdings.
12. Back to **Lookups** tab, select **TaxType**.
13. In the **Conditions** FastTab, select **Add**.
13. In the **Lookup result** field, select **Products**.
10. In Tax Code select all  sales tax code created for products.
13. In the **Lookup result** field, select **Services**.
14. In Tax Code select all sales tax code created for Services.
To ensure that the report shows the transactions that meet the configured conditions, complete the **Lookup result** fields as **Not Applicable** or **No** with **blank** and **non-blank** conditions

## Run Format 606 DO report:

To generate the ** Format 606 DO ** report, follow these steps.

1. Go to **Tax > Inquiries and reports > LATAM > Tax reporting**.
2. In the Format mapping field, enter or select a value.
3. Select OK.
4. In the TAX application Id field, specify the tax application code that you created for this report.
5. In the From date field, enter a date.
6. In the To date field, enter a date.
7. Select OK.

You can generate the excel file performing the same configuration in **Format 606 (Excel)DO**
