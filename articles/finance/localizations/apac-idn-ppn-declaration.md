---
# required metadata

title: VAT declaration for Indonesia (ID-00004)
description: This topic explains how to configure and generate the SPT Masa PPN 1111 (Pajak Pertambahan Nilai) form for Indonesia.
author: sndray
ms.date: 10/12/2021
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
ms.search.region: Indonesia
# ms.search.industry: 
ms.author: sndray
ms.search.validFrom: 2021-09-01
ms.dyn365.ops.version: 10.0.20

---

# VAT declaration for Indonesia (ID-00004)

This topic explains how to set up and generate the VAT return form for legal entities in Indonesia.
The VAT return form is commonly referred as **SPT Masa PPN 1111( Pajak Pertambahan Nilai)** and should be issued by corporate taxpayers to report the calculated amount of tax both to report Value add tax (PPN) and Luxury Goods Sales Tax (PPnBM) that is owed. In addition to reporting payments or paying taxes, the SPT Masa PPN 1111 form is used to report property, liabilities, and tax deposits from cutters or collectors.

The **SPT Masa PPN 1111( Pajak Pertambahan Nilai)** page in Dynamics 365 Finance includes the following reports:

- Master SPT Masa PPN 1111 form. This reports provides a breakdown of amounts, adjustments, and VAT amount per line item in the VAT Return form as is described in the legislation.
- Form 1111 AB.
- A1 (Sales Export)
- A2 (List of Output Tax on Domestic Sales)
- B1 (Input Tax recoverable on Import)
- B2 (Input Tax recoverable for Domestic)
- B3 (Input Tax non recoverable) 
	
## Prerequisites

- The primary address of the legal entity must be in Indonesia.
- In the **Feature management** workspace, enable the following features:
	- **VAT statement format reports**
	- **Enable credit invoicing for vendor invoices**

For more information about how to enable features, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Upload Electronic reporting configurations

Implementing the VAT return form for Indonesia is based on Electronic reporting (ER) configurations. For more information about the capabilities and concepts of configurable reporting, see [Electronic reporting](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md).

In the **Electronic reporting** workspace, import the **VAT Declaration Excel (ID)** Electronic Reporting format from the repository.
This format is based on **Tax declaration model** and uses the **Tax declaration model mapping**. These additional configurations will be automatically imported.

After you finish downloading the ER configurations from Lifecycle Services (LCS) or the global repository, complete the remaining steps in this topic.

 
## Set up application-specific parameters

The **SPT Masa PPN 1111** form includes a set of boxes that correspond to specific parts of the PPN return process. Each box includes information about the base, adjustment, PPN, and PPNnBM amounts. To include the requirements established by the form, configure each box with the information that's automatically provided from the sales tax transactions that are generated from sales, purchases, or other operations where PPN or PPNnBM tax is posted through the sales tax code configuration.

The application-specific parameters option lets you establish the criteria of how the tax transactions are collected and calculated in each box of the declaration form when the report is generated depending on the configuration of the sales tax code. The available criteria include

- Sales tax group
- Item sales tax group
- Sales tax code
- Transaction classifier

### Example

**BoxA1 - Export of Tangible BKP / Intangible BKP / JKP** . As per legal the definition, this box should include the total amount of export sales invoices including credit notes.

Depending on the tax configuration in Finance, you can have a specific sales tax group or item tax group or sales tax code implemented that represents and calculates the operations classified as export sales invoices. In this example, it is necessary to configure **BoxA1** as follows:

1. In the **Electronic reporting** workspace, select **Configurations** > **Setup** to set up the rules to identify the tax transaction into the related box of the SPT Masa PPN 1111 form.
2. Select the current version, and on the **Lookups** FastTab, select the lookup name, **ReportFieldLookup**. This lookup identifies the list of boxes in the SPT Masa PPN 1111 that are required by the tax authority. 
3. On the **Conditions** FastTab, select **Add**, and in the new line in the **Lookup result** column, select the related line of SPT Masa PPN 1111 form.
4. In the **Sales tax group** column, select the sales tax group that's used to calculate the related line of SPT Masa PPN 1111 form. For example, PPN_EXP.
5. In the **Item sales tax group** column, select **Not blank** because box 1a will be identified only by sales tax group.
6. In the **Tax code** column, select **Not blank** because the box 1a will be identified only by sales tax group.
7. In the **Transaction classifier** column, select the tax transaction classification where the sales tax group code is used.
8. Repeat steps 3-5 for all SPT Masa PPN 1111 form boxes and the combination of sales tax code and tax transaction types configured in your legal entity.
9. Select **Add** again, and then follow these steps to include the final record line:
   1. In the **Lookup result** column, select **NA - Not applicable**.
   2. In the **Sales tax group** column, select **Not blank**.
   3. In the **Item sales tax group** column, select **Not blank**.
   4. In the **Tax code** column, select **Not blank**.
   5. In the **Transaction classifier** column, select **Not blank**.

By adding this last record **(NA)**, you define the following rule: When the tax code and name that is passed as an argument doesn't satisfy any of the previous rules, the transactions will not be included in the VAT return form. Although this rule isn't used when generating the report, the rule does help to avoid errors in report generation when there is a missing rule configuration. 

In addition to this configuration, complete the steps below to classify the tax type required by the tax authority. You must be able to indicate if the tax is PPN or PPNnBM (luxury tax).

1. In the **Electronic reporting** workspace, select **Configurations** > **Setup** to set up the rules to identify the tax transaction into the related box of the SPT Masa PPN 1111 form.
2. Select the current version and on the **Lookups** FastTab, select the lookup name **TaxTypeLookup**. This lookup identifies the tax type in the SPT Masa PPN 1111 that's required by the tax authority. 
3. On the **Conditions** FastTab, select **Add**, and in the new line in the **Lookup result** column, select the type of tax. For example, PPN.
4. In the **Tax code** column, select the sales tax code that represents the tax type selected in the first column. For example, PPN10%.
5. Repeat steps 3-4 for all sales tax codes that are configured in your legal entity.
6. Select **Add** again, and then follow these steps to include the final record line:
   1. In the **Lookup result** column, select **NA - Not applicable**.
   2. In the **Tax code** column, select **Not blank**.
7. In the **State** field, select **Completed**, and then select **Save**. 
8. Close the **Application specific parameters** page.

The following table represents an example of how to configure the parameters to establish the configuration between the different boxes in the declaration form and sales tax configuration implemented in Finance.

| Lookup Result | Label                                                          | Line | Sales tax group  | Item sales tax group | Tax code    | Transaction classifier |
|---------------|----------------------------------------------------------------|------|------------------|----------------------|-------------|------------------------|
| BoxA1         | Export sales of tangible BKP, intangible BKP, and JKP          | 1    | PPN_EXP          | *Not blank*          | *Not blank* | Sales                  |
| BoxA1         | Export sales of tangible BKP, intangible BKP, and JKP          | 2    | PPN_EXP          | *Not blank*          | *Not blank* | SalesCreditNote        |
| BoxA2         | Output taxes on domestic sales with tax invoices               | 3    | PPN_DOM          | *Not blank*          | *Not blank* | Sales                  |
| BoxA2         | Output taxes on domestic sales with tax invoices               | 4    | PPN_DOM          | *Not blank*          | *Not blank* | SalesCreditNote        |
| BoxA2         | Output taxes on domestic sales with tax invoices               | 5    | PPN_EXE          | *Not blank*          | *Not blank* | SaleExempt             |
| BoxA2         | Output taxes on domestic sales with tax invoices               | 6    | PPN_EXE          | *Not blank*          | *Not blank* | SalesExemptCreditNote  |
| BoxB1         | Input taxes that can be on the import of BKP and utilization   | 7    | PPN_IMP          | *Not blank*          | *Not blank* | Purchase               |
| BoxB1         | Input taxes that can be on the import of BKP and utilization   | 8    | PPN_IMP          | *Not blank*          | *Not blank* | PurchaseCreditNote     |
| BoxB2         | Input taxes that can be credited for the acquisition of BKP    | 9    | *Not blank*      | *Not blank*          | PPN10%      | Purchase               |
| BoxB2         | Input taxes that can be credited for the acquisition of BKP    | 10   | *Not blank*      | *Not blank*          | PPN10%      | PurchaseCreditNote     |
| BoxB3         | Input taxes that can't be credited or that get facilities      | 11   | *Not blank*      | *Not blank*          | PPN_NO      | Purchase               |
| BoxB3         | Input taxes that can't be credited or that get facilities      | 12   | *Not blank*      | *Not blank*          | PPN_NO      | PurchaseCreditNote     |
| BoxAdj        | Adjustments                                                    | 13   | *Blank*          | *Blank*              | PPN_ADJ     | Sales                  |
| BoxAdj        | Adjustments                                                    | 14   | *Blank*          | *Blank*              | PPN_ADJ     | SalesCreditNote        |
| BoxAdj        | Adjustments                                                    | 15   | *Blank*          | *Blank*              | PPN_ADJ     | Purchase               |
| BoxAdj        | Adjustments                                                    | 16   | *Blank*          | *Blank*              | PPN_ADJ     | PurchaseCreditNote     |
| NA            | Not applicable                                                 | 17   | *Not blank*      | *Not blank*          | *Not blank* | *Not blank*            |

To help prevent issues when the report is generated, create all mappings where the sales tax codes and sales tax group are posted. For example, if **SalesCreditNote** is omitted on the line for **BoxA2** in this configuration, and tax transactions are posted by using the **PPN_DOM** sales tax group, you will encounter issues when the report is generated. Select **Tax** > **Inquire** > **Posted sales tax** to review all posted sales tax transactions and transactions that aren't included in this mapping of the configuration.

The following table provides the available values for the **Transaction classifier** field. This information explains how the tax transactions are classified and assigned to the related sales tax code.

| Classifier                      | Condition                            |
|---------------------------------|--------------------------------------|
| PurchaseCreditNote              | Credit note<br>Tax direction = Sales tax receivable   |
| Purchase                        | Not credit note<br>Tax direction = Sales tax receivable |
| SalesCreditNote                 | Credit note<br>Tax direction = Sales tax payable  |
| Sales                           | Not credit note<br>Tax direction = Sales tax payable |
| PurchaseExemptCreditNote        | Credit note<br>Tax direction = Tax-free purchase |
| PurchaseExempt                  | Not credit note<br>Tax direction = Tax-free purchase |
| SalesExemptCreditNote           | Credit note<br>Tax direction = Tax-free sales  |
| SaleExempt                      | Not credit note<br>Tax direction = Tax-free sales |
| UseTaxCreditNote                | Credit note<br>Tax direction = Use tax |
| UseTax                          | Not credit note<br>Tax direction = Use tax |
| PurchaseReverseChargeCreditNote | Credit note<br>Tax direction = Sales tax receivable<br>ReverseCharge_W = Yes    |
| PurchaseReverseCharge           | Not credit note<br>Tax direction = Sales tax receivable<br>ReverseCharge_W = Yes  |
| SalesReverseChargeCreditNote    | Credit note<br>Tax direction = Sales tax payable<br>ReverseCharge_W = Yes  |
| SalesReverseCharge              | Not credit note<br>Tax direction = Sales tax payable<br>ReverseCharge_W = Yes |

## Set up General ledger parameters

To generate the SPT Masa PPN 1111 form report in Microsoft Excel format, define an ER format on the **General ledger parameters** page.

1. Go to **Tax** > **Setup** > **General ledger parameters**.
2. On the **Sales tax** tab, in the **Tax options** section, in the **VAT statement format mapping** field, select **VAT Declaration Excel (ID)**. If you leave the field blank, the standard sales tax report will be generated in SQL Server Reporting Services (SSRS) format.

## Generate a SPT Masa PPN 1111 report

The process of preparing and submitting a SPT Masa PPN 1111 report for a period is based on sales tax payment transactions that were posted during the **Settle and post sales tax** job. For more information about sales tax settlement and reporting, see [Sales tax overview](../general-ledger/indirect-taxes-overview.md).

Follow these steps to generate the tax declaration report.

1. Go to **Tax** > **Declarations** > **Sales tax** > **Report sales tax for settlement period** or **Settle and post sales tax**.
2. Select the settlement period.
3. Select the from date.
4. Select the sales tax payment version.
5. Select **OK**. 
6. In the next dialog box, enter the following information:
	- The business activity code.
	- The amount of compensation for excess VAT due to the correction of the Tax Period VAT SPT if applicable.
	- The amount of Previous Tax Period VAT excess compensation if applicable.
	- The Date of compensation for excess VAT if applicable.
	- The amount of VAT paid in advance in the same tax period.
	- The number of version. Valid number from 0 to 7. 
7. Select **OK** to confirm and generate the report.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]


