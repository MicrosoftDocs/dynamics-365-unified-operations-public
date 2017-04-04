---
# required metadata

title: X++ run-time functions
description: This topic describes the X++ run-time functions.
author: RobinARH
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 61
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 31461
ms.assetid: 9cf83640-536c-4a99-8e0d-7a4e97d3c91f
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# X++ run-time functions

This topic describes the X++ run-time functions.

The X++ language provides nearly 200 system functions that aren't part of any class and are executed at run time. Run-time functions are used for data type conversions, mathematical operations, and so on. Here are some common run-time functions:

-   **str2Int** – Creates an int value from a str value.
-   **abs** – Creates a positive real value from a real value that is either positive or negative.
-   **conFind** – Retrieves the location of an element in a container.

### Call run-time functions from .NET

The logic of the X++ run-time functions is also implemented in the following .NET assembly.

    Microsoft.Dynamics.AX.Xpp.Support.DLL

Inside this assembly, the X++ run-time functions are implemented as static methods of the following class.

    Microsoft.Dynamics.AX.Xpp.PredefinedFunctions

## Categories and functions
The following table lists and describes only the categories of X++ functions. These categories are intended to help you understand the many functions. However, the categories don't represent any formal construct.

| Category                  | Description                                                                                                                                                                                                                |
|---------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Business](#business)     | Functions that enter financial data and calculate formulas. For more information, see [X++ Business Run-Time Functions](xpp-business-run-time-functions.md).                              |
| [Container](#container)   | Functions that operate on the container data type of X++. For more information, see [X++ Container Run-Time Functions](xpp-container-run-time-functions.md).                               |
| [Conversion](#conversion) | Functions that translate data of one type into data of another type. For more information, see [X++ Conversion Run-Time Functions](xpp-conversion-run-time-functions.md).                  |
| [Date](#date)             | Functions that operate on the date data type. For more information, see [X++ Date Run-Time Functions](xpp-date-run-time-functions.md).                                                     |
| [Math](#Math)             | Functions that perform mathematical calculations. For more information, see [X++ Math Run-Time Functions](xpp-math-run-time-functions.md).                                                 |
| [Reflection](#reflection) | Functions that access the metadata about objects and return other metadata about them. For more information, see [X++ Reflection Run-Time Functions](xpp-reflection-run-time-functions.md). |
| [Session](#Session)       | Functions that change or report on the context of the current user connection. For more information, see [X++ Session Run-Time Functions](xpp-session-run-time-functions.md).             |
| [String](#string)         | Functions that operate on the str data type. For more information, see [X++ String Run-Time Functions](xpp-string-run-time-functions.md).                                                 |
| Other                     | [beep](#beep), [newGuid](#newguid), [sleep](#sleep)                                                                                                                                                                        |

## Business
For more information, see [X++ Business Run-Time Functions](xpp-business-run-time-functions.md).

|          |         |          |        |
|----------|---------|----------|--------|
| cTerm    | ddb     | dg       | fV     |
| idg      | intvMax | intvName | intvNo |
| intvNorm | pmt     | pt       | pv     |
| rate     | sln     | syd      | term   |

## Container
For more information, see [X++ Container Run-Time Functions](xpp-container-run-time-functions.md).

conDel

conFind

conIns

conLen

conNull

conPeek

conPoke

## Conversion
For more information, see [X++ Conversion Run-Time Functions](xpp-conversion-run-time-functions.md).

|           |              |              |            |
|-----------|--------------|--------------|------------|
| any2Date  | any2Enum     | any2Guid     | any2Int    |
| any2Int64 | any2Real     | any2Str      | anytodate  |
| anytoenum | anytoguid    | anytoint     | anytoint64 |
| anytoreal | anytostr     | char2Num     | date2Num   |
| date2Str  | datetime2Str | enum2str     | guid2Str   |
| int2Str   | int642Str    | num2Char     | num2Date   |
| num2Str   | str2Date     | str2Datetime | str2Enum   |
| str2Guid  | str2Int      | str2Int64    | str2Num    |
| str2Time  | time2Str     | uint2Str     |            |

## Date
For more information, see [X++ Date Run-Time Functions](xpp-date-run-time-functions.md).

|         |          |               |               |
|---------|----------|---------------|---------------|
| dayName | dayOfMth | dayOfWk       | dayOfYr       |
| endMth  | mkDate   | mthName       | mthOfYr       |
| nextMth | nextQtr  | nextYr        | prevMth       |
| prevQtr | prevYr   | systemDateGet | systemDateSet |
| timeNow | today    | wkOfYr        | year          |

## Math
For more information, see [X++ Math Run-Time Functions](xpp-math-run-time-functions.md).

|         |          |               |               |
|---------|----------|---------------|---------------|
|abs|acos|asin|atan|
|corrFlagGet|corrFlagSet|cos|cosh|
|decRound|exp|exp10|frac|
|log10|logN|max|min|
|power|round|sin|sinh|
|tan|tanh|trunc||

## Reflection
For more information, see [X++ Reflection Run-Time Functions](xpp-reflection-run-time-functions.md).

|              |               |              |               |
|--------------|---------------|--------------|---------------|
| classIdGet   | dimOf         | fieldId2Name | fieldId2PName |
| fieldName2Id | indexId2Name  | indexName2Id | refPrintAll   |
| tableId2Name | tableId2PName | tableName2Id | typeOf        |

## Session
For more information, see [X++ Session Run-Time Functions](xpp-session-run-time-functions.md).

|                          |           |           |                     |
|--------------------------|-----------|-----------|---------------------|
| curExt                   | curUserId | funcName  | getCurrentPartition |
| getCurrentPartitionRecId | getPrefix | sessionId | prmIsDefault        |
| runAs                    | setPrefix |           |                     |

## String
For more information, see [X++ String Run-Time Functions](xpp-string-run-time-functions.md).

|         |          |          |           |
|---------|----------|----------|-----------|
| match   | strAlpha | strCmp   | strColSeq |
| strDel  | strFind  | strFmt   | strIns    |
| strKeep | strLen   | strLine  | strLTrim  |
| strLwr  | strNFind | strPoke  | strPrompt |
| strRem  | strRep   | strRTrim | strScan   |
| strUpr  | subStr   |          |           |

## beep
Emits a short sound from the speakers on the computer.

    void beep()

### Example

    static void beepExample(Args _args)
    {
            beep();
    }

## newGuid
Creates a globally unique identifier (GUID).

    guid newGuid()

### Return value

A GUID.

### Example

The following example creates a GUID.

    static void newGuidExample(Args _arg)
    {
            guid myGuid;

            myGuid = newguid();
            print strfmt("The GUID is: %1", myGuid);
    }

## sleep
Pauses the execution of the current thread for the specified number of milliseconds.

    int sleep(int _duration)

### Parameters

| Parameter  | Description                          |
|------------|--------------------------------------|
| \_duration | The number of milliseconds to pause. |

### Return value

The number of milliseconds that the thread actually paused.

### Example

    static void sleepExample(Args _arg)
    {
            int seconds = 10;
            int i;

            i = sleep(seconds*1000);
            print "job slept for " + int2str(i/1000) + " seconds";
    }



