---
title: Configure printing for the Declaration Reports Relationship Sales Book for Venezuela
description: Configure printing for the Declaration Reports Relationship Sales Book for  Venezuela
author: Cpicon85
ms.date: 05/23/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-cpicon
---

# Configure printing for the Declaration Reports Relationship Sales Book for Venezuela

[!INCLUDE[banner](../../includes/banner.md)]

This article explains how to set up and generate the Declaration Reports Relationship Sales Book for Venezuela in Microsoft Dynamics 365 Finance.
The Declaration Reports Relationship Sales Book in Venezuela is a document that details the sales transactions made by a company during a specific period. This report is essential for compliance with tax obligations, as it allows the tax authorities to verify the accuracy of the income declared and calculate the corresponding taxes. In addition, it facilitates auditing and internal control of companies, ensuring transparency and proper financial management. It is generally issued on a monthly basis and includes details such as the date of the transaction, the invoice number, the amount of the sale, the customer's name and the type of product or service sold. In Dynamics 365 Finance and Operations (D365FO), the report is issued in digital format, allowing export to formats such as Excel and PDF.

## Prerequisites

Before you can generate the report, the following prerequisites must be met:

* The legal entity's address must be in Venezuela.
* You must enable both the general Latin American (LATAM) feature and the country/region-specific LATAM feature for Venezuela.
* You must download the specific report configuration from the Dataverse configuration repository. 
Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).
* You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](electronic-reporting-er-configure-parameters.md).

You must download the following reports:
    - LTM Tax Report
    - LTM Tax Report mapping
    - Declaration Reports Relationship Sales Book VEN
   
## Additional configuration required for the Declaration Reports Relationship Sales Book for Venezuela

* You must create a **tax application code** to use on this report. Learn more in [Tax application for Latin America](ltm-core-tax-application.mp).
* You must create a **tax application code** for each document type you will use in this report.
* You must create the following **Sales point** : Manual.

## Configure application-specific parameters 

To configure application-specific parameters, follow these steps.

1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**, and select **Reporting configurations**.
1. Into the LTM Tax report group, select  the **Declaration Reports Relationship Sales Book VEN** format. 
1. On the Action Pane, in the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
1. On the **Application specific parameters** page, on the **Lookups** tab, select **TaxType**
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Tax code (TaxCode)** field, select tax codes to be used.
1. Repeat steps 6 and 7 to add as many more tax codes as you need.
1. In the **Lookup result** field, select **No**.
1. In the **Tax code (TaxCode)** field, select both **Blank** and **Non-blank** 
1. On the **Application specific parameters** page, on the **Lookups** tab, select **Invoices**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification Id (VoucherClassId)** field select all document classes that are required for customers transactions .
1. Repeat steps 13 and 14 to add as many more tax codes as you need.

> Complete each lookup with **No** or **Not applicable** conditions where you select **Blank** and **Not blank**.

## Run Declaration Reports Relationship Sales Book  for Venezuela :

To generate Declaration Reports Relationship Sales Book  for Venezuela follow these steps:

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
1. In the **Format mapping** field, enter or select the **Declaration Reports Relationship Sales Book VEN**, and then select **OK**.
1. In the **From date** and **To date** fields, specify the date range for the report.
1. Select **OK**.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
