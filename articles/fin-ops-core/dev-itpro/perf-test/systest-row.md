---
title: SysTestRow attribute to test multiple values
description: This topic outlines the systestrow attributes that can be used with SysTest methods for the purpose of testing multiple values.
author: jorisdg
ms.date: 01/22/2019
ms.topic: article
ms.prod: 
ms.technology: 

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: tfehr
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jorisde
ms.search.validFrom: 2017-11-15
ms.dyn365.ops.version: AX 7.0.0

---

# Unit Testing Multiple Values

[!include [banner](../includes/banner.md)]

Sometimes tests have to test multiple input values for the same feature. It is good practice to not test multiple things in the same test method, because that makes troubleshooting and reporting more difficult. Instead of creating multiple methods, the SysTest framework now supports the **SysTestRow** attribute similar to the **DataRow** attribute in **C#**.

## SysTestRow

In this example we have a method that squares a number, which we would like to test.

```xpp
public class MyMath
{
    public static int square(int _i)
    {
        return _i * _i;
    }
}
```

We may want to test this method with a few different numbers that include special cases that should work. We can write the following test method which uses the **SysTestRow** attribute to test multiple values using the same method.

```xpp
public class MathTests extends SysTestCase
{
    [SysTestMethod,
    SysTestRow(0,0),
    SysTestRow(1,1),
    SysTestRow(-1, 1),
    SysTestRow(4, 16),
    SysTestRow(-4, 16)]
    public void SquareTests(int _value, int _result)
    {
        int testResult = MyMath::square(_value);

        this.assertEquals(_result, testResult);
    }
}
```

**Visual Studio** will show each test row as a separate numbered result.

- `SquareTests#1`
- `SquareTests#2`
- `SquareTests#3`
- `SquareTests#4`
- `SquareTests#5`

## SysTestRowInactive

Any **SysTestRow** attribute can be replaced with the **SysTestRowInactive** attribute, causing **Visual Studio** to show that test row as a disabled test.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]