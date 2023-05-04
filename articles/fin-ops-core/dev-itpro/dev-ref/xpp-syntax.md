---
title: X++ syntax
description: This article contains the syntax reference for X++.
author: josaw1
ms.date: 07/22/2019
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# X++ syntax

[!include [banner](../includes/banner.md)]

This article contains the syntax reference for X++. 

## X++ Keywords

The X++ keywords shown in the following table are reserved. These keywords cannot be used for any other purpose.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Reserved word</th>
<th>Description</th>
<th>More information</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>!</strong></td>
<td>Not.</td>
<td>Relational Operators</td>
</tr>
<tr class="even">
<td><strong>!=</strong></td>
<td>Inequality operator (not equal to).</td>
<td>Relational Operators</td>
</tr>
<tr class="odd">
<td><strong>#</strong></td>
<td>Prefix on macro names.</td>
<td>How to: Use #define and #if to Test a Macro</td>
</tr>
<tr class="even">
<td><strong>&amp;</strong></td>
<td>Binary AND.</td>
<td>Arithmetic Operators</td>
</tr>
<tr class="odd">
<td><strong>&amp;&amp;</strong></td>
<td>Logical AND.</td>
<td>Relational Operators</td>
</tr>
<tr class="even">
<td><strong>(</strong></td>
<td>Function call operator, which indicates the beginning of the function call.</td>
<td></td>
</tr>
<tr class="odd">
<td><strong>)</strong></td>
<td>Function call operator, which indicates the end of the function call.</td>
<td></td>
</tr>
<tr class="even">
<td><strong><em></strong></td>
<td>Multiply. The asterisk (<span class="code"></em></span>) is also used in X++ SQL. One use is to signify all fields from the tables on a <code>select</code> statement. Another use is as a wildcard with the <code>like</code> operator, to signify 0 to many characters of any kind. The <code>like</code> operator also uses the <span class="code">?</span> character.</td>
<td>Arithmetic Operators</td>
</tr>
<tr class="odd">
<td><strong>^</strong></td>
<td>Binary XOR.</td>
<td>Arithmetic Operators</td>
</tr>
<tr class="even">
<td><strong>|</strong></td>
<td>Binary OR.</td>
<td>Arithmetic Operators</td>
</tr>
<tr class="odd">
<td><strong>||</strong></td>
<td>Logical OR.</td>
<td>Relational Operators</td>
</tr>
<tr class="even">
<td><strong>~</strong></td>
<td>Not.</td>
<td>Arithmetic Operators</td>
</tr>
<tr class="odd">
<td><strong>+</strong></td>
<td>Plus.</td>
<td>Arithmetic Operators</td>
</tr>
<tr class="even">
<td><strong>++</strong></td>
<td>Increment.</td>
<td>Assignment Operators</td>
</tr>
<tr class="odd">
<td><strong>+=</strong></td>
<td>Additive assignment.</td>
<td>Assignment Operators</td>
</tr>
<tr class="even">
<td><strong>,</strong></td>
<td>Comma operator. Expressions separated by commas are evaluated left-to-right.</td>
<td></td>
</tr>
<tr class="odd">
<td><strong>-</strong></td>
<td>Minus.</td>
<td>Arithmetic Operators</td>
</tr>
<tr class="even">
<td><strong>--</strong></td>
<td>Decrement operator.</td>
<td>Assignment Operators</td>
</tr>
<tr class="odd">
<td><strong>-=</strong></td>
<td>Subtractive assignment.</td>
<td>Assignment Operators</td>
</tr>
<tr class="even">
<td><strong>.</strong></td>
<td>Class member access operator, for example, <code>formRun.run</code> accesses the <code>run</code> method of an object of the class type <code>FormRun</code>.</td>
<td></td>
</tr>
<tr class="odd">
<td><strong>/</strong></td>
<td>Divide.</td>
<td>Arithmetic Operators</td>
</tr>
<tr class="even">
<td><strong>&lt;/strong&gt;</td>
<td>Escape in strings. Escapes extra quotation marks, and certain letters such as <span class="code">\t</span> for tab.</td>
<td></td>
</tr>
<tr class="odd">
<td><strong>@</strong></td>
<td>Escape of keywords. For example, <span class="code">str <xref href="abstract" data-throw-if-not-resolved="False" data-raw-source="@abstract"></xref>;</span> would fail to compile without the <strong>@</strong> sign. Also affects literal strings, by negating the effect of the \ escape character, and by enabling the string to span more than one line in the source code. The new line is represented by one character of hexadecimal 0x0A, which is commonly called a line feed. No carriage return character of hexadecimal 0x0D is included, as in 0x0D0A.</td>
<td></td>
</tr>
<tr class="even">
<td><strong>:</strong></td>
<td>Field declaration or label specifier. The colon (<span class="code">:</span>) character is also used on the <code>switch</code> statement.</td>
<td></td>
</tr>
<tr class="odd">
<td><strong>::</strong></td>
<td>Used to call static (class) methods: <span class="code">ClassName::methodName</span>.</td>
<td></td>
</tr>
<tr class="even">
<td><strong>;</strong></td>
<td>Terminates statements. Used in <code>for</code> loops or as a separator of statements.</td>
<td></td>
</tr>
<tr class="odd">
<td><strong>&lt;</strong></td>
<td>Less than.</td>
<td>Relational Operators</td>
</tr>
<tr class="even">
<td><strong>&lt;&lt;</strong></td>
<td>Left shift.</td>
<td>Arithmetic Operators</td>
</tr>
<tr class="odd">
<td><strong>&lt;=</strong></td>
<td>Less than or equal.</td>
<td>Arithmetic Operators</td>
</tr>
<tr class="even">
<td><strong>=</strong></td>
<td>Assignment operator. The argument to the left of &quot;<strong>=</strong>&quot; is set to the value of the argument to the right.</td>
<td>Assignment Operators</td>
</tr>
<tr class="odd">
<td><strong>==</strong></td>
<td>Returns true if both expressions are equal.</td>
<td>Relational Operators</td>
</tr>
<tr class="even">
<td><strong>&gt;</strong></td>
<td>Greater than.</td>
<td>Relational Operators</td>
</tr>
<tr class="odd">
<td><strong>&gt;=</strong></td>
<td>Greater than or equal.</td>
<td>Relational Operators</td>
</tr>
<tr class="even">
<td><strong>&gt;&gt;</strong></td>
<td>Right shift.</td>
<td>Arithmetic Operators</td>
</tr>
<tr class="odd">
<td><strong>?</strong></td>
<td>Ternary operator. The question mark (<span class="code">?</span>) character is also used by the <code>like</code> operator to signify exactly one character of any kind. The <code>like</code> operator also uses the <span class="code"><em></span> character.</td>
<td>Ternary Operator (?)</td>
</tr>
<tr class="even">
<td><strong>[</strong></td>
<td>Array declarator, open. Must be used with &quot;<strong>]</strong>&quot;.</td>
<td></td>
</tr>
<tr class="odd">
<td><strong>]</strong></td>
<td>Array declarator, close. Must be used with &quot;<strong>[</strong>&quot;.</td>
<td></td>
</tr>
<tr class="even">
<td><strong>{</strong></td>
<td>Indicates the beginning of a number of statements. The last of these statements must be followed by a &quot;<strong>}</strong>&quot;.</td>
<td></td>
</tr>
<tr class="odd">
<td><strong>}</strong></td>
<td>Indicates the end of a number of statements. A &quot;<strong>{</strong>&quot; must appear before the first of these statements.</td>
<td></td>
</tr>
<tr class="even">
<td><strong>abstract</strong></td>
<td>Class and method modifier. An <strong>abstract</strong> class cannot be constructed with the <strong>new</strong> keyword. An <strong>abstract</strong> method cannot be called. A table can also be modified as abstract by setting its <span class="ui">Abstract</span> property to <span class="ui">Yes</span> in the AOT, or by using the <code>DictTable</code> class. The <span class="ui">Abstract</span> property defaults to <span class="ui">No</span>, and it cannot be set unless the table is extended by another table. Each row in an abstract table must have a dependent row in a derived table. This means that each row in an abstract table has a value greater than 0 (zero) in its <span class="ui">InstanceRelationType</span> property field. There are no other effects from marking a table as abstract. Informally, programmers often use the term <span class="term">concrete</span> to describe a class that is non-<strong>abstract</strong>.</td>
<td>Method Modifiers Table Inheritance Overview</td>
</tr>
<tr class="odd">
<td><strong>anytype</strong></td>
<td>The method can return any data type.</td>
<td>Anytype</td>
</tr>
<tr class="even">
<td><strong>as</strong></td>
<td>Needed when you assign a base class variable to a derived class variable. For example, given a <code>Derived</code> class that <strong>extends</strong> a <code>Base</code> class, the statement <code>myDerived = myBase as Derived;</code> avoids a compiler error by using the <strong>as</strong> keyword. This keyword also applies when you assign a base table variable to a derived table variable.</td>
<td>Expression Operators: Is and As for Inheritance</td>
</tr>
<tr class="odd">
<td><strong>asc</strong></td>
<td>An option on the <code>order</code> <code>by</code> or <code>group</code> <code>by</code> clause in a <code>select</code> statement. The sorting is ascending.</td>
<td>Select Statement Syntax</td>
</tr>
<tr class="even">
<td><strong>at</strong></td>
<td>Specifies the position of a print window.</td>
<td>Print Statements</td>
</tr>
<tr class="odd">
<td><strong>avg</strong></td>
<td>Returns the average of the fields from the rows specified by the <code>group by</code> clause in a <code>select</code> statement.</td>
<td>Select Statement Syntax</td>
</tr>
<tr class="even">
<td><strong>break</strong></td>
<td>Immediate exit from code block.</td>
<td>Break Statements</td>
</tr>
<tr class="odd">
<td><strong>breakpoint</strong></td>
<td>Represents a breakpoint that is set for debugging purposes. To set a breakpoint in your code, write: <code>breakpoint;</code></td>
<td></td>
</tr>
<tr class="even">
<td><strong>by</strong></td>
<td>Part of a reserved term, such as group by and order by.</td>
<td></td>
</tr>
<tr class="odd">
<td><strong>byref</strong></td>
<td>Specifies that the parameter being passed to the called method is being passed by reference (address), instead of by value. <strong>Byref</strong> is used in X++ when calling a .NET method that takes a parameter by reference (such as with the C# keywords <strong>out</strong> or <strong>ref</strong>).</td>
<td>How to: Use the byref Keyword for CLR Interop.</td>
</tr>
<tr class="even">
<td><strong>case</strong></td>
<td>Selection within a <code>switch</code> statement.</td>
<td>Switch Statements</td>
</tr>
<tr class="odd">
<td><strong>catch</strong></td>
<td>Used in exception handling.</td>
<td>Exception Handling with try and catch Keywords</td>
</tr>
<tr class="even">
<td><strong>changeCompany</strong></td>
<td>Changes database settings to another company.</td>
<td>Change Company Design Pattern</td>
</tr>
<tr class="odd">
<td><strong>class</strong></td>
<td>Declares a class.</td>
<td>Classes in X++</td>
</tr>
<tr class="even">
<td><strong>client</strong></td>
<td>Method modifier.</td>
<td>Method Modifiers</td>
</tr>
<tr class="odd">
<td><strong>container</strong></td>
<td>Specifies a variable of type <code>container</code>.</td>
<td>Containers</td>
</tr>
<tr class="even">
<td><strong>continue</strong></td>
<td>Forces the next iteration of a loop.</td>
<td>Continue Statements</td>
</tr>
<tr class="odd">
<td><strong>count</strong></td>
<td>Returns the number of records from the rows specified by the <code>group by</code> clause in a <code>select</code> statement.</td>
<td>Select Statement Syntax</td>
</tr>
<tr class="even">
<td><strong>crossCompany</strong></td>
<td>Causes a <code>select</code> statement to return data for all companies that the user is authorized to read from.</td>
<td>Cross-Company X++ Code Basics</td>
</tr>
<tr class="odd">
<td><strong>date</strong></td>
<td>Specifies a variable of type <code>date</code>.</td>
<td>Dates</td>
</tr>
<tr class="even">
<td><strong>default</strong></td>
<td>Default case within <code>switch</code> statements.</td>
<td>Switch Statements</td>
</tr>
<tr class="odd">
<td><strong>delegate</strong></td>
<td>A class member that is able to store multiple references to methods in other classes, and to call all those methods when prompted to do so. A delegate can store references to various kinds of methods including the following:
<ul>
<li>static methods on X++ classes</li>
<li>instance methods on X++ classes</li>
<li>methods on .NET Framework classes</li>
</ul></td>
<td>Event Terminology and Keywords X++, C# Comparison: Event</td>
</tr>
<tr class="even">
<td><strong>delete_from</strong></td>
<td>Allows you to delete multiple records from the database at the same time.</td>
<td>delete_from</td>
</tr>
<tr class="odd">
<td><strong>desc</strong></td>
<td>An option on the <code>order by</code> or <code>group by</code> clause in a <code>select</code> statement. The sorting is descending.</td>
<td>Select Statement Syntax</td>
</tr>
<tr class="even">
<td><strong>display</strong></td>
<td>Method modifier.</td>
<td>Method Modifiers</td>
</tr>
<tr class="odd">
<td><strong>div</strong></td>
<td>Integer division.</td>
<td>Arithmetic Operators</td>
</tr>
<tr class="even">
<td><strong>do</strong></td>
<td>Beginning of a <code>do...while</code> loop.</td>
<td>Do...while Loops</td>
</tr>
<tr class="odd">
<td><strong>edit</strong></td>
<td>Method modifier.</td>
<td>Method Modifiers</td>
</tr>
<tr class="even">
<td><strong>else</strong></td>
<td>Conditional execution (<code>if...else</code>).</td>
<td>if and if ... else Statements</td>
</tr>
<tr class="odd">
<td><strong>eventHandler</strong></td>
<td>Must be used each time you either add or delete a method reference from a delegate by using the <span class="code">+=</span> or <span class="code">-=</span> operator. For example: <span class="code">myDelegate += eventHandler(OtherClass::myStaticMethod);</span></td>
<td>Event Terminology and Keywords X++, C# Comparison: Event</td>
</tr>
<tr class="even">
<td><strong>exists</strong></td>
<td>Used with <code>join</code> clauses in <code>select</code> statements.</td>
<td>Select Statement Syntax</td>
</tr>
<tr class="odd">
<td><strong>extends</strong></td>
<td>A class or interface declaration clause. If your class does not explicitly extend another class, your class is considered to extend the <code>Object</code> class (as if you had written &quot;extends Object&quot;).</td>
<td>Creating a Subclass</td>
</tr>
<tr class="even">
<td><strong>false</strong></td>
<td>Boolean literal.</td>
<td>Booleans</td>
</tr>
<tr class="odd">
<td><strong>final</strong></td>
<td>Class and method modifier.</td>
<td>Method Modifiers</td>
</tr>
<tr class="even">
<td><strong>firstFast</strong></td>
<td>Used in <code>select</code> statements to speed up the fetch for the first row.</td>
<td>Select Statement Syntax</td>
</tr>
<tr class="odd">
<td><strong>firstOnly</strong></td>
<td>Used in <code>select</code> statements to fetch only the first record. The <code>firstOnly</code> keyword does not guarantee that a maximum of one record is retrieved by an X++ SQL <code>select</code> statement. If the AOS can use the <code>EntireTable</code> cache to satisfy the data demands of the <code>select</code> statement, the <code>firstOnly</code> keyword is ignored.</td>
<td>Select Statement Syntax Set-based Caching</td>
</tr>
<tr class="even">
<td><strong>firstOnly10</strong></td>
<td>Same as <strong>firstOnly</strong>, except returns 10 rows instead of one.</td>
<td></td>
</tr>
<tr class="odd">
<td><strong>firstOnly100</strong></td>
<td>Same as <strong>firstOnly</strong>, except returns 100 rows instead of one.</td>
<td></td>
</tr>
<tr class="even">
<td><strong>firstOnly1000</strong></td>
<td>Same as <strong>firstOnly</strong>, except returns 1000 rows instead of one.</td>
<td></td>
</tr>
<tr class="odd">
<td><strong>flush</strong></td>
<td>Clears an entire table cache. Here is the syntax for the <code>flush</code> statement applied to the buffer of type <code>YourTable</code>:<p><p>```xpp<p><code>YourTable t;</code><p><code>...</code><p><code>flush t;</code><p>```</td>
<td>Set-based Caching</td>
</tr>
<tr class="even">
<td><strong>for</strong></td>
<td>For loop iteration.</td>
<td>For Loops</td>
</tr>
<tr class="odd">
<td><strong>forceLiterals</strong></td>
<td>Used in <code>select</code> statements to reveal actual values that are used in <code>where</code> clauses to the Microsoft SQL Server database at the time of optimization.</td>
<td>Select Statement Syntax</td>
</tr>
<tr class="even">
<td><strong>forceNestedLoop</strong></td>
<td>Forces the SQL Server database to use a nested-loop algorithm to process a particular SQL statement containing a <code>join</code>.</td>
<td>Select Statement Syntax</td>
</tr>
<tr class="odd">
<td><strong>forcePlaceholders</strong></td>
<td>Used in <code>select</code> statements to instruct the kernel not to reveal the actual values used in <code>where</code> clauses to the Microsoft SQL Server database at the time of optimization.</td>
<td>Select Statement Syntax</td>
</tr>
<tr class="even">
<td><strong>forceSelectOrder</strong></td>
<td>Forces the SQL Server database to access the tables in a join in the specified order.</td>
<td>Select Statement Syntax</td>
</tr>
<tr class="odd">
<td><strong>forUpdate</strong></td>
<td>Selects records exclusively for update. The operation to be performed on the records that are fetched is an update. Depending on the underlying database, the records may be locked for other users.</td>
<td>Select Statement Syntax</td>
</tr>
<tr class="even">
<td><strong>from</strong></td>
<td>Part of a <code>select</code> statement. The <code>from</code> clause specifies the table in which the columns exists.</td>
<td>Select Statement Syntax</td>
</tr>
<tr class="odd">
<td><strong>group</strong></td>
<td>Part of the <code>group by</code> clause in a <code>select</code> statement.</td>
<td>Select Statement Syntax</td>
</tr>
<tr class="even">
<td><strong>if</strong></td>
<td>Conditional execution.</td>
<td>if and if ... else Statements</td>
</tr>
<tr class="odd">
<td><strong>implements</strong></td>
<td>Implements an interface.</td>
<td>Interfaces Overview</td>
</tr>
<tr class="even">
<td><strong>insert_recordset</strong></td>
<td>Copies data from one or more tables into one resulting destination table on a single server trip.</td>
<td>insert_recordset</td>
</tr>
<tr class="odd">
<td><strong>int</strong></td>
<td>Specifies a variable of type <code>integer</code> (32-bit).</td>
<td>Integers</td>
</tr>
<tr class="even">
<td><strong>int64</strong></td>
<td>Specifies a variable of type <code>integer</code> (64-bit).</td>
<td>Integers</td>
</tr>
<tr class="odd">
<td><strong>interface</strong></td>
<td>Interface declaration.</td>
<td>Interfaces Overview</td>
</tr>
<tr class="even">
<td><strong>is</strong></td>
<td>Asks whether the object referenced by a class variable either inherits from the given class or is of the given class. For example, given a <code>Derived</code> class that <strong>extends</strong> a <code>Base</code> class, the expression <code>(myDerived is Base)</code> returns <strong>true</strong>. This keyword applies to class inheritance and table inheritance.</td>
<td>Expression Operators: Is and As for Inheritance</td>
</tr>
<tr class="odd">
<td><strong>join</strong></td>
<td>Tables are joined on columns common to both tables. You can generate a single result set based on multiple tables through the use of joins.</td>
<td>Select Statement Syntax</td>
</tr>
<tr class="even">
<td><strong>like</strong></td>
<td>Tests for matches by pattern, with wildcard symbols * and ?. The string on the right side of the <code>like</code> operator must use four backslash characters to represent one backslash. Examples follow:
<ul>
<li><span class="code">(&quot;&amp;quot; like &quot;</em>&lt;em&gt;&quot; )</span> //Resolves to false.</li>
<li><span class="code">(&quot;&amp;quot; like &quot;</em>\*&quot;)</span> //Resolves to true.</li>
</ul></td>
<td>Relational Operators</td>
</tr>
<tr class="odd">
<td><strong>maxof</strong></td>
<td>Returns the maximum of the fields from the rows specified by the <code>group by</code> clause.</td>
<td>Select Statement Syntax</td>
</tr>
<tr class="even">
<td><strong>minof</strong></td>
<td>Returns the minimum of the fields from the rows specified by the <code>group by</code> clause.</td>
<td>Select Statement Syntax</td>
</tr>
<tr class="odd">
<td><strong>mod</strong></td>
<td>Returns the integer remainder of the left expression1 divided by the right expression2. Informally this is sometimes called the modulo operator. <code>((12 mod 7) == 5)</code> is true.</td>
<td></td>
</tr>
<tr class="even">
<td><strong>new</strong></td>
<td>Operator. Creates an instance of an anonymous class that is assignment-compatible with the named class/interface reference variables, or allocates memory for an array.</td>
<td></td>
</tr>
<tr class="odd">
<td><strong>next</strong></td>
<td>Fetches the next record in a table.</td>
<td></td>
</tr>
<tr class="even">
<td><strong>noFetch</strong></td>
<td>Indicates that no records are to be fetched at present.</td>
<td>Select Statement Syntax</td>
</tr>
<tr class="odd">
<td><strong>notExists</strong></td>
<td>Used with <code>join</code> clauses in <code>select</code> statements.</td>
<td>Select Statement Syntax</td>
</tr>
<tr class="even">
<td><strong>null</strong></td>
<td>Symbolic constant.</td>
<td></td>
</tr>
<tr class="odd">
<td><strong>optimisticLock</strong></td>
<td>Forces a statement to run with optimistic concurrency control, even if a different value is set on the table.</td>
<td>Select Statement Syntax</td>
</tr>
<tr class="even">
<td><strong>order</strong></td>
<td>Part of the <code>order by</code> clause in a <code>select</code> statement.</td>
<td>Select Statement Syntax</td>
</tr>
<tr class="odd">
<td><strong>outer</strong></td>
<td><span class="keyword">outer join</span>.</td>
<td>Select Statement Syntax</td>
</tr>
<tr class="even">
<td><strong>pause</strong></td>
<td>Halts the execution of a job. The user is asked to state whether execution should continue.</td>
<td>Select Statements</td>
</tr>
<tr class="odd">
<td><strong>pessimisticLock</strong></td>
<td>Forces a statement to run with pessimistic concurrency control, even if a different value is set on the table.</td>
<td>Select Statement Syntax</td>
</tr>
<tr class="even">
<td><strong>print</strong></td>
<td>Allows you to display output on the screen.</td>
<td>Print Statements</td>
</tr>
<tr class="odd">
<td><strong>private</strong></td>
<td>Method access modifier.</td>
<td>Method Access Control</td>
</tr>
<tr class="even">
<td><strong>protected</strong></td>
<td>Method access modifier.</td>
<td>Method Access Control</td>
</tr>
<tr class="odd">
<td><strong>public</strong></td>
<td>Method access modifier.</td>
<td>Method Access Control</td>
</tr>
<tr class="even">
<td><strong>real</strong></td>
<td>Specifies a variable of type <code>real</code>.</td>
<td>Reals</td>
</tr>
<tr class="odd">
<td><strong>repeatableRead</strong></td>
<td>Specifies that no other transactions can modify data that has been read by logic inside the current transaction, until after the current transaction completes. An explicit transaction completes at either <strong>ttsAbort</strong> or at the outermost <strong>ttsCommit</strong>. For a stand-alone <strong>select</strong> statement, the transaction duration is the duration of the <strong>select</strong> command. However, the database sometimes enforces the equivalent of <strong>repeatableRead</strong> in individual <strong>select</strong> statements even without this keyword appearing in your X++ code (depending on how the database decides to scan the tables).</td>
<td>For more information, see the documentation for the underlying relational database product.</td>
</tr>
<tr class="even">
<td><strong>retry</strong></td>
<td>Used in exception handling.</td>
<td>Exception Handling with try and catch Keywords</td>
</tr>
<tr class="odd">
<td><strong>return</strong></td>
<td>Exits from a method.</td>
<td>Declaration of Methods</td>
</tr>
<tr class="even">
<td><strong>reverse</strong></td>
<td>Records are returned in reverse order.</td>
<td>Select Statement Syntax</td>
</tr>
<tr class="odd">
<td><strong>select</strong></td>
<td>The <code>select</code> clause designates which columns or views are shown in the result set.</td>
<td>Select Statements</td>
</tr>
<tr class="even">
<td><strong>server</strong></td>
<td>Method modifier.</td>
<td>Method Modifiers</td>
</tr>
<tr class="odd">
<td><strong>setting</strong></td>
<td>Used with the <span class="code">update_recordset</span> command.</td>
<td>update_recordset</td>
</tr>
<tr class="even">
<td><strong>static</strong></td>
<td>Static methods may not refer to instance variables (only to static variables); may be invoked by using the class name rather than on an instance of the class (&quot;<code>MyClass.aStaticProcedure</code>&quot;).</td>
<td>Method Modifiers</td>
</tr>
<tr class="odd">
<td><strong>str</strong></td>
<td>Specifies a variable of type <code>string</code>.</td>
<td>Strings</td>
</tr>
<tr class="even">
<td><strong>sum</strong></td>
<td>Returns the sum of the fields from the rows specified by the <code>group by</code> clause in a <code>select</code> statement.</td>
<td>Select Statement Syntax</td>
</tr>
<tr class="odd">
<td><strong>super</strong></td>
<td>Calls the method that was overridden by the current method.</td>
<td>Table Methods</td>
</tr>
<tr class="even">
<td><strong>switch</strong></td>
<td>Switch selection statement.</td>
<td>Switch Statements</td>
</tr>
<tr class="odd">
<td><strong>tableLock</strong></td>
<td>Obsolete; <strong>tableLock</strong> is no longer available.</td>
<td></td>
</tr>
<tr class="even">
<td><strong>this</strong></td>
<td>A reference to the current instance of the class. Used in X++ code inside a method of the class. Used to reference <em>method</em> members of the class, but not <em>field</em> members of the class.<code>public str getFullName()</code>  <span class="code">{</span>  <span class="code">    // Next statement fails to compile without &#39;this.&#39;.</span>  <code>    return this.concatenateFirstAndLastNames();</code>  <span class="code">}</span></td>
<td>Loosely similar to the system variable that is named <code>element</code>. You use <code>element</code> in form control methods to reference the containing form. For more information, see Using Variables with Forms.</td>
</tr>
<tr class="odd">
<td><strong>throw</strong></td>
<td>Used in exception handling.</td>
<td>Exception Handling with try and catch Keywords</td>
</tr>
<tr class="even">
<td><strong>true</strong></td>
<td>Boolean literal.</td>
<td>Booleans</td>
</tr>
<tr class="odd">
<td><strong>try</strong></td>
<td>Used in exception handling.</td>
<td>Exception Handling with try and catch Keywords</td>
</tr>
<tr class="even">
<td><strong>ttsAbort</strong></td>
<td>Discards all changes in the current transaction.</td>
<td>Transaction Integrity</td>
</tr>
<tr class="odd">
<td><strong>ttsBegin</strong></td>
<td>Marks the beginning of a transaction.</td>
<td>Transaction Integrity</td>
</tr>
<tr class="even">
<td><strong>ttsCommit</strong></td>
<td>Marks the end of a transaction.</td>
<td>Transaction Integrity</td>
</tr>
<tr class="odd">
<td><strong>update_recordset</strong></td>
<td>Allows the manipulation of row sets within one operation.</td>
<td>update_recordset</td>
</tr>
<tr class="even">
<td><strong>validTimeState</strong></td>
<td>Filters rows that are retrieved from a valid time state table by an X++ SQL <code>select</code> statement. For example: <span class="code">select validTimeState(myDateEffective) * from xMyTable;</span> ...or...  <span class="code">select validTimeState(myDateFrom, myDateTo) * from xMyTable;</span></td>
<td>Effects of Valid Time State Tables on Read and Write Operations</td>
</tr>
<tr class="odd">
<td><strong>void</strong></td>
<td>Identifies a method that does not return a value.</td>
<td>Declaration of Methods</td>
</tr>
<tr class="even">
<td><strong>where</strong></td>
<td>Part of a <code>select</code> statement. The <code>where</code> clause specifies the conditions to be satisfied; that is, the rows that you want to include in the result.</td>
<td>Select Statement Syntax</td>
</tr>
<tr class="odd">
<td><strong>while</strong></td>
<td>Iteration statement. Executes a statement or block repeatedly when a test condition is true.</td>
<td>While Loops while select Statements</td>
</tr>
<tr class="even">
<td><strong>window</strong></td>
<td>Allows you to alter the size of the output window.</td>
<td>Print Statements</td>
</tr>
</tbody>
</table>

## Expressions Syntax
An expression in X++ is used in either a mathematical or logical way. Expressions are built on the data types of the language; that is, an expression returns a value of some type. This value can be used in calculations, assignments, conditional statements, and so on.

### EBNF Description of Expressions in X++

|    Term            | &nbsp; |   Definition                                                |
|--------------------|---|-------------------------------------------------------------|
|     Expression     | = | Simple-expression \[RelationalOperator Simple-expression \] |
| RelationalOperator | = |                              =                              |
| Simple-expression  | = |                   Simple-expression \[ +                    |
|        Term        | = |           Compfactor { Mult-operator CompFactor }           |
|   Mult-operator    | = |                             \*                              |
|     CompFactor     | = |                        \[ ! \] \[ -                         |
|       Factor       | = |                           Literal                           |
|        Enum        | = |                     EnumName :: Literal                     |
|      Variable      | = |    Identifier \[ \[ Expression \] \] \[ . Expression \]     |
|    FunctionCall    | = |                      \[ Expression (.                       |
|   If-expression    | = |            Expression ? Expression : Expression             |

Semantic restrictions apply on the preceding syntax. You cannot call any method using the :: operator. Similarly, you cannot use the **this** keyword without an active object; that is, if you are not within a method and so on.

### Examples

| Example of expression                                       | Description                                                                                                                                    |
|-------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------|
| `1`                                                         | An integer literal.                                                                                                                            |
| NoYes::No                                                   | An enum-reference.                                                                                                                             |
| `A`                                                         | A variable-reference.                                                                                                                          |
| Debtor::Find("1")                                           | A static method-call (returns a customer variable).                                                                                            |
| (A &gt; 3 ? true : false)                                   | An if-expression that returns **true** or **false**.                                                                                           |
| (select CustTable where CustTable.Account == "100").NameRef | A select-expression. Returns the nameref field in the customer table. This is a string.                                                        |
| A &gt;= B                                                   | A logical expression. Returns **true** or **false**.                                                                                           |
| A + B                                                       | An arithmetic expression. Sums A and B.                                                                                                        |
| A + B / C                                                   | Calculates B/C, and then adds this to A.                                                                                                       |
| ~A + this.Value()                                           | Sums binary not A and the result of the method-call Value on the object in scope (this).                                                       |
| Debtor::Find("1").NameRef                                   | Returns the NameRef field of the found customer record.                                                                                        |
| Debtor::Find("1").Balance()                                 | A method call to `Balance` in the customer table (Debtor::Find returns a customer). Returns the balance of the customer with account number 1. |

## EBNF Overview
Extended Backus Naur Form (EBNF) is a metalanguage and is used in this guide to describe the language syntax. An EBNF definition consists of production rules, nonterminals, and terminals. The key terms are shown in the following table.


|    Key terms     |       Example        |                                                                                                          Description                                                                                                          |
|------------------|----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Terminals     |      Work\_Team      |                                                                           A terminal is one character or a string of characters that never change.                                                                            |
|   Nonterminals   |      `Employee`      | A nonterminal is a description of part of a valid sentence in the language that is defined either by a production rule or a textual description. A nonterminal symbol can always be expanded to one or more terminal symbols. |
| Production rules | Employee = Developer |                                                                                                            Tester                                                                                                             |

### Example

Work\_Team = Manager Employee {, Employee}  Employee = Developer | Tester This example defines a Work\_Team as consisting of a `Manager` and one or more `Employees`. An `Employee` is defined as being a `Developer`, or a `Tester`. The symbols used in the example are described in the following table.

### Special Symbols in EBNF

|         Symbol          |                                                               Description                                                               |
|-------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
|  (<em>Expression</em>)  | Parentheses hold the symbols (terminals and nonterminals) together. They can be placed anywhere on the right side of a production rule. |
|  <em>Expression1</em>   |                                                          <em>Expression2</em>                                                           |
| \[<em>Expression</em>\] |               Optional: The items between \[ and \] are optional. All or none of the items in the brackets are included.                |
|      {Expression}       |                     Repeat: The items between { and } are optional, but can be repeated as many times as necessary.                     |

For example, if the accessories you buy for your bicycle consist of a saddle, water-bottle holders, bells, and horns, and you could have either a bell or a horn, and zero, one, or more water bottle holders, and exactly one saddle, this could be expressed as: Bicycle\_Accessories = saddle \[bell | horn\] {water\_bottle\_holders} This grammar defines the following possibilities: `saddle`  `saddle bell`  `saddle horn`  saddle water\_bottle\_holder  saddle bell water\_bottle\_holder  saddle bell water\_bottle\_holder water\_bottle\_holder And so on.

## X++ Grammar
This article shows the formal grammar of the X++ language.

### How to Interpret the Formal BNF Grammar

This section describes the grammar of X++ in Backus Naur Form (BNF). A small example of BNF is described here.

```xpp
AA ::= BB  CC_SYM
BB ::= JJ_SYM
   ::= KK_SYM
```

`AA` is the name of a production rule. An `AA` requires a `BB`, followed by a CC\_SYM. A `BB` is also a production rule. Therefore, `BB` is not a terminal. `BB` must be either a JJ\_SYM or a KK\_SYM. Both JJ\_SYM and KK\_SYM are terminals because they are not the names of any other production rules. CC\_SYM is also a terminal.

In the BNF for X++ grammar, most of the terminals have \_SYM as the suffix of their name.

### The Formal X++ Grammar in BNF

This section contains the BNF that defines the grammar of X++.

```xpp
    CMPL_UNIT ::= RETTYPEID  FUNC_HDR  FUNC_HEAD  BODY
              ::= RETTYPEID  DATA_HDR  CLASS_DECL
              ::= EXPR_HDR  IF_EXPR  SEMIOPT
              ::= RETTYPEID  FUNC_HDR  EVENT_DECL  BODY
    SEMIOPT ::= SEMICOLON_SYM
            ::= 
    CLASS_DECL ::= CLASS_HEADER  LEFTBR_SYM  DCL_EVENTMAP  DCL_LIST  RIGHTBR_SYM
    CLASS_HEADER ::= ATTRIBUTE_DEF  CLASS_MODIFIERS  CLASSORINTERFACE  STD_ID  EXTENDS  IMPLEMENTS
    ATTRIBUTE_DEF ::= LEFT_BRKT_SYM  ATTRIBUTE_INIT  ATTRIBUTE_LIST  RETTYPEID  RGHT_BRKT_SYM
                  ::= 
    ATTRIBUTE_INIT ::= 
                   .
    ATTRIBUTE_LIST ::= ATTRIBUTE
                   ::= ATTRIBUTE_LIST  LIST_SEP_SYM  ATTRIBUTE
    ATTRIBUTE ::= STD_ID
              ::= ATTRIBUTE_WITH_ARGS_BEGINS  ATTRIBUTE_WITH_ARGS_ENDS
    ATTRIBUTE_WITH_ARGS_BEGINS ::= STD_ID  LEFT_PAR_SYM
    ATTRIBUTE_WITH_ARGS_ENDS ::= ATTRIBUTE_ARGS  RGHT_PAR_SYM
    ATTRIBUTE_ARGS ::= ATTRIBUTE_CONSTANT
                   ::= ATTRIBUTE_ARGS  LIST_SEP_SYM  ATTRIBUTE_CONSTANT
    ATTRIBUTE_CONSTANT ::= INT_SYM
                       ::= DBL_SYM
                       ::= STR_SYM
                       ::= DATE_SYM
                       ::= DATETIME_SYM
                       ::= STD_ID  DBLCOLON_SYM  STD_ID
                       ::= TRUE_SYM
                       ::= FALSE_SYM
                       ::= INT64_SYM
                       ::= ATTRIBUTE_INTRINSIC
    ATTRIBUTE_INTRINSIC ::= INTRI_ID  LEFT_PAR_SYM  IARGS  RGHT_PAR_SYM
    CLASSORINTERFACE ::= CLASS_SYM
                     ::= INTERFACE_SYM
    CLASS_MODIFIERS ::= CLASS_MODS
                    ::= 
    CLASS_MODS ::= CLASS_MODIFIER
               ::= CLASS_MODS  RETTYPEID  CLASS_MODIFIER
    CLASS_MODIFIER ::= PUBLIC_SYM
                   ::= FINAL_SYM
                   ::= STATIC_SYM
                   ::= ABSTRACT_SYM
                   ::= PRIVATE_SYM
    EXTENDS ::= EXTENDS_SYM  STD_ID
            ::= 
    IMPLEMENTS ::= IMPLEMENTS_SYM  IMPLEMENTLIST
               ::= 
    IMPLEMENTLIST ::= STD_ID
                  ::= IMPLEMENTLIST  LIST_SEP_SYM  STD_ID
    DCL_EVENTMAP ::= 
    EVENT_DECL ::= ATTRIBUTE_DEF  EVENT_HEADER  PARM_DCL_LIST
    EVENT_HEADER ::= EVENT_MODIFIER  VOID_TYPE_SYM  STD_ID
    EVENT_MODIFIER ::= EVENT_SYM
    FUNC_HEAD ::= ATTRIBUTE_DEF  FUNCNAME  PARM_DCL_LIST
    FUNCNAME ::= FUNCTYPE  STD_ID
    FUNCTYPE ::= FUNC_MODIFIERS  DECL_TYPE
    FUNC_MODIFIERS ::= FUNC_MODS
                   ::= 
    FUNC_MODS ::= RETTYPEID  FUNC_MODIFIER
              ::= FUNC_MODS  RETTYPEID  FUNC_MODIFIER
    FUNC_MODIFIER ::= PUBLIC_SYM
                  ::= PRIVATE_SYM
                  ::= PROTECTED_SYM
                  ::= FINAL_SYM
                  ::= STATIC_SYM
                  ::= ABSTRACT_SYM
                  ::= DISPLAY_SYM
                  ::= EDIT_SYM
                  ::= SERVER_SYM
                  ::= CLIENT_SYM
    BODY ::= LEFTBR_SYM  DCL_FUNC_LIST  SEMIOPT  SECAUTHZCHECK  STMTLIST  SECAUTHZEND  RIGHTBR_SYM
    SECAUTHZCHECK ::= 
    SECAUTHZEND ::= 
    RETTYPEID ::= 
    FUNCTION_DEF ::= FUNC_HEADER  PARM_DCL_LIST  LOCAL_BODY
    FUNC_HEADER ::= DECL_TYPE  STD_ID
    PARM_DCL_LIST ::= RETTYPEID  PARM_START  PARM_LIST_OPT  RGHT_PAR_SYM  RETTYPEID
    PARM_START ::= LEFT_PAR_SYM
    PARM_LIST_OPT ::= PARM_LIST
                  ::= 
    PARM_LIST ::= DCL_INIT
              ::= PARM_LIST  LIST_SEP_SYM  DCL_INIT
    LOCAL_BODY ::= LEFTBR_SYM  DCL_LIST  SEMIOPT  STMTLIST  RETTYPEID  RIGHTBR_SYM
    DCL_LIST ::= DCL_LIST2
             ::= 
    DCL_LIST2 ::= DCL_STMT
              ::= DCL_LIST2  DCL_STMT
    DCL_FUNC_LIST ::= DCL_FUNC_LIST2
                  ::= 
    DCL_FUNC_LIST2 ::= DCL_STMT
                   ::= FUNCTION_DEF
                   ::= DCL_FUNC_LIST2  DCL_STMT
                   ::= DCL_FUNC_LIST2  FUNCTION_DEF
    DCL_STMT ::= DCL_INIT_LIST  RETTYPEID  SEMICOLON_SYM
    DCL_INIT_LIST ::= DCL_INIT
                  ::= DCL_CLIST  ASG_CLAUSE
    DCL_CLIST ::= DCL_INIT_LIST  LIST_SEP_SYM  STD_ID  ARR_DCL_IDX
    DCL_INIT ::= DECL  ASG_CLAUSE
    DECL ::= DECL_TYPE  STD_ID  ARR_DCL_IDX
    DECL_TYPE ::= STR_TYPE_SYM  STR_LEN
              ::= INT_TYPE_SYM
              ::= DBL_TYPE_SYM
              ::= DATE_TYPE_SYM
              ::= DATETIME_TYPE_SYM
              ::= TYPE_ID
              ::= QUEUE_TYPE_SYM
              ::= VOID_TYPE_SYM
              ::= ANY_TYPE_SYM
              ::= GUID_TYPE_SYM
              ::= INT64_TYPE_SYM
              ::= CLR_TYPE
    CLR_TYPE ::= CLR_NAMESPACE  TYPE_ID  CLR_ARRAY_TYPE_EXT
             ::= CLR_NAMESPACE  CLR_TYPE
    CLR_NAMESPACE ::= TYPE_ID  PERIOD_SYM
    CLR_ARRAY_TYPE_EXT ::= CLR_ARRAY_SPEC
                       ::= 
    CLR_ARRAY_SPEC ::= CLR_ARRAY_PART
                   ::= CLR_ARRAY_SPEC  CLR_ARRAY_PART
    CLR_ARRAY_PART ::= CLR_ARRAY_LEFT_PART  CLR_RECTANGULAR_LIST  RGHT_BRKT_SYM
    CLR_ARRAY_LEFT_PART ::= LEFT_BRKT_SYM
    CLR_RECTANGULAR_LIST ::= CLR_COMMA_LIST
                         ::= 
    CLR_COMMA_LIST ::= LIST_SEP_SYM
                   ::= CLR_COMMA_LIST  LIST_SEP_SYM
    STR_LEN ::= INT_SYM
            ::= 
    ARR_DCL_IDX ::= LEFT_BRKT_SYM  RANGE  ARRAY_MEM  RGHT_BRKT_SYM
                ::= 
    RANGE ::= IF_EXPR
          ::= 
    ARRAY_MEM ::= LIST_SEP_SYM  IF_EXPR
              ::= 
    ASG_CLAUSE ::= INIT_START  IF_EXPR
               ::= 
    INIT_START ::= ASG_SYM
    ASG_STMT ::= LVAL_FLD  ASSIGN  IF_EXPR
             ::= LVAL_LIST  ASG_SYM  IF_EXPR
             ::= LVAL_FLD  ASG_INC_DEC
             ::= ASG_INC_DEC  LVAL_FLD
             ::= LVAL_FLD  ASG_EVENT_HANDLER
    ASSIGN ::= ASG_SYM
           ::= ASGINC_SYM
           ::= ASGDEC_SYM
    ASG_INCDEC ::= ASGINC_SYM
               ::= ASGDEC_SYM
    ASG_EVENT_HANDLER ::= ASG_INCDEC  EVENTHANDLER_SYM  LEFT_PAR_SYM  QUALIFIER  STD_ID  RGHT_PAR_SYM
      ::= ASG_INCDEC  EVENTHANDLER_SYM  LEFT_PAR_SYM  STD_ID  DBLCOLON_SYM  STD_ID  RGHT_PAR_SYM
      ::= ASG_INCDEC  EVENTHANDLER_SYM  LEFT_PAR_SYM  QUALIFIER  EVAL_CLR_TYPE  DBLCOLON_SYM  STD_ID  RGHT_PAR_SYM
    ASG_INC_DEC ::= INC_SYM
                ::= DEC_SYM
    LVAL_FLD ::= FIELD
    LVAL_START ::= LEFT_BRKT_SYM
    LVAL_LIST ::= LVAL_START  LVALUES  RGHT_BRKT_SYM
    LVALUE ::= FIELD
    LVALUES ::= LVALUE
            ::= LVALUES  NEXTLVAL  LVALUE
    NEXTLVAL ::= LIST_SEP_SYM
    IF_EXPR ::= COND_TRUE  IF_EXPR
            ::= BOOL_EXPR
    COND_TRUE ::= COND_TEST  IF_EXPR  COLON_SYM
    COND_TEST ::= BOOL_EXPR  QUEST_SYM
    BOOL_EXPR ::= BOOL_EXPR  LOGOP  EXPR
              ::= EXPR
    LOGOP ::= AND_SYM
          ::= OR_SYM
    EXPR ::= SMPL_EXPR  RELOP  SMPL_EXPR
         ::= SMPL_EXPR  AS_SYM  STD_ID
         ::= SMPL_EXPR  IS_SYM  STD_ID
         ::= SMPL_EXPR  AS_SYM  EVAL_CLR_TYPE
         ::= SMPL_EXPR  IS_SYM  EVAL_CLR_TYPE
         ::= SMPL_EXPR
    RELOP ::= LT_SYM
          ::= LE_SYM
          ::= EQ_SYM
          ::= NE_SYM
          ::= GT_SYM
          ::= GE_SYM
          ::= LIKE_SYM
    SMPL_EXPR ::= SMPL_EXPR  ADDOP  TERM
              ::= TERM
    ADDOP ::= PLUS_SYM
          ::= MINUS_SYM
          ::= PHYSOR_SYM
    TERM ::= TERM  MULOP  CMPL_FACT
         ::= CMPL_FACT
    MULOP ::= MULT_SYM
          ::= DIV_SYM
          ::= MOD_SYM
          ::= INTDIV_SYM
          ::= SHIFTL_SYM
          ::= SHIFTR_SYM
          ::= PHYSAND_SYM
          ::= PHYSXOR_SYM
    CMPL_FACT ::= NOT_SYM  SGND_FACT
              ::= SGND_FACT
    SGND_FACT ::= SIGNOP  FACTOR
              ::= FACTOR
    SIGNOP ::= UMINUS_SYM
           ::= PHYSNOT_SYM
    FACTOR ::= LEFT_PAR_SYM  IF_EXPR  RGHT_PAR_SYM
           ::= CONSTANT
           ::= FIELD
           ::= DIRSEARCH
           ::= FUNCTION
           ::= INTRINSICS
           ::= EVAL
           ::= CONLITTERAL
           ::= NEW_CLR_ARRAY
    NEW_CLR_ARRAY ::= NEW_SYM  EVAL_CLR_TYPE  NEW_CLR_ARRAY_PART  LEFT_PAR_SYM  RGHT_PAR_SYM
    NEW_CLR_ARRAY_PART ::= CLR_SIZED_ARRAY  CLR_NOSIZED_ARRAY_SPEC
    CLR_SIZED_ARRAY ::= LEFT_BRKT_SYM  CLR_SMPL_EXPR_COMMA_LIST  RGHT_BRKT_SYM
    CLR_SMPL_EXPR_COMMA_LIST ::= SMPL_EXPR
      ::= CLR_SMPL_EXPR_COMMA_LIST  LIST_SEP_SYM  SMPL_EXPR
    CLR_NOSIZED_ARRAY_SPEC ::= CLR_NOSIZED_ARRAY_LIST
                           ::= 
    CLR_NOSIZED_ARRAY_LIST ::= CLR_NOSIZED_ARRAY
                           ::= CLR_NOSIZED_ARRAY_LIST  CLR_NOSIZED_ARRAY
    CLR_NOSIZED_ARRAY ::= LEFT_BRKT_SYM  CLR_EMPTY_COMMA_LIST  RGHT_BRKT_SYM
    CLR_EMPTY_COMMA_LIST ::= CLR_EMPTY_RECT_COMMA_LIST
                         ::= 
    CLR_EMPTY_RECT_COMMA_LIST ::= LIST_SEP_SYM
                              ::= CLR_EMPTY_RECT_COMMA_LIST  LIST_SEP_SYM
    CONLITTERAL ::= LEFT_BRKT_SYM  IF_EXPR  EXPR_LIST  RGHT_BRKT_SYM
    CONSTANT ::= INT_SYM
             ::= DBL_SYM
             ::= STR_SYM
             ::= DATE_SYM
             ::= DATETIME_SYM
             ::= STD_ID  DBLCOLON_SYM  STD_ID
             ::= TRUE_SYM
             ::= FALSE_SYM
             ::= NULL_SYM
             ::= INT64_SYM
             ::= QUALIFIER  EVAL_CLR_TYPE  DBLCOLON_SYM  STD_ID
             ::= QUALIFIER  STD_ID  DBLCOLON_SYM  STD_ID
    DIRSEARCH ::= DIRS_HEADER  PERIOD_SYM  STD_ID  ARR_IDX
              ::= DIRS_HEADER  PERIOD_SYM  FLD_NUM  ARR_IDX
    DIRS_HEADER ::= LEFT_PAR_SYM  SET_DIRS  FIND_JOIN  RGHT_PAR_SYM
    SET_DIRS ::= 
    FIELD ::= QUALIFIER  STD_ID  ARR_IDX
          ::= QUALIFIER  FLD_NUM  ARR_IDX
          ::= STD_ID  ARR_IDX
    QUALIFIER ::= EVAL  PERIOD_SYM
              ::= STD_ID  PERIOD_SYM
    FLD_NUM ::= LEFT_PAR_SYM  IF_EXPR  RGHT_PAR_SYM
    ARR_IDX ::= LEFT_BRKT_SYM  SMPL_EXPR  RGHT_BRKT_SYM
            ::= 
    EXPR_LIST ::= EXPR_LIST2
              ::= 
    EXPR_LIST2 ::= LIST_SEP_SYM  IF_EXPR
               ::= EXPR_LIST2  LIST_SEP_SYM  IF_EXPR
    FUNCTION ::= FUNC_ID  LEFT_PAR_SYM  EVAL_FUNCTION_NAME  PAR_LIST  RGHT_PAR_SYM
    EVAL_FUNCTION_NAME ::= 
    EVAL_NAME ::= EVAL_ID  LEFT_PAR_SYM
              ::= STD_ID  LEFT_PAR_SYM
              ::= STD_ID  DBLCOLON_SYM  STD_ID  LEFT_PAR_SYM
              ::= SUPER_SYM  LEFT_PAR_SYM
              ::= NEW_SYM  STD_ID  LEFT_PAR_SYM
              ::= NEW_SYM  EVAL_CLR_TYPE  LEFT_PAR_SYM
              ::= QUALIFIER  EVAL_CLR_TYPE  DBLCOLON_SYM  STD_ID  LEFT_PAR_SYM
              ::= QUALIFIER  STD_ID  LEFT_PAR_SYM
              ::= QUALIFIER  STD_ID  DBLCOLON_SYM  STD_ID  LEFT_PAR_SYM
    EVAL_CLR_TYPE ::= NAMESPACE  STD_ID
                  ::= NAMESPACE  EVAL_CLR_TYPE
    NAMESPACE ::= STD_ID  PERIOD_SYM
    EVAL ::= EVAL_NAME  PAR_LIST  RGHT_PAR_SYM
    PAR_LIST ::= PRM_LIST
             ::= 
    PRM_LIST ::= PAR_ELEM
             ::= PRM_LIST  LIST_SEP_SYM  PAR_ELEM
    PAR_ELEM ::= IF_EXPR
             ::= BYREF_SYM  FIELD
    INTRINSICS ::= INTRI_ID  LEFT_PAR_SYM  IARGS  RGHT_PAR_SYM
    IARGS ::= STD_ID
          ::= STR_SYM
          ::= STD_ID  LIST_SEP_SYM  STD_ID
          ::= 
    STMTLIST ::= STATEMENTS
             ::= 
    STATEMENTS ::= STATEMENT
               ::= STATEMENTS  STATEMENT
    STATEMENT ::= COMPOUND_STMT
              ::= WHILE_STMT
              ::= FOR_STMT
              ::= DO_STMT
              ::= SEARCH_STMT
              ::= FIND_STMT
              ::= PRINT_STMT
              ::= WINDOW_STMT
              ::= IF_STMT
              ::= SWITCH_STMT
              ::= EXPR_STMT
              ::= PAUSE_STMT
              ::= BP_CLAUSE
              ::= BREAK_STMT
              ::= CONTINUE_STMT
              ::= RETURN_CLAUSE
              ::= MOVE_REC_STMT
              ::= THROW_STMT
              ::= TRY_STMT
              ::= RETRY_STMT
              ::= TTS_STMT
              ::= FLUSH_STMT
              ::= TBLLOCK_STMT
              ::= CHANGE_STMT
              ::= UPDATE_STMT
              ::= INSERT_STMT
              ::= UNCHECKED_STMT
    COMPOUND_STMT ::= LEFTBR_SYM  STMTLIST  RIGHTBR_SYM
    THROW_STMT ::= THROW_SYM  IF_EXPR  SEMICOLON_SYM
    TRY_STMT ::= TRY_BLOCK  CATCH_LIST
    TRY_BLOCK ::= TRY_START  STATEMENT
    TRY_START ::= TRY_SYM
    CATCH_LIST ::= CATCH_STMT
               ::= CATCH_LIST  CATCH_STMT
    CATCH_STMT ::= CATCH_EXPR  PRE_CATCH  STATEMENT  POST_CATCH
    CATCH_EXPR ::= CATCH_SYM  LEFT_PAR_SYM  IF_EXPR  RGHT_PAR_SYM
      ::= CATCH_SYM  LEFT_PAR_SYM  IF_EXPR  LIST_SEP_SYM  TABLEINSTANCE  RGHT_PAR_SYM
      ::= CATCH_SYM
    PRE_CATCH ::= 
    POST_CATCH ::= 
    TABLEINSTANCE ::= INSTANCENAME
    INSTANCENAME ::= QUALIFIER  STD_ID  ARR_IDX
                 ::= STD_ID  ARR_IDX
    RETRY_STMT ::= RETRY_SYM  SEMICOLON_SYM
    WHILE_STMT ::= WHILE_TEST  STATEMENT
    WHILE_TEST ::= WHILE  LEFT_PAR_SYM  IF_EXPR  RGHT_PAR_SYM
    WHILE ::= WHILE_SYM
    DO_STMT ::= DO_BODY  DO_TEST  SEMICOLON_SYM
    DO_BODY ::= DO_HEADER  STATEMENT
    DO_HEADER ::= DO_SYM
    DO_TEST ::= WHILE_SYM  LEFT_PAR_SYM  IF_EXPR  RGHT_PAR_SYM
    FOR_STMT ::= FOR_HEADER  STATEMENT
    FOR_HEADER ::= FOR_TEST  SEMICOLON_SYM  FOR_ASG  RGHT_PAR_SYM
    FOR_TEST ::= FOR_INIT  SEMICOLON_SYM  IF_EXPR
    FOR_INIT ::= FOR_SYM  LEFT_PAR_SYM  FOR_ASG
    FOR_ASG ::= LVAL_FLD  ASSIGN  IF_EXPR
            ::= LVAL_FLD  ASG_INC_DEC
            ::= ASG_INC_DEC  LVAL_FLD
    JOIN_LIST ::= JOIN_SPECS
              ::= 
    JOIN_SPECS ::= JOIN_SPEC
               ::= JOIN_SPECS  JOIN_SPEC
    JOIN_SPEC ::= JOIN_ORDER  WHERE  IF_EXPR
              ::= JOIN_ORDER
    JOIN_ORDER ::= JOIN_USING
               ::= JOIN_USING  ORDER_GROUP
    JOIN_USING ::= JOIN_CLAUSE  USING_INDEX  STD_ID
               ::= JOIN_CLAUSE  USING_INDEX  HINT_SYM  STD_ID
               ::= JOIN_CLAUSE
    JOIN_CLAUSE ::= OUTER  JOIN_SYM  SELECTOPT  TABLE
    OUTER ::= OUTER_SYM
          ::= EXISTS_SYM
          ::= NOTEXISTS_SYM
          ::= 
    SEARCH_STMT ::= SEARCH_JOIN  STATEMENT
    SEARCH_JOIN ::= SEARCH_WHERE  JOIN_LIST
    SEARCH_WHERE ::= SEARCH_ORDER  WHERE  IF_EXPR
                 ::= SEARCH_ORDER
    WHERE ::= WHERE_SYM
    SUM_ELEM ::= SUM_FUNC  LEFT_PAR_SYM  STD_ID  RGHT_PAR_SYM
    SUM_FUNC ::= SUM_SYM
             ::= AVG_SYM
             ::= CNT_SYM
             ::= MINOF_SYM
             ::= MAXOF_SYM
    SEARCH_ORDER ::= SEARCH_USING
                 ::= SEARCH_USING  ORDER_GROUP
    ORDER_GROUP ::= ORDERBY_CLAUSE  OPT_GROUPBY
                ::= GROUPBY_CLAUSE  OPT_ORDERBY
    OPT_GROUPBY ::= GROUPBY_CLAUSE
                ::= 
    OPT_ORDERBY ::= ORDERBY_CLAUSE
                ::= 
    ORDERBY_CLAUSE ::= ORDER_SYM  OPT_BY  ORDER_ELEM
                   ::= ORDERBY_CLAUSE  LIST_SEP_SYM  ORDER_ELEM
    GROUPBY_CLAUSE ::= GROUP_SYM  OPT_BY  ORDER_ELEM
                   ::= GROUPBY_CLAUSE  LIST_SEP_SYM  ORDER_ELEM
    ORDER_ELEM ::= STD_ID  INDEX  DIRECTION
               ::= ORDER_QUALIFIER  STD_ID  INDEX  DIRECTION
    ORDER_QUALIFIER ::= STD_ID  PERIOD_SYM
    INDEX ::= LEFT_BRKT_SYM  INT_SYM  RGHT_BRKT_SYM
          ::= 
    DIRECTION ::= ASCEND_SYM
              ::= DESCEND_SYM
              ::= 
    OPT_BY ::= BY_SYM
           ::= 
    SEARCH_USING ::= SEARCH_CLAUSE  USING_INDEX  STD_ID
                 ::= SEARCH_CLAUSE  USING_INDEX  HINT_SYM  STD_ID
                 ::= SEARCH_CLAUSE
    USING_INDEX ::= INDEX_SYM
    SEARCH_CLAUSE ::= WHILE_SYM  SELECT_SYM  SELECTOPT  CROSSCOMPANY_CLAUSE  VALIDTIMESTATE_CLAUSE  TABLE
    CROSSCOMPANY_CLAUSE ::= CROSSCOMPANY_SYM
                        ::= CROSSCOMPANY_SYM  COLON_SYM  STD_ID
                        ::= 
    VALIDTIMESTATE_CLAUSE ::= VALIDTIMESTATE_SYM  LEFT_PAR_SYM  STD_ID  LIST_SEP_SYM  STD_ID  RGHT_PAR_SYM
      ::= VALIDTIMESTATE_SYM  LEFT_PAR_SYM  STD_ID  RGHT_PAR_SYM
      ::= 
    SELECTOPT ::= 
              ::= SELECTOPT  REVERSE_SYM
              ::= SELECTOPT  FIRSTFAST_SYM
              ::= SELECTOPT  FIRSTONLY_SYM
              ::= SELECTOPT  FIRSTONLY_SYM1
              ::= SELECTOPT  FIRSTONLY_SYM10
              ::= SELECTOPT  FIRSTONLY_SYM100
              ::= SELECTOPT  FIRSTONLY_SYM1000
              ::= SELECTOPT  FORUPDATE_SYM
              ::= SELECTOPT  NOFETCH_SYM
              ::= SELECTOPT  FORCE_SELECT_ORDER_SYM
              ::= SELECTOPT  FORCE_NESTED_LOOP_SYM
              ::= SELECTOPT  FORCE_LITERALS_SYM
              ::= SELECTOPT  FORCE_PLACEHOLDERS_SYM
              ::= SELECTOPT  REPEATABLEREAD_SYM
              ::= SELECTOPT  OPTIMISTICLOCK_SYM
              ::= SELECTOPT  PESSIMISTICLOCK_SYM
              ::= SELECTOPT  GENERATEONLY_SYM
    FIND_STMT ::= FIND_JOIN  SEMICOLON_SYM
    FIND_JOIN ::= FIND_WHERE  JOIN_LIST
    FIND_WHERE ::= FIND_ORDER  WHERE  IF_EXPR
               ::= FIND_ORDER
    FIND_ORDER ::= FIND_USING
               ::= FIND_USING  ORDER_GROUP
    FIND_USING ::= FIND_TABLE  USING_INDEX  STD_ID
               ::= FIND_TABLE  USING_INDEX  HINT_SYM  STD_ID
               ::= FIND_TABLE
    FIND_TABLE ::= SELECT_SYM  SELECTOPT  CROSSCOMPANY_CLAUSE  VALIDTIMESTATE_CLAUSE  TABLE
      ::= DELETE_SYM  SELECTOPT  CROSSCOMPANY_CLAUSE  VALIDTIMESTATE_CLAUSE  TABLE
    TABLE ::= FLD_LIST  OPT_FROM
    FLD_LIST ::= MULT_SYM
             ::= FIELD_LIST
    FIELD_LIST ::= FIELD_SPEC
               ::= FIELD_LIST  LIST_SEP_SYM  FIELD_SPEC
    FIELD_SPEC ::= STD_ID  INDEX
               ::= SUM_ELEM
    OPT_FROM ::= FROM_SYM  STD_ID
             ::= 
    SETFIELDSMODE ::= 
    UPDATE_STMT ::= UPDATETABLE  SET_SYM  SETFIELDSMODE  FIELDASSIGNMENTS  OPT_WHERE  JOIN_LIST  SEMICOLON_SYM
    UPDATETABLE ::= UPDATE_SYM  SELECTOPT  CROSSCOMPANY_CLAUSE  STD_ID
    OPT_WHERE ::= WHERE  IF_EXPR
              ::= 
    FIELDASSIGNMENTS ::= FIELDASSIGNMENTS  LIST_SEP_SYM  FIELDASSIGNMENT
                     ::= FIELDASSIGNMENT
    FIELDASSIGNMENT ::= STD_ID  INDEX  ASG_SYM  IF_EXPR
    INSERT_PART ::= INSERT_SYM  CROSSCOMPANY_CLAUSE  INSERT_NAME  LEFT_PAR_SYM  INSERTFIELDLIST  RGHT_PAR_SYM
    INSERT_NAME ::= STD_ID
    INSERT_STMT ::= INSERT_PART  FIND_JOIN  SEMICOLON_SYM
    INSERTFIELDLIST ::= INSERTFIELD
                    ::= INSERTFIELDLIST  LIST_SEP_SYM  INSERTFIELD
    INSERTFIELD ::= STD_ID  INDEX
    PRINT_STMT ::= PRINT_CLAUSE  AT_CLAUSE  SEMICOLON_SYM
    PRINT_CLAUSE ::= PRINT  IF_EXPR  EXPR_LIST
    PRINT ::= PRINT_SYM
    AT_CLAUSE ::= AT_SYM  IF_EXPR  LIST_SEP_SYM  IF_EXPR
              ::= 
    WINDOW_STMT ::= WINDOW_SYM  IF_EXPR  LIST_SEP_SYM  IF_EXPR  AT_CLAUSE  SEMICOLON_SYM
    IF_STMT ::= ELSE_STMT
            ::= IF_CONDS
    IF_CONDS ::= IF_COND  STATEMENT
    IF_COND ::= IF_SYM  LEFT_PAR_SYM  IF_EXPR  RGHT_PAR_SYM
    ELSE_STMT ::= ELSE  STATEMENT
    ELSE ::= IF_CONDS  ELSE_SYM
    SWITCH_STMT ::= CASE_LIST  RIGHTBR_SYM
    CASE_LIST ::= SWITCH_SYM  LEFT_PAR_SYM  IF_EXPR  RGHT_PAR_SYM  LEFTBR_SYM
              ::= CASE_TESTS  STMTLIST
    CASE_TESTS ::= CASE_HEADER  COLON_SYM
               ::= CASE_LIST  DEFAULT_SYM  COLON_SYM
    CASE_HEADER ::= CASE  IF_EXPR
                ::= CASEALT  IF_EXPR
    CASE ::= CASE_LIST  CASE_SYM
    CASEALT ::= CASE_HEADER  LIST_SEP_SYM
    EXPR_STMT ::= ASG_STMT  SEMICOLON_SYM
              ::= FUNCTION  SEMICOLON_SYM
              ::= INTRINSICS  SEMICOLON_SYM
              ::= EVAL  SEMICOLON_SYM
    PAUSE_STMT ::= PAUSE_SYM  SEMICOLON_SYM
    BP_CLAUSE ::= BP_SYM  SEMICOLON_SYM
    BREAK_STMT ::= BREAK_SYM  SEMICOLON_SYM
    CONTINUE_STMT ::= CONTINUE_SYM  SEMICOLON_SYM
    RETURN_CLAUSE ::= RETURN_SYM  SEMICOLON_SYM
                  ::= RETURN_SYM  IF_EXPR  SEMICOLON_SYM
    TTS_STMT ::= TTSABORT_SYM  SEMICOLON_SYM
             ::= TTSBEGIN_SYM  SEMICOLON_SYM
             ::= TTSEND_SYM  SEMICOLON_SYM
    FLUSH_STMT ::= FLUSH  ID_LIST  SEMICOLON_SYM
    FLUSH ::= FLUSH_SYM
    TBLLOCK_STMT ::= TABLELOCK  ID_LIST  SEMICOLON_SYM
    TABLELOCK ::= TABLELOCK_SYM
    ID_LIST ::= STD_ID
            ::= ID_LIST  LIST_SEP_SYM  STD_ID
    MOVE_REC_STMT ::= NEXT_SYM  TABLE  SEMICOLON_SYM
    CHANGE_STMT ::= CHANGE_HEADER  STATEMENT
    CHANGE_HEADER ::= CHANGE  LEFT_PAR_SYM  IF_EXPR  RGHT_PAR_SYM
    CHANGE ::= CHANGECOMP_SYM
           ::= CHANGESITE_SYM
    UNCHECKED_STMT ::= UNCHECKED_HEADER  STATEMENT
    UNCHECKED_HEADER ::= UNCHECKED_SYM  LEFT_PAR_SYM  IF_EXPR  RGHT_PAR_SYM
```
 

## X++ Language Syntax is Stricter in Microsoft Dynamics AX 2012
Starting in Microsoft Dynamics AX 2012, the syntax rules for X++ are stricter than in previous versions of the product. This article describes the syntax changes.

### Table of X++ Syntax Changes

The following table displays a list of syntax changes that start in Microsoft Dynamics AX 2012.

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Area</th>
<th>Syntax rule</th>
<th>Before Microsoft Dynamics AX 2012</th>
<th>Starting with Microsoft Dynamics AX 2012</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Escape</td>
<td>The backslash character <span class="code">&lt;/span&gt; is rejected by the compiler for unrecognized escapes</td>
<td>The compiler used to accept &quot;31\12\2002&quot;, but during run time the literal string was interpreted as a different value.</td>
<td>Now the following X++ statement is rejected by the compiler: <span class="code">str myDateString = &quot;31\12\2002&quot;;</span> The proper syntax is <span class="code">&quot;31\12\2002&quot;</span>.</td>
</tr>
<tr class="even">
<td>Exceptions</td>
<td>Retry is no longer allowed outside of a catch block</td>
<td>It was possible to write the <strong>retry</strong> keyword outside of a <strong>catch</strong> block. This caused the program to end when the <strong>retry</strong> was reached during runtime.</td>
<td>Now <strong>retry</strong> can occur only inside a <strong>catch</strong> block. For more information, see Exception Handling with try and catch Keywords.</td>
</tr>
<tr class="odd">
<td>Exceptions</td>
<td>Now you can throw and catch only <code>int</code> values</td>
<td>It was possible to throw scalar expressions like strings and dates, such as <code>throw &quot;hello world&quot;;</code>, and get no compile error. At runtime this was catch-able by a <code>catch</code> block that was not decorated with any specific value, such as <span class="code">catch {print(&quot;Catch worked.&quot;);}</span>.</td>
<td>Now the only expression you can put on the <strong>throw</strong> keyword is an <code>int</code>. Often the best thing to throw is <span class="code">Global::error(&quot;Explanation&quot;);</span>. Often the best thing to catch is an element of the <code>Exception</code> enum. For more information, see Exception Handling with try and catch Keywords.</td>
</tr>
<tr class="even">
<td>Inheritance</td>
<td>Downcasting can now be explicit.
<table>
<thead>
<tr class="header">
<th><strong>Note</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>It is good programming practice to avoid implicit downcasts.</td>
</tr>
</tbody>
</table></td>
<td>It was possible to assign a base object to a derived object with the simple assignment operator, which is the equals sign (<code>=</code>). The compiler accepted these assignments, but during run time any misuse of an improper downcast assignment caused an error.</td>
<td>Now all downcasts can be explicit. This is accomplished with the new <strong>as</strong> expression operator. Explicit downcasting with the <strong>as</strong> keyword is illustrated by the following code example, in which <code>ThingClass</code> extends <code>Object</code>: <code>ThingClass myThing = new ThingClass();</code>  <code>Object myObject = myThing;</code>  <code>myThing = myObject as ThingClass; // Explicit downcast, good.</code> For more information, see Expression Operators: Is and As for Inheritance.</td>
</tr>
<tr class="odd">
<td>Inheritance</td>
<td>Override of a base method cannot be less accessible than the base method</td>
<td>It was possible to have a base method be decorated with <strong>protected</strong> and yet have an override of that method be <strong>private</strong>.</td>
<td>Now when a base method is <strong>protected</strong>, the override method must be either <strong>protected</strong> or <strong>public</strong>, and the override method cannot be <strong>private</strong>. For more information, see Method Access Control.</td>
</tr>
<tr class="even">
<td>Inheritance</td>
<td>Override of a base method must have the exact same return type and parameter signature as the base method</td>
<td>Suppose a base class had a method that inputs a parameter of the <code>Common</code> table, which is the base of all tables. In a derived class it was possible to override the method to instead input <code>MyTable</code>.</td>
<td>Now the parameter signatures of the base method and its override method must match exactly. Also, the return types must match exactly. For more information, see Overriding a Method.</td>
</tr>
<tr class="odd">
<td>Interfaces</td>
<td>Implementation of an interface method must match the parameter signature exactly</td>
<td>Suppose an interface had a method that input a parameter of an <code>int</code>. In a class that implements the interface, it was possible to write the method with a parameter of a <code>str</code>.</td>
<td>Now the parameter signatures of the method must exactly match between the interface and the implementation of the method on a class. Also, the return types must match exactly. For more information, see Interfaces Overview.</td>
</tr>
<tr class="even">
<td>Interfaces</td>
<td>A non-abstract base class that implements an interface cannot rely on a derived class for that implementation</td>
<td>When a base class implements an interface, it was possible for the class to not implement the methods of the interface if a derived class implemented the methods. The only limitation was that the <code>new</code> constructor method could not be called on the class.</td>
<td>Now the compiler requires that every class that implements an interface must have or inherit a complete implementation of every method of the interface. For more information, see X++, C# Comparison: Object Oriented Programming.</td>
</tr>
<tr class="odd">
<td>Modifiers</td>
<td>The <strong>static</strong> modifier should not be applied to an interface</td>
<td>It was possible to write <span class="code">static interface IMyInterface {}</span>, but the <strong>static</strong> modifier had no effect because it makes no sense in this context.</td>
<td>Sometime after Dynamics AX 2009 the X++ compiler might stop allowing the <strong>static</strong> modifier on interface declarations. For more information, see Interfaces Overview.</td>
</tr>
<tr class="even">
<td>Modifiers</td>
<td>The <strong>static</strong> modifier must not be applied to the <code>new</code> constructor</td>
<td>It was possible to apply the <strong>static</strong> modifier to the declaration of the <code>new</code> constructor method. This caused <code>new MyClass();</code> to behave as a null operation. Instead, the statement <span class="code">MyClass::new();</span> would call the static <code>new</code> method, but that would not construct an object.</td>
<td>Now the compiler issues an error when the <strong>static</strong> modifier is applied to the <code>new</code> method. For more information, see Constructors.</td>
</tr>
<tr class="odd">
<td>Modifiers</td>
<td>Use an explicit access modifier on each method</td>
<td>In the past the menu item of <span class="ui">AOT</span> &gt; <span class="ui">Classes</span> &gt; <em>MyClass</em> &gt; <span class="ui">New Method</span> created the method without any access modifier. This meant that the method was implicitly <strong>public</strong>, although some X++ developers might not have been fully aware of the default. This created extra work later when a developer needed to modify the code in the method, because the developer had to research everywhere that the method might be called from.</td>
<td>Now the <span class="ui">New Method</span> menu item explicitly includes the <strong>private</strong> keyword in its automatic declaration of the new method. The developer can type in a different modifier if appropriate. For more information, see Method Modifiers.</td>
</tr>
<tr class="even">
<td>Parameters</td>
<td>Parameters given in a call to a <code>new</code> constructor method must match the parameters on the <code>new</code> constructor method</td>
<td>It was possible to pass in multiple parameters on call to a <code>new</code> constructor method even when the <code>new</code> method was declared to input no parameters.</td>
<td>Now the call to the <code>new</code> method must exactly match the declared parameter signature of the <code>new</code> method. For more information, see Creating a Subclass.</td>
</tr>
<tr class="odd">
<td>Parameters</td>
<td>Parameters with default values must come after all parameters that do not have default values</td>
<td>It was possible to declare a method that takes in two parameters, and have only the first parameter offer a default value. There was no purpose to this. There was no way to accept the default of the first parameter because the call must specify a value for the second parameter and cannot omit the first parameter.</td>
<td>Now in the declaration of a method, any parameter that offers a default value must come after all the parameters that do not. For more information, see the following topics:
<ul>
<li>Using Optional Parameters</li>
<li>Best Practices for Parameters</li>
</ul></td>
</tr>
<tr class="even">
<td>Parameters</td>
<td>Override of a method must have the same default parameters as the overridden method</td>
<td>It was possible to declare a method as <span class="code">public void myMethod(int i=22){}</span> and the override as <span class="code">public void myMethod(){}</span>. But if the override method was called as <code>derivedObject(333);</code> an error occurred.</td>
<td>Now the override method must list the same parameter types in the same sequence that they are declared in the overridden method. For more information, see Overriding a Method.</td>
</tr>
<tr class="odd">
<td>Preprocessor</td>
<td>A <strong>TODO</strong> in a comment must be the first non-whitespace in the first line of the comment</td>
<td>The X++ preprocessor used to detect the <strong>TODO</strong> keyword in a multi-line <span class="code">/* ... */</span> task comment even when the <strong>TODO</strong> appeared after other text after the first comment line.</td>
<td>Now the X++ preprocessor detects the <strong>TODO</strong> keyword only if <strong>TODO</strong> appears on the first line of the comment, and as the first non-whitespace in the comment. For more information, see TODO Comments for X++ Developer Tasks.</td>
</tr>
</tbody>
</table>



## Additional resources

[X++ Language Reference](xpp-language-reference.md)




[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
