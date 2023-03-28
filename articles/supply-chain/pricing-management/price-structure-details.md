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

Regardless of whether you are using a single price structure or multiple price structures, the procedure for arranging your price components codes into a price structure is the same. The only difference is that when you use multiple price structures, you'll also set a condition for choosing which structure to use in each situation.

- For instructions on how to create and manage a single price structure, see [Set up company to use a single price structure](price-structure-single.md). Then return here when you're ready to add, arrange, and configure the price component codes in the structure
- For instructions on how to create and manage multiple price structures, see [Set up company to use a multiple price structures](price-structure-multiple.md). Then return here when you're ready to add, arrange, and configure the price component codes in each structure.

## Configure a price structure

Follow these steps to create and configure a price structure.

1. Do one of the following steps:
    - If you are using a single pricing structure, then follow the instructions given in [Set up company to use a single price structure](price-structure-single.md). Then go to **Pricing management \> Setup \> Price component codes \> Price component code setup** and continue with this procedure.
    - If you are using multiple pricing structures, then follow the instructions given in [Set up company to use a multiple price structures](price-structure-multiple.md). Then go to the **Pricing management \> Setup \> Price component codes \> Price trees**, create or select a price tree and expand the **Price component code list** FastTab and continue with this procedure.

1. Add each price component code that should be part of the current price structure. Use the buttons in the toolbar to add and remove lines as needed. The following settings and information are available for each line.

    - **Group by** – In the grid, the price component types are grouped by type, with the type shown in this column and the relevant price component codes shown as indented under their group name. When you create a new code, a default group is chosen for this, but it will be replaced automatically when you choose the **Price component code**. You can't edit this value directly.
    - **Price component code** – If you're adding a new line, then select an existing price component code for the line (you can't edit this for existing lines). Each price component code can appear only once in the list, so you'll get an error if you try to choose one that is already listed. For details about how to create and configure price component codes, see [Price component codes](price-component-code.md).
    - **Description** – Enter a short description.
    - **Price component** – Shows the type of the price component code selected for the line. This comes from the **Price component** setting of the selected price component code and establishes the group into which line is placed.
    - **Pricing sequence** – Enter an integer to establish a calculation sequence for the various lines. The calculation proceeds from the lowest sequence number to the highest number. We recommend that you leave some space between your numbers to allow for new pricing components to be added in between existing lines later. For example, use 10, 20, 30, 40, and so on instead of 1, 2, 3, 4. The sequence can have a significant effect on the final unit price, especially if you use percentage-based calculations and compounding.
    - **Compound** – This setting only applies to those price component codes where **Price component** is *Margin component*. Select this check box for lines where you want to calculate the price adjustment based on the compound price (running total). Clear this check box for lines where you want to calculate the price adjustment based on the original base price. For discounts, the compounding behavior is instead controlled by the **Discount compound behavior** setting on the **Pricing management parameters** page (see the [Resolving concurrent price codes within a price structure](price-structure-concurrence.md) for details).
    - **Post to price component code** and **Posting profile** – To post to a price component code, select the **Post to price component code** check box and then choose the **Posting profile** you want to use. See also [Price component posting](price-component-posting.md)
    - **Default concurrency mode** – Shows the default concurrency mode set for the selected **Price component code**. For details about how to make this settings and how to interpret its value, see [Price component codes](price-component-code.md).
    - **Concurrency mode across priority** – This setting only applies for lines where the **Price component** is either *Margin component* or *Discounts*. Select one of the following values:
        - *Compounded* – The system will first compute the price adjustment or discount for each line in the structure and then will calculate the final discount or adjustment by adding up the value for each line. This value is only available for lines with a **Price component** of *Discounts* or *Margin component* (For margin components, this is the only available setting).
        - *Best price* – If the price structure includes more than one price component code with this setting, then  only one of those lines will contribute to the final unit price (the one with the highest discount).  This value is only available for lines with a **Price component** of *Discounts*.

        This setting only affects discount calculations when the **Best price and compound concurrency control model** is set to *Best price and compound within priority, best price and compound across priority* on the **Pricing management parameters** page. See [Resolving concurrent price codes within a price structure](price-structure-concurrence.md) for details.

    - **Mandatory**– This setting isn't available on the **Price component code setup** page, it's only on the **Price trees** page (see also [Use multiple price structures within a company](price-structure-multiple.md)). For price trees where **Enable mandatory check** is set to *Yes*, use this check box to mark each price component code that is mandatory in the sales order, in case of not applicable, it will post an error. <!--KFM: This isn't clear. What do we mean by price component code to be mandatory in an order? What happens if it isn't there? Does the error mentioned here only occur when setting up the price tree? -->

    > [!NOTE]
    > When you use multiple price structures (price tress), your price structures can't include price component codes with a **Price component** of *Auto charge*. Instead, the system will apply the standard Supply Chain Management auto-charge logic, which means that when an auto-charge rule record is applicable, the auto charge will apply to the sales order. You can include auto charge components in the price structure for [companies configured to use a single price structure](price-structure-single.md).

1. Continue working until you have set up all the lines you need in your price structure.

1. Select **Save** on the Action Pane.
