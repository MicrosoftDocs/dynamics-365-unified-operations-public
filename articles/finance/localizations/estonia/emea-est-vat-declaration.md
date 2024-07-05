---
title: VAT declaration for Estonia
description: Learn how to set up a value-added tax (VAT) declaration for legal entities in Estonia, including an overview on VAT declarations.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.date: 01/15/2024
ms.custom: 266904
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Estonia
ms.search.validFrom: 2024-01-15
ms.search.form: TaxPeriod, TaxReportCollection, TaxReportVoucher
ms.dyn365.ops.version: AX 7.0.1
---

# VAT declaration for Estonia

[!include [banner](../../includes/banner.md)]

This article describes how to set up and generate a value-added tax (VAT) declaration for Estonia in the official XML format. It also describes how to preview the VAT declaration in Microsoft Excel.

As of 10.0.36 version of Dynamics 365 Finance, the VAT declaration feature for Estonia supports filing a VAT return for [multiple VAT registrations](../global/emea-multiple-vat-registration-numbers.md) and for companies that report as a VAT group in the same system database. For each version of Finance that's listed in the following table, these capabilities are supported as of the specified build number.

| Version | Build | 
|---------|-------|
| 10.0.38 | 10.0.1777.94 |
| 10.0.37 | 10.0.1725.138 |
| 10.0.36 | 10.0.1695.149 |

## VAT declaration overview

To automatically generate the report, first create enough sales tax codes to keep a separate VAT accounting for each type of operation that's subject to reporting in the VAT declaration for Estonia. Additionally, in the application-specific parameters of the Electronic reporting (ER) format for the VAT declaration, associate available sales tax transaction attributes (sales tax code, tax classifier, item sales tax group, and sales tax group) with the lookup result of the **Report field lookup** lookup field. In the following table, the "Lookup result" column shows the lookup result that's preconfigured for a specific VAT declaration field (tag) in the VAT declaration format. Use this information to correctly associate tax transaction attributes with the lookup result and then with the field (tag) of the VAT declaration.

| Lookup result | Label (EN) | Label (EE) | \<declarationBody\> | \<salesAnnex\> - Part A of VAT INF return, TAX\_RATE\_SALES | \<purchasesAnnex\> - Part B of VAT INF return | Description (EN) | Description (EE) |
|---|---|---|---|---|---|---|---|
| 22-sales | KMD1-22% | KMD1-22% | 1 | 22 | Not included | Acts and transactions subject to tax at a rate of 22% (line 1 of VAT return (KMD)) | 22% määraga maksustatavad toimingud ja tehingud (KMD rida 1) |
| 22erikord-sales | KMD1-22%special | KMD1-22%erikord | 1 | 22erikord | Not included | **Special procedure** for VAT taxation at a rate of 22% (line 1 of VAT return (KMD)) | Käibemaksu maksustamise erikord 22% määraga (käibemaksudeklaratsiooni (KMD) rida 1) |
| EUAcquisitionsServicesUseTax-22 | KMD1UseTaxEU\_S-22% | KMD1UseTaxEU\_S-22% | 1 and 6 | Not included | Not included | UseTax Intra-Community acquisitions of **services** received from a taxable person of another Member State, total, incl. (line 1, 6 without 6.1 of VAT return) at a rate of 22% | UseTax auba ühendusesisene teise liikmesriigi maksukohustuslaselt saadud teenused kokku (KMD rida 1, 6 ilma 6.1) - 22% |
| EUAcquisitionsGoodsUseTax-22 | KMD1UseTaxEU\_G-22% | KMD1UseTaxEU\_G-22% | 1, 6.1, and 6 | Not included | Not included | UseTax Intra-Community acquisitions of **goods** (line 1, 6.1 of VAT return) at a rate of 22% | UseTax Kauba ühendusesisene soetamine (KMD rida 1, 6.1) - 22% |
| OtherAcquisitionAct411UseTax-22 | KMD1UseTaxAcq411-22% | KMD1UseTaxAcq411-22% | 1, 7.1, and 7 | 22 | Included | UseTax Acquisition of immovables, scrap metal, precious metal, and metal products subject to value-added tax under the special arrangements (VAT Act §41¹) (line 1, 7.1 of VAT return) at a rate of 22% | UseTax Erikorra alusel maksustatava kinnisasja, metallijäätmete, väärismetalli ja metalltoodete soetamine (KMS § 411) (KMD rida 7.1) - 22% |
| OtherAcquisitionUseTax-22 | KMD1UseTaxAcqOther-22% | KMD1UseTaxAcqOther-22% | 1 and 7 | 22 | Included | UseTax Acquisition of other goods and services subject to VAT incl. (line 1, 7 of VAT return) at a rate of 22% | UseTax Muu kauba soetamine ja teenuse saamine, mida maksustatakse käibemaksuga (KMD rida 1, 7) - 22% |
| 20-sales | KMD11-20% | KMD11-20% | 11 | 20 | Not included | Acts and transactions subject to tax at a rate of 20% (line 11 of VAT return (KMD)), excluding self-supply of goods or services taxable at 20% | 20% määraga maksustatavad toimingud ja tehingud (KMD rida 11), välja arvatud 20% määraga maksustatav kauba või teenuse omatarve |
| 20erikord-sales | KMD11-20%special | KMD11-20%erikord | 11 | 20erikord | Not included | **Special procedure** for VAT taxation at a rate of 20% (line 11 of VAT return (KMD)) | Käibemaksu maksustamise erikord 20% määraga (käibemaksudeklaratsiooni (KMD) rida 11) |
| 20-selfsupply | KMD1.1-20%selfsupply | KMD1.1-20%selfsupply | 11 | 20 | Not included | Self-supply of goods or services taxable at 20% (line 11 of VAT return) | 20% määraga maksustatav kauba või teenuse omatarve (KMD rida 11) |
| EUAcquisitionsServicesUseTax-20 | KMD11UseTaxEU\_S-20% | KMD11UseTaxEU\_S-20% | 11 and 6 | Not included | Not included | UseTax Intra-Community acquisitions of services received from a taxable person of another Member State, total, incl. (line 11, 6 without 6.1 of VAT return) at a rate of 20% | UseTax auba ühendusesisene teise liikmesriigi maksukohustuslaselt saadud teenused kokku (KMD rida 11, 6 ilma 6.1) - 20% |
| EUAcquisitionsGoodsUseTax-20 | KMD11UseTaxEU\_G-20% | KMD11UseTaxEU\_G-20% | 11, 6.1, and 6 | Not included | Not included | UseTax Intra-Community acquisitions of goods (line 11, 6.1 of VAT return) at a rate of 20% | UseTax Kauba ühendusesisene soetamine (KMD rida 11, 6.1) - 20% |
| OtherAcquisitionAct411UseTax-20 | KMD1UseTaxAcq411-20% | KMD1UseTaxAcq411-20% | 11, 7.1, and 7 | 20 | Included | UseTax Acquisition of immovables, scrap metal, precious metal, and metal products subject to value-added tax under the special arrangements (VAT Act §41¹) (line 11, 7.1 of VAT return) at a rate of 20% | UseTax Erikorra alusel maksustatava kinnisasja, metallijäätmete, väärismetalli ja metalltoodete soetamine (KMS § 411) (KMD rida 11, 7.1) - 20% |
| OtherAcquisitionUseTax-20 | KMD1UseTaxAcqOther-20% | KMD1UseTaxAcqOther-20% | 11 and 7 | 20 | Included | UseTax Acquisition of other goods and services subject to VAT incl. (line 11, 7 of VAT return) at a rate of 20% | UseTax Muu kauba soetamine ja teenuse saamine, mida maksustatakse käibemaksuga (KMD rida 11, 7) - 20% |
| 9-sales | KMD2-9% | KMD2-9% | 2 | 9 | Not included | Acts and transactions subject to tax at a rate of 9% (line 2 of VAT return), excluding self-supply of goods or services taxable at 9% | 9% määraga maksustatavad toimingud ja tehingud (KMD rida 2), välja arvatud 9% määraga maksustatav kauba või teenuse omatarve |
| 9erikord-sales | KMD2-9%special | KMD2-9%erikord | 2 | 9erikord | Not included | **Special procedure** for VAT taxation at a rate of 9% (line 2 of VAT return (KMD)) | Käibemaksu maksustamise erikord 9% määraga (käibemaksudeklaratsiooni (KMD) rida 2) |
| 9-selfsupply | KMD2.1-9%selfsupply | KMD2.1-9%selfsupply | 2 | 9 | Not included | Self-supply of goods or services taxable at 9% (line 2 of VAT return) | 9% määraga maksustatav kauba või teenuse omatarve (KMD rida 2) |
| EUAcquisitionsServicesUseTax-9 | KMD2UseTaxEU\_S-9% | KMD2UseTaxEU\_S-9% | 2 and 6 | Not included | Not included | UseTax Intra-Community acquisitions of services received from a taxable person of another Member State, total, incl. (line 2, 6 without 6.1 of VAT return) at a rate of 9% | UseTax auba ühendusesisene teise liikmesriigi maksukohustuslaselt saadud teenused kokku (KMD rida 2, 6 ilma 6.1) - 9% |
| EUAcquisitionsGoodsUseTax-9 | KMD2UseTaxEU\_G-9% | KMD2UseTaxEU\_G-9% | 2, 6.1, and 6 | Not included | Not included | UseTax Intra-Community acquisitions of goods (line 2, 6.1 of VAT return) at a rate of 9% | UseTax Kauba ühendusesisene soetamine (KMD rida 2, 6.1) - 9% |
| OtherAcquisitionAct411UseTax-9 | KMD1UseTaxAcq411-9% | KMD1UseTaxAcq411-9% | 2, 7.1, and 7 | 9 | Included | UseTax Acquisition of immovables, scrap metal, precious metal, and metal products subject to value-added tax under the special arrangements (VAT Act §41¹) (line 2, 7.1 of VAT return) at a rate of 9% | UseTax Erikorra alusel maksustatava kinnisasja, metallijäätmete, väärismetalli ja metalltoodete soetamine (KMS § 411) (KMD rida 2, 7.1) - 9% |
| OtherAcquisitionUseTax-9 | KMD1UseTaxAcqOther-9% | KMD1UseTaxAcqOther-9% | 2 and 7 | 9, PurchAnnex | Not included | UseTax Acquisition of other goods and services subject to VAT incl. (line 2, 7 of VAT return) at a rate of 9% | UseTax Muu kauba soetamine ja teenuse saamine, mida maksustatakse käibemaksuga (KMD rida 2, 7) - 9% |
| 5-sales | KMD21-5% | KMD21-5% | 21 | 5 | Not included | Acts and transactions subject to tax at a rate of 5% (line 21 of VAT return) | 5% määraga maksustatavad toimingud ja tehingud (KMD rida 21) |
| 5erikord-sales | KMD21-5%special | KMD2-5%erikord | 21 | 5erikord | Not included | **Special procedure** for VAT taxation at a rate of 5% (line 21 of VAT return (KMD)) | Käibemaksu maksustamise erikord 5% määraga (käibemaksudeklaratsiooni (KMD) rida 21) |
| EUAcquisitionsServicesUseTax-5 | KMD21UseTaxEU\_S-5% | KMD21UseTaxEU\_S-5% | 21 and 6 | Not included | Not included | UseTax Intra-Community acquisitions of services received from a taxable person of another Member State, total, incl. (line 21 and 6 without 6.1 of VAT return) at a rate of 5% | UseTax auba ühendusesisene teise liikmesriigi maksukohustuslaselt saadud teenused kokku (KMD rida 21, 6 ilma 6.1) - 5% |
| EUAcquisitionsGoodsUseTax-5 | KMD21UseTaxEU\_G-5% | KMD21UseTaxEU\_G-5% | 21, 6, and 6.1 | Not included | Not included | UseTax Intra-Community acquisitions of goods (line 21 and 6.1 of VAT return) at a rate of 5% | UseTax Kauba ühendusesisene soetamine (KMD rida 21, 6.1) - 5% |
| OtherAcquisitionAct411UseTax-5 | KMD1UseTaxAcq411-5% | KMD1UseTaxAcq411-5% | 21, 7.1, and 7 | 5 | Included | UseTax Acquisition of immovables, scrap metal, precious metal, and metal products subject to value-added tax under the special arrangements (VAT Act §41¹) (line 21, 7.1 of VAT return) at a rate of 5% | UseTax Erikorra alusel maksustatava kinnisasja, metallijäätmete, väärismetalli ja metalltoodete soetamine (KMS § 411) (KMD rida 21, 7.1) - 5% |
| OtherAcquisitionUseTax-5 | KMD1UseTaxAcqOther-5% | KMD1UseTaxAcqOther-5% | 21 and 7 | 5 | Included | UseTax Acquisition of other goods and services subject to VAT incl. (line 21, 7 of VAT return) at a rate of 5% | UseTax Muu kauba soetamine ja teenuse saamine, mida maksustatakse käibemaksuga (KMD rida 21, 7) - 5% |
| 0-sales | KMD3-0% | KMD3-0% | 3 | Not included | Not included | Acts and transactions subject to tax at a rate of 0%, incl. (line 3 without 3.1 and 3.2 of VAT return), excluding EU supplies and exportation of goods | 0% määraga maksustatavad toimingud ja tehingud (KMD rida 3 ilma 3.1 ja 3.2), välja arvatud ELi tarned ja kaupade eksport |
| 0-EU | KMD3.1-0% | KMD3.1-0% | 3.1 and 3 | Not included | Not included | Intra-Community supply of goods and services provided to a taxable person of another Member State/taxable person with limited liability, total, incl. (line 3.1 without 3.1.1 of VAT return), excluding Intra-Community supply of goods | Kauba ühendusesisene käive ja teise liikmesriigi maksukohustuslasele/piiratud maksukohustuslasele osutatud teenuste käive kokku (KMD rida 3.1 ilma 3.1.1), välja Kauba ühendusesisene käive |
| 0-Goods-EU | KMD3.1.1-0% | KMD3.1.1-0% | 3.1.1, 3.1, and 3 | Not included | Not included | Intra-Community supply of goods (line 3.1.1 pf VAT return) | Kauba ühendusesisene käive (KMD rida 3.1.1) |
| 0-Export | KMD3.2-0% | KMD3.2-0% | 3.2 and 3 | Not included | Not included | Exportation of goods, incl. (line 3.2 without 3.2.1 of VAT return), excluding sale to passengers with return of VAT | Kauba eksport (KMD rida 3.2 ilma 3.2.1), välja Käibemaksutagastusega müük reisijale |
| 0-Export-Passengers | KMD3.2.1-0% | KMD3.2.1-0% | 3.2.1, 3.2, and 3 | Not included | Not included | Sale to passengers with return of value-added tax (line 3.2.1 of VAT return) | Käibemaksutagastusega müük reisijale (KMD rida 3.2.1) |
| InputVAT | KMD5 | KMD5 | 5 | Not included | Included | Total amount of input VAT subject to deduction pursuant to law (line 5 without 5.1, 5.2, 5.3, 5.4 of VAT return), excluding import, fixed assets, acquisition of a car used for business purposes, and related operations (5.3, 5.4) | Kokku sisendkäibemaksusumma, mis on seadusega lubatud maha arvata (KMD rida 5 ilma 5.1, 5.2, 5.3, 5.4), välja import, põhivara, ettevõtluses kasutatava sõiduauto soetamine ja sellega seotud toimingud (5.3, 5.4) |
| PayableVATImport | KMD4.1 | KMD4.1 | 4.1 | Not included | Not included | VAT payable on import (line 4.1 of VAT return) | Impordilt tasutud või tasumisele kuuluv käibemaks (KMD rida 4.1) |
| ImportUseTax | KMD4.1-5.1UseTax | KMD4.1-5.1UseTax | 4.1, 5.1, and 5 | Not included | Not included | VAT payable on import (line 4.1 and 5.1 of VAT return) | Impordilt tasutud või tasumisele kuuluv käibemaks (KMD rida 4.1, 5.1) |
| DeductibleVATImport | KMD5.1 | KMD5.1 | 5.1 and 5 | Not included | Not included | VAT paid or payable on import that is allowed to be deducted by law (line 5.1 of VAT return) | Impordilt tasutud või tasumisele kuuluv käibemaks (KMD rida 5.1) |
| FixedAssets | KMD5.2 | KMD5.2 | 5.2 and 5 | Not included | Included | VAT paid or payable on acquisition of fixed assets (line of 5.2 of VAT return) | Põhivara soetamiselt tasutud või tasumisele kuuluv käibemaks (KMD rida 5.2) |
| Cars | KMD5.3 | KMD5.3 | 5.3 and 5 | Not included | Included | VAT paid or payable on acquisition of a car used for business purposes (100%), and on acquisition of goods and receipt of services for such car (line 5.3 of VAT return) | Ettevõtluses (100%) kasutatava sõiduautosoetamiselt ja sellise sõiduauto tarbeks kaupade soetamiselt ja teenuste saamiselt tasutud või tasumisele kuuluv käibemaks. (KMD rida 5.3) |
| CarsRelated | KMD5.4 | KMD5.4 | 5.4 and 5 | Not included | Included | VAT paid or payable on acquisition of a car used partially for business purposes, and on acquisition of goods and receipt of services for such car (line 5.4 of VAT return) | Osaliselt ettevõtluses kasutatava sõiduauto soetamiselt ja sellise sõiduauto tarbekskaupade soetamiselt ja teenuste saamiselt tasutudvõi tasumisele kuuluv käibemaks. (KMD rida 5.4) |
| EUAcquisitionsServices | KMD6 | KMD6 | 6 | Not included | Not included | Intra-Community acquisitions of services received from a taxable person of another Member State, total, incl. (line 6 without 6.1 of VAT return) | Kauba ühendusesisene teise liikmesriigi maksukohustuslaselt saadud teenused kokku (KMD rida 6 ilma 6.1) |
| EUAcquisitionsGoods | KMD6.1 | KMD6.1 | 6.1 and 6 | Not included | Not included | Intra-Community acquisitions of goods (line 6.1 of VAT return) | Kauba ühendusesisene soetamine (KMD rida 6.1) |
| OtherAcquisition | KMD7 | KMD7 | 7 | Not included | Included | Acquisition of other goods and services subject to VAT incl. (line 7 of VAT return), excluding immovables, scrap metal, precious metal, and metal products (line 7.1) | Muu kauba soetamine ja teenuse saamine, mida maksustatakse käibemaksuga (KMD rida 7), välja Erikorra alusel maksustatava kinnisasja, metallijäätmete, väärismetalli ja metalltoodete soetamine (KMS § 411) (KMD rida 7.1) |
| OtherAcquisitionAct411 | KMD7.1 | KMD7.1 | 7.1 and 7 | Not included | Included | Acquisition of immovables, scrap metal, precious metal, and metal products subject to value-added tax under the special arrangements (VAT Act §41¹) (line 7.1 of VAT return) | Erikorra alusel maksustatava kinnisasja, metallijäätmete, väärismetalli ja metalltoodete soetamine (KMS § 411) (KMD rida 7.1) |
| SupplyExemptFromTax | KMD8 | KMD8 | 8 | Not included | Not included | Supply exempt from tax (line 8 of VAT return) | Maksuvaba käive (KMD rida 8) |
| SupplySpecialArrangements | KMD9 | KMD9 | 9 | Not included | Not included | Supply of immovables, scrap metal, precious metal, and metal products subject to value-added tax under the special arrangements (VAT Act §41¹) and taxable value of goods to be installed or assembled in another Member State (line 9 of VAT return) | Erikorra alusel maksustatava kinnisasja, metallijäätmete ja väärismetalli käive (KMS § 411) ning teises liikmesriigis paigaldatava või kokkupandava kauba maksustatav väärtus (KMD rida 9) |
| Adjustments | KMD10-11 | KMD10-11 | 10 or 11 | Not included | Not included | Adjustments (\+) (line 10 of VAT return) (-) (line 11 of VAT return) | Täpsustused (\+) (KMD rida 10) (-) (KMD rida 11) |
| Other | Other | Muud | Not applicable | Not included | Not included | Other | Muud |

For more information about how to configure reverse charge VAT, see [Reverse charges](../global/emea-reverse-charge.md).

For more information about how to set up application-specific parameters, see the [Set up application-specific parameters for VAT declaration fields](#set-up) section later in this article.

## Set up the VAT declaration for Estonia

These tasks will prepare your Finance environment to generate the electronic file for the VAT declaration for Estonia and preview the VAT amounts in Excel format.

- [Import ER configurations](#import-er).
- [Set up application-specific parameters for VAT declaration fields](#set-up).
- [Set up the VAT reporting format to preview amounts in Excel](#setup-preview).
- [Set up electronic messages](#setup-em).
- [Set up the VAT registration number of the company that's reporting VAT](#vat-id).

### <a name="import-er"></a>Import ER configurations

Open the **Electronic reporting** workspace, and import the latest versions of these ER formats under **Tax declaration model**:

- VAT Declaration XML (EE)
- VAT Declaration Excel (EE)

Import **Tax declaration model mapping** under **Tax declaration model**, and mark it **Default for model mapping**.

For more information, see [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

### <a name="set-up"></a>Set up application-specific parameters for VAT declaration fields

To automatically generate the VAT declaration, associate available sales tax transaction attributes (sales tax code, tax classifier, item sales tax group, and sales tax group) in Finance and lookup results in the ER configuration.

> [!NOTE]
> We recommend that you enable the **Use application specific parameters from previous versions of ER formats** feature in the **Feature management** workspace. When this feature is enabled, parameters that are configured for an earlier version of an ER format automatically become applicable for a later version of the same format. If this feature isn't enabled, you must explicitly configure application-specific parameters for each format version. The **Use application specific parameters from previous versions of ER formats** feature is available in the **Feature management** workspace as of Finance version 10.0.23. For more information about how to set up the parameters of an ER format for each legal entity, see [Set up the parameters of an ER format per legal entity](../../../fin-ops-core/dev-itpro/analytics/er-app-specific-parameters-set-up.md).

Follow these steps to define which of the available sales tax transaction attributes (sales tax code, tax classifier, item sales tax group, or sales tax group) in Finance generates which field of the VAT declaration for Estonia.

1. Go to **Workspaces** \> **Electronic reporting**, and select **Reporting configurations**.
2. Select the **VAT declaration XML (EE)** configuration, and then, on the Action Pane, select **Configurations** \> **Application specific parameters setup**.
3. On the **Application specific parameters** page, on the **Lookups** FastTab, select **Report field lookup**.
4. On the **Conditions** FastTab, set the following fields to associate the sales tax codes and report fields.

    | Field | Description |
    |---|---|
    | Lookup result | Select the value of the report field. For more information about the values and their assignment to VAT declaration rows, see the [VAT declaration overview](#vat-declaration-overview) section earlier in this article. |
    | Tax code | Select the sales tax code to associate with the report field. Posted tax transactions that use the selected sales tax code will be collected in the appropriate declaration box. We recommend that you separate sales tax codes in such a way that one sales tax code generates amounts in only one declaration box. |
    | Transaction classifier | <p>If you created enough sales tax codes to determine a declaration box, select **\*Not blank\***. If you didn't create enough sales tax codes so that one sales tax code generates amounts in only one declaration box, you can set up a transaction classifier. The following transaction classifiers are available:</p><ul><li>**Purchase**</li><li>**PurchaseExempt** (tax-exempt purchase)</li><li>**PurchaseReverseCharge** (tax receivable from a purchase reverse charge)</li><li>**Sales**</li><li>**SalesExempt** (tax-exempt sale)</li><li>**SalesReverseCharge** (tax payable from a purchase reverse charge or a sales reverse charge)</li><li>**Use tax**</li></ul><p>For each transaction classifier, a classifier for the credit note is also available. For example, one of these classifiers is **PurchaseCreditNote** (purchase credit note).</p><p>Be sure to create two lines for each sales tax code: one that has the transaction classifier value and one that has the transaction classifier for credit note value.</p> |
    | Item sales tax group | Use the **Item sales tax group** column to supplement your setup that's specified with **Tax code** and **Transaction classifier** columns when necessary. |
    | Sales tax group | Use the **Sales tax group** column to supplement your setup that's specified with **Tax code** and **Transaction classifier** columns when necessary. |

    > [!NOTE]
    > Associate all sales tax codes (or combinations of a sales tax code, tax classifier, item sales tax group, and sales tax group) with lookup results. If any combination should not generate values on the VAT declaration, associate it with the **Other** lookup result.

5. In the **State** field, change the value to **Completed**.
6. On the Action Pane, select **Export** to export the settings of the application-specific parameters.
7. Select the **VAT declaration Excel (EE)** configuration, and then, on the Action Pane, select **Import** to import the parameters that you configured for **VAT declaration XML (EE)**.
8. In the **State** field, select **Completed**.

### <a name="setup-preview"></a>Set up the VAT reporting format to preview amounts in Excel

1. In the **Feature management** workspace, find and select the **VAT statement format reports** feature in the list, and then select **Enable now**.
2. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax authorities**, and select the tax authority.
3. In the **Report layout** field, select **Default**.
4. Go to **General ledger** \> **Setup** \> **General ledger parameters**.
5. On the **Sales tax** tab, on the **Tax options** FastTab, in the **VAT statement format mapping** field, select the **VAT declaration Excel (EE)** ER format.

This format is printed when you run the **Report sales tax for settlement period** report. It's also printed when you select **Print** on the **Sales tax payments** page.

If you're configuring the VAT declaration for Estonia in a legal entity that has [multiple VAT registrations](../global/emea-reporting-for-multiple-vat-registrations.md), follow these steps.

1. Go to **General ledger** \> **Setup** \> **General ledger parameters**.
2. On the **Sales tax** tab, on the **Electronic reporting for countries/regions** FastTab, on the line for **EST**, select the **VAT Declaration Excel (EE)** ER format.

### <a name="setup-em"></a>Set up electronic messages

Electronic messaging (EM) functionality is provided to maintain the different processes that are used in electronic reporting for different document types. For more information about electronic messages, see [Electronic messaging](../../general-ledger/electronic-messaging.md).

#### <a name="import-em"></a>Download and import the data package that has example settings for electronic messages

The process of setting up the **Electronic messages** functionality to generate the VAT declaration for Estonia in XML format and preview it in Excel has many steps. Because the data of some entities is used in the ER configurations, use a set of predefined values that are delivered in a package of data entities for the related tables. You can extend these settings or create your own.

> [!NOTE]
> Some records in the data entities in the package include a link to ER configurations. Before you start to import the data entities package, [import ER configurations into Finance](#import-er).

1. In [Microsoft Dynamics Lifecycle Services](https://lcs.dynamics.com/v2), in the Shared asset library, select **Data package** as the asset type, and then download **EE VAT declaration - KMD - EM setup v.\#**. The downloaded file is named **EE VAT declaration - KMD - EM setup v.\#.zip**. Always download the latest version of the package that's available in Lifecycle Services.
2. In Finance, in the **Data management** workspace, select **Import**.
3. On the **Import** FastTab, in the **Group name** field, enter a name for the job.
4. On the **Selected entities** FastTab, select **Add file**.
5. In the **Add file** dialog box, verify that the **Source data format** field is set to **Package**, select **Upload and add**, and then select the zip file that you downloaded earlier.
6. Select **Close**.
7. After the data entities are uploaded, on the Action Pane, select **Import**.
8. Go to **Tax** \> **Inquiries and reports** \> **Electronic messages** \> **Electronic messages**, and validate the electronic message processing that you imported (**EE VAT declaration**).

For more information about how you can use the data management framework, see [Data management](../../../fin-ops-core/dev-itpro/data-entities/data-entities-data-packages.md).

#### Configure electronic messages

1. Go to **Tax** \> **Setup** \> **Electronic messages** \> **Populate records actions**.
2. Select the line for **EE Populate VAT return records**, and then select **Edit query**.
3. Use the filter to specify the settlement periods to include on the report.
4. If you must report tax transactions from other settlement periods in a different declaration, create a new **Populate records** action, and select the appropriate settlement periods.

### <a id="vat-id"></a>Set up the VAT registration number of the company that's reporting VAT

To generate the VAT declaration, you must configure the tax registration number of your organization.

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
2. Select the legal entity, and then select **Registration IDs**.
3. Select or create the address in Estonia, and then, on the **Registration ID** FastTab, select **Add**.
4. In the **Registration type** field, select the registration type that's dedicated to Estonia and that uses the **VAT ID** registration category.
5. In the **Registration number** field, enter the tax number.
6. On the **General** tab, in the **Effective** field, enter the date when the number becomes effective.

For more information about how to set up registration categories and registration types, see [Registration IDs](../europe/emea-registration-ids.md).

Follow these steps to define the VAT registration number that EM uses during generation of the VAT declaration for Estonia.

1. Go to **Tax** \> **Setup** \> **Electronic messages** \> **Electronic messages processing**, and select the **EE VAT declaration** processing.
2. On the **Message additional fields** FastTab, in the **Tax registration number** field, define the VAT registration number that should be used in the VAT declaration for Estonia.
3. Save your changes.

If the VAT registration number isn't specified in the **Tax registration number** additional field of the **EE VAT declaration** processing, the system retrieves it from the registration ID that's defined in the properties of the legal entity that's associated with the **VAT ID** registration category.

## Preview the VAT declaration in Excel

### <a name="report-sales-tax-for-settlement-period"></a>Preview the VAT declaration in Excel from the Report sales tax for settlement period periodic task

1. Go to **Tax** \> **Periodic tasks** \> **Declarations** \> **Sales tax** \> **Report sales tax for settlement period**.
2. Set the following fields.

    | Field | Description |
    |---|---|
    | From date | Select the start date of the reporting period. |
    | Settlement period | Select the settlement period. |
    | Sales tax payment version | <p>Select one of the following values:</p><ul><li>**Original** – Generate a report for the sales tax transactions of the original sales tax payment or before the sales tax payment is generated.</li><li>**Corrections** – Generate a report for the sales tax transactions of all the subsequent sales tax payments for the period.</li><li>**Total list** – Generate a report for all the sales tax transactions for the period, including the original and all corrections.</li></ul> |

3. Select **OK**, and then, in the next dialog box, set the following fields.

    | Field | Description |
    |---|---|
    | Report composition | <p>Select one or more of the following values in the lookup list to specify which parts the report must include:</p><ul><li>Declaration body</li><li>Sales Annex - Part A</li><li>Purchases Annex - Part B</li></ul> |
    | Summarize sales per partner | Select this checkbox to report information in Sales annexes grouped by partner. If this checkbox is selected, the invoice number and date aren't mandatory fields in part A, and amounts are summarized per partner. |
    | Summarize purchases per partner | Select this checkbox to report information in Purchase annexes grouped by partner. If this checkbox is selected, the invoice number and date aren't mandatory fields in part B, and amounts are summarized per partner. |
    | Number of cars used for business purposes | Specify the number of cars that were acquired solely (100 percent) for business purposes. If no value is entered, the system collects the number from referenced inventory transactions. |
    | Number of cars used partially for business purposes | Specify the number of cars that were acquired partially for business purposes. If no value is entered, the system collects the number from referenced inventory transactions. |
    | Invoice threshold | Specify the threshold to apply for reporting invoices in Sales annexes and Purchase annexes. Invoices where the amounts are below the specified threshold aren't included in the annexes. |
    | Declaration period type | Select the declaration period type in the list: **Normal period** (the default value) or **Bankruptcy period**. |
    | Submitter person | Select a person who will submit the VAT declaration. |

4. On the **Run in the background** FastTab, specify parameters of the batch processing, and select the **Batch processing** checkbox to run the report in batch mode.
5. Select **OK**, and review the Excel report. When the report is run in batch mode, you can find the generated file as an attachment of the batch job on the **Electronic reporting jobs** page (**Organization administration** \> **Electronic reporting** \> **Electronic reporting jobs**).

### Preview the VAT declaration in Excel from a sales tax payment

Sales tax payment transactions are produced by the [Settle and post sales tax](../../general-ledger/tasks/create-sales-tax-payment.md) job procedure that settles sales tax balances in the sales tax accounts and offsets them to the sales tax settlement account for a given period. After the **Settle and post sales tax** job procedure is completed for an interval of the sales tax settlement period, you can generate the VAT declaration in Excel from the **Sales tax payments** page.

1. Go to **Tax** \> **Inquiries and reports** \> **Sales tax inquiries** \> **Sales tax payments**, and select a sales tax payment line.
2. Select **Print report**, specify report parameters as described in the [Preview the VAT declaration in Excel from the Report sales tax for settlement period periodic task](#report-sales-tax-for-settlement-period) section earlier in this article, and then select **OK**.
3. Review the Excel file that's generated for the selected sales tax payment line.

    > [!NOTE]
    > The report is generated only for the selected line of the sales tax payment. If you must generate, for example, a corrective declaration that contains all corrections for the period, or a replacement declaration that contains original data and all corrections, use the [Report sales tax for settlement period](#report-sales-tax-for-settlement-period) periodic task.

## Generate the electronic file for the VAT declaration from electronic messages

When you use electronic messages to generate the report, you can collect tax data from multiple legal entities. For more information, see the [Run the VAT declaration for multiple legal entities](#run-the-vat-declaration-for-multiple-legal-entities) section later in this article.

The following procedure applies to the electronic message processing example that you [imported earlier from the Lifecycle Services Shared asset library](#import-em).

1. Go to **Tax** \> **Inquiries and reports** \> **Electronic messages** \> **Electronic messages**.
2. In the left pane, select **EE VAT declaration**.
3. On the **Messages** FastTab, select **New**.
4. In the **Run processing** dialog box, the **EE VAT Create message** action is predefined. Select **OK**.
5. Select the message line that's created, enter a description, and then specify the start and end dates for the declaration.
6. On the **Messages** FastTab, select **Collect data**, and then select **OK**. The sales tax payments that were generated earlier because of the [Settle and post sales tax](../../general-ledger/tasks/create-sales-tax-payment.md) job procedure are added to the message.
7. On the **Message items** FastTab, review the sales tax payments that are transferred for processing. By default, all sales tax payments of the selected period that weren't included in any other message of the same processing are included.
8. Optional: Select **Original document** to review the sales tax payments, or select **Delete** to exclude sales tax payments from processing.
9. On the **Messages** FastTab, select **Update status**.
10. In the **Update status** dialog box, select **EE VAT Ready to generate**, and then select **OK**.
11. Verify that the message status is changed to **EE VAT Ready to generate VAT return**.
12. Select **Generate report**.
13. To preview the VAT declaration amounts, in the **Run processing** dialog box, select **EE VAT Preview report**, and then select **OK**.
14. In the **Electronic reporting parameters** dialog box, set the fields as described in the [Preview the VAT declaration in Excel from the Report sales tax for settlement period periodic task](#report-sales-tax-for-settlement-period) section earlier in this article, and then select **OK**.
15. Select the **Attachments** button (paper clip symbol) in the upper-right corner of the page, and then select **Open** to open the file.
16. Review the amounts in the Excel document, and then select **Generate report**.
17. To generate the VAT declaration in TXT format, in the **Run processing** dialog box, select **EE VAT Generate report**, and then select **OK**.
18. In the **Electronic reporting parameters** dialog box, set the fields as described in the [Preview the VAT declaration in Excel from the Report sales tax for settlement period periodic task](#report-sales-tax-for-settlement-period) section, and then select **OK**.
19. Select the **Attachments** button (paper clip symbol) in the upper-right corner of the page, download the file, and use it for your submission to the tax authority.

## Run the VAT declaration for multiple legal entities

To use the formats to report the VAT declaration for a group of legal entities, you must first set up the application-specific parameters of the ER formats for sales tax codes from all required legal entities.

### Set up electronic messages to collect tax data from several legal entities

Follow these steps to set up electronic messages to collect data from multiple legal entities.

1. Go to **Workspaces** \> **Feature management**.
2. Find and select the **Cross-company queries for the populate records actions** feature in the list, and then select **Enable now**.
3. Go to **Tax** \> **Setup** \> **Electronic messages** \> **Populate records actions**.
4. On the **Populate records action** page, select the line for **EE Populate VAT return records**.

    In the **Datasources setup** grid, a new **Company** field is available. For existing records, this field shows the identifier of the current legal entity.

5. In the **Datasources setup** grid, add a line for each additional legal entity that must be included in reporting. For each new line, set the following fields.

    | Field | Description |
    |---|---|
    | Name | Enter a value that will help you understand where this record comes from. For example, enter **VAT payment of Subsidiary 1**. |
    | Message item type | Select **VAT return**. This value is the only value that's available for all the records. |
    | Account type | Select **All**. |
    | Master table name | Specify **TaxReportVoucher** for all the records. |
    | Document number field | Specify **Voucher** for all the records. |
    | Document date field | Specify **TransDate** for all the records. |
    | Document account field | Specify **TaxPeriod** for all the records. |
    | Company | Select the ID of the legal entity. |
    | User query | This checkbox is automatically selected when you define criteria by selecting **Edit query**. |

6. For each new line, select **Edit query**, and specify a related settlement period for the legal entity that's specified in the **Company** field on the line.

    When the setup is completed, the **Collect data** function on the **Electronic messages** page collects sales tax payments from all legal entities that you defined.
