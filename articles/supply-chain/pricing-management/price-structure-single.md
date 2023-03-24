---
title: Set up company to use a single price structure
description: This article explains how to configure a company to use a single price structure (price tree) and how to set up that structure.
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form: GUPPriceComponentCodeSetup, GUPParameters
ms.topic: how-to
ms.date: 04/03/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Set up company to use a single price structure

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

This article explains how to configure a company to use a single price structure (price tree) and how to set up that structure. In this scenario, the pricing engine matches each sales order with the price component codes based on the pricing sequence that is defined in the single tree.

In this case, companies and price structures have a 1:1 relationship, and this single price structure is called the *Price component code setup*.

The purpose of a price structure is to establish the order in which the system calculates each type of price adjustment and establish other options, such as concurrency and compounding rules, for each price component code.

The price component code setup is the single-structure equivalent of the price trees used for multiple price structures, and provides nearly all the same settings. See also [Set up company to use a multiple price structures](price-structure-multiple.md).

## Configure a company to use a single price structure

To use a single price structure for a company:

1. Select the company from the company picker.
1. Go to **Pricing management \> Setup \> Pricing management parameters**
1. Open the **Price attribute** tab and set **Enable multiple price trees** to *No*.

## Configure the single price structure

To set up the price structure for a company that uses a single structure, you will use the **Price component code setup** page, as described in the following procedure.

1. Go to **Pricing management \> Setup \> Price component codes \> Price component code setup**. This page shows your current price structure (if any), and allows you to add or remove price component codes in the structure. The components are grouped according to the **Price component** set for each listed price component code.

    [<img src="media/price-component-code-setup.png" alt="The Price component code setup page." title="The Price component code setup page" width="720" />](media/price-component-code-setup.png#lightbox)

1. Set up your price structure by adding and removing lines to establish a price sequence and make other settings for each price component code that you want to include. These settings work in exactly the same as they do on the **Price component code list** FastTab of the **Price trees** page. For details about how to make these settings, and examples of how they work, see [Arrange price component codes into a price structure](price-structure-details.md).

1. Continue working until you have set up all lines as required. Then select **Save** on the Action Pane.
