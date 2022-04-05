---
title: Classes and methods
description: This topic describes how to create and use classes in X++.
author: RobinARH
ms.date: 08/27/2021
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: tfehr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Classes and methods

[!include [banner](../includes/banner.md)]

This topic describes how to create and use classes in X++.

A *class* is a software construct that defines the data and methods of the instances that are later constructed from that class. The *class* is an abstraction of an *object* in the problem domain. The instances that are constructed from the *class* are known as *instances* or *objects*. This topic uses the term *instance*. The data represents the state of the object, whereas the methods represent the behavior of the object.

*Variables* contain the data for the class, and are called *fields*. Every instance that is constructed from the class declaration has its own copy of the variables. These variables are known as *instance variables* or *instance fields*. This topic will use the term *field* in most cases.

Methods define the behavior of a class. They are the sequences of statements that operate on the data (instance fields). By default, methods are declared to operate on the instance fields of the class. These methods are known as *instance methods* or *object methods*.

You can declare *static methods* and *static fields*, that do not have access to *instance fields*. These are described in [X++ static classes](xpp-static-classes.md).

## Declare a class

You must use the **Add new item** dialog in Visual Studio to add a class to your project.

1. In Server Explorer, right-click the project, and then click **Add**.
2. In the **New Item** dialog box, select **Installed > Dynamics 365 Items > Code** in the left navigation. Then select **Class**, and then enter a name for the class.
3. Click **Add**.

All classes are public. If you remove the **public** modifier, the system still treats the class as public. You can specify other modifiers on the class declaration, such as **final** and **extends**.

## Fields

Instance fields are **protected** by default. This means that they can only be accessed in the same class or [a derived class](xpp-inheritance.md). You can modify an instance field declaration by using the **private**, **protected**, or **public** keywords.

> [!NOTE]
> Making a member field public may not be a good idea since it exposes the internal workings of the class to its consumers, creating a strong dependency between the class implementation and its consumers. You should always strive to only depend on a contract, not an implementation.

You can assign a value to a field inline, that is, along with the declaration of the field itself. This applies to both static and instance fields.

The following example shows how to use accessor methods to make the field data public. The field **firstName** is protected, so accessor (get and set) methods are implemented to allow access to the protected field. The field **lastName** is public, so code can directly get and set the value of the field.

```xpp
// This is the class definition.
public class HasAFirstName
{
    str firstName = "";
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

One particularly useful attribute is the **SysObsolete** attribute. If the **SysObsolete** attribute is applied to a field, then the compiler generates an error or warning on any reference to the field. Whether it's a warning or error depends on the second parameter in the attribute.

```xpp
class MyClass
{
    [SysObsolete("This field is obsolete.", true)]
    public int myField;
}
```

## Constructors

To create an instance of a class, you must instantiate it by using a *constructor*.

+ You can define only one **new** method (constructor) in a class.
+ If you do not define a constructor, a default constructor with no parameters is created automatically by the compiler.
+ You can simulate a default constructor by assigning default values to the parameters in the **new** method.

The following example defines a parameterless constructor in the **Point** class.

```xpp
class Point
{

    // Instance fields that are public. In practice, you would probably make this protected or private.
    // and create accessor methods.
    public real x = 0.0;
    public real y = 0.0;

    void new() {
    }
}
```

Following is information about how to create a clean inheritance model and minimize problems when code is upgraded:

+ Each class must have a single public construction method unless the class is abstract. If no initialization is required, use a static construct method. Otherwise, use a static **new** method (the default constructor for the class should be protected).
+ Each class should have at least one static **construct** method.
+ Each class should have at least one static **new** method.
+ Each class should have a **new** method (the default constructor). This method should be **protected**.
+ Create accessor methods to get and set class fields.
+ Create **init** methods to carry out any specialized initialization tasks that should be carried out after instantiation.

### Create other objects in a constructor

A class constructor can instantiate other objects in addition to creating an instance of the class. For example, the following code declares a **Rectangle** class that uses two **Point** objects to define its bounds. In this case, the **Point** class has a constructor that has two **real** parameters.

```xpp

class Point
{
    // Instance fields that are public. In practice, you would probably make this protected or private.
    // and create accessor methods.
    public real x = 0.0;
    public real y = 0.0;

    // Constructor to initialize to a specific or default value
    void new(real _x = 10, real _y = 10)
    {
        x = _x;
        y = _y;
    }
}

class Rectangle
{
    public Point lowerLeft;
    public Point upperRight;

    void new(real _topLeftX = 0.0, real _topLeftY = 0.0, real _bottomRightX = 1.0, real _bottomRightY = 1.0)
    {
        lowerLeft  = new Point(_topLeftX, _topLeftY);
        upperRight = new Point(_bottomRightX, _bottomRightY);
    }

}

// This code creates two instances of the Rectangle class.
Rectangle defaultRectangle = new Rectangle();
info(any2Str(defaultRectangle.lowerLeft.x));
info(any2Str(defaultRectangle.lowerLeft.y));
// Output is "0.0" and "0.0".

Rectangle customRectangle = new Rectangle(1.0, 1.0, 2.0, 2.0);
info(any2Str(customRectangle.lowerLeft.x));
info(any2Str(customRectangle.lowerLeft.y));
// Output is "1.0" and "1.0".
```

## Create an instance of an object

The constructor, **new**, returns a new instance of the class. The following code example creates two instances of the Point class.

```xpp
// Declare a field to refer to a Point instance.
Point myPoint;

// Create an instance of the Point class.
myPoint = new Point();

// Declare and instantiate a Point instance.
Point ap = new Point();
```

## Destructors

You use a *destructor* to explicitly destroy a class instance. Instances are automatically destroyed when there are no references to them. However, you can destroy objects explicitly in the following ways:

+ Use the **finalize** method.
+ Set the reference variable to **null**.

### Use the finalize method

Use the **finalize** method to explicitly destroy an object. There are no implicit calls to the **finalize** method. You must call the method to run the statements in it. In the **finalize** method, you should also put any clean-up code that is required. For example, if your class uses a dynamic-link library (DLL) module, you can use the **finalize** method to release the DLL when you no longer require it. Use the **finalize** method carefully. It will destroy an object even if there are references to it.

The following example shows the basic structure for a call to the **finalize** method.

```xpp
// From any method in a class.
if (condition)
{
    // Removes object from memory.
    this.finalize();
}
```

### Set reference variable to null

Set the reference variable to **null** to terminate an object. This approach destroys an object only if no other variables point to that object. You should verify that other code isn't using the variable. The following example creates a reference variable and then sets it to **null**.

```xpp
Point myPoint = new Point();
myPoint = null;
```

## Methods

### Instance methods

Instance methods are embedded in each instance that is created from the class. You must instantiate the object before you can use the method. The following code shows how to define an instance method and call it from an instance.

```xpp
class Square
{

    int side = 0;

    void new(int _side = 1) {
        side = _side;
    }

    int getArea() {
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

Static methods, which are also known as *class methods*, belong to a class and are created by using the keyword **static**. You don't have to instantiate an object before you use static methods. Static methods are often used to work with data that is stored in tables. Member fields can't be accessed from a static method.

You use the following syntax to call static methods.

```xpp
ClassName::methodName();
```

If you convert an instance method to a static method, you must restart the client. Otherwise, the compiler doesn't detect the change. After you've converted an instance method to a static method, you can no longer call the method from the instance of the class. Instead, you must call the method from the class itself. For more information about static methods, see [X++ static classes](xpp-static-classes.md).

### main methods

A **main** method is a class method that is run directly from a menu option. The method should only create an instance of the object and then call the required member methods. The **\_args** parameter lets you transfer data to the method.

```xpp
static void main (Args _args)
{
    // Your code here.
}
```

### Declaration of methods

Method declarations consist of a header and a body. The method header declares the method's name and return type), the method modifiers, and parameters. (The return type might be **void**.) The method body consists of fields declarations, method declarations, and statements.

### Return type

A return type is required for each method. If a method doesn't return anything, use the **void** keyword as the return type.

The following example shows two methods. One method has a return type, but the other method doesn't have a return type.

```xpp
void methodNameNoReturnValue()
{
    // Your code here.
}

// If a method returns something, you must specify the return type and include a return statement.
int methodNameIntegerReturnValue()
{
    return 1;
}
```

### Syntax

Method declaration = *Heading*  *Body* Heading = **\[** *Modifiers* **\]**  *ReturnType*  *MethodName*  **(**  *ParameterList*  **)**

Modifiers = **\[client\] \[server\] \[edit | display | public | protected | private\] \[static | abstract | final \]**

ReturnType = *Datatype*  **| void | anytype**

MethodName = *Identifier*

ParameterList = **\[** *Parameter*  **{ ,**  *Parameter*  **}\]**

Parameter = *Datatype*  *Variableidentifier*  **\[ =**  *Expression*  **\]**

Body = **{ \[**  *VariableDeclarations*  **\] \[**  *EmbeddedFunctionDeclarations*  **\] \[**  *Statements*  **\] }**

EmbeddedFunctionDeclaration = *Heading*  **{\[**  *VariableDeclarations*  **\] \[**  *Statements*  **\]}**

If you use the **anytype** return type, the method can return any data type.

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
        ||(this.blocked == CustVendorBlocked::Invoice
        && amountCur > 0 ))
    return checkFailed(strFmt("@SYS7987",this.accountNum));
    return true;
}
```

## Method modifiers

Several modifiers can be applied to method declarations. Some of the modifiers can be combined (for example, **final static**). Here are the method modifier keywords:

+ **abstract**: The method is declared but isn't implemented in a parent class. The method must be overridden in subclasses. If you try to create an object from a subclass where one or more abstract methods that belong to the parent class haven't been overridden, you receive a compiler error.

    Classes can also be abstract. Sometimes, a class should not be instantiated even though it represents an abstract concept. Only subclasses should be instantiated. Base classes of this type can be declared as **abstract**. For example, you want to model the concept of an account. Accounts are abstract, because only derived classes (ledger accounts and so on) exist in the real world. This example describes a clear case where you should declare the **Account** class as **abstract**.
+ **display**: The method's return value should be shown on a page or a report. The value can't be modified on the page or report. Typically, the return value is a calculated value, such as a sum.
+ **edit**: The method's return type should be used to provide information for a field that is used on a page. The value in the field can be modified.
+ **final**: The method can't be overridden in any class that derives from its class.
+ **public**: Methods that are declared as **public** can be accessed anywhere that the class is accessible, and they can be overridden by subclasses. Methods that have no access modifier are implicitly public.
+ **protected**: Methods that are declared as **protected** can be called only from methods in the class and in subclasses that extend the class where the method is declared.
+ **private**: Methods that are declared as **private** can be called only from methods in the class where the private method is declared.
+ **static**: The method is a class method and doesn't act on an instance. Static methods can't refer to instance fields. They aren't invoked on an instance of the class. Instead, they are invoked by using the class name (for example, **MyClass::aStaticProcedure()**).

### Methods that have modifiers

The following examples show only the method headers.

```xpp
// A method that cannot be overridden
final int dontAlterMe()

// A static method
static void noChange()

// A display method that returns an integer
display int value()
```

## Method access control

You use the accessor keywords **public**, **protected**, and **private** to control whether the methods in other classes can call the methods on your class. The accessor keywords on methods also interact with the rules for class inheritance. Here are the accessor keywords that you use with methods:

+ **public**: Methods that are declared as **public** can be called from anywhere that the class is accessible. In addition, a public method can be overridden by a subclass, unless the method is declared as **final**.
+ **protected**: Methods that are declared as **protected** can be called only from the following methods:
    + Methods in the class.
    + Methods in a subclass of the class that contains the protected method. Methods that are protected can be overridden in subclasses.
+ **private**: Methods that are declared as **private** can be called only from methods in the class where the private method is declared. No private method can be overridden in a subclass. By default, when you create a new method, the **private** accessor keyword appears in the code editor. For maximum security, **private** is the most conservative default accessor keyword.

### Static and instance methods

The accessor keywords on methods never restrict calls between two methods that are in the same class, regardless of which method is static or non-static. In a static method, calls to the **new** constructor method are valid even if the **new** constructor method is decorated with the **private** modifier. The syntax for these calls requires that the **new** keyword be used. The code in a static method must construct an instance object of its own class before it can call any instance methods on the class.

### Increasing access during overrides

When a method is overridden in a subclass, the overriding method must be at least as accessible as the overridden method. For example, the following compiler rules apply when a protected method is overridden in a subclass:

+ A public method in a superclass can be overridden only by a public method in the subclass.
+ In a subclass, a public or protected method can override a protected method of the superclass.
+ In a subclass, a private method can't override a protected method of the superclass.

## Optional parameters

Parameters can be initialized in the method declaration. In this case, the parameter becomes an *optional parameter*. If no value is supplied in the method call, the default value is used. All required parameters must be listed before the first optional parameter. The following examples show how to create and call a method that has optional parameters. The example of the **AddThreeInts** method shows that you can't skip default parameters when you call a method.

### Examples of optional parameters

The following code example shows a class with a default parameter.

```xpp
// This is an example of a function being used as the default.
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
    // optional parameter. In this example, the default value is the
    // return value of a function.
    public real CalculateAgeAsOfDate(date _calcToDate = DateTimeUtil::getToday(DateTimeUtil::getUserPreferredTimeZone()) )
    {
        return (_calcToDate - birthDate) / 365;
    }

    public static void callPerson()
    {

        Person person = new Person(13\5\2010);

        // Optional parameter's default is used.
        Info(strFmt('Age in years today is %1 years',
                real2int(person.CalculateAgeAsOfDate())));

        // January 2, 2044  is the parameter value for _date.
        Info(strFmt('Age in years on %1 is %2 years',
                2\1\2044,
                real2int(person.CalculateAgeAsOfDate(2\1\2044))));
    }

}
```

This is an example of how you cannot skip to a second optional parameter. The **AddThreeInts** method has two optional parameters. The **callAdditions** method calls the **AddThreeInts** method. The commented out code tries to override only the **\_i3** default value, but the compiler requires that all prior optional parameters also be overridden in the call.

```xpp
class Additions
{
    public static int AddThreeInts(int _i1, int _i2 = 2,int _i3 = 3)
    {
        return _i1 + _i2 + _i3;
    }

    public static void callAdditions()
    {
        // The next statement does not compile, because it skips the _i2 parameter.
        // info(int2Str(Additions::AddThreeInts(1, , 99)));

        // You must specify both optional parameters.
        info(int2Str(Additions::AddThreeInts(1, 2, 99)));
    }

}
```

## Accessor methods

Class fields are protected by default. By hiding details of the internal implementation of a class, you can change the implementation of the class later without breaking any code that uses that class. To access the data from reference fields, you must create accessor methods. The following example defines a **Point** class that uses accessor methods to access the fields **x** and **y**.

```xpp
class Point
{
    // Instance fields
    real x;
    real y;

    // Constructor to initialize to a specific or default value
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

## Parameters

All methods have their own *scope*. A method can take one or more parameters. Within the scope of the method, these parameters are treated as local variables and are initialized with a value from the parameter in the method call. All parameters are passed by value, which means that you can't change the value of the original variable. You can change only the local variable in the method. This local variable is a copy of the original variable.

## Scope of variables in methods

A scope defines the area in which an item can be accessed. Variables that are defined in a class are available to the methods within that class. Variables in methods can be accessed only within the current block.

## Local functions

You can declare functions inside a method. These are called local functions. While possible, it is not a best practice. Instead, you should add private methods to the class.

+ The declarations of local functions must physically precede any non-declaration statements in the method.
+ You can declare more than one local function in your method. However, all local functions must be declared in an uninterrupted series.
+ Code that is inside the local function can access variables that are declared in the method that contains the local function.
+ Code that is outside the local function can't access variables that are declared in the local function.
+ A local function can be called only by code in the same method where the local function is declared.
+ A local function should never call itself. Such recursion can prevent successful compilation.

The following example shows valid declarations of two local functions, **localFunctionA** and **localFunctionB**. Calls to the local functions occur after the function declarations in the example, as is required.

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

    void localFunctionB()
    {
        info("Printing from inside localFunctionB.");
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
// Printing from inside localFunctionB.
```

## Extension methods

The extension method feature lets you add extension methods to a target class by writing the methods in a separate extension class. The following rules apply:

- The extension class must be static.
- The name of the extension class must end with the ten-character suffix \_Extension. However, there's no restriction on the part of the name that precedes the suffix.
- Every extension method in the extension class must be declared as public static.
- The first parameter in every extension method is the type that the extension method extends. However, when the extension method is called, the caller must not pass in anything for the first parameter. Instead, the system automatically passes in the required object for the first parameter.

It's perfectly valid to have private or protected static methods in an extension class. These are typically used for implementation details and are not exposed as extensions. The example below illustrates an extension class holding a few extension methods:

```xpp
public static class AtlInventLocation_Extension
{
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

The extension method technique doesn't affect the source code of the class it extends. Therefore, the addition to the class can be done without over-layering. Upgrades to the target class are never affected by any existing extension methods. However, if an upgrade to the target class adds a method that has the same name as your extension method, your extension method becomes unreachable through objects of the target class. Extension methods are easy to use. The extension method technique uses the same dot-delimited syntax that you routinely use the call regular instance methods. Extension methods can access all public artifacts of the target class, but they can't access things that are protected or private. In this way, extension methods can be seen as a kind of syntactic sugar.

### Where can extension methods be applied

The target of an extension method must be one of the following application object types:

- Class
- Table
- View
- Map

Regardless of the target type, an extension *class* is used to add extension methods to the type. For example, an extension table is *not* used to add methods to a table, and there's no such thing as an extension table.

## The this keyword

The **this** keyword is a reference to the instance of the class or table where the **this** keyword is used. The **this** reference is never required, but it can clarify your code and enhances the behavior of IntelliSense in the code editor. All calls to instance methods must be qualified by either the **this** reference or a variable. The **this** reference can be used to qualify the following information:

+ The names of other instance (non-static) methods in the same class where the **this** reference is used. Here is an example: `boolColorChanged = this.colorItOrange();`
+ The names of methods that are inherited by the **this** object.
+ The names of fields on the table that contains the method that the **this** keyword is used in.

The **this** reference can't be used in the following ways:

+ It can't qualify the names of member variables that are declared in the **classDeclaration** code.
+ It can't be used in a static method.
+ It can't qualify the names of static methods of the class or table.

## Nested classes

Classes can be nested in X++ source code. Nested classes are available only inside forms (such as a class that extends FormRun) to represent controls, data sources, or data fields.

## Jobs

There is no concept of an X++ job from preview versions (AX2102 and earlier). To quickly and easily run an X++ method, add a `static Main` method to a class, and then set the class as the startup object form for the project in Microsoft Visual Studio. When the project is run, the `Main` method will be run.

## Call stack limitation

The depth of the call stack is limited to 100.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
