---
title: VAT declaration (Finland)
description: Learn how to set up and generate a value-added tax (VAT) declaration for Finland, including a table that defines various field IDs.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: article
ms.date: 11/03/2023
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Finland
ms.search.validFrom: 
ms.dyn365.ops.version: 
---

# VAT declaration (Finland)

[!include [banner](../../includes/banner.md)]

This article describes how to set up and generate a value-added tax (VAT) declaration for Finland in the official TXT format. It also describes how to preview the VAT declaration in Microsoft Excel.

To automatically generate the report, first create enough sales tax codes to keep a separate VAT accounting for each type of operation that is subject to reporting in the VAT declaration for Finland. Additionally, in the application-specific parameters of the Electronic reporting (ER) format for the VAT declaration, associate sales tax codes with the lookup result of the **Report field lookup** lookup field. In the following table, the "Lookup result" column shows the lookup result that is preconfigured for a specific VAT declaration field ID in the VAT declaration format. Use this information to correctly associate sales tax codes with the lookup result and then with the field ID of the VAT declaration.

## VAT declaration overview

The VAT declaration for Finland contains the following fields that are used to report VAT-related amounts.

| Field ID (Tunnus) | Description (English) | Description (Finnish) | Lookup result |
|---|---|---|---|
| 301 | Tax on domestic sales at a standard tax rate. | Kotimaan verollinen myynti yleisellä verokannalla | DomesticSalesStandardRate |
| 302 | Tax on domestic sales at a higher reduced tax rate. | Kotimaan verollinen myynti suuremman alennetun verokannan mukaan | DomesticSalesHigherReducedRate |
| 303 | Tax on domestic sales at a lower reduced tax rate. | Kotimaan verollinen myynti pienemmän alennetun verokannan mukaan | DomesticSalesLowerReducedRate |
| 304 | Tax on the import of goods from outside the European Union (EU). | Vero tavaroiden maahantuonnista EU:n ulkopuolelta | <p>ImportsOfGoods</p><p>ImportsOfGoodsUseTax (when the **Use tax** option is used)</p> |
| 305 | Tax on goods purchased from other EU member states. | Vero tavaraostoista muista EU-maista | <p>GoodsPurchasedFromEU</p><p>GoodsPurchasedFromEUUseTax (when the **Use tax** option is used)</p> |
| 306 | Tax on services purchased from other EU member states. | Vero palveluostoista muista EU-maista | <p>ServicesPurchasedFromEU</p><p>ServicesPurchasedFromEUUseTax (when the **Use tax** option is used)</p> |
| 307 | Tax deductible for the tax period. | Verokauden vähennettävä vero | <p>Deductible</p><p>When the **Use tax** option is used:</p><ul><li>GoodsPurchasedFromEUUseTax</li><li>ImportsOfGoodsUseTax</li><li>PurchasesReverseChargeUseTax</li><li>ServicesPurchasedFromEUUseTax</li></ul> |
| 308 | Tax payable/Negative tax that qualifies for refund (‒). | Maksettava vero / Palautukseen oikeuttava vero (-) | Not applicable. The amount is automatically calculated. |
| 309 | Turnover taxable at a VAT rate of 0 (zero). | 0-verokannan alainen liikevaihto | TaxableSalesZero |
| 310 | Imports of goods from outside the EU. | Tavaroiden maahantuonnit EU:n ulkopuolelta | <p>ImportsOfGoods</p><p>ImportsOfGoodsUseTax (when the **Use tax** option is used)</p> |
| 311 | Sales of goods to other EU member states. | Tavaroiden myynnit muihin EU-maihin | EUSalesOfGoods |
| 312 | Sales of services to other EU member states. | Palveluiden myynnit muihin EU-maihin | EUSalesOfServices |
| 313 | Purchases of goods from other EU member states. | Tavaraostot muista EU-maista | <p>GoodsPurchasedFromEU</p><p>GoodsPurchasedFromEUUseTax (when the **Use tax** option is used)</p> |
| 314 | Purchases of services from other EU member states. | Palveluostot muista EU-maista | <p>ServicesPurchasedFromEU</p><p>ServicesPurchasedFromEUUseTax (when the **Use tax** option is used)</p> |
| 315 | Turnover that qualifies for VAT relief. | Alarajahuojennukseen oikeuttava liikevaihto | Not applicable. The amount is filled in by using the **VAT relief - sales amount** user input parameter in the report dialog box. |
| 316 | Tax that qualifies for VAT relief. | Alarajahuojennukseen oikeuttava vero | Not applicable. The amount is filled in by using the **VAT relief - tax amount** user input parameter in the report dialog box. |
| 317 | The amount of VAT relief. | Alarajahuojennuksen määrä | Not applicable. The amount is automatically calculated. |
| 318 | Tax on purchases of construction services and scrap metal (reverse charge). | Vero rakentamispalvelun ja metalliromun ostoista | <p>PurchasesReverseCharge</p><p>PurchasesReverseChargeUseTax (when the **Use tax** option is used)</p> |
| 319 | Sales of construction services and scrap metal (reverse charge). | Rakentamispalvelun ja metalliromun myynnit | SalesReverseCharge |
| 320 | Purchases of construction services and scrap metal (reverse charge). | Rakentamispalvelun ja metalliromun ostot | <p>PurchasesReverseCharge</p><p>PurchasesReverseChargeUseTax (when the **Use tax** option is used)</p> |

For more information about how to configure reverse charge VAT, see [Reverse charges](../global/emea-reverse-charge.md).

For more information about how to set up application-specific parameters, see the [Set up application-specific parameters for VAT declaration fields](#set-up) section later in this article.

## Set up the VAT declaration for Finland

These tasks will prepare your Microsoft Dynamics 365 Finance environment to generate the electronic file for the VAT declaration for Finland and preview the VAT amounts in Excel format.

- [Import ER configurations](#import-er).
- [Set up application-specific parameters for VAT declaration fields](#set-up).
- [Set up the VAT reporting format to preview amounts in Excel](#setup-preview).
- [Set up electronic messages](#setup-em).
- [Set up the VAT registration number of the company that is reporting VAT](#vat-id).

### <a name="import-er"></a>Import ER configurations

Open the **Electronic reporting** workspace, and import the latest versions of these ER formats under **Tax declaration model**:

- VAT Declaration TXT (FI)
- VAT Declaration Excel (FI)

For more information, see [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

### <a name="set-up"></a>Set up application-specific parameters for VAT declaration fields

To automatically generate the VAT declaration, associate sales tax codes in Finance and lookup results in the ER configuration.

> [!NOTE]
> We recommend that you enable the **Use application specific parameters from previous versions of ER formats** feature in the **Feature management** workspace. When this feature is enabled, parameters that are configured for an earlier version of an ER format automatically become applicable for a later version of the same format. If this feature isn't enabled, you must explicitly configure application-specific parameters for each format version. The **Use application specific parameters from previous versions of ER formats** feature is available in the **Feature management** workspace as of Finance version 10.0.23. For more information about how to set up the parameters of an ER format for each legal entity, see [Set up the parameters of an ER format per legal entity](../../../fin-ops-core/dev-itpro/analytics/er-app-specific-parameters-set-up.md).

Follow these steps to define which sales tax codes in your Finance generate which field ID on the VAT declaration for Finland.

1. Go to **Workspaces** \> **Electronic reporting**, and select **Reporting configurations**.
2. Select the **VAT declaration TXT (FI)** configuration, and then, on the Action Pane, select **Configurations \> Application specific parameters setup**.
3. On the **Application specific parameters** page, on the **Lookups** FastTab, select **Report field lookup**.
4. On the **Conditions** FastTab, set the following fields to associate the sales tax codes and report fields.


    | Field | Description |
    |---|---|
    | Lookup result | Select the value of the report field. For more information about the values and their assignment to VAT declaration rows, see the [VAT declaration overview](#vat-declaration-overview) section earlier in this article. |
    | Tax code | Select the sales tax code to associate with the report field. Posted tax transactions that use the selected sales tax code will be collected in the appropriate declaration box. We recommend that you separate sales tax codes in such a way that one sales tax code generates amounts in only one declaration box. |
    | Transaction classifier | <p>If you created enough sales tax codes to determine a declaration box, select **\*Not blank\***. If you didn't create enough sales tax codes so that one sales tax code generates amounts in only one declaration box, you can set up a transaction classifier. The following transaction classifiers are available:</p><ul><li>**Purchase**</li><li>**PurchaseExempt** (tax-exempt purchase)</li><li>**PurchaseReverseCharge** (tax receivable from a purchase reverse charge)</li><li>**Sales**</li><li>**SalesExempt** (tax-exempt sale)</li><li>**SalesReverseCharge** (tax payable from a purchase reverse charge or a sales reverse charge)</li><li>**Use tax**</li></ul><p>For each transaction classifier, a classifier for the credit note is also available. For example, one of these classifiers is **PurchaseCreditNote** (purchase credit note).</p><p>Be sure to create two lines for each sales tax code: one that has the transaction classifier value and one that has the transaction classifier for credit note value.</p> |

    > [!NOTE]
    > Associate all sales tax codes with lookup results. If any sales tax codes should not generate values on the VAT declaration, associate them with the **Other** lookup result.

5. In the **State** field, change the value to **Completed**.
6. On the Action Pane, select **Export** to export the settings of the application-specific parameters.
7. Select the **VAT declaration Excel (FI)** configuration, and then, on the Action Pane, select **Import** to import the parameters that you configured for **VAT declaration TXT (FI)**.
8. In the **State** field, select **Completed**.

In Finland, for ER formats for the VAT declaration that are based on **Tax declaration model mapping**, it's crucial that the tax directions of the tax transactions are posted in the relevant reporting period.

When positive and negative lines are posted in the same document in the general journal, if the document is a customer invoice, the **Sales tax payable** direction is used by default, and both transactions contribute in the same box (for example, box \[303\]). If the negative tax transaction must be reported in box \[307\], the following settings are recommended:

- In the settings of the main account that's used on the negative line, define the **Legal entity overrides** rule for sales tax so that it applies the **Sales tax receivable** tax direction.
- On the **General** tab of the general journal for the negative line, enable the **Sales tax direction** parameter.
- Validate that, for this line, the sales tax transaction has the **Sales tax receivable** tax direction.

When the journal line is posted with the **Sales tax receivable** tax direction, if the relevant tax code and **Purchase** transaction classifier are set up for box \[307\] in the application-specific parameters of the format, the amount from the negative line is reported in box \[307\].

### <a name="setup-preview"></a>Set up the VAT reporting format to preview amounts in Excel

1. In the **Feature management** workspace, find and select the **VAT statement format reports** feature in the list, and then select **Enable now**.
2. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax authorities**, and select the tax authority.
3. In the **Report layout** field, select **Default**.
4. Go to **General ledger** \> **Setup** \> **General ledger parameters**.
5. On the **Sales tax** tab, on the **Tax options** FastTab, in the **VAT statement format mapping** field, select the **VAT declaration Excel (FI)** ER format.

    This format is printed when you run the **Report sales tax for settlement period** report. It's also printed when you select **Print** on the **Sales tax payments** page.

6. If you must report the corrections, on the **Special report** section, set **Include corrections** to **Yes**.

If you're configuring the VAT declaration for Finland in a legal entity that has [multiple VAT registrations](../global/emea-reporting-for-multiple-vat-registrations.md),
follow these steps.

1. Go to **General ledger** \> **Setup** \> **General ledger parameters**.
2. On the **Sales tax** tab, on the **Electronic reporting for countries/regions** FastTab, on the line for **FIN**, select the **VAT Declaration Excel (FI)** ER format.

### <a name="setup-em"></a>Set up electronic messages

Electronic messaging (EM) functionality is provided to maintain the different processes that are used in electronic reporting for different document types. For more information about electronic messages, see [Electronic messaging](../../general-ledger/electronic-messaging.md).

#### <a name="import-em"></a>Download and import the data package that has example settings for electronic messages

The process of setting up the Electronic messages functionality to generate the VAT declaration for Finland in TXT format and preview it in Excel has many steps. Because the data of some entities is used in the ER configurations, use a set of predefined values that are delivered in a package of data entities for the related tables. You can extend these settings or create your own.

> [!NOTE]
> Some records in the data entities in the package include a link to ER configurations. Before you start to import the data entities package, [import ER configurations into Finance](#import-er).

1. In [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/v2), in the Shared asset library, select **Data package** as the asset type, and then download **FI VAT declaration EM package**. The downloaded file is named **FI VAT declaration EM package.zip**.
2. In Finance, in the **Data management** workspace, select **Import**.
3. On the **Import** FastTab, in the **Group name** field, enter a name for the job.
4. On the **Selected entities** FastTab, select **Add file**.
5. In the **Add file** dialog box, verify that the **Source data format** field is set to **Package**, select **Upload and add**, and then select the zip file that you downloaded earlier.
6. Select **Close**.
7. After the data entities are uploaded, on the Action Pane, select **Import**.
8. Go to **Tax** \> **Inquiries and reports** \> **Electronic messages** \> **Electronic messages**, and validate the electronic message processing that you imported (**FI VAT declaration**).

For more information about how you can use the data management framework, see [Data management](../../../fin-ops-core/dev-itpro/data-entities/data-entities-data-packages.md).

#### Configure electronic messages

1. Go to **Tax** \> **Setup** \> **Electronic messages** \> **Populate records actions**.
2. Select the line for **FI Populate VAT return records**, and then select **Edit query**.
3. Use the filter to specify the settlement periods to include on the report.
4. If you must report tax transactions from other settlement periods in a different declaration, create a new **Populate records** action, and select the appropriate settlement periods.

### <a id="vat-id"></a>Set up the VAT registration number of the company that is reporting VAT

To generate the VAT declaration, you must configure the tax registration number of your organization (field 010, "Asiakkaan y-tunnus tai henkilötunnus").

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
2. Select the legal entity, and then select **Registration IDs**.
3. Select or create the address in Finland, and then, on the **Registration ID** FastTab, select **Add**.
4. In the **Registration type** field, select the registration type that is dedicated to Finland and that uses the **VAT ID** registration category.
5. In the **Registration number** field, enter the tax number.
6. On the **General** tab, in the **Effective** field, enter the date when the number becomes effective.

For more information about how to set up registration categories and registration types, see [Registration IDs](../europe/emea-registration-ids.md).

Follow these steps to define the VAT registration number that EM uses during generation of the VAT declaration for Finland.

1. Go to **Tax** \> **Setup** \> **Electronic messages** \> **Electronic messages processing**, and select the **FI VAT declaration** processing.
2. On the **Message additional fields** FastTab, in the **Tax registration number** field, define the VAT registration number that should be used in the VAT declaration for Finland.
3. Save your changes.

If the VAT registration number isn't specified in the **Tax registration number** additional field of the **FI VAT declaration** processing, the system retrieves it from the registration ID that is defined in the properties of the legal entity that is associated with the **VAT ID** registration category.

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
    | VAT relief - sales amount | Specify the amount of sales that qualify for VAT relief. |
    | VAT relief - tax amount | Specify the amount of tax that qualifies for VAT relief. |
    | VAT relief - reason | <p>**Note:** VAT relief can be requested only for the final tax period of the accounting year, the final quarter of the calendar year, and the period when the VAT taxpayer's obligation is ended.</p><p>Select the reason why you're requesting VAT relief:</p><ul><li>**1** – This tax period is the final tax period of the accounting year.</li><li>**2** – This quarter is the final quarter of the calendar year.</li><li>**3** – Your VAT obligation ended during this tax period.</li><li>**0** – No relief is requested (default value).</li></ul> |
    | Accounting for VAT on cash basis | Set this option to **Yes** if VAT is being accounted for on a cash basis. |
    | Correction reasons | Select one or more correction reasons as required. |
    | Contact person | Select the contact person. |

4. Select **OK**, and review the Excel report.

### Preview the VAT declaration in Excel from a sales tax payment

Sales tax payment transaction are produced by the [Settle and post sales tax](../../general-ledger/tasks/create-sales-tax-payment.md) job procedure that settles sales tax balances in the sales tax accounts and offsets them to the sales tax settlement account for a given period. After the **Settle and post sales tax** job procedure is completed for an interval of the sales tax settlement period, you can generate the VAT declaration in Excel from the **Sales tax payments** page.

1. Go to **Tax** \> **Inquiries and reports** \> **Sales tax inquiries** \> **Sales tax payments**, and select a sales tax payment line.
2. Select **Print report**, and then select **OK**.
3. Review the Excel file that is generated for the selected sales tax payment line.

    > [!NOTE]
    > The report is generated only for the selected line of the sales tax payment. If you must generate, for example, a corrective declaration that contains all corrections for the period, or a replacement declaration that contains original data and all corrections, use the [Report sales tax for settlement period](#report-sales-tax-for-settlement-period) periodic task.

## Generate the electronic file for the VAT declaration from electronic messages

When you use electronic messages to generate the report, you can collect tax data from multiple legal entities. For more information, see the [Run the VAT declaration for multiple legal entities](#run-the-vat-declaration-for-multiple-legal-entities) section later in this article.

The following procedure applies to the electronic message processing example that you [imported earlier from the LCS Shared asset library](#import-em).

1. Go to **Tax** \> **Inquiries and reports** \> **Electronic messages** \> **Electronic messages**.
2. In the left pane, select **FI VAT declaration**.
3. On the **Messages** FastTab, select **New**.
4. In the **Run processing** dialog box, the **FI VAT Create message** action is predefined. Select **OK**.
5. Select the message line that is created, enter a description, and then specify the start and end dates for the declaration.
6. On the **Messages** FastTab, select **Collect data**, and then select **OK**. The sales tax payments that were generated earlier because of the [Settle and post sales tax](../../general-ledger/tasks/create-sales-tax-payment.md) job procedure are added to the message.
7. On the **Message items** FastTab, review the sales tax payments that are transferred for processing. By default, all sales tax payments of the selected period that weren't included in any other message of the same processing are included.
8. Optional: Select **Original document** to review the sales tax payments, or select **Delete** to exclude sales tax payments from processing.
9. On the **Messages** FastTab, select **Update status**.
10. In the **Update status** dialog box, select **FI VAT Ready to generate**, and then select **OK**.
11. Verify that the message status is changed to **FI VAT Ready to generate VAT return**.
12. Select **Generate report**.
13. To preview the VAT declaration amounts, in the **Run processing** dialog box, select **FI VAT Preview report**, and then select **OK**.
14. In the **Electronic reporting parameters** dialog box, set the fields as described in the [Preview the VAT declaration in Excel from the Report sales tax for settlement period periodic task](#report-sales-tax-for-settlement-period) section earlier in this article, and then select **OK**.
15. Select the **Attachments** button (paper clip symbol) in the upper-right corner of the page, and then select **Open** to open the file.
16. Review the amounts in the Excel document, and then select **Generate report**.
17. To generate the VAT declaration in TXT format, in the **Run processing** dialog box, select **FI VAT Generate report**, and then select **OK**.
18. In the **Electronic reporting parameters** dialog box, set the fields as described in the [Preview the VAT declaration in Excel from the Report sales tax for settlement period periodic task](#report-sales-tax-for-settlement-period) section, and then select **OK**.
19. Select the **Attachments** button (paper clip symbol) in the upper-right corner of the page, download the file, and use it for your submission to the tax authority.

## Run the VAT declaration for multiple legal entities

To use the formats to report the VAT declaration for a group of legal entities, you must first set up the application-specific parameters of the ER formats for sales tax codes from all required legal entities.

### Set up electronic messages to collect tax data from several legal entities

Follow these steps to set up electronic messages to collect data from multiple legal entities.

1. Go to **Workspaces** \> **Feature management**.
2. Find and select the **Cross-company queries for the populate records actions** feature in the list, and then select **Enable now**.
3. Go to **Tax** \> **Setup** \> **Electronic messages** \> **Populate records actions**.
4. On the **Populate records action** page, select the line for **FI Populate VAT return records**.

    In the **Datasources setup** grid, a new **Company** field is available. For existing records, this field shows the identifier of the current legal entity.

5. In the **Datasources setup** grid, add a line for each additional legal entity that must be included in reporting. For each new line, set the following fields.

    | Field | Description |
    |---|---|
    | Name | Enter a value that will help you understand where this record comes from. For example, enter **VAT payment of Subsidiary 1**. |
    | Message item type | Select **VAT return**. This value is the only value that is available for all the records. |
    | Account type | Select **All**. |
    | Master table name | Specify **TaxReportVoucher** for all the records. |
    | Document number field | Specify **Voucher** for all the records. |
    | Document date field | Specify **TransDate** for all the records. |
    | Document account field | Specify **TaxPeriod** for all the records. |
    | Company | Select the ID of the legal entity. |
    | User query | This checkbox is automatically selected when you define criteria by selecting **Edit query**. |

6. For each new line, select **Edit query**, and specify a related settlement period for the legal entity that is specified in the **Company** field on the line.

    When the setup is completed, the **Collect data** function on the **Electronic messages** page collects sales tax payments from all legal entities that you defined.
