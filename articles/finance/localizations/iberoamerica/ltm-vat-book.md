---
title: VAT book printing configuration
description: Learn how to set up and use value-added tax (VAT) books, including an outline on configuring application-specific parameters.
author: Cpicon85
ms.author: v-cpicon
ms.topic: conceptual
ms.date: 09/20/2023 
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# VAT book printing configuration

[!include [banner](../../includes/banner.md)]

Value-added tax (VAT) books refer to the records and accounting documents that businesses use to keep track of their transactions for VAT purposes. Although the specific requirements for VAT books can vary from one country/region to another, they generally include the date of the transaction, the customer/vendor information, and the tax information details.

The article describes how to set up and use sales and purchase VAT tax books for the Latin American (LATAM) countries.

## Prerequisites

Before you complete the steps in this article to generate and print the report, the following prerequisites must be met:

- The legal entity's address must be in a country/region that's within the LATAM localization.
- The country/region-specific LATAM feature and the general LATAM feature must be enabled.
- You must download the specific report from the Global repository. For more information, see [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).
- You must configure the Electronic reporting (ER) parameters. For more information, see [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Configure application-specific parameters

Lookups and conditions are designed so that you can select the combination of document classification IDs and sales tax codes that's used in the transactions. Depending on the country/region that you want to configure the report for, the applicable conditions are shown.

1. Open the **Electronic reporting** workspace, and select **Reporting configurations**.
2. Select the VAT book format for your country, and then, on the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
3. On the **Application specific parameters** page, On the **Conditions** FastTab, select **Add**.
4. In the **Lookup result** field, select an option. For example, select **VAT**.
5. In the **Tax Code** field, select the appropriate tax code that's used for VAT tax rates for your country/region.

    > [!NOTE]
    > VAT books are formats that depend on the LTM tax report model. Therefore, it's important that taxes are registered for transactions. The codes that you select here must match the codes that are registered in the transactions.

6. Repeat steps 4 and 5 for each column of the report.

To ensure that the report shows the transactions that meet the configured conditions, complete the **Lookup result** field with blank and non-blank conditions.

## Run VAT books
Follow these steps to generate the VAT book report.

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
2. In the **Format mapping** field, enter or select a value. Then select **OK**.
3. In the **From date** and **To date** fields, enter the date range to include on the report.
4. Select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
