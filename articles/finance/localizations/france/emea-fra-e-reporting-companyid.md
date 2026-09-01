--- 
title: Seller and buyer identification (CompanyId) in French e-reporting
description: Learn how the Seller and Buyer company identifier (CompanyId) and its scheme identifier are determined and reported in the French e-reporting (electronic reporting of transactions) feature in Microsoft Dynamics 365 Finance. 
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.date: 08/12/2026
ms.custom:
  - bap-template
ms.reviewer: johnmichalak 
ms.search.region: France
ms.search.validFrom: 2026-06-30
ms.search.form: CustTable, VendTable, OMLegalEntity
ms.dyn365.ops.version: Version 7.0.0 
---

# Seller and buyer identification (CompanyId) in French e-reporting

[!INCLUDE [banner](../../includes/banner.md)]

This article describes how the French e-reporting (electronic reporting of transactions) feature determines and reports the party identifier, `CompanyId`, and its scheme identifier, `schemeId`, for the **Seller** and **Buyer** nodes of a transaction. Use this information to understand which value is reported for each party, why a specific scheme code is used, and where the reported value comes from in Dynamics 365 Finance.

The `CompanyId` element identifies each party of a transaction as a legal entity. It is different from the party's VAT registration number, which is reported separately in the `TaxRegistrationId` element. Both elements can be present for the same party, and each is derived independently.

## Where the seller and buyer appear in the report

For the `TransactionsReportType` report type, each `Invoice` node (the business-to-business, or B2B, part of the report) contains a `Seller` node and a `Buyer` node. Each node can carry a `CompanyId` element that identifies the party.

The structure of the two nodes, as defined by the transaction schema, is the following.

| Node     | Element                       | Occurrence | Semantic ID | Reported at                                            |
|----------|-------------------------------|------------|-------------|--------------------------------------------------------|
| `Seller` | `CompanyId`                   | Mandatory  | TT-33       | `.../Invoice/Seller/CompanyId`                          |
| `Seller` | `CompanyId/@schemeId`         | Mandatory  | TT-33-1     | `.../Invoice/Seller/CompanyId/@schemeId`               |
| `Seller` | `TaxRegistrationId`           | Optional   | TT-34       | `.../Invoice/Seller/TaxRegistrationId`                  |
| `Seller` | `TaxRegistrationId/@qualifyingId` | Mandatory when the element is present | TT-34-0 | `.../Invoice/Seller/TaxRegistrationId/@qualifyingId` |
| `Buyer`  | `CompanyId`                   | Optional   | TT-36       | `.../Invoice/Buyer/CompanyId`                           |
| `Buyer`  | `CompanyId/@schemeId`         | Mandatory when the element is present | TT-37 | `.../Invoice/Buyer/CompanyId/@schemeId`                |
| `Buyer`  | `TaxRegistrationId`           | Optional   | TT-38       | `.../Invoice/Buyer/TaxRegistrationId`                   |
| `Buyer`  | `TaxRegistrationId/@qualifyingId` | Mandatory when the element is present | TT-38-0 | `.../Invoice/Buyer/TaxRegistrationId/@qualifyingId` |

## Which party is the seller and which is the buyer

The **Seller** and the **Buyer** are functional roles that you assign per transaction, based on the direction of the underlying invoice. The reporting legal entity can be either the seller or the buyer of a given transaction.

### Customer invoice (sale)

When the reported transaction is a **customer invoice** (or a customer prepayment invoice, project invoice, or project advance invoice), the reporting legal entity is the party that issues the invoice. Therefore:

- The `Seller` node identifies the **reporting legal entity**.
- The `Buyer` node identifies the **customer** (the counterparty).
- The report issuer `RoleCode` (semantic ID TT-15) is `SE` (the declarant is the seller).

### Vendor invoice (purchase with reverse charge)

When the reported transaction is a **vendor invoice** that carries a self-assessed tax (**use tax**, or reverse-charge **sales tax payable**), the reporting legal entity is the party that receives the invoice. Therefore, the nodes are reversed compared to a customer invoice:

- The `Seller` node identifies the **vendor** (the counterparty).
- The `Buyer` node identifies the **reporting legal entity**.
- The report issuer `RoleCode` (semantic ID TT-15) is `BY` (the declarant is the buyer).

## How the CompanyId value and scheme are determined

For each party, the feature reports two related values:

- The `schemeId` attribute, which declares the type of identifier that is reported. It uses the ISO 6523 ICD code list.
- The `CompanyId` value itself, which is the identifier that corresponds to the declared scheme.

### Step 1 – Select the scheme identifier

The following table lists the scheme identifiers that are allowed for the `Seller/CompanyId` and `Buyer/CompanyId` elements, the party situation that each scheme represents, and the expected format of the identifier. The values and formats come from the ISO 6523 (ICD) code list, as adopted by the French tax administration.

| `schemeId` | Scheme          | Party situation                                                                                 | Identifier format                                                                                       |
|------------|-----------------|-------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------|
| `0002`     | SIREN           | The party is established, and registered, in mainland France.                                    | 9 numeric characters.                                                                                   |
| `0223`     | UE_HORS_FRANCE  | The party is established in the European Union, outside France.                                  | The intra-community VAT identifier. Up to 18 characters.                                                |
| `0227`     | HORS_UE         | The party is established outside the European Union (including Wallis and Futuna).               | The country code followed by the first 16 characters of the legal name. Up to 18 characters.            |
| `0228`     | RIDET           | The party is established in New Caledonia.                                                        | 9 or 10 characters.                                                                                     |
| `0229`     | TAHITI          | The party is established in French Polynesia.                                                     | 9 characters.                                                                                           |

The scheme comes from the registration identifiers that you configure for the party:

- For the **reporting legal entity**, use the scheme that reflects the legal entity's own registration: `0002` for a French company that uses its SIREN.
- For the **counterparty** (customer or vendor), use one of the schemes `0223` (UE_HORS_FRANCE), `0227` (HORS_UE), or `0002` for a French vendor that uses its SIREN. Select the scheme from the **registration category** of the registration ID, as described in [Step 2 – Take the identifier value](#step-2--take-the-identifier-value).

### Step 2 – Take the identifier value

After you select the scheme, take the `CompanyId` value from the registration numbers stored for the invoice or party master data:

- For the **reporting legal entity**, take the SIREN registration number from the registration numbers that are stored for the invoice or configured for the legal entity.
- For the **counterparty**, take the identifier from the registration numbers that are stored for the invoice or configured for the customer or the vendor. The scheme identifier is determined by the **registration category** that you assign to that registration ID.

For a customer or a vendor, the feature covers the following registration categories and maps each one to a scheme identifier:

| Registration category of the customer/vendor registration ID | `schemeId` | Scheme          |
|--------------------------------------------------------------|------------|-----------------|
| EU VAT ID                                                    | `0223`     | UE_HORS_FRANCE  |
| Enterprise ID                                                | `0227`     | HORS_UE         |

To report a counterparty identifier, assign the appropriate registration category (**EU VAT ID** or **Enterprise ID**) to the registration ID of the customer or the vendor in the registration IDs setup. The registration ID that carries that category provides the `CompanyId` value, and the category selects the corresponding `schemeId`.

### Step 3 – Report the VAT registration identifier (TaxRegistrationId)

The `TaxRegistrationId` element carries the party's VAT registration number and is reported independently of the `CompanyId`:

- Always set the `@qualifyingId` attribute of `TaxRegistrationId` to the value `VAT`.
- For the seller, you need the VAT registration number when the invoice contains an exemption (a line with the tax category code `E`). In that situation, you must report either the seller's VAT number or the VAT number of the seller's tax representative.

## Examples

The following examples use a French reporting legal entity and a counterparty that is established in Germany. They show how the `Seller` and `Buyer` nodes swap between the two invoice directions.

### Customer invoice (sale to the German customer)

The reporting French legal entity issues a customer invoice, so it reports as the seller and the customer reports as the buyer.

- **Seller** node — the reporting French legal entity:
  - `CompanyId` = the company's SIREN, `schemeId` = `0002`.
  - `TaxRegistrationId` = the company's French VAT number, `@qualifyingId` = `VAT`.
- **Buyer** node — the German customer (counterparty):
  - `CompanyId` = the customer's EU VAT ID **Registration category**, `schemeId` = `0223` (because the registration category is **EU VAT ID**).
  - `TaxRegistrationId` = the customer's VAT number assigned with VAT ID **Registration category**, `@qualifyingId` = `VAT`.

### Vendor invoice (purchase from the German vendor, reverse charge)

The reporting French legal entity receives a vendor invoice with self-assessed tax, so the nodes are reversed: the vendor reports as the seller and the reporting legal entity reports as the buyer.

- **Seller** node — the German vendor (counterparty):
  - `CompanyId` = the vendor's EU VAT ID **Registration category**, `schemeId` = `0223` (because the registration category is **EU VAT ID**).
  - `TaxRegistrationId` = the vendor's VAT number assigned with VAT ID **Registration category**, `@qualifyingId` = `VAT`.
- **Buyer** node — the reporting French legal entity:
  - `CompanyId` = the company's SIREN, `schemeId` = `0002`.
  - `TaxRegistrationId` = the company's French VAT number, `@qualifyingId` = `VAT`.

The next examples use a French reporting legal entity and a counterparty that is established outside the European Union — in this case, a company in Switzerland. A Swiss company has a genuine national business identifier, the UID (Unternehmens-Identifikationsnummer, also called IDE), which you record on the counterparty registration ID with the **Enterprise ID** registration category. As a result, you report its `CompanyId` with `schemeId` = `0227`.

### Customer invoice (sale to a non-EU customer)

The reporting French legal entity issues a customer invoice to a customer that's established in Switzerland.

- **Seller** node — the reporting French legal entity:
  - `CompanyId` = the company's SIREN, `schemeId` = `0002`.
  - `TaxRegistrationId` = the company's French VAT number, `@qualifyingId` = `VAT`.
- **Buyer** node — the Swiss customer (counterparty):
  - `CompanyId` = the customer's enterprise identifier (for example, the Swiss UID), `schemeId` = `0227` (because the registration category is **Enterprise ID**).
  - `TaxRegistrationId` = the customer's VAT number, `@qualifyingId` = `VAT`, when a VAT registration number is available for the counterparty.

### Vendor invoice (purchase from a non-EU vendor, reverse charge)

The reporting French legal entity receives a vendor invoice with self-assessed tax from a vendor that's established in Switzerland, so the nodes are reversed.

- **Seller** node — the Swiss vendor (counterparty):
  - `CompanyId` = the vendor's enterprise identifier (for example, the Swiss UID), `schemeId` = `0227` (because the registration category is **Enterprise ID**).
  - `TaxRegistrationId` = the vendor's VAT number, `@qualifyingId` = `VAT`, when a VAT registration number is available for the counterparty.
- **Buyer** node — the reporting French legal entity:
  - `CompanyId` = the company's SIREN, `schemeId` = `0002`.
  - `TaxRegistrationId` = the company's French VAT number, `@qualifyingId` = `VAT`.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
