---
# required metadata

title: SST-02 declaration for Malaysia
description: This topic explains how to configure and generate the SST-02 return form for Malaysia.
author: sndray
ms.date: 09/11/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
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

The SST-02 return form is the official electronic form that is used to declare and pay indirect taxes (Sales and Services Tax \[SST\]). These indirect taxes are grouped by specific classifications, as described by the tax authorities in the legislation. Registered manufacturers and legal persons must declare SST-02 returns every two months, according to the taxable period. SST replaces the existing Goods and Services Tax (GST), and affects all domestic and import operations.

The SST-02 return form report in Microsoft Dynamics 365 Finance includes the following reports:

* Part B1: Detailed transactions by tariff code and service type
* Part B2: Consolidated amounts in accordance with layout proposed by Malaysian government

## Prerequisites

The primary address of the legal entity must be in Malaysia.

## Turn on the feature

In the **Feature management** workspace, turn on the feature that is named **(Malaysia) Category hierarchy for Sales and purchase tax report**.

For more information about how to turn on features, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Download Electronic reporting configurations

The implementation of the SST-02 return form for Malaysia is based on Electronic reporting (ER) configurations. For more information about the capabilities and concepts of configurable reporting, see [Electronic reporting](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md).

For production and user acceptance testing (UAT) environments, follow the instructions in [Download Electronic reporting configurations from Lifecycle Services](../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

To generate the SST-02 return form and the related reports in a Malaysian legal entity, you must upload the following ER configurations:

1. Tax declaration model.version.67.xml 
2. Tax declaration model mapping.version.67.93.xml 
3. SST-02 Declaration Excel (MY).version.67.3.xml or a later version
 
After you've finished downloading the ER configurations from Microsoft Dynamics Lifecycle Services (LCS) or the Global repository, follow these steps.

1. In Finance, in the **Electronic reporting** workspace, select the **Reporting configurations** tile. 
2. On the **Configurations** page, on the Action Pane, select **Exchange** \> **Load from XML file**, and upload all the files in the order in which they are listed earlier in this section.

After all the ER configurations are uploaded, the configuration tree should be present in Finance.

### Set up application-specific parameters

The SST-02 return form includes a set of boxes (lines) that correspond to specific parts of the SST return form. Each box should include information about SST amounts and operations. To meet the requirements that are established by the form, you must configure each box with the correct information. This information automatically comes from the sales tax transactions that are generated from sales, purchases, or other operations where SST tax is posted through the sales tax code configuration.

The **Application-specific parameters** option lets you define the criteria that determine how the tax transactions will be collected and calculated in each box of the declaration form when you generate the report, depending on the sales tax code configuration.

1. In the **Electronic reporting** workspace, select **Configurations** \> **Setup** to set up the rules that are used to identify the tax transaction in the related box of the SST-022 return form.
2. Select the current version, and then, on the **Lookups** FastTab, select **ReportFieldLookup**. This lookup identifies the list of boxes that are required by the tax authority in the SST-02 return form. 
3. On the **Conditions** FastTab, select **Add**, and then, on the new line, in the **Lookup result** field, select the related line of the SST-02 return form.
4. In the **Tax code (Code)** field, select the sales tax code that is used to calculate the related line of the SST-02 return form.
5. In the **Name** field, select the tax transaction classification where the sales tax code is used.
6. Repeat steps 3 through 5 for all the lines (boxes) of the SST-02 return form, and for the combination of sales tax codes and tax transaction types that is configured in your legal entity.
7. Select **Add** again, and then, in the **Lookup result** field, select **Other**.
8. In the **Tax code (Code)** and **Name** fields, select **Not blank**.

    By adding the last record, **Other**, you define the following rule: If the tax code and name that are passed as an argument doesn't satisfy any of the previous rules, the transactions won't be included in the SST-02 return form. Although this rule isn't used to generate the report, it helps prevent errors from occurring in the generated report because of a missing rule configuration. 

    The following table provides an example of a configuration. However, you can use a different combination of a tax code and a name, depending on your Finance implementation.

    | Form (section)           | Lookup result (ReportFieldLookup)                     |        Description                                                                                              |    Line      |   Tax code           |     Name                     |
    |-----------------|---------------------------------------|------------------------------------------------------------------------------------------------------|----------|--------------|--------------------------|
    | PART B2-11a     | TaxableGoods5                         | Taxable goods at 5% Rate                                                                             | 1        | SST5         | Sales                    |
    | PART B2-11a     | TaxableGoods5                         | Taxable goods at 5% Rate                                                                             | 2        | SST5\_O      | Sales                    |
    | PART B2-11b     | TaxableGoods10                        | Taxable goods at 10% Rate                                                                            | 3        | SST10        | Sales                    |
    | PART B2-11b     | TaxableGoods10                        | Taxable goods at 10% Rate                                                                            | 4        | SST10\_O     | Sales                    |
    | PART B2-11c     | TaxableServices6                      | Taxable services at 6% rate                                                                          | 5        | SST6         | Sales                    |
    | PART B2-11d     | TaxableServiceGroupH                  | Taxable services from group H                                                                        | 6        | SSTH         | Sales                    |
    | PART B2-13      | TaxableCredit                         | Amount of Tax\_Deducted from Credit Note                                                             | 7        | SST5         | SalesCreditNote          |
    | PART B2-13      | TaxableCredit                         | Amount of Tax\_Deducted from Credit Note                                                             | 8        | SST5\_O      | SalesCreditNote          |
    | PART B2-13      | TaxableCredit                         | Amount of Tax\_Deducted from Credit Note                                                             | 9        | SST10        | SalesCreditNote          |
    | PART B2-13      | TaxableCredit                         | Amount of Tax\_Deducted from Credit Note                                                             | 10       | SST10\_O     | SalesCreditNote          |
    | PART B2-13      | TaxableCredit                         | Amount of Tax\_Deducted from Credit Note                                                             | 11       | SST6         | SalesCreditNote          |
    | PART B2-13      | TaxableCredit                         | Amount of Tax\_Deducted from Credit Note                                                             | 12       | SSTH         | SalesCreditNote          |
    | PART B2-18a     | Exempted\_Export                      | Exempted Export, Special Area and Designated Area                                                    | 13       | SSTE         | SalesExempt              |
    | PART B2-18a     | Exempted\_Export                      | Exempted Export, Special Area and Designated Area                                                    | 14       | SSTE         | SalesExemptCreditNote    |
    | PART B2-18b1    | Exempted\_ClassOfPerson               | Schedule A (Class of Person)                                                                         | 15       | SSTE\_A      | SalesExempt              |
    | PART B2-18b1    | Exempted\_ClassOfPerson               | Schedule A (Class of Person)                                                                         | 16       | SSTE\_A      | SalesExemptCreditNote    |
    | PART B2-18b2    | Exempted\_Manufacturer                | Schedule B (Manufacturer of specific nontaxable goods)                                               | 17       | SSTE\_B      | SalesExempt              |
    | PART B2-18b2    | Exempted\_Manufacturer                | Schedule B (Manufacturer of specific nontaxable goods)                                               | 18       | SSTE\_B      | SalesExemptCreditNote    |
    | PART B2-18b3i   | Exempted\_CRawMaterials               | Purchase or Importation of Raw Material Exempted From Sales Tax                                      | 19       | SSTE\_C1     | SalesExempt              |
    | PART B2-18b3i   | Exempted\_CRawMaterials               | Purchase or Importation of Raw Material Exempted From Sales Tax                                      | 20       | SSTE\_C1     | SalesExemptCreditNote    |
    | PART B2-18b3ii  | Exempted\_CManufacturer               | Purchase or Importation of Raw Material on behalf of Registered Manufacturer Exempted From Sales Tax | 21       | SSTE\_C2     | SalesExempt              |
    | PART B2-18b3ii  | Exempted\_CManufacturer               | Purchase or Importation of Raw Material on behalf of Registered Manufacturer Exempted From Sales Tax | 22       | SSTE\_C2     | SalesExemptCreditNote    |
    | PART B2-18b3iii | Exempted\_CValueofWork                | Value of Work Performed Exempted from Sales Tax                                                      | 23       | SSTE\_C3     | SalesExempt              |
    | PART B2-18b3iii | Exempted\_CValueofWork                | Value of Work Performed Exempted from Sales Tax                                                      | 24       | SSTE\_C3     | SalesExemptCreditNote    |
    | PART B2-19      | PurchaseImportRawMaterial             | Purchase or Importation of Raw materials exempted from sales tax                                     | 25       | SSTP\_1      | PurchaseExempt           |
    | PART B2-19      | PurchaseImportRawMaterial             | Purchase or Importation of Raw materials exempted from sales tax                                     | 26       | SSTP\_1      | PurchaseExemptCreditNote |
    | PART B2-20      | PurchaseImportRawMaterialManufacturer | Purchase or Importation of Raw material on behalf of Registered Manufacturer exempted from sales tax | 27       | SSTP\_2      | PurchaseExempt           |
    | PART B2-20      | PurchaseImportRawMaterialManufacturer | Purchase or Importation of Raw material on behalf of Registered Manufacturer exempted from sales tax | 28       | SSTP\_2      | PurchaseExemptCreditNote |
    | PART B2-21      | PurchaseOtherExempted                 | Value of work performed exempted from sales tax                                                      | 29       | SSTP\_3      | PurchaseExempt           |
    | PART B2-21      | PurchaseOtherExempted                 | Value of work performed exempted from sales tax                                                      | 30       | SSTP\_3      | PurchaseExemptCreditNote |
    | Not applicable  | Other                                 | Other                                                                                                | 31       | Not blank    | Not blank                |

9. Repeat the previous steps for the **ReportFieldDetailed** lookup. The following table provides an example of a configuration. However, you can use a different combination of a tax code and a name, depending on your Finance implementation.

    | Form (section)         | Lookup result (ReportFieldDetailed)      |          Description                                                          |    Line      |  Tax code             |    Name             |
    |----------------|--------------------------|--------------------------------------------------------------------|----------|--------------|-----------------|
    | PART B1-8      | TaxableGoods\_B18        | Value of Taxable Goods Sold Value of Work Performed                | 1        | SST5         | Sales           |
    | PART B1-8      | TaxableGoods\_B18        | Value of Taxable Goods Sold Value of Work Performed                | 2        | SST10        | Sales           |
    | PART B1-8      | TaxableGoods\_B18        | Value of Taxable Goods Sold Value of Work Performed                | 3        | SST5         | SalesCreditNote |
    | PART B1-8      | TaxableGoods\_B18        | Value of Taxable Goods Sold Value of Work Performed                | 4        | SST10        | SalesCreditNote |
    | PART B1-9      | OwnUsedFreeServices\_B19 | Value of Goods For Own Used or Disposed or Values of Free Services | 5        | SST5\_O      | Sales           |
    | PART B1-9      | OwnUsedFreeServices\_B19 | Value of Goods For Own Used or Disposed or Values of Free Services | 6        | SST10\_O     | Sales           |
    | PART B1-9      | OwnUsedFreeServices\_B19 | Value of Goods For Own Used or Disposed or Values of Free Services | 7        | SST5\_O      | SalesCreditNote |
    | PART B1-9      | OwnUsedFreeServices\_B19 | Value of Goods For Own Used or Disposed or Values of Free Services | 8        | SST10\_O     | SalesCreditNote |
    | PART B1-10     | TaxableServices\_B110    | Value of Taxable Service                                           | 9        | SST6         | Sales           |
    | PART B1-10     | TaxableServices\_B110    | Value of Taxable Service                                           | 10       | SSTH         | Sales           |
    | PART B1-10     | TaxableServices\_B110    | Value of Taxable Service                                           | 11       | SST6         | SalesCreditNote |
    | PART B1-10     | TaxableServices\_B110    | Value of Taxable Service                                           | 12       | SSTH         | SalesCreditNote |
    | Not applicable | Other                    | Other                                                              | 13       | Not blank    | Not blank       |

10. After the configuration is completed, in the **State** field, select **Completed**.
11. Select **Save**, and then close the **Application specific parameters** page.

> [!NOTE]
> To help prevent issues when the report is generated, create all mappings where the sales tax codes are posted. For example, if the line has omitted the operation name (**SalesCreditNote** in this configuration), and tax transactions are posted by using sales tax code **SST5**, you will encounter issues when the report is generated. We recommend that you go to **Tax** \> **Inquire** \> **Posted sales tax** to review all the posted sales tax codes and the sales tax codes that aren't included in this mapping of the configuration.

The following table provides a definition of the **Name** column to help you understand how the tax transactions are classified.

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
| PurchaseReverseChargeCreditNote | <ul><li>Credit note</li><li>Tax direction = Sales tax receivable</li><li>ReverseCharge\_W = Yes</li></ul> |
| PurchaseReverseCharge           | <ul><li>Not credit note</li><li>Tax direction = Sales tax receivable</li><li>ReverseCharge\_W = Yes</li></ul> |
| SalesReverseChargeCreditNote    | <ul><li>Credit note</li><li>Tax direction = Sales tax payable</li><li>ReverseCharge\_W = Yes</li></ul> |
| SalesReverseCharge              | <ul><li>Not credit note</li><li>Tax direction = Sales tax payable</li><li>ReverseCharge\_W = Yes</li></ul> |

## Set up General ledger parameters

To generate the SST-02 return form report in Excel, you must define an ER format on the **General ledger parameters** page.

1. Go to **Tax** \> **Setup** \> **General ledger parameters**.
2. On the **Sales tax** tab, in the **Tax options** section, in the **Electronic reporting** field, select **SST-02 Declaration Excel (MY)**. If you leave the **SST statement format mapping** field blank, the standard sales tax report will be generated in SQL Server Reporting Services (SSRS) format.
3. Select the category hierarchy. This category makes the **Commodity code** field on the **Foreign trade** tab available, so that users can select and classify goods and services. A detailed description of this classification is provided on sales and purchase transaction reports.

## Generate an SST-02 return form report

The process of preparing and submitting an SST-02 return form report for a period is based on sales tax payment transactions that were posted during the **Settle and post sales tax** job. For more information about sales tax settlement and reporting, see [Sales tax overview](../general-ledger/indirect-taxes-overview.md).

Follow these steps to generate the tax declaration report.

1. Go to **Tax** \> **Declarations** \> **Sales tax** \> **Report sales tax for settlement period** or **Settle and post sales tax**.
2. Select the settlement period.
3. Select the "from" date.
4. Select the sales tax payment version, and then select **OK** to save your changes.
5. Select the report type:

    * SST for goods and services
    * SST for goods
    * SST for services

6. Select **OK** to confirm your settings and generate the report.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]