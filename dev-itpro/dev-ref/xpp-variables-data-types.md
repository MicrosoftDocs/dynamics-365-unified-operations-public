---
# required metadata

title: X++ variables and data types
description: This topic describes variables and data types in X++.
author: RobinARH
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
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
ms.assetid: 0ff4e759-851d-4b53-aa67-6f03eee53f02
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# X++ variables and data types

This topic describes variables and data types in X++.

Variables
---------

A *variable* is an identifier that points to a memory location where information of a specific data type is stored. The size, precision, default value, implicit and explicit [conversion](xpp-conversion-run-time-functions.md) functions, and range depend on the variable's data type. The *scope* of a variable defines the area in the code where an item can be accessed. *Instance variables* are declared in class declarations, and can be accessed from any methods in the class or from methods that extend the class. *Local variables* can be accessed only in the block where they were defined. When a variable is declared, memory is allocated, and the variable is initialized to the default value. You can assign values to both static fields and instance fields as part of the declaration statement. Variables can be declared anywhere in a code block in a method. They don't have to be declared at the beginning of a method. *Constants* are variables where the value can't be changed when the variable is declared. They use the **const** or **readonly** keyword. Constants differ from *read-only fields* in only one way. Read-only fields can be assigned a value only one time, and that value never changes. The field can be assigned its value either inline, at the place where the field is declared, or in the constructor. When you declare variables of managed types that aren't authored in X++, you have two options. You can fully qualify the type names in the declaration by including the full namespace, or you can add a **using** statement to your file and then omit the namespace from the type name.

### Variable examples

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
    class ScopeExample
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
    public class FieldAssignmentExample
    {
        int field1 = 1;
        str field2 = "Banana";
        void new()
        {
            // ...
        }
    }
     
    class ConstantExample
    {
        // An example of a constant being declared at the class level.
        public const str MyContent = 'SomeValue';
        public int ResultSoFar()
        {
            return 1;
        }
    }

    // The constants can then be referenced by using the double-colon syntax.
    str value = ConstantExample::MyContent;
    // If you're in the scope of the class where the const is defined, 
    // you can omit the type name prefix (ConstantExample in this example).
     
    // An example of the using clause where the alias can denote
    // namespaces and classes.
    using System;
    using IONS=System.IO; // Namespace alias.
    using Alist=System.Collections.ArrayList; // Class alias.
    public class NamespaceExample
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

### var

You can declare a variable without explicitly providing the type of the variable, if the compiler can determine the type from the initialization expression. The variable is still strongly-typed into one, unambiguous type. You can use **var** only on declarations where initialization expressions are provided. (The compiler will infer the type from the initialization expression.) In some cases, this approach can make code easier to read. You should use **var** to declare local variables in these situations:

-   When the type of the variable is obvious from the right side of the assignment
-   When the exact type isn't important
-   For the declarations of **for** loop counters
-   For disposable objects inside **using** statements

Don't use **var** when the type isn't clear from the initialization expression.

### var examples

    // When the type of a variable is clear from
    // the context, use var in the declaration.
    var var1 = "This is clearly a string.";
    var var2 = 27; // This is an integer (not a real).
    var i = System.Convert::ToInt32(3.4);
            
    // Don't use var when the type of the variable is not clear
    // from the context. Use an explicit type instead.
    int var4 = myObject.ResultSoFar();

### Declare anywhere

Declarations can now be provided wherever statements can be provided. A declaration is syntactically a statement, a *declaration statement*. You can provide declarations immediately before the variable is used, and you don’t have to declare all the variables in one place. Therefore, you have precise control over the scope of your variables. You can give variables smaller scopes, outside which the variables can’t be referenced. The lifetime of the variable is the scope that it’s declared in. Scopes can be started at the block level (inside compound statements), in **for** statements, and in **using** statements. There are several advantages to making scopes small:

-   Readability is enhanced.
-   You reduce the risk that a variable will be reused in an inappropriate manner during long-term maintenance of the code.
-   It's easier to refactor code. You can copy in code without having to worry that variables might be reused in contexts where they shouldn’t be reused.

In the following example, we declare the loop counter inside the **for** statement that it's used in.

    void MyMethod()
    {
        for (int i = 0; i < 10; i++)
        {
            info(strfmt("i is %1", i));
        }
    }

The scope of the variable is the **for** statement itself, and includes the condition expression and the loop update parts. The value can’t be used outside this scope. In the following example, when the compiler reaches the **info** statement, it will issue the following error message: "'i' isn't declared."

    void MyMethod()
    {
        for (int i = 0; i < 10; i++)
        {
            if (i == 7)
            {
                break;
            }
        }
        // The next statement causes a compiler error.
        info(strfmt("Found: %1", i));
    }

You can also scope variables to a **using** statement, as shown in the following example.

    static void AnotherMethod()
    {
        str textFromFile;
        using (System.IO.StreamReader sr = new System.IO.StreamReader("c:\\test.txt"))
        {
            textFromFile = sr.ReadToEnd();
        }
    }

When you use an object that implements **IDisposable**, you should declare and instantiate that object in a **using** statement. The **using** statement calls the **Dispose** method on the object correctly, even if an exception occurs while you're calling methods on the object. You can achieve the same result by putting the object inside a **try** block and then explicitly calling **Dispose** in a **finally** block. In fact, the compiler translates the **using** statement in just this manner. The following example shows some of the features that we have been describing.

    // loop variable declared within the loop: It will
    // not be misused outside the loop
    for(int i = 1; i < 10; i++)
    {
        // Because this value is not used from outside the loop,
        // its declaration belongs in this smaller scope.
        str s = int2str(i);
        info(s);
    }

To prevent confusion, the compiler issues an error message if you try to introduce a variable that will hide another variable in an enclosing scope, or even in the same scope. For example, the following code will cause the compiler to issue the following diagnostic message: "A local variable named 'i' can't be declared in this scope because it would give a different meaning to 'i', which is already used in a parent or current scope to denote something else."

    {
        int i;
        {
            int i;
        }
    }

### Constants, read-only variables, and macros

The concept of macros is fully supported. However, constants have the following advantages over macros:

-   You can add a documentation comment to a constant but not to the value of a macro. Eventually, the language service will pick up this comment and provide useful information to the user.
-   A constant is known by IntelliSense.
-   A constant is cross-referenced. Therefore, you can find all references for a specific constant but not for a macro.
-   A constant is subject to access modifiers. You can use the **private**, **protected**, and **public** modifiers. The accessibility of macros isn't rigorously defined.
-   Constant variables have scope, whereas macros don't have scope.
-   You can see the value of a constant or a read-only variable in the debugger.

Macros that are defined in class scopes (that is, in class declarations) are effectively available in all methods of all derived classes. This feature was originally a bug in the implementation of the legacy compiler macro. However, many application programmers often take advantage of it now. The X++ compiler still honors this feature, but no new code that uses it should be written. This feature also has a significant effect on the performance of the compiler. Constants can be declared at the class level, as shown in the following example.

    private const str MyConstant = 'SomeValue';

The constants can then be referenced by using the double colon (::) syntax.

    str value = MyClass::MyConstant;

If you're in the scope of the class where the constant (**const**) is defined, you can omit the type name prefix (**MyClass** in the preceding example). Therefore, you can easily implement the concept of a macro library. The list of macro symbols becomes a class that has public **const** definitions. You can also define constants as variables only. The compiler will maintain the invariant so that the value can't be modified.

    {
        const int Blue = 0x0000FF;
        const int Green = 0x00FF00;
        const int Red = 0xFF0000;
    }

## Primitive data types
The primitive data types in X++ are **anytype**, **boolean**, **date**, **enum**, **guid**, **int**, **int64**, **real**, **str**, **timeOfDay**, and **utcdatetime**.

### anytype

The **anytype** data type is a placeholder for any data type. You should use variables of this type only as arguments and return values. To use **anytype** as a variable, you must first assign a value to it. Otherwise, a run-time error occurs. After you've assigned a value to **anytype**, you can't convert it to another data type. Although you can use **anytype** variables in expressions, they're usually used as arguments and return types. The size, precision, scope, default value, and range of **anytype** depend on the conversion type that you assign to it. You can use **anytype** just as you use the data type that you convert it to. For example, if you assign an integer, you can then apply relational and arithmetic operators to the variable. An **anytype** variable is automatically converted to a date, enumeration (enum), integer, real, string, extended data type (EDT) (record), class, or container when a value is assigned to the type. Additionally, the following explicit [conversion functions](xpp-conversion-run-time-functions.md) can be used: **any2date**, **any2enum**, **any2int**, **any2real**, and **any2str**. You can't change the variable to another data type after you've converted it to **anytype**.

#### anytype examples

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

### boolean

The **boolean** data type contains a value that is evaluated as either **true** or **false**. You can use the reserved literal keywords **true** and **false** wherever a **boolean** expression is expected. The size of a **boolean** is 1 byte. The default value is **false**, and the internal representation is a short number. A **boolean** is automatically converted to an **int**, **date**, or **real**. It has no explicit conversion functions. The internal representation of a **boolean** is an integer. You can assign any integer value to a variable that is declared as the **boolean** type. The integer value **0** (zero) is evaluated as **false**, and all other integer values are evaluated as **true**. Because the internal representation of a **boolean** is an integer, **boolean** values are automatically converted to integers and reals.

#### boolean examples

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

### date

The **date** data type contains the day, month, and year. Dates can be written as literals by using the following syntax: **Date literal = day \\ month \\ year**. You must use four digits for the year. The **date** data type can hold dates between January 1, 1900, and December 31, 2154. The size of a **date** is 32 bits. The default value is **null**, and the internal representation is a date. A **date** has no implicit conversions. However, the following explicit [conversion functions](xpp-conversion-run-time-functions.md) can used: **str2date**, **date2str**, **date2num**, and **int2date**. You can add and subtract integers from dates, but you can't add or subtract two dates from each other. If you try, a compiler error occurs.

#### date examples

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

### enum

An **enum** is a list of literals. Before you can use an **enum**, you must declare it in Application Explorer. The literal values are represented internally as integers. The first literal has the number 0, the next literal has the number 1, the next literal has the number 2, and so on. You can use **enum** values as integers in expressions. The default value for the first entry is **0**, and the internal representation is a short number. An **enum** value is automatically converted to a **boolean**, **int**, or **real**. Additionally, the following explicit [conversion functions](xpp-conversion-run-time-functions.md) can be used: **enum2str** and **str2enum**. Hundreds of enumerable types are built into the standard application. For example, the **NoYes** enum has two associated literals: **No** has the value **0**, and **Yes** has the value **1**. You can create as many enum types as you want, and you can declare up to 251 (0 to 250) literals in a single enum type. To reference an **enum** value, enter the name of the enum, two colons, and then the name of the literal. For example, to use the literal **No** in the **NoYes** enum, enter **NoYes::No**.

#### Create an enum

1.  In Solution Explorer, right-click the project, point to **Add**, and then click **New Item**.
2.  Under **Artifacts**, select **Data Types**.
3.  Click **Base Enum** to select the new item type.
4.  In the **Name** field, enter a name for the enum, and then click **Add**. A new enum is added to the project, and the enum designer for the new element is opened.
5.  In the enum designer, right-click the enum name, and then click **New Element**.
6.  In the **Properties** window, enter the name of the enum element.

#### enum examples

    public void EnumMethod()
    {
        // Declare the enum (a NoYes enum) in the Application Explorer.
        NoYes done;
            
        // An array of Criteria enums.
        Criteria crit[100];
    }

### guid

The **guid** data type holds a *globally unique identifier* (GUID) value. A GUID is an integer that can be used across all computers and networks, wherever a unique identifier is required. It's unlikely that the number will be duplicated. A valid GUID meets all the following specifications:

-   It must have 32 hexadecimal digits.
-   It must have four dash characters that are embedded at the following locations: 8-4-4-4-12.
-   Braces ({}) at the beginning and end of a string are optional. For example, both "12345678-BBBb-cCCCC-0000-123456789012" and "{12345678-BBBb-cCCCC-0000-123456789012}" are valid GUID strings.
-   It must have a total of either 36 or 38 characters, depending on whether braces are added.
-   The hexadecimal digits a–f (or A–F) can be uppercase, lowercase, or mixed.

The size of a **guid** is 16 bytes or 128 bits. The following explicit [conversion functions](xpp-conversion-run-time-functions.md) can be used: **any2guid**, **guid2str**, **newGuid**, **str2guid**, **Global::guidFromString**, and **Global::stringFromGuid**.

#### guid examples

The following set of examples shows how to use the **guid** functions. The code output of these examples follows.

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

#### guid code output

The following output appears in the Infolog. Note that the string includes the optional braces.

    Message (02:26:46 pm)
    Info_a1:  guid2 == {93945629-734B-475E-99CE-6AA7AFA43259}
    Info_a2:  string3 == {93945629-734B-475E-99CE-6AA7AFA43259}
    Info_a3:  guid2 == {93945629-734B-475E-99CE-6AA7AFA43259}
    Info_b1:  8-4-4-4-12 format for dashes works ({BB345678-ABCD-ABCD-0000-BBBBFFFF9012})
    Info_b2:  Mixed upper and lower case works.
    Info_c1:  These embedded dash locations are required.  {00000000-0000-0000-0000-000000000000}
    Info_d1:  Braces {} are optional ({DD345678-ABCD-ABCD-0000-DDDDAAAA9012})

### int and int64

*Integers* are numbers that have no decimal places. There are two integer types: **int** and **int64**. Integers are used as control variables in repetitive statements or as indexes in arrays. You can also use *integer literals* anywhere that an integer expression is expected, and both relational and arithmetic operators can be applied. An integer literal is the integer as it's entered directly in the code, such as **32768**. An **int** is 32 bits wide, and an **int64** is 64 bits wide. The default value is **0**, and the internal representation is a long number. An integer is automatically converted to a **boolean**, **enum**, or **real**. Additionally, the following explicit [conversion functions](xpp-conversion-run-time-functions.md) can be used: **str2int**, **int2str**, **str2int64**, and **int642str**. The range of an **int** is \[-2,147,483,647 : 2,147,483,647\], and the range of an **int64** is \[-9,223,372,036,854,775,808 : 9,223,372,036,854,775,808\]. All integers in either of these ranges can be used as literals.

#### int and int64 examples

The following example shows how to declare integers and use them in expressions. If you try to assign the largest integer plus 1 to an **int64**, you get the wrong result, because the number is interpreted as a 32-bit number. Therefore, the number is wrapped around and stored as -2,147,483,647 instead. To prevent this behavior, add "u" to the end of the number. For example, enter **int64 i = 0x8000 0000u** (0x8000 0000 is 2,147,483,648).

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

### real

A **real** variable can hold decimal values in addition to integers. You can use *decimal literals* anywhere that a **real** is expected. A decimal literal is the decimal as it's entered directly in the code, such as **2.123876**. Real literals can also be written by using exponential notation, such as **1.0e3**. Reals can be used in all expressions, and they can be used with both relational and arithmetic operators. A **real** has a precision of 16 significant digits. The default value for a **real** is **0.0**, and the internal representation is a binary-coded digital (BCD) number. The BCD encoding enables exact representations of values that are multiples of 0.1. The range of a **real** variable is -(10)¹²⁷ through (10)¹²⁷. All reals in this range can be used as literals in X++. A **real** variable is automatically converted to a **boolean**, **enum**, or **int**. If the result is an integer, or if the operator is an integer operator, the **real** is converted to an integer. If the result is a **boolean**, the **real** is converted to a **boolean**, and so on. Additionally, the following explicit [conversion functions](xpp-conversion-run-time-functions.md) can be used: **str2num** and **num2str**. Direct assignments between X++ **real** and Microsoft .NET Framework **System.Decimal** convert the value correctly. A call to a conversion function isn't required. A *decimal number* is a floating-point value that consists of a sign, a numeric value where each digit is in the range 0 through 9, and a scaling factor that indicates the position of a floating decimal point that separates the integral and fractional parts of the numeric value. The binary representation of a **real** value consists of a 1-bit sign, a 96-bit integer number, and a scaling factor. The scaling factor is used to divide the 96-bit integer and specify what part of it is a decimal fraction. The scaling factor is implicitly the number 10 raised to an exponent in the range 0 through 28. Therefore, the binary representation of a decimal value represents (\[-2⁹⁶ through 2⁹⁶\] ÷ 10(0\\ through\\ 28)), where -(2⁹⁶-1) is the minimum value that can be expressed and 2⁹⁶-1 is the maximum value. **Note:** The type that is used to represent **real** values in Microsoft Dynamics 365 for Operations has changed from the interpreted X++ of Microsoft Dynamics AX 2012. However, you don't have to rewrite any code, because the new type can express all the values that the old type could express. We provide this material in the interest of full disclosure only. All instances of the **real** type are now implemented as instances of the .NET decimal type (**System.Decimal**). Just as the **real** type in previous versions, the decimal type in a binary-coded decimal type is resilient to rounding errors. The range and resolution of the decimal type differ from previous versions. The original X++ **real** type supported 16 digits and an exponent that defined the position of the decimal point. However, the X++ **real** type for Microsoft Dynamics 365 for Operations and later can represent decimal numbers in the range 79,228,162,514,264,337,593,543,950,335 (2⁹⁶-1) through -79,228,162,514,264,337,593,543,950,335 (-\[2⁹⁶-1\]). Rounding is still required for the new **real** type. For example, the following code produces a result of 0.9999999999999999999999999999 instead of 1. No number of decimals will suffice to represent the value of 1/3 accurately. The discrepancy obtained here is due to the fact that only a finite number of decimals are provided. You should use the **round** function to round to the number of decimals required.

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

#### real examples

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

### str

A **str** variable (a *string*) is a sequence of characters that are used as texts, help lines, addresses, telephone numbers, and so on. To declare a string, use the **str** keyword. *String literals* are characters that are enclosed in quotation marks (""). String literals can be used wherever string expressions are expected. Examples of string literals include "StringLit" and "Hello World". If you want the string to span more than one line, precede it with an at sign (@). You can use strings in logical expressions, such as comparisons. You can also concatenate strings by using the + operator. The default value for a string is **empty**, and the internal representation is a list of characters. There are no automatic conversions for strings. However, the following explicit [conversion functions](xpp-conversion-run-time-functions.md) can be used: **str2int**, **str2int64**, **int2str**, **str2num**, **num2str**, **str2date**, and **date2str**. A string can hold an unlimited number of characters. However, you can specify the maximum length of a string in the variable declaration. The string is then truncated to that maximum length. An example is shown in the next section.

#### str examples

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

### timeOfDay

The **timeOfDay** (time) data type is an integer value that represents the number of seconds that have passed since midnight. Like integers, **timeOfDay** variables can be used as literals. Relational and arithmetic operators can be applied to **timeOfDay** variables. A **timeOfDay** variable can also be used in expressions. The range of a **timeOfDay** data type is in the closed interval \[0; 86,400\]. Values above 86,400 (23:59:59) can't be interpreted. A **timeOfDay** variable is automatically converted to a **boolean**, **enum**, or **real**. Additionally, the following explicit [conversion functions](xpp-conversion-run-time-functions.md) can be used: **str2time** and **time2str**.

#### timeOfDay examples

    public void TimeofdayMethod()
    {
        // Declaration of a timeOfDay variable, time1.
        timeOfDay time1;
            
        // Declaration and initialization of a timeOfDay variable to 00:21:35.
        timeOfDay time2 = 1295;
    }

### utcdatetime

The **utcdatetime** data type combines the **date** type and the **timeOfDay** type. A **utcdatetime** variable also holds information about the time zone. However, this information can't be accessed in code. The format for a **utcdatetime** literal is **yyyy-mm-ddThh:mm:ss**. The uppercase "T" is required. This format can be written without quotation marks. The minimum value is **1900-01-01T00:00:00**, and the maximum value is **1900-01-01T00:00:00**. This maximum value matches the upper range of **date** and **timeOfDay**. The smallest unit of time in **utcdatetime** is one second. A **utcdatetime** variable that has been declared but hasn't been initialized has the default value **1900-01-01T00:00:00**. This value is the value that is returned by **DateTimeUtil::minValue()**. Some functions treat an input parameter of this minimum value as **null**. For example, the **DateTimeUtil::toStr** method returns an empty string. However, the **DateTimeUtil::addSeconds** method returns a usable **utcdatetime** value. There are no implicit conversions for the **utcdatetime** data type. The **DateTimeUtil** class provides many methods that you can use to manipulate **utcdatetime** values. The following explicit [conversion functions](xpp-conversion-run-time-functions.md) can also be used: **str2datetime** and **datetime2str**. Additionally, the **Global** class provides the **utcDateTime2SystemDateTime** and **CLRSystemDateTime2UtcDateTime** conversion methods to support common language runtime (CLR) interop. Comparison operators are the only type of operators that can be used with the **utcdatetime** data type. The following operators can be used to compare two **utcdatetime** values: !=, &lt;, &lt;=, ==, &gt;, and &gt;=. When you add a **utcdatetime** field to a table, we recommend that you base the field on an EDT.

#### utcdatetime examples

    public void UtcdatetimeMethod()
    {
        // Declaring a utcdatetime literal.
        utcdatetime myUtc2 = 1988-07-20T13:34:45;
            
        // Another example of declaring a utcdatetime literal.
        int iDay = DateTimeUtil::day(1988-07-20T13:34:45);
            
        // utcdatetime using a quoted string parameter into the DateTimeUtil::parse method.
        utcdatetime myUtc4 = DateTimeUtil::parse("1988-07-20T13:34:45");
    }

## Composite data types
The composite data types in X++ are arrays, containers, classes as data types, delegates as data types, and tables as data types.

### Array

An *array* is a variable that contains a list of items that have the same data type. The elements of an array are accessed by using integer indexes. You use a separate statement to initialize each element in an array. When you use a container data type or an array object to create a collection, you can initialize multiple elements by using a single statement. By default, all the items in an array have the default value of the data type in the array. There are three kinds of arrays: *dynamic arrays*, *fixed-length arrays*, and *partly on disk arrays*.

-   **Dynamic arrays** – These arrays are declared by using an empty array option. In other word, they have only brackets (\[\]).
-   **Fixed-length arrays** – These arrays can hold the number of items that is specified in the declaration. Fixed-length arrays are declared like dynamic arrays, but a length option is included in the brackets.
-   **Partly on disk arrays** – These arrays are declared as either dynamic arrays or fixed-length arrays that have an extra option that declares how many items should be held in memory. The other items are stored on disk and are automatically loaded when they are referenced.

X++ supports only one-dimensional arrays. However, you can mimic the behavior of multiple array indexes. (For more information, see the "Multiple array indexes" section). Variables in objects and tables can be declared as arrays. For example, this functionality is used in address lines in the standard application. An array collection class lets you store objects in an array. Array indexes begin at 1. The first item in the array is referenced as \[1\], the second item is referenced as \[2\], and so on. The following syntax is used to access an array element: **ArrayItemReference = ArrayVariable \[ Index \]**. In this syntax, **ArrayVariable** is the identifier of the array, and **Index** is the number of the array element. **Index** can be an integer expression. Item zero \[0\] is used to clear the array. If a value is assigned to index 0 in an array, all elements in the array are reset to their default value.

#### Array examples

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

#### Multiple array indexes

Some languages, such as C++ and C\#, let you declare arrays that have more than one index. In other words, you can define "arrays of arrays." In X++, you can't directly create multiple array indexes, because only one-dimensional arrays are supported. However, you can implement multiple indexes by using the method that is described in this section. For example, you want to declare an array that has two dimensions, to hold an amount that is earned by country by dimension. There are 10 countries and three dimensions. In C++ and C\#, you declare the following array.

    // This is C# or C++ code, not X++ code.
    real earning[10, 3];

However, X++ doesn't support this declaration. Instead, you can define a one-dimensional array where the number of elements is the product of the elements in each dimension. Here is an example.

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

### Container

A *container* object is a dynamic list of items that contain primitive data types or composite data types. A container is useful when you must pass various types of values between the client and server tiers. However, if you plan to repeatedly add to a list in a loop, a container isn't a good choice. Containers are most suitable for processes that don't involve excessive modification to the size or contents of the container. When a container undergoes excessive additions of data, overall system performance can decrease, because container data must be repeatedly copied, and new space must be repeatedly allocated. A container isn't a class. A container contains an ordered sequence of primitive values or other containers. Because of the flexibility of **anytype**, a container offers a good way to store values of different types together. A container can be stored in the database. A container is one of the column types that you can select when you use Application Explorer to add a column to a table. A container slightly resembles an array, or collections such as the **List** or **Stack** classes. However, you can never change the size or content of a container after the container is created. X++ statements that appear to modify a container are internally building a new container and copying values as required. Even an assignment of a container to another container variable creates a new copy of the container. All these operations can affect performance. In the functions that provide access to a container (such as **conPeek**), the container is 1-based, not 0-based. Indexing is 1-based for arrays. The default value of a container is **empty**. The container doesn't contain any values. Some statements that use containers might appear to modify a container. However, inside the system, containers are never modified. Instead, the data from the original container is combined with data from the command to build a new container. You can create a new container by using one of the following functions: **conDel**, **conIns**, or **conPoke**. Additionally, the **Global** class has static methods for handling containers. These methods include **con2ArraySource**, **con2Buf**, **con2List**, **con2Str**, **containerFromXmlNode**, **conView**, and **str2Con**. There are several intrinsic functions for handling a container, such as **conIns** and **conPeek**. The X++ **conPeek** function returns an **anytype** type. Therefore, it's easier to read the values from a container when you don't know the type of each value. An **anytype** can be assigned to any X++ value type, provided that the value can be converted. Your code is easier to read when it avoids explicit data type conversions. Therefore, assign values from a container to the same data type that was used to put the value into the container. You must not assign a container to an **anytype**, because the system might not be able to determine the correct conversions. In these cases, unexpected behavior or errors might occur.

#### Comparing container to other options

The **container** type resembles other constructs, such as arrays and collection classes such as **List** and **Stack**. The difference between a container and **List** is that an instance of the **List** class is mutable. A **List** object first allocates more space than its data consumes. Then, as data is added, the space is filled. This behavior is more efficient than allocating more space every time that an element is added. An update of a **List** performs faster than similar operations on a container. When you construct a **List** object, you determine the one type of data that the **List** object can store. This restriction is less flexible for a **List** than it is for a container. However, you can store objects in a **List**, whereas a container can store only value types. The difference between a container and an array is that an array can hold only items of its declared type. You can allocate memory space for an array and fill that space with values later. For example, you can fill in values in a loop. This behavior is efficient and performs well. When you want to build a new container by appending new data, you can use either the **+=** operator or the **conIns** function. The **+=** operator is the faster alternative. Use the **conIns** function only when you want to add new data before the last index of the original data. In Dynamics AX 2012, although you could use the X++ compiler to store object references in containers, the result would fail at run time. However, in Microsoft Dynamics 365 for Operations, when the compiler sees an attempt to store an object reference in a container, it issues an error message. If the type of the element that is added to the container is **anytype**, the compiler can’t determine whether the value is a reference type. In this case, the compiler allows the attempt. It's assumed that the user knows what he or she is doing. Although the compiler doesn't diagnose the code as erroneous, an error will be thrown at run time.

#### Container examples

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

### Classes as data types

A *class* is a type definition that describes both variables and methods for instances of the class. (The instances of a class are also known as *objects*.) A class is only a definition for objects, and all objects are **null** when they are declared. In Application Explorer, every application class under the **Classes** node is a data type. You can declare variables of these types in your code. You can construct instances of a class and assign the instances to variables. Classes can be nested in source code. Nested classes are available only inside forms (such as a class that extends **FormRun**), and are used to represent controls, data sources, or data fields. An attribute decoration, such as the attribute decoration on a class or a method, can omit the suffix of the attribute name if the suffix is **Attribute**. Therefore, X++ allows **\[MyFavorite\]** instead of requiring **\[MyFavoriteAttribute\]**. Additionally, attributes are now applied to the handlers of delegates and methods, to map the handlers to those targets. In AX 2012 and earlier versions, you could designate a method to run on either the client or the server. However, in Microsoft Dynamics 365 for Operations and later versions, all compiled X++ code is run as .NET Common Intermediate Language (CIL) on the server. There is no longer any code that is evaluated at the client site or in the browser. Therefore, the **client** and **server** keywords are now ignored. Although these keywords don't cause a compile error if they are used, they should not be used in any new code.

#### Private and protected member variables

Previously, all member variables that were defined in a class were protected. You can now make the visibility of member variables explicit by adding the **private**, **protected**, and **public** keywords. The interpretation of these modifiers is obvious and is aligned with the semantics for methods:

-   **private** – The member variable can be used only within the class where it’s defined.
-   **protected** – The member variable can be used in the class where it’s defined and all subclasses of that class.
-   **public** – The member variable can be used anywhere. It’s visible outside the confines of the class hierarchy where it’s defined.

By default, member variables that aren’t adorned with an explicit modifier are still protected. However, as a best practice, you should explicitly specify the visibility. As we described earlier, when a member variable is defined as **public**, it can be accessed outside the class where it’s defined. In this case, you must specify a qualifier that designates the object that is hosting the variable. To specify the qualifier, use the dot notation, as you do for method calls. In the following example, **field1** is accessed by using the explicit **this** qualifier. In this case, it might not be a good idea to make a member variable public, because that approach exposes the internal workings of the class to its consumers, and therefore creates a strong dependency between the class implementation and its consumers. You should always try to depend only on a contract, not an implementation.

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

#### Static constructors and static fields

*Static fields* are fields that are declared by using the **static** keyword. Conceptually, static fields apply to the class, not to instances of the class. Static constructors are guaranteed to run before any static calls or instance calls are made to the class. The execution of the static constructor is relative to the user’s session. You never call the static constructor explicitly. Instead, the compiler will generate code to make sure that the constructor is called exactly one time, before any other method on the class is called. A static constructor is used to initialize any static data or perform an action that must be performed only one time. You can't provide parameters for the static constructor, and it must be marked with the **static** keyword.

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

#### Class elements in Application Explorer

Under most class nodes in Application Explorer, there are two special nodes: a **classDeclaration** node and a **new** node. A **classDeclaration** always contains the X++ **class** keyword. Additional keywords, such as **extends**, can be included to modify the class. This node can also contain declarations of member variables. The member variables can't be initialized to a value in **classDeclaration**, and they can't be static. In the following example, the variables **m\_priority** and **m\_rectangle** are members of the class.

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

A **new** operator contains logic that is run when the **new** operator is used to create an instance of the class. The logic in the **new** method might construct an object and assign that object to a variable that is declared in the **classDeclaration**. Each class can have only one **new** method. However, in the **new** method, you often should call the **new** method of the base class. To call the **new** method of the base class, call **super()**. The following example shows the **new** method for the **YourDerivedClass** class in the previous **classDeclaration** example. In this **new** method, the code constructs an instance of the **Rectangle** class. The instance is assigned to the **m\_rectangle** variable. The **this** keyword that is used in the example is optional. However, if you include it, IntelliSense might be more helpful.

    // An example of the new method from the previous classDeclaration example.
    void new(int _length, int _width)
    {
        this.m_rectangle = new Rectangle(_length, _width);
    }

#### Garbage collection

Eventually during run time, most objects no longer have any variable that points to them. The system scans for these objects and erases them from memory. The memory space then becomes available for other uses. The **Object** class has a method that is named **finalize**. However, the **finalize** method isn't a destructor. The runtime never calls the **finalize** method, even when an object is collected as garbage.

#### System classes

In Application Explorer, under **System Documentation** &gt; **Classes**, there is a list of the kernel classes or system classes. System classes aren't written in X++, and you can't see their source code. You can't add system classes. System classes usually have a **new** method, but they don't have a **classDeclaration** node. Every application class implicitly extends the **Object** system class. Some system classes are extended by an application class that has a similar name. For instance, **xClassFactory** is extended by **ClassFactory**. In these cases, you should not use the system class. For more information, see "Substitute application classes for system classes" in [X++ classes and methods](xpp-classes-methods.md).

#### Extension methods

The extension method feature lets you add extension methods to a target class by writing the methods in a separate extension class. The following rules apply:

-   The extension class must be static.
-   The name of the extension class must end with the ten-character suffix **\_Extension**. However, there’s no restriction on the part of the name that precedes the suffix.
-   Every extension method in the extension class must be declared as **public static**.
-   The first parameter in every extension method is the type that the extension method extends. However, when the extension method is called, the caller must not pass in anything for the first parameter. Instead, the system automatically passes in the required object for the first parameter.
-   The target of an extension method must be a class, table, view, or map application object type.

An extension class can contain private or protected static methods. These methods are typically used for implementation details and aren't exposed as extensions. The extension method technique doesn’t affect the source code of the class that it extends. Therefore, the addition to the class doesn't require over-layering. Upgrades to the target class are never affected by any existing extension methods. However, if an upgrade to the target class adds a method that has the same name as your extension method, your extension method can no longer be reached through objects of the target class. The extension method technique uses the same dot-delimited syntax that you often use to call regular instance methods. Extension methods can access all public artifacts of the target class, but they can’t access anything that is protected or private. Therefore, extension methods can be considered a type of syntactic sugar. Regardless of the target type, an extension class is used to add extension methods to the type. For example, an extension table isn't used to add methods to a table, and there’s no such thing as an extension table.

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

### Delegates as data types

A *delegate* collects methods that subscribe to it. The delegate specifies the parameter signature that all its subscriber methods must share. When the delegate is called, the delegate calls each of its subscribers. A delegate never returns a value and **can't have a default value**. At first, every delegate has no subscribed methods. There is no limit on the number of parameters that a delegate can declare, and there is no limitation on the type of those parameters. The delegate body is always empty, because the delegate's only purpose is to define the contract that subscribers must conform to. A delegate doesn't have to be defined in a class. Delegates can also be defined in a table, form, or query.

#### Delegate examples

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
            info("A notification has occurred calling static handler:" +
                DateTimeUtil::toStr(_dateTime) +
                " Message:" +
                _changeDescription);
        }
    }

### Tables as data types

All tables can be treated as class definitions. A table variable can be considered an instance (object) of the table (class) definition. For every field in a table variable, the default value is **empty**. You can address fields and create methods on tables. The methods can be invoked on instances of the table. To manipulate (that is, read, update, insert, and delete) records in tables, you must declare at least one table variable that can hold the record in focus. As a best practice, you should use the name of the table as the name of the variable but use an initial lowercase letter. Here are a few important differences between tables and objects:

-   You can't allocate space for table variables. Allocation is done implicitly.
-   Fields in table variables are public. You can reference them anywhere.
-   Fields in table variables can be referenced by using expressions.

There is no automatic conversion, but table variables that are declared as **Common** can hold data from any table.

#### Scope of table variables

In most respects, table variables can be considered objects. However, unlike objects, they aren't explicitly allocated. Only a variable declaration is required. All tables are compatible with the Common table, just as all objects are compatible with the **Object** class. Table variables are declared as common buffers and can be used to hold data from any table. You can't access tables that don't have table variables. The principles for declaring table variables and objects are the same, except with regard to the allocation of space.

#### Table examples

The syntax enables various possibilities for referencing fields in records. For example, you can use the **TableName.(FieldId)** syntax. The following example prints the contents of the fields in the current record in the Customer table.

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

The following example uses the **fieldCnt** and **fieldCnt2Id** methods. The **fieldCnt** method counts the number of fields in a table, whereas **fieldCnt2Id** returns the ID for a field number. For example, you can use the **fieldCnt2Id** method to learn that field number 6 in a table has the ID 54. This conversion is required, because there is no guarantee that the IDs of the fields in a table are consecutive.

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

## Collection classes
The X++ language syntax provides two composite types: arrays and containers. These composite types are useful for aggregating values of primitive types. However, you can't store class objects in arrays or containers. *Collection classes* are used to store objects. They let you create arrays, lists, sets, maps, and structs that can hold any data type, even objects. For maximum performance, the classes are implemented in C++ (they are system classes). Collection classes were previously known as *foundation classes*. The collection classes are **Array**, **List**, **Map**, **Set**, and **Struct**.

-   **Array** – This class resembles the **array** type in the X++ language, but it can hold values of any single type, even objects and records. Objects are accessed in a specific order.
-   **List** – This class contains elements that are accessed sequentially. Unlike an array, the **List** class provides an **addStart** method. Like the **Set** class, the **List** class provides the **getEnumerator** and **getIterator** methods. You can use an iterator to insert and delete items from a **List** object.
-   **Map** – This class associates a key value with another value.
-   **Set** – This class holds values of any single type. Values aren't stored in the sequence in which they are added. Instead, the **Set** object stores the value in a manner that optimizes performance for the **in** method. A **Set** object ignores any attempt to add a value that the **Set** object is already storing. Unlike the **Array** class, the **Set** class provides the **in** and **remove** methods.
-   **Struct** – This class can contain values of more than one type. It's used to group information about a specific entity.

The constructor for every collection class except **Struct** takes a type parameter that is an element of the **Types** system enum. The collection instance can store items of that type only. The **Types::AnyType** enum element is a special case that can't be used to construct a collection object, such as a **Set** object. The **null** value can't be stored as an element in a **Set** object. Additionally, **null** can't be a key in a **Map** object. You can iterate through a collection object by using an iterator or enumerator. Here are typical examples that show how you can obtain an iterator.

    new MapIterator(myMap)
    myMap.getEnumerator()

For **Set** objects, if any elements are added or removed after an iterator is created, the iterator instance can no longer be used to read from or step through the collection. For **Map** objects, as for **Set** objects, if any elements are removed, the iterator is no longer valid. However, a **MapIterator** object remains valid even after a call to the **Map.insert** method, regardless of whether the key is new, or whether the key already exists and only the value is being updated in the **Map** element. Code that calls **Map.insert** and depends on the iterator object remaining valid might fail if it's run as .NET Framework CIL. You can use the collection classes to form more complex classes. For example, you can easily implement a stack by using a list where elements are always added to the beginning of the list. The newest element then occupies the top of the stack. You can also extend the collection classes. For example, you can extend the **List** class to create a list of customer records where the operations are type-safe. In this case, the derived collection class will accept only customer records.

## Extended data types
*Extended data types* are user-defined types that are based on the **boolean**, **int**, **int64**, **real**, **str**, and **date** primitive data types, and on the **container** composite type. An EDT is a primitive data type or container that has a supplementary name and additional properties. For example, you can create a new EDT that is named **Name** and base it on a string. You can then use the new EDT in variable and field declarations in the development environment. You can also base EDTs on other EDTs. EDTs are standard data types, but they have a specific name and additional properties. EDTs undergo the same value and type [conversions](xpp-conversion-run-time-functions.md) as the standard data types that they are based on. Here are the benefits of EDTs:

-   Code is easier to read, because variables have a meaningful data type. For example, the data type is **Name** instead of **str**.
-   The properties that you set for an EDT are used by all instances of that type. Therefore, EDTs help reduce work and promote consistency. For example, account numbers (**AccountNum** data type) have the same properties throughout the system.
-   You can create hierarchies of EDTs. The EDTs can inherit the appropriate properties from the parent, and you can change other properties. For example, the **ItemCode** data type is used as the basis for the **MarkupItemCode** and **PriceDiscItemCode** data types.

### Create an EDT

This feature isn't implemented as a language construct. To create an EDT, follow these steps.

1.  In Solution Explorer, right-click on the project, point to **Add**, and then click **New item**.
2.  In the **Add New Item** dialog box, select **Installed** and then **Artifacts** in the left pane.
3.  In the middle pane, select the EDT type to create.
4.  Enter a name, and then click **Add**.

### EDT example

    public void EdtMethod()
    {
        // Example of declaring EDT variables where
        // a UserGroupID (integer) variable is declared and initialized to 1.
        UserGroupID groupID = 1;
            
        // An Amount (real) variable is declared.
        Amount currency;
    }

## Null values for data types
Microsoft Dynamics 365 for Operations doesn't support the concept of **null** values that is available in many other database management systems (DBMSs). A variable in X++ always has a type and a value. However, for each data type, one value is considered **null** (for example, when the **validateField** table method is run).

| Type        | Value that is treated as null                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|-------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Date        | 1900-01-01                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Enum        | An element that has its value set to **0**                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Integer     | 0                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| Real        | 0.0                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| String      | An empty string                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Time        | 00:00:00                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| Utcdatetime | Any value that has its date portion set to **1900-01-01**, regardless of the value of the time portion For example, the value **1900-01-01T22:33:44** is treated as **null**. Note that any **utcDateTime** value that has its date portion set to **1900-01-01** is shown as blank by the X++ **print** statement. Only the value **1900-01-01T00:00:00** is shown as blank by the **Global::info** method. That value is the value from the **DateTimeUtil::MinValue** method. |

Therefore, when the **validateField** method checks whether a user has entered a value in a mandatory field, **0** isn't accepted in an **integer** type field, the first entry isn't accepted in an **enum** type field, and so on. Additionally, in SQL X++ statements, the values that are listed in the previous table yield **false** in a Boolean comparison. However, In non-SQL X++ statements, the equal and relational operators work with these values, just as they work with other values. Variables of the **container** type, and classes and variables of the **table** type can be **null** in the traditional DBMS sense. A **table** type is **null** if all its fields have their **null** value.

