---
title: Use a single price structure within a company
description: This article explains how to set up one single pricing structure within a company. In this scenario, the pricing engine will be matching the sales order with the price component codes following the same pricing sequence that is defined in the single tree.
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form:
ms.topic: overview
ms.date: 03/03/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Use a single price structure within a company

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

This article explains how to set up one single pricing structure within a company. In this scenario, the pricing engine will be matching the sales order with the price component codes following the same pricing sequence that is defined in the single tree.

In this case, company and pricing tree have 1: 1 relationship. And this single pricing tree is called **Price component code setup**.

## Configure the price component code set up.

For the rule record of each price component code to work, a pricing structure with the price component codes must be built. This document illustrates how to set up the single price tree per company with the **Price component code setup** page.

1.  To configure price component code setup, go to **Pricing management &gt; Setup &gt; Price component code &gt; Price component code setup**.

![](media/image1.png)

2.  Select **New**, to add a new component in the list and make the following settings for the new code:

    - **Group by** – Shows the type of each price component code and groups the line in the list according to the price component (type). When you create a new code, a default value is chosen for this, but this will be replaced automatically when you choose the **Price component code**. You can't edit this value directly.

    - **Price component code** – Only those components can be added which are created in the **Price component codes** page. You can only have on the code setup for each price component code, so you will get an error if you select a price component code that is already included in the grid.

    - **Description** – Enter a short description.

    - **Price component** –Display the type of price component code.

    - **Pricing sequence** – Denotes the sequence the codes are supposed to follow, and sequence starts from lower number to the higher number. It is advised that you allow some room in the sequence for buffer so that you may subsequently insert more pricing component codes between them. For example, use 10, 20, 25, 30, rather than 1, 2, 3, 4.

The sequence is applicable for those price component codes that can be compounded within the same price component type：

- **Margin component price adjustments**

- **Discounts**

    - **Compounded**– This field **only** takes effect for those Price component codes that of the Price component= Margin component price adjustment. Using this checkmark, you can select whether you want to apply the price adjustment on the compounded price or the base price.

Below gives an example of the 'Compounded.'

| **Price Component Code** | **Description** | **Pricing Sequence** | **Calculation Method** | **Value** | **Compounded** | **Calculated Value** |
|-------------------------|-------------------------|-------------------------|-------------------------|-------------------------|-------------------------|-------------------------|
| Base</br>Price | Base Price- Inventory Cost | 10 |   |   |   | 1000.00 |
| MC01 | Ullage | 20 | Percent | 5 | No | 50.00 |
| MC02 | Freight | 30 | Percent | -2 | Yes | -21.00 |
| MC03 | Group Margin adjustment | 40 | Amount | 10 | No | 10.00 |
| MC04 | Contract Margin adjustment | 50 | Percent | 5 | Yes | 51.95 |
| MC05 | Pickup fee | 60 | Amount | 2 | Yes | 2.00 |
| MC06 | Other cost to sell | 70 | Percent | 5 | Yes | 54.64 |
| **Unit price** | **1147.59** |  |  |  |  |  |


The 'Compounded' will not apply to the discount compound behavior. To setup the discount compound behavior, go to the **Price management &gt; Setup&gt; Price management parameters&gt; Prices and discount** tab.

![](media/image2.png)

- **Post to Price Component Code** – When you check this field, it allows you to select the posting profile for this price component code.

- **Posting profile** – You can select the posting profile for this price component code. More posting rule will be covered in the Price component code posting profile section.

- **Default discount concurrency mode** – Display the default discount concurrency mode you set up in the Price component code.

- **Concurrency mode across priority** – The concurrency model across priority only applicable for those price component codes:

<!-- -->

- **Margin component price adjustment**: It always set as the '**Compounded.**' The System will first compute the price adjustment per each price component code and add up to the amount as the total price adjustment.

- **Discounts**: Concurrency mode can be either **Compounded** or **Best** price for the discounts. The setting will take effect when you set up the discount concurrency control as "**Best price and compounded within priority, best price and compound across priority"**

Here, the priority means the 'Pricing component code' with the sequence.

![](media/image3.png)

| **Price component code**   | **Price sequence** | **Concurrency mode across priority** | **Price component (type)** | **Computed value with the price component** |
|----------------------------|--------------------|--------------------------------------|----------------------------|---------------------------------------------|
| MAC01                      | 10                 | Compounded                           | Margin component           | $50                                         |
| MAC02                      | 20                 | Compounded                           | Margin component           | $20                                         |
| **Total price adjustment** | $70                |                                      |                            |                                             |
| DIS 01                     | 30                 | Best price                           | Discounts                  | $10                                         |
| DIS 02                     | 40                 | Best price                           | Discounts                  | **$20**                                     |
| DIS 03                     | 50                 | Compounded                           | Discounts                  | $30                                         |
| **Total discounts**        | $50                |                                      |                            |                                             |

3.  Select **Save**.
