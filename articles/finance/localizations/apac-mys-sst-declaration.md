---
# required metadata

title: SST-02 declaration for Malaysia
description: This topic explains how to configure and generate the SST-02 return form for Malaysia.
author: sndray
manager: AnnBe
ms.date: 07/29/2020
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
[!include [banner](../includes/preview-banner.md)]

This topic explains how to set up and generate the SST-02 return form for legal entities in Malaysia.

The SST-02 return form is the official electronic form to declare and pay indirect taxes (SST) grouped by specific classifications as is described in the legislation by the tax authorities. Registered manufacturers and legal persons must declare SST-02 returns every two months according to the taxable period. The SST replaces the existing Goods and Services Tax (GST) and affects all domestic and import operations.

The SST-02 form report in Dynamics 365 Finance includes the following reports:

* Part B1: Detailed transactions by tariff code and service type
* Part B2: Consolidated amounts in accordance with layout proposed by Malaysian government

## Prerequisites
The primary address of the legal entity must be in Malaysia.

## Features enabling

In the **Feature management** workspace, enable the feature, **(Malaysia) Category hierarchy for Sales and purchase tax report.**

For more information about how to enable features, see [Feature management overview](../../fin-and-ops/get-started/feature-management/feature-management-overview.md).

## Download Electronic reporting configurations

The implementation of SST-02 return form for Malaysia is based on Electronic reporting (ER) configurations. For more information about the capabilities and concepts of configurable reporting, see [Electronic reporting](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md).

For production and user acceptance testing (UAT) environments, follow the instructions in the topic, [Download Electronic reporting configurations from Lifecycle Services](../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

To generate the SST-02 return form and the related reports in Malaysia legal entity, you need to upload the following configurations:

- Tax declaration model.version.67.xml 
- Tax declaration model mapping.version.67.93.xml 
- SST-02 Declaration Excel (MY).version.67.3.xml  or a later versions
 
After you've finished downloading the ER configurations from LCS or Global repository, complete the following steps.

1. In Dynamics 365 Finance in the Electronic reporting workspace, select the **Reporting configurations** tile. 
2. On the **Configurations** page, on the Action Pane, select **Exchange** > **Load from XML file**, and upload all the files in the order in which they are listed in the previous bullets.
After all the configurations are uploaded, the configuration tree should be present in Finance.

### Set up application-specific parameters
The SST-02 return form includes a set of boxes (lines) that correspond to specific parts of the SST Return form. Each box should include information about SST amounts and operations. To include the requirements established by the form, you must configure each box with the proper information that is coming automatically from the sales tax transactions generated from sales, purchases, or other operations where SST tax is posted through the sales tax code configuration.

The **Application-specific parameters** option lets the user establish the criteria of how the tax transactions will be collected and calculated in each box of the declaration form when generating the report, depending on the configuration of sales tax code.

1. In the Electronic reporting workspace, select **Configurations** > **Setup**. This action is used to set up the rules to identify the tax transaction in the related box of the SST-022 return form.
2. Select the current version, and on the **Lookups** FastTab, select **ReportFieldLookup**. This lookup identifies the list of boxes in the SST-02 form required by the tax authority. 
3. On the **Conditions** FastTab, select **Add** and in the new line in the **Lookup result** column, select the related line of SST-02 return form.
4.  In the **Tax code (Code)** column, select the sales tax code that is used to calculate the related line of SST-02 return form.
5. In the **Name** column, select the tax transaction classification where the sales tax code is used.
6. Repeat 3 - 5 for all of the SST-02 return form lines (boxes) and the combination of sales tax code and tax transaction types configured in your legal entity.
7. Select **Add** again, and in the **Lookup result** column, select **Other**.
8. In the **Tax code (Code)** and **Name** columns, select **Not blank**.

By adding the last record **Other**, you define the following rule: Whenever the **Tax code** and **Name** that is passed as an argument doesn't satisfy any of the previous rules, the transactions will not be included in SST-02 return form.  Although this rule is not used to generate the report, it does help to avoid errors in the generated report due to a missing rule configuration. 

The following table provides an example of potential configuration, but you can use another combination of tax code and name depending on the Finance implementation.

| Form            | ReportFieldLookup                     |                                                                                                           |      |              |                          |
|-----------------|---------------------------------------|-----------------------------------------------------------------------------------------------------------|------|--------------|--------------------------|
| Sections        | Lookup   result                       | Description                                                                                               | Line | Tax   code   | Name                     |
| PART B2-11a     | TaxableGoods5                         | Taxable   goods at 5% Rate                                                                                |    1 | SST5         | Sales                    |
| PART B2-11a     | TaxableGoods5                         | Taxable   goods at 5% Rate                                                                                |    2 | SST5_O       | Sales                    |
| PART B2-11b     | TaxableGoods10                        | Taxable   goods at 10% Rate                                                                               |    3 | SST10        | Sales                    |
| PART B2-11b     | TaxableGoods10                        | Taxable   goods at 10% Rate                                                                               |    4 | SST10_O      | Sales                    |
| PART B2-11c     | TaxableServices6                      | Taxable   services at 6% rate                                                                             |    5 | SST6         | Sales                    |
| PART B2-11d     | TaxableServiceGroupH                  | Taxable   services from group H                                                                           |    6 | SSTH         | Sales                    |
| PART B2-13      | TaxableCredit                         | Amount   of Tax_Deducted from Credit Note                                                                 |    7 | SST5         | SalesCreditNote          |
| PART B2-13      | TaxableCredit                         | Amount   of Tax_Deducted from Credit Note                                                                 |    8 | SST5_O       | SalesCreditNote          |
| PART B2-13      | TaxableCredit                         | Amount   of Tax_Deducted from Credit Note                                                                 |    9 | SST10        | SalesCreditNote          |
| PART B2-13      | TaxableCredit                         | Amount   of Tax_Deducted from Credit Note                                                                 |   10 | SST10_O      | SalesCreditNote          |
| PART B2-13      | TaxableCredit                         | Amount   of Tax_Deducted from Credit Note                                                                 |   11 | SST6         | SalesCreditNote          |
| PART B2-13      | TaxableCredit                         | Amount   of Tax_Deducted from Credit Note                                                                 |   12 | SSTH         | SalesCreditNote          |
| PART B2-18a     | Exempted_Export                       | Exempted   Export, Special Area and Designated Area                                                       |   13 | SSTE         | SalesExempt              |
| PART B2-18a     | Exempted_Export                       | Exempted   Export, Special Area and Designated Area                                                       |   14 | SSTE         | SalesExemptCreditNote    |
| PART B2-18b1    | Exempted_ClassOfPerson                | Schedule   A (Class of Person)                                                                            |   15 | SSTE_A       | SalesExempt              |
| PART B2-18b1    | Exempted_ClassOfPerson                | Schedule   A (Class of Person)                                                                            |   16 | SSTE_A       | SalesExemptCreditNote    |
| PART B2-18b2    | Exempted_Manufacturer                 | Schedule   B (Manufacturer of specific nontaxable    goods)                                               |   17 | SSTE_B       | SalesExempt              |
| PART B2-18b2    | Exempted_Manufacturer                 | Schedule   B (Manufacturer of specific nontaxable    goods)                                               |   18 | SSTE_B       | SalesExemptCreditNote    |
| PART B2-18b3i   | Exempted_CRawMaterials                | Purchase   or Importation of Raw Material Exempted    From Sales Tax                                      |   19 | SSTE_C1      | SalesExempt              |
| PART B2-18b3i   | Exempted_CRawMaterials                | Purchase   or Importation of Raw Material Exempted    From Sales Tax                                      |   20 | SSTE_C1      | SalesExemptCreditNote    |
| PART B2-18b3ii  | Exempted_CManufacturer                | Purchase   or  Importation of Raw Material on   behalf of Registered Manufacturer Exempted From Sales Tax |   21 | SSTE_C2      | SalesExempt              |
| PART B2-18b3ii  | Exempted_CManufacturer                | Purchase   or  Importation of Raw Material on   behalf of Registered Manufacturer Exempted From Sales Tax |   22 | SSTE_C2      | SalesExemptCreditNote    |
| PART B2-18b3iii | Exempted_CValueofWork                 | Value   of Work Performed Exempted from Sales Tax                                                         |   23 | SSTE_C3      | SalesExempt              |
| PART B2-18b3iii | Exempted_CValueofWork                 | Value   of Work Performed Exempted from Sales Tax                                                         |   24 | SSTE_C3      | SalesExemptCreditNote    |
| PART B2-19      | PurchaseImportRawMaterial             | Purchase   or Importation of Raw materials exempted from sales tax                                        |   25 | SSTP_1       | PurchaseExempt           |
| PART B2-19      | PurchaseImportRawMaterial             | Purchase   or Importation of Raw materials exempted from sales tax                                        |   26 | SSTP_1       | PurchaseExemptCreditNote |
| PART B2-20      | PurchaseImportRawMaterialManufacturer | Purchase   or Importation of Raw material on behalf of Registered Manufacturer exempted   from sales tax  |   27 | SSTP_2       | PurchaseExempt           |
| PART B2-20      | PurchaseImportRawMaterialManufacturer | Purchase   or Importation of Raw material on behalf of Registered Manufacturer exempted   from sales tax  |   28 | SSTP_2       | PurchaseExemptCreditNote |
| PART B2-21      | PurchaseOtherExempted                 | Value   of work performed exempted from sales tax                                                         |   29 | SSTP_3       | PurchaseExempt           |
| PART B2-21      | PurchaseOtherExempted                 | Value   of work performed exempted from sales tax                                                         |   30 | SSTP_3       | PurchaseExempCreditNote  |
| NOT APPLICABLE  | Other                                 | Other                                                                                                     |   31 | *No   blank* | *No   Blank*             |

  
9. Repeat the previous steps for the lookup name, **ReportFieldDetailed**. The following table provides an example of a potential configuration, however you can use another combination of tax code and name depending on your Finance implementation

| Form           | ReportFieldDetailed     |                                                                         |      |              |                 |
|----------------|-------------------------|-------------------------------------------------------------------------|------|--------------|-----------------|
| Sections       | Lookup   result         | Description                                                             | Line | Tax   code   | Name            |
| PART B1-8      | TaxableGoods_B18        | Value   of Taxable Goods Sold  Value of Work   Performed                |    1 | SST5         | Sales           |
| PART B1-8      | TaxableGoods_B18        | Value   of Taxable Goods Sold  Value of Work   Performed                |    2 | SST10        | Sales           |
| PART B1-8      | TaxableGoods_B18        | Value   of Taxable Goods Sold  Value of Work   Performed                |    3 | SST5         | SalesCreditNote |
| PART B1-8      | TaxableGoods_B18        | Value   of Taxable Goods Sold  Value of Work   Performed                |    4 | SST10        | SalesCreditNote |
| PART B1-9      | OwnUsedFreeServices_B19 | Value   of Goods For Own Used or Disposed or Values    of Free Services |    5 | SST5_O       | Sales           |
| PART B1-9      | OwnUsedFreeServices_B19 | Value   of Goods For Own Used or Disposed or Values    of Free Services |    6 | SST10_O      | Sales           |
| PART B1-9      | OwnUsedFreeServices_B19 | Value   of Goods For Own Used or Disposed or Values    of Free Services |    7 | SST5_O       | SalesCreditNote |
| PART B1-9      | OwnUsedFreeServices_B19 | Value   of Goods For Own Used or Disposed or Values    of Free Services |    8 | SST10_O      | SalesCreditNote |
| PART B1-10     | TaxableServices_B110    | Value   of Taxable Service                                              |    9 | SST6         | Sales           |
| PART B1-10     | TaxableServices_B110    | Value   of Taxable Service                                              |   10 | SSTH         | Sales           |
| PART B1-10     | TaxableServices_B110    | Value   of Taxable Service                                              |   11 | SST6         | SalesCreditNote |
| PART B1-10     | TaxableServices_B110    | Value   of Taxable Service                                              |   12 | SSTH         | SalesCreditNote |
| NOT APPLICABLE | Other                   | Other                                                                   |   13 | *No   blank* | *No   Blank*    |
  
10. After the comfinguration is complete, in the **State** field, select **Completed**, select **Save**, and then close the **Application specific parameters** page.

> [!NOTE]
> To avoid issues when the report is generated, create all mappings where the sales tax codes are posted. For example, if the line has ommitted the operations name, **SalesCreditNote** in this configuration, and tax transactions are posted by using sales tax code SST5, you will face some issues when the report is generated. We recommend that you go to **Tax** > **Inquire** > **Posted sales tax** to review all of the posted sales tax codes and those one that are not included in this mapping of the configuration.

The following table provides a definition of the column **Name** to understand how the tax transactions are classified:
  

| Classifier value                | Condition |
|---------------------------------|-----------|
| PurchaseCreditNote              | <ul><li>Credit note</li><li>Tax direction = Sales tax receivable</li></ul> |
| Purchase                        | <ul><li>Not credit note</li><li>Tax direction = Sales tax receivable</li></ul> |
| SalesCreditNote                 | <ul><li>Credit note</li><li>Tax direction = Sales tax payable</li></ul> |
| Sales                           | <ul><li>Not credit note</li><li>Tax direction = Sales tax payable</li></ul> |
| PurchaseExemptCreditNote        | <ul><li>Credit note</li><li>Tax direction = Tax-free purchase</li></ul> |
| PurchaseExempt                  | <ul><li>Not credit note</li><li>Tax direction = Tax-free purchase</li></ul> |
| SalesExemptCreditNote           | <ul><li>Credit note</li><li>Tax direction = Tax-free sales</li></ul> |
| SaleExempt                      | <ul><li>Not credit note</li><li>Tax direction = Tax-free sales</li></ul> |
| UseTaxCreditNote                | <ul><li>Credit note</li><li>Tax direction = Use tax</li></ul> |
| UseTax                          | <ul><li>Not credit note</li><li>Tax direction = Use tax</li></ul> |
| PurchaseReverseChargeCreditNote | <ul><li>Credit note</li><li>Tax direction = Sales tax receivable</li><li>ReverseCharge_W = Yes</li></ul> |
| PurchaseReverseCharge           | <ul><li>Not credit note</li><li>Tax direction = Sales tax receivable</li><li>ReverseCharge_W = Yes</li></ul> |
| SalesReverseChargeCreditNote    | <ul><li>Credit note</li><li>Tax direction = Sales tax payable</li><li>ReverseCharge_W = Yes</li></ul> |
| SalesReverseCharge              | <ul><li>Not credit note</li><li>Tax direction = Sales tax payable</li><li>ReverseCharge_W = Yes</li></ul> |  
  
## Set up General ledger parameters

To generate the SST-02 return form report in Excel you must define an ER format on the **General ledger parameters** page.

1. Go to **Tax** > **Setup** > **General ledger parameters**.
2. On the **Sales tax** tab, in the **Tax options** section, in the **Electronic reporting** field, select **SST-02 Declaration Excel (MY)**. If you leave the **SST statement format mapping** field blank, the standard sales tax report will be generated in SSRS format.
3. Select the **Category hierarchy**. This category enables the **Commodity code** on the **Foreign trade** tab to allow users to select and classify goods and services. The description of this classification is detailed in sales and purchase transaction reports.

## Generate a SST-02 return report

The process of preparing and submitting a SST-02 return report for a period is based on sales tax payment transactions that were posted during the **Settle and post sales tax** job. For more information about sales tax settlement and reporting, see [Sales tax overview](../general-ledger/indirect-taxes-overview.md)

Complete the following steps to generate the tax declaration report.

1. Go to **Tax** > **Declarations** > **Sales tax** > **Report sales tax for settlement period** or **Settle and post sales tax**
2. Select the **Settlement period**.
3. Select the from date.
4. Select the sales tax payment version and then select **OK** to save your changes.
6. Select the repot type:

	* SST for goods and services
	* SST for goods
	* SST for services
	
6. Select **OK** to confirm and generate the report.
		
