---
title: Classes and methods
description: Learn how to create and use classes and methods in X++, including overviews on how to declare classes and create instances of objects.
author: pvillads
ms.author: pvillads
ms.topic: article
ms.date: 06/06/2025
ms.reviewer: twheeloc
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Classes and methods

[!include [banner](../includes/banner.md)]

This article describes how to create and use classes and methods in X++. Most of semantics and syntax of classes and methods are similar to the semantics from other programming languages, like Java or C#. Classes and methods in X++ map closely to classes and methods in the managed runtime. In fact, classes from .NET can be directly used from X++.

A *class* defines the data and methods of the instances that are later constructed from that class. The *class* is an abstraction of an *object* in the problem domain. The instances that can be constructed from the *class* are known as *instances* or *objects*. This article uses the term *instance*. The data represents the state of the object and the methods represent the behavior of the object.

*Fields* contain the data for the class. Every instance that's constructed from the class declaration has its own copy of the fields. These are known as *instance fields*. This article uses the term *field* in most cases.

*Methods* define the behavior of a class. They contain the statements that operate on the data. By default, methods are declared to operate on the instance fields of the class. These methods are known as *instance methods* or *object methods*.

You can declare *static methods* and *static fields* that don't have access to *instance fields*. For more information, see [X++ static classes](xpp-static-classes.md).

## Declare a class

You must use the **Add new item** dialog in Visual Studio to add a class to your project.

1. In Server Explorer, right-click the project, and then click **Add**.
2. In the **New item** dialog box, select **Installed > Dynamics 365 Items > Code** in the left navigation. Select **Class** and enter a name for the class.
3. Click **Add**.

All classes are public by default. If you remove the **public** modifier, the system still treats the class as public. You can specify other modifiers on the class declaration, such as **final**, **internal**, **static**, and **abstract**.

## Fields

Instance fields are **protected** by default. This means that they can only be accessed in the same class or [a derived class](xpp-inheritance.md). You can modify an instance field declaration by using the **private**, **protected**, or **public** keywords.

> [!NOTE]
> Making a member field public may not be a good idea since it exposes the internal workings of the class to its consumers, creating a strong dependency between the class implementation and its consumers. You should always strive to only depend on a contract, not an implementation.

You can assign a value to a field inline along with the declaration of the field itself. This applies to both static and instance fields. These values are assigned as the class is initialized (for instance classes), or when the static constructor (**typeNew**) is called.

The following example shows how to use accessor methods to make the field data public. The field **firstName** is protected, so accessor (get and set) methods are implemented to allow access to the protected field. The field **lastName** is public, code can get and set the value of the field.

```xpp
// This is the class definition.
public class HasAFirstName
{
    str firstName = ""; // protected by default
    public str lastName = "";

    public str getFirstName()
    {
        return firstName;
    }

    public void setFirstName(str newName)
    {
       firstName = newName;
    }
}

// This code creates an instance of the class and gets the fields.
public static void TestLastName()
{
    HasAFirstName hasFirstName = new HasAFirstName();
    
    hasFirstName.setFirstName("Dion");
    info(hasFirstName.getFirstName());

    hasFirstName.lastName = ("Townes");
    info(hasFirstName.lastName);
}
// The output is "Dion" and "Townes".
```

### Field attributes

You can decorate a field with an attribute, in the same way that attributes can decorate classes and methods. The following example decorates the **myField** field with the **MyAtribute** attribute.

```xpp
class MyClass
{
    [MyAttribute]
    public int myField;
}
```

A useful attribute is the **SysObsolete** attribute. If the **SysObsolete** attribute is applied to a field, the compiler generates an error or warning on any reference to the field. Whether it's a warning or error depends on the second parameter in the attribute, as shown below:

```xpp
class MyClass
{
    // Generate an error (because the second attribute parameter is true) 
    // if the field is referenced.
    [SysObsolete("This field is obsolete.", true)]
    public int myField;
}
```

## Constructors

To create an instance of a class, you must instantiate it. The class is instantiated by using the **new** keyword. When the **new** expression is evaluated, memory is allocated on the heap for that state, and the *constructor* is called.

 - You can define only one **new** method (constructor) in a class.
 - If you don't define a constructor, a default constructor with no parameters is created automatically by the compiler.
 - You can simulate a default constructor by assigning default values to the parameters in the **new** method.

The following example defines a parameterless constructor in the **Point** class.

```xpp
class Point
{

    // Public instance fields. In practice, you should make these protected or private
    // and create accessor methods.
    public real x = 0.0;
    public real y = 0.0;

    void new() 
    {
    }
}
```

To create a clean inheritance model and minimize problems when code is upgraded, follow these steps:

 - Each class must have a single public construction method unless the class is abstract.
 - Each class should have at least one static **construct** method.
 - Each class should have a **new** method (the constructor). This method should be **protected**.
 - Create accessor methods to get and set class fields.
 - Create **init** methods to carry out any specialized initialization tasks after instantiation.

## Create an instance of an object

The constructor, **new**, returns a new instance of the class. The following code example creates two instances of the Point class.

```xpp
// Declare a field to refer to a Point instance.
Point myPoint; // the default value is null.

// Create an instance of the Point class.
myPoint = new Point();
```

## Destructors

Instances are automatically destroyed when there are no references to them. 

### Use the finalize method

Use the **finalize** method to explicitly clean up the state of an object. This is a convention, there's no special semantics for this method, and no implicit calls made to the **finalize** method when the object is disposed by the managed runtime. You must call the method to explicitly clean up. In most cases, you don't need to provide final methods.

### Set reference variable to null

Set the reference variable to **null** to terminate an object. This approach destroys an object only if no other variables point to that object. You should verify that other code isn't using the variable. The following example creates a reference variable and sets it to **null**.

```xpp
Point myPoint = new Point();
myPoint = null;
```

## Methods

### Instance methods

Instance methods are called with an instance of the class so you must instantiate the object before you can use the method. The following code shows how to define an instance method and call it from an instance.

```xpp
class Square
{
    private int side = 0;

    public void new(int _side = 1) 
    {
        side = _side;
    }

    public int getArea() 
    {
        return side * side;
    }

}

// This code creates an instance of Square and calls getArea.
Square square = new Square(15);
int area = square.getArea();
info(int2Str(area));
// Output is "225".
```

### Static methods

Static methods, which are also known as *class methods*, belong to a class and are defined by using the **static** keyword. You don't have to instantiate an object before you use static methods. Static methods can access the values of the class static fields and call static methods.

You use the following syntax to call static methods.

```xpp
ClassName::methodName();
```

### Main methods

A **main** method is a class method that can be run directly from a menu option. The **\_args** parameter lets you transfer data to the method.

```xpp
static void main (Args _args)
{
    // Your code here.
}
```

### Declaration of methods

Method declarations consist of a header and a body. The method header declares the method's name and return type, the method modifiers, and parameters. (The return type might be **void**.) The method body consists of variable declarations, local function declarations, and statements.

### Return type

A return type is required for each method. If a method doesn't return anything, use the **void** keyword as the return type.

The following example shows two methods. One method has a return type, and the other method doesn't have a return type.

```xpp
void methodWithNoReturnValue()
{
    // Your code here.
    // ...
    // The return statement can be provided without parameters
    return; 
    
    // There's an implicit return when the method flow reaches the end.
}

// If a method returns something, you must specify the return type and include a return statement.
int methodNameIntegerReturnValue()
{
    return 1;
}
```

### Syntax

Method declaration = *Heading* *Body* Heading = **\[** *Modifiers* **\]**  *ReturnType*  *MethodName*  **(** *ParameterList* **)**

Modifiers = **\[edit | display \] \[ public | protected | private \] \[static | abstract | final \]**

ReturnType = *Datatype*  **| void***

MethodName = *Identifier*

ParameterList = **\[** *Parameter* **{ ,** *Parameter* **}\]**

Parameter = *Datatype* *Variableidentifier* **\[ =** *Expression* **\]**

Body = { *Statement* }

Statement = *VariableDeclarationStatement* | *EmbeddedFunctionDeclarationStatement* | ... 

EmbeddedFunctionDeclaration = *Heading* **{\[** *VariableDeclarations* **\] \[** *Statements* **\]}**

### Example of a method that doesn't have a return type

```xpp
void update ()
{
    // Field declared and initialized
    CustTable this_Orig = this.orig();

    // First statement in body (begin transaction)
    ttsBegin;
    this.setNameAlias();
    // Calls super's implementation of update
    super();
    this.setAccountOnVend(this_Orig);
    if (this_Orig.custGroup != this.custGroup)
        ForecastSales::setCustGroupId(
            this.accountNum,
            this_Orig.custGroup,
            this.custGroup);
    // Commits transaction
    ttsCommit;
}
```

### Example of a method that has parameters

In the following example, the **checkAccountBlocked** method returns a Boolean value and acts on the **amountCur** parameter.

```xpp
boolean checkAccountBlocked(AmountCur amountCur)
{
    if (this.blocked == CustVendorBlocked::All
       || (this.blocked == CustVendorBlocked::Invoice && amountCur > 0 ))
    {
        return checkFailed(strFmt("@SYS7987",this.accountNum));
    }
    return true;
}
```

## Method modifiers

Several modifiers can be applied to method declarations. Some of the modifiers can be combined (for example, **final static**). Here are the method modifier keywords:

 - **abstract** - The method is declared but isn't implemented. The method must be overridden in all subclasses. If you try to create an object from a subclass where one or more abstract methods that belong to the parent class haven't been overridden, you receive a compiler error. Abstract methods can only be defined in abstract classes.

Classes can also be abstract. Sometimes, a class shouldn't be instantiated because it represents an abstract concept. Only subclasses should be instantiated. Base classes of this type can be declared as **abstract**. For example, you want to model the concept of an account. Accounts are abstract entities, because only derived classes (savings accounts, and so on) exist in the real world. This example describes a clear case where you should declare the **Account** class as **abstract** and have derived classes for CheckingAccount, SavingsAccount, and so on.
 - **display** - The method's return value should be shown on a page or a report. The value can't be modified on the page or report. Typically, the return value is a calculated value, such as a sum.
 - **edit** - The method's return type used to provide information for a field that is used on a page. The value in the field can be modified.
 - **final** - The method can't be overridden in any class that derives from its class.
 - **public** - Methods that are declared as **public** can be accessed anywhere that the class is accessible, and they can be overridden by subclasses. Methods without an access modifier are implicitly public.
 - **protected** - Methods that are declared as **protected** can only be called from methods in the class and in subclasses that extend the class where the method is declared.
 - **private** - Methods that are declared as **private** can only be called from methods in the class where the private method is declared.
 - **internal** - Methods that are declared as **internal** can only be called from methods in the class that are defined in the same model as the class where the method is defined.
 - **static** - The method is a class method. Static methods can't refer to instance fields. They aren't invoked on an instance of the class. Instead, they're invoked by using the class name (for example, **MyClass::aStaticProcedure()**).

### Methods that have modifiers

The following examples only show the method headers.

```xpp
// A method that can't be overridden
final int dontAlterMe()

// A static method
static void noChange()

// A display method that returns an integer
display int value()
```

## Method access control

You use the accessor keywords **public**, **protected**, and **private** to control if the methods in other classes can call the methods on your class. The accessor keywords on methods also interact with the rules for class inheritance. 

The accessor keywords that you use with methods:
 - **public** - Methods that are declared as **public** can be called from anywhere that the class is accessible. In addition, a public method can be overridden by a subclass, unless the method is declared as **final**.
 - **protected** - Methods that are declared as **protected** can only be called from the following methods:
      - Methods in the class.
      - Methods in a subclass of the class that contains the protected method. Methods that are protected can be overridden in subclasses.
 - **private** - Methods that are declared as **private** can only be called from methods in the class where the private method is declared. No private method can be overridden in a subclass. You should hide implementation details as private methods to make maintenance of your code easier.

### Static and instance methods

The accessor keywords on methods never restrict calls between two methods that are in the same class, regardless of which method is static or nonstatic. In a static method, calls to the **new** constructor method are valid even if the **new** constructor method is decorated with the **private** modifier. The syntax for these calls requires that the **new** keyword be used. The code in a static method must construct an instance object of its own class before it can call any instance methods on the class.

### Increasing access during overrides

When a method is overridden in a subclass, the overriding method must be at least as accessible as the overridden method. For example, the following compiler rules apply when a protected method is overridden in a subclass:
 - A public method in a superclass can be overridden only by a public method in the subclass.
 - In a subclass, a public or protected method can override a protected method of the superclass.
 - In a subclass, a private method can't override a protected method of the superclass.

## Optional parameters

Parameters can be initialized in the method declaration parameter list. In this case, the parameter becomes an *optional parameter*. If no value is supplied in the method call, the default value is used. All required parameters must be listed before the first optional parameter. The following examples show how to create and call a method that has optional parameters. 

### Optional parameters examples

The following code example shows a method with a default parameter.

```xpp
class Person
{
    date birthDate;

    // The constructor that takes a date type as a parameter.
    // That value is assigned to the field member birthDate.
    void new(date _date)
    {
        birthDate = _date;
    }

    // The CalculateAgeAsOfDate method references the birthDate field and has an
    // optional parameter.
    public real CalculateAgeAsOfDate(
        date _calcToDate = DateTimeUtil::getToday(DateTimeUtil::getUserPreferredTimeZone()))
    {
        return (_calcToDate - birthDate) / 365;
    }

    public static void callPerson()
    {
        var person = new Person(13\5\2010);

        // Optional parameter's default is used.
        Info(strFmt('Age in years today is %1 years',
                real2int(person.calculateAgeAsOfDate())));

        // January 2, 2044  is the parameter value for _date.
        Info(strFmt('Age in years on %1 is %2 years',
                2\1\2044,
                real2int(person.calculateAgeAsOfDate(2\1\2044))));
    }
}
```

This shows how you can't skip to a second optional parameter. The **addThreeInts** method has two optional parameters. The **callAdditions** method calls the **AddThreeInts** method. The commented out code tries to provide a value only to the **\_i3** parameter (but not for **\_i2**), but the compiler requires that all prior mandatory and optional parameters also be provided in the call.

```xpp
class Additions
{
    public static int addThreeInts(int _i1, int _i2 = 2,int _i3 = 3)
    {
        return _i1 + _i2 + _i3;
    }

    public static void callAdditions()
    {
        // The next statement doesn't compile, because it skips the _i2 parameter.
        // info(int2Str(Additions::AddThreeInts(1, , 99)));

        // These are legal
        info(int2Str(Additions::AddThreeInts(1, 2)));
        info(int2Str(Additions::AddThreeInts(1, 2, 99)));
    }

}
```

## Accessor methods

Class fields are protected by default. By hiding details of the internal implementation of a class, you can change the implementation of the class later without breaking any code that uses that class. To access the data from reference fields from outside, you should create accessor methods. The following example defines a **Point** class that uses accessor methods to access the fields **x** and **y**.

```xpp
class Point
{
    // Instance fields
    real x;
    real y;

    void new(real _x = 10, real _y = 10)
    {
        x = _x;
        y = _y;
    }

    // Accessor methods
    void setX(real _x)
    {
        x = _x;
    }

    void setY(real _y)
    {
        y = _y;
    }

    real getX()
    {
        return x;
    }

    real getY()
    {
        return y;
    }
}
```
These method declarations show how the **Point** class provides access to its fields from the outside world. Other objects can manipulate the instance fields of **Point** objects by using the accessor methods.

```xpp
Point myPoint = new Point();
// Set the x fields using the accessor method.
myPoint.setX(4.0);
// Get the x fields using the accessor method.
info(any2Str(myPoint.getX()));
```

There are other ways to implement the accessors to private fields. Consider the following method:

```xpp
    public int parmX(int _x = x)
    {
        x = _x;
        return x;
    }
```

There's another way where the prmIsDefault predefined function is used to determine at runtime if the parameter was provided when the methods were called.

```xpp
    public int parmX(int _x = x)
    {
        if (!prmIsDefault(_x))
        {
            // This is the setter. Do something with the incoming value...
            x = _x + 2;
        }
        return x;
    }
```

In both cases the *parm* method can be called with a parameter, which sets the field, or without parameters, which returns it. In this way, there's only one accessor method instead of two. In any case, the convention is to use a naming convention to identify these methods, naming them with a "parm" prefix.

## Parameters

All methods define their own *scope*. Within the scope of the method, the parameters are treated as local variables and are initialized with a value from the expression in the method call. All parameters are passed by value, if a variable is used as a parameter value in the call, that variable won't reflect any changes made to the parameter.

## Scope of variables in methods

A scope defines the area in which an item can be accessed. Variables that are defined in a class are available to the methods within that class. Variables in methods can be accessed only within the current block. Compound statements and local function declarations all establish their own nested scopes.

## Local functions

You can declare functions inside a method. These are called local functions.

 - You can declare more any number of local function in your method.
 - Code that's inside the local function can access variables that are declared before it's in the method that contains the local function.
 - Code that's outside the local function can't access variables that are declared in the local function.
 - A local function can only be called by code in the method where the local function is declared.

The following example shows valid declarations of two local functions, **localFunctionA** and **localFunctionB**. Calls to the local functions occur after the function declarations as required.

```xpp
static void StaticFunction()
{
    int number = 654;

    void localFunctionA(int _iNum)  // The local function.
    {
        str innerString = "String in localFunctionA";
        str output = strFmt("localFunctionA: %1 , %2 , %3", _iNum, innerString, number);
        info(output);
    }

    int outer = 42;
    void localFunctionB()
    {
        info("Printing from inside localFunctionB. " + int2str(outer));
    }

    localFunctionA(55);
    localFunctionB();

    // Next info statement would fail to compile,
    // because innerString is restricted to the
    // scope of the local function in which it is declared.
    // print innerString;
}

// When called, the output is:
// localFunctionA: 55 , String in localFunctionA , 654
// Printing from inside localFunctionB. 42
```

## Extension methods

The extension method feature adds extension methods to a target class by writing the methods in a separate extension class. From the user's perspective, it's if the extension method was written on the extended method. The following rules apply:

- The extension class must be static.
- The name of the extension class must end with the ten-character suffix \_Extension. However, there's no restriction on the part of the name that precedes the suffix.
- Every extension method in the extension class must be declared as public static.
- The first parameter in every extension method is the type that the extension method extends. However, when the extension method is called, the caller must not pass in anything for the first parameter. Instead, the system automatically passes in the required object for the first parameter.

It's perfectly valid to have private or protected static methods in an extension class. These are typically used for implementation details and aren't exposed as extensions. The example below illustrates an extension class holding a few extension methods:

```xpp
public static class AtlInventLocation_Extension
{
    // This method is available on the InventLocation type.
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
```

### Reasons to use extension methods

The extension method technique doesn't affect the source code of the class it extends. Upgrades to the target class are never affected by any existing extension methods. However, if an upgrade to the target class adds a method that has the same name as your extension method, your extension method becomes unreachable through objects of the target class. Extension methods are easy to use. The extension method technique uses the same dot-delimited syntax that you routinely use the call regular instance methods. Extension methods can access all public artifacts of the target class, but they can't access things that are protected or private. 

### Where can extension methods be applied

The target of an extension method must be one of the following application object types:

- Class
- Table
- View
- Map

Regardless of the target type, an extension *class* is used to add extension methods to the type. For example, an extension table isn't used to add methods to a table, and there's no such thing as an extension table.

## The this keyword

The **this** keyword is a reference to the instance of the class or table where the **this** keyword is used. The **this** reference is required on instance method calls (if the method called in on a class in the class or any of its superclasses), but it can clarify your code and enhances the behavior of IntelliSense in the code editor. All calls to instance methods must be qualified by either the **this** reference or a variable. The **this** reference can be used to qualify the following information:

 - The names of other instance (nonstatic) methods in the same class where the **this** reference is used. Here's an example: `boolColorChanged = this.colorItOrange();`
 - The names of methods that are inherited by the **this** object.
 - The names of fields on the table that contains the method that the **this** keyword is used in.

The **this** reference can't be used in the following ways:
 - It can't qualify the names of member variables that are declared in the **classDeclaration** code.
 - It can't be used in a static method.
 - It can't qualify the names of static methods of the class or table.

## Nested classes

Classes can be nested in X++ source code. Nested classes are available only inside forms (that is, classes that extend FormRun) to represent controls, data sources, or data fields.

## Jobs

To quickly and easily run an X++ method, add a `static Main(xArgs args)` method to a class, and set the class as the startup object form for the project in Microsoft Visual Studio. When the project is run, the `Main` method is executed.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
