---
title: Best practices for financial dimension customizations
description: Learn about best practices when writing customizations that interact with the financial dimension framework, including calling dimension APIs and building DimAttribute views.
author: ethanrimes
ms.author: ethanrimes
ms.topic: best-practice
ms.date: 03/03/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2019-01-16
ms.dyn365.ops.version: AX 7.0.0
---

# Best practices for financial dimension customizations

[!include [banner](../includes/banner.md)]

This article describes best practices for writing customizations that interact with the financial dimension framework. These guidelines are based on the most common mistakes observed in partner and ISV code. Following them helps avoid runtime errors, missing dimensions, and data integrity issues.

## Validate records before calling dimension APIs

Before calling `DimensionAttributeValue::findByDimensionAttributeAndValue()`, always confirm that the record you're referencing actually exists in the backing table. The dimension framework validates that the backing record exists and throws an error if it doesn't. The framework doesn't own the backing tables — your code is responsible for passing valid data.

For example, if your code asks the framework to resolve Project "123" but that project doesn't exist in `ProjTable`, the call fails. Always query the backing table first.

## Match the legal entity context to the transaction

When your code looks up a record, make sure the legal entity (company) context matches the context set on the transaction or journal line. A common mistake is querying a record in one company but assigning it to a transaction in a different company. The dimension framework resolves values within the company context of the transaction, not the context of your lookup.

For example, looking up a vendor in company `001` but setting the offset company to `002` on the journal line causes the framework to search for the vendor in company `002`, where it may not exist.

## Match the account type to the source table

When passing a natural key to the dimension framework, ensure the account type parameter matches the table the value came from. If your code reads an account number from `VendTable` but sets the account type to `Customer`, the framework looks for that value in `CustTable` instead. Unless the same value exists in both tables, this fails.

## Avoid creating dimension references during delete operations

If your customization runs logic during a record delete, don't attempt to assign that same record as a dimension value within the same transaction scope. Because the backing record has already been deleted (or is in the process of being deleted) within the transaction, the dimension framework can't resolve it.

## Don't apply Extensible Data Security (XDS) to dimension backing tables

XDS security policies are **not compatible** with the financial dimension framework. Many dimension processes run under the current user's context, not a system administrator context. If XDS policies are enabled on a backing table or its `DimAttribute*` wrapping view, the framework may be unable to resolve dimension values for users who don't have access under those policies.

Remove XDS policies from any tables and `DimAttribute*` views that serve as financial dimension sources.

## Sanitize data to prevent hidden characters in dimension values

Invisible characters such as non-breaking spaces (ALT+0160) or other Unicode characters can be introduced through integrations or manual entry. These characters look identical to normal characters but cause lookups to fail because the strings don't match.

If your customization imports data that will be used as dimension values, validate and sanitize input before writing it to the backing table.

## Don't add fields to DimAttribute views

The dimension framework expects a specific number of fields on each `DimAttribute*` view — exactly **three fields** for standard (non-date-effective) views. If a partner extension adds extra columns to a shipped `DimAttribute*` view or creates a custom view with the wrong field count, the framework silently skips that dimension. This causes the dimension to disappear from the **Financial Dimensions** details form and become unavailable in account structures and integration formats.

If you need to create a new backing table for use as a financial dimension, follow the guidance in [Make backing tables consumable as financial dimensions](/dynamics365/fin-ops-core/dev-itpro/financial/dimensionable-entities). If you've extended a shipped `DimAttribute*` view, remove the extra fields.

> [!IMPORTANT]
> Never modify `DimAttribute*` views directly in the database. This can cause data corruption and runtime errors due to metadata inconsistencies. Always deploy corrections through code.

## Don't set Primary Company Control on shared financial dimension entities

The **Primary Company Control** property on a data entity tells the entity framework that each record belongs to a single legal entity. When set, the framework adds a `DATAAREAID` column to the entity's backing view and automatically injects a company filter at runtime. This is correct for company-specific entities like Customers or Vendors.

Financial dimension values are shared reference data that exist once and are reused across all legal entities. If a customization sets Primary Company Control on a shared entity like **Financial Dimension Values**, the entity framework silently converts it from cross-company to company-specific. Exports through DMF, OData, and Excel add-ins then return only the current company's values.

There is no runtime workaround — the entity framework re-applies the filter from metadata even if you manually alter the view. Remove the Primary Company Control setting from the entity to restore cross-company behavior.

## See also

- [Make backing tables consumable as financial dimensions](/dynamics365/fin-ops-core/dev-itpro/financial/dimensionable-entities)
- [Dimension FK reference EDT usage](/dynamics365/fin-ops-core/dev-itpro/financial/dimension-fk-edt-usage.md)
- [Modifying financial dimension data](/dynamics365/fin-ops-core/dev-itpro/financial/modifying-financial-dimension-data.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
