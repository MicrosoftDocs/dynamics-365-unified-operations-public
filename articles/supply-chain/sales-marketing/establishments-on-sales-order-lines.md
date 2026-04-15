---
title: Establishments on Sales Order Lines
description: Learn how to configure, default, and validate establishments on sales order lines to meet invoice compliance requirements.
author: Aditi Pattanaik
ms.author: adpattanaik
ms.reviewer: kamaybac
ms.search.form: PurchCreateFromSalesOrder, SalesTable
ms.topic: how-to
ms.date: 04/13/2026
ms.custom: 
  - bap-template
---

# Establishments on Sales Order Lines

[!include [banner](../includes/banner.md)]

This article provides information about how to configure,default and validate establishments on sales order lines to meet invoice compliance requirements. 

## Overview

The Establishments feature introduces an establishment field at the sales order line level to support legal and fiscal compliance requirements (notably for France) while remaining globally applicable. An Establishment represents an operating unit within a legal entity that buys or sells goods, and is tied to tax registration identifiers (for example SIRET/SIREN).

To enable the establishments on sales order line, enable the parameter highlighted in the table below.

| Parameter name | Parameter location in Finance | Description | 
|----------------|-----------------|-------------|
| **Require establishment on customer invoice** checkbox |  **Accounts receivable** > **Setup** > **Accounts receivable parameters** > **Updates** tab > **Invoice** FastTab | When enabled, the system enforces establishment requirements on the customer invoice header. <br>• Enables the **Establishment** field on customer invoice documents. <br> • Applies defaulting logic to automatically populate the **Establishment** where possible, based on **Site** setup or **Financial dimensions** on the document. <br>• Validates that an **Establishment** is specified before posting and prevents posting if the field is empty. <br> **Note**: The **Establishment** value cannot be changed after the invoice is posted. |

This parameter control whether an **Establishment** is required on invoices and determine when establishment‑level **Registration IDs** must be enforced during invoice posting.
When establishment enforcement is enabled, the system validates that an applicable establishment is specified on the invoice and uses the defined applicability rules to resolve the corresponding **Registration IDs**. 
This ensures consistent identification of invoice parties at both legal entity and establishment levels and guarantees that the correct registration information is validated and immutably stored on posted invoices.

For more information about **Establishments** and how they are defined, see [Establishments](organizations-organizational-hierarchies.md#establishments).

To learn more about Registration IDs, see [ Registration ID ](articles/fin-ops-core/dev-itpro/organization-administration/registration-ids.md).


## Why Establishments Matter?

Invoices must include the correct establishment and related tax registration identifiers for audit and compliance. During invoice posting, the system enforces that each invoice contains one and only one establishment unless invoices are split by site. Once posted, establishment and registration IDs are stored immutably on the invoice for compliance and audit purposes.

## Where Establishments Are Stored?

- Sales order lines contain the establishment field (line-level granularity).
- Establishments are not intended to be shown at sales order header list pages because they are header-centric views, while establishments are line-driven.

## How Establishments Are Determined?

On a sales order line, the establishment can be derived using the following logic:

1. Site-based derivation (primary)
2. Financial dimensions (fallback or complementary)
3. Manual override by the user (allowed if defaulting fails or adjustment is needed)

If the site or relevant dimensions change, the establishment is recalculated to stay consistent with the new context.

## Defaulting Behavior

- Establishment defaulting occurs during sales line insert and update operations.
- For legacy or previously created unposted documents, establishment values can be populated using a Backfill Establishments batch job instead of relying on form-load logic, to avoid performance issues.

## Invoice Posting & Validation Rules

Before an invoice can be posted:

- All sales order lines must have an establishment.
- All lines on a single invoice must share the same establishment.
- If sales order lines span multiple sites (and therefore multiple establishments), invoice posting fails unless the Split invoice by site parameter is enabled.

Clear validation and error messages guide users toward corrective actions such as running the backfill job or adjusting parameters.

## Error Handling and User Guidance

Error messages related to establishments can be corrected by -

- Running the Backfill Establishment on sales order lines batch job.
- Enabling Split invoice by site when multiple establishments are involved.
- Manually aligning establishments on all relevant sales order lines.

## Backfill Establishments Batch Job 

A dedicated batch job allows administrators or sales managers to populate establishment values on open sales order lines within a specified date range. 
Key characteristics of this backfill batch job are - 
- Set-based processing for performance.
- Controlled by security roles (for example Trade Sales Manager).
- Designed to address gaps in historical or legacy data.


## User Interface Considerations

- Establishment is shown at the sales order line level and can be added as a column where needed.
- Displaying establishment at the invoice header was intentionally avoided due to performance and aggregation complexity.
- Line-level visibility ensures clarity while avoiding costly recalculations.

## Key Takeaways

- Establishments are a line-level compliance construct, not a header attribute.
- Defaulting is automatic but overridable, with strong validations at invoice posting time.
- Batch backfill and actionable error messages ensure operational continuity and compliance.


