---
title: Configure Ecuador purchase refunds report printing 
description: The article describes how to configure Purchases refunds for printing. 
author: Fhernandez0088
ms.date: 12/30/2024
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Configure Ecuador purchase refunds report printing

[!INCLUDE[banner](../../includes/banner.md)]

The article describes how to configure Purchases refunds for printing. This report provides information about purchases refunds transactions.  This type of operation is used when there are intermediaries in the purchases. In these types of transactions there are three figures, the vendor, the intermediary and the beneficiary. The vendor issues the invoice in the name of the intermediary and the intermediary is who pays the vendor, but the expenses and the VAT credit correspond to the beneficiary and the intermediary must comply with a refund request process, so the beneficiary reimburses to the intermediary for the expense made. 

## Prerequisites

Before you complete the steps in this article to generate and print the report, the following prerequisites must be met: 

- The legal entity's address must be in a country/region that's within the LATAM localization. 
- The country/region-specific LATAM feature and the general LATAM feature must be enabled.
- You must download the specific report from the Global repository. For more information, see [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md). 
- You must configure the Electronic reporting (ER) parameters. For more information, see [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md). 
- You must post vendor invoices for the specific period. For more information, see [Purchase invoice posting for Latin America](/dynamics365/finance/localizations/iberoamerica/ltm-core-purchase-invoice-posting) .
- You must post vendor payments. For more information, see [Use the LATAM extension in vendor payments journals](/dynamics365/finance/localizations/iberoamerica/ltm-latam-in-vendor-payment).
- You can follow the instructions in the [Ecuadorian refund invoice transactions posting](ltm-Ecuadorian-refunds-invoice.md) article.

## Configure application-specific parameters

Lookups and conditions are designed so that you can select the combination of document classification IDs and sales tax codes that's used in the transactions. Depending on the country/region that you want to configure the report for, the applicable conditions are shown.

To configure application-specific parameters, follow these steps.

1. Open the **Electronic Reporting** workspace, and select **Reporting configurations**.
1. Select the **Purchases refunds** and then select **Setup** on the **Action** pane, on the **Configurations** tab, in the **Application specific parameters** group.
1. In the **Lookups names**, select **TaxType**.
1. In the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select an option in the list. 
1. In the **Tax code** field, select an option in the list. 
1. Repeat steps 5 and 6 as many as many times as tax codes you need.
1. Back to **Lookups names**, select **VendorApplicableInvoices**.
1. In the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification Id** field, select an option in the list. 
1. Repeat steps 10 and 11 as many document classes you need.
1. Back to **Lookups names**, select **ApplicableWithholdings**.
1. In the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select an option in the list.
1. In the **Document classification Id** field, select an option in the list. 
1. Repeat steps 15 and 16 as many withhdolding document classes you need.

> [!NOTE]
> Purchases refunds are formats that depend on the LTM tax report model. Therefore, it's important that taxes and document classes are registered for transactions. The codes and document classes that you select in this field must match the codes and document classes that are registered in the transactions.
To ensure that the report shows the transactions that meet the configured conditions, complete each **Lookup result** field as **Not Applicable** or **No** with **blank** and **non-blank** conditions.


## Run Purchases refunds

To generate the **purchases refunds**, follow these steps.

1. Go to **Tax** > **Inquiries and reports** > **LATAM** > **Tax reporting**.
1. In the **Format mapping** field, select **Purchases refunds** value. Then select **OK**.
1. In the **From date** and **To date** fields, enter the date range to include on the report.
1. Select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
