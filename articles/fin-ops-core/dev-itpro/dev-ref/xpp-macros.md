---
title: Macros in X++
description: Learn how to create and use macros in X++, including outlines of define and if directives, including using and testing Macro values.
author: josaw1
ms.author: josaw
ms.topic: language-reference
ms.date: 11/24/2025
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Macros in X++

[!include [banner](../includes/banner.md)]

This article describes how to create and use macros in X++.

Precompiler directives, that is, macros, are conceptually processed before the code is compiled. The directives declare and handle macros and their values. The directives are replaced with the content they designate, so the compiler never encounters them. The X++ compiler only sees the sequence of characters written into the X++ code by the directives.

> [!WARNING]
> Macros are legacy features and might be deprecated in future releases. Use language constructs instead:
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

All precompiler directives and symbols start with the `#` character.

Define a macro with the following syntax:
```xpp
#define.MyMacro(Value) // creates a macro with a value.
#define.AnotherMacro() // creates a macro without a value.
```
 You can define a macro anywhere in your code. The macro can have a value that is a sequence of characters, but it doesn't need to have a value. The `#define` directive instructs the precompiler to create the macro variable, optionally including a value. 
 
  The `#if` directive checks whether the variable is defined and, optionally, whether it has a specific value, as shown in the following example:
  
  ```xpp
  #if.MyMacro
    // The MyNaacro is defined.
  #endif

  #ifnot.MyMacro
    // The MyNaacro is not defined.
  #endif
  ```
  The X++ precompiler directives, the macro names they define, and the `#if` directive value tests are all case-insensitive. However, define macro names that start with an uppercase letter.

## #undef directive

Use the `#undef` directive to remove a macro definition that exists from a previous `#define`. 
```xpp
#undef.MyMacro
#if.MyMacro
   // The macro is not defined, so this is not included
#endif
```
You can redefine a macro name that you removed with `#undef` by using another `#define`.

## Use a Macro Value

You can define a macro name to have a value. 
```xpp
#define.Offset(42)
...
print #Offset; // 42
```
A macro value doesn't have a particular data type - it's just a sequence of characters. Assign a value to a macro by providing the value enclosed in parentheses at the end of a `#define.MyMacro` directive. Use the macro symbol wherever you want the value to occur in the X++ code. A macro symbol is the name of the macro with the `#` character added as a prefix. The following code sample shows a macro symbol **\#MyMacro.** The symbol is replaced by the value of the macro.

## Test a Macro Value

You can test a macro to determine whether it has a value. You can also determine whether its value is equal to a specific sequence of characters. These tests enable you to conditionally include lines of code in your X++ program. There's no way to test whether a defined macro has a value. You can only test whether the macro value matches a specific value. As a best practice, always define a value for any macro name you define, or never define a value. When you alternate between these modes, your code becomes difficult to understand. 

## \#defInc and \#defDec directives

`#defInc` and `#defDec` are the only directives that interpret the value of a macro. They apply only to macros that have a value that the precompiler can convert to the formal **int** type. These directives change the numeric value of a macro at compile time. The value can only contain numbers. The only non-numeric character allowed is a leading negative sign (-). The integer value is treated as an X++ **int**, not as an **int64**. For macro names that the `#defInc` directive uses, the `#define` directive that creates the macro shouldn't reside in a class declaration. The behavior of `#defInc` in these cases is unpredictable. Instead, define such macros in only a method. Use the `#defInc` and `#defDec` directives only for macros that have an integer value. The precompiler follows special rules for `#defInc` when the macro value isn't an integer, or when the value is unusual or extreme. The following table lists the values that `#defInc` converts to zero (0) and then increments. When `#defInc` converts a value to 0, you can't recover the original value, not even by using `#defDec`.

| Macro value | defInc Value |  Behavior |
|-------------------|----------|---|
| (+55)      | 56 | The positive sign (+) prefix makes the precompiler treat this value as a non-numeric string. The precompiler treats all non-numeric strings as 0 when it handles a `#defInc` (or `#defDec`) directive. |
| ("3")      | 1 | Integers enclosed in quotation marks are treated as 0. |
| ( )               | 1 | A string of spaces is treated as 0. |
| ()                | 1 | A zero-length string is treated as 0. |
| (Random string.)  | 1 | Any non-numeric string of characters is treated as 0. |
| (0x12)            | 1 | Hexadecimal numbers are treated as non-numeric strings. Therefore, the precompiler converts them to 0. |
| (-44)             | -43 | Negative numbers are acceptable. |
| (2147483647)      | -2147483648 | The maximum positive **int** value overflows to the minimum negative **int** value by `#defInc`. |
| (999888777666555) | 1 | Any large number, beyond the capacity of **int** and **int64**. |
| (5.8)             | 1 | Real numbers are interpreted as 0. |
|                   | 1 | When no value and no parentheses are provided for the directive `#define.MyValuelessMacro` the value is 0. |


## \#globaldefine directive

The `#globaldefine` directive is similar to the `#define` directive. Use `#define` instead of `#globaldefine`.

## \#localmacro and \#macro directives

The `#localmacro` directive is a good choice when you want a macro to have a value that's several lines long, or when your macro value contains a closing parenthesis, making them good candidates to contain source code fragments.
```xpp
    #macro.RetailMatchedAggregatedSalesLine(
                %1.price            == %2.price
        &&      %1.businessDate     == %2.businessDate
        &&      %1.itemId           == %2.itemId
        &&      ((((%3) && (%1.qty <= 0)) || ((! %3) && (%1.qty > 0))) || (%4))
    )
    #endmacro
```
 The `#localmacro` directive can be written as `#macro`. However, `#localmacro` is the recommended term. By using the `#if` directive, you can test whether a macro name is declared with the `#define` directive. However, you can't test whether the macro name is declared with the `#localmacro` directive. Only macros declared by using the `#define` directive are affected by the `#undef` directive. In a `#define` directive, you can specify a name that is already in scope as a `#localmacro`. The effect is to discard the `#localmacro` and create a `#define` macro. This also applies to the opposite sequence, which means that a `#localmacro` can redefine a `#define`. A `#localmacro` (that has both a macro name and a value) always overrides a previous `#localmacro` that has the same name. This same problem occurs with `#globaldefine`. The main difference between a `#define` macro and a `#localmacro` macro is in how their syntax is terminated. The terminators are as follows:

- `#define` – is terminated by– `)`
- `#localmacro` – is terminated by– `#endmacro`

`#localmacro` is a better choice for macros with multiple line values. Multiple line values are typically lines of X++ or SQL code. X++ and SQL contain lots of parentheses, and these would prematurely terminate a #define. Both `#define` and `#localmacro` can be declared and terminated on either a single line or on subsequent lines. In practice, the `#define` is terminated on the same line that it's declared on. In practice, the `#localmacro` is terminated on a subsequent line.

## Macro parameters

You can define macro values to include parameter symbols. The first parameter symbol is `%1`, the second is `%2`, and so on. You pass values for the parameters when you reference the macro symbol name for expansion. Macro parameter values are character sequences of no formal type, and they're comma delimited. There's no way to pass in a comma as part of a parameter value. The number of parameters passed can be less than, greater than, or equal to the number of parameters that the macro value is designed to receive. The system tolerates mismatches in the number of parameters passed. If fewer parameters are passed than the macro expects, each omitted parameter is treated as a zero-length sequence of characters.

## Nesting Macro Symbols

You can nest precompiler definition directives inside an outer definition directive. The main definition directives are `#define` and `#localmacro`.

A `#define` directive can be given inside a `#localmacro` directive, and a `#localmacro` can be inside a `#define`.

## \#macrolib directive

In the Application Explorer under the Macros node under the Code node, there are many library nodes that contain sets of macro directives. Both `#define` and `#localmacro` often appear in the contents of these macro libraries. You can use the **\#macrolib.MyAOTMacroLibrary** to include the contents of a macro library in your X++ code. The `#if` and `#undef` directives don't apply to `#macrolib` names. However, they do apply to `#define` directives that are the contents of a `#macrolib` macro. The directive **\#macrolib.MyAOTMacroLibrary** can also be written as **\#MyAOTMacroLibrary.** The `#macrolib` prefix is recommended because it's never ambiguous to a person who later reads the code.

## \#linenumber Directive

You can use the `#linenumber` directive during your development and debugging of code. It's replaced by the physical line number in the code file prior to any macro expansion.

## Macro scope

The range in which you can reference a macro depends on where you define the macro. In a class, you can reference macros that you define in the parent class. When the precompiler handles a child class, it first traces the inheritance chain to the root class. The precompiler then processes all the directives from the root class to the class being compiled. It stores all the macros and their values in its internal tables. The results of the directives in each class declaration apply to the internal tables that are already populated from directives that it found earlier in the inheritance chain. 

However, the precompiler handles each method separately. It updates its internal tables so it can restore the state of the tables as they were before processing the current method. After the precompiler handles the first method, it restores the internal tables before handling the next method. 

In this context, a method is defined as the contents of a method node in the Application Object Tree (AOT). In the AOT, you can expand the Classes node, expand a class node, right-click a method node, and then select **Edit**. Then you can add a line for `#define.MyMacro("abc")` before the method declaration. The precompiler treats this `#define` directive as part of the method, even though the `#define` occurs outside the `{}` block of the method.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
