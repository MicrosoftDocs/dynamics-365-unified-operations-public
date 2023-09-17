---
title: VAT declaration (Belgium)
description: This article provides information about the VAT declaration for Belgium.
author: AdamTrukawka
ms.date: 06/02/2022
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Belgium
ms.author: atrukawk
ms.search.validFrom: 2019-01-04
ms.dyn365.ops.version: 10.0.1
ms.search.form: 
---

# VAT declaration (Belgium)

[!include [banner](../includes/banner.md)]


This article describes how to set up the value-added tax (VAT) declaration for Belgium in XML format, and how to preview the VAT declaration and sales and purchase transactions in Microsoft Excel.

To automatically generate the reports, first create enough sales tax codes to keep a separate VAT accounting for each box on the VAT declaration. Additionally, in the application-specific parameters of the Electronic reporting (ER) format for the VAT declaration, associate sales tax codes with the lookup result of the lookups for the boxes on the VAT declaration.

For Belgium, you must configure the following elements:

- Report field lookup
- Nature
- Advances that are related to intra-community acquisitions

For more information about how to set up application-specific parameters, see the [Set up application-specific parameters for VAT declaration fields](#set-up-application-specific-parameters-for-vat-declaration-fields) section later in this article.

In the following table, the "Lookup result" column shows the lookup result that is preconfigured for a specific VAT declaration row in the VAT declaration format. Use this information to correctly associate sales tax codes with the lookup result and then with the row of the VAT declaration.

## VAT declaration overview

The VAT declaration in Belgium contains the following information.

**SECTION II OUTGOING OPERATIONS**

You can use the following table to determine how a lookup result that is preconfigured in the format is associated with a VAT declaration box.

A lookup result might generate an amount in several boxes. Those boxes are shown in parentheses. For example, for the **01_SalesLowerReducedRate** lookup result, "(01/54)" indicates that the VAT base amount of the transaction is shown in box 01, and the VAT amount of the transaction is shown in box 54.

| Description   | Box | Lookup result of Report field lookup (VAT base)   |
|---------------|-----|---------------------------------------------------|
| A. Operations subject to a special regulation    | 00  | 00_ExemptSalesSpecialScheme    |
| B. Transactions for which the VAT is due by the declarant:              | &nbsp;    |   &nbsp;  |
| \- at the rate of 6 pc.     | 01  | 01_SalesLowerReducedRate (01/54)   |
| \- at the rate of 12 pc.    | 02  | 02_SalesHigherReducedRate (02/54)  |
| \- at the rate of 21 pc.    | 03  | 03_SalesStandardRate (03/54)       |
| C. Services for which the foreign VAT is due by the contracting partner | 44  | 44_ForeignSalesServicesReverseCharge  |
| D. Transactions for which the VAT is due by the contracting partner     | 45  | 45_SalesReverseCharge  |
| E. Exempt intra-Community supplies made in Belgium and ABC sales        | 46  | 46_EUSales  |
| F. Other exempt operations and other operations performed abroad        | 47  | 47_OtherExemptSales  |
| G. Amount of credit notes issued and negative corrections:              | &nbsp;    | &nbsp;     |
| \- with regard to the operations registered in grids 44 and 46          | 48  | **Lookup results for credit notes:** 48_ForeignSalesServicesReverseChargeCreditNoteCorr</br> 48_EUSalesCreditNoteCorr    |
| \- with regard to other operations of Section II    | 49  | **Lookup results for credit notes:** 49_ExemptSalesSpecialSchemeCreditNoteCorr</br> 49_SalesStandardRateCreditNote (49/64)</br> 49_SalesHigherReducedRateCreditNote (49/64)</br> 49_SalesLowerReducedRateCreditNote (49/64)</br> 49_SalesLowerReducedRateNegativeCorrection (49/62)</br> 49_SalesHigherReducedRateNegativeCorrection (49/62)</br> 49_SalesStandardRateNegativeCorrection (49/62)</br> 49_SalesReverseChargeCreditNoteCorr</br> 49_OtherExemptSalesCreditNoteCorr |

**SECTION III INCOMING OPERATIONS**

You can use the following table to determine how a lookup result that is preconfigured in the format is associated with a VAT declaration box.

A lookup result might generate an amount in several boxes, and the amounts might have different signs. Those boxes and signs are shown in parentheses. For example, for the **8185_PurchasesGoodsCreditNote** lookup result, "(-81 +85/63)" indicates that the VAT base amount of the transaction is shown in box 81 as a negative value and in box 85 as a positive value, and the VAT amount of the transaction is shown in box 63 as a positive value.

> [!NOTE]
> Boxes 81, 82, and 83 always contain the VAT base amount plus the amount of non-deductible VAT. Other boxes in this section contain the VAT base amount.

| Description    | Box | Lookup result of Report field lookup |
|----------------|-----|--------------------------------------|
| A. Amount of incoming operations taking into account the credit notes received and other corrections:</br>  \- goods, raw materials and consumables    | 81  | 81_PurchasesGoods (81/59)</br> 81_PurchasesGoodsRegularizations (-81 +61)</br> **Lookup result for credit notes:**</br> 8185_PurchasesGoodsCreditNote (-81 +85/63)</br> **Lookup results for use tax:**</br> 8681_EUPurchasesGoodsUseTax (86/81 55/59)</br> 8781_OtherPurchasesDomesticReverseChargeGoodsUseTax (87/81 56/59)</br> 8781_OtherPurchasesImportsDeferredTaxGoodsUseTax (87/81 57/59)</br> **Lookup results for credit notes with use tax:**</br> 868184_EUPurchasesGoodsCreditNoteUseTax (-86/81 +84/61/62)</br> 878185_OtherPurchasesDomesticReverseChargeGoodsCNUseTax (-87/81 +85/61/62)</br> 878185_OtherPurchasesImportsDeferredTaxGoodsCNUseTax (-87/81 +85/61/62)  |
| \- services and miscellaneous goods  | 82  | 82_PurchasesServicesMisc (82/59)</br>  82_PurchasesServicesRegularizations (-82 +61)</br> **Lookup result for credit notes:**</br> 8285_PurchasesServicesMiscCreditNote (-82 +85/63)</br> **Lookup results for use tax:**</br> 8682_EUPurchasesMiscUseTax (86/82 55/59)</br> 8782_OtherPurchasesDomesticReverseChargeMiscUseTax (87/82 56/59)</br> 8782_OtherPurchasesImportsDeferredTaxMiscUseTax (87/82 57/59)</br> 8882_EUPurchasesServicesUseTax (88/82 55/59)</br> **Lookup results for credit notes with use tax:**</br> 868284_EUPurchasesMiscCreditNoteUseTax (-86/82 +84/61/62)</br> 878285_OtherPurchasesDomesticReverseChargeMiscCNUseTax (-87/82 +85/61/62)</br> 878285_OtherPurchasesImportsDeferredTaxMiscCNUseTax (-87/82 +85/61/62)</br> 888284_EUPurchasesServicesCreditNoteUseTax (-88/82 +84/61/62)  |
| \- company assets   | 83  | 83_PurchasesCapitalGoods (83/59)</br>  83_PurchasesCapitalGoodsRegularizations (-83 +61)</br>  **Lookup result for credit notes:**</br>  8385_PurchasesCapitalGoodsCreditNote (-83 +85/63)</br>  **Lookup results for use tax:**</br>  8683_EUPurchasesCapitalGoodsUseTax (86/83 55/59)</br>  8783_OtherPurchasesDomesticReverseChargeCapitalGoodsUseTax (87/83 56/59) </br> 8783_OtherPurchasesImportsDeferredTaxCapitalGoodsUseTax (87/83 57/59)</br>  **Lookup results for credit notes with use tax:**</br>  868384_EUPurchasesCapitalGoodsCreditNoteUseTax (-86/83 +84/61/62)</br>  878385_OtherPurchasesDomesticReverseChargeCapitalGoodsUseTax (-87/83 +85/61/62) </br> 878385_OtherPurchasesImportsDeferredTaxCapitalGoodsUseTax (-87/83 +85/61/62)  |
| B. Amount of credit notes received and negative corrections:  |  &nbsp;   |  &nbsp;  |
| \- with regard to the operations registered in boxes 86 and 88   | 84  | **Lookup results for credit notes:**</br>  8684_EUPurchasesCreditNoteRC (-86 +84/62)</br>  8884_EUPurchasesServicesCreditNoteRC (-88 +84/62)</br>  **Lookup results for credit notes with use tax:**</br>  868184_EUPurchasesGoodsCreditNoteUseTax (-86/81 +84/61/62)</br>  868284_EUPurchasesMiscCreditNoteUseTax (-86/82 +84/61/62)</br>  868384_EUPurchasesCapitalGoodsCreditNoteUseTax (-86/83 +84/61/62)</br>  888284_EUPurchasesServicesCreditNoteUseTax (-88/82 +84/61/62)  |
| \- with regard to the other operations of Box III   | 85  | **Lookup results for credit notes:**</br>  8185_PurchasesGoodsCreditNote (-81 +85/63)</br>  8285_PurchasesServicesMiscCreditNote (-82 +85/63)</br>  8785_OtherPurchasesImportsDeferredTaxCreditNote (-87 +85/62)</br>  **Lookup results for credit notes with use tax:**</br>  878185_OtherPurchasesDomesticReverseChargeGoodsCNUseTax (-87/81 +85/61/62)</br>  878285_OtherPurchasesDomesticReverseChargeMiscCNUseTax (-87/82 +85/61/62)</br>  878385_OtherPurchasesDomesticReverseChargeCapitalGoodsUseTax (-87/83 +85/61/62)</br>  878185_OtherPurchasesImportsDeferredTaxGoodsCNUseTax (-87/81 +85/61/62)</br>  878285_OtherPurchasesImportsDeferredTaxMiscCNUseTax (-87/82 +85/61/62)</br>  878385_OtherPurchasesImportsDeferredTaxCapitalGoodsUseTax (-87/83 +85/61/62)   |
| C. Intra-Community acquisitions made in Belgium and ABC sales   | 86  | 86_EUPurchasesRC (86/55)</br>  **Lookup result for credit notes:**</br>  8684_EUPurchasesCreditNoteRC (-86 +84/62)</br>  **Lookup results for use tax:**</br>  8681_EUPurchasesGoodsUseTax (86/81 55/59)</br>  8682_EUPurchasesMiscUseTax (86/82 55/59)</br>  8683_EUPurchasesCapitalGoodsUseTax (86/83 55/59)</br>  **Lookup results for credit notes with use tax:** </br> 868184_EUPurchasesGoodsCreditNoteUseTax (-86/81 +84/61/62)</br>  868284_EUPurchasesMiscCreditNoteUseTax (-86/82 +84/61/62) </br> 868384_EUPurchasesCapitalGoodsCreditNoteUseTax (-86/83 +84/61/62)   |
| D. Other incoming operations for which the VAT is due by the declarant    | 87  | 87_OtherPurchasesDomesticReverseCharge (87/56) </br> 87_OtherPurchasesImportsDeferredTax (87/57)</br>  **Lookup results for credit notes:**</br>  8785_OtherPurchasesDomesticReverseChargeCreditNote (-87 +85/62) </br> 8785_OtherPurchasesImportsDeferredTaxCreditNote (-87 +85/62)</br>  **Lookup results for use tax:**</br>  8781_OtherPurchasesImportsDeferredTaxGoodsUseTax (87/81 57/59)</br>  8782_OtherPurchasesImportsDeferredTaxMiscUseTax (87/82 57/59)</br>  8783_OtherPurchasesImportsDeferredTaxCapitalGoodsUseTax (87/83 57/59) </br> 8781_OtherPurchasesDomesticReverseChargeGoodsUseTax (87/81 56/59)</br>  8782_OtherPurchasesDomesticReverseChargeMiscUseTax (87/82 56/59) </br> 8783_OtherPurchasesDomesticReverseChargeCapitalGoodsUseTax (87/83 56/59)</br>  **Lookup results for credit notes with use tax:** </br> 878185_OtherPurchasesImportsDeferredTaxGoodsCNUseTax (-87/81 +85/61/62)</br>  878285_OtherPurchasesImportsDeferredTaxMiscCNUseTax (-87/82 +85/61/62) </br> 878385_OtherPurchasesImportsDeferredTaxCapitalGoodsUseTax (-87/83 +85/61/62)</br>  878185_OtherPurchasesDomesticReverseChargeGoodsCNUseTax (-87/81 +85/61/62) </br> 878285_OtherPurchasesDomesticReverseChargeMiscCNUseTax (-87/82 +85/61/62)</br>  878385_OtherPurchasesDomesticReverseChargeCapitalGoodsUseTax (-87/83 +85/61/62) |
| E. Intra-Community services with reverse charge    | 88  | 88_EUPurchasesServicesRC (88/55)</br>  **Lookup result for credit notes:**</br>  8884_EUPurchasesServicesCreditNoteRC (-88 +84/62)</br>  **Lookup result for use tax:**</br>  8882_EUPurchasesServicesUseTax (88/82 55/59) </br> **Lookup result for credit notes with use tax:**</br>  888284_EUPurchasesServicesCreditNoteUseTax (-88/82 +84/61/62)    |

**SECTION IV TAX PAYABLE**

You can use the following table to determine how a lookup result that is preconfigured in the format is associated with a VAT declaration box.

| Description   | Box    | Lookup result of Report field lookup   |
|---------------|--------|----------------------------------------|
|A. VAT on the operations indicated in:</br>  \- the boxes 01, 02 and 03     | 54    | 01_SalesLowerReducedRate (01/54)</br> 02_SalesHigherReducedRate (02/54)</br> 03_SalesStandardRate (03/54)   |
| \- the boxes 86 and 88  | 55  | 86_EUPurchasesRC (86/55)</br> 88_EUPurchasesServicesRC (88/55)</br> **Lookup results for use tax:**</br> 8681_EUPurchasesGoodsUseTax (86/81 55/59)</br> 8682_EUPurchasesMiscUseTax (86/82 55/59)</br> 8882_EUPurchasesServicesUseTax (88/82 55/59) </br>8683_EUPurchasesCapitalGoodsUseTax (86/83 55/59) |
| \- box 87, with the exception of imports with reverse charge | 56   | 87_OtherPurchasesDomesticReverseCharge (87/56)</br> **Lookup results for use tax:** </br>8781_OtherPurchasesDomesticReverseChargeGoodsUseTax (87/81 56/59)</br> 8782_OtherPurchasesDomesticReverseChargeMiscUseTax (87/82 56/59) </br>8783_OtherPurchasesDomesticReverseChargeCapitalGoodsUseTax (87/83 56/59)  |
| B. VAT on imports with reverse charge  | 57   | 87_OtherPurchasesImportsDeferredTax (87/57)</br> **Lookup results for use tax:** </br>8781_OtherPurchasesImportsDeferredTaxGoodsUseTax (87/81 57/59)</br> 8782_OtherPurchasesImportsDeferredTaxMiscUseTax (87/82 57/59) </br>8783_OtherPurchasesImportsDeferredTaxCapitalGoodsUseTax (87/83 57/59)   |
| C. Various VAT regularizations in favor of the State   | 61   | 61_VATRegularizationsDue</br> 81_PurchasesGoodsRegularizations (-81 +61)</br> 82_PurchasesServicesRegularizations (-82 +61)</br> 83_PurchasesCapitalGoodsRegularizations (-83 +61)</br> **Lookup results for credit notes with use tax:** </br>868184_EUPurchasesGoodsCreditNoteUseTax (-86/81 +84/61/62)</br> 868284_EUPurchasesMiscCreditNoteUseTax (-86/82 +84/61/62)</br> 868384_EUPurchasesCapitalGoodsCreditNoteUseTax (-86/83 +84/61/62)</br> 878185_OtherPurchasesDomesticReverseChargeGoodsCNUseTax (-87/81 +85/61/62)</br> 878285_OtherPurchasesDomesticReverseChargeMiscCNUseTax (-87/82 +85/61/62)</br> 878385_OtherPurchasesDomesticReverseChargeCapitalGoodsUseTax (-87/83 +85/61/62) </br>878185_OtherPurchasesImportsDeferredTaxGoodsCNUseTax (-87/81 +85/61/62)</br> 878285_OtherPurchasesImportsDeferredTaxMiscCNUseTax (-87/82 +85/61/62) </br>878385_OtherPurchasesImportsDeferredTaxCapitalGoodsUseTax (-87/83 +85/61/62)</br> 888284_EUPurchasesServicesCreditNoteUseTax (-88/82 +84/61/62)</br> |
| D. Refundable VAT stated on credit notes received   | 63  | **Lookup results for credit notes:**</br> 8185_PurchasesGoodsCreditNote (-81 +85/63) </br>8285_PurchasesServicesMiscCreditNote (-82 +85/63)</br> 8385_PurchasesCapitalGoodsCreditNote (-83 +85/63)     |
| **Total of the boxes 54, 55, 56, 57, 61 and 63**    | **XX** | **54 + 55 + 56 + 57 + 61 + 63**    |

**SECTION V TAX DEDUCTIBLE**

You can use the following table to determine how a lookup result that is preconfigured in the format is associated with a VAT declaration box.

| Description  | Box    | Lookup result of Report field lookup  |
|--------------|--------|---------------------------------------|
| A. Deductible VAT  | 59  | 81_PurchasesGoods (81/59)</br> 82_PurchasesServicesMisc (82/59)</br> 83_PurchasesCapitalGoods (83/59)</br> **Lookup results for use tax:**</br> 8681_EUPurchasesGoodsUseTax (86/81 55/59)</br> 8682_EUPurchasesMiscUseTax (86/82 55/59) </br>8683_EUPurchasesCapitalGoodsUseTax (86/83 55/59)</br> 8781_OtherPurchasesDomesticReverseChargeGoodsUseTax (87/81 56/59) </br>8782_OtherPurchasesDomesticReverseChargeMiscUseTax (87/82 56/59)</br> 8783_OtherPurchasesDomesticReverseChargeCapitalGoodsUseTax (87/83 56/59) </br>8781_OtherPurchasesImportsDeferredTaxGoodsUseTax (87/81 57/59)</br> 8782_OtherPurchasesImportsDeferredTaxMiscUseTax (87/82 57/59) </br>8783_OtherPurchasesImportsDeferredTaxCapitalGoodsUseTax (87/83 57/59)</br> 8882_EUPurchasesServicesUseTax (88/82 55/59) |
| B. Various VAT regularizations in favor of the declarant | 62  | 62_VATRegularizationsDeduction</br> **Lookup results for credit notes and corrections:** </br>49_SalesLowerReducedRateNegativeCorrection (49/62)</br> 49_SalesHigherReducedRateNegativeCorrection (49/62)</br> 49_SalesStandardRateNegativeCorrection (49/62) </br>8684_EUPurchasesCreditNoteRC (-86 +84/62)</br> 8884_EUPurchasesServicesCreditNoteRC (-88 +84/62)</br> 8785_OtherPurchasesImportsDeferredTaxCreditNote (-87 +85/62) </br>8785_OtherPurchasesDomesticReverseChargeCreditNote (-87 +85/62)</br> 8884_EUPurchasesServicesCreditNoteRC (-88 +84/62)</br> **Lookup results for credit notes with use tax:**</br>868184_EUPurchasesGoodsCreditNoteUseTax (-86/81 +84/61/62)</br> 868284_EUPurchasesMiscCreditNoteUseTax (-86/82 +84/61/62) </br>868384_EUPurchasesCapitalGoodsCreditNoteUseTax (-86/83 +84/61/62)</br> 878185_OtherPurchasesDomesticReverseChargeGoodsCNUseTax (-87/81 +85/61/62) </br>878285_OtherPurchasesDomesticReverseChargeMiscCNUseTax (-87/82 +85/61/62)</br> 878385_OtherPurchasesDomesticReverseChargeCapitalGoodsUseTax (-87/83 +85/61/62)</br> 878185_OtherPurchasesImportsDeferredTaxGoodsCNUseTax (-87/81 +85/61/62)</br> 878285_OtherPurchasesImportsDeferredTaxMiscCNUseTax (-87/82 +85/61/62) </br>878385_OtherPurchasesImportsDeferredTaxCapitalGoodsUseTax (-87/83 +85/61/62)</br> 888284_EUPurchasesServicesCreditNoteUseTax (-88/82 +84/61/62) |
| C. VAT to be recovered stated on credit notes issued   | 64   | **Lookup results for credit notes:**</br> 49_SalesStandardRateCreditNote (49/64)</br> 49_SalesHigherReducedRateCreditNote (49/64)</br> 49_SalesLowerReducedRateCreditNote (49/64)  |
| **Total of the boxes 59, 62 and 64**    | **YY** | **59 + 62 + 64**  |

**SECTION VI BALANCE**

| Description                                           | Box | Calculation           |
|-------------------------------------------------------|-----|-----------------------|
| Only one of the two following boxes can be filled in: |     |                       |
| Tax due to the State: box XX - box YY                 | 71  | XX – YY, if XX \>= YY |
| Amounts owed by the State: box YY - box XX            | 72  | YY – XX, if YY \> XX  |

**SECTION VII DEPOSIT**

| Description  | Box | Calculation   |
|--------------|-----|---------------|
| Actual VAT due for the period from December 1 to December 20 in the monthly declaration, or for the period from October 1 to December 20 in the quarterly declaration | 91  | The **91 Deposit amount to be paid in December** input parameter in the user dialog box |

## Purchase reverse charge VAT

If you configure sales tax codes to post incoming reverse charge VAT by using use tax, associate your sales tax codes with the lookup result of **Report field lookup** that contains "UseTax" in the name.

Alternatively, you can configure two separate sales tax codes: one for VAT due and one for VAT deduction. Then associate each code with the corresponding lookup results of **Report field lookup**.

For example, for taxable intra-community acquisitions, you configure sales tax code **UT_S_EU** with use tax and associate it with the **8681_EUPurchasesGoodsUseTax (86/81 55/59)** lookup result of **Report field lookup**. In this case, tax amounts that use the **UT_S_EU** sales tax code are reflected in boxes 59 ("Deductible VAT") and 55 ("VAT on the operations indicated in the boxes 86, 88"). Tax bases are reflected in boxes 81 ("Amount of incoming operations: goods, raw materials and consumables") and 86 ("Intra-Community acquisitions made in Belgium and ABC sales").

Alternatively, you configure two sales tax codes:

- **VAT_S_EU**, which has a tax rate value of -25 percent
- **InVAT_S_EU**, which has a tax rate value of 25 percent

You then associate the codes with lookup results of **Report field lookup** in the following way:

- Associate **VAT_S_EU** with the **EUPurchaseStandard (86/55)** lookup result.
- Associate **InVAT_S_EU** with the **EUPurchaseStandardDeduction (81/59)** lookup result.

In this case, amounts that use the **VAT_S_EU** sales tax code are reflected in boxes 55 ("VAT on the operations indicated in the boxes 86, 88") and 86 ("Intra-Community acquisitions made in Belgium and ABC sales"). Amounts that use the **InVAT_S_EU** sales tax code are reflected in boxes 59 ("Deductible VAT") and 81 ("Amount of incoming operations: goods, raw materials and consumables").

For more information about how to configure reverse charge VAT, see [Reverse charges](emea-reverse-charge.md).

## Credit notes and negative corrections

In Belgium, amounts of credit notes and negative corrections are shown in separate boxes on the VAT declaration. Therefore, in the preceding tables, specific lookup results for **Report field lookup** are dedicated to credit notes and negative corrections.

**Example: Sales**

A sale of goods (Invoice 1) has a VAT base of 1,000.00 euros (EUR) and a VAT amount of 210.00 EUR. This sale can be shown in the following boxes:

- **Box 03 ("Transactions for which the VAT is due by the declarant: at the rate of 21 pc."):** 1,000.00
- **Box 54 ("VAT on the operations indicated in the boxes 01, 02 and 03"):** 210.00

A credit note (Credit note 1) that is issued or a negative correction for the preceding invoice has a VAT base of -300.00 EUR and a VAT amount of -63.00 EUR. This credit note or correction can be shown in the following boxes:

- **Box 49 ("Amount of credit notes issued and negative corrections with regard to other operations of Section II"):** 300.00
- **Box 64 ("VAT to be recovered stated on credit notes issued"):** 63.00

**Example: Purchases**

A purchase of goods (Invoice 2) has a VAT base of 1,000.00 EUR and a VAT amount of 210.00 EUR. This purchase can be shown in the following boxes:

- **Box 81 ("Amount of incoming operations taking into account the credit notes received and other corrections - goods, raw materials and consumables"):** 1,000.00
- **Box 59 ("Deductible VAT"):** 210.00

A credit note (Credit note 2) that is received or a negative correction for the preceding invoice has a VAT base of -400 EUR and a VAT amount of -84 EUR. This credit note or correction can be shown in the following boxes:

- **Box 81 ("Amount of incoming operations taking into account the credit notes received and other corrections - goods, raw materials and consumables"):** -400.00
- **Box 85 ("Amount of credit notes issued and negative corrections with regard to the other operations of Box III"):** 400.00
- **Box 63 ("Refundable VAT stated on credit notes received"):** 84.00

## Sales transaction and purchase transaction overview

In Belgium, you can generate a list of sales and purchase transactions.

The following examples show what these reports look like for the examples in the previous section.

**Example: Sales transactions**

| Document number | Box 03   | Box 54 | Box 49 | Box 64 |
|-----------------|----------|--------|--------|--------|
| Invoice 1       | 1,000.00 | 210.00 | 00.00  | 00.00  |
| Credit note 1   | 00.00    | 00.00  | 300.00 | 63.00  |

**Example: Purchases transactions**

| Document number | Box 81   | Box 59 | Box 85 | Box 63 |
|-----------------|----------|--------|--------|--------|
| Invoice 2       | 1,000.00 | 210.00 | 00.00  | 00.00  |
| Credit note 2   | \-400.00 | 00.00  | 400.00 | 84.00  |

## Set up a VAT declaration for Belgium

### Configure system parameters

To generate a VAT declaration, you must configure the enterprise tax number.

1. Go to **Organization administration** > **Organizations** > **Legal entities**.
2. Select the legal entity, and then select **Registration IDs**.
3. Select or create the address in Belgium, and then, on the **Registration ID** FastTab, select **Add**.
4. In the **Registration type** field, select the registration type that is dedicated to Belgium, and that uses the **Enterprise Id** registration category.
5. In the **Registration number** field, enter the tax number in the format *BTW BE 1234.567.890*.
6. On the **General** tab, in the **Effective** field, enter the date when the number becomes effective.

For more information about how to set up registration categories and registration types, see [Registration IDs](emea-registration-ids.md).

### Import ER configurations

- Open the **Electronic reporting** workspace, and import the following ER formats:
- VAT declaration XML (BE)
- VAT Declaration Excel (BE)

For more information, see [Download ER configurations from the Global repository of Configuration service](../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

### Set up application-specific parameters for VAT declaration fields

> [!NOTE]
> We recommend that you enable the **Use application specific parameters from previous versions of ER formats** feature in the **Feature management** workspace. When this feature is enabled, parameters that are configured for earlier versions of an ER format automatically become applicable for later versions of the same format. If this feature isn't enabled, you must explicitly configure application-specific parameters for each format version. The **Use application specific parameters from previous versions of ER formats** feature is available in the **Feature management** workspace as of Dynamics 365 Finance version 10.0.23. For more information about how to set up the parameters of an ER format for each legal entity, see [Set up the parameters of an ER format per legal entity](../../fin-ops-core/dev-itpro/analytics/er-app-specific-parameters-set-up.md).

To automatically generate a VAT declaration, associate sales tax codes in the application and lookup results in the ER configuration.

#### Set up application-specific parameters for Report field lookup

Follow these steps to define which sales tax codes generate which boxes on the VAT declaration.

1. Go to **Workspaces** > **Electronic reporting** and select **Reporting configurations**.
2.  Select the **VAT declaration XML (BE)** configuration, and then select **Configurations \> Application specific parameters setup**.
3.  On the **Application specific parameters** page, on the **Lookups** FastTab, select **Report field lookup**.
4.  On the **Conditions** FastTab, set the following fields to associate the sales tax codes and report fields.

    | Field     | Description   |
    |-----------|---------------|
    | Lookup result  | Select the value of the report field. For more information about the values and their assignment to VAT declaration rows, see the [VAT declaration overview](#vat-declaration-overview) section earlier in this article.  |
    | Tax code   | Select the sales tax code to associate with the report field. Posted tax transactions that use the selected sales tax code will be collected in the appropriate declaration box. We recommend that you separate sales tax codes in such a way that one sales tax code generates amounts in only one declaration box. |
    | Transaction classifier | Select a transaction classifier. The following transaction classifiers are available: </br> - **Purchase** (tax receivable) </br> - **PurchaseExempt** (tax-exempt purchase)  </br>- **PurchaseReverseCharge** (tax receivable from a purchase reverse charge)  </br> - **Sales** (tax payable) </br> -  **SalesExempt** (tax-exempt sale) </br>- **SalesReverseCharge** (tax payable from a purchase reverse charge) </br>- **Use tax** (use tax) </br> For each transaction classifier, a classifier for the credit note is also available. For example, one of these classifiers is **PurchaseCreditNote** (purchase credit note). Be sure to create two lines for each sales tax code: one that has the transaction classifier value and one that has the transaction classifier for the credit note value.  |

> [!NOTE]
> Associate all sales tax codes with lookup results. If any sales tax codes should not generate values on the VAT declaration, associate them with the **Other** lookup result. There is a value for the **Private** lookup result. If you associate a sales tax code with the **Private** lookup result, the transaction amount that has the selected sales tax code won't be shown in any box of the VAT declaration. Instead, it will be shown in the **Private** column of the **Purchase transactions** report. You can identify purchases that are used for private purposes only setting up a sales tax code with Non deductible % field set to 100 percent. If purchases are partially used for private purposes, you should have separate sales tax codes for normal use and private use.

##### Credit notes and negative corrections

> [!IMPORTANT]
> Any negative tax transaction is classified as a credit note in the **Transaction classifier** field. Before you set up application-specific parameters, carefully review all types of negative operations in the application that are related to credit notes, negative corrections, and cancellations. Before you post any operations, decide whether you must configure additional sales tax codes for all or some negative transactions, or whether the same sales tax codes that you use for invoices can be used for some negative transactions.

The following examples show how different setting affect the results on the VAT declaration.

**Scenario 1: An invoice and a negative invoice are posted by using the same sales tax code**

For this example, an invoice has a VAT base of 1,000.00 EUR and a VAT amount of 210.00 EUR. A negative invoice has a VAT base of -600.00 and a VAT amount of -126.00 EUR. Both are posted by using the **VAT_S** sales tax code.

**Case 1:** Lookup results are set up in the following way.

| Lookup result                  | Label                                                                                 | Line | Tax code | Transaction classifier |
|--------------------------------|---------------------------------------------------------------------------------------|------|----------|------------------------|
| 03_SalesStandardRate           | 03/54 Transactions subject to the rate of 21 %                                        | 1    | VAT_S    | Sales                  |
| 49_SalesStandardRateCreditNote | 49/64 Credit notes issued in respect of transactions subject to the rate of 21 % [03] | 2    | VAT_S    | SalesCreditNote        |

In this case, the VAT declaration will show the following results:

- **Box 03:** 1,000.00
- **Box 54:** 210.00
- **Box 49:** 600.00
- **Box 64:** 126.00

**Case 2:** Lookup results are set up in the following way.

| Lookup result | Label    | Line | Tax code | Transaction classifier |
|---------------|----------|------|----------|------------------------|
| 03_SalesStandardRate  | 03/54 Transactions subject to the rate of 21 %   | 1   | VAT_S   | Sales |
| 49_SalesStandardRateNegativeCorrection (49/62) | 49/62 Negative corrections in respect of transactions subject to the rate of 21 % [03] | 2  | VAT_S | SalesCreditNote  |

In this case, the VAT declaration will show the following results:

- **Box 03:** 1,000.00
- **Box 54:** 210.00
- **Box 49:** 600.00
- **Box 62:** 126.00

**Case 3:** Lookup results are set up in the following way.

| Lookup result        | Label                                          | Line | Tax code | Transaction classifier |
|----------------------|------------------------------------------------|------|----------|------------------------|
| 03_SalesStandardRate | 03/54 Transactions subject to the rate of 21 % | 1    | VAT_S    | Sales                  |
| 03_SalesStandardRate | 03/54 Transactions subject to the rate of 21 % | 2    | VAT_S    | SalesCreditNote        |

In this case, the VAT declaration will show the following results.

- **Box 03:** 400.00
- **Box 54:** 84.00

**Scenario 2: An invoice and one negative invoice are posted by using the same sales tax code, but another negative invoice is posted by using a specially defined sales tax code**

For this example, an invoice has a VAT base of 1,000.00 EUR and a VAT amount of 210.00 EUR. Negative invoice 1 has a VAT base of -600.00 and a VAT amount of -126.00 EUR. Negative invoice 2 has a VAT base of -100.00 and a VAT amount of -21.00.

The invoice and negative invoice 1 are posted by using the **VAT_S** sales tax code, but negative invoice 2 is posted by using a specially defined sales tax code, **VAT_S_CN**.

Lookup results are set up in the following way.

| Lookup result  | Label | Line | Tax code | Transaction classifier |
|----------------|-------|------|----------|------------------------|
| 03_SalesStandardRate | 03/54 Transactions subject to the rate of 21 %   | 1  | VAT_S  | Sales  |
| 49_SalesStandardRateNegativeCorrection (49/62) | 49/62 Negative corrections in respect of transactions subject to the rate of 21 % [03] | 2  | VAT_S | SalesCreditNote |
| 49_SalesStandardRateCreditNote | 49/64 Credit notes issued in respect of transactions subject to the rate of 21 % [03]  | 3  | VAT_S_CN | SalesCreditNote |

In this case, the VAT declaration will show the following results:

- **Box 03:** 1,000.00
- **Box 54:** 210.00
- **Box 49:** 700.00 (= 600.00 + 100.00)
- **Box 64:** 126.00
- **Box 62:** 21.00

#### Set up application-specific parameters for Advances related to Intra-community acquisitions

In Belgium, the **Outgoing operations** and **Incoming operations** reports include a column that should show the amount of advances that are related to intra-community acquisitions. You should have a separate sales tax code for these types of advances.

Follow these steps to define which sales tax codes generate the amount of advances that are related to intra-community acquisitions. These steps are a continuation of the steps in the [Set up application-specific parameters for Report field lookup](#set-up-application-specific-parameters-for-report-field-lookup) section.

1. On the **Application specific parameters** page, on the **Lookups** FastTab, select **Advances related to Intra-community acquisitions**.
2. On the **Conditions** FastTab, create a new line and set the following fields:

    - **Lookup result** – Select **Yes** if the sales tax code is used for advances that are related to intra-community acquisitions.
    - **Tax code** – Select a sales tax code.

3. On the **Conditions** FastTab, create a new line and set the following fields:

    - **Lookup result** – Select **No**
    - **Tax code** – Select **Not blank** to define that all other sales tax codes are not related to intra-community acquisitions.

#### Set up application-specific parameters for Nature

The **Incoming operations** report includes a **Nature** column that can show a description of goods and services.

Follow these steps to define which item sales tax groups generate which description of the nature on the report. These steps are continuation of the steps in the previous section.

1. On the **Application specific parameters** page, on the **Lookups** FastTab, select **Nature**.
2. On the **Conditions** FastTab, set the following fields:

    - **Lookup result** – Define the text of the nature.
    - **Item tax group** – Select an item sales tax group.

3. In the **State** field, change the value to **Completed**.
4. On the Action Pane, select **Export** to export the settings in an XML file. Then close the page.
5. Select the **VAT declaration Excel (BE)** configuration, and then select **Configurations** \> **Application specific parameters setup**.
6. Select **Import**, and select the file that you exported earlier.

### Set up the VAT reporting format for preview amounts in Excel

1. In the **Feature management** workspace, find and select the **VAT statement format reports** feature in the list, and then select **Enable now**.
2. Go to **General ledger \> Setup \> General ledger parameters**.
3. On the **Sales tax** tab, on the **Tax options** FastTab, in the **VAT statement format mapping** field, select the **VAT declaration Excel (BE)** ER format.

   This format is printed when you run the **Report sales tax for settlement period** report. It's also printed when you select **Print** on the **Sales tax payments** page.

4. In the **Special report** section, check that **Include corrections** is set to **Yes**.
5. On the **Tax authorities** page, select the tax authority, and in the **Report layout** field, select **Default**.

If you're configuring the VAT declaration in a legal entity that has [multiple VAT registrations](emea-reporting-for-multiple-vat-registrations.md), follow these steps.

1. Go to **General ledger** > **Setup** > **General ledger parameters**.
2. On the **Sales tax** tab, on the **Electronic reporting for countries/regions** FastTab, on the line for **BEL** select the **VAT Declaration Excel (BE)** ER format.

## Set up electronic messages

### Download and import the data package that has example settings for electronic messages

The data package contains electronic message settings that are used to preview the VAT declaration in Excel. You can extend these settings or create your own. For more information about how to work with electronic messaging and create your own settings, see [Electronic messaging](../general-ledger/electronic-messaging.md).

1. In [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/v2), in the Shared asset library, select **Data package** as the asset type, and then download **BE VAT declaration package**. The downloaded file is named **BE VAT declaration package.zip**.
2. In Finance, in the **Data management** workspace, select **Import**.
3. On the **Import** FastTab, in the **Group name** field, enter a name for the job.
4. On the **Selected entities** FastTab, select **Add file**.
5. In the **Add file** dialog box, verify that the **Source data format** field is set to **Package**, select **Upload and add**, and then select the zip file that you downloaded earlier.
6. Select **Close**.
7. After the data entities are uploaded, on the Action Pane, select **Import**.
8. Go to **Ta**x \> **Inquiries and reports** \> **Electronic messages** \> **Electronic messages** and validate the electronic message processing that you imported (**BE VAT declaration**).

### Configure electronic messages

1. Go to **Tax** \> **Setup** \> **Electronic messages** \> **Populate records actions**.
2. Select the line for **BE Populate VAT return records**, and then select **Edit query**.
3. Use the filter to specify the settlement periods to include on the report.
4. If you must report tax transactions from other settlement periods in a different declaration, create a new **Populate records** action, and select the appropriate settlement periods.

## Preview the VAT declaration, incoming transactions, and outgoing transactions in Excel

### Preview the VAT declaration in Excel from the Report sales tax for settlement period periodic task

1. Go to **Tax** \> **Periodic tasks** \> **Declarations** \> **Sales tax** \> **Report sales tax for settlement period**.
2. Set the following fields.

    | Field                     | Description                                    |
    |---------------------------|------------------------------------------------|
    | Settlement period         | Select the settlement period.                  |
    | From date                 | Select the start date of the reporting period.|

3. Select **OK**, and then, in the **Electronic report parameters** dialog box, set the following fields.

    | Field   | Description  |
    |---------|--------------|
    | 91 Deposit amount to be paid in December | Enter the amount, if applicable. |
    | Generate reports  | Select the reports that should be generated:</br> - Incoming operations </br>- Outgoing operations</br>- VAT declaration preview  |
    | Include fields  | Select the columns that should be visible on the **Incoming operations** and **Outgoing operations** reports, in addition to the **Date**, **Supplier**, and **Customer name** columns: </br> -   Document date</br>-   Document number </br>   -   Account </br> -   Voucher </br> -   Vat ID|

4. Select **OK**, and review the Excel report.

### Settle and post sales tax

1. Go to **Tax** \> **Periodic tasks** \> **Declarations** \> **Sales tax** \> **Settle and post sales tax**.
2. Set the following fields.

    | Field                     | Description                                    |
    |---------------------------|------------------------------------------------|
    | Settlement period         | Select the settlement period.                  |
    | From date                 | Select the start date of the reporting period. |

3. Select **OK**.

### Preview the VAT declaration, incoming operations, and outgoing operations in Excel from a sales tax payment

1. Go to **Tax** \> **Inquiries and reports** \> **Sales tax inquiries** \> **Sales tax payments**, and select a sales tax payment line.
2. Select **Print report**, and then select **OK**.
3. Review the Excel file that is generated for the selected sales tax payment line.

> [!NOTE]
> The report is generated only for the selected line of the sales tax payment. If you must generate, for example, a corrective declaration that contains all corrections for the period, or a replacement declaration that contains original data and all corrections, use the **Report sales tax for settlement period** periodic task.

## Generate a VAT declaration, incoming operations, and outgoing operations from electronic messages

When you use electronic messages to generate the report, you can collect tax data from multiple legal entities. For more information, see the [Run a VAT declaration for multiple legal entities](#run-a-vat-declaration-for-multiple-legal-entities) section later in this article.

The following procedure applies to the electronic message processing example that you imported earlier from the LCS Shared asset library.

1. Go to **Tax \> Inquiries and reports \> Electronic messages \> Electronic messages**.
2. In the left pane, select **BE VAT declaration**.
3. On the **Messages** FastTab, select **New**, and then, in the **Run processing** dialog box, select **OK**.
4. Select the message line that is created, enter a description, and then specify the start and end dates for the declaration.

> [!NOTE]
> Steps 5 through 7 are optional.

5. Optional: On the **Messages** FastTab, select **Collect data**, and then select **OK**. The sales tax payments that were generated earlier are added to the message. For more information, see the [Settle and post sales tax](#settle-and-post-sales-tax) section earlier in this article. If you skip this step, you can still generate a VAT declaration by using the **Tax declaration version** field in the **Declaration** dialog box.
6. Optional: On the **Message items** FastTab, review the sales tax payments that are transferred for processing. By default, all sales tax payments of the selected period that weren't included in any other message of the same processing are included.
7. Optional: Select **Original document** to review the sales tax payments or select **Delete** to exclude sales tax payments from processing. If you skip this step, you can still generate a VAT declaration by using the **Tax declaration version** field in the **Declaration** dialog box.
8. On the **Messages** FastTab, select **Update status**. In the **Update status** dialog box, select **Ready to generate**, and then select **OK**. Verify that the message status is changed to **Ready to generate**.
9. Select **Generate report**. To preview the VAT declaration amounts, in the **Run processing** dialog box, select **Preview report**, and then select **OK**.
10. In the **Electronic reporting parameters** dialog box, set the fields as described in the [Preview the VAT declaration in Excel from the Report sales tax for settlement period periodic task](#preview-the-vat-declaration-in-excel-from-the-report-sales-tax-for-settlement-period-periodic-task) section earlier in this article, and then select **OK**.
11. Select the **Attachments** button (paper clip symbol) in the upper-right corner of the page, and then select **Open** to open the file. Review the amounts in the Excel documents.
12. Select **Generate report**.
13. To generate a report in XML format, in the **Run processing** dialog box, select **Generate report**, and then select **OK**.
14. Set the following fields.

    | Field                       | Description                  |
    |-----------------------------|------------------------------|
    | Report periodicity          | Select **Monthly** or **Quarterly**.  |
    | 61 VAT regularizations due amount carried over</br> 62 VAT regularizations deduction amount carried over</br> 81 Purchases goods amount carried over</br> 82 Purchases services amount carried over</br> 83 Purchases capital goods amount carried over</br> 86 EU purchases goods amount carried over</br> 87 Other purchases with VAT payable amount carried over</br> 88 EU purchases services amount carried over | In these fields, you can enter an amount that will be added to the subsequent box amount. You can enter a negative amount. For example, you might have to set these fields if the amount in a box was negative in the previous period, and you had to report 0 (zero) because negative amounts aren't allowed for the box. However, you can carry over the amount from the previous period to the current period. |
    | 91 Deposit amount to be paid in December   | Enter the amount, if applicable.  |
    | Replaced VAT declaration  | Enter the number of the declaration that you're replacing, if you're reporting corrections.   |
    | Request for reimbursement | Select **Yes**, or leave the value set to **No**.    |
    | Request for payment forms | Select **Yes**, or leave the value set to **No**.    |
    | Nil annual listing        | Select **Yes**, or leave the value set to **No**.    |

15. Select **OK** 
16. Select the **Attachments** button (paper clip symbol) in the upper-right corner of the page, and download the electronic file that was generated. You should then manually upload this file to the government portal.

## Run a VAT declaration for multiple legal entities

To use the formats to report the VAT declaration for a group of legal entities, you must first set up the application-specific parameters of the ER formats for sales tax codes from all required legal entities.

### Set up electronic messages to collect tax data from several legal entities

Follow these steps to set up electronic messages to collect data from multiple legal entities.

1. Go to **Workspaces \> Feature management**.
2. Find and select the **Cross-company queries for the populate records actions** feature in the list, and then select **Enable now**.
3. Go to **Tax \> Setup \> Electronic messages \> Populate records actions**.
4. On the **Populate records action** page, select the line for **BE Populate VAT return records**.

   In the **Datasources setup** grid, a new **Company** field is available. For existing records, this field shows the identifier of the current legal entity.

5. In the **Datasources setup** grid, add a line for each additional legal entity that must be included in reporting. For each new line, set the following fields.

    | Field                  | Description                                                                                                                   |
    |------------------------|-------------------------------------------------------------------------------------------------------------------------------|
    | Name                   | Enter a value that will help you understand where this record comes from. For example, enter **VAT payment of Subsidiary 1**. |
    | Message item type      | Select **VAT return**. This value is the only value that is available for all the records.                                    |
    | Account type           | Select **All**.                                                                                                               |
    | Master table name      | Specify **TaxReportVoucher** for all the records.                                                                             |
    | Document number field  | Specify **Voucher** for all the records.                                                                                      |
    | Document date field    | Specify **TransDate** for all the records.                                                                                    |
    | Document account field | Specify **TaxPeriod** for all the records.                                                                                    |
    | Company                | Select the ID of the legal entity.                                                                                            |
    | User query             | This checkbox is automatically selected when you define criteria by selecting **Edit query**.                                 |

6. For each new line, select **Edit query**, and specify a related settlement period for the legal entity that is specified in the **Company** field on the line.

When the setup is complete, the **Collect data** function on the **Electronic messages** page collects sales tax payments from all the legal entities that you defined.

## Migrating a setup of reporting codes to a setup of application-specific parameters

This section provides recommendations about how to migrate your setup of the INTERVAT declaration that is based on the reporting codes framework to the setup of VAT declaration (BE) that is based on application-specific parameters in the **Electronic reporting** workspace.

> [!NOTE]
> In the examples that follow, the same sales tax code is used for different types of transactions: domestic sales, intra-community sales, domestic purchases, intra-community purchases, and so on. This approach has been used only for the purpose of illustration. For an easier experience when you reconcile your taxes, we recommend that you to create as many sales tax codes as possible, so that each sales tax code can uniquely identify a specific transaction type. Then, during a tax audit, you will be able to explain the source of each transaction based on the sales tax code and will have to use only standard sales tax reconciliation reports.
> 
> Additionally, in the examples, all negative tax transactions are configured so that they are considered credit notes. This approach has also been used only for the purpose of illustration. To configure the correct settings, you should consider the information in the [Credit notes and negative corrections](#credit-notes-and-negative-corrections-1) section earlier in this article.

The tables in this section use the following abbreviations:

- **ICA** – Intra-community acquisitions
- **ICS** – Intra-community supplies

### Commercial goods and services at a standard rate

For example, for the following sales tax code:

| Sales tax code | Percentage | Comment                                                                                  |
|----------------|------------|------------------------------------------------------------------------------------------|
| CommGoods      | 21         | Commercial goods and services that are traded within Belgium and the European Union (EU) |

You have the following setup of reporting codes.

| **Transaction**       | **Taxable sales** | **Sales tax payable** | **Tax free sales (ICS)** | **Taxable purchases** | **Sales tax receivable** | **Tax free purchases** | **Taxable import** | **Offset taxable import** | **Use tax** | **Offset use tax** |
|-------------|-------------------|-----------------------|--------------------------|-----------------------|--------------------------|------------------------|--------------------|---------------------------|-------------|--------------------|
| Invoice     | 03   | 54    | 46     | 81   | 59    |    &nbsp;     | 81     | 86   | 59          | 55   |
| Credit note | 49                | 64                    | 48                       | \-81+85               | 63                       |    &nbsp;                     | \-81 +84           | \-86                      | 61          | 62                 |

In this case, you can have the following setup of application-specific parameters.

| Lookup result  | Label  | Line | Tax code  | Transaction classifier |
|----------------|--------|------|-----------|------------------------|
| 03_SalesStandardRate  | 03/54 Transactions subject to the rate of 21 %  | 1    | CommGoods | Sales  |
| 49_SalesStandardRateCreditNote   | 49/64 Credit notes issued in respect of transactions subject to the rate of 21 % [03]  | 2    | CommGoods | SalesCreditNote  |
| 46_EUSales  | 46 Exempt intra-community supplies made in Belgium and ABC sales | 3    | CommGoods | SalesExempt  |
| 48_EUSalesCreditNoteCorr  | 48 Credit notes issued and negative corrections in respect of exempt intra-community supplies made in Belgium and ABC sales [46] | 4    | CommGoods | SalesExemptCreditNote  |
| 81_PurchasesGoods   | 81/59 Purchases of commercial goods, rawmaterials and consumables (for Tax base - taking into account the credit notes received and other corrections) | 5 | CommGoods | Purchase  |
| 8185_PurchasesGoodsCreditNote   | \-81 +85/63 Credit notes received and negative corrections relating to purchases of commercial goods, rawmaterials and consumables | 6  | CommGoods | PurchaseCreditNote  |
| 8681_EUPurchasesGoodsUseTax  | 86/81 55/59 Intra-Community acquisitions of commercial goods, rawmaterials and consumables carried out in Belgium and ABC sales - UseTax  | 7  | CommGoods | UseTax                 |
| 868184_EUPurchasesGoodsCreditNoteUseTax | \-86/81 +84/61/62 Credit notes received and negative corrections relating to purchases of commercial goods, rawmaterials and consumables - UseTax | 8  | CommGoods | UseTaxCreditNote   |

### Commercial goods and services at a reduced rate

For example, for the following sales tax code:

| Sales tax code | Percentage | Comment                                                                                               |
|----------------|------------|-------------------------------------------------------------------------------------------------------|
| RedComGood     | 6          | Items/goods (but not services) that have a reduced sales tax and are traded within Belgium and the EU |

You have the following setup of reporting codes.

| **Transaction **   | **Taxable sales** | **Sales tax payable** | **Tax free sales (ICS)** | **Taxable purchases** | **Sales tax receivable** | **Tax free purchases** | **Taxable import** | **Offset taxable import** | **Use tax** | **Offset use tax** |
|-------------|-------------------|-----------------------|--------------------------|-----------------------|--------------------------|------------------------|--------------------|---------------------------|-------------|--------------------|
| Invoice     | 01                | 54                    | 46                       | 81                    | 59                       |     &nbsp;                    | 81                 | 86                        | 59          | 55                 |
| Credit note | 49                | 64                    | 48                       | \-81 +85              | 63                       |      &nbsp;                   | \-81 +84           | \-86                      | 61          | 62                 |

In this case, you can have the following setup of application-specific parameters.

| Lookup result  | Label  | Line | Tax code  | Transaction classifier |
|----------------|--------|------|------------|------------------------|
| 01_SalesLowerReducedRate  | 01/54 Transactions subject to the rate of 6 %  | 1  | RedComGood | Sales   |
| 49_SalesLowerReducedRateCreditNote  | 49/64 Credit notes issued in respect of transactions subject to the rate of 6 % [01]  | 2  | RedComGood | SalesCreditNote   |
| 46_EUSales  | 46 Exempt intra-community supplies made in Belgium and ABC sales | 3    | RedComGood | SalesExempt  |
| 48_EUSalesCreditNoteCorr  | 48 Credit notes issued and negative corrections in respect of exempt intra-community supplies made in Belgium and ABC sales [46] | 4  | RedComGood | SalesExemptCreditNote  |
| 81_PurchasesGoods  | 81/59 Purchases of commercial goods, rawmaterials and consumables (for Tax base - taking into account the credit notes received and other corrections) | 5   | RedComGood | Purchase    |
| 8185_PurchasesGoodsCreditNote  | \-81 +85/63 Credit notes received and negative corrections relating to purchases of commercial goods, rawmaterials and consumables  | 6   | RedComGood | PurchaseCreditNote  |
| 8681_EUPurchasesGoodsUseTax  | 86/81 55/59 Intra-Community acquisitions of commercial goods, rawmaterials and consumables carried out in Belgium and ABC sales - UseTax  | 7  | RedComGood | UseTax                 |
| 868184_EUPurchasesGoodsCreditNoteUseTax | \-86/81 +84/61/62 Credit notes received and negative corrections relating to purchases of commercial goods, rawmaterials and consumables - UseTax      | 8    | RedComGood | UseTaxCreditNote  |

### Commercial goods for trade outside the EU

For example, for the following sales tax code:

| Sales tax code | Percentage | Comment                                                                |
|----------------|------------|------------------------------------------------------------------------|
| ComGood-3      | 21         | Commercial goods that are imported from or exported to other countries/regions |

You have the following setup of reporting codes.

|  **Transaction**  | **Taxable sales** | **Sales tax payable**                        | **Tax free sales (ICS)**       | **Taxable purchases** | **Sales tax receivable** | **Tax free purchases** | **Taxable import** | **Offset taxable import** | **Use tax** | **Offset use tax** |
|-------------|-------------------|----------------------------------------------|--------------------------------|-----------------------|--------------------------|------------------------|--------------------|---------------------------|-------------|--------------------|
| Invoice     |     &nbsp;               |             &nbsp;                                  | 47                             | 81                    | 59                       | 81                     | 81                 | 87                        | 59          | 57                 |
| Credit note |       &nbsp;             |      &nbsp;                                         | 49                             | \-81 +85              | 63                       | \-81 +85               | \-81 +85           | \-87                      | 61          | 62                 |

In this case, you can have the following setup of application-specific parameters.

| Lookup result  | Label | Line | Tax code  | Transaction classifier   |
|----------------|-------|------|-----------|--------------------------|
| 47_OtherExemptSales   | 47 Other exempt transactions and other transactions carried out abroad | 1   | ComGood-3 | SalesExempt   |
| 49_ExemptSalesSpecialSchemeCreditNoteCorr  | 49 Credit notes issued and negative corrections in respect of transactions subject to special regulations [00]  | 2  | ComGood-3 | SalesExemptCreditNote  |
| 81_PurchasesGoods  | 81/59 Purchases of commercial goods, rawmaterials and consumables (for Tax base - taking into account the credit notes received and other corrections)  | 3    | ComGood-3 | Purchase  |
| 8185_PurchasesGoodsCreditNote  | \-81 +85/63 Credit notes received and negative corrections relating to purchases of commercial goods, rawmaterials and consumables   | 4  | ComGood-3 | PurchaseCreditNote  |
| 81_PurchasesGoods  | 81/59 Purchases of commercial goods, rawmaterials and consumables (for Tax base - taking into account the credit notes received and other corrections)  | 5    | ComGood-3 | PurchaseExempt  |
| 8185_PurchasesGoodsCreditNote  | \-81 +85/63 Credit notes received and negative corrections relating to purchases of commercial goods, rawmaterials and consumables | 6  | ComGood-3 | PurchaseExemptCreditNote |
| 8781_OtherPurchasesImportsDeferredTaxGoodsUseTax | 87/81 57/59 Other purchases of commercial goods, rawmaterials and consumables for which VAT is due by the declarant (imports with deferred tax collection) - UseTax  | 7    | ComGood-3 | UseTax   |
| 878185_OtherPurchasesImportsDeferredTaxGoodsCNUseTax | \-87/81 +85/61/62 Credit notes received and negative corrections relating to other purchases of commercial goods, rawmaterials and consumables for which VAT is due by the declarant (imports with deferred tax collection) - UseTax | 8  | ComGood-3 | UseTaxCreditNote    |

### Services at a standard rate and goods purchased for internal use

For example, for the following sales tax code:

| Sales tax code | Percentage | Comment                                                                                        |
|----------------|------------|------------------------------------------------------------------------------------------------|
| Service21      | 21         | Services and internally used goods that are traded within Belgium, the EU, and other countries/regions |

You have the following setup of reporting codes.

| **Transaction**   | **Taxable sales**       | **Sales tax payable**       | **Tax free sales (ICS)**                                                           | **Taxable purchases** | **Sales tax receivable** | **Tax free purchases** | **Taxable import** | **Offset taxable import** | **Use tax** | **Offset use tax** |
|-------------|-------------------------|-----------------------------|------------------------------------------------------------------------------------|-----------------------|--------------------------|------------------------|--------------------|---------------------------|-------------|--------------------|
| Invoice     | 03                      | 54                          | 47                                                                                 | 82                    | 59                       | 82                     | 82                 |    &nbsp;                        |    &nbsp;          |     &nbsp;                |
| Credit note | 49                      | 64                          | 49                                                                                 | \-82 +85              | 63                       | \-82 +85               | \-82 +85           |      &nbsp;                      |     &nbsp;         |    &nbsp;                 |

In this case, you can have the following setup of application-specific parameters.

| Lookup result    | Label     | Line | Tax code  | Transaction classifier   |
|------------------|-----------|------|-----------|--------------------------|
| 03_SalesStandardRate   | 03/54 Transactions subject to the rate of 21 %  | 1  | Service21 | Sales  |
| 49_SalesStandardRateCreditNote  | 49/64 Credit notes issued in respect of transactions subject to the rate of 21 % [03]  | 2 | Service21 | SalesCreditNote  |
| 47_OtherExemptSales | 47 Other exempt transactions and other transactions carried out abroad  | 3  | Service21 | SalesExempt  |
| 49_ExemptSalesSpecialSchemeCreditNoteCorr | 49 Credit notes issued and negative corrections in respect of transactions subject to special regulations [00]  | 4  | Service21 | SalesExemptCreditNote  |
| 82_PurchasesServicesMisc  | 82/59 Purchases of services and miscellaneous goods (for Tax base - taking into account the credit notes received and other corrections) | 5   | Service21 | Purchase  |
| 8285_PurchasesServicesMiscCreditNote  | \-82 +85/63 Credit notes received and negative corrections relating to purchases of services and miscellaneous goods | 6  | Service21 | PurchaseCreditNote  |
| 82_PurchasesServicesMisc  | 82/59 Purchases of services and miscellaneous goods (for Tax base - taking into account the credit notes received and other corrections) | 7  | Service21 | PurchaseExempt  |
| 8285_PurchasesServicesMiscCreditNote   | \-82 +85/63 Credit notes received and negative corrections relating to purchases of services and miscellaneous goods | 8    | Service21 | PurchaseExemptCreditNote |

> [!NOTE]
> In this example, don't post the UseTax purchase, and don't set up **UseTax** in the application-specific parameters. Use the **taxable purchases** or **tax free purchases** transaction for the purchase of services from outside Belgium.

### Capital goods

For example, for the following sales tax code:

| Tax code  | Percentage | Comment                                                 |
|-----------|------------|---------------------------------------------------------|
| Capital21 | 21         | Capital items that are traded within Belgium and the EU |

You have the following setup of reporting codes.

| **Transaction**            | **Taxable sales** | **Sales tax payable**       | **Tax free sales (ICS)**             | **Taxable purchases** | **Sales tax receivable** | **Tax free purchases** | **Taxable import** | **Offset taxable import** | **Use tax** | **Offset use tax** |
|-------------|-------------------|-----------------------------|--------------------------------------|-----------------------|--------------------------|------------------------|--------------------|---------------------------|-------------|--------------------|
| Invoice     | 03                | 54                          | 46                                   | 83                    | 59                |     &nbsp;   | 83                 | 86                        | 59          | 55                 |
| Credit note | 49                | 64                          | 48                                   | \-83 +85              | 63      |        &nbsp;            | \-83 +84           | \-86                      | 61          | 62                 |

In this case, you can have the following setup of application-specific parameters.

| Lookup result  | Label  | Line | Tax code  | Transaction classifier |
|----------------|--------|------|-----------|------------------------|
| 03_SalesStandardRate   | 03/54 Transactions subject to the rate of 21 %  | 1    | Capital21 | Sales  |
| 49_SalesStandardRateCreditNote | 49/64 Credit notes issued in respect of transactions subject to the rate of 21 % [03] | 2    | Capital21 | SalesCreditNote   |
| 46_EUSales | 46 Exempt intra-community supplies made in Belgium and ABC sales  | 3    | Capital21 | SalesExempt  |
| 48_EUSalesCreditNoteCorr  | 48 Credit notes issued and negative corrections in respect of exempt intra-community supplies made in Belgium and ABC sales [46] | 4    | Capital21 | SalesExemptCreditNote  |
| 83_PurchasesCapitalGoods  | 83/59 Purchases of capital goods (for Tax base - taking into account the credit notes received and other corrections) | 5  | Capital21 | Purchase  |
| 8385_PurchasesCapitalGoodsCreditNote| \-83 +85/63 Credit notes received and negative corrections  | 6    | Capital21 | PurchaseCreditNote   |
| 8683_EUPurchasesCapitalGoodsUseTax   | 86/83 55/59 Intra-Community acquisitions of capital goods carried out in Belgium and ABC sales - UseTax  | 7  | Capital21 | UseTax   |
| 868384_EUPurchasesCapitalGoodsCreditNoteUseTax | \-86/83 +84/61/62 Credit notes received and negative corrections relating to purchases of capital goods - UseTax  | 8  | Capital21 | UseTaxCreditNote  |

### Special services

For example, for the following sales tax code:

| Sales tax code | Percentage | Comment                                                         |
|----------------|------------|-----------------------------------------------------------------|
| SpecServ       | 0          | Special services, where sales tax will be paid by the recipient |

You have the following setup of reporting codes.

| **Transaction**   | **Taxable sales** | **Sales tax payable** | **Tax free sales (ICS)** | **Taxable purchases** | **Sales tax receivable** | **Tax free purchases** | **Taxable import** | **Offset taxable import** | **Use tax** | **Offset use tax** |
|-------------|-------------------|-----------------------|--------------------------|-----------------------|--------------------------|------------------------|--------------------|---------------------------|-------------|--------------------|
| Invoice     |     &nbsp;               |       &nbsp;                 | 45         |   &nbsp;     |     &nbsp;        |      &nbsp;     | 82                 | 87                        |   &nbsp;  |     &nbsp;    |
| Credit note |    &nbsp;       |    &nbsp;      | 49           |      &nbsp;     |      &nbsp;    |      &nbsp;       | \-82 +85           | \-87             |   &nbsp;    |    &nbsp;     |

In this case, you can have the following setup of application-specific parameters.

| Lookup result   | Label   | Line | Tax code  | Transaction classifier |
|-----------------|---------|------|-----------|------------------------|
| 46_EUSales   | 46 Exempt intra-community supplies made in Belgium and ABC sales  | 3    | Capital21 | SalesExempt    |
| 48_EUSalesCreditNoteCorr  | 48 Credit notes issued and negative corrections in respect of exempt intra-community supplies made in Belgium and ABC sales [46]  | 4    | Capital21 | SalesExemptCreditNote  |
| 8782_OtherPurchasesDomesticReverseChargeMiscUseTax     | 87/82 56/59 Other purchases of miscellaneous goods for which VAT is due by the declarant (domestic reverse charge) - UseTax    | 7    | Capital21 | UseTax  |
| 878285_OtherPurchasesDomesticReverseChargeMiscCNUseTax | \-87/82 +85/61/62 Credit notes received and negative corrections relating to other purchases of miscellaneous goods for which VAT is due by the declarant (domestic reverse charge) - UseTax | 8    | Capital21 | UseTaxCreditNote  |


## Examples of posting and reporting

The examples in this section are provided for the setup of application-specific parameters for the [Commercial goods and services at a standard rate](#commercial-goods-and-services-at-a-standard-rate) section earlier in this article.

### Example 1: Sale in Belgium

This example shows a sale in Belgium, where the invoice net amount is 1,000 EUR plus 21-percent sales tax.

**Posting**

| Account            | Debit    | Credit   |
|--------------------|----------|----------|
| Customer           | 1,210.00 |  &nbsp;         |
| Sale               |    &nbsp;       | 1,000.00 |
| Outgoing sales tax |   &nbsp;        | 210.00   |

**Reporting**

| Field in sales tax report | Amount   |
|---------------------------|----------|
| Field 03                  | 1,000.00 |
| Field 54                  | 210.00   |

### Example 2: Credit note for a sale in Belgium

This example shows a credit note for a sale in Belgium, where the credit note net amount is 1,000 EUR plus 21-percent sales tax.

**Posting**

| Account            | Debit    | Credit   |
|--------------------|----------|----------|
| Customer           |   &nbsp;        | 1,210.00 |
| Sale               | 1,000.00 |   &nbsp;        |
| Outgoing sales tax | 210.00   |    &nbsp;       |

**Reporting**

| Field in sales tax report | Amount   |
|---------------------------|----------|
| Field 49                  | 1,000.00 |
| Field 64                  | 210.00   |

### Example 3: Purchase in Belgium

This example shows a purchase in Belgium, where the invoice net amount is 1,000 EUR plus 21-percent sales tax.

**Posting**

| Account            | Debit    | Credit   |
|--------------------|----------|----------|
| Vendor             |  &nbsp;         | 1,210.00 |
| Cost               | 1,000.00 |  &nbsp;         |
| Incoming sales tax | 210.00   |    &nbsp;       |

**Reporting**

| Field in sales tax report | Amount   |
|---------------------------|----------|
| Field 81                  | 1,000.00 |
| Field 59                  | 210.00   |

### Example 4: Credit note for a purchase in Belgium

This example shows a credit note for a purchase in Belgium, where the credit note net amount is 1,000 EUR plus 21-percent sales tax.

**Posting**

| Account            | Debit    | Credit   |
|--------------------|----------|----------|
| Vendor             | 1,210.00 |  &nbsp;         |
| Cost               |  &nbsp;         | 1,000.00 |
| Incoming sales tax |   &nbsp;        | 210.00   |

**Reporting**

| Field in sales tax report | Amount     |
|---------------------------|------------|
| Field 81                  | \-1,000.00 |
| Field 85                  | 1,000.00   |
| Field 63                  | 210.00     |

### Example 5: Intra-community acquisition

This example shows an intra-community acquisition (that is, an acquisition from a vendor that is in the EU but outside Belgium), where the invoice net amount is 1,000 EUR. Belgian 21-percent sales tax will have to be self-accounted.

**Posting**

| Account                                  | Debit    | Credit   |
|------------------------------------------|----------|----------|
| Vendor                                   |   &nbsp;        | 1,000.00 |
| Cost                                     | 1,000.00 |   &nbsp;        |
| Import (self-accounted) sales tax        | 210.00   |   &nbsp;        |
| Import (self-accounted) sales tax offset |  &nbsp;         | 210.00   |

**Reporting**

| Field in sales tax report | Amount   |
|---------------------------|----------|
| Field 81                  | 1,000.00 |
| Field 86                  | 1,000.00 |
| Field 59                  | 210.00   |
| Field 55                  | 210.00   |

### Example 6: Credit note for an intra-community acquisition

This example shows a credit note for an intra-community acquisition (that is, an acquisition from a vendor that is in the EU but outside Belgium), where the credit note net amount is 1,000 EUR. Belgian 21-percent sales tax will have to be self-accounted.

**Posting**

| Account                                   | Debit    | Credit   |
|-------------------------------------------|----------|----------|
| Vendor                                    | 1,000.00 | &nbsp;          |
| Cost                                      | &nbsp;          | 1,000.00 |
| Import (self-accounted) sales tax         |   &nbsp;        | 210.00   |
| Import (self-accounted) sales tax set off | 210.00   |     &nbsp;      |

**Reporting**

| Field in sales tax report | Amount     |
|---------------------------|------------|
| Field 81                  | \-1,000.00 |
| Field 86                  | \-1,000.00 |
| Field 84                  | 1,000.00   |
| Field 61                  | 210.00     |
| Field 62                  | 210.00     |

### Example 7: Intra-community supply

This example shows intra-community supply (that is, supply to a customer that is in another EU member state and has a sales tax registration number in that member state), where the invoice net amount is 1,000 EUR and is tax-free.

**Posting**

| Account  | Debit    | Credit   |
|----------|----------|----------|
| Customer | 1,000.00 | &nbsp;          |
| Sale     |   &nbsp;        | 1,000.00 |

**Reporting**

| Field in sales tax report | Amount   |
|---------------------------|----------|
| Field 46                  | 1,000.00 |

### Example 8: Credit note for intra-community supply

This example shows a credit note for intra-community supply (that is, supply to a customer that is in another EU member state and has a sales tax registration number in that member state), where the credit note net amount is 1,000 EUR.

**Reporting**

| Field in sales tax report | Amount   |
|---------------------------|----------|
| Field 48                  | 1,000.00 |


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
