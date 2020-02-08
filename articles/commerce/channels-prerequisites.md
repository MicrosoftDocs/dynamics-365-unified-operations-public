---
# required metadata

title: Channel setup prerequisites
description: This topic presents an overview of channels setup prerequisites in Microsoft Dynamics 365 Commerce.
author: samjarawan
manager: annbe
ms.date: 01/27/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2020-01-20
ms.dyn365.ops.version: Release 10.0.8

---
# Channel setup prerequisites


[!include [banner](includes/banner.md)]

This topic presents an overview of channel setup prerequisites in Microsoft Dynamics 365 Commerce.

## Overview

Before a Dynamics 365 Commerce channel can be created, several prerequisite tasks must be completed. The following lists of prerequisite tasks are organized by channel type.

> [!NOTE]
> Some documentation is still being written, and links will be updated as new content is published.

## Initialization

- [Initialize seed data](../retail/enable-configure-retail-functionality.md)

## Global prerequisities required for all channel types

- [Define and configure your legal entity structure](channels-legal-entities.md) 
- [Configure your organizational hierarchy](channels-org-hierarchies.md)
- [Set up a warehouse](channels-setup-warehouse.md)
- [Configure sales tax](https://docs.microsoft.com/en-us/dynamics365/finance/general-ledger/indirect-taxes-overview?toc=/dynamics365/commerce/toc.json)
- [Set up an email notification profile](email-notification-profiles.md)
- [Set up number sequences](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/organization-administration/number-sequence-overview?toc=/dynamics365/commerce/toc.json)
- [Set up a default customer and address book](default-customer.md)
<!--
- [Configure commerce parameters](commerce-parameters.md)
-->

## Retail channel prerequisites

- [Info codes and info code groups](https://docs.microsoft.com/en-us/dynamics365/retail/info-codes-retail?toc=/dynamics365/commerce/toc.json)
- [Set up a retail functionality profile](retail-functionality-profile.md)
- [Set up an employee address book](new-address-book.md)
- [Set up a screen layout](https://docs.microsoft.com/en-us/dynamics365/retail/pos-screen-layouts?toc=/dynamics365/commerce/toc.json)
- [Set up a hardware station](https://docs.microsoft.com/en-us/dynamics365/retail/retail-hardware-station-configuration-installation?toc=/dynamics365/commerce/toc.json)

## Call Center channel prerequisites

- Call center parameters
- Call center refund methods
- Rental types
- Payment services
- Order hold codes

## Online channel prerequisites

- [Create an online functionality profile](online-functionality-profile.md)

## Additional resources

[Channels overview](channels-overview.md)

[Organizations and organizational hierarchies overview](../fin-ops-core/fin-ops/organization-administration/organizations-organizational-hierarchies.md?toc=/dynamics365/commerce/toc.json)

[Set up organization hierarchies](channels-org-hierarchies.md)

[Create legal entities](channels-legal-entities.md)

[Set up a retail channel](channel-setup-retail.md)
	
[Set up an online channel](channel-setup-online.md)
