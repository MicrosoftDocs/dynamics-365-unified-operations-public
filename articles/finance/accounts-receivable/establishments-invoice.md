---
title: Establishment and Registration ID enforcement on invoices
description: Discover how to set up and validate Establishments and Registration IDs on customer and free text invoices.
author: twheeloc
ms.author: twheeloc
ms.reviewer: twheeloc
ms.date: 04/20/2026
ms.topic: concept-article
---

# Establishment behavior by invoice type

This article explains how Dynamics 365 Finance applies establishments and registration IDs to customer invoices and free text invoices. It covers defaulting behavior, validation rules, and relevant accounts receivable parameter considerations. These capabilities support regulatory compliance scenarios such as French electronic invoicing (e-invoicing).

## What is an establishment?

An establishment represents a specific operational unit of a legal entity that issues or receives invoices. In Dynamics 365 Finance, you model an establishment as an operating unit that's included in an organization hierarchy configured for enterprise establishments.

For more information, see [Establishments](../../fin-ops-core/fin-ops/organization-administration/organizations-organizational-hierarchies.md#establishments).

### What are registration IDs?

Registration IDs are legally required identifiers that represent a legal entity, establishment, customer, or vendor. Examples include VAT ID, SIREN, or SIRET.

For more information, see [Registration ids](../../fin-ops-core/dev-itpro/organization-administration/registration-ids.md).

### Invoice party applicability rules

Invoice party applicability rules validate registration IDs. These rules define:

- Which party role (legal entity, establishment, customer)
- Which address purpose (invoice, delivery, head office)
- Require a specific registration type

For more information, see [Invoice party applicability rules](../../fin-ops-core/dev-itpro/organization-administration/invoice-party-applicability-rules.md).

### Prerequisites

The behavior described in this article applies when you enable the **Establishment and Registration ID governance on invoices** feature.

#### Accounts receivable parameters

Two new parameters control how strictly the system enforces establishment and registration rules during customer invoice posting.

1. Go to **Accounts receivable** > **Setup** > **Accounts receivable parameters** > **Updates** > **Invoice**.
1. Select the **Require establishment on customer invoice** parameter to require an establishment on all customer invoices, including free text invoices.

You can't post an invoice unless the system determines an establishment or you select one manually.

1. Select the **Require registration IDs on customer invoice** parameter to require all mandatory registration IDs be available at posting.

- At posting, the system validates registration IDs based on:
  - Registration type validation rules
  - Party role (Legal entity, Establishment, Customer)
  - Address purpose (Invoice, Delivery, Head office)
  - Invoice date

If any required registration ID is missing or invalid, posting is blocked.

### Establishment defaults logic

The system defaults the establishment on customer invoices (including prepayment invoices) based on the following logic:

1. Site-based defaulting - on customer invoice posting from a sales order, the system leverages the existing invoice split functionality by site and delivery information. Go to **Accounts receivable** > **Setup** > **Accounts receivable parameters** > **Summary update** > **Split based on**. This functionality helps guarantee that the site linked to establishment representing the company’s establishment in the transaction and the delivery information representing the customer’s establishment in transaction are identified for the invoice.  

Based on this information, the system defines:

    - Establishment on the invoice header
    - Registration IDs of the company’s establishment: The **Registration IDs** field allows users to preview and validate all registration identifiers that the system uses during invoice posting.

1. Financial dimension–based defaulting - on customer invoice posting from General journal or Free text invoice. If a financial dimension value used on the invoice is linked to an establishment, the system automatically assigns the linked establishment.

    - Validation rule: If multiple financial dimensions point to different establishments, posting fails with a validation error.

1. Manual – when none of the financial dimension values used on the invoice posting are associated with an establishment or site, users can manually select the establishment on:

- Free text invoice
- General journals - when customer account is used to post customer invoice

> [!NOTE]
If you don't assign an **Establishment** to an invoice, the system treats this scenario as only one establishment represented by legal entity itself. In this case, the **Establishment** field isn't filled in and no registration IDs are defined and stored for establishment source.

1. **Registration IDs** set up as mandatory are effective on the invoice date for the address purposes of the address set as default for “Head company” purpose or primary address if there is no address marked with “Head company” purpose of given legal entity must be stored for the customer invoice header.

1. Mandatory **Registration IDs** of the **Establishment** stored for the customer invoice must be stored for the customer invoice header based on the **Validation rules** settings effective on the invoice date. If the **Establishment** wasn't assigned to invoice, this is treated as an only one establishment represented by legal entity itself scenario. In this case, it is expected that all the registration IDs including the one identifying the establishment of the main company is also specified on the legal entity.

1. Customer's **Registration IDs** that are set up as mandatory are effective on the invoice date in the **Validation rules** settings. The invoice date must be stored for the customer invoice header for the following customer’s addresses:

- Customers establishment – delivery: Delivery address from the given invoice, where the delivery address is the existing field on the invoice header, which is filled in using the Invoice address purpose.

- Customer head company: Customer’s (invoice account) address set as default for a Head company purpose or primary address if there's no address marked with a Head company purpose.

When establishment id governance is enabled:

- Customer invoices and free text invoices always represent one issuing establishment.
- Required registration IDs are validated and stored.
- Accounts receivable parameters decide the defaulting behaviour.
