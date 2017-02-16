---
# required metadata

title: Macros in X++
description: This topic describes how to create and use macros in X++.
author: RobinARH
manager: AnnBe
ms.date: 2016-09-01 19 - 30 - 15
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
ms.custom: 189441
ms.assetid: 25a66c5e-5ff3-40c5-935f-4696c7f759a1
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.dyn365.ops.intro: Feb-16
ms.dyn365.ops.version: AX 7.0.0

---

# Macros in X++

This topic describes how to create and use macros in X++.

Precompiler directives are processed before the the code is compiler. The directives declare and handle macros and their values. The directives are removed by the precompiler so that the X++ compiler never encounters them. The X++ compiler only sees the sequence of characters written into the X++ code by the directives.

## \#define and \#if directives
All precompiler directives and symbols begin with the \# character. A macro can be defined at any point in the code. The variable can have a value that is a sequence of characters, but it is not required to have a value. The **\#define** directive tells the precompiler to create the macro variable, including an optional value. The **\#if** directive tests whether the variable is defined, and optionally, whether it has a specific value. The X++ precompiler directives, the macro names that they define, and the **\#if** directive value tests are all case-insensitive. However, it is a best practice to begin macro names with an uppercase letter.

### Code example

In the following code sample, a macro named **MyMacro** is defined. It is not given a value in the **\#define.MyMacro** definition line. Therefore it behaves as if the value is a zero-length sequence of characters. The **\#if.MyMacro** statement tests whether **MyMacro** is defined. Because **MyMacro** is defined, the lines of code before the first **\#endif** are included in the X++ code at the test location. Near the end of the example there is an **\#ifnot.MyMacro** test. Because **MyMacro** is defined, that test is false and no lines are written into the X++ code. After the precompile phase ends for this method, the **MyMacro** definition goes out of scope and is no longer known to the system.

    static void SimpleDefineIfJob(Args _args)
    {
        str sTest = "Initial value.";
        
        #define.MyMacro // MyMacro is now defined.
        #if.MyMacro
            sTest = "Yes, MyMacro is defined.";
            info(sTest);
        #endif
        // Notice the non-code sentence line causes no X++ compiler error,
        // because the X++ compiler never sees it.
        #ifnot.MyMacro
            The X++ compiler would reject this sentence.
            sTest = "No, MyMacro is not defined.";
            info(sTest);
        #endif
    /********** Actual output
    Message (03:46:20 pm)
    Yes, MyMacro is defined.
    **********/
    }

## Precompile and Compile Error Messages
When you are developing code that contains macros, you must understand whether an error message is generated during the precompile or the compile phase. The two key words to look for are:

-   Lexical – This indicates a precompile error.
-   Syntax – This indicates a compile error.

The following code example has a lexical error caused by the first closing parenthesis, which marks the end of the directive. Therefore the precompiler is confused by the last two characters, "";)".

    #define.MyMacro1(info("Hello");)

The following code example has a syntax error caused by using the non-existent **++++** operator. The X++ compiler encounters this operator after **\#MyMacro2** is replaced by the macro value.The macro definition is correct even though its value is not accepted X++ syntax.

    #define.MyMacro2(++++iTest;) 
    #MyMacro2

## \#undef directive
You can use the **\#undef** directive to remove a macro definition that exists from a previous **\#define.** After a macro name has been created by **\#define** and then removed by **\#undef,** the macro can be created again by another **\#define.** **\#undef** has no effect on macros that are created by the **\#localmacro** directive. In the following code sample, the macro **MyMacro** is undefined by using the \#undef directive. The \#undef occurs between the two \#if tests for its existence. The output shows only the first \#if test was true.

    static void UndefMacroJob(Args _args)
    {
        #define.MyMacro
        #if.MyMacro
            info("Macro is defined (1)");
        #endif
        #undef.MyMacro // Removes the macro.
        #if.MyMacro
            info("Macro is defined (2)");
        #endif
    /************* Actual output
    Message (10:19:15 am)
    Macro is defined (1)
    *************/
    }

## Use a Macro Value
You can define a macro name to have a value. A macro value is a sequence of characters. A macro value is not a string (or **str**) in the formal sense of a data type. You assign a value to a macro by appending the value enclosed in parentheses at the end of a \#define directive. You can use the macro symbol where you want the value to occur in the X++ code. A macro symbol is the name of the macro with the \# character added as a prefix. The following code sample shows a macro symbol **\#MyMacro.** The symbol is replaced by the value of the macro.

    static void MacroWithIntValueJob(Args _args)
    {
        int iTest = 8;
        ;
        #define.MyMacro(32)
        // This next #define, which has no value for the macro name,
        // would not disrupt the value 32 set by the previous #define.
        //#define.MyMacro
        // This next #define, which has a different value than 32,
        // would overwrite the value 32 set by the previous #define.
        //#define.MyMacro(444)
        iTest = #MyMacro;
        info(int2str(iTest));
    /**********  Actual output
    Message (04:33:49 pm)
    32
    **********/
    }

## Test a Macro Value
You can test a macro to see whether it has a value. You can also test to see whether its value is equal to a specific sequence of characters. These tests enable you to conditionally include lines of code in your X++ program. There is no way you can test whether a defined macro has a value. You can only test whether a specific value matches the value of a macro. As a best practice, any macro name that you define should always have a value, or it should never have a value. When you alternate between these modes, your code becomes difficult to understand. For macros that have a value, you can vary the value when you see fit. In the following code sample, two **\#if** tests are run to determine whether the macro **MyIntMacro** exists. The **\#if.MyIntMacro()** test is true. This syntax behaves the same as **\#if.MyIntMacro.**

    static void TestMacroValue6Job(Args _args)
    {
        #define.MyIntMacro(66)
        // #if tests.
        #if.MyIntMacro()
            info("A: " + int2str(#MyIntMacro));
        #endif
        #if.MyIntMacro(66)
            info("B: " + int2str(#MyIntMacro));
        #endif
        // #ifNOT tests.
        #ifNOT.MyIntMacro(7777)
            info("C: " + int2str(#MyIntMacro));
        #endif
        #ifNOT.No_Such_Macro_Name(66)
            info("D: " + int2str(#MyIntMacro));
        #endif
    /****************  Actual output
    Message (11:24:47 am)
    A: 66
    B: 66
    C: 66
    D: 66
    ****************/
    }

The following code sample shows the **\#if.DebugMacro(heavy)** directive that tests the value of the **DebugMacro** macro. If the value is the five character sequence **heavy**, then the test is true.

    static void TestMacroSpecificValue8Job(Args _args)
    {
        ;
        // Uncomment either one of these defines, or neither.
        //#define.DebugMacro(light) // This line for: light debugging.
        #define.DebugMacro(heavy) // This line for: heavy debugging.
        #if.DebugMacro
            info("Starting the job.");
        #endif
        #if.DebugMacro(heavy)
            info("UTC == "
                + DateTimeUtil ::toStr
                    (DateTimeUtil::utcNow()
                    )
                );
        #endif
        // Do something useful here.
    /**********  Actual output
    Message (01:58:12 pm)
    Starting the job.
    UTC == 2007-12-05T21:58:12
    **********/
    }

## \#defInc and \#defDec directives
**\#defInc** and **\#defDec** are the only directives that interpret the value of a macro and they apply apply only to macros that have a value that can be converted to the formal **int** type. The value can only contain numerals. The only non-numeric character allowed is a leading negative sign (-). The integer value is treated as an X++ **int**, not as an **int64**. For macro names that are used by the **\#defInc** directive, it is important that the **\#define** directive that creates the macro not reside in a class declaration. The behavior of **\#defInc** in these cases is unpredictable. Instead, such macros should be defined in only a method. We recommend that the **\#defInc** and **\#defDec** directives only be used for macros that have an integer value. The precompiler follows special rules for **\#defInc** when the macro value is not an integer, or when the value is unusual or extreme. The following table lists the values that **\#defInc** converts to zero (0) and then increments. When a value is converted to 0 by **\#defInc,** the original value cannot be recovered, not even by **\#defDec.**

| Macro value       | Behavior                                                                                                                                                                                               |
|-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| (+55)             | The positive sign (+) prefix makes the precompiler treat this as a non-numeric string. The precompiler treats all non-numeric strings as 0 when it handles a **\#defInc** (or **\#defDec)** directive. |
| ("3")             | Integers enclosed in quotation marks are treated as 0. The quotation marks are discarded, and these changes persist.                                                                                   |
| ( )               | A string of spaces is treated as 0, and then incremented.                                                                                                                                              |
| ()                | A zero-length string is treated as 0, and then incremented, when the value is enclosed in parentheses, as in **\#define.MyMac().**                                                                     |
| (Random string.)  | Any non-numeric string of characters is treated as 0, and then incremented.                                                                                                                            |
| (0x12)            | Hexadecimal numbers are treated as non-numeric strings. Therefore they are converted to 0, and then incremented.                                                                                       |
| (-44)             | Negative numbers are acceptable, including integers without the negative sign (-).                                                                                                                     |
| (2147483647)      | The maximum positive **int** value is changed to the minimum negative **int** value by \#defInc.                                                                                                       |
| (999888777666555) | Any large number, beyond the capacity of **int** and **int64**. This is treated as the maximum positive **int** value.                                                                                 |
| (5.8)             | Real numbers are truncated by \#defDec (and \#defInc). Subsequent symbol substitution shows that the truncation persists.                                                                              |
|                   | When no value and no parentheses are provided for the directive \#define.MyValuelessMacro, the precompiler rejects use of the directive \#defInc.MyValuelessMacro.                                     |

### Code example

In the following code sample, the initial value of the macro **CounterMacroA** is a string that can be converted into an integer. The sample shows how the **\#defInc** and **\#defDec** directives can be used for this macro name.

    static void SimpleDefINCJob(Args _args)
    {
        ;
        #define.CounterMacroA(1)
        #defInc.CounterMacroA
        info("mg11: # CounterMacroA == " + int2str(#CounterMacroA));
        #if.CounterMacroA(2)
            info("mg12: # if confirms CounterMacroA == 2");
        #endif
        #defDec.CounterMacroA
        info("mg23: # CounterMacroA == " + int2str(#CounterMacroA));
        #if.CounterMacroA(1)
            info("mg24: # if confirms CounterMacroA == 1");
        #endif
    /**************  Actual Infolog output
    Message (12:47:57 pm)
    mg11: # CounterMacroA == 2
    mg12: # if confirms CounterMacroA == 2
    mg23: # CounterMacroA == 1
    mg24: # if confirms CounterMacroA == 1
    **************/
    }

## \#globaldefine directive
The **\#globaldefine** directive is similar to the **\#define** directive. The difference is that **\#define** directives generally take precedence over **\#globalmacro** directives. This is true regardless of which directive occurs first in the X++ code. A **\#globaldefine** never overwrites a **\#define** directive that has both a macro name and a value. A **\#globaldefine** can overwrite another **\#globaldefine. **A **\#define** directive that has only a name does not overwrite a \#globalmacro that has both a name and a value. It is recommended that you use **\#define,** and that you do not use **\#globaldefine.** Use of **\#globaldefine** can create uncertainty that makes code difficult to maintain. The exact semantics of **\#globaldefine** cannot be achieved through **\#if** test directives. By using **\#if** tests you can avoid overwriting a **\#define** and a **\#globaldefine.** But **\#if** tests cannot distinguish between **\#define** and **\#globaldefine** macros. The following code sample is the closest you can come to achieving the **\#globaldefine** semantic with other directives such as **\#if.**

    static void IfNotDefineNestGlobalJob (Args _args)
    {
        ;
        #undef.MaybeMac
        #ifnot.MaybeMac
            #define.MaybeMac(4444) // Works.
        #endif
        #if.MaybeMac
            info(int2str(#MaybeMac));
        #endif
    /**********************  Actual Infolog output
    Message (07:43:32 pm)
    4444
    **********************/
    }

### Code example

The following code sample shows a difference in the behavior of **\#define** and **\#globaldefine.** Following the code sample is a table explaining the conclusions from the output. The primary test case in the code sample is labeled **12**.

    static void InteractDefineGlobalJob(Args _args)
    {
        ;
        // Pairs of #define - #globaldefine directives (same macro names).
        #define.11_DEFINEvalue_GLOBALnoval("11__DEFINE.")
        #globaldefine.11_DEFINEvalue_GLOBALnoval
        #define.12_DEFINEnoval_GLOBALvalue
        #globaldefine.12_DEFINEnoval_GLOBALvalue("12_GLOBAL.")
        #define.13_DEFINEvalue_GLOBALvalue("13__DEFINE.")
        #globaldefine.13_DEFINEvalue_GLOBALvalue("13_GLOBAL.")
        // Pairs of #globaldefine - #define directives.
        #globaldefine.27_GLOBALvalue_DEFINEnoval("27_GLOBAL.")
        #define.27_GLOBALvalue_DEFINEnoval
        #globaldefine.28_GLOBALnoval_DEFINEvalue
        #define.28_GLOBALnoval_DEFINEvalue("28__DEFINE.")
        #globaldefine.29_GLOBALvalue_DEFINEvalue("29_GLOBAL.")
        #define.29_GLOBALvalue_DEFINEvalue("29__DEFINE.")
        // Pairs of same directive types.
        #define.50_DEFINEvalue_DEFINEnoval("50__DEFINE 1.")
        #define.50_DEFINEvalue_DEFINEnoval
        #globaldefine.64_GLOBALvalue_GLOBALnoval("64_GLOBAL 1.")
        #globaldefine.64_GLOBALvalue_GLOBALnoval
        #globaldefine.65_GLOBALnoval_GLOBALvalue
        #globaldefine.65_GLOBALnoval_GLOBALvalue("65_GLOBAL 2.")
        #globaldefine.66_GLOBALvalue_GLOBALvalue("66_GLOBAL 1.")
        #globaldefine.66_GLOBALvalue_GLOBALvalue("66_GLOBAL 2.")
        // Infolog outputs.
        info(#11_DEFINEvalue_GLOBALnoval);
        info(#12_DEFINEnoval_GLOBALvalue);
        info(#13_DEFINEvalue_GLOBALvalue);
        info(#27_GLOBALvalue_DEFINEnoval);
        info(#28_GLOBALnoval_DEFINEvalue);
        info(#29_GLOBALvalue_DEFINEvalue);
        info(#50_DEFINEvalue_DEFINEnoval);
        info(#64_GLOBALvalue_GLOBALnoval);
        info(#65_GLOBALnoval_GLOBALvalue);
        info(#66_GLOBALvalue_GLOBALvalue);
    /*****************************  Actual Infolog output
    Message (09:31:26 pm)
    11__DEFINE.
    12_GLOBAL. Shows that #globaldefine overwrites #define when #globaldefine is giving a value to an existing macro that has no value.Test cases 13 and 29 are more common and realistic.
    13__DEFINE. Shows that #define usually takes precedence over #globaldefine, regardless of which directive occurs first in the X++ code.Test case 12 shows this is not always true.
    27_GLOBAL.
    28__DEFINE.
    29__DEFINE. Shows that #define usually takes precedence over #globaldefine, regardless of which directive occurs first in the X++ code.Test case 12 shows this is not always true.
    50__DEFINE 1. Shows that a #globaldefine that has a name but no value does not overwrite a #globaldefine that has both a name and a value. The same is true between a pair of #define directives.This resembles test case 12.
    64_GLOBAL 1. Shows that a #globaldefine that has a name but no value does not overwrite a #globaldefine that has both a name and a value. The same is true between a pair of #define directives.This resembles test case 12.
    65_GLOBAL 2. Shows that a #globaldefine that has both a name and a value overwrites a previous #globaldefine.
    66_GLOBAL 2. Shows that a #globaldefine that has both a name and a value overwrites a previous #globaldefine.
    *****************************/
    }

## Macro parameters
You can define macro values to include parameter symbols. The first parameter symbol is %1, the second is %2, and so on. You pass values for the parameters when you reference the macro symbol name for expansion. Macro parameter values are character sequences of no formal type, and they are comma delimited. There is no way to pass in a comma as part of a parameter value. The number of parameters passed can be less than, greater than, or equal to the number of parameters that the macro value is designed to receive. The system tolerates mismatches in the number of parameters passed. If fewer parameters are passed than the macro expects, each omitted parameter is treated as a zero-length sequence of characters. In the following code sample, **MyMacro** is defined to have a value that contains parameters. Macro substitution symbols are given with parameter values in parentheses.

    static void MacroParameterSubstitutionJob(Args _args)
    {
        ;
        #define.MyMacro("One == [%1] ,  Two == [%2]")
        // Make parameter substitutions:
        info("AA: " + #MyMacro(Apple));
        info("BB: " + #MyMacro(Apple,Banana));
        info("CC: " + #MyMacro(Apple, Banana, cranberry));
        info("DD: " + #MyMacro(,Apple,Banana));
        info("EE: " + #MyMacro());
        info("FF: " + #MyMacro);
    /************  Actual Infolog output
    Message (03:22:07 pm)
    AA: One == [Apple] ,  Two == []
    BB: One == [Apple] ,  Two == [Banana]
    CC: One == [Apple] ,  Two == [ Banana]
    DD: One == [] ,  Two == [Apple]
    EE: One == [] ,  Two == []
    FF: One == [] ,  Two == []
    ************/
    }

## \#localmacro and \#globalmacro directives
The **\#localmacro** directive is a good choice when you want a macro to have a value that is several lines long, or when your macro value contains a closing parenthesis. The **\#localmacro** directive is a good choice when you want your macro value to be lines of X++ or SQL code. The **\#localmacro** directive can be written as **\#macro.** However, **\#localmacro** is the recommended term. Both macros have the same behavior. By using the **\#if** directive, you can test whether a macro name is declared with the **\#define** directive. However, you cannot test whether the macro name is declared with the **\#localmacro** directive. Only macros declared by using the **\#define** directive are affected by the **\#undef** directive. In a **\#define** directive, you can specify a name that is already in scope as a **\#localmacro.** The effect is to discard the **\#localmacro** and create a **\#define** macro. This also applies to the opposite sequence, which means that a **\#localmacro** can redefine a **\#define.** A **\#localmacro** (that has both a macro name and a value) always overrides a previous **\#localmacro** that has the same name. However, you cannot always be sure whether the override occurs when you use **\#globalmacro.** For this reason we recommend that you do not use **\#globalmacro. **This same problem occurs with **\#globaldefine.** The main difference between a **\#define** macro and a **\#localmacro** macro is in how their syntax is terminated. The terminators are as follows:

-   **\#define** – is terminated by– **)**
-   **\#localmacro** – is terminated by– **\#endmacro**

**\#localmacro** is a better choice for macros with multiple line values. Multiple line values are typically lines of X++ or SQL code. X++ and SQL contain lots of parentheses, and these would prematurely terminate a \#define. Both **\#define** and **\#localmacro** can be declared and terminated on either a single line or on subsequent lines. In practice, the **\#define** is terminated on the same line that it is declared on. In practice, the **\#localmacro** is terminated on a subsequent line. Where both macro names and values are supplied, the **\#globalmacro** directive cannot override the \#define directive. Also, the **\#globaldefine** directive cannot override the **\#localmacro** directive.

### Code examples

The following code sample shows how to use the **\#localmacro** directive. It demonstrates that the **\#undef** directive does not affect **\#localmacro** macros. It also shows that \#if tests cannot determine whether a **\#localmacro** macro has been defined.

    static void LocalMacroJob(Args _args)
    {
        ;
        #localmacro.LMacReportLog
            print("%1  --LM, print.");
            info("%1  --LM, Infolog.");
        #endmacro
        #LMacReportLog(g11: Hello World )
        #if.LMacReportLog
            info("The # IF LMacReportLog is true");
        #endif
        #undef.LMacReportLog
        #LMacReportLog(g22: Greetings World)
        #localmacro.LMacReportLog
        #endmacro // No lines for value before this end.
        #LMacReportLog(g33: Bye Bye) // Not present in the output.
    /*************  Actual Infolog output
    Message (03:10:17 pm)
    g11: Hello World   --LM, Infolog.
    g22: Greetings World  --LM, Infolog.
    *************/
    }

The following X++ code sample shows that **\#localmacro** overrides a **\#globalmacro** of the same macro name, but that **\#globalmacro** does not override **\#localmacro.**

    static void GlobalMacroNotOverrideJob(Args _args)
    {
        ;
        //---------  LGMa ,  L then G  ---------
        #localmacro.LGMa
            info("LGMa: Loc 11");
        #endmacro
        #globalmacro.LGMa
            info("LGMa: Glob 12");
        #endmacro
        #LGMa
        //---------  LGMb ,  G then L  ---------
        #globalmacro.LGMb
            info("LGMb: Glob 24");
        #endmacro
        #localmacro.LGMb
            info("LGMb: Loc 25");
        #endmacro
        #LGMb
    /****************  Actual Infolog output
    Message (06:39:42 am)
    LGMa: Loc 11
    LGMb: Loc 25
    ****************/
    }

## Nesting Macro Symbols
You can nest precompiler definition directives inside an outer definition directive. The main definition directives are **\#define** and **\#localmacro. **The cases for which this topic provides code samples are as follows:

-   Transitive substitution: A **\#define** macro can have the symbol for another macro as its value. Transitive substitution of the symbol occurs in X++ code.
-   No transitive substitution: An **\#if** directive test of a macro value does not perform substitutions.
-   Macro within a macro: A \#define directive can be given inside a **\#localmacro** directive, or a **\#localmacro** can be inside a **\#define.**

### Transitive Substitution

In the following code sample, the value of the first **\#define** variable includes a symbol (\#D) of the second **\#define** variable. This works even though the expansion symbol \#D occurs before macro **D** is defined.

    static void NestMacroJobA1(Args _args)
    {
        ;
        #define.Cd("Cd +: # D == " + #D)
        // If not commented out, this next code line would cause the
        // error message "The macro does not exist.", because
        // #D in the value of #Cd cannot be expanded before it is defined.
        //info(#Cd);
        #define.D("D")
        info(#Cd);
    /************  Actual Infolog output
    Message (10:42:13 am)
    Cd +: # D == D
    ************/
    }

### No transitive substitution

The following code sample tries to determine whether two macro variables have the same value, without specifying what that value might be. The output shows that this determination cannot be made..

    static void NestMacroJobA2(Args _args)
    {
        ;
        #define.A1(5)
        #define.A2(5)
        info("Status: A1==" + int2Str(#A1) + " , A2==" + int2Str(#A2));
        #if.A1(#A2)
            info("Yes, symbol substitution does work on # IF test.  Unexpected.");
        #endif
        #ifNOT.A1(#A2)
            info("No, symbol substitution does not work on # IF test.");
        #endif
    /************  Actual Infolog output
    Message (11:27:38 am)
    Status: A1==5 , A2==5
    No, symbol substitution does not work on # IF test.
    ************/
    }

The following code sample shows that the \#defInc directive does not lead to transitive substitution of symbol values. For more information about the \#defInc directive, see How to: Use the \#defInc and \#defDec Directives. After the \#defInc.E2 directive, the subsequent output value for \#E2 shows the value for **E2** is converted to zero (0) by \#defInc.E2 before it is incremented to one (1). Before the conversion, the value of **E2** was the three characters \#E2. The output for test case **36** shows the value has been converted to 1.

    static void NestMacroJobA4(Args _args)
    {
        ;
        #define.E1(5)
        #define.E2(#E1)
        info("11:  # E1 == " + int2Str(#E1));
        info("12:  # E2 == " + int2Str(#E2));
        #defInc.E1
        info(" -------");
        info("23: After Inc.E1,  # E1 == " + int2Str(#E1));
        info("24: After Inc.E1,  # E2 == " + int2Str(#E2));
        #defInc.E2
        info(" -------");
        info("35: After Inc.E2,  # E1 == " + int2Str(#E1));
        info("36: After Inc.E2,  # E2 == " + int2Str(#E2));
    /************  Actual Infolog output
    Message (02:39:41 pm)
    11:  # E1 == 5
    12:  # E2 == 5
     -------
    23: After Inc.E1,  # E1 == 6
    24: After Inc.E1,  # E2 == 6
     -------
    35: After Inc.E2,  # E1 == 6
    36: After Inc.E2,  # E2 == 1
    ************/
    }

### Macro within a macro

A **\#define** directive can be given inside a **\#localmacro** directive, and a **\#localmacro** can be inside a \#define. This is shown in the following code sample.

    static void NestMacroJobB5(Args _args)
    {
        int iTest = 31;
        ;
        //-------------  J  ---------------
        #localmacro.LocMacOuterJL
            #define.DefinInnerJD(5)
        #endmacro
        #LocMacOuterJL
        info("J: Directive nesting works if 5 appears: # DefinInnerJD == "
                + int2Str(#DefinInnerJD));
        //-------------  K  ---------------
        #define.DefinOuterKD(#localmacro.LocMacInnerKL ++iTest; #endmacro)
        ++iTest; // Result is 32.
        #DefinOuterKD
        #LocMacInnerKL
        info("K: Directive nesting works if 33 appears: iTest == "
                + int2Str(iTest));
    /**************  Actual Infolog output
    Message (11:21:02 am)
    J: Directive nesting works if 5 appears: # DefinInnerJD == 5
    K: Directive nesting works if 33 appears: iTest == 33
    **************/
    }

## \#macrolib directive
In the Application Explorer under the Macros node, there are many library nodes that contain sets of macro directives. Both **\#define** and **\#localmacro** often appear in the contents of these macro libraries. You can use the **\#macrolib.MyAOTMacroLibrary** to include the contents of a macro library in your X++ code. The **\#if** and **\#undef** directives do not apply to **\#macrolib** names. However, they do apply to **\#define** directives that are the contents of a **\#macrolib** macro. The directive **\#macrolib.MyAOTMacroLibrary** can also be written as **\#MyAOTMacroLibrary.** The **\#macrolib** prefix is recommended because it is never ambiguous to a person who later reads the code.

### Create a macro library

To create a macro library:

1.  In **Solution Explorer,** right-click on the project, select **Add** and then **New item.**
2.  In the **Add New Item** dialog, select Installed and then **AX Artifacts** in the left pane.
3.  In the middle pane, select **Macro.**
4.  Enter a name and click **Add.** Save the macro file and refresh the Application Explorer to find your macro library.

### Code examples

Dynamics AX has an macro library that is named **Event.** This macro library contains the directive **\#define.DefaultEventPollFrequency(15)**. The following code sample shows that the **\#macrolib.Event** directive makes the macro **\#DefaultEventPollFrequency** available.

    static void SystemProvidedMacroLibraryJob(Args _args)
    {
        ;
        #macrolib.Event // Contains: #define.DefaultEventPollFrequency(15)
        info("# DefaultEventPollFrequency == "
                + int2str(#DefaultEventPollFrequency));
    /***************  Actual Infolog output
    Message (06:31:26 pm)
    # DefaultEventPollFrequency == 15
    ***************/
    }

The following code example shows what happens when you write a **\#define** for a name that is already the name of a node in the macro library. For this example, there is a node named **MacLib23,** and its contents are one **\#define** as follows:

    #define.DefinInMacLib23("_This is inside AOT macrolib MacLib23.")

After a \#macrolib directive is issued for **MacLib23**, **\#define** and **\#undef** directives have no effect on the **\#macrolib** macro (see output \_BB). However, a **\#define** in the contents of a **\#macrolib** macro can be overwritten by a subsequent \#define or **\#undef** in the code (see output \_DD).

    static void PrecedenceMacrolibDefineJob(Args _args)
    {
        ;
        #define.MacLib23("_11:  Plain #define value for MacLib23, same name as the AOT macrolib macro.")
        info("_AA: " + #MacLib23);
        #macrolib.MacLib23
        info("_BB: " + #DefinInMacLib23); // Defined inside the macrolib macro.
        info("_CC: " + #MacLib23); // Output shows plain #define, not the macrolib macro contents.
        #define.DefinInMacLib23("_33:  Plain #define in the job code, overwrite of same macro name defined inside the macrolib macro.")
        info("_DD: " + #DefinInMacLib23);
    /***************************  Actual Infolog output
    Message (10:53:13 am)
    _AA: 11:  Plain #define value for MacLib23, same name as the AOT macrolib macro.
    _BB: This is inside AOT macrolib MacLib23.
    _CC: 11:  Plain #define value for MacLib23, same name as the AOT macrolib macro.
    _DD: 33:  Plain #define in the job code, overwrite of same macro name defined inside the macrolib macro.
    ***************************/
    }

## \#linenumber Directive
You can use the \#linenumber directive during your development and debugging of code. It is replaced by the physical line number in the code file.

### Code example

The following X++ code sample shows the behavior of the **\#linenumber** directive.

    static void LinenumberPhysicalJob(Args _args)
    {
        ;
        #define.Debug(light)
        #if.Debug
            info("Physical Line 8: # linenumber == "
                + int2Str(#linenumber));
        #endif
    /******************  Actual Infolog output
    Message (08:55:26 pm)
    Physical Line 8: # linenumber == 8
    ******************/
    }

## Range (scope) of macros
The range in which a macro can be referenced depends on where the macro is defined. In a class, macros that are defined in the parent class can be referenced, but macros defined in a child class cannot be referenced. When the precompiler handles a child class, the precompiler first traces the inheritance chain to the most ascendant class. The precompiler processes all the directives from the class declaration part of the ascendant class. It stores all the macros and their values in its internal tables. The precompiler handles the next class in the inheritance chain the same way. The result of the directives in each class declaration are applied to the internal tables that are already populated from directives that were found earlier in the inheritance chain. When the precompiler reaches the target child class, it again handles the class declaration part. However, it next handles each method in a series of separate operations. The precompiler updates its internal tables in a way that the state of the tables can be restored as they were before processing of the current method began. After the first method is handled, the internal tables are restored before the next method is handled.

#### The Method is All Contents of the Node

In this context, a method is defined as the contents of a method node in the Application Object Tree (AOT). In the AOT, you can expand the Classes node, expand a class node, right-click a method node, and then select Edit. Then you can add a line for \#define.MyMacro("abc") before the method declaration. The precompiler treats this \#define directive as part of the method, even though the \#define occurs outside the {} block of the method.

### Class Inheritance and Macro Reference Range

The following code example demonstrates the range of macro referencing in class inheritance scenarios. The primary line to notice in the method's output is the line labeled ClassC\_h. It shows that a macro defined in a grandparent class can be referenced in a method of the grandchild class. Another important line in the output is labeled ClassA\_k. This line shows that a macro defined in a method is not available in other methods. ClassA is the base class and it defines several macros in its class declaration. Its descendant classes reference these macros. The base class also defines a macro inside one of its methods. A second method in this class determines the macro is defined out of range and cannot be referenced in the second method. The **\#undef.MacroRange333** in the method **UseOtherMethodMacro** affects the availability of macro **MacroRange333** in the rest of that method. Descendant classes can still reference **MacroRange333**. ClassB extends ClassA and it undefines the macro **MacroRangeA** that is defined in its parent class. This makes the macro unavailable to any class that extends the present class. The present class also redefines the macro **MacroRangeB** that is defined in its parent class. This changes the value of the macro (from positive to negative). ClassC extends ClassB and it uses **\#ifnot** to demonstrate that it cannot access the **MacroRangeA** macro that the base class, ClassInheritanceOfMacrosCBase1, defines. The reason is that the mid-level class undefined the macro. This class also demonstrates that it can access the macro **MacroRange333** that ClassInheritanceOfMacrosCBase1 class defines. TestClass contains a method that calls the demonstration methods and displays the results.

    class ClassA
    {
        // Unless disturbed by other directives, these macros can
        // be referenced by method in this class in child classes.
        #define.MacroRangeA
        #define.MacroRangeB(22)
        #define.MacroRange333(333)

        static void UseMacros()
        {
            //  This method shows that a macro that is defined
            // in the class declaration is in range in every
            // method in that class.
            // This method also contains a define for macro
            // MacroDefInMethodD, and tests outside this
            // method determine the macro is not in range.
            ;
            info("ClassA: #MacroRangeB == " + int2str(#MacroRangeB));
            #define.MacroDefInMethodD // Cannot be referenced in other methods.
        }

        static void UseOtherMethodMacro()
        {
            // This method shows that the macro MacroDefInMethodD
            // that was defined in another method in this class
            // cannot be referenced in this method.
            // This method contains an #undef of MacroRange333,
            // yet descendant classes can still reference this macro.
            #ifnot.MacroDefInMethodD
            info("ClassA_k: This means MacroDefInMethodD is in not range here.");
            #endif
            #undef.MacroRange333
        }
    }


    class ClassB extends ClassA
    {
        // This class declaration makes the macro MacroRangeA
        // unavailable to methods in this class and child classes.
        // This class declaration also redefines MacroRangeB for
        // this class and child classes.
        #undef.MacroRangeA // Makes unavailable to child classes.
        #define.MacroRangeB(-22) 
        // Redefining with a different value.
        static void UseMacros()
        {
            // This method shows that the value for #MacroRangeB comes
            // from its redefinition in this class, instead of from
            // the definition in the parent class.
          
            info("ClassB_c: #MacroRangeB == " + int2str(#MacroRangeB)
                + " (Is now negative due to later redefinition.)");
        }
    }


    class ClassC extends ClassB
    {
        static void UseMacros()
        {
            //   This method shows that the #undef in the parent
            // class overwrites the #define in the grandparent class.
            //   This method also shows that a macro defined in the
            // grandparent class is in range in methods on this class.
            ;
            #ifnot.MacroRangeA
            info("ClassC_f: MacroRangeA is no longer defined, due to #undef in ClassB.");
            #endif
            info("ClassC_h: #MacroRange333 == " + int2str(#MacroRange333)
                + " (Defined in ClassA.)");
        }
    }


    class TestClass
    {
        static void JobClassesCC(Args _args)
        {
            ;
            ClassA ::UseMacros();
            ClassA ::UseOtherMethodMacro();
            ClassB ::UseMacros();
            ClassC ::UseMacros();
            /****************  Actual output
            Message (08:10:59 am)
            ClassA_a: #MacroRangeB == 22
            ClassA_k: This means MacroDefInMethodD is not in range here.
            ClassB_c: #MacroRangeB == -22 (Is now negative due to later redefinition.)
            ClassC_f: MacroRangeA is no longer defined, due to #undef in child class ClassB.
            ClassC_h: #MacroRange333 == 333 (Defined in ClassA.)
            ****************/
        }
    }

