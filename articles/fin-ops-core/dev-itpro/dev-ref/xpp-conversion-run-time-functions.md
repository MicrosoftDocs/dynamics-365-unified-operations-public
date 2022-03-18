---
title: X++ conversion runtime functions
description: This topic describes the conversion run-time functions.
author: RobinARH
ms.date: 06/26/2018
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: tfehr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# X++ conversion runtime functions

[!include [banner](../includes/banner.md)]

This topic describes the conversion run-time functions.

## any2Date

Converts an **anytype** value to a **date** value.

```xpp
date any2Date(anytype object)
```

### Parameters

| Parameter | Description                     |
|-----------|---------------------------------|
| object    | The value to convert to a date. |

### Return value

A **date** value.

### Remarks

The *object* parameter can be of most data types, but useful output is obtained when it's of the **str** or **int** type. Inappropriate content generates a run-time error.

### Example

```xpp
static void any2DateExample(Args _args)
{
    date myDate;
    str s;
    int i;
    s = "2010 6 17"; // A string object, of yyyy mm dd.
    myDate = any2Date(s);
    Global::info(strFmt("%1  is output, from input of "2010 6 17"", myDate));
    i = 40361; // An int object, which represents the number of days from 1900/01/01.
    myDate = any2Date(i);
    Global::info(strFmt("%1  is output, from input of 40361", myDate));
}
/**** Infolog display.
Message (04:44:15 pm)
6/17/2010 is output, from input of "2010 6 17"
7/4/2010 is output, from input of 40361
****/
```

## any2Enum
Converts an **anytype** value to the **Name** property value of an element in the target enum.

```xpp
enum any2Enum(anytype object)
```

### Parameters

| Parameter | Description                                                                 |
|-----------|-----------------------------------------------------------------------------|
| object    | The value to match the **Value** property of an element in the target enum. |

### Return value

The value of the **Name** property for whichever element in the target enum has a **Value** property that matches the input parameter.

### Remarks

The *object* parameter can be of most data types, but useful data is obtained only when you use a parameter of the **str** or **int** type. This input *object* parameter refers to the **Value** property of an individual element in the target enum.

### Example

```xpp
static void any2EnumExample(Args _args)
{
    NoYes myNoYes;  // NoYes is an enum.
    int i;
    str s;
    i = 0;  // An int that will be converted.
    myNoYes = any2Enum(i);
    Global::info(strfmt("'%1' - is the output, from input of the %2 as int.", myNoYes, i));
    s = "1";  // A str that will be converted.
    myNoYes = any2Enum(s);
    Global::info(strfmt("'%1' - is the output, from input of the %2 as str.", myNoYes, s));
    /**** Infolog display.
    Message (01:05:32 pm)
    'No' - is the output, from input of the 0 as int.
    'Yes' - is the output, from input of the 1 as str.
    ****/
}
```

## any2Guid
Converts the specified **anytype** object to a GUID object.

```xpp
guid any2Guid(anytype object)
```

### Parameters

| Parameter | Description                            |
|-----------|----------------------------------------|
| object    | The value to convert to a GUID object. |

### Return value

A GUID object.

## any2Int
Converts an **anytype** value to an **int** value.

```xpp
int any2Int(anytype object)
```

### Parameters

| Parameter | Description           |
|-----------|-----------------------|
| object    | The value to convert. |

### Return value

An **int** value.

### Remarks

The *object* parameter can be of most data types, but useful data is obtained only when you use parameters of the **enum**, **real**, or **str** type.

### Example

```xpp
static void any2IntExample(Args _args)
{
    int myInt;
    str s;
    NoYes a;
    real r;
    s = "31";
    myInt = any2Int(s);
    Global::info(strfmt("%1 is the output, from input of 31 as a str value.", myInt));
    a = NoYes::No;
    myInt = any2Int(a);
    Global::info(strfmt("%1 is the output, from input of NoYes::No as an enum value.", myInt));
    r = 5.34e2;
    myInt = any2Int(r);
    Global::info(strfmt("%1 is the output, from the input of 5.34e2 as a real value.", myInt));
}
/**** Infolog display.
Message (02:23:59 pm)
31 is the output, from input of 31 as a str value.
0 is the output, from input of NoYes::No as an enum value.
534 is the output, from the input of 5.34e2 as a real value.
****/
```

## any2Int64
Converts an **anytype** object to an **int64** object.

```xpp
int64 any2Int64(anytype object)
```

### Parameters

| Parameter | Description                        |
|-----------|------------------------------------|
| object    | The **anytype** object to convert. |

### Return value

An **int64** object.

## any2Real
Converts an **anytype** value to a **real** value.

```xpp
real any2Real(anytype object)
```

### Parameters

| Parameter | Description           |
|-----------|-----------------------|
| object    | The value to convert. |

### Return value

A **real** value.

### Remarks

The *object* parameter can be of most data types, but useful output is obtained for input elements of the **date**, **int**, **enum**, and **str** types.

### Example

```xpp
static void any2RealExample(Args _args)
{
    real myReal;
    str s;
    int i;
    NoYes a;
    s = "5.12";
    myReal = any2Real(s);
    Global::info(strfmt("%1 is the output from the input of 5.12 as a str object", myReal));
    i = 64;
    myReal = any2Real(i);
    Global::info(strfmt("%1 is the output from the input of 64 as an int object", myReal));
    a = NoYes::Yes;
    myReal = any2Real(a);
    Global::info(strfmt("%1 is the output from the input of NoYes::Yes as an enum object", myReal));
}
/****Infolog display.
Message (02:43:57 pm)
5.12 is the output from the input of 5.12 as a str object
64.00 is the output from the input of 64 as an int object
1.00 is the output from the input of NoYes::Yes as an enum object
****/
```

## any2Str
Converts an **anytype** value to a **str** value.

```xpp
str any2Str(anytype object)
```

### Parameters

| Parameter | Description           |
|-----------|-----------------------|
| object    | The value to convert. |

### Return value

A **str** value.

### Remarks

The *object* parameter can be of most data types, but useful output is obtained from input elements of the **date**, **int**, and **enum** types.

### Example

```xpp
static void any2StrExample(Args _args)
{
    str myStr;
    anytype a;
    a = "Any to string";
    myStr = any2Str(a);
    Global::info(strFmt("%1 is output, from input of Any to string as a str value", myStr));
    a = NoYes::Yes;
    myStr = any2Str(a);
    Global::info(strFmt("%1 is output, from input of NoYes::Yes as an enumeration", myStr));
}
/****Infolog Display
Message (09:08:46 am)
Any to string is output, from input of Any to string as a str value
1 is output, from input of NoYes::Yes as an enumeration
****/
```

## anytodate
See [any2Date](#any2date).

## anytoenum
See [any2Enum](#any2enum).

## anytoguid
See [any2Guid](#any2guid).

## anytoint
See [any2Int](#any2int).

## anytoint64
See [any2Int64](#any2int64).

## anytoreal
See [any2Real](#any2real).

## anytostr
See [any2Str](#any2str).

## char2Num

Converts a character in a string to the ASCII value of the character.

```xpp
int char2Num(str text, int position)
```

### Parameters

| Parameter | Description                                  |
|-----------|----------------------------------------------|
| text      | The string that contains the character.      |
| position  | The position of the character in the string. |

### Return value

The ASCII value of the character as an **int** object.

### Remarks

```xpp
char2Num("ABCDEFG",3); //Returns the numeric value of C, which is 67.
char2Num("ABCDEFG",1); //Returns the numeric value of A, which is 65.
```

## date2Num
Converts a date to an integer that corresponds to the number of days since January 1, 1900.

```xpp
int date2Num(date _date)
```

### Parameters

| Parameter | Description          |
|-----------|----------------------|
| \_date    | The date to convert. |

### Return value

The number of days between January 1, 1900, and the specified date.

### Example

```xpp
//Returns the value377.
date2Num(1311901);
static void date2NumExample(Args _arg)
{
    date d = today();
    int i;
    i = date2Num(d);
    print i;
}
```

## date2Str
Converts the specified date to a string.

```xpp
str date2Str(date date, int sequence, int day, int separator1, int month, int separator2, int year [, int flags = DateFlags::None])
```

### Parameters

| Parameter  | Description                                                                                                                                                                                                 |
|------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| date       | The date to convert.                                                                                                                                                                                        |
| sequence   | A three-digit number that indicates the sequence for the components of the date: **1** for day, **2** for month, and **3** for year.                                                                        |
| day        | An enumeration value that indicates the format for the day component of the date.                                                                                                                            |
| separator1 | An enumeration value that indicates the separator to use between the first two components of the date.                                                                                                       |
| month      | An enumeration value that indicates the format for the month component of the date.                                                                                                                          |
| separator2 | An enumeration value that indicates the separator to use between the last two components of the date.                                                                                                        |
| year       | An enumeration value that indicates the format for the year component of the date.                                                                                                                           |
| flags      | A **DateFlags** enumeration value that indicates whether the language settings on the local computer should be used to calculate the proper left-to-right or right-to-left sequence in the returned string. |

### Return value

A string that represents the specified date.

### Remarks

MorphX allocates valid values to the formatting parameters if the specified values aren't valid. To use the date format that the user specified in Regional Settings, use the **strFmt** or **date2Str** function and specify **-1** in all the formatting parameters. When the regional settings control the date format, the settings can change from user to user. If **-1** is used for either *separator* parameter, both separators default to Regional Settings. The *sequence* parameter values must be any three-digit number that contains exactly one occurrence of each the digits 1, 2 and 3. The digits 1, 2, and 3 represent day, month, and year, respectively. For example, **321** produces the sequence year, month, and day. Or the value can be **-1** to use Regional Settings. No enumeration type should be used for this parameter, because numbers such as 321 exceed the range of valid values for enumeration values, which is 0 through 250, inclusive. The default value of the *flags* parameter is the **DateFlags::None** enumeration value, which means no left-to-right or right-to-left sequence processing is done.

### Example

The following example displays the current date in the sequence of year, month, and day.

```xpp
static void Job2(Args _args)
{
    date currentDate = today();
    str s;
    int iEnum;
    s = date2Str
    (currentDate, 
        321,
        DateDay::Digits2,
        DateSeparator::Hyphen, // separator1
        DateMonth::Digits2,
        DateSeparator::Hyphen, // separator2
        DateYear::Digits4
    );
    info("Today is:  " + s);
}
/** Example Infolog output
Message (12:36:21 pm)
Today is:  2009-01-13
**/
```

## datetime2Str
Converts a **utcdatetime** value into a string.

```xpp
str datetime2Str(utcdatetime datetime [, int flags = DateFlags::None])
```

### Parameters

| Parameter | Description                                                                                              |
|-----------|----------------------------------------------------------------------------------------------------------|
| datetime  | The **utcdatetime** value to convert.                                                                    |
| flags     | A **DateFlags** enumeration value that indicates whether to use local settings for right-to-left output. |

### Return value

A string that represents the **utcdatetime** value that was specified as the *datetime* parameter.

### Remarks

#### Null date-time input

If the minimum **utcdatetime** value is specified for the *datetime* parameter, the **datetime2Str** function treats it as a null input value. This causes the function to return an empty string. The date-time **1900-01-01T00:00:00** is returned by the **DateTimeUtil::minValue** method. This minimum value is treated as null.

#### Right-to-left local settings

The default behavior of this function is to generate the string in left-to-right sequence, where the year portion is leftmost. However, the *flags* parameter value of the **DateFlags::FormatAll** enumeration value directs the function to generate the string in right-to-left sequence if the local settings are configured for right-to-left. The format of the **toStr** method of the **DateTimeUtil** class is unaffected by regional settings.

### Example

```xpp
static void jobTestDatetime2str( Args _args )
{
    utcdatetime utc2 = 1959-06-17T15:44:33;
    str s3;
    s3 = datetime2Str( utc2 );
    info( s3 );
}
```

## enum2Str
Converts the specified enumerated text to a character representation.

```xpp
str enum2Str(enum enum)
```

### Parameters

| Parameter | Description                     |
|-----------|---------------------------------|
| enum      | The enumerated text to convert. |

### Return value

The value of the enumeration as a string.

### Example

The following example returns the string "Not included." This is the label for the **IncludeNot** value of the **ListCode** enumeration type.

```xpp
static void enum2StrExample(Args _arg)
{
    ListCode l;
    l =  ListCode::IncludeNot;
    print enum2Str(l);
}
```

## guid2Str
Converts the specified GUID object to the equivalent string.

```xpp
str guid2String(guid _uuid)
```

### Parameters

| Parameter | Description                 |
|-----------|-----------------------------|
| \_uuid    | The GUID object to convert. |

### Return value

The string equivalent of the specified GUID object.

### Example

```xpp
static void guid2StrExample()
{
    guid _guid;
    str stringGuid;
    _guid = Global::guidFromString("{12345678-1234-1234-1234-123456789abc}");
    print strfmt("GUID is %1", _guid);
    stringGuid = guid2str(_guid);
    info("String GUID is " + stringGuid);
}
/**** Output to Infolog
String GUID is {12345678-1234-1234-1234-123456789ABC}
****/
```

## int2Str
Converts an integer to the equivalent string.

```xpp
str int2Str(int integer)
```

### Parameters

| Parameter | Description             |
|-----------|-------------------------|
| integer   | The integer to convert. |

### Return value

A string representation of the integer.

### Example

```xpp
static void int2StrExample(Args _arg)
{
    print "This is int2Str, value is " + int2Str(intMax());
    print "This is int642Str, value is " + int642Str(int64Max());
}
```

## int642Str
Converts the specified *integer* parameter to the equivalent text string.

```xpp
str int642Str(int64 integer)
```

### Parameters

| Parameter | Description                       |
|-----------|-----------------------------------|
| integer   | The int64 to convert to a string. |

### Return value

The equivalent text string of the *integer* parameter.

### Example

```xpp
static void example()
{
    print "This is int2Str, value is " + int2Str(intMax());
    print "This is int642Str, value is " + int642Str(int64Max());
}
```

## num2Char
Converts an integer to the corresponding ASCII character.

```xpp
str num2Char(int figure)
```

### Parameters

| Parameter | Description                            |
|-----------|----------------------------------------|
| figure    | The integer to convert to a character. |

### Return value

The character that is represented by the specified integer.

### Example

```xpp
static void num2CharExample(Args _arg)
{
    str s;
    s = num2Char(42);
    // Prints an asterisk * -the character represented by 42.
    print s;
}
```

## num2Date
Retrieves the date that corresponds to the specified number of days after January 1, 1900.

```xpp
date num2Date(int _days)
```

### Parameters

| Parameter | Description                                                                                                                                                                                                                |
|-----------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| \_days    | The number of days after January 1, 1900 to return the date for. **Note:** The first valid date is January 1, 1901. Therefore, the **num2Date** function doesn't return a valid date unless *\_days* is more than **365**. |

### Return value

The date that is the number of days that is specified by the *\_days* parameter after January 1, 1900.

### Remarks

```xpp
num2Date(366); //Returns the date 01/01/1901 (1 January 1901).
```

## num2Str
Converts a real number to a string.

```xpp
str num2Str(real number, int character, int decimals, int separator1, int separator2)
```

### Parameters

| Parameter  | Description                                                     |
|------------|-----------------------------------------------------------------|
| number     | The real number to convert to a string.                         |
| character  | The minimum number of characters that are required in the text. |
| decimals   | The required number of decimal places.                          |
| separator1 | A **DecimalSeparator** enumeration value.                       |
| separator2 | A **ThousandSeparator** enumeration value.                      |

### Return value

A string that represents the number.

### Remarks

For the *decimals* parameter, the maximum value is **16**. If a larger number is used, this method obtains a value for the *decimals* parameter from the local computer instead. In both cases, rounding occurs. Here are the possible enumeration values for the *separator1* parameter:

-   **99** – Auto (the formatting settings of the user determine what decimal separator is used), enumeration value DecimalSeparator::Auto 
-   **1** – Dot (.), enumeration value DecimalSeparator::Dot
-   **2** – Comma (,), enumeration value DecimalSeparator::Comma

Here are the possible values for the *separator2* parameter:

-   **99** – Auto (the formatting settings of the user determine what thousand separator is used)
-   **0** – None (no thousand separator), enumeration value ThousandSeparator::None
-   **1** – Dot (.), enumeration value ThousandSeparator::Dot
-   **2** – Comma (,), enumeration value ThousandSeparator::Comma
-   **3** – Apostrophe ('), enumeration value ThousandSeparator::Apostrophe
-   **4** – Space ( ), enumeration value ThousandSeparator::Space

### Example

In the following code example, the first call to the **num2str** method provides **16** for the *decimals* parameter, and the second call provides **17**.

```xpp
static void Job_Num2Str(Args _args)
{
    real realNum = 0.1294567890123456777; // 19 decimals places.
    info(Num2Str(realNum, 0, 16, DecimalSeparator::Dot, ThousandSeparator::Space)); // 16 decimal places
    info(Num2Str(realNum, 0, 17, DecimalSeparator::Dot, ThousandSeparator::Space)); // 17 decimal places
}
```

### Output

The messages are in the following Infolog output. The first number in the output contains 16 decimal place digits, whereas the second number contains only two decimal place digits.

```xpp
Message (10:18:12)
0.1294567890123457
0.13
```

## str2Date
Converts the specified string to a **date** value.

```xpp
date str2Date(str _text, str _sequence)
```

### Parameters

| Parameter  | Description                                                                                              |
|------------|----------------------------------------------------------------------------------------------------------|
| \_text     | The string to convert to a **date** value.                                                               |
| \_sequence | A three-digit integer that describes the positions of the day, month, and year in the string to convert. |

### Return value

A **date** value.

### Remarks

Use the following values to specify the positions of the day, month, and year in the *\_sequence* parameter:

-   **Day:** 1
-   **Month:** 2
-   **Year:** 3

For example, if the sequence in the string is month, year, and then day, the *\_sequence* parameter must be **231**. A **0** (zero) date is returned if the input parameters specify an invalid date. The following two examples specify an invalid date.

```xpp
str2Date("31/12/44", 123) // Year must be four digits to reach the minimum of January 1 1901.
str2Date("31/12/2044", 213) // 213 means the month occurs first in the string, but 31 cannot be a month.
```

### Example

```xpp
static void str2DateExample(Args _arg)
{
    date d;
    d = str2Date("22/11/2007", 123);
    print d;
}
```

## str2Datetime
Generates a **utcdatetime** value from the specified string of date and time information.

```xpp
utcdatetime str2datetime( str text, int sequence )
```

### Parameters

| Parameter | Description                                                                                      |
|-----------|--------------------------------------------------------------------------------------------------|
| text      | The string to convert to a **utcdatetime** value.                                                |
| sequence  | A three-digit number that describes the sequence of the date components in the *text* parameter. |

### Return value

A **utcdatetime** value that represents the specified date and time.

### Remarks

The syntax requirements for the date portion of the *text* parameter are flexible. The variety of valid formats is the same as in the **date2str** function. Each of the following calls to **str2datetime** is valid, and all of them produce the same output.

```xpp
utc3 = str2datetime( "1985/02/25 23:04:59" ,321 );
utc3 = str2datetime( "Feb-1985-25 11:04:59 pm" ,231 );
utc3 = str2datetime( "2 25 1985 11:04:59 pm" ,123 );
```

Each component of the date time is represented by a digit in the *sequence* parameter:

-   **1** – Day
-   **2** – Month
-   **3** – Year

For example, year, month, day order is **321**. All valid values contain each of these three digits exactly one time. If the value of the *sequence* parameter isn't valid, the regional settings are used to interpret the input *text* parameter. If the input parameters describe an invalid date and time, an empty string is returned.

### Example

```xpp
static void JobTestStr2datetime( Args _args )
{
    utcdatetime utc3;
    str sTemp;
    utc3 = str2datetime( "1985/02/25 23:04:59" ,321 );
    sTemp = datetime2str( utc3 );
    print( "sTemp == " + sTemp );
}
```

## str2Enum
Retrieves the enum element for which the localized **Label** property value matches the input string.

```xpp
enum str2Enum(enum _type, str _text)
```

### Parameters

| Parameter | Description                                                              |
|-----------|--------------------------------------------------------------------------|
| \_type    | A variable that is declared of the **enum** type.                        |
| \_text    | The localized **Label** property text of the target element in the enum. |

### Return value

An element of the target enum, which also represents an int.

### Remarks

The related function **enum2str** returns the value of a **Label** property from one element in the enum. The value that is returned by **enum2str** function can be the input for the *\_type* parameter of the **str2enum** function. An appropriate value for the *\_text* parameter is **enum2Str(BankAccountType::SavingsAccount)**. Each element of an enum has a **Name** property and a **Label** property. In a fresh install, the **Name** values are almost always English words. In the English edition, the **Label** property value is almost always the same as the **Name** value. However, in non-English editions, the **Label** values are localized and therefore don't match the **Name** values.

### Example

To avoid string mismatches that are caused by localization to other spoken languages, we recommend that you use the **enum2str** function to generate the input into the **str2enum** function. The following example shows the appropriate way to use the **str2enum** function together with the **enum2str** function.

```xpp
static void str2Enum_AcrossLangs(Args _arg)
{
    BankAccountType bat;
    str sEnumValueLabelLocalized;
    int nInt;
    // enum2str.
    sEnumValueLabelLocalized = enum2str(BankAccountType::SavingsAccount);
    info("Localized friendly string: "
        + sEnumValueLabelLocalized);
    // str2enum.
    bat = str2Enum(bat, sEnumValueLabelLocalized);
    nInt = bat;
    info("nInt = " + int2str(nInt));
    /********** Actual output:
    Message (04:32:12 pm)
    Localized friendly string: Savings account
    nInt = 1
    **********/
}
```

## str2Guid
Converts a string to a GUID object.

```xpp
Guid str2Guid(str text)
```

### Parameters

| Parameter | Description                      |
|-----------|----------------------------------|
| guid      | A string that represents a GUID. |

### Return value

A GUID that is represented by the input string.

### Remarks

For example, a valid value for the *guid* parameter is **{12345678-1234-abCD-3456-123456789012}**, either with or without the braces.

## str2Int
Converts a string to the equivalent integer.

```xpp
int str2Int(str _text)
```

### Parameters

| Parameter | Description                          |
|-----------|--------------------------------------|
| \_text    | The string to convert to an integer. |

### Return value

The integer equivalent of the specified string.

### Example

```xpp
static void str2IntExample(Args _arg)
{
    int i;
    i = str2Int("1234567890");
    print "i = " + int2Str(i);
}
```

## str2Int64
Converts a string into an **Int64** value.

```xpp
int str2Int64(str text)
```

### Parameters

| Parameter | Description            |
|-----------|------------------------|
| text      | The string to convert. |

### Return value

The **Int64** value of the specified string.

### Example

```xpp
static void str2Int64Example(Args _args)
{
    str myStr;
    str tooBig;
    Int64 myInt64;
    myStr = "1234567890";
    tooBig = int642str(int64Max()+1);
    myInt64 = str2Int64(mystr);
    print strfmt ("int64: %1",myInt64);
    myInt64 = str2Int64(tooBig);
    print strfmt ("Too big int64: %1",myInt64);
}
```

## str2Num
Converts a string to a real number.

```xpp
real str2Num(str _text)
```

### Parameters

| Parameter | Description                             |
|-----------|-----------------------------------------|
| \_text    | The string to convert to a real number. |

### Return value

The real number if the specified string contains a valid number; otherwise, **0** (zero).

### Remarks

The following examples show how this function is used.

```xpp
str2Num("123.45") returns the value 123.45.
str2Num("a123") returns the value 0.0.
str2Num("123a") returns the value 123.00.
```

Scanning occurs from left to right and ends when a character can't be converted to part of a real number.

### Example

```xpp
static void str2NumToReal(Args _arg)
{
    real r;
    str s;
    r = str2Num("3.15");
    s = strFmt("r = %1", r);
    info(s);
}
/*** Infolog output.
Message_@SYS14327 (02:36:12 pm)
r = 3.15
***/

static void str2NumExponentialSyntax(Args _args)
{
    Qty qty1, qty2, qty3;
    qty1 = str2num('1e-3'); // Bad syntax by the user.
    qty2 = str2num('1.e-3');
    qty3 = str2num('1.0e-3');
    info(strfmt('Result: %1; Expected: %2', num2str(qty1, 0,3,2,0), '0.001'));
    info(strfmt('Result: %1; Expected: %2', num2str(qty2, 0,3,2,0), '0.001'));
    info(strfmt('Result: %1; Expected: %2', num2str(qty3, 0,3,2,0), '0.001'));
}
/*** Infolog output. The first result differs from expectations.
Message_@SYS14327 (02:20:55 pm)
Result: 1,000; Expected: 0.001
Result: 0,001; Expected: 0.001
Result: 0,001; Expected: 0.001
***/
```

## str2Time
Converts a string to a **timeOfDay** value.

```xpp
int str2Time(str _text)
```

### Parameters

| Parameter | Description                                                        |
|-----------|--------------------------------------------------------------------|
| \_text    | The time to use to calculate the number of seconds since midnight. |

### Return value

The number of seconds between midnight and the *\_text* parameter; otherwise, **-1**.

### Remarks

```xpp
str2Time("05:01:37") //Returns the value 18097.
str2Time("7 o'clock") //Returns the value -1.
```

### Example

```xpp
static void str2TimeExample(Args _arg)
{
    int i;
    i = str2Time("11:30");
    print i;
}
```

## time2Str
Converts a **timeOfDay** value to a string that includes hours, minutes, and seconds.

```xpp
str time2Str(int _time, int _separator, int _timeFormat)
```

### Parameters

| Parameter    | Description                                                                                                                       |
|--------------|-----------------------------------------------------------------------------------------------------------------------------------|
| \_time       | A **timeOfDay** value.                                                                                                            |
| \_separator  | A **TimeSeparator** enumeration value that indicates the characters between the hours, minutes, and seconds in the output string. |
| \_timeFormat | A **TimeFormat** enumeration value that indicates whether a 12-hour clock or a 24-hour clock is used.                             |

### Return value

A string that represents the specified time.

### Remarks

The value of the *\_time* parameter is the number of seconds since midnight.

### Example

```xpp
static void TimeJob4(Args _args)
{
    timeOfDay theTime = timeNow();
    info( time2Str(theTime, TimeSeparator::Colon, TimeFormat::AMPM) );
}
/**
Message (04:33:56 pm)
04:33:56 pm
**/
```

## uint2Str
Converts an integer to a string. The assumption is that the integer is unsigned.

```xpp
str uint2Str(int integer)
```

### Parameters

| Parameter | Description             |
|-----------|-------------------------|
| integer   | The integer to convert. |

### Return value

The string equivalent to the specified unsigned integer.

### Remarks

Use this function instead of the **int2str** function for very large integers, such as record IDs.

```xpp
info(int2str(3123456789)); //returns -1171510507 as a string.
info(uint2str(3123456789)); //returns 3123456789 as a string.
```




[!INCLUDE[footer-include](../../../includes/footer-banner.md)]