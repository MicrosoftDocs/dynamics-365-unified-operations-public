---

title: Class extension - Method wrapping and Chain of Command
description: This topic discusses how to extend the business logic of public and protected methods by using method wrapping.
author: jorisdg
ms.date: 12/18/2018
ms.topic: article
ms.prod: 
ms.technology: 

# ms.search.form:
# ROBOTS:
audience: Developer
# ms.devlang: 
ms.reviewer: tfehr
# ms.tgt_pltfrm: 
# ms.custom:
ms.search.region: Global
# ms.search.industry:
ms.author: jorisde
ms.search.validFrom: 2017-08-21
ms.dyn365.ops.version: AX 7.0.0

---

# Class extension - Method wrapping and Chain of Command

[!include [banner](../includes/banner.md)]

The functionality for class extension, or class augmentation, has been improved. You can now wrap logic around methods that are defined in the base class that you're augmenting. You can extend the logic of public and protected methods without having to use event handlers. When you wrap a method, you can also access public and protected methods, and variables of the base class. In this way, you can start transactions and easily manage state variables that are associated with your class.

For example, a model contains the following code.

```xpp
class BusinessLogic1
{
    str doSomething(int arg) 
    {
        // ...
    }
}
```

You can now augment the functionality of the **doSomething** method inside an extension class by reusing the same method name. An extension class must belong to a package that references the model where the augmented class is defined.

```xpp
[ExtensionOf(classStr(BusinessLogic1))]
final class BusinessLogic1_Extension
{
    str doSomething(int arg) 
    {
        // Part 1
        var s = next doSomething(arg + 4);
        // Part 2
        return s;
    }
}
```


In this example, the wrapper around **doSomething** and the required use of the **next** keyword create a Chain of Command (CoC) for the method. CoC is a design pattern where a request is handled by a series of receivers. The pattern supports loose coupling of the sender and the receivers.

We now run the following code.

```xpp
BusinessLogic1 object = new BusinessLogic1();
info(object.doSomething(33));
```

When this code is run, the system finds any method that wraps the **doSomething** method. The system randomly runs one of these methods, such as the **doSomething** method of the **BusinessLogic1_Extension** class. When the call to the next **doSomething** method occurs, the system randomly picks another method in the CoC. If no more wrapped methods exist, the system calls the original implementation.

## Supported versions
> [!IMPORTANT]
> The functionality that is described in this topic (CoC and access to protected methods and variables) is available in Platform update 9. However, the class that is being augmented must also be compiled on Platform update 9 or later. As of August 2017, all current releases of the applications for Finance and Operations have been compiled on Platform update 8 or earlier. Therefore, to wrap a method that is defined in a base package (such as Application Suite), you must recompile that base package on Platform update 9 or later.
As an example: If you create your own extension model that is augmenting a class that exists in the Application Suite model, and if you are using CoC or accessing protected methods/variables, you will need to build both Application Suite and your extension model. You will also need to create a deployable package that includes both models in order to deploy this functionality on a runtime environment.

## Capabilities
The following sections give more details about the capabilities of method wrapping and CoC.

### Wrapping public and protected methods
Protected or public methods of classes, tables, data entities, or forms can be wrapped by using an extension class. The wrapper method must have the same signature as the base method.

- When you augment form classes, only root-level methods can be wrapped. You can't wrap methods that are defined in nested classes.
- Currently, only methods that are defined in regular classes can be wrapped. Methods that are defined in extension classes can't be wrapped by augmenting the extension classes. This capability is planned for a future update.

### What about default parameters?
Methods that have default parameters can be wrapped by extension classes. However, the method signature in the wrapper method must not include the default value of the parameter.

For example, the following simple class has a method that has a default parameter.

```xpp
class Person 
{
    public void salute(str message = "Hi") {...}
}
```

In this case, the wrapper method must resemble the following example.

```xpp
[ExtensionOf(classStr(Person))]
final class APerson_Extension
{
    public void salute(str message)
    {
        // ...
    }
}
```

In the **APerson_Extension** extension class, notice that the **salute** method doesn't include the default value of the **message** parameter. 

### Wrapping instance and static methods
Instance and static methods can be wrapped by extension classes. If a static method is the target that will be wrapped, the method in the extension must be qualified by using the **static** keyword.

For example, we have the following **A** class.

```xpp
class A 
{
    public static void aStaticMethod(int parameter1)
    {
        // ...
    }
}
```
 
In this case, the wrapper method must resemble the following example.

```xpp
[ExtensionOf(classStr(A)]
final class An_Extension
{
    public static void aStaticMethod(int parameter1)
    {
        // ...
        next aStaticMethod(parameter1);
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
> If a method is replaceable, extenders don't have to unconditionally call **next** when wrapping the method by using chain of command. Although extenders can break the chain, the expectation is that they will only conditionally break it. The compiler doesn't enforce calls to **next** for methods with the attribute, **Replaceable**.  

### Wrapping a base method in an extension of a derived class
The following example shows how to wrap a base method in an extension of a derived class. For this example, the following class hierarchy is used.

```xpp
class A
{
    public void salute(str message)
    {   
        info(message);
    }
}

class B extends A {}
class C extends A {}
```

Therefore, there is one base class, **A**. Two classes, **B** and **C**, are derived from **A**. We will augment or create an extension class of one of the derived classes (in this case, **B**), as shown here.

```xpp
[ExtensionOf(classStr(B))]
final class B_Extension
{
    public void salute(str message)
    {
        next salute(message);
        info("B extension");
    }
}
```

Although the **B_Extension** class is an extension of **B**, and **B** doesn't have a method definition for the **salute** method, you can wrap the **salute** method that is defined in the base class, **A**. Therefore, only instances of the **B** class will include the wrapping of the **salute** method. Instances of the **A** and **C** classes will never call the wrapper method that is defined in the extension of the **B** class. 

This behavior becomes clearer if we implement a method that uses these three classes.

```xpp
class ProgramTest 
{
    public static void main(Args args)
    {
        var a = new A();
        var b = new B();
        var c = new C();

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
If a method is explicitly marked as **[Hookable(false)]**, the method can't be wrapped in an extension class. In the following example, **anyMethod** can't be wrapped in a class that augments **AnyClass1**.

```xpp
class AnyClass1 
{
    [Hookable(false)]
    public void anyMethod() {...}
}
```

> [!NOTE]
> For compatibility reasons, **[Hookable(false)]** overrides the behavior of chain of command in addition to pre- and post-handlers. However, **[Hookable(true)]** only applies to pre- and post-handlers and does not influence chain of command wrapping.

### Final methods and the Wrappable attribute
Public and protected methods that are marked as **final** can't be wrapped in extension classes. You can override this restriction by using the **Wrappable** attribute and setting the attribute parameter to **true** (**[Wrappable(true)]**). Similarly, to override the default capability for (non-final) public or protected methods, you can mark those methods as non-wrappable (**[Wrappable(false)]**).

In the following example, the **doSomething** method is explicitly marked as non-wrappable, even though it's a public method. The **doSomethingElse** method is explicitly marked as wrappable, even though it's a final method.

```xpp
class AnyClass2 
{
    [Wrappable(false)]
    public void doSomething(str message) {...}

    [Wrappable(true)]
    final public void doSomethingElse(str message) {...}
}
```


### Extensions of form-nested concepts such as data sources, data fields, and controls

In order to implement CoC methods for form-nested concepts, such as data sources, data fields, and controls, an extension class is required for each nested concept. 

#### Form data sources

In this example, **FormToExtend** is the form, **DataSource1** is a valid existing data source in the form, and **init** and **validateWrite** are methods that can be wrapped in the data source.

```C#
[ExtensionOf(formdatasourcestr(FormToExtend, DataSource1))]
final class FormDataSource1_Extension
{
    public void init()
    {
        next init();
        //...
        //use element.FormToExtendVariable to access form's variables and datasources
        //element.FormToExtendMethod() to call form methods
    }
 
    public boolean validateWrite()
    {
        boolean ret;
        //...
        ret = next validateWrite();
        //...
        return ret;
    }
}
```

#### Form data fields

In this example, a data field is extended. **FormToExtend** is the form, **DataSource1** is a data source in the form, **Field1** is a field in the data source, and **validate** is one of many methods that can be wrapped in this nested concept.

```C#
[ExtensionOf(formdatafieldstr(FormToExtend, DataSource1, Field1))]
final class FormDataField1_Extension 
{ 
    public boolean validate()
    {
        boolean ret
        //...
        ret = next validate();
        //...
        return ret;
    }
}
```

#### Controls

In this example, **FormToExtend** is the form, **Button1** is the button control in the form, and **clicked** is a method that can be wrapped on the button control.

```C#
[ExtensionOf(formControlStr(FormToExtend, Button1))]
final class FormButton1_Extension
{
    public void clicked()
    {
        next clicked();
        //...
    }
}
```

#### Requirements and considerations when you write CoC methods on extensions for form-nested concepts

- Like other CoC methods, these methods must always call **next** to invoke the next method in the chain, so that the chain can go all the way to the kernel or native implementation in the runtime behavior. The call to next is equivalent to a call to **super()** from the form itself to help guarantee that the base behavior in the runtime is always run as expected.
- Currently, the X++ editor in Microsoft Visual Studio doesn't support discovery of methods that can be wrapped. Therefore, you must refer to the system documentation for each nested concept to identify the correct method to wrap and its exact signature.
- You **cannot** add CoC to wrap methods that aren't defined in the original base behavior of the nested control type. For example, you can't add **methodInButton1** CoC on an extension. However, from the control extension, you can make a call into this method if the method has been defined as public or protected. Here is an example where the **Button1** control is defined in the **FormToExtend** form in such a way that it has the **methodInButton1** method.

    ```C#
    [Form]
    public class FormToExtend extends FormRun
    {
        [Control("Button")]
        class Button1
        {
            public void methodInButton1(str param1)
            {
                info("Hi from methodInButton1");
                //...
    ```

- You do **not** have to recompile the module where the original form is defined to support CoC methods on nested concepts on that form from an extension. For example, if the **FormToExtend** form from the previous examples is in the **ApplicationSuite** module, you don't have to recompile **ApplicationSuite** to extend it with CoC for nested concepts on that form from a different module.

### Extensions of tables and data entities

An extension class is required for each concept. 

#### Tables

In this example, **TableToExtend** is the table and **delete**, **canSubmitToWorkflow**, and **caption** are methods that can be wrapped in the table.

```C#
[ExtensionOf(tablestr(TableToExtend))]
final class TableToExtend_Extension
{
    public void delete()
    {
        next delete();
        //...
    }
 
     public boolean canSubmitToWorkflow(str _workflowType)
    {
        boolean ret;
        //...
        ret = next canSubmitToWorkflow(_workflowType);
        //...
        return ret;
    }
        
    public str caption()
    {
        str ret;
        //...
        ret = next caption();
        //...
        return ret;
    }
}
```

#### Data entities
In this example, **DataEntityToExtend** is the data entity and **validateDelete** and **validateWrite** are methods that can be wrapped in the data entity.

```C#
[ExtensionOf(tableStr(DataEntityToExtend))]
final class DataEntityToExtend_Extension
{
    public boolean validateDelete()
    {
        boolean ret;
        //...
        ret = next validateDelete();
        //...
        return ret;
    }

    public boolean validateWrite()
    {
        boolean ret;
        //...
        ret = next validateWrite();
        //...
        return ret;
    }
}
```

## Restrictions on wrapper methods
The following sections describe restrictions on the use of CoC and method wrapping.

### X++ classes that are compiled by using Platform update 8 or earlier 
The method wrapping feature requires specific functionality that is emitted by an X++ compiler that is part of Platform update 9 or later. Methods that are compiled by using earlier versions don't have the infrastructure to support this feature.

### Methods on types nested within forms can be wrapped in Platform update 16 and later
The ability to wrap methods on types nested within forms (data sources and controls) by using class extensions was added in Platform update 16. This means that Chain of Command can be used to provide overrides for data source methods and form control methods.

However, wrapping (extension) of purely X++ methods on those nested types (form controls and form data sources) is not yet supported like it is on other types (forms, tables, data entities). Currently, if a developer uses Chain of Command on purely X++ methods on types inside forms, then it compiles, but the extension methods are not invoked at runtime. This capability is planned for a future update.

### Unimplemented system methods on tables and data entities can be wrapped in Platform update 22 and later
The ability to wrap methods in nested classes by using class extensions was added in Platform update 16. The concept of nested classes in X++ applies to forms for overriding data source methods and form control methods.

### Next calls can be put inside try/catch/finally in Platform update 21 and later 
In a CoC extension method, the next call must not be called conditionally. However, in Platform update 21 and later next calls can be placed inside a try/catch/finally to allow for standard handling of exceptions and resource cleanup.

```C#
    public void someMethod()
    {
        try
        {
            //...
            next someMethod();
            //...
        }
        catch(Exception::Error)
        {
            //...
        }
    }
```

### Extensions of extensions are not yet supported
Currently, only methods that are defined in regular classes can be wrapped. Methods that are defined in extension classes can't be wrapped by augmenting the extension classes. This capability is planned for a future release.

### Extensions of constructors
Constructors cannot be extended. A **new** method that is defined on an extension class will define a constructor for the extension class itself. Additionally, the **new** method has to be public, and it can't have any arguments. For more information, see [Constructors](class-extensions.md#constructors).

### Tooling
For the features that are described in this topic, the Microsoft Visual Studio X++ editor doesn't yet offer complete support for cross-references and Microsoft IntelliSense.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
