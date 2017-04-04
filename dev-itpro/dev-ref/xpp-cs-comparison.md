---
# required metadata

title: X++ and C# comparison
description: This topic compares X++ and C# syntax and programming.
author: RobinARH
manager: AnnBe
ms.date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 2051
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 72424
ms.assetid: 9e0b3126-aa04-4b76-a254-bfbd3fcd6552
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# X++ and C# comparison

This topic compares X++ and C# syntax and programming.

X++, C\# Comparison: Hello World
--------------------------------

This topic compares the simplest X++ program to its counterpart in C\#.

### X++ to C\# Comparisons

The following sections describe some basic similarities and differences between X++ and C\#.
#### Similarities

The following X++ features are the same for C\#:
-   Single line (`//`) and multi-line (/\* \*/) comments.
-   `==` (equal) operator for determining whether two values are equal.
-   != (not equal to) operator for determining whether two values are not equivalent.
-   + (plus sign) operator for string concatenation.

#### Differences

The following table lists X++ features that are different in C\#.
<table>
<thead>
<tr class="header">
<th>Features</th>
<th>X++</th>
<th>C#</th>
<th>Comments</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Declarations</td>
<td>All declarations must be at the start of the method, before any X++ statements.</td>
<td>Declarations can occur anywhere in the method.</td>
<td>Both languages permit multiple variables of the same type to be listed together in one declaration. Both languages allow you to assign an initial value in the declaration statement.</td>
</tr>
<tr class="even">
<td><code>if</code> and <code>else</code> conditional statements</td>
<td>The <code>if</code> statement accepts any type of expression that it can automatically convert to a Boolean. Common examples include an <code>int</code> for which 0 means false, or an object for which null means false.</td>
<td>The <code>if</code> statement requires a Boolean expression.</td>
<td>The syntax structure regarding curly braces and parentheses is exactly the same between X++ and C#.</td>
</tr>
<tr class="odd">
<td>Literal string</td>
<td>A literal string can be delimited by either of the following:
<ul>
<li>A pair of double quotation mark (&quot;) characters.</li>
<li>A pair of single quotation mark (') characters.</li>
</ul></td>
<td>A literal string must be delimited by a pair of double quotation mark (&quot;) characters.</td>
<td>For X++, the double quotation mark characters are usually used to delimit strings. However, it is convenient delimit a string with single quotation mark characters when your string must contain a double quotation mark character.</td>
</tr>
<tr class="even">
<td><code>char</code> type</td>
<td>There is no <code>char</code> or character type in X++. You can declare a <code>str</code> of length one, but it is still a string: <code>str 1 myString = &quot;a&quot;;</code></td>
<td>There is a <code>char</code> in C#. You cannot pass a <code>char</code> as the parameter to a method that inputs a <code>string</code> parameter, although you can first explicitly convert the <code>char</code> to a <code>string</code>.</td>
<td>For more information about X++ data types, see Primitive Data Types.</td>
</tr>
<tr class="odd">
<td>Output of messages</td>
<td>X++ delivers messages to the user in the Infolog window. Common methods include the following:
<ul>
<li>The <strong>print</strong> statement:</li>
<li>static methods on the <code>Global</code> class:
<ul>
<li>Global::info</li>
<li>Global::warning</li>
<li>Global::error</li>
</ul></li>
</ul></td>
<td>For a command line C# program, messages can be delivered to the console. Common methods include the following:
<ul>
<li><code>Console.Out.WriteLine</code></li>
<li><code>Console.Error.WriteLine</code></li>
</ul></td>
<td>The <strong>print</strong> statement is not a function nor a method. Recommended use would be <code>print mystring;</code> rather than <code>print(mystring);</code>. A <code>pause;</code> statement is always useful shortly after a <strong>print</strong> statement. The print statement is convenient for testing because it automatically converts <strong>int</strong> and other primitive values to strings for display. For more information, see Print Statements. The <code>Global</code> class has special recognition in the X++ compiler. The <code>info</code> method can be called without including the Global:: prefix. For more information, see, Global::info Method.</td>
</tr>
</tbody>
</table>

### X++ and C++ Samples

This section contains two simple code samples. One sample is written in X++, and the other is in C\#. Both samples achieve the same result. The following X++ features are demonstrated:
-   `//` single line comment
-   /\* \*/ multi-line comment
-   `if` statement
-   `==` operator
-   != operator
-   + operator to concatenate strings
-   Global::info for message output, with and without the Global:: prefix
-   Global::error for message output
-   The use of single and double quotation characters (' and ") as string delimiters.

    | **Note**                                                                                               |
    |--------------------------------------------------------------------------------------------------------|
    | The best practice is to use double quotation marks for any string that might be displayed to the user. |

#### X++ Sample

This X++ code sample is in the form of a job. There is a node titled Jobs in the Application Object Tree (AOT). This sample can be added under the Jobs node, and then the job can be run.

    static void JobRs001a_HelloWorld(Args _args)
    {
        if (1 == 1) 
        {
            // These two info() calls are identical to the X++ compiler.
            // The second form is the one typically used in X++.
            Global::info(&quot;Hello World, 1.&quot;);
            info(&#39;Hello World, 2.&#39;);
        }
        if (1 != 1)
        {
            error(&quot;This message will not appear.&quot;);
        }
        else
        {
            // These two methods are also from the Global class.
            // The &#39;+&#39; operator concatenates two strings.
            warning(&quot;This is like info,&quot; + &quot; but is for warnings, 3.&quot;);
            error(&quot;This is like info,&quot; + &quot; but is for errors, 4.&quot;);
        }
    }

##### Output

Here is the actual output from the Infolog window:
    Message (09:49:48)
    Hello World, 1.
    Hello World, 2.
    This is like info, but is for warnings, 3.
    This is like info, but is for errors, 4.

#### C\# Sample

The following C\# program is a rewrite of the previous X++ program. The differences between X++ and C\# are highlighted by commenting out the X++ lines, and replacing them with the C\# syntax.

C#

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
                Console .Out .WriteLine(
                    "Hello World, Explicit .Out , 1.");
                Console .WriteLine(
                    "Hello World, Implicit default to .Out , 2.");
            }
            if (1 != 1)
            {
                Console .Error .WriteLine(
                    "This message will not appear.");
            }
            else
            {
                Console .Error .WriteLine(".Error is like .Out,"
                    + " but can be for warnings, 3.");
                Console .Error .WriteLine(".Error is like .Out,"
                    + " but is for errors, 4.");
            }
        }
    }

##### Output

Here is the actual output to the C\# console:

    `Hello World, Explicit .Out , 
    1.` `Hello World, Implicit default to .Out , 
    2.` `.Error is like .Out, but can be for warnings, 
    3.` `.Error is like .Out, but is for errors, 4.`

## X++, C\# Comparison: Loops
This topic compares the loop features between X++ and C\#.

### X++ to C\# Comparisons

####  Similarities

The following features are the same in X++ and C\#:
-   Declarations for variables of the int primitive data type. Declarations for other primitive types are almost the same, but the types might have different names.
-   while statement for loops.
-   break statement to exit a loop.
-   continue statement to jump up to the top of a loop.
-   &lt;= (less than or equal) comparison operator.

####  Differences

The following table lists X++ features that are different in C\#.
<table>
<thead>
<tr class="header">
<th>Features</th>
<th>X++</th>
<th>C#</th>
<th>Discussion</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>The <code>for</code> statement.</td>
<td>The for statement is available for loops.</td>
<td>The C# <code>for</code> statement is slightly different from <code>for</code> in X++.</td>
<td>In C# you can declare the counter integer in the <code>for</code> statement. But in X++ the counter must declared outside the <code>for</code> statement.</td>
</tr>
<tr class="even">
<td>++ increment operator.</td>
<td>An ++ increment operator is available in X++. But an <strong>int</strong> variable that is decorated with ++ can only be used as a statement, not as an expression. For example, the following lines of X++ code would not compile: int age=42; print age++; However, the following lines of X++ code would compile: int age=42; age++; print age;</td>
<td>The C# ++ operator is more flexible than in X++.</td>
<td>The following lines of code are the same in both languages:
<ul>
<li>++ myInteger;</li>
<li>myInteger++;</li>
</ul>
But the following lines of code have a different effect from each other, and are valid only in C#:
<ul>
<li>yourInt = ++myInt;</li>
<li>yourInt = myInt++;</li>
</ul></td>
</tr>
<tr class="odd">
<td>modulo operator.</td>
<td>In X++ the modulo operator is mod.</td>
<td>In C# the modulo operator is %.</td>
<td>The symbols for the modulo operator are different, but their behavior is the same in both languages.</td>
</tr>
<tr class="even">
<td>Temporarily suspend a console program that has already begun.</td>
<td>The <code>pause</code> statement.</td>
<td>In C#, a command line program can be paused by the following line of code:
<ul>
<li><code>Console.In.Read();</code></li>
</ul></td>
<td>In X++ you continue by clicking an OK button on a modal dialog box. In C# you continue by pressing any keyboard on the keyboard.</td>
</tr>
<tr class="odd">
<td>Display a message.</td>
<td>In X++, the <code>print</code> statement displays a message in the Print window.</td>
<td>In C# a message can be displayed on the console by the following line of code:
<ul>
<li><code>Console.WriteLine();</code></li>
</ul></td>
<td>The X++ <code>print</code> function is used only when you test. An X++ program that uses <code>print</code> almost always uses the <code>pause</code> statement somewhere later in the code. For production X++ code, use the Global::info Method instead of <code>print</code>. The <code>strfmt</code> function is often used together with <code>info</code>. There is no reason to use <code>pause</code> after <code>info</code>.</td>
</tr>
<tr class="even">
<td>Make a sound.</td>
<td>The beep function makes a sound that you can hear.</td>
<td>In C# a sound that you can hear is issued by the following line of code:
<ul>
<li><code>Console.Beep();</code></li>
</ul></td>
<td>The statements each produce a short tone.</td>
</tr>
</tbody>
</table>

### Print and Global::info

The X++ code samples in this topic use the `print` function to display results. In X++ you can use the `print` statement can display any primitive data type without having to call functions that convert it to a string first. This makes `print` useful in quick test situations. Generally the Global::info method is used more often than `print`. The `info` method can only display strings. Therefore the strfmt function is often used together with `info`. A limitation of `print` is that you cannot copy the contents of the Print window to the clipboard (such as with Ctrl+C). Global::info writes to the Infolog window which does support copy to the clipboard.

### Example 1: The while Loop

The **while** keyword supports looping in both X++ and C\#.
#### X++ Sample of while

    static void JobRs002a_LoopsWhile(Args _args)
    {
        int nLoops = 1;
        while (nLoops &lt;= 88)
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

##### Output

The output in the X++ Print window is as follows:

    1
    2
    3
    4

#### C\# Sample of while

C#

    using System;
    public class Pgm_CSharp
    {
        static void Main( string[] args )
        {
            new Pgm_CSharp().Rs002a_CSharp_ControlOFlowWhile();
        }
        void Rs002a_CSharp_ControlOFlowWhile()
        {
            int nLoops = 1;
            while (nLoops <= 88)
            {
                Console.Out.WriteLine( nLoops.ToString() );
                Console.Out.WriteLine( "(Press any key to resume.)" );
                // Paused until user presses a key.
                Console.In.Read();
                if ((nLoops % 4) == 0) break;
                ++ nLoops;
            }
            Console.Beep();
            Console.In.Read();
        }
    }

 

##### Output

The console output from the C\# program is as follows:

    [C:\MyDirectory\]
    &gt;&gt; Rosetta_CSharp_1.exe
    1
    (Press any key to resume.)
    2
    (Press any key to resume.)
    3
    (Press any key to resume.)
    4
    (Press any key to resume.)

### Example 2: The for Loop

The **for** keyword supports looping in both X++ and C\#.
#### X++ Sample of for

In X++ the counter variable cannot be declared as part of the **for** statement.

    static void JobRs002a_LoopsWhileFor(Args _args)
    {
        int ii; // The counter.
        for (ii=1; ii &lt; 5; ii++)
        {
            print ii;
            pause;
            // You must click the OK button to proceed
            // beyond a pause statement.
            // ii is always less than 99.
            if (ii &lt; 99)
            {
                continue;
            }
            print &quot;This message never appears.&quot;;
        }
        pause; // X++ keyword.
}

 

##### Output

The output in the X++ Print window is as follows:

    1
    2
    3
    4

#### C\# Sample of for

C#

    using System;
    public class Pgm_CSharp
    {
        static void Main( string[] args )
        {
            new Pgm_CSharp().Rs002a_CSharp_ControlOFlowFor();
        }
        void Rs002a_CSharp_ControlOFlowFor()
        {
            int nLoops = 1,
                ii;
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

 

##### Output

The console output from the C\# program is as follows:
    1
    (Press any key to resume.)
    2
    (Press any key to resume.)
    3
    (Press any key to resume.)
    4
    (Press any key to resume.)
    (Press any key to resume.)

## X++, C\# Comparison: Switch
This topic compares the **switch** statement in X++ and C\#.

### X++ to C\# Comparisons

In both X++ and C\#, the **switch** statement involves the keywords **case**, **break**, and **default**. The following table lists the differences in the **switch** statement between X++ and C\#.

| Feature                                      | X++                                                                                                                                                                                                                                                                                                                                   | C\#                                                                                                                                                                                                                                                               | Comments                                                                                                                                      |
|----------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| `break;` at the end of each case block       | In X++, when any **case** block matches the expression value on the **switch** clause, all other **case** and **default** blocks are executed until a `break;` statement is reached. No `break;` statement is ever required in an X++ **switch** statement, but `break;` statements are important in almost all practical situations. | In C\#, a `break;` statement is always needed after the statements in a **case** or **default** block. If a **case** clause has no statements between itself and the next **case** clause, a `break;` statement is not required between the two **case** clauses. | We recommend against omitting the `break;` statement after any case **block**, because it can confuse the next programmer who edits the code. |
| `break;` at the end of the **default** block | In X++ there is no effect of adding a `break;` statement at the end of the **default** block.                                                                                                                                                                                                                                         | In C\# the compiler requires a `break;` statement at the end of the **default** block.                                                                                                                                                                            | For more information, see Switch Statements.                                                                                                  |
| Only constant values on a **case** block     | In X++ you can specify either a literal value or a variable on a case block. For example, you can write case myInteger:.                                                                                                                                                                                                              | In C\# you must specify exactly one literal value on each **case** block, and no variables are allowed.                                                                                                                                                           | No comments.                                                                                                                                  |
| Multiple values on one **case** block        | In X++ you can specify multiple values on each case block. The values must be separated by a comma. For example, you can write case 4,5,myInteger:.                                                                                                                                                                                   | In C\# you must specify exactly one value on each **case** block.                                                                                                                                                                                                 | In X++ it is better to write multiple values on one **case** block than to omit the `break;` statement at the end of one or more case blocks. |

### Code Examples for switch

The following sections show comparable switch statements in X++ and C\#.
#### X++ switch Example

The X++ switch example shows the following:
-   case iTemp: and case (93-90): to show that **case** expressions are not limited to constants, as they are in C\#.
-   `//break;` to show that `break;` statements are not required in X++, although they are almost always desirable.
-   case 2, (93-90), 5: to show that multiple expressions can be listed on on **case** clause in X++.

X++

    static void GXppSwitchJob21(Args _args)  // X++ job in AOT &gt; Jobs.
    {
        int iEnum = 3;
        int iTemp = 6;
        switch (iEnum)
        {
            case 1:
            case iTemp:  // 6
                info(strFmt(&quot;iEnum is one of these values: 1,6: %1&quot;, iEnum));
                break;
            case 2, (93-90), str2Int(&quot;5&quot;):  // Equivalent to three &#39;case&#39; clauses stacked, valid in X++.
                //case 2:
                //case (93-90):  // Value after each &#39;case&#39; can be a constant, variable, or expression; in X++.
                //case str2Int(&quot;5&quot;):
                info(strFmt(&quot;iEnum is one of these values: 2,3,5: %1&quot;, iEnum));
                //break;  // Not required in X++, but usually wanted.
            case 4:
                info(strFmt(&quot;iEnum is one of these values: 4: %1&quot;, iEnum));
                break;
            default:
                info(strFmt(&quot;iEnum is an unforeseen value: %1&quot;, iEnum));
                break;
                // None of these &#39;break&#39; occurrences in this example are required for X++ compiler.
        }
        return;
    }

    /*** Copied from the Infolog:
    Message (02:32:08 pm)
    iEnum is one of these values: 2,3,5: 3
    iEnum is one of these values: 4: 3
    ***


#### C\# switch Example

The C\# switch example shows the following:
-   case 1: has a comment explaining that only constant expressions can be given on a **case** clause.
-   `break;` statements occur after the last statement in each **case** block that has statements, as is required by C\#.

C#

    using System;  // C#
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

 

## X++, C\# Comparison: String Case and Delimiters
This topic compares the treatment of strings with mixed casing in X++ and C\#. It also explains the string delimiters that are available in X++.

### X++ to C\# Comparisons

There are similarities and differences in how strings are delimited in X++ and C\#.
#### Similarities

The following X++ features are the same as in C\#:
-   The backslash (\\) is the escape operator for string delimiters.
-   The at sign (@) nullifies the escape effect of the backslash when the at sign is written immediately before the open quotation mark of a string.
-   The plus sign (+) is the string concatenation operator.

#### Differences

X++ features that are different in C\# are listed in the following table.
<table>
<thead>
<tr class="header">
<th>Feature</th>
<th>X++</th>
<th>C#</th>
<th>Comments</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><code>== </code>comparison operator</td>
<td>Insensitive: the <code>==</code> operator is insensitive to differences in string casing.</td>
<td>In C#, the <code>==</code> operator is sensitive to differences in string casing.</td>
<td>In X++ you can use the strCmp Function for case sensitive comparisons between strings.</td>
</tr>
<tr class="even">
<td>String delimiters</td>
<td>In X++ you can use either the single (') or double (<code>&quot;</code>) quotation mark as the string delimiter.
<div class="alert">
<table>
<thead>
<tr class="header">
<th><strong>Note</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Usually the best practice is to use double quotation marks for strings that might be displayed to the user. However, it is convenient to delimit a string with single quotation marks when a double quotation mark is one of the characters in the string.</td>
</tr>
</tbody>
</table>
</div></td>
<td>In C# you must use the double quotation mark as the string delimiter. This refers to the type <code>System.String</code>.</td>
<td>In X++ and C# you have the option of embedding a delimiter in a literal string and escaping it with \. In X++ you also have the alternative of embedding single quotation marks in a string that is delimited by double quotation marks (or the reverse), without having to use the escape.</td>
</tr>
<tr class="odd">
<td>Character delimiters</td>
<td>X++ has a string data type (<code>str</code>), but no character type.</td>
<td>In C# you must use the single quotation mark as the character delimiter. This refers to the type <code>System.Char</code>.</td>
<td>In the .NET Framework, a <code>System.String</code> of length one is a different data type than a <code>System.Char</code> character.</td>
</tr>
</tbody>
</table>

### Example 1: Case Sensitivity of the == Operator

The `==` and != operators are case insensitive in X++, but are case sensitive in C\#, as is illustrated by the following example.

| X++                               | C\#                                | Comments                                        |
|-----------------------------------|------------------------------------|-------------------------------------------------|
| `"HELLO" == "hello"` True in X++. | `"HELLO" == "hello"` False in C\#. | Different case comparisons between X++ and C\#. |

### Example 2: The + String Concatenation Operator

The + and += operators are used to concatenate strings in both X++ and C\#, as is shown by the examples in the following table.

| X++                                                                                            | C\#                | Comments                                                                                                                                          |
|------------------------------------------------------------------------------------------------|--------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| myString1 = "Hello" + " world"; Result is equality: `myString1 == "Hello world"`               | (Same as for X++.) | In both X++ and C\#, the behavior of the + operator depends on the data type of its operands. The operator concatenates strings, or adds numbers. |
| `mystring2 = "Hello";` myString2 += " world"; Result is equality: `myString2 == "Hello world"` | (Same as for X++.) | In both X++ and C\#, the following statements are equivalent: a = a + b; a += b;                                                                  |

### Example 3: Embedding and Escaping String Delimiters

Either single or double quotation marks can be used to delimit strings in X++. The escape character (\\) can be used to embed delimiters in a string. These are illustrated in the following table.

| X++                                                                   | C\#                                                                                                               | Comments                                                                                                                                                                                                                                                                                                                                                                        |
|-----------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| myString1 = "He said \\"yes\\"."; Result: He said "yes".              | (Same as for X++.)                                                                                                | The escape character enables you to embed string delimiters inside strings.                                                                                                                                                                                                                                                                                                     |
| myString2 = 'He said "yes".'; Result: He said "yes".                  | C\# syntax does not allow for single quotation marks to delimit strings.                                          | For strings that may be seen by the user, it is considered a best practice to use the escape character instead of the single quotation marks as shown in the example.                                                                                                                                                                                                           |
| myString3 = "He said 'yes'."; Result: He said 'yes'.                  | (Same as for X++.)                                                                                                | In X++, the single quotation marks are not treated as delimiters unless the string starts with a single quotation mark delimiter. In C\# the single quotation mark has no special meaning for strings, and it cannot be used to delimit strings. In C\# the single quotation mark is the required delimiter for literals of type `System.Char`. X++ has no character data type. |
| str myString4 = 'C'; Here the single quotation is a string delimiter. | char myChar4 = 'C'; Here the single quotation mark is a `System.Char` delimiter, not a `System.String` delimiter. | X++ has no data type that corresponds to `System.Char` in the .NET Framework. An X++ string that is limited to a length of one is still a string, not a character data type.                                                                                                                                                                                                    |

### Example 4: Single Escape Character

Examples that illustrate the single escape character in either the input or the output are shown in the following table.

| X++                                            | C\#                                                                                                                                      | Comments                                                                                                       |
|------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
| myString1 = "Red\\ shoe"; Result: Red shoe     | A literal string in C\# cannot contain the two character sequence of escape followed by a space, such as "\\ ". A compiler error occurs. | When the X++ compiler encounters the two character sequence of "\\ ", it discards the single escape character. |
| myString2 = "Red\\\\ shoe"; Result: Red\\ shoe | (Same as for X++.)                                                                                                                       | In a pair of escape characters, the first negates the special meaning of the second.                           |

## X++, C\# Comparison: Array Syntax
This topic compares array syntax between X++ and C\#.

### X++ to C\# Comparisons

There are similarities and differences in the features and syntax for arrays in X++ versus C\#.
#### Similarities

Overall there is much similarity in the syntax and treatment of arrays in X++ and C\#. However there are many differences.

#### Differences

The following table lists areas in the \[\] syntax for arrays that are different for X++ and C\#.
<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Category</th>
<th>X++</th>
<th>C#</th>
<th>Comments</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Declaration</td>
<td>An array is declared with square brackets appended to the variable name.</td>
<td>An array is declared with square brackets appended to the data type.</td>
<td>int myInts[]; // X++
<div class="alert">
<table>
<thead>
<tr class="header">
<th><strong>Note</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>An X++ array cannot be a parameter in a method.</td>
</tr>
</tbody>
</table>
</div>
int[] myInts; // C#</td>
</tr>
<tr class="even">
<td>Declaration</td>
<td>The array syntax supports only primitive data types, such as <code>int</code> and <code>str</code>. The syntax does not support classes or tables.</td>
<td>The array syntax supports primitive data types and classes.</td>
<td>In X++ you can use the <code>Array</code> Array for an array of objects.</td>
</tr>
<tr class="odd">
<td>Declaration</td>
<td>X++ is limited to single dimension arrays (myStrings[8]).</td>
<td>C# adds support for multi-dimensional arrays (myStrings[8,3]) and for jagged arrays (myStrings[8][3]).</td>
<td>In X++ you cannot have an array of arrays. However, there is advanced syntax for limiting the amount of active memory that a large array can consume, which looks like the multi-dimensional syntax in C#: int intArray[1024,16];. For more information, see Best Practice Performance Optimizations: Swapping Arrays to Disk.</td>
</tr>
<tr class="even">
<td>Declaration</td>
<td>In X++ an array is a special construct but it is not an object.</td>
<td>In C# all arrays are objects regardless of syntax variations.</td>
<td>X++ does have an Array class, but its underlying mechanism differs from arrays created by using the [] syntax. In C# all arrays use the same underlying mechanism, regardless of whether [] syntax of the <code>System.Array</code> class is used in your code.</td>
</tr>
<tr class="odd">
<td>Length</td>
<td>In X++ the length of a static sized array is determined in the declaration syntax.</td>
<td>In C# the size of an array is determined when the array object is constructed.</td>
<td>When you use the [] declaration syntax in X++, no more preparation is needed before you assign values to the array. In C# you must declare and then construct the array before assigning to it.</td>
</tr>
<tr class="even">
<td>Length</td>
<td>An X++ array can have a dynamic length that can be increased even after population has begun. This applies only when the array is declared without a number inside the []. Performance might be slowed if the length of the dynamic array is increased many times.</td>
<td>In C# the length of an array cannot be changed after the length is set.</td>
<td>In the following fragment of X++ code, only the <code>myInts</code> array is dynamic and can increase in size. int myInts[]; int myBools[5]; <code>;</code> myInts[2] = 12; myInts[3] = 13; myBools[6] = 26; //Error</td>
</tr>
<tr class="odd">
<td>Length</td>
<td>You can get the length of some arrays by using the <code>dimOf</code> function.</td>
<td>C# arrays are objects that have a <code>Length</code> property.</td>
<td>No comments.</td>
</tr>
<tr class="even">
<td>Indexing</td>
<td>Array indexing is 1 based.</td>
<td>Array indexing is 0 based.</td>
<td>mtIntArray[0] would cause an error in X++.</td>
</tr>
<tr class="odd">
<td>Constant</td>
<td>In X++ a constant value is best achieved by using the <strong>#define</strong> precompiler directive.</td>
<td>In C# you can decorate your variable declaration with the keyword <strong>const</strong>, to achieve a constant value.</td>
<td>X++ has no <strong>const</strong> keyword. C# cannot assign values to variables that are created by its #define precompiler directive.</td>
</tr>
</tbody>
</table>

### X++ and C\# Samples

The following code samples show how arrays of primitive data types are handled. The first sample is in X++, and the second sample is in C\#. Both samples achieve the same results.
#### X++ Sample

<table>
<colgroup>
<col width="100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><pre><code>static void JobRs005a_ArraySimple(Args _args)
{
    #define.macroArrayLength(3)
    // Static length.
    str sSports[#macroArrayLength];
    // Dynamic length, changeable during run time.
    int years[];
    int xx;
    Global::warning(&quot;-------- SPORTS --------&quot;);
    sSports[#macroArrayLength] = &quot;Baseball&quot;;
    for (xx=1; xx &lt;= #macroArrayLength; xx++)
    {
        info(int2str(xx) + &quot; , [&quot; + sSports[xx] + &quot;]&quot;);
    }
    warning(&quot;-------- YEARS --------&quot;);
    years[ 4] = 2008;
    years[10] = 1930;
    for (xx=1; xx &lt;= 10; xx++)
    {
        info(int2str(xx) + &quot; , &quot; + int2str(years[xx]));
    }
}</code></pre></td>
</tr>
</tbody>
</table>

 

##### Output

The output to the Infolog is as follows:
<table>
<colgroup>
<col width="100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><pre><code>Message (14:16:08)
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
10 , 1930</code></pre></td>
</tr>
</tbody>
</table>

#### C\# Sample

C#

    using System;
    public class Pgm_CSharp
    {
        static public void Main( string[] args )
        {
            new Pgm_CSharp().Rs005a_CSharp_ArraySimple();
        }
        private void Rs005a_CSharp_ArraySimple()
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
                Console.WriteLine( xx.ToString()
                    + " , [" + sSports[xx] + "]" );
            }
            Console.WriteLine("-------- YEARS --------");
            // In C# you must construct the array before assigning to it.
            years = new int[10];
            years[ 4] = 2008;
            years[10 - 1] = 1930;
            for (xx=0; xx < 10; xx++)
            {
                Console.WriteLine( xx.ToString()
                    + " , [" + years[xx].ToString() + "]" );
            }
        }
    } // EOClass

 

##### Output

The output from the C\# program to the command line console is as follows:
<table>
<colgroup>
<col width="100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><pre><code>-------- SPORTS --------
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
9 , [1930]</code></pre></td>
</tr>
</tbody>
</table>

### Additional X++ Features

The **container** is a special data type that is available in X++. It can be considered as similar to an array, or similar to a `List` collection. For more information, see Containers.

## X++, C\# Comparison: Collections
Microsoft Dynamics 365 for Operations provides the X++ `List` collection class. The .NET Framework that is used in C\# has a similar class named `System.Collections.Generic.List`.

### Comparing the Use of the List Classes

The following table compares methods on the X++ `List` class to the methods on `System.Collections.Generic.List` from the .NET Framework and C\#.
<table>
<thead>
<tr class="header">
<th>Feature</th>
<th>X++</th>
<th>C#</th>
<th>Discussion</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Declaration of collection</td>
<td><code>List myList;</code></td>
<td>List&lt;string&gt; myList;</td>
<td>The X++ declaration does not include the type of elements to be stored.</td>
</tr>
<tr class="even">
<td>Declaration of iterator</td>
<td><ul>
<li><code>ListIterator iter;</code></li>
<li><code>ListEnumerator enumer;</code></li>
</ul></td>
<td>IEnumerator&lt;string&gt; iter;</td>
<td>In X++ the <code>ListIterator</code> object has methods that can <code>insert</code> and <code>delete</code> items from the <code>List</code>. The X++ <code>ListEnumerator</code> cannot modify the contents of the <code>List</code>. In X++ the <code>ListEnumerator</code> object is always created on the same tier as the <code>List</code>. This is not always true for <code>ListIterator</code>.</td>
</tr>
<tr class="odd">
<td>Obtaining an iterator</td>
<td><ul>
<li><code>new ListIterator (myList)</code></li>
<li><code>myList.getEnumerator()</code></li>
</ul></td>
<td><code>myList.GetEnumerator()</code></td>
<td>In both X++ and C#, the List object has a getter method for an associated enumerator.</td>
</tr>
<tr class="even">
<td>Constructor</td>
<td>new List(Types::String)</td>
<td>new List&lt;string&gt;()</td>
<td>Information about the type of objects to be stored inside the <code>List</code> classes is given to the constructor in both X++ and C#.</td>
</tr>
<tr class="odd">
<td>Updating data</td>
<td><ul>
<li>Enumerator – the enumerator becomes invalid if any items in the <code>List</code> are added or removed.</li>
<li>Iterator – the iterator has methods that insert and delete items from the <code>List</code>. The iterator remains valid.</li>
</ul></td>
<td>Enumerator – the enumerator becomes invalid if any items in the <code>List</code> are added or removed.</td>
<td>Enumerators become invalid after items are added or deleted from the <code>List</code>, in both X++ and C#.</td>
</tr>
<tr class="even">
<td>Updating data</td>
<td>In X++ the <code>List</code> class has methods for adding items at the start or end of the list.</td>
<td>In C# the <code>List</code> class has methods for adding members at any position in the list. It also has methods for removing items from any position.</td>
<td>In X++ items can be removed from the <code>List</code> only by an iterator.</td>
</tr>
</tbody>
</table>

### Example 1: Declaration of a List

The following table displays code examples in X++ and C\# that declare `List` collections.

| X++                                                              | C\#                                                                                                                                                                            |
|------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `List listStrings ,list2 ,listMerged;` `ListIterator literator;` | `using System;` `using SysCollGen = System.Collections.Generic;` SysCollGen.List&lt;string&gt; listStrings ,list2 ,listMerged; SysCollGen.IEnumerator&lt;string&gt; literator; |

### Example 2: Construction of a List

In both languages, the type of items that the collection stores must be specified at the time of construction. For class types, X++ can get no more specific than whether the type is a class (Types::Class). Code examples are in the following table.

| X++                                      | C\#                                                |
|------------------------------------------|----------------------------------------------------|
| listStrings = new List( Types::String ); | listStrings = new SysCollGen.List&lt;string&gt;(); |

### Example 3: Add Items to a List

In both X++ and C\#, the collection provides a method for appending an item to the end of the collection, and for inserting an item the start. In C\# the collection provides a method for inserting at any point in the collection based on an index value. In X++ a collection iterator can insert an item at its current position. Code examples are in the following table.

| X++                                                                                           | C\#                                                                         |
|-----------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------|
| listStrings.addEnd ("String\_BB."); listStrings.addStart ("String\_AA.");                     | listStrings.Add ("String\_BB."); listStrings.Insert (0 ,"String\_AA.");     |
| // Iterator performs a midpoint // insert at current position. `listIterator.insert ("dog");` | // Index 7 determines the insertion point. `listStrings.Insert (7 ,"dog");` |

### Example 4: Iterate Through a List

Both X++ and C\# have iterator classes that you can use to step through the items in a collection. Code examples are in the following table.

| X++                                                                                                                                                                               | C\#                                                                                                                                                                                                    |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `literator = new ListIterator` ` (listStrings);` // Now the iterator points at the first item.                                                                                    | `literator = listStrings` ` .GetEnumerator();` // Now enumerator points before // the first item, not at // the first item.                                                                            |
| // The `more` method answers whether // the iterator currently points // at an item. `while (literator.more())` { ` info(any2str` ` (literator.value()));` ` literator.next();` } | // The `MoveNext` method both // advances the item pointer, and // answers whether the pointer is // pointing at an item. `while (literator.MoveNext())` { ` Console.WriteLine (literator.Current);` } |

### Example 4b: foreach in C\#

In C\# the **foreach** keyword is often used to simplify the task of iterating through a list. The following code example behaves the same as the previous C\# example. 

    foreach (string currentString in listStrings)` { ` Console.WriteLine(currentString);` }

###  Example 5: Delete the Second Item

The following table contains code examples that delete the second item from the collection. In X++ this requires an iterator. In C\# the collection itself provides the method for removing an item.

| X++                                                            | C\#                        |
|----------------------------------------------------------------|----------------------------|
| `literator.begin();` `literator.next();` `literator.delete();` | `listStrings.RemoveAt(1);` |

###  Example 6: Combine Two Collections

The following table contains code examples that combine the contents of two collections into one.

| X++                                                                                                                            | C\#                                                         |
|--------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------|
| listStrings = List::merge ` (listStrings ,listStr3);` // Or use the `.appendList` method: `listStrings.appendList (listStr3);` | `listStrings.InsertRange` ` (listStrings.Count ,listStr3);` |

## X++, C\# Comparison: Collections of Keys with Values
Microsoft Dynamics 365 for Operations provides the `Map` collection class. The `Map` collection holds pairs of values, the key value plus a data value. This resembles the .NET Framework class named `System.Collections.Generic.Dictionary`.

### X++ to C\# Comparisons

There are similarities and differences in how a key-value collection is implemented in X++ and C\#.
#### Similarities

The following list describes similarities between X++ and C\# regarding their collections that store key-value pairs:
-   Both prevent duplicate keys.
-   Both use an enumerator (or iterator) to loop through the items.
-   Both key-value collection objects are constructed with designations of the types that are stored as key and value.
-   Both can store class objects, and are not limited to storing primitives like **int**.

#### Differences

The following table describes differences between X++ and C\# regarding their collections classes that store key-value pairs:

| Feature        | X++                                                                                                                                                                      | C\#                                                                                    | Comments                                                                                                                     |
|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
| Duplicate keys | In X++ the `Map` class prevents duplicate keys by implicitly treating your call to its `insert` method as an operation to update only the value associated with the key. | In C\# the `Dictionary` class throws an exception when you try to add a duplicate key. | Duplicate keys are prevented in both languages, although by different techniques.                                            |
| Delete items   | In X++ the `delete` method on an iterator object is used to remove an unwanted key-value pair from a `Map`.                                                              | In C\# the `Dictionary` class has a `remove` method.                                   | In both languages, an enumerator is made invalid if the collection item count is modified during the life of the enumerator. |

### Example 1: Declaration of a Key-Value Collection

In both languages, the type of items that the key-value collection stores must be specified. In X++ the type is specified at time of construction. In C\# the type is specified at both the time of declaration and the time of construction. Code examples are in the following table.

| X++                                                               | C\#                                                                                                                                                                                                                     |
|-------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Map mapKeyValue;` `MapEnumerator enumer;` `MapIterator mapIter;` | `SysCollGen.Dictionary` &lt;int,string&gt; ` dictKeyValue;` `SysCollGen.IEnumerator` &lt;SysCollGen.KeyValuePair &lt;int,string&gt;&gt; enumer; `SysCollGen.KeyValuePair` &lt;int,string&gt; ` kvpCurrentKeyValuePair;` |

### Example 2: Construction of the Collection

In both languages, the type of items that the key-value collection stores specified during construction. For class types, X++ can get no more specific than whether the type is a class (Types::Class). Code examples are in the following table.

| X++                                                         | C\#                                                                 |
|-------------------------------------------------------------|---------------------------------------------------------------------|
| `mapKeyValue =` ` new Map` (Types::Integer ,Types::String); | `dictKeyValue = new` ` SysCollGen.Dictionary` &lt;int,string&gt;(); |

### Example 3: Add an Item to the Collection

There is almost no difference in how an item is added to a key-value collection, in X++ and C\#. Code examples are in the following table.

| X++                                                    | C\#                                                    |
|--------------------------------------------------------|--------------------------------------------------------|
| `mapKeyValue.insert` ` (xx ,int2str(xx)` + "\_Value"); | `dictKeyValue.Add` ` (xx ,xx.ToString()` + "\_Value"); |

### Example 4: Iterate Through a Key-Value Collection

Enumerators are used to loop through the key-value collections in both X++ and C\#. Code examples are in the following table.

| X++                                                                                                                                                                                      | C\#                                                                                                                                                                                                     |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `enumer = mapKeyValue.getEnumerator();` `while (enumer.moveNext())` { ` iCurrentKey = enumer.currentKey();` ` sCurrentValue = enumer.currentValue();` `// Display key and value here.` } | `enumer = dictKeyValue` ` .GetEnumerator();` `while (enumer.MoveNext())` { ` kvpCurrentKeyValuePair = enumer.Current;` ` // Display .Key and .Value properties` ` // of kvpCurrentKeyValuePair here.` } |

### Example 5: Update the Value Associated with a Key

The syntax is very different between the two languages for an update of the value associated to a given key. Code examples for the key 102 are in the following table.

| X++                                                                                        | C\#                                                                                                 |
|--------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
| `mapKeyValue.insert` (102 ,".insert(), Re-inserted" + " key 102 with a different value."); | dictKeyValue\[102\] = "The semi-hidden .item property" + " in C\#, Updated the value for key 102."; |

###  Example 6: Delete One Item

The syntax is very different between the two languages to delete one key-value pair from a collection, while iterating through the collection members. Code examples for the key 102 are shown below.

X++

    mapIter = new MapIterator
    (mapKeyValue);
    //mapIter.begin();
    while (mapIter.more())
    {
        iCurrentKey = mapIter.key();
        if (104 == iCurrentKey)
        {
            // mapKeyValue.remove would invalidate the iterator.
            mapIter.delete();
            break;`
        }
        mapIter.next();
    }

C#

    dictKeyValue` .Remove(104);

## X++, C\# Comparison: Exceptions
There are some similarities but many differences when we compare exception related behavior between X++ and C\#.

### X++ to C\# Comparisons

The **try**, **catch**, and **throw** keywords behave the same in X++ and C\#. But the types of exceptions thrown and caught are different for the two languages.
#### Similarities

Similarities between X++ and C\# regarding their exception features include the following:
-   Both languages have the same **try** keyword.
-   Both have the same **catch** keyword.
-   Both enable for a **catch** statement that does not specify any particular exception. Such a **catch** statement catches all exceptions that reach it.
-   Both have the same **throw** keyword.

#### Differences

Exception-related differences between X++ and C\# are described in the following table.
<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Feature</th>
<th>X++</th>
<th>C#</th>
<th>Comments</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>retry</strong></td>
<td>Jumps to the first instruction in the associated <strong>try</strong> block. For more information, see Exception Handling with try and catch Keywords.</td>
<td>The functionality of the <strong>retry</strong> keyword can be mimicked in C# code, but there is no corresponding keyword.</td>
<td>Only X++ has a <strong>retry</strong> keyword. C# has no counterpart. For more information, see X++, C# Comparison: Automated Retry After an Exception.</td>
</tr>
<tr class="even">
<td><strong>finally</strong></td>
<td>The <code>finally</code> keyword is supported to follow the <code>try</code> and <code>catch</code> keywords.</td>
<td>The <strong>finally</strong> keyword marks a block of code that follows the <strong>try</strong> and <strong>catch</strong> blocks. The finally will be executed regardless of whether any exception is thrown or caught.</td>
<td>The semantics are identical to the semantics in C#.</td>
</tr>
<tr class="odd">
<td>Specific exceptions</td>
<td>In X++ an exception is an element of the <code>Exception</code> enum, such as:
<ul>
<li><code>Error</code></li>
<li><code>Deadlock</code></li>
<li><code>CodeAccessSecurity</code></li>
</ul>
No exception can contain another.</td>
<td>In C# an exception is an instance of the <code>System.Exception</code> base class, or any class that inherits from it. An exception can be contained in the <code>InnerException</code> property of the thrown exception.</td>
<td>In X++ each thrown exception is a value of the Exception enum. For more information, see Exception Enumeration.</td>
</tr>
<tr class="even">
<td>Exception message</td>
<td>In X++ the message that is created when an exception is raised is available only in the Infolog, and the message is not directly tied to the exception.</td>
<td>In C# the message is the <code>Message</code> member of the <code>System.Exception</code> object.</td>
<td>In X++ the Global::error method is the mechanism that display exception messages in the Infolog. For more information, see Exception Handling with try and catch Keywords.</td>
</tr>
<tr class="odd">
<td>Exception conditions</td>
<td>In X++ an error occurs when you call an instance method on an object variable that has not yet had anything assigned to it. However, no exception is raised along with this error. Therefore no <code>catch</code> block can gain control even if the unassigned variable is misused in a <code>try</code> block. In the following code example, the error caused by the code <code>box4.toString();</code> does not cause control to transfer to any <code>catch</code> block: <code>DialogBox box4;</code> <code>try</code> { <code> box4.toString();</code> <code> info(&quot;toString did not error, but expected an error.&quot;);</code> } catch (Exception::Error) // No Exception value catches this. { <code> info(&quot;Invalid use of box4 gave control to catch, unexpected.&quot;);</code> }</td>
<td>In C# a <code>System.NullReferenceException</code> is raised when an uninitialized variable is treated as an object reference.</td>
<td>There might be several other differences in the conditions that raise exceptions.</td>
</tr>
<tr class="even">
<td>SQL transactions</td>
<td>In X++ when an SQL exception occurs in a <strong>ttsBegin</strong> - <strong>ttsCommit</strong> transaction, no <strong>catch</strong> statement inside the transaction block can process the exception.</td>
<td>In C# a catch block inside an SQL transaction can catch the exception.</td>
<td>For more information about X++ exceptions during SQL transactions, see the following topics:
<ul>
<li>Deadlocks</li>
<li>X++ Standards: ttsBegin and ttsCommit</li>
<li>Exception Handling with try and catch Keywords</li>
</ul></td>
</tr>
</tbody>
</table>

### X++ and C\# Samples

This section contains two code samples. One sample is written in X++, and the other is in C\#. Both samples achieve the same result. The following X++ features are demonstrated:
-   **try** keyword.
-   **catch** keyword.
-   The behavior after an Exception::Error exception occurs.

#### X++ Sample

<table>
<colgroup>
<col width="100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><pre><code>static void JobRs008a_Exceptions(Args _args)
{
    str sStrings[4];
    int iIndex = 77;
    try
    {
        info(&quot;On purpose, this uses an invalid index for this array: &quot;
            + sStrings[iIndex]);
        warning(&quot;This message does not appear in the Infolog,&quot;
            + &quot; it is unreached code.&quot;);
    }
    // Next is a catch for some of the values of
    // the X++ Exception enumeration.
    catch (Exception::CodeAccessSecurity)
    {
        info(&quot;In catch block for -- Exception::CodeAccessSecurity&quot;);
    }
    catch (Exception::Error)
    {
        info(&quot;In catch block for -- Exception::Error&quot;);
    }
    catch (Exception::Warning)
    {
        info(&quot;In catch block for -- Exception::Warning&quot;);
    }
    catch
    {
        info(&quot;This last &#39;catch&#39; is of an unspecified exception.&quot;);
    }
    //finally
    //{
    //    //Global::Warning(&quot;&#39;finally&#39; is not an X++ keyword, although it is in C#.&quot;);
    //}
    info(&quot;End of program.&quot;);
}</code></pre></td>
</tr>
</tbody>
</table>

 

##### Output

Here is the actual output from the Infolog window:
<table>
<colgroup>
<col width="100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><pre><code>Message (18:07:24)
Error executing code: Array index 77 is out of bounds.
Stack trace
(C)\Jobs\JobRs008a_Exceptions - line 8
In catch block for -- Exception::Error
End of program.</code></pre></td>
</tr>
</tbody>
</table>

#### C\# Sample

The following C\# program is a rewrite of the previous X++ program.

C#

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
                Console.WriteLine
                    ("On purpose, this uses an invalid index"
                    + " for this array: " + sStrings[77]);
                Console.Error.WriteLine
                    ("This message does not appear in the Infolog,"
                    + " it is unreached code.");
            }
            catch (NullReferenceException exc)
            {
                Console.WriteLine("(e1) In catch block for -- "
                    + exc.GetType().ToString() );
            }
            catch (IndexOutOfRangeException exc)
            {
                Console.WriteLine("(e2) In catch block for -- "
                    + exc.GetType().ToString() );
            }
            // In C#, System.Exception is the base of all
            // .NET Framework exception classes.
            // No as yet uncaught exception can get beyond
            // this next catch.
            catch (Exception exc)
            {
                Console.WriteLine
                    ("This last 'catch' is of the abstract"
                    + " base type Exception: "
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
                Console.WriteLine
                    ("'finally' is not an X++ keyword,"
                    + " although it is in C#.");
            }
            Console.WriteLine("End of program.");
        }
    } // EOClass

 

##### Output

Here is the actual output to the C\# console:
<table>
<colgroup>
<col width="100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><pre><code>(e2) In catch block for -- System.IndexOutOfRangeException
&#39;finally&#39; is not an X++ keyword, although it is in C#.
End of program.</code></pre></td>
</tr>
</tbody>
</table>

## X++, C\# Comparison: Automated Retry After an Exception
Sometimes you can write code in a catch block that fixes the cause of an exception that occurs during run time. X++ provides a **retry** keyword that can be used only inside a **catch** block. The **retry** keyword enables a program to jump back to the start of the **try** block after the problem has been corrected by code in the **catch** block. C\# does not have a **retry** keyword. However, C\# code can be written to provide equivalent behavior.

### X++ and C\# Code Samples for Retry

The following X++ sample program causes an Exception::Error to be raised. This occurs when it first tries to read an element from the `sStrings` array by using an invalid index value. When the exception is caught, corrective action is taken during run time inside the **catch** block. The retry statement then jumps back to the first statement in the **try** block. This second iteration works without encountering any exception.
<table>
<colgroup>
<col width="100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><pre><code>static void JobRs008b_ExceptionsAndRetry(Args _args)
{
    str sStrings[4];
    str sTemp;
    int iIndex = 0;
    ;
    sStrings[1] = &quot;First array element.&quot;;
    try
    {
        print(&quot;At top of try block: &quot; + int2str(iIndex));
        sTemp = sStrings[iIndex];
        print( &quot;The array element is: &quot; + sTemp );
    }
    catch (Exception::Error)
    {
        print(&quot;In catch of -- Exception::Error (will retry).&quot;
            + &quot; Entering catch.&quot;);
        ++iIndex;
        print(&quot;In catch of -- Exception::Error (will retry).
            + &quot; Leaving catch.&quot;);
        // Here is the retry statement.
        retry;
    }
    print(&quot;End of X++ retry program.&quot;);
    pause;
}</code></pre></td>
</tr>
</tbody>
</table>

 

##### Output

Here is the actual output to the Print window:
<table>
<colgroup>
<col width="100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><pre><code>At top of try block: 0
In catch of -- Exception::Error (will retry). Entering catch.
In catch of -- Exception::Error (will retry). Leaving catch.
At top of try block: 1
The array element is: First array element.
End of X++ retry program.</code></pre></td>
</tr>
</tbody>
</table>

#### C\# Sample

The following C\# sample is not a line-by-line translation from the previous X++ sample. Instead the C\# program has a different structure so that it mimics the behavior of the **retry** keyword that the X++ program relies on. The **try** and **catch** blocks are in a called method. The variables that are used in the **try** block are stored in the caller method. The caller method passes the variables as parameters that are decorated with the **ref** keyword, so that their values can be corrected inside the **catch** block of the called method. The called method captures all exceptions, and returns a **boolean** to communicate back to the caller whether a second call is required.

C#


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
                    bReturnCode = this
                        .Rs008b_CSharp_ExceptionsAndRetry_Callee
                        (ref iIndex);
                }
                else
                {
                    break;
                }
            }
            Console.WriteLine("End of C# caller method.");
        }
        private bool Rs008b_CSharp_ExceptionsAndRetry_Callee
                (ref int iIndex)
        {
            bool bReturnCode = true; // Means call this method again.
            string[] sStrings = new string[4];
            string sTemp;
            sStrings[0] = "First array element.";
            try
            {
                Console.WriteLine("At top of try block: "
                    + iIndex.ToString());
                sTemp = sStrings[iIndex];
                Console.WriteLine( "The array element is: " + sTemp );
                bReturnCode = false; // Means do not call this method again.
            }
            catch (Exception)
            {
                Console.WriteLine
                    ("In catch of -- Exception. Entering catch.");
                ++iIndex; // The 'ref' parameter in C#.
                Console.WriteLine
                    ("In catch of -- Exception. Leaving catch.");
                //retry;
                // In C# we let the caller method do the work
                // that the retry keyword does in X++.
            }
            Console.WriteLine("End of C# callee method.");
            return bReturnCode;
        }
    }

 

##### Output

Here is the actual output to the console:
<table>
<colgroup>
<col width="100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><pre><code>At top of try block: -1
In catch of -- Exception. Entering catch.
In catch of -- Exception. Leaving catch.
End of C# callee method.
At top of try block: 0
The array element is: First array element.
End of C# callee method.
End of C# caller method.</code></pre></td>
</tr>
</tbody>
</table>

## X++, C\# Comparison: Operators
This topic compares the operators between X++ and C\#.

### Assignment Operators

The following table displays the differences between the assignment operators in X++ and C\#.
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>X++ and C#</th>
<th>Differences</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><code>=</code></td>
<td>In X++ this operator causes an implicit conversion whenever a loss of precision might occur, such for an assignment from an <strong>int64</strong> to an <strong>int</strong>. But in C# the assignment causes a compile error.</td>
</tr>
<tr class="even">
<td>+= and -=</td>
<td>The only difference is that in C# these operators are also used in delegate manipulation.</td>
</tr>
<tr class="odd">
<td>++ and --</td>
<td>These are the increment and decrement operators in both languages. The following line is identical in both languages:
<ul>
<li>++myInteger;</li>
</ul>
But in X++ these two operators are for statements, not for expressions. Therefore the following lines generate compile errors in X++:
<ul>
<li>myStr = int2str(++myInteger);</li>
<li>myIntA = myIntBB++;</li>
</ul></td>
</tr>
</tbody>
</table>

### Arithmetic Operators

The following table lists the arithmetic operators.
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>X++ and C#</th>
<th>Differences</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>*</td>
<td>As the multiplication operator, there are no differences.
<div class="alert">
<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Note</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>The asterisk is also used in the SQL statements that are part of the X++ language. In these SQL statements the asterisk can also be one of the following:
<ul>
<li>A wildcard indicating that all the columns should be returned.</li>
<li>A wildcard for characters in a string that is used on a <strong>like</strong> clause.</li>
</ul>
For more information, see Relational Operators.</td>
</tr>
</tbody>
</table>
</div></td>
</tr>
<tr class="even">
<td><code>/</code></td>
<td>The division operator is the same in X++ and C#.</td>
</tr>
<tr class="odd">
<td><code>MOD</code></td>
<td>For modulo operations, the only difference is that the % symbol is used in C#.</td>
</tr>
<tr class="even">
<td>+</td>
<td>The addition operator is the same in X++ and C#. The plus sign is also used for string concatenation. This operator adds numbers and concatenates strings in both languages.</td>
</tr>
<tr class="odd">
<td>-</td>
<td>The subtraction operator is the same in X++ and C#.</td>
</tr>
</tbody>
</table>

### Bitwise Operators

The following table compares the bitwise operators between X++ and C\#.

| X++ and C\# | Differences                                          |
|-------------|------------------------------------------------------|
| &lt;&lt;    | The left shift operator is the same in X++ and C\#.  |
| &gt;&gt;    | The right shift operator is the same in X++ and C\#. |
| ~           | The bitwise NOT operator is the same in X++ and C\#. |
| &           | The binary AND operator is the same in X++ and C\#.  |
| ^           | The binary XOR operator is the same in X++ and C\#.  |
| |           | The binary OR operator is the same in X++ and C\#.   |

### Relational Operators

The following relational operators are the same in X++ and C\#:
-   `==`
-   &gt;=
-   &lt;=
-   &gt;
-   &lt;
-   !=
-   &&
-   ||
-   !
-   ? :

## X++, C\# Comparison: Event
There are some differences in how X++ and C\# implement the event design pattern. For more information, see Event Terminology and Keywords.

### Comparison of Events between X++ and C\#

There are differences in the way delegates are used for events in X++ versus C\#.
<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Item</th>
<th>X++</th>
<th>C#</th>
<th>Comment</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>delegate</strong></td>
<td>In X++, a delegate can be declared only as a member on a class. A delegate cannot be a member on a table. All delegates are instance members of their class, not <strong>static</strong> members. No access modifier can be used on a delegate declaration, because all delegates are <strong>protected</strong> members. Therefore, the event can be raised only by code within the same class where the delegate is a member. However, the one exception to the private nature of a delegate is that code outside their class can operate on the delegates by using the += and -= operators.</td>
<td>In C#, each <strong>delegate</strong> is a type, just as every <strong>class</strong> is a type. A delegate is declared independently of any class. Without the <strong>event</strong> keyword, you can have a delegate as a parameter type on a method, just as you can have a class as a parameter type. You can construct an instance of a delegate to pass in for the parameter value.</td>
<td>In X++, each class is a type, but no delegate is a type. You cannot construct an instance of a delegate. No delegate can be a parameter for a method. But you can create a class that has a delegate member, and you can pass instances of the class as parameter values. For more information, see X++ Keywords.</td>
</tr>
<tr class="even">
<td><strong>event</strong></td>
<td>In X++ code, an event is one of the following:
<ul>
<li>An explicit call to a delegate.</li>
<li>The start or end of a method.</li>
</ul>
There is no <strong>event</strong> keyword in X++.</td>
<td>In C#, the <strong>event</strong> keyword is used to declare a <strong>delegate</strong> type as a member of a class. The effect of the <strong>event</strong> keyword is to make the delegate <strong>protected</strong>, yet still accessible for the += and -= operators. You can subscribe event handler methods to an <strong>event</strong> by using the += operator. A <strong>delegate</strong> can be useful without the <strong>event</strong> keyword, as a technique for passing a function pointer as a parameter into a method.</td>
<td>The automatic events that occur before the start of a method, and after the end of a method, can be subscribed to only by using the AOT.</td>
</tr>
<tr class="odd">
<td>+= and -= operators</td>
<td>In X++, you use the += operator to subscribe methods to a <strong>delegate</strong>. The -= operator unsubscribes a method from a delegate.</td>
<td>In C#, you use the += operator to subscribe methods to an <strong>event</strong>, or to a <strong>delegate</strong> that is not used with the <strong>event</strong> keyword.</td>
<td>The delegate contains a reference to all the objects that have methods subscribed to the delegate. Those objects are not eligible for garbage collection while delegate holds those references.</td>
</tr>
<tr class="even">
<td><code>eventHandler</code></td>
<td>In X++, the <strong>eventHandler</strong> keyword is required when you use either the += or -= operator to subscribe or unsubscribe a method from a delegate.</td>
<td><code>System.EventHandler</code> is a delegate type in the .NET Framework.</td>
<td>This term is used differently in X++ than it is in C# or the .NET Framework. For more information, see X++ Keywords.</td>
</tr>
</tbody>
</table>

### X++ and C\# Code Examples

This section contains an X++ code example for the event design pattern. It also contains a C\# code sample for the same design pattern.
#### X++ Example

The important things to notice in the X++ example are the following:

-   The `XppClass` has a delegate member that is named `myDelegate`. **Note**: The AOT contains a node for the delegate. The node is located at AOT &gt; Classes &gt; XppClass &gt; myDelegate. Several event handler nodes can be located under the myDelegate node. Event handlers that are represented by nodes in the AOT cannot be removed by the -= operator during run time. 
-   The {} braces at the end of the delegate declaration are required, but they cannot have any code in them.
-   The `XppClass` has two methods whose parameter signatures are compatible with the delegate. One method is static.
-   The two compatible methods are added to the delegate with the += operator and the **eventHandler** keyword. These statements do not call the event handler methods, the statements only add the methods to the delegate.
-   The event is raised by one call to the delegate.
-   The parameter value that passed in to the delegate is received by each event handler method.
-   The short X++ job at the top of the example starts the test.


X++

    // Simple job to start the delegate event test.
    static void DelegateEventTestJob()
    {
        XppClass::runTheTest(&quot;The information from the X++ job.&quot;);
    }
    // The X++ class that contains the delegate and the event handlers.
    class XppClass
    {
        delegate void myDelegate(str _information)
        {
        }
        public void myEventSubscriberMethod2(str _information)
        {
            info(&quot;X++, hello from instance event handler 2: &quot; + _information);
        }
        static public void myEventSubscriberMethod3(str _information)
        {
            info(&quot;X++, hello from static event handler 3: &quot; + _information);
        }
        static public void runTheTest(str _stringFromJob)
        {
            XppClass myXppClass = new XppClass();
            // Subscribe two event handler methods to the delegate.
            myXppClass.myDelegate += eventHandler
                    (myXppClass.myEventSubscriberMethod2);
            myXppClass.myDelegate += eventHandler
                    (XppClass::myEventSubscriberMethod3);
            // Raise the event by calling the delegate one time,
            // which calls all the subscribed event handler methods.
            myXppClass.myDelegate(_stringFromJob);
        }
    }
 

The output from the previous X++ job is as follows:

    X++, hello from static event handler 
    3: The information from the X++ job. X++, hello from instance event handler 
    2: The information from the X++ job.

#### C\# Sample

This section contains a C\# code sample for the event design pattern of the previous X++ sample.

C#


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
            myCsClass.MyEvent += new MyDelegate
                    (myCsClass.MyEventSubscriberMethod2);
            myCsClass.MyEvent += new MyDelegate
                    (CsClass.MyEventSubscriberMethod3);
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

 

The output from the previous C\# sample is as follows:

    CsClass.exe C#, hello from instance event handler 
    2: The information from the C\# Main. C\#, hello from static event handler 
    3: The information from the C\# Main. |

### Events and the AOT

Microsoft Dynamics 365 for Operations has other event systems that apply only to items in the AOT. For more information, see Event Handler Nodes in the AOT.

## X++, C\# Comparison: Precompiler Directives
X++ and C\# share some keywords for their precompiler directive syntax, but the meanings are not always the same.

### X++ to C\# Comparisons

The following sections describe the similarities and differences between the precompiler directives used in X++ and C\#.
#### Similarities

The X++ and C\# compilers recognize many of the same keywords. In most cases, the keywords mean the same for both language compilers.

#### Differences

A fundamental difference between the precompiler directives in X++ versus C\# is the \#define keyword that both language precompilers recognize. Unlike C\#, in X++ the \#define directive requires a dot in its syntax. In X++, parentheses can be used to give the defined symbol a value. These differences are shown in the following examples:
-   In X++: \#define.InitialYear(2003)
-   In C\#: \#define InitialYear

A minor difference is that in C\# there can be spaces and tab characters between the \# character and the directive keyword, such as \# define Testing.

### Comparison Tables

The following tables compare the details of precompiler directives between X++ and C\#.
#### Identical Keywords

The following table lists precompiler directives that are similar in X++ and C\#.

| Keyword  | X++                                                                                                           | C\#                                                                                                                                                                                                                                            | Comments                                                                                                                                                                                                     |
|----------|---------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| \#define | In X++, a precompiler variable name can be defined, and a value can be given to that variable.                | In C\#, a precompiler variable name can be defined, but no value can be given to that variable. Also, any \#define in C\# must occur at the top of the file, and cannot occur after any code such as a using statement or a class declaration. | The C\# compiler can input a command line parameter of `/define` to define a precompiler variable name without defining the variable in any C\# code file. The X++ compiler has no counterpart to `/define`. |
| \#if     | In X++, \#if can determine whether a precompiler variable exists, and whether the variable has a given value. | In C\#, \#if can only determine whether a precompiler variable exists. It cannot test for any value because no value can be assigned.                                                                                                          |                                                                                                                                                                                                              |
| \#endif  | In X++, \#endif marks the end of an \#if block. It also ends an \#ifnot block.                                | In C\#, \#endif marks the end of an \#if block, regardless of whether the block includes a \#else.                                                                                                                                             |                                                                                                                                                                                                              |

#### Different Keywords with the Same Processing Result

The following table lists precompiler directives that are named differently in X++ and C\#, but that give the same results when processed.

| X++                         | C\#              | Comments                                                                                                                                                                                                                                                                                                                                        |
|-----------------------------|------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| \#ifnot                     | \#if \#else      | There is no \#else directive in X++, but the \#ifnot provides similar functionality. In X++, \#ifnot can determine whether a precompiler variable exists, and whether the variable does not have a specific given value. In C\#, \#if can determine whether a precompiler variable exists when the ‘!’ symbol is prefixed to the variable name. |
| `//BP Deviation documented` | \#pragma warning | These X++ and C\# entries are not equivalent, but there is a partial similarity. Both suppress compiler warning messages.                                                                                                                                                                                                                       |
| \#macrolib                  | .HPP file in C++ | There is a partial similarity between the X++ directive \#macrolib versus an .HPP file in C++. Both can contain several \#define statements.                                                                                                                                                                                                    |

#### Precompiler Directives Exclusive to X++

The following table lists X++ precompiler directives that have no direct counterpart in C\#.

| X++                  | Comments                                                                                                                                                                                                                                                                                                                             |
|----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| \#linenumber         | The \#linenumber directive is for obtaining the line number, so that it can be output to the Infolog. The C\# directive \#line is different because its purpose is for setting the line number.                                                                                                                                      |
| \#defdec \#definc    |                                                                                                                                                                                                                                                                                                                                      |
| \#globaldefine       | In X++, there is a small difference between \#globaldefine versus \#define. The difference is that \#globaldefine never overwrites a current nonnull value that was assigned to a precompiler variable by \#define. C\# has nothing similar to this difference, because in C\#, a precompiler variable name cannot be given a value. |
| \#localmacro \#macro | In X++, \#localmacro enables you to assign a multiline value to a precompiler variable. \#macro is a synonym, but \#localmacro is recommended. In C\#, the \#define directive has part of this functionality, but it cannot assign a value to a precompiler variable.                                                                |
| \#globalmacro        | In X++, \#globalmacro is almost the same as the preferred \#localmacro.                                                                                                                                                                                                                                                              |

## X++, C\# Comparison: Object Oriented Programming
The object oriented programming (OOP) principles of X++ differ from C\#.

### Conceptual Comparisons

The following table compares the implementation of OOP principles between X++ and C\#.
<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Feature</th>
<th>X++</th>
<th>C#</th>
<th>Comments</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Casting</td>
<td>The X++ language has the keywords <strong>is</strong> and <strong>as</strong>, which are used to make downcasts safe and explicit.
<div class="alert">
<table>
<thead>
<tr class="header">
<th><strong>Tip</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>X++ does not require the use of the <strong>as</strong> keyword when you downcast a base class variable to a derived class variable. However, we recommend that all downcast statements use the <strong>as</strong> keyword.</td>
</tr>
</tbody>
</table>
</div></td>
<td>An object can be cast either up or down the inheritance path. Downcasts require the <strong>as</strong> keyword.</td>
<td>For more information about the X++ keywords <strong>is</strong> and <strong>as</strong>, see Expression Operators: Is and As for Inheritance.</td>
</tr>
<tr class="even">
<td>Local functions</td>
<td>A method can contain a declaration and code body for zero or more local functions. Only that method can have calls to the local function.</td>
<td>C# 3.0 supports lambda expressions, which have some similarity to anonymous functions and local functions. Lambda expressions are often used with delegates.</td>
<td>For more information about local functions in X++, see Local Functions.</td>
</tr>
<tr class="odd">
<td>Method overloading</td>
<td>Method overloading is not supported. A method name can occur only one time per class.</td>
<td>Method overloading is supported. A method name can occur multiple times in one class, with different parameter signatures in each case.</td>
<td>X++ does support optional parameters on methods. Optional parameters can partially mimic method overloading. For more information, see the row for optional parameters in this table.</td>
</tr>
<tr class="even">
<td>Method overriding</td>
<td>Method overriding is supported. A derived class can have a method by the same name as in the base class, as long as the parameter signature is the same in both cases. The only exception is that the overriding method can add a default value to a parameter.</td>
<td>Method overriding is supported. The <strong>virtual</strong> keyword must be applied to a method before the method can be overridden in a derived class.</td>
<td>The concept of overriding a method includes the method name, its parameter signature, and its return type. The concept of method overriding does not apply if the base method and the overriding method differ in any of these aspects.</td>
</tr>
<tr class="odd">
<td>Optional parameters</td>
<td>A parameter declaration can be followed by a default value assignment. The method caller has the option of passing a value for that parameter, or ignoring the parameter to accept the default value. This feature mimics method overloading because two calls to the same method name can pass different numbers of parameters. Each parameter that has a default value must follow the last parameter that does not have a default value.</td>
<td>Optional parameters are supported by the <strong>params</strong> keyword. Even without the <strong>params</strong> keyword, from the point of view of the caller, method overloading can provide partially similar functionality.</td>
<td>For more information, see Parameters and Scoping and Using Optional Parameters.</td>
</tr>
<tr class="even">
<td>Single inheritance</td>
<td>You can derive your X++ class from another X++ class by using the <strong>extends</strong> keyword in the classDeclaration node of your class, in the AOT. No class implicitly derives directly from another class. If you want your class to directly derive from the <code>Object</code> class, you must use the <strong>extends</strong> keyword. You can specify only one class on the <strong>extends</strong> keyword.
<div class="alert">
<table>
<thead>
<tr class="header">
<th><strong>Caution</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>When you modify an X++ base class that other classes derive from, you must recompile that base class using the Compile forward. This option ensures that the derived classes are also recompiled. To ensure the derived classes are also recompiled, right-click the base class node, and then click Add-Ins &gt; Compile forward. The alternative of clicking Build &gt; Compile (or pressing the F7 key) is sometimes insufficientfor a base class change.</td>
</tr>
</tbody>
</table>
</div>
A class can implement zero to many interfaces. An X++ table implicitly inherits from the <code>Common</code> table, and from the <code>xRecord</code> class.</td>
<td>C# uses the <strong>extends</strong> keyword to derive from another class. All .NET Framework classes implicitly derive from the <code>System.Object</code> class, unless they explicitly derive from another class.</td>
<td>For more information about X++ interfaces, see Interfaces Overview.</td>
</tr>
</tbody>
</table>

### Keyword Comparisons

The following table lists the OOP-related keywords in X++. The usage of each keyword is compared between X++ and C\#.
<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Keyword</th>
<th>X++</th>
<th>C#</th>
<th>Comments</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>abstract</strong></td>
<td></td>
<td></td>
<td>No difference.</td>
</tr>
<tr class="even">
<td><strong>class</strong></td>
<td>The modifiers <strong>public</strong> and <strong>private</strong> are ignored on class declarations. There is no concept of a namespace grouping of classes. There are no dots (.) in any class names.</td>
<td>The modifiers <strong>public</strong> and <strong>private</strong> can be used to modify class declarations. C# also has the keyword <strong>internal</strong>, which relates to how classes are grouped together in assembly files.</td>
<td>There is no concept of a <strong>protected</strong> class, only <strong>protected</strong> members of a class.</td>
</tr>
<tr class="odd">
<td><strong>extends</strong></td>
<td>A class declaration can inherit from another class by using the <strong>extends</strong> keyword.</td>
<td>A colon (:) is used where the keywords <strong>extends</strong> and <strong>implements</strong> are used in X++.</td>
<td></td>
</tr>
<tr class="even">
<td><strong>final</strong></td>
<td>A <strong>final</strong> method cannot be overridden in a derived class. A <strong>final</strong> class cannot be extended.</td>
<td>The keyword <strong>sealed</strong> on a class means the same thing that <strong>final</strong> means on an X++ class.</td>
<td></td>
</tr>
<tr class="odd">
<td><strong>implements</strong></td>
<td>A class declaration can implement an <strong>interface</strong> by using the <strong>implements</strong> keyword.</td>
<td>(See <strong>extends</strong>.)</td>
<td></td>
</tr>
<tr class="even">
<td><strong>interface</strong></td>
<td>An <strong>interface</strong> can specify methods that the class must implement.</td>
<td>An <strong>interface</strong> can specify methods that the class must implement.</td>
<td></td>
</tr>
<tr class="odd">
<td><strong>new</strong></td>
<td>The <strong>new</strong> keyword is used to allocate a new instance of a class. Then the constructor is automatically called. Each class has exactly one constructor, and the constructor is named <code>new</code>. You can decide what parameters the constructor should input.</td>
<td>The <strong>new</strong> keyword is used to create a new instance of a class. Then the constructor is automatically called. Constructor methods themselves are not named <code>new</code>, they have the same name as the class.
<div class="alert">
<table>
<thead>
<tr class="header">
<th><strong>Note</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>The <strong>new</strong> keyword can also be used on a method, to modify the way in which the method overrides the same method in the base class.</td>
</tr>
</tbody>
</table>
</div></td>
<td>Both X++ and C# assume a default constructor for classes that have no constructor explicitly written in their code.</td>
</tr>
<tr class="even">
<td><strong>null</strong></td>
<td></td>
<td></td>
<td>No difference.</td>
</tr>
<tr class="odd">
<td><strong>private</strong> and <strong>protected</strong></td>
<td>The <strong>private</strong> and <strong>protected</strong> keywords can be used to modify the declaration of a class member.</td>
<td>The <strong>private</strong> and <strong>protected</strong> keywords can be used to modify the declaration of a class member.</td>
<td>For more information, see Method Access Control.</td>
</tr>
<tr class="even">
<td><strong>public</strong></td>
<td>A method that is not modified with <strong>public</strong>, <strong>protected</strong>, or <strong>private</strong> has the default access level of <strong>public</strong>.</td>
<td>A method that is not modified with <strong>public</strong>, <strong>protected</strong>, or <strong>private</strong> has the default access level of <strong>private</strong>.</td>
<td>(For more information, see <strong>private</strong>.)</td>
</tr>
<tr class="odd">
<td><strong>static</strong></td>
<td>A method can be <strong>static</strong>, but a field cannot.</td>
<td>Both methods and fields can be <strong>static</strong>.</td>
<td></td>
</tr>
<tr class="even">
<td><strong>super</strong></td>
<td>The <strong>super</strong> keyword is used in a derived class to access the same method on its base class. <code>void method2()</code> { <code> ;</code> <code> // Call method2 method</code> <code> // on the base class.</code> <code> super();</code> }</td>
<td>The <strong>base</strong> keyword is used in a derived class to access various methods in its base class. <code>void method2()</code> { <code> // Call methods on</code> <code> // the base class.</code> <code> base.method2();</code> <code> base.method3();</code> }</td>
<td>In C#, there is special syntax for using <strong>base</strong> to call the base constructor.</td>
</tr>
<tr class="odd">
<td><strong>this</strong></td>
<td>For a call from one instance method to another on the same object, a qualifier for the called method is required. The keyword <strong>this</strong> is available as a qualifier for the current object.</td>
<td>For a call from one instance method to another on the same object, a qualifier for the called method is not required. However, the <strong>this</strong> keyword is available as a qualifier for the current object. In practice, the keyword <strong>this</strong> can be helpful by displaying IntelliSense information.</td>
<td></td>
</tr>
<tr class="even">
<td><code>finalize</code></td>
<td>The <code>Object</code> class contains the <code>finalize</code> method. The <code>finalize</code> method is not <strong>final</strong>, and it can be overridden. The <code>finalize</code> method appears to resemble the <code>System.Object.Finalize</code> method in C#, but in X++ the <code>finalize</code> method has no special meaning of any kind. An object is automatically removed from memory when the last reference to the object stops referencing the object. For example, this can happen when the last reference goes out of scope or is assigned another object to reference.</td>
<td>The methods <code>Finalize</code> and <code>Dispose</code> are common on some types of classes. The garbage collector calls the <code>Finalize</code> and <code>Dispose</code> methods when it destroys and object.</td>
<td>In C#, the <code>System.GC.Collect</code> method in the .NET Framework can be called to start the garbage collector. There is no similar function in X++ because X++ uses a deterministic garbage collector.</td>
</tr>
<tr class="odd">
<td><code>main</code></td>
<td>Classes that are invoked from a menu have their <code>main</code> method called by the system.</td>
<td>Classes that are invoked from a command line console have their <code>Main</code> method called by the system.</td>
<td></td>
</tr>
</tbody>
</table>

## X++, C\# Comparison: Classes
When you use C\# in the .NET Framework, classes are grouped into namespaces. Each namespace focuses on a functional area such as file operations or reflection. However, when you use the classes in X++, there are no visible groupings like a namespace.

X++, C\# Comparison: Classes about Reflection  

X++, C\# Comparison: Classes about File IO  

## X++, C\# Comparison: Classes about Reflection
In X++ the `TreeNode` class provides access to the Application Object Tree (AOT). The `TreeNode` class is the center of reflection functionality in X++. The `TreeNode` class and its methods can be compared to the `System.Reflection` namespace in the .NET Framework that C\# uses.

### Table of Class Comparisons

The following table lists several classes that are available to you when you write C\# code. These are .NET Framework classes. For this table, all C\# classes are in the `System.Reflection` namespace unless otherwise specified. Each row shows the corresponding class, or class member, that is available to you when your write X++ code.

| X++                                                                                        | C\#                                               | Comments                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|--------------------------------------------------------------------------------------------|---------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `TreeNode`                                                                                 | `System .Assembly`                                | Assembly is the first class to use when a C\# program must gather reflection information. Static methods on the X++ class `TreeNode` are the starting point for reflection in X++.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `TreeNode`                                                                                 | `System .Type`                                    | Instance methods on `TreeNode` correspond to instance methods on `System.Type`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `TreeNode .AOTgetSource`                                                                   | `MethodInfo`                                      | The `AOTgetSource` method returns several pieces of information together in one string. This includes the X++ source code in the method. In contrast, `MethodInfo` has a separate member for each piece of information.                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `TreeNode .AOTfirstChild` `TreeNode .AOTnextSibling` `TreeNode .AOTiterator` `AOTiterator` | MethodInfo\[\] (an array)                         | In C\#, the `GetMethods` method on `System.Type` returns an array of MethodInfo objects. You can loop through the array by the common technique of incrementing an indexer. In contrast, the X++ model is to navigate the tree control of the AOT. The `TreeNode` methods of `AOTfirstChild` and `AOTnextSibling` accomplish the navigation. As an equivalent alternative, the X++ `AOTiterator` class is designed to navigate the tree control of the AOT. A class node is the parent over several method nodes. The `AOTiterator` steps through child nodes, returning each as another `TreeNode` instance. See also the `TreeNode` methods that are named `AOTparent` and `AOTprevious`. |
| `TreeNode .AOTgetProperty` `TreeNode .AOTgetProperties` `TreeNode .AOTname`                | `PropertyInfo`                                    | In X++, the `AOTgetProperties` method returns a long string that contains name-value pairs for all the properties of the `TreeNode`. The `AOTname` method returns a string that contains only the value for the name property.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `TreeNode .AOTsave` `TreeNode .AOTinsert`                                                  | `System .Reflection .Emit` (namespace of classes) | The `AOTsave` method applies changes from a `TreeNode` object in your X++ code to the AOT, and the changes are persisted. For a large code sample, see TreeNode.AOTsave Method.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |

## X++, C\# Comparison: Classes about File IO
There are several classes that perform file input and output (IO) operations. In the .NET Framework that is used in C\#, the counterparts to these classes reside in the `System.IO` namespace.

### Table of Class Comparisons

The following table lists several .NET Framework classes for C\# that are in the `System.IO` namespace. Each row in the table shows the X++ class or method that best corresponds to the .NET Framework class.
<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>X++</th>
<th>C#</th>
<th>Comments</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><code>BinaryIo</code></td>
<td><code>FileStream</code> <code>BinaryReader</code> <code>BinaryWriter</code></td>
<td>X++ classes such as <code>BinaryIo</code> that extend from the abstract class <code>Io</code> serve as a stream, and they also serve as a reader and writer for that stream. In C# the stream is a separate class the from the class that has the more specific read and write methods.</td>
</tr>
<tr class="even">
<td><code>TextBuffer</code></td>
<td><code>MemoryStream</code></td>
<td>These classes contain an in-memory buffer, and some of the methods treat the buffer as if it were a file on the hard disk.</td>
</tr>
<tr class="odd">
<td>WINAPI::createDirectory WINAPI::folderExists WINAPI::removeDirectory</td>
<td><code>Directory</code> <code>DirectoryInfo</code> <code>Path</code></td>
<td>X++ can use static methods in the <code>WINAPI</code> class for many basic operating system functions that involve directories.</td>
</tr>
<tr class="even">
<td>WINAPI::getDriveType</td>
<td><code>DriveInfo</code> <code>DriveType</code></td>
<td>These classes and methods are used to obtain drive related information.</td>
</tr>
<tr class="odd">
<td>WINAPI::copyFile WINAPI::createFile WINAPI::deleteFile WINAPI::fileExists</td>
<td><code>File</code> <code>FileAttributes</code> <code>FileInfo</code></td>
<td>X++ can use static methods in the <code>WINAPI</code> class for many basic operating system functions that involve files.</td>
</tr>
<tr class="even">
<td><code>CommaIo</code> <code>Comma7Io</code></td>
<td>(No corresponding class.)</td>
<td>These X++ classes can generate files that Microsoft Excel can import. In X++ an <a href="http://epplus.codeplex.com/">EPPlus</a> library reference is available for additional interaction with Excel.</td>
</tr>
<tr class="odd">
<td><code>AsciiIo</code> <code>TextIo</code></td>
<td><code>FileStream</code> <code>TextReader</code> <code>TextWriter</code></td>
<td>These classes use different code pages.</td>
</tr>
<tr class="even">
<td><code>Io</code></td>
<td><code>Stream</code> <code>StreamReader</code> <code>StreamWriter</code> <code>FileStream</code></td>
<td>These are often used as base classes that other classes extend.</td>
</tr>
<tr class="odd">
<td><code>CodeAccessPermission</code> <code>FileIoPermission</code></td>
<td><code>System.Security</code> <code>.CodeAccessPermission</code> The namespace <code>System.Security.Permissions</code> includes the following classes:
<ul>
<li><code>CodeAccessSecurityAttribute</code></li>
<li><code>FileIOPermissionAttribute</code></li>
<li><code>FileIOPermission</code></li>
<li><code>FileIOPermissionAccess</code></li>
</ul></td>
<td>The concepts and methods of <code>assert</code>, <code>demand</code>, and <code>revertAssert</code> apply to both languages. However, the <code>deny</code> and <code>revertDeny</code> methods that are available in C# are not available in X++.</td>
</tr>
</tbody>
</table>

## X++, ANSI SQL Comparison: SQL Select
In X++, the SQL **select** statement syntax differs from the American National Standards Institute (ANSI) specification.

### Single Table Select

The following table lists differences between the select statements of X++ SQL and ANSI SQL.
<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Feature</th>
<th>X++ SQL</th>
<th>ANSI SQL</th>
<th>Comments</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Table name on the <strong>from</strong> clause.</td>
<td>The <strong>from</strong> clause lists a record buffer instance that is declared from a table, such as from the <code>CustTable</code> table.</td>
<td>The <strong>from</strong> clause lists a table name, not the name of a buffer.</td>
<td>The record buffer has all the methods that the <code>xRecord</code>class has in X++.</td>
</tr>
<tr class="even">
<td>Syntax sequence of the order by versus <strong>where</strong> clauses.</td>
<td>The order by clause must appear before the <strong>where</strong> clause. The order by clause must appear after the <strong>from</strong> or <strong>join</strong> clause. The group by clause must follow the same syntax positioning rules that the order by follows.</td>
<td>The order by clause must appear after the <strong>where</strong> clause. The <strong>where</strong> clause must appear after the <strong>from</strong> or <strong>join</strong> clause.</td>
<td>In both X++ and ANSI SQL, the <strong>from</strong> and <strong>join</strong> clauses must appear before the order by and <strong>where</strong> clauses.</td>
</tr>
<tr class="odd">
<td>Condition negation.</td>
<td>The exclamation mark ('!') is used for negation.</td>
<td>The <strong>not</strong> keyword is used for negation.</td>
<td>X++ does not support the syntax !like. Instead, you must apply the ! operator to a clause.</td>
</tr>
<tr class="even">
<td>Wildcard characters for the <strong>like</strong> operator.</td>
<td><ul>
<li>0 to many – Asterisk ('*')</li>
<li>Exactly 1 – Question mark ('?')</li>
</ul></td>
<td><ul>
<li>0 to many – Percent sign ('%')</li>
<li>Exactly 1 – Underbar ('_')</li>
</ul></td>
<td>For more information, see Relational Operators.</td>
</tr>
<tr class="odd">
<td>Logical operators in the <strong>where</strong> clause.</td>
<td><ul>
<li>And – &amp;&amp;</li>
<li>Or – ||</li>
</ul></td>
<td><ul>
<li>And – <strong>and</strong></li>
<li>Or – <strong>or</strong></li>
</ul></td>
<td>For more information, see Relational Operators.</td>
</tr>
</tbody>
</table>

#### Code Example

The following code example illustrates features in the previous table.
<table>
<colgroup>
<col width="100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><pre><code>static void OByWhere452Job(Args _args)
{
    // Declare the table buffer variable.
    CustTable tCustTable;
    ;
    while
    SELECT * from tCustTable
        order by tCustTable.AccountNum desc
        where (!(tCustTable.Name like &#39;*i*i*&#39;) &amp;&amp; tCustTable.Name like &#39;T?e *&#39;)
    {
        info(tCustTable.AccountNum + &quot; , &quot; + tCustTable.Name);
    }
}
/*** InfoLog output
Message (04:02:29 pm)
4010 , The Lamp Shop
4008 , The Warehouse
4001 , The Bulb
***/</code></pre></td>
</tr>
</tbody>
</table>

 

#### X++ SQL Keywords

The following X++ SQL keywords are among those that are not part of ANSI SQL:
-   crosscompany
-   firstonly100
-   forceliterals
-   forcenestedloop
-   forceplaceholders
-   forceselectorder
-   validtimestate

### Join Clause

The following table lists differences about the **join** keyword of X++ SQL and ANSI SQL.

| Feature                          | X++ SQL                                                                                                                                                                                               | ANSI SQL                                                                                                                                                                                           | Comments                                                                               |
|----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------|
| Columns list.                    | The columns in the columns list must all come from the table listed in the **from** clause, and not from any table in a **join** clause. Columns in the list cannot be qualified by their table name. | The columns in the columns list can come from any table in the **from** or **join** clauses. It helps others to maintain your code when you qualify the columns in the list with their table name. | For more information, see Select Statements on Fields.                                 |
| **Join** clause syntax.          | The **join** clause follows the **where** clause.                                                                                                                                                     | The **join** clause follows a table in the **from** clause.                                                                                                                                        | In the X++ code example, the **join** criteria is an equality of `SalesPoolId` values. |
| **Inner** keyword.               | The default **join** mode is inner join. There is no **inner** keyword.                                                                                                                               | The default **join** mode is inner join. The **inner** keyword is available to make the code explicit.                                                                                             | The **outer** keyword exists in both X++ SQL and ANSI SQL.                             |
| **Left** and **right** keywords. | The **left** and **right** keywords are not available. All joins are left.                                                                                                                            | The **left** and **right** keywords are available to modify the **join** keyword.                                                                                                                  | No comments.                                                                           |
| Equality operator.               | The double equal sign operator ('`==`') is used to test for the equality of two values.                                                                                                               | The single equal sign operator ('`=`') is used to test for the equality of two values.                                                                                                             | No comments.                                                                           |

#### Code Example

The following code example illustrates the **join** syntax in X++ SQL.
<table>
<colgroup>
<col width="100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><pre><code>static void OByWhere453Job(Args _args)
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
            where (tCustTable.Name like &#39;The *&#39;)
        join tSalesPool
            where tCustTable.SalesPoolId == tSalesPool.SalesPoolId
    {
        info(tCustTable.AccountNum + &quot; , &quot; + tCustTable.Name);
    }
}</code></pre></td>
</tr>
</tbody>
</table>

 

### Aggregate Fields

The following table lists some differences in how aggregate fields in the **select** column list are referenced between X++ SQL and ANSI SQL. Aggregate fields are those that are derived by functions such as **sum** or **avg**.

| Feature                     | X++ SQL                                                  | ANSI SQL                                                                                                                    | Comments                                                                       |
|-----------------------------|----------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------|
| Aggregate field name alias. | The aggregate value is in the field that was aggregated. | You can use the **as** keyword to tag an aggregate field with a name alias. The alias can be referenced in subsequent code. | For more information, see Aggregate Functions: Differences Between X++ and SQL |

#### Code Example

In the following code example, the call to the info method illustrates the way to reference aggregate fields (see `tPurchLine.QtyOrdered`).
<table>
<colgroup>
<col width="100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><pre><code>static void Null673Job(Args _args)
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
            &quot;QtyOrdered:  &quot; + num2str(tPurchLine.QtyOrdered, 
            3,  // Minimum number of output characters.
            2,  // Required number of decimal places in the output.
            1,  // &#39;.&#39;  Separator to mark the start of the decimal places.
            2   // &#39;,&#39;  The thousands separator.
            ));
    }
    info(&quot;End.&quot;);
}
/***
Message (12:23:08 pm)
QtyOrdered:  261,550.00
End.
***/</code></pre></td>
</tr>
</tbody>
</table>

 

### Other Differences

The following table lists other differences of the **select** statement between the X++ SQL and ANSI SQL.
Feature
X++ SQL
ANSI SQL
Comments
The **having** keyword.
There is no **having** keyword.
The **having** keyword enables you to specify filter criteria for rows that are generated by the group by clause.
No comments.
Null results.
In a **while** select statement, if the **where** clause filters out all rows, no special count row is returned to report that.
In a **select**, if the **where** clause filters out all rows, a special count row is returned. The count value is 0.
No comments.
Cursors for navigating returned rows.
The while select statement provides cursor functionality. The alternative is to use the **next** keyword.
You can declare a **cursor** for looping through the rows that are returned from a **select** statement.
For more information, see Methods in X++.
**From** clause.
The **from** keyword is optional when no columns are listed and only one table is referenced. The following two syntax options are equivalent: select \* from tCustTable; `select tCustTable;`
A **select** statement cannot read from a table unless the **from** clause is used.
In X++ SQL, the simple **select** statement fills the table buffer variable with the first row that was returned. This is illustrated by the following code fragment: select \* from tCustTable; `info(tCustTable.Name);`



