---
title: Configure Ecuador purchases Withholdings book printing
description: The article provides description on how to configure Ecuador Purchases Withholding report for printing.
author: Fhernandez0088
ms.date: 12/30/2024
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Configure Ecuador purchases Withholdings book printing

[!INCLUDE[banner](../../includes/banner.md)]

The article describes how to configure and print the Ecuador Purchases Withholdings book report. The withholding book is a record where companies detail the tax withholdings for each invoice transaction withheld in its payment.

## Prerequisites

Before you complete the steps in this article to generate and print the report, the following prerequisites must be met: 

- The legal entity's address must be in a country/region that's within the LATAM localization. 
- The country/region-specific LATAM feature and the general LATAM feature must be enabled.
- You must download the specific report from the Global repository. For more information, see [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md). 
- You must configure the Electronic reporting (ER) parameters. For more information, see [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md). 
- You must post vendor invoices for the specific period. For more information, see [Purchase invoice posting for Latin America](/dynamics365/finance/localizations/iberoamerica/ltm-core-purchase-invoice-posting).
- You must post vendors payments. For more information see [Use the LATAM extension in vendor payments journals](/dynamics365/finance/localizations/iberoamerica/ltm-latam-in-vendor-payment).


## Configure application-specific parameters

Lookups and conditions are designed so that you can select the combination of document classification IDs and sales tax codes that's used in the transactions. Depending on the country/region that you want to configure the report for, the applicable conditions are shown.

To configure application-specific parameters, follow these steps.

1. Open the **Electronic Reporting** workspace, and select **Reporting configurations**
1. Select the **Purchases Withholding books**, and then select **Setup** on the **Action** pane, on the **Configurations** tab, in the **Application specific parameters** group.
1. In the **Lookup name**, select the following option **Withholdings**.
1. In the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select an option from the list.
1. In the **Document Classification Id** field, select an option from the list. 
1. Repeat steps 5 and 6 as many **Lookups results** as you need to configure. 
1. Back to **Lookup name**, select the following option **VendorApplicableInvoices**.
1. In the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document Classification Id** field, select an option from the list.
1. Repeat steps 10 and 11 as many **Lookups results** as you need to configure.

> [!NOTE]
> Purchases Withholdings book are formats that depend on the LTM report model. Therefore, it is important that Withholdings are registered for the transactions. The codes that you select here must match the codes that are registered in the transactions.
To ensure that the report shows the transactions that meet the configured conditions, complete the **Lookup result** field as **Not Applicable** or **No** with blank and non-blank conditions.


## Run Purchases Withholdings books

To generate the **Purchases Withholdings book**, follow these steps.

1. Go to **Tax** > **Inquiries and reports** > **LATAM** > **Tax reporting**.
1. In the **Format mapping** field, select ** Purchases Withholdings book** a value. Then select **OK**.
1. In the **From date** and **To date** fields, enter the date range to include on the report.
1. Select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
