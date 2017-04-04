---
# required metadata

title: X++ math run-time functions
description: This topic describes the math run-time functions.
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
ms.reviewer: RobinARH
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 31361
ms.assetid: 8982f158-f638-46d7-b3f7-ba8cfd356d57
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# X++ math run-time functions

This topic describes the math run-time functions.

These functions perform mathematical calculations.

abs
---

Retrieves the absolute value of a real number. Examples:

-   **abs(-100.0)** returns the value **100.0**.
-   **abs(30.56)** returns the value **30.56**.

### Syntax

    real abs(real arg)

### Parameters

| Parameter | Description                              |
|-----------|------------------------------------------|
| arg       | The number to get the absolute value of. |

### Return value

The absolute value of *arg*.

### Example

    static void absExample(Args _args)
    {
        real r1;
        real r2;
        ;
        r1 = abs(-3.14);
        r2 = abs(3.14);
        if (r1 == r2)
        {
            print "abs of values are the same";
            pause;
        }
    }

## acos
Retrieves the arc cosine of a real number. **Note:** Argument values that are outside the -1 to 1 range cause the following run-time error: "Argument for trigonometric function out of range."

### Syntax

    real acos(real arg)

### Parameters

| Parameter | Description                               |
|-----------|-------------------------------------------|
| arg       | The number to retrieve the arc cosine of. |

### Return value

The arc cosine of *arg*.

### Example

    static void acosExample(Args _args)
    {
        real r;
        str  s;
        ;
        r = acos(0.0);
        s = strFmt("The arc cosine of 0.0 is %1 ", r);
        print s;
        pause;
    }

## asin
Retrieves the arc sine of a real number. **Note:** Argument values that are outside the -1 to 1 range cause the following run-time error: "Argument for trigonometric function out of range."

### Syntax

    real asin(real arg)

### Parameters

| Parameter | Description                               |
|-----------|-------------------------------------------|
| arg       | The number to calculate the arc sine for. |

### Return value

The arc sine of the specified number.

### Remarks

**aSin(0.36)** returns **0.37**.

## atan
Retrieves the arc tangent of a real number.

### Syntax

    real atan(real arg)

### Parameters

| Parameter | Description                                  |
|-----------|----------------------------------------------|
| arg       | The number to calculate the arc tangent for. |

### Return value

The arc tangent of the specified number.

### Remarks

**aTan(0.36)** returns **0.35**.

### Example

    static void atanExample(Args _args)
    {
        real r;
        ;
        r = atan(1.0);
        print strFmt("The Arc Tangent of 1.0 is %1", r);
        pause;
    }

## corrFlagGet
Retrieves the state of the correction flag for a real number.

### Syntax

    int corrFlagGet(real arg)

### Parameters

| Parameter | Description                         |
|-----------|-------------------------------------|
| arg       | The flag to retrieve the state for. |

### Return value

A non-zero value if the flag is set; **0** (zero) if the flag is cleared.

### Example

The following example displays **1**.

    static void corrFlagGetExample(Args _args)
    {
        real rr;
        rr = corrFlagSet(0.36,2);
        print(corrFlagGet(rr));
    }

## corrFlagSet
Controls the correction flag for a real number.

### Syntax

    real corrFlagSet(real real, int arg)

### Parameters

| Parameter | Description                                                       |
|-----------|-------------------------------------------------------------------|
| real      | The number in which to turn the correction flag on or off.        |
| arg       | **0** to turn the flag off; a non-zero value to turn the flag on. |

### Return value

**0** if the flag is now off; a non-zero value if the flag is now on.

cos
---

Retrieves the cosine of a real number.

### Syntax

    real cos(real arg)

### Parameters

| Parameter | Description                        |
|-----------|------------------------------------|
| arg       | The number to find the cosine for. |

### Return value

The cosine of the specified number.

### Remarks

The value of the *arg* parameter must be in radians.

### Example

The following code example displays **0.76**.

    static void cosExample(Args _arg)
    {
        real r;
        ;
        r = cos(15);
        print strFmt("Cos of 15 is %1", r);
        pause;
    }

## cosh
Retrieves the hyperbolic cosine of a real number. **Note:** Argument values that are outside the -250 to 250 range cause the following run-time error: "Argument for trigonometric function out of range."

### Syntax

    real cosh(real arg)

### Parameters

| Parameter | Description                                        |
|-----------|----------------------------------------------------|
| arg       | The hyperbolic number to calculate the cosine for. |

### Return value

The hyperbolic cosine of the specified number.

### Remarks

The value of the *arg* parameter must be in radians.

### Example

    static void coshExample(Args _arg)
    {
        real r;
        ;
        r = cosh(0.1);
        print "The hyperbolic cosine of 0.1 is " + num2Str(r, 2, 2, 1, 1);
        pause;
    }

## decRound
Rounds a number to the specified number of decimal places.

### Syntax

    real decRound(real figure, int decimals)

### Parameters

| Parameter | Description                               |
|-----------|-------------------------------------------|
| figure    | The number to round.                      |
| decimals  | The number of decimal places to round to. |

### Return value

The value of the specified number, rounded to the specified number of decimal places.

### Remarks

The value of the *decimals* parameter can be positive, 0 (zero), or negative.

-   **decRound(1234.6574,2)** returns the value **1234.66**.
-   **decRound(1234.6574,0)** returns the value **1235**.
-   **decRound(1234.6574,-2)** returns the value **1200**.
-   **decRound(12345.6789,1)** returns the value **12345.70**.
-   **decRound(12345.6789,-1)** returns the value **12350.00**.

exp
---

Retrieves the natural antilogarithm of the specified real number.

### Syntax

    real exp(real arg)

### Parameters

| Parameter | Description                                                 |
|-----------|-------------------------------------------------------------|
| arg       | The real number to calculate the natural antilogarithm for. |

### Return value

The natural antilogarithm of the specified real number.

### Remarks

The calculated natural antilogarithm is the natural logarithm e raised to the power that is indicated by the *arg* parameter.

### Example

    static void expExample(Args _arg)
    {
        real r1;
        real r2;
        ;
        r1 = exp(2.302585093);
        r2 = exp10(2.302585093);
        print strFmt("exp of 2.302585093 is %1", r1);
        print strFmt("exp10 of 230258 is %1", r2);
        pause;
    }

## exp10
Retrieves the base-10 antilogarithm of the specified real number.

### Syntax

    real exp10(real decimal)

### Parameters

| Parameter | Description                                                 |
|-----------|-------------------------------------------------------------|
| decimal   | The real number to calculate the base-10 antilogarithm for. |

### Return value

The 10-based antilogarithm of the value of the *decimal* parameter.

### Example

    static void exp10Example(Args _arg)
    {
        real r1;
        real r2;
        ;
        r1 = exp(2.302585093);
        r2 = exp10(2.302585093);
        print strFmt("exp of 2.302585093 is %1", r1);
        print strFmt("exp10 of 230258 is %1", r2);
        pause;
    }

## frac
Retrieves the decimal part of a real number.

### Syntax

    real frac(real decimal)

### Parameters

| Parameter | Description                                       |
|-----------|---------------------------------------------------|
| decimal   | The real number to retrieve the decimal part for. |

### Return value

The decimal part of the specified number.

### Remarks

**frac(12.345)** returns the value **0.345**.

## log10
Retrieves the 10-digit logarithm of a real number.

### Syntax

    real log10(real arg)

### Parameters

| Parameter | Description                                |
|-----------|--------------------------------------------|
| arg       | The number to calculate the logarithm for. |

### Return value

The base-10 logarithm of the specified number.

### Remarks

**log10(200)** returns the value **2.30**.

## logN
Retrieves the natural logarithm of the specified real number.

### Syntax

    real logN(real arg)

### Parameters

| Parameter | Description                                        |
|-----------|----------------------------------------------------|
| arg       | The number to calculate the natural logarithm for. |

### Return value

The natural logarithm of the specified number.

### Remarks

**logN(45)** returns the value **3.81**.

max
---

Retrieves the larger of two specified values.

    anytype max(anytype object1, anytype object2)

### Parameters

| Parameter | Description       |
|-----------|-------------------|
| object1   | The first value.  |
| object2   | The second value. |

### Return value

The larger of the two values that are specified by the *object1* and *object2* parameters.

### Remarks

-   **max(12.0,12.1)** returns the value **12.1**.
-   **max(2,33)** returns the value **33**.

min
---

Retrieves the smaller of two specified values.

    anytype min(anytype object1, anytype object2)

### Parameters

| Parameter | Description       |
|-----------|-------------------|
| object1   | The first value.  |
| object2   | The second value. |

### Return value

The smaller of the two values that are specified by the *object1* and *object2* parameters.

### Remarks

**min(2,33**) returns the value **2**.

### Example

    static void minExample(Args _arg)
    {
            anytype a;
            real r = 3.0;
            real s = 2.0;

            a = min(r, s);
            print num2Str(a, 1, 2, 1, 1) + " is less than the other number.";
    }

## power
Raises a real number to the power of another real number.

### Syntax

    real power(real arg, real exponent)

### Parameters

| Parameter | Description                                                                 |
|-----------|-----------------------------------------------------------------------------|
| arg       | The number to calculate the power of.                                       |
| exponent  | The number to raise the number that is specified by the *arg* parameter to. |

### Return value

The real number that is the number specified by the *arg* parameter to the power of the number specified by the *exponent* parameter.

### Remarks

-   **power(5.0,2.0)** returns the value **25.0**.
-   **power(4.0,0.5)** returns the value **2.0**.

## round
Rounds a real number to the nearest multiple of another real number.

### Syntax

    real round(real _arg, real _decimals)

### Parameters

| Parameter  | Description                                                                          |
|------------|--------------------------------------------------------------------------------------|
| \_arg      | The original number.                                                                 |
| \_decimals | The number that the value of the *\_arg* parameter must be rounded to a multiple of. |

### Return value

The number that is a multiple of the value specified by the *\_decimals* parameter and is closest to the value specified by the *\_arg* parameter.

### Remarks

To round a real number to a specified number of decimal places, use the [decround function](http://msdn.microsoft.com/library/03bd2ea2-414e-43e0-ba05-f5db1a943b91(AX.60).aspx).

### Remarks

-   **round(123.45,5.00)** returns the value **125.00**.
-   **round(7.45,1.05)** returns the value **7.35**.
-   **round(23.9,5.0)** returns the value **25.00**.
-   **round(26.1,5.0)** returns the value **25.00**.

sin
---

Retrieves the sine of a real number.

### Syntax

    real sin(real _arg)

### Parameters

| Parameter | Description                           |
|-----------|---------------------------------------|
| \_arg     | The number to calculate the sine for. |

### Return value

The sine of the specified real number.

### Remarks

The value of the *\_arg* parameter must be in radians.

### Example

    static void sinExample(Args _arg)
    {
        real angleDegrees = 15.0;
        real angleRadians;
        real pi = 3.14;
        real r;
        ;
        angleRadians = pi * angleDegrees / 180;
        r = sin(angleRadians);
        print "sin of a "
            + num2Str(angleDegrees, 2, 2, 1, 1)
            + " degree angle is "
            + num2Str(r, 2, 10, 1, 1);
        pause;
    }

## sinh
Retrieves the hyperbolic sine of a real number.

### Syntax

    real sinh(real _arg)

### Parameters

| Parameter | Description                                      |
|-----------|--------------------------------------------------|
| \_arg     | The number to calculate the hyperbolic sine for. |

### Return value

The hyperbolic sine of the specified real number.

### Remarks

Values for the *\_arg* parameter that are outside the -250 to 250 range cause the following run-time error: "Argument for trigonometric function out of range."

### Example

The following example illustrates the **sinh** function.

    static void sinhExample(Args _arg)
    {
        real angleDegrees = 45.0;
        real angleRadians;
        real pi = 3.14;
        real r;
        ;
        angleRadians = pi * angleDegrees / 180;
        r = sinh(angleRadians);
        print "sinh of a "
        + num2Str(angleDegrees, 2, 2, 1, 1)
        + " degree angle is "
        + num2Str(r, 2, 15, 1, 1);
        pause;
    }

tan
---

Retrieves the tangent of a real number.

### Syntax

    real tan(real arg)

### Parameters

| Parameter | Description                                   |
|-----------|-----------------------------------------------|
| arg       | The real number to calculate the tangent for. |

### Return value

The tangent of the specified real number.

### Remarks

Values for the *arg* parameter that are outside the -250 to 250 range cause the following run-time error: "Argument for trigonometric function out of range."

### Example

The following example illustrates the **tan** function.

    static void tanExample(Args _arg)
    {
        real r;
        ;
        r = tan(250);
        print strFmt("Tan of 250 is %1", r);
        pause;
    }

## tanh
Retrieves the hyperbolic tangent of a real number.

### Syntax

    real tanh(real _arg)

### Parameters

| Parameter | Description                                         |
|-----------|-----------------------------------------------------|
| \_arg     | The number to calculate the hyperbolic tangent for. |

### Return value

The hyperbolic tangent of the specified real number.

### Example

The following example illustrates the **tanh** function.

    static void tanhExample(Args _arg)
    {
        real r;
        ;
        r = tanh(0.1);
        print "The hyperbolic tangent of angle 0.1 is "
        + num2Str(r, 2, 10, 1, 1);
        pause;
    }

## trunc
Truncates a real number by removing any decimal places.

### Syntax

    real trunc(real _decimal)

### Parameters

| Parameter | Description             |
|-----------|-------------------------|
| \_decimal | The number to truncate. |

### Return value

A number that is equivalent to the value of the *\_decimal* parameter after the decimal places have been removed.

### Remarks

This function always rounds numbers down to a complete integer.

### Example

The following example truncates 2.7147 to 2.00.

    static void truncExample(Args _arg)
    {
        real r;
        ;
        r = trunc(2.7147);
        print strFmt("r = %1",  r);
        pause;
    }

