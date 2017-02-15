---
# required metadata

title: X++ variables and data types
description: This topic describes variables and data types in X++.
author: annbe
manager: AnnBe
ms.date: 2016-08-27 00 - 35 - 19
ms.topic: 
ms.prod: 
ms.service: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 61
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 150183
ms.assetid: 13cc0454-6be9-49a0-819d-0e0644ab4e14
ms.search.region: Global
# ms.search.industry: 
ms.author: annbe
ms.dyn365.intro: Feb-16
ms.dyn365.version: AX 7.0.0

---

# X++ variables and data types

This topic describes variables and data types in X++.

Variables
---------

A **variable** is an identifier that points to a memory location where information of a specific data type is stored. The size, precision, default value, implicit and explicit [conversion](xpp-conversion-run-time-functions.md) functions, and range depends on the variable's data type. The scope of a variable defines the area in in the code which an item can be accessed. This area includes instance variables and local variables. **Instance variables** are declared in class declarations and can be accessed from any methods in the class or from methods that extend the class. **Local variables** can be accessed only in the block in which they were defined. All variables created by users have local scope. When a variable is **declared**, memory is allocated and the variable is initialized to the default value. You can assign a value to a field inline, i.e. along with the declaration of the field itself. This applies to both static and instance fields. Variables can be declared anywhere in a code block in a method, not just at the beginning of a method. **Constant variables** (using the keywords `const` or `readonly`) are variables where the value cannot be changed when the variable is declared. Compared to macros, constants have the following benefits:

-   You can add a documentation comment to the const, not to the value of the macro. Ultimately, the language service will pick this up and provide good information to the user.
-   The const is known by IntelliSense.
-   The const is cross referenced, so you can find all references of a particular constant. This is not the case for a macro.
-   The const is subject to access modifiers, either private, protected, or public. The accessibility of macros is not well understood or even rigorously defined.
-   Const variables have scope, while macros do not.
-   You can see the value of a const or a readonly variable in the debugger.

**Read-only fields** can only be assigned a value once, and that value never changes; the field can be assigned its value either inline, at the place where the field is declared, or in the constructor. Currently, that’s the only difference between const and read-only. When declaring variables of managed types that aren't authored in X++, you have two options. You can fully qualify the type names in the declaration by including the full namespace, or you can add a **using** statement to your file and then leave the namespace off of the type name.

### Variable Code Examples

            
    // An example of two valid variable names.
    str variableName;
    CustInfo custNumber;
            
    // An example of simultaneously declaring and initializing a variable.
    real pi = 3.14159265359; // Assigns value of pi to 12 significant digits.
            
    // An example of initializing an object by using the new method on the class.
    Access accessObject = new Access(); // Simple call to the new method in the Access class.
            
    // An example of multiple declarations using integers.
    int i,j; // Declares 2 integers, i and j.
            
    // An example of multiple declarations using an array.
    int a[100,5], b=1; // Declares array with 100 integers with 5 in memory and b as an integer with value 1.
     
    // An example of how variable scopes work.
    class ANewClass
    {
        // The variable a is declared within the class.
        int a;
        
        // Because the method below is declared within the class,
        // it can access all the variables defined within the class.
        void aNewMethod()
        {
            // The variable b is declared within the method.
            // It can only be accessed by this method.
            int b;
        }
    }
     
    // An example of an assignment of field members inline.
    public class MyClass2
    {
        int field1 = 1;
        str field2 = "Banana";
        void new()
        {
            // ...
        }
    }
     
    class MyClass
    {
        // An example of a constant being declared at the class level.
        public const str MyContent = 'SomeValue';
     
        public int ResultSoFar()
        {
            return 1;
        }
    }

     
    // The constants can then be referenced by using the double-colon syntax.
    str value = MyClass::MyContent;
    // If you're in the scope of the class where the const is defined, 
    // you can omit the type name prefix (MyClass in this example).
     
        
    // An example of the using clause where the alias can denote
    // namespaces and classes.
    using System;
    using IONS=System.IO; // Namespace alias.
    using Alist=System.Collections.ArrayList; // Class alias.
    public class MyClass3
    {
        public static void Main(Args a)
        {
            Int32 I; // Alternative to System.Int32.
            Alist al; // Using a class alias.
            al = new Alist();
            str s;
            al.Add(1);
            s.IONS.Path::ChangeExtension(@"c:\tmp\test.xml", ".txt");
        }
    }

### Var

You can now declare a variable without explicitly providing the type of the variable, if the compiler can determine the type from the initialization expression. Note that the variable is still strongly-typed into one, unambiguous type. It’s only possible to use **var** on declarations where an initialization expressions are provided (from which the compiler will infer the type). There are situations where this can make code easier to read, but this feature shouldn’t be misused. You should use a var when you want to declare local variables when the type of the variable is obvious from the right side of the assignment, or when the precise type is not important, for the declarations of for loop counters, and for disposable objects inside using statements. Don't use var when the type isn't apparent from the initialization expression.

### Var Code Examples

            
    // When the type of a variable is clear from
    // the context, use var in the declaration.
    var var1 = "This is clearly a string.";
    var var2 = 27; // This is an integer (not a real).
    var i = System.Convert::ToInt32(3.4);
            
    // Don't use var when the type of the variable is not clear
    // from the context. Use an explicit type instead.
    int var4 = myObject.ResultSoFar();

### Declare anywhere

Declarations can now be provided anywhere statements can be provided. A declaration is syntactically a statement, a declaration statement. You can, therefore, provide declarations immediately prior to the usage, and you don’t have to declare the variables all in one place. This gives you fine-grained control over the scope of your variables. You can provide smaller scopes for variables, outside of which the variables can’t be referenced. The lifetime of the variable is the scope in which it’s declared. Scopes can be started at the block level (inside compound statements), in **for** statements, and in **using** statements. There are several advantages to making scopes small.

-   Readability is enhanced.
-   You can reduce the risk of reusing a variable inappropriately during long-term maintenance of the code.
-   Refactoring becomes much easier. You can copy code in without having to worry about variables being reused in contexts they shouldn’t.

In this example, we declare the loop counter inside the **for** statement in which it's used.

      void MyMethod()
      {
        for (int i = 0; i < 10; i++)
        {
          info(strfmt("i is %1", i));
        }
      }

The scope of the variable is the **for** statement itself, including the condition expression and the loop update parts. The value can’t be used outside this scope. If you attempt to do that, you will get the following. The compiler will issue an error message in the info call, "'i' is not declared."

      void MyMethod()
      {
        for (int i = 0; i < 10; i++)
        {
          if (i == 7)
          {
            break;
          }
        }
        info(strfmt("Found: %1", i));
      }

You can also scope variables to a **using** statement.

      static void AnotherMethod()
      {
        str textFromFile;

        using (System.IO.StreamReader sr = new System.IO.StreamReader("c:\\test.txt"))
        {
          textFromFile = sr.ReadToEnd();
        }
      }

When you use an object that implements **IDisposable, **you should declare and instantiate it in a **using** statement. The **using** statement calls the **Dispose** method on the object in the correct way, even if an exception occurs while you are calling methods on the object. You can achieve the same result by putting the object inside a try block, and then explicitly calling **Dispose** in a finally block; in fact, this is how the **using** statement is translated by the compiler. The following example shows some of the features described above.

      // loop variable declared within the loop: It will
      // not be misused outside the loop
      for(int i = 1; i < 10; i++)
      {
      // Because this value is not used from outside the loop,
      // its declaration belongs in this smaller scope.
        str s = int2str(i);
        info(s);
      }

To avoid confusion, the compiler will issue an error if you attempt to introduce a variable that would hide another variable in an enclosing scope or even in the same scope. For instance, the following code will cause the compiler to issue the following diagnostic message: "A local variable named 'i' cannot be declared in this scope because it would give a different meaning to 'i', which is already used in a parent or current scope to denote something else." This aligns well with the rules that are known from C\#, but is different from the rule in C++ where shadowing is not diagnosed.

      {
        int i;
        {
          int i;
        }
      }

### Consts/Readonly variables

The concept of macros continues to be fully supported in X++. However, using constants instead of \#defines has a number of benefits.

-   You can add a documentation comment to the const, not to the value of the macro. Ultimately, the language service will pick this up and provide good information to the user.
-   The const is known by IntelliSense.
-   The const is cross-referenced, so you can find all references of a particular constant. This is not the case for a macro.
-   The const is subject to access modifiers, either private, protected, or public. The accessibility of macros is not well understood or even rigorously defined.
-   Consts have scope, while macros do not.
-   You can see the value of consts and readonly variables in the debugger.

Macros that are defined in class scopes (in class declarations) are effectively available in all methods of all derived classes. This was originally a bug in the legacy compiler macro implementation, but this loophole is now massively exploited by application programmers. The new X++ compiler still honors this, but no new code that uses this should be written. This particular feature also considerably impacts compiler performance. Constants can be declared at the class level as suggested below.

    private const str MyContant = 'SomeValue';

The constants can then be referenced by using the double-colon syntax.

      str value = MyClass::MyContant;

If you're in the scope of the class where the const is defined, you can omit the type name prefix (MyClass in the example above). You can easily implement the concept of a macro library this way. The list of macro symbols becomes a class with public const definitions. You can also define consts solely as variables. The compiler will maintain the invariant that the value can't be modified.

    {
      const int Blue = 0x0000FF;
      const int Green = 0x00FF00;
      const int Red = 0xFF0000;
    }

Read-only fields can only be assigned a value once, and that value never changes; the field can be assigned its value either inline, at the place where the field is declared, or in the constructor. Currently, that's the only difference between const and read-only.

## Primitive Data Types
The primitive data types in X++ are anytype, booleans, dates, enums, GUIDs, integers, reals, strings, timeOfDay, and utcdatetime.

## Anytype
The **anytype** data type is a placeholder for any data type. Variables of this type should only be used as arguments and return values. If anytype is used as a variable, you must assign a value to it before it can be used or you will get a run-time error. After you have assigned a value to it, you cannot convert it to another data type. You can use anytype variables in expressions although anytype is usually used as arguments and return types. The size, precision, scope, default value, and range of anytype depends on the conversion type that you assign to it. You can use them in the same way that you can use the data type that you convert them to. For example, if you assign an integer, you can then apply relational and arithmetic operators to the variable. Anytype is automatically converted to dates, enums, integers, reals, strings, extended data types (records), classes, and containers by assigning a value to the type. Explicit [conversion](xpp-conversion-run-time-functions.md) functions can be done by using `any2date`, `any2enum`, `any2int`, `any2real`, and `any2str`. You cannot change the variable to another data type after you have converted to anytype.

### Anytype Code Examples

        
    // An example of using anytype variables.
    public static str range(anytype _from, anytype _to)
    {
        return queryValue(_from) + '..' + queryValue(_to);
    }

    // Another example of using anytype variables.
    void put(int position, anytype data)
    {
        record = conPoke (record, position, data);
    }

    public void AnytypeMethod()
    {
        // An example of automatic conversion for anytype.
        anytype a;
        a = "text"; // Automatically assigns a string literal.
    }

## Boolean
The **boolean** data type contains a value that evaluates to either **true** or **false**. You can use the X++ reserved literals true and false where ever a boolean expression is expected. A boolean's size is 1 byte. The default value for a boolean is **false** and its internal representation is as a short number. A boolean is automatically converted to **int**, **date**, or **real**. It has no explicit conversion functions. In X++, the internal representation of a boolean is an integer. You can assign any integer value to a variable declared of type boolean. The integer value 0 (zero) evaluates to false, and all other integer values evaluate to true. Because the internal representation of a boolean is an integer, boolean values are automatically converted into integers and reals.

### Boolean Code Examples

        
    public void BooleanMethod()
    {
        // Simple declaration of a boolean variable, b.
        boolean b;
            
        // Multiple declarations of booleans.
        boolean b1, b2;
          
        // Boolean variable is initialized to true.
        boolean b3 = true;
            
        // Declares a dynamic array of booleans.
        boolean b4[];
            
        // This example shows the most common usage of a boolean: a boolean in
        // a conditional statement and as a result of a logical expression.
        void main()
        {
            // Declares a boolean called exprValue.
            boolean exprValue;
                
            // Assigns ExprValue the value of (7*6 == 42), which equates to true.
            exprValue = (7*6 == 42);
                
            // If the conditional statement is true, print "OK".
            if (exprValue)
            {
                print "OK";  //"OK" is printed because the expression is true.
            }
        }
    }

## Date
The **date** data type contains the day, month, and year. Dates can be written as literals in X++ by using this syntax: `Date literal = day \ month \ year`. You must use four digits for the year. The date data type can hold dates between January 1, 1900, and December 31, 2154. The size of a date is 32 bits. The default value is **null** and the internal representation is as a **date**. A date has no implicit conversions, but can be explicitly [converted](xpp-conversion-run-time-functions.md) through the use of `str2date`, `date2str`, `date2num`, and `int2date`. You can add and subtract integers from dates but you cannot add or subtract two dates from each other. This will result in a compiler error.

### Date Code Examples

        
    public void DateMethod()
    {
        // Simple declaration of a date variable, d.
       date d;
            
        // Multiple declaration of two date variables.
        date d1, d2;
            
        // A date variable, d3, is initialized to the 21st of November 1998.
        date d3 = 21\11\1998;
            
        // Declaration of a dynamic array of dates.
        date d4[];
            
        // Using arithmetic operators with integer variables and dates.
        void myMethod()
        {
            int anInteger;
            date aDate;
            // Sets the date variable aDate to January 1, 1998.
            aDate = 1\1\1998;
            // Sets the integer variable anInteger to 30.
            anInteger = 30;
            // Uses an integer value in the computation of dates.
            // This sets aDate to aDate + 30; that is the 31st of January 1998.
            aDate = aDate + anInteger;
                
            // Create 2 variables, set bDate, and then subtract from that date.
            date bDate;
            int dateDifference;

            bDate = 2\10\1998; 
            dateDifference = bDate - aDate;    // dateDifference will equal 9.
        }
    }

## Enums
An **enum** (also known as an **enumerable**) is a list of literals that X++ uses. You must declare an enum in the Application Explorer before you can use it. Enum values are represented internally as integers. The first literal has number 0, the next has number 1, the next has number 2, and so on. You can use enums as integers in expressions. The default value for the first entry is **0** and the internal representation is a short number. Enums are automatically converted to a **boolean**, **int**, or **real**. An enum can also be explicitly [converted](xpp-conversion-run-time-functions.md) through the use of `enum2str` and `str2enum`. There are hundreds of enumerable types that are built into the standard application. For example, the enum `NoYes` has two associated literals, where No has the value 0, and Yes has the value 1. You can create as many enums as you want, and you can declare up to 251 (0 to 250) literals in a single enum type. To reference an enum, use the name of the enum, followed by the name of the literal, separated by two colons. For example, to use the literal `No` in the `NoYes` enum, write `NoYes::No`.

### Creating an Enum

1.  In **Solution Explorer**, right-click the project, point to **Add**, and then click **New Item**.
2.  Under **AX Artifacts**, select **Data Types**.
3.  Click **Base Enum** to select the new item type.
4.  In the **Name** field, enter the name of your enum, and then click **Add**. This adds a new enum to the project, and opens the enum designer for the new element.
5.  In the enum designer, right-click on the enum name and then click **New Element**.
6.  In the **Properties** window, enter the Name of the enum element.

### Enum Code Examples

        
    public void EnumMethod()
    {
        // Declare the enum (a NoYes enum) in the Application Explorer.
        NoYes done;
            
        // An array of Criteria enums.
        Criteria crit[100];
    }

## GUIDs
A **GUID** (a **globally unique identifier**) is an integer that can be used across all computers and networks wherever a unique identifier is required. Such a number has a very low probability of being duplicated. A valid GUID meets all of these specifications:

-   It must have 32 hexadecimal digits.
-   It must have four dash characters embedded at the locations 8-4-4-4-12.
-   Braces (`{}`) at the beginning and end of a string are optional. For example, both `"12345678-BBBb-cCCCC-0000-123456789012"` and `"{12345678-BBBb-cCCCC-0000-123456789012}"` are valid GUID strings.
-   It must have a total of either 36 or 38 characters, depending on whether or not braces are added.
-   The hexadecimal digits a-f (or A-F) can be uppercase, lowercase, or mixed.

The size of a GUID is 16 bytes or 128 bits. The six explicit [conversion](xpp-conversion-run-time-functions.md) functions for a GUID are `any2guid`, `guid2str`, `newGuid`, `str2guid`, `Global::guidFromString`, and `Global::stringFromGuid. `

### GUID Code Examples

The following X++ code examples illustrates how to use the GUID functions. The output of these examples is shown below.

        
    // An example of how to use the GUID functions.
    static void GuidRoundTripJob(Args _args)
    {
        guid guid2;
        str string3;
            
        // Convert a guid to a string, and back to a guid.
        guid2 = newGuid();
        info(strFmt("Info_a1:  guid2 == %1", guid2));
        string3 = guid2str(guid2);
        info(strFmt("Info_a2:  string3 == %1", string3));
        guid2 = str2guid(string3);
        info(strFmt("Info_a3:  guid2 == %1", guid2));
            
        // Test string representations of a guid. Mixing upper and lower case letters does not affect the guid.
        guid2 = str2guid("BB345678-abcd-ABCD-0000-bbbbffff9012");
        string3 = guid2str(guid2);
        info(strFmt("Info_b1:  8-4-4-4-12 format for dashes works (%1)", string3));
        info(strFmt("Info_b2:  Mixed upper and lower case works."));
            
        // Test invalid dash locations, see output is all zeros. Dash locations must be exact.
        guid2 = str2guid("CC2345678abcd-ABCD-0000-cccc9012");
        string3 = guid2str(guid2);
        info(strFmt("Info_c1:  These embedded dash locations are required.  %1", string3));
            
        // Braces {} are optional.
        guid2 = str2guid("{DD345678-abcd-ABCD-0000-ddddaaaa9012}");
        string3 = guid2str(guid2);
        info(strFmt("Info_d1:  Braces {} are optional (%1)", string3));
    }

### GUID Code Output

The output that is displayed in the Infolog is as follows. Note that Microsoft Dynamics AX includes the optional braces when it converts a GUID to a string.

    Message (02:26:46 pm)
    Info_a1:  guid2 == {93945629-734B-475E-99CE-6AA7AFA43259}
    Info_a2:  string3 == {93945629-734B-475E-99CE-6AA7AFA43259}
    Info_a3:  guid2 == {93945629-734B-475E-99CE-6AA7AFA43259}
    Info_b1:  8-4-4-4-12 format for dashes works ({BB345678-ABCD-ABCD-0000-BBBBFFFF9012})
    Info_b2:  Mixed upper and lower case works.
    Info_c1:  These embedded dash locations are required.  {00000000-0000-0000-0000-000000000000}
    Info_d1:  Braces {} are optional ({DD345678-ABCD-ABCD-0000-DDDDAAAA9012})

## Integers
**Integers** are numbers without decimals. X++ has two integer types: **int **and **int64**. Integers are used as control variables in repetitive statements or as indexes in arrays. You can also use integer literals anywhere an integer-expression is expected and both relational and arithmetic operators can be applied. An integer literal is the integer written directly in the code, for example, 32768. An int is 32 bits wide and an int64 is 64 bits wide. The default value is **0** and the internal representation is a long number. Integers are automatically converted into **boolean**, **enum**, and **real**. There are four explicit [conversion](xpp-conversion-run-time-functions.md) functions for integers: `str2int`, `int2str`, `str2int64`, and `int642str`. The range of an int is \[-2,147,483,647 : 2,147,483,647\]. The range of an int64 is \[-9,223,372,036,854,775,808 : 9,223,372,036,854,775,808\]. All integers in either of these ranges can be used as literals in X++.

### Integer Code Examples

Here is an example of declaring integers and using integers in expressions. If you try to assign the largest integer plus 1 to an int64, you will get the wrong result. This is because it is interpreted as a 32-bit number, and therefore the number is wrapped around and stored as -2,147,483,647 instead. To prevent this, add a "u" to the end of the number, for example: `int64 i = 0x8000 0000u` (0x8000 0000 is 2,147,483,648).

        
    public void IntegerMethod()
    {
        // Declaration of an integer variable, i.
        int i;
            
        // Declaration of two int64 variables.
        int64 i1, i2;
            
        // An integer variable is initialized to the value 100.
        int i3 = 100;
            
        // Declaration of a dynamic array of integers.
        int i4[];
        void element()
        {
            // Two integer variables are declared and initialized.
            int k = 1, j = 2;
                
            // j is assigned the result of j + ((i + i) DIV 2).
            j +=(i + i) div 2;
                
            // This results in: j=3.

            if (j > 2 )
            {
                print "J is greater than 2";
            }
            else
            {
                print "J is NOT greater than 2";
            }
        }
    }

## Reals
**Real** variables can hold decimal values in addition to holding integers. You can use decimal literals anywhere where a real is expected. A decimal literal is the decimal written directly in the code, for example, 2.123876. Real literals can also be written using exponential notation such as 1.0e3. Reals can be used in all expressions and with both relational operators and arithmetic operators. A real has a precision of 16 significant digits. The default for a real is **0.0**, and it's internal representation is as a BCD (binary-coded digital) number. The BCD encoding makes it possible to make exact representations of values that are multiples of 0.1. A real variable's range is -(10)¹²⁷ to (10)¹²⁷. All reals in this range can be used as literals in X++. Real variables are automatically converted to **boolean**, **enum**, or **int**. If the result is an integer or the operator is an integer-operator, reals **** are converted into integers. If the result is a Boolean, reals are converted to Booleans, and so on. You can also explicitly convert using `str2num` or `num2str`. Direct assignments between X++ `real` and .NET Framework `System.Decimal` convert the value correctly without the need to call any conversion function. The type used to represent real values has changed from interpreted X++. This won’t require you to rewrite any code, because the new type can express all of the values that the old one could. We provide this material in the interest of full disclosure only. All instances of the real type are now implemented as instances of the .NET decimal type (System.Decimal). Just as the real type in previous versions, the decimal type in a binary coded decimal type that, unlike floating point type, is resilient to rounding errors. The range and resolution of the decimal type are different from the original types. The original X++ real type supported 16 digits and an exponent that defined where the decimal point is placed. The new X++ real type can represent decimal numbers ranging from positive 79,228,162,514,264,337,593,543,950,335 (2⁹⁶-1) to negative 79,228,162,514,264,337,593,543,950,335 (-(2⁹⁶-1)). The new real type doesn’t eliminate the need for rounding. For example, the following code produces a result of 0.9999999999999999999999999999 instead of 1. A decimal number is a floating-point value that consists of a sign, a numeric value where each digit in the value ranges from 0 to 9, and a scaling factor that indicates the position of a floating decimal point that separates the integral and fractional parts of the numeric value. The binary representation of a real value consists of a 1-bit sign, a 96-bit integer number, and a scaling factor used to divide the 96-bit integer and specify what portion of it is a decimal fraction. The scaling factor is implicitly the number 10, raised to an exponent ranging from 0 to 28. Therefore, the binary representation of a decimal value represents ((-2⁹⁶ to 2⁹⁶)/10(0\\ to\\ 28)), where -(2⁹⁶-1) is equal to the minimum value and 2⁹⁶-1 is equal to the maximum value that can be expressed.

### Real Code Examples

        
    public void RealMethod()
    {
        // Simple declaration of a real variable, r.
        real r;
            
        // Multiple declaration of two real variables.
        real r1, r2;
          
        // A real variable is initialized to the approximate value of pi.
        real r3 = 3.1415;
            
        // Declaration of a dynamic array of reals.
        real r4[];
            
        // An example of a real literal written using exponential notation.
        real r;
        r = 1.000e3;
        r = 1.2345e+3;
        r = 1.2345e+03;
        r = 1234.5e4;
        r = 1.0e1; // Means 1.0E1 
    }
            
    // An example of automatic conversions.
    void main()
    {
        // Declares a variable of type integer with the name exprValue.
        int exprValue;
            
        // Declares a real variable with the name area.
        real area = 3.141528;
        exprValue = Area/3;
                
        // The expression Area/3 is a real expression because
        // division is a real operator, and the result is 1.047176. This result is
        // automatically converted (actually truncated) to an integer with the value 1,
        // because exprValue is an integer.
    }
            
    // An example of a real being converted to .NET System.Decimal.
    void AnotherMain(Args _args)
    {
        real real9;
        System.Decimal sysdec1;
                
        // Direct assignments supported between these types.
        sysdec1 = 2.3456;
        real9 = sysdec1;
        info(strFmt("strFmt says real9 == %1", real9));
    }
            
    /***
    Message (05:48:43 pm)
    strFmt says real9 == 2.35
    ***/
            
    // An example of using reals in expressions.
    void myMethod()
    {
        // Two real variables are declared and initialized.
        real i = 2.5, j = 2.5;
            
        // j is assigned the result of j * i, so j=6.25.
        j = j * i;
        if (j > (i * 2)) // If j > 5 
        {
            print "Great"; // "Great" is printed.
        }
        else
        {
           print "Oops"; // else "Oops" is printed.
        }
    }
            
    // An example of using the debugger to show the value of the variables.
    public static void UseTheDebugger(Args a)
    {
        real dividend = 1.0;
        real divisor = 3.0;
        str stringvalue;
        System.Decimal valueAsDecimal;
        real value = dividend/divisor * divisor; 
        valueAsDecimal = value;
        info(valueAsDecimal.ToString("G28"));
        // An example of using the Round function to round to the number of decimals required.
        value  = round(value, 2);
    }

## Strings
**Strings** are sequences of characters that are used as texts, help lines, addresses, telephone numbers, and so on. To declare a string in X++, use the `str` keyword. String literals are characters that are enclosed in quotation marks (" ") that can be used where string expressions are expected. Some examples of this would be "StringLit" and "Hello World". If you want the string to span more than one line, precede it with an "@" character. You can use strings in logical expressions, such as comparisons. You can also concatenate strings by using the + operator. The default value for a string is **empty **and the internal representation is that of a list of characters. There are no automatic conversions for strings but there are several explicit [conversion](xpp-conversion-run-time-functions.md) functions: `str2int`, `str2int64`, `int2str`, `str2num`, `num2str`, `str2date`, and `date2str`. A string can hold an unlimited number of characters. You can specify the maximum length of characters within a string in the variable declaration and force a truncation  to the maximum length of the string. An example is shown in the next section.

### String Code Examples

        
    void StringMethod()
    {
        // Declare a dynamic string of unlimited length.
        str unlimitedString;
            
        // Declare a string with a maximum of 64 characters
        // in order to force a truncation, initialized to "A".
        str 64 maxLengthString = "A";
            
        // Declare an array of 100 strings.
       str 30 hundredStrings[100];
            
        // Using strings in expressions.
        void myMethod()
        {
            // Two strings are declared and initialized.
            str a="Hello", b="World";
                
            // The concatenation of a, " " and b is printed in a window.
            print a+" "+b;
        }
    }

## TimeOfDay
The **timeOfDay** (or time data type) is an integer value representing the number of seconds that have elapsed since midnight. TimeOfDay variables can be used as literals in the same way as integers are used as literals. TimeOfDay variables can have relational operators and arithmetic operators applied to them. They can also be used in expressions. The range of a timeOfDay data type is in the closed interval \[0; 86400\]. Values above 86400 (23:59:59) cannot be interpreted. TimeOfDay variables are automatically converted into **boolean**, **enum**, and **real**. Use the `str2time` and `time2str` conversion functions to explicitly convert timeOfDay.

### TimeOfDay Code Examples

        
    public void TimeofdayMethod()
    {
        // Declaration of a timeOfDay variable, time1.
        timeOfDay time1;
            
        // Declaration and initialization of a timeOfDay variable to 00:21:35.
        timeOfDay time2 = 1295;
    }

## utcdatetime
The **utcdatetime** data type combines the **date** type and the **timeOfDay** type into one type. A utcdatetime variable also holds time zone information, though this information is not accessible to X++ code. The format for a utcdatetime literal is `yyyy-mm-ddThh:mm:ss`, with the uppercase "T" being a required literal character. This format can be written without quotes. The minimum value is `1900-01-01T00:00:00` and the maximum value is `1900-01-01T00:00:00`. This matches the upper range of `date` and `timeOfDay`. The smallest unit of time in utcdatetime is **1 second**. A utcdatetime variable that has been declared but not initialized has the default value of `1900-01-01T00:00:00`. This is the value returned by `DateTimeUtil::minValue()`. Some functions treat an input parameter of this minimum value as null. For instance, the `DateTimeUtil::toStr` method returns an empty string, however, the `DateTimeUtil::addSeconds` method returns a usable utcdatetime value. There are no implicit conversion for the utcdatetime data type. The `DateTimeUtil` class provides many methods for manipulating utcdatetime values. The explicit [conversion](xpp-conversion-run-time-functions.md) functions for utcdatetime are `str2datetime` and `datetime2str`. Also, the `Global` class provides the conversion methods `utcDateTime2SystemDateTime` and `CLRSystemDateTime2UtcDateTime` to support common language runtime (CLR) interop. Comparison operators are the only kind of operators that can be used with the `utcdatetime` data type. The following operators can be used to compare two utcdatetime values: !=, &lt;, &lt;=, == , &gt;, and &gt;=. When you add a utcdatetime field to a table, we recommend that you base the field on an extended data type (EDT).

### utcdatetime Code Examples

        
    public void UtcdatetimeMethod()
    {
        // Declaring a utcdatetime literal.
        utcdatetime myUtc2 = 1988-07-20T13:34:45;
            
        // Another example of declaring a utcdatetime literal.
        int iDay = DateTimeUtil::day(1988-07-20T13:34:45);
            
        // utcdatetime using a quoted string parameter into the DateTimeUtil::parse method.
        utcdatetime myUtc4 = DateTimeUtil::parse("1988-07-20T13:34:45");
    }

## Composite Data Types
The composite data types in X++ are arrays, containers, classes as data types, delegates as data types, and tables as data types.

## Array
An **array** is a variable that contains a list of items that all have the same data type. The elements of an array are accessed with integer indexes. You use a separate statement to initialize each element in an array. When you use a **Container** data type or an **Array** object to create a collection, you can initialize multiple elements by using a single statement. When declaring an array, if a `Length` is specified, the array is a **fixed-length array** with `Length` elements. Otherwise, it is a **dynamic array**. If `Memory` is specified, it is a **partly on disk array**. By default, all the items in an array have the default value of the data type in the array. The three kinds of arrays are **dynamic arrays**, **fixed-length arrays**, and **partly on disk arrays**.

-   A **dynamic array** is declared with an empty array option (that is, only square brackets).
-   A **fixed-length array** can hold the number of items that is specified in the declaration. Fixed-length arrays are declared like dynamic arrays but with a length option in the square brackets.
-   **Partly on disk arrays** are declared either as dynamic or fixed-length arrays with an extra option that declares how many items should be held in memory. The other items are stored on disk and automatically loaded when referenced.

X++ only supports one-dimensional arrays. It is possible, however, to mimic the behavior of multiple array indices (see the next section on multiple array indices). Variables in objects and tables can be declared as arrays. For example, this is used in address lines in the standard application. An Array collection class enables you to store objects in an array. Array indices begin at 1. The first item in the array is referenced with \[1\], the second \[2\], and so on. The syntax for accessing an array element is `ArrayItemReference = ArrayVariable [ Index ] `where `ArrayVariable` is the identifier of the array, and `Index` is the number of the array element. `Index` can be an integer expression. Item zero\[0\] is used to clear the array. Assigning a value to index 0 in an array resets all elements in the array to the default value.

### Array Code Examples

        
    public void ArrayMethod()
    {
        int myArray[10]; // Fixed-length array with 10 integers.
        myArray[4] = 1; // Accessing the 4th element in the array.
        myArray[0] = 0; // Resets all elements in intArray. 
     
        // Dynamic array of integers.
        int intArray[];
            
        // Dynamic array of variables of type Datatype.
        //Datatype arrayVariable[];
            
        // Fixed-length arrays.
        boolean boolArray[100]; // Fixed-length array of booleans with 100 items.
            
        // Two examples of Partly On Disk Arrays.
        // Dynamic integer array with only 100 elements in memory.
        int arrayVariable [ ,100];
        // Fixed-length string array with 1000 elements, and only 200 in memory.
        str arrayVariable2 [1000,200];

            // A dynamic array of integers.
            int i[];
            // A fixed-length real array with 100 elements.
            real r[100];
            // A dynamic array of dates with only 10 elements in memory.
            date d[,10];
            // A fixed length array of NoYes variables with 100 elements and 10 in memory.
            NoYes ny[100,10];
    }

### Multiple Array Indices

Some languages, such as C++ and C\#, allow you to declare arrays with more than one index; that is, to define "arrays of arrays." You cannot directly create multiple array indexes in X++ - only one-dimensional arrays are supported. However, you can implement multiple indexes by using the following scheme. For example, in C++ and C\#, if you wanted to declare an array with two dimensions for holding an amount earned by country by dimension, and there were 10 countries and 3 dimensions, you would declare the following: `real earning[10, 3];` This is not possible in X++. Instead, you can define a one-dimensional array with the number of elements that is the product of the elements in each dimension. An example of this is shown below.

    public void MultipleArrayMethod()
    {
        // Step 1: define a one-dimensional array with the number
        // of elements that is the product of the elements in each dimension.
        real earnings[10*3];
            
        // Step 2: to refer to a specific element, such as earnings[i,j], write the following:
        // declare i and j (maybe) and assign the value to something
        int i = 1;
        int j = 2;
        real element = earnings[(i-1)*3 + j];
    }

    // This can be written into a macro like this:
    #localmacro.earningIndex
    (%1-1)*3+%2
    #endmacro

    public void CallTheMacro()
    {
        // Next, call the specific element within the macro like this:
        int i = 1;
        int j = 2;
        real element = earnings[#earningIndex(i,j)];

        // The previous scheme can be extended to any number of dimensions.
        // The element a[i1, i2, ..., ik] can be accessed by computing the
        // offset into an array containing (d1*d2*...*dk) elements.
        //(i1 - 1)*d2*d3*..*dk +
        //(i2 - 1)*d3*d4*...*dk + .... +
        //(ik-1 -1)*dk +
        //(ik-1)
    }

## Containers
A **container** is a dynamic list of items containing primitive data types or composite data types. A container is helpful when you must pass a variety of value types between the client and server tiers. A container is a poor choice when you intend to repeatedly add to a list in a loop because a container is best suited for processes that do not involve excessive modification to the size or contents of the container. When a container undergoes excessive additions of data, overall system performance can be decreased by the need to repeatedly copy container data and allocate new space. A container is not a class. A container contains an ordered sequence of primitive values or other containers. The flexibility of `anytype` makes container a good way to store values of different types together. A container can be stored in the database. A container is one of the column types that you can select when you use the Application Explorer to add a column to a table. A container slightly resembles an array, or collections such as the `List` or `Stack` classes. However, you can never change the size or content of a container after the container is created. X++ statements that appear to modify a container are internally building a new container and copying values as necessary. Even an assignment of a container to another container variable creates a new copy of the container. All of this has performance implications. In the X++ functions that provide access to a container (such as `conPeek`), the container is 1 based not 0 based. Indexing is 1-based for arrays. The default value of a container is **empty**. The container does not contain any values. Some X++ statements with containers might appear like they modify a container, but inside the system this never occurs. Instead, the data from the original container is combined with data from the command to build a new container. You can create a new container by using one of these functions: `conDel`, `conIns`, or `conPoke`. The Global Class has static methods for handling containers. These methods include `con2ArraySource`, `con2Buf`, `con2List`, `con2Str`, `containerFromXmlNode`, `conView`, and `str2Con`. There are several intrinsic X++ functions for handling a container, such as `conIns` and `conPeek`. The X++ function `conPeek` returns an `anytype` type. This makes it easier to read the values from a container when you do not know what type each value is. An `anytype` can be assigned to any X++ value type, as long as the value can be converted. Your code is easier to read when it avoids explicit data type conversions. Assign values from a container to the same data type that was used to put the value into the container. You must not assign a container to an `anytype`, because the system is unable to determine the correct conversions in some cases. In these cases, unexpected behavior or errors might occur.

### Comparing container to other options

The container type resembles other constructs, such as arrays and collection classes like `List` and `Stack`. The difference between a container and a List is that an instance of the List class is mutable. A `List` object first allocates more space than its data consumes. As data is added the space is filled. This is more efficient than allocating more space every time that an element is added. Updating a `List` performs faster than similar operations on a container. When you construct a `List` object, you determine the one type of data that the `List` object can store. This restriction is less flexible than for a container. However, you can choose to store objects in a `List`, whereas a container can only store value types. The difference between a container and an array is that an array can hold only items of its declared type. You can allocate memory space for an array and fill that space with values later, such as in a loop. This is efficient and performs well. When you want to build a new container by appending new data, you can use either the **+=** operator or the `conIns` function. The **+=** operator is the faster alternative. Use the `conIns` function only when you want to add new data before the last index of the original data. In previous incarnations of the X++ compiler, it was possible to store object references into containers, even though this would fail at runtime. This is no longer possible. When the compiler sees an attempt to store an object reference into a container, it will issue an error message. If the type of the element that is added to the container is anytype the compiler can’t make the determination of whether or not the value is a reference type. The compiler will allow this under the assumption that the user knows what they’re doing. The compiler won't diagnose the code as erroneous but an error will be thrown at runtime.

### Container Code Examples

    public void ContainerExample() 
    {
        // First, declare the variables you are using.  
        container myContainer;
        container myContainer4;
        container myContainer5; 
        // Three ways to declare a container.
        myContainer = [1];
        myContainer += [2];
        myContainer4 = myContainer5;
            
        // Declare a container.
        container cr3;
            
        // Assign a literal container to a container variable.
        cr3 = [22, "blue"];
            
        // Declare and assign a container.
        container cr2 = [1, "blue", true];
            
        // Mimic container modification (implicitly creates a copy).
        cr3 += [16, strMyColorString];
        cr3 = conIns(cr3, 1, 3.14);
        cr3 = conPoke(cr3, 2, "violet");
            
        // Assignment of a container (implicitly creates a copy).
        cr2 = cr3;
            
        // Read a value from the container.
        str  myStr = conPeek(cr2, 1);
            
        // One statement that does multiple assignments from a container.
        str myStr;
        int myInt;
        container cr4 = ["Hello", 22, 20\07\1988];
        [myStr, myInt] = cr4; // "Hello", 22
            
        // Example of applying the = operator to a container. The example
        // initializes myContainer2 and myContainer33.
        myContainer2 = [2, "apple"];
            
        // Next, you make a copy of myContainer33 and assign the copy to myContainer2.
        myContainer33 = [33, "grape"];
        myContainer2 = myContainer33;  // The container that myContainer2 had been holding is no longer available and cannot be recovered.
        // An example of building a new container by
        // assigning a new value to myContainer33 through the += operator.
        myContainer33 += [34, "banana"];
    }

    // List class example. In this example, variable2 and variable3 refer to the same List object.
    static void JobC(Args _args)
    {
        container variable2, variable33;
        variable2 += [98];
        variable33 = variable2;
        variable2 += [97];
    }

    // Container example. The variable2 and variable3 hold different containers.
    static void JobL(Args _args)
    {
        List variable2,variable33;
        variable2 = new List(Types::Integer);
        variable2.addEnd(98);
        variable33 = variable2;
        variable2.addEnd(97);
    }

    // The automatic type conversion by anytype also applies to the special syntax for making multiple
    // assignments from a container in one statement. This is shown in the following code example,
    // which assigns a str to an int, and an int to a str.
    static void JobContainerMultiAssignmentUsesAnytype(Args _args)
    {
        container con2;
        int int4;
        str str7;
        con2 = ["11", 222];
        [int4, str7] = con2;
        info(strfmt("int4==11==(%1), str7==222==(%2)", int4, str7));
    }
    /***  Output:
    Message (10:36:22 am)
    int4==11==(11), str7==222==(222)
    ***/
        
    static void UseQuery()
    {
        // An example of how the compiler diagnoses attempts to store object in containers
        container c = [new Query()];   // This statement will cause the error message shown below.
        /*** Instance of type 'Query' cannot be added to a container. ***/
            
        // An example of a code that won't cause an error message, but will
        // cause an error message to be thrown at runtime.
        anytype a = new Query();
        container d = [a];
    }

## Classes as Data Types
A **class** is a type definition that describes both variables and methods for instances (objects) of the class. A class is only a definition for objects, and all objects are **null** when they are declared. Every application class in the Application Explorer under the **Classes** node is a data type in X++. You can declare variables of these types in your code. You can construct instances of a class and assign the instances to variables. The instances are also known as objects. Classes can now be nested in source code. Nested classes are available only inside forms (such as a class that extends FormRun) to represent controls, data sources, or data fields. An attribute decoration, such as on a class or a method, can now omit the suffix of the attribute name if the suffix is `Attribute`. So X++ allows `[MyFavorite]` instead of requiring `[MyFavoriteAttribute]`. Also, attributes are now applied to the handlers of delegates and methods, to map the handlers to those targets. In legacy X++, it was possible to designate a method to run either on the client or the server. This is no longer possible. All compiled X++ code is executed as .NET CIL on the server. There is no longer any code that is evaluated at the client site or in the browser, therefore, the two keywords, *client* and *server*, are now ignored. Their use doesn’t cause a compile error, but they should not be used in any new code.

### Private and Protected  Member Variables

Previously, all member variables defined in a class were invariably protected. It’s now possible to make the visibility of member variables explicit by adding the private, protected, and public keywords. The interpretation of these modifiers is obvious and aligns with the semantics for methods:

-   A private member can only be used within the class where it’s defined.
-   a protected member can be used in the class where it’s defined, and all subclasses thereof.
-   A public member can be used anywhere: it’s visible outside the confines of the class hierarchy in which it’s defined.

The default for member variables that aren’t adorned with an explicit modifier is still protected. You should make it a habit of explicitly specifying the visibility. As described, when a member variable is defined as public, it may be consumed outside of the class in which it’s defined. In this case, a qualifier designating the object hosting the variable has to be specified, using the dot notation (as is the case for method calls). Reusing the code from above:

    public class AnotherClass3
    {
        int field1;
        str field2;
        void new()
        {
            this.field1 = 1;   // Explicit object designated.
            field2 = "Banana";  // 'this' assumed, as usual.
        }
    }

In this case, field1 is accessed using the explicit ‘this.’ qualifier. Making a member variable public may not be a good idea since it exposes the internal workings of the class to its consumers, creating a strong dependency between the class implementation and its consumers. You should always strive to only depend on a contract, not an implementation.

### Static Constructors and Static Fields

Static constructors and static fields are new features in the X++ language. Static constructors are guaranteed to run before any static or instance calls are made to the class. The execution of the static constructor is relative to the user’s session. You’ll never call the static constructor explicitly; the compiler will generate code to ensure that the constructor is called exactly once prior to any other method on the class. A static constructor is used to initialize any static data, or to perform a particular action that needs to be performed only once. No parameters can be provided for the static constructor, and it must be marked as static. Static fields are fields that are declared using the static keyword. Conceptually they apply to the class, not instances of the class.

    // An example of how a singleton (call instance in the example below)
    // can be created using the static constructor.
    public class Singleton
    {
        private static Singleton instance;

        private void new()
        {
        }

        static void TypeNew()    // This is the static constructor.
        {
            instance = new Singleton();
        }

        public static Singleton Instance()
        {
            return Singleton::instance;
        }
    }
     
    // The singleton ensures that only one instance of the class
    // will be called, which is consumed by the following. 
    {
        // Your code here.
        Singleton i = Singleton::Instance();
    }

### Class Elements in the Application Explorer

Under most **class** nodes there are two special nodes: a **classDeclaration** node and a **new** node. A **classDeclaration** contains the X++ `class` keyword. It can also have additional keywords such as `extends` to modify the class. This node can also contain declarations of member variables. The member variables cannot be initialized to a value in `classDeclaration`. The member variables cannot be `static`. In the following example the variables `m_priority` and `m_rectangle` are members of the class:

    // An example of a classDeclaration.
    public class YourDerivedClass extends YourBaseClass
    {
        int m_priority;
        Rectangle m_rectangle;
        void new(int _length, int _width)
        {
            this.m_rectangle = new Rectangle(_length, _width);
        }
    }

A **new** operator contains X++ logic that is run when the `new` operator is used to create an instance of the class. The logic in the `new` method might construct an object, and assign the object to a variable that is declared in the `classDeclaration`. Each class is limited to only one `new` method. However, in the `new` method you often should call the `new` method of the base class, and you do so by calling `super()`. The following example is the `new` method for the `YourDerivedClass` class in the previous `classDeclaration` example. In this `new` method, the X++ code constructs an instance of the Rectangle class. The instance is assigned to the `m_rectangle` variable. The `this` keyword that is used in the example below is optional, although in practice it sometimes enables IntelliSense to be more helpful.

    // An example of the new method from the previous classDeclaration example.
    void new(int _length, int _width)
    {
        this.m_rectangle = new Rectangle(_length, _width);
    }

### Garbage Collection

During run time, most objects eventually no longer have any variable pointing to them. The system scans for such objects and erases them from memory. This makes the memory space available for other uses. The `Object` class has a method named `finalize`. However, the `finalize` method is not a destructor. The Microsoft Dynamics AX system never calls the `finalize` method, even when an object is garbage collected.

### System Classes

In the Application Explorer under **System Documentation** &gt; **Classes** you can see a list of the kernel or system classes. System classes are not written in X++, and you cannot see their source code. You cannot add any system classes. System classes usually have a `new` method, but they do not have a `classDeclaration` node. Every application class implicitly extends the `Object` system class. Some system classes are extended by an application class of nearly the same name. For instance, `xClassFactory` is extended by `ClassFactory`. In such cases you should not use the system class. For more information, see Substitute Application Classes for System Classes.

### Extension Methods

The extension method feature lets you add extension methods to a target class by writing the methods in a separate extension class. The following rules apply:

-   The extension class must be static.
-   The name of the extension class must end with the ten-character suffix \_Extension. However, there’s no restriction on the part of the name that precedes the suffix.
-   Every extension method in the extension class must be declared as public static.
-   The first parameter in every extension method is the type that the extension method extends. However, when the extension method is called, the caller must not pass in anything for the first parameter. Instead, the system automatically passes in the required object for the first parameter.

It’s perfectly valid to have private or protected static methods in an extension class. These are typically used for implementation details and are not exposed as extensions. The extension method technique doesn’t affect the source code of the class it extends. Therefore, the addition to the class can be done without over-layering. Upgrades to the target class are never affected by any existing extension methods. However, if an upgrade to the target class adds a method that has the same name as your extension method, your extension method becomes unreachable through objects of the target class. Extension methods are easy to use. The extension method technique uses the same dot-delimited syntax that you routinely use the call regular instance methods. Extension methods can access all public artifacts of the target class, but they can’t access things that are protected or private. In this way, extension methods can be seen as a kind of syntactic sugar. The target of an extension method must be a class, table, view, or map application object type. Regardless of the target type, an extension **class** is used to add extension methods to the type. For example, an extension table is **not** used to add methods to a table, and there’s no such thing as an extension table.

    // An example of an extension class holding a few extension methods.
    public static class AtlInventLocation_Extension
    {
        public static InventLocation refillEnabled(
           InventLocation _warehouse,
           boolean _isRefillEnabled = true)
        {
           _warehouse.ReqRefill = _isRefillEnabled;
           return _warehouse;
        }

        public static InventLocation save(InventLocation _warehouse)
        {
           _warehouse.write();
           return _warehouse;
        }
    }

## Delegates as Data Types
A **delegate** collects methods that subscribe to it. The delegate specifies the parameter signature that all its subscriber methods must share. When the delegate is called, the delegate calls each of its subscriber. A delegate never returns a value and is **unable to have a default value**. However, each delegate starts with zero methods subscribed to it. There is no limitation on the number of parameters a delegate can declare and there is no limitation on the type of those parameters. The delegate body is always empty because the delegate's only purpose is to define the contract that subscribers must conform to. A delegate can now be defined in a table, form, or query, and not just in a class.

### Delegates Code Examples

    abstract class VarDatClass
    {
        // delegatemethod examples
        // An example of declaring a delegate.
        delegate void notifyChange(utcdatetime _dateTime, str _changeDescription)
        {
        }

        // An example of subscribing an event handler to a delegate.
        public static void notifyStatic(utcDateTime _dateTime, str _changeDescription)
        {
            info("A notification has occured calling static handler:" +
                                        DateTimeUtil::toStr(_dateTime) +
                                        " Message:" +
                                        _changeDescription);
        }
    }

## Tables as Data Types
All **tables** can be treated like class definitions (at least in all practical aspects) in the X++ programming language. A table variable can be seen as an instance (an object) of the table (class) definition. For every field in a table variable, the default value is **empty**. You can address fields and create methods on tables. The methods can be invoked on instances of the table. To manipulate (read, update, insert, and delete) records in tables, you must declare at least one table variable, which can hold the record in focus. The best practice to use the name of the table as the name of the variable, but with an initial lowercase letter. Here are a few important differences between tables and objects:

-   You cannot allocate space for table variables—it is done implicitly.
-   Fields in table variables are public—you can reference them anywhere.
-   Fields in table variables can be referenced with expressions.

There is no automatic conversion, but table variables that are declared as `Common` can hold data from any table.

### Scope of Table Variables

In most respects, table variables can be considered objects. Contrary to objects, they are not allocated explicitly. Only a variable declaration is required. All tables are compatible with the `Common` table in the same way that all objects are compatible with the `Object` class. Table variables, which are declared as common buffers, can be used to hold data from any table. You cannot access tables without table variables. The principles for declaring table variables and objects are the same except for the allocation of space.

### Table Code Examples

        
    // Declares and allocates space for one CustTable record.
    public void myMethod()
    {
        CustomerTable custTable;
    }

    // An example of referencing table variables.
    public void printAccountNo()
    {
        CustomerTable custTable;
        print custTable.AccountNo;  // Prints the field reference.
    }

The syntax, however, also allows various possibilities for referencing fields in records, for example by using the `TableName.(FieldId)` syntax. The following example prints the contents of the fields in the current record in the Customer table. Note: the following example uses the `fieldCnt` and `fieldCnt2Id` methods. The `fieldCnt` method counts the number of fields in a table, while `fieldCnt2Id` returns the ID for a field number. For example, you can use the `fieldCnt2Id` method to find out that field number 6 in a table has the ID 54. It is necessary to perform this conversion because it is not guaranteed that the IDs of the fields in a table are consecutive.

        
    // An example of the various possibilities for referencing fields in records.
    public void printCust()
    {
        int i, n, k;
        CustomerTable custTable;
        DictTable dictTable;
        dictTable = new DictTable(custTable.TableId);
        n = dictTable.fieldCnt();
        print "Number of fields in table: ", n;
        for(i=1; i<=n; i++)
        {
            k = dictTable.fieldCnt2Id(i);
            print "The ", dictTable.fieldName(k),
            " field with Id=",k, " contains '",
            custTable.(k), "'";
        }
    }

## Collection Classes
The X++ language syntax provides two composite types: arrays and containers. They are useful for aggregating values of primitive types. However, you cannot store class objects in arrays or containers. **Collection classes** are for storing objects by allowing you to create arrays, lists, sets, maps, and structs that can hold any data type, including objects. The classes are implemented in C++ to achieve the maximum performance (they are system classes). Collection classes were formerly called Foundation classes.

### Collection Classes

The collection classes consist of **arrays**, **lists**, **maps**, **sets**, and **structs**.

-   An **array** is similar to the X++ language array type except that it can hold values of any single type, including objects and records. Objects are accessed in a specific order.
-   A **list** contains elements that are accessed sequentially. Unlike the `Array` class, the `List` class provides an `addStart` method. As with the `Set` class, the `List` class provides methods `getEnumerator` and `getIterator`. You can use an iterator to insert and delete items from a `List` object.
-   A **map** associates a key value with another value.
-   A **set** holds values of any single type. Values are not stored in the sequence they are added. Instead, the `Set` object stores them in a manner that optimizes performance for the `in` method. When you add a value to a `Set` object which is already storing that same value, the add attempt is ignored by the `Set` object. Unlike the `Array` class, the `Set` class provides the methods `in` and `remove`.
-   A **struct** can contain values of more than one type. Used to group information about a specific entity.

### Types Stored in Collections

The constructor for each collection class, except `Struct`, takes in a type parameter that is an element of the `Types` system enum. The collection instance can store items of that type only. The `Types::AnyType` enum element is a special case and it cannot be used to construct a collection object, such as a `Set` object. The `null` value cannot be stored as an element in a `Set` object. And `null` cannot be a key in a `Map` object.

### Elements Cannot Be Changed During Iteration

You can iterate through an X++ collection object with an iterator or enumerator. Here are typical examples of how you can obtain an iterator:

-   `new MapIterator(myMap)`
-   `myMap.getEnumerator()`

For`Set` objects, if any elements are added or removed after an iterator is created, the iterator instance can no longer be used to read from or step through the collection. For `Map` objects, element removals invalidate the iterator just as for `Set` objects. However, a `MapIterator` object remains valid even after a call to the `Map.insert` method. This is true whether the key is new, or whether the key already exists and only the value is actually being updated in the `Map` element. X++ code that calls `Map.insert` and relies on the iterator object remaining valid might fail if run as .NET Framework CIL.

### Extend a Collection Class

You can use the collection classes to form more complex classes. For example, a stack might easily be implemented by using a list where the elements are always added to the start of the list. The newest element then occupies the top of the stack. You can also extend the collection classes. For example, you might extend the `List` class to create a list of customer records where the operations could be made type safe. The derived collection class would accept only customer records, not just any record.

## Extended Data Types (EDTs)
**Extended data types (EDTs)** are user-defined types, based on the primitive data types `boolean`, `integer`, `real`, `string`, and `date`, and the composite type `container`. An EDT is a primitive data type or container with a supplementary name and some additional properties. For example, you could create a new EDT called `Name` and base it on a `string`. Thereafter you can use the new EDT in variable and field declarations in the development environment. You can also base EDTs on other EDTs. EDTs are standard data types, but with a specific name and additional properties. EDTs undergo the same value and type [conversions](xpp-conversion-run-time-functions.md) as do the standard data types they are based on. The benefits of EDTs are:

-   Code is easier to read because variables have a meaningful data type. For example, `Name` instead of `string`.
-   The properties you set for an EDT are used by all instances of that type, which reduces work and promotes consistency. For example, account numbers (`AccountNum` data type) have the same properties throughout the system.
-   You can create hierarchies of EDTs, inheriting the properties that are appropriate from the parent and changing the other properties. For example, the`ItemCode` data type is used as the basis for the`MarkupItemCode` and `PriceDiscItemCode` data types.

### Create an extended data type

This feature is not implemented as a language construct. To create an EDT:

1.  In **Solution Explorer,** right-click on the project, select **Add** and then **New item.**
2.  In the **Add New Item** dialog, select Installed and then **AX Artifacts** in the left pane.
3.  In the middle pane, select the EDT type you want to create.
4.  Enter a name and click **Add.**

### EDT Code Example

        
    public void EdtMethod()
    {
        // Example of declaring EDT variables where
        // a UserGroupID (integer) variable is declared and initialized to 1.
        UserGroupID groupID = 1;
            
        // An Amount (real) variable is declared.
        Amount currency;
    }

## Null Values for Data Types
Microsoft Dynamics AX does not support the concept of **null** values that is available in many other Database Management Systems (DBMS). A variable in X++ always has a type and a value. For each data type, however, one value is considered null (for example, when the `validateField` table method is executed).

| Type        | Value treated as null                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|-------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Date        | 1900-01-01                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Enum        | Element with its value set to 0.                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Integer     | 0                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Real        | 0.0                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| String      | An empty string                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| Time        | 00:00:00                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| Utcdatetime | Any value with its date portion as 1900-01-01 is treated as **null**, regardless of the time portion value. Therefore the value 1900-01-01T22:33:44 is treated as `null`. Note that any **utcDateTime** value with its date portion as 1900-01-01 is displayed as blank by the X++ **print** statement. Only the value 1900-01-01T00:00:00 is displayed as blank by the `Global::info` method. That is the value from the `DateTimeUtil::MinValue` method. |

As a result, when the `validateField` method checks whether a user has entered a value in a mandatory field, 0 is not accepted in an integer type field, the first entry is not accepted in an enum type field, and so on. Also, the values that are listed in the previous table yield **false** in a Boolean comparison, in X++ SQL. In non-SQL X++ statements, the equal and relational operators work with these values the same normal way that they work with other values. Variables of type container, and classes and variables of table type can be null in the traditional database management system (DBMS) sense. A table type is **null** if all its fields have their null value.

