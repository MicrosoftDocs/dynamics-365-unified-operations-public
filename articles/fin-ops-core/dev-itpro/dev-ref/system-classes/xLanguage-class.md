---
title: xLanguage class
description: This topic describes the xLanguage class.
author: robinarh
manager: tonyafehr
ms.date: 06/25/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

audience: Developer
ms.reviewer: rhaertle
ms.search.scope: Operations
ms.search.region: Global
ms.author: rhaertle
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Class xLanguage

[!include [banner](../../includes/banner.md)]

```xpp
class xLanguage extends Object
```

The xLanguage class provides access to a list of language IDs and information about existing label files.

## Remarks

ISO 639 defines the names of languages, such as "en" for English. Microsoft has listed a set of language codes, such "en-us" for English (United States). These language codes are referred to as Language IDs. "ko-jo" is used for Korean (Johab). In the Microsoft list, "ko" is both Korean and Korean (Johab). "no-ny" is used for for Norwegian (Nynorsk). In the Microsoft list, "no" is both Norwegian (Bokmal) and Norwegian (Nynorsk). "es-tr" is used to represent Spanish (Spain - Traditional Sort). In the Microsoft list, "es" is both Spanish (Spain - Modern Sort) and Spanish (Spain - Traditional Sort). A language name in the following format, such as "English (United States)", is referred to as the description.

## Examples

The following example prints all the language IDs from the Microsoft list and a list of existing label files.

```xpp
static void aaaTestLanguage(args a) 
{ 
    int i; 
    int cnt; 
    str languageID; 
    str description; 
    str shortName; 
    cnt = xlanguage::languageCount(); 
    for (i = 0; i<=cnt; i++) 
    { 
        languageID =xLanguage::index2languageID(i); 
        print "Language ", i, ":", languageID, ":"; 
    } 
    cnt = xLanguage::labelFileCount(); 
    for (i = 0; i<=cnt; i++) 
    { 
        shortName =xLanguage::labelFileNumber2LanguageID(i); 
        languageID =xLanguage::index2languageID(i); 
        description = xLanguage::languageID2Description(languageID); 
        print i, ":", shortName, ":", description; 
    } 
    pause; 
}
```

## Methods

| Method                                                     | Description                                                                                                 |
|------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| ::public static str index2languageID(int number)           | Retrieves the language ID (for example, "en-us") of the specified language.                                 |
| ::public static int labelFileCount()                       | Returns the number of label files.                                                                          |
| ::public static str labelFileNumber2LanguageID(int number) |                                                                                                             |
| ::public static int languageCount()                        |                                                                                                             |
| ::public static str languageID2Description(str languageID) | Returns the name of the specified language (for example, "English (United States)"), given the language ID. |
| ::public static int languageID2LCID(str languageID)        |                                                                                                             |
| ::public static str lcid2languageID(int lcid)              |                                                                                                             |

## Method index2languageID

Retrieves the language ID (for example, "en-us") of the specified language.

```xpp
public static str index2languageID(int number)
```

### Parameters - index2languageID

number  
A number between 1 and the return value of the languageCount method.

### Return Value - index2languageID

The language ID.

## Method labelFileCount

Returns the number of label files.

```xpp
public static int labelFileCount()
```

### Return Value - labelFileCount

The number of label files (that is, the number of files that have names in the form ax???\*.ald).

## Method labelFileNumber2LanguageID

```xpp
public static str labelFileNumber2LanguageID(int number)
```

### Parameters - labelFileNumber2LanguageID

number  

### Return Value - labelFileNumber2LanguageID

## Method languageCount

```xpp
public static int languageCount()
```

### Return Value - languageCount

## Method languageID2Description

Returns the name of the specified language (for example, "English (United States)"), given the language ID.

```xpp
public static str languageID2Description(str languageID)
```

### Parameters - languageID2Description

languageID  
The ID of the language (for example, "en-us").

### Return Value - languageID2Description

A string that contains the description of a language.

## Method languageID2LCID

```xpp
public static int languageID2LCID(str languageID)
```

### Parameters - languageID2LCID

languageID  

### Return Value - languageID2LCID

## Method lcid2languageID

```xpp
public static str lcid2languageID(int lcid)
```

### Parameters - lcid2languageID

lcid  

### Return Value - lcid2languageID

