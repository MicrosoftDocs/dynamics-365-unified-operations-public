---
# required metadata

title: Class extension: Method wrapping and Chain of Commandf (CoC)
description: This topic discusses how to extend the business logic of public and protected methods using method wrapping. 
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

# Class extension: Method wrapping and Chain of Commandf (CoC)
Class extension functionality (also known as class augmentation) has been improved to allow you to wrap logic around methods defined in the base class being augmented. You can extend the logic of public and protected methods without using event handlers. When you wrap a method, you can also access public and protected methods and variables of the base class. This way, you can start transactions and easily manage state variables associated with your class.

Consider the following situation. A model contains the following code.
```
class BusinessLogic1
{
    str DoSomething(int arg) {
    …
    }
}
```
It is now possible to augment the functionality of the method **DoSomething** inside an extension class by reusing the same method name. An extension class must belong to a package that references the model where the augmented class is defined.
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
Wrapping **DoSomething** and the required use of the **next** keyword creates a Chain of Command (CoC) for the method. Here is what happens when the following code executes.
```
BusinessLogic1 c = new BusinessLogic1();
info(c.DoSomething(33));
```
The system will find any method that wraps the method **DoSomething**. It will randomly execute one of these methods, for example, **DoSomething** of the **BusinessLogic1_Extension** class. When the call to next **DoSomething** occurs, the system randomly picks another method in the CoC or calls the original implementation if no further wrapped methods exist.

## Supported versions
> [!IMPORTANT]
> The functionality described in this topic is available as of platform update 9 (CoC and access to protected methods and variables). However, this functionality requires the class being augmented to be compiled on platform update 9 or newer as well. As of August 2017, all current releases of the Dynamics 365 for Finance and Operations applications have been compiled on platform update 8 or earlier. You will then need to re-compile a base package (like Application Suite) on platform update 9 or newer in order to wrap a method that is defined in that package.

## Capabilities
The following sections describe in more details the capabilities of method wrapping and CoC.

### Wrapping public and protected methods
Protected or public methods of classes, tables or forms can be wrapped using an extension class that augments that class, table or form. The wrapper method must have the same signature as the base method.

- When augmenting form classes, only root level method can be wrapped. You cannot wrap methods defined in nested classes.
- Only methods defined in regular classes can be wrapped. Methods defined in extension classes cannot be wrapped by augmenting the extension class.

### What about default parameters?
Methods with default parameters can be wrapped by extension classes; however, the method signature in the wrapper method must not include the default value of the parameter. In other words, consider the following simple class with a method having a default parameter:
``` 
 class Person 
 {
     Public void salute( str message = “Hi”){ }
 }
```
The wrapper method must look like:
```
[ExtensionOf(classtr(Person))]
final class aPerson_Extension
{
    Public void salute( str message ){ }
}
```
Notice how in the extension class aPerson_Extension class, the salute method does not include the default value of the “message” parameter. 

## Wrapping instance and static methods
Instance and Static methods can be wrapped by extension classes. If a static method is the target to be wrapped, the method in the extension needs to be qualified with the static keyword. For example, if we have the following class A
```
class A 
{
   public static void aStaticMethod( int parameter1)
   {
   // …
   }
}
```
 
The wrapping method must look like:
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
Note: Wrapping static methods does not apply to forms. In X++, a form class is not really a new class and cannot be instantiated or referenced as a normal class. Static methods in forms do not have any semantics.
Wrapper Methods must always call next. 
Any wrapper method in an extension class must always call next, ensuring the next method in the chain and finally the original implementation are always called. This makes sure every method in the chain will contribute to the result.
The current implementation of this restriction forces the call to next to be in the first level statements in the method body.
Some rules important rules are:
* Call to next cannot be done conditionally inside an if statement. 
* Call to next cannot be done in a while, do-while, or for loop statements. 
* A next statement cannot be preceded by a return statement. 
* A call to next cannot be in logical expressions due to optimization of this type of expressions (At runtime, the execution of the complete expression is not guaranteed). 

## Wrap a base method in an extension of a derived class
The following example illustrates this capability. Assume the following class hierarchy:
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
Under this definition we have one base class A and two classes that derive from it, B and C. Let us augment (create an extension class) one of the derived classes, in this case B as follows:
```
[Extensionof(classstr(B))]
final class aB_Extension
{
   public void salute(str message)
   {
     next salute( message );
     Info(“B extension”);
   }
}
```
While the class aB_Extension is an extension of B, and B does not have a method definition for the salute method, it is still possible to wrap the salute method defined in the base class A. This means only instances of the class B will include the wrapping of the salute method. Instances of class A and class C will never call the the wrapper method defined in the extension of B. 
This gets clearer if we implement a method to use these three classes:
```
class ProgramTest 
{
   Public static void Main( Args _args)
   {
     var a = new A( );
     var b = new B( );
     var c = new C( );

     a.salute(“Hi”);
     b.salute(“Hi”);
     c.salute(“Hi”);
   }
}
```
In the case of a.salute(“Hi”), only the message “Hi”  is shown in the infolog. The same happens for the calls to c.salute(“Hi”). On the other hand, when b.salute(“Hi”) is called, the infolog will contain “Hi” followed by “B extension”. 
With this mechanism, it is possible to wrap the original method only for specific derived classes.

## Access protected members from extension classes
Access to protected members including fields and methods is now possible from extension classes, as of platform update 9. It is important to mention that this support is not specific to wrapping methods, but to all the methods in the class extension, making class extensions more powerful than before.

## The hookable attribute
If a method is explicitly marked as [Hookable(false)], the method cannot be wrapped in an extension class.
For example, anyMethod below cannot be wrapped in a class that augments anyClass1.
```
class anyClass1 
{
   [HookableAttribute(false)]
   public void anyMethod() {…}
}
```

## Final methods and the wrappable attribute
Public and protected methods that are marked as final cannot be wrapped in extension classes. However, this restriction can be overridden with the usage of wrappable attribute with the attribute parameter set to true, [Wrappable(true)].
Similarly, if you want to override the default capability for (non final) public or protected methods, you can mark them as non wrappable, [Wrappable(false)].
In the example below, the method doSomething is explicitly marked to by non-wrappable, even though it is a public method. The method doSomethingElse is explicitly marked to by wrappable, even though it is a final method.
```
class anyClass2 
{
   [Wrappable(false)]
   public void  doSomething(str message) { …}

   [Wrappable(true)]
   final public void  doSomethingElse(str message){ …}
}
```

# Restrictions on wrapper methods
The following describes restrictions on the use of CoC and method wrapping.

## No wrapping of kernel methods 
Kernel classes are classes defined in the kernel of the Dynamics 365 unified operations platform, they are not X++ classes. Even though extension classes are supported for kernel classes, method wrapping is not supported on methods of kernel classes. In other words, to wrap a method, the base method must be an X++ method.

## X++ classes compiled with platform update 8 or earlier 
Wrapping methods is a feature that requires specific functionality emitted by an X++ compiler that is part of platform update 9 or newer. Methods compiled with earlier versions do not have the infrastructure to support this feature.

## No wrapping of nested class methods (Forms)
Nested classes in X++ is a concept that applies to forms for overriding data source and form control methods. Methods nested classes cannot be wrapped in class extensions.

## Tooling
Support for cross reference and Intellisense (in the Visual Studio X++ Editor) for the features described in this topic is not complete. It is planned to be available starting in platform update 10.
