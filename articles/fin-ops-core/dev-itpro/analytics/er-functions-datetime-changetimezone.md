---
# required metadata

title: CHANGETIMEZONE ER function
description: This topic provides information about how the CHANGETIMEZONE Electronic reporting (ER) function is used.
author: NickSelin
ms.date: 09/01/2021
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ERDataModelDesigner, ERExpressionDesignerFormula, ERMappedFormatDesigner, ERModelMappingDesigner
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 58771
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2021-09-01
ms.dyn365.ops.version: AX 10.0.23

---

# CHANGETIMEZONE ER function

[!include [banner](../includes/banner.md)]

The `CHANGETIMEZONE` function returns a *[DateTime](er-formula-supported-data-types-primitive.md#datetime)* value in Coordinated Universal Time (Greenwich Mean Time \[GMT\]) that is converted from a given date/time in one time zone to a date/time in another time zone.

## Syntax

```vb
CHANGETIMEZONE (datetime, base time zone, target time zone)
```

## Arguments

`datetime`: *DateTime*

A date/time value in Coordinated Universal Time (Greenwich Mean Time \[GMT\]) time zone that represents the date/time to convert.

`base time zone`: *[String](er-formula-supported-data-types-primitive.md#string)*

The name of a time zone to which a given date/time is shifted before conversion.

`target time zone`: *String*

The name of a time zone to which a converted date/time is shifted during conversion.

## Return values

*DateTime*

The resulting date/time value in Coordinated Universal Time (Greenwich Mean Time \[GMT\]) time zone.

## Usage notes

To specify source and target time zones, you can use either time zone names that are [provided](https://data.iana.org/time-zones/releases/) by the [Internet Assigned Numbers Authority (IANA)](https://www.iana.org/) or that are [supported](https://docs.microsoft.com/windows-hardware/manufacture/desktop/default-time-zones) by Microsoft Windows.

The exception **Time zone '\<time zone name\>' does not exist** is thrown at runtime when the provided name is not found neither in the IANA list nor in the Windows registry. 

The conversion takes into account the UTC DST offset for time zones where daylight saving time (DST) is observed. The latest available information about the UTC DST offset is used during conversion.

## Example 1

You can configure the **DSX** data source of the **Calculated field** type containing the following expression:

```vb
CONCATENATE(
    DATETIMEFORMAT( DSY, "O"), 
    " -> ", 
    DATETIMEFORMAT( CHANGETIMEZONE(DSY, "E. Europe Standard Time", "Hawaiian Standard Time"), "O")
)
```

When you configure the expression of the **DSY** data source of the **Calculated field** type as `DATETIMEVALUE ("01-Jun-2021 12:55:00", "dd-MMM-yyyy HH:mm:ss", "EN")`, the **DSX** data source returns the text **2021-06-01T12:55:00.0000000+00:00 -> 2021-05-31T23:55:00.0000000+00:00** showing that the time difference between two provided time zones on June, 1st is greater than 24 hours. So, the converted date/time is one day earlier than the given date/time as the base time zone is ahead of the target one.

When you configure the expression of the **DSY** data source of the **Calculated field** type as `DATETIMEVALUE ("01-Dec-2021 12:55:00", "dd-MMM-yyyy HH:mm:ss", "EN")`, the **DSX** data source returns the text **2021-12-01T12:55:00.0000000+00:00 -> 2021-12-01T00:55:00.0000000+00:00** showing that the time difference between two provided time zones on December, 1st is less than 24 hours. So, the converted date/time is equal to the given date/time.

> [!NOTE]
> The same expression returns different variance between the provided and converted date/time values for the same pair of time zones as the different UTC DST offset is observed for provided time zones on a given date/time.

Note that the time zone names for Windows were used in this example.

## Example 2

You can configure the **DSX** data source of the **Calculated field** type containing the following expression:

```vb
CONCATENATE(
    DATETIMEFORMAT( DSY, "O"), 
    " -> ", 
    DATETIMEFORMAT( CHANGETIMEZONE(DSY, "Europe/Athens", "US/Hawaii"), "O")
)
```

When you configure the expression of the **DSY** data source of the **Calculated field** type as `DATETIMEVALUE ("01-Jun-2021 12:55:00", "dd-MMM-yyyy HH:mm:ss", "EN")`, the **DSX** data source returns the text **2021-06-01T12:55:00.0000000+00:00 -> 2021-05-31T23:55:00.0000000+00:00** showing that the time difference between two provided time zones on June, 1st is greater than 24 hours. So, the converted date/time is one day earlier than the given date/time as the base time zone is ahead of the target one.

When you configure the expression of the **DSY** data source of the **Calculated field** type as `DATETIMEVALUE ("01-Dec-2021 12:55:00", "dd-MMM-yyyy HH:mm:ss", "EN")`, the **DSX** data source returns the text **2021-12-01T12:55:00.0000000+00:00 -> 2021-12-01T00:55:00.0000000+00:00** showing that the time difference between two provided time zones on December, 1st is less than 24 hours. So, the converted date/time is equal to the given date/time.

Note that the IANA time zone names were used in this example.

## Example 3

You can configure the **DSX** data source of the **Calculated field** type containing the following expression:

```vb
CONCATENATE(
    DATETIMEFORMAT( DSY, "O"), 
    " -> ", 
    DATETIMEFORMAT( CHANGETIMEZONE(DSY, "US/Hawaii", "Europe/Athens"), "O")
)
```

When you configure the expression of the **DSY** data source of the **Calculated field** type as `DATETIMEVALUE ("01-Jun-2021 12:55:00", "dd-MMM-yyyy HH:mm:ss", "EN")`, the **DSX** data source returns the text **2021-06-01T12:55:00.0000000+00:00 -> 2021-06-02T01:55:00.0000000+00:00'** showing that the time difference between two provided time zones on June, 1st is greater than 24 hours. So, the converted date/time is one day later than the given date/time as the target time zone is ahead of the base one.

## Example 4

You can receive from an external source a date/time stamp as a text that contains no time zone information but you are aware of the time zone in which that source is operated. For example, it can be the time stamp **01/12/2021 12:55:00** from a service that is operated in Spain. To properly save such date/time value to database, you must do the following conversion:

- Configure the **DSY** data source of the **Calculated field** type to convert a date/time stamp from a text to the GMT date/time value:

    `DATETIMEVALUE ("01/12/2021 12:55:00", "dd/MM/yyyy HH:mm:ss", "ES")`

- Configure the **DSX** data source of the **Calculated field** type to shift to GMT the converted date/time value as the date/time of the time zone of the external source:

    `CHANGETIMEZONE(DSY, "Romance Standard Time", "GMT Standard Time")`

> [!NOTE]
> When you use the `CHANGETIMEZONE` function for date/time conversion, pay attention to the fact that any date/time value is stored in database as the GMT time zone value. For presenting date/time values on application pages, this value is transformed taking into account the time zone that is [set](../../fin-ops/organization-administration/tasks/set-users-preferred-time-zone.md) as a preferred zone for the currently logged application user.

## Additional resources

[Date and time functions](er-functions-category-datetime.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
