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

## Capabilities

When the feature is enabled, selective changes become visible in the Microsoft Dynamics 365 Supply Chain Management user interface.

> [!NOTE]
> These changes only come to live when the feature is configured with an external contract lifecycle management (CLM) solution

Navigate to **Procurement and Sourcing** \> **Setup**\> **CLM integration**. This section includes the two forms: Contract types and Contract management parameters.

Contract types represent the types of external contracts, which depending upon the type of integration, are either integrated seamlessly with or accessible from the Microsoft Dynamics 365 Supply Chain Management user interface. The types created here should be mapped against the external contract types against which to integrate.

Contract management parameters represent the configuration of the connection parameters for the external contract management system.

CLM integration covers tasks typically performed by a system administrator or system integrator.

Navigate to **Procurement and Sourcing** \> **Contracts**. This section includes the one form: All contracts. The All contracts form allows users such as purchasing agents and purchasing managers to see selective data for contracts integrated with the external CLM. In the case where the external contract is integrated to a Microsoft Dynamics 365 Supply Chain Management purchase agreement, this will be visible from this form.

The form is intended to represent the central repository for any user, purchasing agent, purchase manager, sourcing manager and the like working in the Microsoft Dynamics 365 Supply Chain Management user interface to gain a quick overview of which external contracts exist with a given supplier party, the current status, while allowing to view selective detailed contractual information and perform selective contractual tasks depending on the configuration with the external contract lifecycle management (CLM) solution.

All contracts can be accessed for all suppliers, or for a specific supplier context. For the latter, navigate to **Procurement and Sourcing** \> **Vendors** \> **All vendors**. In the header ribbon for tab Procurement, Group Agreements, click menu button *Contracts*. This will open the All contracts within the specific vendor context, only including contracts for the particular vendor selected.

> [!NOTE]
> Multi-select vendor and access contracts aren't supported.

## Purchase agreements with external CLM integration

When the feature is enabled and configured to integrate with purchase agreements, then selective changes are applied to the purchase agreement. Contract ID and Contract status columns are added to the *Purchase agreements* list page, allowing the user to easily identify if the purchase agreement exists within the context of an external contract.

The most important change is *Purchase agreement ownership type*. Purchase agreement ownership type is visible in the purchase agreements details form, on the header section on the **Contract** FastTab. A purchase agreement can only reference one external contract.

In the scenario where the purchase agreement is created directly in Microsoft Dynamics 365 Supply Chain Management, the ownership type is *Supply Chain Management*.

In the scenario, where the purchase agreement is created from a contract in an external CLM, the ownership type will be *External contract management*. When ownership type is *External contract management*, then the **Contract ID** and **Status** from the external CLM will be visible in the **Contract** FastTab. This will available the user working with the purchase agreement in the Microsoft Dynamics 365 Supply Chain Management UI to without additional navigation quickly identify external contract ID and the status.

## Importance of ownership type

Ownership type controls which data can be modified and added on the purchase agreement through the Microsoft Dynamics 365 Supply Chain Management user interface and the kind of purchase agreement processing supported in Microsoft Dynamics 365 Supply Chain Management.

When ownership type is different from Supply Chain Management, the purchase agreement is controlled by another party and process and edit possibilities are very limited in the Microsoft Dynamics 365 Supply Chain Management UI. All edits and lifecycle changes are controlled and done within the external CLM owning the contract. Once executed in the external CLM, these changes update the purchase agreement in Microsoft Dynamics 365 Supply Chain Management accordingly.

## Field ownership

When a purchase agreement is owned by an external CLM, the following header actions are not supported:

- Intercompany: Generate sales agreement
- Intercompany: View sales agreement
- Maintain: Activities
- Generate: Confirmation and proforma confirmation
- Generate: Proforma confirmation
- Delete purchase agreement

When a purchase agreement is owned by an external CLM, only the following header updates are supported within the Microsoft Dynamics 365 Supply Chain Management UI:

- Vendor reference
- External document reference
- Line matching policy
- Delivery address
- Payment specification
- Charges group
- Mode of delivery
- Buyer group
- Pool
- Shipping carrier
- Carrier service
- Carrier group
- Mode
- Route plan
- Transportation template ID
- All financial dimensions

Other header fields have values set through the integration from the external CLM and are not editable from within the Microsoft Dynamics 365 Supply Chain Management UI.

If an approval workflow is configured then such a workflow configuration will not be applied when ownership is *External contract management*. The purchase agreement status will be updated from on hold to effective from the integration bypassing any workflow configuration. Reason for this is, that the contract has been approved by all relevant parties, signed and executed in the external CLM resulting in updating the status of the purchase agreement from on hold to effective. Any additional approval workflow applied in Microsoft Dynamics 365 Supply Chain Management would be disruptive to the approval process already conducted in the external CLM.

When a purchase agreement is owned by an external CLM, only the following line updates are supported within the Microsoft Dynamics 365 Supply Chain Management UI:

- All financial dimensions

Known limitations:

- Intercompany purchase and sales agreement are not supported.
- Purchase agreement approval workflow is not supported.
