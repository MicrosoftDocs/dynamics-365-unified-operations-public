---
title: List of ER functions in the business domain–specific category
description: This article provides information about the business domain–specific functions that are supported in Electronic reporting (ER).
author: kfend
ms.date: 12/12/2019
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

# List of ER functions in the business domain–specific category

[!include [banner](../includes/banner.md)]

Electronic reporting (ER) domain-specific functions can be used to perform calculations and data access requests that are specific to the implementation of Microsoft Dynamics 365 Finance. This article provides a summary of these functions.

## List of supported functions

| Function| Description |
|---------|-------------|
| [CH_Bank_Mod_10](er-functions-other-chbankmode10.md) | This function returns a *String* value that represents a creditor reference as an MOD10 expression, based on the digits of the specified invoice number. |
| [CN_GBT_AdditionalDimensionID](er-functions-other-cngbtadditionaldimensionid.md) | This function returns a *String* value that represents a single financial dimension ID that is taken from the specified string. The specified string presents all dimensions as a comma-separated list of IDs. |
| [ConvertCurrency](er-functions-other-convertcurrency.md) | This function returns a *Real* value that represents the result of converting the specified monetary amount from the specified source currency to the specified target currency by using the settings of the specified company on the specified date. |
| [CurCredRef](er-functions-other-curcredref.md) | This function returns a *String* value that represents a creditor reference, based on the digits of the specified invoice number. |
| [FA_Balance](er-functions-other-fabalance.md) | This function returns a *Container (record)* value that consists of data for the fixed asset balance for the specified fixed asset item, value model code, reporting year, and reporting date. |
| [FA_Sum](er-functions-other-fasum.md) | This function returns a *Container (record)* value that consists of data for the fixed asset amounts for the specified fixed asset item, value model code, and period of dates. |
| [GetCurrentCompany](er-functions-other-getcurrentcompany.md) | This function returns a *String* value that represents the code for the legal entity (company) that a user is currently signed in to. |
| [ISOCredRef](er-functions-other-isocredref.md) | This function returns a *String* value that represents an International Organization for Standardization (ISO) creditor reference, based on the digits and alphabetic symbols of the specified invoice number. |
| [IsValidCharacterISO7064](er-functions-other-isvalidchariso7064.md) | This function returns a *Boolean* value of **TRUE** if the specified string represents a valid international bank account number (IBAN). Otherwise, it returns a *Boolean* value of **FALSE**. |
| [Mod_97](er-functions-other-mod97.md) | This function returns a *String* value that represents a creditor reference as a MOD97 expression, based on the digits of the specified invoice number. |
| [NumSeqValue](er-functions-other-numseqvalue.md) | This function returns a *String* value that represents the new generated value of a number sequence, based on the specified number sequence, scope, and scope ID. The scope ID equals the company code that is supplied by the context that the ER format is run under. |
| [RoundAmount](er-functions-other-roundamount.md) | This function returns a *Real* value that represents the result of rounding the specified amount to the specified number of decimal places according to the specified rounding rule. |
| [TableName2ID](er-functions-other-tablename2id.md) | This function returns a numeric representation of the table ID for the specified table name as an *Integer* value. |

## Additional resources

[Electronic Reporting overview](general-electronic-reporting.md)

[Formula designer in Electronic reporting](general-electronic-reporting-formula-designer.md)

[Electronic reporting formula language](er-formula-language.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
