---
title: VAT declaration for Indonesia (ID-00004)
description: Learn how to configure and generate the SPT Masa PPN 1111 (Pajak Pertambahan Nilai) form for Indonesia, including prerequisites.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/27/2024
ms.reviewer: johnmichalak
ms.search.region: Indonesia
ms.search.validFrom: 2021-09-01
ms.dyn365.ops.version: 10.0.20
---

# VAT declaration for Indonesia (ID-00004)

This article explains how to set up and generate the value-added tax (VAT) return form for legal entities in Indonesia. This form is often referred as *SPT Masa PPN 1111 (Pajak Pertambahan Nilai)*. Corporate taxpayers should issue it to report the calculated amount of tax so that they can report VAT (PPN) and Luxury Goods Sales Tax (PPNnBM) that are owed. In addition to being used to report payments or pay taxes, the SPT Masa PPN 1111 form is used to report property, liabilities, and tax deposits from cutters or collectors.

The **SPT Masa PPN 1111 (Pajak Pertambahan Nilai)** page in Microsoft Dynamics 365 Finance includes the following reports:

- **Master SPT Masa PPN 1111 form** – This report provides a breakdown of amounts, adjustments, and VAT amount per line item in the VAT return form, as described in the legislation.
- **Form 1111 AB**
- **A1 (Sales Export)**
- **A2 (List of Output Tax on Domestic Sales)**
- **B1 (Input Tax recoverable on Import)**
- **B2 (Input Tax recoverable for Domestic)**
- **B3 (Input Tax non recoverable)**

## Prerequisites

- The primary address of the legal entity must be in Indonesia.
- In the **Feature management** workspace, enable the following features:

    - VAT statement format reports
    - Enable credit invoicing for vendor invoices

   For more information about how to enable features, see [Feature management overview](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Upload Electronic reporting configurations

Implementation of the VAT return form for Indonesia is based on Electronic reporting (ER) configurations. For more information about the capabilities and concepts of configurable reporting, see [Electronic reporting](../../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md).

In the **Electronic reporting** workspace, import the **VAT Declaration Excel (ID)** ER format from the repository. This format is based on the **Tax declaration model** configuration and uses the **Tax declaration model mapping** configuration. These additional configurations will be automatically imported.

After you've finished downloading the ER configurations from Microsoft Dynamics Lifecycle Services (LCS) or the Global repository, complete the remaining steps in this article.

## Set up application-specific parameters

The **SPT Masa PPN 1111** page includes a set of boxes that correspond to specific parts of the PPN return process. Each box includes information about the base, adjustment, PPN (VAT), and PPNnBM (luxury tax) amounts. To include the requirements that are established by the form, configure each box with the information that is automatically provided from the sales tax transactions that are generated from sales, purchases, or other operations where PPN or PPNnBM tax is posted through the sales tax code configuration.

The application-specific parameters option lets you establish the criteria that define how the tax transactions are collected and calculated in each box of the declaration form when the report is generated, based on the configuration of the sales tax code. Here are some of the available criteria:

- Sales tax group
- Item sales tax group
- Sales tax code
- Transaction classifier

### Example

Per the legal definition, **BoxA1 - Export of Tangible BKP / Intangible BKP / JKP** should include the total amount of export sales invoices, including credit notes.

Depending on the tax configuration in Finance, you can implement a specific sales tax group, item tax group, or sales tax code that represents and calculates the operations that are classified as export sales invoices. For this example, configure **BoxA1** as shown here.

1. In the **Electronic reporting** workspace, select **Configurations** \> **Setup** to set up the rules to identify the tax transaction in the related box of the SPT Masa PPN 1111 form.
2. Select the current version, and then, on the **Lookups** FastTab, select the lookup name **ReportFieldLookup**. This lookup identifies the list of boxes that the tax authority requires in the SPT Masa PPN 1111 form.
3. On the **Conditions** FastTab, select **Add**.
4. On the new line, in the **Lookup result** field, select the related line of the SPT Masa PPN 1111 form.
5. In the **Sales tax group** field, select the sales tax group that is used to calculate the related line of the SPT Masa PPN 1111 form. For example, select **PPN\_EXP**.
6. In the **Item sales tax group** field, select **\*Not blank\***, because box 1a will be identified only by sales tax group.
7. In the **Tax code** field, select **\*Not blank\***, because box 1a will be identified only by sales tax group.
8. In the **Transaction classifier** field, select the tax transaction classification where the sales tax group code is used.
9. Repeat steps 3 through 8 for all SPT Masa PPN 1111 form boxes and the combination of sales tax code and tax transaction types that is configured in your legal entity.
10. Select **Add**, and then follow these steps to add the final record line:

    1. In the **Lookup result** field, select **NA - Not applicable**.
    2. In the **Sales tax group** field, select **\*Not blank\***.
    3. In the **Item sales tax group** field, select **\*Not blank\***.
    4. In the **Tax code** field, select **\*Not blank\***.
    5. In the **Transaction classifier** field, select **\*Not blank\***.

    By adding this last record (**NA**), you define the following rule: If the tax code and name that are passed as an argument don't satisfy any of the previous rules, the transactions won't be included in the VAT return form. Although this rule isn't used when the report is generated, it helps prevent errors during report generation if there is a missing rule configuration.

In addition to the previous configuration, you must follow these steps to classify the tax type that the tax authority requires. You must be able to indicate whether the tax is PPN (VAT) or PPNnBM (luxury tax).

1. In the **Electronic reporting** workspace, select **Configurations** \> **Setup** to set up rules to identify the tax transaction in the related box of the SPT Masa PPN 1111 form.
2. Select the current version, and then, on the **Lookups** FastTab, select the **TaxTypeLookup** lookup name. This lookup identifies the tax type that the tax authority requires in the SPT Masa PPN 1111 form.
3. On the **Conditions** FastTab, select **Add**.
4. On the new line, in the **Lookup result** field, select the type of tax. For example, select **PPN**.
5. In the **Tax code** field, select the sales tax code that represents the tax type that you selected in the **Lookup result** field. For example, select **PPN10%**.
6. Repeat steps 3 through 5 for all sales tax codes that are configured in your legal entity.
7. Select **Add** again, and then follow these steps to add the final record line:

    1. In the **Lookup result** field, select **NA - Not applicable**.
    2. In the **Tax code** field, select **\*Not blank\***.

8. In the **State** field, select **Completed**.
9. Select **Save**.
10. Close the **Application specific parameters** page.

The following table represents an example that shows how to configure the parameters to establish the configuration between the different boxes in the declaration form and sales tax configuration that is implemented in Finance.

| Lookup result | Label                                                        | Line | Sales tax group | Item sales tax group | Tax code      | Transaction classifier |
|---------------|--------------------------------------------------------------|------|-----------------|----------------------|---------------|------------------------|
| BoxA1         | Export sales of tangible BKP, intangible BKP, and JKP        | 1    | PPN\_EXP        | \*Not blank\*        | \*Not blank\* | Sales                  |
| BoxA1         | Export sales of tangible BKP, intangible BKP, and JKP        | 2    | PPN\_EXP        | \*Not blank\*        | \*Not blank\* | SalesCreditNote        |
| BoxA2         | Output taxes on domestic sales with tax invoices             | 3    | PPN\_DOM        | \*Not blank\*        | \*Not blank\* | Sales                  |
| BoxA2         | Output taxes on domestic sales with tax invoices             | 4    | PPN\_DOM        | \*Not blank\*        | \*Not blank\* | SalesCreditNote        |
| BoxA2         | Output taxes on domestic sales with tax invoices             | 5    | PPN\_EXE        | \*Not blank\*        | \*Not blank\* | SaleExempt             |
| BoxA2         | Output taxes on domestic sales with tax invoices             | 6    | PPN\_EXE        | \*Not blank\*        | \*Not blank\* | SalesExemptCreditNote  |
| BoxB1         | Input taxes that can be on the import of BKP and utilization | 7    | PPN\_IMP        | \*Not blank\*        | \*Not blank\* | Purchase               |
| BoxB1         | Input taxes that can be on the import of BKP and utilization | 8    | PPN\_IMP        | \*Not blank\*        | \*Not blank\* | PurchaseCreditNote     |
| BoxB2         | Input taxes that can be credited for the acquisition of BKP  | 9    | \*Not blank\*   | \*Not blank\*        | PPN10%        | Purchase               |
| BoxB2         | Input taxes that can be credited for the acquisition of BKP  | 10   | \*Not blank\*   | \*Not blank\*        | PPN10%        | PurchaseCreditNote     |
| BoxB3         | Input taxes that can't be credited or that get facilities    | 11   | \*Not blank\*   | \*Not blank\*        | PPN\_NO       | Purchase               |
| BoxB3         | Input taxes that can't be credited or that get facilities    | 12   | \*Not blank\*   | \*Not blank\*        | PPN\_NO       | PurchaseCreditNote     |
| BoxAdj        | Adjustments                                                  | 13   | \*Blank\*       | \*Blank\*            | PPN\_ADJ      | Sales                  |
| BoxAdj        | Adjustments                                                  | 14   | \*Blank\*       | \*Blank\*            | PPN\_ADJ      | SalesCreditNote        |
| BoxAdj        | Adjustments                                                  | 15   | \*Blank\*       | \*Blank\*            | PPN\_ADJ      | Purchase               |
| BoxAdj        | Adjustments                                                  | 16   | \*Blank\*       | \*Blank\*            | PPN\_ADJ      | PurchaseCreditNote     |
| NA            | Not applicable                                               | 17   | \*Not blank\*   | \*Blank\*            | \*Not blank\* |\*Not blank\*          |

To help prevent issues when the report is generated, create all mappings where the sales tax codes and sales tax group are posted. For example, if **SalesCreditNote** is removed from the line for **BoxA2** in this configuration, and tax transactions are posted by using the **PPN\_DOM** sales tax group, you will encounter issues when the report is generated. Select **Tax** \> **Inquire** \> **Posted sales tax** to review all posted sales tax transactions and transactions that aren't included in this mapping of the configuration.

The following table shows the available values for the **Transaction classifier** field. This information explains how the tax transactions are classified and assigned to the related sales tax code.

| Classifier                      | Condition |
|---------------------------------|-----------|
| PurchaseCreditNote              | <p>Credit note</p><p>Tax direction = Sales tax receivable</p> |
| Purchase                        | <p>Not credit note</p><p>Tax direction = Sales tax receivable</p> |
| SalesCreditNote                 | <p>Credit note</p><p>Tax direction = Sales tax payable</p> |
| Sales                           | <p>Not credit note</p><p>Tax direction = Sales tax payable</p> |
| PurchaseExemptCreditNote        | <p>Credit note</p><p>Tax direction = Tax-free purchase</p> |
| PurchaseExempt                  | <p>Not credit note</p><p>Tax direction = Tax-free purchase</p> |
| SalesExemptCreditNote           | <p>Credit note</p><p>Tax direction = Tax-free sales</p> |
| SaleExempt                      | <p>Not credit note</p><p>Tax direction = Tax-free sales</p> |
| UseTaxCreditNote                | <p>Credit note</p><p>Tax direction = Use tax</p> |
| UseTax                          | <p>Not credit note</p><p>Tax direction = Use tax</p> |
| PurchaseReverseChargeCreditNote | <p>Credit note</p><p>Tax direction = Sales tax receivable</p><p>ReverseCharge\_W = Yes</p> |
| PurchaseReverseCharge           | <p>Not credit note</p><p>Tax direction = Sales tax receivable</p><p>ReverseCharge\_W = Yes</p> |
| SalesReverseChargeCreditNote    | <p>Credit note</p><p>Tax direction = Sales tax payable</p><p>ReverseCharge\_W = Yes</p> |
| SalesReverseCharge              | <p>Not credit note</p><p>Tax direction = Sales tax payable</p><p>ReverseCharge\_W = Yes</p> |

## Set up General ledger parameters

To generate the SPT Masa PPN 1111 report in Excel format, define an ER format on the **General ledger parameters** page.

1. Go to **Tax** \> **Setup** \> **General ledger parameters**.
2. On the **Sales tax** tab, in the **Tax options** section, in the **VAT statement format mapping** field, select **VAT Declaration Excel (ID)**. If you leave the field blank, the standard sales tax report will be generated in SQL Server Reporting Services (SSRS) format.

## Generate an SPT Masa PPN 1111 report

The process of preparing and submitting an SPT Masa PPN 1111 report for a period is based on sales tax payment transactions that were posted during the **Settle and post sales tax** job. For more information about sales tax settlement and reporting, see [Sales tax overview](../../general-ledger/indirect-taxes-overview.md).

Follow these steps to generate the tax declaration report.

1. Go to **Tax** \> **Declarations** \> **Sales tax** \> **Report sales tax for settlement period** or **Settle and post sales tax**.
2. Select the settlement period.
3. Select the from date.
4. Select the sales tax payment version.
5. Select **OK**. 
6. In the next dialog box, enter the following information:

    - The business activity code.
    - The amount of compensation for excess VAT that was caused by correction of the tax period's VAT SPT, if applicable.
    - The amount of VAT excess compensation for the previous tax period, if applicable.
    - The date of compensation for excess VAT, if applicable.
    - The amount of VAT that was paid in advance during the same tax period.
    - The version number. Valid version numbers are from 0 through 7.

7. Select **OK** to confirm your settings and generate the report.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
