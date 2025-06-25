---
title: Configure printing for the VAT withholding certificate for Venezuela
description: Learn how to set up and generate the value-added tax (VAT) withholding certificate for Venezuela.
author: Cpicon85
ms.date: 05/22/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-cpicon
---

# Configure printing for the VAT withholding certificate for Venezuela

[!include [banner](../../includes/banner.md)]

This article explains how to set up and generate the value-added tax (VAT) withholding certificate for Venezuela in Microsoft Dynamics 365 Finance. This document contains information about the withholdings that are generated from vendor invoices, debit notes, and credit notes.

## Prerequisites

Before you can generate the report, the following prerequisites must be met:

- The legal entity's address must be in Venezuela.
- You must enable both the general Latin American (LATAM) feature and the country/region-specific LATAM feature for Venezuela.
- You must download the specific report configuration from the Dataverse configuration repository. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

    The following formats constitute the VAT withholding certificate:

    - LTM Tax Report
    - LTM Tax Report mapping
    - VAT withholding certificate

- You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Additional configuration required for the VAT withholding certificate

- You must create a **tax application code** to use on this report. Learn more in [Tax application for Latin America](ltm-core-tax-application.md).
- Follow these steps to configure the applicable VAT and withholding tax rates and codes according to your requirements:

    1. Go to **Tax** \> **Indirect tax** \> **Sales tax**\> **Sales tax codes**\> **Latam**.
    1. On the Action Pane, select **Tax application**.
    1. In the **Tax application ID** field, enter the tax application code that was created for this report.
    1. In the **Income tax code** field, enter **IVA**.
    1. In the **Code regime** field, enter **16** if you're configuring VAT 16% rate.


## Configure application-specific parameters for the VAT withholding certificate

To configure application-specific parameters, follow these steps.

1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**, and select **Reporting configurations**.
1. Select the **VAT Withholding certificate** format.
1. On the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
1. On the **Application specific parameters** page, on the **Lookups** FastTab, select **TaxType**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Tax Code** field, select the tax codes that are used as VAT withholding taxes.
1. On the **Lookups** FastTab, select **InvoiceIsApplicable**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification Id (VoucherClassId)** field, select all document classes that are required for vendor transactions (invoices, debit notes, and credit notes).

> [!NOTE]
> Complete each lookup with **No** or **Not applicable** conditions where you select **Blank** and **Not blank**.

## Generate the VAT withholding certificate

To generate the VAT withholding certificate follow these steps.

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
1. In the **Format mapping** field, enter or select **VAT Withholding certificate**.
1. Select **OK**.
1. In the **TAX application Id** field, enter the tax application code that was created for this report.
1. In the **From date** and **To date** fields, specify the date range for the report.
1. Select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
