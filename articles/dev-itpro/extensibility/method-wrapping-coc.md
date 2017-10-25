---
# required metadata

title: Class extension - Method wrapping and Chain of Command
description: This topic discusses how to extend the business logic of public and protected methods by using method wrapping. 
author: robadawy
manager: AnnBe
ms.date: 08/21/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 26961
ms.search.region: Global
# ms.search.industry: 
ms.author: robadawy
ms.search.validFrom: 2017-08-21
ms.dyn365.ops.version: AX 7.0.0

---

# Class extension: Method wrapping and Chain of Command
The functionality for class extension, or class augmentation, has been improved. You can now wrap logic around methods that are defined in the base class that you're augmenting. You can extend the logic of public and protected methods without having to use event handlers. When you wrap a method, you can also access public and protected methods, and variables of the base class. In this way, you can start transactions and easily manage state variables that are associated with your class.

For example, a model contains the following code.

```
class BusinessLogic1
{
    str DoSomething(int arg) {
    …
    }
}
```

You can now augment the functionality of the **DoSomething** method inside an extension class by reusing the same method name. An extension class must belong to a package that references the model where the augmented class is defined.

```
[ExtensionOf(ClassStr(BusinessLogic1))]
final class BusinessLogic1_Extension
{
    str DoSomething(int arg) {
        // Part 1
        var s = next DoSomething(arg + 4);
        // Part 2
        return s;
    }
}
```


In this example, the wrapper around **DoSomething** and the required use of the **next** keyword create a Chain of Command (CoC) for the method. CoC is a design pattern where a request is handled by a series of receivers. The pattern supports loose coupling of the sender and the receivers.

We now run the following code.

```
BusinessLogic1 c = new BusinessLogic1();
info(c.DoSomething(33));
```

When this code is run, the system finds any method that wraps the **DoSomething** method. The system randomly runs one of these methods, such as the **DoSomething** method of the **BusinessLogic1_Extension** class. When the call to the next **DoSomething** method occurs, the system randomly picks another method in the CoC. If no more wrapped methods exist, the system calls the original implementation.

## Supported versions
> [!IMPORTANT]
> The functionality that is described in this topic (CoC and access to protected methods and variables) is available in Microsoft Dynamics 365 Unified Operations Platform update 9. However, the class that is being augmented must also be compiled on Platform update 9 or later. As of August 2017, all current releases of the applications for Microsoft Dynamics 365 for Finance and Operations, Enterprise edition, have been compiled on Platform update 8 or earlier. Therefore, to wrap a method that is defined in a base package (such as Application Suite), you must recompile that base package on Platform update 9 or later.
As an example: If you create your own extension model that is augmenting a class that exists in the Application Suite model, and if you are using CoC or acccessing protected methods/variables, you will need to build both Application Suite and your extension model. You will also need to create a deployable package that includes both models in order to deploy this functionality on a runtime environment.
This is a temporary situation until the next release of the Microsoft Dynamics 365 for Finance and Operations application.

## Capabilities
The following sections give more details about the capabilities of method wrapping and CoC.

### Wrapping public and protected methods
Protected or public methods of classes, tables, or forms can be wrapped by using an extension class that augments that class, table, or form. The wrapper method must have the same signature as the base method.

- When you augment form classes, only root-level methods can be wrapped. You can't wrap methods that are defined in nested classes.
- Only methods that are defined in regular classes can be wrapped. Methods that are defined in extension classes can't be wrapped by augmenting the extension classes.

### What about default parameters?
Methods that have default parameters can be wrapped by extension classes. However, the method signature in the wrapper method must not include the default value of the parameter.

For example, the following simple class has a method that has a default parameter.

``` 
class Person 
{
    Public void salute( str message = "Hi"){ }
}
```

In this case, the wrapper method must resemble the following example.

```
[ExtensionOf(classtr(Person))]
final class aPerson_Extension
{
    Public void salute( str message ){ }
}
```

In the **aPerson_Extension** extension class, notice that the **salute** method doesn't include the default value of the **message** parameter. 

### Wrapping instance and static methods
Instance and static methods can be wrapped by extension classes. If a static method is the target that will be wrapped, the method in the extension must be qualified by using the **static** keyword.

For example, we have the following **A** class.

```
class A 
{
    public static void aStaticMethod( int parameter1)
    {
    // …
    }
}
```
 
In this case, the wrapper method must resemble the following example.

```
[ExtensionOf(classstr(A)]
final class An_Extension
{
    public static void aStaticMethod( int parameter1)
    {
        Next aStaticMethod( 10 );
    }
}
```

> [!IMPORTANT]
> The ability to wrap static methods doesn't apply to forms. In X++, a form class isn't a new class, and can't be instantiated or referenced as a normal class. Static methods in forms don't have any semantics.

### Wrapper methods must always call next 

Wrapper methods in an extension class must always call **next**, so that the next method in the chain and, finally, the original implementation are always called. This restriction helps guarantee that every method in the chain contributes to the result.

In the current implementation of this restriction, the call to **next** must be in the first-level statements in the method body.

Here are some important rules:

- Calls to **next** can't be done conditionally inside an **if** statement. 
- Calls to **next** can't be done in **while**, **do-while**, or **for** loop statements. 
- A **next** statement can't be preceded by a **return** statement. 
- Because logical expressions are optimized, calls to **next** can't occur in logical expressions. At runtime, the execution of the complete expression isn't guaranteed.

> [!NOTE]
> The author of the original implementation of a method can explicitly allow wrapper methods to skip calling next. If the method you are wrapping is tagged with the [Replaceable] attribute, an extension class can wrap this method without calling the **next** keyword. Replaceable methods are methods that implement logic that can safely be "replaced" by custom implementation. This functionality is available with the release of Platform Update 11. 

### Wrapping a base method in an extension of a derived class
The following example shows how to wrap a base method in an extension of a derived class. For this example, the following class hierarchy is used.

```
class A
{
    public void salute(str message)
    {
        Info(message);
    }
}

class B extends A { }
class C extends A { }
```

Therefore, there is one base class, **A**. Two classes, **B** and **C**, are derived from **A**. We will augment or create an extension class of one of the derived classes (in this case, **B**), as shown here.

```
[Extensionof(classstr(B))]
final class aB_Extension
{
    public void salute(str message)
    {
        next salute( message );
        Info("B extension");
    }
}
```

Although the **aB_Extension** class is an extension of **B**, and **B** doesn't have a method definition for the **salute** method, you can wrap the **salute** method that is defined in the base class, **A**. Therefore, only instances of the **B** class will include the wrapping of the **salute** method. Instances of the **A** and **C** classes will never call the wrapper method that is defined in the extension of the **B** class. 

This behavior becomes clearer if we implement a method that uses these three classes.

```
class ProgramTest 
{
    Public static void Main( Args _args)
    {
        var a = new A( );
        var b = new B( );
        var c = new C( );

        a.salute("Hi");
        b.salute("Hi");
        c.salute("Hi");
    }
}
```

For calls to **a.salute(“Hi”)** and **c.salute(“Hi”)**, the Infolog shows only the message “Hi.” However, when **b.salute(“Hi”)** is called, the Infolog shows “Hi” followed by “B extension.” 

By using this mechanism, you can wrap the original method only for specific derived classes.

### Accessing protected members from extension classes
As of Platform update 9, you can access protected members from extension classes. These protected members include fields and methods. Note that this support isn't specific to wrapping methods but applies all the methods in the class extension. Therefore, class extensions are more powerful than they were before.

### The Hookable attribute
If a method is explicitly marked as **[Hookable(false)]**, the method can't be wrapped in an extension class. In the following example, **anyMethod** can't be wrapped in a class that augments **anyClass1**.

```
class anyClass1 
{
    [HookableAttribute(false)]
    public void anyMethod() {…}
}
```

### Final methods and the Wrappable attribute
Public and protected methods that are marked as **final** can't be wrapped in extension classes. You can override this restriction by using the **Wrappable** attribute and setting the attribute parameter to **true** (**[Wrappable(true)]**). Similarly, to override the default capability for (non-final) public or protected methods, you can mark those methods as non-wrappable (**[Wrappable(false)]**).

In the following example, the **doSomething** method is explicitly marked as non-wrappable, even though it's a public method. The **doSomethingElse** method is explicitly marked as wrappable, even though it's a final method.

```
class anyClass2 
{
    [Wrappable(false)]
    public void  doSomething(str message) { …}

    [Wrappable(true)]
    final public void  doSomethingElse(str message){ …}
}
```

## Restrictions on wrapper methods
The following sections describe restrictions on the use of CoC and method wrapping.

### Kernel methods can't be wrapped
Kernel classes aren't X++ classes. Instead, they are classes that are defined in the kernel of the Microsoft Dynamics 365 Unified Operations platform. Even though extension classes are supported for kernel classes, method wrapping isn't supported for methods of kernel classes. In other words, if you want to wrap a method, the base method must be an X++ method.

### X++ classes that are compiled by using Platform update 8 or earlier 
The method wrapping feature requires specific functionality that is emitted by an X++ compiler that is part of Platform update 9 or later. Methods that are compiled by using earlier versions don't have the infrastructure to support this feature.

### Nested class methods (forms) can't be wrapped
The concept of nested classes in X++ applies to forms for overriding data source methods and form control methods. Methods in nested classes can't be wrapped in class extensions.

### Tooling
For the features that are described in this topic, the Microsoft Visual Studio X++ editor doesn't yet offer complete support for cross-references and Microsoft IntelliSense. We plan to make complete support available in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition platform update 10.
