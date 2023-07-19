---
title: X++ composite data types
description: This article describes composite data types in X++.
author: josaw1
ms.date: 08/27/2021
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# X++ composite data types

[!include [banner](../includes/banner.md)]

This article describes composite data types in X++. The composite data types in X++ are arrays, containers, classes as data types, delegates as data types, and tables as data types.

## Array

An *array* is a variable that contains a list of items that have the same data type. The elements of an array are accessed by using integer indexes. You use a separate statement to initialize each element in an array. When you use a container data type or an array object to create a collection, you can initialize multiple elements by using a single statement. By default, all the items in an array have the default value of the data type in the array. There are three kinds of arrays: *dynamic arrays*, *fixed-length arrays*, and *partly on disk arrays*.

- **Dynamic arrays** – These arrays are declared by using an empty array option. In other words, they have only brackets (\[\]).
- **Fixed-length arrays** – These arrays can hold the number of items that is specified in the declaration. Fixed-length arrays are declared like dynamic arrays, but a length option is included in the brackets.
- **Partly on disk arrays** – These arrays are declared as either dynamic arrays or fixed-length arrays that have an extra option that declares how many items should be held in memory. The other items are stored on disk and are automatically loaded when they are referenced.

X++ supports only one-dimensional arrays. However, you can mimic the behavior of multiple array indexes. (For more information, see the [Multiple array indexes](#multiple-array-indexes) section). Variables in objects and tables can be declared as arrays. For example, this functionality is used in address lines in the standard application. An array collection class lets you store objects in an array.

Array indexes begin at 1. The first item in the array is referenced as \[1\], the second item is referenced as \[2\], and so on. The following syntax is used to access an array element: **ArrayItemReference = ArrayVariable \[ Index \]**. In this syntax, **ArrayVariable** is the identifier of the array, and **Index** is the number of the array element. **Index** can be an integer expression. Item zero \[0\] is used to clear the array. If a value is assigned to index 0 in an array, all elements in the array are reset to their default value.

An assignment of one entire array to another is performed by reference.

### Array examples

```xpp
public void ArrayMethod()
{
    int myArray[10]; // Fixed-length array with 10 integers.
    myArray[4] = 1; // Accessing the 4th element in the array.
    myArray[0] = 0; // Resets all elements in intArray.

    // Dynamic array of integers.
    int intArray[];

    // Dynamic array of variables of type Datatype.
    //Datatype arrayVariable[];

    // Fixed-length arrays.
    boolean boolArray[100]; // Fixed-length array of booleans with 100 items.

    // Two examples of Partly On Disk Arrays.
    // Dynamic integer array with only 100 elements in memory.
    int arrayVariable [ ,100];
    // Fixed-length string array with 1000 elements, and only 200 in memory.
    str arrayVariable2 [1000,200];

    // A dynamic array of integers.
    int i[];
    // A fixed-length real array with 100 elements.
    real r[100];
    // A dynamic array of dates with only 10 elements in memory.
    date d[,10];
    // A fixed length array of NoYes variables with 100 elements and 10 in memory.
    NoYes ny[100,10];
}
```

### Multiple array indexes

Some languages, such as C++ and C\#, let you declare arrays that have more than one index. In other words, you can define "arrays of arrays." In X++, you can't directly create multiple array indexes because only one-dimensional arrays are supported. However, you can implement multiple indexes by using the method that is described in this section. For example, you want to declare an array that has two dimensions, to hold an amount that is earned by country/region by dimension. There are 10 countries and three dimensions. In C++ and C\#, you declare the following array.

```csharp
// This is C# or C++ code, not X++ code.
long earning[10, 3];
```

However, X++ doesn't support this declaration. Instead, you can define a one-dimensional array where the number of elements is the product of the elements in each dimension. Here is an example.

```xpp
public void MultipleArrayMethod()
{
    // Step 1: define a one-dimensional array with the number
    // of elements that is the product of the elements in each dimension.
    real earnings[10*3];

    // Step 2: to refer to a specific element, such as earnings[i,j], write the following:
    // declare i and j (maybe) and assign the value to something
    int i = 1;
    int j = 2;
    real element = earnings[(i-1)*3 + j];
}

// This can be written into a macro like this:
#localmacro.earningIndex
(%1-1)*3+%2
#endmacro

public void CallTheMacro()
{
    // Next, call the specific element within the macro like this:
    int i = 1;
    int j = 2;
    real element = earnings[#earningIndex(i,j)];

    // The previous scheme can be extended to any number of dimensions.
    // The element a[i1, i2, ..., ik] can be accessed by computing the
    // offset into an array containing (d1*d2*...*dk) elements.
    //(i1 - 1)*d2*d3*..*dk +
    //(i2 - 1)*d3*d4*...*dk + .... +
    //(ik-1 -1)*dk +
    //(ik-1)
}
```

## Container

A *container* object is a dynamic list of items that contains primitive data types or composite data types. A container is useful when you must pass various types of values between the client and server tiers. However, if you plan to repeatedly add to a list in a loop, a container isn't a good choice. Containers are most suitable for processes that don't involve excessive modification to the size or contents of the container. When a container undergoes excessive additions of data, overall system performance can decrease because container data must be repeatedly copied and new space must be repeatedly allocated.

A container isn't a class. A container contains an ordered sequence of primitive values or other containers. Because of the flexibility of **anytype**, a container offers a good way to store values of different types together. A container can be stored in the database. A container is one of the column types that you can select when you use Application Explorer to add a column to a table. A container slightly resembles an array, or collections, such as the **List** or **Stack** classes. However, you can never change the size or content of a container after the container is created.

X++ statements that appear to modify a container are internally building a new container and copying values as required. Even an assignment of a container to another container variable creates a new copy of the container. All these operations can affect performance. In the functions that provide access to a container (such as **conPeek**), the container is 1-based, not 0-based. Indexing is 1-based for arrays. The default value of a container is **empty**. The container doesn't contain any values. Some statements that use containers might appear to modify a container, however, inside the system, containers are never modified. Instead, the data from the original container is combined with data from the command to build a new container. You can create a new container by using one of the following functions: **conDel**, **conIns**, or **conPoke**.

Additionally, the **Global** class has static methods for handling containers. These methods include **con2ArraySource**, **con2Buf**, **con2List**, **con2Str**, **containerFromXmlNode**, **conView**, and **str2Con**. There are several intrinsic functions for handling a container, such as **conIns** and **conPeek**. The X++ **conPeek** function returns an **anytype** type, therefore, it's easier to read the values from a container when you don't know the type of each value. An **anytype** can be assigned to any X++ value type, provided that the value can be converted. Your code is easier to read when it avoids explicit data type conversions. Therefore, assign values from a container to the same data type that was used to put the value into the container. You must not assign a container to an **anytype** because the system might not be able to determine the correct conversions. In these cases, unexpected behavior or errors might occur.

### Comparing container to other options

The **container** type resembles other constructs, such as arrays and collection classes, such as **List** and **Stack**. The difference between a **container** and **List** is that an instance of the **List** class is mutable. A **List** object first allocates more space than its data consumes. Then, as data is added, the space is filled. This behavior is more efficient than allocating more space every time that an element is added. An update of a **List** performs faster than similar operations on a container.

When you construct a **List** object, you determine the one type of data that the **List** object can store. This restriction is less flexible for a **List** than it is for a container. However, you can store objects in a **List**, whereas a container can store only value types. The difference between a container and an array is that an array can hold only items of its declared type. You can allocate memory space for an array and fill that space with values later. For example, you can fill in values in a loop. This behavior is efficient and performs well. When you want to build a new container by appending new data, you can use either the **+=** operator or the **conIns** function. The **+=** operator is the faster alternative. Use the **conIns** function only when you want to add new data before the last index of the original data.

You can't store object references in containers. When the compiler detects an attempt to store an object reference in a container, it issues an error message. If the type of the element that is added to the container is **anytype**, the compiler can’t determine whether the value is a reference type. In this case, the compiler allows the attempt. Although the compiler doesn't diagnose the code as erroneous, an error will be thrown at run time.

### Container examples

```xpp
public void ContainerExample()
{
    // First, declare the variables you are using.
    container myContainer;
    container myContainer4;
    container myContainer5;
    // Three ways to declare a container.
    myContainer = [1];
    myContainer += [2];
    myContainer4 = myContainer5;

    // Declare a container.
    container cr3;

    // Assign a literal container to a container variable.
    cr3 = [22, "blue"];

    // Declare and assign a container.
    container cr2 = [1, "blue", true];

    // Mimic container modification (implicitly creates a copy).
    cr3 += [16, strMyColorString];
    cr3 = conIns(cr3, 1, 3.14);
    cr3 = conPoke(cr3, 2, "violet");

    // Assignment of a container (implicitly creates a copy).
    cr2 = cr3;

    // Read a value from the container.
    str  myStr = conPeek(cr2, 1);

    // One statement that does multiple assignments from a container.
    str myStr;
    int myInt;
    container cr4 = ["Hello", 22, 20\07\1988];
    [myStr, myInt] = cr4; // "Hello", 22

    // Example of applying the = operator to a container. The example
    // initializes myContainer2 and myContainer33.
    myContainer2 = [2, "apple"];

    // Next, you make a copy of myContainer33 and assign the copy to myContainer2.
    myContainer33 = [33, "grape"];
    myContainer2 = myContainer33;  // The container that myContainer2 had been holding is no longer available and cannot be recovered.
    // An example of building a new container by
    // assigning a new value to myContainer33 through the += operator.
    myContainer33 += [34, "banana"];
}

// Container example. In this example, variable2 and variable33 hold different containers.
static void JobC(Args _args)
{
    container variable2, variable33;
    variable2 += [98];
    variable33 = variable2;
    variable2 += [97];
}

// List class example. In this example, variable2 and variable33 refer to the same List object.
static void JobL(Args _args)
{
    List variable2,variable33;
    variable2 = new List(Types::Integer);
    variable2.addEnd(98);
    variable33 = variable2;
    variable2.addEnd(97);
}

// The automatic type conversion by anytype also applies to the special syntax for making multiple
// assignments from a container in one statement. This is shown in the following code example,
// which assigns a str to an int, and an int to a str.
static void JobContainerMultiAssignmentUsesAnytype(Args _args)
{
    container con2;
    int int4;
    str str7;
    con2 = ["11", 222];
    [int4, str7] = con2;
    info(strfmt("int4==11==(%1), str7==222==(%2)", int4, str7));
}

/***  Output:
Message (10:36:22 am)
int4==11==(11), str7==222==(222)
***/

static void UseQuery()
{
    // An example of how the compiler diagnoses attempts to store object in containers
    container c = [new Query()];   // This statement will cause the error message shown below.
    /*** Instance of type 'Query' cannot be added to a container. ***/

    // An example of a code that won't cause an error message, but will
    // cause an error message to be thrown at runtime.
    anytype a = new Query();
    container d = [a];
}
```

## Classes as data types

A *class* is a type definition that describes both variables and methods for instances of the class. (The instances of a class are also known as *objects*.) A class is only a definition for objects, and all objects are **null** when they are declared. In Application Explorer, every application class under the **Classes** node is a data type. You can declare variables of these types in your code. You can construct instances of a class and assign the instances to variables.

Classes can be nested in source code. Nested classes are available only inside forms (such as a class that extends **FormRun**), and are used to represent controls, data sources, or data fields. An attribute decoration, such as the attribute decoration on a class or a method, can omit the suffix of the attribute name if the suffix is **Attribute**. Therefore, X++ allows **\[MyFavorite\]** instead of requiring **\[MyFavoriteAttribute\]**. Additionally, attributes are now applied to the handlers of delegates and methods, to map the handlers to those targets.

In AX 2012 and earlier versions, you could designate a method to run on either the client or the server. However, in finance and operations applications, all compiled X++ code is run as .NET Common Intermediate Language (CIL) on the server. There is no longer any code that is evaluated at the client site or in the browser. Therefore, the **client** and **server** keywords are now ignored. Although these keywords don't cause a compile error if they are used, they should not be used in any new code.

### Private and protected member variables

Previously, all member variables that were defined in a class were protected. You can now make the visibility of member variables explicit by adding the **private**, **protected**, and **public** keywords. The interpretation of these modifiers is obvious and is aligned with the semantics for methods:

- **private** – The member variable can be used only within the class where it’s defined.
- **protected** – The member variable can be used in the class where it’s defined and all subclasses of that class.
- **public** – The member variable can be used anywhere. It’s visible outside the confines of the class hierarchy where it’s defined.

By default, member variables that aren’t adorned with an explicit modifier are still protected. However, as a best practice, you should explicitly specify the visibility. As we described earlier, when a member variable is defined as **public**, it can be accessed outside the class where it’s defined. In this case, you must specify a qualifier that designates the object that is hosting the variable. To specify the qualifier, use the dot notation, as you do for method calls.

In the following example, **field1** is accessed by using the explicit **this** qualifier. In this case, it might not be a good idea to make a member variable public, because that approach exposes the internal workings of the class to its consumers, and therefore creates a strong dependency between the class implementation and its consumers. You should always try to depend only on a contract, not an implementation.

```xpp
public class AnotherClass3
{
    int field1;
    str field2;
    void new()
    {
        this.field1 = 1;   // Explicit object designated.
        field2 = "Banana";  // 'this' assumed, as usual.
    }
}
```

### Static constructors and static fields

*Static fields* are fields that are declared by using the **static** keyword. Conceptually, static fields apply to the class, not to instances of the class. Static constructors are guaranteed to run before any static calls or instance calls are made to the class. The execution of the static constructor is relative to the user’s session. You never call the static constructor explicitly. Instead, the compiler will generate code to make sure that the constructor is called exactly one time, before any other method on the class is called. A static constructor is used to initialize any static data or perform an action that must be performed only one time. You can't provide parameters for the static constructor, and it must be marked with the **static** keyword.

```xpp
// An example of how a singleton (call instance in the example below)
// can be created using the static constructor.
public class Singleton
{
    private static Singleton instance;
    private void new()
    {
    }
    static void TypeNew()    // This is the static constructor.
    {
        instance = new Singleton();
    }

    public static Singleton Instance()
    {
        return Singleton::instance;
    }
}

// The singleton ensures that only one instance of the class
// will be called, which is consumed by the following.
{
    // Your code here.
    Singleton i = Singleton::Instance();
}
```

### Class elements in Application Explorer

Under most class nodes in Application Explorer, there are two special nodes: a **classDeclaration** node and a **new** node. A **classDeclaration** always contains the X++ **class** keyword. Additional keywords, such as **extends**, can be included to modify the class. This node can also contain declarations of member variables.

In the following example, the variables **m\_priority** and **m\_rectangle** are members of the class.

```xpp
// An example of a classDeclaration.
public class YourDerivedClass extends YourBaseClass
{
    int m_priority;
    Rectangle m_rectangle;
    void new(int _length, int _width)
    {
        this.m_rectangle = new Rectangle(_length, _width);
    }
}
```

A **new** operator contains logic that is run when the **new** operator is used to create an instance of the class. The logic in the **new** method might construct an object and assign that object to a variable that is declared in the **classDeclaration**. Each class can have only one **new** method. However, in the **new** method, you often should call the **new** method of the base class. To call the **new** method of the base class, call **super()**.

The following example shows the **new** method for the **YourDerivedClass** class in the previous **classDeclaration** example. In this **new** method, the code constructs an instance of the **Rectangle** class. The instance is assigned to the **m\_rectangle** variable. The **this** keyword that is used in the example is optional, however, if you include it, IntelliSense might be more helpful.

```xpp
// An example of the new method from the previous classDeclaration example.
void new(int _length, int _width)
{
    this.m_rectangle = new Rectangle(_length, _width);
}
```

### Garbage collection

Eventually during run time, most objects no longer have any variable that points to them. The system scans for these objects and erases them from memory. The memory space then becomes available for other uses. The **Object** class has a method that is named **finalize**. However, the **finalize** method isn't a destructor. The runtime never calls the **finalize** method, even when an object is collected as garbage.

### System classes

In Application Explorer, under **System Documentation** &gt; **Classes**, there is a list of the kernel classes or system classes. System classes aren't written in X++, and you can't see their source code. You can't add system classes. System classes usually have a **new** method, but they don't have a **classDeclaration** node. Every application class implicitly extends the **Object** system class. Some system classes are extended by an application class that has a similar name. For instance, **xClassFactory** is extended by **ClassFactory**. In these cases, you should not use the system class. For more information, see "Substitute application classes for system classes" in [Classes and methods](xpp-classes-methods.md).

### Extension methods

The extension method feature lets you add extension methods to a target class by writing the methods in a separate extension class. The following rules apply:

- The extension class must be static.
- The name of the extension class must end with the ten-character suffix **\_Extension**, however, there’s no restriction on the part of the name that precedes the suffix.
- Every extension method in the extension class must be declared as **public static**.
- The first parameter in every extension method is the type that the extension method extends. However, when the extension method is called, the caller must not pass in anything for the first parameter. Instead, the system automatically passes in the required object for the first parameter.
- The target of an extension method must be a class, table, view, or map application object type.

An extension class can contain private or protected static methods. These methods are typically used for implementation details and aren't exposed as extensions. The extension method technique doesn’t affect the source code of the class that it extends, therefore, the addition to the class doesn't require over-layering.

Upgrades to the target class are never affected by any existing extension methods. If an upgrade to the target class adds a method that has the same name as your extension method, your extension method can no longer be reached through objects of the target class. The extension method technique uses the same dot-delimited syntax that you often use to call regular instance methods. Extension methods can access all public artifacts of the target class, but they can’t access anything that is protected or private. Therefore, extension methods can be considered a type of syntactic sugar. Regardless of the target type, an extension class is used to add extension methods to the type. For example, an extension table isn't used to add methods to a table, and there’s no such thing as an extension table.

```xpp
// An example of an extension class holding a few extension methods.
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

## Delegates as data types

A *delegate* collects methods that subscribe to it. The delegate specifies the parameter signature that all its subscriber methods must share. When the delegate is called, the delegate calls each of its subscribers. A delegate never returns a value and **can't have a default value**. At first, every delegate has no subscribed methods. There is no limit on the number of parameters that a delegate can declare, and there is no limitation on the type of those parameters. The delegate body is always empty, because the delegate's only purpose is to define the contract that subscribers must conform to. A delegate doesn't have to be defined in a class. Delegates can also be defined in a table, form, or query.

### Delegate examples

```xpp
abstract class VarDatClass
{

    void new(utcdatetime _dateTime, str _changeDescription)
    {
        // An example of subscribing a delegate.
        this.notifyChanged += eventhandler(this.InfologChanges);
        this.notifyChanged += eventhandler(this.SaveInDatabase);
        
        notifyChange(_dateTime, _changeDescription);
    }

    void notifyChange(utcdatetime _dateTime, str _changeDescription)
    {
        // An example of calling a delegate.
        this.notifyChanged(_dateTime, _changeDescription);
    }
    
    // delegate method examples
    // An example of declaring a delegate.
    delegate void notifyChanged(utcdatetime _dateTime, str _changeDescription)
    {
    }

    // method that is to be subscribed.
    public static void InfologChanges(utcDateTime _dateTime, str _changeDescription)
    {
        info("A notification has occurred calling static handler:" +
            DateTimeUtil::toStr(_dateTime) +
            " Message:" +
            _changeDescription);
    }
    
    // method that is to be subscribed.
    public static void SaveInDatabase(utcDateTime _dateTime, str _changeDescription)
    {
       // save changes in database.
    }
    
    
}
```

## Tables as data types

All tables can be treated as class definitions. A table variable can be considered an instance (object) of the table (class) definition. For every field in a table variable, the default value is **empty**. You can address fields and create methods on tables. The methods can be invoked on instances of the table. To manipulate (that is, read, update, insert, and delete) records in tables, you must declare at least one table variable that can hold the record in focus. As a best practice, you should use the name of the table as the name of the variable but use an initial lowercase letter. Here are a few important differences between tables and objects:

- You can't allocate space for table variables. Allocation is done implicitly.
- Fields in table variables are public. You can reference them anywhere.
- Fields in table variables can be referenced by using expressions.

There is no automatic conversion, but table variables that are declared as **Common** can hold data from any table.

### Scope of table variables

In most respects, table variables can be considered objects, however, unlike objects, they aren't explicitly allocated. Only a variable declaration is required. All tables are compatible with the **Common** table, just as all objects are compatible with the **Object** class. Table variables are declared as common buffers and can be used to hold data from any table. You can't access tables that don't have table variables. The principles for declaring table variables and objects are the same, except with regard to the allocation of space.

### Table examples

The syntax enables various possibilities for referencing fields in records. For example, you can use the **TableName.(FieldId)** syntax.

The following example prints the contents of the fields in the current record in the Customer table.

```xpp
// Declares and allocates space for one CustTable record.
public void myMethod()
{
    CustomerTable custTable;
}

// An example of referencing table variables.
public void printAccountNo()
{
    CustomerTable custTable;
    print custTable.AccountNo;  // Prints the field reference.
}
```

The following example uses the **fieldCnt** and **fieldCnt2Id** methods. The **fieldCnt** method counts the number of fields in a table, whereas **fieldCnt2Id** returns the ID for a field number. For example, you can use the **fieldCnt2Id** method to learn that field number 6 in a table has the ID 54. This conversion is required, because there is no guarantee that the IDs of the fields in a table are consecutive.

```xpp
// An example of the various possibilities for referencing fields in records.
public void printCust()
{
    int i, n, k;
    CustomerTable custTable;
    DictTable dictTable;
    dictTable = new DictTable(custTable.TableId);
    n = dictTable.fieldCnt();
    print "Number of fields in table: ", n;
    for(i=1; i<=n; i++)
    {
        k = dictTable.fieldCnt2Id(i);
        print "The ", dictTable.fieldName(k),
        " field with Id=",k, " contains '",
        custTable.(k), "'";
    }
}
```

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

