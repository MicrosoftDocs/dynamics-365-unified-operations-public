---
title: Generate and print the Withholding tax book report for Chile
description: Learn how to generate and print the Withholding tax book report for Chile, including prerequisites and an outline on configuring application-specific parameters.
author: Cpicon85
ms.author: v-cpicon 
ms.topic: article
ms.date: 10/11/2023 
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Generate and print the Withholding tax book report for Chile

[!include [banner](../../includes/banner.md)]

The **Withholding Tax Book** (**Libro de Retenciones**) report is an accounting record that businesses that have an address in Chile use to record withholding tax transactions.

## Prerequisites

Before you complete the procedures in this article to generate and print the report, the following prerequisites must be met:

- The legal entity's address must be in a country/region that's within the Latin American (LATAM) localization.
- The country/region-specific LATAM feature and the general LATAM feature must be enabled.
- You must download the report from the Global repository. For more information about the reports, see [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).
- You must configure the Electronic Reporting (ER) parameters. For more information about ER parameters, see [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Configure application-specific parameters

After the model, mapping, and corresponding format have been downloaded, configure the specific parameters of the withholding tax book format. When the parameters are configured, you can select the document class ID and tax codes that are used in the corresponding transactions. Lookups and conditions are designed so that you can select the combination of document classification IDs and sales tax codes.

To configure parameters, follow these steps.

1. Open the **Electronic reporting** workspace, and select **Reporting configurations**.
2. Select **Witholding Book CL**, and then, on the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
3. On the **Application specific parameters** page, configure the rules for the lookup data source.

    - For the **vendorinvoiceisapplicable** lookup, follow these steps:

        1. On the **Conditions** FastTab, select **Add**, and then, in the **Lookup result** field, select **Yes**.
        2. In the **Document classification id.** field, select the appropriate document classification. for example, select **Bol-Hon**.
        3. Select **Add**, and then, in the **Lookup result** field, select **No**.
        4. In the **Document classification id.** field, select **Blank**
        5. Select **Add**, and then, in the **Lookup result** field, select **No**.
        6. In the **Document classification id.** field, select **Not Blank**.

    - For the **TaxType** lookup, follow these steps:

        1. On the **Conditions** FastTab, select **Add**, and then, in the **Lookup result** field, select **VAT**.
        2. In the **Tax code** field, select the appropriate tax code. for example, select **Ret-Hon**.
        3. Select **Add**, and then, in the **Lookup result** field, select **NotApplicable**.
        4. In the **Tax code** field, select **Blank**.
        5. Select **Add**, and then, in the **Lookup result** field, select **NotApplicable**.
        6. In the **Tax code** field, select **Not Blank**.

## Run the Withholding tax books report

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
2. In the **Format mapping** field, enter or select a value.
3. Select **OK**.
4. In the **From date** field, enter a date.
5. In the **To date** field, enter a date.
6. Select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
