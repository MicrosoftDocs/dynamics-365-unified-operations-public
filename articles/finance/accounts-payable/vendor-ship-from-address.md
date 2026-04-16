---
title: Vendor ship‑from address support on invoices
description: Learn about specifying and storing a vendor ship‑from address on vendor invoices in Dynamics 365 Finance.
author: liza-golub
ms.author: egolub
ms.topic: overview
ms.date: 04/24/2026
ms.reviewer: twheeloc
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2026-02-28
ms.search.form: VendorInvoiceWorkspace, VendInvoiceInfoListPage
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 
---

# Vendor ship‑from address support on invoices

Starting in Dynamics 365 Finance version 10.0.48, the **Vendor ship‑from address support on invoices** feature introduces support for specifying and storing a vendor ship‑from address on vendor invoices. The ship‑from address represents the vendor establishment involved in the transaction and is used during invoice processing and posting.

You can capture the address on vendor invoices created from purchase orders and invoice journals. The system immutably stores the address on the posted invoice.

This capability enables correct identification of the vendor establishment, supports validation and immutable storage of mandatory **Registration IDs**, and ensures compliance, auditability, and accurate regulatory reporting for vendor invoices when you use this feature together with the [**Establishment and Registration ID governance on invoices** feature](../../fin-ops-core/dev-itpro/organization-administration/invoice-party-applicability-rules.md).

## What is the vendor ship‑from address?

The ship‑from address identifies the vendor location (establishment) from which goods or services are supplied. Unlike the vendor’s head office address, the ship‑from address reflects the actual issuing establishment and can vary per transaction. You need this information in scenarios where vendors operate through multiple establishments and regulatory or audit requirements mandate identification of the issuing location.

## Key capabilities

When you enable the **Vendor ship‑from address support on invoices** feature, the system provides the following capabilities:

- Allows you to specify a ship‑from address on vendor invoices.
- Supports defaulting of the ship‑from address from the purchase order or other document context, where applicable.
- Enables validation of the ship‑from address during invoice posting when required by vendor setup.
- Immutably stores the ship‑from address on the posted invoice to preserve historical accuracy.
- Supports correct resolution and storage of vendor establishment‑level **Registration IDs** when used together with establishment and registration ID governance features.

## Vendor configuration

When you enable the **Vendor ship-from address support on invoices** feature, you see a new vendor-level parameter on the vendor master record: **Require ship from on vendor invoice**.

When you enable this parameter for a vendor:

- You must specify a ship-from address on the vendor invoice before posting.
- The system prevents vendor invoice posting if the ship-from address is missing.
- After posting, you can't change the ship-from address.

You can enforce these requirements selectively based on vendor and regulatory requirements.

## Invoice processing behavior

When you enable vendor ship-from address support:

- The system automatically populates the **Ship-from address** from a vendor address that you mark with the **Invoice** address purpose.
- The system automatically populates the **Ship-from address** from the purchase order when you create invoices from purchase orders.
- You can manually select the **Ship-from address** on vendor invoices when applicable.
- During posting, the system validates the presence of the **Ship-from address** if the vendor requires it.
- The system stores the **Ship-from address** immutably on the posted invoice for audit and traceability purposes.

## Relationship to establishments and Registration IDs

The vendor ship‑from address represents the vendor establishment involved in the transaction. When you use the [**Establishment and Registration ID governance on invoices** feature](../../fin-ops-core/dev-itpro/organization-administration/invoice-party-applicability-rules.md) together with this feature, you can:

- Identify the correct vendor establishment.
- Resolve and store establishment‑level Registration IDs for vendor invoices in an immutable way.
- Handle vendor invoice data consistently and compliantly across posting, inquiry, and reporting scenarios.
