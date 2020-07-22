---
# required metadata

title: VAT declaration (The Czech Republic)
description: This topic provides information about the value-added tax (VAT) declaration for the Czech Republic. 
author: anasyash
manager: AnnBe
ms.date: 07/21/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.assetid: 
ms.search.region: Czech Republic
# ms.search.industry: 
ms.author: anasyash
ms.search.validFrom: 2017-07-20
ms.dyn365.ops.version: 10.0.13

---

# VAT declaration (The Czech Republic)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic provides information about the value-added tax (VAT) declaration for the Czech Republic, including instructions for setting up and generating the VAT declaration and VAT control statement.

## <a name="overview"></a>VAT declaration overview

### VAT declaration

This section describes the sections and rows of the VAT declaration, calculations, and relations between the VAT declaration and VAT control statement.

To generate the VAT declaration and VAT control statement automatically, first create enough sales tax codes to keep separate VAT accounting for each box on the VAT declaration. You must also associate **Sales tax codes** with the **Lookup result** of the **Lookup for the VAT declaration boxes** in the **Application specific parameters** of the VAT declaration format and VAT control statement format. You can find more details about how to set up application specific parameters in the [Set up parameters for declarations fields](#set-up-parameters-for-declarations-fields) section later in this topic.

The **Lookup result** column in the table in Section 1, shows you which **Lookup result** is preconfigured for a specific VAT declaration row in the VAT declaration format and VAT control statement format. Use this information to correctly associate sales tax codes with the lookup result, and subsequently with the VAT declaration row.

> [!NOTE]
> If you configure Sales tax codes for posting incoming reverse charge VAT with **Use tax**, you should associate your sales tax codes with the lookup result that contains **UseTax** in the name. For example, for EU purchases, configure **EUPurchaseGoodsUseTaxStandard** for **Use tax** sales tax codes, or **EUPurchaseGoodsVATPayableStandard** for sales tax codes with a reverse charge. For more information about configuring reverse charge VAT, see [Reverse charges](emea-reverse-charge.md).

VAT declaration format in the Czech Republic contains the following sections:

- [Section 1: Taxable transactions](#taxabletransactions)
- [Section 2: Other supplies and supplies that originate outside of the Czech Republic with the right to deduct](#othersupplies)
- [Section 3: Additional data](#additionaldata)
- [Section 4: VAT deduction](#vatreduction)
- [Section 5: Reduction of the right to deduct](#righttodeduct)
- [Section 6: Tax calculation](#taxcalculation)

### <a name="taxabletransactions"></a>Section 1: Taxable transactions

| Row | Control statement section | Description                                                              | Rate     | Tax base (xml element) | Tax payable (xml element) | Lookup result                                                                                                                                    |
|-----|---------------------------|--------------------------------------------------------------------------|----------|------------------------|---------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1   | A4/A5                     | Domestic sales of goods and   services                                   | Standard | obrat23                | dan23                     | DomesticSalesVATPayableStandard - VATAdjustmentCustomerBadDebtsStandard                                                                                                                     |
| 2   | A4/A5                     | Domestic sales of goods and   services                                   | Reduced  | obrat5                 | dan5                      | DomesticSalesVATPayableReduced - VATAdjustmentCustomerBadDebtsReduced <br><br> DomesticSalesVATPayableReduced2 - VATAdjustmentCustomerBadDebtsReduced2                                       |
| 3   | A2                        | Intra-community purchase of   goods                                      | Standard | p_zb23                 | dan_pzb23                 | EUPurchaseGoodsVATPayableStandard <br> EUPurchaseGoodsUseTaxStandard                                                                                                                               |
| 4   | A2                        | Intra-community purchase of   goods                                      | Reduced  | p_zb5                  | dan_pzb5                  | EUPurchaseGoodsVATPayableReduced <br> EUPurchaseGoodsVATPayableReduced2 <br> EUPurchaseGoodsUseTaxReduced <br> EUPurchaseGoodsUseTaxReduced2                                                           |
| 5   | A2                        | Intra-community purchase of   services                                   | Standard | p_sl23_e               | dan_psl23_e               | EUPurchaseServicesVATPayableStandard <br> EUPurchaseServicesUseTaxStandard                                                                                                                         |
| 6   | A2                        | Intra-community purchase of   services                                   | Reduced  | p_sl5_e                | dan_psl5_e                | EUPurchaseServicesVATPayableReduced <br> EUPurchaseServicesVATPayableReduced2 <br> EUPurchaseServicesUseTaxReduced <br> EUPurchaseServicesUseTaxReduced2                                               |
| 7   | N/A                       | Import of goods                                                          | Standard | dov_zb23               | dan_dzb23                 | ImportGoodsVATPayableStandard <br> ImportGoodsUseTaxStandard                                                                                                                                       |
| 8   | N/A                       | Import of goods                                                          | Reduced  | dov_zb5                | dan_dzb5                  | ImportGoodsVATPayableReduced <br> ImportGoodsUseTaxReduced                                                                                                                                         |
| 9   | A2                        | Intra-community purchase of new   means of transport                     | N/A      | p_dop_nrg              | dan_pdop_nrg              | EUPurchaseNewTransportVATPayable <br> EUPurchaseNewTransportUseTax                                                                                                                                 |
| 10  | B1                        | Purchase of goods and services   under the domestic reverse charge ($92) | Standard | rez_pren23             | dan_rpren23               | DomesticPurchaseReverseChargeVATPayableStandard <br> DomesticPurchaseReverseChargeUseTaxStandard                                                                                                   |
| 11  | B1                        | Purchase of goods and services   under the domestic reverse charge ($92) | Reduced  | rez_pren5              | dan_rpren5                | DomesticPurchaseReverseChargeVATPayableReduced <br> DomesticPurchaseReverseChargeVATPayableReduced2 <br> DomesticPurchaseReverseChargeUseTaxReduced <br> DomesticPurchaseReverseChargeUseTaxReduced2 |
| 12  | A2                        | Other purchases with an   obligation to pay VAT                          | Standard | p_sl23_z               | dan_psl23_z               | OtherPurchasesVATPayableStandard <br> OtherPurchasesUseTaxStandard                                                                                                                                 |
| 13  | A2                        | Other purchases with an   obligation to pay VAT                          | Reduced  | p_sl5_z                | dan_psl5_z                | OtherPurchasesVATPayableReduced <br> OtherPurchasesVATPayableReduced2 <br> OtherPurchasesUseTaxReduced <br> OtherPurchasesUseTaxReduced2                                                               |

## <a name="othersupplies"></a>Section 2: Other supplies and supplies that originate outside of the Czech Republic with the right to deduct

| Row | Control statement section | Description                                                           | Tax base (xml element)  | Report field  (lookup result)                                                |
|-----|---------------------------|-----------------------------------------------------------------------|-------------------------|------------------------------------------------------------------------------|
| 20  | N/A                       | Intra-community sales of goods                                        | dod_zb                  | EUSalesGoods                                                                 |
| 21  | N/A                       | Intra-community sales of   services                                   | pln_sluzby              | EUSalesServices                                                              |
| 22  | N/A                       | Export of goods                                                       | pln_vyvoz               | ExportGoods                                                                  |
| 23  | N/A                       | Intra-community sales of new   transport to a non-taxable person      | dod_dop_nrg             | EUSalesNewTransport                                                          |
| 24  | N/A                       | Intra-community consignment of   goods                                | pln_zaslani             | EUConsignmentGoods                                                           |
| 25  | A1                        | Sales of goods and services   under the domestic reverse charge ($92) | pln_rez_pren            | DomesticSalesReverseCharge                                                   |
| 26  | A3 and other              | Other tax deductible   transactions                                   | pln_ost                 | OtherSalesWithRightToDeduct <br> OtherSalesWithRightToDeductGoldInvestment |


## <a name="additionaldata"></a>Section 3: Additional data

| Row | Control statement section | Description                                                  | Tax base (xml element)  | Tax amount (xml element) | Report field  (lookup result)                                                                                                                                         |
|-----|---------------------------|--------------------------------------------------------------|-------------------------|--------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 30  | N/A                       | Simplified triangular   intra-community acquisition of goods | tri_pozb                | N/A                      | SimplifiedTriangularEUPurchaseGoods                                                                                                                                   |
| 31  | N/A                       | Simplified triangular   intra-community sale of goods        | tri_dozb                | N/A                      | SimplifiedTriangularEUSalesGoods                                                                                                                                      |
| 32  | N/A                       | Import of exempt goods                                       | dov_osv                 | N/A                      | ImportGoodsVATExempt                                                                                                                                                  |
| 33  | A4                        | VAT amount adjustment for bad debts - creditor             | N/A                     | opr_verit                | Informative value included in rows 1 and 2: <br><br> VATAdjustmentCustomerBadDebtsStandard <br> VATAdjustmentCustomerBadDebtsReduced <br> VATAdjustmentCustomerBadDebtsReduced2 |
| 34  | B2                        | VAT amount adjustment for bad   debts - debtor               | N/A                     | opr_dluz                 | Informative value included in rows 40 and 41: <br><br> VATAdjustmentVendorBadDebtsStandard <br> VATAdjustmentVendorBadDebtsReduced <br> VATAdjustmentVendorBadDebtsReduced2     |

## <a name="vatreduction"></a>Section 4: VAT deduction

<table width="99%">
<tbody>
<tr>
<td width="4%">
<p><strong>Row</strong></p>
</td>
<td width="7%">
<p><strong>&nbsp;Control statement </strong><strong>section</strong></p>
</td>
<td width="20%">
<p><strong>Description</strong></p>
</td>
<td width="7%">
<p><strong>&nbsp;</strong><strong>Rate</strong></p>
</td>
<td width="9%">
<p><strong>XML element - </strong><strong>Tax base</strong></p>
</td>
<td width="7%">
<p><strong>XML element -Full tax deduction</strong></p>
</td>
<td width="9%">
<p><strong>XML element - Tax deduction adjustment</strong></p>
</td>
<td width="34%">
<p><strong>Report field (Application specific parameters &ndash; lookup result)</strong></p>
</td>
</tr>
<tr>
<td width="4%">
<p>40</p>
</td>
<td width="7%">
<p>B2/B3</p>
</td>
<td width="20%">
<p>From taxable purchases</p>
</td>
<td width="7%">
<p>standard</p>
</td>
<td width="9%">
<p>pln23</p>
</td>
<td width="7%">
<p>odp_tuz23_nar</p>
</td>
<td width="9%">
<p>odp_tuz23</p>
</td>
<td width="34%">
<p><strong>Full deduction:</strong><br /> PurchaseVATDeductionStandard<br /> AcquiredAssetsStandard<br /> (minus) VATAdjustmentVendorBadDebtsStandard<br /> <br /> <strong>Deduction adjustment</strong>:<br /> PurchaseVATDeductionAdjustStandard</p>
<p>AcquiredAssetsAdjustStandard<br /> (minus) VATAdjustmentVendorBadDebtsAdjustStandard<br /> </p>
</td>
</tr>
<tr>
<td width="4%">
<p>41</p>
</td>
<td width="7%">
<p>B2/B3</p>
</td>
<td width="20%">
<p>From taxable purchases</p>
</td>
<td width="7%">
<p>reduced</p>
</td>
<td width="9%">
<p>pln5</p>
</td>
<td width="7%">
<p>odp_tuz5_nar</p>
</td>
<td width="9%">
<p>odp_tuz5</p>
</td>
<td width="34%">
<p><strong>Full deduction:</strong><br /> PurchaseVATDeductionReduced<br /> PurchaseVATDeductionReduced2<br /> AcquiredAssetsReduced<br /> (minus) VATAdjustmentVendorBadDebtsReduced<br /> (minus) VATAdjustmentVendorBadDebtsReduced2<br /> <br /> <strong>Deduction adjustment</strong>:<br /> PurchaseVATDeductionAdjustReduced<br /> PurchaseVATDeductionAdjustReduced2<br /> (minus)VATAdjustmentVendorBadDebtsAdjustReduced<br /> (minus)VATAdjustmentVendorBadDebtsAdjustReduced2<br /> AcquiredAssetsAdjustReduced</p>
</td>
</tr>
<tr>
<td width="4%">
<p>42</p>
</td>
<td width="7%">
<p>n/a</p>
</td>
<td width="20%">
<p>From import of goods when Tax authority is the customs office</p>
</td>
<td width="7%">&nbsp;</td>
<td width="9%">
<p>dov_cu</p>
</td>
<td width="7%">
<p>odp_cu_nar</p>
</td>
<td width="9%">
<p>odp_cu</p>
</td>
<td width="34%">
<p><strong>Full deduction:</strong><br /> ImportVATDeductionTaxAdminCustomsOffice<br /> <br /> <strong>Deduction adjustment</strong>:<br /> ImportVATDeductionAdjustTaxAdminCustomsOffice</p>
</td>
</tr>
<tr>
<td width="4%">
<p>43</p>
</td>
<td width="7%">
<p>n/a</p>
</td>
<td width="20%">
<p>From taxable transactions reported in rows 3-13</p>
</td>
<td width="7%">
<p>standard</p>
</td>
<td width="9%">
<p>nar_zdp23</p>
</td>
<td width="7%">
<p>od_zdp23</p>
</td>
<td width="9%">
<p>odkr_zdp23</p>
</td>
<td width="34%">
<p><strong>Full deduction:</strong><br /> VATDeductionFromPurchasesWithVATPayableStandard</p>
<p>&nbsp;</p>
<p>EUPurchaseGoodsUseTaxStandard (from row 3)</p>
<p>EUPurchaseServicesUseTaxStandard (from row 5)</p>
<p>ImportGoodsUseTaxStandard (from row 7)</p>
<p>EUPurchaseNewTransportUseTax (from row 9)</p>
<p>DomesticPurchaseReverseChargeUseTaxStandard&nbsp; (from row 10)</p>
<p>OtherPurchasesUseTaxStandard (from row 12)<br /> <br /> <strong>Deduction adjustment</strong>:<br /> VATDeductionAdjustFromPurchasesWithVATPayableStandard</p>
</td>
</tr>
<tr>
<td width="4%">
<p>44</p>
</td>
<td width="7%">
<p>n/a</p>
</td>
<td width="20%">
<p>From taxable transactions reported in rows 3-13</p>
</td>
<td width="7%">
<p>reduced</p>
</td>
<td width="9%">
<p>nar_zdp5</p>
</td>
<td width="7%">
<p>od_zdp5</p>
</td>
<td width="9%">
<p>odkr_zdp5</p>
</td>
<td width="34%">
<p><strong>Full deduction:</strong><br /> VATDeductionFromPurchasesWithVATPayableReduced</p>
<p>&nbsp;</p>
<p>EUPurchaseGoodsUseTaxReduced (from row 4)</p>
<p>EUPurchaseGoodsUseTaxReduced2 (from row 4)</p>
<p>EUPurchaseServicesUseTaxReduced&nbsp; (from row 6)</p>
<p>EUPurchaseServicesUseTaxReduced2 (from row 6)</p>
<p>ImportGoodsUseTaxReduced (from row 8)</p>
<p>DomesticPurchaseReverseChargeUseTaxReduced (from row 11)</p>
<p>DomesticPurchaseReverseChargeUseTaxReduced2 (from row 11)</p>
<p>OtherPurchasesUseTaxReduced (from row 13)</p>
<p>OtherPurchasesUseTaxReduced2 (from row 13)<br /> <br /> <strong>Deduction adjustment</strong>:<br /> VATDeductionAdjustFromPurchasesWithVATPayableReduced</p>
</td>
</tr>
<tr>
<td width="4%">
<p>45</p>
</td>
<td width="7%">
<p>n/a</p>
</td>
<td width="20%">
<p>Correction of tax deductions</p>
</td>
<td width="7%">&nbsp;</td>
<td width="9%">
<p>n/a</p>
</td>
<td width="7%">
<p>odp_rez_nar</p>
</td>
<td width="9%">
<p>odp_rezim</p>
</td>
<td width="34%">
<p><strong>Full deduction:</strong><br /> VATDeductionCorrection<br /> <br /> <strong>Deduction adjustment</strong>:<br /> VATDeductionAdjustCorrection</p>
</td>
</tr>
<tr>
<td width="4%">
<p><strong>46</strong></p>
</td>
<td width="7%">
<p>n/a</p>
</td>
<td width="20%">
<p><strong>Total deduction (40 + 41 + 42 + 43 + 44 + 45)</strong></p>
</td>
<td width="7%">&nbsp;</td>
<td width="9%">
<p><strong>n/a</strong></p>
</td>
<td width="7%">
<p><strong>odp_sum_nar</strong></p>
</td>
<td width="9%">
<p><strong>odp_sum_kr</strong></p>
</td>
<td width="34%">&nbsp;</td>
</tr>
<tr>
<td width="4%">
<p>47</p>
</td>
<td width="7%">
<p>n/a</p>
</td>
<td width="20%">
<p>Value of acquired assets defined in &sect; 4 para. d) ae)</p>
</td>
<td width="7%">
<p>x</p>
</td>
<td width="9%">
<p>nar_maj</p>
</td>
<td width="7%">
<p>od_maj</p>
</td>
<td width="9%">
<p>odkr_maj</p>
</td>
<td width="34%">
<p><em>Informative value. Included in Rows 40 and 41</em></p>
<p>&nbsp;</p>
<p><strong>Full deduction:</strong></p>
<p>AcquiredAssetsStandard<br /> AcquiredAssetsReduced<br /> </p>
<p><strong>Deduction adjustment</strong>:</p>
<p>AcquiredAssetsAdjustStandard</p>
<p>AcquiredAssetsAdjustReduced</p>
</td>
</tr>
</tbody>
</table>


### <a name="righttodeduct"></a>Section 5: Reduction of the right to deduct

| Row | Description                                                                                      | Tax base (xml element) | Comment                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|-----|--------------------------------------------------------------------------------------------------|------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 50  | Exempt sales                                                                                     | plnosv_kf              | Application specific parameter   lookup result: SalesVATExempt                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| 51  | Value of sales not included in   claculation of coefficient row 53 - with the right to deduct    | pln_nkf                | Informative value: Only for   December declaration. Relates to all January through December transactions.   <br> <br> The user manually inputs the amount in the parameter,   **Value of the taxable sales not included in calculation of the coefficient**   on the report dialog.                                                                                                                                                                                                                                                                                                                                                                                                |
| 51  | Value of sales not included in   calculation of coefficient row 53 - without the right to deduct | plnosv_nkf             | Informative value: Only for   December declaration. Relates to all January through December transactions.   <br> <br> The user manually inputs the amount in the parameter,   **Value of the taxable sales not included in calculation of the coefficient**   on the report dialog.                                                                                                                                                                                                                                                                                                                                                                                                |
| 52  | Part of the reduced tax   deduction (with deduction adjustment): pro rata coefficient            | koef_p20_nov           | Pro rata coefficient.   <br><br> User input parameter **Pro rata coefficient**.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| 52  | Part of the reduced tax   deduction (with deduction adjustment): deduction amount                | dp_uprav_kf            | Calculated automatically as,   Deduction amount = 46.odp_sum_kr * 52.koef_p20_nov                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| 53  | Settlement of tax deduction -   New pro rata coefficient                                         | koef_p20_vypor         | Only for December   declaration.<br><br> New pro rata coefficient. User manually   inputs the amount in the parameter, **New pro rata coefficient**. <br>   You can calcuate this amount manually based on all January through December   declarations amounts: <br> <br> 1. Calculate **Value of taxable   sales** = rows (1 + 2 + 20 + 21 + 22 + 23 + 24 + 25 + 26 + 31).TaxBase.   <br>2. Calcuate **Value of exempt sales** = row50.TaxBase. <br>   3. Calculate **New pro rata coefficient** = **Value of taxable sales** -   **Value of taxable sales not included in calculation of coefficient** -   **Value of exempt sales not included in calculation of coefficient**. |
| 53  | Settlement of tax deduction -   Change of deduction                                              | vypor_odp              | Only for December   declaration.<br><br> Adjustment of tax deduction. This line   reflects the correction of annual VAT deductions based on actual pro rata   coefficient vs. applied during the year estimated in the pro rata   coefficient. <br><br> he user manually inputs the amount in the   parameter, **Value of annual settlement of tax deduction** on the report   dialog. <br><br> You can calculate this amount manually based on   all declarations amounts that occurred January through December, as follows:   <br> Row 46.Tax deduction adjustment * (**New pro rata coefficient** -   **Pro rata coefficient**).                                              |


### <a name="taxcalculation"></a>Section 6: Tax calculation

| Row | Description                         | Value      | Comment                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|-----|-------------------------------------|------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 60  | Tax deduction adjustment            | uprav_odp  | *Only for December declaration*   <br><br> Application specific parameter lookup result:<br>   VATDeductionAdjustmentFA <br><br> For all fixed assets from which   the taxpayer claimed a VAT deduction, the taxpayer has to mintor how the   fixed assets are used. If the entitlement to the VAT deduction changes during   the monitoring period, the tax payer is obliged to adjust the relevant VAT   deduction in the VAT statement for December of the year when the entitlement   to VAT deduction has changed.    <br> Set up a special sales tax code for tax deduction   adjustment due to the change in fixed assets usage and manually post the tax   transaction for 100 percent of the tax amount when you need to adjust the VAT   deduction in this line.                  |
| 61  | Tax refunt                          | dan_vrac   | Application specific parameter   lookup result: <br> TaxRefund <br><br> Under some   conditions, a taxpayer is obliged to refund a partial amount of VAT paid by a   customer. For example, an individual from a third country, who paid Czech VAT   from goods that they purchased in the Czech Republic and then transported to   a third country. <br> This means that the taxpayer will declare the   respective transaction on row 1 or 2 in the VAT statement and then they can   claim a tax refund on row 61 after all of the conditions stipulated by the   Czech VAT Act are met. <br> Set up a special sales tax code for tax   refund to the individuals and manually post the tax transaction for 100% of   the tax amount when you need to show the tax refund on this line.  |
| 62  | Total tax payable                   | dan_zocelk | Calculated automatically as rows   1 + 2 + 3 + 4 + 5 + 6 + 7 + 8 + 9 + 10 + 11 + 12 + 13 - 61                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| 63  | Total tax deduction                 | odp_zocelk | Calculated automatically as   **row 46.Full tax deduction** + **row 52. Deduction** + **row 53.Change of   deduction** + **Ros 60**.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| 64  | Tax to be paid                      | dano_da    | Calculated automatically as row   62 - row 63 if 62 is > 63                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| 65  | Excess deduction                    | dano_no    | Calculated automatically as row   63 - row 62 if 63 is > 62                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| 66  | Adjustment for aditional tax return | dano       | Calculated automatically as row   62 - row 63                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |

## VAT control statement

The following sections provide an overview of the sections in the VAT control statement.

### Section A1: Sale of goods and services under domestic reverse charges

Section A1 shows the documents that generate the amount in row 25 of the VAT declaration.

This section contains the following information about each document:

| **Field**                                      | **XML element** |
|------------------------------------------------|-----------------|
| Tax document number                            | c_evid_dd       |
| VAT number of the customer (numeric part only) | ic_odb          |
| Date (which is the date of VAT register)       | duzp            |
| Subject code                                   | kod_pred_pl     |
| Tax base                                       | zakl_dane1      |

To automatically determine the **Subject code** for the document, set up enough **Reverse charge item groups** and associate them with Items (products), Items groups, or procurement categories. For more information, see the [Set up reverse charge item groups](#set-up-reverse-charge-item-groups) section later in this topic. You
can also find more information about how to configure reverse charges in the topic [Reverse charge VAT](emea-reverse-charge.md). If you are going to post incoming reverse charges in the vendor invoice journals that are not associated with products, you should have enough item sales tax groups to differentiate the subject codes of the reverse charges.

You also need to associate the pairs **Reverse charge item groups** – **Tax code** with the **Lookup result** of the **\$SubjectCodeLookup** in the **Application
specific parameters** of the **VAT control statement (CZ)** format. For more information about setupe application specific parameters, see the [Set up parameters for subject codes](#set-up-parameters-for-subject-codes) section in this topic.

The following subject codes are available in the **VAT control statement XML (CZ)** format:

| **Code**                 | **Description**                                                               |
|--------------------------|-------------------------------------------------------------------------------|
| GoldDelivery             | 1. Gold delivery (§92b)                                                       |
| TangibleAssetDelivery    | 3. Delivery of tangible assets (§92d)                                          |
| ConstructionInstallation | 4. Construction or installation (§92e)                                        |
| GoodsAnnex5              | 5. Goods listed in Annex 5 of the VAT Act (§92c)                                  |
| AllowancesGasEmission    | 11. Transfer of allowances and greenhouse gas emissions                       |
| CerealsIndustrialCrops   | 12. Cereals and industrial crops                                              |
| Metals                   | 13. Metals, including precious metals                                          |
| MobilePhones             | 14. Mobile phones                                                             |
| Integrated circuits      | 15. Integrated circuits and printed circuit boards                            |
| PortableDevices          | 16. Portable devices for automatic data processing (e.g. tablets or notebook) |
| VideoGameConsole         | 17. Video game consoles                                                       |

### Section B1: Purchase of goods and services under the domestic reverse charge (\$92)

Section B1 contains the information included on the document that is used to generate the amounts in rows 10 and 11 of the VAT declaration.

This section contains the following information about each document:

| **Field**                                           | **XML element** |
|-----------------------------------------------------|-----------------|
| Tax document number                                 | c_evid_dd       |
| VAT number of the vendor (numeric part only)        | dic_dod         |
| Date (which is the date of incoming vendor invoice) | duzp            |
| Subject code                                        | kod_pred_pl     |
| Tax base at standard rate                           | zakl_dane1      |
| Tax amount at standard rate                         | dan1            |
| Tax base at first reduced rate                      | zakl_dane2      |
| Tax amount at first reduced rate                    | dan2            |
| Tax base at second reduced rate                     | zakl_dane3      |
| Tax amount at second reduced rate                   | dan3            |

To automatically determine the **Subject code** for the document, you should use the same settings as described above for the Section A1.

### Section A2: Purchases with reverse charge, excluding domestic reverse charge, with an obligation to pay VAT

Section A2 shows documents which amounts are generated in rows 3, 4, 5, 6, and 9 (intra-community purchase of goods and services), and in rows 11 and 12 (O\other
purchases with the obligation to pay VAT) of the VAT declaration.

This section contains the following information about each document:

| **Field**                                                              | **XML element** |
|------------------------------------------------------------------------|-----------------|
| Tax document number                                                    | c_evid_dd       |
| VAT number of the vendor from another Member State (numeric part only) | vatid_dod       |
| Country that allocated the VAT number to the vendor                    | k_stat          |
| Date (which is the date of VAT register)                               | Dppd            |
| Tax base at standard rate                                              | zakl_dane1      |
| Tax amount at standard rate                                            | dan1            |
| Tax base at first reduced rate                                         | zakl_dane2      |
| Tax amount at first reduced rate                                       | dan2            |
| Tax base at second reduced rate                                        | zakl_dane3      |
| Tax amount at second reduced rate                                      | dan3            |

### Section A3: Transactions with the special scheme of gold sales

Section A3 shows the documents that generate the amount in the row 25 of the VAT declaration and other sales that have the right to deduct incoming VAT.

To determine the transactions automatically, set up a special sales tax code for these transactions and associate this sales tax code with the
**Lookup result OtherSalesWithRightToDeductGoldInvestment** of the **\$ReportFieldLookup** in the **Application specific parameters** of the VAT declaration format and VAT control statement format.

This section contains the following information about each document:

| **Field**                                                     | **XML element** |
|---------------------------------------------------------------|-----------------|
| Tax document number                                           | c_evid_dd       |
| VAT number of the customer (numeric part only) if it exists   | vatid_odb       |
| Country that allocated the VAT number to the customer         | k_stat          |
| Date (VAT register)                                           | dup             |
| The value of the sales                                        | osv_plneni      |
| Place of residence of the customer if there is no VAT number  | m_pobytu_sidlo  |
| First and last name of the customer if there is no VAT number | jm_prijm_obch   |
| Date of birth of the customer if there is no VAT number       | d_narozeni      |

## <a name="sectionA4"></a>Section A4: Taxable sales with amounts above 10,000 including VAT and all VAT adjustments made for customer bad debts

Sections A4 and A5 show documents that generate amounts in rows 1 and 2 of the VAT declaration.

Information about VAT amount adjustments for customer bad debts is also shown in row 33 of the VAT declaration.

To automatically determine the amount of VAT adjustment for bad debts, create a special tax code and post the write off the customer bad debts using this tax code. For more information, see the [Write off customer bad debts using Write off function](#write-off-customer-bad-debts-using-write-off-function) section in this topic. Also, associate this sales tax code with the lookup results, **VATAdjustmentCustomerBadDebtsStandard**, **VATAdjustmentCustomerBadDebtsReduced**, and **VATAdjustmentCustomerBadDebtsReduced2** of the **\$ReportFieldLookup** in the **Application specific parameters** of the VAT declaration format and VAT control statement format.

This section contains the following information about each document:

| **Field**                                                                                                                                          | **XML element** |
|----------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|
| Tax document number                                                                                                                                | c_evid_dd       |
| VAT number of the customer                                                                                                                         | dic_odb         |
| Date (VAT register)                                                                                                           | Dppd            |
| Fulfillment mode code: <br>**0** for normal filling<br>**1** for special scheme for travel service <br>**2** for special regime for second-hand goods         | kod_rezim_pl    |
| Tax base at standard rate                                                                                                                          | zakl_dane1      |
| Tax amount at standard rate                                                                                                                        | dan1            |
| Tax base at first reduced rate                                                                                                                     | zakl_dane2      |
| Tax amount at first reduced rate                                                                                                                   | dan2            |
| Tax base at second reduced rate                                                                                                                    | zakl_dane3      |
| Tax amount at second reduced rate                                                                                                                  | dan3            |
| Flag of VAT adjustment for bad debts:<br>**N** if the document is not VAT adjustment of bad debts <br>**P** if the document is VAT adjustment of bad debts | zdph_44         |

To determine the fulfillment mode code automatically, associate sales tax codes with the **Lookup result** of the **\$FulfillmentModeCodeLookup** in the
**Application specific parameters** of the VAT control statement (XML) format. For more information on how to set up **Application specific parameters** see the section, [How to post VAT adjustment for bad debts](#set-up-parameters-for-fulfillment-mode-codes) in this topic.

The following fulfillment mode codes are available in the format VAT control statement XML:

| **Code**                        | **Description**                                     |
|---------------------------------|-----------------------------------------------------|
| NormalFilling                   | 0. Normal filling                                   |
| SpecialSchemeForTravelService   | 1. § 89 ZDPH (special scheme for travel service)    |
| SpecialRegimeForSecondHandGoods | 2. § 90 ZDPH (special regime for second-hand goods) |

### Section B2: Taxable purchases with an amount above 10,000 including VAT and all VAT adjustments made for vendor bad debts

Sections B2 and B3 show documents that generate amounts in rows 40 and 41 of the VAT declaration.

Information about VAT amount adjustments for vendor bad debts is also shown in row 34 of the VAT declaration.

To automatically determine amount of VAT adjustment for bad debts, create a special tax code and post the writeoff of vendor bad debts using this tax code. For more information about this procedure, see the section [Write off vendor bad debts manually](#write-off-vendor-bad-debts-manually) in this topic. Associate this sales tax code with the lookup results, **VATAdjustmentVendorBadDebtsStandard**, **VATAdjustmentVendorBadDebtsReduced**, and **VATAdjustmentVendorBadDebtsReduced2** of the
**\$ReportFieldLookup** in the **Application specific parameters** of the VAT declaration format and the VAT control statement format.

Section B2 contains the following information about each document:

| **Field**                                                                                                                                           | **XML element** |
|-----------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|
| Tax document number                                                                                                                                 | c_evid_dd       |
| VAT number of the vendor                                                                                                                            | dic_dod         |
| Date (date of the incoming vendor invoice)                                                                                                 | Dppd            |
| Tax base at standard rate                                                                                                                           | zakl_dane1      |
| Tax amount at standard rate                                                                                                                         | dan1            |
| Tax base at first reduced rate                                                                                                                      | zakl_dane2      |
| Tax amount at first reduced rate                                                                                                                    | dan2            |
| Tax base at second reduced rate                                                                                                                     | zakl_dane3      |
| Tax amount at second reduced rate                                                                                                                   | dan3            |
| Flag of VAT adjustment for bad debts: <br>**N** if the document is not the VAT adjustment of bad debts <br>**P** if the document is VAT adjustment of bad debts | zdph_44         |
| Flag of the proportional right of deduction: Yes/No                                                                                                 | pomer           |

Out-of-the-box, the flag of the proportional right of deduction is set to **No**.

### Section A5: Taxable sales with an amount below 10 000 including VAT, and when there is no obligation to issue a tax document

Sections A4 and A5 show documents that generate amounts in rows 1 and 2 of the VAT declaration.

Section A5 contains one line with the following information for all documents included in this section:

| **Field**                         | **XML element** |
|-----------------------------------|-----------------|
| Tax base at standard rate         | zakl_dane1      |
| Tax amount at standard rate       | dan1            |
| Tax base at first reduced rate    | zakl_dane2      |
| Tax amount at first reduced rate  | dan2            |
| Tax base at second reduced rate   | zakl_dane3      |
| Tax amount at second reduced rate | dan3            |

### Section B3: Taxable purchases with an amount below 10,000 including VAT

Sections B2 and B3 show documents that generate amounts in rows 40 and 41 of the VAT declaration.

Section B3 contains one line with the following information for all documents included in this section.

| **Field**                         | **XML element** |
|-----------------------------------|-----------------|
| Tax base at standard rate         | zakl_dane1      |
| Tax amount at standard rate       | dan1            |
| Tax base at first reduced rate    | zakl_dane2      |
| Tax amount at first reduced rate  | dan2            |
| Tax base at second reduced rate   | zakl_dane3      |
| Tax amount at second reduced rate | dan3            |

## Set up the VAT declaration

To begin working with the VAT declaration, you should download electronic reporting formats. In [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/V2),
in the Shared asset library, download the latest versions of the Electronic reporting (ER) configurations for the VAT declaration format:

-   **Tax declaration model**
-   **Tax declaration model mapping**
-   **VAT declaration XML (CZ)**: This is configured in XML format DPHDP3.
-   **VAT declaration Excel (CZ)**: This configuration could be used to preview VAT declaration amounts in Microsoft Excel. Take into account that the Excel template in is English only. If you need to have the report printed in another language, you must have a small customization to translate the Excel template to another language and attach it to your derived configuration.
-   **VAT control statement (CZ)**: This is configured in XML format DPHKH1.

>   For more information, see [Download Electronic reporting configurations from Lifecycle Services](https://docs.microsoft.com/dynamics365/dev-itpro/analytics/download-electronic-reporting-configuration-lcs).

## Set up Application specific parameters for formats

### Set up parameters for declarations fields

To automatically generate VAT declaration, you should associate sales tax codes in the application and report fields in the Electronic reporting configuration.

1.  Go to **Workspaces** > **Electronic reporting** and select **Reporting configurations**.

2.  Select the configuration, **VAT declaration XML (CZ)** and then select **Configurations** > **Application specific parameters setup**.

3.  On the **Lookups** FastTab, select the lookup, **\$ReportFieldLookup**.

4.  On the **Conditions** FastTab, associate the sales tax codes and report fields:

<table>
<tbody>
<tr>
<td>
<p><strong>Column</strong></p>
</td>
<td>
<p><strong>Description</strong></p>
</td>
</tr>
<tr>
<td>
<p>Lookup result</p>
</td>
<td>
<p>Select report field for which you make setup. See details on report fields assignment to VAT declaration rows in the section [VAT declaration overview](#overview)</p>
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td>
<p>Tax code (Code)</p>
</td>
<td>
<p>Select Sales tax code which you associate to the report field. Tax transactions posted with the selected sales tax code will be collected in the respective report field.</p>
<p>It&rsquo;s highly recommended to separate sales tax codes in a way that one sales tax code is generating amounts in only one report field.</p>
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td>
<p>Name</p>
</td>
<td>
<p>If you didn&rsquo;t create enough sales tax codes so that one sales tax code is generating amounts in only one report field, you can additionally setup <strong>Transaction classifier</strong> in this column.</p>
<p>The following transaction classifiers are available for selection:</p>
<p>-&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &ldquo;Purchase&rdquo; (Purchase),</p>
<p>-&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &ldquo;PurchaseExempt&rdquo; (Tax exempt purchase),</p>
<p>-&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &ldquo;PurchaseReverseCharge&rdquo; (Tax receivable from purchase reverse charge),</p>
<p>-&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &ldquo;Sales&rdquo; (Sales),</p>
<p>-&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &ldquo;SalesExempt&rdquo; (Tax exempt sales),</p>
<p>-&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &ldquo;SalesReverseCharge&rdquo; (Tax payable from purchase reverse charge/ Sales reverse charge),</p>
<p>-&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &ldquo;Use tax&rdquo; (Use tax)</p>
<p>&nbsp;</p>
<p>For each transaction classifier a classifier for the credit note is also available, for example, &ldquo;PurchaseCreditNote&rdquo; (Purchase credit note)</p>
<p>&nbsp;</p>
</td>
</tr>
</tbody>
</table>

To prevent the format to throw an exception error message due to missed setup,
you can create the following line in the parameters:

| **Lookup result** | **Tax code (Code)** | **Name**      |
|-------------------|---------------------|---------------|
| Other             | \*Not blank\*       | \*Not blank\* |

> [!NOTE]
> This line must be created as the last line in the parameters. If you create this line, you should make sure that you set up parameters for all sales tax codes in the system. If some sales tax codes are missing in the setup, tax transactions with them will not be collected to VAT declaration. If you don’t create this line, you’ll get error message during the report run in case of there is tax transaction with the sales tax code that is not configured in the Application specific parameters.

5.  Change **State** of Application specific parameters to **Completed**.

6.  Review example of parameters on the picture:

[![Lookup for the Report fields](media/Pic1_ReportFieldLookup.png)](media/Pic1_ReportFieldLookup.png)

7.  On the Action pane, click **Export** to export parameters at XML file.

8.  Select configuration **VAT declaration Excel (CZ**). On the **Action pane**, click **Import** to import parameters that you configured for **VAT declaration XML (CZ)**. Change the entry in the **State** field to **Completed**.

9.  Select configuration **VAT control statement XML (CZ)**. Make the same settings manually as you did in point 4 above. Change **State** to **Completed**.

### Set up parameters for subject codes 

To classify the transaction to the subject code of reverse charge automatically
in VAT control statement sections A1 and B1, associate pairs of the
reverse charge item groups and item sales tax groups in the application and
supply codes in the Electronic reporting configuration.

1.  Go to **Workspaces \> Electronic reporting**. Select **Reporting
    configurations**.

2.  Select configuration **VAT control statement XML (CZ)**. Click
    **Configurations \> Application specific parameters setup.**

3.  On the **Lookups** FastTab, select lookup **\$SubjectCodeLookup**

4.  On the **Conditions** FastTab, associate **Reverse charge item groups** and subject codes:


| **Column**                          | **Description**                  |
|-------------------------------------|----------------------------------|
| Lookup result                       | Select subject code. The full list of subject codes is available above in [Section A1 Sales of goods and services under domestic reverse charge](#section-a1-sales-of-goods-and-services-under-domestic-reverse-charge)                  |
| Reverse charge code (Code)          | Select the Reverse charge item group that you associate with the selected Subject code. Note that if for certain transactions you post incoming reverse charge transaction without reference to the product, you must associate item sales tax group to the **Subject** code and in this case you should select \*Blank\* in this field. You must always have one line in the ** theApplication specific parameter** with **Lookup result** = **Other** and **Reverse charge code (Code)** = **\*Blank\*** to avoid generating an exception error when taking transactions without reverse charge. This must be the last line in the setup. |
| Item sales tax group (TaxItemGroup) | Select the item sales tax group that's associated with the selected **Subject** code. You must select specific item sales tax group if you do not have an appropriate reverse charge item group that will post the incoming reverse charge transaction without reference to the product (for example from the vendor invoice journal). Otherwise for all lines you can select **\*Not blank\*** in this column.                                                                                                                                                                                                          |

To prevent the format to fail with exception due to missed setup, you should set up the following lines as the last lines:

| **Lookup result** | **Reverse charge code (Code)** | **Item sales tax group (TaxItemGroup)** | **Comment**                    |
|-------------------|--------------------------------|-----------------------------------------|--------------------------------|
| Other             | \*Blank\*                      | \*Not blank\*                           | This line must be set up to prevent an error message being generated for transactions without a reverse charge code. |

Review example of parameters on the picture:

[![Lookup for the Subject code](media/Pic2_SubjectCodeLookup.png)](media/Pic2_SubjectCodeLookup.png)

## Set up parameters for fulfillment mode codes

To automatically classify the transaction to the fulfillment mode code in VAT
control statement section A4, you should associate sales tax codes in the
application and fulfillment subjects mode codes in the Electronic reporting
configuration.

1.  Go to **Workspaces > Electronic reporting**. Select **Reporting
    configurations**.

2.  Select configuration **VAT control statement XML (CZ)**. Click
    **Configurations > Application specific parameters setup**.

3.  On the **Lookups** FastTab, select **\$FulfillmentModeCodeLookup**.

4.  On the **Conditions** FastTab, associate sales tax codes and fulfillment
    subjects mode codes as follows:

| **Column**      | **Description**                                                                                                                                                                                                                                                                                                    |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Lookup result   | Select fulfillment code. The full list of codes is available above in [Section A4. Taxable sales with amount above 10 000 including VAT and all VAT adjustments made for customer bad debts](#sectiona4). |
| Tax code (Code) | Select sales tax code                                                                                                                                                                                                                                                                                              |

If you have only transactions with normal filling, you can create the following lines of the setting:

| **Lookup result** | **Tax code (Code)** |
|-------------------|---------------------|
| NormalFilling     | \*Not blank\*       |

Otherwise, set up the same line as the last line of the preceding setting to prevent the format from failing with an exception because of the missed setup.

### Set up parameters for no obligation to issue tax document

To automatically classify the sales transaction to the condition that there was
no obligation to issue tax document and consequently the transaction should be
shown in Section A5 regardless the threshold, you should associate pairs of
Sales tax group and sales tax code from the application to Yes or No condition
in the Electronic reporting configuration.

1.  Go to **Workspaces > Electronic reporting**. Select **Reporting configurations**.

2.  Select configuration **VAT control statement XML (CZ)**. Click
    **Configurations > Application specific parameters setup**.

3.  On the **Lookups** FastTab, select lookup **\$NoTaxDocument**.

4.  On the **Conditions** FastTab, associate sales tax groups and sales tax
    codes:

| **Column**      | **Description**                 |
|-----------------|---------------------------------|
| Lookup result   | Select Yes if there is no obligation to issue tax document (primarily this may be because customer is not registered for VAT purposes).                                                                                  |
| Sales tax group | Select sales tax group that you associate to customer when there is no obligation to issue tax document to them. If you are going to determine the condition using Sales tax code values, select **\*Not blank\*** here. |
| Tax code (Code) | Select sales tax code assigned to transaction if there is no obligation to issue tax document. If you can determine conditions using Sales tax group only, select **\*Not blank\*** here.                                |

5.  To prevent the format to fail with exception due to missed setup, create the
    following line as the last line in the setup:

| **Lookup result** | **Sales tax group (TaxGroup)** | **Tax code (Code)** |
|-------------------|--------------------------------|---------------------|
| No                | \*Not blank\*                  | \*Not blank\*       |

Review example of parameters on the picture:

[![Lookup for no obligation to issue tax document](media/Pic3_NoTaxDocumentLookup.png)](media/Pic3_NoTaxDocumentLookup.png)

6.  Change **State** of all parameters to **Completed**.

## Download and import the Data management package with example settings of Electronic messages.

>   The data package with example settings contains Electronic message settings
>   that are used to generate VAT declaration and VAT control statement as well
>   as to preview VAT declaration in Excel. You can extend these settings or
>   create your own. For more information about how to work with Electronic
>   messaging and how to create your own settings, see [Electronic messaging](https://docs.microsoft.com/dynamics365/finance/general-ledger/electronic-messaging).

Follow these steps:

1.  In the LCS Shared asset library, select **Data package** as the asset type.
    Download the package that is named **CZ VAT EM declaration package**. The
    file that is downloaded is named **CZ VAT declaration EM package.zip**.

2.  In the **Data management** workspace, select **Import**.

3.  In the **Job details** section, set the following values:

    -   In the **Name** field, enter any name for the job.

    -   In the **Data source format** field, select **Package**.

4.  In the **Upload data file** field, select **Upload**, and then select
    the **CZ VAT declaration EM package.zip** file that you downloaded earlier.

5.  After the data entities are uploaded, select **Import**.

6.  Go to **Tax > Inquiries and reports > Electronic messages > Electronic
    messages** and validate the electronic message processings that you
    imported.

| **Processing**        | **Processing code** | **Description**                             |
|-----------------------|---------------------|---------------------------------------------|
| VAT declaration       | DPHDP3              | VAT declaration in the Czech Republic       |
| VAT control statement | DPHKH1              | VAT control statement in the Czech Republic |

## Configure Electronic messages

1.  Set up information about Taxpayer in Electronic message additional fields

    1.1  Go to **Tax > Setup > Electronic messages > Additional fields**

    1.2  Select the line with additional field and on the **Value** FastTab add
        respective values of the field:

| **Additional field**     | **Value**                                                                                                                                                                           |
|--------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **DataBoxID**            | Enter identifier of the company’s Data box.                                                                                                                                         |
| **MainEconomicActivity** | Enter the code of company’s main economic activity                                                                                                                                  |
| **TaxAuthorityToFile**   | Enter the code of the tax authority to which the declaration file will be sent                                                                                                      |
| **ProRataCoef**          | Enter the pro rata coefficient applied during the year. If you need to apply pro rata coefficient in the declaration, enter the decimal value between 0 and 1 with comma separator. |

2.  Set up default values for declarations run in Electronic message processing

    2.1  Go to **Tax > Setup > Electronic messages > Electronic message
        processing**

    2.2  Select the line with processing and set up default values for
        declarations parameters on the **Message additional fields** FastTab:

| **Processing**                                           | **Additional field**         | **Comment**                                                                                                                                               | **XML element**               |
|----------------------------------------------------------|------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| DPHKH1 (VAT control statement)                           | **\<DataBoxID\>**            | Select the Data box ID that was entered earlier                                                                                                                        | id_dats                                                                                                                             |
| DPHDP3 (VAT declaration)                                 | **\<MainEconomicActivity\>** | Select main economic activity code entered earlier                                                                                                        | c_okec                                                                                                                              |
| DPHDP3 (VAT declaration), DPHKH1 (VAT control statement) | **\<TaxAuthorityToFile\>**   | Select tax authority code entered earlier                                                                                                                 | c_pracufo                                                                                                                           |
| DPHDP3 (VAT declaration), DPHKH1 (VAT control statement) | **\<ReportPeriodicity\>**    | Select the periodicity of the declaration submission in the reporting year: Monthly or Quarterly                                                          | Ctvrt – will be filled with the quarter number for Quarterly report Mesic – will be filled with the month number for Monthly report |
| DPHDP3 (VAT declaration)                                 | **\<TaxpayerType\>**         | Select the type of the Taxpayer: Taxpayer, Group or Other                                                                                                 | typ_platce                                                                                                                          |
| DPHDP3 (VAT declaration), DPHKH1 (VAT control statement) | **\<TaxpayerLegalForm\>**    | Select the form of the taxpayer: Person or Organization                                                                                                   | typ_ds                                                                                                                              |
| DPHDP3 (VAT declaration)                                 | **\<ProRataCoef\>**          | Select the pro rata coefficient entered earlier                                                                                                           | koef_p20_nov                                                                                                                        |
| DPHDP3 (VAT declaration), DPHKH1 (VAT control statement) | **\<NullDeclaration\>**      | Select No, which is the default value, whether you submit Null declaration. You should be able to change this default value during declaration processing | VAT declaration: Trans = “N”, if Yes = “A”, if No VAT control statement: vyzva_odp = “B”, if Yes                                    |

3.  Set up parameters in Populate records

    3.1  Go to **Tax** > **Setup** > **Electronic messages** > **Populate records actions**. On the **Populate records action** page, select the
        line and select **Edit query.** Specify filter on settlement period(s)
        to be included in the report.

    3.2  If you need to report tax transactions from other settlement periods in
        a different declaration, create new Populate records action,
        and select appropriate settlement period(s).

## Configure system parameters and master records

You should do the following settings prior to generating VAT declaration:

<table>
<tbody>
<tr>
<td width="387">
<p><strong>Page</strong></p>
</td>
<td width="567">
<p><strong>Description</strong></p>
</td>
</tr>
<tr>
<td width="387">
<p><strong>Legal entities</strong> (Go to<strong> Organization administration &gt; Organizations &gt; Legal entities</strong>)</p>
</td>
<td width="567">
<p><strong>Click Registration IDs</strong>. Set up Tax registration number of the company.</p>
<p>&nbsp;</p>
<p>It should be setup for <strong>Tax registration type</strong> that is assigned to Tax registration category <strong>VAT ID</strong>.</p>
<p>Find more details in <a href="https://docs.microsoft.com/dynamics365/finance/localizations/tasks/eur-00015-vat-id">Set up VAT ID</a>.</p>
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="387">
<p><strong>Legal entities</strong></p>
<p>&nbsp;</p>
</td>
<td width="567">
<p>On the <strong>Addresses</strong> FastTab, define the primary address for the legal entity.</p>
<p>On the Contact information FastTab, define <strong>Phone</strong> and <strong>Email address. </strong>Set them to <strong>Primary.</strong></p>
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="387">
<p><strong>Tax Authorities</strong></p>
</td>
<td width="567">
<p>Go to <strong>Tax &gt; Indirect taxes &gt; Sales tax &gt; Sales tax authorities</strong>. Create the tax authority where the tax declaration is provided. Enter the tax authority code in the field <strong>Authority identification</strong>.</p>
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="387">
<p><strong>All customers (Go to Accounts receivable &gt; Customers &gt; All customers)</strong></p>
<p><strong>All vendors (Go to Accounts payable &gt; Vendors &gt; All vendors)</strong></p>
<p>&nbsp;</p>
</td>
<td width="567">
<p>Set up Vat IDs for customers and vendors.</p>
<p>Find more details in <a href="https://docs.microsoft.com/dynamics365/finance/localizations/tasks/eur-00015-registration-vendor-vat-id">Registration of vendor VAT ID</a></p>
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="387">
<p><strong>General ledger parameters </strong>(Go to <strong>General ledger &gt; Setup &gt; Ledger setup &gt; General ledger parameters</strong>)</p>
</td>
<td width="567">
<p>On the tab <strong>Sales tax</strong>, FastTab <strong>Tax options</strong>, in the <strong>Electronic reporting</strong> group of fields, in the <strong>VAT statement format mapping</strong> field, select <strong>VAT declaration Excel (CZ)</strong> format.</p>
<p>This format will be printed when you run <strong>Report sales tax for settlement period</strong>. Also this format will be printed when you click <strong>Print</strong> in <strong>Sales tax payments</strong> page.</p>
<p>Find more details in the sections below.</p>
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="387">
<p><strong>General ledger parameters</strong></p>
</td>
<td width="567">
<p>On the <strong>Sales tax tab</strong>, <strong>Tax options</strong> FastTab, in the <strong>Special report </strong>group of fields, select<strong> Yes </strong>in the<strong> Date of VAT register </strong>field.</p>
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="387">
<p><strong>General ledger parameters</strong></p>
</td>
<td width="567">
<p>On the tab <strong>Sales tax</strong>, on the <strong>VAT statement</strong> FastTab, you can define some parameters of the company:</p>
<p><strong>Taxpayer status</strong> - select <strong>Taxpayer</strong>, <strong>Group</strong>, or<strong> Other</strong></p>
<p><strong>Taxpayer type</strong> - select <strong>Individual</strong>, or <strong>Corporation</strong></p>
<p><strong>Main economic activity</strong> - Enter the code</p>
<p><strong>Factor </strong>- Enter the pro rata coefficient applied during the year.</p>
<p>&nbsp;</p>
<p>Note that you can configure the same information about the company in <strong>Additional fields </strong>of<strong> Electronic messages.</strong></p>
<p>When you run the declaration, you&rsquo;ll be able to select the source of information about the company in the field <strong>Tax Jurisdiction</strong>: local fields described below that are available for the legal entity in CZE country\region only (select <strong>The Czech Republic</strong>) or Electronic message additional fields (select <strong>Default</strong>).</p>
<p>&nbsp;</p>
</td>
</tr>
</tbody>
</table>

## Set up reverse charge item groups

Refer to the topic [Reverse charge VAT](https://docs.microsoft.com/dynamics365/finance/localizations/emea-reverse-charge)
to find all details about how to set up and use reverse charges functionality.

1.  Go to **Tax > Setup > Sales tax > Reverse charge item groups**. Create the new group.

2.  On the **Setup** FastTab, in the **Sales/purchase field**, select **Purchase.** Create a line and define Item code, Item group or Procurement category code that purchase is associated to the created reverse charge item group: 
  2.1 In the field **Item code** select **Table**, **Group** or **Category**.
  2.2 In the field **Item relation**, select item code or item group.
  2.3 In the field **Category**, select procurement category.

3.  On the **Setup** FastTab, in the **Sales/purchase field**, select **Sales** and associate the item, item group and procurement category as described above.

## Generate VAT declaration

### Generate VAT declaration from Electronic messages.

The processing steps described below are applicable to the example, Electronic
message processing, that's available from LCS.

1.  To generate the VAT declaration XML file, go to **Tax > Inquiries and reports > Electronic messages > Electronic messages**.

2.  In the left pane, select the report format to generate. For example,
    select **DPHDP3**.

3.  On the **Messages** FastTab, select **New**, and then in the **Run processing** dialog box, select **OK**.

4.  Select the message line that was created. Enter a **Description** and
    specify the **Start date** and **End date** for the declaration.

5.  On the **Messages** FastTab, select **Collect data**, select **OK**.

    On the **Message items** FastTab, review the s ales tax payments that aretransferred for processing. The sales tax payments of the selected period that were not included in any other message of the same processing are included by default.

    Click **Original document** to review sales tax payment.

    Click **Delete** to exclude sales tax payments from processing. Note, that this step is optional. If you skip this step, you can still 
    generate VAT declaration using the **Tax declaration version** parameter on the
    declaration dialog. This is explained further later in this topic.

6.  On the **Message additional fields** FastTab, validate the value of the
    field \<**NullDeclaration\>**. Select **Yes** if you are reporting the null
    declaration.

7.  On the **Messages** FastTab, select **Update status**. In the **Update status** dialog, select **Ready to generate** action. Select **OK**.
    Validate that the message status has changed to **Ready to generate**.

8.  On the **Messages** FastTab, select **Generate report**. Then, to preview
    VAT declaration amounts, select **Preview DPHDP3 in Excel** in the **Run processing** dialog box,
    and then click **OK**. In the **Electronic reporting parameters** dialog box, enter parameters of the VAT declaration. The details of available parameters are listed and described later in this topic.

9.  Select **OK**. When you generate an Excel file with VAT declaration preview,
    select the **Attachments** button (the paper clip symbol) in the upper-right
    corner of the page. Then select **Open** to open the file. Review the amounts that are in the
    Excel document.

10.  On the **Messages** FastTab, select **Generate report**. Then, in the **Run
    processing** dialog box, select **Generate DPHDP3** to generate an XML file and
    click **OK**.

11.  In the **Electronic reporting parameters** dialog box, enter the following
    information:

<table width="973">
<thead>
<tr>
<td width="255">
<p><strong>Field</strong></p>
</td>
<td width="718">
<p><strong>Description</strong></p>
</td>
</tr>
</thead>
<tbody>
<tr>
<td width="255">
<p>Tax settlement period</p>
</td>
<td width="718">
<p>If you run <strong>Collect data</strong> above, skip this step. Otherwise, select the applicable settlement period.</p>
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="255">
<p>Tax declaration version</p>
</td>
<td width="718">
<p>If you run <strong>Collect data</strong> above, skip this step. Report will be generated for sales tax transactions included in the collected sales tax payments.</p>
<p>Otherwise, select one of the following values:</p>
<p>&middot;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <strong>Original</strong>&nbsp;&ndash; Generate a report for sales tax transactions of the original sales tax payment, or before the sales tax payment is generated (<strong>Sales tax payment version</strong> has value <strong>Original</strong>).</p>
<p>&middot;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <strong>Corrections</strong>&nbsp;&ndash; Generate a report for sales tax transactions of all the subsequent sales tax payments for the period (<strong>Sales tax payment version</strong> has value <strong>Latest corrections</strong>).</p>
<p>&middot;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <strong>Total list</strong>&nbsp;&ndash; Generate a report for all sales tax transactions for the period, including the original and all corrections.</p>
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="255">
<p>Tax Jurisdiction</p>
</td>
<td width="718">
<p>Select <strong>Default</strong> to take information about the company from <strong>Additional fields</strong> of <strong>Electronic messages</strong>.</p>
<p>Select The Czech Republic to take information about the company from the local Czech fields in <strong>General ledger parameters</strong> page.</p>
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="255">
<p>Contact person</p>
</td>
<td width="718">
<p>Select the employee who has created the report. Name, surname and phone of this employee will be exported to XML file.</p>
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="255">
<p>Signatory</p>
</td>
<td width="718">
<p>Select employee who has signed the report. Name, surname and position of this employee in the company will be exported to XML file.</p>
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="255">
<p>Correction reason date</p>
</td>
<td width="718">
<p>Enter date on which the reason for submitting supplementary declaration was observed. Applicable for Supplementary and Supplementary/corrective declarations.</p>
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="255">
<p>New pro rata coefficient</p>
</td>
<td width="718">
<p>For December declaration, enter new pro rata coefficient which you have calculated based on annual data.</p>
<p>This value will be exported to Row 53 if the declaration.</p>
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="255">
<p>Next year report periodicity</p>
</td>
<td width="718">
<p>For December declaration specify periodicity of declaration for the next year of this is different from the current periodicity.</p>
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="255">
<p>Value of exempt sales not included in calculation of coefficient,</p>
<p>Value of taxable sales not included in calculation of coefficient</p>
</td>
<td width="718">
<p>For December declaration specify amounts of exempt and taxable sales respectively that are not included in calculation of new coefficient if your company had such sales during the year.</p>
<p>These amounts will be exported to Row 51 of the declaration.</p>
</td>
</tr>
<tr>
<td width="255">
<p>Value of annual settlement of tax deduction</p>
</td>
<td width="718">
<p>For December declaration specify amount of annual tax deduction adjustment due to applying of the new pro rata coefficient.</p>
<p>This amount will be exported to Row 53 of the declaration.</p>
<p>&nbsp;</p>
</td>
</tr>
</tbody>
</table>

12.  Select **OK**. When the declaration in XML is generated, the status of the
    message will change to **Generated**.

[![Electronic messages](media/PicEM.jpg)](media/PicEM.jpg)

  If an error occurs while the report is being generated, the status of the message is changed to **Technical error**.

13.  Select the **Attachments** button (the paper clip symbol) in the upper-right
    corner of the page. Then select **Open** to open the file.

14.  Review the file and if this is ok, update the status to **Approved** to
    finish the processing. Select **Update status**, and then, in the **Update
    status** dialog box, select **Approve**, and then **OK**.

   If it's necessary to delete a message, you can select action **Allow delete**, and then select **OK**. Now you can delete the message.

   If the message status is **Technical error**, you can update the message status to one of initial statuses: **Created** or **Ready to generate**.

15.  On the **Action log** FastTab, review all user actions for the current
    message.

16.  When you've finished generating the VAT declaration, send
    the generated file to the tax authority manually.

## Generate VAT control statement from Electronic messages.

1.  To generate the VAT control statement XML file, go to **Tax > Inquiries and reports > Electronic messages > Electronic messages**.

2.  In the left pane, select the report format to generate. For example,
    select **DPHKH1**.

3.  Follow steps 3-7 of previous procedure to create the message and update the
    status to **Ready to generate**.

4.  On the **Messages** FastTab, select **Generate report**. Then, in the **Run processing** dialog box, select **Generate DPHKH1** to generate the XML file, and
    click **OK**.

5.  In the **Electronic reporting parameters** dialog box, enter the following information:

| **Field**                                                                                                           | **Description**                                                                                                     |
|---------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| Tax settlement period, Tax declaration version, Contact person, Signatory, Correction reason date, Declaration type | Define values in the same way as described in the paragraph above for VAT declaration                               |
| Reference number                                                                                                    | Enter reference number if applicable                                                                                |
| Threshold                                                                                                           | Enter threshold amount to split documents between sections A4/A5 and B2/B3. For example, for year 2020 enter 10000. |

## Generate VAT declaration in Excel from Inquiries and reports menu item.

1. Go to **Tax > Periodic tasks > Declarations > Sales tax > Report sales tax for settlement period**. In the **Report sales tax for settlement period** dialog, select the following:

<table width="973">
<thead>
<tr>
<td width="255">
<p><strong>Field</strong></p>
</td>
<td width="718">
<p><strong>Description</strong></p>
</td>
</tr>
</thead>
<tbody>
<tr>
<td width="255">
<p>Settlement period</p>
<p>&nbsp;</p>
</td>
<td width="718">
<p>Select the settlement period</p>
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="255">
<p>Sales tax payment version</p>
</td>
<td width="718">
<p>Select the following:</p>
<p>&middot;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <strong>Original</strong>&nbsp;&ndash; Generate a report for sales tax transactions of the original sales tax payment, or before the sales tax payment is generated (<strong>Sales tax payment version</strong> has value <strong>Original</strong>).</p>
<p>&middot;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <strong>Corrections</strong>&nbsp;&ndash; Generate a report for sales tax transactions of all the subsequent sales tax payments for the period (<strong>Sales tax payment version</strong> has value <strong>Latest corrections</strong>).</p>
<p>&middot;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <strong>Total list</strong>&nbsp;&ndash; Generate a report for all sales tax transactions for the period, including the original and all corrections.</p>
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="255">
<p>From date</p>
</td>
<td width="718">
<p>Select the first date of the reporting period</p>
<p>&nbsp;</p>
</td>
</tr>
</tbody>
</table>

2.  Select **OK**, and review the Excel file that was generated.

## Generate VAT declaration in Excel from Sales tax payments

1. Go to **Tax \> Periodic tasks > Declarations > Sales tax > Settle and post sales tax.** In the **Settle and post sales tax** dialog, define the following:

<table width="973">
<thead>
<tr>
<td width="255">
<p><strong>Field</strong></p>
</td>
<td width="718">
<p><strong>Description</strong></p>
</td>
</tr>
</thead>
<tbody>
<tr>
<td width="255">
<p>Settlement period</p>
<p>&nbsp;</p>
</td>
<td width="718">
<p>Select the settlement period</p>
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="255">
<p>Sales tax payment version</p>
</td>
<td width="718">
<p>Select the following:</p>
<p>&middot;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <strong>Original</strong>&nbsp;&ndash; Generate original sales tax payment for settlement period.</p>
<p>&middot;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <strong>Latest corrections</strong>&nbsp;&ndash; Generate a correction sales tax payment after the original sales tax payment for the settlement period was created.</p>
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="255">
<p>From date</p>
</td>
<td width="718">
<p>Select the first date of the reporting period</p>
<p>&nbsp;</p>
</td>
</tr>
</tbody>
</table>

2. Select **OK**. Go to **Tax > Inquiries and reports > Sales tax inquiries > Sales tax payments**. Review generated sales tax payment line.

## Set up to run VAT declaration for several legal entities

To use the formats to report the VAT declaration for a group of several legal
entities, you should first set up Application specific parameters of the ER
formats for each of the legal entities.

## Set up Electronic messages to collect data from several legal entities

1.  Turn on the **Cross-company queries for the populate records actions** feature in Feature management. Go to **Workspaces** > **Feature management**, find **Cross-company queries for the populate records actions** in the list, and then select **Enable now** in the lower right area of the page.

2.  Go to **Tax** > **Setup** > **Electronic messages** > **Populate records actions**. On the **Populate records action** page, a new **Company** field
    is available in the **Datasources setup** grid. For existing records, this field shows the identifier of the current legal entity.

3.  In the **Datasources setup** grid, add a line for each additional legal entity that must be included in reporting. Set up the following fields.

| **Field name**         | **Value**                                                                                                                          |
|------------------------|------------------------------------------------------------------------------------------------------------------------------------|
| Name                   | Enter a text value that will help you understand where this record comes from. For example, enter **VAT payment of Subsidiary 1**. |
| Message item type      | Select **VAT return**. This value is the only value that is available for all the records.                                         |
| Account type           | Select **All**.                                                                                                                    |
| Master table name      | Specify **TaxReportVoucher** for all the records.                                                                                  |
| Document number field  | Specify **Voucher** for all the records.                                                                                           |
| Document date field    | Specify **TransDate** for all the records.                                                                                         |
| Document account field | Specify **TaxPeriod** for all the records.                                                                                         |
| Company                | Select the ID of the legal entity.                                                                                                 |
| User query             | The check box is automatically selected when you define criteria by using **Edit query** button.                                   |

4.  For each new line, select **Edit query**, and specify a related settlement
    period for the legal entity that is specified in the **Company** field on
    the line.

5.  As result of this setup, **Collect data** function on **Electronic
    message**s page will collect sales tax payments from all legal entities that
    you define here.

## Generate VAT declaration for several legal entities

The following are preconditions for running this procedure:

1.  The field **Date of VAT register** on **General ledger parameters** page,
    **Sales tax** tab, has the same value for all legal entities for which you
    collect data.

2.  Sales tax payment is posted for the reporting period in all legal entities.

    To generate a VAT declaration for multiple legal entities, complete the following steps:

3.  Go to **Tax > Inquiries and reports > Electronic messages > Electronic messages**.

4.  In the left pane, select the report format to generate. For example,
    select **DPHDP3**.

5.  On the **Messages** FastTab, select **New**. Then, in the **Run processing** dialog box, select **OK**.

6.  Select the message line that was created. Enter a **Description** and
    specify the **Start date** and **End date** for the declaration.

7.  On the **Messages** FastTab, select **Collect data**, select **OK**.

    On the **Message items** FastTab, review the Sales tax payments that are
    transferred for processing. Value in the field **Company** indicates the
    legal entity where Sales tax payment is processed.

    Click **Original document** to review sales tax payment.

    Click **Delete** to exclude some sales tax payments from processing

8.  Process the declaration in standard way. When the file is generated, review and verify that
    the report contains all the tax transactions that included in the selected sales tax
    payments.

## How to attach a File or a Note to the VAT declaration

Complete the following steps to attach a file or a note to the VAT declaration XML file.

Attached text notes will be exported to **VetaR** sections of the VAT
declaration XML file.

Attached files will be exported as Base64 binary file attachments to the **Prilohy** XML element.

1.  Go to **Organization administration > Document management > Active document tables**. In the **Table name** select **Sales tax payment**.

2.  Go to **Tax > Inquiries and reports > Sales tax inquiries > Sales tax payments**. Select a line with sales tax payment and click the the paperclip 
    link in the upper right corner.

3.  In the opened page **Attachments for Sales tax payments**, select **New > File** and add a file attachment.

4.  Select **New > Note** and enter information in the **Description** and **Notes** fields.

## How to post VAT adjustment for bad debts

### Write off customer bad debts using Write off function

Follow the example steps to write off customer bad debts:

1.  Create a customer on the **All customers** page.

2.  Create and post a free text invoice on the **All free text invoices** page.

3.  Create a sales tax code WRITEOFF21 on **Sales tax codes** page, specifically
    for in writing off bad debts with 21% of the VAT rate.

4.  Go to **General ledger > Ledger setup > Journal setup > Journal names**.
    Create a general ledger journal “WriteOff”. Select **Journal type** =
    **Daily**.

5.  **Go to Accounts receivable > Setup > Account receivable parameters > Collections** tab **> Write-off** FastTab. Select the journal,
    “WriteOff” in the **Write-off journal** field. Set the **Separate sales tax** field to **Yes.**

6.  Go to **Accounts receivable > Customers > All customers**. Select the
    customer record created above. Select **Collections > Write off**. On the
    **Write off** dialog, enter the **Write-off date**, **Reason code** and
    **Description**, and click **OK**.

7.  Go to **General ledger > Journal entries > General journals**. Select the
    journal writeOff that was automatically generated. Select **Lines**. Review
    that tree lines were created:

    -   Account type **Customer** – on the total invoice amount including VAT
    -   Account type **Ledger** – on the invoice amount without VAT
    -   Account type **Ledger** – on the VAT amount.

8.  Select the line with VAT amount. Go to Tab **General**. Select sales tax code WRITEOFF21 created above in the field **Sales tax code**.

9.  Post the journal. Review posted sales tax transaction:

   -   **Sales tax direction** = **Sales tax payable**
   -   **Amount origin** is equal to invoice amount without VAT
   -   **Actual sales tax amount** is equal to VAT amount

10.  Go to **Electronic reporting** workspace, select configuration with VAT declaration format. Select **Configurations > Application specific parameters > Set up**. Create the following lines:

| **Lookup result**                     | **Tax code (Code)** | **Name**          |
|---------------------------------------|---------------------|-------------------|
| VATAdjustmentCustomerBadDebtsStandard | WRITEOFF19          | Sales             |
| VATAdjustmentCustomerBadDebtsStandard | WRITEOFF19          | Sales credit note |

### Write off vendor bad debts manually

Follow the example steps to write off vendor bad debts:

1.  Create a vendor on **All vendors** page.

2.  Create and post a vendor invoice on **Invoice journal** page.

3.  Review the settings of the sales tax code **WRITEOFF21** created above using the **Sales tax codes** page. Alternatively, you can create a new vendor before writing off     vendor bad debts.

4.  Create Sales tax group **WRITEOFF**. Add a line with sales tax code
    **WRITEOFF21** on the **Setup** FastTab.

5.  Go to **Items sales tax groups**. Select affected item sales tax group. Add a line with sales tax code WRITEOFF21 on the **Setup** FastTab.

6.  Go to the **Daily general journal** page, and create a line for writing off the vendor invoice manually. Enter information in the following fields:

    - Enter the **Date**
    - Select Vendor in the field **Account type**
    - Select vendor account created above in the field **Account**
    - Enter write off amount in the field **Debit**
    - On tab **General**, select Sales tax group **WRITEOFF,** and **Item sales tax group** selected in step 5 above

7.  Settle open vendor invoice in standard way and Post the journal. Then review the following items in the posted sales tax transaction:

    -   **Sales tax direction** = **Sales tax receivable**
    -   **Amount origin** is equal to invoice amount without VAT
    -   **Actual sales tax amount** is equal to VAT amount

8.  Go to the **Electronic reporting** workspace, select configuration with VAT declaration format. Select **Configurations > Application specific parameters > Set up**. Create the following lines:

| **Lookup result**                   | **Tax code (Code)** | **Name**             |
|-------------------------------------|---------------------|----------------------|
| VATAdjustmentVendorBadDebtsStandard | WRITEOFF19          | Purchase             |
| VATAdjustmentVendorBadDebtsStandard | WRITEOFF19          | Purchase credit note |

## How to post tax amount correction

Follow the example steps to post correction of VAT deduction (Row 45)

1.  Create a sales tax code **CORR** on **Sales tax codes** page, specifically for usage in correction of the VAT deduction that is reflected in Row 45 of VAT declaration

2.  Go to **General ledger > Journal entries > General journals**. Select the daily journal. Select **Lines**.

3.  Create the following journal line:

| **Date**       | **Account type**  | **Account**                                         | **Description**                       | **Debit**                                     | **Offset account type** | **Offset account**                                           |
|----------------|-------------------|-----------------------------------------------------|---------------------------------------|-----------------------------------------------|-------------------------|--------------------------------------------------------------|
| Enter the date | Select **Ledger** | Select **Ledger account** for posting VAT deduction | Enter description for the transaction | Enter amount in increase VAT deduction amount | Select **Ledger**       | Select **Ledger account** to offset posting of VAT deduction |

4.  Go to Tab **General**. Select sales tax code **CORR** created above in the field **Sales tax code**.

5.  Post the journal. Review posted sales tax transaction:

    -   **Sales tax direction** = **Sales tax receivable**
    -   **Amount origin** is equal to zero
    -   **Actual sales tax amount** is equal to Debit amount

6.  Go to **Electronic reporting** workspace, select configuration with VAT declaration format. Select **Configurations > Application specific parameters > Set up**. Create the following lines:

| **Lookup result**      | **Tax code (Code)** | **Name**             |
|------------------------|---------------------|----------------------|
| VATDeductionCorrection | CORR                | Purchase             |
| VATDeductionCorrection | CORR                | Purchase credit note |
