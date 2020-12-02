---
# required metadata

title: Mitigate a SQL injection attack
description: This topic describes how to mitigate a SQL injection attack in X++.
author: pvillads
manager: tfehr
ms.date: 12/01/2020
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
# ms.tgt_pltfrm: 
ms.custom: 31301
ms.search.region: Global
# ms.search.industry: 
ms.author: rhaertle
ms.search.validFrom: 2020-12-01
ms.dyn365.ops.version: AX 7.0.0

---

# Mitigate a SQL injection attack

[!include [banner](../includes/banner.md)]

[!include [preview-banner](../includes/preview-banner.md)]

A SQL injection attack happens when malicious data values are passed to SQL Server in a query string. Those values can wreak havoc in a database. A SQL injection can happen if you are not vigilant in how you pass data that comes from an uncontrolled source, such as user input, to SQL Server by using a query. A SQL injection is not usually an issue in Finance and Operations apps, because using the built-in data access statements in X++ precludes the possibility of this attack. It can happen when you use Direct-SQL, and raw SQL code is passed to the server.

## The problem

To illustrate the scenario, let's consider this example. Suppose that a developer writes code to look up the first name of a customer given their last name, using the code in the following example:

```xpp
public str GetFirstName(str name)
{
    str sqlStatementText = "SELECT TOP(1) firstName FROM Customer WHERE customer.Name = '" + name + "'";

    // Create a connection to the SQL Server
    var connection = new Connection();

    // Create a statement and submit the sql statement to the server:
    Statement statement = connection.createStatement();
    var results= statement.executeQuery(sqlStatementText);

    // Get the first record:
    results.next();
    statement.close();

    // Harvest the results.
    return results.getString(1);
}
```

Suppose also that there is a form that allows the user to enter the name in a string field, or perhaps a service endpoint that allows names to come into the server. All is well when the user enters a valid name like "Jones". A malicious user might enter a name that looks like this:

```xpp
'; drop table Customer --
```

The final query that the server runs is:

```xpp
SELECT TOP(1) firstName FROM Customer WHERE customer.Name = ''; drop table Customer --'
```

The first quote in the given string just ends the string literal that should contain the name we are looking for. Then another SQL statement is run, because of the `;` statement terminator token. This second statement irretrievably wipes out the **Customer** table and all the data in it. Finally, the commenting characters, `--`, make sure that the ending single quote does not cause syntax errors, making the string perfectly valid T/SQL. The developer will be looking for a new job soon.

SQL injection occurs because we consider developers are assumed to be reasonable people who know what they are doing. The connection to the SQL server does not impose any restrictions that preclude it from doing operations that create or delete tables, views, and stored procedures at runtime.

## The solution

SQL mitigates this threat by using *statement parameters*. Statement parameters never use literals that are subject to textual changes to the resulting string. Instead, they provide named parameters where the actual content of the parameter is provided contextually. For this release, we have added a new API that lets you use parameters instead of building SQL strings in code.

Let us examine what the code above looks like with these changes.

```xpp
public str GetFirstName(str name)
{
    str sqlStatementText = "SELECT TOP(1) firstName FROM Customer WHERE customer.Name = @Name";

    // Create a connection to the SQL Server
    var connection = new Connection();

    // Submit the sql statement to the server:
    Statement statement = connection.createStatement();

    // Create a mapping from parameter names onto values
    Map paramMap = SqlParams::create();
    paramMap.add('Name', name);

    // Execute the query, providing both the query
    // and the parameters.
    var results= statement.executeQueryWithParameters(sqlStatementText);

    // Capture the results:
    results.next();
    statement.close();

    return results.getString(1);
}
```

The updated example uses the new API named **executeQueryWithParameters** instead of the old API that did not take parameters. The code builds the map containing the mapping from parameter names onto parameter values. In this case, **Name** will be the value of **\@Name** in SQL. The incoming **name** could be anything.

There is a related method on the **Statement** type that is used to run statements that return integer values instead or rows. Typically, the integer value is the number of rows impacted. This example uses the X++ data statements with the **executeQueryWithParameters** API:

```xpp
public void InsertWithStrParameter()
{
    var connection = new Connection();
    Statement statement = connection.createStatement();

    connection.ttsbegin();

    str sql = @"
        UPDATE Wages
        SET Wages.Wage = Wages.Wage * @percent
        WHERE Wages.Level = @Level";

    Map paramMap = SqlParams::create();
    paramMap.add('percent', 1.1);        // 10 percent increase
    paramMap.add('Level', 'Manager');    // Management increase

    int cnt = statement.executeUpdateWithParameters(sql, paramMap);
    statement.close();

    connection.ttscommit();
}
```

## Conclusion

As we introduce the new methods, we are also marking the existing ones (the ones without the parameters) as obsolete. The usual deprecation periods apply, so that you can update your code to take advantage of the new protection provided by the parameters.

The **executeQueryWithParameters** API allows you to protect your customer from disasters, but you are not forced to use the new API. You can still do string concatenations and provide an empty parameter set, negating the advantages provided by parameters. We hope that you will take this opportunity to weed out any dangerous usage you have in your code.
