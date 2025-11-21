---
title: Macros in X++
description: Learn how to create and use macros in X++, including outlines of define and if directives, including using and testing Macro values.
author: josaw1
ms.author: josaw
ms.topic: language-reference
ms.date: 08/27/2021
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Macros in X++

[!include [banner](../includes/banner.md)]

This article describes how to create and use macros in X++.

Precompiler directives, i.e. macros, are conceptually processed before the code is compiled. The directives declare and handle macros and their values. The directives are replaced with the content they designate, so the compiler never encounters them. The X++ compiler only sees the sequence of characters written into the X++ code by the directives.

> [!WARNING]
> Macros are legacy features and may be deprecated in future releases. Use language constructs instead:
> Instead of macros, use language constructs like these:
>
> + [Constants](xpp-variables-data-types.md#constants-read-only-variables-and-macros)
> + [Sysda](sysda.md) for queries.

## Defining Macros
You define a named macro by using the syntax shown below
- #define.MyMacro(Value) creates a macro with an optional value.
- #if.MyMacro checks if a macro is defined.
- #undef.MyMacro removes a macro definition.

## #define and #if directives

All precompiler directives and symbols begin with the `#` character.

A macro is defined with the following syntax:
```xpp
#define.MyMacro(Value) // creates a macro with a value.
#define.AnotherMacro() // creates a macro without a value.
```
 A macro can be defined at any point in the code. The variable can have a value that is a sequence of characters, but it is not required to have a value. The `#define` directive tells the precompiler to create the macro variable, including an optional value. 
 
  The `#if` directive tests whether the variable is defined, and optionally, whether it has a specific value, as shown below:
  
  ```xpp
  #if.MyMacro
    // The MyNaacro is defined.
  #endif

  #ifnot.MyMacro
    // The MyNaacro is not defined.
  #endif
  ```
  The X++ precompiler directives, the macro names that they define, and the `#if` directive value tests are all case-insensitive. However, it is a best practice to define macro names starting with an uppercase letter.

## #undef directive

You can use the `#undef` directive to remove a macro definition that exists from a previous `#define`. 
```xpp
#undef.MyMacro
#if.MyMacro
   // The macro is not defined, so this is not included
#endif
```
A macro name that has been removed by `#undef` can be redefined by another `#define`.

## Use a Macro Value

You can define a macro name to have a value. 
```xpp
#define.Offset(42)
...
print #Offset; // 42
```
A macro value has not particular data type - It is just a sequence of characters. You assign a value to a macro by providing the value enclosed in parentheses at the end of a `#define.MyMacro` directive. You can use the macro symbol where you want the value to occur in the X++ code. A macro symbol is the name of the macro with the `#` character added as a prefix. The following code sample shows a macro symbol **\#MyMacro.** The symbol is replaced by the value of the macro.

## Test a Macro Value

You can test a macro to determine whether it has a value. You can also determine whether its value is equal to a specific sequence of characters. These tests enable you to conditionally include lines of code in your X++ program. There is no way you can test whether or not a defined macro has a value. You can only test whether the macro value matches a specific value. As a best practice, any macro name that you define should always have a value, or it should never have a value. When you alternate between these modes, your code becomes difficult to understand. 

## \#defInc and \#defDec directives

`#defInc` and `#defDec` are the only directives that interpret the value of a macro and they apply only to macros that have a value that can be converted to the formal **int** type. These directives mutate the numeric value of a macro at compile time. The value can only contain numbers. The only non-numeric character allowed is a leading negative sign (-). The integer value is treated as an X++ **int**, not as an **int64**. For macro names that are used by the `#defInc` directive, it is important that the `#define` directive that creates the macro not reside in a class declaration. The behavior of `#defInc` in these cases is unpredictable. Instead, such macros should be defined in only a method. We recommend that the `#defInc` and `#defDec` directives only be used for macros that have an integer value. The precompiler follows special rules for `#defInc` when the macro value is not an integer, or when the value is unusual or extreme. The following table lists the values that `#defInc` converts to zero (0) and then increments. When a value is converted to 0 by `#defInc`, the original value cannot be recovered, not even by `#defDec`.

| Macro value       | defInc Value |  Behavior |
|-------------------|----------| --- |
| (+55)      | 56 | The positive sign (+) prefix makes the precompiler treat this as a non-numeric string. |The precompiler treats all non-numeric strings as 0 when it handles a `#defInc` (or `#defDec`) directive. |
| ("3")      | 1 | Integers enclosed in quotation marks are treated as 0. |
| ( )               | 1 | A string of spaces is treated as 0. |
| ()                | 1 | A zero-length string is treated as 0. |
| (Random string.)  | 1 | Any non-numeric string of characters is treated as 0. |
| (0x12)            | 1 | Hexadecimal numbers are treated as non-numeric strings. Therefore they are converted to 0. |
| (-44)             | -43 | Negative numbers are acceptable. |
| (2147483647)      | -2147483648 | The maximum positive **int** value overflows to the minimum negative **int** value by `#defInc`. |
| (999888777666555) | 1 | Any large number, beyond the capacity of **int** and **int64**. |
| (5.8)             | 1 | Real numbers are interpreted as 0. |
|                   | 1 | When no value and no parentheses are provided for the directive `#define.MyValuelessMacro` the value is 0. |


## \#globaldefine directive

The `#globaldefine` directive is similar to the `#define` directive. Use `#define` instead of `#globaldefine`.

## \#localmacro and \#macro directives

The `#localmacro` directive is a good choice when you want a macro to have a value that is several lines long, or when your macro value contains a closing parenthesis, making them good candidates to contain source code fragments.
```xpp
    #macro.RetailMatchedAggregatedSalesLine(
                %1.price            == %2.price
        &&      %1.businessDate     == %2.businessDate
        &&      %1.itemId           == %2.itemId
        &&      ((((%3) && (%1.qty <= 0)) || ((! %3) && (%1.qty > 0))) || (%4))
    )
    #endmacro
```
 The `#localmacro` directive can be written as `#macro`. However, `#localmacro` is the recommended term. By using the `#if` directive, you can test whether a macro name is declared with the `#define` directive. However, you cannot test whether the macro name is declared with the `#localmacro` directive. Only macros declared by using the `#define` directive are affected by the `#undef` directive. In a `#define` directive, you can specify a name that is already in scope as a `#localmacro`. The effect is to discard the `#localmacro` and create a `#define` macro. This also applies to the opposite sequence, which means that a `#localmacro` can redefine a `#define`. A `#localmacro` (that has both a macro name and a value) always overrides a previous `#localmacro` that has the same name. This same problem occurs with `#globaldefine`. The main difference between a `#define` macro and a `#localmacro` macro is in how their syntax is terminated. The terminators are as follows:

- `#define` – is terminated by– `)`
- `#localmacro` – is terminated by– `#endmacro`

`#localmacro` is a better choice for macros with multiple line values. Multiple line values are typically lines of X++ or SQL code. X++ and SQL contain lots of parentheses, and these would prematurely terminate a #define. Both `#define` and `#localmacro` can be declared and terminated on either a single line or on subsequent lines. In practice, the `#define` is terminated on the same line that it is declared on. In practice, the `#localmacro` is terminated on a subsequent line.

## Macro parameters

You can define macro values to include parameter symbols. The first parameter symbol is `%1`, the second is `%2`, and so on. You pass values for the parameters when you reference the macro symbol name for expansion. Macro parameter values are character sequences of no formal type, and they are comma delimited. There is no way to pass in a comma as part of a parameter value. The number of parameters passed can be less than, greater than, or equal to the number of parameters that the macro value is designed to receive. The system tolerates mismatches in the number of parameters passed. If fewer parameters are passed than the macro expects, each omitted parameter is treated as a zero-length sequence of characters.

## Nesting Macro Symbols

You can nest precompiler definition directives inside an outer definition directive. The main definition directives are `#define` and `#localmacro`.

A `#define` directive can be given inside a `#localmacro` directive, and a `#localmacro` can be inside a `#define`.

## \#macrolib directive

In the Application Explorer under the Macros node under the Code node, there are many library nodes that contain sets of macro directives. Both `#define` and `#localmacro` often appear in the contents of these macro libraries. You can use the **\#macrolib.MyAOTMacroLibrary** to include the contents of a macro library in your X++ code. The `#if` and `#undef` directives do not apply to `#macrolib` names. However, they do apply to `#define` directives that are the contents of a `#macrolib` macro. The directive **\#macrolib.MyAOTMacroLibrary** can also be written as **\#MyAOTMacroLibrary.** The `#macrolib` prefix is recommended because it is never ambiguous to a person who later reads the code.

## \#linenumber Directive

You can use the `#linenumber` directive during your development and debugging of code. It is replaced by the physical line number in the code file prior to any macro expansion.

## Macro Scope

The range in which a macro can be referenced depends on where the macro is defined. In a class, macros that are defined in the parent class can be referenced: When the precompiler handles a child class, the precompiler first traces the inheritance chain to the root class. The precompiler then processes all the directives from the root class to the class being compiled. It stores all the macros and their values in its internal tables. The results of the directives in each class declaration are applied to the internal tables that are already populated from directives that were found earlier in the inheritance chain. 

However, each method is handled separately. The precompiler updates its internal tables such that the state of the tables can be restored as they were before processing of the current method began. After the first method is handled, the internal tables are restored before the next method is handled. 

In this context, a method is defined as the contents of a method node in the Application Object Tree (AOT). In the AOT, you can expand the Classes node, expand a class node, right-click a method node, and then select Edit. Then you can add a line for `#define.MyMacro("abc")` before the method declaration. The precompiler treats this `#define` directive as part of the method, even though the `#define` occurs outside the `{}` block of the method.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
