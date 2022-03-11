---
# required metadata

title: VAT declaration (Finland)
description: This topic describes how to set up and generate a value-added tax (VAT) declaration for Finland in the official TXT format and preview in Microsoft Excel. 
author: liza-golub
ms.date: 03/10/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Finland
ms.author: liza-golub
# ms.search.industry: 
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# VAT declaration (Finland)

[!include [banner](../includes/banner.md)]

This topic describes how to set up and generate a value-added tax (VAT) declaration for Finland in the official TXT format. 
It also describes how to preview the VAT declaration in Microsoft Excel.

To automatically generate the report, first create enough sales tax codes to keep a separate VAT accounting for each type of the operations that are subject to reporting in VAT declaration of Finland. Additionally, in the application-specific parameters of the Electronic reporting (ER) format for the VAT declaration, associate sales tax codes with the lookup result of **Report field lookup** lookup field. In the following table, the "Lookup result" column shows the lookup result that is preconfigured for a specific VAT declaration field ID in the VAT declaration format. Use this information to correctly associate sales tax codes with the lookup result and then with the field ID of the VAT declaration.

## VAT declaration overview

The VAT declaration for Finalnd contains the following fields to report amounts related to VAT.

| **Field ID (Tunnus)** | **Description (English)** | **Description (Finnish)** | **Lookup result** |
| --- | --- | --- | --- |
| 301 | Tax on domestic sales at standard tax rate | Kotimaan verollinen myynti yleisellä verokannalla | DomesticSalesStandardRate |
| 302 | Tax on domestic sales at higher reduced tax rate | Kotimaan verollinen myynti suuremman alennetun verokannan mukaan | DomesticSalesHigherReducedRate |
| 303 | Tax on domestic sales lower reduced tax rate | Kotimaan verollinen myynti pienemmän alennetun verokannan mukaan | DomesticSalesLowerReducedRate |
| 304 | Tax on imports of goods from outside the EU | Vero tavaroiden maahantuonnista EU:n ulkopuolelta | ImportsOfGoods</br>ImportsOfGoodsUseTax – when *Use tax* option is used |
| 305 | Tax on goods purchased from other EU Member States | Vero tavaraostoista muista EU-maista | GoodsPurchasedFromEU</br>GoodsPurchasedFromEUUseTax – when *Use tax* option is used |
| 306 | Tax on services purchased from other EU Member States | Vero palveluostoista muista EU-maista | ServicesPurchasedFromEU</br>ServicesPurchasedFromEUUseTax – when *Use tax* option is used |
| 307 | Tax deductible for the tax period | Verokauden vähennettävä vero | Deductible</br>When *Use tax* is used:</br>- GoodsPurchasedFromEUUseTax</br>- ImportsOfGoodsUseTax</br>- PurchasesReverseChargeUseTax</br>- ServicesPurchasedFromEUUseTax |
| **308** | **Tax payable / Negative tax that qualifies for refund (‒)** | **Maksettava vero / Palautukseen oikeuttava vero (-)** | **Not applicable, calculated automatically** |
| 309 | Turnover taxable at zero VAT rate | 0-verokannan alainen liikevaihto | TaxableSalesZero |
| 310 | Imports of goods from outside the EU | Tavaroiden maahantuonnit EU:n ulkopuolelta | ImportsOfGoods</br>ImportsOfGoodsUseTax – when *Use tax* option is used |
| 311 | Sales of goods to other EU Member States | Tavaroiden myynnit muihin EU-maihin | EUSalesOfGoods |
| 312 | Sales of services to other EU Member States | Palveluiden myynnit muihin EU-maihin | EUSalesOfServices |
| 313 | Purchases of goods from other EU Member States | Tavaraostot muista EU-maista | GoodsPurchasedFromEU</br>GoodsPurchasedFromEUUseTax – when *Use tax* option is used |
| 314 | Purchases of services from other EU Member States | Palveluostot muista EU-maista | ServicesPurchasedFromEU</br>ServicesPurchasedFromEUUseTax – when *Use tax* option is used |
| 315 | Turnover that qualifies for VAT relief | Alarajahuojennukseen oikeuttava liikevaihto | Not applicable, filled in using **VAT relief - sales amount** user input parameter of the dialogue of the report. |
| 316 | Tax that qualifies for VAT relief | Alarajahuojennukseen oikeuttava vero | Not applicable, filled in using **VAT relief - tax amount** user input parameter of the dialogue of the report. |
| 317 | Amount of VAT relief | Alarajahuojennuksen määrä | Not applicable, calculated automatically. |
| 318 | Tax on purchases of construction services and scrap metal (reverse charge) | Vero rakentamispalvelun ja metalliromun ostoista | PurchasesReverseCharge</br>PurchasesReverseChargeUseTax – when *Use tax* option is used |
| 319 | Sales of construction services and scrap metal (reverse charge) | Rakentamispalvelun ja metalliromun myynnit | SalesReverseCharge |
| 320 | Purchases of construction services and scrap metal (reverse charge) | Rakentamispalvelun ja metalliromun ostot | PurchasesReverseCharge</br>PurchasesReverseChargeUseTax – when *Use tax* option is used |

For more information about how to configure reverse charge VAT, see [Reverse charges](emea-reverse-charge.md).

For more information about how to set up application-specific parameters, see the [Set up application-specific parameters for VAT declaration fields](#set-up) section later in this topic.

## Set up a VAT declaration for Finland

These tasks will prepare your Microsoft Dynamics 365 Finance environment to generate electronic file for VAT declaration for Finland and preview VAT amounts in Excel format.

- [Import ER configurations](#import-er)
- [Set up application-specific parameters for VAT declaration fields](#set-up)
- [Set up the VAT reporting format for preview amounts in Excel](#setup-preview)
- [Set up electronic messages](#setup-em)
- [Set up the VAT registration number of the company that is reporting VAT](#vat-id)

### <a name="import-er"></a>Import ER configurations

Open the **Electronic reporting** workspace, and import the latest versions of these ER formats under **Tax declaration model**:

- VAT Declaration TXT (FI)
- VAT Declaration Excel (FI)

For more information, see [Download ER configurations from the Global repository of Configuration service](../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

### <a name="set-up"></a>Set up application-specific parameters for VAT declaration fields

To automatically generate a VAT declaration, associate sales tax codes in Finance application and lookup results in the ER configuration.

> [!NOTE]
> We recommend that you enable the **Use application specific parameters from previous versions of ER formats** feature in the **Feature management** workspace. When this feature is enabled, parameters that are configured for an earlier version of an ER format automatically become applicable for a later version of the same format. If this feature isn't enabled, you must explicitly configure application-specific parameters for each format version. The **Use application specific parameters from previous versions of ER formats** feature is available in the **Feature management** workspace as of Finance version 10.0.23. For more information about how to set up the parameters of an ER format for each legal entity, see [Set up the parameters of an ER format per legal entity](../../fin-ops-core/dev-itpro/analytics/er-app-specific-parameters-set-up.md).

Follow these steps to define which sales tax codes in your Finance generate which filed ID on the VAT declaration for Finland.

1. Go to **Workspaces** > **Electronic reporting**, and select **Reporting configurations**.
2. Select the **VAT declaration TXT (FI)** configuration, and then select **Configurations \> Application specific parameters setup** on the Action pane.
3. On the **Application specific parameters** page, on the **Lookups** FastTab, select **Report field lookup**.
4. On the **Conditions** FastTab, set the following fields to associate the sales tax codes and report fields.


   | Field                  | Description                                                                                                                                                                                                                                                                                                          |
   |------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | Lookup result          | Select the value of the report field. For more information about the values and their assignment to VAT declaration rows, see the [VAT declaration overview](#vat-declaration-overview) section earlier in this topic.                                                                                               |
   | Tax code               | Select the sales tax code to associate with the report field. Posted tax transactions that use the selected sales tax code will be collected in the appropriate declaration box. We recommend that you separate sales tax codes in such a way that one sales tax code generates amounts in only one declaration box. |
   | Transaction classifier | If you created enough sales tax codes to determine a declaration box, select **\*Not blank\***. If you didn't create enough sales tax codes so that one sales tax code generates amounts in only one declaration box, you can set up a transaction classifier. The following transaction classifiers are available: </br>-   **Purchase**</br>-   **PurchaseExempt** (tax-exempt purchase)</br>-   **PurchaseReverseCharge** (tax receivable from a purchase reverse charge)</br>-   **Sales**</br>-   **SalesExempt** (tax-exempt sale)</br>-   **SalesReverseCharge** (tax payable from a purchase reverse charge or a sales reverse charge)</br>-   **Use tax**. </br>For each transaction classifier, a classifier for the credit note is also available. For example, one of these classifiers is **PurchaseCreditNote** (purchase credit note).</br>Be sure to create two lines for each sales tax code: one that has the transaction classifier value and one that has the transaction classifier for credit note value. |

   > [!NOTE]
   > Associate all sales tax codes with lookup results. If any sales tax codes should not generate values on the VAT declaration, associate them with the **Other** lookup result.

5. In the **State** field, change the value to **Completed**.
6. On the Action Pane, select **Export** to export the settings of the application-specific parameters.
7. Select the **VAT declaration Excel (FI)** configuration, and then, on the Action Pane, select **Import** to import the parameters that you configured for **VAT declaration TXT (FI)**.
8. In the **State** field, select **Completed**.

### <a name="setup-preview"></a>Set up the VAT reporting format for preview amounts in Excel

1. In the **Feature management** workspace, find and select the **VAT statement format reports** feature in the list, and then select **Enable now**.
2. On the **Tax authorities** page (**Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax authorities**), select the tax authority, and then, in the **Report layout** field, select **Default**.
3. Go to **General ledger** > **Setup** > **General ledger parameters**.
4. On the **Sales tax** tab, on the **Tax options** FastTab, in the **VAT statement format mapping** field, select the **VAT declaration Excel (FI)** ER format.

   This format is printed when you run the **Report sales tax for settlement period** report. It's also printed when you select **Print** on the **Sales tax payments** page.

If you're configuring the VAT declaration for Finland in a legal entity that has [multiple VAT registrations](emea-reporting-for-multiple-vat-registrations.md),
follow these steps.

1. Go to **General ledger** \> **Setup** \> **General ledger parameters**.
2. On the **Sales tax** tab, on the **Electronic reporting for countries/regions** FastTab, on the line for **FIN**, select the **VAT Declaration Excel (FI)** ER format.

### <a name="setup-em"></a>Set up electronic messages

Electronic messaging (EM) functionality is provided to maintain the different processes that are used in electronic reporting for different document types. For more information about electronic messages, see [Electronic messaging](../general-ledger/electronic-messaging.md).

#### Download and import the data package that has example settings for electronic messages

The process of setting up the Electronic messages functionality to generate the VAT declaration for Finland in TXT format and preview it in Excel has many steps. Because the data of some entities is used in the ER configurations, use a set of predefined values that are delivered in a package of data entities for the related tables. You can extend these settings or create your own.

> [!NOTE]
> Some records in the data entities in the package include a link to ER configurations. Before you start to import the data entities package, [import ER configurations into Finance](#import-er).

1. In [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/v2), in the Shared asset library, select **Data package** as the asset type, and then download **FI VAT declaration EM package**. The downloaded file is named **FI VAT declaration EM package.zip**.
2. In Dynamics 365 Finance, in the **Data management** workspace, select **Import**.
3. On the **Import** FastTab, in the **Group name** field, enter a name for the job.
4. On the **Selected entities** FastTab, select **Add file**.
5. In the **Add file** dialog box, verify that the **Source data format** field is set to **Package**, select **Upload and add**, and then select the zip file that you downloaded earlier.
6. Select **Close**.
7. After the data entities are uploaded, on the Action Pane, select **Import**.
8. Go to **Tax** > **Inquiries and reports** > **Electronic messages** > **Electronic messages**, and validate the electronic message processing that you imported (**FI VAT declaration**).

For more information about how you can use the data management framework, see [Data management](../../fin-ops-core/dev-itpro/data-entities/data-entities-data-packages.md).

#### Configure electronic messages

1. Go to **Tax** \> **Setup** \> **Electronic messages** \> **Populate records actions**.
2. Select the line for **FI Populate VAT return records**, and then select **Edit query**.
3. Use the filter to specify the settlement periods to include on the report.
4. If you must report tax transactions from other settlement periods in a different declaration, create a new **Populate records** action, and select the appropriate settlement periods.

### <a id="vat-id"></a>Set up the VAT registration number of the company that is reporting VAT

To generate a VAT declaration, you must configure the tax registration number of your organization (field \"010\" - Asiakkaan y-tunnus tai henkilötunnus).

1. Go to **Organization administration** > **Organizations** > **Legal entities**.
2. Select the legal entity, and then select **Registration IDs**.
3. Select or create the address in Finland and then, on the **Registration ID** FastTab, select **Add**.
4. In the **Registration type** field, select the registration type that is dedicated to Finland and that uses the **VAT ID** registration category.
5. In the **Registration number** field, enter the tax number.
6. On the **General** tab, in the **Effective** field, enter the date when the number becomes effective.

For more information about how to set up registration categories and registration types, see [Registration IDs](emea-registration-ids.md).

Follow these steps to define the VAT registration number that is used by **Electronic messaging** during generation of VAT declaration for Finland.

1. Go to **Tax** \> **Setup** \> **Electronic messages** \> **Electronic messages processing**, and select the **FI VAT declaration** processing.
2. On the **Message additional fields** FastTab, in the **Tax registration number** field, define the VAT registration number that should be used in VAT declaration for Finland.
3. Save your changes.

If the VAT registration number isn't specified in the **Tax registration number** additional field of the **FI VAT declaration** processing, the system retrieves it from the registration ID that is defined in the properties of the legal entity that is associated with the **VAT ID** registration category. 

## Preview the VAT declaration in Excel

### <a name="report-sales-tax-for-settlement-period"></a>Preview the VAT declaration in Excel from the Report sales tax for settlement period periodic task

1. Go to **Tax** \> **Periodic tasks** \> **Declarations** \> **Sales tax** \> **Report sales tax for settlement period**.
2. Set the following fields.

   | Field                                 | Description                                                                                                                                                                                                                          |
   |---------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | From date | Select the start date of the reporting period.  |
   | Settlement period                     | Select the settlement period.                                                                                                                                                                                                        |
   | Sales tax payment version | Select one of the following values:</br>-**Original** – Generate a report for the sales tax transactions of the original sales tax payment or before the sales tax payment is generated.</br>-**Corrections** – Generate a report for the sales tax transactions of all the subsequent sales tax payments for the period.</br>-**Total list** – Generate a report for all the sales tax transactions for the period, including the original and all corrections.|
   
3. Select **OK** and in the next dialog page set the following fields.

   | Field                                 | Description                                                                                                                                                                                                                          |
   |---------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | VAT relief - sales amount | Specify the amount of sales that qualify for VAT relief |
   | VAT relief - tax amount | Specify the amount of tax that qualifies for VAT relief |
   | VAT relief - reason | Note: VAT relief cannot be requested at other times than for the final tax period of the accounting year, the final quarter of the calendar year, and the period when the VAT taxpayer’s obligation is ended. Select the following reason to VAT relief:</br>1 - requesting relief because this is the final tax period for the accounting year</br>2 - requesting relief because this is the final quarter of the calendar year</br>3 - requesting relief because my VAT obligation has ended during this tax period</br>0 - no relief requested (default value).|
   | Accounting for VAT on cash basis | Select "Yes" in case of accounting for VAT on cash basis. |
   | Correction reasons | Select one or many correction reasons if needed. |
   | Contact person | Select the the contact person. |
      
3. Select **OK**, and review the Excel report.

### Preview the VAT declaration in Excel from a sales tax payment

Sales tax payment transaction results the [Settle and post sales tax](../general-ledger/tasks/create-sales-tax-payment.md) job procedure that settles sales tax balances on the sales tax accounts, and offsets them to the sales tax settlement account for a given period. When **Settle and post sales tax** job procedure is completed for an interval of the selas tax settlement period, you can generate of it a VAT declaration in Excel from **Sales tax payments** page.

1. Go to **Tax** \> **Inquiries and reports** \> **Sales tax inquiries** \> **Sales tax payments**, and select a sales tax payment line.
2. Select **Print report**, and then select **OK**.
3. Review the Excel file that is generated for the selected sales tax payment line.

   > [!NOTE]
   > The report is generated only for the selected line of the sales tax payment. If you must generate, for example, a corrective declaration that contains all corrections for the period, or a replacement declaration that contains original data and all corrections, use the [**Report sales tax for settlement period**](#report-sales-tax-for-settlement-period) periodic task.

## Generate electronic file for VAT declaration from electronic messages

When you use electronic messages to generate the report, you can collect tax data from multiple legal entities. For more information, see the [Run a VAT declaration for multiple legal entities](#run-a-vat-declaration-for-multiple-legal-entities) section later in this topic.

The following procedure applies to the electronic message processing example that you [imported earlier from the LCS Shared asset library](#import-em).

1. Go to **Tax** > **Inquiries and reports** > **Electronic messages** > **Electronic messages**.
2. In the left pane, select **FI VAT declaration**.
3. On the **Messages** FastTab, select **New**. In the **Run processing** dialog box, **FI VAT Create message** action is predefined, select **OK**.
4. Select the message line that is created, enter a description, and then specify the start and end dates for the declaration.
5. On the **Messages** FastTab, select **Collect data**, and then select **OK**. The sales tax payments that were generated earlier as a result of the [Settle and post sales tax](../general-ledger/tasks/create-sales-tax-payment.md) job procedureare are added to the message.
6. On the **Message items** FastTab, review the sales tax payments that are transferred for processing. By default, all sales tax payments of the selected period that weren't included in any other message of the same processing are included.
7. Optional: Select **Original document** to review the sales tax payments, or select **Delete** to exclude sales tax payments from processing.
8. On the **Messages** FastTab, select **Update status**. In the **Update status** dialog box, select **FI VAT Ready to generate**, and then select **OK**. Verify that the message status is changed to **FI VAT Ready to generate VAT return**.
9. Select **Generate report**. To preview the VAT declaration amounts, in the **Run processing** dialog box, select **FI VAT Preview report**, and then select **OK**.
10. In the **Electronic reporting parameters** dialog box, set the fields as described in the [Preview the VAT declaration in Excel from the Report sales tax for settlement period periodic tas](#report-sales-tax-for-settlement-period) section earlier in this topic, and then select **OK**.
11. Select the **Attachments** button (paper clip symbol) in the upper-right corner of the page, and then select **Open** to open the file.
12. Review the amounts in the Excel document, and then select **Generate report**.
13. To generate a VAT declaration in TXT format, in the **Run processing** dialog box, select **FI VAT Generate report**, and then select **OK**.
14. In the **Electronic reporting parameters** dialog box, set the fields as described in the [Preview the VAT declaration in Excel from the Report sales tax for settlement period periodic task](#report-sales-tax-for-settlement-period) section earlier in this topic, and then select **OK**.
15. Select the **Attachments** button (paper clip symbol) in the upper-right corner of the page, download the file, and use it for your submission to the tax authority.

## Run a VAT declaration for multiple legal entities

To use the formats to report the VAT declaration for a group of legal entities, you must first set up the application-specific parameters of the ER formats for sales tax codes from all required legal entities.

### Set up electronic messages to collect tax data from several legal entities

Follow these steps to set up electronic messages to collect data from multiple legal entities.

1. Go to **Workspaces** \> **Feature management**.
2. Find and select the **Cross-company queries for the populate records actions** feature in the list, and then select **Enable now**.
3. Go to **Tax** \> **Setup** \> **Electronic messages** \> **Populate records actions**.
4. On the **Populate records action** page, select the line for **FI Populate VAT return records**.

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

   When the setup is completed, the **Collect data** function on the **Electronic messages** page collects sales tax payments from all legal entities that you defined.

