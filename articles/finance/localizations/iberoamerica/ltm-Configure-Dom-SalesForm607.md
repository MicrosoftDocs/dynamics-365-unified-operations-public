---
title: Configure printing Goods and Services sales Submission Form 607
description: Learn about the required configuration for printing report of Goods and Services sales Submission Form 607 for the Dominican Republic 
author: Cpicon85
ms.date: 04/14/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-cpicon
---

# Configure printing for report of sales of Goods and services Form 607 for Dominican Republic.

[!INCLUDE[banner](../../includes/banner.md)]

This article explains how to configure the Goods and Services Sales Submission Form (607) so it can be printed. Sales transactions records that companies use keep a detailed record of their operations. For each transaction, these records indicate the customer information and document details. If applicable, the records also indicate the corresponding taxes and tax withholdings.

## Prerequisites

Before you complete the steps in this article to generate the report, the following prerequisites must be met:

- The legal entity's address must be in Dominican Republic.
- Both the country/region-specific LATAM feature for Dominican Republic and the general LATAM feature must be enabled.
- You must download the specific report configuration from the Dataverse configuration repository. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md). 
- You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](/dynamics365/fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters).

## Other configurations required for Goods and Services Sales Submission Form (607)

- You must create tax application as F607 to use on the report. Learn more in [Tax application for Latin America](ltm-core-tax-application.md).
- Configure master field list 1 to add and classify the Type of Income of your sales. In this form you could add  its respective code in tax application option. Learn more in [Field list configuration for Latin America](ltm-core-field-master-lists.md).
- You must create sales tax codes that will be used for Tax on Transfers of Industrialized Goods and Services (ITBIS), including ITBIS 18% and ITBIS 0% (goods and services respectively). 
- You must create and configure one document class payment media for each type, for example, cash, bank transfer, etc. Learn more in [Document classes for Latin America](ltm-core-document-class.md). Then, in tax application option you must configure with one of the following list:
  
     |Document class payment| Code |
     |--|--|
     |Cash| E|
     |Check, bank transfer, deposit| D|
     |Debit or credit card| C|
     |Bonds or Gift Certificates|B|
     |Swap| P|
     |Other forms of sales| O|


- You must configure in the document class of sales transactions (invoices, debit notes or credit notes) in additional data section **field list>field 1** as required. 

## Configure application-specific parameters

To configure application-specific parameters, follow these steps.

1. Go to **Organization administration** > **Workspace** > and select **Reporting configurations**.
1. In the LTM Tax report select **Format 607 DO**, and then, on the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group select **Setup**.
1. On the **Application specific parameters** page, on the **Lookups** tab, select **CustomerApplicableInvoices**.
1. In the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**
1. In Document classification Id (VoucherClassId) select all document classes that represent sales (invoice, debit and credit note)
1. Back to **Lookups** tab, select **Withholdings**.
1. In the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Income** 
1. In Document classification Id (VoucherClassId) select all document classes for each of income withholdings. 
1. In the **Lookup result** field, select **ITBIS**
1. In Document classification Id (VoucherClassId) select all document classes for each of ITBIS withholdings.
1. Back to **Lookups** tab, select **TaxType**.
1. In the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **ITBIS**.
1. In **Tax Code** select all sales tax code created for ITBIS tax.
1. Repeat steps 15 and 16 for each column of the report.

To ensure that the report shows the transactions that meet the configured conditions, complete the **Lookup result** fields as **Not Applicable** or **No** with **blank** and **non-blank** conditions

## Run Format 607 DO report:

To generate the **Format 607 DO** report, follow these steps.

1. Go to **Tax > Inquiries and reports > LATAM > Tax reporting**.
1. In the **Format mapping** field, enter or select a value.
1. Select **OK**.
1. In the **TAX application ID** field, specify the tax application code that you created for this report.
1. In the **From date** field, enter a date.
1. In the **To date** field, enter a date.
1. Select **OK**.
   
You can generate the excel file performing the same configuration in **Format 607 (Excel)DO**

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
