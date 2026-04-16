---
title: Use establishments on Sales Order Lines
description: Learn how to configure, default, and validate establishments on sales order lines to meet invoice compliance requirements.
author: Aditi Pattanaik
ms.author: adpattanaik
ms.reviewer: kamaybac
ms.search.form: PurchCreateFromSalesOrder, SalesTable
ms.topic: how-to
ms.date: 04/16/2026
ms.custom: 
  - bap-template
---

# Use establishments on sales order lines

[!include [banner](../includes/banner.md)]

This article provides information about how to configure, default, and validate establishments on sales order lines to meet invoice compliance requirements. 

## Overview

The **Establishments** feature adds an establishment field at the sales order line level to support legal and fiscal compliance requirements (notably for France) while remaining globally applicable. An establishment represents an operating unit within a legal entity that buys or sells goods, and is tied to tax registration identifiers, such as SIRET or SIREN.

To enable establishments on sales order lines, turn on the parameter highlighted in the following table.

| Parameter name | Parameter location in Finance | Description | 
|----------------|-----------------|-------------|
| **Require establishment on customer invoice** checkbox |  **Accounts receivable** > **Setup** > **Accounts receivable parameters** > **Updates** tab > **Invoice** FastTab | When enabled, the system enforces establishment requirements on the customer invoice header. <br>• Enables the **Establishment** field on customer invoice documents. <br> • Applies defaulting logic to automatically populate the **Establishment** where possible, based on **Site** setup or **Financial dimensions** on the document. <br>• Validates that an **Establishment** is specified before posting and prevents posting if the field is empty. <br> > [!NOTE] You can't change the **Establishment** value after the invoice is posted. |

This parameter controls whether an **Establishment** is required on invoices and determines when establishment‑level **Registration IDs** must be enforced during invoice posting.
When you enable establishment enforcement, the system validates that an applicable establishment is specified on the invoice and uses the defined applicability rules to resolve the corresponding **Registration IDs**. 
This validation ensures consistent identification of invoice parties at both legal entity and establishment levels and guarantees that the correct registration information is validated and immutably stored on posted invoices.

For more information about **Establishments** and how they're defined, see [Establishments](organizations-organizational-hierarchies.md#establishments).

To learn more about Registration IDs, see [Registration ID](articles/fin-ops-core/dev-itpro/organization-administration/registration-ids.md).


## Why establishments matter

Invoices must include the correct establishment and related tax registration identifiers for audit and compliance. During invoice posting, the system enforces that each invoice contains one and only one establishment unless invoices are split by site. Once posted, the system stores establishment and registration IDs immutably on the invoice for compliance and audit purposes.

## Where are establishments stored?

- Sales order lines contain the establishment field, which provides line-level granularity.
- Establishments aren't intended to appear on sales order header list pages because these pages are header-centric views, while establishments are line-driven.

## How Establishments Are Determined?

On a sales order line, the establishment can be derived using the following logic:

1. Site-based derivation (primary)
1. Financial dimensions (fallback or complementary)
1. Manual override by the user (allowed if defaulting fails or adjustment is needed)

If the site or relevant dimensions change, the system recalculates the establishment to stay consistent with the new context.

## Defaulting Behavior

## Defaulting behavior
- The system defaults the establishment during sales line insert and update operations.

- For legacy or previously created unposted documents, use the **Backfill Establishments** batch job to populate establishment values instead of relying on form-load logic, to avoid performance problems.

Before an invoice can be posted:

- All sales order lines must have an establishment.
- All lines on a single invoice must share the same establishment.
- If sales order lines span multiple sites (and therefore multiple establishments), invoice posting fails unless you enable the **Split invoice by site** parameter.

Clear validation and error messages guide users toward corrective actions, such as running the backfill job or adjusting parameters.

## Error handling and user guidance

You can correct error messages related to establishments by:

- Running the **Backfill Establishment on sales order lines** batch job.
- Enabling **Split invoice by site when multiple establishments are involved**.
- Manually aligning establishments on all relevant sales order lines.

## Backfill establishments batch job 

Use a dedicated batch job to populate establishment values on open sales order lines within a specified date range. 
Key characteristics of this backfill batch job include: 
- Set-based processing for performance.
- Security roles control (for example, Trade Sales Manager).
- Designed to address gaps in historical or legacy data.


## User interface considerations

- You see establishment at the sales order line level, and you can add it as a column where needed.
- To avoid performance and aggregation complexity, the establishment doesn't appear at the invoice header.
- Line-level visibility ensures clarity while avoiding costly recalculations.

## Key takeaways

- Establishments are a line-level compliance construct, not a header attribute.
- Defaulting is automatic but overridable, with strong validations at invoice posting time.
- Batch backfill and actionable error messages ensure operational continuity and compliance.


