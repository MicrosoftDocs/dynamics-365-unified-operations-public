---
# required metadata

title: X++ container runtime functions
description: This topic describes the container run-time functions.
author: RobinARH
manager: AnnBe
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
ms.assetid: 5b4741a5-dec1-4a3b-b739-6c12142ac668
ms.search.region: Global
# ms.search.industry: 
ms.author: rhaertle
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Injection attack mitigation
Injection attacks is the term used for attacks where an adversary uses specially crafted data values to wreak havoc in a database. It can only happen if the developer who crafted the code is not vigilant about how he is passing data that came from an uncontrolled source (e.g. user input) to a query that gets executed by the SQL database. This is normally not an issue at all in Dynamics AX for F&O, since using the built-in data access statements in X++ precludes the possiblity of this attach, but it can happen when the developer resorts to using Direct-SQL where "raw" SQL code is passed to the server.

## The problem
To illustrate the scenario, let's consider an example (that may be a little contrived, but should serve to illustrate the point) - Imagine that John, a freshman developer, wrote code to look up the first name of customers given their last names like this:

```X++
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

Let's further imagine there is a form that allows the user to enter the name in a string field, or perhaps a service endpoint that allows names to come into the server that way. All is well when the user enters valid names like "Jones" but consider what happens when the antagonist puts in a "name" that looks like this:

'; drop table Customer --

As you can see, the final query that the server will execute is:

```X++
SELECT TOP(1) firstName FROM Customer WHERE customer.Name = ''; drop table Customer --'
```

In other words: The first quote in the given string just ends the string literal that should contain the name we are looking for. Then another SQL statement is executed (due to the ';' statement terminator token). This second statement will irretrievably wipe out the Customer table and all the data in it. Finally the commenting characters -- are there to make sure that the ending single quote does not cause syntax errors, making the string perfectly valid T/SQL. John will be looking for a new job soon.

This is a problem because we consider developers as Gods in the X++ pantheon who are assumed to be reasonable people who know what they are doing. The connection to the SQL server does not impose any restrictions that preclude it from doing DML operations that create or delete tables, views, stored procedures etc. at runtime.

## The solution
Fortunately SQL has a way to mitigate this threat, namely by using what is known as statement parameters. This works by never using literals that are subject to textual changes to the resulting string, instead providing named parameters where the actual content of the parameter is provided contextually. For this release we have provided a new API that allows the developer to use these parameters instead of building SQL strings in code.

Let us examine what the code above looks like with these changes.

```X++
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

As you can see, we are using a new API called executeQueryWithParameters instead of the old API that did not take parameters. We build the map containing the mapping from parameter names (here Name which will be the value of @Name in SQL) onto parameter values (here the incoming name, over which we have no control).

There is a sister method on the Statement type that is used to execute DML statements, i.e. statements that do not return rows, but integer values (typically the number of rows impacted). For the sake of completeness we provide an example using the new method below:

```X++
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
As we are introducing the new methods we are also marking the old ones (i.e. the ones without the parameters) as obsolete. You have the usual grace period to update your code to take advantage of the new protection provided by the parameters.

Please note that the introduction of these new possiblities allows you to protect your customer from disasters (and perhaps yourself from litigation), but it does not force you to use them. You can still do string concatenations and provide an empty parameter set, negating the advantages provided by parameters. We hope that you will take this opportunity to weed out any dangerous usage you have in your code.
