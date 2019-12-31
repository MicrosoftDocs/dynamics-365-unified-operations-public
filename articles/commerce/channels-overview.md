---
# required metadata

title: Channels overview
description: This topic presents an overview of Microsoft Dynamics 365 Commerce channels.
author: samjarawan
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.8

---
# Channels overview

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic presents an overview of Microsoft Dynamics 365 Commerce channel set up. It includes information about the tasks that you must complete both before and after you set up each channel.

## Channels
Dynamics 365 Commerce supports three different channel types: **Retail**, **Call Center** and **Online**.  Below you'll find details relating to each. 

### Retail channel
Retail channels represent standard brick-and-mortar stores. Each retail store can have its own point of sale (POS) registers, income accounts and expense accounts, and staff. 

### Call Center channel
Call center channels represent call center order and customer management.

### Online channel
Online channels represent online e-Commerce storefronts. Once an online channel is created a site must be created using the [site builder](link tbd) tool or third part e-Commerce solutions can be used.

## Channel set up basics
Channel set up is perfomed in the Commerce Headquarters tool. Each channel can have its own payment methods, price groups, product hierarchies, assortments and set of products. After you create the channel, you assign the products that you want it to carry and sell. Each channel type has a unique set of features that may need to be configured, for example, a retail channel needs assigned employees, registers, and customers. Once a new channel is created it need to be assigned to an organization hierarchy.

## Channel setup prerequisites
Before you can set up a channel, you must complete some prerequisite tasks based on the channel type. For more information see
[channel prerequisites](channels-prerequisites.md).

## Set up a channel
After you complete the prerequisite tasks, follow the link to the channel type you want to create for set up instructions.
[Set up a Retail channel - tbd](channel-setup-retail.md)
[Set up a Call Center channel - tbd)(channel-setup-callcenter.md)
[Set up an Online channel - tbd)(channel-setup-online.md)

## Post channel configuration
After you create a channel, you may need to complete some of the below tasks:

* Configure the POS registers for the store.
* Assign product assortments to the store.
* Process assortments to generate the list of products that are included in the assortment and to make the products available in the retail store.
* Send data such as number sequences, hardware profiles, and POS screen layouts to the Retail POS registers.
* Publish the retail store to send store data to Retail POS.
* Run the jobs to send the store data to Retail POS.
