---
# required metadata

title: NUMSEQVALUE ER function
description: This topic explains how the NUMSEQVALUE ER function is used
author: NickSelin
manager: kfend
ms.date: 11/29/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: ERDataModelDesigner, ERExpressionDesignerFormula, ERMappedFormatDesigner, ERModelMappingDesigner
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 58771
ms.assetid: 24223e13-727a-4be6-a22d-4d427f504ac9
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# <a name="NUMSEQVALUE">NUMSEQVALUE Function</a>

[!include [banner](../includes/banner.md)]

The `NUMSEQVALUE` function returns a *String* value of the new generated value of a number sequence, based on the specified number sequence, the scope, and (as the scope ID) the code of the company that is supplied by the context the ER format is run under.

## Syntax 1

```
NUMSEQVALUE (number sequence code)
```

## Syntax 2

```
NUMSEQVALUE (number sequence record ID)
```

## Syntax 3

```
NUMSEQVALUE (number sequence code, scope type, scope id)
```

## Arguments

`number sequence code` : *String*

A text representing a code of the number sequence a new value of which is required.

`number sequence record ID`: *Int64*

An *Int64* value representing the record ID of a record in the **NumberSequenceTable** table containing the definition of the number sequence a new value of which is required.

`scope type` : *Enum value*

An *Enum value* of the **ERExpressionNumberSequenceScopeType** enumeration (**Shared**, **Legal entity**, or **Company**) defining the scope of the number sequence a new value of which is required.

`scope ID`: *String*

A *String* value identifying the scope based on the specified scope type.

## Returns

*String*

The result text value.

## Usage notes

For the **Shared** scope, specify an empty string as the **scope ID**.

For the **Company** and **Legal entity** scopes, specify the company code as the **scope ID**.

For the **Company** and **Legal entity** scopes, if you specify an empty string as the **scope ID**, the current company code is used.

When the syntax 1 is used, the number sequence is requested for the **Company** scope and the code of the company is supplied by the context the ER format is run under.

## Example 1

In your ER format, you define the **AskNumSeq** data source of the *User input parameter* type referring to the **Description** extended data type. Then, you
define the **NumSeq** data source of the *Calculated field* type containing the expression `NUMSEQVALUE (AskNumSeq)`. When the **NumSeq** data source is called, it returns the new generated value of a number sequence the code of which has been entered on the dialog page at runtime. The number sequence is requested for the **Company** scope. The code of the company is supplied by the context the ER format is run under.

## Example 2

You define the following data sources in your model mapping:

-   **LedgerParms** (*Table* type), which refers to the **LedgerParameters** table
-   **NumSeq** (*Calculated field* type), which contains the expression `NUMSEQVALUE ( LedgerParameters.'numRefJournalNum()'.NumberSequenceId)`

When the **NumSeq** data source is called, it returns the new generated value of the number sequence that has been configured in the **General ledger** parameters for the company that supplies the context that the ER format is run
under. This number sequence uniquely identifies journals and acts as a batch number that links the transactions together.

## Example 3

You define the following data sources in your model mapping:

-   **enumScope** (Dynamics 365 for Finance *enumeration type*), which refers to the **ERExpressionNumberSequenceScopeType** enumeration
-   **NumSeq** (**Calculated field** type), which contains the expression `NUMSEQVALUE ("Gene_1", enumScope.Company, "")`

When the **NumSeq** data source is called, it returns the new generated value of the **Gene_1** number sequence that has been configured for the company that supplies the context that the ER format is run under.

## Additional resources

[Other (business domain–specific) functions](er-functions-category-other.md)
