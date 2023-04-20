---
title: Arrange price component codes into a price structure
description:
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form: GUPPricingTree, GUPParameters, GUPPriceComponentCodeSetup
ms.topic: how-to
ms.date: 04/03/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Arrange price component codes into a price structure

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Regardless of whether you're using a single price structure or multiple price structures, you use the same basic procedure to arrange your price component codes into a price structure. The only difference is that, if you use multiple price structures, you also define a condition to select the structure that's used in each situation.

- For information about how to create and manage a single price structure, see [Set up a company to use a single price structure](price-structure-single.md). Then, when you're ready to add, arrange, and configure the price component codes in the structure, return to this article.
- For information about how to create and manage multiple price structures, see [Set up a company to use multiple price structures](price-structure-multiple.md). Then, when you're ready to add, arrange, and configure the price component codes in each structure, return to this article.

## Configure a price structure

Follow these steps to create and configure a price structure.

1. Follow one of these steps:

    - If you're using a single price structure, follow the instructions in [Set up a company to use a single price structure](price-structure-single.md). Then go to **Pricing management \> Setup \> Price component codes \> Price component code setup**, and continue with step 2 of this procedure.
    - If you're using multiple price structures, follow the instructions in [Set up a company to use multiple price structures](price-structure-multiple.md). Then go to **Pricing management \> Setup \> Price component codes \> Price trees**, create or select a price tree, select the **Price component code list** FastTab, and continue with step 2 of this procedure.

1. Add each price component code that should be part of the current price structure. Use the buttons on the toolbar to add and remove lines as required. The following fields are available for each line:

    - **Group by** – In the grid, the price component codes are grouped by type. The type is shown in the **Group by** column, and the relevant price component codes are indented under their group name. When you first create a new code, a default group is selected for it. However, the default group will automatically be replaced when you select a value in the **Price component code** field. You can't edit this field directly.
    - **Price component code** – If you're adding a new line, select an existing price component code for it. (You can't edit this field for existing lines.) Each price component code can appear only once in the list. Therefore, you'll receive an error if you try to select a code that's already listed. For information about how to create and configure price component codes, see [Price component codes](price-component-code.md).
    - **Description** – Enter a short description.
    - **Price component** – This field shows the type of the price component code that was selected for the line. The value comes from the **Price component** setting of the selected price component code and establishes the group that the line was put into.
    - **Pricing sequence** – Enter an integer to define a calculation sequence for the different lines. The calculation proceeds from the lowest sequence number to the highest number. We recommend that you leave some space between numbers, so that there's room for new pricing components to be added between existing lines later. For example, use *10*, *20*, *30*, *40*, and so on, instead of *1*, *2*, *3*, *4*, and so on. The sequence can have a significant effect on the final unit price, especially if you use percentage-based calculations and compounding.
    - **Compound** – This checkbox applies only to price component codes where the **Price component** field is set to *Margin component*. Select the checkbox for lines where you want to calculate the price adjustment based on the compound price (running total). Clear it for lines where you want to calculate the price adjustment based on the original base price. For discounts, the compounding behavior is controlled instead by the **Discount compound behavior** setting on the **Pricing management parameters** page. (For more information, see [Resolve concurrency across price component codes](concurrence-cross-codes.md).)
    - **Post to price component code** and **Posting profile** – To post to a price component code, select the **Post to price component code** checkbox, and then select the posting profile that you want to use. For more information, see [Price component posting](price-component-posting.md).
    - **Default concurrency mode** – This field shows the default concurrency mode that was set for the selected price component code. For information about how to set the default concurrency mode and interpret its value, see [Price component codes](price-component-code.md).
    - **Concurrency mode across priority** – This field applies only to lines where the **Price component** field is set to either *Margin component* or *Discounts*. Select one of the following values:

        - *Compounded* – The system will first compute the price adjustment or discount for each line in the structure. It will then calculate the final discount or adjustment by adding the value for every line. This value is available only for lines where the **Price component** field is set to *Discounts* or *Margin component*. (It's the only available value for margin components.)
        - *Best price* – If the price structure includes more than one price component code that has this value, only one of those lines (the one that has the largest discount) will contribute to the final unit price. This value is available only for lines where the **Price component** field is set to *Discounts*.

        This field affects discount calculations only when the **Best price and compound concurrency control model** field on the **Pricing management parameters** page is set to *Best price and compound within priority, best price and compound across priority*. For more information, see [Resolve concurrency across price component codes](concurrence-cross-codes.md).

    - **Mandatory** – This field isn't available on the **Price component code setup** page. It's available only on the **Price trees** page. (For more information, see [Use multiple price structures within a company](price-structure-multiple.md).) For price trees where the **Enable mandatory check** option is set to *Yes*, use this checkbox to mark each price component code that's mandatory in the sales order. If a price component code isn't applicable, an error will be shown.

    > [!NOTE]
    > If you use multiple price structures (price trees), they can't include price component codes where the **Price component** field is set to *Auto charge*. Instead, the system will apply the standard auto charge logic in Microsoft Dynamics 365 Supply Chain Management. In other words, if an auto charge rule record is applicable, the auto charge will apply to the sales order. You can include auto charge components in the price structure for [companies that are configured to use a single price structure](price-structure-single.md).

    [<img src="media/price-component-code-setup.png" alt="Price component code setup page." title="Price component code setup page" width="720" />](media/price-component-code-setup.png#lightbox)

1. When you've set up all the lines that you need in your price structure, select **Save** on the Action Pane.
