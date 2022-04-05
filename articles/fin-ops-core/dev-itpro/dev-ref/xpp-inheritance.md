---
title: X++ inheritance
description: This topic describes inheritance in X++.
author: tonyafehr
ms.date: 06/18/2019
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: tfehr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# X++ inheritance

[!include [banner](../includes/banner.md)]

This topic describes inheritance in X++, including how to create a subclass and override a method.

## Creating a subclass
*Subclasses* are classes that extend or inherit from other classes. A class can extend only one other class. Multiple inheritance isn't supported. If you extend a class, the subclass inherits all the methods and variables in the parent class (the *superclass*). Subclasses let you reuse existing code for a more specific purpose. Therefore, they help save you time during design, development, and testing. To customize the behavior of a superclass, override the methods in a subclass. A superclass is often known as a *base class*, and a subclass is often known as a *derived class*.

### Subclass example

The following example first creates a class that is named **Point**. It then extends the **Point** class to create a new class that is named **ThreePoint**.

```xpp
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
```

### Preventing class inheritance

You can prevent classes from being inherited by using the **final** modifier.

```xpp
public final class Attribute
{
    int objectField;
}
```

## Overriding a method
The methods in a class are inherited by any class that extends the class. To change the functionality of an inherited method, you create a method in the subclass, and then give that method the same name and parameters as the method in the superclass. This process is known as *overriding* the method. 

When you instantiate the subclass, you can assign the reference to either a variable of the superclass type or the subclass type. Regardless of the type of the variable, the overridden method is called. 

In the following code example, the subclass overrides the **write** method. Two variables, both of type **Point** are created. One is assigned a **Point** object, the other is assigned a **ThreePoint** object. When the **write** method is called on the **ThreePoint** object, the **ThreePoint** version of the method is called.

```xpp
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

    void write()
    {
        info("(" + any2Str(x) + ", " + any2Str(y) + ")");
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

    void write()
    {
        info("(" + any2Str(x) + ", " + any2Str(y) + ", " + any2Str(z) + ")");
    }

}

// Code that creates Point objects and calls the write method.
Point point2 = new Point(1.0, 2.0);
Point point3 = new ThreePoint(3.0, 4.0, 5.0);

point2.write();
// Output is "(1.0, 2.0)".

point3.write();
// Output is "(3.0, 4.0, 5.0)".
```


### Preventing method overrides

Static methods can't be overridden, because they exist per class. To protect other sensitive methods, or core methods, from being overridden, use the **final** modifier. In the following example, because **methodAtt** is declared as **final**, it can't be overridden in any class that extends **Attribute**. You should not specify **new** or **finalize** methods as **final**. 

The following example shows how to use the **final** keyword.

```xpp
public class Attribute
{
    int objectVariable;

    final void methodAtt()
    {
        //Some statements
    }
}
```

### Overriding vs. overloading

Overriding occurs when the superclass's implementation of a method is changed by the subclass's implementation of that method, but the signatures of both methods are the same. 

By contrast, *overloading* occurs when more than one method has the same name, but the methods have different signatures (return types, parameter lists, or both). X++ supports overriding, but it doesn't support overloading.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
