---
title: Generate and print the Fees certificate report - Chile
description: Learn how to generate and print the Fees certificate report for Chile, including prerequisites and an outline on configuring application-specific parameters.
author: Cpicon85
ms.author: v-cpicon 
ms.topic: article
ms.date: 10/20/2023 
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Generate and print the Fees certificate report - Chile

[!include [banner](../../includes/banner.md)]

The **Fees certificate** (**Certificado de Honorarios**) report includes tax information such as the vendor's name and tax identification number (Rol Único Tributario \[RUT\]), the total amount of fees that were received, and any tax withholdings that the vendor made.

## Prerequisites

Before you generate and print the report, the following prerequisites must be met:

- The legal entity must have an address in a country/region that's within the LATAM localization.
- The country/region-specific LATAM feature and the general feature must be enabled.
- You must download the specific report from the Global repository. For more information, see [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).
- You must configure the Electronic reporting (ER) parameters. For more information, see [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
- You must complete the **Monetary adjustment factors** form by using the information that's published by the fiscal authorities.

## Configure application-specific parameters

Lookups and conditions are designed so that you can select the combination of document classification IDs and sales tax codes that's used in the transactions.

1. In the **Electronic reporting** workspace, select **Reporting configurations**.
2. Select the **Fees certificate report** format, and on the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
3. On the **Application specific parameters** page, On the **Conditions** FastTab, select **Add**.
4. In the **Lookup result** field, select an option. For example, select **vendorinvoiceisapplicable**.
5. In the **Document classification ID** field, select an option in the list. Select the appropriate document classification that represents the professional fees invoice. In Chile, this invoice is named *boleta de honorarios*.
6. In the **Lookup result** field, select an option. For example, select **taxisapplicable**.
7. In the **Tax code** field, select an option in the list. For example, select **BOL-HON**. The **Fees certificate** report depends on the LTM tax report model. Therefore, it's important that taxes are registered for transactions. The codes that you select in this field must match the codes that are registered in the transactions.
9. Repeat the previous steps for each column of the report.

To ensure that the report shows the transactions that meet the configured conditions, complete the **Lookup result** field with blank and non-blank conditions.

## Run the Fees certificate report

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
2. In the **Format mapping** field, enter or select a value. Then select **OK**.
3. In the **From date** and **To date** fields, select the date range for the report.
4. Select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
