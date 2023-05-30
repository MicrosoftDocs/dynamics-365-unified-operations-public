---
title: NUMSEQVALUE ER function
description: This article provides information about how the NUMSEQVALUE Electronic reporting (ER) function is used.
author: kfend
ms.date: 12/17/2019
ms.prod: 
ms.technology: 
audience: Application User, IT Pro
ms.reviewer: kfend
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 24223e13-727a-4be6-a22d-4d427f504ac9
ms.search.form: ERDataModelDesigner, ERExpressionDesignerFormula, ERMappedFormatDesigner, ERModelMappingDesigner
---

# NUMSEQVALUE ER function

[!include [banner](../includes/banner.md)]

The `NUMSEQVALUE` function returns a *String* value that represents the new generated value of a number sequence, based on the specified number sequence, scope, and scope ID. The scope ID equals the company code that is supplied by the context that the Electronic reporting (ER) format is run under.

## Syntax 1

```vb
NUMSEQVALUE (number sequence code)
```

## Syntax 2

```vb
NUMSEQVALUE (number sequence record ID)
```

## Syntax 3

```vb
NUMSEQVALUE (number sequence code, scope type, scope ID)
```

## Arguments

`number sequence code`: *String*

A text value that represents the code of the number sequence that a new value is required in.

`number sequence record ID`: *Int64*

An *Int64* value that represents the record ID of a record in the NumberSequenceTable table that contains the definition of the number sequence that a new value is required in.

`scope type`: *Enum value*

An enumeration value of the **ERExpressionNumberSequenceScopeType** enumeration that defines the scope of the number sequence that a new value is required in. The available scope types are **Shared**, **Legal entity**, and **Company**.

`scope ID`: *String*

A *String* value that identifies the scope, based on the specified scope type.

## Return values

*String*

The resulting text value.

## Usage notes

For the **Shared** scope type, specify an empty string as the scope ID.

For the **Company** and **Legal entity** scope types, specify the company code as the scope ID. If you specify an empty string as the scope ID for these scope types, the current company code is used.

When syntax 1 is used, the number sequence is requested for the **Company** scope type, and the company code is supplied by the context that the ER format is run under.

## Example 1

In your ER format, you define the **AskNumSeq** data source of the *User input parameter* type. This data source refers to the **Description** extended data type (EDT). Next, you define the **NumSeq** data source of the *Calculated field* type. This data source contains the expression `NUMSEQVALUE (AskNumSeq)`. When the **NumSeq** data source is called, it returns the new generated value of the number sequence that was specified at runtime by entering its code in the dialog box. The number sequence is requested for the **Company** scope type. The company code is supplied by the context that the ER format is run under.

## Example 2

The following data sources are defined in your model mapping:

- The **LedgerParms** data source of the *Table* type. This data source refers to the LedgerParameters table.
- The **NumSeq** data source of the *Calculated field* type. This data source contains the expression `NUMSEQVALUE ( LedgerParameters.'numRefJournalNum()'.NumberSequenceId)`.

When the **NumSeq** data source is called, it returns the new generated value of the number sequence that has been configured in the General ledger parameters for the company that supplies the context that the ER format is run under. This number sequence uniquely identifies journals and acts as a batch number that links the transactions together.

## Example 3

The following data sources are defined in your model mapping:

- The **enumScope** data source of the Microsoft Dynamics 365 Finance *enumeration* type. This data source refers to the **ERExpressionNumberSequenceScopeType** enumeration.
- The **NumSeq** data source of the *Calculated field* type. This data source contains the expression `NUMSEQVALUE ("Gene_1", enumScope.Company, "")`.

When the **NumSeq** data source is called, it returns the new generated value of the **Gene\_1** number sequence that has been configured for the company that supplies the context that the ER format is run under.

## Additional resources

[Other (business domain–specific) functions](er-functions-category-other.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
