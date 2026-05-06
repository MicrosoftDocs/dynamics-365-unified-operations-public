--- 
title: Registration IDs set up for France
description: Learn how to create and enter Registration IDs setup for France for legal entities, customers, vendors. 
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.date: 05/04/2026
ms.custom:
ms.reviewer: johnmichalak 
audience: Application User
ms.search.region: France
ms.search.validFrom: 2026-06-30
ms.search.form: CustTable, VendTable, OMLegalEntity
ms.dyn365.ops.version: Version 7.0.0 
---

# Registration numbers set up for France

In France, invoices must identify both the issuing or receiving legal entities and their establishments involved in the transaction.
To support this requirement, Dynamics 365 Finance uses [Registration IDs](../../../fin-ops-core/dev-itpro/organization-administration/registration-ids.md) 
together with [Invoice party applicability rules](../../../fin-ops-core/dev-itpro/organization-administration/invoice-party-applicability-rules.md) 
to determine which identifiers to validate and store when posting an invoice.

This section explains how to configure **Registration IDs** for France.

## Supported registration types for France

Create and use the following **Registration types** configured for the **FRA** country/region:

| Registration type | Description | Restricted to | Unique |
|---|---|---|---|
| SIREN | Official identifier of a French legal entity | Organization | Yes |
| SIRET | Official identifier of a French establishment | Organization | No |
| VAT ID | Official tax identification number for VAT purposes| Organization | Yes |

Each registration type is configured with:

- Country/region: FRA
- Can be updated: No

The **SIRET** registration type is configured as nonunique to allow the legal entity head office and the corresponding head-office establishment to share the same identifier where applicable.

## Registration categories

Assign each **Registration type** to a **Registration category** for validation and reporting.

For France, use the following **Registration categories**:

| Registration type | Registration category |
|---|---|
| VAT ID | VAT ID |
| SIRET | SIRET |
| SIREN  | Enterprise ID (COID) |

Define **Invoice party applicability rules** for these categories to determine:

- Which invoice party roles must provide a Registration ID.
- Which address purposes are evaluated during invoice posting.

### Example 1

For example, a VAT ID-type registration number is required for legal entity, customers, and vendors with primary address in France:

:::image type="content" source="../media/emea-fra-vat-id-setup.png" alt-text="Screenshot of an example VAT ID setup for France.":::

### Example 2

If customers or vendors have their primary address outside France but are also registered for VAT in France, you can extend the French VAT ID registration settings by assigning the **Head company** purpose in the **Customer** and **Vendor** registration setup:

:::image type="content" source="../media/emea-fra-vat-id-setup-head-company.png" alt-text="Screenshot of an example VAT ID setup for France for head company.":::

When you enable these settings, during invoice posting runtime the system first attempts to retrieve a French VAT ID–type registration ID from the customer or vendor address that belongs to the French country/region provided the delivery or ship-from address defined for the invoice is in France, and is assigned as the **Head company** purpose.

If the system doesn't find such a registration ID, it falls back to the primary address, provided it's also in French country/region as the delivery or ship-from address of the invoice, and retrieves the French VAT ID from there.

### Example 3

The **SIREN** is the official identifier of a legal entity in France. You must specify it on invoices as part of the business identification details of the parties, in accordance with French invoicing requirements.

:::image type="content" source="../media/emea-fra-vat-id-setup-siren-fr.png" alt-text="Screenshot of an example SIREN setup for France for head company.":::

### Example 4

The **SIRET** is the unique identifier of an establishment in France, composed of the company’s SIREN and an extra code that distinguishes each location.

:::image type="content" source="../media/emea-fra-vat-id-setup-siret-fr.png" alt-text="Screenshot of an example SIRET setup for France for head company.":::

### Example 5

If your legal entity has establishments outside France and you enable the [Multiple VAT registration numbers](../global/emea-multiple-vat-registration-numbers.md) feature, configure addresses in those countries or regions with the required VAT ID–type registration IDs.

In this case:

- Assign the **Head company** purpose to these addresses.
- Add the **Head company** purpose to the VAT ID registration category for the relevant countries in the Legal entity settings.
- Create [Establishments](../../../fin-ops-core/fin-ops/organization-administration/organizations-organizational-hierarchies.md#establishments) for each country where your company is registered for VAT.
- Configure a primary address in the corresponding country or region for each estbishment. This address doesn't require a VAT ID–type registration ID.

For example, if your French legal entity has VAT ID registration in Germany:

:::image type="content" source="../media/emea-fra-vat-id-setup-multi-tax-legal-entity.png" alt-text="Screenshot of an example VAT ID setup for France - multiple tax registration IDs.":::

With this setup, when you select an establishment in Germany on the invoice, the system retrieves the German VAT ID from the legal entity address in Germany that you assigned the **Head company** purpose to, during invoice posting runtime. 

### Example 6

When your legal entity has its primary address outside France (for example, in Germany) and also has one or many establishments in France, complete more setup to ensure correct identification in French invoices:

- Assign the **Head company** purpose to the legal entity address in France that represents the head office.
- For this address, configure the required registration IDs, including **SIREN**, **SIRET**, and **VAT ID**.

In addition:

- Create as many [establishments](../../../fin-ops-core/fin-ops/organization-administration/organizations-organizational-hierarchies.md#establishments) in France as there are registered SIRET numbers for your company.
- For each establishment, define a primary address in France and assign the corresponding SIRET registration ID.

Configure the **Registration categories** for France as follows.

**SIREN** registration type for France.

:::image type="content" source="../media/emea-fra-vat-id-setup-siren.png" alt-text="Screenshot of an example SIREN setup for France.":::

**VAT ID** registration type for France.

:::image type="content" source="../media/emea-fra-vat-id-setup-vat-id.png" alt-text="Screenshot of an example VAT ID setup for France with primary address outside France.":::

> [!NOTE]
> For correct VAT reporting in multiple tax registration scenarios, enable the [Multiple VAT registration numbers](../global/emea-multiple-vat-registration-numbers.md) feature.

**SIRET** registration type for France.

:::image type="content" source="../media/emea-fra-vat-id-setup-siret.png" alt-text="Screenshot of an example SIRET setup for France.":::

At the same time, configure the **VAT ID** registration settings for Germany based on the legal entity’s **primary address** in Germany for correct invoicing from Germany:

- Ensure that the German VAT ID–type registration ID is configured for this address.
- Configure the **VAT ID** registration category for Germany to include the **primary address** in Legal entity settings.

:::image type="content" source="../media/emea-fra-vat-id-setup-deu-vat-id.png" alt-text="Screenshot of an example VAT ID setup for Germany.":::

## Legal entity registration IDs

Set up registration IDs of the **VAT ID**, **SIREN**, and **SIRET** types, and assign them to the legal entity’s address with the **Head company** purpose or to the **primary address**.

:::image type="content" source="../media/emea-fra-vat-id-setup-le-reg-ids.png" alt-text="Screenshot of an example Registration IDs set up for French legal entity.":::

> [!NOTE]
> Registration IDs are date-sensitive. Ensure that you specify the **Effective** date on the **General** tab of the **Registration IDs** FastTab.

## Establishment registration IDs

Each [Establishment](../../../fin-ops-core/fin-ops/organization-administration/organizations-organizational-hierarchies.md#establishments) represents a physical or operational unit of a legal entity in France.

If your legal entity has only one establishment in France, disable the following parameters:

| Parameter name | Parameter location in Finance | Description |
|----------------|-----------------|-------------|
| **Require establishment on vendor invoice** checkbox | **Accounts payable** > **Setup** > **Accounts payable parameters** > **Invoice** tab > **Invoice** FastTab | When enabled, the system enforces establishment requirements on vendor invoice header or lines: <br>• Enables the **Establishment** field on vendor invoice documents. <br> • Applies defaulting logic to automatically populate the **Establishment** where possible, based on **Site** setup or **Financial dimensions** on the document. <br>• Validates that an **Establishment** is specified before posting and prevents posting if the field is empty. <br> > **NOTE**: You can't change the **Establishment** value after the invoice is posted. |
| **Require establishment on customer invoice** checkbox |  **Accounts receivable** > **Setup** > **Accounts receivable parameters** > **Updates** tab > **Invoice** FastTab | When enabled, the system enforces establishment requirements on the customer invoice header. <br>• Enables the **Establishment** field on customer invoice documents. <br> • Applies defaulting logic to automatically populate the **Establishment** where possible, based on **Site** setup or **Financial dimensions** on the document. <br>• Validates that an **Establishment** is specified before posting and prevents posting if the field is empty. <br> > **NOTE**: You can't change the **Establishment** value after the invoice is posted. |
| **Require establishment on project invoice** checkbox | **Project management and accounting** > **Setup** > **Project management and accounting parameters** > **Invoice** tab | When enabled, the system enforces establishment requirements on the project invoice header. <br>• Enables the **Establishment** field on project invoice documents. <br> • Applies defaulting logic to automatically populate the **Establishment** where possible, based on **Financial dimensions** on the document. <br>• Validates that an **Establishment** is specified before posting and prevents posting if the field is empty. <br> > **NOTE**: You can't change the **Establishment** value after the invoice is posted. |

If your legal entity has multiple establishments in France, enable these parameters accordingly in module parameters. Set up a registration ID of the **SIRET** type for each of the establishments, and assign it to the establishment's address with the **Invoice** purpose or to the **primary address** of that establishment.

:::image type="content" source="../media/emea-fra-vat-id-setup-establishment-reg-id.png" alt-text="Screenshot of an example Registration IDs setup for French establishment.":::

> [!NOTE]
> Registration IDs are date-sensitive. Ensure that you specify the **Effective** date on the **General** tab of the **Registration IDs** FastTab.

## Customer and vendor registration IDs

Customers and vendors can also have establishment-level registration IDs assigned to their addresses.

Set up registration IDs of the **VAT ID**, **SIREN**, and **SIRET** types and assign them to the customers' and vendors' addresses with the **Head company** purpose or to the **primary address**.

:::image type="content" source="../media/emea-fra-vat-id-setup-cust-head-com-reg-ids.png" alt-text="Screenshot of an example Registration IDs setup for French customer head company.":::

Set up a registration ID of the **SIRET** type and assign it to the customers' and vendors' addresses with the **Invoice** purpose. If a customer or vendor has multiple establishments, set up a registration ID of the **SIRET** type for each address of that customer or vendor that represents an establishment and assign **Invoice** and **Delivery** purposes to those addresses.

:::image type="content" source="../media/emea-fra-vat-id-setup-cust-invoice-reg-id.png" alt-text="Screenshot of an example Registration IDs setup for French customer delivery establishment.":::

> [!NOTE]
> Registration IDs are date-sensitive. Ensure that you specify the **Effective** date on the **General** tab of the **Registration IDs** FastTab.

In France, a counterparty can operate under the legal status of entrepreneur individual (for example, as a micro-entrepreneur), where a natural person conducts business activities in their own name and is assigned official business identifiers such as SIREN, SIRET, or VAT ID.
You must configure such counterparties as the **Organization** party type in Dynamics 365 Finance to allow establishment-level registration IDs to be assigned and validated during invoice posting.

## Validation and storage of registration IDs on invoice posting

When you use [Invoice party applicability rules](../../../fin-ops-core/dev-itpro/organization-administration/invoice-party-applicability-rules.md):

- The system resolves the applicable registration IDs for each invoice.
- The invoice posting process controls that required registration IDs are defined for each invoice.
- The system immutably stores all applicable registration IDs on the invoice for audit and reporting purposes after posting.
