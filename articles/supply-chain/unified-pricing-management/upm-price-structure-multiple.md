---
title: Set up a company to use multiple price structures
description: Learn how to set up multiple price structures in a company, including a step-by-step process for configuring a company to use multiple price structures.
author: sherry-zheng
ms.author: chuzheng
ms.topic: how-to
ms.date: 05/28/2026
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form: GUPPricingTree, GUPParameters
---

# Set up a company to use multiple price structures

[!include [banner](../includes/banner.md)]

This article explains how to set up multiple price structures in a company. A price structure defines the order in which the system calculates each type of price adjustment. It also defines other options for each price component code, such as concurrency and compounding rules.

In this scenario, companies and price structures have a one-to-many (1:N) relationship. In addition, there are multiple price structures. The pricing engine selects a price structure based on the specified **Price tree attribute**, which is one of the order attributes. After it determines the applicable price structure, the price engine matches the sales order with the price component codes according to the pricing sequence that's defined in the applicable price tree.

## Configure a company to use multiple price structures

Follow these steps to use multiple price structures for a company.

1. Select the company in the company picker.
1. Go to **Pricing management > Setup > Pricing management parameters**.
1. On the **Price attribute** tab, set the **Enable multiple price trees** option to *Yes*.
1. Use the value of one of the order attributes to select which price tree to use. Set the **Price tree attribute** field to the order attribute that you want to use.

## Configure the price structures

Follow these steps to create and configure a price structure.

1. Go to **Pricing management > Setup > Price component codes > Price trees**. The **Price trees** page shows your current price structures (if you have any), and lets you add, remove, and configure price trees.

    :::image type="content" source="media/price-trees-setup.png" alt-text="Screenshot of current price structures on the Price trees page." lightbox="media/price-trees-setup.png":::

1. Follow one of these steps:

    - To add a new price tree, select **New** on the Action Pane.
    - To edit an existing price tree, select it in the list pane, and then select **Edit** on the Action Pane.
    - To delete a price tree, select it in the list pane, and then select **Delete** on the Action Pane.

1. On the header of the new or selected price tree, set the following fields:

    - **Price tree** – Enter a name for the price tree.
    - **Status** – This field shows the current status of the price tree. Only price trees that have a **Status** of *Enabled* affect your price calculations. To change the status, select **Disable** or **Enable** on the Action Pane.
    - **Description** – Enter a short description of the price tree.
    - **Enable mandatory check** – If you want to mark one or more price component codes as mandatory, set this option to *Yes*.

1. On the **Price component code list** FastTab, add each price component code that should be part of the price structure for the current price tree. Use the buttons on the toolbar to add and remove lines as required. For information about how to set these fields, and examples that show how the settings work, see [Arrange price component codes into a price structure](upm-price-structure-details.md).
1. When you set up all lines as required, select **Save** on the Action Pane.
1. On the Action Pane, select **Price tree attribute** to specify the value of the price tree attribute that causes this price tree to apply to a given order.
1. On the Action Pane, select **Enable** to enable the current price tree.

## Auto charges in single and multiple price structures

Price component codes of the *Auto charges* type work differently depending on whether you use a single price structure or multiple price structures.

- *If you use a single price structure*, you can add the price component code for auto charges in the price tree.
- *If you use multiple price structures*, you can't add auto charges in the price tree structures. Instead, the system applies the standard auto charge logic to determine which auto charges apply to the sales order.
