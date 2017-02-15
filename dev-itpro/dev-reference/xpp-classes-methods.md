---
# required metadata

title: X++ classes and methods
description: This topic describes how to create and use class and interfaces in X++.
author: annbe
manager: AnnBe
ms.date: 2016-08-27 00 - 36 - 06
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
ms.custom: 150303
ms.assetid: fcd5d429-9e28-4dce-acd4-3a181b5a3a84
ms.search.region: Global
# ms.search.industry: 
ms.author: annbe
ms.dyn365.intro: Feb-16
ms.dyn365.version: AX 7.0.0

---

# X++ classes and methods

This topic describes how to create and use class and interfaces in X++.

Classes in X++
--------------

A **class** is a software construct that defines the data and methods of the specific concrete objects that are subsequently constructed from that class. The data represents the state of the object. The methods represent the behavior of the object. **Variables** are the data for the class. Variables in a class are specific to objects that are constructed from that class. Every object constructed from the class declaration has its own copy of the variables. Such variables are known as instance variables. **Methods** define the behavior of a class. They are the sequences of statements that operate on the data. Methods are typically declared to operate on the instance variables of the class, and are known as instance methods or object methods. You can also declare static methods and static fields.

## Declaration of Classes
### Creating a Class in Visual Studio

You create a class by following these steps:

1.  In **Server Explorer**, right-click on the project, and select **Add**.
2.  In the **New Item** dialog, select **Class** and enter a name for the class.
3.  Click **Add**.

All classes are **public**. If you remove the **public** modifier, the system still treats the class as **public**. Other modifiers can be specified on the class declaration, including **final** and **extends**.

### Creating Variables in a Class

All classes are public, but all member variables are implicitly private. Even though all member variables are private, you cannot decorate a member variable with the **private** keyword. All member variables belong only to object instances of the class. The following code shows you how you would use accessor methods to make the variable data public. For more information, see [Accessor Methods](#Accessor%20Methods).

    public class HasAFirstName
    {
        str firstName;
        public str getFirstName()
        {
            return firstName;
        }
        
        public void setFirstName(str newName)
        {
           firstName = newName;
        }
    }

## Constructors
To create an instance of a class (an object), you have to instantiate it. The default constructor is the **new** method:

    // Declare a variable to refer to a Point object
    Point myPoint; 
        
    // Allocate an instance of a Point object
    myPoint = new Point(); 

It is a best practice to make the **new** method protected, and instead, use a **static construct** method, or **static new** method as the public constructor for the class. If no initialization is required, use a **static construct** method, otherwise use a **static new** method. For more information, see Best Practices for Constructors.

### Creating Other Objects from a Constructor

A class constructor can instantiate other objects, in addition to creating an instance of the class. The following code illustrates one such situation by declaring a **Rectangle** class that uses two **Point** objects to define its bounds.

    class Rectangle1
    {
        Point lowerLeft;
        Point upperRight;

        void new(real _topLeftX, real _topLeftY, real _bottomRightX, real _bottomRightY)
        {
            lowerLeft  = new Point(_topLeftX, _topLeftY);
            upperRight = new Point(_bottomRightX, _bottomRightY);
        }
    }

## Destructors
A **destructor** is used to explicitly destroy a class object. Objects are destructed automatically when there are no more references to them. You can destruct them explicitly in the following ways:

-   Use the **finalize** method.
-   Set the object handle to **null**.

### finalize method

Use the **finalize** method to explicitly destruct an object. There are no implicit calls to the **finalize** method. You must call it to execute the statements in it.

    // From any method in a class.
    if (Condition)
    {
        // Removes object from memory.
        this.finalize(); 
    }

The **finalize** method is also where to put any other clean-up code. For example, if your class uses a DLL module, you can use the **finalize** method to release the DLL when you no longer need it. Use **finalize** carefully. It will destruct an object even if there are references to it.

### Set an Object Handle to null

Set the object handle to **null** to terminate an object. This only destroys the object if there are no other object handles pointing to it. Check that other programmers haven't already used the object handle. For example:

    // Create an object handle of the type MyObject.
    MyObject mo;
    // Create an object of MyObject type andlink it to the object handle.
    mo = new myObject();
    // Terminate the object.
    mo = null;

## Creating a Subclass
Subclasses are classes that extend or inherit from other classes. A class can only extend one other class; multiple inheritance is not supported. If you extend a class, it inherits all the methods and variables in the parent class (the superclass). Subclasses enable you to reuse existing code for a more specific purpose, saving time on design, development, and testing. To customize the behavior of the superclass, override the methods in your subclass. A superclass is often called a **base** class, and a subclass is often called a **derived** class.

### Subclass Example

The following example creates a class called **Point** and extends it to create a new class called **ThreePoint**.

    class Point
    {
        // Instance fields.
        real x; 
        real y; 

        // Constructor to initialize fields x and y.
        void new(real _x, real _y)
        { 
            x = _x;
            y = _y;
        }
    }

    class ThreePoint extends Point
    {
        // Additional instance fields z. Fields x and y are inherited.
        real z; 

        // Constructor is overridden to initialize z.
        void new(real _x, real _y, real _z)
        {
            // Initialize the fields.
            super(_x, _y); 
            z = _z;
        }
    }

### Preventing Class Inheritance

You can prevent classes from being inherited by using the **final** modifier: **public final class Attribute**  **{**  **    int objectField;**  **}**

## Methods
The following list describes the code block types that are standard for application classes:

-   ****classDescription** declaration block**: Contains class modifiers such as **public**, **private**, and **extends**. Also contains the field members for objects that are constructed from this class. IntelliSense can display a list of the members when you type the keyword **this**.
-   ****new** method**: Creates an instance of the class. The constructor can be called only by using the **new** keyword. Derived classes can call the **new** method of their constructor by calling **super** method reference.
-   ****finalize** method**: Finalizes an instance of the class. The destructor method. However, this is a destructor only by convention. The **finalize** method is not called automatically by the system during garbage collection.

Additional methods for a class fall into the following types:

-   Instance methods
-   Static methods
-   Main methods

Methods can be created on many kinds of items. The list includes the following:

-   Classes
-   Maps
-   Views
-   Data Sets
-   Forms
-   Queries

### Instance Methods

Instance methods, or object methods, are embedded in each object that is created from the class. You must instantiate the object before you can use the method. If you later convert an instance method to a static method, you must restart the client for the compiler to note the change. Once you have converted the instance method to a static method, you can no longer call this method from the instance of the class, only from the class itself. Static methods are discussed in the next section. Instance methods are called by using the following syntax:

    ClassName objectHandleName = new ClassName();
    objectHandleName.methodName();

### Static Methods

Static methods, also called class methods, belong to a class and are created by using the keyword **static**. You do not need to instantiate an object before you use static methods. Static methods are widely used in Microsoft Dynamics AX to work with data that is stored in tables. It is not possible to use member variables in a static method. Static methods are called by using the following syntax:

    ClassName::methodName();

### Main Methods

A **main** method is a class method that is executed directly from a menu option. The method should only create an instance of the object and then call the necessary member methods. The **\_args** parameter allows you to transfer data to the method.

    static void main (Args _args)
    {
        // Your code here.
    }

### Declaration of Methods

Method declarations consist of a header and a body. The method header declares the name and return type (possibly **void**) of the method, the method modifiers, and parameters. The method body consists of variable declarations, method declarations, and statements.

### Return Type

If a method does not return anything, you must specify this with the **void** keyword. The following example shows two methods, one with return type and one without.

    void methodNameNoReturnValue()
    {
        // Your code here.
    }

    // If a method returns something, you must specify the return type and include a return statement.
    int methodNameIntegerReturnValue()
    {
        return 1;
    }

### Syntax

Method declaration = *Heading*  *Body* Heading = **\[** *Modifiers* **\]**  *ReturnType*  *MethodName*  **(**  *ParameterList*  **)** Modifiers = **\[client\] \[server\] \[edit | display | public | protected | private\] \[static | abstract | final \]** ReturnType = *Datatype*  **| void | anytype** MethodName = *Identifier* ParameterList = **\[** *Parameter*  **{ ,**  *Parameter*  **}\]** Parameter = *Datatype*  *Variableidentifier*  **\[ =**  *Expression*  **\]** Body = **{ \[**  *VariableDeclarations*  **\] \[**  *EmbeddedFunctionDeclarations*  **\] \[**  *Statements*  **\] }** EmbeddedFunctionDeclaration = *Heading*  **{\[**  *VariableDeclarations*  **\] \[**  *Statements*  **\]}** If you use the **anytype** return type, the method can return any data type.

### Code Example: Method Without a Return Type

    void update ()
    {   
        // Variable declared and initialized
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

### Code Example: Method with Parameters

In the following code example, the **checkAccountBlocked** method returns a **Boolean** value and acts on the parameter **amountCur**.

    boolean checkAccountBlocked(AmountCur amountCur)
    {
        if (this.blocked == CustVendorBlocked::All 
            ||(this.blocked == CustVendorBlocked::Invoice 
            && amountCur > 0 ))
        return checkFailed(strFmt("@SYS7987",this.accountNum));
        return true;
    }

## Method Modifiers
There are several modifiers that can be applied to method declarations. Some of the modifiers can be combined (for example, **final static**). The following list describes method modifier keywords:

-   **abstract**: The method is declared but not implemented in a parent class. The method must be overridden in subclasses. If you try to create an object from a subclass where one or more of the abstract methods belonging to the parent class have not been overridden, you will get a compiler error. Classes can also be abstract. Sometimes a class represents an abstract concept, but it should not be instantiated: Only subclasses should be instantiated. Such base classes can be declared abstract. Consider the case where the programmer wants to model the concept of an account. Accounts are abstract, because only derived classes (ledger accounts and so on) exist in the real world. This would be a clear case for declaring the **Account** class abstract.
-   **display**: Indicates that the method's return value is to be displayed on a form or a report. The value cannot be altered in the form or report.The return value is typically a calculated value, for example, a sum.
-   **edit**: Indicates that the method's return type is to be used to provide information for a field that is used in a form. The value in the field can be edited.
-   **final**: Indicates that the method cannot be overridden in any class that derives from its class.
-   **public**: Methods that are declared as **public** are accessible anywhere the class is accessible and can be overridden by subclasses. Methods that have no access modifier are implicitly **public**.
-   **protected**: Methods that are declared as **protected** can only be called from methods in the class and in subclasses that extend the class where the method is declared.
-   **private**: Methods that are declared as **private** can be called only from methods in the class where the private method is declared.
-   **static**: Specifies that the method is a class method and does not operate on an instance. **static** methods cannot refer to instance variables and are invoked by using the class name rather than on an instance of the class (**MyClass::aStaticProcedure()**).

### Methods with Modifiers

Only the method headers are shown in the following examples.

    // A method that cannot be overridden
    final int dontAlterMe() 

    // A static method 
    static void noChange()

    // A display method that returns an integer
    display int value()

## Static Class Members
You declare static class members by using the **static** keyword. The **static** keyword instructs the system to create only one instance of the method regardless of how many times you call new. This single instance is used throughout your session. Static methods are generally intended for cases where the following criteria are met:

-   The method has no reason to access the member variables that are declared in the class.
-   The method has no reason to call any instance (non-static) methods of the class.

#### Static methods

Consider the example of a software key type that is used for piracy prevention. Each instance of a software key can have its own unique value. But all software keys must conform to the rules of software key design. Therefore the logic to test for software key conformance is the same for all software keys. The method that contains the conformance validation logic should be static. Here is an example of a method that is declared with the **static** keyword:

    static public boolean validateSoftwareKey(str _softwareKeyString)  {      // Your code here. }

In the following example, there is no need to first construct an instance of the **SoftwareKey** class before you call a static method on the class. To call the static method **validateSoftwareKey**, the syntax starts with the name of the class that contains the method. A pair of colon (**::**) characters is used to connect the class name to the static method name.

    boolean yourBool = SoftwareKey::validateSoftwareKey(yourSoftwareKeyString);

#### Static fields

Static fields are supported in X++.

### Static constructors

Static constructors are guaranteed to run before any static or instance calls are made to the class. In C\#, the concept of static relates to the whole executing application domain. The execution of the static constructor is relative to the user’s session. The static constructor has the following syntax:

    static void TypeNew() 

You never call the static constructor explicitly; the compiler will generate code to ensure that the constructor is called exactly once prior to any other method on the class. A static constructor is used to initialize any static data, or to perform a particular action that needs to be performed only once. No parameters can be provided for the static constructor, and it must be marked as static. Static fields are fields that are declared using the static keyword. Conceptually they apply to the class, not instances of the class. The following example shows how to create a singleton instance by using a static constructor.

    public class Singleton
    {
      private static Singleton instance;

      private void new()
      {
      }

      static void TypeNew()
      {
        instance = new Singleton();
      }

      public static Singleton Instance()
      {
        return Singleton::instance;
      }
    }

The singleton will guarantee that only one instance of the class will ever be called. The following code example shows how to instantiate the singleton.

    {

        Singleton i = Singleton::Instance();
    }

## Method Access Control
You use the accessor keywords **public**, **protected**, and **private** to control whether the methods in other classes can call the methods on your class. The accessor keywords on methods also interact with the rules for class inheritance. The following list describes the accessor keywords you use with methods.

-   **public**: Methods that are declared as **public** can be called from anywhere the class is accessible. In addition, a public method can be overridden by a subclass, unless the method is declared as **final**.
-   **protected**: Methods that are declared as **protected** can be called only from the following:
    -   From methods in the class.
    -   From methods in a subclass of the class that contains the protected method. Methods that are **protected** can be overridden in subclasses.
-   **private**: Methods that are declared as **private** can be called only from methods in the class where the private method is declared. No private method can be overridden in a subclass.When you create a new method, the default accessor keyword that appears in the code editor is **private**. This is the most conservative default for maximum security.

### Static and Instance Methods

The accessor keywords on methods never restrict call between two methods that are in the same class. This is true regardless of which of the two methods are **static** or non-static. In a static method, calls to the **new** constructor method are valid even if the **new** constructor method is decorated with the **private** modifier. The syntax for these calls requires the use of the **new** keyword. The code in a static method must construct an instance object of its own class before the code can call any instance methods on the class.

### Increase Access When Overriding

When a method is overridden in a subclass, the overriding method must be at least as accessible as the overridden method. For example, the following compiler rules apply to overriding a **protected** method in a subclass:

-   A **public** method in a superclass can be overridden only by a **public** method in the subclass.
-   In a subclass, a **public** method or a **protected** method can override a **protected** method of the superclass.
-   In a subclass, a **private** method cannot override a **protected** method of the superclass.

## Using Optional Parameters
It is possible to initialize parameters in the method declaration. This makes the parameter an optional parameter. If no value is supplied in the method call, the default value is used. All required parameters must be listed before the first optional parameter. The following code examples show how to create and call a method with optional parameters. The **AddThreeInts** method shows that you cannot skip over default parameters when calling the method.

### Optional Parameters Code Examples

    // This is an example of a function being used as the default.
    public class Person 
    {
        date birthDate;

        // The constructor that takes a date type as
        // a parameter. That value is assigned to the field member birthDate. 
        void new(date _date)
        {
            birthDate = _date;
        }

        // The CalculateAgeAsOfDate method references
        // the birthDate field, is called by the Main method, and has an 
        // optional parameter. In this example, the default value is the
        // return value of a function. 
        public real CalculateAgeAsOfDate(date _calcToDate = DateTimeUtil::getToday(DateTimeUtil::getUserPreferredTimeZone()) )  
        {
            return (_calcToDate - birthDate) / 365;
        }

        // The Main method calls the CalculateAgeAsOfDate method twice. 
        static public void Main(Args _args)
        {
            Person mc = new Person(13\5\2010);   // birthDate is initialized.
            // Optional parameter's default is used.
            print( "Age in years: " + num2str(mc.CalculateAgeAsOfDate(),2,0,0,0));
            // January 2, 2044  is the parameter value for _date.
            print "Age in years: " + num2str(mc.CalculateAgeAsOfDate(2\1\2044),2,0,0,0);
        }
    }

    // This is an example of how you cannot skip to a second optional parameter. 
    // The first method has two optional parameters. The second method is a caller 
    // of the first method. The caller wants to override only the _i3 default value, but the 
    // compiler requires that all prior optional parameters also 
    // be overriden in the call. 
    public class Additions {
        static public int AddThreeInts(int _i1, int _i2 = 2,int _i3 = 3)
        {
            return _i1 + _i2 + _i3;
        }
    }

    // The second method has a commented section showing the
    // failed attempt to accept the default of the first optional 
    // parameter (_i2) while trying to override the final optional 
    // parameter (_i3).
    static public void Main(Args _args)
    { 
        // No way to skip the first optional parameter (so it can default)
        // while also specifying the value of the second optional parameter.
        // The next statement does not compile.
        //print Additions::AddThreeInts(1, , 99);

        // Settle for overriding both optional parameters.
        print Additions::AddThreeInts(1, 2, 99);
    }

## Accessor Methods
Class variables are private. By hiding details of the internal implementation of a class, X++ allows the programmer to change the implementation of the class in the future without breaking any code that uses that class. To access the data from reference variables, you need to create accessor methods. The following example defines a **Point** class that uses accessor methods to access the variables **x** and **y**.

    class Point
    {
        // Instance variables
        real x; 
        real y;

        //Constructor to initialize to a specific or default value
        void new(real _x=10, real _y=10) 
        {
            x = _x;
            y = _y;
        }

        //Accessor methods
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

These method declarations illustrate how the **Point** class provides access to its variables from the outside world. Other objects can manipulate the instance variables of **Point** objects by using the accessor methods:

    // Declare a variable to refer to a Point object
    Point myPoint; 
    // Create a Point object
    myPoint = new Point(); 
    // Set the x variable using the accessor method
    myPoint.setX(10.0); 
    // Set the y variable by means of the accessor method
    myPoint.setY(25.7);

The X++ callstack depth is limited to 100.

## Overriding a Method
The methods in a class are inherited by any class that extends it. You can alter the functionality of an inherited method by creating a method in the subclass with the same name and parameters as in the superclass. This is called overriding the method. In the following code example, **ColorAttribute** is a subclass of **Attribute** and therefore inherits the method **methodAttr**. However, because **ColorAttribute** defines a method with the same name and the same number of arguments, the method in the superclass is overridden.

    // Superclass: Attribute
    public class Attribute
    {
        int objectVariable;

        void methodAtt()
        {
            //Some statements
        }
    }

    // Subclass: ColorAttribute
    public class ColorAttribute extends Attribute
    {
        int addedObjectVariable;

        void methodAtt()
        {
            //Some statements
        }
    }

### Preventing Method Overriding

Static methods cannot be overridden because they exist per class. To protect other sensitive methods, or core methods, from being overridden, use the **final** modifier. In the example below, **methodAtt** is declared as **final**, and so it cannot be overridden in any class that extends **Attribute**. You should not specify **new** or **finalize** methods as **final**. The following example shows how to use the **final** keyword.

    public class Attribute
    {
        int objectVariable;

        final void methodAtt()
        {
            //Some statements
        }
    }

### Overriding vs. Overloading

Overloading is where there is more than one method with the same name, but the methods have different signatures (return type or parameter lists or both). Overriding is where the superclass's implementation of a method is altered by the subclass's implementation of the method, but the signatures of both methods are the same. X++ supports overriding, but it does not support overloading.

## Parameters
The scope rules in X++ state that all methods have their own scope. A method can take one or more parameters. Within the scope of the method, these parameters are treated like local variables and are initialized with the value from the parameter in the method-call. The following table shows an example. All parameters are passed by value. You cannot change the value of the original variable, you can change only the local variable in the method, which is a copy of the original. .

## Scope of Variables in Methods
A scope defines the area in which an item can be accessed. Variables defined in a class are available to the methods within that class. Variables in methods can be accessed only within the current block, as shown in the following figure.

## Local Functions
You can declare local functions inside a method. The best practice is to add private methods to the class rather than to add local functions inside the method. The following code example shows valid declarations of two local functions named **localFunc55b** and **localFunc66c**. This calls to the local functions occur after the function declarations in the code example, as is required.

    static void G_LocalFuncJob2(Args _args) 
    {
        int nn = 654;
        void localFunc55b(int _iNum)  // The local function.
        {
            str sInnerString;
            sInnerString = "String_in_localFunc55b";
            info(strFmt("localFunc55b: %1 , %2 , %3", 
                _iNum, sInnerString, nn));
        }

        void localFunc66c()
        {
            info("Printing from inside localFunc66c.");
        }


        localFunc55b(55);
        localFunc66c();
        // Next print statement would fail to compile,
        // because sInnerString is restricted to the
        // scope of the local function in which it is declared.
        // print sInnerString; 
    }
    /***  Infolog window display:
    Message (07:38:54 pm)
    localFunc55b: 55 , String_in_localFunc55b , 654
    Printing from inside localFunc66c.
    ***/

### Declaration of Local Functions

-   The local functions must be declared physically above any non-declaration statements that exist in the method.
-   You can declare more than one local function in your method. But all local functions must be declared in an uninterrupted series, with the set terminated by one semicolon.

### Scoping of Variables

-   Code that is inside the local function can access variables that are declared in the method that contains the local function.
-   Code that is outside the local function cannot access variables that are declared in the local function.

### Calls to Local Functions

-   A local function can be called only by code in the same method where the local function is declared.
-   A local function should never call itself. Such recursion can prevent the successful compilation.

## The this Object
The keyword **this** is a reference to the instance of the class or table in which the **this** keyword is used. The **this** reference is never required, but it can clarify your code, and it enhances the behavior of IntelliSense in the code editor. All calls to instance methods must be qualified, either with the **this** reference or with a variable. The **this** reference can be used in the following ways:

-   Can be used to qualify the names of other instance (non-**static**) methods in the same class where the **this** reference is used. For example: **boolColorChanged = this.colorItOrange();**
-   Can be used to quality the names of methods that are inherited by the **this** object.
-   Can be used to qualify the names of fields on the table that contains the method that the **this** keyword is used in.

The **this** reference cannot be used in the following ways:

-   Cannot be used to qualify the names of member variables that are declared in the **classDeclaration** code.
-   Cannot be used in a **static** method.
-   Cannot be used to qualify the names of **static** methods of the class or table.

## Interfaces
An interface is a specification for a set of public instance methods. The purpose of interfaces is to define and enforce similarities between unrelated classes without having to artificially derive one class from the other. All interfaces are public regardless of whether you explicitly write the keyword **public** in front of the keyword **interface** in the **classDeclaration**. The methods on an interface are also public, and again the explicit inclusion of the keyword **public** is optional. To create an interface:

1.  In **Server Explorer**, right-clickon the project, and select **Add**.
2.  In the **New Item** dialog, select **Interface** and enter a name for the interface.
3.  Click **Add**.

You can add the **implements** keyword on a class declaration, and this requires the class to declare the methods that are specified by the interface. A class declaration can implement multiple interfaces by listing them after the single occurrence of the **implements** keyword, with commas separating the interface names. All interface methods that a class implements must be declared with the explicit keyword **public** in the class. Also, a class that implements an interface must also be declared with **public**. An interface can extend another interface by using the **extends** keyword. An interface cannot extend more than one interface.

### Interface Code Example

This section shows the code for an **Automobile** class that implements an **IDrivable** interface.  The keyword **is** is supported for testing whether a class that implements an interface.

    public interface IDrivable
    {
        public int getSpeed()
        {
        }

        public void setSpeed(int newSpeed)
        {
        }
    }

    class Automobile implements IDrivable
    {
        int m_speed;

        public int getSpeed()
        {
            return m_speed;
        }

        public void setSpeed(int newSpeed)
        {
            m_speed = newSpeed;
        }
    }

    class UseAnAutomobile
    {
        void DriveAutomobile()
        {
            IDrivable yourIDrivable;
            Automobile myAutomobile;
            str sTemp = "object is not an IDrivable";
            
            myAutomobile = new Automobile();
            
            if (myAutomobile is IDrivable)
            {
                yourIDrivable = myAutomobile;
                yourIDrivable.setSpeed(42);
                sTemp = int2str(yourIDrivable.getSpeed());
            }
            
            Global::info(sTemp);
            return;
            // output
            // Message (06:46:33 pm)
            // 42
        }
    }

## Microsoft Dynamics AX Class Overview
There are two main kinds of classes in Microsoft Dynamics AX:

-   Application classes are implemented in X++. They are available in the Classes node in the Application Explorer.
-   System classes, sometimes called kernel classes, are implemented in C++. They are listed under the **System Documentation &gt; Classes** node in the Application Explorer. However, the source code for these classes is not available.

## Substitute Application Classes for System Classes
You should call the substitute application classes instead of calling the system classes that they extend. In the **Application Explorer **under **System Documentation &gt; Classes** there are several kernel or system classes whose names begin with a lowercase x. Examples of the x system classes include **xApplication** and **xVersionControl.** Some of the x system classes are extended by application classes. For example, the Application class extends the xApplication system class. The classes that derive from the x system classes are called **substitute application classes**. In the **Application Explorer **under the **Classes** node, the icon next to the substitute application classes differs from the standard icon.

### Special X++ Global Variables

Some of the substitute application classes that extend an x system class are associated with a special global variable that represents an instance of the class. For example, the **appl** variable references a pre-instantiated object from the Application class. The advantage of the **appl** variable is that the system maintains the object throughout the scope of your session. It would be less efficient for your code to repeatedly use the **new Application()** syntax to obtain an instance of the **Application** class. You should not use the **xApplication** system class. Use the **Application** substitute application class instead. You can reference the static members of the **Application** class by using the standard syntax **Application::checkForNewBatchJobs()**. But you should reference the instance members of the **Application** class by using its corresponding special system variable **appl**, if one exists. This pattern applies to most of the x system classes. The **Session** substitute application class is one exception to this pattern, because there is no special system variable for **Session**. The following table lists x system classes for which there is a corresponding substitute application class. The special global variables are also shown for those classes that have one.

| Application class | System class        | Global variable    |
|-------------------|---------------------|--------------------|
| Args              | **xArgs**           | (none)             |
| Application       | **xApplication**    | **appl**           |
| ClassFactory      | **xClassFactory**   | **classFactory**   |
| Company           | **xCompany**        | **appl.company**   |
| Global            | **xGlobal**         | (none)             |
| Info              | **xInfo**           | **Infolog**        |
| MenuFunction      | **xMenuFunction**   | (none)             |
| Session           | **xSession**        | (none)             |
| VersionControl    | **xVersionControl** | **versionControl** |

### Example Method That Uses Special Variables

The following method demonstrates the syntax for using several special variables that reference instances of the substitute application classes.

    static void UseSpecialSystemVariablesForXJob(Args _a)
    {
        TreeNode treeNode2;
        Args     args3;
        FormRun  formRun4;
        // appl variable
        print appl.buildNo();
        // company variable
        appl.company().reloadRights(); // referenced through appl
        // Infolog variable
        treeNode2 = infolog.findNode("\\forms\\custTable");
        print treeNode2.AOTgetProperty("Name");
     
        // classFactory variable
        args3 = new Args(formstr(vendTable));
        formRun4 = classFactory.formRunClass(args3);
        formRun4.init();
        formRun4.run();
        formRun4.detach();
        Global::info("Method is ending. This is a message in the Infolog.");
    }

## Execute Startup Commands
Use the **SysStartupCmd** class framework to execute commands at startup. When Microsoft Dynamics AX starts, calls are made to the \***startup** methods on the application-substituted kernel classes **Application** (**Application.startup**) and **Info** (**Info.startup**). The \***startup** methods are used for vital system and version-specific calls, and you must never directly modify these methods. Instead, use the **SysStartupCmd** framework. Serious consequences may follow if the SYS layer versions of the startup methods are not called. When Microsoft Dynamics AX is started, calls are executed in the sequence shown in the following code.

    appl.startup() // The SysStartupCmd class is instantiated here.
    sysStartupCmd.applInit()
    super()
    sysStartupCmd.applRun()
    info.startup()
    sysStartupCmd.infoInit()
    super()
    sysStartupCmd.infoRun()

### Commands Available when Microsoft Dynamics AX Starts

The commands that are available when Microsoft Dynamics AX starts are listed in the **SysStartupCmd.construct** method. The commands include the following:

-   AutoRun
-   AOTImport
-   Synchronize

The following code example shows how to execute a new command when Dynamics AX starts. A class that extends SysStartupCmd is created that performs your specific task. Then modify the construct method on SysStartupCmd to call your class. You can add parameters commands that are executed on startup to the Command to run at application startup field on the General tab in the Microsoft Dynamics AX Configuration Utility. Instead of giving the command from the Dynamics AX Configuration Utility, you might choose to use the command-line parameter **-startupcmd=** *MyCommand*.

    public class SysStartupCmdAutoRun : extends SysStartupCmd 
    {
        void new(str s, str parm) 
        {
            // Your code here.
        }
    }

    // This is a framework class. Customizing this class may cause problems with future upgrades to the software.
    class SysStartupCmd
    {
        // Code delete for readability

        static SysStartupCmd construct(str startupCommand)
        {
            // Code delete for readability
            switch (s)
            {
                // Other cases delete for readability    
                case 'autorun':
                    sysStartupCmd = new SysStartupCmdAutoRun(s,parm);
                    break;
                // Other cases delete for readability
            }
            // Code delete for readability
        }
    }

## Batch Processing Classes
Implement classes by using the batch processing system, and by extending the **RunBase** and the **RunBaseBatch** classes. Remove the **Recurrence** button from the **Batch processing** dialog by using the **Args::parmEnum** method. It is recommended that you designate a class to run as a server-bound batch method. Server-bound batch methods are more secure than methods that are not server-bound batch for the following reasons:

-   The method executes by using the permissions of the user who submitted the method.
-   The method can interact with the Microsoft Dynamics AX client, which is processing the method, by using only certain Info and Global class methods. This limits interaction with the client.

### Enable a Class to Run as a Server-Bound Batch Method

1.  Create a class that extends the RunBaseBatch class.
2.  Override the RunBaseBatch.runsImpersonated method to return a value of **true**, as shown in the following example.

        public boolean runsImpersonated()
        {
            return true;
        }

3.  Confirm that the class calls only the following **Info** and **Global** class methods:
    -   **add**
    -   **Info.copy**
    -   **Info.cut**
    -   **Info.import**
    -   **Info.export**
    -   **Info.line**
    -   **Info.num**
    -   **Global::error**
    -   **Global::info**
    -   **Global::warning**

    The **Info.line** and **Info.num** methods are inherited from the xInfo class.

### Remove the Recurrence Button from the Batch Processing Dialog

When you implement a class by using the batch processing system, call the **Args.parmEnum** method, and pass the **NoYes::Yes** system enumeration value to remove the **Recurrence** button. The **NoYes** system enumeration determines whether the recurrence button is removed from the batch processing dialog. The default value is **NoYes::No**. In the following code example, the **InventTransferMultiShip** class is implemented. The **BatchDialog::main** method creates the **Batch processing** dialog.

    static void noRecurrenceButton(Args _args)
    {
        Args a;
        InventTransferMultiShip inventTransferMultiShip;
        a = new Args();
        inventTransferMultiShip = InventTransferMultiShip::construct();
        a.caller(inventTransferMultiShip);
        a.parmEnum(NoYes::Yes);
        BatchDialog::main(a);
    }

## Image Manipulation Classes
There are two system classes that enable you to manipulate graphics and icons. The **Image** class enables you to load, save, and manipulate individual images. For example, you can capture a screen and save it as an image, crop or rotate an image, or manipulate the color depth. The **Imagelist** class enables you to work with a set of images that have some common properties, such as size and transparency color. The image lists that are used in the application can be viewed in the application classes called **ImageListAppl\_\***.

## Query Object Model
The query object model contains classes to define and run a query. These objects are used to define the query data source, the fields returned, record ranges and relations to child data sources. The following illustration shows the object model. The query components shown in the previous figure are system classes. The query classes are more visible when you create a dynamic query in code, but they are also used behind the scenes when you create a static query in the **Application Explorer**.

| System class             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|--------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **QueryRun**             | Executes the query and fetches the data.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| **Query**                | Holds some properties itself and has one or more related data sources. The top level of the query definition.                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| **QueryBuildDataSource** | Defines access to a single data source in the query. If more than one data source exists at the same level in a query, they result in separate SQL statements that are executed sequentially. If one data source exists as a child of another data source, a join is created between the two data sources.                                                                                                                                                                                                                                          |
| **QueryBuildFieldList**  | Defines which fields are returned from the database. The default is that the field list is dynamic, which returns all fields from the data source table, map, or view. Each data source has only one **QueryBuildFieldList** object, which contains information on all selected fields. It's possible to specify aggregate functions like **SUM**, **COUNT**, and **AVG** on the field list object.                                                                                                                                                 |
| **QueryBuildRange**      | Defines a subset of records returned based on a single field. A range is translated into a **WHERE** clause in the query SQL statement. If more than one field is used to limit the query (**WHERE** clause), the data source will contain more than one range.                                                                                                                                                                                                                                                                                     |
| **QueryBuildDynalink**   | Contains information regarding a relation (limitation) to an external record. When the query is run, this information is converted to additional entries in the **WHERE** clause of the query SQL statement. Can only exist on the parent data source of a query. The function is used by forms, when two data sources are synchronized. Then the child data source will contain a dynalink or dynalinks to the parent data source. The function is used even if the two data sources are placed in two different forms but are still synchronized. |
| **QueryBuildLink**       | Specifies the relation between the two data sources in the join. Can only exist on a child data source.                                                                                                                                                                                                                                                                                                                                                                                                                                             |

## System Classes Overview
System classes (or kernel classes) are implemented in C++. The source for these classes is not available. A system class can have:

-   Static methods (or class methods)
-   Dynamic methods
-   Properties: these are member functions to set properties. For example, **LeftMargin**.

You cannot override system class methods. It is not intended that you design your application objects from scratch by using the system classes. Instead, use them to extend or alter the default functionality in the **Application Explorer**. For example, you could dynamically add extra information to an existing report or change the available options on a form, depending on the user's choice in a previous form.

### Collection Classes

The Collection Classes in Microsoft Dynamics AX enable you to create lists, sets, structs, maps, and arrays.

### Application Objects Classes

These system classes hold functions that are activated whenever you use the **Application Explorer **to create your application. For example, the system uses the **FormDesign** class when you define the layout of your form in the **Designs** node in the **Application Explorer.** These classes also enable you to create and modify application objects. For example, if you want to change a property on a form string field, see Forms System classes and Query System Classes.

### Integration Classes

The integration to the environment of Microsoft Dynamics AX is typically implemented by classes. Some examples of classes of this category are:

-   **COM**: call of methods on COM objects
-   **DLL**: call of Microsoft Windows DLL functions
-   **IO**: Read and write external files
-   **ODBCConnection**: an ODBC interface to a foreign database

### 

## Event Terminology and Keywords
In Microsoft Dynamics AX, you can use the event design pattern to make your code more modular and reusable. The term **event** is a metaphor that explains how **delegates** are used. When something important occurs during a program run, there might be other modules that need to process the occurrence. These important occurrences are called **events**. When an event occurs, the program tells its **notifier** for the event that the notifier must send notifications of the event. A notification must be sent to all the **event handlers** that are **subscribers** of the notifier. When the program tells its notifier to send the notifications, we call that **raising** an event. The following table displays the terms that are used to describe the event metaphor.

| Metaphorical term | Description                                                                                                               |
|-------------------|---------------------------------------------------------------------------------------------------------------------------|
| event             | An important occurrence in a program module where additional modules must process the occurrence.                         |
| notifier          | The program element that sends information about the event to all the event handlers that are subscribed to the notifier. |
| subscriber        | The program functions or methods that are subscribed to an event notifier.                                                |
| event handler     | The methods that subscribe to an event notifier. Only the appropriate kind of methods can be event handlers.              |

### Keywords used for X++ Programming with Delegates

The following table shows the X++ keywords that describe the use of delegates.

| X++ keyword or term                         | Code                                                                         | Description                                                                                                                                                                                                                                                                            |
|---------------------------------------------|------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **delegate**                                | **delegate myDelegate(str \_information) {}**                                | The code shows how the delegate looks in the method editor in the MorphX client. The return type is always void, so it is not mentioned in the syntax. No code is allowed inside the **{}** braces.                                                                                    |
| **eventHandler**                            | **myClassInstance.myDelegate += eventHandler(otherClass.myInstanceMethod);** | The syntax of the **eventHandler** keyword might give the impression that **eventHandler** is an X++ function, but it is not a function. The **eventHandler** keyword tells the compiler that a method is being subscribed to a delegate.                                              |
| Subscribe or add a method to a **delegate** | **myClassInstance.myDelegate += eventHandler(OtherClass::aStaticMethod);**   | The static method **OtherClass::aStaticMethod** becomes subscribed to the delegate.                                                                                                                                                                                                    |
| Call a **delegate**                         | **myClassInstance.myDelegate("Hello");**                                     | This call to the delegate prompts the delegate to call each method that is subscribed to the delegate. The subscribed methods are called in the same sequence in which they were added to the delegate. One subscribed method must complete before the delegate calls the next method. |



