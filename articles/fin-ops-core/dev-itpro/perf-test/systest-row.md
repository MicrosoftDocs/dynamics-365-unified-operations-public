---
title: SysTestRow attribute for testing multiple values
description: This topic outlines the SysTestRow attribute that can be used with SysTest methods to test multiple values.
author: jorisdg
ms.date: 01/13/2022
ms.topic: article
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: jorisde
ms.search.validFrom: 2022-01-13

---

# SysTestRow attribute for testing multiple values

[!include [banner](../includes/banner.md)]


Sometimes, tests must test multiple input values for the same feature. To make troubleshooting and reporting easier, you should avoid testing multiple things in the same test method. Instead of creating multiple methods, you can use the **SysTestRow** attribute that the SysTest framework now supports. This attribute works like the **DataRow** attribute in C\#.

> [!NOTE]
> The **SysTestRow** attribute is available in version 10.0.25 and later.

## SysTestRow example

In this example, you have a method that squares a number.

```xpp
public class MyMath
{
    public static int square(int _i)
    {
        return _i * _i;
    }
}
```

You want to test this method by using a few different numbers. Among these numbers, you want to include special cases that should work. Therefore, you write the following test method that uses the **SysTestRow** attribute to test multiple values in the same method.

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

Microsoft Visual Studio shows each test row as a separate numbered result.

- `SquareTests#1`
- `SquareTests#2`
- `SquareTests#3`
- `SquareTests#4`
- `SquareTests#5`

## SysTestRowInactive

Any **SysTestRow** attribute can be replaced with the **SysTestRowInactive** attribute. In this case, Visual Studio shows the test row as a disabled test.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
