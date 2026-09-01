---
title: Avoid validation errors for dynamic accounts in default dimensions
description: Learn how to keep dynamic accounts separate from default financial dimensions and fix validation errors in customizations.
author: ethanrimes
ms.author: ethankallett
ms.topic: best-practice
ms.date: 08/27/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2019-01-16
ms.dyn365.ops.version: AX 7.0.0
---

# Avoid validation errors for dynamic accounts in default dimensions

[!INCLUDE [banner](../includes/banner.md)]

This article explains how to keep dynamic accounts separate from default financial dimensions in customizations and integrations. A dynamic account identifies the account for a journal line based on its account type. Mixing a non-ledger dynamic account into a default dimension can cause validation errors that block journal entry, posting, batch, or integration operations. Use this guidance when your customizations and integrations create accounts, copy dimensions, or call financial dimension APIs.

## Recognize the validation messages

An unsupported call pattern can produce the following message:

> We detected an attempt to create a default dimension with a system-generated journal account type. We will block these attempts soon. Review any customizations that might cause this error. Reference Dimension ID *\<unique reference ID\>* if you need to contact support.

The message doesn't stop the operation. Its **Dimension ID** is a unique reference ID that Microsoft Support can use to locate diagnostic information, not a default- or ledger-dimension record ID.

If enforcement blocks the operation, you receive the following error:

> Function DimensionAttributeValueSetStorage::validateDimensionAttributeType was called incorrectly.

Because multiple APIs use *was called incorrectly*, apply this guidance only when the function is `DimensionAttributeValueSetStorage::validateDimensionAttributeType`.

> [!IMPORTANT]
> Fix the customization or integration that constructs the dimension. Don't change validation settings, update financial dimension framework tables directly, or delete dimension records to work around the message.
>
> Validation runs before the dimension API returns and saves the default dimension; conversion results can also be cached. Removing the dynamic account attribute from the returned value doesn't prevent the message. Add the guard before the call.

## Keep account identities and default dimensions separate

A dynamic account identifies the account for a journal line. Its account type determines which record or value backs the account. For `LedgerJournalACType::Ledger`, the dynamic account is a main-account-backed combination. A non-ledger dynamic account contains a system-generated `DynamicAccount` attribute that identifies a customer, vendor, bank account, project, fixed asset, or another backing record. The validation message refers to this case as a *system-generated journal account type*.

The following table shows common non-ledger dynamic accounts.

| Dynamic account | Account-type value | Backing record or value |
| --- | --- | --- |
| Customer | `LedgerJournalACType::Cust` | Customer account |
| Vendor | `LedgerJournalACType::Vend` | Vendor account |
| Bank | `LedgerJournalACType::Bank` | Bank account |
| Project | `LedgerJournalACType::Project` | Project |
| Fixed asset | `LedgerJournalACType::FixedAssets` | Fixed asset and, when required, asset book |
| Worker or item | A value in another account-type enumeration | Worker employment or item |
| Localized or custom account | A localized or extension-defined value | The record defined by the applicable account-type mapping |

These account identities belong in a ledger dimension, not in a default dimension. A default dimension describes how a transaction is analyzed, whereas a dynamic account identifies the record that the transaction is for.

The dimension extended data types (EDTs) represent different data contracts.

| EDT | Backing table | Use |
| --- | --- | --- |
| `DimensionDefault` | `DimensionAttributeValueSet` | Financial dimension values only. Don't include a main account or dynamic account attribute. |
| `DimensionDynamicAccount` and `DimensionDynamicDefaultAccount` | `DimensionAttributeValueCombination` | An account whose account type determines the backing entity. For `LedgerJournalACType::Ledger`, the value is a main-account combination. For a non-ledger account type, it's a dynamic account such as a customer, vendor, or bank account. |
| `LedgerDimensionAccount` | `DimensionAttributeValueCombination` | A main-account-backed ledger account combination with financial dimension values. |
| `LedgerDimensionDefaultAccount` | `DimensionAttributeValueCombination` | A main account without financial dimension values. |

These EDTs contain 64-bit record IDs, so X++ can compile a call that violates the data contract.

> [!NOTE]
> A dynamic account for a customer or vendor differs from a financial dimension value based on a customer or vendor. The financial dimension value is valid in a `DimensionDefault`.

## Don't derive default dimensions from a dynamic account

The following pattern is incorrect when the ledger dimension contains a customer, vendor, bank, project, fixed asset, worker, item, or another dynamic account.

**X++ (incorrect)**

```xpp
DimensionDynamicAccount dynamicAccount =
    LedgerDynamicAccountHelper::getDynamicAccountFromAccountNumber(
        accountNumber,
        LedgerJournalACType::Cust);

ledgerJournalTrans.LedgerDimension = dynamicAccount;
ledgerJournalTrans.DefaultDimension =
    LedgerDimensionFacade::getDefaultDimensionFromLedgerDimension(dynamicAccount); // Incorrect: Not main-account-backed.
```

The call compiles, but it treats a ledger-dimension combination that contains a dynamic account attribute as financial dimension values. `LedgerDimensionFacade::getDefaultDimensionFromLedgerDimension()` requires a main-account-backed combination. Check the account type or hierarchy first.

The same restriction applies to the lower-level `DimensionAttributeValueSetStorage::getDefaultDimensionFromDimensionCombination()` API.

## Use an account-type-aware default dimension source

For a `LedgerJournalTrans` record, the account-side fields are `AccountType`, `LedgerDimension`, and `DefaultDimension`. The offset-side fields are `OffsetAccountType`, `OffsetLedgerDimension`, and `OffsetDefaultDimension`. Apply the same decision process to both sides, while keeping ledger-dimension and default-dimension values separate. For a ledger account, financial dimensions are already part of `LedgerDimension` or `OffsetLedgerDimension`, and the corresponding default-dimension field should be `0`.

Choose the default-dimension source as follows.

| Condition | Default-dimension source |
| --- | --- |
| The account type is `LedgerJournalACType::Ledger`. | Keep the financial dimension values in the main-account-backed ledger dimension, and set the corresponding default-dimension field to `0`. |
| A default dimension already exists for a non-ledger dynamic account. | Use `DefaultDimension` or `OffsetDefaultDimension` as the highest-precedence source. |
| The account is a supported non-ledger `LedgerJournalACType` value. | Use `LedgerJournalEngine::getAccountDefaultDimension()` and supply any required context. |
| The account type is unsupported, extension-defined, uses another enumeration, or is a localized type that the method doesn't support. | Obtain the default dimension from the backing record or the applicable defaulting logic. |

The following example keeps the account and default dimension values separate for standard `LedgerJournalACType` values.

```xpp
if (ledgerJournalTrans.AccountType == LedgerJournalACType::Ledger)
{
    ledgerJournalTrans.DefaultDimension = 0;
}
else
{
    DimensionDefault accountDefaultDimension =
        LedgerJournalEngine::getAccountDefaultDimension(
            ledgerJournalTrans.parmAccount(),
            ledgerJournalTrans.Company,
            ledgerJournalTrans.AccountType);

    ledgerJournalTrans.DefaultDimension =
        LedgerDimensionDefaultFacade::serviceMergeDefaultDimensions(
            ledgerJournalTrans.DefaultDimension,
            accountDefaultDimension);
}
```

> [!NOTE]
> Apply the same decision process to the offset account by using `OffsetAccountType`, `OffsetLedgerDimension`, and `OffsetDefaultDimension`. For a ledger offset account, keep the financial dimensions in `OffsetLedgerDimension` and set `OffsetDefaultDimension` to `0`. For a non-ledger offset account, derive only a valid `DimensionDefault` and merge it into `OffsetDefaultDimension`.

For each attribute, `serviceMergeDefaultDimensions()` keeps the first supplied value. Put the highest-precedence source first.

Some account types need more context. Fixed assets can require a book ID; localized types can require a standard or book ID and transaction date. Pass the required parameters to `LedgerJournalEngine::getAccountDefaultDimension()`.

The method handles only its switch cases and returns an empty value for others, including `LedgerJournalACType::Ledger` and `LedgerJournalACType::RCash`. The empty value is expected for a ledger account because its financial dimensions remain in the ledger dimension. For another unsupported type, use the journal line or backing record instead.

Types outside `LedgerJournalACType`, such as a worker in Expense management, aren't resolved. Read the default dimension from the backing record. Worker default dimensions are date-effective and stored per legal entity on the employment record.

### Handle custom account-type enumerations

You need this check only when your customization uses an account-type enumeration other than `LedgerJournalACType`.

```xpp
DimensionHierarchyType hierarchyType =
    DimensionHierarchyHelper::getHierarchyTypeByAccountType(
        enum2int(accountType),
        enumNum(MyAccountType));
```

Always pass the enumeration ID in the second parameter; otherwise, the method interprets the value as `LedgerJournalACType`. For a value shared by customers and vendors, also pass the third parameter.

Only `DimensionHierarchyType::AccountStructure` is main-account-backed. The method raises an *incorrectly called* error for an account type that it can't map (such as dynamic accounts).

The `getHierarchyTypeByAccountTypeDelegate` delegate is called only for an enumeration that the method doesn't handle. It doesn't cover extension-defined values in a handled enumeration. Some mappings depend on a configuration key, country/region, or feature. Implement a handler for a custom enumeration, and guard extension-defined and unmapped values.

## Compose dimensions in the supported direction

Use the correct EDTs for account and default-dimension record IDs. Merge default dimensions, and then apply the result to the account.

```xpp
DimensionDefault mergedDefaultDimension =
    LedgerDimensionDefaultFacade::serviceMergeDefaultDimensions(
        documentDefaultDimension,
        accountDefaultDimension);

LedgerDimensionAccount ledgerDimension =
    LedgerDimensionFacade::serviceCreateLedgerDimension(
        accountLedgerDimension,
        mergedDefaultDimension);
```

Don't swap `DimensionDefault` and ledger-dimension arguments. Because both are record IDs, swapped arguments can compile but return zero, omit dimensions, use an unrelated record, or cause another validation error.

## Audit customizations and integrations

Search custom code for the following APIs and verify the source and destination of every dimension record ID.

| API or pattern | What to verify |
| --- | --- |
| `LedgerDimensionFacade::getDefaultDimensionFromLedgerDimension()` | The argument is main-account-backed. For journal lines, guard the call by account type. |
| `DimensionAttributeValueSetStorage::getDefaultDimensionFromDimensionCombination()` | The combination doesn't contain a `DynamicAccount` attribute. `LedgerDimensionFacade::getDefaultDimensionFromLedgerDimension()` calls this method directly, so switching between the two APIs doesn't change the outcome. Both exclude only the main account. |
| `DimensionAttributeValueSetStorage::addItem()` and `addItemValues()` | The attribute is a financial dimension and its `DimensionAttribute.Type` isn't `DynamicAccount`. |
| `LedgerDimensionDefaultingEngine::getLedgerDimensionSpecifiers()` followed by `getDefaultDimension()` | Don't feed ledger specifiers into default-dimension storage unless dynamic account attributes are excluded before the call. Setting the exclude-main-account or include-main-account parameters isn't sufficient, because the main account and dynamic account are separate attributes. |
| `DimensionAttributeValueSetStorage::find()` and default-dimension merge or replace APIs | Every input is a real `DimensionDefault`. Existing invalid dimension sets can surface the same validation when they're read or copied. |
| `LedgerDimensionFacade::serviceCreateLedgerDimension()`, `serviceCreateLedgerDimForDefaultDim()`, and `serviceMergeLedgerDimensions()` | Account and default-dimension arguments are in the documented positions and use the correct EDTs. `serviceCreateLedgerDimension()` takes the ledger dimension first and the default dimensions after it, and `serviceCreateLedgerDimForDefaultDim()` takes the default dimension first. Because both are record IDs, swapping them compiles. |
| Data entity, OData, and Data management mappings | Account display values map to account or ledger-dimension fields. Financial dimension values map to default-dimension fields. |
| Custom name/value resolvers or direct storage construction | Contracts don't name or add dynamic account attributes to a default dimension. |

Don't rely only on the declared EDT; trace where the record ID was created. A posted ledger account combination is normally main-account-backed even for accounts receivable or payable. A non-ledger journal line can instead hold a dynamic account in `LedgerDimension` or `OffsetLedgerDimension`.

## Diagnose and correct an occurrence

1. Confirm that the function name in the error is `DimensionAttributeValueSetStorage::validateDimensionAttributeType`.
1. If the nonblocking message includes a **Dimension ID**, retain that unique reference ID.

    > [!NOTE]
    > Dimension results can be cached, so the message might not appear for every call. Its absence doesn't prove that the call pattern changed. Verify the code path.

1. Find the customization, ISV extension, or integration mapping that creates or copies the default dimension. Search first for the APIs in the preceding table.
1. Trace the input record ID to its producer. For `LedgerJournalACType`, `AccountType == LedgerJournalACType::Ledger` identifies a main-account-backed ledger dimension. For another enumeration, guard unmapped values, and then call `DimensionHierarchyHelper::getHierarchyTypeByAccountType()` with the enumeration ID.
1. For a dynamic account, stop converting its ledger dimension to a default dimension. Source valid default dimensions from the journal field, document, or backing account record instead.
1. Keep the dynamic account in the ledger-dimension flow. Merge only valid default dimension sets, and apply them to the account with a ledger-dimension creation API.
1. Complete the correction only when all the following conditions are met for each supported account type:

    - No validation message or error occurs.
    - The account identity is preserved.
    - The expected default financial dimensions remain.
    - Journal entry, posting, batch, and integration scenarios complete successfully.

If you can't locate the caller, contact Microsoft Support and provide the complete message, unique reference ID, timestamp, legal entity, and operation that produced the message. Don't include sensitive business data unless Support requests it through an approved channel.

## See also

- [Default financial dimensions](dimension-defaulting.md)
- [Best practices for financial dimension customizations](financial-dimension-customization-errors.md)
- [Choosing the correct extended data type (EDT) for financial dimension foreign keys](dimension-fk-edt-usage.md)
- [Ledger account combinations](LedgerAccountCombinations.md)
- [Modifying financial dimension data](modifying-financial-dimension-data.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
