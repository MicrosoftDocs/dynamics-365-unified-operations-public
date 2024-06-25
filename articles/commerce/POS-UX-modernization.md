---
title: POS UX upgrade
description: This article describes store commerce UX modernization features.
author: anush6121
ms.author: anvenkat 
ms.topic: article 
ms.date: 06/24/2024
ms.custom: 
  - bap-template
ms.reviewer: v-chrgriffin
---

# POS UX modernization

The article describes the store commerce UX modernization features and how to enable them.

## Streamlined workflow for adding items to a transaction from the product page:

When you add an item to the cart from the product description page or search results, a confirmation dialog is now displayed with the list of products being added. Navigation options to go to the transaction or stay on the product or search page are added. Additionally, a new configuration option in the Visual profile in Headquarters can be used to bypass the confirmation dialog and take the user directly to the transaction when an item is added to the sale.
To bypass the item added dialog and directly go into the transaction page upon adding an item set **Bypass Item added dialog** under **General** section in **POS visual profiles** to **yes** in headquarters.

## Configure display of search results:

The default view for displaying search results can now be configured in the Visual profile in Headquarters. Before this release, the default view for search results for products, customer and categories was list view, but we received feedback from customers that they prefer card view, especially on mobile devices. To enable your search view preference, set **default view** for **Search view** under **General** section in **POS visual profiles** to **List view** or **Card view** in headquarters.

## Reset button grids at the end of a transaction:

To reduce confusion and provide a consistent experience for point of sale users, the default button grid assigned to the first tab is restored when a transaction is completed, suspended, or voided. This feature is enabled by default to all users.

## Reprint receipts from journal:

To reduce number of clicks in reprinting receipts, **print receipt** button is available on the bottom of  **show journal** screen. To reprint receipts, select journal and **print receipt** in a single click.

## Enhanced date picker:

To allow for customer's customization and localization needs, the date picker in store commerce app has been enhanced.

## Persist Zoom level:

Store associates can persist the zoom settings to fix their display and not have to adjust it again. This is especially useful for those that run the devices in kiosk mode without keyboard and mouse.

