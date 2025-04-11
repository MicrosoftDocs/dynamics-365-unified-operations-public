---
title: Configure printing for Goods and Services Purchases Submission Form 606
description: Learn about the required configuration for printing Goods and Services Purchases Submission Form 606 for the Dominican Republic
author: Cpicon85
ms.date: 04/14/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-cpicon
---

# Configure printing Goods and Services Purchases 606 report of Dominican Republic.

[!INCLUDE[banner](../../includes/banner.md)]

This article explains how to configure Goods and Services Purchase Submission Form (606) so it can be printed. Purchase transactions records that companies use to keep a detailed record of their operations indicate the vendor information and document details. If applicable, they also indicate the corresponding taxes and tax withholdings, including local and foreign transactions and other mandatory information that the regulations specify.

## Prerequisites

Before you complete the steps in this article to generate the report, the following prerequisites must be met:

- The legal entity's address must be in Dominican Republic.
- Both the country/region-specific LATAM feature for Dominican Republic and the general LATAM feature must be enabled.
- You must download the specific report configuration from the Dataverse configuration repository. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md). 
- You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](/dynamics365/fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters).

## Other configurations required for Goods and Services Purchase Submission Form (606) report

- You must create tax application as F606 to use on the report. See [Tax application for Latin America](../ltm-core-tax-application.md).
- Configure master field list: first **list 2** for Type of Goods and Services Purchased with its respective code and then, configure field **list 3** for Method of Payment with its respective code in tax application code. Learn more in [Field list configuration for Latin America](ltm-core-field-master-lists.md).
- You must create sales tax codes, one for purchases and one for services that will be used for Tax on Transfers of Industrialized Goods and Services (ITBIS), including ITBIS 18% and ITBIS 0% (goods and services respectively). Also remember to use a code, for ITBIS taken to cost and one for ITBIS subject to proportionality.
- Once you create sales tax codes, follow these steps.
   1. Go to **Tax > indirect tax  > sales tax > sales tax codes**.
   1. Select a sales tax. 
   1. On the Action Pane, select **Tax application**.
   1. In the **Tax application ID** field, verify that F606 is entered.
   1. In the **Income tax code** field, enter **C** for **ITBIS taken to cost** or **P** for **ITBIS subject to proportionality**.
- You must configure LATAM withholding tax codes and set tax application code for income withholding and ITBIS withholdings if you need it. 
- You must configure in documentthe document class of purchase transactions (invoices, debit notes or credit notes) in additional data section Field list, **list field 2** and **3** as required. 
- You must create a special document class for foreign service payments as a purchase document. To configure the country identification number of the foreign vendor, go to **Address setup** > **country/region** > **latam** > **Country per taxpayer type identification**. You will need a **Tax Id Type** configurated as Not foreign document type and complete the country identification number with the number of the legal entity. When you use this document, income withholdings made to foreign vendor will not be shown in this report.  

## Configure application-specific parameters

To configure application-specific parameters, follow these steps. 
1. Go to **Organization administration** > **Workspace** > and select **Reporting configurations**.
1. In the LTM Tax report select **Format 606 DO**, and then, on the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group select **Setup**.
1. On the **Application specific parameters** page, on the **Lookups** tab, select **VendorApplicableInvoices**.
1. In the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**
1. In Document classification Id (VoucherClassId) select all document classes received from vendors including special document class for foreign service payments
1. Back to **Lookups** tab, select **Withholdings**.
1. In the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Income** 
1. In Document classification Id (VoucherClassId) select all document classes for each of income withholdings. 
1. In the **Lookup result** field, select **ITBIS**
1. In Document classification Id (VoucherClassId) select all document classes for each of ITBIS withholdings.
1. Back to **Lookups** tab, select **TaxType**.
1. In the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Products**.
1. In **Tax Code** select all sales tax code created for products.
1. In the **Lookup result** field, select **Services**.
1. In Tax Code select all sales tax code created for Services.
To ensure that the report shows the transactions that meet the configured conditions, complete the **Lookup result** fields as **Not Applicable** or **No** with **blank** and **non-blank** conditions

## Run Format 606 DO report:

To generate the **Format 606 DO** report, follow these steps.

1. Go to **Tax > Inquiries and reports > LATAM > Tax reporting**.
1. In the **Format mapping** field, enter or select a value.
1. Select **OK**.
1. In the **TAX application ID** field, specify the tax application code that you created for this report.
1. In the **From date** field, enter a date.
1. In the **To date** field, enter a date.
1. Select **OK**.

You can generate the excel file performing the same configuration in **Format 606 (Excel)DO**

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
