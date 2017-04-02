---
# required metadata

title: X++ classes and methods
description: This topic describes how to create and use classes and interfaces in X++.
author: RobinARH
manager: AnnBe
ms date: 2017-04-04
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
ms.assetid: 1b2d76d1-52d9-46b2-937f-5a3b62f2d516
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# X++ classes and methods

This topic describes how to create and use classes and interfaces in X++.

Classes in X++
--------------

A *class* is a software construct that defines the data and methods of the objects that are later constructed from that class. The objects that are constructed are known as *instances* or *objects*. (This topic uses the two terms interchangeably.) The data represents the state of the object, whereas the methods represent the behavior of the object. *Variables* contain the data for the class. Variables in a class are specific to objects that are constructed from that class. Every object that is constructed from the class declaration has its own copy of the variables. These variables are known as *instance variables*. Methods define the behavior of a class. They are the sequences of statements that operate on the data. Typically, methods are declared to operate on the instance variables of the class. These methods are known as *instance methods* or *object methods*. You can also declare *static methods* and *static fields*.

## Declaration of classes
### Create a class in Visual Studio

Follow these steps to create a class in Microsoft Visual Studio.

1.  In Server Explorer, right-click the project, and then click **Add**.
2.  In the **New Item** dialog box, select **Class**, and then enter a name for the class.
3.  Click **Add**.

All classes are public. If you remove the **public** modifier, the system still treats the class as public. You can specify other modifiers on the class declaration, such as **final** and **extends**.

### Creating variables in a class

All classes are public, but all member variables are implicitly private. However, even though all member variables are private, you can't decorate a member variable with the **private** keyword. All member variables belong to only object instances of the class. The following example shows how to use accessor methods to make the variable data public.

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
To create an instance of a class, you must instantiate it by using a *constructor*. The default constructor is the **new** method.

    // Declare a variable to refer to a Point object
    Point myPoint; 
        
    // Create an instance of a Point object
    myPoint = new Point(); 

As a best practice, you should make the **new** method protected. Instead, if initialization isn't required, you should use a **static construct** method as the public constructor for the class. Otherwise, you should use a **static new** method.

### Creating other objects in a constructor

A class constructor can instantiate other objects in addition to creating an instance of the class. For example, the following code declares a **Rectangle** class that uses two **Point** objects to define its bounds.

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
A *destructor* is used to explicitly destroy a class object. Objects are automatically destroyed when there are no references to them. However, you can destroy objects explicitly in the following ways:

-   Use the **finalize** method.
-   Set the object handle to **null**.

### Using the finalize method

Use the **finalize** method to explicitly destroy an object. There are no implicit calls to the **finalize** method. You must call the method to run the statements in it. The following example shows the basic structure for a call to the **finalize** method.

    // From any method in a class.
    if (condition)
    {
        // Removes object from memory.
        this.finalize(); 
    }

In the **finalize** method, you should also put any clean-up code that is required. For example, if your class uses a dynamic-link library (DLL) module, you can use the **finalize** method to release the DLL when you no longer require it. Use the **finalize** method carefully. It will destroy an object even if there are references to it.

### Setting an object handle to null

Set the object handle to **null** to terminate an object. This approach destroys an object only if no other object handles point to that object. You should verify that other code isn't using the object handle. The following example creates an object handle and then sets it to **null**.

    // Create an object handle of the type MyObject.
    MyObject mo;
    // Create an object of MyObject type and link it to the object handle.
    mo = new myObject();
    // Terminate the object.
    mo = null;

## Creating a subclass
*Subclasses* are classes that extend or inherit from other classes. A class can extend only one other class. Multiple inheritance isn't supported. If you extend a class, the subclass inherits all the methods and variables in the parent class (the *superclass*). Subclasses let you reuse existing code for a more specific purpose. Therefore, they help save you time during design, development, and testing. To customize the behavior of a superclass, override the methods in a subclass. A superclass is often known as a *base class*, and a subclass is often known as a *derived class*.

### Subclass example

The following example first creates a class that is named **Point**. It then extends the **Point** class to create a new class that is named **ThreePoint**.

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

### Preventing class inheritance

You can prevent classes from being inherited by using the **final** modifier.

    public final class Attribute
    {
        int objectField;
    }

## Methods
The following code block types are standard for application classes:

-   ****classDescription** declaration block** – This declaration block contains class modifiers such as **public**, **private**, and **extends**. It also contains the field members for objects that are constructed from the class. When you type the keyword **this**, IntelliSense can show a list of the members.
-   ****new** method** – This method creates an instance of the class. The constructor can be called only by using the **new** keyword. Derived classes can call the **new** method of their constructor by calling the **super** method reference.
-   ****finalize** method** – This method finalizes an instance of the class. This method is the destructor method. However, it's a destructor by convention only. The system doesn't automatically call the **finalize** method during garbage collection.

Additional methods for a class have the following types:

-   Instance methods
-   Static methods
-   Main methods

Methods can be created on many kinds of items. Here are some examples:

-   Classes
-   Maps
-   Views
-   Data Sets
-   Forms
-   Queries

### Instance methods

Instance methods, or object methods, are embedded in each object that is created from the class. You must instantiate the object before you can use the method. If you later convert an instance method to a static method, you must restart the client. Otherwise, the compiler doesn't detect the change. After you've converted an instance method to a static method, you can no longer call the method from the instance of the class. Instead, you must call the method from the class itself. Static methods are discussed in the next section. You use the following syntax to call instance methods.

    ClassName objectHandleName = new ClassName();
    objectHandleName.methodName();

### Static methods

Static methods, which are also known as *class methods*, belong to a class and are created by using the keyword **static**. You don't have to instantiate an object before you use static methods. Static methods are often used to work with data that is stored in tables. Member variables can't be used in a static method. You use the following syntax to call static methods.

    ClassName::methodName();

### Main methods

A **main** method is a class method that is run directly from a menu option. The method should only create an instance of the object and then call the required member methods. The **\_args** parameter lets you transfer data to the method.

    static void main (Args _args)
    {
        // Your code here.
    }

### Declaration of methods

Method declarations consist of a header and a body. The method header declares the method's name and return type), the method modifiers, and parameters. (The return type might be **void**.) The method body consists of variable declarations, method declarations, and statements.

### Return type

If a method doesn't return anything, you must use the **void** keyword. The following example shows two methods. One method has a return type, but the other method doesn't have a return type.

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

### Example of a method that doesn't have a return type

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

### Example of a method that has parameters

In the following example, the **checkAccountBlocked** method returns a Boolean value and acts on the **amountCur** parameter.

    boolean checkAccountBlocked(AmountCur amountCur)
    {
        if (this.blocked == CustVendorBlocked::All 
            ||(this.blocked == CustVendorBlocked::Invoice 
            && amountCur > 0 ))
        return checkFailed(strFmt("@SYS7987",this.accountNum));
        return true;
    }

## Method modifiers
Several modifiers can be applied to method declarations. Some of the modifiers can be combined (for example, **final static**). Here are the method modifier keywords:

-   **abstract** – The method is declared but isn't implemented in a parent class. The method must be overridden in subclasses. If you try to create an object from a subclass where one or more abstract methods that belong to the parent class haven't been overridden, you receive a compiler error. Classes can also be abstract. Sometimes, a class should not be instantiated even though it represents an abstract concept. Only subclasses should be instantiated. Base classes of this type can be declared as **abstract**. For example, you want to model the concept of an account. Accounts are abstract, because only derived classes (ledger accounts and so on) exist in the real world. This examples describes a clear case where you should declare the **Account** class as **abstract**.
-   **display** – The method's return value should be shown on a page or a report. The value can't be modified on the page or report. Typically, the return value is a calculated value, such as a sum.
-   **edit** – The method's return type should be used to provide information for a field that is used on a page. The value in the field can be modified.
-   **final** – The method can't be overridden in any class that derives from its class.
-   **public** – Methods that are declared as **public** can be accessed anywhere that the class is accessible, and they can be overridden by subclasses. Methods that have no access modifier are implicitly public.
-   **protected** – Methods that are declared as **protected** can be called only from methods in the class and in subclasses that extend the class where the method is declared.
-   **private** – Methods that are declared as **private** can be called only from methods in the class where the private method is declared.
-   **static** – The method is a class method and doesn't act on an instance. Static methods can't refer to instance variables. They aren't invoked on an instance of the class. Instead, the are invoked by using the class name (for example, **MyClass::aStaticProcedure()**).

### Methods that have modifiers

**Note:** The following examples show only the method headers.

    // A method that cannot be overridden
    final int dontAlterMe() 

    // A static method 
    static void noChange()

    // A display method that returns an integer
    display int value()

## Static class members
You declare static class members by using the **static** keyword. The **static** keyword instructs the system to create only one instance of the method, regardless of the number of times that you call **new**. This one instance is used throughout your session. In general, static methods are intended for cases where the following criteria are met:

-   The method has no reason to access the member variables that are declared in the class.
-   The method has no reason to call any instance (non-static) methods of the class.

#### Static methods

This section describes a scenario where a software key type is used to help prevent piracy. Each instance of a software key can have its own unique value. However, because all software keys must conform to the rules of software key design, the logic that tests for software key conformance is the same for all software keys. Therefore, the method that contains the conformance validation logic should be static. Here is an example of a method that is declared by using the **static** keyword.

    static public boolean validateSoftwareKey(str _softwareKeyString)
    {
          // Your code here.
    }

In the following example, you don't have to construct an instance of the **SoftwareKey** class before you call a static method on the class. When you want to call the static **validateSoftwareKey** method, the syntax starts with the name of the class that contains the method. A pair of colons (::) is used to connect the class name to the static method name.

    boolean yourBool = SoftwareKey::validateSoftwareKey(yourSoftwareKeyString);

#### Static fields

Static fields are fields that are declared by using the **static** keyword. Conceptually, they apply to the class, not to instances of the class.

### Static constructors

Static constructors are guaranteed to run before any static or instance calls are made to the class. In C\#, the *static* concept is related to the whole executing application domain. However, in X++, the execution of the static constructor is relative to the user’s session. The static constructor has the following syntax.

    static void TypeNew() 

You never explicitly call the static constructor. The compiler will generate code to make sure that the constructor is called exactly one time before any other method on the class. A static constructor is used to initialize any static data or perform a particular action that must be performed only one time. No parameters can be provided for the static constructor, and it must be marked as **static**. The following example shows how to create a singleton instance by using a static constructor.

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

The singleton guarantees that only one instance of the class will ever be called. The following example shows how to instantiate the singleton.

    {
        Singleton i = Singleton::Instance();
    }

## Method access control
You use the accessor keywords **public**, **protected**, and **private** to control whether the methods in other classes can call the methods on your class. The accessor keywords on methods also interact with the rules for class inheritance. Here are the accessor keywords that you use with methods:

-   **public** – Methods that are declared as **public** can be called from anywhere that the class is accessible. In addition, a public method can be overridden by a subclass, unless the method is declared as **final**.
-   **protected** – Methods that are declared as **protected** can be called only from the following methods:
    -   Methods in the class.
    -   Methods in a subclass of the class that contains the protected method. Methods that are protected can be overridden in subclasses.
-   **private** – Methods that are declared as **private** can be called only from methods in the class where the private method is declared. No private method can be overridden in a subclass. By default, when you create a new method, the **private** accessor keyword appears in the code editor. For maximum security, **private** is the most conservative default accessor keyword.

### Static and instance methods

The accessor keywords on methods never restrict calls between two methods that are in the same class, regardless of which method is static or non-static. In a static method, calls to the **new** constructor method are valid even if the **new** constructor method is decorated with the **private** modifier. The syntax for these calls requires that the **new** keyword be used. The code in a static method must construct an instance object of its own class before it can call any instance methods on the class.

### Increasing access during overrides

When a method is overridden in a subclass, the overriding method must be at least as accessible as the overridden method. For example, the following compiler rules apply when a protected method is overridden in a subclass:

-   A public method in a superclass can be overridden only by a public method in the subclass.
-   In a subclass, a public or protected method can override a protected method of the superclass.
-   In a subclass, a private method can't override a protected method of the superclass.

## Optional parameters
Parameters can be initialized in the method declaration. In this case, the parameter becomes an *optional parameter*. If no value is supplied in the method call, the default value is used. All required parameters must be listed before the first optional parameter. The following examples show how to create and call a method that has optional parameters. The example of the **AddThreeInts** method shows that you can't skip default parameters when you call a method.

### Examples of optional parameters

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
    // be overridden in the call. 
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

## Accessor methods
Class variables are private. By hiding details of the internal implementation of a class, you can change the implementation of the class later without breaking any code that uses that class. To access the data from reference variables, you must create accessor methods. The following example defines a **Point** class that uses accessor methods to access the variables **x** and **y**.

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

These method declarations show how the **Point** class provides access to its variables from the outside world. Other objects can manipulate the instance variables of **Point** objects by using the accessor methods.

    // Declare a variable to refer to a Point object
    Point myPoint; 
    // Create a Point object
    myPoint = new Point(); 
    // Set the x variable using the accessor method
    myPoint.setX(10.0); 
    // Set the y variable by means of the accessor method
    myPoint.setY(25.7);

The depth of the call stack is limited to 100.

## Overriding a method
The methods in a class are inherited by any class that extends it. To change the functionality of an inherited method, you can create a method in the subclass, and then give that method the same name and parameters as the method in the superclass. This process is known as *overriding* the method. In the following example, **ColorAttribute** is a subclass of **Attribute** and therefore inherits the **methodAttr** method. However, because **ColorAttribute** defines a method that has the same name and the same number of arguments, the method in the superclass is overridden.

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

### Preventing method overrides

Static methods can't be overridden, because they exist per class. To protect other sensitive methods, or core methods, from being overridden, use the **final** modifier. In the following example, because **methodAtt** is declared as **final**, it can't be overridden in any class that extends **Attribute**. You should not specify **new** or **finalize** methods as **final**. The following example shows how to use the **final** keyword.

    public class Attribute
    {
        int objectVariable;

        final void methodAtt()
        {
            //Some statements
        }
    }

### Overriding vs. overloading

Overriding occurs when the superclass's implementation of a method is changed by the subclass's implementation of that method, but the signatures of both methods are the same. By contrast, *overloading* occurs when more than one method has the same name, but the methods have different signatures (return types, parameter lists, or both). X++ supports overriding, but it doesn't support overloading.

## Parameters
All methods have their own *scope*. A method can take one or more parameters. Within the scope of the method, these parameters are treated as local variables and are initialized with a value from the parameter in the method call. All parameters are passed by value. You can't change the value of the original variable. You can change only the local variable in the method. This local variable is a copy of the original variable.

## Scope of variables in methods
A scope defines the area in which an item can be accessed. Variables that are defined in a class are available to the methods within that class. Variables in methods can be accessed only within the current block.

## Local functions
You can declare local functions inside a method. However, as a best practice, you shouldn't add local functions inside the method. Instead, you should add private methods to the class. The following example shows valid declarations of two local functions, **localFunc55b** and **localFunc66c**. Calls to the local functions occur after the function declarations in the example, as is required.

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

### Declaration of local functions

-   The declarations of local functions must physically precede any non-declaration statements in the method.
-   You can declare more than one local function in your method. However, all local functions must be declared in an uninterrupted series, and the set must be terminated by one semicolon (;).

### Variable scope

-   Code that is inside the local function can access variables that are declared in the method that contains the local function.
-   Code that is outside the local function can't access variables that are declared in the local function.

### Calls to local functions

-   A local function can be called only by code in the same method where the local function is declared.
-   A local function should never call itself. Such recursion can prevent successful compilation.

## The this keyword
The **this** keyword is a reference to the instance of the class or table where the **this** keyword is used. The **this** reference is never required, but it can clarify your code and enhances the behavior of IntelliSense in the code editor. All calls to instance methods must be qualified by either the **this** reference or a variable. The **this** reference can be used to qualify the following information:

-   The names of other instance (non-static) methods in the same class where the **this** reference is used. Here is an example: **boolColorChanged = this.colorItOrange();**
-   The names of methods that are inherited by the **this** object.
-   The names of fields on the table that contains the method that the **this** keyword is used in.

The **this** reference can't be used in the following ways:

-   It can't qualify the names of member variables that are declared in the **classDeclaration** code.
-   It can't be used in a static method.
-   It can't qualify the names of static methods of the class or table.

## Interfaces
An *interface* is a specification for a set of public instance methods. An interface defines and enforces similarities between unrelated classes without having to derive one class from the other. All interfaces are public, even if you don't explicitly add the **public** keyword ****in front of the **interface** keyword ****in the **classDeclaration** code. The methods on an interface are also public. Once again, explicit inclusion of the keyword **public** is optional. To create an interface, follow these steps.

1.  In Server Explorer, right-click the project, and then click **Add**.
2.  In the **New Item** dialog box, select **Interface**, and then enter a name for the interface.
3.  Click **Add**.

When you add the **implements** keyword on a class declaration, the class must declare the methods that are specified by the interface. A class declaration can implement multiple interfaces. Just list the interfaces after the single occurrence of the **implements** keyword, and separate the interface names by using commas. All interface methods that a class implements must be explicitly declared as **public** by using the **public** keyword in the class. A class that implements an interface must also be declared as **public**. An interface can extend another interface by using the **extends** keyword. However, an interface can't extend more than one interface.

### Interface example

In the following example, an **Automobile** class implements an **IDrivable** interface. The **is** keyword is supported and lets you test whether a class implements an interface.

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

## Class library overview
There are two kinds of classes: *application classes* and *system classes*.

-   **Application classes** – These classes are implemented in X++. They are available in the **Classes** node in Application Explorer.
-   **System classes** – These classes are sometimes known as *kernel classes* and are implemented in C++. They are listed under the **System Documentation** &gt; **Classes** node in Application Explorer. However, the source code for these classes isn't available.

For a list of these classes, see [API, class, and table reference](api-reference.md).

## Substituting application classes for system classes
You should call the *substitute application classes* instead of the system classes that they extend. In Application Explorer, under **System Documentation** &gt; **Classes**, several kernel or system classes have names that begin with a lowercase *x*. These classes are known as *x-system classes*. Examples of these system classes are **xApplication** and **xVersionControl**. Some of these classes are extended by application classes. For example, the **Application** class extends the **xApplication** system class. The classes that derive from x-system classes are known as substitute application classes. In Application Explorer, under the **Classes** node, the icon next to the substitute application classes differs from the standard icon.

### x-system classes

Some of the substitute application classes are associated with a special global variable that represents an instance of the class. For example, the **appl** variable references a pre-instantiated object from the **Application** class. The advantage of the **appl** variable is that the system maintains the object throughout the scope of your session. Your code would be less efficient if it repeatedly used the **new Application()** syntax to obtain an instance of the **Application** class. You should not use the **xApplication** system class. Instead, use the **Application** substitute application class. You can reference the static members of the **Application** class by using the following standard syntax: **Application::checkForNewBatchJobs()**. However, to reference the instance members of the **Application** class, you should use that class's **appl** variable, if it exists. This pattern applies to most of the x-system classes. The **Session** substitute application class is one exception, because there is no special global variable for **Session**. The following table lists the x-system classes that have a corresponding substitute application class. The special global variables are also shown for those classes that have one.

| Application class | x-system class  | Global variable    |
|-------------------|-----------------|--------------------|
| Args              | xArgs           | Not applicable     |
| Application       | xApplication    | **appl**           |
| ClassFactory      | xClassFactory   | **classFactory**   |
| Company           | xCompany        | **appl.company**   |
| Global            | xGlobal         | Not applicable     |
| Info              | xInfo           | **Infolog**        |
| MenuFunction      | xMenuFunction   | Not applicable     |
| Session           | xSession        | Not applicable     |
| VersionControl    | xVersionControl | **versionControl** |

### Example of x-system classes

The following example shows the syntax for using several special variables that reference instances of the substitute application classes.

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

## Running startup commands
You use the **SysStartupCmd** class framework to run commands at startup. When Microsoft Dynamics 365 for Operations starts, calls are made to the **startup** methods on the application-substituted kernel classes **Application** (**Application.startup**) and **Info** (**Info.startup**). The **startup** methods are used for vital system and version-specific calls, and you must never directly modify these methods. Instead, use the **SysStartupCmd** framework. Serious issues can occur if the SYS layer versions of the **startup** methods aren't called. The following example shows the order that calls are run in when Dynamics 365 for Operations starts.

    appl.startup() // The SysStartupCmd class is instantiated here.
    sysStartupCmd.applInit()
    super()
    sysStartupCmd.applRun()
    info.startup()
    sysStartupCmd.infoInit()
    super()
    sysStartupCmd.infoRun()

### Commands that are available when Dynamics 365 for Operations starts

The **SysStartupCmd.construct** method lists the commands that are available when Dynamics 365 for Operations starts. Here are some of these commands:

-   AutoRun
-   AOTImport
-   Synchronize

The following example shows how to run a new command when Dynamics 365 for Operations starts. First, a class that extends **SysStartupCmd** is created. This new class performs your specific task. You then modify the construct method on **SysStartupCmd** to call your class. In the Dynamics 365 for Operations Configuration Utility, on the **General** tab, in the **Command to run at application startup** field, you can add commands that are run at startup. Alternatively, you can use the **-startupcmd= *MyCommand*** command-line parameter.

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

## Batch processing classes
You implement classes by using the batch processing system, and by extending the **RunBase** and **RunBaseBatch** classes. To remove the **Recurrence** button from the **Batch processing** dialog box, you use the **Args::parmEnum** method. We recommend that you designate a class to run as a server-bound batch method. Server-bound batch methods are more secure than batch methods that aren't server-bound for the following reasons:

-   The method is run by using the permissions of the user who submitted the method.
-   The method can use only specific **Info** and **Global** class methods to interact with the client that is processing it. This restriction limits interaction with the client.

### Enable a class to run as a server-bound batch method

1.  Create a class that extends the **RunBaseBatch** class.
2.  Override the **RunBaseBatch.runsImpersonated** method to return a value of **true**, as shown in the following example.

        public boolean runsImpersonated()
        {
            return true;
        }

3.  Confirm that the class calls only the following **Info** and **Global** class methods:
    -   add
    -   Info.copy
    -   Info.cut
    -   Info.import
    -   Info.export
    -   Info.line
    -   Info.num
    -   Global::error
    -   Global::info
    -   Global::warning

    **Note:** The **Info.line** and **Info.num** methods are inherited from the **xInfo** class.

### Removing the Recurrence button from the batch processing dialog box

When you implement a class by using the batch processing system, you can remove the **Recurrence** button by calling the **Args.parmEnum** method and passing the **NoYes::Yes** system enumeration value. The **NoYes** system enumeration determines whether the **Recurrence** button is removed from the dialog box. The default value is **NoYes::No**. In the following example, the **InventTransferMultiShip** class is implemented. The **BatchDialog::main** method creates the **Batch processing** dialog box.

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

## Image manipulation classes
Two system classes let you to manipulate graphics and icons: **Image** and **Imagelist**.

-   **Image** – This class lets you load, save, and manipulate individual images. For example, you can capture a screen and save it as an image, crop or rotate an image, or manipulate the color depth.
-   **Imagelist** – This class lets you work with a set of images that have common properties, such as the size and transparency color. You can view the image lists that are used in Dynamics 365 for Operations in the **ImageListAppl\_\*** application classes.

## Query object model
The query object model contains classes that are used to define and run a query. The query objects are used to define the query data source, the fields that are returned, record ranges, and relations to child data sources. The query classes are more visible when you create a dynamic query in code, but they are also used behind the scenes when you create a static query in Application Explorer. The following table describes the classes in the query object model.

| System class         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| QueryRun             | This class runs the query and fetches the data.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Query                | This class holds some properties, and has one or more related data sources. It's the top level of the query definition.                                                                                                                                                                                                                                                                                                                                                                                                                             |
| QueryBuildDataSource | This class defines access to a single data source in the query. If there is more than one data source at the same level in a query, separate SQL statements are produced and are run sequentially. If one data source is a child of another data source, a join is created between the two data sources.                                                                                                                                                                                                                                            |
| QueryBuildFieldList  | This class defines the fields that are returned from the database. By default, the field list is dynamic, and all fields are returned from the data source table, map, or view. Each data source has only one **QueryBuildFieldList** object. This object contains information about all selected fields. You can specify aggregate functions, such as **SUM**, **COUNT**, and **AVG**, on the field list object.                                                                                                                                   |
| QueryBuildRange      | This class defines a subset of records that is returned, based on a single field. A range is translated into a **WHERE** clause in the query SQL statement. If more than one field is used to limit the query (**WHERE** clause), the data source will contain more than one range.                                                                                                                                                                                                                                                                 |
| QueryBuildDynalink   | This class contains information about a relation (limitation) to an external record. When the query is run, this information is converted to additional entries in the **WHERE** clause of the query SQL statement. This class can exist only on the parent data source of a query. Forms use the function when two data sources are synchronized. The child data source will then contain one or more DLLs to the parent data source. The function is used even if the two data sources are put in two different forms but are still synchronized. |
| QueryBuildLink       | This class specifies the relation between the two data sources in the join. This class can exist only on a child data source.                                                                                                                                                                                                                                                                                                                                                                                                                       |

## System classes overview
System classes (or kernel classes) are implemented in C++. The source for these classes isn't available. A system class can have the following characteristics:

-   Static methods (or class methods)
-   Dynamic methods
-   Properties – These properties are member functions that are used to set properties. An example is **LeftMargin**.

You can't override system class methods. It isn't our intention that you will use the system classes to design your application objects from scratch. Instead, use them to extend or modify the default functionality in Application Explorer. For example, you can dynamically add extra information to an existing report. Alternatively, you can change the options that are available on a page, based on the user's selection on a previous page.

### Collection classes

The *collection classes* let you create lists, sets, structs, maps, and arrays.

### Application object classes

These system classes hold functions that are activated whenever you use Application Explorer to create your application. For example, the system uses the **FormDesign** class when you define the layout of your form in the **Designs** node in Application Explorer. These classes also let you to create and modify application objects.

### Integration classes

The integration with the environment is typically implemented by classes. Here are some examples of the classes in this category:

-   **COM** – The call of methods on COM objects.
-   **DLL** – The call of Microsoft Windows DLL functions.
-   **IO** – Read and write external files.
-   **ODBCConnection** – An Open Database Connectivity (ODBC) interface to a foreign database.

## Event terminology and keywords
You can use the event design pattern to make your code more modular and reusable. The term *event* is a metaphor that explains how delegates are used. When something important occurs during a program run, other modules might have to process the occurrence. These important occurrences are known as *events*. When an event occurs, the program tells its notifier for the event that the notifier must send notifications about the event. A notification must be sent to all the event handlers that are subscribers of the notifier. When the program tells its notifier to send the notifications, we call that process *raising* an event. The following table shows the terms that are used to describe the event metaphor.

| Term          | Description                                                                                                               |
|---------------|---------------------------------------------------------------------------------------------------------------------------|
| Event         | An important occurrence in a program module where additional modules must process the occurrence.                         |
| Notifier      | The program element that sends information about the event to all the event handlers that are subscribed to the notifier. |
| Subscriber    | The program functions or methods that are subscribed to an event notifier.                                                |
| Event handler | The methods that subscribe to an event notifier. Only the appropriate kind of methods can be event handlers.              |

### Keywords that are used for programming that uses delegates

The following table shows the keywords that describe the use of delegates.

| Keyword or term                         | Code                                                                     | Description                                                                                                                                                                                                                                                                             |
|-----------------------------------------|--------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| delegate                                | delegate myDelegate(str \_information) {}                                | The code shows what the delegate looks like in the method editor in the Microsoft MorphX client. Because the return type is always **void**, it isn't mentioned in the syntax. No code is allowed inside the braces ({}).                                                               |
| eventHandler                            | myClassInstance.myDelegate += eventHandler(otherClass.myInstanceMethod); | Although the syntax of the **eventHandler** keyword might give the impression that **eventHandler** is an X++ function, it isn't a function. The **eventHandler** keyword tells the compiler that a method is being subscribed to a delegate.                                           |
| Subscribe or add a method to a delegate | myClassInstance.myDelegate += eventHandler(OtherClass::aStaticMethod);   | In the code, the static method **OtherClass::aStaticMethod** becomes subscribed to the delegate.                                                                                                                                                                                        |
| Call a delegate                         | myClassInstance.myDelegate("Hello");                                     | This call to the delegate prompts the delegate to call each method that is subscribed to the delegate. The subscribed methods are called in the same order in which they were added to the delegate. One subscribed method must be completed before the delegate calls the next method. |



