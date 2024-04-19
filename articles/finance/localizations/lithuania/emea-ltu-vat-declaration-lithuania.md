---
title: VAT declaration for Lithuania
description: This article explains how to set up a VAT declaration for legal entities in Lithuania.
author: liza-golub
ms.date: 04/18/2024
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: johnmichalak
ms.search.region: Lithuania
ms.author: egolub
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1
ms.search.form: TaxAuthority, TaxReportCollection, TaxReportVoucher, TaxTable
---

# VAT declaration for Lithuania (FR0600)

[!include [banner](../../includes/banner.md)]

This article describes how to set up and generate a value-added tax (VAT) declaration for Lithuania in the XML format (FR0600) and how to preview it in Microsoft Excel.

The VAT declaration feature for Lithuania supports filing a VAT return for companies with [multiple VAT registrations](../global/emea-multiple-vat-registration-numbers.md) and for companies that report as a VAT group in the same system database.

## <a name="vat-declaration-overview"></a> VAT declaration overview

To automatically generate the report, first create enough sales tax codes to keep a separate VAT accounting for each type of operation that's subject to reporting in the VAT declaration for Lithuania. 
Additionally, in the application-specific parameters of the Electronic reporting (ER) format for the VAT declaration, associate available sales tax transaction attributes 
(sales tax code, tax classifier) with the lookup result of the **Report field lookup** lookup field. 
In the following table, the "Lookup result" column shows the lookup result that's preconfigured for a specific VAT declaration field in the VAT declaration format. 
Use this information to correctly associate tax transaction attributes with the lookup result and then with the field of the VAT declaration.

| **Operation description**      | **FR0600: Tax Base**<br><br>**(sum without VAT)** | **FR0600: VAT amount** | **Lookup result <br>(ReportFieldLookup)** | **Lookup result description label EN** | **Lookup result description label LT** |
| ------------------------------- | --- | --- | --- | --- | --- |
| Sales in Lithuania, VAT 21%     | 11  | 29  | DomesticSalesStandardRate | 11/29 Sales in Lithuania, VAT 21% | 11/29 Pardavimai Lietuvoje, kai taikomas 21 proc. PVM tarifas |
| Sales in Lithuania, VAT 9%      | 11  | 30  | DomesticSalesReducedRate | 11/30 Sales in Lithuania, VAT 9% | 11/30 Pardavimai Lietuvoje, kai taikomas 9 proc. PVM tarifas |
| Sales in Lithuania, VAT 5%      | 11  | 31  | DomesticSalesSecondReducedRate | 11/31 Sales in Lithuania, VAT 5% | 11/31 Pardavimai Lietuvoje, kai taikomas 5 proc. PVM tarifas |
| Sales in Lithuania, when reverse charge VAT is applied Art. 96. | 12  | not reported | DomesticSalesReverseCharge | 12 Sales in Lithuania, when reverse charge VAT is applied Art. 96. | 12 Pardavimai Lietuvoje, kai taikomas PVMĮ 96 str. (atvirkštinis apmokestinamas) |
| Supply of goods to a EU VAT payer (0% VAT rate is applied, according to VAT Article 49 d. 1) | 18  | not reported | EUSalesZeroRate | 18 Supply of goods to a EU VAT payer (0% VAT rate is applied, according to VAT Article 49 d. 1) | 18 Prekių tiekimas Europos Sąjungos PVM mokėtojui (taikomas 0 proc. PVM tarifas, pagal PVMĮ 49 str. 1 d.) |
| Triangular trade: phase I       | 18  | not reported | SalesTriangularTradePhaseI | 18 Triangular trade (sales): phase I | 18 Trikampė prekyba: I grandis |
| Triangular trade: phase II      | 20  | not reported | SalesTriangularTradePhaseII | 20 Triangular trade (sales): phase II | 20 Trikampė prekyba: II grandis |
| Export of goods (sales to third countries with 0% VAT rate according to Article 41 of VAT) | 17<br><br>&nbsp; | not reported | Export | 17 Export of goods (sales to third countries with 0% VAT rate according to Article 41 of VAT) | 17 Prekių eksportas (pardavimai į trečiąsias<br><br>šalis su 0 proc. PVM tarifu pagal PVMĮ 41 str.) |
| Sales that are not subject to VAT according to Articles 20-33 of VAT. | 13  | not reported | NonTaxableSales | 13 Sales that are not subject to VAT according to Articles 20-33 of VAT. | 13 Pardavimai, kurie neapmokestinami PVM pagal PVMĮ 20-33 str. |
| Sales under the margin charge scheme when the margin is positive, 21% | 16  | 29  | MarginSchemaPositiveStandardRate | 16/29 Sales under the margin charge scheme when the margin is positive, 21% | 16/29 Pardavimai pagal maržos apmokestinimo schemą (kai marža teigiama), 21% |
| Sales under the margin charge scheme when the margin is positive, 9% | 16  | 30  | MarginSchemaPositiveReducedRate | 16/30 Sales under the margin charge scheme when the margin is positive, 9% | 16/30 Pardavimai pagal maržos apmokestinimo schemą (kai marža teigiama), 9% |
| Sales under the margin charge scheme when the margin is positive, 5% | 16  | 31  | MarginSchemaPositiveSecondReducedRate | 16/31 Sales under the margin charge scheme when the margin is positive, 5% | 16/31 Pardavimai pagal maržos apmokestinimo schemą (kai marža teigiama), 5% |
| Sales under the margin charge scheme when the negative margin, 21% | not reported | not reported | n/a | n/a | n/a |
| Sales under the margin charge scheme when the negative margin, 9% | not reported | not reported | n/a | n/a | n/a |
| Sales under the margin charge scheme when the negative margin, 5% | not reported | not reported | n/a | n/a | n/a |
| Sales under the margin charge scheme with 0% | not reported | not reported | n/a | n/a | n/a |
| Sales under the margin tax scheme, where the margin is positive and can be applied at 0% VAT rate according to Article 108¹ of VAT. | 16  | not reported | MarginSchemaPositiveZeroRate | 16 Sales under the margin tax scheme, where the margin is positive and can be applied at 0% VAT rate according to Article 108¹ of VAT. | 16 Pardavimas pagal maržos apmokestinimo schemą (kai marža lygi 0 arba neigiama) |
| Other cases when sales in Lithuania are taxed at 0% VAT rate (Articles 42, 43, 44, 45, 46, 47, 48, 49, Articles 2 and 3 of VAT, Articles 51, 52, 53) | 19  | not reported | OtherSalesZeroRate | 19 Other cases when sales in Lithuania are taxed at 0% VAT rate (Articles 42, 43, 44, 45, 46, 47, 48, 49, Articles 2 and 3 of VAT, Articles 51, 52, 53) | 19 Kiti atvejai, kai pardavimas Lietuvoje apmokestinamas 0 proc. PVM tarifu (PVMĮ 42, 43, 44, 45, 46, 47, 48, 49 str. 2 ir 3 d., 51, 52, 53 str.) |
| Sales that are not considered a VAT object in Lithuania, if VAT deduction is possible according to Article 58 of VAT. | 20  | not reported | NonTaxableSalesOutsideLithuania15 | 20 (PVM15) Sales that are not considered a VAT object in Lithuania, if VAT deduction is possible according to Article 58 of VAT. | 20 (PVM15) Pardavimai, kurie laikomi ne PVM objektu Lietuvoje |
| Sales that are not considered a VAT object in Lithuania, if VAT deduction is not possible according to Article 58 of VAT. | 20  | not reported | NonTaxableSalesOutsideLithuania34 | 20 (PVM34) Sales that are not considered a VAT object in Lithuania, if VAT deduction is not possible according to Article 58 of VAT. | 20 (PVM34) Pardavimai, kurie laikomi ne PVM objektu Lietuvoje |
| Production of tangible fixed assets, 21% VAT rate | 15  | 29, 25, 35<br><br> | FixedAssetProduction | 15/29/25/35 Production of tangible fixed assets, 21% VAT rate | 15/29/25/35 Ilgalaikio turto pasigaminimas, kai apskaičiuojamas 21 proc. PVM tarifas |
| Consumption for private needs, 21% | 14  | 29  | PrivateConsumptionStandardRate | 14/29 Consumption for private needs, 21% | 14/29 Suvartojimas privatiems poreikiams, 21% |
| Consumption for private needs, 9% | 14  | 30  | PrivateConsumptionReducedRate | 14/30 Consumption for private needs, 9% | 14/30 Suvartojimas privatiems poreikiams, 9% |
| Consumption for private needs, 5% | 14  | 31  | PrivateConsumptionSecondReducedRate | 14/31 Consumption for private needs, 5% | 14/31 Suvartojimas privatiems poreikiams, 5% |
| Purchase in Lithuania with VAT 21%, 9%, 5%. | not reported | 25, 35 | DomesticPurchase | 25/35 Purchase in Lithuania with VAT 21%, 9%, 5% | 25/35 Standartiniai pirkimai Lietuvoje su PVM (21 proc., 9 proc., 5 proc.) |
| Purchase in Lithuania, when reverse charge VAT is applied Art. 96 | not reported | 25, 33, 35 | DomesticPurchaseReverseCharge | 25/33/35 Purchase in Lithuania, when reverse charge VAT is applied Art. 96 | 25/33/35 Pirkimai Lietuvoje, kai taikomas PVMĮ\* 96 str. (atvirkštinis apmokestinimas) |
| Purchase in Lithuania, 0% VAT (VAT 41, 42, 43, 44, 45,46, 47, 48, 51, 52, 53 str.) | not reported | not reported | n/a | n/a | n/a |
| Purchase in Lithuania, when the margin tax scheme is applied | not reported | not reported | n/a | n/a | n/a |
| Purchase of goods from EU VAT payers, when there is an obligation to calculate VAT in Lithuania (VAT Article 4¹ and Article 12²) | 21  | 25, 34, 35<br><br> | EUPurchaseGoods | 21/34/25/35 Purchase of goods from EU VAT payers, when there is an obligation to calculate VAT in Lithuania (VAT Article 4¹ and Article 12²) | 21/34/25/35 Prekių įsigijimas iš Europos Sąjungos PVM mokėtojų, kai atsiranda prievolė priskaičiuoti PVM Lietuvoje (PVMĮ 4¹ str. ir 12² str.) |
| Import of goods (purchases of goods from third countries) when import VAT is paid to customs | not reported | 26, 35  | ImportPaid | 26/35 Import of goods (purchases of goods from third countries) when import VAT is paid to customs | 26/35 Prekių importas (prekių įsigijimai iš trečiųjų šalių) - kai importo PVM mokamas muitinei |
| Import of goods (purchases of goods from third countries) when control of import VAT payment is taken over by VMI. | not reported | 27, 35<br><br> | ImportControlledVMI | 27/35 Import of goods (purchases of goods from third countries) when control of import VAT payment is taken over by VMI. | 27/35 Prekių importas (prekių įsigijimai iš trečiųjų šalių) - kai importo PVM mokėjimo kontrolę perima VMI |
| Purchases of services from foreign countries, when 21% VAT is calculated by the buyer (VAT Article 95, Part 2), when the services are purchased from an EU VAT payer. | 23, 24 | 25, 32, 35<br><br> | ForeignPurchaseServicesEU | 23/24/32/25/35 Purchases of services from foreign countries, when 21% VAT is calculated by the buyer (VAT Article 95, Part 2), when the services are purchased from an EU VAT payer. | 23/24/32/25/35 Paslaugų įsigijimai iš užsienio valstybių, kai 21 proc. pardavimo PVM apskaičiuoja pirkėjas (PVMĮ 95 str. 2 dalis) - Paslaugos įsigytos iš ES PVM mokėtojo |
| Purchases of services from foreign countries, when 21% VAT is calculated by the buyer (VAT Article 95, Part 2), when the services are purchased from third parties or non-EU VAT payer. | 23  | 25, 32, 35<br><br> | ForeignPurchaseServicesNonEU | 23/32/25/35 Purchases of services from foreign countries, when 21% VAT is calculated by the buyer (VAT Article 95, Part 2), when the services are purchased from third parties or non-EU VAT payer. | 23/32/25/35 Paslaugų įsigijimai iš užsienio valstybių, kai 21 proc. pardavimo PVM apskaičiuoja pirkėjas (PVMĮ 95 str. 2 dalis) - Paslaugos įsigytos iš trečiųjų šalių arba ES ne PVM mokėtojo |
| Triangular trade: Phase II | 22  | not reported | PurchaseTriangularTradePhaseII | 22 Triangular trade (purchase): Phase II | 22 Trikampė prekyba: II grandis |
| Triangular trade: Phase III | not reported | 25, 32, 35<br><br> | PurchaseTriangularTradePhaseIII | 32/25/35 Triangular trade (purchase): Phase III | 32/25/35 Trikampė prekyba: III grandis |
| Cases where the "reserve" rule applies for the purchase of goods from another EU Member State | 21  | 25, 34 | EUPurchaseGoodsReserve | 21/25/34 Cases where the "reserve" rule applies for the purchase of goods from another Member State | 21/25/34 Atvejai, kai dėl prekių įsigijimo iš kitos valstybės narės taikoma „rezervo“ taisyklė |

For more information about how to set up application-specific parameters, see the [Set up application-specific parameters for VAT declaration fields](#set-up) section later in this article.

## Set up the VAT declaration for Lithuania

These tasks will prepare your Finance environment to generate the electronic file for the VAT declaration for Lithuania and preview the VAT amounts in Excel format.

- [Import ER configurations](#import-er).
- [Set up application-specific parameters for VAT declaration fields](#set-up).
- [Set up the VAT reporting format to preview amounts in Excel](#setup-preview).
- [Set up electronic messages](#setup-em).
- [Set up the VAT registration number of the company that's reporting VAT](#vat-id).

### <a name="import-er"></a>Import ER configurations

Open the **Electronic reporting** workspace, and import the latest versions of these ER formats under **Tax declaration model**:

- VAT Declaration XML (LT)
- VAT Declaration Excel (LT)

For more information, see [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

### <a name="set-up"></a>Set up application-specific parameters for VAT declaration fields

To automatically generate the VAT declaration, associate available sales tax transaction attributes (sales tax code, tax classifier) in Finance and lookup results in the ER configuration.

> [!NOTE]
> We recommend that you enable the **Use application specific parameters from previous versions of ER formats** feature in the **Feature management** workspace. When this feature is enabled, parameters that are configured for an earlier version of an ER format automatically become applicable for a later version of the same format. If this feature isn't enabled, you must explicitly configure application-specific parameters for each format version. The **Use application specific parameters from previous versions of ER formats** feature is available in the **Feature management** workspace as of Finance version 10.0.23. For more information about how to set up the parameters of an ER format for each legal entity, see [Set up the parameters of an ER format per legal entity](../../../fin-ops-core/dev-itpro/analytics/er-app-specific-parameters-set-up.md).

Follow these steps to define which of the available sales tax transaction attributes (sales tax code, tax classifier) in Finance generates which field of the VAT declaration for Lithuania.

1. Go to **Workspaces** \> **Electronic reporting**, and select **Reporting configurations**.
2. Select the **VAT declaration XML (LT)** configuration, and then, on the Action Pane, select **Configurations** \> **Application specific parameters setup**.
3. On the **Application specific parameters** page, on the **Lookups** FastTab, select **Report field lookup**.
4. On the **Conditions** FastTab, set the following fields to associate the sales tax codes and report fields.

    | Field     | Description |
    |-----------|---|
    | **Lookup result** | Select the value of the report field. For more information about the values and their assignment to VAT declaration rows, see the [VAT declaration overview](#vat-declaration-overview) section earlier in this article. |
    | **Tax code**  | Select the sales tax code to associate with the report field. Posted tax transactions that use the selected sales tax code will be collected in the appropriate declaration box. We recommend that you separate sales tax codes in such a way that one sales tax code generates amounts in only one declaration box. |
    | **Transaction classifier** | <p>If you created enough sales tax codes to determine a declaration box, select **\*Not blank\***. If you didn't create enough sales tax codes so that one sales tax code generates amounts in only one declaration box, you can set up a transaction classifier. The following transaction classifiers are available:</p><ul><li>**Purchase**</li><li>**PurchaseExempt** (tax-exempt purchase)</li><li>**PurchaseReverseCharge** (tax receivable from a purchase reverse charge)</li><li>**Sales**</li><li>**SalesExempt** (tax-exempt sale)</li><li>**SalesReverseCharge** (tax payable from a purchase reverse charge or a sales reverse charge)</li><li>**Use tax**</li></ul><p>For each transaction classifier, a classifier for the credit note is also available. For example, one of these classifiers is **PurchaseCreditNote** (purchase credit note).</p><p>Be sure to create two lines for each sales tax code: one that has the transaction classifier value and one that has the transaction classifier for credit note value.</p> |

    > [!NOTE]
    > Associate all sales tax codes (or combinations of a sales tax code, tax classifier) with lookup results. If any combination should not generate values on the VAT declaration, associate it with the **Other** lookup result.

5. In the **State** field, change the value to **Completed**.
6. On the Action Pane, select **Export** to export the settings of the application-specific parameters.
7. Select the **VAT declaration Excel (LT)** configuration, and then, on the Action Pane, select **Import** to import the parameters that you configured for **VAT declaration XML (LT)**.
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


## Set up sales tax authorities

To generate a VAT declaration in the required format for the appropriate tax authority, you must set up the report layout for sales tax authorities. 
On the **Sales tax authorities** page, in the **Report layout** field, select **Default**. Select the same sales tax authority for the sales tax settlement period that will be used for sales tax codes.
