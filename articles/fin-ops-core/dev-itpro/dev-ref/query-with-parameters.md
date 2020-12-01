---
# required metadata

title: Mitigate a SQL injection attack
description: This topic describes how to mitigate a SQL injection attack in X++.
author: pvillads
manager: tfehr
ms.date: 06/20/2017
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
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Mitigate a SQL injection attack

A SQL injection attack happens when malicious data values are passed to SQL Server. Those values can wreak havoc in a database. SQL injections can happen if are not vigilant in how you are passing data that came from an uncontrolled source, for example, user input, to a query, and then that query runs against the SQL database. A SQL injection is normally not an issue at all in Finance and Operations apps, because using the built-in data access statements in X++ precludes the possibility of this attach. It can happen when you use Direct-SQL, and raw SQL code is passed to the server.

## The problem

To illustrate the scenario, let's consider this contrived example. A developer write code to look up the first name of customers given their last names, using the code in the following example:

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

In addition, there is a form that allows the user to enter the name in a string field, or perhaps a service endpoint that allows names to come into the server that way. All is well when the user enters a valid name like "Jones". A malicious user might a name that looks like this:

'; drop table Customer --

As you can see, the final query that the server will execute is:

```xpp
SELECT TOP(1) firstName FROM Customer WHERE customer.Name = ''; drop table Customer --'
```

The first quote in the given string just ends the string literal that should contain the name we are looking for. Then another SQL statement is executed (due to the `;` statement terminator token). This second statement irretrievably wipes out the **Customer** table and all the data in it. Finally the commenting characters, `--`, are there to make sure that the ending single quote does not cause syntax errors, making the string perfectly valid T/SQL. The developer will be looking for a new job soon.

SQL injection occurs because we consider developers as gods in the X++ pantheon who are assumed to be reasonable people who know what they are doing. The connection to the SQL server does not impose any restrictions that preclude it from doing operations that create or delete tables, views, and stored procedures at runtime.

## The solution

SQL mitigates this threat by using *statement parameters*. Statement parameters never use literals that are subject to textual changes to the resulting string. Instead, they provide named parameters where the actual content of the parameter is provided contextually. For this release we have provided a new API that allows the developer to use these parameters instead of building SQL strings in code.

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

The updated examples use the new API name **executeQueryWithParameters** instead of the old API that did not take parameters. The code builds the map containing the mapping from parameter names onto parameter values. In this case, **Name** will be the value of **@Name** in SQL. The incoming **name** could be anything.

There is a related method on the **Statement** type that is used to run statements that return integer values instead or rows. Typically, the integer value is the number of rows impacted. This examples uses the X++ data statements with the **executeQueryWithParameters** API:

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
        paramMap.add('percent', 1.1);     // 10 percent increase
        paramMap.add('Level', 'Boss');    // For the top brass

        int cnt = statement.executeUpdateWithParameters(sql, paramMap);
        statement.close();

        connection.ttscommit();
    }
```

## Conclusion

As we are introduce the new methods we are also marking the existing ones (the ones without the parameters) as obsolete. The usual deprecation periods apply, so that you can update your code to take advantage of the new protection provided by the parameters.

The **executeQueryWithParameters** API allows you to protect your customer from disasters, but you are not forced to use the new API. You can still do string concatenations and provide an empty parameter set, negating the advantages provided by parameters. We hope that you will take this opportunity to weed out any dangerous usage you have in your code.
