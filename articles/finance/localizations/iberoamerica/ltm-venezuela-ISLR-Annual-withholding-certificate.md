---
title: Configure printing for the annual ISLR withholding certificate for Venezuela
description: Learn how to set up and generate the annual income tax (ISLR) withholding certificate for Venezuela.
author: Cpicon85
ms.date: 06/05/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-cpicon
---

# Configure printing for the annual ISLR withholding certificate for Venezuela

[!include [banner](../../includes/banner.md)]

This article explains how to set up and generate the annual income tax (ISLR) withholding certificate for Venezuela in Microsoft Dynamics 365 Finance. This document contains information about the withholdings that are generated from vendor invoices, debit notes, and credit notes.

## Prerequisites

Before you can generate the report, the following prerequisites must be met:

- The legal entity's address must be in Venezuela.
- You must enable both the general Latin American (LATAM) feature and the country/region-specific LATAM feature for Venezuela.
- You must download the specific report configuration from the Dataverse configuration repository. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

    The following formats constitute the annual ISLR withholding certificate:

    - LTM Tax Report
    - LTM Tax Report mapping
    - VEN Annual withholding certificate

- You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Configure application-specific parameters for the report

To configure application-specific parameters, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration** \> **Workspaces** \> **Electronic reporting**, and select **Reporting configurations**.
1. Select the **VEN Annual withholding certificate** format.
1. On the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
1. On the **Application specific parameters** page, on the **Lookups** FastTab, select **VendorApplicableInvoices**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification Id (VoucherClassId)** field, select all document classes that are required for vendor transactions (invoices, debit notes, and credit notes).
1. On the **Lookups** FastTab, select **ApplicableTax**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Tax code** field, select the tax codes that are used as annual ISLR withholding taxes.

> [!NOTE]
> Complete each lookup with **No** or **Not applicable** conditions where you select **Blank** and **Not blank**.

## Generate the annual ISLR withholding certificate

To generate the annual ISLR withholding certificate, follow these steps.

1. In Finance, go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
1. In the **Format mapping** field, enter or select **VEN Annual withholding certificate**.
1. Select **OK**.
1. In the **From date** and **To date** fields, specify the date range for the report.
1. Select **OK**.
1. In the **Account number** field, you can specify the account to show.
1. Select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
