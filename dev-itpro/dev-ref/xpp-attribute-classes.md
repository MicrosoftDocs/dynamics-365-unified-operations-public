---
# required metadata

title: X++ attribute classes
description: This topic describes the use of attributes in X++.
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
ms.custom: 150243
ms.assetid: 9c927660-3268-4a77-9a83-97759a487483
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# X++ attribute classes

[!include[banner](../includes/banner.md)]


This topic describes the use of attributes in X++.

An attribute is a non-abstract class that extends (inherits from) the **SysAttribute** class. Attributes represent or store metadata about types and methods. An attribute can be attached to a class, an interface, or a method of a class, interface, or table.

## Creating an attribute class
An attribute class can extend the **SysAttribute** class directly, or it can extend any descendant of the **SysAttribute** class. The **SysAttribute** class cannot be used as an attribute because it is declared **abstract**. The following example shows the declaration and design of an ordinary attribute class that you could create.

    public class PracticeAttribute extends SysAttribute
    {
        // Fields in the classDeclaration.
        StartEnd startEndEnum;
        str reason;
        // Constructor.
        public void new(StartEnd _startEndEnum, str _reason)
        {
            startEndEnum  = _startEndEnum;
            reason = _reason;
        }
        // Other methods can go here.
    }

### Decorating a class with an attribute

The following example shows a class and a method that are decorated with the **PracticeAttribute** given in the previous example. If the constructor of the attribute takes no parameters, the parentheses for the parameters are optional. The attribute decoration could be `[AnotherAttribute]` without parentheses.

    [PracticeAttribute(StartEnd::End, "Use the RegularClass class at the end.")]
    public class RegularClass
    {
        [PracticeAttribute(Startend::Start, "Use the rehearse method at the start.")]
        public int rehearse()
        {
            // Logic goes here.
        }
        // More fields and methods belong here.
    }

### Attribute constructors

You can enable your attribute class to store tailored metadata each time it is used to decorate a class, by having its constructor take parameters. The parameters for the constructor must be literals of the primitive types, such as **int,** **enum,** or **str**. The compiler does not construct an instance of the attribute class. It stores the name of the attribute class, plus the literal values for its constructor. Therefore, if the logic in an attribute constructor would throw an exception, the exception would not be found by decorating a class with the attribute. The exception would be found later when a process looks at a class to see the attribute it is decorated with. That is when the attribute is constructed.

### Naming conventions

All attribute classes have the suffix **Attribute** in their name. The **Attribute** suffix is the name convention that we recommend, but it is not a system requirement. You can determine whether a class **extends** directly from **SysAttribute** by selecting the class in the **Application Explorer** and reviewing the **Extends** property in the **Properties** window.

## SysObsoleteAttribute
The system provides several attributes, including the **SysObsoleteAttribute** class. One use of the **SysObsoleteAttribute** class is to notify the compiler that the compile should fail if a particular method is called in the source code. The compiler rejects the compile, and displays the specific message that is stored in this use of the attribute. The **SysObsoleteAttribute** class can also be used to notify the compiler to issue warning messages instead of errors.

### SysObsoleteAttribute code example

    [SysObsoleteAttribute("The Automobile class might have faster performance.", false)]
    class Bicycle
    {
        // Members of the Bicycle class go here.
    }

## Metadata reflection
You use reflection to find the attribute metadata that is attached to a class. The classes to use for attribute reflection are as follows:

-   **DictClass** class – For classes and interfaces.
-   **DictMethod** class – For methods on classes, interfaces, or tables.

On the previous reflection classes, the methods for reflecting on attribute metadata are as follows:

-   **getAllAttributes** method
-   **getAttribute** method
-   **getAttributedClasses** method
-   **getAttributes** method

### Metadata reflection code example

You use the **DictMethod** class to find the metadata value of an attribute that is decoration on a method. The following code example uses the **SysEntryPointAttribute** class as the attribute. It accepts your parameter values for the method name, and for the name of the class that contains the method. The **parmChecked** method is particular to the **SysEntryPointAttribute** class, and it is not inherited from its base class **SysAttribute**. Each attribute class can have its own method name for its metadata.

    static public int MetadataOfSysEntryPointAttributeOnMethod
                (
                str _sNameOfClass,
                str _sNameOfMethod
                )
    {
        // Return Values:
        // 0 == Has the attribute, its metadata value is false;
        // 1 == Has the attribute, its metadata value is true;
        // 2 == The method lacks the SysEntryPointAttribute.
        int nReturnValue = -1,
            nClassId;
        boolean boolParmChecked;
        DictMethod dm;
        Object attributeAsObject;
        SysEntryPointAttribute sepAttribute;
        Global::info("Starting AttributeReflection" 
            + " ::MetadataOfSysEntryPointAttributeOnMethod ....");
        Global::info(strFmt
            ("Parameters are: _sNameOfClass = %1 ,  _sNameOfMethod = %2 .", 
            _sNameOfClass, _sNameOfMethod)
            );
        nClassId = Global::className2Id(_sNameOfClass);
        dm = new DictMethod
            (UtilElementType::ClassInstanceMethod,
            nClassId,
            _sNameOfMethod
            );
        attributeAsObject = dm.getAttribute("SysEntryPointAttribute");
        if (attributeAsObject is SysEntryPointAttribute)
        {
            sepAttribute = attributeAsObject as SysEntryPointAttribute;
            boolParmChecked = sepAttribute.parmChecked();
            if (boolParmChecked)
                nReturnValue = 1;
            else
                nReturnValue = 0;
            Global::info(
                strFmt("Return value is %1.",
                    nReturnValue)
                );
        }
        else
        {
            nReturnValue = 2;
            Global::error("Object is not a SysEntryPointAttribute??");
        }
        return nReturnValue;
    }
    /*** Output displayed in the Infolog.
    Message (05:03:22 pm)
    Starting AttributeReflection ::MetadataOfSysEntryPointAttributeOnMethod ....
    Parameters are: _sNameOfClass = CustCustomerService ,  _sNameOfMethod = create .
    Return value is 1.
    ***/
    /**************
    // Simple AOT > Jobs job to run the method.
    static void AttributeReflection33Job(Args _args)
    {
        AttributeReflection::MetadataOfSysEntryPointAttributeOnMethod
            ("CustCustomerService", "create");
    }
    **************/



