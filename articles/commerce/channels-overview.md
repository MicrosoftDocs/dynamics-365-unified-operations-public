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

This topic presents an overview of setting up Microsoft Dynamics 365 Commerce channels.

## Overview
This topic provides an overview of the section on setting up the various Dynamic 365 Commerce channels. It includes information about the tasks that you must complete both before and after you set up each channel. 

## Channels
Dynamics 365 Commerce supports three different channel types: **Retail**, **Call Center** and **Online**.  Below you'll find details relating to each. 

### Retail channel
Retail channels represent standard brick-and-mortar stores. Each retail store can have its own point of sale (POS) registers, income accounts and expense accounts, and staff. 

### Call Center channel
Call center channels(TBD).

### Online channel
Online channels represent online e-Commerce storefronts. Once an online channel is created a site must be created using the [site builder](link tbd) tool.

## Channel set up basics
Channel set up is perfomed in the Commerce Headquarters tool. Each channel can have its own payment methods, price groups, product hierarchies, assortments and set of products. You must set up some of these elements before you create the channel but they can be modified afterwards as well. After you create the channel, you assign the products that you want it to carry. You also assign employees, registers, and customers to retail channels. Finally, you add the new channel to an organization hierarchy.

## Channel setup pre-requisites
Before you can set up a channel, you must complete some prerequisite tasks. You can then create the channel and add details.

* [Define and configure your legal entity structure](tbd.md)
* [Configure your organizational hierarchy](tbd.md)
* [Set up a warehouse](tbd.md)
* [Set up a default customer](tbd.md)
* [Set up a customer address book](tbd.md)
* [Set up an employee address book](tbd.md)
* [Set up an email notification profile](tbd.md)
* [Set up a functionality profile](tbd.md)
* [Set up sales tax groups](tbd.md)
* [Set up a screen layout](tbd.md) (Retail only)
* [Set up a hardware station](tbd.md) (Retail only)
* [Set up number sequences, store statements and statement vouchers](tbd.md)
* [Configure parameters for Commerce](tbd.md)
* [Set up methods of payments](tbd.md) 
* [Set up payment services to process credit card transactions](tbd.md)
* [Set up modes of delivery](tbd.md)
* [Set up products](tbd.md) As part of this task, you'll also set up retail product hierarchies, product variants, and product assortments.
* [Set up product price groups](tbd.md)
* [Set up product pricing](tbd.md)  As part of this task, you also set up price adjustments, discounts and discount periods.
* [Set up staff members]
* [Configure the Retail POS profiles to assign to the store](tbd.md).  This task includes many other tasks, such as setting up registers, setting up offline profiles and setting up receipt formats and profiles.

## Set up a channel
After you complete the prerequisite tasks, follow the link to the channel type you want to create for set up instructions.
[Set up a Retail channel](tbd.md)
[Set up a Call Center channel)(tbd.md)
[Set up an Online channel)(tbd.md)

## After you set up a channel
After you create a channel, complete these tasks:

* Configure the POS registers for the store.
* Assign product assortments to the store.
* Process assortments to generate the list of products that are included in the assortment and to make the products available in the retail store.
* Send data such as number sequences, hardware profiles, and POS screen layouts to the Retail POS registers.
* Publish the retail store to send store data to Retail POS.
* Run the jobs to send the store data to Retail POS.








