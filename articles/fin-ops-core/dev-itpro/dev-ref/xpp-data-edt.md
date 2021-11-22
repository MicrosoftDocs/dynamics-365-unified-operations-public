---
title: X++ extended data types
description: This topic describes extended data types in X++.
author: RobinARH
ms.date: 06/17/2019
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: tfehr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# X++ extended data types

[!include [banner](../includes/banner.md)]

This topic describes extended data types in X++. 

*Extended data types* are user-defined types that are based on the **boolean**, **int**, **int64**, **real**, **str**, and **date** primitive data types, and on the **container** composite type. An EDT is a primitive data type or container that has a supplementary name and additional properties. For example, you can create a new EDT that is named **Name** and base it on a string. You can then use the new EDT in variable and field declarations in the development environment. 

You can also base EDTs on other EDTs. EDTs are standard data types, but they have a specific name and additional properties. EDTs undergo the same value and type [conversions](xpp-conversion-run-time-functions.md) as the standard data types that they are based on. Here are the benefits of EDTs:

-   Code is easier to read, because variables have a meaningful data type. For example, the data type is **Name** instead of **str**.
-   The properties that you set for an EDT are used by all instances of that type. Therefore, EDTs help reduce work and promote consistency. For example, account numbers (**AccountNum** data type) have the same properties throughout the system.
-   You can create hierarchies of EDTs. The EDTs can inherit the appropriate properties from the parent, and you can change other properties. For example, the **ItemCode** data type is used as the basis for the **MarkupItemCode** and **PriceDiscItemCode** data types.

## Create an EDT

This feature isn't implemented as a language construct. To create an EDT, follow these steps.

1.  In Solution Explorer, right-click on the project, point to **Add**, and then click **New item**.
2.  In the **Add New Item** dialog box, select **Installed** and then **Artifacts** in the left pane.
3.  In the middle pane, select the EDT type to create.
4.  Enter a name, and then click **Add**.

## EDT example

```xpp
public void EdtMethod()
{
    // Example of declaring EDT variables where
    // a UserGroupID (integer) variable is declared and initialized to 1.
    UserGroupID groupID = 1;

    // An Amount (real) variable is declared.
    Amount currency;
}
```


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]