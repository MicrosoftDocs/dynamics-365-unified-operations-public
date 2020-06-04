---
# required metadata

title: Writing a select statement as an expression
description: You can use a select statement as an expression.
author: robinarh
manager: AnnBe
ms.date: 05/22/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom:
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.dyn365.ops.version: AX 7.0.0
ms.search.validFrom: 2016-02-28
---

## Writing a select statement as an expression

[!include [banner](../../includes/banner.md)]

You can use a **select** statement as an expression. This type of **select** statement is known as an *expression **select** statement*. A table buffer variable can't be used in an expression **select** statement. The name of the table must be used in the **from** clause. One limitation of expression **select** statements is that the **join** keyword isn't supported in an expression join.

In the following example, the **select** statement inside the parentheses returns one row.

- The only column that can be populated with data is the column that is named before the **from** clause in the **select** clause.
- After the closing parenthesis, the name of that column is used to reference the data value: **AccountNum**.
- This example returns a maximum of one row, because it uses the `firstonly` keyword. However, the value that is assigned to **sAccountNum** is the same, even if the `firstonly` keyword is omitted.
- The table name can't be used to qualify a field name in the **order by** clause.

```xpp
str sAccountNum;
sAccountNum = (select firstonly AccountNum from CustTable
    order by AccountNum des)
    .AccountNum;
info(strFmt("Max AccountNum: %1", sAccountNum));

// Output: Max AccountNum: 4507
```

Here is a simpler way to achieve the same result as the previous example.

```xpp
str sAccountNum;
sAccountNum = (select maxof(AccountNum) from CustTable).AccountNum;
info(strFmt("Max RecId: %1", sAccountNum));

// Output: Max AccountNum: 4507
```

The following example returns the maximum RecId of customers that are not blocked. In a **where** clause, the table name must be used as a qualifier of the field. Here, the **maxof** aggregate function is used, and the **RecId** field is mentioned in the function. The field that is mentioned in the aggregate function must be the same as the field name that is used to reference the data value after the closing parenthesis. Otherwise, empty data is returned.

```xpp
int64 nRecId;
nRecId = (select maxof(RecId) from CustTable
    where CustTable.Blocked == CustVendorBlocked::No)
    .RecId;
info(strFmt("Max RecId: %1", nRecId));

// Output: Max RecId: 5637144604
```

In the following example, a field name (in this case, **RecId**) is used to reference a data value that isn't a **RecId** value. The **count** aggregate function doesn't return a **RecId** value. Typically, the **RecId** field is used with the **count** function.

```xpp
int64 nRecId;
nRecId = (select count(RecId) from CustTable
    where CustTable.Blocked == CustVendorBlocked::No)
    .RecId;
info(strFmt("Count of unblocked customers: %1", nRecId));

// Output: Count of unblocked customers: 29
```

There are some limitations of **expression select statements**:
+ The `join` keyword isn't supported in **expression select statements**. 
+ You can only mention one table in an **expression select statement**, therefore subselects are not supported as a workaround to the unsupported `join` keyword.



### select statements on fields

You can use a **select** statement in a lookup on a field. After a **select** statement that fetches a record in a table, you can enter **.fieldName** to reference a field in the table. These **select** statements must be used in expressions. A *normal **select** statement* differs from a *field **select** statement*:

-   The field **select** statement operates directly on a table.
-   The normal **select** statement operates on a table buffer variable.

### select field example

```xpp
// Prints the NameRef field from the selected customer
print (select CustTable order by AccountStatement).AccountStatement;

// Uses the balance field from the customer with AccountNum 3000
if ((select custTable where CustTable.AccountNum == '3000').CreditMax < 5000)
print "This customer has a credit maximum less than $5000.";
```