---
# required metadata

title: Withholding tax declaration for Egypt
description: This topic explains how to configure and generate the Withholding tax declarations for Egypt.
author: sndray
manager: AnnBe
ms.date: 02/25/2021
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope:
# ms.tgt_pltfrm: 
# ms.custom: NotInTOC
ms.search.region: Global
# ms.search.industry:
ms.author: tfehr
ms.search.validFrom: 2017-06-20
ms.dyn365.ops.version: 10.0.18
---

#  Withholding tax declaration for Egypt (EG-00005)

[!include[banner](../includes/banner.md)]

## Overview
This topic explains how to set up and generate the withholding tax declaration for legal entities in Egypt.
This topic explains how to set up and generate the withholding tax declaration form 41 and 11 for legal entities in Egypt.


All the Egyptian entities must prepare the form No. 41  that summarizes all taxes retained from their local suppliers and service providers. In addition to this, an additional form No. 11 must be generated to details all retained taxed from foreign providers. 

The Withholding tax declaration report  Dynamics 365 Finance includes the following reports:

- Declaration form No. 41
- Declaration form No. 11
	
	
## Prerequisites
The primary address of the legal entity must be in Egypt.
In the **Feature management** workspace, enable the following features:

- Global withholding tax.

For more information about how to enable features, see Feature management overview.

In the **Tax > Setup > Parameters > General ledger parameters > Withholding tax**  tab, set the Enable global withholding tax option to Yes.

In the **Electronic reporting** workspace, import the following Electronic Reporting formats from the repository:

- WHT Declaration Excel (EG)

> [!NOTE]
> The formats above are based on **Tax declaration model** and use **Tax declaration model mapping**. These additional configurations will be automatically imported.

For more information about how to import Electronic Reporting configurations, see [Download Electronic reporting configurations from Lifecycle Services](../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

## Download Electronic reporting configurations

The implementation of the WHT declaraton forms for Egypt is based on Electronic reporting (ER) configurations. For more information about the capabilities and concepts of configurable reporting, see [Electronic reporting](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md).

For production and user acceptance testing (UAT) environments, follow the instructions [Download Electronic reporting configurations from Lifecycle Services](../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

To generate the Withholding declarations in a Egypt legal entity, you need to upload the following configurations:

- Tax declaration model.version.82.xml or later version
- Tax declaration model mapping.version.82.133.xml or a later version
- WHT Declaration Excel (EG).version.82.21  or a later version

After you've finished downloading the ER configurations from Lifecycle Services (LCS) or the global repository, complete the following steps.

1. Go to the **Electronic reporting** workspace. Select the Reporting configurations tile.
1. On the **Configurations** page, on the Action Pane, select **Exchange > Load from XML file**.
1. Upload all the files in the order in which they are listed in the previous bullets. After all the configurations are uploaded, the configuration tree should be present in Finance.

## Set up application-specific parameters

The Application-specific parameters option let the users to establish the criteria of how the tax transactions will be classified and calculated in each line  when the report is generated depending on the configuration of **withholding tax item group** or other criteria established in the definition of lookup.

The withholding declaration form 41 includes a specific column where the withholding tax transaction must be classified in accordance with the tax authority classification named **Discount code type**. Instead of including these new classifications as new entry data when the transactions are posted, the classifications will be determined based on different Lookups we have introduced in **Configurations>Set up application-specific parameters>Setup** to attend the requirements of Withholding reports for Egypt. 

The following configuration is used to classify the transactions in Withholding declaration form 41 report:

- **DiscountTaxTypeLookup**-> Column No 18 

Complete the following steps to setup the different lookups used in the generation of WHT declaration and related books reports. 

1. In the **Electronic reporting** workspace, select **Configurations > Setup** to set up the rules to identify how the transactions are goind to be classified in the WHT declaration report. 
1. Select the current version. On the Lookups FastTab, select the lookup name for example **DiscountTaxTypeLookup**. This lookup identifies the list of discount types required by the tax authority.
1. On the **Conditions** FastTab, select **Add** and in the new line in the Lookup result column, select the related line that represents the classification in the **Column 18**.
1. In the **Withholding tax item group** column, select the related code  that is used to identify the classification for example **Allowed discount**.  
1. Repeat steps 3-5 for all available lookups.
1. Select **Add** again, and then follow these steps to include the final record line:
   1. In the Lookup result column, select **Not applicable**. 
   1. In the remainder columns, select **Not blank**. 

> [!NOTE]
> By adding this last record **Not applicable**, you define the following rule: When the **Withholding tax item group** that is passed as an argument doesn't satisfy any of the previous rules, the transactions will not be included in the Withholding declaration form 41. Although this rule is not used when generating the report, the rule does help to avoid errors in report generation when there is a missing rule configuration.

## Set up General ledger parameters

To generate the WHT declaration forms reports in Microsoft Excel format, you must define an ER format on the **General ledger parameters** page.

1. Go to **Tax** > **Setup** > **General ledger parameters**.
2. On the **Withholding tax**  in the **WHT declaration format mapping** field, select **WHT Declaration Excel (EG)**. If you leave the field blank, the standard sales tax report will be generated in SSRS format.


![Declaration form](media/egypt-wht-declaration-setup1.png)

## Generate a Withholding declaration forms
The process of preparing and submitting a Withholding declaration forms for a specific period is based on withholding tax transactions posted during the settle and post payment tax job. For more information about global witholding tax see [Global withholding tax](../general-ledger/global-withholding-tax-overview.md).

Complete the following steps to generate the tax declaration report.

1. Go to **Tax > Declarations** > **Withholding tax** > **Withholding tax payment*.
2. Select the **Settlement period**.
3. Select the **From date.
4. Enter the **Transaction date** .
5. Select **OK** to confirm the above steps. 

In the nex dialog box, follow these additional steps to complete the generation of withholding forms reports
1. Select the form type: **Form No 41 **, **Form No 11**, **None**. Multiple selections are available. In case of selecting None, the standard report will be generated. 
1. Select the language. All reports are translated in **en-us** and **ar-eg**.
1. Enter the **Branch** and **Name** of Bank where the tax payment will be paid.
1. Select the **Business type***.
1. Enter the **Check** and **Document** number.
1. Enter the **Entity type**.
1. Enter the name of person who is registered to assign the form.
1. Click **OK** to confirm the generation of report. 

 
[!INCLUDE[footer-include](../../includes/footer-banner.md)]
