---
title: Japan consumption tax report
description: This article explains how to set up and generate the Japan consumption tax report for legal entities in Japan.
author: liza-golub
ms.date: 06/10/2022
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Japan
ms.author: egolub
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.search.form: LedgerConsumptionTaxCalcTrans_JP,LedgerConsumptionTaxCalcTrans2023_JP, LedgerConsumptionTaxReportTrans_JP, LedgerConsumptionTaxReportTrans2023_JP
---

# Japan consumption tax report

[!include [banner](../../includes/banner.md)]

This topic explains how to set up and generate the Japan Consumption Tax (JCT) return report for legal entities in Japan.

The Japan consumption tax report consists of: **Consumption Tax and Local Consumption Tax Return** (Table 1), **Breakdown of Taxable Base Amount** (Table 2) and Appendixes:

- **Appendix 1**, that represents **Consumption tax amount calculation table by tax rate and consumption tax amount calculation sheet that serves as the tax base for local consumption tax** and can be composed of Appendix 1-3 for tax rates 6.24 ％ and 7.8 ％ supplemented with Appendix 1-1 and Appendix 1-2 in case when other tax rates were used during reporting period (3%, 4%, 6.3%).

- **Appendix 2**, that represents **Calculation table for taxable sales ratio, deductible purchase tax amount, etc.** and can be composed of Appendix 2-3 for tax rates 6.24 ％ and 7.8 ％ supplemented with Appendix 2-1 and Appendix 2-2 in case when other tax rates were used during reporting period (3%, 4%, 6.3%).

For a description of the calculation rules for JCT return report, see [Procedure 1 for preparing a tax return](https://www.nta.go.jp/taxes/shiraberu/zeimokubetsu/shohi/keigenzeiritsu/pdf/0018008-056_01.pdf).

## Enable the consumption tax report

1. Go to **Tax** > **Setup** > **Parameters** > **General ledger parameters**.
2. On the **Sales tax** tab, on the **Japanese tax reporting** FastTab, set the **Consumption tax reports** option to **Yes**.

## Enter Japan reporting information for a legal entity

1. Go to **Organization administration** > **Organizations** > **Legal entities**.
2. On the **Registration numbers** FastTab, select **Edit**.
3. In the **Accounting personnel** field, enter a value.
4. In the **Company representative** field, enter a value.

## Set up Sales tax reporting codes for consumption tax reporting

Set up sales tax reporting codes by following the instructions in [Set up sales tax reporting codes](../../general-ledger/tasks/set-up-sales-tax-reporting-codes.md).

For more information about general approach on setting up and generating the tax statement by **Reporting codes**, see [Tax reporting by Reporting codes](../europe/emea-vat-reporting.md).

The following table provides an example of sales tax reporting codes for Japan. For some of the **Reporting codes** several options are available.

| Reporting code | Reporting code name | Sales tax codes setup  |
|----------------|---------------------|-------------------------------------------------------|
| **1**          | **Taxable sales**   | <li> Taxable sales     |
| 8001           | Consumption tax amount of taxable sales   | <li> Sales tax payable     |
| 9001           | Taxable sales credit note   | Taxable sales credit note    |
| 7001           | Consumption tax amount of taxable sales credit note     | <li> Sales tax on sales credit note    |
| **12**         | Taxable purchases related to specified taxable purchases - reverse charge | <li> Taxable sales <br> <li> Taxable import |
| 8012           | Consumption tax on taxable purchases related to specified taxable purchases - reverse charge | <li> Sales tax payable <br> <li> Use tax |
| 9012           | Taxable purchases credit note related to specified taxable purchases - reverse charge  | <li> Taxable sales credit note <br> <li> Taxable import credit note |
| 7012           | Consumption tax on taxable purchases credit note related to specified taxable purchases - reverse charge | <li> Sales tax on sales credit note <br> <li> Sales tax on import credit note |
| **202**        | **Tax-exempt sales**    | <li> Tax-free sale      |
| 9202           | Tax-exempt sales credit note    | <li> Tax exempt sales credit note    |
| **203**        | **Non-taxable export**    |  <li> Tax-free sale    |
| 9203           | Credit note on non-taxable export     |  <li> Tax exempt sales credit note    |
| **206**        | **Non-taxable sales**    | <li> Tax-free sale      |
| 9206           | Non-taxable sales credit note   |  <li> Tax exempt sales credit note    |
| **208**        | **Taxable purchases related to taxable sales**     | <li> Taxable purchases     |
| 8208           | Consumption tax amount of taxable purchases related to taxable sales   |  <li> Sales tax receivable     |
| 9208           | Taxable purchase credit note related to taxable sales   | <li> Taxable purchase credit note     |
| 7208           | Consumption tax amount of taxable purchase credit note related to taxable sales   | <li> Sales tax on purchase credit note |
| **214**        | **Taxable purchases related to non-taxable sales**     | <li> Taxable purchases   |
| 8214           | Consumption tax amount of taxable purchases related to non-taxable sales  |  <li> Sales tax receivable     |
| 9214           | Taxable purchase credit note related to non-taxable sales   |  <li> Taxable purchase credit note   |
| 7214           | Consumption tax amount of taxable purchase credit note related to non-taxable sales | <li> Sales tax on purchase credit note |
| **215**        | **Common taxable purchases (related to both taxable and non-taxable sales)**        |  <li> Taxable purchases   |
| 8215           | Consumption tax amount of common taxable purchases    |  <li> Sales tax receivable    |
| 9215           | Common taxable purchase сredit note    | <li> Taxable purchase credit note      |
| 7215           | Consumption tax amount of common taxable purchase credit note   | <li> Sales tax on purchase credit note |
| **210**        | **Taxable import**     |  <li> Taxable import   |
| 8210           | Consumption tax amount of taxable import  |  <li> Use tax  |
| 9210           | Taxable import credit note   |  <li> Taxable import credit note        |
| 7210           | Consumption tax amount of taxable import credit note   | <li> Sales tax on import credit note   |
|                | **Bad debt** | |
| 8308           | Bad debt   |  <li> Sales tax receivable  |
| 8310           | Bad debt - paid    |  <li> Sales tax on purchase credit note |
|                | **Adjustments** | |
| 221            | Adjustment (addition or subtraction) amount of consumption tax related to fixed assets subject to adjustment when taxable sales ratio changes |  <li> Sales tax payable <br> <li> Sales tax on purchase credit note <br> <li> Sales tax receivable <br> <li> Sales tax on purchase credit note |
| 222            | Adjustment (addition or subtraction) amount when fixed assets subject to adjustment are converted to taxable business use (tax-exempt business use) | <li> Sales tax payable <br> <li> Sales tax on purchase credit note <br> <li> Sales tax receivable <br> <li> Sales tax on purchase credit note  |
| 223            | Additional amount when a residential rental building is provided (transferred) for tax rental purposes | <li> Sales tax payable <br> <li> Sales tax on purchase credit note <br> <li> Sales tax receivable <br> <li> Sales tax on purchase credit note  |
| 2014           | Amount of adjustment (addition or subtraction) to the amount of consumption tax in case you do not receive (receive) exemption from tax liability | <li> Sales tax payable <br> <li> Sales tax on purchase credit note <br> <li> Sales tax receivable <br> <li> Sales tax on purchase credit note  |

## Set up Sales tax codes

Set up **Sales tax codes** as it is described in [Set up sales tax for JCT](apac-jpn-qualified-invoice-system.md#set-up-sales-tax-for-jct) topic.

The following table shows the correspondence between sales tax rates in the sales tax code and consumption tax rates on the reports.

| Sales tax rate | Tax type | Consumption tax rate | Calculation of the consumption tax amount | 
|----------------|----------|----------------------|-------------------------------------------|
| 3              | Standard | 3                    | Sales amount including tax × 3 ÷ 103      |
| 5              | Standard |  4                   | Sales amount including tax × 4 ÷ 105      |
| 8              | Standard |  6.3                 | Sales amount including tax – 6.3 ÷ 108    |
| 8              | Reduced  |  6.24                | Sales amount including tax × 6.24 ÷ 108   |
| 10             | Standard |  7.8                 | Sales amount including tax × 7.8 ÷ 110    |

> [!IMPORTANT]
> In the **Tax type** field of the **Sales tax code**, select the **Reduced** or **Standard** tax type.

## Set up tax reporting accounts for bad debts

Set up ledger accounts for bad debt and collected bad debt that will be used to select the transactions to report.

1. Go to **Tax** > **Setup** > **Sales tax** > **Tax reporting accounts**.
2. Select **Edit**.
3. In the **Bad debt** field, specify the ledger account. For example, in the **JPMF** legal entity, select **84720**.
4. In the **Collected bad debt** field, specify the ledger account. For example, in the **JPMF** legal entity, select **84710**.

## Generate the Japan consumption tax report

1. Go to **Tax** > **Declarations** > **Sales tax** > **Japanese sales tax report**.
2. In **Consumption tax working sheet** dialog box, set the following fields.

    | Field                  | Description   |
    |------------------------|---------------|
    | **From date, To date** | Enter the first and last dates of the **Sales tax settlement period** to calculate consumption tax for. |
    | **Settlement period**  | Select the applicable **Sales tax settlement period**.    |
    | **Declaration type**   | Select **Final** or **Interim**. |
    | **Calculation method** | If you have both taxable and non-taxable sales, select the method that is used to calculate the tax deduction amount: Individual method, Lump sum method.  |
    | **Amendment**          | Set this option to **Yes** if you're preparing the amendment report for the previously generated report. |

3. Select **OK** to calculate amounts on the **Consumption tax calculation sheet** page.
4. Review the values in the **Item** fields of **Appendix 1** and **Appendix 2** tabs of **Consumption tax calculation sheet** page. These values represent the amounts that will be entered in the rows of **Table 1** and **Table 2**.

### Appendix 1-3 - Consumption tax amount calculation table by tax rate and consumption tax amount calculation sheet that serves as the tax base for local consumption tax

> [!NOTE] 
> In the "Calculation" column of the following table, brackets ([…]) in the formulas enclose the values of the reporting codes.

| Field           | Description   | Calculation  |
|-----------------|---------------|--------------|
| **Item1**      | Tax basis amount  | The value of this field is calculated as **Item 1-1** + **Item 1-2**.  |
| **Item1-1**    | Taxable sales  | The value of this field is calculated as [1].  |
| **Item1-2**    | Specific taxable purchases. Specific taxable purchases mean cross border services such as movies, performances by actors, musicians, athletes, etc. accepted by domestic businesses. These are consumed in Japan and thus subject to JCT via the reverse charge method. This value is reported only for businesses with less than 95% and have specific tax purchases. | The value of this field is calculated as [12].  |
| **Item2**      | Consumption tax  | The value of this field is calculated as [8001] + [8012].  |
| **Item3**      | Adjustment of excess deductions  | The value of this field is collected from **Item 25** + **Item 26** of **Appendix 2**.  |
| **Item4**      | Amount of deductible tax on purchases  | The value of this field is collected from **Item 24** of **Appendix 2**.  |
| **Item5**      | Tax amount on refund  | The value of this field is calculated as **Item 5-1** + **Item 5-2**.  |
| **Item5-1**    | Tax amount on sales refund  | The value of this field is calculated as [7001].  |
| **Item5-2**    | Tax amount on refund of specific taxable purchases  | The value of this field is calculated as [7012].  |
| **Item6**      | Tax amount related to bad debts  | The value of this field is calculated as [8308] or tax transactions posted in general ledger using main account that is set up as **Bad debt** in **Tax** > **Setup** > **Sales tax** > **Tax reporting accounts**.  |
| **Item7**      | Deduction tax subtotal （④＋⑤＋⑥）| The value of this field is calculated as **Item 4** + **Item 5** + **Item 6**.  |
| **Item8**      | Amount of tax refundable （⑦－②－③）| The value of this field is calculated as **Item 7** - **Item 2** - **Item 3**.  |
| **Item9**      | Amount of tax payable （②＋③－⑦）| The value of this field is calculated as **Item 2** + **Item 3** - **Item 7**.  |
| **Item10**     | Tax refund due to insufficient amount of tax deduction （⑧）| The value of this field is calculated as **Item 8**.  |
| **Item11**     | Netted tax amount （⑨）| The value of this field is calculated as **Item 9**.  |
| **Item12**     | Tax refund | The value of this field is calculated as **Item 10** * 22 // 78.  |
| **Item13**     | Tax payment | The value of this field is calculated as **Item 11** * 22 // 78.  |

### Appendix 2-3 - Calculation table for taxable sales ratio, deductible purchase tax amount, etc.

> [!NOTE] 
> In the "Calculation" column of the following table, brackets ([…]) in the formulas enclose the values of the reporting codes.

| Field (Row)     | Description   | Calculation  |
|-----------------|---------------|--------------|
| Item1 (Row1)   | Taxable sales (excluding tax amount)  | The value of this field is calculated as [1] – [9001].  |
| Item2 (Row2)   | Tax-exempt sales  | The value of this field is calculated as [202] – [9202].   |
| Item3 (Row3)   | Amount of non-taxable assets for export, amount of assets transferred to offices abroad | The value of this field is calculated as [203] – [9203]. |
| Item4 (Row4)   | Amount of all taxable sales  | The value of this field is calculated as **Item1** + **Item2** + **Item3**. |
| Item5 (Row5)   | Amount of the transfer value of taxable assets, etc.  | The value of this field equals **Item4**.   |
| Item6 (Row6)   | Non-taxable sales   | The value of this field is calculated as [206] – [9206].    |
| Item7 (Row7)   | Total amount of sales   | The value of this field is calculated as **Item5** + **Item6**.   |
| Ratio of taxable sales (Row8)   | Ratio of taxable sales   | The value of this field is calculated as **Item4** ÷ **Item7**.    |
| Item8 (Row9)   | Amount of taxable purchases (including tax amount)  | The value of this field is calculated as [208] + [214] + [215] + [8208] + [8214] + [8215] – [9208] – [9214] – [9215] – [7208] – [7214] – [7215].  |
| Item9 (Row10)  | Amount of consumption tax on taxable purchases   | The value of this field is calculated as the sum of consumption tax amounts of **Item8** by tax rate.   |
| Item10 (Row13)  | Amount of consumption tax on taxable import  | The value of this field is calculated as the sum of consumption tax amounts of ([210] + [8210] – [9210] – [7210]) by tax rate.  |
| Item11 (Row14)    | Amount of consumption tax adjustment (addition and subtraction)  | The value of this field is **0** (zero).   |
| Item12 (Row15)  | Total amount of taxes on taxable purchases    | The value of this field is calculated as **Item9** + **Item10** + **Item11**.   |
| Item13 (Row16)  | Total amount of taxes on taxable purchases, if **Ratio of taxable sales** is \>= 0.95    | If the value of the **Ratio of taxable sales** field is 0.95 or more, the value of this field equals **Item12**. Otherwise, the value is **0** (zero).  |

    **Item14**, **Item15**, and **Item16** are calculated if both the following conditions are met: 
    
    - The value of the **Ratio of taxable sales** field is less than 0.95.
    - **Individual method** is selected in the **Calculation method** field in the **Consumption tax working sheet** dialog box.
    
    Otherwise, the value of these fields is **0** (zero).

| Field (Row)  | Description  | Calculation   |
|--------------|--------------|---------------|
| Item14 (Row17)   | Portion of Item12 related to taxable sales only  | The value of this field is calculated as the sum of consumption tax amounts of ([208] + [8208] – [9208] – [7208]) by tax rate.   |
| Item15 (Row18)   | Portion of Item12 related to both taxable and nontaxable sales  | The value of this field is calculated as the sum of consumption tax amounts of ([215] + [8215] – [9215] – [7215]) by tax rate.  |
| Item16 (Row19)  | Amount of deductible taxes on taxable purchases. | The value of this field is calculated as **Item14** + **Item15** × **Ratio of taxable sales**  |
| Item17 (Row20)  | Amount of deductible taxes on taxable purchases calculated by the lump sum distribution method  | If the value of the **Ratio of taxable sales** field is less than 0.95, and **Lump sum method** is selected in the **Calculation method** field in the **Consumption tax working sheet** dialog box, the value of this field is calculated as **Item12** × **Ratio of taxable sales**. Otherwise, the value is **0** (zero).  |
| Item18 (Row21)  | Adjustment (addition or decrease) of consumption tax on fixed assets subject to adjustment when sales ratio changes | The value of this field is **0** (zero).     |
| Item19 (Row22)   | Adjustment (addition or decrease) of consumption tax amount when the fixed assets are moved to taxable business (from non-taxable business) | The value of this field is **0** (zero).  |
| Item20 (Row23)     | Deductible tax on purchase  | If the value of the **Ratio of taxable sales** field is 0.95 or more, the value of this field is calculated as **Item13** + **Item18** + **Item19**. If the value of the **Ratio of taxable sales** field is less than 0.95, and **Individual method** is selected in the **Calculation method** field in the **Consumption tax working sheet** dialog box, the value of this field is calculated as **Item16** + **Item18** + **Item19**. If the value of the **Ratio of taxable sales** field is less than 0.95, and **Lump sum method** is selected in the **Calculation method** field in the **Consumption tax working sheet** dialog box, the value of this field is calculated as **Item17** + **Item18** + **Item19**. |
| Item21 (Row24)   | Excess deduction on purchases    | If the value of the **Item20** field is more than 0, the value of this field is **0** (zero). Otherwise, the value of this field is calculated as ABS(Item20), and the **Item20** field is set to **0** (zero).   |
| Item22 (Row25)  | Amount of consumption tax relating to recovered bad debt    | The value of this field is calculated as [8310] × 6.3 ÷ 108. **Note:** The amount of reporting code 8310 is related to the ledger account that is set up in the **Collected bad debt** field on the **Tax reporting accounts** page. For more information, see the [Set up tax reporting accounts for bad debts](#set-up-tax-reporting-accounts-for-bad-debts) section of this topic.  |

6. Select **Finalize** to finalize tax amounts.
7. After you've finalized tax amounts, select **Consumption tax report** to generate amounts on the **Consumption tax report** page.

    ![Consumption tax report page, Tax calculation tab.](../media/e8aaba7ef01662b2bd6aaec8be74cc2d.png)

8. On the **Header** tab, review the header information.

| Field                                                                | Description                              |
|----------------------------------------------------------------------|------------------------------------------|
| Taxation office name                                                 | The details of the tax office name.      |
| Company representative, Accounting personnel                         | The name of the company representative.  |
| From date, To date                                                   | The tax calculation period.              |
| From date for mid term declaration, To date for mid term declaration | The dates for interim sales tax reports. |

9. On the **Tax calculation** tab, review the tax amounts in the **Items** fields. The values represent the amounts that will be entered in the rows of Table 3-(2) ("Consumption tax return form").

> [!NOTE]
> In the "Calculation" column of the following table, brackets ([…]) in the formulas enclose the values of the reporting codes. The values of **Item** fields on the **Consumption tax calculation sheet** page are referenced as **CalcSheet.Item**.
> 
> Fields that are marked with an asterisk (\*) in the "Field (Row)" column aren't used on the **Consumption tax report** report (Table 3-(2)) as of October 1, 2019.

| Field (Row)  | Description   | Calculation  |
|--------------|---------------|--------------|
| **Calculation of consumption tax**   |   &nbsp;   |   &nbsp;  |
| Item1 (Row1..Row6 (at tax rates), Row7 (total)) | Taxable base amount   | The value of this field equals [1] rounded to the thousands.  |
| Item2 (Row11..Row16 (at tax rates))  | Consumption tax amount  | The value of this field is calculated as the sum of the consumption tax amounts of ([1] + [8001]) by tax rate.   |
| Item3\*   | Adjustment amount of excessive tax deduction | The value of this field is calculated as **CalcSheet.Item21** + **CalcSheet.Item22**.  |
| Item4\*    | Deductible tax on purchases     | The value of this field equals **CalcSheet.Item20**.  |
| Item5 (Row18)  | Tax amount refund from sales credit notes   | The value of this field is calculated as the sum of the consumption tax amounts of ([9001] + [7001]) by tax rate.     |
| Item6\*        | Tax amount related to uncollectable debts   | The value of this field is calculated as [8308] × 6.3 ÷ 108. **Note:** The amount of reporting code 8308 is related to the ledger account that is set up in the **Bad debt** field on the **Tax reporting accounts** page. For more information, see the [Set up tax reporting accounts for bad debts](#set-up-tax-reporting-accounts-for-bad-debts) section of this topic. |
| Item7\*    | Tax deduction subtotal   | The value of this field is calculated as **Item4** + **Item5** + **Item6**.   |
| Item8\*      | Tax refund        | The value of this field is calculated as **Item7** – **Item2** – **Item3** if the resulting value is positive. Otherwise, the value is **0** (zero).   |
| Item9\*     | Netted tax amount     | The value of this field is calculated as **Item2** + **Item3** – **Item7** if the resulting value is positive. Otherwise, the value is zero.     |
| Item10\*     | Intermediate tax payment  | The value of this field is zero.    |
| Item11\*     | Tax to be paid          | If **Item9** is more than **Item10**, the value of this field is calculated as **Item9** – **Item10**. Otherwise, the value is zero.     |
| Item12\*    | Tax to be refunded     | If **Item10** is more than **Item9**, the value of this field is calculated as **Item10** – **Item9**. Otherwise, the value is zero.    |
| Item13\*    | Previously declared tax (If this declaration is an amended declaration)   | The value of this field is zero.   |
| Item14\*    | Tax due (If this declaration is an amended declaration)    | The value of this field is zero.     |
| Item15\*    | Amount of taxable sales (taxable sales percentage)    | The value of this field equals **CalcSheet.Item4**.    |
| Item16\*    | Total amount of sales (taxable sales percentage)    | The value of this field is calculated as **Item15** + [206] – [9206] and equals **CalcSheet.Item7**.    |
| **Calculation of local consumption tax**  | &nbsp; |   &nbsp; |
| Item17\*   | Tax refund     | The value of this field equals **Item8**.   |
| Item18\*   | Netted tax amount      | The value of this field equals **Item9**.  |
| Item19\*   | Tax refund amount (Transfer amount)      | The value of this field is calculated as -((Row22 × 17 ÷ 63) + (Row23 × 22 ÷78)) rounded to the thousands if the value in parentheses is negative. You can find an example of the calculation of Row22 and Row23 at the end of the [Example](#example) section of this topic.  |
| Item20\*   | Tax payment amount (Transfer amount)    | The value of this field is calculated as (Row22 × 17 ÷ 63) + (Row23 × 22 ÷ 78) rounded to the thousands if the resulting value is positive. You can find an example of the calculation of Row22 and Row23 at the end of the [Example](#example) section. |
| Item21\*   | Interim tax payment (local)   | The value of this field is zero.   |
| Item22\*   | Tax to be paid     | If **Item20** is more than **Item21**, the value of this field is calculated as **Item20** – **Item21**. Otherwise, the value is **0** (zero).    |
| Item23\*    | Tax to be refunded     | If **Item21** is more than **Item20**, the value of this field is calculated as **Item21** – **Item20**. Otherwise, the value is **0** (zero).    |
| Item24\*    | Previously declared tax (if this declaration is an amended declaration)   | The value of this field is zero.   |
| Item25\*      | Netted tax payment amount (if this declaration is an amended declaration) | The value of this field is zero.   |
| Item26\*    | Total consumption tax and local consumption tax (payment or refund)    | If you set the **Amendment** option to **Yes** in the **Consumption tax working sheet** dialog box, the value of this field is calculated as **Item14** + **Item25**. Otherwise, the value is calculated as **Item11** + **Item22** – **Item8** – **Item12** – **Item19** – **Item23**.    |

10. On the **Consumption tax report** page, on the **Additional information** tab, set the following fields.

| Field                                    | Description                                                                       |
|------------------------------------------|-----------------------------------------------------------------------------------|
| Installment basis                        | Set this option to **Yes** to apply the installment basis.                        |
| Deferred payment basis                   | Set this option to **Yes** to apply deferred payment.                             |
| Percentage of completion basis           | Set this option to **Yes** to apply the percentage of completion basis.           |
| Cash basis accounting                    | Set this option to **Yes** to apply the cash basis accounting.                    |
| Exceptional tax calculation treatment    | Set this option to **Yes** to apply the exceptional tax calculation treatment.    |
| Individual method                        | Set this option to **Yes** for the individual method of tax calculation.          |
| Lump sum method                          | Set this option to **Yes** for the lump sum method of tax calculation.            |
| Fully deductible                         | Set this option to **Yes** if the tax amount is fully deductible.                 |
| Taxable sales amount of benchmark period | Enter the taxable sales amount of the benchmark period.                           |
| Bank information                         | Select the bank account if **Bank** is selected for the refund payment method.    |
| Comments                                 | Enter comments for the report.                                                    |
| Name of the tax accountant               | Enter the name of the tax accountant.                                             |
| Document submitted law No.30             | Set this option to **Yes** if the document is submitted according to law No.30.   |
| Document submitted law No.33-2           | Set this option to **Yes** if the document is submitted according to law No.33-2. |

11. Select **Finalize** to finalize tax amounts.
12. After you've finalized tax amounts, select **Consumption tax report \> Print** to print the **Consumption tax calculation sheet** and **Consumption tax report** reports.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
