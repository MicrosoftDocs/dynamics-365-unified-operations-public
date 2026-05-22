---
title: Class extension model in X++
description: Learn about the class extension model in X++, including overviews on the effective class concept and extension class variations.
author: pvillads
ms.author: pvillads
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/27/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: Platform update 1
ms.assetid: 271dabb1-ecb8-497f-b866-397733a954b8
---

# Class extension model in X++

[!include [banner](../includes/banner.md)]

This article describes the class extension model in X++.

An extension is a feature that you use to extend existing artifacts in a new model. You can extend both X++ code and metadata. This article describes how you can extend X++ code to add methods and state to artifacts defined in other models without recompiling those models.

X++ already supports a similar code extension mechanism that's modeled after the corresponding feature in C#. By using this extension mechanism, you can designate a class as an extension class through a naming convention and by hosting public static methods. These classes are a programming utility concept that you use to add methods to existing types, namely the type of the first parameter to the extension method. By using this approach, the method "extends" the new class with a method that it didn't originally have. This article describes the next step that offers a more capable and natural extension story. In object-oriented programming, the term *extend* has a well-defined meaning. When you say, "class B extends class A," you mean that B inherits from A, that A is B's parent class, and the usual object-oriented rules are implied. In X++ syntax, you use this term in class declarations to express this relationship. The term *extension* can describe metadata that has contributions from several models. *Class augmentation* designates the relationship between a class A in a base model and a class B in a model that depends on it. Class B provides additional functionality to class A in the context of that model. This article continues to use the term *extension class* because it's so prevalent.

## The effective class concept

It's useful to have a term for a class that consists of the public members of the augmented artifact and all the public members of all the class extensions that augment that artifact. This class is called the effective class in a given model. The following illustration shows an artifact, **MyArtifact**, that is defined in a base model, **MyModel**, and two dependent models that have extension classes for **MyArtifact**.

:::image type="content" source="./media/extensions-11.png" alt-text="Screenshot of artifact MyArtifact that is defined in base model MyModel, and two dependent models that have extension classes for MyArtifact.":::

In this example, the effective class is the class in the extension models that contains all the original methods and all the public artifacts from the extension classes. The effective class isn't the same in every model because it includes only the class extensions that are defined in a given model. The following illustration shows the effective class of **MyArtifact** in the **MyExtensionModel** model.

:::image type="content" source="./media/extensions-21.png" alt-text="Screenshot of the effective class of MyArtifact in MyExtensionModel.":::

You describe class extensions by using a class named **MyClass** in a model named **MyModel**.

```xpp
class MyClass
{
    public int mycState;
    public str mycMethod(int _arg)
    {
        // ...
    }
}
```

You can add new methods and state to **MyClass** by introducing an extension class in the extension model (**MyExtensionModel**) that builds on top of (that is, has a dependency on) **MyModel**.

## Extension class declarations

Extension classes are final classes that use the **ExtensionOf** attribute and have names that end with the **\_Extension** suffix. The name of the extension class is otherwise unimportant, but be consistent with your best practices. The class augments the artifact specified in the parameter of the **ExtensionOf** attribute, as shown in the following example.

```xpp
[ExtensionOf(classStr(MyClass))]
final class MyClass_Extension
{
    private void new()
    {
    }
}
```

Because the runtime system expresses the classes, it's not meaningful to derive from the extension class. Therefore, the extension class must be marked as **final**. The extension class **MyClass_Extension** doesn't extend the designated class (**MyClass**). Therefore, you can't override methods from **MyClass** in **MyClass_Extension**. In the example preceding, the **classStr** compile-time function designates the augmented class and serves two purposes:

- It produces a compilation error if the **MyClass** class doesn't exist.
- It informs the compiler about what kind of artifact is augmented. Artifact names by themselves don't uniquely identify a given artifact to augment. For example, forms can have the same names as tables, classes, and enums.

Any number of extension classes can augment a given artifact in a particular model. The runtime system directly references extension classes.

## Extension class inheritance

Any class that inherits from an augmented class also inherits the effective class. In other words, the classes that inherit from a class that has extensions inherit the methods defined in the extension classes.

## Constructors

The following section describes restrictions and requirements for constructors in extension classes.

### Instance constructors

The instance constructor is the method named **new**. Constructors are useful for initializing the state of the extension objects. The instance constructor defined in an extension class can't have parameters. The runtime system creates instances of the extension classes and calls their constructors as required by the usage scenario. Your code never explicitly calls these constructors. It's guaranteed that the constructor provided in an extension class is called once before any instance method or the instance state on the extension class is accessed. However, if no such references are made, the constructor isn't called.

### Static constructors

Static constructors are the parameterless static methods named **typenew**. You can define static constructors on extension classes. The runtime system calls the constructor exactly once before the first reference to the extension type. You can't assume any particular order of invocation for static construction among a set of extensions. Be careful about referencing static data from other classes in static constructors.

## Methods

Extension classes define public methods that add functionality to the augmented class within the model where you define the extension class. Only public methods are exposed this way. You can define private methods to help implement the public methods, but those private methods aren't part of the effective class. Because extension classes are final, don't mark methods as **protected** since you can't create derived classes to override the method.

### Instance methods

The following example defines an extension method named **ExtensionMethod** in a class that augments **MyClass**.

```xpp
[ExtensionOf(classStr(MyClass))]
final class MyClass_Extension
{
    private void new()
    {
    }
    public int ExtensionMethod(int arg)
    {
    }
}
```

The public instance method (**ExtensionMethod**) is defined in the extension class. It's available as if it were defined in **MyClass** in the context of the model where you define the extension class. The following example shows how to call the method in the model.

```xpp
MyClass c = new MyClass();
print c.ExtensionMethod(32); // Call the extension method from MyClass_Extension on the instance of the class
```

As shown, you use the instance method defined in the extension class as an instance method on the augmented artifact. An extension method can access public and protected members only from the artifact that it augments. This behavior is by design. No artifact can interact directly with state and methods that are explicitly hidden through the **private** or **internal** keywords. Otherwise, direct interaction with explicitly hidden state and methods could cause malfunction by invalidating key implementation assumptions in those artifacts. Methods and statements in the method body can use the **this** keyword. In this context, the type of **this** is the effective class of the augmented artifact.

### Static methods

If you define methods as public and static in the extension class, they're available as static methods on the artifact that you augment.

```xpp
[ExtensionOf(classStr(MyClass))]
final class MyClass_Extension
{
    private void new()
    {
    }
    public int method1(int arg)
    {
    }
    public static real CelsiusToFahrenheit(real celsius)
    {
        return (celsius * 9.0 / 5.0) + 32.0;
    }
}
```

The following example shows how to call the method in the model.

```xpp
var temp = MyClass::CelsiusToFahrenheit(20.0);
```

A static method can access the public static methods and state in the effective class of the augmented artifact. As an interesting side effect, static extension methods on the **Global** class become available in the language as functions, which are available without any prefix.

## State

In addition to providing static and instance methods to an artifact, you can add instance state and static state.

### Instance state

You can specify instance state, which is state that pertains to a particular instance of an artifact, on extension classes. The following example defines a state named **state**.

```xpp
[ExtensionOf(classStr(MyClass))]
final class MyClass_Extension
{
    public int state;
    private void new()
    {
    }
}
```

The following example shows how to use **state** in your code.

```xpp
MyClass c = new MyClass();
c.state = 12;
```

### Static state

Static state applies to the type, not instances of the type. The following example defines a static member called **staticState** in the Extension class that augments the **MyClass** class.

```xpp
[ExtensionOf(classStr(MyClass))]
final class MyClass_Extension
{
    public int state;
    public static int staticState;
    static void TypeNew()
    {
        staticState = 77;
    }
}
```

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
