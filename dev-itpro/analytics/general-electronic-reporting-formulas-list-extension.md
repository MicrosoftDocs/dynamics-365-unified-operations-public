---
# required metadata

title: Extend the list of Electronic reporting functions
description: Various types of functions are supported in Electronic reporting expressions for data transformation -  text, date and time, mathematical logical, information, data type conversion, and other (business domain–specific functions). In addition to built-in functions, Electronic reporting lets you extend the list of available functions. This article includes an overview of key tasks that you must complete to introduce a new function.
author: kfend
manager: AnnBe
ms date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: ERExpressionDesignerFormula
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 71
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 58911
ms.assetid: 62c740dc-6a88-4ded-9c41-6857b82b335e
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Extend the list of Electronic reporting functions

Various types of functions are supported in Electronic reporting expressions for data transformation -  text, date and time, mathematical logical, information, data type conversion, and other (business domain–specific functions). In addition to built-in functions, Electronic reporting lets you extend the list of available functions. This article includes an overview of key tasks that you must complete to introduce a new function.

All Electronic reporting functions in Microsoft Dynamics 365 for Operations code are represented as classes that extend the **ERExpression** class. Two types of functions are recognized:

-   **Fixed number of arguments** – These functions are represented by classes that include methods that have the prefix **parm** (see **parmInput**, **parmStartNum** in the sample code the follows). The order of arguments is set by the **SysOperationDisplayOrderAttribute** attribute.
-   **Variable number of arguments** – These functions (see the **ERExpressionGenericCase** class) are represented by classes that implement the **ERIObjectContainer** interface. An additional **Add** method is used to declare the types that a function accepts.

Here are the recommended steps for introducing a new function for Electronic reporting expressions:

-   Select a base class for your function, based on the return value type (see **ERExpressionString** in the sample code that follows).
    -   Create a new class that extends the selected class (see **ERExpressionStringMid** in the sample code the follows).
        -   Provide required attributes:
            -   **SysOperationLabelAttribute** – This attribute defines the function’s name.
            -   **SysOperationHelpTextAttribute** – This attribute defines the function’s Help text.
            -   **ERComponentGroupAttribute** – This attribute defines the group that the function belongs to. (For more information, see [Formula designer in Electronic reporting](general-electronic-reporting-formula-designer.md).)
        -   Provide arguments:
            -   For a fixed number of arguments function, provide methods that have the prefix **parm**, and use the **SysOperationDisplayOrderAttribute** attribute to set the order of the arguments.
            -   For a variable number of argument function, implement the **ERIObjectContainer** interface.
        -   Provide an evaluation method.

Here is an example.

    /// <summary>
    /// Returns the characters from the middle of a text string, given a starting position and length.
    /// </summary>
    [
        SysOperationLabelAttribute ('MID'),
        SysOperationHelpTextAttribute ("@ElectronicReporting:ExpressionStringMidHelpText"),
        ERComponentGroupAttribute ("@ElectronicReporting:String")
    ]
    class ERExpressionStringMid extends ERExpressionString
    {
        ERExpressionString input;
        ERExpressionInt startNum;
        ERExpressionInt numChars;
        public str evaluateString(ERIDataContext _dataContext)
        {
            return subStr(
            this.parmInput().evaluateString(_dataContext),
            this.parmStartNum().evaluateInt(_dataContext),
            this.parmNumChars().evaluateInt(_dataContext));
        }
        [DataMemberAttribute, SysOperationLabelAttribute ("@ElectronicReporting:Input"), SysOperationDisplayOrderAttribute ("1")]
        public ERExpressionString parmInput(ERExpressionString _input = input)
        {
            input = _input;
            return input;
        }
        [DataMemberAttribute, SysOperationLabelAttribute ("@ElectronicReporting:NumChars"), SysOperationDisplayOrderAttribute ("3")]
        public ERExpressionInt parmNumChars(ERExpressionInt _numChars = numChars)
        {
            numChars = _numChars;
            return numChars;
        }
        [DataMemberAttribute, SysOperationLabelAttribute ("@ElectronicReporting:StartNum"), SysOperationDisplayOrderAttribute ("2")]
        public ERExpressionInt parmStartNum(ERExpressionInt _startNum = startNum)
        {
            startNum = _startNum;
            return startNum;
        }
        public str toString()
        {
            return ERExpressionStringPresenter::namedFunctionToStr(this);
        }
    }

## Suggested guidance
The following guidance is intended to help you design your custom Electronic reporting functions:

-   Reuse the names of Microsoft Excel functions whenever you can, so that Electronic reporting formulas remain Excel-like. In this way, you will keep Electronic reporting formulas intelligible for end users.
-   Electronic reporting doesn't support list types for primitive data types. Therefore, we have decided to use a data container list that has a single **Value** item in it.
-   Release a new function's list extension as a new Dynamics 365 for Operations hotfix. Electronic reporting designers will refer to the hotfix number in Electronic reporting configurations that use that new custom function. Whenever a configuration of this type is imported into a new instance of Dynamics 365 for Operations, Electronic reporting will evaluate whether the required hotfix has been installed, to maintain compliance between the Electronic reporting configuration and the Dynamics 365 for Operations version that configuration is imported into.


See also
--------

[Electronic reporting overview](general-electronic-reporting.md)

[Formula designer in Electronic reporting](general-electronic-reporting-formula-designer.md)

