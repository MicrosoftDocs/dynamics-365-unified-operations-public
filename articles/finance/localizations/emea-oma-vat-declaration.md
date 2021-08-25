---
# required metadata

title: VAT declaration for Oman
description: This topic explains how to configure and generate the VAT return form for Oman.
author: sndray
ms.date: 06/10/2021
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
ms.search.region: Oman
# ms.search.industry: 
ms.author: sndray
ms.search.validFrom: 2021-06-10
ms.dyn365.ops.version: 10.0.22

---

# VAT declaration for Oman (OM-00003)

[!include [banner](../includes/banner.md)]

## Overview

This topic explains how to set up and generate the VAT return form for legal entities in Oman.

The VAT return form for Oman is the standard document that summarizes the total output VAT tax amount due, the total input VAT tax amount recoverable, and the related VAT tax amount  liability. The form is used for all types of taxpayers and should be completed manually through the tax authority portal. The VAT return form is commonly referred to as *Filing VAT returns*.

The VAT return form in Dynamics 365 Finance includes the following reports:

 - VAT return form, which provides a breakdown of amounts, adjustments, and VAT amount per line item in the VAT return form as is described in the legislation.
 - Sales transactions details.
 - Purchase transaction details.
  
## Prerequisites

- The primary address of the legal entity must be in Oman.

In the **Feature management** workspace, enable the following features:
- VAT statement format reports.
- Category hierarchy for Sales and purchase tax report. This is optional if you want to use commodity code as goods and service description in VAT books.

For more information about how to enable features, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Upload Electronic reporting configurations

The implementation of the VAT return form for Oman is based on Electronic reporting (ER) configurations. For more information about the capabilities and concepts of configurable reporting, see [Electronic reporting](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md).

In the **Electronic reporting** workspace, import the following Electronic Reporting format from the repository:

  -  VAT Return Filing Excel (OM)
 
> [!NOTE]
> The formats above are based on **Tax declaration model** and use **Tax declaration model mapping**. These additional configurations will be automatically imported.

After you've finished downloading the ER configurations from Lifecycle Services (LCS) or the global repository, complete the following steps.

 
### Set up application-specific parameters

The VAT declaration form includes a set of boxes (lines) that correspond to specific parts of the VAT return process. Each box should include information about the base, adjustment, and VAT amounts. To include the requirements established by the form, you must configure each box with the information that is automatically provided from the sales tax transactions generated from sales, purchases, or other operations where VAT tax is posted through the sales tax code configuration.

The Application-specific parameters option let the users to establish the criteria of how the tax transactions will be collected and calculated in each box (line) of the declaration form when the report is generated depending on the configuration of sales tax code. The available criteria are the following:

- Sales tax group
- Item sales tax group
- Salex tax code

#### Example

**Box: 1a - Supplies of goods / services taxed at 5%** . As per legal definition, in this box should be reported the total value of standard rated supplies of goods and services in the Sultanate, including deemed supplies. Report the VAT-exclusive value only.

In Finance and depending on the tax configuration you can have a specific sales tax group code implemented that represents and calculates the operations at a standard sales rate. In this example, it is necessary to configure **Box 1a** as follows:

1. In the Electronic reporting workspace, select **Configurations** > **Setup** to set up the rules to identify the tax transaction into the related box of the VAT return form.
2. Select the current version. On the **Lookups** FastTab, select the lookup name **VATBoxesLookup**. This lookup identifies the list of boxes (lines) in the VAT form required by tax authority. 
3. On the **Conditions** FastTab, select **Add**, and in the new line in the **Lookup result** column, select the related line of VAT return form.
4. In the **Sales tax group** column, select the sales tax group that is used to calculate the related line of VAT return form. Example: VAT_DOM
5. In the **Item sales tax group** column, select **Not blank** because the box 1a is going to be identified by Sales tax group only.
6. In the **Tax code** column, select **Not blank** because the box 1a is going to be identified by Sales tax group only.
7. In the **Transaction classifier** column, select the tax transaction classification where the sales tax group code is used.
8. Repeat steps 3-5 for all VAT return form boxes (lines) and the combination of sales tax code and tax transaction types configured in your legal entity.
9. Select **Add** again, and then follow these steps to include the final record line:
   a. In the **Lookup result** column, select **Not applicable**.
   b. In the **Sales tax group** column, select **Not blank**.
   c. In the **Item sales tax group** column, select **Not blank**.
   d. In the **Tax code** column, select **Not blank**.
   c. In the **Transaction classifier** column, select **Not blank**.

By adding this last record (NA), you define the following rule: When the tax code and name that is passed as an argument doesn't satisfy any of the previous rules, the transactions will not be included in the VAT return form. Although this rule is not used when generating the report, the rule does help to avoid errors in report generation when there is a missing rule configuration. 
	
8. In the **State** field, select **Completed**, and then select **Save**. 
9. Close the **Application specific parameters** page.

The following table represent an example of how the user needs to configure these parameters to establish the configuration between the different boxes in the declaration form and sales tax code configuration implemented in Finance.

|                                    Lookup   result                                   | Sales tax group | Item sales tax   group |   Tax code  |  Transacction   classifier |
|:------------------------------------------------------------------------------------:|:---------------:|:----------------------:|:-----------:|:--------------------------:|
| 1a. Supplies of goods / services taxed at 5%                                         | VAT_DOM         | *Not blank*            | *Not blank* | Sales                      |
| 1a. Supplies of goods / services taxed at 5%                                         | VAT_DOM         | *Not blank*            | *Not blank* | Sales credit note          |
| 1b. Supplies of goods / services taxed at 0%                                         | VAT_0%          | *Not blank*            | *Not blank* | Sales                      |
| 1b. Supplies of goods / services taxed at 0%                                         | VAT_0%          | *Not blank*            | *Not blank* | Sales credit note          |
| 1c. Supplies of goods / services tax exempt                                          | VAT_EXE         | *Not blank*            | *Not blank* | Sales Exempt               |
| 1c. Supplies of goods / services tax exempt                                          | VAT_EXE         | *Not blank*            | *Not blank* | Sales Exempt Credit note   |
| 1d. Supplies of goods, tax levy shifted to recipient inside GCC (reverse charge)     | VAT_RCGS        | *Not blank*            | *Not blank* | Sales                      |
| 1d. Supplies of goods, tax levy shifted to recipient inside GCC (reverse charge)     | VAT_RCGS        | *Not blank*            | *Not blank* | Sales credit note          |
| 1e. Supplies of services, tax levy shifted to recipient inside GCC ( reverse charge) | VAT_RCSS        | *Not blank*            | *Not blank* | Sales                      |
| 1e. Supplies of services, tax levy shifted to recipient inside GCC ( reverse charge) | VAT_RCSS        | *Not blank*            | *Not blank* | Sales credit note          |
| 2a. Purchases from the GCC subject to Reverse Charge Mechanism                       | VAT_RCGP        | *Not blank*            | *Not blank* | Purchase                   |
| 2a. Purchases from the GCC subject to Reverse Charge Mechanism                       | VAT_RCGP        | *Not blank*            | *Not blank* | Purchase credit note       |
| 2b. Purchases from outside of GCC subject to Reverse Charge Mechanism                | VAT_RCOP        | *Not blank*            | *Not blank* | Purchase                   |
| 2b. Purchases from outside of GCC subject to Reverse Charge Mechanism                | VAT_RCOP        | *Not blank*            | *Not blank* | Purchase credit note       |
| 3a. Exports                                                                          | VAT_EXP         | *Not blank*            | *Not blank* | Sales                      |
| 3a. Exports                                                                          | VAT_EXP         | *Not blank*            | *Not blank* | Sales credit note          |
| 4a. Import of Goods (Postponed payment)                                              | VAT_IMPP        | *Not blank*            | *Not blank* | Purchase                   |
| 4a. Import of Goods (Postponed payment)                                              | VAT_IMPP        | *Not blank*            | *Not blank* | Purchase credit note       |
| 4b. Total goods imported                                                             | VAT_IMP         | *Not blank*            | *Not blank* | Purchase                   |
| 4b. Total goods imported                                                             | VAT_IMP         | *Not blank*            | *Not blank* | Purchase credit note       |
| 5b. Adjustment of VAT due                                                            | *Not blank*     | *Not blank*            | VATADJ      | Sales                      |
| 5b. Adjustment of VAT due                                                            | *Not blank*     | *Not blank*            | VATADJ      | Sales credit note          |
| 6a. Purchases (except import of goods)                                               | VAT_DOM         | *Not blank*            | *Not blank* | Purchase                   |
| 6a. Purchases (except import of goods)                                               | VAT_DOM         | *Not blank*            | *Not blank* | Purchase credit note       |
| 6b. Import of goods                                                                  | VAT_IMPR        | *Not blank*            | *Not blank* | Purchase                   |
| 6b. Import of goods                                                                  | VAT_IMPR        | *Not blank*            | *Not blank* | Purchase credit note       |
| 6c. VAT on acquisition of fixed assets                                               | VAT_FA          | *Not blank*            | *Not blank* | Purchase                   |
| 6c. VAT on acquisition of fixed assets                                               | VAT_FA          | *Not blank*            | *Not blank* | Purchase credit note       |
| 6d. Adjustment of input VAT credit                                                   | *Not blank*     | *Not blank*            | VATADJ      | Purchase                   |
| 6d. Adjustment of input VAT credit                                                   | *Not blank*     | *Not blank*            | VATADJ      | Purchase credit note       |
| Not applicable                                                                       | *Not blank*     | *Not blank*            | *Not blank* | *Not blank*                |

To avoid issues when the report is generated, create all mappings where the sales tax codes and sales tax group are posted. For example, if the line of **box 1a**  has SalesCreditNote is omitted in this configuration, and tax transactions are posted by using sales tax group VAT_DOM, you will encounter issues when the report is generated. We recommend that you use the **Tax > Inquire > Posted sales tax** menu to review all posted sales tax transactions and those that are not included in this mapping of the configuration.

The following table provides the available values in the **Transaction classifier** column. This information will help you understand how the tax transactions are classified and assigned to the related sales tax code.

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
To generate the VAT return form report in Microsoft Excel format, you must define an ER format on the **General ledger parameters** page.

1. Go to **Tax** > **Setup** > **General ledger parameters**.
2. On the **Sales tax** tab, in the **Tax options** section, in the **VAT statement format mapping** field, select **VAT Return Filing Excel (OM)**. If you leave the field blank, the standard sales tax report will be generated in SSRS format.

## Generate a VAT return report
The process of preparing and submitting a VAT return report for a period is based on sales tax payment transactions that were posted during the Settle and post sales tax job. For more information about sales tax settlement and reporting, see [Sales tax overview](../general-ledger/indirect-taxes-overview.md).

Complete the following steps to generate the tax declaration report.

1. Go to **Tax > Declarations** > **Sales tax** > **Report sales tax for settlement period** or **Settle and post sales tax**.
2. Select the **Settlement period**.
3. Select the from date.
4. Select the sales tax payment version.
5. Select **OK** to confirm the above steps. 
6. Enter the amount of credit from the previous period, if applicable, or leave the amount as zero.
7. In the **Generate details** field, select one or more of the following available options. The VAT return form is always generated in this process.
   - **Purchase transactions**
   - **Sales transactions**
8. Select **OK** to confirm the generation of reports.
  
[!INCLUDE[footer-include](../../includes/footer-banner.md)]
