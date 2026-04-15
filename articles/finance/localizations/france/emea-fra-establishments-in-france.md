--- 
title: Use establishments in France
description: Learn how to configure Establishments in France for legal entities, customers, vendors. 
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.date: 04/13/2026
ms.custom:
ms.reviewer: johnmichalak 
audience: Application User
ms.search.region: France
ms.search.validFrom: 2026-06-30
ms.search.form: CustTable, VendTable, OMLegalEntity
ms.dyn365.ops.version: Version 7.0.0 
---

# Use establishments in France

In France, invoices must identify the specific establishment involved in the transaction, in addition to the legal entity of the supplier or customer.
An establishment represents a physical or operational location where business activity is carried out and is assigned its own official identifier (SIRET).

Each establishment may issue or receive invoices and must therefore be identifiable during invoice processing.

As of 10.0.48 version, in Dynamics 365 Finance, [Establishments](.../../../fin-ops-core/fin-ops/organization-administration/organizations-organizational-hierarchies.md#establishments) are used during invoice posting to determine and validate the applicable [Registration IDs](../../../fin-ops-core/dev-itpro/organization-administration/registration-ids.md) for each invoice party:

- legal entity establishments
- customer establishments
- vendor establishments.

## Legal entity establishments

Legal entities may operate through multiple [Establishments](../../../fin-ops-core/fin-ops/organization-administration/organizations-organizational-hierarchies.md#establishments), each of which has its own:

- address
- SIRET Registration ID.

For example:

- Head office
- Regional consulting office
- Operations back‑office site.

Each establishment is included in the [**Enterprise establishment structure organization hierarchy**](../../../fin-ops-core/fin-ops/organization-administration/tasks/create-organization-hierarchy.md), which is used during invoice processing to resolve the issuing establishment of the invoice.

When a customer or vendor invoice is created:

- the establishment may be derived from Site or financial dimension involved in transaction
- the applicable establishment‑level [**Registration IDs**](../../../fin-ops-core/dev-itpro/organization-administration/registration-ids.md)
are determined by using [**Invoice party applicability rules**](../../../fin-ops-core/dev-itpro/organization-administration/invoice-party-applicability-rules.md)

Invoice posting cannot proceed if required Registration IDs for the legal entity's establishment are required and missing.

## Customer establishments

Customer establishments in customer invoice and project invoice are represented by **delivery addresses** in the invoice.

In France, a customer may operate multiple establishments, each of which:

- has a distinct delivery location
- is assigned its own SIRET Registration ID

Each establishment of the customer must be set up as an address of that customer and assigned with **Delivery** and **Invoice** address purposes. For each of the customer establishment address, 
configure the establishment‑level **SIRET** Registration IDs.

When a customer invoice or project invoice is created:

- the delivery address on the invoice represents the receiving customer establishment
- **Invoice party applicability rules** evaluate this address when determining the applicable Registration IDs for the Customer establishment party role.

This allows the system to validate and store **Registration IDs** for the correct receiving establishment, rather than only for the customer head office.

## Vendor establishments

Vendor establishments are represented by the [**ship‑from address**](../../finance/accounts-payable/vendor-ship-from-address.md) captured on the vendor invoice.
When the **Require ship from on vendor invoice** paramter is enabled for a vendor in transaction:

- the ship‑from address identifies the vendor establishment that issued the goods or services
- the address may be used as the Vendor invoice party during evaluation of **Invoice party applicability rules**

Vendor accounts may therefore be configured with:

- Head company Registration IDs at the primary address
- establishment‑level **SIRET** identifiers at **Invoice** addresses representing vendor establishments

During invoice posting:

- the ship‑from address is evaluated against **Invoice party applicability rules**
- the system determines which vendor establishment‑level **Registration IDs** must be present

Invoice posting is blocked if required **Registration IDs** for the vendor establishment identified by the ship‑from address are required and missing.

## Establishments in invoice processing

When an invoice is created:

- the issuing or receiving establishment is determined based on:
  - Site or financial dimension - for legal entity's establishment
  - delivery address - for customer's establishment
  - ship‑from address - for vendor's establishment

The applicable **Registration IDs** are resolved based on:

- the invoice party role
- the establishment address
- invoice party applicability rules

After posting, all applicable legal entity‑level and establishment‑level **Registration IDs** are immutably stored on the invoice for audit and reporting purposes. 

This configuration ensures that invoices issued or received in France are associated with the correct establishments of each party and include the **Registration IDs** required for regulatory reporting.
