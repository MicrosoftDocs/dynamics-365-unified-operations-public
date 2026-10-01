---
title: Avoid validation errors for dynamic accounts in default dimensions
description: Learn how to keep dynamic accounts separate from default financial dimensions and fix validation errors in customizations.
author: ethanrimes
ms.author: ethankallett
ms.topic: best-practice
ms.date: 09/30/2026
ms.reviewer: twheeloc
ms.search.region: Global
ms.search.validFrom: 2019-01-16
ms.dyn365.ops.version: AX 7.0.0
---

# Avoid validation errors for dynamic accounts in default dimensions

[!INCLUDE [banner](../includes/banner.md)]

 This article provides guidance when your customizations and integrations create accounts, copy dimensions, or call financial dimension APIs. Keep account identities separate from default financial dimensions in your customizations and integrations. Mixing them can create invalid shared dimension data or cause errors during journal entry, posting, defaulting, integrations, and even read operations.

## Recognize the validation messages

An unsupported operation, or a read of an existing invalid default dimension, can produce this message:

> We detected an attempt to create a default dimension with a system-generated journal account type. We will block these attempts soon. Review any customizations that might cause this error. Reference Dimension ID *\<unique reference ID\>* if you need to contact support.

This message alone doesn't stop the operation. Its **Dimension ID** is a diagnostic reference for Microsoft Support, not a default- or ledger-dimension record ID.

If enforcement blocks the operation, you receive:

> Function DimensionAttributeValueSetStorage::validateDimensionAttributeType was called incorrectly.

Other APIs can also report *was called incorrectly*. Apply this guidance when the function is `DimensionAttributeValueSetStorage::validateDimensionAttributeType`.

> [!IMPORTANT]
> A call stack identifies where invalid input was detected, not necessarily where it was created. Both standard application code and customizations can encounter data created earlier. Correct the input and its source rather than suppressing validation.

### Keep account identities and default dimensions separate

For `LedgerJournalACType::Ledger`, an account combination is main-account-backed. A **dynamic account** instead identifies a non-ledger account through a `DynamicAccount` attribute. The validation message calls this a *system-generated journal account type*. Default financial dimensions describe how a transaction is analyzed; the dynamic account identifies the record that the transaction is for.

The following table gives examples of non-ledger account types; it isn't exhaustive.

| Non-ledger account type | Record identified by the dynamic account |
| --- | --- |
| Customer | Customer record |
| Vendor | Vendor record |
| Bank | Bank account |
| Project | Project record |
| Fixed asset | Fixed asset record |
| Worker | Worker record |
| Item | Item record |

Localization or extensions can provide other account types. These examples don't all use the same account-type enumeration or defaulting API.

The following table summarizes selected EDTs; it isn't an exhaustive list of financial-dimension EDTs.

| Extended data type (EDT) | Backing table | Contract |
| --- | --- | --- |
| `DimensionDefault` | `DimensionAttributeValueSet` | Financial dimension values only; no `MainAccount` or `DynamicAccount` attributes. |
| `DimensionDynamicAccount`, `DimensionDynamicDefaultAccount` | `DimensionAttributeValueCombination` | Account identity determined by the account type; it can be ledger or non-ledger. |
| `LedgerDimensionAccount` | `DimensionAttributeValueCombination` | Main-account-backed combination with financial dimension values. |
| `LedgerDimensionDefaultAccount` | `DimensionAttributeValueCombination` | Main account without financial dimension values. |

These EDTs contain 64-bit record IDs. A call can compile even when an argument comes from the wrong table. Trace where each ID was created; its variable name or EDT isn't proof.

Classify attributes by `DimensionAttribute.Type`: financial dimensions use `ExistingList` or `CustomList`, not `DynamicAccount` or `MainAccount`. A dynamic account for a customer or vendor is different from a **financial dimension value based on a customer or vendor**. The financial dimension value is valid in `DimensionDefault`; the dynamic account identity isn't.

### Audit customizations and integrations

The following table is the complete checklist of identified mechanisms for constructing, propagating, or detecting invalid default dimensions. Review every row, including equivalent APIs, wrappers, and extensions.

Review journal and offset-account defaulting, manual copy and edit helpers, posting and voucher creation, imports, OData and Data management mappings, and custom name and value resolvers. Also inspect display and report methods, entity `postLoad` and export code, workflow, and validation hooks: a read-oriented caller can invoke an API that constructs and saves dimensions.

| Code path to review | Problem and correction |
| --- | --- |
| `LedgerDimensionFacade::getDefaultDimensionFromLedgerDimension()`, its `LedgerDimensionProvider` wrapper, and `DimensionAttributeValueSetStorage::getDefaultDimensionFromDimensionCombination()` | Conversion excludes **only the main account**, not dynamic accounts. Use it only for a main-account-backed combination. For non-ledger accounts, obtain valid defaults from the document, journal, or backing record instead. |
| `DimensionAttributeValueSetStorage.addItem()` / `addItemValues()` in custom constructors, mappings, or copy loops | An account attribute can enter storage directly, without conversion. Check the attribute type **before** resolving or adding values. Map account columns to the appropriate account or offset fields and financial dimension columns to default dimensions. Reject invalid mappings explicitly; don't silently drop their values. |
| `LedgerDimensionDefaultingEngine::getDefaultDimension()` consuming specifier maps | Maps can contain account attributes from `getLedgerDimensionSpecifiers()`, invalid stored membership from `getDefaultDimensionSpecifiers()`, or custom entries. Verify every map's source and attribute types before rebuilding defaults. Exclude-main-account and include-main-account options don't filter dynamic accounts. |
| `LedgerDimensionDefaultFacade::serviceMergeDefaultDimensions()` and equivalent defaulting or reference-copy paths | Merging or copying an invalid default set can propagate it. Trace **every source**, not just the result. A one-source merge can return the input unchanged, without validating its members. Merge is not a data-repair operation. |
| `LedgerDimensionDefaultFacade::serviceReplaceAttributeValue()` | Replacement retains the target's other attributes and copies the selected attribute from the source. Replacing a department doesn't remove an unrelated invalid account attribute; selecting an account attribute can introduce one. Verify both the retained target and the selected source attribute. |
| `DimensionAttributeValueSetStorage::find()` and `DimensionDefaultFacade::areEqual()` | Loading reconstructs stored members through `addItem`; comparison can load and save sets internally. An error can precede the intended edit or cleanup. Investigate the stored input rather than bypassing validation in the reader. |
| `DimensionAttributeValueSetStorage.save()` in custom helpers | Save can revalidate dynamic account attributes. Trace how storage was populated; a save frame alone doesn't identify the original producer or prove that a write committed. |

### X++ (incorrect): converting a dynamic account to default dimensions

In this example, `dynamicAccount` identifies a customer, not a main account. The conversion call is invalid even though both values are record IDs.

```xpp
DimensionDynamicAccount dynamicAccount =
    LedgerDynamicAccountHelper::getDynamicAccountFromAccountNumber(
        accountNumber, LedgerJournalACType::Cust);

ledgerJournalTrans.DefaultDimension =
    LedgerDimensionFacade::getDefaultDimensionFromLedgerDimension(dynamicAccount); // Incorrect: converts a customer account identity to default dimensions.
```

> [!WARNING]
> Guard **before** conversion or construction. Conversion saves before returning, so converting a dynamic account and then removing its account attribute is too late. Loading can also fail before cleanup runs. Passing a zero value to `addItemValues()` isn't a workaround: attribute validation occurs before removal.

Results can be cached, and some operations return an input without rebuilding it. The absence of a new message doesn't establish that the data or call pattern is valid.

### Use an account-type-aware default dimension source

For `LedgerJournalTrans`, keep each side's fields and company context together:

| Side | Account type and identity | Financial defaults |
| --- | --- | --- |
| Account | `AccountType`, `LedgerDimension` | `DefaultDimension` |
| Offset | `OffsetAccountType`, `OffsetLedgerDimension` | `OffsetDefaultDimension` |

For a **ledger** side, financial dimensions reside in its ledger dimension; the corresponding default-dimension field is `0`. Don't assign a default-set merge result to a ledger side's `DefaultDimension` or `OffsetDefaultDimension`. This rule applies to journal storage and isn't advice to clear dimensions to resolve an error.

For a **non-ledger** side, preserve valid line and document defaults and use the applicable account-defaulting logic. `LedgerJournalEngine::getAccountDefaultDimension()` resolves supported `LedgerJournalACType` values from the backing record in the supplied company. Supply the asset book, localized standard or book, and transaction date required by that account type. The offset company can differ from the account company.

This method doesn't resolve every account type. For unsupported or custom types, use the appropriate backing-record defaulting API. Don't interpret an empty result as proof that the method handled the account type. Worker defaults require the applicable employment, legal entity, and effective date.

For other account-type enumerations, use `DimensionHierarchyHelper::getHierarchyTypeByAccountType()` with the enumeration ID and, when required, the discriminator that selects customer or vendor. `AccountStructure` denotes a main-account-backed type. Handle unmapped or extension-defined values explicitly. Don't cast them to `LedgerJournalACType` or assume every custom value has a mapping.

### Compose dimensions in the supported direction

Merge **valid default sets**, then supply them to the appropriate account-composition API. Preserve the process's defaulting precedence; `serviceMergeDefaultDimensions()` uses the first supplied value for each attribute.

For example, with valid document/account defaults and a main-account-backed combination:

```xpp
DimensionDefault mergedDefaults =
    LedgerDimensionDefaultFacade::serviceMergeDefaultDimensions(
        documentDefaults, accountDefaults);

LedgerDimensionAccount ledgerAccount =
    LedgerDimensionFacade::serviceCreateLedgerDimension(
        mainAccountCombination, mergedDefaults);
```

Check each API's parameter order:

- `LedgerDimensionFacade::serviceCreateLedgerDimension(accountCombination, defaults)` takes the account first.
- `LedgerDimensionFacade::serviceCreateLedgerDimForDefaultDim(defaults, accountCombination)` takes defaults first.

Swapping these IDs queries the wrong table; it isn't an implicit conversion between accounts and defaults. These APIs also differ in precedence, so don't substitute one for another just to avoid an error. For non-ledger accounts, keep the identity in the account flow and follow the journal's account-type-aware defaulting logic.

### Don't hide or propagate an existing invalid default dimension

Fixing a producer doesn't repair records that already reference its output. Don't disable validation, copy an invalid set into more records, catch the validation exception and return `0`, silently remove financial values, or retry unchanged input. Clearing caches or suppressing warnings isn't data repair.

Don't assume a helper is read-only because its name starts with *get* or it runs during display or comparison. Helpers can save internally; discarding a result or rolling back the outer operation doesn't guarantee that nothing persisted.

Default-dimension sets are shared. Don't rewrite their hashes, delete their items, or repair their references directly in custom code or SQL. Don't depend on system-generated account columns in default-dimension tables; use account APIs instead. Removing such columns doesn't repair existing default-dimension sets. Contact Microsoft Support for an appropriate repair that preserves valid financial values and legitimate account identities.

### Diagnose and correct an occurrence

1. Retain the complete message, diagnostic reference ID, timestamp, legal entity, and operation.
2. Find the nearest conversion, add, map reconstruction, merge, replacement, load, or save in the stack. Trace its actual input IDs and attribute types to their sources. A map-producing method might already have returned and be absent from the stack.
3. Correct invalid construction or mapping before the API call. For an existing invalid set, identify affected source and consumer records and arrange supported repair separately.
4. Exercise each supported account type on both account and offset sides, including different companies and required asset/employment context. Cover new and previously affected records; journal entry, posting, batch, import/export, workflow, validation, and read/display paths.
5. Confirm that account identity, expected financial dimensions, and defaulting precedence are preserved, not merely that the message disappeared. Include first-use and cached paths. A code correction alone isn't proof that existing data was repaired.

If the source remains unclear, contact Microsoft Support with the diagnostic details. Provide sensitive business data only when requested through an approved support channel.

#### See also

- [Default financial dimensions](dimension-defaulting.md)
- [Best practices for financial dimension customizations](financial-dimension-customization-errors.md)
- [Choosing the correct extended data type (EDT) for financial dimension foreign keys](dimension-fk-edt-usage.md)
- [Ledger account combinations](LedgerAccountCombinations.md)
- [Modifying financial dimension data](modifying-financial-dimension-data.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
