---
title: SST-02 declaration for Malaysia
description: This article explains how to configure and generate the SST-02 return form for Malaysia.
author: liza-golub
ms.author: egolub
ms.date: 03/02/2026
ms.topic: how-to
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
ms.search.region: Bahrain
ms.search.validFrom: 2020-06-03
ms.dyn365.ops.version: 10.0.13

---

# SST-02 declaration for Malaysia

[!include [banner](../../includes/banner.md)]

This article explains how to set up and generate the SST-02 return form for legal entities in Malaysia.

The SST-02 return form is the official electronic form that you use to declare and pay indirect taxes (Sales and Services Tax \[SST\]). The tax authorities group these indirect taxes by specific classifications, as described in the legislation. Registered manufacturers and legal persons must declare SST-02 returns every two months, according to the taxable period. SST replaces the existing Goods and Services Tax (GST), and affects all domestic and import operations.

The SST-02 return form report in Microsoft Dynamics 365 Finance includes the following reports:

* Part B1: Detailed transactions by tariff code and service type
* Part B2: Consolidated amounts in accordance with layout proposed by Malaysian government

## Prerequisites

In the **Feature management** workspace, turn on the feature that is named **Category hierarchy for Sales and purchase tax report**.

For more information about how to turn on features, see [Feature management overview](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Download electronic reporting configurations

To generate the SST-02 return form and the related reports in a Malaysian legal entity in Microsoft Dynamics 365 Finance, import the following ER configurations from Dataverse. 
Learn more about how to import ER configurations in [Import Electronic reporting (ER) configurations from Dataverse](../../localizations/global/workspace/gsw-import-er-config-dataverse.md).

1. Tax declaration model
1. Tax declaration model mapping
1. SST-02 Declaration Excel (MY)

Import the most recent versions of the configurations. The version description usually includes the number of the Knowledge Base (KB) article that explains the changes that were introduced in the configuration version.

### Set up application-specific parameters

The SST-02 return form includes a set of boxes (lines) that correspond to specific parts of the SST return form. Each box should include information about SST amounts and operations. To meet the requirements that the form establishes, you must configure each box with the correct information. This information automatically comes from the sales tax transactions that sales generate, purchases, or other operations where SST tax is posted through the sales tax code configuration.

The **Application-specific parameters** option lets you define the criteria that determine how the tax transactions are collected and calculated in each box of the declaration form when you generate the report, depending on the sales tax code configuration.

1. In the **Electronic reporting** workspace, select **Configurations** \> **Setup** to set up the rules that identify the tax transaction in the related box of the SST-022 return form.
1. Select the current version, and then, on the **Lookups** FastTab, select **ReportFieldLookup**. This lookup identifies the list of boxes that the tax authority requires in the SST-02 return form.
1. On the **Conditions** FastTab, select **Add**, and then, on the new line, in the **Lookup result** field, select the related line of the SST-02 return form.
1. In the **Tax code (Code)** field, select the sales tax code that calculates the related line of the SST-02 return form.
1. In the **Name** field, select the tax transaction classification where the sales tax code is used.
1. Repeat steps 3 through 5 for all the lines (boxes) of the SST-02 return form, and for the combination of sales tax codes and tax transaction types that you configure in your legal entity.
1. Select **Add** again, and then, in the **Lookup result** field, select **Other**.
1. In the **Tax code (Code)** and **Name** fields, select **Not blank**.

    By adding the last record, **Other**, you define the following rule: If the tax code and name that are passed as an argument don't satisfy any of the previous rules, the transactions aren't included in the SST-02 return form. Although this rule isn't used to generate the report, it helps prevent errors in the generated report because of a missing rule configuration.

    The following table provides an example of a configuration. However, you can use a different combination of a tax code and a name, depending on your Finance implementation.

    | Form (section)  | Lookup result (ReportFieldLookup)     |        Description                                                                                   |   Line   |   Tax code   |     Name                 |
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
    | PART B2-13d     | BadDebtRelief                         | Total tax value of bad debt relief                                                                   | 13       | SSTBD        | SalesCreditNote          |
    | PART B2-18a     | Exempted\_Export                      | Exempted Export, Special Area and Designated Area                                                    | 14       | SSTE         | Not blank                |
    | PART B2-18a     | Exempted\_Export                      | Exempted Export, Special Area and Designated Area                                                    | 15       | SSTE         | SalesExemptCreditNote    |
    | PART B2-18b1    | Exempted\_ClassOfPerson               | Schedule A (Class of Person)                                                                         | 16       | SSTE\_A      | SalesExempt              |
    | PART B2-18b1    | Exempted\_ClassOfPerson               | Schedule A (Class of Person)                                                                         | 17       | SSTE\_A      | SalesExemptCreditNote    |
    | PART B2-18b2    | Exempted\_Manufacturer                | Schedule B (Manufacturer of specific nontaxable goods)                                               | 18       | SSTE\_B      | SalesExempt              |
    | PART B2-18b2    | Exempted\_Manufacturer                | Schedule B (Manufacturer of specific nontaxable goods)                                               | 19       | SSTE\_B      | SalesExemptCreditNote    |
    | PART B2-18b3i   | Exempted\_CRawMaterials               | Purchase or Importation of Raw Material Exempted From Sales Tax                                      | 20       | SSTE\_C1     | SalesExempt              |
    | PART B2-18b3i   | Exempted\_CRawMaterials               | Purchase or Importation of Raw Material Exempted From Sales Tax                                      | 21       | SSTE\_C1     | SalesExemptCreditNote    |
    | PART B2-18b3ii  | Exempted\_CManufacturer               | Purchase or Importation of Raw Material on behalf of Registered Manufacturer Exempted From Sales Tax | 22       | SSTE\_C2     | SalesExempt              |
    | PART B2-18b3ii  | Exempted\_CManufacturer               | Purchase or Importation of Raw Material on behalf of Registered Manufacturer Exempted From Sales Tax | 23       | SSTE\_C2     | SalesExemptCreditNote    |
    | PART B2-18b3iii | Exempted\_CValueofWork                | Value of Work Performed Exempted from Sales Tax                                                      | 24       | SSTE\_C3     | SalesExempt              |
    | PART B2-18b3iii | Exempted\_CValueofWork                | Value of Work Performed Exempted from Sales Tax                                                      | 25       | SSTE\_C3     | SalesExemptCreditNote    |
    | PART B2-18c1    | Exempted\_B2BExemption                | B2B exemption (registered to registered person)                                                      | 26       | SSTE\_C31    | SalesExempt              |
    | PART B2-18c1    | Exempted\_B2BExemption                | B2B exemption (registered to registered person)                                                      | 27       | SSTE\_C31    | SalesExemptCreditNote    |
    | PART B2-18c2    | Exempted\_GroupRelief                 | Group relief                                                                                         | 28       | SSTE\_C32    | SalesExempt              |
    | PART B2-18c2    | Exempted\_GroupRelief                 | Group relief                                                                                         | 29       | SSTE\_C32    | SalesExemptCreditNote    |
    | PART B2-18c3    | Exempted\_OtherExemptions             | Other exemptions                                                                                     | 30       | SSTE\_C33    | SalesExempt              |
    | PART B2-18c3    | Exempted\_OtherExemptions             | Other exemptions                                                                                     | 31       | SSTE\_C33    | SalesExempt              |
    | PART B2-18c     | Exempted\_CValueofWork                | (Deprecated) Value of Work Performed Exempted from Sales Tax                                         | -        | -            | -                        |
    | PART B2-18d     | Exempted\_CValueofWork                | Nontaxable services                                                                                  | 32       | SSTE\_D      | SalesExempt              |
    | PART B2-18d     | Exempted\_CValueofWork                | Nontaxable services                                                                                  | 32       | SSTE\_D      | SalesExemptCreditNote    |
    | PART B2-18e     | Exempted\_CValueofWork                | Sales exempted under Sales Tax Act 2018 s.35(3) and/or s.61A                                         | 33       | SSTE\_E      | SalesExempt              |
    | PART B2-18e     | Exempted\_CValueofWork                | Sales exempted under Sales Tax Act 2018 s.35(3) and/or s.61A                                         | 33       | SSTE\_E      | SalesExemptCreditNote    |
    | PART B2-19      | PurchaseImportRawMaterial             | Purchase or Importation of Raw materials exempted from sales tax                                     | 34       | SSTP\_1      | PurchaseExempt           |
    | PART B2-19      | PurchaseImportRawMaterial             | Purchase or Importation of Raw materials exempted from sales tax                                     | 35       | SSTP\_1      | PurchaseExemptCreditNote |
    | PART B2-20      | PurchaseImportRawMaterialManufacturer | Purchase or Importation of Raw material on behalf of Registered Manufacturer exempted from sales tax | 36       | SSTP\_2      | PurchaseExempt           |
    | PART B2-20      | PurchaseImportRawMaterialManufacturer | Purchase or Importation of Raw material on behalf of Registered Manufacturer exempted from sales tax | 37       | SSTP\_2      | PurchaseExemptCreditNote |
    | PART B2-21      | PurchaseOtherExempted                 | Value of work performed exempted from sales tax                                                      | 38       | SSTP\_3      | PurchaseExempt           |
    | PART B2-21      | PurchaseOtherExempted                 | Value of work performed exempted from sales tax                                                      | 39       | SSTP\_3      | PurchaseExemptCreditNote |
    | Not applicable  | Other                                 | Other                                                                                                | 40       | Not blank    | Not blank                |

1. Repeat the previous steps for the **ReportFieldDetailed** lookup. The following table provides an example of a configuration. However, you can use a different combination of a tax code and a name, depending on your Finance implementation.

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

1. After you complete the configuration, select **Completed** in the **State** field.
1. Select **Save**, and then close the **Application specific parameters** page.

> [!NOTE]
> To help prevent problems when the report is generated, create all mappings where the sales tax codes are posted. For example, if the line omits the operation name (**SalesCreditNote** in this configuration), and tax transactions use sales tax code **SST5** to post, you encounter problems when the report is generated. Go to **Tax** \> **Inquire** \> **Posted sales tax** to review all the posted sales tax codes and the sales tax codes that aren't included in this mapping of the configuration.

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
1. On the **Sales tax** tab, in the **Tax options** section, in the **Electronic reporting** field, select **SST-02 Declaration Excel (MY)**. If you leave the **SST statement format mapping** field blank, the standard sales tax report is generated in SQL Server Reporting Services (SSRS) format.
1. Select the category hierarchy. This category makes the **Commodity code** field on the **Foreign trade** tab available, so that users can select and classify goods and services. A detailed description of this classification is provided on sales and purchase transaction reports.

## Generate an SST-02 return form report

The process of preparing and submitting an SST-02 return form report for a period is based on sales tax payment transactions that the **Settle and post sales tax** job posts. For more information about sales tax settlement and reporting, see [Sales tax overview](../../general-ledger/indirect-taxes-overview.md).

Follow these steps to generate the tax declaration report.

1. Go to **Tax** \> **Declarations** \> **Sales tax** \> **Report sales tax for settlement period** or **Settle and post sales tax**.
1. Select the settlement period.
1. Select the start date.
1. Select the sales tax payment version, and then select **OK** to save your changes.
1. Select the report type:

    * SST for goods and services
    * SST for goods
    * SST for services

1. Select **OK** to confirm your settings and generate the report.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
