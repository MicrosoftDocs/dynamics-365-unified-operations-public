---
title: Generate and print the Fees certificate resume report - Chile
description: The article describes how to generate and print the Fees certificate resume report for Chile.
author: Cpicon85 
ms.date: 09/26/2023 
ms.topic: article
ms.reviewer: kfend
ms.author: Cpicon85 
ms.custom: bap-template
---

# Generate and print the Fees certificate resume report - Chile

[!include [banner](../../includes/banner.md)]

The **Fees certificate resume** (**Certificado de Honorarios Resumen**) report includes tax information such as the vendor's name and tax identification number (Rol Único Tributario \[RUT\]), the total amount of fees that were received, and any tax withholdings that the vendor made.

## Prerequisites

Before you generate and print the report, the following prerequisites must be met:

- The legal entity must have an address in a country/region that's within the LATAM localization.
- The country/region-specific LATAM feature and the general feature must be enabled.
- You must download the specific report from the Global repository. For more information, see [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).
- You must configure the Electronic reporting (ER) parameters. For more information, see [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
- You must complete the **Monetary adjustment factors** form by using the information that's published by the fiscal authorities.

## Configure application-specific parameters

Lookups and conditions are designed so that you can select the combination of document classification IDs and sales tax codes that's used in the transactions.

1. On the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
2. On the **Conditions** FastTab, select **Add**.
3. In the **Lookup result** field, select an option. For example, select **vendorinvoiceisapplicable**.
4. In the **Document classification ID** field, select an option in the list. Select the appropriate document classification that represents the professional fees invoice. In Chile, this invoice is named *boleta de honorarios*.
5. In the **Lookup result** field, select an option. For example, select **taxisapplicable**.
6. In the **Tax code** field, select an option in the list. For example, select **BOL-HON**. The **Fees certificate resume** report depends on the LTM tax report model. Therefore, it's important that taxes are registered for transactions. The codes that you select in this field must match the codes that are registered in the transactions.
7. Repeat the previous steps for each column of the report.

To ensure that the report shows the transactions that meet the configured conditions, complete the **Lookup result** field with blank and non-blank conditions.

## Run the Fees certificate resume report

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
2. In the **Format mapping** field, enter or select a value. Then select **OK**.
3. In the **From date** and **To date** fields, select the date range for the report.
4. Select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
