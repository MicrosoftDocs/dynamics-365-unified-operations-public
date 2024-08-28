---
title: Japan consumption tax report
description: Learn how to set up and generate the Japan consumption tax report for legal entities in Japan, including a process for enabling the consumption tax report.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.date: 07/12/2024
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Japan
ms.search.validFrom: 2016-02-28
ms.search.form: LedgerConsumptionTaxCalcTrans_JP,LedgerConsumptionTaxCalcTrans2023_JP, LedgerConsumptionTaxReportTrans_JP, LedgerConsumptionTaxReportTrans2023_JP
ms.dyn365.ops.version: AX 7.0.0
---

# Japan consumption tax report

[!include [banner](../../includes/banner.md)]

This article explains how to set up and generate the Japan Consumption Tax (JCT) return report for legal entities in Japan.

The Japan consumption tax report consists of: **Consumption Tax and Local Consumption Tax Return** (Table 1), **Breakdown of Taxable Base Amount** (Table 2), and the following Appendixes:

- **Appendix 1** represents **Consumption tax amount calculation table by tax rate and consumption tax amount calculation sheet that serves as the tax base for local consumption tax**. It can be composed of Appendix 1-3 for the 6.24 percent and 7.8 percent tax rates, supplemented by Appendix 1-1 and Appendix 1-2 in cases where other tax rates were used during the reporting period (3 percent, 4 percent, or 6.3 percent).
- **Appendix 2** represents **Calculation table for taxable sales ratio, deductible purchase tax amount, etc.** It can be composed of Appendix 2-3 for the 6.24 percent and 7.8 percent tax rates, supplemented by Appendix 2-1 and Appendix 2-2 in cases where other tax rates were used during the reporting period (3 percent, 4 percent, or 6.3 percent).

For a description of the calculation rules for the JCT return report, see [Procedure 1 for preparing a tax return](https://www.nta.go.jp/taxes/shiraberu/zeimokubetsu/shohi/keigenzeiritsu/pdf/0018008-056_01.pdf).

## Enable the consumption tax report

1. Go to **Tax** \> **Setup** \> **Parameters** \> **General ledger parameters**.
2. On the **Sales tax** tab, on the **Japanese tax reporting** FastTab, set the **Consumption tax reports** option to **Yes**.

## Enter Japan reporting information for a legal entity

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
2. On the **Registration numbers** FastTab, select **Edit**.
3. In the **Accounting personnel** field, enter a value.
4. In the **Company representative** field, enter a value.

## Set up sales tax reporting codes for consumption tax reporting

Set up sales tax reporting codes by following the instructions in [Set up sales tax reporting codes](../../general-ledger/tasks/set-up-sales-tax-reporting-codes.md).

For more information about the general approach for setting up and generating the tax statement by reporting codes, see [Tax reporting by reporting codes](../europe/emea-vat-reporting.md).

The following table provides an example of sales tax reporting codes for Japan. For some of the reporting codes, several options are available.

| Reporting code | Reporting code name | Sales tax codes setup |
|----------------|---------------------|-----------------------|
| **1**          | **Taxable sales** | <ul><li>Taxable sales</li></ul> |
| 8001           | Consumption tax amount of taxable sales | <ul><li>Sales tax payable</li></ul> |
| 9001           | Taxable sales credit note | <ul><li>Taxable sales credit note</li></ul> |
| 7001           | Consumption tax amount of taxable sales credit note | <ul><li>Sales tax on sales credit note</li></ul> |
| **12**         | Taxable purchases related to specified taxable purchases - reverse charge | <ul><li>Taxable sales</li><li>Taxable import</li></ul> |
| 8012           | Consumption tax on taxable purchases related to specified taxable purchases - reverse charge | <ul><li>Sales tax payable</li><li>Use tax</li></ul> |
| 9012           | Taxable purchases credit note related to specified taxable purchases - reverse charge | <ul><li>Taxable sales credit note</li><li>Taxable import credit note</li></ul> |
| 7012           | Consumption tax on taxable purchases credit note related to specified taxable purchases - reverse charge | <ul><li>Sales tax on sales credit note</li><li>Sales tax on import credit note</li></ul> |
| **202**        | **Tax-exempt sales** | <ul><li>Tax-free sale</li></ul> |
| 9202           | Tax-exempt sales credit note | <ul><li>Tax exempt sales credit note</li></ul> |
| **203**        | **Non-taxable export** | <ul><li>Tax-free sale</li></ul> |
| 9203           | Credit note on non-taxable export | <ul><li>Tax exempt sales credit note</li></ul> |
| **206**        | **Non-taxable sales** | <ul><li>Tax-free sale</li></ul> |
| 9206           | Non-taxable sales credit note | <ul><li>Tax exempt sales credit note</li></ul> |
| **208**        | **Taxable purchases related to taxable sales** | <ul><li>Taxable purchases</li></ul> |
| 8208           | Consumption tax amount of taxable purchases related to taxable sales | <ul><li>Sales tax receivable</li></ul> |
| 9208           | Taxable purchase credit note related to taxable sales | <ul><li>Taxable purchase credit note</li></ul> |
| 7208           | Consumption tax amount of taxable purchase credit note related to taxable sales | <ul><li>Sales tax on purchase credit note</li></ul> |
| **214**        | **Taxable purchases related to non-taxable sales** | <ul><li>Taxable purchases</li></ul> |
| 8214           | Consumption tax amount of taxable purchases related to non-taxable sales | <ul><li>Sales tax receivable</li></ul> |
| 9214           | Taxable purchase credit note related to non-taxable sales | <ul><li>Taxable purchase credit note</li></ul> |
| 7214           | Consumption tax amount of taxable purchase credit note related to non-taxable sales | <ul><li>Sales tax on purchase credit note</li></ul> |
| **215**        | **Common taxable purchases (related to both taxable and non-taxable sales)** | <ul><li>Taxable purchases</li></ul> |
| 8215           | Consumption tax amount of common taxable purchases | <ul><li>Sales tax receivable</li></ul> |
| 9215           | Common taxable purchase credit note | <ul><li>Taxable purchase credit note</li></ul> |
| 7215           | Consumption tax amount of common taxable purchase credit note | <ul><li>Sales tax on purchase credit note</li></ul> |
| **210**        | **Taxable import** | <ul><li>Taxable import</li></ul> |
| 8210           | Consumption tax amount of taxable import | <ul><li>Use tax</li></ul> |
| 9210           | Taxable import credit note | <ul><li>Taxable import credit note</li></ul> |
| 7210           | Consumption tax amount of taxable import credit note | <ul><li>Sales tax on import credit note</li></ul> |
|                | **Bad debt** | |
| 8308           | Bad debt | <ul><li>Sales tax receivable</li></ul> |
| 8310           | Bad debt - paid | <ul><li>Sales tax on purchase credit note</li></ul> |
|                | **Adjustments** | |
| 8221           | Adjustment (addition) amount of consumption tax related to fixed assets subject to adjustment when taxable sales ratio changes | <ul><li>Sales tax receivable</li></ul> |
| 8222           | Adjustment (addition) amount when fixed assets subject to adjustment are converted to taxable business use (tax-exempt business use) | <ul><li>Sales tax receivable</li></ul> |
| 8223           | Additional amount when a residential rental building is provided (transferred) for tax rental purposes | <ul><li>Sales tax receivable</li></ul> |
| 8014           | Amount of adjustment (addition) to the amount of consumption tax in case you do not receive exemption from tax liability | <ul><li>Sales tax receivable</li></ul> |
| 7221           | Adjustment (subtraction) amount of consumption tax related to fixed assets subject to adjustment when taxable sales ratio changes | <ul><li>Sales tax on sales credit note</li></ul> |
| 7222           | Adjustment (subtraction) amount when fixed assets subject to adjustment are converted to taxable business use (tax-exempt business use) | <ul><li>Sales tax on sales credit note</li></ul> |
| 7014           | Amount of adjustment (subtraction) to the amount of consumption tax in case you receive exemption from tax liability | <ul><li>Sales tax on sales credit note</li></ul> |

## Set up sales tax codes

Set up sales tax codes as described in [Set up sales tax for JCT](apac-jpn-qualified-invoice-system.md#set-up-sales-tax-for-jct).

The following table shows the correspondence between sales tax rates in the sales tax code and consumption tax rates on the reports.

| Sales tax rate | Tax type | Consumption tax rate | Calculation of the consumption tax amount |
|----------------|----------|----------------------|-------------------------------------------|
| 3              | Standard | 3                    | Sales amount including tax × 3 ÷ 103      |
| 5              | Standard | 4                    | Sales amount including tax × 4 ÷ 105      |
| 8              | Standard | 6.3                  | Sales amount including tax – 6.3 ÷ 108    |
| 8              | Reduced  | 6.24                 | Sales amount including tax × 6.24 ÷ 108   |
| 10             | Standard | 7.8                  | Sales amount including tax × 7.8 ÷ 110    |

> [!IMPORTANT]
> In the **Tax type** field on the **Sales tax code** page, select the **Reduced** or **Standard** tax type.

## Set up tax reporting accounts for bad debts

Set up ledger accounts for bad debt and collected bad debt that will be used to select the transactions to report.

1. Go to **Tax** \> **Setup** \> **Sales tax** \> **Tax reporting accounts**.
2. Select **Edit**.
3. In the **Bad debt** field, specify the ledger account. For example, in the **JPMF** legal entity, select **84720**.
4. In the **Collected bad debt** field, specify the ledger account. For example, in the **JPMF** legal entity, select **84710**.

## Generate the Japan consumption tax report

1. Go to **Tax** \> **Declarations** \> **Sales tax** \> **Japanese sales tax report**.
2. In **Consumption tax working sheet** dialog box, set the following fields.

    | Field                      | Description |
    |----------------------------|-------------|
    | **From date**, **To date** | Enter the first and last dates of the sales tax settlement period to calculate consumption tax for. |
    | **Settlement period**      | Select the applicable sales tax settlement period. |
    | **Declaration type**       | Select **Final** or **Interim**. |
    | **Calculation method**     | If you have both taxable and non-taxable sales, select the method that's used to calculate the tax deduction amount: **Individual method** or **Lump sum method**. |
    | **Amendment**              | Set this option to **Yes** if you're preparing the amendment report for the previously generated report. |

3. Select **OK** to calculate amounts on the **Consumption tax calculation sheet** page.
4. On the **Consumption tax calculation sheet** page, on the **Appendix 1** and **Appendix 2** tabs, review the values in the **Item** fields. These values represent the amounts that will be entered in the rows of **Table 1** and **Table 2**.

    ### Appendix 1-3 - Consumption tax amount calculation table by tax rate and consumption tax amount calculation sheet that serves as the tax base for local consumption tax

    > [!NOTE]
    > In the "Calculation" column of the following table, brackets (\[…\]) in the formulas enclose the values of the reporting codes.

    | Field   | Description | Calculation |
    |---------|-------------|-------------|
    | Item1   | Tax basis amount | The value of this field is calculated as **Item 1-1** + **Item 1-2**. |
    | Item1-1 | Taxable sales | The value of this field is calculated as \[1\]. |
    | Item1-2 | Specific taxable purchases. Specific taxable purchases mean cross border services such as movies, performances by actors, musicians, athletes, etc. accepted by domestic businesses. These are consumed in Japan and thus subject to JCT via the reverse charge method. This value is reported only for businesses with less than 95% and have specific tax purchases. | The value of this field is calculated as \[12\]. |
    | Item2   | Consumption tax | The value of this field is calculated as \[8001\] + \[8012\]. |
    | Item3   | Adjustment of excess deductions | The value of this field is collected from **Item 25** + **Item 26** of **Appendix 2**. |
    | Item4   | Amount of deductible tax on purchases | The value of this field is collected from **Item 24** of **Appendix 2**. |
    | Item5   | Tax amount on refund | The value of this field is calculated as **Item 5-1** + **Item 5-2**. |
    | Item5-1 | Tax amount on sales refund | The value of this field is calculated as \[7001\]. |
    | Item5-2 | Tax amount on refund of specific taxable purchases | The value of this field is calculated as \[7012\]. |
    | Item6   | Tax amount related to bad debts | The value of this field is calculated as \[8308\] or tax transactions that are posted in the general ledger by using the main account that's set up as **Bad debt** at **Tax** \> **Setup** \> **Sales tax** \> **Tax reporting accounts**. |
    | Item7   | Deduction tax subtotal （④＋⑤＋⑥） | The value of this field is calculated as **Item 4** + **Item 5** + **Item 6**. |
    | Item8   | Amount of tax refundable （⑦－②－③） | The value of this field is calculated as **Item 7** – **Item 2** – **Item 3**. |
    | Item9   | Amount of tax payable （②＋③－⑦） | The value of this field is calculated as **Item 2** + **Item 3** – **Item 7**. |
    | Item10  | Tax refund due to insufficient amount of tax deduction （⑧） | The value of this field is calculated as **Item 8**. |
    | Item11  | Netted tax amount （⑨） | The value of this field is calculated as **Item 9**. |
    | Item12  | Tax refund | The value of this field is calculated as **Item 10** × 22 ÷ 78. |
    | Item13  | Tax payment | The value of this field is calculated as **Item 11** × 22 ÷ 78. |

    ### Appendix 2-3 - Calculation table for taxable sales ratio, deductible purchase tax amount, etc.

    > [!NOTE]
    > In the "Calculation" column of the following table, brackets (\[…\]) in the formulas enclose the values of the reporting codes.

    | Field  | Description | Calculation |
    |--------|-------------|-------------|
    | Item1  | Taxable sales (excluding tax amount) | The value of this field is calculated as \[1\] – \[9001\]. |
    | Item2  | Tax-exempt sales | The value of this field is calculated as \[202\] – \[9202\]. |
    | Item3  | Amount of non-taxable assets for export, amount of assets transferred to offices abroad | The value of this field is calculated as \[203\] – \[9203\]. |
    | Item4  | Amount of the transfer value of taxable assets, etc. （①＋②＋③） | The value of this field is calculated as **Item1** + **Item2** + **Item3**. |
    | Item5  | Amount of the transfer value of taxable assets, etc. （Amount of ④） | The value of this field equals **Item4**. |
    | Item6  | Non-taxable sales | The value of this field is calculated as \[206\] – \[9206\]. |
    | Item7  | Amount of the transfer value of assets, etc. （⑤＋⑥） | The value of this field is calculated as **Item5** + **Item6**. |
    | Item8  | Taxable sales ratio （④／⑦） | The value of this field is calculated as **Item4** ÷ **Item7**. |
    | Item9  | Amount of expenses relating to taxable purchases (tax included) | The value of this field is calculated as \[208\] + \[214\] + \[215\] + \[8208\] + \[8214\] + \[8215\] – \[9208\] – \[9214\] – \[9215\] – \[7208\] – \[7214\] – \[7215\]. |
    | Item10 | Amount of consumption taxes on taxable purchases | The value of this field is calculated as the sum of consumption tax amounts of **Item8** by tax rate. |
    | Item11 | Amount of consideration paid for specified taxable purchases | The value of this field is calculated as \[12\]. |
    | Item12 | Consumption tax amount related to specified tax purchases | The value of this field is calculated as the sum of consumption tax amounts of **Item11** by tax rate. |
    | Item13 | Amount of consumption tax relating to taxable freight | The value of this field is calculated as the sum of consumption tax amounts of (\[210\] + \[8210\] – \[9210\] – \[7210\]) by tax rate. |
    | Item14 | Amount of consumption tax adjustment (addition & subtraction) in the event tax liability exemption status is granted or lost | The value of this field is calculated as \[8014\] - \[7014\]. |
    | Item15 | Total amount of taxes on taxable purchases, etc. （⑩＋⑫＋⑬±⑭） | The value of this field is calculated as the sum of consumption tax amounts of (\[208\] + \[8208\] – \[9208\] – \[7208\]) by tax rate. |
    | Item16 | Taxable sales are 500 million yen or less, and if the taxable sales ratio is 95% or more (Amount of ⑮) | If the value of the **Ratio of taxable sales** field is 0.95 or more, the value of this field is calculated as **Item15**. |
    | Item17 | Portion of ⑮ required for taxable sales only | If the value of the **Ratio of taxable sales** field is less than 0.95, or if amount of the transfer value of taxable assets is less than 500 million yen and **Individual method** is selected, the value of this field is calculated as \[208\] + \[8208\] + \[9208\] + \[7208\]. |
    | Item18 | Portion of ⑮ required for both taxable and non-taxable sales | If the value of the **Ratio of taxable sales** field is less than 0.95, or if amount of the transfer value of taxable assets is less than 500 million yen and **Individual method** is selected, the value of this field is calculated as \[215\] + \[8215\] – \[9215\] – \[7215\]. |
    | Item19 | Amount of deductible taxes on taxable purchases, etc based on the itemized method 〔⑰＋（⑱×④／⑦）〕 | If the value of the **Ratio of taxable sales** field is less than 0.95, or if amount of the transfer value of taxable assets is less than 500 million yen and **Individual method** is selected, the value of this field is calculated as **Item17** + **Item18** × **Ratio of taxable sales**. Otherwise, the value is **0** (zero). |
    | Item20 | Amount of deductible taxes on taxable purchases, etc. based on proportional method （⑮×④／⑦） | If the value of the **Ratio of taxable sales** field is less than 0.95, or if amount of the transfer value of taxable assets is less than 500 million yen and **Lump sum method** is selected, the value of this field is calculated as **Item15** × **Ratio of taxable sales**. Otherwise, the value is **0** (zero). |
    | Item21 | Amount of consumption tax adjustment (addition and subtraction) relating to fixed assets subject to adjustment in the event of a change in the taxable sales ratio | The value of this field is calculated as \[8221\] - \[7221\]. |
    | Item22 | Amount of consumption tax adjustment (addition & subtraction) in the event fixed assets subject to adjustment are converted is to taxable or are non-taxable business assets | The value of this field is calculated as \[8222\] - \[7222\]. |
    | Item23 | Additional amount when a residential rental building is provided (transferred) for tax rental purposes | The value of this field is calculated as \[8223\]. |
    | Item24 | Deductible tax on purchase. When 〔Amount of （⑯、⑲、or ⑳）±㉑±㉒＋㉓〕 is positive | If the value of the **Ratio of taxable sales** field is 0.95 or more, the value of this field is calculated as **Item16** + **Item21** + **Item22** + **Item23**. If the value of the **Ratio of taxable sales** field is less than 0.95, and **Individual method** is selected in the **Calculation method** field in the **Consumption tax working sheet** dialog box, the value of this field is calculated as **Item19** + **Item21** + **Item22** + **Item23**. If the value of the **Ratio of taxable sales** field is less than 0.95, and **Lump sum method** is selected in the **Calculation method** field in the **Consumption tax working sheet** dialog box, the value of this field is calculated as **Item20** + **Item21** + **Item22** + **Item23**. Positive result. |
    | Item25 | Tax adjustment for excess deduction. When 〔Amount of （⑯、⑲、or ⑳）±㉑±㉒＋㉓〕 is negative | If the value of the **Ratio of taxable sales** field is 0.95 or more, the value of this field is calculated as **Item16** + **Item21** + **Item22** + **Item23**. If the value of the **Ratio of taxable sales** field is less than 0.95, and **Individual method** is selected in the **Calculation method** field in the **Consumption tax working sheet** dialog box, the value of this field is calculated as **Item19** + **Item21** + **Item22** + **Item23**. If the value of the **Ratio of taxable sales** field is less than 0.95, and **Lump sum method** is selected in the **Calculation method** field in the **Consumption tax working sheet** dialog box, the value of this field is calculated as **Item20** + **Item21** + **Item22** + **Item23**. Negative result. |
    | Item26 | Amount of consumption tax relating to recovered bad debt | <p>The value of this field is calculated as \[8310\].</p><p><strong>Note:</strong> The amount of reporting code 8310 is related to the ledger account that's set up in the <strong>Collected bad debt</strong> field on the <strong>Tax reporting accounts</strong> page. For more information, see the <a href="#set-up-tax-reporting-accounts-for-bad-debts">Set up tax reporting accounts for bad debts</a> section of this article.</p> |

5. Select **Finalize** to finalize tax amounts.
6. After you finalize tax amounts, select **Consumption tax report** on the Action Pane to generate amounts on the **Consumption tax report** page.
7. On the **Header** tab, review the header information.

    | Field                                                                        | Description |
    |------------------------------------------------------------------------------|-------------|
    | **Taxation office name**                                                     | The details of the tax office name. |
    | **Company representative**, **Accounting personnel**                         | The name of the company representative. |
    | **From date**, **To date**                                                   | The tax calculation period. |
    | **From date for mid term declaration**, **To date for mid term declaration** | The dates for interim sales tax reports. |
    | **Registration number**                                                      | The company registration number. |

8. On the **Tax calculation** tab, review the tax amounts in the **Items** fields. The values represent the amounts that will be entered in the rows of **Table 1**.

    > [!NOTE]
    > In the "Calculation" column of the following table, brackets (\[…\]) in the formulas enclose the values of the reporting codes.

    | Field  | Description | Calculation |
    |--------|-------------|-------------|
    | **Calculation of consumption tax** | | |
    | Item1  | Taxable base amount | The value of this field is calculated as the sum by tax rates of **Item1** from **Appendix 1** rounded to the thousands. |
    | Item2  | Consumption tax amount | The value of this field is calculated as the sum by tax rates of **Item2** from **Appendix 1**. |
    | Item3  | Adjustment amount of excessive tax deduction | The value of this field is calculated as the sum by tax rates of **Item3** from **Appendix 1**. |
    | Item4  | Deductible tax on purchases | The value of this field is calculated as the sum by tax rates of **Item4** from **Appendix 1**. |
    | Item5  | Tax amount refund from sales credit notes | The value of this field is calculated as the sum by tax rates of **Item5** from **Appendix 1**. |
    | Item6  | Tax amount related to uncollectable debts | The value of this field is calculated as the sum by tax rates of **Item6** from **Appendix 1**. |
    | Item7  | Tax deduction subtotal | The value of this field is calculated as **Item4** + **Item5** + **Item6**. |
    | Item8  | Tax refund | The value of this field is calculated as **Item7** – **Item2** – **Item3** if the resulting value is positive. Otherwise, the value is **0** (zero). |
    | Item9  | Netted tax amount | The value of this field is calculated as **Item2** + **Item3** – **Item7** if the resulting value is positive. Otherwise, the value is **0** (zero). |
    | Item10 | Intermediate tax payment | The value of this field can be filled in manually. |
    | Item11 | Tax to be paid | If **Item9** is more than **Item10**, the value of this field is calculated as **Item9** – **Item10**. Otherwise, the value is **0** (zero). |
    | Item12 | Tax to be refunded | If **Item10** is more than **Item9**, the value of this field is calculated as **Item10** – **Item9**. Otherwise, the value is **0** (zero). |
    | Item13 | Previously declared tax (If this declaration is an amended declaration) | The value of this field can be filled in manually. |
    | Item14 | Tax due (If this declaration is an amended declaration) | The value of this field can be filled in manually. |
    | Item15 | Amount of taxable sales | The value of this field is calculated as **Item4** from **Appendix 2**. |
    | Item16 | Total amount of sales | The value of this field is calculated as **Item7** from **Appendix 2**. |
    | **Calculation of local consumption tax** | | |
    | Item17 | Tax refund | The value of this field equals **Item8**. |
    | Item18 | Netted tax amount | The value of this field equals **Item9**. |
    | Item19 | Tax refund amount (Transfer amount) | The value of this field is calculated as the tax refund amount (**Item12** from **Appendix 1**) multiplied by the local rate rounded to the thousands if the value in parentheses is negative. |
    | Item20 | Tax payment amount (Transfer amount) | The value of this field is calculated as the tax payment amount (**Item13** from **Appendix 1**) multiplied by the local rate rounded to the thousands if the resulting value is positive. |
    | Item21 | Interim tax payment (local) | The value of this field can be filled in manually. |
    | Item22 | Tax to be paid | If **Item20** is more than **Item21**, the value of this field is calculated as **Item20** – **Item21**. Otherwise, the value is **0** (zero). |
    | Item23 | Tax to be refunded | If **Item21** is more than **Item20**, the value of this field is calculated as **Item21** – **Item20**. Otherwise, the value is **0** (zero). |
    | Item24 | Previously declared tax (if this declaration is an amended declaration) | The value of this field can be filled in manually. |
    | Item25 | Netted tax payment amount (if this declaration is an amended declaration) | The value of this field can be filled in manually. |
    | Item26 | Total consumption tax and local consumption tax (payment or refund) | The value is calculated as **Item11** + **Item22** – **Item8** – **Item12** – **Item19** – **Item23**. |

9. On the **Breakdown of taxable base amount** tab, review the tax amounts in the **Items** fields. The values represent the amounts that will be entered in the rows of **Table 2**.

    > [!NOTE]
    > In the "Calculation" column of the following table, brackets (\[…\]) in the formulas enclose the values of the reporting codes.

    | Field  | Description | Calculation |
    |--------|-------------|-------------|
    | Item1  | Tax base amount. **Item1** of the Declaration form (Table 1) | The value of this field is calculated as the sum by tax rates of **Item1** from **Appendix 1**. |
    | Item2  | Total amount of consideration for transfer of taxable assets, etc. 3% applicable | The value of this field is calculated as **Item 1-1** from **Appendix 1** by 3% tax rate. |
    | Item3  | Total amount of consideration for transfer of taxable assets, etc. 4% applicable | The value of this field is calculated as **Item 1-1** from **Appendix 1** by 4% tax rate. |
    | Item4  | Total amount of consideration for transfer of taxable assets, etc. 6.3% applicable | The value of this field is calculated as **Item 1-1** from **Appendix 1** by 6.3% tax rate. |
    | Item5  | Total amount of consideration for transfer of taxable assets, etc. 6.24% applicable | The value of this field is calculated as **Item 1-1** from **Appendix 1** by 6.24% tax rate.|
    | Item6  | Total amount of consideration for transfer of taxable assets, etc. 7.8% applicable | The value of this field is calculated as **Item 1-1** from **Appendix 1** by 7.8% tax rate. |
    | Item7  | Total amount of consideration for transfer of taxable assets, etc. | The value of this field is calculated as the sum by tax rates of **Item 1-1** from **Appendix 1**. |
    | Item8  | Total amount of consideration paid for specific taxable purchases Note(1). 6.3% applicable | The value of this field is calculated as **Item 1-2** from **Appendix 1** by 6.3% tax rate. |
    | Item9  | Total amount of consideration paid for specific taxable purchases Note(1). 7.8% applicable | The value of this field is calculated as **Item 1-2** from **Appendix 1** by 7.8% tax rate. |
    | Item10 | Total amount of consideration paid for specific taxable purchases Note(1).| The value of this field is calculated as the sum by tax rates of **Item 1-2** from **Appendix 1**. |
    | Item11 | Consumption tax amount. **Item2** of the Declaration form (Table 1) | The value of this field is calculated as the sum by tax rates of **Item2** from **Appendix 1**. |
    | Item12 | (11) Breakdown. 3% applicable | The value of this field is calculated as **Item2** from **Appendix 1** by 3% tax rate. |
    | Item13 | (11) Breakdown. 4% applicable | The value of this field is calculated as **Item2** from **Appendix 1** by 4% tax rate. |
    | Item14 | (11) Breakdown. 6.3% applicable | The value of this field is calculated as **Item2** from **Appendix 1** by 6.3% tax rate. |
    | Item15 | (11) Breakdown. 6.24% applicable | The value of this field is calculated as **Item2** from **Appendix 1** by 6.24% tax rate. |
    | Item16 | (11) Breakdown. 7.8% applicable | The value of this field is calculated as **Item2** from **Appendix 1** by 7.8% tax rate. |
    | Item17 | Reimbursed tax amount. **Item5** of the Declaration form (Table 1). | The value of this field is calculated as the sum by tax rates of **Item5** from **Appendix 1**. |
    | Item18 | Tax amount related to return of sales | The value of this field is calculated as the sum by tax rates of **Item 5-1** from **Appendix 1**. |
    | Item19 | Tax amount related to refund of specific taxable purchases | The value of this field is calculated as the sum by tax rates of **Item 5-2** from **Appendix 1**. |
    | Item20 | Consumption tax as local consumption tax base Note(2) | The value of this field is calculated as the sum by tax rates of **Item 5-1** from **Appendix 1**. |
    | Item21 | Consumption tax as local consumption tax base Note(2). 4% applicable | The value of this field is calculated as **Item 5-1** from **Appendix 1** by 4% tax rate. |
    | Item22 | Consumption tax as local consumption tax base Note(2). 6.3% applicable | The value of this field is calculated as **Item 5-1** from **Appendix 1** by 6.3% tax rate. |
    | Item23 | Consumption tax as local consumption tax base Note(2). 6.24% and 7.8% applicable | The value of this field is calculated as **Item 5-1** from **Appendix 1** by 6.24% and 7.8% tax rate. |
 
10. On the **Consumption tax report** page, on the **Additional information** tab, set the following fields.

    | Field                                    | Description |
    |------------------------------------------|-------------|
    | Installment basis                        | Set this option to **Yes** to apply the installment basis. |
    | Deferred payment basis                   | Set this option to **Yes** to apply deferred payment. |
    | Percentage of completion basis           | Set this option to **Yes** to apply the percentage of completion basis. |
    | Cash basis accounting                    | Set this option to **Yes** to apply the cash basis accounting. |
    | Exceptional tax calculation treatment    | Set this option to **Yes** to apply the exceptional tax calculation treatment. |
    | Individual method                        | Set this option to **Yes** for the individual method of tax calculation. |
    | Lump sum method                          | Set this option to **Yes** for the lump sum method of tax calculation. |
    | Fully deductible                         | Set this option to **Yes** if the tax amount is fully deductible. |
    | Taxable sales amount of benchmark period | Enter the taxable sales amount of the benchmark period. |
    | Bank information                         | Select the bank account if **Bank** is selected for the refund payment method. |
    | Comments                                 | Enter comments for the report. |
    | Name of the tax accountant               | Enter the name of the tax accountant. |
    | Document submitted law No.30             | Set this option to **Yes** if the document is submitted according to law No.30. |
    | Document submitted law No.33-2           | Set this option to **Yes** if the document is submitted according to law No.33-2. |

11. Select **Finalize** to finalize tax amounts.
12. After you finalize tax amounts, select **Consumption tax report** \> **Print** to print the **Consumption tax calculation sheet** and **Consumption tax report** reports.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
