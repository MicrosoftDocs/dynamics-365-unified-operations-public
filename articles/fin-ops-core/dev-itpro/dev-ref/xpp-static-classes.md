---
title: X++ static class members
description: Learn about static classes in X++, including static methods, examples declared by using the static keyword, constructors, and instance methods.
author: josaw1
ms.author: josaw
ms.topic: language-reference
ms.date: 03/31/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# X++ static class members

[!include [banner](../includes/banner.md)]

This article describes static class members in X++. In general, use static methods for these cases:

- The method doesn't need to access member variables that are declared in the class.
- The method doesn't need to call any instance (non-static) methods of the class.

Declare static class members by using the **static** keyword. The **static** keyword instructs the system to create only one instance of the method, regardless of the number of instances of the class. Use this one instance throughout your session.

## Static methods

This section describes a scenario where a software key type is used to help prevent piracy. Each instance of a software key can have its own unique value. Because all software keys must conform to the rules of software key design, the logic that tests for software key conformance is the same for all software keys. Therefore, the method that contains the conformance validation logic should be static.

Here's an example of a method that's declared by using the **static** keyword.

```xpp
public class SoftwareKey
{
    static public boolean validateSoftwareKey(str _softwareKeyString)
    {
        // Your code here.
        return false;
    }
}
```

In the following example, you don't have to construct an instance of the **SoftwareKey** class before you call a static method on the class. When you want to call the static **validateSoftwareKey** method, the syntax starts with the name of the class that contains the method. A pair of colons (::) connects the class name to the static method name.

```xpp
boolean yourBool = SoftwareKey::validateSoftwareKey(yourSoftwareKeyString);
```

## Static fields

Static fields are variables that you declare by using the **static** keyword. Conceptually, they apply to the class, not to instances of the class.

## Static constructors

A static constructor always runs before any static or instance calls are made to the class. The execution of the static constructor is relative to the user’s session. The static constructor uses the following syntax.

```xpp
static void TypeNew()
```

You never explicitly call the static constructor. The compiler generates code to make sure that the constructor is called exactly one time before any other method on the class. Use a static constructor to initialize any static data or perform a particular action that must be performed only one time. You can't provide parameters for the static constructor, and you must mark it as **static**.

The following code example shows how to create a singleton instance by using a static constructor.

```xpp
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
```

The singleton guarantees that the class has only one instance. The following example shows how to instantiate the singleton.

```xpp
Singleton i = Singleton::Instance();
```

## Static method

Static methods, which are also known as *class methods*, belong to a class and are created by using the keyword **static**. You don't have to instantiate an object before you use static methods. Use static methods to work with data that's stored in tables. You can't use member variables in a static method. Use the following syntax to call static methods.

```xpp
ClassName::methodName();
```

## Static and instance methods

The accessor keywords on methods never restrict calls between two methods that are in the same class, regardless of which method is static or non-static. In a static method, calls to the **new** constructor method are valid even if the **new** constructor method is decorated with the **private** modifier. The syntax for these calls requires that you use the **new** keyword. The code in a static method must construct an instance object of its own class before it can call any instance methods on the class.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
