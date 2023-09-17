---
title: X++ operators
description: This article describes the operators supported in X++.
author: josaw1
ms.date: 12/02/2019
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# X++ operators

[!include [banner](../includes/banner.md)]

This article describes the operators supported in X++.

## Assignment operators

An assignment changes the value of a variable or field. The following table shows the X++ assignment operators. There is no difference between prefix and postfix operators.

| Operator   | Description                                                                                      |
|------------|--------------------------------------------------------------------------------------------------|
| `=`        | Assign the expression on the right of the equal sign to the variable on the left.                |
| `+=`       | Assign the current variable value plus the expression on the right to the variable on the left.  |
| `++`       | Increment the variable by 1.                                                                     |
| `-=`       | Assign the current variable value minus the expression on the right to the variable on the left. |
| `--`       | Decrement the variable by 1.                                                                     |

### Code examples for assignment operators

```xpp
// An example of assignment operators and their output. 
static void Example1()
{
    int i = 1;
    // Using the = operator. i is assigned the value of i, plus 1. i = 2.
    i = i + 1;
    info(strFmt("Example 1: The result is "), i); // The result is 2.
}

static void Example2()
{
    int i = 1;
    // Using the += operator. i is assigned the value of i, plus 1. 
    // i = 2 (i = i + 1).
    i += 1;
    info(strFmt("Example 2: The result is "), i); // The result is 2. 
}

static void Example3()
{
    int i = 1;
    // Using the ++ operator. i is incremented by 1, and then 
    // by 1 again in the second statement. The final value of i is 3.
    i++;
    ++i;
    info(strFmt("Example 3: The result is "), i); // The result is 3. 
}

static void Example4()
{
    int i = 1;
    // Using the -= operator. i is assigned the value of i minus 1. 
    // i = 0 (i = i - 1).
    i -= 1;
    info(strFmt("Example 4: The result is "), i); // The result is 0. 
}

static void Example5()
{
    int i = 1;
    // Using the -- operator. i is decremented by 1, and then by 
    // 1 again in the second statement. The final value of i is -1.
    i--;
    --i;
    info(strFmt("Example 5: The result is "), i); // The result is -1. 
}
```

## Arithmetic operators
You use arithmetic operators to perform numeric calculations. Most of the operators are binary and take two operands. However, the **not** (`~`) operator is unary and takes only one operand. Syntax for binary operators: *expression1* *ArithmeticOperator* *expression2* Syntax for unary operators: *ArithmeticOperator* *expression1*

| Operator   | Description      |
|------------|------------------|
| `<<`       | The **left shift** operator performs *expression2* left shift (multiplication by 2) on *expression1*.              |
| `>>`       | The **right shift** operator performs *expression2* right shift (division by 2) on *expression1*.                  |
| `\*`       | The **multiply** operator multiplies *expression1* by *expression2*.                                               |
| `/`        | The **divide** operator divides *expression1* by *expression2*.                                                    |
| `DIV`      | The **integer division** operator performs an integer division of *expression1* by *expression2*.                  |
| `MOD`      | The **integer remainder** operator returns the remainder of an integer division of *expression1* by *expression2*. |
| `~`        | The **not** operator, or unary operator, performs a binary not operation.                                          |
| `&`        | The **binary AND** operator performs a binary and operation on *expression1* and *expression2*.                    |
| `^`        | The **binary XOR** operator performs a binary XOR-operation on *expression1* and *expression2*.                    |
| `|`        | The **binary OR** operator performs a binary or operation on *expression1* and *expression2*.                      |
| `+`        | The **plus** operator adds *expression1* to *expression2*.                                                         |
| `-`        | The **minus** operator subtracts *expression2* from *expression1*.                                                 |
| `?`        | The **ternary** operator takes three expressions: *expression1* ? *expression2* : *expression3*. If *expression1* is true, *expression2* is returned. Otherwise, *expression3* is returned. |

### Code examples for arithmetic operators

```xpp
int a = 1 << 4;      // Perform four left shifts on 1 (1*2*2*2*2). a=16.
int b = 16 >> 4;     // Perform four right shifts on 16 (16/2/2/2/2). b=1.
int c = 4 * 5;       // Multiply 4 by 5. c=20.
int d = 20 / 5;      // Divide 20 by 5. d=4.
int e = 100 div 21;  // Return the integer division of 100 by 21. e=4 (4*21 = 84, remainder 16).
int f = 100 mod 21;  // Return the remainder of the integer division of 100 by 21. f=16.
int g = ~1;          // Binary negate 1 (all bits are reversed). g=-2.
int h = 1 & 3;       // Binary AND. Return the bits that are in common in the two integers. h=1.
int i = 1 | 3;       // Binary OR. Return the bits that are set in either 1 or 3. i=3.
int j = 1 ^ 3;       // Binary XOR. Return the bits that are set in 1 and NOT set in 3, and vice versa. j=2.
int k = 1 + 3;       // Add 1 and 3. k=4.
int l = 3 - 1;       // Subtract 1 from 3. l=2.
int m = (400 > 4) ? 1 : 5;  // If 400>4, 1 is returned. Otherwise, 5 is returned. Because 400>4, 1 is returned. m=1.
```

## Expression operators
The `as` and `is` expression operators control downcast assignments. Downcast assignments involve class or table inheritance. Assignment statements that implicitly downcast can cause errors that are difficult to predict and diagnose. You can use the `as` keyword to make your downcasts explicit. You can use the `is` keyword to test whether a downcast is valid at run time.

### The as keyword

Use the `as` keyword for assignments that downcast from a base class variable to a derived class variable. The `as` keyword tells other programmers and the compiler that you believe that the downcast will be valid during run time.

-   The compiler reports an error for downcast assignment statements that lack the `as` keyword.
-   At run time, the `as` keyword causes the downcast assignment statement to assign `null` if the downcast isn't valid.
-   This `is` keyword is often used to safely test whether the `as` keyword will work.

#### Code example for the as keyword

In the following code example, the **DerivedClass** class extends the **BaseClass** class. The code example contains two valid assignments between its **basec** and **derivedc** variables. The upcast assignment to **basec** doesn't require the `as` keyword, but the downcast assignment to **derivedc** does require the `as` keyword. The following code will compile and run without errors.

```xpp
static void AsKeywordExample()
{
    // DerivedClass extends BaseClass.
    BaseClass basec;
    DerivedClass derivedc;
    // BottomClass extends DerivedClass.
    BottomClass bottomc;
    derivedc = new DerivedClass();
    // AS is not required for an upcast assignment like this.
    basec = derivedc;
    // AS is required for a downcast assignment like this.
    derivedc = basec as DerivedClass;
    bottomc = new BottomClass();
    // AS causes this invalid downcast to assign null.
    bottomc = basec as DerivedClass;
}
```

### The is keyword

The `is` keyword verifies whether an object is a subtype of a specified class. The `is` expression returns **true** if the object is a subtype of the class, or if the object is the same type as the class. The compiler reports an error if an `is` keyword expression compares two types, but neither type is a subtype of the other, and they aren't of the same type. The compiler reports a similar error for any plain assignment statement between two types, where neither type is a subtype of the other, and they aren't of the same type. At run time, the type of variable that references the underlying object is irrelevant to the `is` keyword. The `is` keyword causes the system to verify the object that the variable references, not the declared type of the variable that references the object.

#### Code examples for the is keyword

The following code examples illustrate the conditions that control whether an `is` expression returns **true** or **false**. The code examples depend on the fact that the **Form** class and the **Query** class both extend the **TreeNode** class.

```xpp
// The compiler issues an error for the following code. 
// The compiler ascertains that the Form class and the Query class are not 
// part of the same inheritance hierarchy. Both the Form class and the Query class
// extend the TreeNode class, but neither Form nor Query is a subtype of the other.
Form myForm = new Form();
info(strFmt("%1", (myForm is Query)));

// The Infolog displays 0 during run time, where 0 means false. No supertype 
// object can be considered to also be of its subtype class.
TreeNode myTreeNode = new TreeNode();
info(strFmt("%1", (myTreeNode is Form)));

// The Infolog displays 0 during run time, where 0 means false. A null 
// reference causes the is expression to return false.
Form myForm;
info(strFmt("%1", (myForm is Form)));

// The Infolog displays 1 during run time, where 1 means true. 
// An object is an instance of its own class type.
Form myForm = new Form();
info(strFmt("%1", (myForm is Form)));

// The Infolog displays 1 during run time, where 1 means true. 
// Every subtype is also of its supertype.
Form myForm = new Form();
info(strFmt("%1", (myForm is TreeNode)));

// The Infolog displays 1 during run time, where 1 means true. 
// The type of the underlying object matters in the is expression,
// not the type of the variable that references the object.
Form myForm = new Form();
TreeNode myTreeNode;
myTreeNode = myForm; // Upcast.
info(strFmt("%1", (myTreeNode is Form)));
```

#### Code example for the is and as keywords

The following code example contains a typical use of the `is` keyword. The `as` keyword is used after the `is` keyword verifies that the `as` keyword will succeed. In this example, the `is` and `as` keywords are uppercase to make them more visible.

```xpp
static void IsKeywordExample() 
{
    DerivedClass derivedc;
    BaseClass basec;
    basec = new DerivedClass();  // An upcast.
    if (basec IS DerivedClass)
    {
        info("Test 1: (basec IS DerivedClass) is true. Good.");
        derivedc = basec AS DerivedClass;
    }
    basec = new BaseClass();
    if (!(basec IS DerivedClass))
    {
        info("Test 2: !(basec IS DerivedClass) is true. Good.");
    }
}

//Output to the Infolog
Test 1: (basec IS DerivedClass) is true. Good.
Test 2: (!(basec IS DerivedClass)) is true. Good.
```

### Object class as a special case

The **Object** class can appear as a special case in inheritance functionality. The compiler bypasses type checking for assignments to and from variables that are declared to be of type **Object**. Some classes inherit from the **Object** class, some classes inherit from another class, and some classes don't inherit from any class. Although the **Dialog** class doesn't inherit from any class, the assignment and call statements in the following code example work. However, if the assignment is `bank4 = dlog3;`, it will fail at compile time, because the **Bank** and **Dialog** classes have no inheritance relationship to each other. The compiler performs only one small validation on assignments to a variable that is declared to be of the **Object** class. The compiler verifies that the item that is being assigned to the **Object** variable is an instance of a class. The compiler doesn't allow an instance of a table buffer to be assigned to the **Object** variable. Additionally, the compiler doesn't allow primitive data types, such as `int` or `str`, to be assigned to the **Object** variable.

```xpp
static void ObjectExample()
{
    Bank bank4;
    Object obj2;
    Dialog dlog3 = new Dialog("Test 4.");
    obj2 = dlog3;  // The assignment does work.
    obj2.run(false);  // The call causes the dialog to appear.
    info("Test 4a is finished.");
}
```

### Tables

All tables inherit directly from the Common system table, unless they explicitly inherit from a different table. The Common table can't be instantiated. It doesn't exist in the underlying physical database. The Common table inherits from the **xRecord** class, but in a special way that isn't appropriate for the `is` keyword or the `as` keyword. When the `as` keyword is used to perform an invalid downcast among tables, the target variable references an unusable non-null entity. Any attempt to de-reference the target variable will cause an error that stops the program.

### The is and as keywords and extended data types

Each extended data type has an **Extends** property. The style of inheritance that this property controls differs from the style of inheritance that the `is` and `as` keywords are designed for.

## Relational operators
The following table lists the relational operators that can be used in X++. Most of the operators are binary and take two operands. However, the **not** (`!`) operator is unary and takes only one operand. Syntax for binary operators: *expression1* *relationalOperator* *expression2* Syntax for unary operators: *relationalOperator* *expression1*

| Operator | Description     |
|----------|--------------------------------|
| `like`   | The **like** relational operator returns **true** if *expression1* is like *expression2*.  |
| `==`     | The **equal** relational operator returns **true** if both expressions are equal.  |
| `>=`     | The **greater than or equal to** relational operator returns **true** if *expression1* is greater than or equal to *expression2*.   |
| `<=`     | The **less than or equal to** relational operator returns **true** if *expression1* is less than or equal to *expression2*.|
| `>`      | The **greater than** relational operator returns **true** if *expression1* is greater than *expression2*. |
| `<`      | The **less than** relational operator returns **true** if *expression1* is less than *expression2*.  |
| `!=`     | The **not equal** relational operator returns **true** if *expression1* differs from (that is, if it isn't equal to) *expression2*.                          |
| `&&`     | The **and** relational operator returns **true** if both *expression1* and *expression2* are true.  |
| `||`     | The **or** relational operator returns **true** if *expression1* or *expression2* is true, or if both are true. |
| `!`      | The **not** or **unary** relational operator negates the expression. It returns **true** if the expression is false and **false** if the expression is true. |

### The like operator

The `like` operator can use `*` as a wildcard character for zero or more characters, and `?` as a wildcard character for one character. The maximum length of the operand is 1,000 characters. The `like` operator is evaluated by the underlying SQL, so the result might differ on different installations. If the expressions that you're comparing contain a file path, you must include four backslashes between each element, as shown in the following example.

```xpp
select * from xRefpaths
where xRefPaths.Path like "\\\\Classes\\\\AddressSelectForm"
```

### The equal (==) operator

When you use the **equal** (`==`) operator to compare objects, the object references are compared, not the objects themselves. This behavior might cause issues if you compare two objects, one of which is located on the server, and the other of which is located on the client. In these cases, you should use the **equal** method in the **Object** class. You can override this method to specify what it means for two objects to be equal. If you don't override the **equal** method, the comparison is identical to the comparison that is done by the **equal** (`==`) operator.

### Code examples for relational operators

```xpp
"Jones" like "Jo?es"  // Returns true, because the ? is equal to any single character.
"Fabrikam, Inc." like "Fa*"  // Returns true, because the * is equal to zero or more characters.
(( 42 * 2) == 84)  // Returns true, because 42*2 is equal to 84.
today() >= 1\1\1980  // Returns true, because today is later than January 1, 1980.
((11 div 10) >= 1)  // Returns true, because 11 div 10 is 1 (therefore, >= 1 is true).
(11<= 12)  // Returns true, because 11 is less than 12.
((11 div 10) > 1)  // Returns false, because 11 div 10 is 1.
(11 div 10) < 1)  // Returns false, because 11 div 10 is 1.
(11 != 12)  // Returns true, because 11 is not equal to 12.
(1 == 1) && (3 > 1)  // Returns true, because both expressions are true.
```

## Operator precedence
The order that a compound expression is evaluated in can be important. For example, `(x + y / 100)` gives a different result, depending on whether the addition or the division is done first. You can use parentheses (`()`) to explicitly tell the compiler how it should evaluate an expression. For example, you can specify `(x + y) / 100`. If you don't explicitly tell the compiler the order that you want operations to be done in, the order is based on the precedence that is assigned to the operators. For example, the division operator has higher precedence than the addition operator. Therefore, for the expression `x + y / 100`, the compiler evaluates `y / 100` first. In other words, `x + y / 100` is equivalent to `x + (y / 100)`. To make your code easy to read and maintain, be explicit. Use parentheses to indicate which operators should be evaluated first. The following table lists the operators in order of precedence. The higher an operator appears in the table, the higher its precedence. Operators that have higher precedence are evaluated before operators that have lower precedence. Note that the operator precedence of X++ isn't the same as the operator precedence of other languages, such as C\# and Java.


| Operator groups, in order of precedence                          |                 Operators    |
|------------------------------------------------------------------|------------------------------|
| Unary                                                            | `- ~ !`                      |
| Multiplicative, shift, bitwise **AND**, bitwise exclusive **OR** | `* / % DIV << >> & ^ `       |
| Additive, bitwise inclusive **OR**                               | `+ - |`                     |
| Relational, equality                                             | `< <= == != > >= like as is` |
| Logical (**AND**, **OR**)                                        | `&&` `||`                    |
| Conditional                                                      | `? :`                        |

Operators on the same line have equal precedence. If an expression includes more than one of these operators, it's evaluated from left to right, unless assignment operators are used. (Assignment operators are evaluated from right to left.) For example, `&&` (logical `AND`) and `||` (logical `OR`) have the same precedence, and are evaluated from left to right. Therefore: 
+ `0 && 0 || 1` is equal to `1`
+ `1 || 0 && 0` is equal to `0`.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
