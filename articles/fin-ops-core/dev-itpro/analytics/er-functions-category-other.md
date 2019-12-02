---
# required metadata

title: List of ER functions of the business domain–specific category
description: This topic explains what business domain–specific functions are supported in ER
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

# Other (business domain–specific) functions

[!include [banner](../includes/banner.md)]

Electronic reporting (ER) domain–specific functions can be used to perform Dynamics 365 Finance implementation specific calculations and data access requests. You can find a summary of such functions below in this article.

## List of supported functions

| **Function**  | **Description**  |
|---------------|------------------|
| [CH_Bank_Mod_10](er-functions-other-chbankmode10.md)       | Returns a *String* value of a creditor reference as an MOD10 expression, based on the digits of the specified invoice number.                                                      |
| [CN_GBT_AdditionalDimensionID](er-functions-other-cngbtadditionaldimensionid.md)           | Returns a *String* value of a single financial dimension ID that is taken from the specified string of all dimensions that are represented as IDs that are separated by commas.         |
| [ConvertCurrency](er-functions-other-convertcurrency.md)   | Returns a *Real* value as the result of the conversion of the specified monetary amount from the specified source currency to the specified target currency by using the settings of the specified company on the specified date.                     |
| [CurCredRef](er-functions-other-curcredref.md)             | Returns a *String* value of a creditor reference, based on the digits of the specified invoice number.                      |
| [FA_Balance](er-functions-other-fabalance.md)              | Returns a *Container (record)* of data of the fixed asset balance for the specified fixed asset item, value model code, reporting year and reporting date.                           |
| [FA_Sum](er-functions-other-fasum.md)                      | Returns a *Container (record)* of data of the fixed asset amounts for the specified fixed asset item, value model code, and period of dates.                                         |
| [GetCurrentCompany](er-functions-other-getcurrentcompany.md)| Returns a *String* value as representation of the code for the legal entity (company) that a user is currently signed in to.                                                          |
| [ISOCredRef](er-functions-other-isocredref.md)             | Returns a *String* value of an International Organization for Standardization (ISO) creditor reference, based on the digits and alphabetic symbols of the specified invoice number.      |
| [IsValidCharacterISO7064](er-functions-other-isvalidchariso7064.md)                   | Returns a *Boolean* value **TRUE** when the specified string represents a valid international bank account number (IBAN). Otherwise, returns **FALSE**.                                |
| [Mod_97](er-functions-other-mod97.md)                     | Returns a *String* value of a creditor reference as a MOD97 expression, based on the digits of the specified invoice number.                                                      |
| [NumSeqValue](er-functions-other-numseqvalue.md)           | Returns a *String* value of the new generated value of a number sequence, based on the specified number sequence, the scope, and (as the scope ID) the code of the company that is supplied by the context the ER format is run under.          |
| [RoundAmount](er-functions-other-roundamount.md)           | Returns a *Real* value as the result of rounding of the specified amount to the specified number of decimal places according to the specified rounding rule.                    |
| [TableName2ID](er-functions-other-tablename2id.md)         | Returns an *Integer* value as the numeric representation of a table ID for the specified table name.                       |

## Additional resources

[Electronic Reporting overview](general-electronic-reporting.md)

[Formula designer in Electronic reporting](general-electronic-reporting-formula-designer.md)

[Electronic reporting formula language](er-formula-language.md)
