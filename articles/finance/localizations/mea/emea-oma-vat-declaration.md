---
title: VAT declaration for Oman (OM-00003)
description: Learn how to configure and generate the value-added tax (VAT) return form for Oman, including an outline on uploading electronic reporting configurations.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/11/2024
ms.reviewer: johnmichalak
ms.search.region: Oman
ms.search.validFrom: 2021-06-10
ms.dyn365.ops.version: 10.0.22
---

# VAT declaration for Oman (OM-00003)

[!include [banner](../../includes/banner.md)]

This article explains how to set up and generate the value-added tax (VAT) return form for legal entities in Oman.

The VAT return form for Oman is the standard document that summarizes the total output VAT amount due, the total input VAT amount recoverable, and the related VAT amount liability. The form is used for all types of taxpayers and should be manually completed through the tax authority portal. The VAT return form is commonly referred to as *Filing VAT returns*.

The VAT return form in Microsoft Dynamics 365 Finance includes the following reports:

- The VAT return form, which provides a breakdown of amounts, adjustments, and VAT amount per line item in the VAT return form as is described in the legislation
- Sales transactions details
- Purchase transaction details

## Prerequisites

- The primary address of the legal entity must be in Oman.
- In the **Feature management** workspace, the following features must be enabled:

    - **VAT statement format reports**
    - **Category hierarchy for Sales and purchase tax report** – This feature is optional if you want to use commodity codes as goods and service descriptions in VAT books.

    For more information about how to enable features, see [Feature management overview](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Upload Electronic reporting configurations

The implementation of the VAT return form for Oman is based on Electronic reporting (ER) configurations. For more information about the capabilities and concepts of configurable reporting, see [Electronic reporting](../../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md).

In the **Electronic reporting** workspace, import the **VAT Return Filing Excel (OM)** ER format from the repository.

> [!NOTE]
> This format is based on the **Tax declaration model** configuration and uses the **Tax declaration model mapping** configuration. These additional configurations are automatically imported.

After you've finished downloading the ER configurations from Microsoft Dynamics Lifecycle Services (LCS) or the global repository, complete the remaining procedures in this article.

## Set up application-specific parameters

The VAT declaration form includes a set of boxes (lines) that correspond to specific parts of the VAT return process. Each box should include information about the base, adjustment, and VAT amounts. To include the requirements that are established by the form, configure each box with the information that is automatically provided from the sales tax transactions that are generated from sales, purchases, or other operations where VAT tax is posted through the sales tax code configuration.

The **Application-specific parameters** option lets you establish the criteria that define how the tax transactions will be collected and calculated in each box of the declaration form when the report is generated, depending on the configuration of the sales tax code. The following criteria are available:

- Sales tax group
- Item sales tax group
- Salex tax code

### Example

Per the legal definition, the value of box 1a, "Supplies of goods / services taxed at 5%," should be the reported total value of standard rate supplies of goods and services in the Sultanate, including deemed supplies. Report the VAT-exclusive value only.

In Finance, and depending on the tax configuration, you can implement a specific sales tax group code that represents and calculates the operations at a standard sales rate. The following procedure shows how to configure box 1a for this example.

1. In the **Electronic reporting** workspace, select **Configurations** \> **Setup** to set up the rules that will be used identify the tax transaction in the related box of the VAT return form.
2. Select the current version, and then, on the **Lookups** FastTab, select the **VATBoxesLookup** lookup. This lookup identifies the list of boxes that the tax authority requires in the VAT form.
3. On the **Conditions** FastTab, select **Add**.
4. On the new line, in the **Lookup result** field, select the related line of the VAT return form.
5. In the **Sales tax group** field, select the sales tax group that is used to calculate the related line of VAT return form. For example, select **VAT\_DOM**.
6. In the **Item sales tax group** field, select **\*Not blank\***. Box 1a will be identified by sales tax group only.
7. In the **Tax code** field, select **\*Not blank\***. Box 1a will be identified by sales tax group only.
8. In the **Transaction classifier** field, select the tax transaction classification where the sales tax group code is used.
9. Repeat steps 3 through 8 for all boxes in the VAT return form, and for the combination of sales tax codes and tax transaction types that is configured in your legal entity.
10. Select **Add**, and then follow these steps to define the last record line:

    1. In the **Lookup result** field, select **Not applicable**.
    2. In the **Sales tax group** field, select **\*Not blank\***.
    3. In the **Item sales tax group** field, select **\*Not blank\***.
    4. In the **Tax code** field, select **\*Not blank\***.
    5. In the **Transaction classifier** field, select **\*Not blank\***.

    By adding this last record, you define the following rule: If the tax code and name that are passed as an argument don't satisfy any of the previous rules, the transactions won't be included in the VAT return form. Although this rule isn't used when the report is generated, it helps prevent errors during report generation if a rule configuration is missing.
	
11. In the **State** field, select **Completed**, and then select **Save**.
12. Close the **Application specific parameters** page.

The following table represent an example that shows how you must configure these parameters to establish the configuration between the different boxes in the declaration form and sales tax code configuration that is implemented in Finance.

| Lookup result                                                      | Sales tax group | Item sales tax group | Tax code      | Transaction classifier |
|--------------------------------------------------------------------|-----------------|----------------------|---------------|------------------------|
| 1a. Supplies of goods / services taxed at 5%                       | VAT\_DOM        | \*Not blank\*        | \*Not blank\* | Sales                  |
| 1a. Supplies of goods / services taxed at 5%                       | VAT\_DOM        | \*Not blank\*        | \*Not blank\* | SalesCreditNote        |
| 1b. Supplies of goods / services taxed at 0%                       | VAT\_0%         | \*Not blank\*        | \*Not blank\* | Sales                  |
| 1b. Supplies of goods / services taxed at 0%                       | VAT\_0%         | \*Not blank\*        | \*Not blank\* | SalesCreditNote        |
| 1c. Supplies of goods / services tax exempt                        | VAT\_EXE        | \*Not blank\*        | \*Not blank\* | SalesExempt            |
| 1c. Supplies of goods / services tax exempt                        | VAT\_EXE        | \*Not blank\*        | \*Not blank\* | SalesExemptCreditNote  |
| 1d. Supplies of goods, tax levy shifted to recipient inside GCC    | VAT\_RCGS       | \*Not blank\*        | \*Not blank\* | Sales                  |
| 1d. Supplies of goods, tax levy shifted to recipient inside GCC    | VAT\_RCGS       | \*Not blank\*        | \*Not blank\* | SalesCreditNote        |
| 1e. Supplies of services, tax levy shifted to recipient inside GCC | VAT\_RCSS       | \*Not blank\*        | \*Not blank\* | Sales                  |
| 1e. Supplies of services, tax levy shifted to recipient inside GCC | VAT\_RCSS       | \*Not blank\*        | \*Not blank\* | SalesCreditNote        |
| 2a. Purchases from the GCC subject to Reverse Charge Mechanism     | VAT\_RCGP       | \*Not blank\*        | \*Not blank\* | Purchase               |
| 2a. Purchases from the GCC subject to Reverse Charge Mechanism     | VAT\_RCGP       | \*Not blank\*        | \*Not blank\* | PurchaseCreditNote     |
| 2b. Purchases from outside of GCC subject to RCM                   | VAT\_RCOP       | \*Not blank\*        | \*Not blank\* | Purchase               |
| 2b. Purchases from outside of GCC subject to RCM                   | VAT\_RCOP       | \*Not blank\*        | \*Not blank\* | PurchaseCreditNote     |
| 3a. Exports                                                        | VAT\_EXP        | \*Not blank\*        | \*Not blank\* | Sales                  |
| 3a. Exports                                                        | VAT\_EXP        | \*Not blank\*        | \*Not blank\* | SalesCreditNote        |
| 4a. Import of Goods (Postponed payment)                            | VAT\_IMPP       | \*Not blank\*        | \*Not blank\* | Purchase               |
| 4a. Import of Goods (Postponed payment)                            | VAT\_IMPP       | \*Not blank\*        | \*Not blank\* | PurchaseCreditNote     |
| 4b. Total goods imported                                           | VAT\_IMP        | \*Not blank\*        | \*Not blank\* | Purchase               |
| 4b. Total goods imported                                           | VAT\_IMP        | \*Not blank\*        | \*Not blank\* | PurchaseCreditNote     |
| 5b. Adjustment of VAT due                                          | \*Not blank\*   | \*Not blank\*        | VAT\_ADJ      | Sales                  |
| 5b. Adjustment of VAT due                                          | \*Not blank\*   | \*Not blank\*        | VAT\_ADJ      | SalesCreditNote        |
| 6a. Purchases (except import of goods)                             | VAT\_DOM        | \*Not blank\*        | \*Not blank\* | Purchase               |
| 6a. Purchases (except import of goods)                             | VAT\_DOM        | \*Not blank\*        | \*Not blank\* | PurchaseCreditNote     |
| 6b. Import of goods                                                | VAT\_IMPR       | \*Not blank\*        | \*Not blank\* | Purchase               |
| 6b. Import of goods                                                | VAT\_IMPR       | \*Not blank\*        | \*Not blank\* | PurchaseCreditNote     |
| 6c. VAT on acquisition of fixed assets                             | VAT\_FA         | \*Not blank\*        | \*Not blank\* | Purchase               |
| 6c. VAT on acquisition of fixed assets                             | VAT\_FA         | \*Not blank\*        | \*Not blank\* | PurchaseCreditNote     |
| 6d. Adjustment of input VAT credit                                 | \*Not blank\*   | \*Not blank\*        | VAT\_ADJ      | Purchase               |
| 6d. Adjustment of input VAT credit                                 | \*Not blank\*   | \*Not blank\*        | VAT\_ADJ      | PurchaseCreditNote     |
| Not applicable                                                     | \*Not blank\*   | \*Not blank\*        | \*Not blank\* | \*Not blank\*          |

To help prevent issues when the report is generated, create all mappings where the sales tax codes and sales tax group are posted. For example, if **SalesCreditNote** is omitted on the line for box 1a in this configuration, and tax transactions are posted by using the **VAT\_DOM** sales tax group, you will encounter issues when the report is generated. We recommend that you select **Tax** \> **Inquire** \> **Posted sales tax** to review all posted sales tax transactions and transactions that aren't included in this mapping of the configuration.

The following table provides the available values for the **Transaction classifier** field. This information will help you understand how the tax transactions are classified and assigned to the related sales tax code.

| Transaction classifier value    | Condition |
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

To generate the VAT return form report in Excel format, define an ER format on the **General ledger parameters** page.

1. Go to **Tax** \> **Setup** \> **General ledger parameters**.
2. On the **Sales tax** tab, in the **Tax options** section, in the **VAT statement format mapping** field, select **VAT Return Filing Excel (OM)**. If you leave the field blank, the standard sales tax report will be generated in SQL Server Reporting Services (SSRS) format.

## Generate a VAT return report

The process of preparing and submitting a VAT return report for a period is based on sales tax payment transactions that were posted during the **Settle and post sales tax** job. For more information about sales tax settlement and reporting, see [Sales tax overview](../../general-ledger/indirect-taxes-overview.md).

Follow these steps to generate the tax declaration report.

1. Go to **Tax** \> **Declarations** \> **Sales tax** \> **Report sales tax for settlement period** or **Settle and post sales tax**.
2. Select the settlement period.
3. Select the "from" date.
4. Select the sales tax payment version.
5. Select **OK**. 
6. Enter the amount of the credit from the previous period, if applicable, or leave the amount as **0** (zero).
7. In the **Generate details** field, select one or both of the following options. The VAT return form is always generated in this process.

    - Purchase transactions
    - Sales transactions

8. Select **OK** to confirm the generation of reports.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
