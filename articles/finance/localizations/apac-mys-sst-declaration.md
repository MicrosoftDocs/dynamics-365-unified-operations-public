---
# required metadata

title: SST-02 declaration for Malaysia
description: This topic explains how to configure and generate the SST-02 return form for Malaysia.
author: sndray
manager: AnnBe
ms.date: 07/23/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Bahrain
# ms.search.industry: 
ms.author: sndray
ms.search.validFrom: 2020-06-03
ms.dyn365.ops.version: 10.0.13

---

# SST-02 declaration for Malaysia

[!include [banner](../includes/banner.md)]

This topic explains how to set up and generate the SST-02 return form for legal entities in Malaysia.

The SST-02 return form is the official electronic form to declare and pay indirect taxes (SST) grouped by specific classifications as is described in the legislation by the tax authorities. Registered manufacturers and legal persons must declare SST-02 returns form every two months according to the taxable period. The SST replaces the existing Goods and Services Tax (GST) and affects all domestic and import operations.

The SST-02 form report in Dynamics 365 Finance includes the following reports:

* **Part B1**: Detailed transactions by tariff code and service type.
* **Part B2**: Consolidated amounts in accordance with layout proposed by Malaysian government

## Prerequisites
The primary address of the legal entity must be in Malaysia.

## Features enabling

In the Feature management workspace, enable the following features: **(Malaysia) Category hierarchy for Sales and purchase tax report.**

For more information about how to enable features, see [Feature management overview](../../fin-and-ops/get-started/feature-management/feature-management-overview.md).

## Download Electronic reporting configurations

The implementation of SST-02 return form for Malaysia is based on Electronic reporting (ER) configurations. For more information about the capabilities and concepts of configurable reporting, see [Electronic reporting](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md).

For production and user acceptance testing (UAT) environments, follow the instructions in Download Electronic reporting configurations from Lifecycle Services to download ER configurations.

To generate the VAT return form and related reports in Malaysia legal entity,  you need to upload the following configurations:
	• Tax declaration model.version.67.xml 
	• Tax declaration model mapping.version.67.93.xml 
	• SST-02 Declaration Excel (MY).version.67.3.xml  or a later versions
 
After you've finished downloading the ER configurations from LCS or Global repository, follow these steps.

1. In Dynamics 365 Finance in the Electronic reporting workspace, select the **Reporting configurations** tile. 
2. Then, on the Configurations page, on the Action Pane, select **Exchange > Load from XML file**, and upload all the files in the order in which they are listed in the previous bullets.
3. After all the configurations are uploaded, the configuration tree should be present in Finance and Operations.

### Set up application-specific parameters
The SST-02 return form includes a set of boxes (lines) which correspond to specific parts of the SST Return form. Each box should include information about SST amounts and operations. In order to include the requirements established by the form, the user needs to configure each box with the proper information that is coming automatically from sales tax transactions generated from sales , purchase or other operations where SST tax is posted through the sales tax code configuration.

The **Application-specific parameters** option let the users to establish the criteria of how the tax transactions will be collected and calculated in each box (line) of declaration form during the generation of report depending on the configuration of sales tax code .

1. In the Electronic reporting workspace, select **Configurations > Setup**. This action is used to setup the rules to identify the tax transaction into the related box of VAT return form.
2. Select the current version
3. On the **Lookups** FastTab select the Lookup name ***ReportFieldLookup***. This lookup identifies the list of lines (boxes) in the VAT form required by tax authority . 
4. On the **Conditions** FastTab, select **Add**.
5. In the new line created follow these steps:
   a. In the **Lookup result** column, select the related line of SST-02 return form.
   b. In the **Tax code (Code)** column, select the sales tax code that is used to calculate the related line of VAT return form.
   c. In the **Name** column, select the tax transaction classification where the sales tax code is used
6. Repeat the same steps for all SST-02 return form lines (boxes) and the combination of sales tax code and tax transaction types configured in your legal entity
7. Select Add again, and then follow these steps to include the final record line
   * In the **Lookup result** column, select the Other value.
   * In the **Tax code (Code)** column, select the ***Not blank*** option;
   * In the **Name** column, select the ***Not blank*** option as well

By adding this last record (Other), you define the following rule: Whenever the Tax code and Name that is passed as an argument doesn't satisfy any of the previous rules, the transactions will not be included in VAT return form.  Although this rule is not used in the generation of the report,  introduced to avoid errors in report generation in case of missing rule configuration. 

The table below represents an example of potential configuration, but you can use another combination of tax code and name depending on the Dynamics Finance 365 implementation 

|    <br>Form               |    <br>ReportFieldLookup                        |    <br>                                                                                                             |    <br>        |    <br>                |    <br>                            |
|---------------------------|-------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|----------------|------------------------|------------------------------------|
|    <br>Sections           |    <br>Lookup result                            |    <br>Description                                                                                                  |    <br>Line    |    <br>Tax code        |    <br>Name                        |
|    <br>PART B2-11a        |    <br>TaxableGoods5                            |    <br>Taxable   goods at 5% Rate                                                                                   |    <br>1       |    <br>SST5            |    <br>Sales                       |
|    <br>PART B2-11a        |    <br>TaxableGoods5                            |    <br>Taxable   goods at 5% Rate                                                                                   |    <br>2       |    <br>SST5_O          |    <br>Sales                       |
|    <br>PART B2-11b        |    <br>TaxableGoods10                           |    <br>Taxable   goods at 10% Rate                                                                                  |    <br>3       |    <br>SST10           |    <br>Sales                       |
|    <br>PART B2-11b        |    <br>TaxableGoods10                           |    <br>Taxable   goods at 10% Rate                                                                                  |    <br>4       |    <br>SST10_O         |    <br>Sales                       |
|    <br>PART B2-11c        |    <br>TaxableServices6                         |    <br>Taxable   services at 6% rate                                                                                |    <br>5       |    <br>SST6            |    <br>Sales                       |
|    <br>PART B2-11d        |    <br>TaxableServiceGroupH                     |    <br>Taxable   services from group H                                                                              |    <br>6       |    <br>SSTH            |    <br>Sales                       |
|    <br>PART B2-13         |    <br>TaxableCredit                            |    <br>Amount   of Tax_Deducted from Credit Note                                                                    |    <br>7       |    <br>SST5            |    <br>SalesCreditNote             |
|    <br>PART B2-13         |    <br>TaxableCredit                            |    <br>Amount   of Tax_Deducted from Credit Note                                                                    |    <br>8       |    <br>SST5_O          |    <br>SalesCreditNote             |
|    <br>PART B2-13         |    <br>TaxableCredit                            |    <br>Amount   of Tax_Deducted from Credit Note                                                                    |    <br>9       |    <br>SST10           |    <br>SalesCreditNote             |
|    <br>PART B2-13         |    <br>TaxableCredit                            |    <br>Amount   of Tax_Deducted from Credit Note                                                                    |    <br>10      |    <br>SST10_O         |    <br>SalesCreditNote             |
|    <br>PART B2-13         |    <br>TaxableCredit                            |    <br>Amount   of Tax_Deducted from Credit Note                                                                    |    <br>11      |    <br>SST6            |    <br>SalesCreditNote             |
|    <br>PART B2-13         |    <br>TaxableCredit                            |    <br>Amount   of Tax_Deducted from Credit Note                                                                    |    <br>12      |    <br>SSTH            |    <br>SalesCreditNote             |
|    <br>PART B2-18a        |    <br>Exempted_Export                          |    <br>Exempted   Export, Special Area and Designated Area                                                          |    <br>13      |    <br>SSTE            |    <br>SalesExempt                 |
|    <br>PART B2-18a        |    <br>Exempted_Export                          |    <br>Exempted   Export, Special Area and Designated Area                                                          |    <br>14      |    <br>SSTE            |    <br>SalesExemptCreditNote       |
|    <br>PART B2-18b1       |    <br>Exempted_ClassOfPerson                   |    <br>Schedule   A (Class of Person)                                                                               |    <br>15      |    <br>SSTE_A          |    <br>SalesExempt                 |
|    <br>PART B2-18b1       |    <br>Exempted_ClassOfPerson                   |    <br>Schedule   A (Class of Person)                                                                               |    <br>16      |    <br>SSTE_A          |    <br>SalesExemptCreditNote       |
|    <br>PART B2-18b2       |    <br>Exempted_Manufacturer                    |    <br>Schedule   B (Manufacturer of specific nontaxable    goods)                                                  |    <br>17      |    <br>SSTE_B          |    <br>SalesExempt                 |
|    <br>PART B2-18b2       |    <br>Exempted_Manufacturer                    |    <br>Schedule   B (Manufacturer of specific nontaxable    goods)                                                  |    <br>18      |    <br>SSTE_B          |    <br>SalesExemptCreditNote       |
|    <br>PART B2-18b3i      |    <br>Exempted_CRawMaterials                   |    <br>Purchase   or Importation of Raw Material Exempted    From Sales Tax                                         |    <br>19      |    <br>SSTE_C1         |    <br>SalesExempt                 |
|    <br>PART B2-18b3i      |    <br>Exempted_CRawMaterials                   |    <br>Purchase   or Importation of Raw Material Exempted    From Sales Tax                                         |    <br>20      |    <br>SSTE_C1         |    <br>SalesExemptCreditNote       |
|    <br>PART B2-18b3ii     |    <br>Exempted_CManufacturer                   |    <br>Purchase   or  Importation of Raw Material on   behalf of Registered Manufacturer Exempted From Sales Tax    |    <br>21      |    <br>SSTE_C2         |    <br>SalesExempt                 |
|    <br>PART B2-18b3ii     |    <br>Exempted_CManufacturer                   |    <br>Purchase   or  Importation of Raw Material on   behalf of Registered Manufacturer Exempted From Sales Tax    |    <br>22      |    <br>SSTE_C2         |    <br>SalesExemptCreditNote       |
|    <br>PART B2-18b3iii    |    <br>Exempted_CValueofWork                    |    <br>Value   of Work Performed Exempted from Sales Tax                                                            |    <br>23      |    <br>SSTE_C3         |    <br>SalesExempt                 |
|    <br>PART B2-18b3iii    |    <br>Exempted_CValueofWork                    |    <br>Value   of Work Performed Exempted from Sales Tax                                                            |    <br>24      |    <br>SSTE_C3         |    <br>SalesExemptCreditNote       |
|    <br>PART B2-19         |    <br>PurchaseImportRawMaterial                |    <br>Purchase   or Importation of Raw materials exempted from sales tax                                           |    <br>25      |    <br>SSTP_1          |    <br>PurchaseExempt              |
|    <br>PART B2-19         |    <br>PurchaseImportRawMaterial                |    <br>Purchase   or Importation of Raw materials exempted from sales tax                                           |    <br>26      |    <br>SSTP_1          |    <br>PurchaseExemptCreditNote    |
|    <br>PART B2-20         |    <br>PurchaseImportRawMaterialManufacturer    |    <br>Purchase   or Importation of Raw material on behalf of Registered Manufacturer exempted   from sales tax     |    <br>27      |    <br>SSTP_2          |    <br>PurchaseExempt              |
|    <br>PART B2-20         |    <br>PurchaseImportRawMaterialManufacturer    |    <br>Purchase   or Importation of Raw material on behalf of Registered Manufacturer exempted   from sales tax     |    <br>28      |    <br>SSTP_2          |    <br>PurchaseExemptCreditNote    |
|    <br>PART B2-21         |    <br>PurchaseOtherExempted                    |    <br>Value   of work performed exempted from sales tax                                                            |    <br>29      |    <br>SSTP_3          |    <br>PurchaseExempt              |
|    <br>PART B2-21         |    <br>PurchaseOtherExempted                    |    <br>Value   of work performed exempted from sales tax                                                            |    <br>30      |    <br>SSTP_3          |    <br>PurchaseExempCreditNote     |
|    <br>NOT APPLICABLE     |    <br>Other                                    |    <br>Other                                                                                                        |    <br>31      |    <br>*No   blank*    |    <br>*No   Blank*                |


