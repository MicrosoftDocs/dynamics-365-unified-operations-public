---
title: Mitigate a SQL injection attack
description: This article explains how to mitigate SQL injection attacks in X++.
author: pvillads
ms.date: 02/21/2023
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: pvillads
ms.search.validFrom: 2020-12-01
ms.dyn365.ops.version: AX 7.0.0
---

# Mitigate a SQL injection attack

[!include [banner](../includes/banner.md)]

[!include [preview-banner](../includes/preview-banner.md)]

An SQL injection attack occurs when malicious data values are passed to Microsoft SQL Server in a query string. Those values can cause lots of damage in a database. SQL injection can occur if you aren't careful about how you use a query to pass data that comes from an uncontrolled source, such as user input, to SQL Server. SQL injection isn't usually an issue in finance and operations apps, because the built-in data access statements in X++ prevent it. However, if you use Direct-SQL, SQL injection can occur when raw SQL code is passed to the server.

A new API will help mitigate these attacks. The API is available starting with platform updates for version 10.0.17 of finance and operations apps (April 2021).

## The issue

Consider a scenario where a developer writes the following code to look up the first name of customers, based on their last name.

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
   
    // Harvest the results.
    return results.getString(1);
   
   // Close statement
    statement.close();
    
    return result;
}
```

Additionally, there is either a page where users can enter customer names in a string field, or a service endpoint that enables names to come into the server.

In this scenario, everything works well if users enter valid names such as "Jones." However, a malicious user might enter the following string as a name.

```xpp
'; drop table Customer --
```

In this case, here is the final query that the server runs.

```xpp
SELECT TOP(1) firstName FROM Customer WHERE customer.Name = ''; drop table Customer --'
```

The first quotation mark in the given string just ends the string literal that should contain the name that the user is looking for. Then another SQL statement is run because of the semicolon (;), which is a statement terminator token. This second statement irretrievably deletes the **Customer** table and all the data in it. Finally, the commenting characters (--) ensure that the single quotation mark at the end doesn't cause syntax errors. Therefore, the string is valid Transact SQL (T-SQL).

SQL injection occurs because the connection to SQL Server doesn't impose any restrictions that prevent it from performing operations that create or delete tables, views, and stored procedures at runtime. Therefore, organizations must rely on the assumption that developers are reasonable people who know what they are doing.

## The solution

SQL Server mitigates the threat by using *statement parameters*. Statement parameters never use literals that are subject to textual changes to the resulting string. Instead, they provide named parameters, the actual content of which is provided contextually. For this release, Microsoft has added a new API that lets you use parameters instead of building SQL strings in code.

The following example shows what the code from the previous example looks like after these changes are incorporated.

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
    var results= statement.executeQueryWithParameters(sqlStatementText, paramMap);

    // Capture the results:
    results.next();
  
    // Close statement
      statement.close();

    return results;
}
```

The updated example uses the new **executeQueryWithParameters** API instead of the old API that didn't take parameters. The code builds the map that contains the mapping from parameter names to parameter values. In this case, **Name** will be the value of **\@Name** in SQL. The incoming **name** value can be anything.

A related method on the **Statement** type is used to run statements that return integer values instead of rows. Typically, the integer value indicates the number of rows that are affected. The following example uses the X++ data statements with the **executeQueryWithParameters** API.

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

As Microsoft introduces the new methods, we are also marking the existing methods (that is, the methods without the parameters) as obsolete. The usual deprecation periods apply. Therefore, you can update your code to take advantage of the new protection that the parameters provide.

Although the new **executeQueryWithParameters** API helps you protect your customers from disasters, you aren't required to use it. You can still do string concatenations and provide an empty parameter set. However, in this case, you don't gain the advantages that the parameters provide. We hope that you will take this opportunity to eliminate any dangerous usage that you have in your code.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
