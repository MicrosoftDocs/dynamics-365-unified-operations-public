---
title: Common errors in financial dimension framework customizations
description: Learn how to diagnose and fix common developer mistakes when building DimAttribute views or writing code that calls financial dimension framework APIs.
author: ethanrimes
ms.author: ethanrimes
ms.topic: troubleshooting
ms.date: 03/03/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2019-01-16
ms.dyn365.ops.version: AX 7.0.0
---

# Common errors in financial dimension framework customizations

[!include [banner](../includes/banner.md)]

This article describes two categories of developer errors that are frequently encountered when customizing the financial dimensions framework: incorrect DimAttribute view schemas that cause dimensions to stop appearing in the UI, and incorrect calling code patterns that cause the `DimensionAttributeValue` creation guard to throw an error.

## DimAttribute view schema errors

### Symptoms

A financial dimension backed by a custom or customized DimAttribute view may show any of the following symptoms:

- The dimension no longer appears in the Dimension Details form.
- A dimension that should be backed by an entity (such as `OMDepartment`) shows as **\<Custom dimension\>** instead.
- The dimension can't be added to an integration format or account structure even though other dimensions can.
- The dimension still appears in account structures and in the Segmented Entry Control on existing transactions because it was previously used, but it can't be selected for new use.
- The error `"DimensionAttributeValue.getValue called with an invalid DimensionAttribute record Id"` appears in telemetry.

### Cause

The dimension framework validates the schema of every registered DimAttribute view at startup. The view must contain exactly the columns defined in [Make backing tables consumable as financial dimensions](/dynamics365/fin-ops-core/dev-itpro/financial/dimensionable-entities). If the view has extra columns — for example, because an ISV or customization added fields to a shipped `DimAttribute*` view — the framework rejects the view silently at load time.

The valid column sets are:

- **Standard views:** `Key`, `Value`, `Name` (three columns, plus system columns)
- **Date-effective views:** `Key`, `Value`, `Name`, `ValidFrom`, `ValidTo` (five columns, plus system columns)

### Resolution

Identify which DimAttribute view has the wrong schema and remove the extra fields:

- If a custom model added fields to one of the **shipped** `DimAttribute*` views, undo those customizations. Shipped DimAttribute views must not be extended with additional fields.
- If a **new custom** DimAttribute view has extra fields, correct its schema to match the steps in [Make backing tables consumable as financial dimensions](/dynamics365/fin-ops-core/dev-itpro/financial/dimensionable-entities).

After deploying the corrected code, the dimension reappears in the Dimension Details form automatically on the next AOS startup.

> [!WARNING]
> Don't attempt to fix this by modifying the view definition directly in SQL Server Management Studio. Changes made outside the AOT are inconsistent with SQLDICTIONARY and table metadata caches, and can cause further runtime errors.

## DimensionAttributeValue creation errors

### Symptoms

Code throws one of the following errors when attempting to enter or default a dimension value:

```
No record with the value %1 exists in table %2 in data area %3; this cannot be used as a dimension value.
```
```
Unable to return DimensionAttributeValue record for Dimension %1 with value %2 in table %3 through view %4 as no record exists, or you do not have access to it.
```

These errors always originate from calling code outside the dimension framework. The framework validates that a backing record exists before creating a link to it, and it throws this error when validation fails. The source of the problem is never in the dimension tables themselves.

### Cause 1: Wrong data area context

Code resolves a natural key in one legal entity but passes it to the dimension framework using a different legal entity context.

```xpp
// Incorrect: record looked up in company '001' but dimension set for company '002'
changeCompany('001')
{
    VendTable vendTable;
    select AccountNum from vendTable where vendTable.AccountNum = _account;

    ledgerJournalTrans.parmOffsetCompany('002');
    ledgerJournalTrans.parmOffsetAccountType(LedgerJournalACType::Vend);
    ledgerJournalTrans.parmOffsetAccount(vendTable.AccountNum);
    // Framework throws error unless AccountNum also exists in VendTable for company '002'
}
```

**Fix:** Ensure the company context used to resolve the natural key matches the company context passed to the dimension API call.

### Cause 2: Natural key from the wrong table

Code resolves a key from one table but assigns it as a dimension value for a different table.

```xpp
// Incorrect: key from VendTable used where CustTable dimension is expected
VendTable vendTable;
select AccountNum from vendTable where vendTable.AccountNum = _account;

ledgerJournalTrans.parmAccountType(LedgerJournalACType::Cust);
ledgerJournalTrans.parmAccount(vendTable.AccountNum);
// Framework throws error unless AccountNum happens to exist in both VendTable and CustTable
```

**Fix:** Ensure the natural key passed to the dimension API comes from the same table that the DimAttribute view wraps.

### Cause 3: Backing record deleted within the same transaction

Code that deletes a primary record may trigger other code (such as `validateDelete` on a related table) that tries to create a dimension link to the record that is already deleted within the open transaction.

```xpp
// Pattern that can cause the error:
VendTable.delete()
{
    ttsbegin;
    super(); // VendTable record is now deleted within this transaction

    // ... cascade deletes including VendBankAccount
    ttscommit;
}

VendBankAccount.validateDelete()
{
    // This runs while VendTable is already deleted in the transaction scope
    this.ledgerDimension = DimensionAttributeValue::find(this.VendAccount);
    // Framework throws error because VendTable record no longer exists in this transaction
}
```

**Fix:** Restructure the delete sequence so that dimension references are resolved before the backing record is deleted, or guard the dimension call against the deleted state.

### Cause 4: XDS security on the backing table

Extensible Data Security (XDS) policies applied to a backing table or its DimAttribute wrapping view prevent the dimension framework from finding the record, even if it exists. The framework runs under the current user context, not a system context, so XDS restrictions apply.

> [!IMPORTANT]
> XDS security is not compatible with tables that serve as financial dimension sources. Applying XDS to such a table prevents the dimension framework from resolving values for users subject to that policy.

On version 10.0.41 and later, the error message explicitly identifies XDS as the cause: *"XDS policies prevent successful resolution of the DimensionAttribute RecId %1 for table %2 with view %3."*

**Fix:** Remove XDS policies from the backing table and its DimAttribute view, or restructure data access so that dimension sources are not subject to row-level security.

### Cause 5: Hidden characters in the natural key value

The natural key value stored in the backing table contains non-printable Unicode characters or visually identical substitutes (for example, a non-breaking space ALT+0160 instead of a regular space ALT+0032). The value appears correct in the UI and in SQL results, but the byte sequence doesn't match what the calling code passes to the framework.

A value that looks like `110110` might be stored as `***110110` when the leading bytes are inspected — the invisible characters cause the framework lookup to fail.

On version 10.0.42 and later, the error message identifies this cause: *"At least one record was found in the backing table through the DimAttribute* wrapping view partially matching the requested value. Its natural key string length is longer than supported..."*

**Fix:** Clear and retype the affected value directly in the form to remove hidden characters. If the characters are being introduced by an external integration, add validation to the integration to sanitize the input before it reaches Finance.

## See also

- [Make backing tables consumable as financial dimensions](/dynamics365/fin-ops-core/dev-itpro/financial/dimensionable-entities)
- [Dimension FK reference EDT usage](/dynamics365/fin-ops-core/dev-itpro/financial/dimension-fk-edt-usage.md)
- [Modifying financial dimension data](/dynamics365/fin-ops-core/dev-itpro/financial/modifying-financial-dimension-data.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
