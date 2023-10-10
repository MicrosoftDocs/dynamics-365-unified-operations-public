---
title: Generate and print the Fees certificate resume report - Chile 
description: The article describes how to generate and print the Fees certificate resume report for Chile. 
author: Cpicon85 
ms.date: 26/09/2023 
ms.topic: article
ms.reviewer: kfend
ms.author: Cpicon85 
ms.custom: bap-template
---

# Generate and print the Fees certificate resume report - Chile

[!include [banner](../../includes/banner.md)]

The Fees certificate resume (Certificado de Honorarios Resumen) report includes tax information, including the name and RUT (Rol Único Tributario - Tax Identification Number) of the vendor, the total amount of fees received, and any tax withholdings made by the vendor.

## Prerequisites

Before you generate and print the report, the following prerequisites must be met.

- The legal entity must have an address in a country/region that's within the LATAM localization.
- The country/region-specific LATAM feature and the general feature must be enabled.
- Download the specific report from global repository. To learn more, see [ER download reports](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).
- Configure the Electronic reporting (ER) parameters. To learn more, see [ER configuration](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
- Complete the **Monetary adjustment factors** form with the information published by the fiscal authorities.

## Configure application-specific parameters
Lookups and conditions are designed so that you can select the combination of document classification IDs and sales tax codes used in the transactions.

1.	On the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
2.	On the **Conditions** FastTab, select **Add**.
3.	In the **Lookup result** field, select an option. For example, **vendorinvoiceisapplicable**.
4.	In the **Document classification ID** field, select an option from the list. Select the appropriate document classification that represents the professional fees invoice, which is named **boleta de honorarios** in Chile.
5.	In the **Lookup result** field, select an option. For example, **taxisapplicable**.
6.	In the **Tax code** field, select an option from the list. For example, **“BOL-HON”**. The **Fees certificate** report depends on the LTM tax report model so it's important that taxes are registered for transactions. The codes you select in this menu must match the codes registered in the transactions.
7.	Repeat the previous steps for each column of the report.

To ensure that the report shows the transactions that meet the conditions as they are configured, complete the lookup result field with blank and non-blank conditions.

## Run the Fee certificate report

1. Go to **Tax** > **Inquiries and reports** > **LATAM** > **Tax reporting**.
2. In the **Format mapping** field, enter or select a value and then select **OK**.
3. In the **From date** and **To date** fields, select the date range for the report.
4. Select **OK**.




[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
