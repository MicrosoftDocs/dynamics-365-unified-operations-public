---
title: Configure printing for Cancelled Tax Receipts Submission Form 608
description: Learn about the required configuration for printing report of Cancelled Tax Receipts Submission Form 608 of Dominican Republic 
author: Cpicon85
ms.date: 04/09/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-cpicon
---

# Configure printing for Cancelled Tax Receipts form 608 report of Dominican Republic.
This article explains how to configure CCancelled Tax Receipts form 608 report. This report will allow you to detail cancelled tax receipts.

## Prerequisites
Before you complete the steps in this article to generate the report, the following prerequisites must be met:
- The legal entity's address must be in Dominican Republic.
- Both the country/region-specific LATAM feature for Dominican Republic and the general LATAM feature must be enabled.
- You must download the specific report configuration from the Dataverse configuration repository. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md). 
- You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](/dynamics365/fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters).

## Additional configurations required for Cancelled Tax Receipts Form (608):
- You must create tax application as F608 to use on the report. See [Tax application for Latin America](ltm-core-tax-application.md).
- You must create and configure a **document class** for cancellation purposes. In this document in tax application option, add the letter **A** in letter code field. Learn more in [Document classes for Latin America]( ltm-core-document-class.md)
- Configure master **field list 7** to add and classify the Type of cancellation of your sales. In this form you could add  its respective code in tax application option.Learn more in [Field list configuration for Latin America](ltm-core-field-master-lists.md).
- You must configure in the document class of sales cancellation in additional data section select **field list 7** as required. 

## Configure application-specific parameters
To configure application-specific parameters, follow these steps.
1. Go to **Organization administration** > **Workspace** > and select **Reporting configurations**.
2. In the LTM Tax report select **Format 608 DO**, and then, on the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group select **Setup**.
3. On the **Application specific parameters** page, on the **Lookups** tab, select **DocumentsVoided**.
4. In the **Conditions** FastTab, select **Add**.
5. In the **Lookup result** field, select **Yes**.
6. In Document classification Id (VoucherClassId) select internal document classes that represent DocumentsVoided.

To ensure that the report shows the transactions that meet the configured conditions, complete the **Lookup result** fields as **Not Applicable** or **No** with **blank** and **non-blank** conditions.

## Run Format 608 DO report:

To generate the ** Format 608 DO ** report, follow these steps.
1. Go to Tax > Inquiries and reports > LATAM > Tax reporting.
2. In the Format mapping field, enter or select a value.
3. Select OK.
4. In the TAX application Id field, specify the tax application code that you created for this report.
5. In the From date field, enter a date.
6. In the To date field, enter a date.
7. Select OK.

You can generate the excel file performing the same configuration in **Format 608 (Excel)DO**
