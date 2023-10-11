---
title: Generate and print the Withholding tax book report for Chile
description: The article how to generate and print the Withholding tax book report for Chile. 
author: Cpicon85 
ms.date: 10/11/2023 
ms.topic: article
ms.reviewer: kfend
ms.author: Cpicon85 
ms.custom: bap-template
---

# Chile Withholding tax book report printing configuration

[!include [banner](../../includes/banner.md)]

The **Withholding Tax Book** (Libro de Retenciones) report is an accounting record used by businesses with an address in Chile to record withholding tax transactions.

## Prerequisites

Before you complete the steps in this article to generate and print the report, the following prerequisites must be met:

- The legal entity's address must be in a country/region that's within the LATAM localization.
- The country/region-specific LATAM feature and the general LATAM feature must be enabled.
- Download the report from the global repository. To learn more about the reports, see [ER download reports](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).
- Configure the Electronic Reporting (ER) parameters. To learn more about ER parameters, see [ER configuration](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md)

## Configure application-specific parameters
After the model, mapping, and corresponding format have been downloaded, configure the specific parameters of the withholding tax book format. When the parameters are configured, you can select the document class ID and tax codes used in the corresponding transactions. Lookups and conditions are designed to allow you to choose the combination of document classification IDs and sales tax codes.

To configure parameters follow these steps:

1. Go to the **Electronic reporting** workspace and select **Reporting configurations**.
2. Select **Witholding Book CL** and on the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**
3. On the **Application specific parameters** page, configure the rules for the lookups data source. 

  - For **vendorinvoiceisapplicable** lookup configuration, follow these steps:

     1. On the **Conditions** FastTab, select **Add** and in the **Lookup result** field, select **Yes**.
     2. In the **Document classification id.** field, select the appropriate document classification from the list. for example, **Bol-Hon**.
     3. Select **Add** and in the **Lookup result** field, select **No**.
     4. In the **Document classification id.** field, select **Blank**
     5. Select **Add** and in the **Lookup result** field, select **No**.
     6. In the **Document classification id.** field, select **Not Blank**.

  - For **TaxType** lookup configuration follow these steps:

     1. On the **Conditions** FastTab, select **Add**, and in the **Lookup result** field, select **VAT**.
     2. In the **Tax code** field, select the appropriate tax code from the list. for example, **Ret-Hon**.
     3. Select **Add** and in the **Lookup result** field, select **NotApplicable**.
     4. In the ** Tax code** field, select **Blank**.
     5. Select **Add** and in the **Lookup result** field, select **NotApplicable**.
     6. In the **Tax code** field, select **Not Blank**.


## Run the Withholding tax books report

1. Go to **Tax** > **Inquiries and reports** > **LATAM** > **Tax reporting**.
2. In the **Format mapping** field, enter or select a value.
3. Select **OK**.
4. In the **From date** field, enter a date.
5. In the **To date** field, enter a date.
6. Select **OK**.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
