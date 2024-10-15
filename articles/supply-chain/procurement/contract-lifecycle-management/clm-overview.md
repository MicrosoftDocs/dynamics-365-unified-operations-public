---
title: Contract lifecycle management integration overview (preview)
description: Contract lifecycle management integration overview.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 10/25/2024
ms.custom: 
  - bap-template
---

# Contract lifecycle management integration overview (preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until 10.0.43 GA  -->

*Contract lifecycle management* (CLM) is an important aspect of the source to pay process. Effective Contract lifecycle management helps organizations to manage their contracts with suppliers in a more efficient and effective manner. CLM can help streamline the contract creation, negotiation, execution, and renewal processes, reducing the time and resources required to manage contracts. This can help to ensure that contracts are in compliance with organizational policies and regulations, reducing the risk of penalties or other negative consequences. CLM can also help to improve visibility into contract performance, enabling organizations to make more informed decisions about their supplier relationships. By integrating CLM into the source to pay process, organizations can improve their overall supply chain performance and deliver greater value to their customers.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

In Dynamics 365 Supply Chain Management, the focus has been on the operationalization of contracts. This is exampled by purchase agreements, rebate agreements, brokerage agreements, and regular purchase orders.

However with feature *Integrate with external contract lifecycle management systems*, Dynamics 365 Supply Chain Management offers the ability to integrate to external contract lifecycle management systems over a common integration framework in Procurement and Sourcing.

This will enable organizations to easier integrate to their preferred external CLM in support of common CLM processes of contract creation, authoring, red lining, negotiating, signing, amending, and termination.

## Integration to external contract lifecycle management

This feature allows you to integrate Microsoft Dynamics 365 Supply Chain Management with an external contract lifecycle management (CLM) system. The feature enables a set of capabilities in Microsoft Dynamics 365 Supply Chain Management to allow for an external contract lifecycle management (CLM) system to integrate. Note that by itself the feature is not a CLM solution. To take advantage of the integration capabilities with this feature, an external contract lifecycle management (CLM) solution, leveraging the integration capabilities, is required.

## Contract types

When feature *Integration to external contract lifecycle management* is enabled and configured with an external contract lifecycle management (CLM) solution, the following two contract flows can be integrated:

- Purchase agreements
- Non-disclosure agreements (NDAs)

The purchase agreement lifecycle can be managed seamlessly between the external contract lifecycle management (CLM) system and Microsoft Dynamics 365 Supply Chain Management.

The NDA lifecycle is managed in the external contract lifecycle management (CLM) system however accessible from within Microsoft Dynamics 365 Supply Chain Management.

The feature is extensible to allow for additional contract flows and types to be integrated if required by an organization.

Contract types Purchase agreement and NDA, represent two very different kinds of integration. While type Purchase agreement is deeply integrated with the purchase agreement source document and process in Microsoft Dynamics 365 Supply Chain Management, type NDA represents a very light weight and loosely coupled integration, where the NDA in Microsoft Dynamics 365 Supply Chain Management only exists as a record in All contracts. The NDA represents a kind of supplier contract from an external CLM which does not directly impact any processes in Microsoft Dynamics 365 Supply Chain Management.

