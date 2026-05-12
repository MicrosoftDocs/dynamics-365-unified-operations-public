---
title: Extend the list of Electronic reporting (ER) functions
description: Learn about how to extend the list of electronic reporting functions through an overview of key tasks that you must complete to introduce a new function.
author: kfend
ms.author: filatovm
ms.topic: article
ms.date: 04/08/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: ERExpressionDesignerFormula
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 62c740dc-6a88-4ded-9c41-6857b82b335e
---

# Extend the list of Electronic reporting (ER) functions

[!include [banner](../includes/banner.md)]

Electronic reporting (ER) expressions support various types of functions for data transformation, including text, date and time, mathematical, logical, information, data type conversion, and other business domain–specific functions. In addition to built-in functions, you can extend the list of available functions in ER. This article provides an overview of key tasks that you must complete to introduce a new function.

> [!IMPORTANT]
> In Microsoft Dynamics 365 Finance, Enterprise edition 7.3, extensions of the **ERExpression** class are deprecated. Instead of using extensions of the **ERExpression** class to add custom built-in ER functions, implement your custom logic as public methods of your custom classes. Then, call those methods from ER formats and ER model mappings that configure the required ER data sources of either the [*Class*](er-formula-supported-data-types-composite.md#class) type or the [*Object*](er-formula-supported-data-types-composite.md#object) type. For more information, see [Design ER expressions to call application class methods](tasks/design-expressions-app-class-er.md).

All ER functions in application code are represented as classes that extend the **ERExpression** class. Two types of functions exist:

- **Fixed number of arguments** – These functions are represented by classes that include methods with the prefix **parm** (see **parmInput**, **parmStartNum** in the sample code that follows). The **SysOperationDisplayOrderAttribute** attribute sets the order of arguments.
- **Variable number of arguments** – These functions (see the **ERExpressionGenericCase** class) are represented by classes that implement the **ERIObjectContainer** interface. An additional **Add** method declares the types that a function accepts.

To introduce a new function for ER expressions, follow these steps:

- Select a base class for your function, based on the return value type (see **ERExpressionString** in the sample code that follows).

  - Create a new class that extends the selected class (see **ERExpressionStringMid** in the sample code that follows).

    - Add the required attributes:

      - **SysOperationLabelAttribute** – Defines the function’s name.
      - **SysOperationHelpTextAttribute** – Defines the function’s Help text.
      - **ERComponentGroupAttribute** – Defines the group that the function belongs to. For more information, see [Formula designer in Electronic reporting (ER)](general-electronic-reporting-formula-designer.md).

    - Add arguments:

      - For a fixed number of arguments function, add methods with the prefix **parm**, and use the **SysOperationDisplayOrderAttribute** attribute to set the order of the arguments.
      - For a variable number of arguments function, implement the **ERIObjectContainer** interface.

    - Add an evaluation method.

Here's an example.

```xpp
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
```

## Suggested guidance

The following guidance helps you design your custom ER functions:

- Reuse the names of Microsoft Excel functions whenever you can, so that ER formulas remain Excel-like. In this way, you keep ER formulas intelligible for end users.
- ER doesn't support list types for primitive data types. Therefore, use a data container list that has a single **Value** item in it.
- Release a new function's list extension as a new application hotfix. ER designers refer to the hotfix number in ER configurations that use that new custom function. Whenever you import a configuration of this type into a new instance, ER evaluates whether the required hotfix is installed, to maintain compliance between the ER configuration and the version that configuration is imported into.

## Additional resources

[Electronic reporting (ER) overview](general-electronic-reporting.md)

[Formula designer in Electronic reporting (ER)](general-electronic-reporting-formula-designer.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
