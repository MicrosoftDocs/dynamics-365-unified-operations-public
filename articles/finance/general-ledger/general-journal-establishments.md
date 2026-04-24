---
title: Establishments and registration IDs in general journal
description: This article provides information on how Establishments and registration IDs are used in General journals.
author: JodiChristiansen
ms.date: 4/24/2026
ms.topic: article
audience: Application User
ms.reviewer: twheeloc
ms.search.scope: Core, Operations
ms.custom: 539093
ms.search.region: Global
ms.author: jchrist
ms.search.validFrom: 2021-11-05
ms.dyn365.ops.version: 10.0.24
---

# Establishments and registration IDs in General journals

Starting in Dynamics 365 Finance version 10.0.48, you can enable the **Establishment and Registration ID governance on invoices** feature in Feature management to control how establishments and registration IDs are applied to invoices across finance workflows.

This feature introduces validation rules that determine:

- Whether an **Establishment** must be specified on an invoice
- Which **Registration IDs** are required for each invoice party
- When invoice posting is blocked because required regulatory identifiers are missing
- How registration IDs are resolved and immutably stored at posting time

These validations apply consistently across all invoice entry points, including invoices that originate from General journals.

## What is an establishment?

In Finance, an **Establishment** represents an operational unit of a legal entity that performs business activities on a stable basis and might require its own regulatory identifiers for invoicing or reporting.  

A single legal entity can have one or more establishments. Although these establishments share the same legal identity, they can maintain separate operational identities for invoicing and compliance purposes.

Establishments are modeled by:

- Using existing Operating units
- Including those operating units in an organizational hierarchy that is assigned the **Enterprise establishment structure** purpose

Only operating units that are explicitly included in this hierarchy are treated as valid establishments by the system.

For more information, see Establishments.

## General ledger invoice scenarios

Use general journals in the General ledger to create invoices for customers in Accounts receivable and vendors in Accounts payable. When you enable the establishment governance feature, invoices created from General ledger journals must meet the same establishment and registration ID requirements as invoices that originate from other modules. This requirement includes any journals that you created but didn't post. After you enable the feature, review all open journals for the Registration IDs and Establishments. If you set them up to default to new journals, they automatically populate when you post the existing journals.

Module-specific invoice parameters determine whether:

- You must specify an **Establishment** on the invoice
- The system validates establishment-level registration IDs during posting

For example, when you enable the **Require establishment on customer invoice** parameter or **Require establishment on vendor invoice** parameter:

- The **Establishment** field becomes available on the General journal, Invoice tab
- The system attempts to default the establishment from financial dimensions
- Posting is prevented if you don't specify an establishment
- You can't change the establishment value after the invoice is posted

During posting, the system uses invoice party applicability rules to validate that required registration IDs exist for the legal entity, establishment, customer, or vendor invoiced on the transaction. These rules resolve the correct identifiers based on party role and address purpose and store those identifiers on the posted invoice for audit and compliance purposes.

### Example

Set up three operating units by using the business unit as the operating unit type.

- 252 Head office
- 253 Regional consulting office
- 254 Operational back office

Use the business unit as a financial dimension in the account structure for the ledger. Add the three operating units to the Enterprise establishment structure in Organization hierarchies.

:::image type="content" source="media/establishments-organization-structure.png" alt-text="Screenshot of establishments organizational hierarchy.":::

To default the Establishment from a customer or vendor to the general journals, set the business unit in the Financial dimension fastTab on the customer or vendor to one of the three operating units setup; 252, 253, or 254. Alternatively, a financial dimension can also be added when entering the general journal.

The preceding example shows one way to set up Establishments by using an operating unit tied to a financial dimension called business unit. You can use any dimension for this purpose if it's an operating unit type.

## Registration IDs on invoices

Many countries or regions require registration numbers - such as VAT IDs, company registration numbers, or branch identifiers - to appear on invoices. Starting in Finance version 10.0.48, Finance provides a unified framework for managing these identifiers across legal entities, customers, vendors, and establishments.

If you don't configure required registration IDs for an applicable invoice party, the system blocks invoice posting until you provide the required information.

After posting, the system stores applicable registration IDs immutably on the invoice and uses them for compliance, reporting, and downstream processing.

When you set **Require registration IDs on customer invoices** to **Yes** in Accounts receivable parameters > Updates tab > Invoice fastTab, any customer invoices posted from General journals require the Registration IDs.

When you set **Require registration IDS on vendor invoice** to **Yes** in Accounts payable parameters > Invoice tab, any vendor invoices posted from General journals require the Registration IDs.

For more information, see Configure Registration IDs.
