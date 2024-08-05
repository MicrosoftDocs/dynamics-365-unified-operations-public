---
title: Macros in X++
description: Learn how to create and use macros in X++, including outlines of define and if directives, including using and testing Macro values.
author: josaw1
ms.author: josaw
ms.topic: article
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

Precompiler directives are processed before the code is compiled. The directives declare and handle macros and their values. The directives are removed by the precompiler so that the X++ compiler never encounters them. The X++ compiler only sees the sequence of characters written into the X++ code by the directives.

> [!WARNING]
> Use of macros is not recommended. Macros are supported for backwards compatibility only.
>
> Instead of macros, use language constructs like these:
>
> + [Constants](xpp-variables-data-types.md#constants-read-only-variables-and-macros)
> + [Sysda](sysda.md) for queries.

## #define and #if directives

All precompiler directives and symbols begin with the `#` character. A macro can be defined at any point in the code. The variable can have a value that is a sequence of characters, but it is not required to have a value. The `#define` directive tells the precompiler to create the macro variable, including an optional value. The `#if` directive tests whether the variable is defined, and optionally, whether it has a specific value. The X++ precompiler directives, the macro names that they define, and the `#if` directive value tests are all case-insensitive. However, it is a best practice to begin macro names with an uppercase letter.

## #undef directive

You can use the `#undef` directive to remove a macro definition that exists from a previous `#define`. After a macro name has been created by `#define` and then removed by `#undef`, the macro can be created again by another `#define`. `#undef` has no effect on macros that are created by the `#localmacro` directive.

## Use a Macro Value

You can define a macro name to have a value. A macro value is a sequence of characters. A macro value is not a string (or **str**) in the formal sense of a data type. You assign a value to a macro by appending the value enclosed in parentheses at the end of a `#define` directive. You can use the macro symbol where you want the value to occur in the X++ code. A macro symbol is the name of the macro with the `#` character added as a prefix. The following code sample shows a macro symbol **\#MyMacro.** The symbol is replaced by the value of the macro.

## Test a Macro Value

You can test a macro to see whether it has a value. You can also test to see whether its value is equal to a specific sequence of characters. These tests enable you to conditionally include lines of code in your X++ program. There is no way you can test whether a defined macro has a value. You can only test whether a specific value matches the value of a macro. As a best practice, any macro name that you define should always have a value, or it should never have a value. When you alternate between these modes, your code becomes difficult to understand. For macros that have a value, you can vary the value when you see fit.

## #defInc and #defDec directives

`#defInc` and `#defDec` are the only directives that interpret the value of a macro and they apply only to macros that have a value that can be converted to the formal **int** type. The value can only contain numerals. The only non-numeric character allowed is a leading negative sign (-). The integer value is treated as an X++ **int**, not as an **int64**. For macro names that are used by the `#defInc` directive, it is important that the `#define` directive that creates the macro not reside in a class declaration. The behavior of `#defInc` in these cases is unpredictable. Instead, such macros should be defined in only a method. We recommend that the `#defInc` and `#defDec` directives only be used for macros that have an integer value. The precompiler follows special rules for `#defInc` when the macro value is not an integer, or when the value is unusual or extreme. The following table lists the values that `#defInc` converts to zero (0) and then increments. When a value is converted to 0 by `#defInc`, the original value cannot be recovered, not even by `#defDec`.

| Macro value       | Behavior |
|-------------------|----------|
| (+55)             | The positive sign (+) prefix makes the precompiler treat this as a non-numeric string. The precompiler treats all non-numeric strings as 0 when it handles a `#defInc` (or `#defDec`) directive. |
| ("3")             | Integers enclosed in quotation marks are treated as 0. The quotation marks are discarded, and these changes persist. |
| ( )               | A string of spaces is treated as 0, and then incremented. |
| ()                | A zero-length string is treated as 0, and then incremented, when the value is enclosed in parentheses, as in **\#define.MyMac().** |
| (Random string.)  | Any non-numeric string of characters is treated as 0, and then incremented. |
| (0x12)            | Hexadecimal numbers are treated as non-numeric strings. Therefore they are converted to 0, and then incremented. |
| (-44)             | Negative numbers are acceptable, including integers without the negative sign (`-`). |
| (2147483647)      | The maximum positive **int** value is changed to the minimum negative **int** value by `#defInc`. |
| (999888777666555) | Any large number, beyond the capacity of **int** and **int64**. This is treated as the maximum positive **int** value. |
| (5.8)             | Real numbers are truncated by `#defDec` (and `#defInc`). Subsequent symbol substitution shows that the truncation persists. |
|                   | When no value and no parentheses are provided for the directive `#define.MyValuelessMacro`, the precompiler rejects use of the directive `#defInc`.MyValuelessMacro. |

## \#globaldefine directive

The `#globaldefine` directive is similar to the `#define` directive. The difference is that `#define` directives generally take precedence over `#globalmacro` directives. This is true regardless of which directive occurs first in the X++ code. A `#globaldefine` never overwrites a `#define` directive that has both a macro name and a value. A `#globaldefine` can overwrite another `#globaldefine`. A `#define` directive that has only a name does not overwrite a `#globalmacro` that has both a name and a value. It is recommended that you use `#define,` and that you do not use `#globaldefine.` Use of `#globaldefine` can create uncertainty that makes code difficult to maintain. The exact semantics of `#globaldefine` cannot be achieved through `#if` test directives. By using `#if` tests you can avoid overwriting a `#define` and a `#globaldefine.` But `#if` tests cannot distinguish between `#define` and `#globaldefine` macros.

## Macro parameters

You can define macro values to include parameter symbols. The first parameter symbol is `%1`, the second is `%2`, and so on. You pass values for the parameters when you reference the macro symbol name for expansion. Macro parameter values are character sequences of no formal type, and they are comma delimited. There is no way to pass in a comma as part of a parameter value. The number of parameters passed can be less than, greater than, or equal to the number of parameters that the macro value is designed to receive. The system tolerates mismatches in the number of parameters passed. If fewer parameters are passed than the macro expects, each omitted parameter is treated as a zero-length sequence of characters.

## \#localmacro and \#globalmacro directives

The `#localmacro` directive is a good choice when you want a macro to have a value that is several lines long, or when your macro value contains a closing parenthesis. The `#localmacro` directive is a good choice when you want your macro value to be lines of X++ or SQL code. The `#localmacro` directive can be written as `#macro`. However, `#localmacro` is the recommended term. Both macros have the same behavior. By using the `#if` directive, you can test whether a macro name is declared with the `#define` directive. However, you cannot test whether the macro name is declared with the `#localmacro` directive. Only macros declared by using the `#define` directive are affected by the `#undef` directive. In a `#define` directive, you can specify a name that is already in scope as a `#localmacro`. The effect is to discard the `#localmacro` and create a `#define` macro. This also applies to the opposite sequence, which means that a `#localmacro` can redefine a `#define`. A `#localmacro` (that has both a macro name and a value) always overrides a previous `#localmacro` that has the same name. However, you cannot always be sure whether the override occurs when you use `#globalmacro.` For this reason we recommend that you do not use `#globalmacro`. This same problem occurs with `#globaldefine`. The main difference between a `#define` macro and a `#localmacro` macro is in how their syntax is terminated. The terminators are as follows:

- `#define` – is terminated by– `)`
- `#localmacro` – is terminated by– `#endmacro`

`#localmacro` is a better choice for macros with multiple line values. Multiple line values are typically lines of X++ or SQL code. X++ and SQL contain lots of parentheses, and these would prematurely terminate a #define. Both `#define` and `#localmacro` can be declared and terminated on either a single line or on subsequent lines. In practice, the `#define` is terminated on the same line that it is declared on. In practice, the `#localmacro` is terminated on a subsequent line. Where both macro names and values are supplied, the `#globalmacro` directive cannot override the #define directive. Also, the `#globaldefine` directive cannot override the `#localmacro` directive.

## Nesting Macro Symbols

You can nest precompiler definition directives inside an outer definition directive. The main definition directives are `#define` and `#localmacro`.

A `#define` directive can be given inside a `#localmacro` directive, and a `#localmacro` can be inside a `#define`.

## \#macrolib directive

In the Application Explorer under the Macros node, there are many library nodes that contain sets of macro directives. Both `#define` and `#localmacro` often appear in the contents of these macro libraries. You can use the **\#macrolib.MyAOTMacroLibrary** to include the contents of a macro library in your X++ code. The `#if` and `#undef` directives do not apply to `#macrolib` names. However, they do apply to `#define` directives that are the contents of a `#macrolib` macro. The directive **\#macrolib.MyAOTMacroLibrary** can also be written as **\#MyAOTMacroLibrary.** The `#macrolib` prefix is recommended because it is never ambiguous to a person who later reads the code.

## \#linenumber Directive

You can use the `#linenumber` directive during your development and debugging of code. It is replaced by the physical line number in the code file.

## Range (scope) of macros

The range in which a macro can be referenced depends on where the macro is defined. In a class, macros that are defined in the parent class can be referenced, but macros defined in a child class cannot be referenced. When the precompiler handles a child class, the precompiler first traces the inheritance chain to the most ascendant class. The precompiler processes all the directives from the class declaration part of the ascendant class. It stores all the macros and their values in its internal tables. The precompiler handles the next class in the inheritance chain the same way. The results of the directives in each class declaration are applied to the internal tables that are already populated from directives that were found earlier in the inheritance chain. When the precompiler reaches the target child class, it again handles the class declaration part. However, it next handles each method in a series of separate operations. The precompiler updates its internal tables in a way that the state of the tables can be restored as they were before processing of the current method began. After the first method is handled, the internal tables are restored before the next method is handled.

### The Method is All Contents of the Node

In this context, a method is defined as the contents of a method node in the Application Object Tree (AOT). In the AOT, you can expand the Classes node, expand a class node, right-click a method node, and then select Edit. Then you can add a line for `#define.MyMacro("abc")` before the method declaration. The precompiler treats this `#define` directive as part of the method, even though the `#define` occurs outside the `{}` block of the method.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
