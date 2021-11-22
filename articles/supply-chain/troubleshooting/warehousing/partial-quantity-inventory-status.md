--- 
title: Make inventory status change for partial quantity work 
description: This page explains how to create a menu item with the appropriate settings to enable workers to make an inventory status change for partial quantity of a batch. 
author: perlynne 
ms.date: 06/24/2021 
ms.topic: troubleshooting 
# ms.search.form:  
audience: Application User 
ms.reviewer: kamaybac 
ms.search.region: Global 
ms.author: perlynne 
ms.search.validFrom: 2021-06-24 
ms.dyn365.ops.version: 10.0.20 
--- 

# Enable inventory status change for partial quantity work

## Symptoms

You need to make an inventory status change for a partial quantity of a batch.

## Resolution

To enable workers to make this change, you can create a menu item for the Warehouse Management mobile app. On the **Mobile device menu items** page, create (or edit) a menu item that has the following settings:

- **Mode:** *Work*
- **Use existing work:** *No*
- **Work creation process:** *Movement*
- **Display inventory status:** *Yes*

You can set other fields on the page as you require.
