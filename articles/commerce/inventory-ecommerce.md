---
# required metadata

title: Inventory settings on ecommerce
description: This topic covers how inventory settings work on ecommerce
author:  anupamar-ms
manager: annbe
ms.date: 04/24/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: 
ms.author: anupamar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: 
---

# Inventory settings on ecommerce


[!include [banner](includes/banner.md)]

This topic covers Inventory settings and describes how these settings can be applied across ecommerce

## Overview
Inventory settings for e-commerce are defined in Site builder under Sites Settings\Extensions within a  group called "Inventory". These settings enable Inventory checks on e-commerce. The inventory checks  provide the capability for a retailer to showcase inventory driven merchandising such as "In Stock" "Only few left" etc. When a product is out of stock these settings ensure the product cannot be purchased.

Microsoft Dynamics 365 Commerce provides on-hand availability for products which is used on e-commerce to drive the inventory scenarios. For details on how estimated on-hand availability is calculated for products see this  https://docs.microsoft.com/en-us/dynamics365/commerce/calculated-inventory-retail-channels. 

## Defining inventory thresholds and ranges on HQ

## Site settings on ecommerce 

**Enable inventory check on app** - This setting turns on inventory check on ecommerce. When this setting in on, BuyBox, Cart, Pick up in store modules will check for inventory. 

**Inventory level based on** -  In Dynamics 365 Commerce, inventory threshold and ranges can be defined for each product/category. The inventory APIs return the product inventory information, inventory thresholds are defined in HQ based on which the corresponding display messages are provided to e-commerce. This information is returned for both **Total Available** and **Physical Available**. Its upto the retailer to decide if Total Available or Physical Available should be used for determing the inventory count and the corresponding ranges for in-stock, out-of-stock etc. 

Alternatively, there is a legacy ecommerce setting called **Inventory out of stock threshold**. When this setting is used inventory count is determined from Total Available but thresholds are defined by the Inventory out of stock threshold setting in Site builder.  Its a single threshold for all products across the site. If inventory is below threshold its considered out of stock else in-stock. Overall it is limited in capabilities and not recommended to use if you are using 10.0.12+.

**Inventory ranges to display** - With the inventory ranges a retailer may still choose to decide which type of messages are shown on the BuyBox, Cart, etc. It has settings to show **All**, **Low and out of stock**, **Out of stock**. When All is selected, all inventory ranges from In-stock(AVAIL) to out of stock (OOS) will be shown. When Low and out of stock is chosen, all ranges excpet In Stock(AVAIL) will be displayed. When Out of stock is selcted, only out of stock messages (OOS) will be displayed. THis gives the retailer the flexibility to decide which messages to display across the site.

**Out of stock threadshold**  - As mentioned earlier, this is a legacy setting. For this setting to take effect, you have to choose "Out of stock threshold" property in the "Inventory level based on" setting.

## Modules that use the inventory setting on ecommerce
Buy box, Cart, Wishlist, Store selector, Cart icon modules rely on the inventory settings. These modules display inventory ranges and/or error messages when a product cannot be added to cart due to lack of inventory. 

## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Buy box](add-buy-box.md)

[Cart]

[Wishlist]

[Store selectpr]
