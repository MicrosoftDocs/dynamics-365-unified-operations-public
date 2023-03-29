---
title: Set up company to use a multiple price structures
description: This article explains how to set up multiple price structures within a company.
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form: GUPPricingTree, GUPParameters
ms.topic: how-to
ms.date: 04/03/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Set up company to use a multiple price structures

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

<!-- KFM: Preview until further notice -->

This article explains how to set up multiple price structures (price trees) within a company. In this scenario, the pricing engine will select a price structure based on the specified *price tree attribute*, which is one of the order attributes <!-- KFM: What is an "order attribute"? Maybe this?: [Define and set order attributes](../../commerce/dev-itpro/order-attributes.md) -->. Upon determining the applicable price structure, the price engine will match the sales order with the price component codes following the pricing sequence that is defined in the applicable price tree.  

In this case, companies and price structures have 1:N relationship, and these multiple price structures are called *Price trees*.

The purpose of a price structure is to establish the order in which the system calculates each type of price adjustment and establish other options, such as concurrency and compounding rules, for each price component code.

Price trees are the multiple-structure equivalent of the price component code setup for single price structures, and provide nearly all the same settings. See also [Set up company to use a single price structure](price-structure-single.md).

## Configure a company to use multiple price structures

To use multiple price structures for a company:

1. Select the company from the company picker.
1. Go to **Pricing management \> Setup \> Pricing management parameters**
1. Open the **Price attribute** tab and set **Enable multiple price trees** to *Yes*.
1. Set the **Price tree attribute** to the order attribute whose value you will use to select which price tree to use. <!-- KFM: No values shown here for USMF, even though lots of attributes are present. What are the requirements for an attribute to be listed here? How to set that up? Because of this, I was unable to test this feature while reviewing the documentation. -->

## Configure the price structures

Follow these steps to create and configure a price structure.

1. Go to **Pricing management \> Setup \> Price component codes \> Price trees**. This page shows your current price structures (if any), and allows you to add, remove, and configure your price trees.

    [<img src="media/price-trees-setup.png" alt="The Price trees page." title="The Price trees page" width="720" />](media/price-trees-setup.png#lightbox)

1. Do one of the following steps:
    - To add a new price tree, select **New** on the Action Pane.
    - To edit an existing price tree, select it on the list pane and then select **Edit** on the Action Pane.
    - To delete a price tree, select it on the list pane and then select **Delete** on the Action Pane.

1. Make the following settings in the header:
    - **Price tree** – Enter a name for the price tree
    - **Status** – Shows the current status of the price tree. Only price trees that show a **Status** of *Enabled* will affect your price calculations. To change this value, select **Disable** or **Enable** on the Action Pane. <!-- KFM: I assumed this. Please confirm. -->
    - **Description** – Enter a short description of the price tree.
    - **Enable mandatory check** – If you'd like to be able to mark one or more price component codes as mandatory, set this to *Yes*. <!-- KFM: Why would I set this to *No*? -->

1. On the **Price component code list** FastTab, add each price component code that should be part of the price structure for the current price tree. Use the buttons in the toolbar to add and remove lines as needed. These settings work in exactly the same as they do on the **Price component code setup** page. For details about how to make these settings, and examples of how they work, see [Arrange price component codes into a price structure](price-structure-details.md).

1. Continue working until you have set up all lines as required. Then select **Save** on the Action Pane.

1. On the Action Pane, select **Price tree attribute** to specify the value of the price tree attribute that will cause this price tree to apply to a given order. <!--KFM: What happens now? I couldn't do this. -->

1. On the Action Pane, select **Enable** to enable the current price tree. <!-- KFM: I assumed this. Please confirm. -->

## Auto charges in single and multiple price structures

Price component codes of type *Auto charges* are handled differently based on whether you ane using a single price structure (price component code setup) or multiple price structures (price trees).

- *If you are using a single price structure*, then you can add the price component code for auto charges in the price component code setup.
- *If you are using multiple price structures*, then you can't add auto charges in the price tree structures. The system will instead apply the standard Supply Chain Management auto-charge logic to decide which auto charges will apply to the sales order.
