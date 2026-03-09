---
title: Registration categories' invoice party applicability rules
description: Registration categories' invoice party applicability rules alloew to determine which registration IDs apply to each invoice party role based on country/region requirements.
author: liza-golub
ms.author: egolub
ms.topic: overview
ms.date: 08/03/2026
ms.reviewer: johnmichalak
ms.collection: get-started
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2026-02-28
ms.search.form: DirPartyTable, DirPartyTableRoles
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 
---

# Invoice party applicability rules for registration categories

**Invoice party applicability rules** extend the **Registration ID** framework in Dynamics 365 Finance by defining which registration IDs are required and applicable for each party involved in an invoice, based on the party’s role, address purpose, and country/region requirements.

This functionality is available starting with Dynamics 365 Finance version **10.0.48** and is enabled through the **Establishment and Registration ID governance on invoices** feature in **Feature management**. When enabled, registration categories can be configured with applicability rules that drive validation, selection, and immutable storage of registration IDs on posted invoices.

In many invoicing scenarios, multiple parties can participate in a single transaction. For example, issuing and receiving legal entities, establishments, customers, and vendors. 
Regulatory requirements often differ depending on:

- the *invoice party role* (issuer or receiver),
- the *organizational level* (legal entity or establishment),
- the *address purpose* used on the invoice (such as invoice, or head office).

**Invoice party applicability rules** provide a deterministic and consistent mechanism to define:

- which registration categories apply to each invoice party role,
- when a registration ID is mandatory for an invoice,
- how registration IDs are resolved, validated and immutably stored during invoice posting.

This ensures that invoices consistently include the correct registration IDs for compliance, reporting, auditing, and electronic invoicing scenarios.

Invoice party applicability rules are part of the **Establishment and Registration ID governance on invoices** feature. When this feature is enabled:

- **Registration categories** support invoice‑specific applicability rules.
- **Registration IDs** that are mandatory for a given invoice party role are validated stored at posting time.
- Applicable registration IDs are *immutably stored* on posted invoices and used consistently across downstream processes.

These rules apply across all invoice creation paths, including customer invoices, vendor invoices and project invoices.

## How invoice party applicability rules work

**Invoice party applicability rules** are configured at the registration category level and evaluated during invoice processing.

Each rule defines:

- the *invoice party role* (Legal entity, Establishment, Customer, or Vendor),
- the *address purpose* that determines where the registration ID is resolved from (Head company, Invoice, Primary).

During invoice posting, the system evaluates these rules to determine:

- which **Registration IDs** must be present,
- which **Registration IDs** apply to the specific invoice context,
- invoice posting cannot proceed if required **Registration IDs** are missing.

**Invoice party applicability rules** work together with module‑specific invoice parameters in **Accounts payable**, **Accounts receivable**, and **Project management and accounting**.

| Parameter name | Parameter location in Finance | Description | 
|----------------|-----------------|-------------|
| **Require establishment on vendor invoice** checkbox | **Accounts payable** > **Setup** > **Accounts payable parameters** > **Invoice** tab > **Invoice** FastTab | When enabled, the system enforces establishment requirements on vendor invoice header or lines: <br>• Enables the **Establishment** field on vendor invoice documents. <br> • Applies defaulting logic to automatically populate the **Establishment** where possible, based on **Site** setup or **Financial dimensions** on the document. <br>• Validates that an **Establishment** is specified before posting and prevents posting if the field is empty. <br> **Note**: The **Establishment** value cannot be changed after the invoice is posted. |
| **Require establishment on customer invoice** checkbox |  **Accounts receivable** > **Setup** > **Accounts receivable parameters** > **Updates** tab > **Invoice** FastTab | When enabled, the system enforces establishment requirements on the customer invoice header. <br>• Enables the **Establishment** field on customer invoice documents. <br> • Applies defaulting logic to automatically populate the **Establishment** where possible, based on **Site** setup or **Financial dimensions** on the document. <br>• Validates that an **Establishment** is specified before posting and prevents posting if the field is empty. <br> **Note**: The **Establishment** value cannot be changed after the invoice is posted. |
| **Require establishment on project invoice** checkbox | **Project management and accounting** > **Setup** > **Project management and accounting parameters** > **Invoice** tab | When enabled, the system enforces establishment requirements on the project invoice header. <br>• Enables the **Establishment** field on project invoice documents. <br> • Applies defaulting logic to automatically populate the **Establishment** where possible, based on **Financial dimensions** on the document. <br>• Validates that an **Establishment** is specified before posting and prevents posting if the field is empty. <br> **Note**: The **Establishment** value cannot be changed after the invoice is posted. |

These parameters control whether an **Establishment** is required on invoices and determine when establishment‑level **Registration IDs** must be enforced during invoice posting.
When establishment enforcement is enabled, the system validates that an applicable establishment is specified on the invoice and uses the defined applicability rules to resolve the corresponding **Registration IDs**. 
This ensures consistent identification of invoice parties at both legal entity and establishment levels and guarantees that the correct registration information is validated and immutably stored on posted invoices.

For more information about **Establishments** and how they are defined, see [Establishments](organizations-organizational-hierarchies.md#establishments).

## Invoice party applicability rules and Vendor ship‑from address

For vendor invoices, **Invoice party applicability rules** can also work together with the [**Vendor ship‑from address support on invoices** feature](../../../finance/accounts-payable/vendor-ship‑from-address.md).
When this feature is enabled, the ship‑from address identifies the vendor establishment that issued the goods or services. 
This establishment can be used as an invoice party when evaluating invoice party applicability rules for registration categories.

In this scenario:

- The vendor establishment is derived from the ship‑from address captured on the vendor invoice.
- Invoice party applicability rules that reference the Vendor party role and specific address purposes (such as **Invoice**) are evaluated against the ship‑from address.
- Based on these rules, the system determines which vendor establishment‑level **Registration IDs** must be present for the invoice.
- Invoice posting cannot proceed if required **Registration IDs** that apply to the vendor establishment identified by the ship‑from address are missing.

This integration ensures that vendor invoices are validated against the correct vendor establishment, rather than only the vendor head office, and that the applicable **Registration IDs** are accurately resolved and immutably stored on posted invoices.

For more information about how the ship‑from address is captured and validated on vendor invoices, see [**Vendor ship‑from address support on invoices**](../../../finance/accounts-payable/vendor-ship‑from-address.md).

## Example 1: VAT ID applicability on invoices

This example illustrates how invoice party applicability rules work using the **VAT ID** registration category.

### Scenario

A company issues customer invoices in multiple countries and must ensure that VAT registration numbers are consistently applied and validated on invoices.

### Configuration

A *VAT ID* **Registration type** is created and assigned to the *VAT ID* **Registration category**.

**Require establishment on customer invoice** checkbox is enabled in **Accounts receivable parameters**.

Invoice party applicability rules are defined for the VAT ID category, for example:

- Invoice party role: Legal entity
- Address purpose: Head company or Primary
- Invoice party role: Customer
- Address purpose: Invoice

Before posting an invoice, users can preview the registration IDs that the system has determined by selecting the **Registration IDs** button on the source document page.

### Result

When an invoice is posted:

- The system determines the applicable **Registration IDs** for both the issuing legal entity and the customer based on their roles and addresse purpose configured in **Invoice party applicability rules**.
- Configuration of **Invoice party applicability rules** for *VAT ID* requires a registration IDs to be specified for legal entity (Invoice issuer legal entity) and customer (Invoice receiver legal entity).
- If **Registration ID** of *VAT ID* **Registration category** is not setup for legal entity or customer involved in invoice transaction, invoice posting is blocked.
- If **Registration ID** of *VAT ID* **Registration category** are setup for legal entity or customer involved in invoice transaction, these **Registration IDs** are immutably stored for the posted invoice.

The resolved VAT registration IDs are stored on the posted invoice and used for reporting, compliance, and electronic invoicing. For posted invoices, the **Registration IDs** button in customer invoice journal allows users to review the registration IDs that were determined and stored at the time of posting.

## Example 2: Branch ID applicability on invoices

This example illustrates how invoice party applicability rules work using the **Branch ID** registration category.

### Scenario

A company that has mulptiple branches receives a vendor invoices from a vendor's branch and must ensure that **Branch ID** registration numbers are consistently applied and validated on invoice for both invoice issuer and invoice receiver.

### Configuration

A *Branch ID* **Registration type** is created and assigned to the *Branch ID* **Registration category**.

**Require establishment on vendor invoice** checkbox is enabled in **Accounts payable parameters**.

**Require ship from on vendor invoice** checkbox is enabled for the vendor master record in transaction.

Invoice party applicability rules are defined for the Branch ID category, for example:

- Invoice party role: Establishment
- Address purpose: Invoice
- Invoice party role: Vendor
- Address purpose: Invoice

Before posting an invoice, users can preview the registration IDs that the system has determined by selecting the **Registration IDs** button on the source document page.

### Result

When an invoice is posted:

- The system determines the applicable **Registration IDs** for both the issuing and the receiving parties based on their roles and addresse purpose configured in **Invoice party applicability rules**.
- Configuration of **Invoice party applicability rules** for *Branch ID* requires a registration IDs to be specified for Establishment (Invoice receiver establishment) and Vendor (Invoice issuer establishment).
- If **Registration ID** of *Branch ID* **Registration category** is not setup for establishment or vendor involved in invoice transaction, invoice posting is blocked.
- If **Registration ID** of *Branch ID* **Registration category** are setup for establishment or vendor involved in invoice transaction, these **Registration IDs** are immutably stored for the posted invoice.

The resolved VAT registration IDs are stored on the posted invoice and used for reporting, compliance, and electronic invoicing. For posted invoices, the **Registration IDs** button in vendor invoice journal allows users to review the registration IDs that were determined and stored at the time of posting.

