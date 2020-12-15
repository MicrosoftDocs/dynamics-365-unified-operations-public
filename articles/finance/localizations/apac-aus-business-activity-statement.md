---
# required metadata

title: Business activity statement 
description: This topic provides information about the business activity statement (BAS) for Australia. The BAS is a form that all businesses submit to the Australian Taxation Office to report their taxation obligations.
author: anasyash
manager: tfehr
ms.date: 12/15/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 12641
ms.search.region: Australia
# ms.search.industry: 
ms.author: roschlom
ms.search.validFrom: 
ms.dyn365.ops.version:

---

# Business activity statement (BAS)

This topic provides information about the Business activity statement (BAS) for Australia. The BAS is a form that all businesses submit to the Australian Taxation Office (ATO) to report their taxation obligations.

The Business activity statement (BAS) feature is designed to help you fill in your BAS. The statement resembles the calculation worksheet that the ATO provides when you receive the BAS form in the mail.

The BAS includes the following taxation liabilities:

- Goods and Services Tax (GST) amounts that you owe the ATO from sales
- GST amounts that the ATO owes you from purchases
- Pay-As-You-Go (PAYG) Tax Withheld
- PAYG Installment
- Fringe Benefit Tax (FBT)

# Set up sales tax reporting codes

Set up sales tax reporting codes by following the instructions in [Set up sales tax reporting codes](https://docs.microsoft.com/dynamics365/finance/general-ledger/tasks/set-up-sales-tax-reporting-codes). The following reporting codes are associated with fields on the BAS report.

<table>
<thead>
<tr>
<td>
<p><strong>Report layout</strong></p>
</td>
<td>
<p><strong>Reporting code</strong></p>
</td>
<td>
<p><strong>Report text</strong></p>
</td>
<td>
<p><strong>Report setup</strong></p>
</td>
<td>
<p><strong>Field on the BAS report</strong></p>
</td>
</tr>
</thead>
<tbody>
<tr>
<td colspan="5">
<p style="text-align: center;"><strong>GST</strong></p>
</td>
</tr>
<tr>
<td>
<p>Default</p>
</td>
<td>
<p>1</p>
</td>
<td>
<p>G1 Total sales &amp; income and other supplies</p>
</td>
<td>
<p>Taxable sales and Sales tax payable</p>
</td>
<td>
<p>G1</p>
</td>
</tr>
<tr>
<td>
<p>Default</p>
</td>
<td>
<p>2</p>
</td>
<td>
<p>G2 GST free exports</p>
</td>
<td>
<p>Tax-free sales or Taxable sales</p>
</td>
<td>
<p>G2</p>
</td>
</tr>
<tr>
<td>
<p>Default</p>
</td>
<td>
<p>3</p>
</td>
<td>
<p>G3 Other GST free supplies</p>
</td>
<td>
<p>Tax-free sales or Taxable sales</p>
</td>
<td>
<p>G3</p>
</td>
</tr>
<tr>
<td>
<p>Default</p>
</td>
<td>
<p>4</p>
</td>
<td>
<p>G4 Input taxed sales &amp; income and other supplies</p>
</td>
<td>
<p>Taxable purchases and Sales tax receivable</p>
</td>
<td>
<p>G4</p>
</td>
</tr>
<tr>
<td>
<p>Default</p>
</td>
<td>
<p>7</p>
</td>
<td>
<p>G7 Adjustment payable</p>
</td>
<td>
<p>Sales tax payable</p>
</td>
<td>
<p>G7</p>
</td>
</tr>
<tr>
<td>
<p>Default</p>
</td>
<td>
<p>10</p>
</td>
<td>
<p>G10 Capital acquisitions</p>
</td>
<td>
<p>Taxable purchases and Sales tax receivable</p>
</td>
<td>
<p>G10</p>
</td>
</tr>
<tr>
<td>
<p>Default</p>
</td>
<td>
<p>11</p>
</td>
<td>
<p>G11 Other acquisitions</p>
</td>
<td>
<p>Taxable purchases and Sales tax receivable</p>
</td>
<td>
<p>G11</p>
</td>
</tr>
<tr>
<td>
<p>Default</p>
</td>
<td>
<p>18</p>
</td>
<td>
<p>G18 Adjustment (credit)</p>
</td>
<td>
<p>Sales tax receivable</p>
</td>
<td>
<p>G18</p>
</td>
</tr>
<tr>
<td>
<p>Default</p>
</td>
<td>
<p>1013</p>
</td>
<td>
<p>G10 and G13 Acquisitions for making input taxed sales, income, and other supplies</p>
</td>
<td>
<p>Taxable purchases and Sales tax receivable</p>
</td>
<td>
<p>G10 and G13</p>
</td>
</tr>
<tr>
<td>
<p>Default</p>
</td>
<td>
<p>1014</p>
</td>
<td>
<p>G10, G14 Capital acquisitions with no GST in the price</p>
</td>
<td>
<p>Tax-free purchases or Taxable purchases</p>
</td>
<td>
<p>G10 and G14</p>
</td>
</tr>
<tr>
<td>
<p>Default</p>
</td>
<td>
<p>1015</p>
</td>
<td>
<p>G10, G15 Capital acquisitions for private use or with non-deductible tax</p>
<p><strong>Note:</strong> On the <strong>Sales tax codes</strong> page (<strong>Tax &gt; Indirect taxes &gt; Sales tax &gt; Sales tax codes</strong>), enter a value in the <strong>Non deductible</strong> field for the sales tax code that uses this reporting code in the setup.</p>
</td>
<td>
<p>Taxable purchases and Sales tax receivable</p>
</td>
<td>
<p>G10 and G15</p>
</td>
</tr>
<tr>
<td>
<p>Default</p>
</td>
<td>
<p>101</p>
</td>
<td>
<p>1C Wine equalization tax payable</p>
</td>
<td>
<p>Sales tax payable</p>
</td>
<td>
<p>1C</p>
</td>
</tr>
<tr>
<td>
<p>Default</p>
</td>
<td>
<p>102</p>
</td>
<td>
<p>1D Wine equalization tax refundable</p>
</td>
<td>
<p>Sales tax receivable</p>
</td>
<td>
<p>1D</p>
</td>
</tr>
<tr>
<td>
<p>Default</p>
</td>
<td>
<p>201</p>
</td>
<td>
<p>1E Luxury car tax payable</p>
</td>
<td>
<p>Sales tax payable</p>
</td>
<td>
<p>1E</p>
</td>
</tr>
<tr>
<td>
<p>Default</p>
</td>
<td>
<p>202</p>
</td>
<td>
<p>1F Luxury car tax refundable</p>
</td>
<td>
<p>Sales tax receivable</p>
</td>
<td>
<p>1F</p>
</td>
</tr>
</tbody>
</table>

You can also set up the following reporting codes, and then make transactions or manually fill in corresponding fields of the BAS report. For more information, see the [Generate additional BAS report boxes for the settlement period](#_Generate_additional_BAS) section later in this topic.

<table>
<tbody>
<tr>
<td>
<p><strong>Report layout</strong></p>
</td>
<td>
<p><strong>Reporting code</strong></p>
</td>
<td>
<p><strong>Report text</strong></p>
</td>
<td>
<p><strong>Field on the BAS report</strong></p>
</td>
</tr>
<tr>
<td>
<p>Default</p>
</td>
<td>
<p>700</p>
</td>
<td>
<p>7 Deferred company/ fund instalment</p>
</td>
<td>
<p>7</p>
</td>
</tr>
<tr>
<td>
<p>Default</p>
</td>
<td>
<p>701</p>
</td>
<td>
<p>7A Deferred GST on imports</p>
</td>
<td>
<p>7A</p>
</td>
</tr>
<tr>
<td colspan="4">
<p style="text-align: center;"><strong>PAYG</strong></p>
</td>
</tr>
<tr>
<td>
<p>Default</p>
</td>
<td>
<p>400</p>
</td>
<td>
<p>4 Pay-As You Go Withholding</p>
</td>
<td>
<p>4</p>
</td>
</tr>
<tr>
<td>
<p>Default</p>
</td>
<td>
<p>501</p>
</td>
<td>
<p>5A Pay As You Go Instalment</p>
</td>
<td>
<p>5A</p>
</td>
</tr>
<tr>
<td>
<p>Default</p>
</td>
<td>
<p>502</p>
</td>
<td>
<p>5B Credit arising from reduced Pay As You Go instalment</p>
</td>
<td>
<p>5B</p>
</td>
</tr>
<tr>
<td>
<p>Default</p>
</td>
<td>
<p>31</p>
</td>
<td>
<p>W1 Total of salary, wages and other payments</p>
</td>
<td>
<p>W1</p>
</td>
</tr>
<tr>
<td>
<p>Default</p>
</td>
<td>
<p>32</p>
</td>
<td>
<p>W2 Amounts withheld from salary, wages and other payments</p>
</td>
<td>
<p>W2</p>
</td>
</tr>
<tr>
<td>
<p>Default</p>
</td>
<td>
<p>33</p>
</td>
<td>
<p>W3 Amounts withheld from investment distributions where no TFN is quoted</p>
</td>
<td>
<p>W3</p>
</td>
</tr>
<tr>
<td>
<p>Default</p>
</td>
<td>
<p>34</p>
</td>
<td>
<p>W4 Amounts withheld from payment of invoices where no ABN is quoted</p>
</td>
<td>
<p>W4</p>
</td>
</tr>
<tr>
<td>
<p>Default</p>
</td>
<td>
<p>51</p>
</td>
<td>
<p>T1 Instalment income</p>
</td>
<td>
<p>T1</p>
</td>
</tr>
<tr>
<td colspan="4">
<p style="text-align: center;"><strong>FBT</strong></p>
</td>
</tr>
<tr>
<td>
<p>Default</p>
</td>
<td>
<p>601</p>
</td>
<td>
<p>6A Fringe benefit tax instalment</p>
</td>
<td>
<p>6A</p>
</td>
</tr>
<tr>
<td>
<p>Default</p>
</td>
<td>
<p>602</p>
</td>
<td>
<p>6B Credit arising from fringe benefits tax instalment</p>
</td>
<td>
<p>6B</p>
</td>
</tr>
<tr>
<td>
<p>Default</p>
</td>
<td>
<p>61</p>
</td>
<td>
<p>F1 ATO-calculated fringe benefits tax instalment</p>
</td>
<td>
<p>F1</p>
</td>
</tr>
<tr>
<td>
<p>Default</p>
</td>
<td>
<p>62</p>
</td>
<td>
<p>F2 Estimated total fringe benefits tax payable</p>
</td>
<td>
<p>F2</p>
</td>
</tr>
<tr>
<td>
<p>Default</p>
</td>
<td>
<p>63</p>
</td>
<td>
<p>F3 Varied fringe benefits tax instalment</p>
</td>
<td>
<p>F3</p>
</td>
</tr>
</tbody>
</table>

You can also set up the following reporting codes. However, we recommend that you use reporting codes 1013 through 1015, which generate both field G10 and fields G13 through G15, because the amount in field G10 of the BAS report must contain the amounts in fields G13 through G15.

| **Report layout** | **Reporting code** | **Report text** | **Field on the BAS report** |
| --- | --- | --- | --- |
| Default | 13 | G13 Acquisitions for making input taxed sales &amp; income and other supplies | G13 |
| Default | 14 | G14 Acquisitions with no GST in the price | G14 |
| Default | 15 | G15 Non-income tax deductible acquisitions | G15 |

# Set up the BAS

1. In Microsoft Dynamics 365 Finance, go to **Organization administration \&gt; Organizations \&gt; Legal entities**.
2. On the **Legal entities** page, on the **Tax registration** FastTab, in the **Tax registration number** field, enter the tax registration number.
3. In [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/V2), in the Shared asset library, download the latest versions of the Electronic reporting (ER) configurations for the following report format:

- BAS(AU)

  For more information, see [Download Electronic reporting configurations from Lifecycle Services](https://docs.microsoft.com/dynamics365/dev-itpro/analytics/download-electronic-reporting-configuration-lcs).

4. Back in Finance, go to **General ledger \&gt; Ledger setup \&gt; General ledger parameters**.
5. On the **Sales tax** tab, set the **Apply sales tax taxation rules** option to **No**.
6. In the **Format mapping** field, select the **BAS(AU)** format that you downloaded earlier.

# Set up additional BAS report boxes

## Set up an additional BAS reconciliation account

1. Go to **Tax \&gt; Setup \&gt; Sales tax \&gt; Additional BAS reconciliation account**.
2. In the **BAS reconciliation account** field, specify the ledger account that will be used in the _Settle and post GST_ procedure to post sales tax amounts that are manually entered.

## Set up PAYG reason codes

1. Go to **Tax \&gt; Setup \&gt; Sales tax \&gt; BAS PAYG reason codes**.
2. Select **New** , and set the **Reason code** and **Description** fields.

For a list of PAYG reason codes, see [PAYG reason codes](https://www.ato.gov.au/Rates/PAYG-instalment-variations---reason-codes/).

## Set up fringe benefit reason codes

1. Go to **Tax \&gt; Setup \&gt; Sales tax \&gt; BAS fringe benefit reason codes**.
2. Select **New** , and set the **Reason code** and **Description** fields.

For a list of fringe benefit reason codes, see [FBT reason codes](https://www.ato.gov.au/Business/Business-activity-statements-(BAS)/In-detail/Instructions/FBT---how-to-complete-your-activity-statement-labels/?page=1#F4Reasoncodeforvariation).

# Generate and print the BAS report

## Generate additional BAS report boxes for the settlement period

1. Go to **Tax \&gt; Declarations \&gt; Sales tax \&gt; Additional BAS report boxes**.
2. Select **New** , and set the following fields.

| **Field** | **Description** |
| --- | --- |
| Settlement period | Select the settlement period for sales tax reporting. |
| From date | Enter the start date of the settlement period. |
| To date | Enter the end date of the settlement period. |
| Document identification number | Enter the document identification number for the BAS. |
| Date | The date when tax is settled. This field is automatically set when you create a sales tax payment. |
| Voucher | The voucher number of the sales tax payment. This field is automatically set when you create a sales tax payment. |

![](RackMultipart20201215-4-1fxazi9_html_fff743ec49718145.png)

> [!NOTE]
> When you create a sales tax payment, the date and voucher are filled in for the period, and you can no longer edit the line. If a line on the **Additional BAS report boxes** page wasn&#39;t manually created, it&#39;s automatically created when the _Sales tax payment_ or _Settle and post GST_ procedure is run.

3. On the **Cover page** tab, manually set the following fields if you didn&#39;t post tax transactions on the corresponding reporting codes.

| **Field** | **Description** |
| --- | --- |
| 7 Deferred installment | Enter the company or fund of the deferred installment. |
| 7A Deferred GST on imports | This field isn&#39;t used in the official BAS form. **Note:** In earlier versions of official BAS form, you could use this field to enter the deferred GST amount on imports that organizations can use under the Deferred GST Imports Scheme. |
| 1G Credit for wholesale sales tax | This field isn&#39;t used in the official BAS form. **Note:** In earlier versions of the official BAS form, you could use this field to enter the sales tax for items that are traded wholesale. |
| 5B Credit from PAYG | Enter the credit that is created when PAYG installments are reduced. |
| 6B Credit fringe benefits tax | Enter the credit that is created when FBT installments are reduced. |

4. On the **Back cover page** tab, manually set the following fields if you didn&#39;t post tax transactions on the corresponding reporting codes.

| **Field** | **Description** |
| --- | --- |
| W1 Total payroll | Enter the total for salary, wages, and other payments. |
| W-2 Withheld from payroll | Enter the amount that is withheld from salary, wages, and other payments. |
| W3 Withheld from investment where no TFN | Enter the amount that is withheld from investment distributions that no tax file number (TFN) is available for. |
| W4 Withheld from invoices where no ABN | Enter the amount that is withheld from invoice payments that no Australian Business Number (ABN) is available for. |
| T1 Installment income | Enter the PAYG installment income. |
| T2 Installment rate | Enter the PAYG commissioner&#39;s installment rate as a percentage. |
| T3 New varied installment rate | Enter the PAYG new varied installment rate as a percentage. |
| T4 Reason for variation | Select the reason code for the variation. The list of available reason codes is shown on the **BAS PAYG reason codes** page. For more information, see the [Set up PAYG reason codes](#_Set_up_PAYG) section earlier in this topic. |
| F1 ATO fringe benefit | Enter the FBT installment that is calculated by the ATO. |
| F2 Estimated total fringe benefits | Enter the estimated total FBT that must be paid. |
| F3 Varied fringe benefits tax | Enter the varied FBT installment. |
| F4 Reason for variation | Select the reason code that explains why the amount on the BAS was changed. The list of available reason codes is shown on the **BAS fringe benefit reason codes** page. For more information, see the [Set up fringe benefit reason codes](#_Set_up_fringe) section earlier in this topic. |
| 7C Fuel tax credit over claim | This field isn&#39;t used in the official BAS form. **Note:** In earlier versions of the official BAS, you could use this field to enter the amount of credit that must be claimed on tax for fuel that was used for business activities, machinery, plant equipment, and heavy vehicles. |
| 7D Fuel tax credit | This field isn&#39;t used in the official BAS form. **Note:** In earlier versions of the official BAS, you could use this field to enter the amount that you want to reduce your previously claimed fuel tax refund by. |

## Generate and preview a BAS report, and settle and post GST

1. Go to **Tax \&gt; Declarations \&gt; Sales tax \&gt; Australian BAS**.
2. In the **Australian BAS** dialog box, set the following fields.

| **Field** | **Description** |
| --- | --- |
| Settlement period | Select the settlement period. |
| --- | --- |
| From date | Enter the start date of the settlement period. |
| Transaction date | Enter the posting date for the sales tax settlement. |
| Sales tax payment version | Select the version of the sales tax report to settle:
  - **Original** – Include sales tax transactions of the first settlement calculation that was posted for the period.

  - **Corrections** – Include sales tax transactions of subsequent settlement calculations for the period.

  - **Latest corrections** – Include sales tax transactions of the last settlement calculation that was posted for the period.
  - **Total list** – Include all sales transactions for the period. These transactions include original and corrected transactions.
 |
| Post and settle GST | Set this option to **Yes** to post and settle the transactions for GST and create a sales tax payment.Before you complete the _Post and settle GST_ procedure, make sure that you set up the BAS reconciliation account as described in the [Set up an additional BAS reconciliation account](#_Set_up_an) section earlier in this topic. |

3. Select **OK**.
4. In the **Print Australian BAS** dialog box, select **OK**.

> [!Note] 
> You can find the form for the 2020 official Quarterly BAS report in [BAS C - Quarterly business activity statement](https://www.ato.gov.au/Forms/BAS-C---quarterly-BAS/). For GST, option 1 is supported. For PAYG, option 2 is supported.

5. On the generated BAS report, you can review the following data. You can then use the data to fill in the official BAS form.

> [!Note]
> In the following table, in the formulas in the &quot;Calculation&quot; column, brackets ([…]) enclose the values of reporting codes.

| **Field** | **Description** | **Calculation** | **Reference to the box in official BAS report** |
| --- | --- | --- | --- |
| **GST** |
| G1 | Total sales and income and other supplies | [1] + G2 + G3 + G4 | G1 |
| G2 | Exports | [2] | G2 |
| G3 | Other GST-free supplies | [3] | G3 |
| G4 | Input taxed sales and income and other supplies | [4] | This data isn&#39;t printed. It&#39;s used to calculate G9. |
| G5 | Total GST-free and input taxed supplies | G2 + G3 + G4 | This data isn&#39;t printed. It&#39;s used to calculate G9. |
| G6 | Total taxable supplies | G1 – G5 | This data isn&#39;t printed. It&#39;s used to calculate G9. |
| G7 | Adjustments | [7] or the manual calculation on the **Additional BAS report boxes** page. For more information, see the [Generate additional BAS report boxes for the settlement period](#_Generate_additional_BAS) section earlier in this topic. | This data isn&#39;t printed. It&#39;s used to calculate G9. |
| G8 | Total taxable supplies after adjustments | G6 + G7 | This data isn&#39;t printed. It&#39;s used to calculate G9. |
| G9 | GST on sales | The sales tax amount that is included in G1 + [9] | This data isn&#39;t printed. It&#39;s used to calculate 1A. |
| G10 | Capital acquisitions | [10] + [1013] + [1014] + [1015] | G10 |
| G11 | Other acquisitions | [11] + G13 + G14 + G15 | G11 |
| G12 | Total acquisitions | G10 + G11 | This data isn&#39;t printed. It&#39;s used to calculate G20. |
| G13 | Acquisitions for making input taxed sales and income and other supplies | [13] + [1013] | This data isn&#39;t printed. It&#39;s used to calculate G20. |
| G14 | Acquisitions with no GST in price | [14] + [1014] | This data isn&#39;t printed. It&#39;s used to calculate G20. |
| G15 | Total of estimated private use of acquisitions and non-income tax deductible acquisitions | [15] + [1015] | This data isn&#39;t printed. It&#39;s used to calculate G20. |
| G16 | Total of non-creditable acquisitions | G13 + G14 + G15 | This data isn&#39;t printed. It&#39;s used to calculate G20. |
| G17 | Total of creditable acquisitions | G12 – G16 | This data isn&#39;t printed. It&#39;s used to calculate G20. |
| G18 | Adjustments | [18] | This data isn&#39;t printed. It&#39;s used to calculate G20. |
| G19 | Total of creditable acquisitions after adjustments | G17 + G18 | This data isn&#39;t printed. It&#39;s used to calculate G20. |
| G20 | GST on purchases | The sales tax amount that is included in G12 | This data isn&#39;t printed. It&#39;s used in 1B. |
| **PAYG** |
| W1 | Total of salary, wages and other payments | [31] or the manual calculation on the **Additional BAS report boxes** page | W1 |
| W2 | Amounts withheld from salary, wages and other payments | [32] or the manual calculation on the **Additional BAS report boxes** page | W2 |
| W3 | Amounts withheld from investments distributions where no tax file number (TFN) is quoted. | [33] or the manual calculation on the **Additional BAS report boxes** page | W3 |
| W4 | Amounts withheld from payment of invoices where no Australian business number (ABN) is quoted. | [34] or the manual calculation on the **Additional BAS report boxes** page | W4 |
| T1 | Instalment income | [51] or the manual calculation on the **Additional BAS report boxes** page | T1 |
| T2 | Commissioner&#39;s instalment rate | [52] or the manual calculation on the **Additional BAS report boxes** page | T2 |
| T3 | New varied instalment rate | [53] or the manual calculation on the **Additional BAS report boxes** page | T3 |
| T4 | Reason for variation | The value from the **Additional BAS report boxes** page | T4 |
| **FBT** |
| F1 | ATO-calculated fringe benefits tax instalment | [61] or the manual calculation on the **Additional BAS report boxes** page | F1 |
| F2 | Estimated total fringe benefits tax payable | [62] or the manual calculation on the **Additional BAS report boxes** page | F2 |
| F3 | Varied fringe benefits tax instalment | [63] or the manual calculation on the **Additional BAS report boxes** page | F3 |
| F4 | Reason for fringe benefits tax variation | The value from the **Additional BAS report boxes** page | F4 |
| **Totals** |
| 1A | Goods and services tax payable | G9 | 1A |
| 1B | Credits for goods and services tax paid | G20 | 1B |
| 1C | Wine equalisation tax payable | [101] or the manual calculation on the **Additional BAS report boxes** page | 1C |
| 1D | Wine equalisation tax refundable | [102] or the manual calculation on the **Additional BAS report boxes** page | 1D |
| 1E | Luxury car tax payable | [201] or the manual calculation on the **Additional BAS report boxes** page | 1E |
| 1F | Luxury car tax refundable | [202] or the manual calculation on the **Additional BAS report boxes** page | 1F |
| 1G | Credit for wholesale sales tax | The value from the **Additional BAS report boxes** page | Not used |
| 2A | Total amounts you owe the ATO | 1A + 1C + 1E | Not used |
| 2B | Total amounts the ATO owes you | 1B + 1D + 1F + 1G | Not used |
| 3 | GST net amount | 2A – 2B | Not used |
| 4 | PAYG tax withheld | W2 + W3 + W4 + [400] | 4 |
| 5A | PAYG instalment | T1 × T3 ÷ 100, if T3 is entered. Otherwise, T1 × T2 ÷ 100. | 5A |
| 5B | Credit arising from reduced PAYG instalments | [502] or the manual calculation on the **Additional BAS report boxes** page | 5B |
| 6A | FBT instalment | F3, if a value is entered for that field. Otherwise, F1. | 6A |
| 6B | Credit arising from reduced FBT instalments | [602] or the manual calculation on the **Additional BAS report boxes** page | 6B |
| 7 | Deferred company or fund installment | [700] or the manual calculation on the **Additional BAS report boxes** page | 7 |
| 7A | Deferred GST on imports | [701] or the manual calculation on the **Additional BAS report boxes** page | Not used |
| 7C | Fuel tax credit over claim | The value from the **Additional BAS report boxes** page | Not used |
| 7D | Fuel tax credit | The value from the **Additional BAS report boxes** page | Not used |
| 8A | Total amounts you owe the ATO | 2A + 4 + 5A + 6A + 7 + 7A | 8A |
| 8B | Total amounts the ATO owes you | 2B + 5B + 6B | 8B |
| 9 | Net amount for the statement | 8A – 8B, if 8A \&gt; 8B.8B – 8A, if 8B \&gt; 8A. | 9 |

### Generate an E-BAS XML file

In the **Print Australian BAS** dialog box, set the **Generate E-BAS** option to **Yes** to generate the E-BAS statement. If you set this option on the **Select a file** page, browse to the XML file that you want to use as a template.

For example, create an XML template file that contains the following information.

\&lt;?xml version=&quot;1.0&quot; encoding=&quot;UTF-8&quot;?\&gt;

\&lt;DATA\&gt;

\&lt;field ID=&quot;fA1&quot;\&gt;BAS1\&lt;/field\&gt;

\&lt;field ID=&quot;fA3&quot;\&gt;1/1/2020\&lt;/field\&gt;

\&lt;field ID=&quot;fA4&quot;\&gt;31/3/2020\&lt;/field\&gt;

\&lt;field ID=&quot;fMANUAL\_MODE&quot;\&gt;true\&lt;/field\&gt;

\&lt;FIELD\_LIST\&gt;

\&lt;/FIELD\_LIST\&gt;

\&lt;/DATA\&gt;

Replace the values in the **fA1** , **fA3** , and **fA4** fields with the document identification number and dates that you require. To use this XML file as a template, browse to it on the **Select a file** page.

> [!Note]
> If you&#39;ve previously selected the **Generate E-BAS** option, you don&#39;t have to generate the XML file again the next time that you run the procedure. Instead, follow these steps:

1. Go to **Settings \&gt; User options**.
2. Select **Usage data**.
3. On the **General** tab, select **Reset**.

## Print the BAS report from Sales tax payments page

1. Go to **Tax \&gt; Inquiries and reports \&gt; Sales tax inquiries \&gt; Sales tax payments**.
2. Select the required line.
3. Select **Print Australian BAS**.

## Print the BAS report from the Additional BAS report boxes page

1. Go to **Tax \&gt; Declarations \&gt; Sales tax \&gt; Additional BAS report boxes**.
2. Select the required line.
3. Select **Additional BAS report boxes \&gt; Print Australian BAS**.

# Example

## Generate the BAS statement

The following example shows how you can set up sales tax codes and sales tax reporting codes, post transactions, and generate and print the BAS report. It uses the USMF legal entity.

1. Go to **Organization administration \&gt; Organizations \&gt; Legal entities**.
2. On the **Tax registration** FastTab, in the **Tax registration number** field, enter **AU89434123400**.
3. Go to **Tax \&gt; Indirect taxes \&gt; Sales tax \&gt; Sales tax codes** , and set up the following sales tax codes.

| **Sales tax code** | **Percentage** | **Description** |
| --- | --- | --- |
| CAPITAL | 10 | Capital acquisitionsat a rate of 10 percent. |
| --- | --- | --- |
| GST | 10 | Taxable sales and purchases at a rate of 10 percent. |
| NONDED CAP | 10 (non-deductible part = 25%) | Capital acquisitions at a rate of 10 percent, where the non-deductible part of tax is 25 percent. |
| EXPORTS | 0 | Export sales where the **Exempt** option is set to **Yes**. |
| FREE | 0 | GST-free sales and purchases where the **Exempt** option is set to **Yes**. |
| CAPFREE | 0 | GST-free capital acquisitionswhere the **Exempt** option is set to **Yes**. |
| LUX | 10 | Luxury car sales and purchases at a rate of 10 percent. |

4. On the **Report setup** FastTab, assign reporting codes to sales tax codes.

   The following table shows how to assign the sales tax reporting codes to sales tax codes.

| **Sales tax code** | **Taxable sales** | **Tax-free sale** | **Sales tax payable** | **Taxable purchases** | **Tax-free purchase** | **Sales tax receivable** |
| --- | --- | --- | --- | --- | --- | --- |
| CAPITAL |
 |
 |
 | 10 |
 | 10 |
| --- | --- | --- | --- | --- | --- | --- |
| GST | 1 |
 | 1 | 11 |
 | 11 |
| NONDEDCAP |
 |
 |
 | 1015 |
 | 1015 |
| EXPOTRS | 2 | 2 |
 |
 |
 |
 |
| FREE | 3 | 3 |
 |
 |
 |
 |
| CAPFREE |
 |
 |
 | 1014 | 1014 |
 |
| LUX |
 |
 | 201 |
 |
 | 202 |

> [!Note]
> This configuration is just an example and depends on the structure of the sales tax codes that are used. If you want values to be calculated and transferred to the sales tax report, for each tax code that is used in the sales tax payment process, you must set a relevant sales tax reporting code in one or more fields on the **Report setup** tab.

5. Post the following transactions.

For example, for customer invoices, go to **Accounts receivable \&gt; Invoices \&gt; All free text invoices**. For vendor invoices, go to **Accounts payable \&gt; Invoices \&gt; Invoice journal**.

| **Date** | **Transaction type** | **Amount net** | **VAT amount** | **Sales tax code** | **Amount is expected on the reporting code** | **Amount is expected on BAS report in the field** |
| --- | --- | --- | --- | --- | --- | --- |
| January 1, 2020 | Customer invoice | 2,000 | 200 | GST | 1 | G1 |
| January 1, 2020 | Vendor invoice | 800 | 80 | CAPITAL | 10 | G10 |
| January 1, 2020 | Vendor invoice | 1,400 | 140 (includes a non-deductible amount of 35) | NONDEDCAP | 1015 | G10, G15 |
| January 1, 2020 | Vendor invoice | 700 | 0 | CAPFREE | 1014 | G10, G14 |
| January 1, 2020 | Customer invoice | 1,200 | 0 | EXPOTRS | 2 | G2 |
| January 1, 2020 | Customer invoice | 500 | 0 | FREE | 3 | G3 |
| January 1, 2020 | Customer invoice | 300 | 30 | LUX | 201 | 1E |

6. Go to **Tax \&gt; Declarations \&gt; Sales tax \&gt; Additional BAS report boxes**.
7. Select **New** , and create the following line.

| **Settlement period** | **From date** | **To date** | **Document identification number** |
| --- | --- | --- | --- |
| ND | 1/1/2020 | 3/31/2020 | BAS1 |

8. Go to **Tax \&gt; Declarations \&gt; Sales tax \&gt; Australian BAS**.
9. In the **Australian BAS** dialog box, set the following values:

- **Settlement period:** ND
- **From date:** 1/1/2020
- **Transaction date:** 1/1/2020

10. Select **OK**.
11. In the **Print Australian BAS** dialog box, set the **Generate E-BAS** option to **No**.
12. Select **OK** , and review the following data in the printed form.

| **Field** | **Description** | **Value** |
| --- | --- | --- |
| **GST** |
| G1 | Total sales and income and other supplies | 3,900 (= 2,000 + 200 + 1,200 + 500) |
| G2 | Exports | 1,200 |
| G3 | Other GST-free supplies | 500 |
| G5 | Total GST-free and input taxed supplies | 1,700 (= 1,200 + 500) |
| G6 | Total taxable supplies | 2,200 (= 3,900 – 1,700) |
| G8 | Total taxable supplies after adjustments | 2,200 |
| G9 | GST on sales | 200 |
| G10 | Capital acquisitions | 3,120 (= 800 + 80 + 700 + 1,400 + 140) |
| G12 | Total acquisitions | 3,120 |
| G14 | Acquisitions with no GST in price | 700 |
| G15 | Total of estimated private use of acquisitions and non-income tax deductible acquisitions | 385 (= [1,400 + 140] × 25%) |
| G16 | Total of non-creditable acquisitions | 1,085 (= 700 + 385) |
| G17 | Total of creditable acquisitions | 2,035 (= 3,120 – 1,085) |
| G19 | Total of creditable acquisitions after adjustments | 2,035 |
| G20 | GST on purchases | 185 (= 80 + [140 × 75%]) |
| **Totals** |
| 1A | Goods and services tax payable | 200 |
| 1B | Credits for goods and services tax paid | 185 |
| 1E | Luxury car tax payable | 30 |
| 2A | Total amounts owed to the ATO | 230 (= 200 + 30) |
| 2B | Total amounts owed by the ATO | 185 |
| 3 | GST net amount | 45 (= 230 – 185) |
| 8A | Total amounts owed to the ATO | 230 |
| 8B | Total amounts owed by the ATO | 185 |
| 9 | Net amount for the statement | 45 (= 230 – 185) |

13. Create an XML file that contains the following information.

\&lt;?xml version=&quot;1.0&quot; encoding=&quot;UTF-8&quot;?\&gt;

\&lt;DATA\&gt;

\&lt;field ID=&quot;fA1&quot;\&gt;BAS1\&lt;/field\&gt;

\&lt;field ID=&quot;fA3&quot;\&gt;1/1/2020\&lt;/field\&gt;

\&lt;field ID=&quot;fA4&quot;\&gt;31/3/2020\&lt;/field\&gt;

\&lt;field ID=&quot;fMANUAL\_MODE&quot;\&gt;true\&lt;/field\&gt;

\&lt;FIELD\_LIST\&gt;

\&lt;/FIELD\_LIST\&gt;

\&lt;/DATA\&gt;

14. Go to **Tax \&gt; Declarations \&gt; Sales tax \&gt; Australian BAS**.
15. In the **Australian BAS** dialog box, set the following values:

- **Settlement period:** ND
- **From date:** 1/1/2020
- **Transaction date:** 1/1/2020

16. Select **OK**.
17. In the **Print Australian BAS** dialog box, set the **Generate E-BAS** option to **Yes** , and then select **OK**.
18. Browse to the XML file that you created in step 13 to generate the printed form and XML file.
19. Select **OK** , and review the following data in the XML file.

\&lt;?xml version=&quot;1.0&quot; encoding=&quot;UTF-8&quot;?\&gt;

\&lt;DATA\&gt;

\&lt;field ID=&quot;fA1&quot;\&gt;BAS1\&lt;/field\&gt;

\&lt;field ID=&quot;fA3&quot;\&gt;1/1/2020\&lt;/field\&gt;

\&lt;field ID=&quot;fA4&quot;\&gt;31/3/2020\&lt;/field\&gt;

\&lt;field ID=&quot;fMANUAL\_MODE&quot;\&gt;true\&lt;/field\&gt;

\&lt;FIELD\_LIST\&gt;

\&lt;FIELD ID=&quot;fG10&quot;\&gt;\&lt;VALUE\&gt;3120\&lt;/VALUE\&gt;\&lt;IS\_EDITABLE\&gt;true\&lt;/IS\_EDITABLE\&gt;\&lt;VISIBILITY\&gt;normal\&lt;/VISIBILITY\&gt;\&lt;/FIELD\&gt;\&lt;FIELD ID=&quot;fG1&quot;\&gt;\&lt;VALUE\&gt;3900\&lt;/VALUE\&gt;\&lt;IS\_EDITABLE\&gt;true\&lt;/IS\_EDITABLE\&gt;\&lt;VISIBILITY\&gt;normal\&lt;/VISIBILITY\&gt;\&lt;/FIELD\&gt;\&lt;FIELD ID=&quot;f1E&quot;\&gt;\&lt;VALUE\&gt;30\&lt;/VALUE\&gt;\&lt;IS\_EDITABLE\&gt;true\&lt;/IS\_EDITABLE\&gt;\&lt;VISIBILITY\&gt;normal\&lt;/VISIBILITY\&gt;\&lt;/FIELD\&gt;\&lt;FIELD ID=&quot;fG2&quot;\&gt;\&lt;VALUE\&gt;1200\&lt;/VALUE\&gt;\&lt;IS\_EDITABLE\&gt;true\&lt;/IS\_EDITABLE\&gt;\&lt;VISIBILITY\&gt;normal\&lt;/VISIBILITY\&gt;\&lt;/FIELD\&gt;\&lt;FIELD ID=&quot;fG3&quot;\&gt;\&lt;VALUE\&gt;500\&lt;/VALUE\&gt;\&lt;IS\_EDITABLE\&gt;true\&lt;/IS\_EDITABLE\&gt;\&lt;VISIBILITY\&gt;normal\&lt;/VISIBILITY\&gt;\&lt;/FIELD\&gt;\&lt;FIELD ID=&quot;fG9&quot;\&gt;\&lt;VALUE\&gt;200\&lt;/VALUE\&gt;\&lt;IS\_EDITABLE\&gt;true\&lt;/IS\_EDITABLE\&gt;\&lt;VISIBILITY\&gt;normal\&lt;/VISIBILITY\&gt;\&lt;/FIELD\&gt;\&lt;FIELD ID=&quot;fG14&quot;\&gt;\&lt;VALUE\&gt;700\&lt;/VALUE\&gt;\&lt;IS\_EDITABLE\&gt;true\&lt;/IS\_EDITABLE\&gt;\&lt;VISIBILITY\&gt;normal\&lt;/VISIBILITY\&gt;\&lt;/FIELD\&gt;\&lt;FIELD ID=&quot;fG15&quot;\&gt;\&lt;VALUE\&gt;385\&lt;/VALUE\&gt;\&lt;IS\_EDITABLE\&gt;true\&lt;/IS\_EDITABLE\&gt;\&lt;VISIBILITY\&gt;normal\&lt;/VISIBILITY\&gt;\&lt;/FIELD\&gt;\&lt;FIELD ID=&quot;fG20&quot;\&gt;\&lt;VALUE\&gt;185\&lt;/VALUE\&gt;\&lt;IS\_EDITABLE\&gt;true\&lt;/IS\_EDITABLE\&gt;\&lt;VISIBILITY\&gt;normal\&lt;/VISIBILITY\&gt;\&lt;/FIELD\&gt;\&lt;/FIELD\_LIST\&gt;

\&lt;/DATA\&gt;

## Generate a BAS statement with manual transactions

1. Go to **Tax \&gt; Setup \&gt; Sales tax \&gt; BAS PAYG reason codes**.
2. Select **New** , and create the following line.

| **Reason code** | **Description** |
| --- | --- |
| 21 | Change in investments |

3. Go to **Tax \&gt; Setup \&gt; Sales tax \&gt; BAS fringe benefit reason codes**.
4. Select **New** , and create the following line.

| **Reason code** | **Description** |
| --- | --- |
| 22 | Current business structure not continuing |

5. Go to **Tax \&gt; Declarations \&gt; Sales tax \&gt; Additional BAS report boxes**.
6. Select **New** , and set the following values:

- **Settlement period:** ND
- **From date:** 4/1/2020
- **To date:** 6/30/2020

7. On the **Cover page** tab, set the following values.

| **Field** | **Value** |
| --- | --- |
| 7 Deferred installment | 100 |
| 7A Deferred GST on imports | 200 |
| 1G Credit for wholesale sales tax | 300 |
| 5B Credit from PAYG | 400 |
| 6B Credit fringe benefits tax | 500 |

8. On the **Back cover page** tab, set the following values.

| **Field** | **Value** |
| --- | --- |
| W1 Total payroll | 600 |
| W-2 Withheld from payroll | 700 |
| W3 Withheld from investment where no TFN | 800 |
| W4 Withheld from invoices where no ABN | 900 |
| T1 Installment income | 1,000 |
| T2 Installment rate | 10 |
| T3 New varied installment rate | 15 |
| T4 Reason for variation | 21 |
| F1 ATO fringe benefit | 1,100 |
| F2 Estimated total fringe benefits | 1,200 |
| F3 Varied fringe benefits tax | 1,300 |
| F4 Reason for variation | 22 |
| 7C Fuel tax credit over claim | 1,400 |
| 7D Fuel tax credit | 1,500 |

9. Go to **Tax \&gt; Declarations \&gt; Sales tax \&gt; Australian BAS**.
10. In the **Australian BAS** dialog box, set the following values:

- **Settlement period:** ND
- **From date:** 4/1/2020
- **Transaction date:** 4/1/2020
- **Post and settle GST:** Yes

11. Select **OK**.
12. Go to **Tax \&gt; Inquiries and reports \&gt; Sales tax inquiries \&gt; Sales tax payments**.
13. Select the required line, select **Voucher** , and review the following data.

| **Description** | **Debit** | **Credit** |
| --- | --- | --- |
| 7 Deferred installments | 100 |
 |
| 7A Deferred GST on imports | 200 |
 |
| 1G Credit for wholesale sales tax |
 | 300 |
| 5B Credit from PAYG |
 | 400 |
| 6B Credit fringe benefits tax |
 | 500 |
| Pay as you go withholding | 2,400 (= 700 + 800 + 900) |
 |
| Pay as you go – installment | 150 (= 1,000 × 0.15) |
 |
| Fringe benefits tax installment | 1,300 |
 |
| 7C Fuel tax credit over claim | 1,400 |
 |
| 7D Fuel tax credit |
 | 1,500 |

> [!Note]
> Transactions weren&#39;t generated for amounts in fields **W1** , **F1** , and **F2** , because those fields aren&#39;t related to tax.
