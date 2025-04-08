---
title: Fixed assets accounting for tax purposes
description: Learn about the tax Depreciation functionality for Latvia, including fields to consider when setting up a depreciation profile.
author: evgenypopov
ms.author: evgenypopov
ms.topic: conceptual
ms.custom: 
  - bap-template
ms.date: 06/20/2017
ms.reviewer: johnmichalak
ms.search.region: Latvia
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611
ms.search.form: AssetBookTable, AssetDepreciationProfile, AssetTable, AssetTaxDepreciation
ms.assetid: cbf94106-2c1b-45dd-8734-18a2a56a4682
---

# Fixed assets accounting for tax purposes

[!include [banner](../../includes/banner.md)]

This article provides information about the tax depreciation functionality for Latvia, including the tax depreciation setup and calculation and printing the tax depreciation report. 
> [!NOTE]
> Tax depreciation works with the value models. The value model and depreciation book have been merged into a single concept that is called a *book.* For more information, see [Fixed asset value model and depreciation book merge](../../fixed-assets/fixed-asset-value-model-depreciation-book-merge.md).

## Set up a depreciation profile
When you set up a depreciation profile, consider the following.

  - **Depreciation year**: Select the type of year that you use to calculate the depreciation. The depreciation year and the period frequency are related. Therefore, the options **Period frequency** field depend on the **Depreciation year** field value.                                                                                 
  - **Period frequency**: Select the frequency of ledger accruals during the calendar year or fiscal year. The options that appear in this field vary, depending on the depreciation year that you selected. If you selected **Calendar** as the depreciation year, the options are **Yearly**, **Monthly**, **Quarterly**, **Half-yearly**. 
  - **Full depreciation**: Select this option to fully depreciate the fixed asset when the service life that remains is 0 (zero).                                                                                                                                                                                                             

<!---To set up a depreciation profile, complete the following procedure, [Set up and create depreciation profiles](../../fixed-assets/tasks/set-up-depreciation-profiles.md).-->

## Set up books
Use the **Books** page to define a tax category. Books are also referred to as tax categories. To create a book, select the depreciation profile that has **Reducing balance** selected in the **Method** field in the **Depreciation profiles** page. The **Books** page for legal entities in Latvia contain the following fields:

-   **Posting layer** - Select **Tax** in this field.
-   **Summarize for category** - Select this option if tax depreciation should be summarized and calculated for all fixed assets that have the same book selected in the **Category** field.
-   **Tax coefficients** - You can set up tax coefficients for each coefficient to adjust the acquisition price for the fiscal year.

For more information about setting up books, see [Set up depreciation books (May 2016)](../../fixed-assets/tasks/set-up-depreciation-books-2016-05.md).

### Set up tax depreciation calculation

To set up tax depreciation calculation, on the **Fixed assets** page, select a fixed asset. Then, on the **General** FastTab, select a **Book** in the **Category** field. A fixed asset should only have one book associated in the current posting layer. 
> [!NOTE]
> This field displays the books record with a posting layer value equal to Tax only.

## Calculate tax depreciation
To calculate fixed asset tax depreciation, on the **Tax depreciation** page, create a New tax period to use for reporting.

|    Field name         |                       Description                                                                                                                                         |
|-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Start date**    | Select the date from which the period is valid.                                                                                                                |
| **End date**      | Select the date up to which the period is valid.                                                                                                               |
| **Period status** | Select the period status (**Open** or **Closed**). If the status is **Closed**, **Categories** on the **Category details** FastTab cannot be added or deleted. |

On the **Category details** FastTab, select the book in the **Category** field that you want to calculate tax depreciation for. Click **Calculate** to calculate tax depreciation. Tax depreciation calculates for either individual fixed assets or is based on summary information from all fixed assets that are assigned to the same fixed asset tax category. The calculation is based on the tax coefficient from the selected book, and accounting data on the books of fixed assets associated with the book selected in the **Category** field.

|               Calculation formulas                                                                               |
|------------------------------------------------------------------------------------------------------------------|
| Adjusted Value  = Starting Balance + Value adjustments - Disposal + Acquisition price \* Acquisition Coefficient |
| Tax Depreciation amount = Adjusted Value \* Base Depreciation \*2 /100 \* number of months in period / 12        |
| End Balance = Adjusted Value – Tax Depreciation amount                                                           |
| Starting Balance (current depreciation period) = End Balance (previous depreciation calculation period)          |

To view the tax depreciation details, click **Tax depreciation details** to open the **Tax depreciation details** page.

## Print the Tax depreciation report
The **Tax depreciation** report provides Latvian users with tax reporting that is relevant to fixed assets in a company. To print the report, go to the **Tax depreciation calculation** page, select a specific record to summarize at the **Category** level. Click **Tax depreciation report** for categories that are not summarized using the **Tax depreciation** report.





[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
