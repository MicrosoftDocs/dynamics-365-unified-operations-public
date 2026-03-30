---
title: Printing configuration for the ISLR withholding certificate for Venezuela
description: Learn how to set up and generate an income tax (ISLR) withholding certificate for Venezuela.
author: Fhernandez0088
ms.date: 05/06/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Printing configuration for the ISLR withholding certificate for Venezuela

[!include [banner](../../includes/banner.md)]

This article explains how to set up and generate an income tax (ISLR) withholding certificate for Venezuela in Microsoft Dynamics 365 Finance. This document contains information about the withholdings that are generated from vendor invoices, debit notes, and credit notes.

## Prerequisites

Before you can generate the report, the following prerequisites must be met:

- The legal entity's address must be in Venezuela.
- You must enable both the general Latin American (LATAM) feature and the country/region-specific LATAM feature for Venezuela.
- You must download the specific report configuration from the Dataverse configuration repository. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

    The following formats constitute the ISLR withholding certificate:

    - LTM Tax Report
    - LTM Tax Report mapping
    - VEN Withholding certificate ISLR

- You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Additional configuration required for the ISLR withholding certificate

- You must create a *tax application code* to use on this report. Learn more in [Tax application for Latin America](ltm-core-tax-application.md).
- You must enter the withholding tax fiscal code according to the fiscal authority in the **Tax income** field from the **Tax application** page of the sales tax codes that are used as ISLR withholding taxes.

## Configure application-specific parameters for the ISLR withholding certificate

To configure application-specific parameters, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** \> **Workspaces** \> **Electronic reporting**, and select **Reporting configurations**.
1. Select the **VEN Withholding certificate ISLR** format.
1. On the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
1. On the **Application specific parameters** page, on the **Lookups** tab, select **VendorApplicableDocuments**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification Id (VoucherClassId)** field, select all document classes that are required for vendor transactions (invoices, debit notes, and credit notes).
1. To ensure that the report shows the transactions that meet the configured conditions, set the **Lookup result** fields to **No**, and specify both **Blank** and **Non-blank** conditions.
1. On the **Lookups** FastTab, select **ApplicableWIthholdingTaxes**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Tax code** field, select the tax codes that are used as ISLR withholding taxes.
1. To ensure that the report shows the transactions that meet the configured conditions, set the **Lookup result** fields to **N/A**, and specify both **Blank** and **Non-blank** conditions.

## Generate the ISLR withholding certificate

To generate the certificate, follow these steps:

1. In Finance, go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
1. In the **Format mapping** field, enter or select **VEN Withholding certificate ISLR**.
1. Select **OK**.
1. In the **TAX application Id** field, enter the tax application code that was created for this report.
1. In the **Invoice** field, enter the LATAM complete document number of the invoice.
1. In the **From date** and **To date** fields, specify the date range for the report.
1. Select **OK**.

> [!NOTE]
> The **Invoice** field isn't mandatory for certificate printing. The specified date range can be used to print a group of certificates.
