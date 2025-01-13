---
title: Configure Ecuadorian purchase withholding book printing
description: Learn how to configure the Ecuadorian purchase withholding book report for printing.
author: Fhernandez0088
ms.date: 12/30/2024
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Configure Ecuadorian purchase withholding book printing

[!INCLUDE[banner](../../includes/banner.md)]

The article explains how to configure the Ecuadorian purchase withholding book report so that it can be printed. The withholding book is a record where companies detail the tax withholdings for each invoice transaction that was withheld in its payment.

## Prerequisites

Before you can generate and print the report, the following prerequisites must be met:

- The legal entity's address must be in a country/region that is within the LATAM localization.
- Both the country/region-specific LATAM feature and the general LATAM feature must be enabled.
- You must download the relevant report from the Global repository. Learn more in [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).
- You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
- You must post vendor invoices for the relevant period. Learn more in [Purchase invoice posting for Latin America](/dynamics365/finance/localizations/iberoamerica/ltm-core-purchase-invoice-posting).
- You must post vendors payments. Learn more in [Use the LATAM extension in vendor payments journals](/dynamics365/finance/localizations/iberoamerica/ltm-latam-in-vendor-payment).

## Configure application-specific parameters

Lookups and conditions are designed so that you can select the combination of document classification IDs and sales tax codes that is used in the transactions. Depending on the country/region that you want to configure the report for, the applicable conditions are shown.

To configure application-specific parameters, follow these steps.

1. Open the **Electronic Reporting** workspace, and select **Reporting configurations**.
1. Select **Purchases Withholding books**, and then, on the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
1. On the **Lookups** FastTab, in the **Name** column, select **Withholdings**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select a value.
1. In the **Document Classification Id** field, select a value.
1. Repeat steps 5 and 6 to add as many more **Lookup result** fields as you need.
1. On the **Lookups** FastTab, in the **Name** column, select **VendorApplicableInvoices**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document Classification Id** field, select a value.
1. Repeat steps 10 and 11 to add as many more **Lookup result** fields as you need.

> [!NOTE]
> Purchase withholding books are formats that depend on the **LTM Tax Report** model. Therefore, it's important that Withholdings are registered for the transactions. The codes that you select here must match the codes that are registered in the transactions. To ensure that the report shows the transactions that meet the configured conditions, complete the **Lookup result** field as **Not Applicable** or **No** with blank and non-blank conditions.

## Run the purchase withholding book report

To generate the purchase withholding book report, follow these steps.

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
1. In the **Format mapping** field, select **Purchases Withholdings book**.
1. Select **OK**.
1. In the **From date** and **To date** fields, enter the date range to include on the report.
1. Select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
