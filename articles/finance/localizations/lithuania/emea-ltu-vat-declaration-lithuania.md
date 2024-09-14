---
title: VAT declaration for Lithuania (FR0600)
description: This article explains how to set up a value-added tax (VAT) declaration for legal entities in Lithuania.
author: liza-golub
ms.date: 04/18/2024
ms.topic: article
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

This article describes how to set up and generate a value-added tax (VAT) declaration for Lithuania in the XML format (FR0600), and how to preview it in Microsoft Excel.

The VAT declaration feature for Lithuania supports filing a VAT return for companies that have [multiple VAT registrations](../global/emea-multiple-vat-registration-numbers.md) and for companies that report as a VAT group in the same system database.

## <a name="vat-declaration-overview"></a>VAT declaration overview

To automatically generate the report, first create enough sales tax codes to keep a separate VAT accounting for each type of operation that's subject to reporting in the VAT declaration for Lithuania. Additionally, in the application-specific parameters of the Electronic reporting (ER) format for the VAT declaration, associate available sales tax transaction attributes (sales tax code, tax classifier) with the lookup result of the **Report field lookup** lookup field. 

In the following table, the **Lookup result** column shows the lookup result that's preconfigured for a specific VAT declaration field in the VAT declaration format. 
Use this information to correctly associate tax transaction attributes with the lookup result and then with the field of the VAT declaration.

| Operation description | FR0600: Tax Base<br>(sum without VAT) | FR0600: VAT amount | Lookup result<br>(ReportFieldLookup) | Lookup result description label EN | Lookup result description label LT |
|---|---|---|---|---|---|
| Sales in Lithuania, VAT 21% | 11 | 29 | DomesticSalesStandardRate | 11/29 Sales in Lithuania, VAT 21% | 11/29 Pardavimai Lietuvoje, kai taikomas 21 proc. PVM tarifas |
| Sales in Lithuania, VAT 9% | 11 | 30 | DomesticSalesReducedRate | 11/30 Sales in Lithuania, VAT 9% | 11/30 Pardavimai Lietuvoje, kai taikomas 9 proc. PVM tarifas |
| Sales in Lithuania, VAT 5% | 11 | 31 | DomesticSalesSecondReducedRate | 11/31 Sales in Lithuania, VAT 5% | 11/31 Pardavimai Lietuvoje, kai taikomas 5 proc. PVM tarifas |
| Sales in Lithuania, when reverse charge VAT is applied Art. 96. | 12 | Not reported | DomesticSalesReverseCharge | 12 Sales in Lithuania, when reverse charge VAT is applied Art. 96. | 12 Pardavimai Lietuvoje, kai taikomas PVMĮ 96 str. (atvirkštinis apmokestinamas) |
| Supply of goods to a EU VAT payer (0% VAT rate is applied, according to VAT Article 49 d. 1) | 18 | Not reported | EUSalesZeroRate | 18 Supply of goods to a EU VAT payer (0% VAT rate is applied, according to VAT Article 49 d. 1) | 18 Prekių tiekimas Europos Sąjungos PVM mokėtojui (taikomas 0 proc. PVM tarifas, pagal PVMĮ 49 str. 1 d.) |
| Triangular trade: phase I | 18 | Not reported | SalesTriangularTradePhaseI | 18 Triangular trade (sales): phase I | 18 Trikampė prekyba: I grandis |
| Triangular trade: phase II | 20 | Not reported | SalesTriangularTradePhaseII | 20 Triangular trade (sales): phase II | 20 Trikampė prekyba: II grandis |
| Export of goods (sales to third countries with 0% VAT rate according to Article 41 of VAT) | 17 | Not reported | Export | 17 Export of goods (sales to third countries with 0% VAT rate according to Article 41 of VAT) | 17 Prekių eksportas (pardavimai į trečiąsias šalis su 0 proc. PVM tarifu pagal PVMĮ 41 str.) |
| Sales that are not subject to VAT according to Articles 20-33 of VAT. | 13 | Not reported | NonTaxableSales | 13 Sales that are not subject to VAT according to Articles 20-33 of VAT. | 13 Pardavimai, kurie neapmokestinami PVM pagal PVMĮ 20-33 str. |
| Sales under the margin charge scheme when the margin is positive, 21% | 16 | 29 | MarginSchemaPositiveStandardRate | 16/29 Sales under the margin charge scheme when the margin is positive, 21% | 16/29 Pardavimai pagal maržos apmokestinimo schemą (kai marža teigiama), 21% |
| Sales under the margin charge scheme when the margin is positive, 9% | 16 | 30 | MarginSchemaPositiveReducedRate | 16/30 Sales under the margin charge scheme when the margin is positive, 9% | 16/30 Pardavimai pagal maržos apmokestinimo schemą (kai marža teigiama), 9% |
| Sales under the margin charge scheme when the margin is positive, 5% | 16 | 31 | MarginSchemaPositiveSecondReducedRate | 16/31 Sales under the margin charge scheme when the margin is positive, 5% | 16/31 Pardavimai pagal maržos apmokestinimo schemą (kai marža teigiama), 5% |
| Sales under the margin charge scheme when the negative margin, 21% | Not reported | Not reported | Not applicable | Not applicable | Not applicable |
| Sales under the margin charge scheme when the negative margin, 9% | Not reported | Not reported | Not applicable | Not applicable | Not applicable |
| Sales under the margin charge scheme when the negative margin, 5% | Not reported | Not reported | Not applicable | Not applicable | Not applicable |
| Sales under the margin charge scheme with 0% | Not reported | Not reported | Not applicable | Not applicable | Not applicable |
| Sales under the margin tax scheme, where the margin is positive and can be applied at 0% VAT rate according to Article 108¹ of VAT. | 16 | Not reported | MarginSchemaPositiveZeroRate | 16 Sales under the margin tax scheme, where the margin is positive and can be applied at 0% VAT rate according to Article 108¹ of VAT. | 16 Pardavimas pagal maržos apmokestinimo schemą (kai marža lygi 0 arba neigiama) |
| Other cases when sales in Lithuania are taxed at 0% VAT rate (Articles 42, 43, 44, 45, 46, 47, 48, 49, Articles 2 and 3 of VAT, Articles 51, 52, 53) | 19 | Not reported | OtherSalesZeroRate | 19 Other cases when sales in Lithuania are taxed at 0% VAT rate (Articles 42, 43, 44, 45, 46, 47, 48, 49, Articles 2 and 3 of VAT, Articles 51, 52, 53) | 19 Kiti atvejai, kai pardavimas Lietuvoje apmokestinamas 0 proc. PVM tarifu (PVMĮ 42, 43, 44, 45, 46, 47, 48, 49 str. 2 ir 3 d., 51, 52, 53 str.) |
| Sales that are not considered a VAT object in Lithuania, if VAT deduction is possible according to Article 58 of VAT. | 20 | Not reported | NonTaxableSalesOutsideLithuania15 | 20 (PVM15) Sales that are not considered a VAT object in Lithuania, if VAT deduction is possible according to Article 58 of VAT. | 20 (PVM15) Pardavimai, kurie laikomi ne PVM objektu Lietuvoje |
| Sales that are not considered a VAT object in Lithuania, if VAT deduction is not possible according to Article 58 of VAT. | 20 | Not reported | NonTaxableSalesOutsideLithuania34 | 20 (PVM34) Sales that are not considered a VAT object in Lithuania, if VAT deduction is not possible according to Article 58 of VAT. | 20 (PVM34) Pardavimai, kurie laikomi ne PVM objektu Lietuvoje |
| Production of tangible fixed assets, 21% VAT rate | 15 | 29 | FixedAssetProduction | 15/29 Production of tangible fixed assets, 21% VAT rate | 15/29 Ilgalaikio turto pasigaminimas, kai apskaičiuojamas 21 proc. PVM tarifas |
| Consumption for private needs, 21% | 14 | 29 | PrivateConsumptionStandardRate | 14/29 Consumption for private needs, 21% | 14/29 Suvartojimas privatiems poreikiams, 21% |
| Consumption for private needs, 9% | 14 | 30 | PrivateConsumptionReducedRate | 14/30 Consumption for private needs, 9% | 14/30 Suvartojimas privatiems poreikiams, 9% |
| Consumption for private needs, 5% | 14 | 31 | PrivateConsumptionSecondReducedRate | 14/31 Consumption for private needs, 5% | 14/31 Suvartojimas privatiems poreikiams, 5% |
| Purchase in Lithuania with VAT 21%, 9%, 5%. | Not reported | 25, 35 | DomesticPurchase | 25/35 Purchase in Lithuania with VAT 21%, 9%, 5% | 25/35 Standartiniai pirkimai Lietuvoje su PVM (21 proc., 9 proc., 5 proc.) |
| Purchase in Lithuania, when reverse charge VAT is applied Art. 96 | Not reported | 25, 33, 35 | DomesticPurchaseReverseCharge | 25/33/35 Purchase in Lithuania, when reverse charge VAT is applied Art. 96 | 25/33/35 Pirkimai Lietuvoje, kai taikomas PVMĮ\* 96 str. (atvirkštinis apmokestinimas) |
| Purchase in Lithuania, 0% VAT (VAT 41, 42, 43, 44, 45,46, 47, 48, 51, 52, 53 str.) | Not reported | Not reported | Not applicable | Not applicable | Not applicable |
| Purchase in Lithuania, when the margin tax scheme is applied | Not reported | Not reported | Not applicable | Not applicable | Not applicable |
| Purchase of goods from EU VAT payers, when there is an obligation to calculate VAT in Lithuania (VAT Article 4¹ and Article 12²) | 21 | 25, 34, 35 | EUPurchaseGoods | 21/34/25/35 Purchase of goods from EU VAT payers, when there is an obligation to calculate VAT in Lithuania (VAT Article 4¹ and Article 12²) | 21/34/25/35 Prekių įsigijimas iš Europos Sąjungos PVM mokėtojų, kai atsiranda prievolė priskaičiuoti PVM Lietuvoje (PVMĮ 4¹ str. ir 12² str.) |
| Import of goods (purchases of goods from third countries) when import VAT is paid to customs | Not reported | 26, 35 | ImportPaid | 26/35 Import of goods (purchases of goods from third countries) when import VAT is paid to customs | 26/35 Prekių importas (prekių įsigijimai iš trečiųjų šalių) - kai importo PVM mokamas muitinei |
| Import of goods (purchases of goods from third countries) when control of import VAT payment is taken over by VMI. | Not reported | 27, 35 | ImportControlledVMI | 27/35 Import of goods (purchases of goods from third countries) when control of import VAT payment is taken over by VMI. | 27/35 Prekių importas (prekių įsigijimai iš trečiųjų šalių) - kai importo PVM mokėjimo kontrolę perima VMI |
| Purchases of services from foreign countries, when 21% VAT is calculated by the buyer (VAT Article 95, Part 2), when the services are purchased from an EU VAT payer. | 23, 24 | 25, 32, 35 | ForeignPurchaseServicesEU | 23/24/32/25/35 Purchases of services from foreign countries, when 21% VAT is calculated by the buyer (VAT Article 95, Part 2), when the services are purchased from an EU VAT payer. | 23/24/32/25/35 Paslaugų įsigijimai iš užsienio valstybių, kai 21 proc. pardavimo PVM apskaičiuoja pirkėjas (PVMĮ 95 str. 2 dalis) - Paslaugos įsigytos iš ES PVM mokėtojo |
| Purchases of services from foreign countries, when 21% VAT is calculated by the buyer (VAT Article 95, Part 2), when the services are purchased from third parties or non-EU VAT payer. | 23 | 25, 32, 35 | ForeignPurchaseServicesNonEU | 23/32/25/35 Purchases of services from foreign countries, when 21% VAT is calculated by the buyer (VAT Article 95, Part 2), when the services are purchased from third parties or non-EU VAT payer. | 23/32/25/35 Paslaugų įsigijimai iš užsienio valstybių, kai 21 proc. pardavimo PVM apskaičiuoja pirkėjas (PVMĮ 95 str. 2 dalis) - Paslaugos įsigytos iš trečiųjų šalių arba ES ne PVM mokėtojo |
| Triangular trade: Phase II | 22 | Not reported | PurchaseTriangularTradePhaseII | 22 Triangular trade (purchase): Phase II | 22 Trikampė prekyba: II grandis |
| Triangular trade: Phase III | Not reported | 25, 32, 35 | PurchaseTriangularTradePhaseIII | 32/25/35 Triangular trade (purchase): Phase III | 32/25/35 Trikampė prekyba: III grandis |
| Cases where the "reserve" rule applies for the purchase of goods from another EU Member State | 21 | 25, 34 | EUPurchaseGoodsReserve | 21/25/34 Cases where the "reserve" rule applies for the purchase of goods from another Member State | 21/25/34 Atvejai, kai dėl prekių įsigijimo iš kitos valstybės narės taikoma „rezervo“ taisyklė |

For more information about how to set up application-specific parameters, see the [Set up application-specific parameters for VAT declaration fields](#set-up) section later in this article.

## Set up the VAT declaration for Lithuania

These tasks will prepare your Dynamics 365 Finance environment to generate the electronic file for the VAT declaration for Lithuania and preview the VAT amounts in Excel format.

- [Import ER configurations](#import-er).
- [Set up application-specific parameters for VAT declaration fields](#set-up).
- [Set up the VAT reporting format to preview amounts in Excel](#setup-preview).
- [Set up electronic messages](#setup-em).
- [Set up the VAT registration number of the company that's reporting VAT](#vat-id).

### <a name="import-er"></a>Import ER configurations

Open the **Electronic reporting** workspace, and import the latest versions of these ER formats under **Tax declaration model**:

- VAT Declaration XML (LT)
- VAT Declaration Excel (LT)

Import **Tax declaration model mapping** under **Tax declaration model**, and mark it **Default for model mapping**.

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

    | Field | Description |
    |---|---|
    | Lookup result | Select the value of the report field. For more information about the values and their assignment to VAT declaration rows, see the [VAT declaration overview](#vat-declaration-overview) section earlier in this article. |
    | Tax code | Select the sales tax code to associate with the report field. Posted tax transactions that use the selected sales tax code will be collected in the appropriate declaration box. We recommend that you separate sales tax codes in such a way that one sales tax code generates amounts in only one declaration box. |
    | Transaction classifier | <p>If you created enough sales tax codes to determine a declaration box, select **\*Not blank\***. If you didn't create enough sales tax codes so that one sales tax code generates amounts in only one declaration box, you can set up a transaction classifier. The following transaction classifiers are available:</p><ul><li>**Purchase**</li><li>**PurchaseExempt** (tax-exempt purchase)</li><li>**PurchaseReverseCharge** (tax receivable from a purchase reverse charge)</li><li>**Sales**</li><li>**SalesExempt** (tax-exempt sale)</li><li>**SalesReverseCharge** (tax payable from a purchase reverse charge or a sales reverse charge)</li><li>**Use tax**</li></ul><p>For each transaction classifier, a classifier for the credit note is also available. For example, one of these classifiers is **PurchaseCreditNote** (purchase credit note).</p><p>Be sure to create two lines for each sales tax code: one that has the transaction classifier value and one that has the transaction classifier for credit note value.</p> |

    > [!NOTE]
    > Associate all sales tax codes (or combinations of a sales tax code and a tax classifier) with lookup results. If any combination should not generate values on the VAT declaration, associate it with the **Other** lookup result.

5. In the **State** field, change the value to **Completed**.
6. On the Action Pane, select **Export** to export the settings of the application-specific parameters.
7. Select the **VAT declaration Excel (LT)** configuration, and then, on the Action Pane, select **Import** to import the parameters that you configured for **VAT declaration XML (LT)**.
8. In the **State** field, select **Completed**.

### <a name="setup-preview"></a>Set up the VAT reporting format to preview amounts in Excel

1. In the **Feature management** workspace, find and select the **VAT statement format reports** feature in the list, and then select **Enable now**.
2. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax authorities**, and select the tax authority.
3. In the **Report layout** field, select **Default**.
4. Go to **General ledger** \> **Setup** \> **General ledger parameters**.
5. On the **Sales tax** tab, on the **Tax options** FastTab, in the **VAT statement format mapping** field, select the **VAT declaration Excel (LT)** ER format. This format is printed when you run the **Report sales tax for settlement period** report. It's also printed when you select **Print** on the **Sales tax payments** page.

If you're configuring the VAT declaration for Lithuania in a legal entity that has [multiple VAT registrations](../global/emea-reporting-for-multiple-vat-registrations.md), follow these steps.

1. Go to **General ledger** \> **Setup** \> **General ledger parameters**.
2. On the **Sales tax** tab, on the **Electronic reporting for countries/regions** FastTab, on the line for **LTU**, select the **VAT Declaration Excel (LT)** ER format.

### <a name="setup-em"></a>Set up electronic messages

Electronic messaging (EM) functionality is provided to maintain the different processes that are used in electronic reporting for different document types. For more information about electronic messages, see [Electronic messaging](../../general-ledger/electronic-messaging.md).

#### <a name="import-em"></a>Download and import the data package that has example settings for electronic messages

The process of setting up the **Electronic messages** functionality to generate the VAT declaration for Lithuania in XML format and preview it in Excel has many steps. Because the data of some entities is used in the ER configurations, use a set of predefined values that are delivered in a package of data entities for the related tables. You can extend these settings or create your own.

> [!NOTE]
> Some records in the data entities in the package include a link to ER configurations. Before you start to import the data entities package, [import ER configurations into Finance](#import-er).

1. In [Microsoft Dynamics Lifecycle Services](https://lcs.dynamics.com/v2), in the Shared asset library, select **Data package** as the asset type, and then download **LT VAT declaration - FR0600 - EM setup v.\#**. The downloaded file is named **LT VAT declaration - FR0600 - EM setup v.\#.zip**. Always download the latest version of the package that's available in Lifecycle Services.
2. In Finance, in the **Data management** workspace, select **Import**.
3. On the **Import** FastTab, in the **Group name** field, enter a name for the job.
4. On the **Selected entities** FastTab, select **Add file**.
5. In the **Add file** dialog box, verify that the **Source data format** field is set to **Package**, select **Upload and add**, and then select the zip file that you downloaded earlier.
6. Select **Close**.
7. After the data entities are uploaded, on the Action Pane, select **Import**.
8. Go to **Tax** \> **Inquiries and reports** \> **Electronic messages** \> **Electronic messages**, and validate the electronic message processing that you imported (**LT VAT declaration**).

For more information about how you can use the data management framework, see [Data management](../../../fin-ops-core/dev-itpro/data-entities/data-entities-data-packages.md).

#### Configure electronic messages

1. Go to **Tax** \> **Setup** \> **Electronic messages** \> **Populate records actions**.
2. Select the line for **LT Populate VAT return records**, and then select **Edit query**.
3. Use the filter to specify the settlement periods to include on the report.
4. If you must report tax transactions from other settlement periods in a different declaration, create a new **Populate records** action, and select the appropriate settlement periods.

You can specify default values for **Deduction percent** and **Main economic activity** parameters of your VAT declaration in additional fields of electronic messages.

1. Go to **Tax** \> **Setup** \> **Electronic messages** \> **Electronic messages processing**, and select the **LT VAT declaration** processing.
2. On the **Message additional fields** FastTab, in the **DeductionPercent** (Kalendorinių metų proporcinis PVM atskaitos procentas) field, define the deduction percent that will be used further in reporting as default value.
3. On the **Message additional fields** FastTab, in the **MainEconomicActivity** (Pagrindinė vykdomos veiklos rūšis) field, define the main economic activity code that will be used further in reporting as default value.
4. Save your changes.

### <a id="vat-id"></a>Set up the registration numbers of the company that's reporting FR0600

The FR0600 form of the VAT declaration in Lithuania includes the following fields to identify the reporting company:

- **Mokesčių mokėtojo identifikacinis numeris (kodas)** = **Taxpayer's identification number (code)** – The identification number (code) of the taxpayer must be entered.
- **PVM mokėtojo kodas** = **VAT payer's number** – The VAT identification number is entered without the "LT" prefix.

Follow these steps to configure the registration numbers of your organization.

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
2. Select the legal entity, and then select **Registration IDs**.
3. Select or create the address in Lithuania, and then, on the **Registration ID** FastTab, select **Add**.
4. In the **Registration type** field, select the registration type that's dedicated to Lithuania and that uses the **VAT ID** registration category.
5. In the **Registration number** field, enter the tax number. This value is reported in the "PVM mokėtojo kodas" field of the VAT declaration.
6. On the **General** tab, in the **Effective** field, enter the date when the number becomes effective.
7. In the **Registration type** field, select the registration type that's dedicated to Lithuania and that uses the **Enterprise ID (COID)** registration category.
8. In the **Registration number** field, enter the tax number. This value is reported in the "Mokesčių mokėtojo identifikacinis numeris (kodas)" field of the VAT declaration.
9. On the **General** tab, in the **Effective** field, enter the date when the number becomes effective.

For more information about how to set up registration categories and registration types, see [Registration IDs](../europe/emea-registration-ids.md).

Follow these steps to define the VAT registration number that EM uses during generation of the VAT declaration for Lithuania.

1. Go to **Tax** \> **Setup** \> **Electronic messages** \> **Electronic messages processing**, and select the **LT VAT declaration** processing.
2. On the **Message additional fields** FastTab, in the **Tax registration number** field, define the VAT registration number that should be used in the VAT declaration for Lithuania.
3. Save your changes.

If the VAT registration number isn't specified in the **Tax registration number** additional field of the **LT VAT declaration** processing, the system retrieves it from the registration ID that's defined in the properties of the legal entity that's associated with the **VAT ID** registration category.

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
    | Report date | Specify the date when report is prepared. |
    | Declaration period type | Select **Initial** to prepare a file for initial submission in the reporting period. Select **Corrected** to prepare a file to submit a corrected VAT declaration. |
    | Contact person | Select a contact person in the lookup list. This parameter is available in XML format only. |
    | Main economic activity code | Specify the main economic activity code for your company. |
    | Deduction percent | Specify the deduction percent for the reporting period. |

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
2. In the left pane, select **LT VAT declaration**.
3. On the **Messages** FastTab, select **New**.
4. In the **Run processing** dialog box, the **LT VAT Create message** action is predefined. Select **OK**.
5. Select the message line that's created, enter a description, and then specify the start and end dates for the declaration.
6. On the **Messages** FastTab, select **Collect data**, and then select **OK**. The sales tax payments that were generated earlier because of the [Settle and post sales tax](../../general-ledger/tasks/create-sales-tax-payment.md) job procedure are added to the message.
7. On the **Message items** FastTab, review the sales tax payments that are transferred for processing. By default, all sales tax payments of the selected period that weren't included in any other message of the same processing are included.
8. Optional: Select **Original document** to review the sales tax payments, or select **Delete** to exclude sales tax payments from processing.
9. On the **Messages** FastTab, select **Update status**.
10. In the **Update status** dialog box, select **LT VAT Ready to generate**, and then select **OK**.
11. Verify that the message status is changed to **LT VAT Ready to generate VAT return**.
12. Select **Generate report**.
13. To preview the VAT declaration amounts, in the **Run processing** dialog box, select **LT VAT Preview report**, and then select **OK**.
14. In the **Electronic reporting parameters** dialog box, set the fields as described in the [Preview the VAT declaration in Excel from the Report sales tax for settlement period periodic task](#report-sales-tax-for-settlement-period) section earlier in this article, and then select **OK**.
15. Select the **Attachments** button (paper clip symbol) in the upper-right corner of the page, and then select **Open** to open the file.
16. Review the amounts in the Excel document, and then select **Generate report**.
17. To generate the VAT declaration in XML format, in the **Run processing** dialog box, select **LT VAT Generate report**, and then select **OK**.
18. In the **Electronic reporting parameters** dialog box, set the fields as described in the [Preview the VAT declaration in Excel from the Report sales tax for settlement period periodic task](#report-sales-tax-for-settlement-period) section, and then select **OK**.
19. Select the **Attachments** button (paper clip symbol) in the upper-right corner of the page, download the file, and use it for your submission to the tax authority.

## Run the VAT declaration for multiple legal entities

To use the formats to report the VAT declaration for a group of legal entities, you must first set up the application-specific parameters of the ER formats for sales tax codes from all required legal entities.

### Set up electronic messages to collect tax data from several legal entities

Follow these steps to set up electronic messages to collect data from multiple legal entities.

1. Go to **Workspaces** \> **Feature management**.
2. Find and select the **Cross-company queries for the populate records actions** feature in the list, and then select **Enable now**.
3. Go to **Tax** \> **Setup** \> **Electronic messages** \> **Populate records actions**.
4. On the **Populate records action** page, select the line for **LT Populate VAT return records**.

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
