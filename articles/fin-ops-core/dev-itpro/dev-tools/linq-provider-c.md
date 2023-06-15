---
title: Language Integrated Query (LINQ) provider for C#
description: This article discusses the LINQ provider.
author: pvillads
ms.date: 11/03/2017
ms.topic: article
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: pvillads
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 8bd10c93-9d5e-49d7-b20f-7f804e16e76c
---

# Language Integrated Query (LINQ) provider for C\#

[!include [banner](../includes/banner.md)]

This article discusses the LINQ provider.

LINQ (Language Integrated Query) is a set of classes and methods that enable you to access data that is stored in a variety of places and formats. The LINQ framework is the standard for accessing data in managed languages. LINQ presents to programmers a unified and consistent API for data access from heterogeneous data sources, such as:

- In-memory object graphs
- Active Directory entries
- Flickr pictures and XML
- SQL Server

The LINQ provider allows the user to access business data by using .NET managed languages.

## Two syntactical mechanisms for accessing LINQ

There are two syntactical approaches for using LINQ, as described in the following table.

| Approach | X++ | C\# and Visual Basic |
|-------------------------|------------------|---------------------------|
| LINQ by standard method call syntax. | Impractical. Language support for generics is vital for LINQ and is not supported in X++. | Available, requires lambda syntax. |
| LINQ by specialized syntax that is understood by the compiler. | Not available.   | Available, easier to use. |

There are two syntactic mechanisms for accessing the LINQ provider in C\# (or in Visual Basic):

- By standard, or fluent, method call syntax.
- By specialized syntax that the C\# compiler has been enhanced to understand as equivalent to the LINQ method calls. (Such syntax is sometimes called “syntactic sugar”.)

This article is going to review each syntactic mechanism for LINQ, starting with the easier specialized syntax.

## LINQ by specialized syntax in C\#

Some .NET languages understand specialized syntax for LINQ as an alternative that is easier for us to write. C\# is one such language.

To use LINQ in C\#, you must understand the C\# keyword **var**, which is used to declare variables. The var keyword tells the compiler to figure out the data type of the variable by what is assigned to the variable. This feature is now also available in X++. The type is implicit in the source code, and the type is settled and unvarying after the compilation completes.

### Comparing X++ to C\# LINQ

The X++ language supports the useful and easy to use `while select` statement. This lest you compare the X++ `while select` syntax to the specialized C\# LINQ syntax. First, here is the X++ sample.

```xpp
CustTable ct;     // X++, traditional while select.
CustTrans trans;

while select * from ct
    where ct.AccountNum >= ‘4000’
    join RecId from trans
    where trans.RecId == ct.RecId
    order by ct.AccountNum desc
{
    print ct.AccountNum;
}
```

Next is an equivalent query in C\# with the specialized LINQ syntax.

```csharp
// C#, with specialized LINQ syntax.
// Get access to the data provider:
var provider = new QueryProvider(null);

var customers = new QueryCollection(provider);
var customerTransactions = new QueryCollection(provider);

var query = from ct in customers
            from trans in customerTransactions
            where ct.AccountNum >= “4000”
            where trans.AccountNum == ct.AccountNum
            orderby ct.AccountNum descending
            select ct;

foreach (var ct in query)
{
    System.Console.WriteLine(ct.AccountNum);
}
```

## LINQ query in C\# by method syntax, using the lambda operator >

Next is another use of LINQ in C\#, except this time the more standard syntax is used to call the LINQ API. The approach also involves use of the lambda operator `>`. The following C\# query is functionally equivalent to the preceding C\# query.

```csharp
var query = customers
    .Where(c => string.Compare(c.AccountNum, "4000") >= 0)
    .Join(customers,
        primary => primary.AccountNum,
        foreign => foreign.AccountNum,
        (primary, foreign) => new { P = primary, F = foreign })
    .OrderBy(primaryAndForeign => primaryAndForeign.P.AccountNum)
    .Select(primaryAndForeign => primaryAndForeign.P);
```

There's a good match between the `while select` syntax used in X++ and the specialized LINQ syntax in C\# (Visual Basic has particularly good LINQ syntax). It's evident that the specialized LINQ syntax is actually very useful in expressing joins, but the specialized syntax built into the C\# compiler doesn't handle the extensions provided by the finance and operations applications.

### Limitation of the specialized LINQ syntax

A limitation of the specialized LINQ syntax is that it can't be augmented with extensions to the LINQ provider. In contrast, standard syntax of method calls plus the lambda operator can be extended as needed. For instance, the LINQ framework provides a method for cross-company hints that can't be expressed in the special syntax for LINQ in C\#. Fortunately, due to the ability to compose queries, this limitation need not be a major problem. Calls to esoteric LINQ methods can be appended to the specialized LINQ syntax. The following C\# code shows this being done for the **crosscompany** method.

```csharp
// C#, mixing LINQ syntax mechanisms.
var query = (from ct in customers
            from trans in customerTransactions
            where ct.AccountNum >= “4000”
            where trans.AccountNum == ct.AccountNum
            orderby ct.AccountNum descending
            select ct).crosscompany();
```

## LINQ query execution

The code generated for a LINQ query builds a tree at run time. When the results of the query are required, this tree is passed to the backend that will interpret it, and will provide the data as expressed in the query. The X++ compiler also builds a tree to express the query, but the X++ compiler has intimate knowledge about the capabilities of the database backend. This has several important implications as described in the following subsections.

### Inability to diagnose problems at LINQ compile-time

The C\# compiler is largely unable to foresee and diagnose errors that will occur at run time due to the inability of the backend to process an incompatible LINQ query. For instance, in the following C\# code block, the specialized LINQ syntax is valid according to the C\# compiler. Yet at run time, an error would occur.

```csharp
var customerQuery = from c in db.Customers
                    where (from o in db.Orders
                    where o.ShipCountry == “Germany”
                    select o.CustomerID).Contains(c.CustomerID);
```

This query can't be handled by the current data layer, and while no errors are diagnosed at compile time, an error would occur at run time.

### Performance penalty with LINQ

There is an overhead penalty paid at run time, when analysis of the tree occurs, and a suitable access language is generated. As we might expect, the performance penalty is incurred when analyzing the LINQ expression tree. The time required at run time to actually fetch the data doesn't vary much between C\# and LINQ versus X++ with `while select`. Our preliminary numbers show that the beginning-to-end performance of the query is about three times longer with C\# LINQ, compared to X++ `while select`, when very few records are fetched. But when many records are fetched, the total times are about the same between C\# and X++. The conclusion is that it takes much longer to fetch a lot of records than it takes to analyze the language tree.

### Composing queries with LINQ

The model that's provided by LINQ allows queries to be composed of subqueries. The X++ language can't cleanly provide this feature. To understand this, consider the following C\# LINQ code. A flag is passed to a method to control the ordering of data results.

```csharp
private IEnumerable RichCustomers(bool orderByName)
{
    // Create a query for the rich customers. Note carefully
    // that no data is fetched when this is executed.
    var q = from c in customers where c.AmountMst > 1000000.0m select c;

    if (orderByName)
    {
        // Add the order by clause to the existing query.
        // Still no data is yet fetched.
        return q.OrderBy(c => c.AccountNum);
    }
    else
    {
        return q;
    }
}
```

### Set based operations with LINQ

LINQ queries can be applied for CRUD operations. But the model for updating, deleting, and inserting records isn't useful for the expression of set based operations. We're now working on extensions to add to the LINQ model that will translate into set based operations.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

