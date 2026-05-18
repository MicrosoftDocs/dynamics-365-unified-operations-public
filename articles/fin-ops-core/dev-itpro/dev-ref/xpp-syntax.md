---
title: X++ syntax
description: Learn about the syntax reference for X++, including a table that outlines descriptions for various reserved keywords.
author: pvillads
ms.author: pvillads
ms.topic: language-reference
ms.date: 03/31/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# X++ syntax

[!include [banner](../includes/banner.md)]

This article provides the syntax reference for X++. 

## X++ keywords

The following table lists reserved X++ keywords. You can't use these keywords for any other purpose.

| Reserved word | Description | Related information |
|---|---|---|
| **!** | Not. | Relational Operators |
| **!=** | Inequality operator (not equal to). | Relational Operators |
| **#** | Prefix on macro names. | How to: Use #define and #if to Test a Macro |
| **&** | Binary AND. | Arithmetic Operators |
| **&&** | Logical AND. | Relational Operators |
| **(** | Function call operator, which indicates the beginning of the function call. | |
| **)** | Function call operator, which indicates the end of the function call. | |
| **\*** | Multiply. The asterisk (`*`) is also used in X++ SQL. One use is to signify all fields from the tables on a `select` statement. Another use is as a wildcard with the `like` operator, to signify 0 to many characters of any kind. The `like` operator also uses the `?` character. | Arithmetic Operators |
| **^** | Binary XOR. | Arithmetic Operators |
| **\|** | Binary OR. | Arithmetic Operators |
| **\|\|** | Logical OR. | Relational Operators |
| **~** | Not. | Arithmetic Operators |
| **+** | Plus. | Arithmetic Operators |
| **++** | Increment. | Assignment Operators |
| **+=** | Additive assignment. | Assignment Operators |
| **,** | Comma operator. Expressions separated by commas are evaluated sequentially left-to-right. | |
| **-** | Minus. | Arithmetic Operators |
| **--** | Decrement operator. | Assignment Operators |
| **-=** | Subtractive assignment. | Assignment Operators |
| **.** | Class member access operator, for example, `formRun.run` accesses the `run` method of an object of the class type `FormRun`. | |
| **/** | Divide. | Arithmetic Operators |
| **\\** | Escape in strings. Escapes extra quotation marks, and certain letters such as `'\t'` for tab. | |
| **@** | Escape of keywords. For example, `var @str = 1@abstract;` fails to compile without the **@** character that causes any string following it to be regarded as an identifier. It also affects literal strings, by negating the effect of the \ escape character, and by enabling the string to span more than one line in the source code. The new line is represented by one character of hexadecimal 0x0A, which is commonly called a line feed. No carriage return character of hexadecimal 0x0D is included, as in 0x0D0A. | |
| **:** | The colon (`:`) character is used to delimit case values in the `switch` statement. | |
| **::** | Used to call static (class) methods: `ClassName::methodName() and to designate enumeration literals, like NoYes::Yes`. | |
| **;** | Terminates statements. Used in `for` loops or as a separator of initializer, update, and value check parts. | |
| **<** | Less than. | Relational Operators |
| **<<** | Left shift. | Arithmetic Operators |
| **<=** | Less than or equal. | Arithmetic Operators |
| **=** | Assignment operator. The argument to the left of "**=**" is set to the value of the argument to the right. | Assignment Operators |
| **==** | Returns true if the expressions are equal. | Relational Operators |
| **>** | Greater than. | Relational Operators |
| **>=** | Greater than or equal. | Relational Operators |
| **>>** | Bitwise Right Shift. This operator shifts bits in the left hand side by the amount on the right hand side. Each shift effectively divides the number by 2^n, where n is the number of positions shifted. | Arithmetic Operators |
| **?:** | Ternary operator. The question mark (`?`) character is also used by the `like` operator to signify exactly one character of any kind. The `like` operator also uses the `*` character. | Ternary Operator (?) |
| **[** | Array declarator, open. Must be used with "**]**". | |
| **]** | Array declarator, close. Must be used with "**[**". | |
| **{** | Starts a compound statement that may in turn contain zero or more statements. The compound statement ends with the closest matching "**}**". | |
| **}** | Indicates the end of the compound statement described above. A "**{**" must appear before the first of these statements. | |
| **abstract** | Class and method modifier. An **abstract** class can't be constructed with the **new** keyword - Only the classes derived from it can. An **abstract** method can't be called, only methods that override it can. A table can be modified as abstract by setting its Abstract property to Yes in the AOT, or by using the `DictTable` class. The Abstract property defaults to No, and it can't be set unless the table is extended by another table. Each row in an abstract table must have a dependent row in a derived table. This means that each row in an abstract table has a value greater than zero in its InstanceRelationType property field. There are no other effects from marking a table as abstract. Informally, programmers often use the term concrete to describe a class that is non-**abstract**. | Method Modifiers Table Inheritance Overview |
| **anytype** | A type that can contain values of any type. | Anytype |
| **as** | Needed when you assign a base class variable to a derived class variable. For example, given a `Derived` class that **extends** a `Base` class, the statement `myDerived = myBase as Derived;` avoids a compiler error by using the **as** keyword. This keyword also applies when you assign a base table variable to a derived table variable. If the value (myBase) isn't of the designated type (Derived) the expression returns null. | Expression Operators: Is and As for Inheritance |
| **asc** | An option on the `order` `by` or `group` `by` clause in a `select` statement. The sorting is ascending. | Select Statement Syntax |
| **at** | Specifies the position of a print window as part of a `print` statement. The print statement shouldn't be used. | Print Statements |
| **avg** | Returns the average of the fields from the rows specified by the `group by` clause in a `select` statement. | Select Statement Syntax |
| **break** | Immediate exit from an iterative code block. | Break Statements |
| **breakpoint** | Represents a breakpoint that is set for debugging purposes. To set a breakpoint in your code, write: `breakpoint;` | |
| **by** | Part of a reserved term, such as group by and order by. | |
| **byref** | Specifies that the parameter being passed to the called method is passed by reference (address), instead of by value. **Byref** is used in X++ when calling a .NET method that takes a parameter by reference (such as with the C# keywords **out** or **ref**). | How to: Use the byref Keyword for CLR Interop. |
| **case** | Selection within a `switch` statement. | Switch Statements |
| **catch** | Used in exception handling. | Exception Handling with try, and catch Keywords |
| **changeCompany** | Changes database settings to another company. | Change Company Design Pattern |
| **class** | Declares a class. | Classes in X++ |
| **client** | Method modifier. These modifiers aren't used anymore. All methods are executed on the server tier. | Method Modifiers |
| **container** | Designates the `container` type. Containers contain a sequence of atomic values and other containers. | Containers |
| **continue** | Forces the next iteration of a loop. | Continue Statements |
| **count** | Returns the number of records from the rows specified by the `group by` clause in a `select` statement. | Select Statement Syntax |
| **crossCompany** | Causes a `select` statement to return data for all companies that the user is authorized to read from. | Cross-Company X++ Code Basics |
| **date** | Specifies a variable of type `date`. | Dates |
| **default** | Default case within `switch` statements. The code block in the default part is executed if the switch value doesn't match any of the `case` clauses provided in the `switch` statement. | Switch Statements |
| **delegate** | A class member that can store multiple references to methods in other classes, and call all those methods when prompted to do so. A delegate can store references to various kinds of methods, including the following: static methods on X++ classes; instance methods on X++ classes; methods on .NET Framework classes. | Event Terminology and Keywords X++, C# Comparison: Event |
| **delete_from** | Deletes records from the database. | delete_from |
| **desc** | An option on the `order by` or `group by` clause in a `select` statement. The sorting is descending. | Select Statement Syntax |
| **display** | Method modifier. A `display` method shows calculated values in a form control. Unlike regular fields, these values aren't stored in the database but are computed dynamically. | Method Modifiers |
| **div** | Integer division. | Arithmetic Operators |
| **do** | Beginning of a `do...while` loop. | Do...while Loops |
| **edit** | Method modifier. An `edit` method in X++ allows users to modify values in a form control while executing custom logic. Unlike `display` methods, which only show calculated values, `edit` methods enable both viewing and editing. | Method Modifiers |
| **else** | Conditional execution (`if...else`). The `else` part of the `if` statement is executed if the expression in the if statement evaluates to `false`. | if and if ... else Statements |
| **eventHandler** | Must be used each time you either add or delete a method reference from a delegate by using the `+=` or `-=` operator. For example: `myDelegate += eventHandler(OtherClass::myStaticMethod);` | Event Terminology and Keywords X++, C# Comparison: Event |
| **exists** | Used with `join` clauses in `select` statements. | Select Statement Syntax |
| **extends** | A class or interface declaration clause. If your class doesn't explicitly extend another class, your class is considered to extend the `Object` class (as if you had written "extends Object"). | Creating a Subclass |
| **false** | Boolean literal. | Booleans |
| **final** | Class and method modifier. Specifies that this method can't be overridden. | Method Modifiers |
| **firstFast** | Used in `select` statements to speed up the fetch for the first row. | Select Statement Syntax |
| **firstOnly** | Used in `select` statements to fetch only the first record. The `firstOnly` keyword doesn't guarantee that a maximum of one record is retrieved by an X++ SQL `select` statement. If the AOS can use the `EntireTable` cache to satisfy the data demands of the `select` statement, the `firstOnly` keyword is ignored. | Select Statement Syntax Set-based Caching |
| **firstOnly10** | Same as **firstOnly**, except returns 10 rows instead of one. | |
| **firstOnly100** | Same as **firstOnly**, except returns 100 rows instead of one. | |
| **firstOnly1000** | Same as **firstOnly**, except returns 1,000 rows instead of one. | |
| **flush** | Clears the entire table cache. This action can be useful when you want to ensure that any changes made to the table are immediately reflected in subsequent operations. | Set-based Caching |
| **for** | For loop iteration. | For Loops |
| **forceLiterals** | Used in `select` statements to reveal actual values that are used in `where` clauses to the Microsoft SQL Server database at the time of optimization. | Select Statement Syntax |
| **forceNestedLoop** | Forces the SQL Server database to use a nested-loop algorithm to process a particular SQL statement containing a `join`. | Select Statement Syntax |
| **forcePlaceholders** | Used in `select` statements to instruct the kernel not to reveal the actual values used in `where` clauses to the Microsoft SQL Server database at the time of optimization. | Select Statement Syntax |
| **forceSelectOrder** | Forces the SQL Server database to access the tables in a join in the specified order. | Select Statement Syntax |
| **forUpdate** | Selects records exclusively for update. The operation to perform on the records that are fetched is an update. Depending on the underlying database, the records might be locked for other users. | Select Statement Syntax |
| **from** | Part of a `select` statement. The `from` clause specifies the table buffer in which the columns exist. | Select Statement Syntax |
| **group** | Part of the `group by` clause in a `select` statement. | Select Statement Syntax |
| **if** | Conditional execution. | if and if ... else Statements |
| **implements** | Implementation of an `interface`. | Interfaces Overview |
| **insert_recordset** | Copies data from one or more tables into one resulting destination table on a single server trip. | insert_recordset |
| **int** | Specifies a variable of type `integer` (32-bit). | Integers |
| **int64** | Specifies a variable of type `integer` (64-bit). | Integers |
| **interface** | Interface declaration. | Interfaces Overview |
| **is** | Asks whether the object referenced by a class variable either inherits from the given class or is of the given class. For example, given a `Derived` class that **extends** a `Base` class, the expression `(myDerived is Base)` returns **true**. This keyword applies to class inheritance and table inheritance. | Expression Operators: Is and As for Inheritance |
| **join** | Tables are joined on columns common to both tables. You can generate a single result set based on multiple tables by using joins. | Select Statement Syntax |
| **like** | Tests for matches by pattern, with wildcard symbols '*' and '?'. | Relational Operators |
| **maxof** | Returns the maximum of the fields from the rows specified by the `group by` clause. | Select Statement Syntax |
| **minof** | Returns the minimum of the fields from the rows specified by the `group by` clause. | Select Statement Syntax |
| **mod** | Returns the integer remainder of the left expression1 divided by the right expression2. Informally this is sometimes called the modulo operator. `(12 mod 7) == 5` is true. | |
| **new** | Operator. Creates an instance of a class or allocates memory for an array. | |
| **next** | Fetches the next record in a table or calls the next method in a chain-of-command sequence. | |
| **noFetch** | Indicates that no records are to be fetched now. | Select Statement Syntax |
| **notExists** | Used with `join` clauses in `select` statements. | Select Statement Syntax |
| **null** | Symbolic constant. | |
| **optimisticLock** | Forces a statement to run with optimistic concurrency control, even if a different value is set on the table. | Select Statement Syntax |
| **order** | Part of the `order by` clause in a `select` statement. | Select Statement Syntax |
| **outer** | outer join. | Select Statement Syntax |
| **pause** | Halts the execution of a job. The user is asked to state whether execution should continue. You shouldn't use this statement in production code. | Select Statements |
| **pessimisticLock** | Forces a statement to run with pessimistic concurrency control, even if a different value is set on the table. | Select Statement Syntax |
| **print** | Allows you to display output on the screen. You shouldn't use this statement in production code. | Print Statements |
| **private** | Method access modifier. The method can only be used within the class that declares the method. | Method Access Control |
| **protected** | Method access modifier. The method can be used from methods in the class declaring the methods, and in any derived classes. | Method Access Control |
| **public** | Method access modifier. The method may be called from any class. | Method Access Control |
| **real** | Designates the `real` type, a decimal type without rounding errors. | Reals |
| **repeatableRead** | Specifies that no other transactions can modify data that the current transaction reads until the current transaction finishes. An explicit transaction finishes at either **ttsAbort** or at the outermost **ttsCommit**. For a stand-alone **select** statement, the transaction duration is the duration of the **select** command. However, the database sometimes enforces the equivalent of **repeatableRead** in individual **select** statements even without this keyword appearing in your X++ code (depending on how the database decides to scan the tables). | For more information, see the documentation for the underlying relational database product. |
| **retry** | Used in exception handling. | Exception Handling with try, and catch Keywords |
| **return** | Returns from a method. | Declaration of Methods |
| **reverse** | Records are returned in reverse order. | Select Statement Syntax |
| **select** | The `select` clause designates which columns or views are shown in the result set. | Select Statements |
| **server** | Method modifier. This modifier is ignored and shouldn't be used, since all methods are executed on the server side. | Method Modifiers |
| **setting** | Used with the `update_recordset` command. | update_recordset |
| **static** | Static methods can't refer to instance variables (only to static variables). Invoke static methods by using the class name rather than on an instance of the class ("`MyClass.aStaticProcedure`"). | Method Modifiers |
| **str** | Designates the `string` type. | Strings |
| **sum** | Returns the sum of the fields from the rows specified by the `group by` clause in a `select` statement. | Select Statement Syntax |
| **super** | Calls the method that the current method overrides. | Table Methods |
| **switch** | Switch statement. | Switch Statements |
| **tableLock** | Obsolete; **tableLock** is no longer available. | |
| **this** | A reference to the current instance of the class. Used in X++ code inside an instance method of the class. Used to reference *method* members of the class. | |
| **throw** | Used in exception handling. | Exception Handling with try, and catch Keywords |
| **true** | Boolean literal. | Booleans |
| **try** | Used in exception handling. | Exception Handling with try, and catch Keywords |
| **ttsAbort** | Rolls back (discards) all changes in the current transaction. | Transaction Integrity |
| **ttsBegin** | Marks the beginning of a transaction. | Transaction Integrity |
| **ttsCommit** | Marks the end of a transaction, committing the changes to the tables. | Transaction Integrity |
| **update_recordset** | Allows the manipulation of row sets within one operation. | update_recordset |
| **validTimeState** | Filters rows that an X++ SQL `select` statement retrieves from a valid time state table. For example: `select validTimeState(myDateEffective) * from xMyTable;` ...or... `select validTimeState(myDateFrom, myDateTo) * from xMyTable;` | Effects of Valid Time State Tables on Read and Write Operations |
| **void** | Identifies a method that doesn't return a value. | Declaration of Methods |
| **where** | Part of a `select` statement. The `where` clause specifies the conditions to be satisfied; that is, the rows that you want to include in the result. | Select Statement Syntax |
| **while** | Iteration statement. Executes a statement repeatedly as long as the test condition is true. | While loops while select Statements |
| **window** | Allows you to alter the size of the output window. Used with `print` statements that aren't recommended in production code. | Print Statements |

## Expressions syntax
Use an expression in X++ for mathematical or logical operations. Build expressions on the data types of the language. An expression always returns a value of some type. Use this value in calculations, assignments, conditional statements, and so on.

### EBNF description of expressions in X++

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

Semantic restrictions apply to the preceding syntax. You can't call any method by using the `::` operator. Similarly, you can't use the **this** keyword without an active object. That object must be within an instance method and so on.

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

## EBNF overview
Extended Backus Naur Form (EBNF) is a metalanguage. This guide uses it to describe the language syntax. An EBNF definition consists of production rules, nonterminals, and terminals. The following table shows the key terms.


|    Key terms     |       Example        |              Description                                                                                                          |
|------------------|----------------------|----------------------------------------------------------------------------------------------------------------|
|    Terminals     |      Work\_Team      |     A terminal is one character or a string of characters that never change.                                                                            |
|   Nonterminals   |      `Employee`      | A nonterminal is a description of part of a valid sentence in the language that is defined either by a production rule or a textual description. A nonterminal symbol can always be expanded to one or more terminal symbols. |
| Production rules | Employee = Developer |           Tester                                                                                                             |

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

### How to interpret the Formal BNF grammar

This section describes the grammar of X++ in Backus Naur Form (BNF). A small example of BNF is described here.

```xpp
AA ::= BB  CC_SYM
BB ::= JJ_SYM
   ::= KK_SYM
```

`AA` is the name of a production rule. An `AA` requires a `BB`, followed by a CC\_SYM. A `BB` is also a production rule. Therefore, `BB` isn't a terminal. `BB` must be either a JJ\_SYM or a KK\_SYM. Both JJ\_SYM and KK\_SYM are terminals because they aren't the names of any other production rules. CC\_SYM is also a terminal.

In the BNF for X++ grammar, most of the terminals have \_SYM as the suffix of their name.

### Formal X++ grammar in BNF

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

## Additional resources

[X++ Language Reference](xpp-language-reference.md)




[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
