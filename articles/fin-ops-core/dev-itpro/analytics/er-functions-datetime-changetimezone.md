---
title: CHANGETIMEZONE ER function
description: This article provides information about how the CHANGETIMEZONE Electronic reporting (ER) function is used.
author: kfend
ms.date: 09/09/2021
ms.prod: 
ms.technology: 
audience: Application User, IT Pro
ms.reviewer: kfend
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2021-09-01
ms.dyn365.ops.version: AX 10.0.23
ms.assetid: 
ms.search.form: ERDataModelDesigner, ERExpressionDesignerFormula, ERMappedFormatDesigner, ERModelMappingDesigner
---

# CHANGETIMEZONE ER function

[!include [banner](../includes/banner.md)]

The `CHANGETIMEZONE` function returns a *[DateTime](er-formula-supported-data-types-primitive.md#datetime)* value in Coordinated Universal Time (Greenwich Mean Time \[GMT\]) that is converted from a given date/time value in one time zone to a date/time value in another time zone.

## Syntax

```vb
CHANGETIMEZONE (datetime, base time zone, target time zone)
```

## Arguments

`datetime`: *DateTime*

A date/time value in the Coordinated Universal Time time zone that represents the date/time value to convert.

`base time zone`: *[String](er-formula-supported-data-types-primitive.md#string)*

The name of the time zone that a given date/time value is shifted to before conversion.

`target time zone`: *String*

The name of the time zone that a converted date/time value is shifted to during conversion.

## Return values

*DateTime*

The resulting date/time value in the Coordinated Universal Time time zone.

## Usage notes

To specify source and target time zones, you can use time zone names that are [provided](https://data.iana.org/time-zones/releases/) by the [Internet Assigned Numbers Authority (IANA)](https://www.iana.org/) or that are [supported](/windows-hardware/manufacture/desktop/default-time-zones) by Microsoft Windows.

At runtime, the exception "Time zone '\<time zone name\>' does not exist" is thrown if the provided name isn't found in the IANA list or in the Windows registry.

For time zones where daylight saving time is observed, the conversion considers the Coordinated Universal Time daylight saving time offset. The latest available information about this offset is used during conversion.

## Example 1

In this example, the time zone names for Windows are used.

You configure the **DSX** data source of the **Calculated field** type. It contains the following expression.

```vb
CONCATENATE(
    DATETIMEFORMAT( DSY, "O"), 
    " -> ", 
    DATETIMEFORMAT( CHANGETIMEZONE(DSY, "E. Europe Standard Time", "Hawaiian Standard Time"), "O")
)
```

If you configure the expression of the **DSY** data source of the **Calculated field** type as `DATETIMEVALUE ("01-Jun-2021 12:55:00", "dd-MMM-yyyy HH:mm:ss", "EN")`, the **DSX** data source returns the text **2021-06-01T12:55:00.0000000+00:00 -> 2021-05-31T23:55:00.0000000+00:00**. This text shows that the time difference between the two provided time zones on June 1 is more than 24 hours. Therefore, the converted date/time value is one day earlier than the given date/time value, because the base time zone is ahead of the target time zone.

If you configure the expression of the **DSY** data source of the **Calculated field** type as `DATETIMEVALUE ("01-Dec-2021 12:55:00", "dd-MMM-yyyy HH:mm:ss", "EN")`, the **DSX** data source returns the text **2021-12-01T12:55:00.0000000+00:00 -> 2021-12-01T00:55:00.0000000+00:00**. This text shows that the time difference between the two provided time zones on December 1 is less than 24 hours. Therefore, the converted date/time value equals the given date/time value.

> [!NOTE]
> The same expression returns a different variance between the provided and converted date/time values for the same pair of time zones because a different Coordinated Universal Time daylight saving time offset is observed for the provided time zones on a given date/time.

## Example 2

In this example, the IANA time zone names are used.

You configure the **DSX** data source of the **Calculated field** type. It contains the following expression.

```vb
CONCATENATE(
    DATETIMEFORMAT( DSY, "O"), 
    " -> ", 
    DATETIMEFORMAT( CHANGETIMEZONE(DSY, "Europe/Athens", "US/Hawaii"), "O")
)
```

If you configure the expression of the **DSY** data source of the **Calculated field** type as `DATETIMEVALUE ("01-Jun-2021 12:55:00", "dd-MMM-yyyy HH:mm:ss", "EN")`, the **DSX** data source returns the text **2021-06-01T12:55:00.0000000+00:00 -> 2021-05-31T23:55:00.0000000+00:00**. This text shows that the time difference between the two provided time zones on June 1 is more than 24 hours. Therefore, the converted date/time value is one day earlier than the given date/time value, because the base time zone is ahead of the target time zone.

If you configure the expression of the **DSY** data source of the **Calculated field** type as `DATETIMEVALUE ("01-Dec-2021 12:55:00", "dd-MMM-yyyy HH:mm:ss", "EN")`, the **DSX** data source returns the text **2021-12-01T12:55:00.0000000+00:00 -> 2021-12-01T00:55:00.0000000+00:00**. This text shows that the time difference between the two provided time zones on December 1 is less than 24 hours. Therefore, the converted date/time value equals the given date/time value.

## Example 3

You configure the **DSX** data source of the **Calculated field** type. It contains the following expression.

```vb
CONCATENATE(
    DATETIMEFORMAT( DSY, "O"), 
    " -> ", 
    DATETIMEFORMAT( CHANGETIMEZONE(DSY, "US/Hawaii", "Europe/Athens"), "O")
)
```

If you configure the expression of the **DSY** data source of the **Calculated field** type as `DATETIMEVALUE ("01-Jun-2021 12:55:00", "dd-MMM-yyyy HH:mm:ss", "EN")`, the **DSX** data source returns the text **2021-06-01T12:55:00.0000000+00:00 -> 2021-06-02T01:55:00.0000000+00:00'**. This text shows that the time difference between the two provided time zones on June 1 is more than 24 hours. Therefore, the converted date/time value is one day later than the given date/time value, because the target time zone is ahead of the base time zone.

## Example 4

You might receive a date/time stamp from an external source as text that contains no time zone information. However, you might know the time zone that the source is operated in. For example, you receive the date/time stamp **01/12/2021 12:55:00** from a service that is operated in Spain. To correctly save this date/time value to the database, complete the following conversion:

- Configure the **DSY** data source of the **Calculated field** type to convert a date/time stamp from text to the Coordinated Universal Time date/time value.

    `DATETIMEVALUE ("01/12/2021 12:55:00", "dd/MM/yyyy HH:mm:ss", "ES")`

- Configure the **DSX** data source of the **Calculated field** type to shift the converted date/time value to Coordinated Universal Time as the date/time value of the time zone of the external source.

    `CHANGETIMEZONE(DSY, "Romance Standard Time", "GMT Standard Time")`

> [!NOTE]
> When you use the `CHANGETIMEZONE` function for date/time conversion, be aware that any date/time value is stored in the database as the value in the Coordinated Universal Time time zone. Before this value can be presented on application pages, it's transformed. The transformation considers the time zone that is [set](../../fin-ops/organization-administration/tasks/set-users-preferred-time-zone.md) as a preferred zone for the currently signed-in application user.

## Additional resources

[Date and time functions](er-functions-category-datetime.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
