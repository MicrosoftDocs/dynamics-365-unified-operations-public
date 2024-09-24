---
title: Channels overview
description: This article presents an overview of channels in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 05/29/2024
ms.topic: overview
audience: Application User
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2020-01-20
ms.custom: 
  - bap-template
---
# Channels overview


[!include [banner](includes/banner.md)]

This article presents an overview of channels in Microsoft Dynamics 365 Commerce. It includes information about the tasks that you must complete both before and after you set up each channel.

## Types of Channels

Dynamics 365 Commerce supports three different channel types: retail, call center, and online channels.

### Retail channels

Retail channels represent standard brick-and-mortar stores. Each store can have its own point of sale (POS) registers, income and expense accounts, and staff. 

### Call center channels

Call center channels represent call center order and customer management.

### Online channels

Online channels represent online e-Commerce storefronts. Once an online channel is created, a site must be created using the Microsoft Dynamics 365 Commerce Site Builder tool or other third-party e-Commerce solution.

## Channel setup basics

Channel set up is performed in the Commerce tool. Each channel can have its own payment methods, price groups, product hierarchies, assortments, and set of products. After you create a channel, you assign the products that you want it to carry and sell. Each channel type has a unique set of features that may need to be configured. For example, a retail channel needs assigned employees, registers, and customers. Once a new channel is created, it needs to be assigned to an organization hierarchy.

## Channel setup prerequisites

Before you can set up a channel, you must complete some prerequisite tasks based on the channel type. For more information, see
[Channel setup prerequisites](channels-prerequisites.md).

## Set up a channel

After you complete the prerequisite tasks, for further setup instructions, use the following links.

- [Set up a retail channel](channel-setup-retail.md)
- [Set up a call center channel](channel-setup-callcenter.md)
- [Set up an online channel](channel-setup-online.md)

<!--
## Post-channel configuration

After you create a channel, you may need to complete some of the below tasks:

- [Add channel to an organizational hierarchy](add-channel-org-hierarchy.md)
- Set up fulfillment groups. (LINK TBD)
- Configure the POS registers for the store. (LINK TBD)
- Assign product assortments to the store. (LINK TBD)
- Process assortments to generate the list of products that are included in the assortment and to make the products available in the retail store. (LINK TBD)
- Send data such as number sequences, hardware profiles, and POS screen layouts to the Retail POS registers.(LINK TBD)
- Publish the retail store to send store data to Retail POS. (LINK TBD)
- Run the jobs to send the store data to Retail POS. (LINK TBD)
-->

## Additional resources

[Channel setup prerequisites](channels-prerequisites.md)

[Set up a retail channel](channel-setup-retail.md)
	
[Set up an online channel](channel-setup-online.md)

[Set up a call center channel](channel-setup-callcenter.md)

[Set up organization hierarchies](channels-org-hierarchies.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
