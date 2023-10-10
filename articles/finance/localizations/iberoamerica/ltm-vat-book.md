---
title: VAT book printing configuration
description: The article describes how to set up and use VAT books. 
author: Cpicon85 
ms.date: 20/09/2023 
ms.topic: conceptual
ms.reviewer: kfend
ms.author: Cpicon85 
ms.custom: bap-template
---

# VAT book printing configuration

[!include [banner](../../includes/banner.md)]

Value Added Tax books, refer to the records and accounting documents that businesses use to keep track of their transactions for Value Added Tax (VAT) purposes. 
The specific requirements for VAT books can vary from one country to another, but they generally include date of the transaction, the customer/vendor’s information, and the tax information details

The article describes how to set up and use sales and purchase VAT tax books for the latam countries.

## Prerequisites

Before you complete the steps in this article to generate and print the report, the following prerequisites must be met:

- The legal entity's address must be in a country/region that's within the LATAM localization.
- The country/region-specific LATAM feature and the general LATAM feature must be enabled.
- Download the specific report from global repository. To learn more, see  [ER download reports](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).
- Configure the Electronic reporting (ER) parameters. For more information, see [ER configuration](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Configure application-specific parameters
Lookups and conditions are designed so you can select the combination of documents classification IDs and sales tax codes that are used in the transactions. Depending on the country that you want to configure the report for, the applicable conditions are shown.

1.	On the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
2.	On the **Conditions** FastTab, select **Add**.
3.	In the **Lookup result** field, select an option. For example, **VAT**.
4.	In the **Tax Code** field, select the appropriate tax code used for VAT tax rates for your country.

 > [!NOTE]
 > VAT books are formats that depend on the LTM tax report model so it's important that transactions have registered taxes. The codes you select here must match the codes registered in the transactions.

5. Repeat steps 3 and 4 for each column of the report.
6. To ensure that the report shows the transactions that meet the conditions you configured, complete the lookup result field with blank and non-blank conditions.

## Run VAT books

1. Go to **Tax** > **Inquiries and reports** > **LATAM** > **Tax reporting**.
2. In the **Format mapping** field, enter or select a value and select **OK**.
3. In the **From date** and **To date** fields, enter the date range to include in the report.
4. Select **OK**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
