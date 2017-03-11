---
# required metadata

title: X++ date run-time functions
description: This topic describes the date run-time functions.
author: RobinARH
manager: AnnBe
ms.date: 2016-02-04 22 - 12 - 59
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 2051
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 31341
ms.assetid: fbaf07ef-63d0-40aa-bef5-e44d6c6a4643
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# X++ date run-time functions

This topic describes the date run-time functions.

dayName
-------

Retrieves the name of the day of the week that is specified by a number.

    str dayName(int number)

### Parameters

| Parameter | Description                    |
|-----------|--------------------------------|
| number    | The number of a day in a week. |

### Return value

The day of the week specified by the number parameter.

### Remarks

The valid values for the number parameter are **1** through **7**. Monday is represented by **1**, Tuesday by **2**, and Sunday by **7**.

### Example

    static void dayNameExample(Args _arg)
    {
            str s;
            ;
            s = dayName(01);
            print "First day of the week's name is " + s;
            pause;
    }

## dayOfMth
Calculates the number of the day in the month for the specified date.

    int dayOfMth(date date)

### Parameters

| Parameter | Description       |
|-----------|-------------------|
| date      | The date to test. |

### Return value

An integer between 1 and 31 that indicates the day of the month for the specified date.

### Remarks

    dayOfMth(31122001) //returns 31.

### Example

    static void dayOfMthExample(Args _arg)
    {
            date d = today();
            int i;
            ;
            i = dayOfMth(d);
            print "Today's day of the month is " + int2Str(i);
            pause;
    }

## dayOfWk
Calculates the number of day in the week for the specified date. **Note:** Monday is represented by **1**, Tuesday by **2**, and Sunday by **7**.

    int dayOfWk(date date)

### Parameters

| Parameter | Description                                               |
|-----------|-----------------------------------------------------------|
| date      | A **date** value that indicates the year, month, and day. |

### Return value

The number of the specified day in the week.

### Example

    static void dayOfWkExample(Args _arg)
    {
            date d = today();
            int i;
            ;
            i = dayOfWk(d);
            print "Today's day of the week is " + int2Str(i);
            pause;
    }

## dayOfYr
Calculates the number of days between January 1 and the specified date.

    int dayOfYr(date _date)

### Parameters

| Parameter | Description                                     |
|-----------|-------------------------------------------------|
| \_date    | A date that specifies the year, month, and day. |

### Return value

The number of days between January 1 and the specified date, inclusive.

### Remarks

January 1 is **1**, and December 31 is either **365** or **366**.

### Example

    static void dayOfYrExample(Args _arg)
    {
            date d = today();
            int i;
            ;
            i = dayOfYr(d);
            print "Today's day of the year is " + int2Str(i);
            pause;
    }

## endMth
Calculates the last date in the month of the specified date.

    date endMth(date date)

### Parameters

| Parameter | Description                                             |
|-----------|---------------------------------------------------------|
| date      | A **date** value that indicates a year, month, and day. |

### Return value

The **date** value of the last day in the specified month.

### Remarks

    endMth(0221988); //Returns the date 2921988 because 1988 is a leap year.
    endMth(0221989); //Returns the date 2821989.

## mkDate
Creates a date, based on three integers that indicate the day, month, and year, respectively.

    date mkDate(int day, int month, int year)

### Parameters

| Parameter | Description                                                               |
|-----------|---------------------------------------------------------------------------|
| day       | An integer that represents the day of the month.                          |
| month     | An integer that represents the month of the year.                         |
| year      | An integer that represents the year, which must be between 1900 and 2154. |

### Return value

A **date** value that is based on the values of the *day*, *month*, and *year* parameters.

### Remarks

If the date isn't valid, this method returns a **0** (zero, 1/1/1900) date. Beginning with Dynamics 365 for Operations (February 2016), shortcut values for the year, e.g. 75 for 1975, are not supported. If you provide a shortcut value for the year, a date of 1/1/1900 is returned.

### Example

    static void mkDateExample(Args _arg)
    {
            date d;
            ;
            // Returns the date 0112005.
            d = mkDate(1, 1, 2005);
            print d;
            pause;
    }

## mthName
Retrieves the name of the specified month

    str monthName(int number)

### Parameters

| Parameter | Description              |
|-----------|--------------------------|
| number    | The number of the month. |

### Return value

The name of the specified month.

### Remarks

The valid values of the *number* parameter are **1** through **12**. January is represented by **1** and December by **12**.

### Example

    static void mthNameExample(Args _arg)
    {
            str s;
            ;
            // MthName(6) returns the text string "June".
            s = mthName(6);
            print "Month name is " + s;
            pause;
    }

## mthOfYr
Retrieves the number of the month in the year for the specified date. **Note:** January is **1**, February is **2**, and December is **12**.

    int mthOfYr(date date)

### Parameters

| Parameter | Description                                   |
|-----------|-----------------------------------------------|
| date      | A date that specifies a year, month, and day. |

### Return value

The number of the month in the year, for the month that is represented by the *date* parameter.

### Example

    static void mthOfYrExample(Args _arg)
    {
            int i;
            ;
            i = mthOfYr(today());
            print "The number of the month in today's date is " + int2Str(i);
            pause;
    }

## nextMth
Retrieves the date in the following month that corresponds most closely to the specified date.

    date nextMth(date date)

### Parameters

| Parameter | Description                               |
|-----------|-------------------------------------------|
| date      | The date to match in the following month. |

### Return value

The closest match to the specified date that is found in the next month.

### Remarks

    nextMth(2921996); //returns 29/03/1996.
    nextMth(3111996); //returns 2921996, because 1996 is a leap year.

### Example

    static void nextMthExample(Args _arg)
    {
            date d;
            ;
            d = nextMth(today());
            print "Closest date next month is "
            + date2Str(d, 2, 2, -1, 2, -1, 4);
            pause;
    }

## nextQtr
Retrieves the date in the following quarter that corresponds most closely to the specified date.

    date nextQtr(date date)

### Parameters

| Parameter | Description                                 |
|-----------|---------------------------------------------|
| date      | The date to match in the following quarter. |

### Return value

The closest match to specified date that is found in the next quarter.

### Remarks

For example, **nextQtr(3111998)** returns **3041998**.

### Example

    static void nextQtrExample(Args _arg)
    {
            date d;
            ;
            d = nextQtr(today());
            print "Closest date next quarter is "
                    + date2Str(d, 2, 2, -1, 2, -1, 4);
            pause;
    }

## nextYr
Retrieves the date in the following year that corresponds most closely to the specified date.

    date nextYr(date date)

### Parameters

| Parameter | Description                              |
|-----------|------------------------------------------|
| date      | The date to match in the following year. |

### Return value

The closest match to the specified date that is found in the following year.

### Remarks

For example, **nextyr(2921998)** returns **2821999**.

### Example

    static void nextYrExample(Args _arg)
    {
            date d;
            ;
            d = nextYr(today());
            print "Closest date next year is "
                    + date2Str(d, 2, 2, -1, 2, -1, 4);
            pause;
    }

## prevMth
Retrieves the date in the previous month that corresponds most closely to the specified date.

    date prevMth(date date)

### Parameters

| Parameter | Description                              |
|-----------|------------------------------------------|
| date      | The date to match in the previous month. |

### Return value

The closest match to the specified date that is found in the previous month.

### Remarks

    prevMth(3131996); //Returns the date 29/02/1996 because 1996 is a leap year.
    prevMth(2821998); //Returns the date 28/01/1998.

## prevQtr
Retrieves the date in the previous quarter that corresponds most closely to the specified date.

    date prevQtr(date date)

### Parameters

| Parameter | Description                                |
|-----------|--------------------------------------------|
| date      | The date to match in the previous quarter. |

### Return value

The closest match to the specified date that is found in the previous quarter.

### Remarks

    prevQtr(3041998); //Returns the date 30/01/1998.
    prevQtr(2951996); //Returns the date 29/02/1996, because 1996 is a leap year.

## prevYr
Retrieves the date in the previous year that corresponds most closely to the specified date.

    date prevYr(date date)

### Parameters

| Parameter | Description                             |
|-----------|-----------------------------------------|
| date      | The date to match in the previous year. |

### Return value

The closest match to the specified date that is found in the previous year.

### Remarks

    prevYr(2921996); //Returns the date 28/02/1995 because 1996 is a leap year.
    prevYr(2821998); //Returns the date 28/02/1997.

## systemDateGet
Retrieves the session date, if it has been set.

    date systemDateGet()

### Return value

The session date if it has been set; otherwise, the system date.

### Remarks

Consider using **Session date and time** on the **Tools** menu to open the **Session date and time** page. This page can be used to actively set the session date. After this set action is detected by the system, subsequent calls to the **systemDateGet** function return the session date. The **today** function returns the system date. This function doesn't support time zones.

### Example

The following example shows the date in the Infolog window.

    static void Job_systemDateGet(Args _arg)
    {
            info( date2Str(
                    systemDateGet(),        // X++ language function.
                    321,                    // 321 = ymd
                    DateDay::Digits2,
                    DateSeparator::Hyphen,  // separator1
                    DateMonth::Digits2,
                    DateSeparator::Hyphen,  // separator2
                    DateYear::Digits4
            )
    );
    /*********** Actual Infolog output
    Message (03:46:00 pm)
    2012-04-16
    ***********/
    }

## systemDateSet
Changes the system date.

    date systemDateSet(date _date)

### Parameters

| Parameter | Description                  |
|-----------|------------------------------|
| \_date    | The new date for the system. |

### Return value

The new system date.

### Remarks

This function doesn't affect the session date. This method changes the date, but the time will be set to **0** (zero).

### Example

The following example sets the system date to today's date.

    static void systemDateSetExample(Args _arg)
    {
            date d = today();
            d = systemDateSet(d);
            print d;
    }

## timeNow
Retrieves the current system time.

    int timeNow()

### Return value

The number of seconds that have passed since midnight.

### Example

    static void timeNowExample(Args _arg)
    {
            int i;
            ;
            i = timeNow();
            print "The number of seconds since midnight is " + int2Str(i);
            pause;
    }

## today
Retrieves the current date on the system.

    date today()

### Return value

The current date.

### Example

    static void todayExample(Args _arg)
    {
            date d;
            ;
            d = today();
            print "Today's date is " + date2Str(d, 0, 2, -1, 2, -1, 4);
            pause;
    }

## wkOfYr
Calculates the week of the year that a date falls in, according to the ISO 8601 specification.

    int wkOfYr(date _date)

### Parameters

| Parameter | Description                                     |
|-----------|-------------------------------------------------|
| \_date    | The date to calculate the week of the year for. |

### Return value

The sequence number of the week that the *\_date* parameter occurs in.

### Example

The following code example compares the **wkOfYr** function with the **Global::weekOfYear** method. The function and the method produce different results.

    // X++ job, under AOT > Jobs.
    static void WeekTests3Job(Args _args)
    {
    int weekNum, i;
    date dateTest;
    str sMessages[];
    //---------------------------------------------
    sMessages[1] = "----- #1.  For Sunday, January 5, 2003 -----";
    dateTest = 512003; // DayMonthYear  format.
    weekNum = wkOfYr(dateTest);
    sMessages[2] = int2str(weekNum) + " = wkOfYr funtion";
    weekNum = Global::weekOfYear(dateTest);
    sMessages[3] = int2str(weekNum) + " = Global::weekOfYear method";
    //---------------------------------------------
    sMessages[4] = " ";
    sMessages[5] = "----- #2.  For Wednesday, August 20, 2003 -----";
    dateTest = 2082003;
    weekNum = wkOfYr(dateTest);
    sMessages[6] = int2str(weekNum) + " = wkOfYr funtion";
    weekNum = Global::weekOfYear(dateTest);
    sMessages[7] = int2str(weekNum) + " = Global::weekOfYear method";
    //---------------------------------------------
    sMessages[8] = " ";
    sMessages[9] = "----- #3.  For Sunday, December 28, 2003 -----";
    dateTest = 28122003;
    weekNum = wkOfYr(dateTest);
    sMessages[10] = int2str(weekNum) + " = wkOfYr funtion";
    weekNum = Global::weekOfYear(dateTest);
    sMessages[11] = int2str(weekNum) + " = Global::weekOfYear method";
    for (i=1; i<= 11; i++)
    {
    Global::info(sMessages[i]);
    }
    }

The previous example sent the following information to the Infolog for display. The output shows that there are differences between **wkOfYr** and **Global::weekOfYear**. Message (01:59:13 pm) ----- \#1. For Sunday, January 5, 2003 ----- 1 = wkOfYr funtion 2 = Global::weekOfYear method ----- \#2. For Wednesday, August 20, 2003 ----- 34 = wkOfYr funtion 34 = Global::weekOfYear method ----- \#3. For Sunday, December 28, 2003 ----- 52 = wkOfYr funtion 1 = Global::weekOfYear method

## year
Retrieves the year from a **date** value.

    int year(date _date)

### Parameters

| Parameter | Description                       |
|-----------|-----------------------------------|
| \_date    | The date to return the year from. |

### Return value

The year of the specified date.

### Remarks

    year(0221998); //Returns the value 1998.

