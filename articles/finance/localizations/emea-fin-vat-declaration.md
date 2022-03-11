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

To automatically generate the report, first create enough sales tax codes to keep a separate VAT accounting for each box on the VAT declaration. Additionally, in the application-specific parameters of the Electronic reporting (ER) format for the VAT declaration, associate sales tax codes with the lookup result of the lookups for the boxes on the VAT declaration.

For Finland, you must configure **Report field lookup**. For more information about how to set up application-specific parameters, see the [Set up application-specific parameters for VAT declaration fields](#set-up) section later in this topic.

In the following table, the "Lookup result" column shows the lookup result that is preconfigured for a specific VAT declaration row in the VAT declaration format. Use this information to correctly associate sales tax codes with the lookup result and then with the row of the VAT declaration.

## VAT declaration overview

The VAT declaration for Finalnd contains the following fields to report amounts related to VAT.

| **Field ID (Tunnus)** | **Description (English)** | **Description (Finish)** | **Lookup result** |
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

## Configure system parameters

To generate a VAT declaration, you must configure the tax number (field \"010\" - Asiakkaan y-tunnus tai henkilötunnus) of your organization.

1. Go to **Organization administration** > **Organizations** > **Legal entities**.
2. Select the legal entity, and then select **Registration IDs**.
3. Select or create the address in Finland and then, on the **Registration ID** FastTab, select **Add**.
4. In the **Registration type** field, select the registration type that is dedicated to Finland and that uses the **VAT Id** registration category.
5. In the **Registration number** field, enter the tax number.
6. On the **General** tab, in the **Effective** field, enter the date when the number becomes effective.

For more information about how to set up registration categories and registration types, see [Registration IDs](emea-registration-ids.md).

## Set up a VAT declaration for Finland

These tasks will prepare your Microsoft Dynamics 365 Finance environment to generate electronic file for VAT declaration for Finland and preview VAT amounts in Excel format.

- [Import ER configurations](#import-er)
- [Set up application-specific parameters for VAT declaration fields](#set-up)
- [Set up the VAT reporting format for preview amounts in Excel](#setup-preview)
- [Set up electronic messages](#setup-em)

### <a name="import-er"></a>Import ER configurations

Open the **Electronic reporting** workspace, and import the latest versions of these ER formats under **Tax declaration model**:

- VAT Declaration TXT (FI)
- VAT Declaration Excel (FI)

For more information, see [Download ER configurations from the Global repository of Configuration service](../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

### <a name="set-up"></a>Set up application-specific parameters for VAT declaration fields

To automatically generate a VAT declaration, associate sales tax codes in Finance application and lookup results in the ER configuration.

> [!NOTE]
> We recommend that you enable the **Use application specific parameters from previous versions of ER formats** feature in the **Feature management** workspace. When this feature is enabled, parameters that are configured for an earlier version of an ER format automatically become applicable for a later version of the same format. If this feature isn't enabled, you must explicitly configure application-specific parameters for each format version. The **Use application specific parameters from previous versions of ER formats** feature is available in the **Feature management** workspace as of Finance version 10.0.23. For more information about how to set up the parameters of an ER format for each legal entity, see [Set up the parameters of an ER format per legal entity](../../fin-ops-core/dev-itpro/analytics/er-app-specific-parameters-set-up.md).

Follow these steps to define which sales tax codes in your Finance generate which boxes (filed ID) on the VAT declaration for Finland.

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

## Preview the VAT declaration in Excel

### <a name="report-sales-tax-for-settlement-period"></a>Preview the VAT declaration in Excel from the Report sales tax for settlement period periodic task

1. Go to **Tax** \> **Periodic tasks** \> **Declarations** \> **Sales tax** \> **Report sales tax for settlement period**.
2. Set the following fields.

   | Field                                 | Description                                                                                                                                                                                                                          |
   |---------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | Settlement period                     | Select the settlement period.                                                                                                                                                                                                        |
   | Sales tax payment version             | Select one of the following values:</br>-**Original** – Generate a report for the sales tax transactions of the original sales tax payment or before the sales tax payment is generated.</br>-**Corrections** – Generate a report for the sales tax transactions of all the subsequent sales tax payments for the period.</br>-**Total list** – Generate a report for all the sales tax transactions for the period, including the original and all corrections.|
   | From date                             | Select the start date of the reporting period.  |
   | | |
   | | |
   | | |
   | | |
   | | |

3. Select **OK**, and review the Excel report.

### Settle and post sales tax

1. Go to **Tax** \> **Periodic tasks** \> **Declarations** \> **Sales tax** \> **Settle and post sales tax**.
2. Set the following fields.

   | Field                     | Description                                    |
   |---------------------------|------------------------------------------------|
   | Settlement period         | Select the settlement period.                  |
   | Sales tax payment version | Select one of the following values:</br>-   **Original** – Generate the original sales tax payment for the settlement period. </br> -   **Latest corrections** – Generate a correction sales tax payment after the original sales tax payment for the settlement period was created.       |
   | From date                 | Select the start date of the reporting period. |

3. Select **OK**.

### Preview the VAT declaration in Excel from a sales tax payment

1. Go to **Tax** \> **Inquiries and reports** \> **Sales tax inquiries** \> **Sales tax payments**, and select a sales tax payment line.
2. Select **Print report**, and then select **OK**.
3. Review the Excel file that is generated for the selected sales tax payment line.

   > [!NOTE]
   > The report is generated only for the selected line of the sales tax payment. If you must generate, for example, a corrective declaration that contains all corrections for the period, or a replacement declaration that contains original data and all corrections, use the [**Report sales tax for settlement period**](#report-sales-tax-for-settlement-period) periodic task.
   > 
