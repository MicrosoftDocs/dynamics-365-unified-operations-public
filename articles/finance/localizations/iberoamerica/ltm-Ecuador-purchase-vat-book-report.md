---
title: Configure purchases VAT book details for Ecuador printing
description: The article describes how to configure Purchases VAT book details for printing. 
author: Fhernandez0088
ms.date: 12/30/2024
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Configure purchases VAT book details for Ecuador printing

[!INCLUDE[banner](../../includes/banner.md)]

This article describes how to configure a Purchases VAT book details report for printing. Purchase VAT books are the transaction records used by companies to keep a detailed record of their operations, indicating for each transaction, the vendor information, voucher details with their corresponding taxes and tax withholdings if applicable, including local and foreign transactions and other mandatory information determined by the regulations. 


## Prerequisites

Before you complete the steps in this article to generate and print the report, the following prerequisites must be met: 

- The legal entity's address must be set to Ecuador. 
- The country/region-specific LATAM feature and the general LATAM feature must be enabled.
- You must download the specific report from the Global repository. For more information, see [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md). 
- You must configure the Electronic reporting (ER) parameters. For more information, see [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md). 
- You must post vendors invoices for the specific period. For more information see [Purchase invoice posting for Latin America](/dynamics365/finance/localizations/iberoamerica/ltm-core-purchase-invoice-posting) 

## Configure application-specific parameters

Lookups and conditions are designed so that you can select the combination of document classification IDs and sales tax codes that's used in the transactions. Depending on the country/region that you want to configure the report for, the applicable conditions are shown.

To configure application-specific parameters, follow these steps.

1. Open the **Electronic Reporting** workspace and select **Reporting configurations**.
1. Select the **Purchases Vat Book Details**, and then select **Setup** on the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group.
1. In the **Lookups names**, select **TaxType**.
1. In the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select an option from the list. 
1. In the **Tax code** field, select an option from the list. 
1. Repeat steps 5 and 6 as many tax codes you need.
1. Back to **Lookups names**, select **VendorApplicableInvoices**.
1. In the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification Id** field, select an option from the list. 
1. Repeat steps 10 and 11 as many document classes you need.
1. Back to **Lookups names**, select **WithholdingGroup**.
1. In the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select an option from the list.
1. In the **Document classification Id** field, select an option from the list. 
1. Repeat steps 15 and 16 as many withholding document classes you need.

> [!NOTE]
> Purchases VAT book details is a format that depends on the LTM tax report model. Therefore, it's important that taxes and document classes are registered for transactions. The codes and document classes that you select in this field must match the codes and document classes that are registered in the transactions.
To ensure that the report shows the transactions that meet the configured conditions, complete the **Lookup result** fields as **Not Applicable** or **No** with **blank** and **non-blank** conditions.

## Run Purchases Vat Book Details for Ecuador

To generate the **EC Purchases VAT Book details**, follow these steps.

1. Go to **Tax** > **Inquiries and reports** > **LATAM** > **Tax reporting**.
1. In the **Format mapping** field, select **EC Purchases VAT Book details** value. Then select **OK**.
1. In the **From date** and **To date** fields, enter the date range to include in the report.
1. Select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
