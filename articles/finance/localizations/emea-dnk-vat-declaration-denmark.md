---
title: VAT declaration (Denmark)
description: This article describes how to set up and generate an advance value-added tax (VAT) declaration for Denmark.
author: AdamTrukawka
ms.date: 03/10/2022
ms.topic: article
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: atrukawk
ms.search.validFrom: 
---

# VAT declaration (Denmark)

[!include [banner](../includes/banner.md)]

This article describes how to set up the value-added tax (VAT) declaration for Denmark and preview it in Microsoft Excel.

To automatically generate the report, first create enough sales tax codes to keep a separate VAT accounting for each box on the advance VAT declaration. Additionally, in the application-specific parameters of the Electronic reporting (ER) format for the advance VAT declaration, associate sales tax codes with the lookup result of the lookups for the boxes on the VAT declaration.

For Denmark, you must configure **Report field lookup**. For more information about how to set up application-specific parameters, see the [Set up application-specific parameters for VAT declaration fields](#set-up-application-specific-parameters) section later in this article.

In the following table, the "Lookup result" column shows the lookup result that is preconfigured for a specific VAT declaration row in the VAT declaration format. Use this information to correctly associate sales tax codes with the lookup result and then with the row of the VAT declaration.

### VAT declaration overview

The VAT declaration in Denmark contains the following information.

**VAT payable**

| Description                                                  | Tax base/Tax amount | Lookup result/Total                                                                                                                                                                                                                                                                                                                          |
|--------------------------------------------------------------|---------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Output VAT                                                   | Tax amount          | **OutputVAT**</br> **DomesticVATUseTax** (also reported in the "Input VAT" box)                                                                                                                                                                                                                                                                       |
| VAT on goods etc. purchased abroad                           | Tax amount          | **PurchaseGoodsAbroad**</br>**PurchaseGoodsAbroadUseTax** (also reported in the "Input VAT" box)</br>**PurchaseGoodsEU** (The tax base is reported in "Box A - acquisition of goods.")</br>**PurchaseGoodsEUUseTax** (The tax amount is also reported in the "Input VAT" box. The tax base is reported in "Box A - acquisition of goods.")                   |
| VAT on services purchased abroad subject to a reverse charge | Tax amount          | **PurchaseServicesAbroad**</br> **PurchaseServicesAbroadUseTax** (also reported in the "Input VAT" box)</br>**PurchaseServicesEU** (The tax base is reported in "Box A - acquisition of services.")</br>**PurchaseServicesEUUseTax** (The tax amount is also reported in the "Input VAT" box. The tax base is reported in "Box A - acquisition of services.") |
| Total payable                                                | Tax amount          | Total of the previous three boxes                                                                                                                                                                                                                                                                                                            |

**Deductions**

| Description                                                                               | Tax base/Tax amount | Lookup result/Total                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|-------------------------------------------------------------------------------------------|---------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Input VAT                                                                                 | Tax amount          | **InputVAT**</br> **DomesticVATUseTax** (also reported in the "Output VAT" box)</br>**PurchaseGoodsAbroadUseTax** (also reported in the "VAT on goods etc. purchased abroad" box)</br>**PurchaseServicesAbroadUseTax** (also reported in the "VAT on services purchased abroad subject to a reverse charge" box)</br>**PurchaseGoodsEUUseTax** (also reported in the "VAT on goods etc. purchased abroad" box)</br> **PurchaseServicesEUUseTax** (also reported in the "VAT on services purchased abroad subject to a reverse charge" box) |
| Oil and bottled gas duty                                                                  | Tax amount          | **OilGasDuty**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| Power/electricity duty                                                                    | Tax amount          | **PowerElectricityDuty**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| Natural gas and town gas duty                                                             | Tax amount          | **NaturalTownGasDuty**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Carbon duty                                                                               | Tax amount          | **CarbonDuty**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| CO2Duty                                                                                   | Tax amount          | **CO2Duty**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Water charge                                                                              | Tax amount          | **WaterCharge**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Total deductions                                                                          | Tax amount          | Total of the previous six boxes                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Total amount of duties (positive amount = make payment, negative amount = receive refund) | Tax amount          | "Total payable" – "Total deductions"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |

**Supplementary information**

| Description                                                                                                                                                                                                                                | Tax base/Tax amount | Lookup result/Total                             |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------|-------------------------------------------------|
| Box A - acquisition of goods. The value without VAT of intra-Union acquisition of goods.                                                                                                                                                   | Tax base            | **PurchaseGoodsEU PurchaseGoodsEUUseTax**       |
| Box A - acquisition of services. The value without VAT of intra-Union acquisition of services.                                                                                                                                             | Tax base            | **PurchaseServicesEU PurchaseServicesEUUseTax** |
| Box B - supply of goods - to be reported to "EU-sales without VAT"/DK VIES. The value without VAT of intra-Union supply of goods                                                                                                           | Tax base            | **SalesGoodsEU**                                |
| Box B - supplies - not to be reported to "EU-sales without VAT"/DK VIES. The value without VAT of certain intra-Union supplies, for instance of installation, assembly, distance sales, and new means of transport to non-taxable persons. | Tax base            | **SalesInstallationAssemblyEtcEU**              |
| Box B - supply of services. The value without VAT of intra-Union supply of services for which the purchaser is liable to pay the VAT as reverse charge - must also be reported to "EU-sales without VAT"/DK VIES.                          | Tax base            | **SalesServicesEU**                             |
| Box C - other supplies. Value of supply of other goods and services that are supplied without VAT in the territory of Denmark, to other EU Member States, and to other countries/regions or territories.                                     | Tax base            | **OtherSuppliesWithoutVAT**                     |

#### Purchase reverse charge VAT

If you configure sales tax codes to post incoming reverse charge VAT by using use tax, associate your sales tax codes with the lookup result of **Report field lookup** that contains "UseTax" in the name.

Alternatively, you can configure two separate sales tax codes: one for VAT due and one for VAT deduction. Then associate each code with the corresponding lookup results of **Report field lookup**.

For example, for taxable intra-community acquisitions, you configure sales tax code **UT_S_EU** with use tax and associate it with the **PurchaseGoodsEUUseTax** lookup result of **Report field lookup**. In this case, tax amounts that use the **UT_S_EU** sales tax code are reflected in the "VAT on goods etc. purchased abroad" and "Input VAT" boxes. Tax bases are reflected in "Box A - acquisition of goods."

Alternatively, you configure two sales tax codes:

- **VAT_S_EU**, which has a tax rate value of -25 percent
- **InVAT_S_EU**, which has a tax rate value of 25 percent

You then associate the codes with lookup results of **Report field lookup** in the following way:

- Associate **VAT_S_EU** with the **PurchaseGoodsEU** lookup result.
- Associate **InVAT_S_EU** with the **InputVAT** lookup result.

In this case, amounts that use the **VAT_S_EU** sales tax code are reflected in the "VAT on goods etc. purchased abroad" box and "Box A - acquisition of goods." Amounts that use the **InVAT_S_EU** sales tax code are reflected in the "Input VAT" box.

For more information about how to configure reverse charge VAT, see [Reverse charges](emea-reverse-charge.md).

## Configure system parameters

To generate a VAT declaration, you must configure the VAT number.

1. Go to **Organization administration** > **Organizations** > **Legal entities**.
2. Select the legal entity, and then select **Registration IDs**.
3. Select or create the address in Denmark, and then, on the **Registration ID** FastTab, select **Add**.
4. In the **Registration type** field, select the registration type that is dedicated to Denmark, and that uses the **VAT Id** registration category.
5. In the **Registration number** field, enter the tax number.
6. On the **General** tab, in the **Effective** field, enter the date when the number becomes effective.

For more information about how to set up registration categories and registration types, see [Registration IDs](emea-registration-ids.md).

## Set up a VAT declaration preview for Denmark

### Import ER configurations

Open the **Electronic reporting** workspace, and import the **VAT Declaration Excel (DK)** ER format.

For more information, see [Download ER configurations from the Global repository of Configuration service](../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

### <a name="set-up-application-specific-parameters"></a>Set up application-specific parameters for VAT declaration fields

> [!NOTE]
> We recommend that you enable the feature, **Use application specific parameters from previous versions of ER formats** in the **Feature management** workspace. When this feature is enabled, parameters that are configured for the earlier version of an ER format automatically become applicable for the later version of the same format. If this feature is not enabled, you must configure application-specific parameters explicitly for each format version. The **Use application specific parameters from previous versions of ER formats** feature is available in the **Feature management** workspace starting in Finance version 10.0.23. For more information about how to set up the parameters of an ER format for each legal entity, see [Set up the parameters of an ER format per legal entity](../../fin-ops-core/dev-itpro/analytics/er-app-specific-parameters-set-up.md).

To automatically generate a VAT declaration, associate sales tax codes in the application and lookup results in the ER configuration.

Follow these steps to define which sales tax codes generate which boxes on the VAT declaration.

1. Go to **Workspaces** > **Electronic reporting**, and select **Reporting configurations**.
2. Select the **VAT declaration Excel (DK)** configuration, and then select **Configurations \> Application specific parameters setup**.
3. On the **Application specific parameters** page, on the **Lookups** FastTab, select **Report field lookup**.
4. On the **Conditions** FastTab, set the following fields to associate the sales tax codes and report fields.

    | Field                  | Description                                                                                                                                                                                                                                                                                                          |
    |------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Lookup result          | Select the value of the report field. For more information about the values and their assignment to VAT declaration rows, see the [VAT declaration overview](#vat-declaration-overview) section earlier in this article.                                                                                               |
    | Tax code               | Select the sales tax code to associate with the report field. Posted tax transactions that use the selected sales tax code will be collected in the appropriate declaration box. We recommend that you separate sales tax codes in such a way that one sales tax code generates amounts in only one declaration box. |
    | Transaction classifier | If you created enough sales tax codes to determine a declaration box, select **\*Not blank\***. If you didn't create enough sales tax codes so that one sales tax code generates amounts in only one declaration box, you can set up a transaction classifier. The following transaction classifiers are available:</br>-   **Purchase**</br>-   **PurchaseExempt** (tax-exempt purchase)</br>-   **PurchaseReverseCharge** (tax receivable from a purchase reverse charge)</br>-   **Sales**</br>-   **SalesExempt** (tax-exempt sale)</br>-   **SalesReverseCharge** (tax payable from a purchase reverse charge or a sales reverse charge)</br>-   **Use tax**. </br>For each transaction classifier, a classifier for the credit note is also available. For example, one of these classifiers is **PurchaseCreditNote** (purchase credit note).</br>Be sure to create two lines for each sales tax code: one that has the transaction classifier value and one that has the transaction classifier for credit note value. |


    > [!NOTE]
    > Associate all sales tax codes with lookup results. If any sales tax codes should not generate values on the VAT declaration, associate them with the **Other** lookup result.

    ![Application specific parameters page.](media/7db74920fad66a0db7fad60758698cc0.png)


5. In the **State** field, change the value to **Completed**.

### Set up the VAT reporting format for preview amounts in Excel

1. In the **Feature management** workspace, find and select the **VAT statement format reports.** feature in the list, and then select **Enable now**.
2. Go to **General ledger** > **Setup** > **General ledger parameters**.
3. On the **Sales tax** tab, on the **Tax options** FastTab, in the **VAT statement format mapping** field, select the **VAT declaration Excel (DK)** ER format.

   This format is printed when you run the **Report sales tax for settlement period** report. It's also printed when you select **Print** on the **Sales tax payments** page.

4. On the **Tax authorities** page, select the tax authority, and then, in the **Report layout** field, select **Default**.

If you're configuring the VAT declaration in a legal entity that has [multiple VAT registrations](emea-reporting-for-multiple-vat-registrations.md), follow these steps.

1. Go to **General ledger** \> **Setup** \> **General ledger parameters**.
2. On the **Sales tax** tab, on the **Electronic reporting for countries/regions** FastTab, on the line for **DNK**, select the **VAT Declaration Excel (DK)** ER format.

## Set up electronic messages

### Download and import the data package that has example settings for electronic messages

The data package contains electronic message settings that are used to preview the VAT declaration in Excel. You can extend these settings or create your own. For more information about how to work with electronic messaging and create your own settings, see [Electronic messaging](../general-ledger/electronic-messaging.md).

1. In [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/v2), in the Shared asset library, select **Data package** as the asset type, and then download **DK VAT declaration package**. The downloaded file is named **DK VAT declaration package.zip**.
2. In Finance, in the **Data management** workspace, select **Import**.
3. On the **Import** FastTab, in the **Group name** field, enter a name for the job.
4. On the **Selected entities** FastTab, select **Add file**.
5. In the **Add file** dialog box, verify that the **Source data format** field is set to **Package**, select **Upload and add**, and then select the zip file that you downloaded earlier.
6. Select **Close**.
7. After the data entities are uploaded, on the Action Pane, select **Import**.
8. Go to **Tax** > **Inquiries and reports** > **Electronic messages** > **Electronic messages**, and validate the electronic message processing that you imported (**DK VAT declaration**).

### Configure electronic messages

1. Go to **Tax** > **Setup** > **Electronic messages** > **Populate records actions**.
2. Select the line for **DK Populate VAT return records**, and then select **Edit query**.
3. Use the filter to specify the settlement periods to include on the report.
4. If you must report tax transactions from other settlement periods in a different declaration, create a new **Populate records** action, and select the appropriate settlement periods.

## Preview the VAT declaration in Excel

### <a name="preview-vat-excel"></a>Preview the VAT declaration in Excel from the Report sales tax for settlement period periodic task

1. Go to **Tax** > **Periodic tasks** > **Declarations** > **Sales tax** > **Report sales tax for settlement period**.
2. In the **Settlement period** field, select a value.
3. In the **Sales tax payment version** field, select one of the following values:

    - **Original**: Generate a report for the sales tax transactions of the original sales tax payment or before the sales tax payment is generated.
    - **Corrections**: Generate a report for the sales tax transactions of all the subsequent sales tax payments for the period.
    - **Total list**: Generate a report for all the sales tax transactions for the period, including the original and all corrections.

4. In the **From date** field, select the start date of the reporting period.
5. Select **OK**, and review the Excel report.

### Settle and post sales tax

1. Go to **Tax** > **Periodic tasks** > **Declarations** > **Sales tax** > **Settle and post sales tax**.
2. In the **Settlement period** field, select a value.
3. In the **Sales tax payment version** field, select one of the following values:

    - **Original**: Generate the original sales tax payment for the settlement period.
    - **Latest corrections**: Generate a correction sales tax payment after the original sales tax payment for the settlement period was created.

4. In the **From date** field, select the start date of the reporting period.
5. Select **OK**.

### Preview the VAT declaration in Excel from a sales tax payment

1. Go to **Tax** > **Inquiries and reports** > **Sales tax inquiries** > **Sales tax payments**, and select a sales tax payment line.
2. Select **Print report**, and then select **OK**.
3. Review the Excel file that is generated for the selected sales tax payment line.

> [!NOTE]
> The report is generated only for the selected line of the sales tax payment. If you must generate, for example, a corrective declaration that contains all corrections for the period, or a replacement declaration that contains original data and all corrections, use the **Report sales tax for settlement period** periodic task.

## Generate a VAT declaration from electronic messages

When you use electronic messages to generate the report, you can collect tax data from multiple legal entities. For more information, see the [Run a VAT declaration for multiple legal entities](#run-vat-declaration) section later in this article.

The following procedure applies to the electronic message processing example that you imported earlier from the LCS Shared asset library.

1. Go to **Tax \> Inquiries and reports \> Electronic messages \> Electronic messages**.
2. In the left pane, select **DK VAT declaration**.
3. On the **Messages** FastTab, select **New**, and then, in the **Run processing** dialog box, select **OK**.
4. Select the message line that is created, enter a description, and then specify the start and end dates for the declaration.

   > [!NOTE]
   > Steps 5 through 7 are optional.

5. Optional: On the **Messages** FastTab, select **Collect data**, and then select **OK**. The sales tax payments that were generated earlier are added to the message. For more information, see the [Settle and post sales tax](#settle-and-post-sales-tax) section earlier in this article. If you skip this step, you can still generate a VAT declaration by using the **Tax declaration version** field in the **Declaration** dialog box.
6. Optional: On the **Message items** FastTab, review the sales tax payments that are transferred for processing. By default, all sales tax payments of the selected period that weren't included in any other message of the same processing are included.
7. Optional: Select **Original document** to review the sales tax payments or select **Delete** to exclude sales tax payments from processing. If you skip this step, you can still generate a VAT declaration by using the **Tax declaration version** field in the **Declaration** dialog box.
8. On the **Messages** FastTab, select **Update status**. In the **Update status** dialog box, select **Ready to generate**, and then select **OK**. Verify that the message status is changed to **Ready to generate**.
9. Select **Generate report**. To preview the VAT declaration amounts, in the **Run processing** dialog box, select **Preview report**, and then select **OK**.
10. In the **Electronic reporting parameters** dialog box, set the fields as described in the [Preview the VAT declaration in Excel from the Report sales tax for settlement period periodic task](#preview-vat-excel) section earlier in this article, and then select **OK**.
11. Select the **Attachments** button (paper clip symbol) in the upper-right corner of the page, and then select **Open** to open the file. Review the amounts in the Excel document.

## <a name="run-vat-declaration"></a>Run a VAT declaration for multiple legal entities

To use the formats to report the VAT declaration for a group of legal entities, you must first set up the application-specific parameters of the ER formats for sales tax codes from all required legal entities.

### Set up electronic messages to collect tax data from several legal entities

Follow these steps to set up electronic messages to collect data from multiple legal entities.

1. Go to **Workspaces** > **Feature management**.
2. Find and select the **Cross-company queries for the populate records actions** feature in the list, and then select **Enable now**.
3. Go to **Tax** > **Setup** > **Electronic messages** > **Populate records actions**.
4. On the **Populate records action** page, select the line for **DK Populate VAT return records**.

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


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
