---
title: Configure printing for the ISRL Withholding report for Venezuela
description: Learn how to configure printing for the ISRL Withholding report for Venezuela.
author: Cpicon85
ms.date: 05/30/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-Cpicon85
---

# Configure printing for the ISRL Withholding report for Venezuela

[!INCLUDE[banner](../includes/banner.md)]

This article explains how to configure the ISRL Withholding report for Venezuela in Microsoft Dynamics 365 Finance.

The ISRL Withholding report for Venezuela downloads information about transactions that include withholdings of income taxes, known as **Impuesto sobre la Renta (ISLR)**. The downloaded information is in the presentation structure that is requested by the tax authority **SENIAT**.

## Prerequisites

Before you can generate and print the report, the following prerequisites must be met:

* The legal entity's address must be in Venezuela.
* In Feature management workspace, verify that the LATAM globalization expansion and LATAM globalization expansion – Venezuela features are enabled.
* You must download the specific report configuration from the Dataverse configuration repository. 
Learn more in [Import Electronic reporting (ER) configurations from Dataverse](gsw-import-er-config-dataverse.md).
* You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](electronic-reporting-er-configure-parameters.md).

The following formats constitute the ISRL Withholding report:

* LTM Tax Report
* LTM Tax Report mapping
* File Export ISLR Withholdings


## Additional configuration required for the ISRL Withholding report

- You must create a **tax application code** to use on this report. Learn more in [Tax application for Latin America](ltm-core-tax-application.md).
- Enter the withholding tax fiscal code according to the fiscal authority in the **Tax income** field from the **Tax application** form of the sales tax codes used as ISLR withholding taxes.


## Configure application-specific parameters for the ISRL Withholding report

To configure application-specific parameters, follow these steps.

1. Go to **Organization administration** > **Workspace** > and select **Reporting configurations**.
1. Into the LTM Tax report group, select the **File Export ISLR Withholdings** format. 
1. Go to the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
1. On the **Application specific parameters** page, on the **Lookups** tab, select **VendorApplicableInvoices**.
1. In the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**
1. In **Document classification Id (VoucherClassId)** field select all document classes required for vendor transactions.
1. To ensure that the report shows the transactions that meet the configured conditions, complete the **Lookup result** fields as **No** with **Blank** and **Non-blank** conditions.
1. On the **Application specific parameters** page, on the **Lookups** tab, select **ApplicableTax**.
1. In the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**
1. In **Tax code (TaxCode)** field select all tax codes required for withholdings on vendor transactions.
1. To ensure that the report shows the transactions that meet the configured conditions, complete the **Lookup result** fields as **No** with **Blank** and **Non-blank** conditions.

## Generate the ISRL Withholding report

To generate the ISRL Withholding report follow these steps.

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
1. In the **Format mapping** field, enter or select the **ISRL Withholding report**, and then select **OK**.
1. In the **TAX application Id** field, enter the tax application code that was created for this report.
1. In the **From date** and **To date** fields, specify the date range for the report.
1. Select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
