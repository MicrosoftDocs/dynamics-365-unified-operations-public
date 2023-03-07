---
title: Price trees overview
description: This article provides an overview of how price structures work in Pricing management
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

# Price trees overview

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

You can check the detailed price breakdown including the price component when a sales order is placed. The breakdown corresponds to the price structure that you have configured. The price details that are shown give an audit record of how the price was determined and serve as a starting point for future price investigation.

The following two methods are available for building the price structure:

- **Price component code setup** – Provides a single, uniform pricing structure for each company.
- **Pricing trees** – Enables multiple pricing structures based on order attribute values for each company.

![Chart  treemap chart Description automatically generated](media/image1.png)

## Price component types

There are some principles about the price structure:

| Price component (type) | Price position | Details |
|---|---|---|
| Base price | Unit Price | The base price, which is SKU-level, represents the common price for general use.</br>You can choose *one* of the base price types:<ul></br><li>Base price- inventory price</li><li>Base price- purchase price</li><li>Base price- Sales price</li></ul>The base price source from Item base price form, either manually enter or through calculation.</br></br>If you setup the Bae price in the price structure (Price component code setup\Price tress), and there is no record found in the Item base price form.</br></br>Then, the system will check whether the item is a standard cost item and source the base price from the activate item standard cost. |
| Sales trade agreement price | Unit Price | The Sales trade agreement price shall prevail over the Base Price as it represents the special price arrangement with a particular group of consumers for a certain set of products.</br></br>You can set up *one* price component code for Sales trade agreement price.</br></br>Within the price component code, you can define multiple price rule records, and the concurrency model (parameter level configuration) are:<ul><li>**Find next:** Find the all the applicable records and apply with the cheapest price.</li><li>**Price attribute combination rank:** Find the record that have the highest price attribute combination rank, and apply the price</li></ul> |
| Margin component price adjustment | Unit Price | The Margin component price adjustment represents a list of price adjustment up and down based on top of the Base price or Sales trade agreement price.</br></br>Unit price= Base price\Sales trade agreement price+\ Margin component price adjustment.</br></br>Each price component (type) allows *multiple* price component codes. Within the price component code, you can define multiple price rule records, and the concurrency models are:<ul><li>**Price attribute combination rank:** Find the records that have the highest price attribute combination rank and apply the price.</li></ul>The system will find the applicable rule records in each price component code, and then *compound* the result into price adjustments. |
| Discounts | On-invoice discounts | Depending on the business usage, you can group various discount rule records into different discount types of price component codes.</br></br>This differs from the discount type, the later one is calculation method relevant.</br></br>Each price component (type) allows *multiple* price component codes. Within the price component code, you can define multiple price rule records, and the concurrency models are:<ul><li>Best price</li><li>Compounded</li><li>Exclusive</li><li>Always apply</li><li>Price attribute combination rank</li></ul> |
| **Rebate** | **Off-invoice discounts** | Depending on the business usage, you can group various rebate rule records into different rebate types of price component codes.</br></br>Each price component (type) allows *multiple* price component codes. Within the price component code, you can define multiple price rule records, and the concurrency models are:<ul><li>**Price attribute combination rank:** Find the records that have the highest price attribute combination rank and apply the price.</li></ul> |

> [!NOTE]
> The auto charge for sales is another distinction between the Price component code setup (single price tree) and Price trees (multiple price trees).
>
> - **Price component code setup:** You can add the Price component code for auto charge in the price tree structure configuration.
> - **Price trees**: Auto-charges are not included in the Price tree structure. It will operate according to standard Dynamics 365 Supply Chain Management Auto charge logic, which means that when a rule record is applicable, the auto charge will apply to the sales order.

## Choose a single tree or multiple trees

Price management by default allows you to set up one single structure per company, which is the Price component code setup.

## Single tree configuration

To configure price component code setup, go to **Pricing management \> Setup \> Price component code \> Price component code setup.**

![Graphical user interface  application  table Description automatically generated with medium confidence](media/image2.png)

## Multiple trees configuration

Based on your pricing structure, if you want to switch to the multiple trees structure per company, you need to enable the multiple price tree in the parameters.

To enable the multiple price trees:

1. Go to **Pricing management \> Setup \> Pricing management parameters**
1. Go to the Price attribute tab and set 'Enable multiple price trees' as Yes.
1. And then select the Price tree attributes. The Price tree attributes are **one** of the order attributes that you have configured.

![Graphical user interface  application Description automatically generated](media/image3.png)

As was previously indicated, you must give the value of the pricing tree attribute a value when entering a sales order. The value serves as the system's trigger for choosing which price tree to use to determine the price along the price tree.

To configure price component code setup, go to **Pricing management \> Setup \> Price component code \> Price trees**

You can build multiple price tree structure here, for example:

- Price tree 1- Standard

![Graphical user interface  application Description automatically generated](media/image4.png)

Click **Price tree attributes** in the panel, you can see this price tree is associated with:

| **Order attribute** | **Value** |
|---------------------|-----------|
| Order pool          | Standard  |

![Graphical user interface  text  application Description automatically generated](media/image5.png)

- Price tree 2- Campaign sell

![Graphical user interface  application Description automatically generated](media/image6.png)

Click **Price tree attributes** in the panel, you can see this price tree is associated with:

| **Order attribute** | **Value** |
|---------------------|-----------|
| Order pool          | Campaign  |

![Graphical user interface  application Description automatically generated](media/image7.png)

More details will be covered in the following section on how to configure price component code setup and multiple price trees.
