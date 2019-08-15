---
# required metadata

title: Fixed assets (Russia)
description: This topic provides information about fixed asset management for Russia.
author: ShylaThompson
manager: AnnBe
ms.date: 04/19/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
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


To manage your company's fixed assets, you can use the **Fixed assets** page to store all information (both financial and non-financial) on assets. The following examples show the types of financial information that is related to fixed assets:

-   Asset acquisition cost
-   Cost adjustment
-   Asset depreciation amount
-   Asset budget
-   Tax information

The following examples show the types of non-financial information that is related to fixed assets:

-   Technical information
-   Location
-   Bar codes and inventory numbers
-   Insurance
-   Relationships between different assets

## Register fixed assets

Before you create transactions for any fixed or intangible asset, you must first register the asset record, and provide basic information about it.

1. To register a fixed asset, select **Fixed Assets (Russia)** \> **Common** \> **Fixed Assets**. Select **New** to create a new fixed asset.

    > [!NOTE]
    > You can create a new fixed asset using the copy function (**FIXED ASSET** \> **Copy FA** button). The system copies the selected fixed asset with all its parameters, but with a different inventory number.

![FA page General tab](media/RUS_FA_1%20General%20tab.JPG)

2. Fill in the following fields on the **General** FastTab:

- **FA group** - Select the fixed asset group the fixed asset should be related to.

- **Inventory number** - If automatic numbering is set up in the **Fixed asset parameters** or for the fixed assets group, the information is filled in automatically.

- **Name** - Enter the name of the fixed asset.

- **Acquisition date** - By default, this field is filled in automatically with the current system date but can be changed.

- **Acquisition cost** - Enter a fixed asset acquisition value in the company's home currency. If the fixed asset came from the deferrals model, the invoice amount without taxes in the company's home currency is displayed.

- **Notes** - Enter any additional information about this fixed asset.

- **Type** - Select a fixed asset type. Depending on the value in this field, the different fields are activated on the **Technical Information** and **Tax Reporting** FastTabs. The following are examples of fixed asset types. 

    - **Vehicle** - Select this for the **Government registration** field group to appear on the **Technical Information** FastTab.

    - **Realty** - Select this for the **Tax base** field to appear on the **Tax Reporting** FastTab.

    - **Ground area** - Select this for the **Start date of building** field to appear on the **Technical Information** FastTab.

    > [!NOTE]
    > The following types cannot be selected on the **Fixed asset** page: NVFA, Working clothes, Special rigging. There are special pages for these types. For more information, see [Not valuable fixed assets (NVFAs) accounting for Russia](https://docs.microsoft.com/dynamics365/unified-operations/financials/localizations/rus-not-valuable-assets) and [Working clothes/Special riggings accounting for Russia](https://docs.microsoft.com/dynamics365/unified-operations/financials/localizations/rus-working-clothes-instruments-accounting).

- **Insurance** field group – Fill in the fields for insurance, if needed.

- **Flag of ownership** - Select the appropriate value, by default the value is equal to **Ownership**.

- **Bar code** - You can enter the bar code manually, or the bar code can be generated automatically (the same as the asset inventory number). To generate a bar code automatically, select **Bar code equals inventory number** in the **Fixed assets** parameters (**Fixed Assets \> Fixed Assets** \> **Parameters**).

    > [!NOTE]
    > The **Location** and **Worker ID** fields are filled in automatically when you create a record in the **Transfer FA** page list. (**Fixed asset (Russia)** \> **Common** \> **Fixed assets**, click **FIXED ASSET** \> **HISTORY** \> **Transfer**).

- **Output/mileage** - Enter the size of assumed production/travel of the fixed asset if **Product output/mileage** depreciation profile is selected for FA in a **Value model**. In this case, you  should input records on the **Product Output/Mileage** page list.

![Output mileage page](media/RUS_FA_2%20Output_Mileage%20page.JPG)

3. If a fixed asset is included in the composition of another fixed asset, select the **Structure** FastTab. Select the fixed asset code in the **Main fixed asset** field.

4. In the **FA structure** field, all fixed asset accounts that have a reference to the asset are displayed in the main fixed asset.

5. Select the **Purchase/Sale** FastTab. Information about the purchase and sale of the fixed asset is displayed.

## Fixed asset value models

Follow these steps to update or create value models for the fixed asset.

1. Select the **Value Models** button.

    > [!NOTE]
    > If value models are set up for the fixed asset group, which the fixed asset is assigned to (**Fixed asset (Russia) \> Setup \> FA groups**), then the system creates the value models automatically and you can update field values.

2. You need to create a value model for each asset, and the settings are used to register a transaction. Select **New** to create a new line. Fill in the following fields on the **General** FastTab.

![FA value model](media/RUS_FA_3%20value%20models.JPG)

- **Value model** - Select the model code for the asset.

- **Depreciation groups** - Select a depreciation group within the value model that the fixed asset relates to.

- **Depreciation methods** - Select the depreciation profile. By default, the value specified for the depreciation group is displayed, but you can change it.

- **Posting profile** - Select the posting profile used in the value model. By default, the value is based on the value model settings.

- **Acquisition cost** - Enter the acquisition amount of the fixed asset. If an asset purchase transaction has been created, the transaction amount without taxes is displayed. If the fixed asset acquisition currency is different from the currency set up for this value model, the currencies are converted on the acquisition date.

- **Date of depreciation beginning** - Select the date to start accruing depreciation. By default, this field is filled in according to the setting selected in the **Depreciation group**. If the **Depreciation start date** parameter is set up as **Next month start**, then this field is filled in with the period that follows the period of acquisition.

- **Currency** - Select a currency for the value model for the asset. The default currency from the value model settings is displayed.

- **Remains cost after writing-off** - Enter the remaining amount of the fixed asset after writing off. If a value is filled in, then the book value used in the depreciation calculation is less than the value in this field. After a writing-off transaction is created, an amount equal to the cost of remainders after writing off can be posted to the inventory or the general ledger account.

- **Don't lock** – Set this option to **Yes** to create depreciation transactions for the asset. By default, this option is set to **Yes**.

- **Date of last depreciation, Disposal date** and **Disposal cost** – Filled in automatically when depreciation and writing-off transactions are created.

3. Select the **Dimension** FastTab. Select the default finance dimension codes that will register transactions for the asset.

4. Select the **Lease** FastTab and fill in the **Posting profile** field, select the posting profile used for fixed asset letting. If a letting transaction should be created for a fixed asset, set the **Leased** option to **Yes**.

5. Select **Dimension of rented FA**. Select the dimension codes that should be used when accounting for transactions of this fixed asset is let out.

6. Select **Depreciation accounts.** On this page you can configure the fixed asset depreciation posting amount for the general ledger accounts in the proportions required, as needed. You might need to do this, for example, to calculate the depreciation on a building used for various purposes.

## Inquiries on the Fixed asset page

### View asset transactions

Follow these steps to view the fixed asset transactions.

1. Select **Fixed Assets (Russia) \> Fixed Assets \> Value models \> Transactions.**

2. All fixed asset transactions, executed for the value model, are listed on the **FA transactions** page, regardless of which module they were posted in:

- **Fixed asset (Russia)** module.
- **General ledger** module.
- **Account payable** module.
- **Account receivable** module.

3.  On the **Overview** and **General** tabs, the fixed asset transaction details are displayed.

### View the balance of an asset

The value of an asset on a specific date reflects the results of all transactions for the asset. Follow these steps to view the balance of an asset.

1. Select **Fixed Assets (Russia)\> Common \> Fixed Assets \> Value models**.

2. Select the value model to view the balance for.

3. Select the **Balance** button.

4. In the **Transaction date** field, enter the date for the balance sheet. The default date is the current date.

5. The amounts on the fixed asset **Balance by FA** page are displayed in the currency of the fixed asset value model. If the value model currency is different from the company's default currency, the default currency is also displayed.

![FA value model balance](media/RUS_FA_4%20model%20balance.JPG)
