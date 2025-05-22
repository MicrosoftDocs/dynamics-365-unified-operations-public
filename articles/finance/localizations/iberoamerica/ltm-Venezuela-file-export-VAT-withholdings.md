---
title: Configure printing for the VAT Withholding report in Venezuela
description: Configure printing for the VAT Withholding report in Venezuela
author: Cpicon85
ms.date: 05/21/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-Cpicon85
---
# Configure printing for the VAT Withholding report in Venezuela

This article explains how to set up and generate the VAT withholding report for Venezuela in Microsoft Dynamics 365 Finance.
This document holds information about the withholdings generated from vendor invoices, debit notes, and credit notes.

## Prerequisites

Before you can generate the report, the following prerequisites must be met:

* The legal entity's address must be in Venezuela.
* You must enable both the general Latin American (LATAM) feature and the country/region-specific LATAM feature for Venezuela.
* You must download the specific report configuration from the Dataverse configuration repository. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](gsw-import-er-config-dataverse.md).

    The following formats constitute VAT Withholding report:
    - LTM Tax Report
    - LTM Tax Report mapping
    - File Export VAT Withholdings (VE)
   
* You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](electronic-reporting-er-configure-parameters.md).

## Additional configuration required for the VAT withholding report

* You must create a **tax application code** to use on this report. Learn more in [Tax application for Latin America](ltm-core-tax-application).
* Enter the withholding tax fiscal code according to the fiscal authority in the Tax income field from the **Tax application** form of the sales tax codes used as VAT withholding taxes.
* Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class** \> **Tax application** and enter the code establish by the fiscal authority for invoice, debit and credit note.


## Configure application-specific parameters for the VAT withholding report

To configure application-specific parameters, follow these steps.

1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**, and select **Reporting configurations**.
2. Into the LTM Tax report group, select the **File Export VAT Withholdings** format. 
3. On the Action Pane, in the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
4. On the **Lookups** FastTab, select **WithholdingTax**.
5. On the **Conditions** FastTab, select **Add**.
6. In the **Lookup result** field, select **Withholding**.
7. In the **Tax code** field, select the tax codes that are used as VAT withholding taxes.
8. On the **Lookups** FastTab, select **VendorApplicableInvoices**.
9. On the **Conditions** FastTab, select **Add**.
10. In the **Lookup result** field, select **Yes**.
11. In the **Document classification Id (VoucherClassId)** field, select all document classes that are required for vendor transactions (invoices, debit notes and credit notes).
> [!NOTE]
> Complete each lookup with **No** or **Not applicable** conditions where you select **Blank** and **Not blank**.


## Generate the VAT withholding report

To generate the Report follow these steps.

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
1. In the **Format mapping** field, enter or select the **File Export VAT Withholdings (VE)**, and then select **OK**.
1. In the **TAX application Id** field, enter the tax application code that was created for this report.
1. In the **From date** and **To date** fields, specify the date range for the report.
1. Select **OK**.
