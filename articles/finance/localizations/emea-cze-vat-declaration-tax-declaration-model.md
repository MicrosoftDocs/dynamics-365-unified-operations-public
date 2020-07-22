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

| Row | Control statement section | Description                                                         | Rate     | Tax base (xml element) | Full tax deduction (xml element) | Tax deduction adjustment (xml   element) | Report field (lookup result)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|-----|---------------------------|---------------------------------------------------------------------|----------|------------------------|----------------------------------|------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 40  | B2/B3                     | From taxable purchases                                              | Standard | pln23                  | odp_taz23_nar                    | odp_tuz23                                | **Full   deduction**:<br>PurchaseVATDeductionStandard<br>AcquiredAssetsStandard   - VATAdjustmentVendorBadDebtsStandard<br><br>**Deduction   adjustment**:   PurchaseVATDeductionAdjustStandard<br>AcquiredAssetsAdjustStandard -   VATAdjustmentVendorBadDebtsAdjustStandard                                                                                                                                                                                                                                                                                                                        |
| 41  | B2/B3                     | From taxable purchases                                              | Reduced  | pln5                   | odp_tuz5_nar                     | odp_tuz5                                 | **Full   deduction**:<br>PurchaseVATDeductionReduced<br>PurchaseVATDeductionReduced2<br>AxquiredAssetsREduced   - VATAdjustmentVendorBadDebtsReduced -   VATAdjustmentVendorBadDebtsReduced2<br><br>**Deduction    adjustment**:<br>PurchaseVATDeductionAdjustReduced<br>PurchaseVATDeductionAdjustReduced2   - VATAdjustmentVendorBadDebtsAdjustReduced -   VATAdjustmentVendorBadDebtsAdjustReduced2<br>AcquiredAssetsAdjustReduced                                                                                                                                                                |
| 42  | N/A                       | From import fo goods when the   Tax authority is the customs office | N/A      | dov_cu                 | odp_cu_nar                       | odp_cu                                   | **Full   deduction**:<br>ImportVATDeductionTaxAdminCustomsOffice   <br><br>**Deduction   adjustment**:<br>ImportVATDeductionAdjustTaxAdminCustomsOffice                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| 43  | N/A                       | From taxable transactions   reported in rows 3 - 13                 | Standard | nar_zdp23              | od_zdp23                         | odkr_zdp23                               | **Full   deduction**:<br>VATDeductionFromPurchasesWithBATPayableStandard<br><br>EUPurchaseGoodsUseTaxStandard   (row 3)<br>EUPurchaseServicesUseTaxStandard (row   5)<br>ImportGoodsUseTaxStandard (row 7)<br>EUPurchaseNewTransportUseTax   (row 9)<br>DomesticPurchaseReverseChargeUseTaxStandard (row   10)<br>OtherPurchasesUseTaxStandard (row   12)<br><br>**Deduction   adjustment**:<br>VATDeductionAdjustFromPurchasesWithVATPayableStandard                                                                                                                                                |
| 44  | N/A                       | From taxable transactions   reporting in rows 3 - 13                | Reduced  | nar_zdp5               | od_zdp5                          | odkr_zdp5                                | **Full   deduction**:<br>VATDeductionFromPurchasesWithVATPayableReduced   <br><br>EUPurchaseGoodsUseTaxReduced (row   4)<br>EUPurchaseGoodsUseTaxReduced2 (row   4)<br>EUPurchaseServicesUseTaxReduced (row 6)<br>EUPrchaseServicesUseTaxReduced2   (row 6) <br>ImportGoodsUseTaxReduced (row   8)<br>DomesticPurchaseReverseChargeUseTaxReduced (row 11)   <br>DomesticPurchaseReverseChargeUseTaxReduced (row   11)<br>OtherPurchasesUseTaxReduced (row 13)<br>OtherPurchasesUseTaxReduced2   (row 13) <br><br>**Deduction   adjustment**:<br>VATDeductionAdjustFromPurchasesWithVATPayableReduced |
| 45  | N/A                       | Correction of tax deductions                                        | N/A      | N/A                    | odp_rez_nar                      | odp_rezim                                | **Full deduction**:<br>   VATDeductionCorrection <br><br>**Deduction   adjustment**:<br>VATDeductionAdjustCorrection                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| 46  | N/A                       | Total deduction<br> (40 +   41 + 42 + 43 + 44 + 45)                 | N/A      | N/A                    | odp_sum_nar                      | odp_sum_kr                               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| 47  | N/A                       | Value of acquired assets defined   in &sect; 4 para. d) ae)         | x        | nar_maj                | od_maj                           | odkr_maj                                 | Informative value. Included in   rows 40 and 41. <br><br> **Full deduction**:<br>   AcquiredAssetsSTandard<br>AcquiredAssetsREduced   <br><br>**Deduction   adjustment**:<br>AcquiredAssetsAdjustStandard<br>AxquiredAssetsAdjustReduced                                                                                                                                                                                                                                                                                                                                                             |

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

### <a name="sectiona1"></a>Section A1: Sale of goods and services under domestic reverse charges

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

For more information, see [Download Electronic reporting configurations from Lifecycle Services](../../dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

## Set up Application specific parameters for formats

### Set up parameters for declarations fields

To automatically generate VAT declaration, you should associate sales tax codes in the application and report fields in the Electronic reporting configuration.

1.  Go to **Workspaces** > **Electronic reporting** and select **Reporting configurations**.

2.  Select the configuration, **VAT declaration XML (CZ)** and then select **Configurations** > **Application specific parameters setup**.

3.  On the **Lookups** FastTab, select the lookup, **\$ReportFieldLookup**.

4.  On the **Conditions** FastTab, associate the sales tax codes and report fields:

</table>

| Column          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Lookup result   | Select the report field for   setup. For more information about the report fields and their assignment to   VAT declaration rows, see the [Vat declaration overview](#overview) section.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| Tax code (Code) | Select the sales tax code to   associate with the report field. Tax transactions that are posted with the   selected sales tax code will be collected in the respective report field.   <br> We recommend that you separate sales tax codes in a way that one sales   tax code generates amounts in only one report field.                                                                                                                                                                                                                                                                                                                                                                                                             |
| Name            | If you didn't create enough   sales tax codes to that one sales tax code generates amounts in only one   report field, you can set up a **Transaction classifier**. The following   transaction classifiers are available: <br> - **Purchase** <br> -   **PurchaseExempt** (tax exempt purchase) <br> -   **PurchaseReverseCharge** (tax receivable from a purchase reverse charge)   <br> - **Sales** <br> - **SalesExempt** (tax exempt sales)   <br> - **SalesReverseCharge** (tax payable from purchase reverse charge   or sales reverse charge) <br> - **Use tax**  <br><br> For each transaction   classifier, a classifier for the credit not is also available. For example,   **PurchaseCreditNote** (purchase credit note). |

To prevent the format from throwing an exception error message due to missed setup, create the following line in the parameters:

| **Lookup result** | **Tax code (Code)** | **Name**      |
|-------------------|---------------------|---------------|
| Other             | \*Not blank\*       | \*Not blank\* |

> [!NOTE]
> This line must be created as the last line in the parameters. If you create this line, make sure that you set up parameters for all sales tax codes in the system. If some sales tax codes are missing in the setup, tax transactions with those codes will not be collected for VAT declaration. If you don’t create this line, you’ll receive an error message when you run the report if there is tax transaction with the sales tax code that is not configured in the Application specific parameters.

5.  In the **State** field, select **Completed** and review the parameters.

[Application specific parameters page, Conditions list![Lookup for the Report fields](media/Pic1_ReportFieldLookup.png)](media/Pic1_ReportFieldLookup.png)

7.  On the Action Pane, click **Export** to export parameters to an XML file.

8.  Select the configuration **VAT declaration Excel (CZ**), and on the Action Pane, select **Import** to import the parameters that you configured for **VAT declaration XML (CZ)**. 

9. In the **State** field, select **Completed**.

10.  Select the **VAT control statement XML (CZ)** configuration, and then select the same settings that you did in step 4.

11. In the **State** field, select **Completed**.

### Set up parameters for subject codes 

To automatically classify the transaction to the subject code of reverse charge in VAT control statement sections A1 and B1, associate pairs of the reverse charge item groups and item sales tax groups in the application and then supply the codes to the Electronic reporting configuration.

1.  Go to **Workspaces** > **Electronic reporting** and select **Reporting configurations**.
2.  Select the **VAT control statement XML (CZ)** configuration and then select **Configurations** > **Application specific parameters setup**.
3.  On the **Lookups** FastTab, select **\$SubjectCodeLookup**.
4.  On the **Conditions** FastTab, associate **Reverse charge item groups** and subject codes:


| **Column**                          | **Description**                  |
|-------------------------------------|----------------------------------|
| Lookup result                       | Select the subject code. The full list of subject codes is available in the section, [Section A1: Sale of goods and services under domestic reverse charge](#sectiona1).                  |
| Reverse charge code (Code)          | Select the reverse charge item group that you associate with the selected subject code. For certain transactions, if you post incoming reverse charge transaction without reference to the product, you must associate the item sales tax group to the subject code. In this case, select \*Blank\* in this field. You must always have one line in the ** theApplication specific parameter** with **Lookup result** = **Other** and **Reverse charge code (Code)** = **\*Blank\*** to avoid generating an exception error when taking transactions without a reverse charge. This must be the last line in the setup. |
| Item sales tax group (TaxItemGroup) | Select the item sales tax group that's associated with the selected subject code. You must select a specific item sales tax group if you don't have an appropriate reverse charge item group that will post the incoming reverse charge transaction without reference to the product. For example, from the vendor invoice journal. Otherwise, for all lines you can select **\*Not blank\*** in this column.                                                                                                                                                                                                          |

To prevent the format from failing with an exception due to missed setup, set up the following line as the last lines:

| **Lookup result** | **Reverse charge code (Code)** | **Item sales tax group (TaxItemGroup)** | **Comment**                    |
|-------------------|--------------------------------|-----------------------------------------|--------------------------------|
| Other             | \*Blank\*                      | \*Not blank\*                           | This line must be set up to prevent an error message from being generated for transactions without a reverse charge code. |



[![Lookup for the Subject code](media/Pic2_SubjectCodeLookup.png)](media/Pic2_SubjectCodeLookup.png)

## Set up parameters for fulfillment mode codes

To automatically classify the transaction to the fulfillment mode code in the VAT control statement section A4, associate sales tax codes in the application and fulfillment subjects mode codes in the Electronic reporting configuration.

1.  Go to **Workspaces** > **Electronic reporting** and select **Reporting configurations**.

2.  Select the **VAT control statement XML (CZ)** configuration, and then select **Configurations** > **Application specific parameters setup**.

3.  On the **Lookups** FastTab, select **\$FulfillmentModeCodeLookup**.

4.  On the **Conditions** FastTab, associate the sales tax codes and fulfillment subjects mode codes as follows:

| **Column**      | **Description**                                                                                                                                                                                                                                                                                                    |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Lookup result   | Select a fulfillment code. The full list of codes is available in the section, [Section A4. Taxable sales with amount above 10 000 including VAT and all VAT adjustments made for customer bad debts](#sectiona4). |
| Tax code (Code) | Select the sales tax code.                                                                                                                                                                                                                                                                                              |

If you have transactions with only normal filling, you can create the following lines of the setting:

| **Lookup result** | **Tax code (Code)** |
|-------------------|---------------------|
| NormalFilling     | \*Not blank\*       |

Otherwise, set up the same line as the last line of the preceding setting to prevent the format from failing with an exception because of the missed setup.

### Set up parameters for no obligation to issue a tax document

To automatically classify the sales transaction to the condition that there was no obligation to issue tax document and therefore the transaction should be shown in Section A5 regardless of the threshold, associate pairs of the sales tax group and sales tax code from the application to a **Yes** or **No** condition in the Electronic reporting configuration.

1.  Go to **Workspaces** > **Electronic reporting** and select **Reporting configurations**.

2.  Select the **VAT control statement XML (CZ)** configuration and then select **Configurations** > **Application specific parameters setup**.

3.  On the **Lookups** FastTab, select **\$NoTaxDocument**.

4.  On the **Conditions** FastTab, associate sales tax groups and sales tax codes:

| **Column**      | **Description**                 |
|-----------------|---------------------------------|
| Lookup result   | Select **Yes** if there is no obligation to issue a tax document. This would typically occur because the customer is not registered for VAT purposes.                                                                                  |
| Sales tax group | Select the sales tax group that you associate to the customer when there is no obligation to issue tax document to them. If you are going to determine the condition using sales tax code values, select **\*Not blank\*** here. |
| Tax code (Code) | Select the sales tax code assigned to the transaction if there is no obligation to issue a tax document. If you can determine conditions using a sales tax group only, select **\*Not blank\*** here.                                |

5.  To prevent the format from failing with an exception due to missed setup, create the following line as the last line in the setup:

| **Lookup result** | **Sales tax group (TaxGroup)** | **Tax code (Code)** |
|-------------------|--------------------------------|---------------------|
| No                | \*Not blank\*                  | \*Not blank\*       |

6. Review the parameters.

[![Lookup for no obligation to issue tax document](media/Pic3_NoTaxDocumentLookup.png)](media/Pic3_NoTaxDocumentLookup.png)

6.  Update the **State** field of all the parameters to **Completed**.

## Download and import the Data management package with example settings of Electronic messages

The data package with example settings contains Electronic message settings that are used to generate the VAT declaration and VAT control statement as well as to preview the VAT declaration in Excel. You can extend these settings or create your own. For more information about how to work with Electronic messaging and how to create your own settings, see [Electronic messaging](../general-ledger/electronic-messaging.md).


1.  In the LCS Shared asset library, select **Data package** as the asset type and then download the **CZ VAT EM declaration package** package. The downloaded file is named **CZ VAT declaration EM package.zip**.

2.  In the **Data management** workspace, select **Import**.

3.  In the **Job details** section, set the following values:

    -   In the **Name** field, enter a name for the job.

    -   In the **Data source format** field, select **Package**.

4.  In the **Upload data file** field, select **Upload**, and then select the **CZ VAT declaration EM package.zip** file that you downloaded.

5.  After the data entities are uploaded, select **Import**.

6.  Go to **Tax** > **Inquiries and reports** > **Electronic messages** > **Electronic messages** and validate the electronic message processings that you
    imported.

| **Processing**        | **Processing code** | **Description**                             |
|-----------------------|---------------------|---------------------------------------------|
| VAT declaration       | DPHDP3              | VAT declaration in the Czech Republic       |
| VAT control statement | DPHKH1              | VAT control statement in the Czech Republic |

## Configure Electronic messages

1. Go to **Tax** > **Setup** > **Electronic messages** > **Additional fields** and select the line with an additional field.
2. On the **Value** FastTab add the following respective values of the field:

| **Additional field**     | **Value**                                                                                                                                                                           |
|--------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **DataBoxID**            | Enter the company’s Data box ID.                                                                                                                                         |
| **MainEconomicActivity** | Enter the code of company’s main economic activity.                                                                                                                                  |
| **TaxAuthorityToFile**   | Enter the code of the tax authority to which the declaration file will be sent.                                                                                                      |
| **ProRataCoef**          | Enter the pro rata coefficient applied during the year. If you need to apply pro rata coefficient in the declaration, enter the decimal value between 0 and 1 with a comma separator. |

3. Go to **Tax** > **Setup** > **Electronic messages** > **Electronic message processing** and select the line with processing. 
4. Set up the default values for declarations parameters on the **Message additional fields** FastTab:

| **Processing**                                           | **Additional field**         | **Comment**                                                                                                                                               | **XML element**               |
|----------------------------------------------------------|------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| DPHKH1 (VAT control statement)                           | **\<DataBoxID\>**            | Select the Data box ID that was entered earlier.                                                                                                                        | id_dats                                                                                                                             |
| DPHDP3 (VAT declaration)                                 | **\<MainEconomicActivity\>** | Select main economic activity code entered earlier.                                                                                                        | c_okec                                                                                                                              |
| DPHDP3 (VAT declaration), DPHKH1 (VAT control statement) | **\<TaxAuthorityToFile\>**   | Select tax authority code entered earlier.                                                                                                                 | c_pracufo                                                                                                                           |
| DPHDP3 (VAT declaration), DPHKH1 (VAT control statement) | **\<ReportPeriodicity\>**    | Select the frequency of the declaration submission in the reporting year: Monthly or Quarterly.                                                          | Ctvrt – will be filled with the quarter number for Quarterly report Mesic – will be filled with the month number for Monthly report. |
| DPHDP3 (VAT declaration)                                 | **\<TaxpayerType\>**         | Select the taxpayer type: Taxpayer, Group, or Other.                                                                                                | typ_platce                                                                                                                          |
| DPHDP3 (VAT declaration), DPHKH1 (VAT control statement) | **\<TaxpayerLegalForm\>**    | Select the form of the taxpayer: Person or Organization.                                                                                                   | typ_ds                                                                                                                              |
| DPHDP3 (VAT declaration)                                 | **\<ProRataCoef\>**          | Select the pro rata coefficient entered earlier.                                                                                                           | koef_p20_nov                                                                                                                        |
| DPHDP3 (VAT declaration), DPHKH1 (VAT control statement) | **\<NullDeclaration\>**      | Select **No**, which is the default value, whether you submit Null declaration. You should be able to change this default value during declaration processing. | VAT declaration: Trans = “N”, if Yes = “A”, if No VAT control statement: vyzva_odp = “B”, if Yes.                                    |

6. Go to **Tax** > **Setup** > **Electronic messages** > **Populate records actions** and on the **Populate records action** page, select the line and then select **Edit query.** 
7. Use the filter to specify the settlement periods to be included in the report. 
8. If you need to report tax transactions from other settlement periods in a different declaration, create a new **Populate records** action, and select the appropriate settlement period(s).

## Configure system parameters and master records

You should complete the following settings prior to generating VAT declaration:

| Page                           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|--------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Legal entities                 | **Organization administration** > **Organizations** > **Legal entities** <br><br>The **Tax registration type** should be assigned to the tax registration category, **VAT ID**. <br>For more information, see [Set up VAT ID](tasks/eur-00015-vat-id.md).                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| Legal entities                 | On the **Addresses** FastTab, define the primary adress for the legal entity. <br>On the **Contact information** FastTab, in the **Phone** and **Email** fields, select **Primary**.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| Tax authorities                | **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax authorities**. <br><br>Create the tax authroity where the tax declaration is provided. Enter the tax authority code in the field, **Authority identification**.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| All customers <br> All vendors | **Accounts receivable** >   **Customers** > **All customers**<br>**Accounts payable** > **Vendors** > **All vendors**<br><br>Set up VAT ID's for customers and   vendors. <br>For more information, see [Registration of vendor VAT ID](tasks/eur-00015-registration-vendor-vat-id.md).                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| General leger parameters       | **General ledger** > **Setup** > **Ledger setup** > **General ledger parameters**<br><br>   On the **Sales tax** tab, on the **Tax options** FastTab, in the **VAT   statement format mapping** field, select **VAT declaration Excel (CZ)**.<br>This format will be printed when you run the report, **Report sales tax for settlement period**. This format will also print when   you select **Print** on the **Sales tax payments** page.                                                                                                                                                                                                                                                                                        |
| General leger parameters       | On the **Sales tax** tab, in the **Special report** field group, in the **Date of VAT register** field, select **Yes**.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| General leger parameters       | On the **Sales tax** tab, on the **VAT statement** FastTab, define the following parameters for the company:<br>- **Taxpayer status**<br>- **Taxpayer   type**<br>- **Main economic activity**<br>- **Factor**: Enter the   pro rata coefficient applied during the year. <br><br> You can   configure the same information about the company in the **Additional fields** of **Electronic messages**. <br><br>When you run the declaration,   you will be able to select the source of the information about the company in   the **Tax jurisdiction** field. For local fields that are available for the   legal entity in CZE, select **The Czech Republic**. For electronic message   additional fields, select **Default**. |

## Set up reverse charge item groups

For additional details about setting up and using reverse charge functionality, see [Reverse charge VAT](emea-reverse-charge.md).

1.  Go to **Tax** > **Setup** > **Sales tax** > **Reverse charge item groups** and create a new group.

2.  On the **Setup** FastTab, in the **Sales/purchase field**, select **Purchase.** 
3. Create a new line, and select an item code, item group, or Procurement category code to associate the purchase with the created reverse charge item group. 
4. In the **Item code** field, select **Table**, **Group** or **Category**.
5. In the **Item relation** field, select an item code or item group.
6. In the **Category** field, select a procurement category.
7. On the **Setup** FastTab, in the **Sales/purchase field**, select **Sales** and associate the item, item group and procurement category as described in steps 4-6.

## Generate a VAT declaration

### Generate a VAT declaration from Electronic messages

The following steps are applicable to the example, Electronic message processing, that's available from LCS.

1.  To generate the VAT declaration XML file, go to **Tax** > **Inquiries and reports** > **Electronic messages** > **Electronic messages**.

2.  In the left pane, select the report format to generate. For example, select **DPHDP3**.

3.  On the **Messages** FastTab, select **New**, and then in the **Run processing** dialog box, select **OK**.

4.  Select the message line that was created, enter a description, and then specify the start and end dates for the declaration.

5.  On the **Messages** FastTab, select **Collect data**, and then select **OK**.

6. On the **Message items** FastTab, review the sales tax payments that are transferred for processing. The sales tax payments of the selected period that were not included in any other message of the same processing are included by default.

7. Optional - Select **Original document** to review sales tax payment or select **Delete** to exclude sales tax payments from processing. If you skip this step, you can still  generate VAT declaration using the **Tax declaration version** parameter on the declaration dialog page.

8. On the **Message additional fields** FastTab, validate the value of the field \<**NullDeclaration\>** and select **Yes** if you are reporting the null declaration.

9. On the **Messages** FastTab, select **Update status** and the **Update status** dialog, select **Ready to generate** action, and then select **OK**. Validate that the message status has changed to **Ready to generate**.

10. Select **Generate report**, and then to preview theVAT declaration amounts, select **Preview DPHDP3 in Excel** on the **Run processing** dialog page, and then select **OK**. 

11. On the **Electronic reporting parameters** dialog page, enter the parameters of the VAT declaration and then select **OK**. The details of available parameters are listed and described later in this topic. 

12. When you generate an Excel file with VAT declaration preview, select **Attachments** in the upper-right corner of the page and then select **Open** to open the file. Review the amounts that are in the Excel document.

13.  On the **Messages** FastTab, select **Generate report** and on the **Run processing** dialog page, select **Generate DPHDP3** to generate an XML file, and then select **OK**.

14.  On the **Electronic reporting parameters** dialog box, enter the following information:

| Field                                                                                                                                            | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|--------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Tax settlement period                                                                                                                          | If you selected to run **Collect data** in step 5, skip this field. Otherwise, select the applicable   settlement period.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Tax   declaration version                                                                                                                        | If you selected to run **Collect   data** in step 5, skip this field. The report will be genreated for sales tax   transactions that are included in the collected sales tax payments.   <br> Otherwise, select one of the following values:<br>- **Original**: Generate a report for sales tax transactions of the original sales tax   payment or before the sales tax payment is generated (**Sales tax payment   version** has the value, **Original**).<br>- **Corrections**: Genreate   a report for sales tax transactions of all the subsequent sales tax payments for the period (**Sales tax payment version** has the value, **Lastest   corrections**). <br>- **Total list**: Generate a report for all sales   tax transactions for the period, icnluding the original and all corrections. |
| Tax jurisdiction                                                                                                                               | Select **Default** to use the  information about the company that is included in the **Additional fields**   of **Electronic messages**. <br><br> Select **The Czech Republic** to use the company information in the local Czech fields on the **General ledger parameters** page.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Contact   person                                                                                                                                 | Select the employee who create the report. The name, surna, and phone number of the employee will be exported to the xml file.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Signatory                                                                                                                                        | Select the employee who signed the report. The name, surname, and position of the employee within the company will be exported to the xml file.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Correction reason date                                                                                                                         | Enter the date when the reason for submitting the supplementary declaration occurred. This is applicable to supplementary and supplementary/corrective declarations.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| New pro rata coefficient                                                                                                                       | For December declaration, enter the new pro rata coefficient that you calculated based on the annual data.<br>This value will be exported to row 53 of the declaration.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Next year report periodicity                                                                                                                   | For December declaration,   specify periodicity of declaration for the next year if this is different rom the current periodicity.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| Value of exempt sales not included in calculation of coefficient <br><br>Value of taxable sales not included in claculation of coefficient | For December declaration,   specify the amounts of exempt and taxable sales respectively that are not included in the calculation of the new coefficient, if your company had these   sales during the year. <br>This amount will be exported to row 51 of the declaration.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| Value of annual settlement of tax deduction                                                                                                    | For December declaration,   specify the amount of annual tax deduction adjustment due to applying the new pro rata coefficient.<br>This amount will be exported to row 53 of the   declaration.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |

15.  Select **OK**. When the declaration in XML is generated, the status of the  message will change to **Generated**.

[![Electronic messages](media/PicEM.jpg)](media/PicEM.jpg)

  If an error occurs while the report is being generated, the status of the message is changed to **Technical error**.

16.  Select **Attachments** and then select **Open** to open the file. Review the file, and if it looks correct, update the status to **Approved**. 

17. Select **Update status**, and in the **Update status** dialog page, select **Approve**, and then select **OK**.

   If it's necessary to delete a message, you can select **Allow delete** and then **OK**.

   If the message status is **Technical error**, you can update the message status to one of initial statuses: **Created** or **Ready to generate**.

18.  On the **Action log** FastTab, review all user actions for the current message and when you've finished generating the VAT declaration, send the generated file to the tax authority manually.

## Generate the VAT control statement from Electronic messages

1.  To generate the VAT control statement XML file, go to **Tax** > **Inquiries and reports** > **Electronic messages** > **Electronic messages**.

2.  In the left pane, select the report format to generate. For example, select **DPHKH1**.

3.  Follow steps 3-9 of the previous procedure to create the message and update the status to **Ready to generate**.

4.  On the **Messages** FastTab, select **Generate report** and then on the **Run processing** dialog page, select **Generate DPHKH1** to generate the XML file.

5. Select **OK**.

6.  On the **Electronic reporting parameters** dialog page, enter the following information:

| **Field**                                                                                                           | **Description**                                                                                                     |
|---------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| Tax settlement period, Tax declaration version, Contact person, Signatory, Correction reason date, Declaration type | Define the values in the same way as described in the paragraph above for VAT declaration.                               |
| Reference number                                                                                                    | Enter the reference number if applicable.                                                                                |
| Threshold                                                                                                           | Enter the threshold amount to split documents between sections A4/A5 and B2/B3. For example, for year 2020 enter 10000. |

## Generate a VAT declaration in Excel from the Inquiries and reports menu item

1. Go to **Tax** > **Periodic tasks** > **Declarations** > **Sales tax** > **Report sales tax for settlement period** and select the following:

| Field                       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|-----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Settlement   period         | Select the settlement   period.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Sales   tax payment version | Select the following:<br>-   **Original**: Generate a report for sales tax transactions of the original   sales tax payment, or before the sales tax payment is generated (**Sales tax   payment version** has the value, **Original**). <br>- **Corrections**:   Generate a report for sales tax transactions of all the subsequent sales tax   payments for the period (**Sales tax payment version** has the value,   **Lastest corrections**).<br>- **Total list**: Generate a report for   all sales tax transactions for the period, including the original and all   corrections. |
| From   date                 | Select the first date of the   reporting period.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |

2.  Select **OK**, and review the Excel file that was generated.

## Generate VAT declaration in Excel from Sales tax payments

1. Go to **Tax** \> **Periodic tasks* > **Declarations** > **Sales tax** > **Settle and post sales tax** and define the following:

| Field                       | Description                                                                                                                                                                                                                                                           |
|-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Settlement   period         | Select the settlement   period.                                                                                                                                                                                                                                       |
| Sales   tax payment version | Select the following:<br>-   **Original**: Generate the original sales tax payment for the settlement   period. <br>- **Latest corrections**: Gerneate a correction sales tax   payment after the original sales tax payment for the settlement period was   created. |
| From   date                 | Select the first date of the   reporting period.                                                                                                                                                                                                                      |

2. Select **OK**. 

3. Go to **Tax** > **Inquiries and reports** > **Sales tax inquiries** > Sales tax payments** and review the generated sales tax payment line.

## Set up to run VAT declaration for several legal entities

To use the formats to report the VAT declaration for a group of several legal entities, you should first set up the Application specific parameters of the ER formats for each of the legal entities.

## Set up Electronic messages to collect data from several legal entities

1.  Turn on the **Cross-company queries for the populate records actions** feature in Feature management. Go to **Workspaces** > **Feature management**, find **Cross-company queries for the populate records actions** in the list, and then select **Enable now**.

2.  Go to **Tax** > **Setup** > **Electronic messages** > **Populate records actions** and on the **Populate records action** page, a new **Company** field
    is available in the **Datasources setup** grid. For existing records, this field shows the identifier of the current legal entity.

3.  In the **Datasources setup** grid, add a line for each additional legal entity that must be included in reporting. Set up the following fields.

| **Field name**         | **Value**                                                                                                                          |
|------------------------|------------------------------------------------------------------------------------------------------------------------------------|
| Name                   | Enter a text value that will help you understand where this record comes from. For example, enter **VAT payment of Subsidiary 1**. |
| Message item type      | Select **VAT return**. This is the only value that is available for all the records.                                         |
| Account type           | Select **All**.                                                                                                                    |
| Master table name      | Specify the **TaxReportVoucher** for all the records.                                                                                  |
| Document number field  | Specify the **Voucher** for all the records.                                                                                           |
| Document date field    | Specify the **TransDate** for all the records.                                                                                         |
| Document account field | Specify the **TaxPeriod** for all the records.                                                                                         |
| Company                | Select the ID of the legal entity.                                                                                                 |
| User query             | The check box is automatically selected when you define criteria by using **Edit query**.                                   |

4.  For each new line, select **Edit query**, and specify a related settlement period for the legal entity that is specified in the **Company** field on the line.

5.  As a result of this setup, the **Collect data** function on the **Electronic messages** page will collect sales tax payments from all legal entities that you define here.

## Generate VAT declaration for several legal entities

The following are preconditions for running this procedure:

- The **Date of VAT register** field on the **Sales tax** tab on the **General ledger parameters** page has the same value for all the legal entities for which you collect data.

- Sales tax payment is posted for the reporting period in all legal entities.

To generate a VAT declaration for multiple legal entities, complete the following steps:

1.  Go to **Tax** > **Inquiries and reports** > **Electronic messages** > **Electronic messages**.

2.  In the left pane, select the report format to generate. For example, select **DPHDP3**.

3.  On the **Messages** FastTab, select **New** and on the **Run processing** dialog page, select **OK**.

4.  Select the message line that was created, enter a description, and the specify the start and end dates for the declaration.

5.  On the **Messages** FastTab, select **Collect data** and then select **OK**.

6. On the **Message items** FastTab, review the Sales tax payments that are transferred for processing. The value in the **Company** field indicates the legal entity where sales tax payment is processed.

7. Click **Original document** to review sales tax payment.

8. Click **Delete** to exclude some sales tax payments from processing

9.  Process the declaration. When the file is generated, review and verify that the report contains all the tax transactions included in the selected sales tax payments.

## Attach a file or a note to the VAT declaration

Complete the following steps to attach a file or a note to the VAT declaration XML file.

Attached text notes will be exported to **VetaR** sections of the VAT declaration XML file.

Attached files will be exported as Base64 binary file attachments to the **Prilohy** XML element.

1.  Go to **Organization administration** > **Document management** > **Active document tables** and in the **Table name**, select **Sales tax payment**.

2.  Go to **Tax** > **Inquiries and reports** > **Sales tax inquiries** > **Sales tax payments**, select a line with a sales tax payment, and then select the **Attachements** icon in the upper right corner.

3.  On the **Attachments for Sales tax payments** page, select **New** > **File** and add a file attachment.

4.  Select **New** > **Note**, and enter information in the **Description** and **Notes** fields.

## Post VAT adjustment for bad debts

### Write off customer bad debts using Write off function

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

The following example provides the steps to write off vendor bad debts.

1.  Go to **Accounts payable** > **Vendors** > **All vendors** and create a new vendor record.

2.  Create and post a vendor invoice.

3. On the **Sales tax codes** page, review the settings of the sales tax code **WRITEOFF21**. Or, create a new vendor before writing off the vendor bad debts.

4.  Create the sales tax group **WRITEOFF** and on the **Setup** FastTab, add a line with sales tax code **WRITEOFF21**.

5.  Go to **Items sales tax groups** and select the appropriate item sales tax group. On the **Setup** FastTab, add a line with sales tax code **WRITEOFF21**.

6.  Go to the **Daily general journal** page, and create a line for writing off the vendor invoice manually. Enter information in the following fields:

    - **Date**
    - **Account type**: Select **Vendor** 
    - **Account**: Select the vendor account you just created 
    - **Debit**: Enter the write off amount
    - On tab **General**, select the sales tax group **WRITEOFF,** and **Item sales tax group** selected in step 5.

7.  Settle open vendor invoice and post the journal and then review the following items in the posted sales tax transaction:

    -   **Sales tax direction** = **Sales tax receivable**
    -   **Amount origin** is equal to invoice amount without VAT
    -   **Actual sales tax amount** is equal to VAT amount

8.  Go to the **Electronic reporting** workspace, and select the configuration with VAT declaration format. Select **Configurations** > **Application specific parameters** > **Set up**. Create the following lines:

| **Lookup result**                   | **Tax code (Code)** | **Name**             |
|-------------------------------------|---------------------|----------------------|
| VATAdjustmentVendorBadDebtsStandard | WRITEOFF19          | Purchase             |
| VATAdjustmentVendorBadDebtsStandard | WRITEOFF19          | Purchase credit note |

## Post a tax amount correction

The following example provides the steps to post a correction of VAT deduction (Row 45).

1.  Create the sales tax code **CORR** on **Sales tax codes** page. This code is specifically to use for corrections to the VAT deduction that is reflected in Row 45 of the VAT declaration.

2.  Go to **General ledger** > **Journal entries** > **General journals**. 

3. Select the daily journal, select **Lines** and then create the following journal line:

| **Date**       | **Account type**  | **Account**                                         | **Description**                       | **Debit**                                     | **Offset account type** | **Offset account**                                           |
|----------------|-------------------|-----------------------------------------------------|---------------------------------------|-----------------------------------------------|-------------------------|--------------------------------------------------------------|
| Enter the date | Select **Ledger** | Select **Ledger account** for posting VAT deduction. | Enter a description for the transaction. | Enter the increased VAT deduction amount. | Select **Ledger**       | Select **Ledger account** to offset the posting of the VAT deduction. |

4.  On the **General** tab, in the **Sales tax code** field, select the sales tax code **CORR** that you just created.

5.  Post the journal and then review the posted sales tax transaction:

    -   **Sales tax direction** = **Sales tax receivable**
    -   **Amount origin** is equal to zero
    -   **Actual sales tax amount** is equal to Debit amount

6.  Go to the **Electronic reporting** workspace and select the configuration with VAT declaration format. Select **Configurations** > **Application specific parameters** > **Set up** and create the following lines:

| **Lookup result**      | **Tax code (Code)** | **Name**             |
|------------------------|---------------------|----------------------|
| VATDeductionCorrection | CORR                | Purchase             |
| VATDeductionCorrection | CORR                | Purchase credit note |
