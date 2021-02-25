---
# required metadata

title: VAT declaration for Egypt
description: This topic explains how to configure and generate the VAT return form for Egypt.
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
ms.dyn365.ops.version: 10.0.17
---

#  VAT declaration for Egypt (EG-00002)

[!include[banner](../includes/banner.md)]

## Overview
This topic explains how to set up and generate the VAT return form, sales and purchase books for legal entities in Egypt.

The VAT return form for Egypt the official document that summarizes the total output VAT tax amount due, the total input VAT tax amount recoverable, and the related VAT tax amount liability. The form is used for all types of taxpayers and should be completed manually through the tax authority portal. The VAT return form is commonly referred to as VAT return filing.

The VAT return form in Dynamics 365 Finance includes the following reports:

- VAT return form, which provides a breakdown of amounts, adjustments, and VAT amount per line item in the VAT return form as is described in the legislation.
- Sales transactions book
- Purchase transaction book

## Prerequisites
The primary address of the legal entity must be in Egypt.
In the **Feature management** workspace, enable the following features:

- (Egypt) Category hierarchy for Sales and purchase tax report.

For more information about how to enable features, see Feature management overview.

In the **Electronic reporting** workspace, import the following Electronic Reporting formats from the repository:

- VAT declaration Excel (EG)

> **Note**: The formats above are based on **Tax declaration model** and use **Tax declaration model mapping**. These additional configurations will be automatically imported.

For more information about how to import Electronic Reporting configurations, see [Download Electronic reporting configurations from Lifecycle Services](../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

## Download Electronic reporting configurations

The implementation of the VAT return form for Bahrain is based on Electronic reporting (ER) configurations. For more information about the capabilities and concepts of configurable reporting, see [Electronic reporting](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md).

For production and user acceptance testing (UAT) environments, follow the instructions [Download Electronic reporting configurations from Lifecycle Services](../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

To generate the VAT return form and related reports in a Egypt legal entity, you need to upload the following configurations:

- Tax declaration model.version.70.xml or later version
- Tax declaration model mapping.version.70.120.xml or a later version
- VAT Declaration Excel (EG).version.70.32  or a later version

After you've finished downloading the ER configurations from Lifecycle Services (LCS) or the global repository, complete the following steps.

1. Go to the **Electronic reporting** workspace. Select the Reporting configurations tile.
1. On the **Configurations** page, on the Action Pane, select **Exchange > Load from XML file**.
1. Upload all the files in the order in which they are listed in the previous bullets. After all the configurations are uploaded, the configuration tree should be present in Finance.

## Set up application-specific parameters

The Application-specific parameters option let the users to establish the criteria of how the tax transactions will be classified and calculated in each line  when the report is generated depending on the configuration of **item sales tax group**, **sales tax group**, **sales tax code** or other criteria established in the defnition of lookup.

The Sales and Purchase book reports for Egypt include a set of columns that correspond to specific transactions classifications as type of operation, products and documents that are specific for Egypt. Instead of including these new classifications as new entry data when the transactions are posted, the classifications will be determined based on different Lookups we have introduced in **Configurations>Set up application-specific parameters>Setup** to attend the requirements of VAT reports for Egypt. 

![Declaration form](media/egypt-vat-declaration-setup1.png)

These are the lookups configurations used to classify the transactions in Purchase and  Sales VAT books reports:

- **PurchaseItemTypeLookup**-> Column O: Item type
- **VATRateTypeLookup** -> Column B: Tax Type
- **VATRateTypeLookup** -> Column C: Table item type
- **PurchaseOperationTypeLookup** -> Column A: Document type
- **SalesOperationTypeLookup** -> Column N: Operation type
- **SalesItemTypeLookup** -> Column O: Item type

Complete the following steps to setup the different lookups used in the generation of VAT declaration and related books reports. 

1. In the **Electronic reporting** workspace, select **Configurations > Setup** to set up the rules to identify the tax transaction into the related box of the VAT return form.
1. Select the current version. On the Lookups FastTab, select the lookup name for example **SalesItemTypeLookup**. This lookup identifies the list of above classifications in the Sales VAT book required by tax authority.
1. On the **Conditions** FastTab, select **Add** and in the new line in the Lookup result column, select the related line that represents the classification in the **Column O**.
1. In the **Sales tax group** column, select the sales tax group  that is used to identify the classification for example **Domestic sales invoice**. You can also use **Item Sales tax group**, **tax code*** or the combination of tree attributes in case the configuration is defined in another way. 
1. In the **Name** column, select the tax transaction classification.
1. Repeat steps 3-5 for all available lookups.
1. Select **Add** again, and then follow these steps to include the final record line:
   1. In the Lookup result column, select **Not applicable**. 
   1. In the remainder columns, select **Not blank**. 

> **Note**: By adding this last record **Not applicable**, you define the following rule: When the **sales tax group**, **item sales tax group**, **tax code** and **name** that is passed as an argument doesn't satisfy any of the previous rules, the transactions will not be included in the Sales VAT book. Although this rule is not used when generating the report, the rule does help to avoid errors in report generation when there is a missing rule configuration.

The tables below represent an example of suggested configuration for the described classifications. 

|    <br>SalesItemTypeLookup        |    <br>Line    |    <br>Sales tax group     |    <br>Item sales tax group     |    <br>Tax code (Code)    |    <br>Name                     |
|-----------------------------------|----------------|----------------------------|---------------------------------|---------------------------|---------------------------------|
|    <br>Domestic                   |    <br>1       |    <br>VAT_LOCAL           |    <br>*Not   blank*            |    <br>*Not   blank*      |    <br>Sales                    |
|    <br>Domestic                   |    <br>2       |    <br>VAT_LOCAL           |    <br>*Not   blank*            |    <br>*Not   blank*      |    <br>SalesCreditNote          |
|    <br>Domestic                   |    <br>3       |    <br>VAT_FINALC          |    <br>*Not   blank*            |    <br>*Not   blank*      |    <br>Sales                    |
|    <br>Domestic                   |    <br>4       |    <br>VAT_FINALC          |    <br>*Not   blank*            |    <br>*Not   blank*      |    <br>SalesCreditNote          |
|    <br>Domestic                   |    <br>5       |    <br>VAT_PUBLIO          |    <br>*Not   blank*            |    <br>*Not   blank*      |    <br>Sales                    |
|    <br>Domestic                   |    <br>6       |    <br>VAT_PUBLIO          |    <br>*Not   blank*            |    <br>*Not   blank*      |    <br>SalesCreditNote          |
|    <br>Export                     |    <br>7       |    <br>VAT_EXPORT          |    <br>*Not   blank*            |    <br>*Not   blank*      |    <br>Sales                    |
|    <br>Export                     |    <br>8       |    <br>VAT_EXPORT          |    <br>*Not   blank*            |    <br>*Not   blank*      |    <br>SalesCreditNote          |
|    <br>Machine   and Equipment    |    <br>9       |    <br>*Not   blank*       |    <br>VAT_M&E                  |    <br>*Not   blank*      |    <br>Sales                    |
|    <br>Machine   and Equipment    |    <br>10      |    <br>*Not   blank*       |    <br>VAT_M&E                  |    <br>*Not   blank*      |    <br>SalesCreditNote          |
|    <br>Parts   machines           |    <br>11      |    <br>*Not   blank*       |    <br>VAT_PARTS                |    <br>*Not   blank*      |    <br>Sales                    |
|    <br>Parts   machines           |    <br>12      |    <br>*Not   blank*       |    <br>VAT_PARTS                |    <br>*Not   blank*      |    <br>SalesCreditNote          |
|    <br>Exemptions                 |    <br>13      |    <br>VAT_EXE             |    <br>*Not   blank*            |    <br>*Not   blank*      |    <br>SaleExempt               |
|    <br>Exemptions                 |    <br>14      |    <br>VAT_EXE             |    <br>*Not   blank*            |    <br>*Not   blank*      |    <br>SalesExemptCreditNote    |
|    <br>Not   Applicable           |    <br>15      |    <br>*Blank*             |    <br>*Blank*                  |    <br>VAT_ADJ            |    <br>*Not   blank*            |



