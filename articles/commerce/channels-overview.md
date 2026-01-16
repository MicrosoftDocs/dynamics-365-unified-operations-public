---
title: Channels overview
description: This article provides an overview of channels in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 01/16/2026
ms.topic: overview
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2020-01-20
ms.custom: 
  - bap-template
---
# Channels overview

[!include [banner](includes/banner.md)]

This article provides an overview of channels in Microsoft Dynamics 365 Commerce. It includes information about the tasks that you must complete both before and after you set up each channel.

## Types of channels

Dynamics 365 Commerce supports three different channel types: retail, call center, and online channels.

### Retail channels

Retail channels represent standard brick-and-mortar stores. Each store can have its own point of sale (POS) registers, income and expense accounts, and staff. 

### Call center channels

Call center channels represent call center order and customer management.

### Online channels

Online channels represent online e-commerce storefronts. Once you create an online channel, you must create a site by using Dynamics 365 Commerce site builder, or another e-commerce solution.

## Channel setup basics

Set up channels in the Commerce tool. Each channel can have its own payment methods, price groups, product hierarchies, assortments, and set of products. After you create a channel, assign the products that you want it to carry and sell. Each channel type has a unique set of features that you might need to configure. For example, a retail channel needs assigned employees, registers, and customers. Once you create a new channel, assign it to an organization hierarchy.

## Channel setup prerequisites

Before you set up a channel, complete the prerequisite tasks for the channel type. For more information, see
[Channel setup prerequisites](channels-prerequisites.md).

## Set up a channel

After you complete the prerequisite tasks, use the following links for further setup instructions.

- [Set up a retail channel](channel-setup-retail.md)
- [Set up a call center channel](channel-setup-callcenter.md)
- [Set up an online channel](channel-setup-online.md)

## Additional resources

[Channel setup prerequisites](channels-prerequisites.md)

[Set up a retail channel](channel-setup-retail.md)

[Set up an online channel](channel-setup-online.md)

[Set up a call center channel](channel-setup-callcenter.md)

[Set up organization hierarchies](channels-org-hierarchies.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
