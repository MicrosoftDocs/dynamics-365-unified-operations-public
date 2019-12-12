---
# required metadata

title: LISTOFFIELDS ER function
description: This topic provides information about how the LISTOFFIELDS ER function is used.
author: NickSelin
manager: kfend
ms.date: 12/12/2019
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

# <a name="LISTOFFIELDS">LISTOFFIELDS Function</a>

[!include [banner](../includes/banner.md)]

The `LISTOFFIELDS` function returns a *Record list* that is created based on the structure of a given argument of one of the following types: *Enumeration* or *Container (record)*.

## Syntax 1

```
LISTOFFIELDS (path)
```

## Syntax 2

```
LISTOFFIELDS (path, language)
```

## Arguments

`path` : Data source reference

A valid reference path to a data source of one of the following data types:

- *Model enumeration*
- *Format enumeration*
- *Application enumeration*
- *Container (record)*

`language` : *String*

A text representing a language code.

## Returns

*Record list*

The result list of records.

## Usage notes

The list that is created consists of records having the following fields of the following data types:

- Name: *String*
- Label: *String*
- Description: *String*
- IsTranslated: *Boolean*

When the first argument refers to a data source of the *Container (Record)* type, for every field of the referred container record, a new record is added to the list that is created. The **Name** field of every created record returns the name of the field of the referred container record for which the current record has been created.

When the first argument refers to a data source of one of *Enumerations* type, for every enumeration value of the referred enumeration, a new record is added to the list that is created. The **Name** field of every created record returns the value of the referred enum for which the current record has been created. The **Description** field of every created record returns the description of the referred enum for which the current record has been created. The **Label** field of every created record returns the label of the referred enum for which the current record has been created.

At runtime, when the syntax 1 is used, the **Label** and **Description** fields must return values that are based on the running ER format's language settings:

- When the labels and descriptions for requested language are available, the **Label** and **Description** fields return values that are based on this language and the **IsTranslated** field returns **True**.
- When the labels and descriptions for the requested language are not available, the **Label** and **Description** fields return values that are based on the default **EN-US** language and the **IsTranslated** field returns **False**.

At runtime, when the syntax 2 is used, the **Label** and **Description** fields must return values that are based on the language that is defined as the second argument of the called function:

- When the labels and descriptions for requested language are available, the **Label** and **Description** fields return values that are based on this language and the **IsTranslated** field returns **True**.
- When the labels and descriptions for requested language are not available, the **Label** and **Description** fields return values that are based on the **EN-US** language and the **IsTranslated** field returns **False**.

## Example 1

In the following illustration, an enumeration is introduced in an ER data model.

<a href="./media/ger-listoffields-function-model-enumeration.png"><img src="./media/ger-listoffields-function-model-enumeration-e1474545790761.png" alt="Enumeration in a model" class="alignnone wp-image-1203943 size-full" width="514" height="155" /></a>

The following illustration shows these details:

-   The model enumeration is inserted into a report as a data source.
-   An ER expression uses the model enumeration as a parameter of the `LISTOFFIELDS` function.
-   A data source of the *Record list* type is inserted into a report by using the ER expression that is created.

<a href="./media/ger-listoffields-function-in-format-expression.png"><img src="./media/ger-listoffields-function-in-format-expression-e1474546110395.png" alt="Format" class="alignnone wp-image-1204033 size-full" width="549" height="318" /></a>

The following example shows the ER format elements that are bound to the data source of the *Record list* type that was created by using the `LISTOFFIELDS` function.

<a href="./media/ger-listoffields-function-format-design.png"><img src="./media/ger-listoffields-function-format-design.png" alt="Format design" class="alignnone size-full wp-image-1204043" width="466" height="221" /></a>

The following illustration shows the result when the designed format is run.

<a href="./media/ger-listoffields-function-format-output.png"><img src="./media/ger-listoffields-function-format-output.png" alt="Format output" class="alignnone size-full wp-image-1204053" width="585" height="158" /></a>

> [!NOTE] 
> Based on the language settings of the parent **FILE** and **FOLDER** format elements, translated text for labels and descriptions is entered in the output of the ER format.

## Example 2

For example, you use the `Calculated field` data source type to configure the **enumType_de** and **enumType_deCH** data sources for the <strong>enumType</strong> data model enumeration.

-   **enumType_de** = `LISTOFFIELDS (enumType, "de")`
-   **enumType_deCH** = `LISTOFFIELDS (enumType, "de-CH")`

In this case, you can use the following expression to get the label of the enumeration value in Swiss German, if this translation is available. If the Swiss German translation isn't available, the label is in German.

`
IF (NOT (enumType_deCH.IsTranslated), enumType_de.Label, enumType_deCH.Label)
`

## Additional resources

[List functions](er-functions-category-list.md)
