---
title: Channel setup prerequisites
description: This article presents an overview of channels setup prerequisites in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 02/21/2020
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: samjar
ms.search.validFrom: 2020-01-20
ms.dyn365.ops.version: Release 10.0.8
ms.custom: 
ms.assetid: 
---
# Channel setup prerequisites

[!include [banner](includes/banner.md)]

This article presents an overview of channel setup prerequisites in Microsoft Dynamics 365 Commerce.

Before a Dynamics 365 Commerce channel can be created, several prerequisite tasks must be completed. The following lists of prerequisite tasks are organized by channel type.

> [!NOTE]
> Some documentation is still being written, and links will be updated as new content is published.

## Initialization

- [Initialize seed data](enable-configure-retail-functionality.md)

## Global prerequisites required for all channel types

- [Define and configure your legal entity structure](channels-legal-entities.md) 
- [Configure your organizational hierarchy](channels-org-hierarchies.md)
- [Set up a warehouse](channels-setup-warehouse.md)
- [Configure sales tax](../finance/general-ledger/indirect-taxes-overview.md?toc=/dynamics365/commerce/toc.json)
- [Set up an email notification profile](email-notification-profiles.md)
- [Set up number sequences](../fin-ops-core/fin-ops/organization-administration/number-sequence-overview.md?toc=/dynamics365/commerce/toc.json)
- [Set up a default customer and address book](default-customer.md)
<!--
- [Configure commerce parameters](commerce-parameters.md)
-->

## Retail channel prerequisites

- [Info codes and info code groups](info-codes-retail.md)
- [Set up a retail functionality profile](retail-functionality-profile.md)
- [Set up an employee address book](new-address-book.md)
- [Set up a screen layout](pos-screen-layouts.md)
- [Set up a hardware station](retail-hardware-station-configuration-installation.md)

## Call Center channel prerequisites

- Call center parameters
- [Call center order and refund payment methods](work-with-payments.md)
- [Call center modes of delivery and charges](configure-call-center-delivery.md)

## Online channel prerequisites

- [Create an online functionality profile](online-functionality-profile.md)

## Additional resources

[Channels overview](channels-overview.md)

[Organizations and organizational hierarchies overview](../fin-ops-core/fin-ops/organization-administration/organizations-organizational-hierarchies.md?toc=/dynamics365/commerce/toc.json)

[Set up organization hierarchies](channels-org-hierarchies.md)

[Create legal entities](channels-legal-entities.md)

[Set up a retail channel](channel-setup-retail.md)
	
[Set up an online channel](channel-setup-online.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
