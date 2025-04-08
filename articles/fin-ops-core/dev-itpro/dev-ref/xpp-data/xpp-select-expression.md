---
title: Write select statements as expressions
description: Learn how you can use a select statement as an expression including X++ expressions and examples for select statements on fields.
author: josaw1
ms.author: josaw
ms.topic: article
ms.date: 06/16/2020
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Write select statements as expressions

[!include [banner](../../includes/banner.md)]

You can use a **select** statement as an expression. This type of **select** statement is known as an *expression **select** statement*.

+ You can't use a table buffer variable in an expression **select** statement.
+ The name of the table must be used in the **from** clause.
+ The **join** keyword isn't supported.
+ The table name can't be used to qualify a field name in the **order by** clause.
+ In a **where** clause, the table name must be used as a qualifier of the field.
+ You can mention only one table in an expression **select** statement. Therefore, subselects aren't supported as a workaround for the unsupported **join** keyword.
+ The only column that can be filled with data is the column that is named before the **from** clause in the **select** clause.
+ After the closing parenthesis, the name of a column is used to reference the data value.

The following expression returns the value in the **AccountNum** column of the first row in the CustTable table (if a row exists).

```xpp
str accountNum = (select AccountNum from CustTable order by AccountNum desc).AccountNum;
info('Max AccountNum: ' + accountNum);
```

Here is a simpler way to achieve the same result as the previous example.

```xpp
str accountNum = (select maxof(AccountNum) from CustTable).AccountNum;
info('Max AccountNum: ' + accountNum);
```

The following example returns the maximum **RecId** value of customers that aren't blocked. Here, the **maxof** aggregate function is used, and the **RecId** field is mentioned in the function. The field that is mentioned in the aggregate function must match the field name that is used to reference the data value after the closing parenthesis. Otherwise, empty data is returned.

```xpp
int64 nRecId = (select maxof(RecId) from CustTable
            where CustTable.Blocked == CustVendorBlocked::No).RecId;
info("Max RecId: " + int642Str(nRecId));
```

In the following example, the **RecId** field is used to reference a data value that isn't a **RecId** value. The **count** aggregate function doesn't return a **RecId** value. It's a typical practice to use the **RecId** field with the **count** function.

```xpp
int64 nRecId = (select count(RecId) from CustTable
            where CustTable.Blocked == CustVendorBlocked::No).RecId;
info('Count of unblocked customers: ' + int642Str(nRecId));
```

## select statements on fields

You can use a **select** statement in a lookup on a field. After a **select** statement that fetches a record in a table, you can enter **.fieldName** to reference a field in the table. These **select** statements must be used in expressions. A *normal **select** statement* differs from a *field **select** statement* in the following way:

+ The field **select** statement operates directly on a table.
+ The normal **select** statement operates on a table buffer variable.

The following examples shows how to access fields from a select statement.

```xpp
print((select CustTable order by AccountStatement).AccountStatement);

if ((select custTable where CustTable.AccountNum == '3000').CreditMax < 5000)
{
    info('This customer has a credit maximum less than $5000.');
}
```


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
