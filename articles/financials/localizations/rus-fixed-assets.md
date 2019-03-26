---
# required metadata

title: Fixed assets (Russia)
description: This topic provides information about fixed asset management for Russia.
author: ShylaThompson
manager: AnnBe
ms.date: 03/26/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom
ms.search.region: Russia
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Fixed assets (Russia)

[!include [banner](../includes/banner.md)]


To manage the company's fixed assets, the Fixed assets page is used, which stores all information (both financial and non-financial) on assets. Below are some examples of financial information related to fixed assets:

-   Asset acquisition cost
-   Cost adjustment
-   Asset depreciation amount
-   Asset budget
-   Tax information

Examples of non-financial information related to fixed assets:

-   Technical information
-   Location
-   Bar codes and inventory numbers
-   Insurance
-   Relationships between different assets
-   Etc.

## Register fixed assets in the system

Before you create transactions for any fixed or intangible asset, you must first register the asset record, and provide the basic information about it.

Select **Fixed Assets (Russia)** \> **Common** \> **Fixed Assets** and create a new fixed asset (click **New**).

> [!NOTE]
> A user may create a new fixed asset using copy function (**FIXED ASSET** \> **Copy FA** button). The system copies the selected fixed asset with all its parameters, but with a different inventory number.

### Filling fields on FIXED ASSETS page

Fill in the following fields on **General** FastTab:

![](media/351e55d01d929c092137555b7769536a.jpg)

-   **FA group** - select fixed asset group the fixed asset should be related to.

-   **Inventory number**. If automatic numbering is set up in the **Fixed asset parameters** or for the fixed assets group, the information is filled in automatically.

-   **Name -** enter the name of the fixed asset.

-   **Acquisition date -** by default, this field is filled in automatically with the current system date but can be changed.

-   **Acquisition cost -** enter a fixed asset acquisition value in the company's home currency. If the fixed asset was bought through the deferrals model, the invoice amount without taxes in the company's home currency is displayed.

-   **Notes** - enter any additional information about this fixed asset.

-   **Type** - select a fixed asset type. Depending on the value in this field the different fields are activated on the **Technical Information** and **Tax Reporting** FastTabs.

>   For example:

>   if a user selects **Vehicle** type, the **Government registration** field group appears on **Technical Information** FastTab.

>   If a user selects **Realty** type, the **Tax base** field appears on **Tax Reporting** FastTab.

>   If a user selects **Ground area** type, then the **Start date of building** field appears on **Technical Information** FastTab.

>   Note. The following type could not be selected in FIXED ASSETS page: NVFA, Working clothes, Special rigging. There are special pages for these types. (see [Not valuable fixed assets (NVFAs) accounting for Russia](rus-not-valuable-assets.md),
>   [Working clothes/Special riggings accounting for Russia](rus-working-clothes-instruments-accounting.md)).

-   **Insurance** field group – fill in the fields on insurance, if needed

-   **Flag of ownership** - select the appropriate value, by default the value is equal to **Ownership**.

-   **Bar code –** a user may enter the bar code manually, or bar code may be generated automatically (the same as asset inventory number). To generate a bar code automatically, the **Bar code equals inventory number** must be selected in the **Fixed assets** parameters (**Fixed Assets \> Fixed Assets** \> **Parameters**).

>   *Note*. The **Location** and **Worker ID** fields are filled in automatically, when a user create a record in **Transfer FA** page list. (**Fixed asset (Russia)** \> **Common** \> **Fixed assets**, click **FIXED ASSET** \> **HISTORY** \> **Transfer**).

-   **Output/mileage** - enter the size of assumed production/travel of the fixed asset if **Product output/mileage** depreciation profile is selected for FA in a **Value model**. In this case a user should input records on the **PRODUCT OUTPUT/ MILEAGE** page list:

![](media/830a46de2c35c35c2ff796526cef1046.jpg)

If a fixed asset is included in the composition of another fixed asset click the **Structure** FastTab. and select the fixed asset code in the **Main fixed asset** field,

In the **FA structure** field, all fixed asset accounts that have a reference to the asset are displayed in the main fixed asset.

Click the **Purchase/Sale** FastTab. Information about the purchase and sale of the fixed asset is displayed.

## Fixed asset value models

Click **Value Models** button to update or create value models for the fixed asset.

> [!NOTE]
> If value models are set up for the fixed asset group, which the fixed asset is assigned to (see **Fixed asset (Russia) \> Setup \> FA groups**) then the system creates the value models automatically and a user may update field values.

>   You must create a value model for each asset, and the settings are used to register a transaction. Click **New** to create a new line. Fill in the following fields on **General** FastTab.

![](media/80fe9edd43837f4d1df3077341b6fe2f.jpg)

-   **Value model** - select the model code for the asset.

-   **Depreciation groups** - select a depreciation group within the value model that the fixed asset relates to.

-   **Depreciation methods** - select the depreciation profile**.** By default, the value specified for the depreciation group is displayed, but you can change it.

-   **Posting profile** - select the posting profile used in the value model. By default, the value is based on the value model settings.

-   **Acquisition cost** - enter the acquisition amount of the fixed asset. If an asset purchase transaction has been created, the transaction amount without taxes is displayed. If the fixed asset acquisition currency is different from the currency set up for this value model, the currencies are converted on the acquisition date.

-   **Date of depreciation beginning** - select the date to start accruing depreciation. By default, this field is filled in according to setting in the selected **Depreciation group**. If the **Depreciation start date** parameter is set up as **Next month start** then this field is filled in with the period that follows the period of acquisition.

-   **Currency** - select a currency for the value model for the asset. The default currency from the value model settings is displayed.

-   **Remains cost after writing-off** - enter the remaining amount of the fixed asset after writing-off. If a value is filled in, then the book value used in the depreciation calculation is less than the value in this field. After a writing-off transaction is created, an amount equal to the cost of remainders after writing-off can be posted to the inventory or the general ledger account.

-   **Don't lock** – set this option to **Yes** to create depreciation transactions for the asset. By default, this option is set to **Yes**.

-   **Date of last depreciation, Disposal date** and **Disposal cost** – are filled in automatically when depreciation and writing-off transactions are created.

>   Click **Dimension** FastTab and select the default finance dimension codes that will register transactions for the asset.

>   Click the **Lease** FastTab and fill in the **Posting profile** field, select the posting profile used for fixed asset letting. If a letting transaction should be created for a fixed asset, set the **Leased** option to **Yes**.

>   Click **Dimension of rented FA** select the dimension codes used when accounting for transactions if this fixed asset is let out.

>   Click the **Depreciation accounts.** On this page a user may configure the fixed asset depreciation posting amount for the general ledger accounts in the proportions required, as needed. You might need to do this, for example, to calculate the depreciation on a building used for various purposes.

## Inquires on Fixed asset page

### Overview of asset transactions

To view the fixed asset transactions, click **Fixed Assets (Russia) \> Fixed Assets \> Value models \> Transactions.**

All fixed asset transactions, executed for the value model, are listed on the **FA transactions** page list regardless which module they were posted in:

-   **Fixed asset (Russia)** module.

-   **General ledger** module.

-   **Account payable** module.

-   **Account receivable** module.

-   On the **Overview** and **General** tabs, the fixed asset transaction
    details are displayed.

### Overview the balance of an asset

The value of an asset on a specific date reflects the results of all transactions-for the asset.

Click **Fixed Assets (Russia)\> Common \> Fixed Assets \> Value models**.

Select the value model to view the balance for.

Click the **Balance** button.

In the **Transaction date** field, enter the date for the balance sheet. The default date is the current date.

The amounts on the fixed asset **Balance by FA** page are displayed in the currency of the fixed asset value model. If the value model currency is different from the company's default currency, the default currency is also displayed in the form.

![](media/7914556f28e4f1d043d7aeb6bb7401ce.jpg)
