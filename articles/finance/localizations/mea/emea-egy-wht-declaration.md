---
title: Withholding tax declaration for Egypt
description: Learn how to configure and generate the withholding tax declarations for Egypt in Microsoft Dynamics 365 Finance.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/05/2025
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2017-06-20
---

#  Withholding tax declaration for Egypt (EG-00005)

[!include[banner](../../includes/banner.md)]

This article explains how to configure and generate the withholding tax declarations for Egypt in Microsoft Dynamics 365 Finance.

All Egyptian entities must prepare the form  41 which summarizes all taxes that are retained from local suppliers and service providers. In addition to form 41, form 11 must be generated to detail all of the retained taxed from foreign providers. 

The **Withholding tax declaration** report in Dynamics 365 Finance includes the following reports:

- Declaration form No. 41
- Declaration form No. 11
	
## Prerequisites

The primary address of the legal entity must be in Egypt.

In the **Feature management** workspace, the following feature must be enabled:

   - Global withholding tax

For more information about how to enable features, see [Feature management overview.](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

To enable the global withholding tax feature, follow these steps:

1. In Dynamics 365 Finance, go to **Tax** \> **Setup** \> **Parameters** \> **General ledger parameters**, and on the **Withholding tax** tab, set **Enable global withholding tax** to **Yes**.
1. In the **Electronic reporting** workspace, import the following electronic reporting formats from the repository:

	- WHT Declaration Excel (EG)

	> [!NOTE]
	> The format above is based on the **Tax declaration model** and uses the **Tax declaration model mapping**. This additional configuration is automatically imported.

For more information about how to import electronic reporting configurations, see [Download electronic reporting configurations from Lifecycle Services](../../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

## Download electronic reporting configurations

The implementation of the WHT declaration forms for Egypt is based on electronic reporting (ER) configurations. For more information about the capabilities and concepts of configurable reporting, see [Electronic reporting](../../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md).

For production and user acceptance testing (UAT) environments, follow the instructions in the article, [Download electronic reporting configurations from Lifecycle Services](../../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

To generate the Withholding declarations in an Egyptian legal entity, you need to upload the following configurations:

- Tax declaration model.version.82.xml or later version
- Tax declaration model mapping.version.82.133.xml or a later version
- WHT Declaration Excel (EG).version.82.21  or a later version

After you finish downloading the ER configurations from Lifecycle Services (LCS) or the global repository, follow these steps:

1. In Dynamics 365 Finance, go to the **Electronic reporting** workspace and select the **Reporting configurations** tile.
1. On the **Configurations** page, on the Action Pane, select **Exchange > Load from XML file**.
1. Upload all the files in the order in which they are listed in the previous bullets. After all of the configurations are uploaded, the configuration tree should be present in Finance.

## Set up application-specific parameters

The application-specific parameters option lets users establish the criteria of how the tax transactions will be classified and calculated in each line of a generated report depending on the configuration of **withholding tax item group** or other criteria established in the definition of lookup.

Withholding declaration form 41 includes a specific column where the withholding tax transaction must be classified in accordance with the tax authority classification named **Discount code type**. Instead of including these new classifications as new entry data when the transactions are posted, the classifications will be determined based on the different lookups introduced in **Configurations** \> **Set up application-specific parameters** \> **Setup** to meet the requirements of withholding reports for Egypt. 

The following configuration is used to classify the transactions in the Withholding declaration form 41 report:

- **DiscountTaxTypeLookup**-> Column No 18 

To set up the different lookups used to generate the WHT declaration and related books reports, follow these steps:

1. In the **Electronic reporting** workspace, select **Configurations** \> **Setup** to set up the rules to identify how transactions are classified in the WHT declaration report. 
1. Select the current version, and on the **Lookups** FastTab, select the lookup name. For example, **DiscountTaxTypeLookup**. This lookup identifies the list of discount types required by the tax authority.
1. On the **Conditions** FastTab, select **Add** and in the new line in the **Lookup result** column, select the related line that represents the classification in the **Column 18**.
1. In the **Withholding tax item group** column, select the related code that's used to identify the classification. For example, **Allowed discount**.  
1. Repeat steps 3 and 4 for all available lookups.
1. Select **Add** again to include the final record line, and in the **Lookup result** column, select **Not applicable**. 
1. In the remaining columns, select **Not blank**. 

> [!NOTE]

## Set up general ledger parameters

To generate the WHT declaration form reports in Microsoft Excel, you must define an ER format on the **General ledger parameters** page.

To set up general ledger parameters, follow these steps:

1. In Dynamics 365 Finance, go to **Tax** \> **Setup** \> **General ledger parameters**.
1. On the **Withholding tax** tab, in the **WHT declaration format mapping** field, select **WHT Declaration Excel (EG)**. If you leave the field blank, the standard sales tax report is generated in SSRS format.

![Declaration form.](../media/egypt-wht-declaration-setup1.png)

## Generate the withholding declaration forms

The process of preparing and submitting a Withholding declaration form for a specific period is based on the withholding tax transactions posted during the settle and post payment tax job. For more information about global withholding tax, see [Global withholding tax](../../general-ledger/global-withholding-tax-overview.md).

To generate the withholding declaration forms, follow these steps:

1. In Dynamics 365 Finance, go to **Tax** \> **Declarations** \> **Withholding tax** \> **Withholding tax payment**.
1. Select the settlement period and then select the from date for the report. 
1. Enter the transaction date and then select **OK**.
1. In the dialog box that opens, select one or more of the form types **Form No 41**, **Form No 11**, or **None**. If you select **None**, the standard report is generated. 
1. Select the language. All reports are translated in **en-us** and **ar-eg**.
1. Enter the branch and name of the bank where the tax payment will be paid.
1. Select the business type and then enter the check and document numbers. 
1. Enter the entity type. 
1. Enter the name of person registered to assign the form and select **OK** to confirm the report generation. 

 
[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
