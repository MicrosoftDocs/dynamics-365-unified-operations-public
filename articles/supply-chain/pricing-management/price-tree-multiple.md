---
title: Use multiple price structures within a company
description: This article explains how to set up multiple price structures within a company. In this scenario, the pricing engine will use the price tree attribute, one of the order attributes that is used to determine the price structure (price tree). Upon determining the applicable price structure, the price engine will be matching the sales order with the price component codes following the pricing sequence that is defined in the applicable price tree.  
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

# Use multiple price structures within a company

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

This article explains how to set up multiple price structures within a company. In this scenario, the pricing engine will use the price tree attribute, one of the order attributes that is used to determine the price structure (price tree). Upon determining the applicable price structure, the price engine will be matching the sales order with the price component codes following the pricing sequence that is defined in the applicable price tree.  

In this case, company and pricing tree have 1: N relationship. And these multiple price structures are called **Price trees**. 

## Configure the price trees

Pricing Management provides you with another option to set up multiple price structure with the price trees.

This document illustrates how to set up the multiple price structure with **Price trees** page.

It is the pre-requisite that you go to the **Pricing management &gt; Setup&gt; Pricing management parameters** to enable the multiple price trees feature.

Please refer to 'Build price structure with price trees' section for details.

To enable the multiple price trees feature, you must first navigate to **Pricing management &gt; Setup&gt; Pricing management parameters &gt;Price attribute** tab.

Follow below steps to enable the Price trees page:

1.  To configure price component code setup, go to **Pricing management &gt; Setup &gt; Price component code &gt; Price trees**.

![](media/image1.png)

2.  Select **New**, to add a new component in the list and make the following settings for the new code:

    - **Group by** – Shows the type of each price component code and groups the line in the list according to the price component (type). When you create a new code, a default value is chosen for this, but this will be replaced automatically when you choose the **Price component code**. You can't edit this value directly.

    - **Price component code** – Only those components can be added which are created in the **Price component codes** page. You can only have on the code setup for each price component code, so you will get an error if you select a price component code that is already included in the grid.

    - **Description** – Enter a short description.

    - **Enable mandatory check**– Enable this check you will have the option to mark specific price component code which must be applied to the sales order. Otherwise, it will post an error to notify in the sales order. We advise you to think carefully and only use this feature when you wish to enforce a specific price component code because enabling this feature will have following implications:

-   If you choose to allow this check, the performance will be affected, and

-   The sales order process will fail with error when the mandatory price component code's rule records don't meet the criteria and cannot be applied to the sales order.

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

- **Discounts**: Concurrency mode can be either **Compounded** or **Best** price for the discounts.

The setting will take effect when you set up the discount concurrency control as "**Best price and compounded within priority, best price and compound across priority"**

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

- **Mandatory**– When you set 'Enable mandatory check' as Yes, you are allowed to mark which price component codes are mandatory in the sales order, in case of not applicable, it will post an error.

3.  Select **Save**.

4.  In the head panel, select the **Price tree attribute** button to specify the value of the price tree attribute. As mentioned early, you need to identify one price tree attribute out of the order attributes in the **Pricing management &gt; Setup&gt; Pricing management parameters &gt;Price attribute** tab.

![Graphical user interface  text  application Description automatically generated](media/image4.png)

5.  Click **Enable** to enable the created price tree. Use Disable button to disable if applicable.

**Note**

In the Price trees enabled scenario, you are not allowed to set up the Auto charge price component code in the Price tree.

As the system will follow the Auto charge logic that as long as you maintained the applicable auto charge rule record, system will apply to the sales order.
