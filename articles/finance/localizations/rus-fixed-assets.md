---
# required metadata

title: Fixed assets (Russia)
description: This topic provides information about fixed asset management for Russia.
author: kfend
ms.date: 08/05/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom
ms.search.region: Russia
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Fixed assets (Russia)

[!include [banner](../includes/banner.md)]

To help manage your company's fixed assets, you can use the **Fixed assets** page to store all information about assets. This information includes both financial information and non-financial information.

The following examples show the types of financial information that are related to fixed assets:

- Asset acquisition cost
- Cost adjustment
- Asset depreciation amount
- Asset budget
- Tax information

The following examples show the types of non-financial information that are related to fixed assets:

- Technical information
- Location
- Bar codes and inventory numbers
- Insurance
- Relationships among different assets

## Register fixed assets

Before you create transactions for any fixed or intangible asset, you must register the asset record and provide basic information about the asset.

1. Go to **Fixed assets (Russia) \> Common \> Fixed assets**.
2. On the Action Pane, select **New** to create a fixed asset.

    > [!NOTE]
    > You can also create a fixed asset by using the Copy function. Select the fixed asset to copy, and then, on the Action Pane, on the **Fixed asset** tab, in the **New** group, select **Copy**. In this case, the system copies the selected fixed asset together with all its parameters, but the new asset has a different inventory number.

    ![Fixed assets page.](media/RUS_FA_1%20General%20tab.JPG)

3. On the **General** FastTab, set the following fields:

    - **FA group** – Select the fixed asset group that the fixed asset should be related to.
    - **Number** – If automatic numbering is set up in the Fixed asset parameters or for the fixed assets group, this field is automatically set. Otherwise, enter the inventory number.
    - **Name** – Enter the name of the fixed asset.
    - **Acquisition date** – By default, this field is set to the current system date, but you can change the value.
    - **Acquisition cost** – Enter the acquisition value of the fixed asset in the company's home currency. If the fixed asset came from the deferrals model, this field is set to invoice amount, excluding taxes, in the company's home currency.
    - **Note** – Enter any additional information about the fixed asset.
    - **Type** – Select the fixed asset type. Depending on the value that you select, different fields are available on the **Technical information** and **Tax reporting** FastTabs. Here are some examples of fixed asset types:

        - **Vehicle** – If you select this value, the **Government registration** section appears on the **Technical information** FastTab.
        - **Realty** – If you select this value, the **Tax base** field appears on the **Tax reporting** FastTab.
        - **Ground area** – If you select this value, the **Start date of building** field appears on the **Technical information** FastTab.

        > [!NOTE]
        > The following fixed asset types can't be selected on the **Fixed assets** page: **NVFA**, **Working clothes**, and **Special rigging**. There are special pages for these fixed asset types. For more information, see [Not valuable fixed assets (NVFAs) accounting for Russia](./rus-not-valuable-assets.md) and [Working clothes/Special riggings accounting for Russia](./rus-working-clothes-instruments-accounting.md).

    - **Policy number**, **Insurance amount**, **Replacement cost**, **Insurance date 1**, and **Insurance date 2** – Set the insurance-related fields as you require.
    - **Flag of ownership** – By default, this field is set to **Ownership**, but you can change the value.
    - **Bar code** – You can manually enter the bar code, or it can be automatically generated. To automatically generate a bar code, set the **Bar code equals inventory number** option to **Yes** in the Fixed assets parameters (**Fixed assets (Russia) \> Setup \> Parameters**).

        > [!NOTE]
        > The **Location** and **Worker ID** fields are automatically set when you create a record on the **Transfer FA** page list (go to **Fixed assets (Russia)** \> **Common** \> **Fixed assets**, and then, on the **Fixed asset** tab, in the **History** group, select **Transfer**).

    - **Output/mileage** – Enter the size of the assumed production/travel for the fixed asset if the **Product output/mileage** depreciation profile is selected for the fixed asset in a value model. In this case, you should enter records on the **Product output/mileage** page list.

        ![Product output/mileage page.](media/RUS_FA_2%20Output_Mileage%20page.JPG)

4. If the fixed asset is included in the composition of another fixed asset, on the **Structure** FastTab, in the **Main fixed asset** field, select the fixed asset code.

    The **FA structure** field shows all the fixed asset accounts that have a reference to the fixed asset (if the fixed asset is the main fixed asset).

5. Select the **Purchase/Sale** FastTab to view information about the purchase and sale of the fixed asset.

## Fixed asset value models

Follow these steps to update or create value models for the fixed asset.

1. On the **Fixed assets** page, on the Action Pane, select **Value models**.

    > [!NOTE]
    > If value models are set up for the fixed asset group that the fixed asset is assigned to on the **FA groups** page (**Fixed assets (Russia) \> Setup \> FA groups**), the system automatically creates the value models. However, you can update the field values.

    You must create a value model for every asset. The settings are used to register transactions.

2. On the Action Pane, select **New** to create a line.
3. On the **General** FastTab, set the following fields:

    - **Value model** – Select the model code for the asset.
    - **Depreciation group** – Select a depreciation group in the value model that the fixed asset is related to.
    - **Depreciation method in FA group** – Select the depreciation profile. By default, this field is set to the value that is specified for the depreciation group.
    - **Posting profile** – Select the posting profile that is used in the value model. By default, this field is set according to the value model settings.
    - **Putting into operation amount** – Enter the acquisition amount of the fixed asset. If an asset purchase transaction has been created, the transaction amount without taxes is shown. If the fixed asset acquisition currency differs from the currency that is set up for the value model, the currencies are converted on the acquisition date.
    - **Depreciation start date** – Select the date to start accruing depreciation. By default, this field is set according to the setting that is selected for the depreciation group. If the **Depreciation start date** field in the depreciation group is set to **Next month start**, this field is set to the period after the period of acquisition.
    - **Currency** – Select a currency for the value model for the asset. By default, this field is set to the currency from the value model settings.
    - **Remains cost after writing-off** – Enter the remaining amount of the fixed asset after writing off. If you enter a value, the book value that is used in the depreciation calculation is less than the value of this field. After a writing-off transaction is created, an amount that is equal to the cost of remainders after writing off can be posted to the inventory or the general ledger account.
    - **Don't lock** – Set this option to **Yes** to create depreciation transactions for the asset. By default, this option is set to **Yes**.
    - **Last depreciation date**, **Disposal date**, and **Disposal cost** – These fields are automatically set when depreciation and writing-off transactions are created.

    ![FA value model.](media/RUS_FA_3%20value%20models.JPG)

4. On the **Financial dimensions** FastTab, select the default finance dimension codes that register transactions for the asset.
5. On the **Lease** FastTab, in the **Posting profile** field, select the posting profile to use for fixed asset leasing. If a leasing transaction should be created for a fixed asset, set the **Leased** option to **Yes**.
6. On the **Dimension of rented FA** FastTab, select the dimension used when posting transactions of the fixed asset.
7. On the Action Pane, select **Depreciation accounts**. On the **Depreciation accounts** page, you can configure the fixed asset depreciation posting amount for the general ledger accounts in the required proportions. You might have to complete this step if, for example, you must calculate the depreciation on a building that is used for various purposes.

## Inquiries on the Fixed assets page

### View asset transactions

Follow these steps to view the fixed asset transactions.

1. Go to **Fixed assets (Russia) \> Common \> Fixed assets**.
2. On the Action Pane, select **Value models**.
3. On the Action Pane, select **Transactions**.

    The **FA transactions** page lists all fixed asset transactions that were run for the value model, regardless of the module that they were posted in. Fixed asset transactions can be posted in the following modules:

    - Fixed assets (Russia)
    - General ledger
    - Accounts payable
    - Accounts receivable

2. On the **Overview** and **General** tabs, view the details of the fixed asset transactions.

### View the balance of an asset

The value of an asset on a specific date reflects the results of all transactions for that asset. Follow these steps to view the balance of an asset.

1. Go to **Fixed assets (Russia) \> Common \> Fixed assets**.
2. On the Action Pane, select **Value models**.
2. Select the value model to view the balance for.
3. Select **Balance**.
4. In the **Transaction date** field, enter the date for the balance sheet. By default, this field is set to the current date.

The amounts on the **Balance by FA** dialog box for the fixed asset are shown in the currency of the fixed asset value model. If the value model currency differs from the company's default currency, the default currency is also shown.

![FA value model balance.](media/RUS_FA_4%20model%20balance.JPG)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]