---
# required metadata

title: X++ business run-time functions
description: This wiki describes the business run-time functions.
author: RobinARH
manager: AnnBe
ms.date: 2016-02-04 22 - 11 - 18
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 31281
ms.assetid: e6cdd25b-c364-4b23-b33a-2792a6d0f3ef
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.dyn365.intro: Feb-16
ms.dyn365.version: AX 7.0.0

---

# X++ business run-time functions

This wiki describes the business run-time functions.

These functions enter financial data and calculate formulas.

## cTerm
Calculates the number of periods that are required for the current investment value to yield a target value.

### Syntax

    real cTerm(real interest, real future_value, real current_value)

### Parameters

| Parameter      | Description                   |
|----------------|-------------------------------|
| interest       | The interest rate.            |
| future\_value  | The target value.             |
| current\_value | The current investment value. |

### Return value

The number of periods that are required in order to reach *future\_value*.

### Remarks

The *current\_value* and *future\_value* parameters must have the same prefixed sign (plus or minus).

### Example

    static void cTermExample(Args _arg)
    {
        real r;
        ;
        r = cTerm(10.0, 500.00, 100.00);
        print "The cTerm is " + num2Str(r, 2, 2, 1, 1);
        pause;
    }

ddb
---

Calculates the accelerated depreciation of an asset.

### Syntax

    real ddb(real price, real scrap, real life, int period)

### Parameters

| Parameter | Description                                                |
|-----------|------------------------------------------------------------|
| price     | The purchase price of the asset.                           |
| scrap     | The residual value of the asset that has been written off. |
| life      | The expected lifetime of the asset.                        |
| period    | The period to calculate depreciation over.                 |

### Return value

The depreciation of the asset.

### Remarks

The book value for a specific period is equal to the purchase price minus the accumulated depreciation for previous periods:

-   Book value for Period 1 = Price
-   Book value for Period 2 = Book value for Period 1 – Depreciation for Period 1
-   Book value for Period n = Book value for Period (n–1) – Depreciation for Period (n–1)

There are three variations for the calculation of depreciation: If Period &gt; Life:

-   Depreciation = 0

If (Book value for Period n) – ((Book value for Period n) × 2 ÷ Life) &lt; Residual value:

-   Depreciation = (Book value for Period n) – Residual value

In all other cases: Depreciation = (Book value for Period n) × 2 ÷ Life The **syd** and **sln** functions also calculate the depreciation of an asset. The **syd** and **ddb** functions enables higher depreciation for the earlier years, whereas **sln** calculates a linear depreciation.

    ddb(12000,2000,10,1); //Returns the value 2400.
    ddb(12000,2000,10,3); //Returns the value 1536.

dg
--

Calculates the contribution ratio, which is based on the sales price and the purchase price. If the value of the *sale* parameter is **0.0**, the calculation can't be done.

### Syntax

    real dg(real sale, real purchase)

### Parameters

| Parameter | Description         |
|-----------|---------------------|
| sale      | The sale price.     |
| purchase  | The purchase price. |

### Return value

The contribution ratio.

### Remarks

    dg(1000,300); //Returns the value 0.7.
    dg(100,30); //Returns the value 0.7.
    dg(20000, 11000); //Returns the value 0.45.

fV
--

Calculates the future value of an investment.

### Syntax

    real fV(real amount, real interest, real life)

### Parameters

| Parameter | Description                                     |
|-----------|-------------------------------------------------|
| amount    | The amount that was paid in during each period. |
| interest  | The interest rate.                              |
| life      | The number of investment periods.               |

### Return value

The future value of the investment.

### Remarks

    fV(100,0.14,10); //Returns the value 1933.73.
    fV(400,0.10,5); //Returns the value 2442.04.

idg
---

Calculates the sale price, based on the purchase price and the contribution ratio.

    real idg(real purchase, real contribution_ratio)

### Parameters

| Parameter           | Description             |
|---------------------|-------------------------|
| purchase            | The purchase price.     |
| contribution\_ratio | The contribution ratio. |

### Return value

The sale price.

### Remarks

If the contribution ratio is equal to **1.0**, the calculation can't be done. The **idg** function is the inverse of the **dg** function.

    idg(300,0.7); //Returns the value 1000.
    idg(11000,0.45); //Returns the value 20000.

## intvMax
Retrieves the number of intervals for the specified period when the period is divided into parts as specified by the *func* parameter.

    int intvMax(date input_date, date ref_date, int func)

### Parameters

| Parameter   | Description                                                                |
|-------------|----------------------------------------------------------------------------|
| input\_date | The end of the period, which must be later than the *ref\_date* parameter. |
| ref\_date   | The start of the period.                                                   |
| func        | A **IntvScale** system enumeration value that indicates the division unit. |

### Remarks

Here are the possible values for the *func* parameter:

-   None
-   YearMonthDay
-   YearMonth
-   Year
-   MonthDay
-   Month
-   Day
-   YearQuarter
-   Quarter
-   YearWeek
-   Week
-   WeekDay

### Example

    static void intvMaxExample()
    {
        date refDate = str2Date("4/9/2007", 213);
        date inputDate = str2Date("10/5/2007", 213);
        int numberOfIntervals;
        ;
        numberOfIntervals = intvMax(inputDate, refDate, intvScale::YearMonth);
        print numberOfIntervals;
        pause;
    }

## intvName
Returns the name of the interval that is the specified number of intervals ahead of the specified date.

    str intvName(date input_date, int col, enum func)

### Parameters

| Parameter   | Description                                                                                 |
|-------------|---------------------------------------------------------------------------------------------|
| input\_date | A date in the first interval.                                                               |
| col         | The number of intervals ahead of the date that is specified by the *input\_date* parameter. |
| func        | An **intvScale** enumeration value.                                                         |

### Return value

The name of the interval.

### Remarks

For example, if the *func* parameter is the **IntvScale::WeekDay** enumeration value, this method returns the name of the weekday. If the *func* parameter is the **IntvScale::Week** enumeration value, this method returns a string that contains the number of the week.

### Example

    static void intvNameExample(Args _args)
    {
        date refDate = 2672010;
        str name;
        ;
        name = intvName(refDate, 3,  intvScale::WeekDay);
        Global::info(strfmt("%1 is the output, which indicates the day of the week 3 days after 26\7\2010.", name));
    }
    /**** Infolog display.
    Message (09:56:55 am)
    Thu is the output, which indicates the day of the week 3 days after 2672010.
    ****/

## intvNo
Calculates the number of intervals between two dates when you divide the time into the specified intervals.

### Syntax

    int intvNo(date input_date, date ref_date, int func)

### Parameters

| Parameter   | Description                                    |
|-------------|------------------------------------------------|
| input\_date | A date that indicates the end of the period    |
| ref\_date   | A date that indicates the start of the period. |
| func        | An **intvScale** enumeration value.            |

### Return value

The number of intervals between the dates that are specified by the *ref\_date* and *input\_date* parameters.

### Example

    static void intvNoExample(Args _args)
    {
        date inputDate = str2Date("1/1/2007", 213);
        date refDate = str2Date("3/1/2007", 213);
        int noOfIntervals;
        ;
        noOfIntervals = intvNo(refDate, inputDate, intvScale::Month);
        print noOfIntervals;
        pause;
        //noOfIntervals now holds the difference in months between March and January (2).
    }

## intvNorm
Returns the normalized date for the period.

### Syntax

    date intvNorm(date input_date, date ref_date, int func)

### Parameters

| Parameter   | Description                                                                                              |
|-------------|----------------------------------------------------------------------------------------------------------|
| input\_date | The end of the period, which must be later than the date that is specified by the *ref\_date* parameter. |
| ref\_date   | The start of the period.                                                                                 |
| func        | An **intvScale** enumeration value that indicates the interval division unit.                            |

### Return value

The normalized date for the period.

### Remarks

The returned date will equal the date of the first day in the interval in which the date that is specified by the *ref\_date* parameter exists.

### Example

    static void example()
    {
        print intvNorm(today(), today()-1, IntVScale::WeekDay);
        pause;
    }

pmt
---

Calculates the amount that must be paid every period to repay a loan.

### Syntax

    real pmt(real principal, real interest, real life)

### Parameters

| Parameter | Description                                                               |
|-----------|---------------------------------------------------------------------------|
| principal | The amount that was originally borrowed.                                  |
| interest  | The interest that is applied each period to the amount that was borrowed. |
| life      | The number of periods that the loan is repaid over.                       |

### Return value

The amount that must be paid every period.

### Remarks

The *life* and *interest* parameters must be expressed in the same time units. The value of the *life* parameter must be more than **0.0**.

### Example

    pmt(4000,0.14,4); //Returns the value 1372.82.
    pmt(10000,0.10,20); //Returns the value 1174.60.

pt
--

Retrieves the sum of a number plus a specified percentage of that number.

### Syntax

    real pt(real amount, real percentage)

### Parameters

| Parameter  | Description                |
|------------|----------------------------|
| amount     | The original number.       |
| percentage | The percentage supplement. |

### Return value

The number that is equal to ((*amount *× *percentage*) + *amount*).

### Remarks

    pt(2000.0,0.10); //Returns the value 2200.0.
    pt(20.0,0.10); //Returns the value 22.0.

pv
--

Calculates the present value of an annuity, where an amount is received over multiple periods and the interest rate is deducted for each period.

### Syntax

    real pv(real amount, real interest, real life)

### Parameters

| Parameter | Description                                                                             |
|-----------|-----------------------------------------------------------------------------------------|
| amount    | The amount that is paid during each period.                                             |
| interest  | The interest rate.                                                                      |
| life      | The number of times that the value that is specified by the *amount* parameter is paid. |

### Return value

The current value of an annuity.

### Remarks

    pv(300,0.14,4); //Returns the value 874.11.

## rate
Calculates the interest that is required for the current investment value to attain the future value over the specified number of periods.

### Syntax

    real rate(real _future_value, real _current_value, real _terms)

### Parameters

| Parameter        | Description                                      |
|------------------|--------------------------------------------------|
| \_future\_value  | The future value of the investment.              |
| \_current\_value | The current value of the investment.             |
| \_terms          | The number of periods that the investment spans. |

### Return value

The calculated interest rate.

### Remarks

    rate(10000,1000,20); //Returns the value 0.12.

sln
---

Retrieves the constant depreciation amount for the specified asset for each depreciation period.

### Syntax

    real sln(real price, real scrap, real life)

### Parameters

| Parameter | Description                                              |
|-----------|----------------------------------------------------------|
| price     | The purchase price of the asset.                         |
| scrap     | The scrap value of the asset.                            |
| life      | The number of periods in the expected life of the asset. |

### Return value

The depreciation amount.

### Example

    static void slnExample(Args _arg)
    {
        real r;
        ;
        r = sln(100.00, 50.00, 50.00);
        print r;
        pause;
    }

syd
---

Calculates the depreciation of an asset over a specified period.

### Syntax

    real syd(real _price, real _scrap, real _life, int _period)

### Parameters

| Parameter | Description                                             |
|-----------|---------------------------------------------------------|
| \_price   | The purchase price of the asset.                        |
| \_scrap   | The scrap value of the asset.                           |
| \_life    | The expected life of the asset (the number of periods). |
| \_period  | The period to calculate depreciation for.               |

### Return value

The amount of depreciation over the specified period.

### Remarks

In contrast to the **sln** function, the **syd** function can allow for an accelerated depreciation of the asset. As with the **ddb** function, this enables higher depreciation during the early periods of the life of an asset.

### Example

In the following examples, the periodic depreciation is calculated for an asset that has a purchase price of 10,000, a scrap value of 2,000, and a life of 5. In comparison, **sln(10000,2000,5)** would calculate 1600.00 for each period.

    // Returns the value 2666.67 (for the 1st period).
    syd(10000,2000,5,1);
    // Returns the value 2133.33 (for the 2nd period).
    syd(10000,2000,5,2);
    // Returns the value 1600.00 (for the 3rd period).
    syd(10000,2000,5,3);
    // Returns the value 1066.67 (for the 4th period).
    syd(10000,2000,5,4);
    // Returns the value 533.33 (for 5th - and final- period).
    syd(10000,2000,5,5);

## term
Calculates the number of periods that an investment must run for.

### Syntax

    real term(real amount, real interest, real future_value)

### Parameters

| Parameter     | Description                                             |
|---------------|---------------------------------------------------------|
| amount        | The amount of the periodic investment.                  |
| interest      | The interest rate for each period.                      |
| future\_value | The future value that is anticipated for the investment |

### Return value

The number of periods that the investment must run for.

### Example

    static void termExample(Args _args)
    {
        print term(400,0.08,5000);  //returns the value '9.01'.
        print term(100,0.14,3000);  //returns the value '12.58'.
        pause;
    }

