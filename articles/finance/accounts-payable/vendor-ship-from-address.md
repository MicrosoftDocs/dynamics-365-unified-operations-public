---
title: Vendor ship‑from address support on invoices
description: Learn about specifying and storing a vendor ship‑from address on vendor invoices in Dynamics 365 Finance.
author: liza-golub
ms.author: egolub
ms.topic: overview
ms.date: 03/03/2026
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

Starting in Dynamics 365 Finance version 10.0.48, the **Vendor ship‑from address support on invoices** feature introduces support for specifying and storing a vendor ship‑from address on vendor invoices.
The ship‑from address represents the vendor establishment involved in the transaction and is used during invoice processing and posting. 
The address can be captured on vendor invoices created from purchase orders and invoice journals and is immutably stored on the posted invoice.
This capability enables correct identification of the vendor establishment, supports validation and immutable storage of mandatory **Registration IDs**, and ensures compliance, auditability, 
and accurate regulatory reporting for vendor invoices when this feature is used together with the [**Establishment and Registration ID governance on invoices** feature](../../fin-ops-core/dev-itpro/organization-administration/invoice-party-applicability-rules.md).

## What is the vendor ship‑from address?

The ship‑from address identifies the vendor location (establishment) from which goods or services are supplied. 
Unlike the vendor’s head office address, the ship‑from address reflects the actual issuing establishment and can vary per transaction.
This information is required in scenarios where vendors operate through multiple establishments and regulatory or audit requirements mandate identification of the issuing location.

## Key capabilities

When **Vendor ship‑from address support on invoices** feature is enabled, the system provides the following capabilities:

- Allows users to specify a ship‑from address on vendor invoices.
- Supports defaulting of the ship‑from address from the purchase order or other document context, where applicable.
- Enables validation of the ship‑from address during invoice posting when required by vendor setup.
- Immutably stores the ship‑from address on the posted invoice to preserve historical accuracy.
- Supports correct resolution and storage of vendor establishment‑level **Registration IDs** when used together with establishment and registration ID governance features.

## Vendor configuration

When **Vendor ship‑from address support on invoices** feature is enabled, a new vendor‑level parameter becomes available on the vendor master record: **Require ship from on vendor invoice**.

When this parameter is enabled for a vendor:

- The vendor invoice requires a ship‑from address to be specified before posting.
- System prevents vendor invoice posting if the ship‑from address is missing.
- After posting, the ship‑from address cannot be changed.

This allows enforcement to be applied selectively based on vendor and regulatory requirements.

## Invoice processing behavior

With vendor ship‑from address support enabled:

- The **Ship‑from address** can be automatically populated from a vendor address that is marked with the **Invoice** address purpose.
- The **Ship‑from address** can be automatically populated from the purchase order when invoices are created from purchase orders.
- The **Ship‑from address** can be manually selected on vendor invoices when applicable.
- During posting, the system validates the presence of the **Ship‑from address** if the vendor requires it.
- The **Ship‑from address** is stored immutably on the posted invoice for audit and traceability purposes.

## Relationship to establishments and Registration IDs

The vendor ship‑from address represents the vendor establishment involved in the transaction. When used together with 
[**Establishment and Registration ID governance on invoices** feature](../../fin-ops-core/dev-itpro/organization-administration/invoice-party-applicability-rules.md), this feature enables:

- Identification of the correct vendor establishment.
- Resolution and immutable storage of establishment‑level Registration IDs for vendor invoices.
- Consistent and compliant handling of vendor invoice data across posting, inquiry, and reporting scenarios.
