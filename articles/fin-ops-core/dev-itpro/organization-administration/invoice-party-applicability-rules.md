---
title: Registration categories' invoice party applicability rules
description: Registration categories' invoice party applicability rules allow to determine which registration IDs apply to each invoice party role based on country/region requirements.
author: liza-golub
ms.author: egolub
ms.topic: overview
ms.date: 04/16/2026
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

**Invoice party applicability rules** extend the [**Registration ID**](registration-ids.md) framework in Dynamics 365 Finance by defining which registration IDs are required and applicable for each party involved in an invoice, based on the party’s role, address purpose, and country/region requirements.

This functionality is available starting with Dynamics 365 Finance version **10.0.48** and is enabled through the **Establishment and Registration ID governance on invoices** feature in **Feature management**. When enabled, [registration categories](registration-ids.md#supported-registration-categories) can be configured with applicability rules that drive validation, selection, and immutable storage of registration IDs on posted invoices.

In many invoicing scenarios, multiple parties can participate in a single transaction. For example, issuing and receiving legal entities, establishments, customers, and vendors. 
Regulatory requirements often differ depending on:

- the *invoice party role* (issuer or receiver),
- the *organizational level* (legal entity or establishment),
- the *address purpose* used on the invoice (such as invoice, or head office).

**Invoice party applicability rules** provide a deterministic and consistent mechanism to define:

- which registration categories apply to each invoice party role,
- when a registration ID is mandatory for an invoice,
- how registration IDs are resolved, validated, and immutably stored during invoice posting.

This mechanism ensures that invoices consistently include the correct registration IDs for compliance, reporting, auditing, and electronic invoicing scenarios.

## How invoice party applicability rules work

Invoice party applicability rules are part of the **Establishment and Registration ID governance on invoices** feature. When you enable this feature, you can set up **Registration categories** to support invoice‑specific applicability rules.

**Invoice party applicability rules** work together with module‑specific invoice parameters in **Accounts payable**, **Accounts receivable**, and **Project management and accounting**.

| Parameter name | Parameter location in Finance | Description | 
|----------------|-----------------|-------------|
| **Require Registration ID on vendor invoice** checkbox | **Accounts payable** > **Setup** > **Accounts payable parameters** > **Invoice** tab > **Invoice** FastTab | When enabled, the system enforces registration ID requirements on vendor invoices: Validates that all required Registration IDs are present before posting, ensures registration IDs are properly configured for all invoice party roles, prevents posting when mandatory registration IDs are missing. <br> > [!NOTE]
> The registration IDs are stored immutably after the invoice is posted. |
| **Require Registration ID on customer invoice** checkbox |  **Accounts receivable** > **Setup** > **Accounts receivable parameters** > **Updates** tab > **Invoice** FastTab | When enabled, the system enforces registration ID requirements on customer invoices: Validates that all required Registration IDs are present before posting, ensures registration IDs are properly configured for all invoice party roles, prevents posting when mandatory registration IDs are missing. <br> **Note**: The registration IDs are stored immutably after the invoice is posted. |
| **Require Registration ID on project invoice** checkbox | **Project management and accounting** > **Setup** > **Project management and accounting parameters** > **Invoice** tab | When enabled, the system enforces registration ID requirements on project invoices: Validates that all required Registration IDs are present before posting, ensures registration IDs are properly configured for all invoice party roles, prevents posting when mandatory registration IDs are missing. <br> **Note**: The registration IDs are stored immutably after the invoice is posted. |

These rules apply across all invoice creation paths, including customer invoices, vendor invoices, and project invoices.

You configure **invoice party applicability rules** at the registration category level. The system evaluates these rules during invoice processing.

Each rule defines:

- the *invoice party role* (Legal entity, Establishment, Customer, or Vendor),
- the *address purpose* that determines where the registration ID is resolved from (Head company, Invoice, Primary).

During invoice posting, the system evaluates these rules to determine:

- which **Registration IDs** must be present,
- which **Registration IDs** apply to the specific invoice context.
Invoice posting can't proceed if required **Registration IDs** are missing.

## Use of invoice party applicability rules in establishment‑level invoice governance

**Invoice party applicability rules** work together with [Establishments](../../fin-ops/organization-administration/organizations-organizational-hierarchies.md#establishments) when you enable the module‑specific invoice parameter in **Accounts payable**, **Accounts receivable**, and **Project management and accounting**.

| Parameter name | Parameter location in Finance | Description | 
|----------------|-----------------|-------------|
| **Require establishment on vendor invoice** checkbox | **Accounts payable** > **Setup** > **Accounts payable parameters** > **Invoice** tab > **Invoice** FastTab | When enabled, the system enforces establishment requirements on vendor invoice header or lines: <br>• Enables the **Establishment** field on vendor invoice documents. <br> • Applies defaulting logic to automatically populate the **Establishment** where possible, based on **Site** setup or **Financial dimensions** on the document. <br>• Validates that an **Establishment** is specified before posting and prevents posting if the field is empty. <br> > [!NOTE]
> The **Establishment** value can't be changed after the invoice is posted. |
| **Require establishment on customer invoice** checkbox |  **Accounts receivable** > **Setup** > **Accounts receivable parameters** > **Updates** tab > **Invoice** FastTab | When enabled, the system enforces establishment requirements on the customer invoice header. <br>• Enables the **Establishment** field on customer invoice documents. <br> • Applies defaulting logic to automatically populate the **Establishment** where possible, based on **Site** setup or **Financial dimensions** on the document. <br>• Validates that an **Establishment** is specified before posting and prevents posting if the field is empty. <br> **Note**: The **Establishment** value can't be changed after the invoice is posted. |
| **Require establishment on project invoice** checkbox | **Project management and accounting** > **Setup** > **Project management and accounting parameters** > **Invoice** tab | When enabled, the system enforces establishment requirements on the project invoice header. <br>• Enables the **Establishment** field on project invoice documents. <br> • Applies defaulting logic to automatically populate the **Establishment** where possible, based on **Financial dimensions** on the document. <br>• Validates that an **Establishment** is specified before posting and prevents posting if the field is empty. <br> **Note**: The **Establishment** value can't be changed after the invoice is posted. |

These parameters control whether an **Establishment** is required on invoices and determine when establishment‑level **Registration IDs** must be enforced during invoice posting.
When you enable establishment enforcement, the system validates that an applicable establishment is specified on the invoice and uses the defined applicability rules to resolve the corresponding **Registration IDs**. 

For more information about **Establishments** and how they're defined, see [Establishments](../../fin-ops/organization-administration/organizations-organizational-hierarchies.md#establishments).

## Invoice party applicability rules and vendor ship‑from address

For vendor invoices, **Invoice party applicability rules** can work together with the [**Vendor ship‑from address support on invoices** feature](../../../finance/accounts-payable/vendor-ship-from-address.md).
When you enable this feature, the ship‑from address identifies the vendor establishment that issued the goods or services. 
Use this establishment as an invoice party when evaluating invoice party applicability rules for registration categories.

In this scenario:

- You derive the vendor establishment from the ship‑from address captured on the vendor invoice.
- Evaluate invoice party applicability rules that reference the Vendor party role and specific address purposes (such as **Invoice**) against the ship‑from address.
- Based on these rules, the system determines which vendor establishment‑level **Registration IDs** must be present for the invoice.
- Invoice posting can't proceed if required **Registration IDs** that apply to the vendor establishment identified by the ship‑from address are missing.

This integration ensures that vendor invoices are validated against the correct vendor establishment, rather than only the vendor head office, and that the applicable **Registration IDs** are accurately resolved and immutably stored on posted invoices.

For more information about how the ship‑from address is captured and validated on vendor invoices, see [**Vendor ship‑from address support on invoices**](../../../finance/accounts-payable/vendor-ship-from-address.md).

## Invoice party applicability rules and customer delivery address

For customer and project invoices, **Invoice party applicability rules** can also evaluate the delivery address specified on the invoice.
The delivery address can represent the customer establishment that receives the goods or services and may therefore serve as an invoice party when evaluating invoice party applicability rules for registration categories.

In this scenario:

- The customer establishment comes from the delivery address captured on the invoice.
- Invoice party applicability rules that reference the Customer party role and specific address purposes (such as **Invoice**) are evaluated against the delivery address.
- Based on these rules, the system determines which customer establishment‑level **Registration IDs** must be present for the invoice.
- Invoice posting can't proceed if required **Registration IDs** that apply to the customer establishment identified by the delivery address are missing.

This behavior ensures that customer and project invoices are validated against the appropriate customer establishment associated with the delivery location, rather than only the customer head office, and that the applicable **Registration IDs** are accurately resolved and immutably stored on posted invoices.

## Availability of invoice party applicability rules

You can configure and evaluate **Invoice party applicability rules** for the following registration categories:

- VAT ID
- Enterprise ID (COID)
- Branch ID
- SIRET

**Invoice party applicability rules** aren't evaluated for other registration categories. For registration categories that aren't listed earlier, you can still store and maintain **Registration IDs** by using the Registration ID framework, but the system doesn't validate or enforce them through invoice party applicability rules during invoice processing.

## Example 1: Branch ID applicability on vendor invoice

This example shows how invoice party applicability rules work by using the **Branch ID** registration category.

### Scenario

A company with multiple branches receives vendor invoices from a vendor's branch. The company must ensure that **Branch ID** registration numbers are consistently applied and validated on the invoice for both the invoice issuer and the invoice receiver.

### Configuration

Create a *Branch ID* [**Registration type**](registration-ids.md#registration-type-creation) and assign it to the *Branch ID* [**Registration category**](registration-ids.md#assign-a-registration-category-to-a-registration-type).

Enable the **Require Registration IDs on vendor invoice** and **Require establishment on vendor invoice** parameters in **Accounts payable parameters**.

Enable the **Require ship from on vendor invoice** checkbox for the vendor master record in transaction.

Define invoice party applicability rules for the Branch ID category, for example:

| Invoice party role | Address purpose |
|-------|----------|
| Establishment | Invoice or Primary |
| Vendor | Invoice |

Set up **Registration IDs** for:

| Party role | Address purpose | Registration type |
|-------|----------|-------------|
| Establishment | Invoice or  Primary | Branch ID |
| Vendor | Invoice | Branch ID |

Before posting an invoice, users can preview the registration IDs that the system determines by selecting the **Registration IDs** button on the source document page.

### Result

When you post an invoice:

- The system determines the applicable **Registration IDs** for both the issuing and the receiving parties based on their roles and address purpose configured in **Invoice party applicability rules**.
- Configuring **Invoice party applicability rules** for *Branch ID* requires specifying registration IDs for Establishment (Invoice receiver establishment) and Vendor (Invoice issuer establishment).
- If you don't set up **Registration ID** of *Branch ID* **Registration category** for establishment or vendor involved in invoice transaction, invoice posting is blocked.
- If you set up **Registration ID** of *Branch ID* **Registration category** for establishment or vendor involved in invoice transaction, the system immutably stores these **Registration IDs** for the posted invoice.

The resolved VAT registration IDs are stored on the posted invoice and used for reporting and compliance. 

For posted invoices, the **Registration IDs** button in vendor invoice journal allows users to review the registration IDs that the system determined and stored at the time of posting.

## Example 2: VAT ID and Branch ID applicability on customer invoice

This example illustrates how invoice party applicability rules work using the **VAT ID** and **Branch ID** registration categories.

### Scenario

A company that has multiple branches issues customer invoices and must ensure that VAT registration numbers are consistently applied and validated on invoices and that **Branch ID** registration numbers are consistently applied and validated on invoice for both legal entity establishment and customer delivery establishment.

### Configuration

Create a *VAT ID* [**Registration type**](registration-ids.md#registration-type-creation) and assign it to the *VAT ID* [**Registration category**](registration-ids.md#assign-a-registration-category-to-a-registration-type).

Create a *Branch ID* [**Registration type**](registration-ids.md#registration-type-creation) and assign it to the *Branch ID* [**Registration category**](registration-ids.md#assign-a-registration-category-to-a-registration-type).

Enable the **Require Registration IDs on customer invoice** and **Require establishment on customer invoice** parameters in **Accounts receivable parameters**.

Define **Invoice party applicability rules** for the **VAT ID** category:

| Invoice party role | Address purpose |
|-------|----------|
| Legal entity | Head company or Primary |
| Customer | Head company or Primary |

Define **Invoice party applicability rules** for the **Branch ID** category:

| Invoice party role | Address purpose |
|-------|----------|
| Establishment | Invoice or Primary |
| Customer | Invoice |

Set up **Registration IDs** for:

| Party role | Address purpose | Registration type |
|-------|----------|-------------|
| Legal entity | Head company or Primary | VAT ID |
| Establishment | Invoice or  Primary | Branch ID |
| Customer | Head company or Primary | VAT ID |
| Customer | Invoice | Branch ID |

Before posting an invoice, users can preview the registration IDs that the system determines by selecting the **Registration IDs** button on the source document page.

### Result

When you post an invoice:

- The system determines the applicable **Registration IDs** of VAT ID category for both the issuing legal entity and the customer based on their roles and addresse purpose configured in **Invoice party applicability rules**:
  - Legal entity: VAT ID
  - Establishment: Branch ID
  - Customer head company: VAT ID
  - Customer establishment: Branch ID 
- Configuration of **Invoice party applicability rules** for *VAT ID* and *Branch ID* require registration IDs to be specified for legal entity, establishment, customer, and delivery address.
- If you don't set up **Registration ID** of *VAT ID* or *Branch ID* **Registration category** for legal entity, establishment, or customer involved in invoice transaction, invoice posting is blocked.
- If you set up **Registration ID** of *VAT ID* and *Branch ID* **Registration category** for legal entity, establishment, or customer involved in invoice transaction, the system immutably stores these **Registration IDs** for the posted invoice.

The resolved VAT and branch registration IDs are stored on the posted invoice and used for reporting, compliance, and electronic invoicing. 

For posted invoices, the **Registration IDs** button in customer invoice journal allows users to review the registration IDs that the system determined and stored at the time of posting.
