---
title: Generate and print the Withholding tax book report for Chile
description: The article how to generate and print the Withholding tax book report for Chile. 
author: Cpicon85 
ms.date: 10/06/2023 
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
Once the model, mapping, and corresponding format have been downloaded, it is necessary to configure the specific parameters of the withholding tax book format. This way, you will be able to select the document class id. and tax codes used in the corresponding transactions. Lookups and conditions are designed to allow you to choose the combination of documents classification IDs and sales tax codes.

To configure parameters follow these steps:

1. On the default dashboard, select **Electronic reporting**.
2. Select Reporting configurations.
3. Select **Witholding Book CL** format
4. On the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**

   * For **vendorinvoiceisapplicable** lookup configuration follow these steps:

     1. On the Conditions FastTab, Select **Add**
        1. In the **Lookup result** field, select **Yes**
        2. In the **Document classification id.** field, select an option from the list. Select the appropriate document classification for example **“Bol-Hon”**

     2. Select **Add** and complete:
        1. In the **Lookup result** field, select **No**
        2. In the **Document classification id.** field, select **Blank**

     3. Select **Add** and complete:
        1. In the **Lookup result** field, select **No**
        2. In the **Document classification id.** field, select **Not Blank**

For **TaxType** lookup configuration follow these steps:

1. On the Conditions FastTab, Select **Add**, and then follow these steps:
   1. In the **Lookup result** field, select **VAT**
   2. In the **Tax code** field, select an option from the list. Select the appropriate tax code for example **Ret-Hon**

2. Select **Add** and complete:
   1. In the **Lookup result** field, select **NotApplicable**
   2. In the ** Tax code** field, select **Blank**

3. Select **Add** and complete:
   1. In the **Lookup result** field, select ** NotApplicable **
   2. In the ** Tax code** field, select **Not Blank**


## Run the Withholding tax books report

1. Go to **Tax** > **Inquiries and reports** > **LATAM** > **Tax reporting**.
2. In the **Format mapping** field, enter or select a value.
3. Select **OK**.
4. In the **From date** field, enter a date.
5. In the **To date** field, enter a date.
6. Select **OK**.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
