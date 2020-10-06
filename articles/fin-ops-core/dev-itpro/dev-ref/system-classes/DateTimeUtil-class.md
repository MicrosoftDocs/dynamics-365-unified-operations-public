---
title: DateTimeUtil class
description: This topic describes the DateTimeUtil class.
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

# Class DateTimeUtil

[!include [banner](../../includes/banner.md)]

```xpp
class DateTimeUtil extends Object
```

The DateTimeUtil class can be used to convert or modify utcdatetime and Timezone values.

## Remarks

## Examples

## Methods

| Method                                                                                                                                                                            | Description                                                                                                                                                    |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ::public static DateTime addDays(DateTime t, int value)                                                                                                                           | Adds the specified number of days to a utcdatetime value.                                                                                                      |
| ::public static DateTime addHours(DateTime t, int value)                                                                                                                          | Adds the specified number of hours to a utcdatetime value.                                                                                                     |
| ::public static DateTime addMinutes(DateTime t, int value)                                                                                                                        | Adds the specified number of minutes to a utcdatetime value.                                                                                                   |
| ::public static DateTime addMonths(DateTime t, int value)                                                                                                                         | Adds the specified number of months to a utcdatetime value.                                                                                                    |
| ::public static DateTime addSeconds(DateTime t, Int64 value)                                                                                                                      | Adds the specified number of seconds to a utcdatetime value.                                                                                                   |
| ::public static DateTime addYears(DateTime t, int value)                                                                                                                          | Adds the specified number of years to a utcdatetime value.                                                                                                     |
| ::public static DateTime anyToDateTime(AnyType value)                                                                                                                             | Converts an anytype object to a utcdatetime value.                                                                                                             |
| ::public static DateTime applyTimeZoneOffset(DateTime t, Timezone tz)                                                                                                             | Retrieves a utcdatetime value that is offset from the specified utcdatetime value by the amount that is indicated by the specified Timezone enumeration value. |
| ::public static str applyTimeZoneOffsetFilter(QueryFilter filter)                                                                                                                 | Applies the time zone offset to the filter.                                                                                                                    |
| ::public static str applyTimeZoneOffsetRange(QueryBuildRange range)                                                                                                               | Applies the time zone offset to the range.                                                                                                                     |
| ::public static Date date(DateTime t)                                                                                                                                             | Converts the specified utcdatetime value to a date type.                                                                                                       |
| ::public static int day(DateTime t)                                                                                                                                               | Retrieves the day of the month that is specified by a utcdatetime value.                                                                                       |
| ::public static Timezone getClientMachineTimeZone()                                                                                                                               | Gets the Timezone enumeration value on the client computer.                                                                                                    |
| ::public static Timezone getCompanyTimeZone()                                                                                                                                     | Gets the Timezone value that is set for the current legal entity.                                                                                              |
| ::public static Int64 getDifference(DateTime t1, DateTime t2)                                                                                                                     | Gets the number of seconds between two specified utcdatetime values.                                                                                           |
| ::public static Timezone getOriginatingTimeZone(DateTime t)                                                                                                                       | Gets the originating Timezone enumeration value of the specified utcdatetime value.                                                                            |
| ::public static Date getSystemDate(Timezone tz)                                                                                                                                   |                                                                                                                                                                |
| ::public static DateTime getSystemDateTime()                                                                                                                                      | Gets the current system time as a utcdatetime value.                                                                                                           |
| ::public static TimeOfDay getTimeNow(Timezone tz)                                                                                                                                 |                                                                                                                                                                |
| ::public static TimeZoneId getTimeZoneId(Timezone tz)                                                                                                                             |                                                                                                                                                                |
| ::public static int getTimeZoneOffset(DateTime t, Timezone tz)                                                                                                                    | Gets the offset of the specified utcdatetime value to UTC by using the information in a Timezone enumeration value.                                            |
| ::public static int getTimeZoneRule(DateTime t)                                                                                                                                   | Returns the time zone rule that takes effect on the given date.                                                                                                |
| ::public static Date getToday(Timezone tz)                                                                                                                                        |                                                                                                                                                                |
| ::public static PreferredCalendar getUserPreferredCalendar()                                                                                                                      | Gets the PreferredCalendar enumeration value for the current user.                                                                                             |
| ::public static Timezone getUserPreferredTimeZone()                                                                                                                               | Gets the PreferredTimezone enumeration value for the current user.                                                                                             |
| ::public static int hour(DateTime t)                                                                                                                                              | Retrieves the hour of the day that is specified by a utcdatetime value.                                                                                        |
| ::public static DateTime maxValue()                                                                                                                                               | Retrieves the maximum value that is allowed for a variable of the utcdatetime type.                                                                            |
| ::public static int minute(DateTime t)                                                                                                                                            | Retrieves the minute in the hour that is specified by a utcdatetime value.                                                                                     |
| ::public static DateTime minValue()                                                                                                                                               | Retrieves the minimum value that is allowed for a variable of the utcdatetime type.                                                                            |
| ::public static int month(DateTime t)                                                                                                                                             | Retrieves the month in the year that is specified by a utcdatetime value.                                                                                      |
| ::public static DateTime newDateTime(Date date, TimeOfDay time, \[Timezone tzOffsetToRemove\])                                                                                    | Creates a new utcdatetime value by using the specified date and timeOfDay values.                                                                              |
| ::public static DateTime parse(str s)                                                                                                                                             | Creates a new utcdatetime value from the specified string.                                                                                                     |
| ::public static container populateTimeZoneInfo(int year, Timezone tz)                                                                                                             | Retrieves start and end dates and time bias.                                                                                                                   |
| ::public static DateTime removeTimeZoneOffset(DateTime t, Timezone tz)                                                                                                            | Removes the offset that is indicated by a Timezone enumeration value from the specified utcdatetime value.                                                     |
| ::public static str removeTimeZoneOffsetFilter(QueryFilter filter)                                                                                                                | Removes the time zone offset from the filter.                                                                                                                  |
| ::public static str removeTimeZoneOffsetRange(QueryBuildRange range)                                                                                                              | Removes the time zone offset from the range.                                                                                                                   |
| ::public static int second(DateTime t)                                                                                                                                            | Retrieves the seconds in a minute that is specified by a utcdatetime value.                                                                                    |
| ::public static TimeOfDay time(DateTime t)                                                                                                                                        | Retrieves the number of seconds that have elapsed since midnight as a timeOfDay value from the specified utcdatetime value.                                    |
| ::public static str toFormattedStr(DateTime t, int sequence, int day, int separator1, int month, int separator2, int year, int timeSeparator1, int timeSeparator2, \[int flags\]) |                                                                                                                                                                |
| ::public static str toStr(DateTime t)                                                                                                                                             | Converts a utcdatetime value to a string in the following format: YYYY-MM-DDThh:mm:ss, where T is a character literal.                                         |
| ::public static DateTime utcNow()                                                                                                                                                 | Retrieves a utcdatetime value that indicates the current system time.                                                                                          |
| ::public static int year(DateTime t)                                                                                                                                              | Retrieves the year that is specified by a utcdatetime value.                                                                                                   |
| ::public static void setSystemDateTime(DateTime t)                                                                                                                                | Sets the date and time of the system to the specified utcdatetime value.                                                                                       |
| ::public static void setCompanyTimeZone(Timezone tz, \[boolean persist\])                                                                                                         | Sets the Timezone enumeration value that is used by the current company.                                                                                       |
| ::public static void setUserPreferredCalendar(PreferredCalendar calendar)                                                                                                         | Sets the value of the PreferredCalendar enumeration type of the current user for the current session.                                                          |
| ::public static void setUserPreferredTimeZone(Timezone tz, \[boolean persist\])                                                                                                   | Sets the preferred time zone of the user to the specified Timezone enumeration value.                                                                          |
| private void new()                                                                                                                                                                | Initializes a new instance of the DateTimeUtil class.                                                                                                          |

## Method addDays

Adds the specified number of days to a utcdatetime value.

```xpp
public static DateTime addDays(DateTime t, int value)
```

### Parameters - addDays

t  
The number of days to add.

<!-- -->

value  
The number of days to add.

### Return Value - addDays

A new utcdatetime value.

### Remarks - addDays

If the value of the value parameter is negative, days will be subtracted.

## Method addHours

Adds the specified number of hours to a utcdatetime value.

```xpp
public static DateTime addHours(DateTime t, int value)
```

### Parameters - addHours

t  
The number of hours to add.

<!-- -->

value  
The number of hours to add.

### Return Value - addHours

A new utcdatetime value.

### Remarks - addHours

If the value of the value parameter is negative, hours will be subtracted.

## Method addMinutes

Adds the specified number of minutes to a utcdatetime value.

```xpp
public static DateTime addMinutes(DateTime t, int value)
```

### Parameters - addMinutes

t  
The number of minutes to add.

<!-- -->

value  
The number of minutes to add.

### Return Value - addMinutes

A new utcdatetime value.

### Remarks - addMinutes

If the value of the value parameter is negative, minutes will be subtracted.

## Method addMonths

Adds the specified number of months to a utcdatetime value.

```xpp
public static DateTime addMonths(DateTime t, int value)
```

### Parameters - addMonths

t  
The number of months to add.

<!-- -->

value  
The number of months to add.

### Return Value - addMonths

A new utcdatetime value.

### Remarks - addMonths

If the value of the value parameter is negative, months will be subtracted.

## Method addSeconds

Adds the specified number of seconds to a utcdatetime value.

```xpp
public static DateTime addSeconds(DateTime t, Int64 value)
```

### Parameters - addSeconds

t  
The number of seconds to add.

<!-- -->

value  
The number of seconds to add.

### Return Value - addSeconds

A new utcdatetime value.

### Remarks - addSeconds

If the value of the value parameter is negative, seconds will be subtracted.

## Method addYears

Adds the specified number of years to a utcdatetime value.

```xpp
public static DateTime addYears(DateTime t, int value)
```

### Parameters - addYears

t  
The number of years to add.

<!-- -->

value  
The number of years to add.

### Return Value - addYears

A new utcdatetime value.

### Remarks - addYears

If the value of the value parameter is negative, years will be subtracted.

## Method anyToDateTime

Converts an anytype object to a utcdatetime value.

```xpp
public static DateTime anyToDateTime(AnyType value)
```

### Parameters - anyToDateTime

value  
The object to convert.

### Return Value - anyToDateTime

A new utcdatetime value.

### Remarks - anyToDateTime

The following example string shows the format of a date-time string that this anyToDateTime method can correctly convert: "2009-01-28T13:44:55". The output of the DateTimeUtil::utcNow method is valid input into the anyToDateTime method.

## Method applyTimeZoneOffset

Retrieves a utcdatetime value that is offset from the specified utcdatetime value by the amount that is indicated by the specified Timezone enumeration value.

```xpp
public static DateTime applyTimeZoneOffset(DateTime t, Timezone tz)
```

### Parameters - applyTimeZoneOffset

t  
A Timezone enumeration value that indicates the new offset to use.

<!-- -->

tz  
A Timezone enumeration value that indicates the new offset to use.

### Return Value - applyTimeZoneOffset

A new utcdatetime value.

## Method applyTimeZoneOffsetFilter

Applies the time zone offset to the filter.

```xpp
public static str applyTimeZoneOffsetFilter(QueryFilter filter)
```

### Parameters - applyTimeZoneOffsetFilter

filter  

### Return Value - applyTimeZoneOffsetFilter

The new date/time range value.

## Method applyTimeZoneOffsetRange

Applies the time zone offset to the range.

```xpp
public static str applyTimeZoneOffsetRange(QueryBuildRange range)
```

### Parameters - applyTimeZoneOffsetRange

range  

### Return Value - applyTimeZoneOffsetRange

The new date/time range value.

## Method date

Converts the specified utcdatetime value to a date type.

```xpp
public static Date date(DateTime t)
```

### Parameters - date

t  
The utcdatetime value to convert.

### Return Value - date

A date value.

## Method day

Retrieves the day of the month that is specified by a utcdatetime value.

```xpp
public static int day(DateTime t)
```

### Parameters - day

t  
A utcdatetime value for which to retrieve the value of the day component.

### Return Value - day

The day of the month of the specified utcdatetime value.

## Method getClientMachineTimeZone

Gets the Timezone enumeration value on the client computer.

```xpp
public static Timezone getClientMachineTimeZone()
```

### Return Value - getClientMachineTimeZone

The Timezone enumeration value on the client computer.

## Method getCompanyTimeZone

Gets the Timezone value that is set for the current legal entity.

```xpp
public static Timezone getCompanyTimeZone()
```

### Return Value - getCompanyTimeZone

The Timezone value that is set for the current legal entity.

## Method getDifference

Gets the number of seconds between two specified utcdatetime values.

```xpp
public static Int64 getDifference(DateTime t1, DateTime t2)
```

### Parameters - getDifference

t1  
The second utcdatetime value.

<!-- -->

t2  
The second utcdatetime value.

### Return Value - getDifference

The number of seconds between the two specified utcdatetime values.

## Method getOriginatingTimeZone

Gets the originating Timezone enumeration value of the specified utcdatetime value.

```xpp
public static Timezone getOriginatingTimeZone(DateTime t)
```

### Parameters - getOriginatingTimeZone

t  
The utcdatetime value for which to retrieve the time zone.

### Return Value - getOriginatingTimeZone

The Timezone enumeration value of the specified utcdatetime value.

## Method getSystemDate

```xpp
public static Date getSystemDate(Timezone tz)
```

### Parameters - getSystemDate

tz  

### Return Value - getSystemDate

## Method getSystemDateTime

Gets the current system time as a utcdatetime value.

```xpp
public static DateTime getSystemDateTime()
```

### Return Value - getSystemDateTime

The current system time as a utcdatetime value.

### Remarks - getSystemDateTime

If the system time has a fixed value, it will be returned. Otherwise, the current date and time from the local computer will be returned.

## Method getTimeNow

```xpp
public static TimeOfDay getTimeNow(Timezone tz)
```

### Parameters - getTimeNow

tz  

### Return Value - getTimeNow

## Method getTimeZoneId

```xpp
public static TimeZoneId getTimeZoneId(Timezone tz)
```

### Parameters - getTimeZoneId

tz  

### Return Value - getTimeZoneId

## Method getTimeZoneOffset

Gets the offset of the specified utcdatetime value to UTC by using the information in a Timezone enumeration value.

```xpp
public static int getTimeZoneOffset(DateTime t, Timezone tz)
```

### Parameters - getTimeZoneOffset

t  
A Timezone enumeration value that indicates the time zone of the t parameter.

<!-- -->

tz  
A Timezone enumeration value that indicates the time zone of the t parameter.

### Return Value - getTimeZoneOffset

An integer that indicates the offset of the specified utcdatetime value to UTC.

## Method getTimeZoneRule

Returns the time zone rule that takes effect on the given date.

```xpp
public static int getTimeZoneRule(DateTime t)
```

### Parameters - getTimeZoneRule

t  

### Return Value - getTimeZoneRule

The time zone rule for the given date.

## Method getToday

```xpp
public static Date getToday(Timezone tz)
```

### Parameters - getToday

tz  

### Return Value - getToday

## Method getUserPreferredCalendar

Gets the PreferredCalendar enumeration value for the current user.

```xpp
public static PreferredCalendar getUserPreferredCalendar()
```

### Return Value - getUserPreferredCalendar

The PreferredCalendar enumeration value for the current user.

## Method getUserPreferredTimeZone

Gets the PreferredTimezone enumeration value for the current user.

```xpp
public static Timezone getUserPreferredTimeZone()
```

### Return Value - getUserPreferredTimeZone

The PreferredTimezone enumeration value for the current user.

## Method hour

Retrieves the hour of the day that is specified by a utcdatetime value.

```xpp
public static int hour(DateTime t)
```

### Parameters - hour

t  
A utcdatetime value for which to retrieve the value of the hour component.

### Return Value - hour

The hour in the day of the specified utcdatetime value.

## Method maxValue

Retrieves the maximum value that is allowed for a variable of the utcdatetime type.

```xpp
public static DateTime maxValue()
```

### Return Value - maxValue

The maximum value that is allowed for a variable of the utcdatetime type.

## Method minute

Retrieves the minute in the hour that is specified by a utcdatetime value.

```xpp
public static int minute(DateTime t)
```

### Parameters - minute

t  
A utcdatetime value for which to retrieve the value of the minute component.

### Return Value - minute

The minute in the hour of the specified utcdatetime value.

## Method minValue

Retrieves the minimum value that is allowed for a variable of the utcdatetime type.

```xpp
public static DateTime minValue()
```

### Return Value - minValue

The minimum value that is allowed for a variable of the utcdatetime type.

## Method month

Retrieves the month in the year that is specified by a utcdatetime value.

```xpp
public static int month(DateTime t)
```

### Parameters - month

t  
A utcdatetime value for which to retrieve the value of the month component.

### Return Value - month

The month in the year of the specified utcdatetime value.

## Method newDateTime

Creates a new utcdatetime value by using the specified date and timeOfDay values.

```xpp
public static DateTime newDateTime(Date date, TimeOfDay time, [Timezone tzOffsetToRemove])
```

### Parameters - newDateTime

date  
The time zone in which to create the new utcdatetime value; optional.

<!-- -->

time  
The time zone in which to create the new utcdatetime value; optional.

<!-- -->

tzOffsetToRemove  
The time zone in which to create the new utcdatetime value; optional.

### Return Value - newDateTime

A new utcdatetime value.

### Remarks - newDateTime

If no value is specified for the tzOffsetToRemove parameter, the utcdatetime value will be created in the UTC time zone.

## Method parse

Creates a new utcdatetime value from the specified string.

```xpp
public static DateTime parse(str s)
```

### Parameters - parse

s  
A string in the following format: yyyy-mm-ddThh:mm:ss.

### Return Value - parse

A new utcdatetime value from the specified string.

## Method populateTimeZoneInfo

Retrieves start and end dates and time bias.

```xpp
public static container populateTimeZoneInfo(int year, Timezone tz)
```

### Parameters - populateTimeZoneInfo

year  
The time zone.

<!-- -->

tz  
The time zone.

### Return Value - populateTimeZoneInfo

The start and end dates and time bias.

## Method removeTimeZoneOffset

Removes the offset that is indicated by a Timezone enumeration value from the specified utcdatetime value.

```xpp
public static DateTime removeTimeZoneOffset(DateTime t, Timezone tz)
```

### Parameters - removeTimeZoneOffset

t  
The Timezone enumeration value to remove.

<!-- -->

tz  
The Timezone enumeration value to remove.

### Return Value - removeTimeZoneOffset

A utcdatetime value without a time zone offset.

## Method removeTimeZoneOffsetFilter

Removes the time zone offset from the filter.

```xpp
public static str removeTimeZoneOffsetFilter(QueryFilter filter)
```

### Parameters - removeTimeZoneOffsetFilter

filter  

### Return Value - removeTimeZoneOffsetFilter

The new date/time range value.

## Method removeTimeZoneOffsetRange

Removes the time zone offset from the range.

```xpp
public static str removeTimeZoneOffsetRange(QueryBuildRange range)
```

### Parameters - removeTimeZoneOffsetRange

range  

### Return Value - removeTimeZoneOffsetRange

The new date/time range value.

## Method second

Retrieves the seconds in a minute that is specified by a utcdatetime value.

```xpp
public static int second(DateTime t)
```

### Parameters - second

t  
A utcdatetime value for which to retrieve the value of the second component.

### Return Value - second

The second in the minute of the specified utcdatetime value.

## Method time

Retrieves the number of seconds that have elapsed since midnight as a timeOfDay value from the specified utcdatetime value.

```xpp
public static TimeOfDay time(DateTime t)
```

### Parameters - time

t  
A utcdatetime value for which to retrieve the time.

### Return Value - time

A timeOfDay value that indicates the number of seconds that have elapsed since midnight.

## Method toFormattedStr

```xpp
public static str toFormattedStr(DateTime t, int sequence, int day, int separator1, int month, int separator2, int year, int timeSeparator1, int timeSeparator2, [int flags])
```

### Parameters - toFormattedStr

t  

<!-- -->

sequence  

<!-- -->

day  

<!-- -->

separator1  

<!-- -->

month  

<!-- -->

separator2  

<!-- -->

year  

<!-- -->

timeSeparator1  

<!-- -->

timeSeparator2  

<!-- -->

flags  

### Return Value - toFormattedStr

## Method toStr

Converts a utcdatetime value to a string in the following format: YYYY-MM-DDThh:mm:ss, where T is a character literal.

```xpp
public static str toStr(DateTime t)
```

### Parameters - toStr

t  
The utcdatetime value to convert.

### Return Value - toStr

The string representation of the specified utcdatetime value.

## Method utcNow

Retrieves a utcdatetime value that indicates the current system time.

```xpp
public static DateTime utcNow()
```

### Return Value - utcNow

The current system time as a utcdatetime value.

### Remarks - utcNow

This method is run on the server, so that the time that is returned is the system time of the server.

## Method year

Retrieves the year that is specified by a utcdatetime value.

```xpp
public static int year(DateTime t)
```

### Parameters - year

t  
A utcdatetime value for which to retrieve the value of the year component.

### Return Value - year

The year of the specified utcdatetime value.

## Method setSystemDateTime

Sets the date and time of the system to the specified utcdatetime value.

```xpp
public static void setSystemDateTime(DateTime t)
```

### Parameters - setSystemDateTime

t  
A utcdatetime value to which to set the system date and time.

## Method setCompanyTimeZone

Sets the Timezone enumeration value that is used by the current company.

```xpp
public static void setCompanyTimeZone(Timezone tz, [boolean persist])
```

### Parameters - setCompanyTimeZone

tz  
A Boolean value that indicates whether the new value should be persisted.

<!-- -->

persist  
A Boolean value that indicates whether the new value should be persisted.

## Method setUserPreferredCalendar

Sets the value of the PreferredCalendar enumeration type of the current user for the current session.

```xpp
public static void setUserPreferredCalendar(PreferredCalendar calendar)
```

### Parameters - setUserPreferredCalendar

calendar  
The PreferredCalendar enumeration value to set.

## Method setUserPreferredTimeZone

Sets the preferred time zone of the user to the specified Timezone enumeration value.

```xpp
public static void setUserPreferredTimeZone(Timezone tz, [boolean persist])
```

### Parameters - setUserPreferredTimeZone

tz  
A Boolean value that indicates whether the new value should be persisted.

<!-- -->

persist  
A Boolean value that indicates whether the new value should be persisted.

## Method new

Initializes a new instance of the DateTimeUtil class.

```xpp
private void new()
```

