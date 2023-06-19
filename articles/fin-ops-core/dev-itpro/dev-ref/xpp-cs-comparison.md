---
title: X++ and C# comparison
description: This article compares X++ and C# syntax and programming.
author: josaw1
ms.date: 04/10/2020
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# X++ and C# comparison

[!include [banner](../includes/banner.md)]

This article compares X++ and C# syntax and programming.

## X++, C# Comparison: Hello World

This section compares the simplest X++ program to its counterpart in C#.

### X++ to C# Comparisons

The following sections describe some basic similarities and differences between X++ and C\#.

### Similarities

The following X++ features are the same for C#:
-   Single line (`//`) and multi-line (`/* */`) comments.
-   `==` (equal) operator for determining whether two values are equal.
-   `!=` (not equal to) operator for determining whether two values aren't equivalent.
-   `+` (plus sign) operator for string concatenation.

### Differences

The following table lists X++ features that are different in C#.

| Feature | X++ | C# | Comments |
|---|---|---|---|
| `if` and `else` conditional statements | The `if` statement accepts any type of expression that it can automatically convert to a Boolean. Common examples include an `int` for which 0 means false, or an object for which null means false. | The `if` statement requires a Boolean expression. | The syntax structure regarding curly braces and parentheses is exactly the same between X++ and C#. |
| Literal string | A literal string can be delimited using either of the following methods: <ul><li>A pair of double quotation mark (") characters.</li><li>A pair of single quotation mark (') characters.</li></ul> | A literal string must be delimited by a pair of double quotation mark (") characters. | For X++, the double quotation mark characters are usually used to delimit strings. However, it's convenient delimit a string with single quotation mark characters when your string must contain a double quotation mark character.|
| char `type` | There isn't a `char` or a character type in X++. You can declare a `str` of length one, but it's still a string:<br> `str 1 myString = "a";` | There's a `char` in C#. You can't pass a `char` as the parameter to a method that inputs a `string` parameter, although you can first explicitly convert the `char` to a `string`.| For more information about X++ data types, see Primitive Data Types.|
| Output of messages| X++ delivers messages to the user in the Infolog window. Common methods include:<ul><li>The <strong>print</strong> statement:</li><li>static methods on the `Global` class:<ul><li>Global::info</li><li>Global::warning</li><li>Global::error</li></ul></li></ul>| For a command line program, messages can be delivered to the console. Common methods include: <ul><li>`Console.Out.WriteLine`</li><li>`Console.Error.WriteLine`</li></ul>|  |

### X++ and C# Samples

This section contains two simple code samples. One sample is written in X++, and the other is in C\#. Both samples achieve the same result. The following X++ features are demonstrated:
-   `//` single line comment
-   `/\*` `\*/` multi-line comment
-   `if` statement
-   `==` operator
-   `!=` operator
-   `+` operator to concatenate strings
-   Global::info for message output, with and without the Global:: prefix
-   Global::error for message output
-   The use of single and double quotation characters (' and ") as string delimiters.

> [!NOTE]
> The best practice is to use double quotation marks for any string that might be displayed to the user.

#### X++ Sample

This X++ code sample is in the form of a job. There's a node titled Jobs in the Application Object Tree (AOT). This sample can be added under the Jobs node, and then the job can be run.

```xpp
static void JobRs001a_HelloWorld(Args _args)
{
    if (1 == 1) 
    {
        // These two info() calls are identical to the X++ compiler.
        // The second form is the one typically used in X++.
        Global::info("Hello World, 1.");
        info('Hello World, 2.');
    }
    if (1 != 1)
    {
        error("This message will not appear.");
    }
    else
    {
        // These two methods are also from the Global class.
        // The + operator concatenates two strings.
        warning("This is like info, but is for warnings, 3.");
        error("This is like info, but is for errors, 4.");
    }
}
```

##### Output

Here's the output from the Infolog window:
    Message (09:49:48)
    Hello World, 1.
    Hello World, 2.
    This is like info, but is for warnings, 3.
    This is like info, but is for errors, 4.

#### C# Sample

The following C# program is a rewrite of the previous X++ program. 

```csharp
using System;
class Pgm_CSharp
{
    static void Main( string[] args )
    {
        new Pgm_CSharp().Rs001a_CSharp_HelloWorld();
    }
    void Rs001a_CSharp_HelloWorld()
    {
        if (1 == 1) 
        {
            Console .Out .WriteLine("Hello World, Explicit .Out , 1.");
            Console .WriteLine("Hello World, Implicit default to .Out , 2.");
        }
        if (1 != 1)
        {
            Console .Error .WriteLine("This message will not appear.");
        }
        else
        {
            Console .Error .WriteLine(".Error is like .Out, but can be for warnings, 3.");
            Console .Error .WriteLine(".Error is like .Out, but is for errors, 4.");
        }
    }
}
```

##### Output

Here's the actual output to the C# console:

```Console
Hello World, Explicit .Out, 1. 
Hello World, Implicit default to .Out, 2. 
.Error is like .Out, but can be for warnings, 3. 
.Error is like .Out, but is for errors, 4.
```

## X++, C# Comparison: Loops
This section compares the loop features between X++ and C\#.

###  Similarities

The following features are the same in X++ and C\#:
-   Declarations for variables of the int primitive data type. Declarations for other primitive types are almost the same, but the types might have different names.
-   while statement for loops.
-   break statement to exit a loop.
-   continue statement to jump up to the top of a loop.
-   <= (less than or equal) comparison operator.

###  Differences

The following table lists X++ features that are different in C#.

| Features | X++ | C# | Comments |
|---|---|---|---|
| The `for` statement.| The for statement is available for loops.| The C# `for` statement is slightly different from `for` in X++.| In C# you can declare the counter integer in the `for` statement. But in X++ the counter must be declared outside the `for` statement.|
|++ increment operator.|An ++ increment operator is available in X++. But an <strong>int</strong> variable that is decorated with ++ can only be used as a statement, not as an expression. For example, the following lines of X++ code would not compile:<br>`int age=42;`<br> `print age++;`<br> However, the following lines of X++ code would compile:<br>`int age=42;`<br>`age++; print age;`|The C# ++ operator is more flexible than in X++.|The following lines of code are the same in both languages:<ul><li>++ myInteger;</li><li>myInteger++;</li></ul>But the following lines of code have a different effect from each other, and are valid only in C#:<ul><li>yourInt = ++myInt;</li><li>yourInt = myInt++;</li></ul>|
| modulo operator.| In X++ the modulo operator is mod.| In C# the modulo operator is %.| The symbols for the modulo operator are different, but their behavior is the same in both languages.|
| Temporarily suspend a console program that has already begun.| The `pause` statement.| In C#, a command line program can be paused by the following line of code:<br>`Console.In.Read();`| In X++ you continue by clicking an OK button on a modal dialog box. In C# you continue by pressing any keyboard on the keyboard.|
| Display a message.| In X++, the `print` statement displays a message in the Print window.| In C# a message can be displayed on the console by the following line of code:<br>`Console.WriteLine();`| The X++ `print` function is used only when you test. An X++ program that uses `print` almost always uses the `pause` statement somewhere later in the code. For production X++ code, use the Global::info Method instead of `print`. The `strfmt` function is often used together with `info`. There isn't a reason to use `pause` after `info`.|
| Make a sound.| The beep function makes a sound that you can hear. | In C# a sound that you can hear is issued by the following line of code:<br>`Console.Beep();`| The statements each produce a short tone.|


### Print and Global::info

The X++ code samples for loops use the `print` function to display results. In X++ you can use the `print` statement can display any primitive data type without having to call functions that convert it to a string first. This makes `print` useful in quick test situations. Generally the Global::info method is used more often than `print`. The `info` method can only display strings. Therefore the strfmt function is often used together with `info`. A limitation of `print` is that you can't copy the contents of the Print window to the clipboard (such as with Ctrl+C). Global::info writes to the Infolog window which does support copy to the clipboard.

### Example 1: The while Loop

The **while** keyword supports looping in both X++ and C#.

#### X++ Sample of while

```xpp
static void JobRs002a_LoopsWhile(Args _args)
{
    int nLoops = 1;
    while (nLoops <= 88)
    {
        print nLoops;
        pause;
        // The X++ modulo operator is mod.
        if ((nLoops mod 4) == 0)
        {
            break;
        }
        ++ nLoops;
    }
    beep(); // Function.
    pause; // X++ keyword.
} 
```

##### Output

The output in the X++ Print window is as follows:

```xpp
1
2
3
4
```

#### C# Sample of while

```csharp
using System;
public class Pgm_CSharp
{
    static void Main( string[] args )
    {
        new Pgm_CSharp().WhileLoops();
    }

    void WhileLoops()
    {
        int nLoops = 1;
        while (nLoops <= 88)
        {
            Console.Out.WriteLine(nLoops.ToString());
            Console.Out.WriteLine("(Press any key to resume.)");
            // Paused until user presses a key.
            Console.In.Read();
            if ((nLoops % 4) == 0) {
                break;
            }
            ++ nLoops;
        }
        Console.Beep();
        Console.In.Read();
    }
}
```
 
##### Output

The console output from the C# program is as follows:

```Console
1
(Press any key to resume.)
2
(Press any key to resume.)
3
(Press any key to resume.)
4
(Press any key to resume.)
```

### Example 2: The for Loop

The **for** keyword supports looping in both X++ and C#.

#### X++ Sample of for

In X++ the counter variable can't be declared as part of the **for** statement.

```xpp
static void JobRs002a_LoopsWhileFor(Args _args)
{
    int ii; // The counter.
    for (ii=1; ii < 5; ii++)
    {
        print ii;
        pause;
        // You must click the OK button to proceed beyond a pause statement.
        // ii is always less than 99.
        if (ii < 99)
        {
            continue;
        }
        print "This message never appears.";
    }
    pause;
}
```
 
##### Output

The output in the X++ Print window is as follows:

```xpp
1
2
3
4
```

#### C# Sample of for

```csharp
using System;
public class Pgm_CSharp
{
    static void Main( string[] args )
    {
        new Pgm_CSharp().ForLoops();
    }
    void ForLoops()
    {
        int nLoops = 1, ii;
        for (ii = 1; ii < 5; ii++)
        {
            Console.Out.WriteLine(ii.ToString());
            Console.Out.WriteLine("(Press any key to resume.)");
            Console.In.Read();
            if (ii < 99)
            {
                continue;
            }
            Console.Out.WriteLine("This message never appears.");
        }
        Console.Out.WriteLine("(Press any key to resume.)");
        Console.In.Read();
    }
}
```
 
##### Output

The console output from the C# program is as follows:

```Console
1
(Press any key to resume.)
2
(Press any key to resume.)
3
(Press any key to resume.)
4
(Press any key to resume.)
(Press any key to resume.)
```

### X++, C# Comparison: Switch

In both X++ and C#, the **switch** statement involves the keywords **case**, **break**, and **default**. The following table lists the differences in the **switch** statement between X++ and C\#.

| Feature  | X++ | C# | Comments |
|--------|-----------|------------|-----|
| `break;` at the end of each case block       | In X++, when any **case** block matches the expression value on the **switch** clause, all other **case** and **default** blocks are executed until a `break;` statement is reached. No `break;` statement is ever required in an X++ **switch** statement, but `break;` statements are important in almost all practical situations. | In C\#, a `break;` statement is always needed after the statements in a **case** or **default** block. If a **case** clause has no statements between itself and the next **case** clause, a `break;` statement is not required between the two **case** clauses. | We recommend against omitting the `break;` statement after any case **block**, because it can confuse the next programmer who edits the code. |
| `break;` at the end of the **default** block | In X++ there isn't an effect of adding a `break;` statement at the end of the **default** block.   | In C\# the compiler requires a `break;` statement at the end of the **default** block. | For more information, see Switch Statements. |
| Only constant values on a **case** block     | In X++ you can specify either a literal value or a variable on a case block. For example, you can write case myInteger:.  | In C\# you must specify exactly one literal value on each **case** block, and no variables are allowed. | No comments.  |
| Multiple values on one **case** block        | In X++ you can specify multiple values on each case block. The values must be separated by a comma. For example, you can write `case 4,5,myInteger:`.    | In C\# you must specify exactly one value on each **case** block. | In X++ it's better to write multiple values on one **case** block than to omit the `break;` statement at the end of one or more case blocks. |

### Code Examples for switch

The following sections show comparable switch statements in X++ and C\#.

#### X++ switch Example

The X++ switch example shows the following:
-   `case iTemp:` and `case (93-90):` to show that **case** expressions aren't limited to constants, as they are in C\#.
-   `//break;` to show that `break;` statements aren't required in X++, although they are almost always desirable.
-   `case 2, (93-90), 5:` to show that multiple expressions can be listed on one **case** clause in X++.

```xpp
static void GXppSwitchJob21(Args _args)  // X++ job in AOT &gt; Jobs.
{
    int iEnum = 3;
    int iTemp = 6;
    switch (iEnum)
    {
        case 1:
        case iTemp:  // 6
            info(strFmt("iEnum is one of these values: 1,6: %1", iEnum));
            break;
        case 2, (93-90), str2Int("5"):  // Equivalent to three 'case' clauses stacked, valid in X++.
            //case 2:
            //case (93-90):  // Value after each 'case' can be a constant, variable, or expression; in X++.
            //case str2Int("5"):
            info(strFmt("iEnum is one of these values: 2,3,5: %1", iEnum));
            //break;  // Not required in X++, but usually wanted.
        case 4:
            info(strFmt("iEnum is one of these values: 4: %1", iEnum));
            break;
        default:
            info(strFmt("iEnum is an unforeseen value: %1", iEnum));
            break;
            // None of these 'break' occurrences in this example are required for X++ compiler.
    }
    return;
}

/*** Copied from the Infolog:
Message (02:32:08 pm)
iEnum is one of these values: 2,3,5: 3
iEnum is one of these values: 4: 3
***
```

#### C# switch Example

The C\# switch example shows the following:
-   case 1: has a comment explaining that only constant expressions can be given on a **case** clause.
-   `break;` statements occur after the last statement in each **case** block that has statements, as is required by C\#.

```csharp
using System;
namespace CSharpSwitch2
{
    class Program
    {
        static void Main(string[] args)  // C#
        {
            int iEnum = 3;
            switch (iEnum)
            {
                case 1:  // Value after each 'case' must be a constant.
                case 6:
                    Console.WriteLine("iEnum is one of these values: 1,6: " + iEnum.ToString());
                    break;
                //case 2,3,5:  // In C# this syntax is invalid, and multiple 'case' clauses are needed.
                case 2:
                case 3:
                case 5:
                    Console.WriteLine("iEnum is one of these values: 2,3,5: " + iEnum.ToString());
                    break;
                case 4:
                    Console.WriteLine("iEnum is one of these values: 4: " + iEnum.ToString());
                    break;
                default:
                    Console.WriteLine("iEnum is an unforeseen value: " + iEnum.ToString());
                    break;
                // All 'break' occurrences in this example are required for C# compiler.
            }
          return;
        }
    }
}
/*** Output copied from the console:
>> CSharpSwitch2.exe
iEnum is one of these values: 2,3,5: 3
>>
***/
```
 
## X++, C# Comparison: String Case and Delimiters
This section compares the treatment of strings with mixed casing in X++ and C\#. It also explains the string delimiters that are available in X++.

### Similarities

The following X++ features are the same as in C\#:
-   The backslash (\\) is the escape operator for string delimiters.
-   The at sign (@) nullifies the escape effect of the backslash when the at sign is written immediately before the open quotation mark of a string.
-   The plus sign (+) is the string concatenation operator.

### Differences

X++ features that are different in C\# are listed in the following table.

| Feature | X++ | C# | Comments |
|---|---|---|---|
| `== `comparison operator| Insensitive: the `==` operator is insensitive to differences in string casing.| In C#, the `==` operator is sensitive to differences in string casing.| In X++ you can use the strCmp Function for case sensitive comparisons between strings.|
| String delimiters| In X++ you can use either the single (') or double (`"`) quotation mark as the string delimiter.<p><strong>Note:</strong> Usually the best practice is to use double quotation marks for strings that might be displayed to the user. However, it's convenient to delimit a string with single quotation marks when a double quotation mark is one of the characters in the string.</p>| In C# you must use the double quotation mark as the string delimiter. This refers to the type `System.String`.| In X++ and C# you have the option of embedding a delimiter in a literal string and escaping it with \. <br>In X++ you also have the alternative of embedding single quotation marks in a string that is delimited by double quotation marks (or the reverse), without having to use the escape.|
| Character delimiters| X++ has a string data type (`str`), but no character type.| In C# you must use the single quotation mark as the character delimiter. This refers to the type `System.Char`.| In the .NET Framework, a `System.String` of length one is a different data type than a `System.Char` character.|

### Example 1: Case Sensitivity of the == Operator

The `==` and != operators are case insensitive in X++, but are case sensitive in C\#, as is illustrated by the following example.

| X++    | C#  | Comments       |
|----------------|---------|-----------|
| `"HELLO" == "hello"` <br>True in X++. | `"HELLO" == "hello"` <br>False in C#. | Different case comparisons between X++ and C#. |

### Example 2: The + String Concatenation Operator

The + and += operators are used to concatenate strings in both X++ and C\#, as is shown by the examples in the following table.

| X++  | C#   | Comments |
|---------|--------------------|----------------------------|
| `myString1 = "Hello" + " world";` <br>Result is equality: <br>`myString1 == "Hello world"`  | (Same as for X++.) | In both X++ and C#, the behavior of the + operator depends on the data type of its operands. The operator concatenates strings, or adds numbers. |
| `mystring2 = "Hello";` <br>`myString2 += " world";` <br>Result is equality: `myString2 == "Hello world"` | (Same as for X++.) | In both X++ and C#, the following statements are equivalent: <br>`a = a + b;` <br>`a += b;`  |

### Example 3: Embedding and Escaping String Delimiters

Either single or double quotation marks can be used to delimit strings in X++. The escape character (\\) can be used to embed delimiters in a string. These are illustrated in the following table.

| X++ | C#         | Comments   |
|---------|-----|--------------------------------------|
| `myString1 = "They said \"yes\".";` <br>Result: <br>`They said "yes".`  | (Same as for X++.)  | The escape character enables you to embed string delimiters inside strings.   |
| `myString2 = 'They said "yes".';` <br>Result: <br>`They said "yes".`  | C# syntax doesn't allow for single quotation marks to delimit strings.    | For strings that may be seen by the user, it's considered a best practice to use the escape character instead of the single quotation marks as shown in the example.   |
| `myString3 = "They said 'yes'.";` <br>Result: <br>`They said 'yes'.` | (Same as for X++.) | In X++, the single quotation marks aren't treated as delimiters unless the string starts with a single quotation mark delimiter. In C# the single quotation mark has no special meaning for strings, and it can't be used to delimit strings. In C# the single quotation mark is the required delimiter for literals of type `System.Char`. X++ has no character data type. |
| `str myString4 = 'C';` <br>Here the single quotation is a string delimiter. | `char myChar4 = 'C';` <br>Here the single quotation mark is a `System.Char` delimiter, not a `System.String` delimiter. | X++ has no data type that corresponds to `System.Char` in the .NET Framework. An X++ string that is limited to a length of one is still a string, not a character data type. |

### Example 4: Single Escape Character

Examples that illustrate the single escape character in either the input or the output are shown in the following table.

| X++    | C# | Comments     |
|-----------------------|--------|------------------|
| `myString1 = "Red\ shoe";` <br>Result: <br>`Red shoe`     | A literal string in C# can't contain the two character sequence of escape followed by a space, such as "\ ". A compiler error occurs. | When the X++ compiler encounters the two character sequence of "\ ", it discards the single escape character. |
| `myString2 = "Red\\ shoe";` <br>Result: <br>`Red\ shoe` | (Same as for X++.)  | In a pair of escape characters, the first negates the special meaning of the second.     |

## Comparison: Array Syntax

There are similarities and differences in the features and syntax for arrays in X++ versus C\#.

### Similarities

Overall there's much similarity in the syntax and treatment of arrays in X++ and C#. However there are many differences.

### Differences

The following table lists areas in the [] syntax for arrays that are different for X++ and C#.

| Category | X++ | C# | Comments |
|---|---|---|---|
| Declaration| An array is declared with square brackets appended to the variable name.| An array is declared with square brackets appended to the data type.| `int myInts[]; // X++` <p><strong>Note:</strong> An X++ array can't be a parameter in a method.</p><p>`int[] myInts; // C#`</p>|
| Declaration| The array syntax supports only primitive data types, such as `int` and `str`. The syntax doesn't support classes or tables.|The array syntax supports primitive data types and classes.| In X++ you can use the `Array` Array for an array of objects.|
| Declaration| X++ is limited to single dimension arrays (myStrings[8]).| C# adds support for multi-dimensional arrays (myStrings[8,3]) and for jagged arrays (myStrings[8][3]).| In X++ you can't have an array of arrays. However, there's advanced syntax for limiting the amount of active memory that a large array can consume, which looks like the multi-dimensional syntax in C#: int intArray[1024,16];. For more information, see Best Practice Performance Optimizations: Swapping Arrays to Disk.|
| Declaration| In X++ an array is a special construct but it's not an object.| In C# all arrays are objects regardless of syntax variations.| X++ does have an Array class, but its underlying mechanism differs from arrays created by using the [] syntax. In C# all arrays use the same underlying mechanism, regardless of whether [] syntax of the `System.Array` class is used in your code.|
| Length| In X++ the length of a static sized array is determined in the declaration syntax.| In C# the size of an array is determined when the array object is constructed.| When you use the [] declaration syntax in X++, no more preparation is needed before you assign values to the array. <br>In C# you must declare and then construct the array before assigning to it.|
| Length| An X++ array can have a dynamic length that can be increased even after population has begun. This applies only when the array is declared without a number inside the []. Performance might be slowed if the length of the dynamic array is increased many times.| In C# the length of an array can't be changed after the length is set.| In the following fragment of X++ code, only the `myInts` array is dynamic and can increase in size. <br>`int myInts[];` <br>`int myBools[5];` <br>`myInts[2] = 12;` <br>`myInts[3] = 13;` <br>`myBools[6] = 26; //Error`|
| Length| You can get the length of some arrays by using the `dimOf` function.| C# arrays are objects that have a `Length` property.| No comments.|
| Indexing| Array indexing is 1 based.| Array indexing is 0 based.| mtIntArray[0] would cause an error in X++.|
| Constant| In X++ a constant value is best achieved by using the <strong>#define</strong> precompiler directive.| In C# you can decorate your variable declaration with the keyword <strong>const</strong>, to achieve a constant value.| X++ has no <strong>const</strong> keyword. C# can't assign values to variables that are created by its #define precompiler directive.|

### X++ and C\# Samples

The following code samples show how arrays of primitive data types are handled. The first sample is in X++, and the second sample is in C\#. Both samples achieve the same results.

#### X++ Sample

```xpp
static void JobRs005a_ArraySimple(Args _args)
{
    #define.macroArrayLength(3)
    // Static length.
    str sSports[#macroArrayLength];
    // Dynamic length, changeable during run time.
    int years[];
    int xx;
    Global::warning("-------- SPORTS --------");
    sSports[#macroArrayLength] = "Baseball";
    for (xx=1; xx <= #macroArrayLength; xx++)
    {
        info(int2str(xx) + " , [" + sSports[xx] + "]");
    }
    warning("-------- YEARS --------");
    years[ 4] = 2008;
    years[10] = 1930;
    for (xx=1; xx <= 10; xx++)
    {
        info(int2str(xx) + " , " + int2str(years[xx]));
    }
}
```

##### Output

The output to the Infolog is as follows:

```xpp
Message (14:16:08)
-------- SPORTS --------
1 , []
2 , []
3 , [Baseball]
-------- YEARS --------
1 , 0
2 , 0
3 , 0
4 , 2008
5 , 0
6 , 0
7 , 0
8 , 0
9 , 0
10 , 1930
```

#### C\# Sample

```csharp
using System;
public class Pgm_CSharp
{
    static public void Main( string[] args )
    {
        new Pgm_CSharp().ArraySimple();
    }
    private void ArraySimple()
    {
        const int const_iMacroArrayLength = 3;
        // In C# the length is set at construction during run.
        string[] sSports;
        int[] years;
        int xx;
        Console.WriteLine("-------- SPORTS --------");
        sSports = new string[const_iMacroArrayLength];
        sSports[const_iMacroArrayLength - 1] = "Baseball";
        for (xx=0; xx < const_iMacroArrayLength; xx++)
        {
            Console.WriteLine(xx.ToString() + " , [" + sSports[xx] + "]");
        }
        Console.WriteLine("-------- YEARS --------");
        // In C# you must construct the array before assigning to it.
        years = new int[10];
        years[ 4] = 2008;
        years[10 - 1] = 1930;
        for (xx=0; xx < 10; xx++)
        {
            Console.WriteLine(xx.ToString() + " , [" + years[xx].ToString() + "]");
        }
    }
} // EOClass
```

##### Output

The output from the C# program to the command line console is as follows:

```Console
-------- SPORTS --------
0 , []
1 , []
2 , [Baseball]
-------- YEARS --------
0 , [0]
1 , [0]
2 , [0]
3 , [0]
4 , [2008]
5 , [0]
6 , [0]
7 , [0]
8 , [0]
9 , [1930]
```

## Additional array-like X++ features

The **container** is a special data type that is available in X++. It can be considered as similar to an array, or similar to a `List` collection.

## Comparison: Collections
In a finance and operations application, you can use the X++ `List` collection class. The .NET Framework that is used in C# has a similar class named `System.Collections.Generic.List`.

### Comparing the Use of the List Classes

The following table compares methods on the X++ `List` class to the methods on `System.Collections.Generic.List` from the .NET Framework and C\#.

| Feature | X++ | C# | Comments |
|---|---|---|---|
| Declaration of collection| `List myList;`| `List<string> myList;`| The X++ declaration doesn't include the type of elements to be stored.|
| Declaration of iterator|`ListIterator iter`<br>`ListEnumerator enumer;`| IEnumerator&lt;string&gt; iter;| In X++ the `ListIterator` object has methods that can `insert` and `delete` items from the `List`. The X++ `ListEnumerator` can't modify the contents of the `List`. In X++ the `ListEnumerator` object is always created on the same tier as the `List`. This is not always true for `ListIterator`.|
| Obtaining an iterator|`new ListIterator (myList)`<br>`myList.getEnumerator()`| `myList.GetEnumerator()`| In both X++ and C#, the List object has a getter method for an associated enumerator.|
| Constructor| `new List(Types::String)`| `new List<string>()`|Information about the type of objects to be stored inside the `List` classes is given to the constructor in both X++ and C#.|
| Updating data|Enumerator – the enumerator becomes invalid if any items in the `List` are added or removed.<br>Iterator – the iterator has methods that insert and delete items from the `List`. The iterator remains valid.| Enumerator – the enumerator becomes invalid if any items in the `List` are added or removed.| Enumerators become invalid after items are added or deleted from the `List`, in both X++ and C#.|
| Updating data| In X++ the `List` class has methods for adding items at the start or end of the list.| In C# the `List` class has methods for adding members at any position in the list. It also has methods for removing items from any position.| In X++ items can be removed from the `List` only by an iterator.|

### Example 1: Declaration of a List

The following code examples are in X++ and C# that declare `List` collections.

```xpp
// X++
List listStrings ,list2 ,listMerged;
ListIterator literator;
```

```csharp
// C#
using System;
using System.Collections.Generic;
List<string> listStrings ,list2 ,listMerged; IEnumerator<string> literator;
```

### Example 2: Construction of a List

In both languages, the type of items that the collection stores must be specified at the time of construction. For class types, X++ can get no more specific than whether the type is a class (Types::Class). The following code examples are in X++ and C#.

```xpp
// X++
listStrings = new List( Types::String );
```

```csharp
// C#
listStrings = new List<string>;
```

### Example 3: Add Items to a List

In both X++ and C#, the collection provides a method for appending an item to the end of the collection, and for inserting an item the start. In C# the collection provides a method for inserting at any point in the collection based on an index value. In X++ a collection iterator can insert an item at its current position. The following code examples are in X++ and C#.

```xpp
// X++
listStrings.addEnd ("StringBB."); 
listStrings.addStart ("StringAA.");
// Iterator performs a midpoint insert at current position. 
listIterator.insert ("dog");
```

```csharp
// C#
listStrings.Add ("StringBB."); 
listStrings.Insert (0 ,"StringAA.");
// Index 7 determines the insertion point.
listStrings.Insert (7 ,"dog");
```

### Example 4: Iterate Through a List

Both X++ and C\# have iterator classes that you can use to step through the items in a collection as shown in the following examples. 

```xpp
// X++
literator = new ListIterator (listStrings); 
// Now the iterator points at the first item.

// The more method answers whether 
// the iterator currently points 
// at an item. 
while (literator.more()) 
{ 
    info(any2str (literator.value())); 
    literator.next(); 
}
```

```csharp
// C#
literator = listStrings .GetEnumerator(); 
// Now enumerator points before the first item, not at the first item.

// The MoveNext method both advances the item pointer, and 
// answers whether the pointer is pointing at an item. 
while (literator.MoveNext()) 
{ 
    Console.WriteLine (literator.Current); 
}
```

### Example 4b: foreach in C\#

In C\# the **foreach** keyword is often used to simplify the task of iterating through a list. The following code example behaves the same as the previous C\# example. 

```csharp
foreach (string currentString in listStrings)
{ 
    Console.WriteLine(currentString);
}
```

###  Example 5: Delete the Second Item

The following code examples delete the second item from the collection. In X++ this requires an iterator. In C\# the collection itself provides the method for removing an item.

```xpp
// X++
literator.begin(); 
literator.next(); 
literator.delete();
```

```csharp
// C#
listStrings.RemoveAt(1);
```

###  Example 6: Combine Two Collections

The following code examples combine the contents of two collections into one.

```xpp
// X++
listStrings = List::merge(listStrings ,listStr3);
// Or use the .appendList method:
listStrings.appendList (listStr3);
```

```csharp
// C#
listStrings.InsertRange(listStrings.Count ,listStr3);
```

## Comparison: Collections of keys with values

In a finance and operations application, you can use the `Map` collection class. The `Map` collection holds pairs of values, the key value plus a data value. This resembles the .NET Framework class named `System.Collections.Generic.Dictionary`.

### Similarities

The following list describes similarities between X++ and C\# regarding their collections that store key-value pairs:
-   Both prevent duplicate keys.
-   Both use an enumerator (or iterator) to loop through the items.
-   Both key-value collection objects are constructed with designations of the types that are stored as key and value.
-   Both can store class objects, and aren't limited to storing primitives like **int**.

### Differences

The following table describes differences between X++ and C\# regarding their collections classes that store key-value pairs:

| Feature        | X++     | C#  | Comments |
|---|---|---|---|
| Duplicate keys | In X++ the `Map` class prevents duplicate keys by implicitly treating your call to its `insert` method as an operation to update only the value associated with the key. | In C\# the `Dictionary` class throws an exception when you try to add a duplicate key. | Duplicate keys are prevented in both languages, although by different techniques.               |
| Delete items   | In X++ the `delete` method on an iterator object is used to remove an unwanted key-value pair from a `Map`.    | In C\# the `Dictionary` class has a `remove` method.      | In both languages, an enumerator is made invalid if the collection item count is modified during the life of the enumerator. |

### Example 1: Declaration of a Key-Value Collection

In both languages, the type of items that the key-value collection stores must be specified. In X++ the type is specified at time of construction. In C\# the type is specified at both the time of declaration and the time of construction. The following code examples are in X++ and C#.

```xpp
// X++
Map mapKeyValue;
MapEnumerator enumer;
MapIterator mapIter;
```

```csharp
// C#
Dictionary<int,string> dictKeyValue;
IEnumerator<SysCollGen.KeyValuePair<int,string>> enumer;
KeyValuePair<int,string> kvpCurrentKeyValuePair;
```

### Example 2: Construction of the Collection

In both languages, the type of items that the key-value collection stores specified during construction. For class types, X++ can get no more specific than whether the type is a class (Types::Class). The following code examples are in X++ and C#.

```xpp
// X++
mapKeyValue = new Map(Types::Integer, Types::String);
```

```csharp
// C#
dictKeyValue = new Dictionary<int,string>();
```

### Example 3: Add an Item to the Collection

There's almost no difference in how an item is added to a key-value collection in X++ and C\# as shown in the following code examples.

```xpp
// X++
mapKeyValue.insert(xx ,int2str(xx) + “_Value”);
```

```csharp
// C#
dictKeyValue.Add(xx ,xx.ToString() + “_Value”);
```

### Example 4: Iterate Through a Key-Value Collection

Enumerators are used to loop through the key-value collections in both X++ and C\# as shown in the following code examples.

```xpp
// X++ 
enumer = mapKeyValue.getEnumerator();
while (enumer.moveNext())
{
    iCurrentKey = enumer.currentKey();
    sCurrentValue = enumer.currentValue();
    // Display key and value here.
}
```

```csharp
// C#
enumer = dictKeyValue.GetEnumerator();
while (enumer.MoveNext())
{
    kvpCurrentKeyValuePair = enumer.Current;
    // Display .Key and .Value properties=
    // of kvpCurrentKeyValuePair here.
}
```

### Example 5: Update the Value Associated with a Key

The syntax is very different between the two languages for an update of the value associated to a given key. The ollowing code examples are for the key 102.

```xpp
// X++
mapKeyValue.insert(
    102 ,
    ”.insert(), Re-inserted” + ” key 102 with a different value.”);
```

```csharp
// C#
dictKeyValue[102] = 
    “The semi-hidden .item property in C#, Updated the value for key 102.”;
```

### Example 6: Delete One Item

The syntax is very different between the two languages to delete one key-value pair from a collection, while iterating through the collection members. Code examples for the key 102 are shown below.

```xpp
// X++
mapIter = new MapIterator(mapKeyValue);
//mapIter.begin();
while (mapIter.more())
{
    iCurrentKey = mapIter.key();
    if (104 == iCurrentKey)
    {
        // mapKeyValue.remove would invalidate the iterator.
        mapIter.delete();
        break;
    }
    mapIter.next();
}
```

```csharp
// C#
dictKeyValue.Remove(104);
```

## Comparison: Exceptions
There are some similarities but many differences when we compare exception related behavior between X++ and C\#. The **try**, **catch**, and **throw** keywords behave the same in X++ and C#. But the types of exceptions thrown and caught are different for the two languages.

### Similarities

Similarities between X++ and C\# regarding their exception features include the following examples:
-   Both languages have the same **try** keyword.
-   Both have the same **catch** keyword.
-   Both enable for a **catch** statement that doesn't specify any particular exception. Such a **catch** statement catches all exceptions that reach it.
-   Both have the same **throw** keyword.

### Differences

Exception-related differences between X++ and C\# are described in the following table.

| Feature | X++ | C# | Comments |
|---|---|---|---|
| <strong>retry</strong>| Jumps to the first instruction in the associated <strong>try</strong> block. For more information, see Exception Handling with try and catch Keywords.| The functionality of the <strong>retry</strong> keyword can be mimicked in C# code, but there isn't a corresponding keyword.| Only X++ has a <strong>retry</strong> keyword. C# has no counterpart. For more information, see X++, C# Comparison: Automated Retry After an Exception.|
| <strong>finally</strong>| The `finally` keyword is supported to follow the `try` and `catch` keywords.| The <strong>finally</strong> keyword marks a block of code that follows the <strong>try</strong> and <strong>catch</strong> blocks. The finally will be executed regardless of whether any exception is thrown or caught.| The semantics are identical to the semantics in C#.|
| Specific exceptions| In X++ an exception is an element of the `Exception` enum, such as **Error**, **Deadlock**, or **CodeAccessSecurity**. No exception can contain another.| In C# an exception is an instance of the `System.Exception` base class, or any class that inherits from it. An exception can be contained in the `InnerException` property of the thrown exception.| In X++ each thrown exception is a value of the Exception enum. For more information, see Exception Enumeration.|
| Exception message| In X++ the message that is created when an exception is raised is available only in the Infolog, and the message is not directly tied to the exception.| In C# the message is the `Message` member of the `System.Exception` object.| In X++ the Global::error method is the mechanism that display exception messages in the Infolog. For more information, see Exception Handling with try and catch Keywords.|
| Exception conditions| In X++ an error occurs when you call an instance method on an object variable that has not yet had anything assigned to it. However, no exception is raised along with this error. Therefore no `catch` block can gain control even if the unassigned variable is misused in a `try` block. In the following code example, the error caused by the code `box4.toString();` doesn't cause control to transfer to any `catch` block: `DialogBox box4;` `try` { ` box4.toString();` ` info("toString did not error, but expected an error.");` } catch (Exception::Error) // No Exception value catches this. { ` info("Invalid use of box4 gave control to catch, unexpected.");` }| In C# a `System.NullReferenceException` is raised when an uninitialized variable is treated as an object reference.| There might be several other differences in the conditions that raise exceptions.|
| SQL transactions| In X++ when an SQL exception occurs in a <strong>ttsBegin</strong> - <strong>ttsCommit</strong> transaction, no <strong>catch</strong> statement inside the transaction block can process the exception.| In C# a catch block inside an SQL transaction can catch the exception.| |

### Examples

The following X++ features are demonstrated:
-   **try** keyword.
-   **catch** keyword.
-   The behavior after an Exception::Error exception occurs.

#### X++ Example

```xpp
// X++
static void JobRs008a_Exceptions(Args _args)
{
    str sStrings[4];
    int iIndex = 77;
    try
    {
        info("On purpose, this uses an invalid index for this array: " + sStrings[iIndex]);
        warning("This message doesn't appear in the Infolog," + " it's unreached code.");
    }
    // Next is a catch for some of the values of
    // the X++ Exception enumeration.
    catch (Exception::CodeAccessSecurity)
    {
        info("In catch block for -- Exception::CodeAccessSecurity");
    }
    catch (Exception::Error)
    {
        info("In catch block for -- Exception::Error");
    }
    catch (Exception::Warning)
    {
        info("In catch block for -- Exception::Warning");
    }
    catch
    {
        info("This last 'catch' is of an unspecified exception.");
    }
    //finally
    //{
    //    //Global::Warning("'finally' is not an X++ keyword, although it's in C#.");
    //}
    info("End of program.");
}
```

 
##### Output

Here's the output from the Infolog window:

```xpp
Message (18:07:24)
Error executing code: Array index 77 is out of bounds.
Stack trace
(C)\Jobs\JobRs008a_Exceptions - line 8
In catch block for -- Exception::Error
End of program.
```

#### C# Sample

The following C\# program is a rewrite of the previous X++ program.

```csharp
// C#
using System;
public class Pgm_CSharp
{
    static void Main( string[] args )
    {
        new Pgm_CSharp().Rs008a_CSharp_Exceptions();
    }
    void Rs008a_CSharp_Exceptions()
    {
        //str sStrings[4];
        string[] sStrings = new string[4];
        try
        {
            Console.WriteLine("On purpose, this uses an invalid index for this array: " + sStrings[77]);
            Console.Error.WriteLine("This message doesn't appear in the Infolog, it's unreached code.");
        }
        catch (NullReferenceException exc)
        {
            Console.WriteLine("(e1) In catch block for -- " + exc.GetType().ToString() );
        }
        catch (IndexOutOfRangeException exc)
        {
            Console.WriteLine("(e2) In catch block for -- " + exc.GetType().ToString() );
        }
        // In C#, System.Exception is the base of all
        // .NET Framework exception classes.
        // No as yet uncaught exception can get beyond
        // this next catch.
        catch (Exception exc)
        {
            Console.WriteLine("This last 'catch' is of the abstract base type Exception: "
                + exc.GetType().ToString());
        }
        // The preceding catch of System.Exception makes this catch of
        // an unspecified exception redundant and unnecessary.
        //catch
        //{
        //    Console.WriteLine("This last 'catch' is"
        //        + " of an unspecified exception.");
        //}
        finally
        {
            Console.WriteLine("'finally' is not an X++ keyword, although it's in C#.");
        }
        Console.WriteLine("End of program.");
    }
} // EOClass
```

 
##### Output

Here's the output to the C\# console:

```Console
(e2) In catch block for -- System.IndexOutOfRangeException
'finally' is not an X++ keyword, although it's in C#.
End of program.
```

## Comparison: Automated Retry After an Exception
Sometimes you can write code in a catch block that fixes the cause of an exception that occurs during run time. X++ provides a **retry** keyword that can be used only inside a **catch** block. The **retry** keyword enables a program to jump back to the start of the **try** block after the problem has been corrected by code in the **catch** block. C# doesn't have a **retry** keyword. However, C# code can be written to provide equivalent behavior.

### Code Samples for Retry

The following X++ sample program causes an Exception::Error to be raised. This occurs when it first tries to read an element from the `sStrings` array by using an invalid index value. When the exception is caught, corrective action is taken during run time inside the **catch** block. The retry statement then jumps back to the first statement in the **try** block. This second iteration works without encountering any exception.

```xpp
static void JobRs008b_ExceptionsAndRetry(Args _args)
{
    str sStrings[4];
    str sTemp;
    int iIndex = 0;

    sStrings[1] = "First array element.";
    try
    {
        print("At top of try block: " + int2str(iIndex));
        sTemp = sStrings[iIndex];
        print( "The array element is: " + sTemp );
    }
    catch (Exception::Error)
    {
        print("In catch of -- Exception::Error (will retry)." + " Entering catch.");
        ++iIndex;
        print("In catch of -- Exception::Error (will retry)." + " Leaving catch.");
        // Here is the retry statement.
        retry;
    }
    print("End of X++ retry program.");
    pause;
}
```

#### Output

Here's the output to the Print window:

```xpp
At top of try block: 0
In catch of -- Exception::Error (will retry). Entering catch.
In catch of -- Exception::Error (will retry). Leaving catch.
At top of try block: 1
The array element is: First array element.
End of X++ retry program.
```

### C# Sample

The following C\# sample is not a line-by-line translation from the previous X++ sample. Instead the C\# program has a different structure so that it mimics the behavior of the **retry** keyword that the X++ program relies on. The **try** and **catch** blocks are in a called method. The variables that are used in the **try** block are stored in the caller method. The caller method passes the variables as parameters that are decorated with the **ref** keyword, so that their values can be corrected inside the **catch** block of the called method. The called method captures all exceptions, and returns a **boolean** to communicate back to the caller whether a second call is required.

```csharp
// C#
using System;
public class Pgm_CSharp
{
    static void Main(string[] args)
    {
        new Pgm_CSharp() .Rs008b_CSharp_ExceptionsAndRetry();
    }
    void Rs008b_CSharp_ExceptionsAndRetry() // Caller
    {
        int iIndex = -1
            , iNumRetriesAllowed = 3;
        bool bReturnCode = true; // Means call the callee method.
        for (int xx=0; xx <= iNumRetriesAllowed; xx++)
        {
            if (bReturnCode)
            {
                bReturnCode = this.Rs008b_CSharp_ExceptionsAndRetry_Callee(ref iIndex);
            }
            else
            {
                break;
            }
        }
        Console.WriteLine("End of C# caller method.");
    }
    
    private bool Rs008b_CSharp_ExceptionsAndRetry_Callee(ref int iIndex)
    {
        bool bReturnCode = true; // Means call this method again.
        string[] sStrings = new string[4];
        string sTemp;
        sStrings[0] = "First array element.";
        try
        {
            Console.WriteLine("At top of try block: " + iIndex.ToString());
            sTemp = sStrings[iIndex];
            Console.WriteLine( "The array element is: " + sTemp );
            bReturnCode = false; // Means do not call this method again.
        }
        catch (Exception)
        {
            Console.WriteLine("In catch of -- Exception. Entering catch.");
            ++iIndex; // The 'ref' parameter in C#.
            Console.WriteLine("In catch of -- Exception. Leaving catch.");
            //retry;
            // In C# we let the caller method do the work
            // that the retry keyword does in X++.
        }
        Console.WriteLine("End of C# callee method.");
        return bReturnCode;
    }
}
```

 
#### Output

Here's the output to the console:

```Console
At top of try block: -1
In catch of -- Exception. Entering catch.
In catch of -- Exception. Leaving catch.
End of C# callee method.
At top of try block: 0
The array element is: First array element.
End of C# callee method.
End of C# caller method.
```

## Comparison: Operators
This section compares the operators between X++ and C\#.

### Assignment Operators

The following table displays the differences between the assignment operators in X++ and C\#.

| X++ and C# | Differences |
|---|---|
| `=`| In X++ this operator causes an implicit conversion whenever a loss of precision might occur, such for an assignment from an <strong>int64</strong> to an <strong>int</strong>. But in C# the assignment causes a compile error.|
| `+=` and `-=`| The only difference is that in C# these operators are also used in delegate manipulation.|
| ++ and --| These are the increment and decrement operators in both languages. The following line is identical in both languages:<br>`++myInteger;`<br>But in X++ these two operators are for statements, not for expressions. Therefore the following lines generate compile errors in X++:<br>`myStr = int2str(++myInteger);`<br>`myIntA = myIntBB++;`|

### Arithmetic Operators

The following table lists the arithmetic operators.

|X++ and C# | Differences |
|---|---|
| *| As the multiplication operator, there are no differences.<p><strong>Note:</strong> The asterisk is also used in the SQL statements that are part of the X++ language. In these SQL statements the asterisk can also be one of the following:</p><ul><li>A wildcard indicating that all the columns should be returned.</li><li>A wildcard for characters in a string that is used on a <strong>like</strong> clause.</li></ul>|
| `/`| The division operator is the same in X++ and C#.|
| `MOD`| For modulo operations, the only difference is that the % symbol is used in C#.|
| +| The addition operator is the same in X++ and C#. The plus sign is also used for string concatenation. This operator adds numbers and concatenates strings in both languages.|
| -| The subtraction operator is the same in X++ and C#.|


### Bitwise Operators

The following table compares the bitwise operators between X++ and C\#.


| X++ and C\# |                     Differences                      |
|-------------|------------------------------------------------------|
|  &lt;&lt;   | The left shift operator is the same in X++ and C\#.  |
|  &gt;&gt;   | The right shift operator is the same in X++ and C\#. |
|      ~      | The bitwise NOT operator is the same in X++ and C\#. |
|      &      | The binary AND operator is the same in X++ and C\#.  |
|      ^      | The binary XOR operator is the same in X++ and C\#.  |
|             |                                                      |

### Relational Operators

The following relational operators are the same in X++ and C\#:
-   `==`
-   `<=`
-   `<=`
-   `>`
-   `<`
-   `!=`
-   `&&`
-   `||`
-   `!`
-   `? :`

## Comparison: Events

There are some differences in how X++ and C# implement the event design pattern. For more information, see Event Terminology and Keywords.

### Comparison of Events between X++ and C\#

There are differences in the way delegates are used for events in X++ versus C#.

| Concept | X++ | C# | Comments|
|---|---|---|---|
| <strong>delegate</strong>| In X++, a delegate can be declared only as a member on a class. A delegate can't be a member on a table. All delegates are instance members of their class, not <strong>static</strong> members. No access modifier can be used on a delegate declaration, because all delegates are <strong>protected</strong> members. Therefore, the event can be raised only by code within the same class where the delegate is a member. However, the one exception to the private nature of a delegate is that code outside their class can operate on the delegates by using the += and -= operators.| In C#, each <strong>delegate</strong> is a type, just as every <strong>class</strong> is a type. A delegate is declared independently of any class. Without the <strong>event</strong> keyword, you can have a delegate as a parameter type on a method, just as you can have a class as a parameter type. You can construct an instance of a delegate to pass in for the parameter value.| In X++, each class is a type, but no delegate is a type. You can't construct an instance of a delegate. No delegate can be a parameter for a method. But you can create a class that has a delegate member, and you can pass instances of the class as parameter values. For more information, see X++ Keywords.|
| <strong>event</strong>| In X++ code, an event is one of the following:<ul><li>An explicit call to a delegate.</li><li>The start or end of a method.</li></ul>There isn't a <strong>event</strong> keyword in X++.| In C#, the <strong>event</strong> keyword is used to declare a <strong>delegate</strong> type as a member of a class. The effect of the <strong>event</strong> keyword is to make the delegate <strong>protected</strong>, yet still accessible for the += and -= operators. You can subscribe event handler methods to an <strong>event</strong> by using the += operator. A <strong>delegate</strong> can be useful without the <strong>event</strong> keyword, as a technique for passing a function pointer as a parameter into a method.| The automatic events that occur before the start of a method, and after the end of a method, can be subscribed to only by using the AOT.|
| += and -= operators| In X++, you use the += operator to subscribe methods to a <strong>delegate</strong>. The -= operator unsubscribes a method from a delegate.| In C#, you use the += operator to subscribe methods to an <strong>event</strong>, or to a <strong>delegate</strong> that is not used with the <strong>event</strong> keyword.| The delegate contains a reference to all the objects that have methods subscribed to the delegate. Those objects aren't eligible for garbage collection while delegate holds those references.|
| `eventHandler`| In X++, the <strong>eventHandler</strong> keyword is required when you use either the += or -= operator to subscribe or unsubscribe a method from a delegate.| `System.EventHandler` is a delegate type in the .NET Framework.| This term is used differently in X++ than it's in C# or the .NET Framework. For more information, see X++ Keywords.|

### X++ Example

The important things to notice are the following in the X++ example:

-   The `XppClass` has a delegate member that is named `myDelegate`.

    > [!NOTE]
    > The AOT contains a node for the delegate. The node is located at AOT > Classes > XppClass > myDelegate. Several event handler nodes can be located under the myDelegate node. Event handlers that are represented by nodes in the AOT can't be removed by the -= operator during run time.

-   The {} braces at the end of the delegate declaration are required, but they can't have any code in them.
-   The `XppClass` has two methods whose parameter signatures are compatible with the delegate. One method is static.
-   The two compatible methods are added to the delegate with the += operator and the **eventHandler** keyword. These statements do not call the event handler methods, the statements only add the methods to the delegate.
-   The event is raised by one call to the delegate.
-   The parameter value that passed in to the delegate is received by each event handler method.
-   The short X++ job at the top of the example starts the test.

```xpp
// X++
// Simple job to start the delegate event test.
static void DelegateEventTestJob()
{
    XppClass::runTheTest("The information from the X++ job.");
}
// The X++ class that contains the delegate and the event handlers.
class XppClass
{
    delegate void myDelegate(str _information)
    {
    }
    public void myEventSubscriberMethod2(str _information)
    {
        info("X++, hello from instance event handler 2: " + _information);
    }
    static public void myEventSubscriberMethod3(str _information)
    {
        info("X++, hello from static event handler 3: " + _information);
    }
    static public void runTheTest(str _stringFromJob)
    {
        XppClass myXppClass = new XppClass();
        // Subscribe two event handler methods to the delegate.
        myXppClass.myDelegate += eventHandler(myXppClass.myEventSubscriberMethod2);
        myXppClass.myDelegate += eventHandler(XppClass::myEventSubscriberMethod3);
        // Raise the event by calling the delegate one time,
        // which calls all the subscribed event handler methods.
        myXppClass.myDelegate(_stringFromJob);
    }
}
```

The output from the previous X++ job is as follows:

```xpp
X++, hello from static event handler 
3: The information from the X++ job. X++, hello from instance event handler 
2: The information from the X++ job.
```

### C# Sample

This section contains a C\# code sample for the event design pattern of the previous X++ sample.

```csharp
// C#
using System;
// Define the delegate type named MyDelegate.
public delegate void MyDelegate(string _information);
public class CsClass
{
    protected event MyDelegate MyEvent;
    static public void Main()
    {
        CsClass myCsClass = new CsClass();
        // Subscribe two event handler methods to the delegate.
        myCsClass.MyEvent += new MyDelegate(myCsClass.MyEventSubscriberMethod2);
        myCsClass.MyEvent += new MyDelegate(CsClass.MyEventSubscriberMethod3);
        // Raise the event by calling the event one time, which
        // then calls all the subscribed event handler methods.
        myCsClass.MyEvent("The information from the C# Main.");
    }
    public void MyEventSubscriberMethod2(string _information)
    {
        Console.WriteLine("C#, hello from instance event handler 2: " + _information);
    }
    static public void MyEventSubscriberMethod3(string _information)
    {
        Console.WriteLine("C#, hello from static event handler 3: " + _information);
    }
}
```

The output from the previous C\# sample is as follows:

```Console
CsClass.exe C#, hello from instance event handler 
2: The information from the C\# Main. C\#, hello from static event handler 
3: The information from the C\# Main.
```

### Events and the AOT

There are other event systems that apply only to items in the AOT. For more information, see Event Handler Nodes in the AOT.

## Comparison: Precompiler Directives

X++ and C# share some keywords for their precompiler directive syntax, but the meanings aren't always the same.

### Similarities

The X++ and C\# compilers recognize many of the same keywords. In most cases, the keywords mean the same for both language compilers.

### Differences

A fundamental difference between the precompiler directives in X++ versus C\# is the \#define keyword that both language precompilers recognize. Unlike C\#, in X++ the \#define directive requires a dot in its syntax. In X++, parentheses can be used to give the defined symbol a value. These differences are shown in the following examples:
-   In X++: \#define.InitialYear(2003)
-   In C\#: \#define InitialYear

A minor difference is that in C\# there can be spaces and tab characters between the \# character and the directive keyword, such as \# define Testing.

### Identical Keywords

The following table lists precompiler directives that are similar in X++ and C\#.

| Keyword | X++ | C# | Comments |
|---|---|---|---|
| `#define` | In X++, a precompiler variable name can be defined, and a value can be given to that variable.                | In C\#, a precompiler variable name can be defined, but no value can be given to that variable. Also, any \#define in C\# must occur at the top of the file, and can't occur after any code such as a using statement or a class declaration. | The C\# compiler can input a command line parameter of `/define` to define a precompiler variable name without defining the variable in any C\# code file. The X++ compiler has no counterpart to `/define`. |
|`#if`     | In X++, \#if can determine whether a precompiler variable exists, and whether the variable has a given value. | In C\#, \#if can only determine whether a precompiler variable exists. It can't test for any value because no value can be assigned. |      |
| `#endif`  | In X++, \#endif marks the end of an \#if block. It also ends an \#ifnot block.   | In C\#, \#endif marks the end of an \#if block, regardless of whether the block includes a \#else.       |   |

### Different Keywords with the Same Processing Result

The following table lists precompiler directives that are named differently in X++ and C\#, but that give the same results when processed.

| X++ | C# | Comments |
|---|---|---|
| \#ifnot                     | \#if \#else      | There isn't an \#else directive in X++, but the \#ifnot provides similar functionality. In X++, \#ifnot can determine whether a precompiler variable exists, and whether the variable doesn't have a specific given value. In C\#, \#if can determine whether a precompiler variable exists when the ‘!’ symbol is prefixed to the variable name. |
| `//BP Deviation documented` | \#pragma warning | These X++ and C\# entries aren't equivalent, but there's a partial similarity. Both suppress compiler warning messages.                    |
| \#macrolib                  | .HPP file in C++ | There's a partial similarity between the X++ directive \#macrolib versus an .HPP file in C++. Both can contain several \#define statements.            |

### Precompiler Directives Exclusive to X++

The following table lists X++ precompiler directives that have no direct counterpart in C\#.

| X++                  | Comments    |
|---|---|
| \#linenumber         | The \#linenumber directive is for obtaining the line number, so that it can be output to the Infolog. <br>The C\# directive \#line is different because its purpose is for setting the line number. |
| \#defdec \#definc    |         |
| \#globaldefine       | In X++, there's a small difference between \#globaldefine versus \#define. The difference is that \#globaldefine never overwrites a current nonnull value that was assigned to a precompiler variable by \#define. <br>C\# has nothing similar to this difference, because in C\#, a precompiler variable name can't be given a value. |
| \#localmacro \#macro | In X++, \#localmacro enables you to assign a multiline value to a precompiler variable. \#macro is a synonym, but \#localmacro is recommended. <br>In C\#, the \#define directive has part of this functionality, but it can't assign a value to a precompiler variable.      |
| \#globalmacro        | In X++, \#globalmacro is almost the same as the preferred \#localmacro.          |

## Comparison: Object Oriented Programming
The object oriented programming (OOP) principles of X++ differ from C\#.

### Conceptual Comparisons

The following table compares the implementation of OOP principles between X++ and C\#.

|Feature|X++|C#|Comments|
|---|---|---|---|
| Casting | The X++ language has the keywords <strong>is</strong> and <strong>as</strong>, which are used to make downcasts safe and explicit. **Tip**: X++ doesn't require the use of the <strong>as</strong> keyword when you downcast a base class variable to a derived class variable. However, we recommend that all downcast statements use the <strong>as</strong> keyword.| An object can be cast either up or down the inheritance path. Downcasts require the <strong>as</strong> keyword.| For more information about the X++ keywords <strong>is</strong> and <strong>as</strong>, see Expression Operators: Is and As for Inheritance.|
| Local functions| A method can contain a declaration and code body for zero or more local functions. Only that method can have calls to the local function.| C# 3.0 supports lambda expressions, which have some similarity to anonymous functions and local functions. Lambda expressions are often used with delegates.| |
| Method overloading | Method overloading is not supported. A method name can occur only one time per class.| Method overloading is supported. A method name can occur multiple times in one class, with different parameter signatures in each case.| X++ does support optional parameters on methods. Optional parameters can partially mimic method overloading. For more information, see the row for optional parameters in this table.|
| Method overriding | Method overriding is supported. A derived class can have a method by the same name as in the base class, as long as the parameter signature is the same in both cases. The only exception is that the overriding method can add a default value to a parameter.| Method overriding is supported. The <strong>virtual</strong> keyword must be applied to a method before the method can be overridden in a derived class.| The concept of overriding a method includes the method name, its parameter signature, and its return type. The concept of method overriding doesn't apply if the base method and the overriding method differ in any of these aspects.|
| Optional parameters| A parameter declaration can be followed by a default value assignment. The method caller has the option of passing a value for that parameter, or ignoring the parameter to accept the default value. This feature mimics method overloading because two calls to the same method name can pass different numbers of parameters. Each parameter that has a default value must follow the last parameter that doesn't have a default value.| Optional parameters are supported by the <strong>params</strong> keyword. Even without the <strong>params</strong> keyword, from the point of view of the caller, method overloading can provide partially similar functionality.| For more information, see Parameters and Scoping and Using Optional Parameters.|
| Single inheritance| You can derive your X++ class from another X++ class by using the <strong>extends</strong> keyword in the classDeclaration node of your class, in the AOT. No class implicitly derives directly from another class. If you want your class to directly derive from the `Object` class, you must use the <strong>extends</strong> keyword. You can specify only one class on the <strong>extends</strong> keyword.<br><br>**Caution**: When you modify an X++ base class that other classes derive from, you must recompile that base class using the Compile forward. This option ensures that the derived classes are also recompiled. To ensure the derived classes are also recompiled, right-click the base class node, and then click Add-Ins > Compile forward. The alternative of clicking Build > Compile (or pressing the F7 key) is sometimes insufficient for a base class change.<br><br>A class can implement zero to many interfaces. <br><br>An X++ table implicitly inherits from the `Common` table, and from the `xRecord` class.| C# uses the <strong>extends</strong> keyword to derive from another class. All .NET Framework classes implicitly derive from the `System.Object` class, unless they explicitly derive from another class.| |

### Keyword Comparisons

The following table lists the OOP-related keywords in X++ and C#.

|Keyword|X++|C#|Comments|
|---|---|---|---|
| <strong>abstract</strong>| | | No difference.|
| <strong>class</strong>| The modifiers <strong>public</strong> and <strong>private</strong> are ignored on class declarations. There isn't a concept of a namespace grouping of classes. There are no dots (.) in any class names.| The modifiers <strong>public</strong> and <strong>private</strong> can be used to modify class declarations. C# also has the keyword <strong>internal</strong>, which relates to how classes are grouped together in assembly files.| There isn't concept of a <strong>protected</strong> class, only <strong>protected</strong> members of a class.|
| <strong>extends</strong>| A class declaration can inherit from another class by using the <strong>extends</strong> keyword.| A colon (:) is used where the keywords <strong>extends</strong> and <strong>implements</strong> are used in X++.| |
| <strong>final</strong>| A <strong>final</strong> method can't be overridden in a derived class. A <strong>final</strong> class can't be extended.| The keyword <strong>sealed</strong> on a class means the same thing that <strong>final</strong> means on an X++ class.| |
| <strong>implements</strong>| A class declaration can implement an <strong>interface</strong> by using the <strong>implements</strong> keyword.| | |
| <strong>interface</strong>| An <strong>interface</strong> can specify methods that the class must implement.| An <strong>interface</strong> can specify methods that the class must implement.| |
| <strong>new</strong>| The <strong>new</strong> keyword is used to allocate a new instance of a class. Then the constructor is automatically called. Each class has exactly one constructor, and the constructor is named `new`. You can decide what parameters the constructor should input.| The <strong>new</strong> keyword is used to create a new instance of a class. Then the constructor is automatically called. Constructor methods themselves aren't named `new`, they have the same name as the class.<p><strong>Note:</strong> The <strong>new</strong> keyword can also be used on a method, to modify the way in which the method overrides the same method in the base class.</p> | Both X++ and C# assume a default constructor for classes that have no constructor explicitly written in their code.|
| <strong>null</strong>| | | No difference.|
| <strong>private</strong> and <strong>protected</strong>| The <strong>private</strong> and <strong>protected</strong> keywords can be used to modify the declaration of a class member.| The <strong>private</strong> and <strong>protected</strong> keywords can be used to modify the declaration of a class member.||
| <strong>public</strong>| A method that is not modified with <strong>public</strong>, <strong>protected</strong>, or <strong>private</strong> has the default access level of <strong>public</strong>.| A method that is not modified with <strong>public</strong>, <strong>protected</strong>, or <strong>private</strong> has the default access level of <strong>private</strong>.||
| <strong>static</strong>| A method can be <strong>static</strong>, but a field can't.| Both methods and fields can be <strong>static</strong>.| |
| <strong>super</strong>| The <strong>super</strong> keyword is used in a derived class to access the same method on its base class. `void method2()`<br>`{`<br>`    // Call method2 method`<br> `    // on the base class.`<br> `    super();` <br>`}`<br>| The <strong>base</strong> keyword is used in a derived class to access various methods in its base class. <br>`void method2()` <br>`{`<br> `    // Call methods on`<br> `    // the base class.`<br> `    base.method2();`<br> `    base.method3();` <br>`}`| In C#, there's special syntax for using <strong>base</strong> to call the base constructor.|
| <strong>this</strong>| For a call from one instance method to another on the same object, a qualifier for the called method is required. The keyword <strong>this</strong> is available as a qualifier for the current object.| For a call from one instance method to another on the same object, a qualifier for the called method is not required. However, the <strong>this</strong> keyword is available as a qualifier for the current object. In practice, the keyword <strong>this</strong> can be helpful by displaying IntelliSense information.| |
| `finalize`| The `Object` class contains the `finalize` method. The `finalize` method is not <strong>final</strong>, and it can be overridden. The `finalize` method appears to resemble the `System.Object.Finalize` method in C#, but in X++ the `finalize` method has no special meaning of any kind. An object is automatically removed from memory when the last reference to the object stops referencing the object. For example, this can happen when the last reference goes out of scope or is assigned another object to reference.| The methods `Finalize` and `Dispose` are common on some types of classes. The garbage collector calls the `Finalize` and `Dispose` methods when it destroys and object.| In C#, the `System.GC.Collect` method in the .NET Framework can be called to start the garbage collector. There isn't a similar function in X++ because X++ uses a deterministic garbage collector.|
| `main`| Classes that are invoked from a menu have their `main` method called by the system.| Classes that are invoked from a command line console have their `Main` method called by the system.| |

## Comparison: Classes
When you use C\# in the .NET Framework, classes are grouped into namespaces. Each namespace focuses on a functional area such as file operations or reflection. However, when you use the classes in X++, there are no visible groupings like a namespace.

### Comparison: Classes about Reflection
In X++ the `TreeNode` class provides access to the Application Object Tree (AOT). The `TreeNode` class is the center of reflection functionality in X++. The `TreeNode` class and its methods can be compared to the `System.Reflection` namespace in the .NET Framework that C\# uses.

The following table lists several classes that are available to you when you write C\# code. These are .NET Framework classes. For this table, all C\# classes are in the `System.Reflection` namespace unless otherwise specified. Each row shows the corresponding class, or class member, that is available to you when your write X++ code.

|X++|C#|Comments|
|---|---|---|
| `TreeNode` | `System .Assembly`   | Assembly is the first class to use when a C\# program must gather reflection information. Static methods on the X++ class `TreeNode` are the starting point for reflection in X++.    |
| `TreeNode` | `System .Type`       | Instance methods on `TreeNode` correspond to instance methods on `System.Type`.                |
| `TreeNode .AOTgetSource`         | `MethodInfo`         | The `AOTgetSource` method returns several pieces of information together in one string. This includes the X++ source code in the method. In contrast, `MethodInfo` has a separate member for each piece of information.                  |
| `TreeNode .AOTfirstChild` `TreeNode .AOTnextSibling` `TreeNode .AOTiterator` `AOTiterator` | MethodInfo\[\] (an array)   | In C\#, the `GetMethods` method on `System.Type` returns an array of MethodInfo objects. You can loop through the array by the common technique of incrementing an indexer. In contrast, the X++ model is to navigate the tree control of the AOT. The `TreeNode` methods of `AOTfirstChild` and `AOTnextSibling` accomplish the navigation. As an equivalent alternative, the X++ `AOTiterator` class is designed to navigate the tree control of the AOT. A class node is the parent over several method nodes. The `AOTiterator` steps through child nodes, returning each as another `TreeNode` instance. Additional resources the `TreeNode` methods that are named `AOTparent` and `AOTprevious`. |
| `TreeNode .AOTgetProperty` `TreeNode .AOTgetProperties` `TreeNode .AOTname`                | `PropertyInfo`       | In X++, the `AOTgetProperties` method returns a long string that contains name-value pairs for all the properties of the `TreeNode`. The `AOTname` method returns a string that contains only the value for the name property.                  |
| `TreeNode .AOTsave` `TreeNode .AOTinsert`                     | `System .Reflection .Emit` (namespace of classes) | The `AOTsave` method applies changes from a `TreeNode` object in your X++ code to the AOT, and the changes are persisted. For a large code sample, see TreeNode.AOTsave Method.       |

### Comparison: Classes about File IO
There are several classes that perform file input and output (IO) operations. In the .NET Framework that is used in C\#, the counterparts to these classes reside in the `System.IO` namespace.

The following table lists several .NET Framework classes for C\# that are in the `System.IO` namespace. Each row in the table shows the X++ class or method that best corresponds to the .NET Framework class.

|X++|C#|Comments|
|---|---|---|
| `BinaryIo`| `FileStream` `BinaryReader` `BinaryWriter` | X++ classes such as `BinaryIo` that extend from the abstract class `Io` serve as a stream, and they also serve as a reader and writer for that stream. In C#, the stream is a separate class from the class that has more specific read and write methods.|
| `TextBuffer`| `MemoryStream`| These classes contain an in-memory buffer, and some of the methods treat the buffer as if it were a file on the hard disk.|
| WINAPI::createDirectory WINAPI::folderExists WINAPI::removeDirectory| `Directory` `DirectoryInfo` `Path`| X++ can use static methods in the `WINAPI` class for many basic operating system functions that involve directories.|
| WINAPI::getDriveType| `DriveInfo` `DriveType`| These classes and methods are used to obtain drive related information.|
| WINAPI::copyFile WINAPI::createFile WINAPI::deleteFile WINAPI::fileExists| `File` `FileAttributes` `FileInfo`| X++ can use static methods in the `WINAPI` class for many basic operating system functions that involve files.|
| `CommaIo` `Comma7Io`| (No corresponding class.)| These X++ classes can generate files that Microsoft Excel can import. In X++ an <a href="">EPPlus</a> library reference is available for additional interaction with Excel.|
| `AsciiIo` `TextIo`| `FileStream` `TextReader` `TextWriter`| These classes use different code pages.|
| `Io`| `Stream` `StreamReader` `StreamWriter` `FileStream`| These are often used as base classes that other classes extend.|
| `CodeAccessPermission` `FileIoPermission`| `System.Security` `.CodeAccessPermission` The namespace `System.Security.Permissions` includes the following classes:<ul><li>`CodeAccessSecurityAttribute`</li><li>`FileIOPermissionAttribute`</li><li>`FileIOPermission`</li><li>`FileIOPermissionAccess`</li></ul>| The concepts and methods of `assert`, `demand`, and `revertAssert` apply to both languages. However, the `deny` and `revertDeny` methods that are available in C# aren't available in X++.|

## X++, ANSI SQL Comparison: SQL Select
In X++, the SQL **select** statement syntax differs from the American National Standards Institute (ANSI) specification.

### Single Table Select

The following table lists differences between the select statements of X++ SQL and ANSI SQL.

|Feature|X++ SQL|ANSI SQL|Comments|
|---|---|---|---|
| Table name on the <strong>from</strong> clause.| The <strong>from</strong> clause lists a record buffer instance that is declared from a table, such as from the `CustTable` table.| The <strong>from</strong> clause lists a table name, not the name of a buffer.| The record buffer has all the methods that the `xRecord`class has in X++.|
| Syntax sequence of the order by versus <strong>where</strong> clauses.| The order by clause must appear before the <strong>where</strong> clause. The order by clause must appear after the <strong>from</strong> or <strong>join</strong> clause. The group by clause must follow the same syntax positioning rules that the order by follows.| The order by clause must appear after the <strong>where</strong> clause. The <strong>where</strong> clause must appear after the <strong>from</strong> or <strong>join</strong> clause.| In both X++ and ANSI SQL, the <strong>from</strong> and <strong>join</strong> clauses must appear before the order by and <strong>where</strong> clauses.|
| Condition negation.| The exclamation mark ('!') is used for negation.| The <strong>not</strong> keyword is used for negation.| X++ doesn't support the syntax !like. Instead, you must apply the ! operator to a clause.|
| Wildcard characters for the <strong>like</strong> operator.|0 to many – Asterisk ('*')<br>Exactly 1 – Question mark ('?')|0 to many – Percent sign ('%')<br>Exactly 1 – Underbar ('_')| |
| Logical operators in the <strong>where</strong> clause.|And – &&<br>Or – \|\| |And – <strong>and</strong><br>Or – <strong>or</strong>| |

### Code Example

The following code example illustrates features in the previous table.

```xpp
static void OByWhere452Job(Args _args)
{
    // Declare the table buffer variable.
    CustTable tCustTable;
    ;
    while
    SELECT * from tCustTable
        order by tCustTable.AccountNum desc
        where (!(tCustTable.Name like '*i*i*') &amp;&amp; tCustTable.Name like 'T?e *')
    {
        info(tCustTable.AccountNum + " , " + tCustTable.Name);
    }
}
/*** InfoLog output
Message (04:02:29 pm)
4010 , The Lamp Shop
4008 , The Warehouse
4001 , The Bulb
***/
```
 
### X++ SQL Keywords

The following X++ SQL keywords are among those that are't part of ANSI SQL:
-   crosscompany
-   firstonly100
-   forceliterals
-   forcenestedloop
-   forceplaceholders
-   forceselectorder
-   validtimestate

#### Join Clause

The following table lists differences about the **join** keyword of X++ SQL and ANSI SQL.

|Feature|X++ SQL|ANSI SQL|Comments|
|---|---|---|---|
| Columns list.                    | The columns in the columns list must all come from the table listed in the **from** clause, and not from any table in a **join** clause. Columns in the list can't be qualified by their table name. | The columns in the columns list can come from any table in the **from** or **join** clauses. It helps others to maintain your code when you qualify the columns in the list with their table name. | For more information, see Select Statements on Fields.    |
| **Join** clause syntax.          | The **join** clause follows the **where** clause.           | The **join** clause follows a table in the **from** clause.                    | In the X++ code example, the **join** criteria is an equality of `SalesPoolId` values. |
| **Inner** keyword.               | The default **join** mode is inner join. There isn't an **inner** keyword.           | The default **join** mode is inner join. The **inner** keyword is available to make the code explicit.      | The **outer** keyword exists in both X++ SQL and ANSI SQL.       |
| **Left** and **right** keywords. | The **left** and **right** keywords aren't available. All joins are left.        | The **left** and **right** keywords are available to modify the **join** keyword.     | No comments.                 |
| Equality operator.               | The double equal sign operator ('`==`') is used to test for the equality of two values.  | The single equal sign operator ('`=`') is used to test for the equality of two values.                      | No comments.                 |

### Code Example

The following code example illustrates the **join** syntax in X++ SQL.

```xpp
static void OByWhere453Job(Args _args)
{
    // Declare table buffer variables.
    CustTable tCustTable;
    SalesPool tSalesPool;
    ;
    while
    SELECT
            // Not allowed to qualify by table buffer.
            // These fields must be from the table
            // in the from clause.
            AccountNum,
            Name
        from tCustTable
            order by tCustTable.AccountNum desc
            where (tCustTable.Name like 'The *')
        join tSalesPool
            where tCustTable.SalesPoolId == tSalesPool.SalesPoolId
    {
        info(tCustTable.AccountNum + " , " + tCustTable.Name);
    }
}
```
 
### Aggregate Fields

The following table lists some differences in how aggregate fields in the **select** column list are referenced between X++ SQL and ANSI SQL. Aggregate fields are those that are derived by functions such as **sum** or **avg**.

|Feature|X++ SQL|ANSI SQL|Comments|
|---|---|---|---|
| Aggregate field name alias. | The aggregate value is in the field that was aggregated. | You can use the **as** keyword to tag an aggregate field with a name alias. The alias can be referenced in subsequent code. | For more information, see Aggregate Functions: Differences Between X++ and SQL |

### Code Example

In the following code example, the call to the info method illustrates the way to reference aggregate fields (see `tPurchLine.QtyOrdered`).

```xpp
static void Null673Job(Args _args)
{
    PurchLine tPurchLine;
    ;
    while
    select
        // This aggregate field cannot be assigned an alias name.
        sum(QtyOrdered)
        from tPurchLine
    {
        info(
            // QtyOrdered is used to reference the sum.
            "QtyOrdered:  " + num2str(tPurchLine.QtyOrdered, 
            3,  // Minimum number of output characters.
            2,  // Required number of decimal places in the output.
            1,  // '.'  Separator to mark the start of the decimal places.
            2   // ','  The thousands separator.
            ));
    }
    info("End.");
}
/***
Message (12:23:08 pm)
QtyOrdered:  261,550.00
End.
***/
```

### Other Differences

The following table lists other differences of the **select** statement between the X++ SQL and ANSI SQL.

|Feature|X++ SQL|ANSI SQL|Comments|
|---|---|---|---|
|The **having** keyword.|There isn't a **having** keyword.|The **having** keyword enables you to specify filter criteria for rows that are generated by the group by clause.|No comments.|
|Null results.|In a **while** select statement, if the **where** clause filters out all rows, no special count row is returned to report that.|In a **select**, if the **where** clause filters out all rows, a special count row is returned. The count value is 0.|No comments.|
|Cursors for navigating returned rows.|The while select statement provides cursor functionality. The alternative is to use the **next** keyword.|You can declare a **cursor** for looping through the rows that are returned from a **select** statement.||
|**From** clause.|The **from** keyword is optional when no columns are listed and only one table is referenced. The following two syntax options are equivalent: <br>`select \* from tCustTable;` <br>`select tCustTable;`|A **select** statement can't read from a table unless the **from** clause is used.|In X++ SQL, the simple **select** statement fills the table buffer variable with the first row that was returned. This is illustrated by the following code fragment: <br>`select \* from tCustTable;` <br>`info(tCustTable.Name);`|



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

