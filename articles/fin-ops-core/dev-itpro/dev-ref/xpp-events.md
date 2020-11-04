---
# required metadata

title: X++ event terminology and keywords
description: This topic describes event terminology and keywords in X++.
author: robinarh
manager: AnnBe
ms.date: 06/18/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
# ms.tgt_pltfrm: 
ms.custom: 150303
ms.assetid: 1b2d76d1-52d9-46b2-937f-5a3b62f2d516
ms.search.region: Global
# ms.search.industry: 
ms.author: rhaertle
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# X++ event terminology and keywords

[!include [banner](../includes/banner.md)]

This topic describes event terminology and keywords in X++. 

You can use the event design pattern to make your code more modular and reusable. The term *event* is a metaphor that explains how delegates are used. When something important occurs during a program run, other modules might have to process the occurrence. These important occurrences are known as *events*. When an event occurs, the program tells its notifier for the event that the notifier must send notifications about the event. A notification must be sent to all the event handlers that are subscribers of the notifier. When the program tells its notifier to send the notifications, we call that process *raising* an event. 

The following table shows the terms that are used to describe the event metaphor.

| Term          | Description                                                 |
|---------------|-------------------------------------------------------------|
| Event         | An important occurrence in a program module where additional modules must process the occurrence.    |
| Notifier      | The program element that sends information about the event to all the event handlers that are subscribed to the notifier. |
| Subscriber    | The program functions or methods that are subscribed to an event notifier.                          |
| Event handler | The methods that subscribe to an event notifier. Only the appropriate kind of methods can be event handlers.  |

## Keywords that are used for programming that uses delegates

The following table shows the keywords that describe the use of delegates.

| Keyword or term           | Code      | Description           |
|---------------------------|-----------|-----------------------|
| delegate                                | `delegate myDelegate(str information) {}`                                | The code shows what the delegate looks like in the code editor. Because the return type is always **void**, it isn't mentioned in the syntax. No code is allowed inside the braces ({}).                                                               |
| eventHandler                            | `myClassInstance.myDelegate += eventHandler(otherClass.myInstanceMethod);` | Although the syntax of the **eventHandler** keyword might give the impression that **eventHandler** is an X++ function, it isn't a function. The **eventHandler** keyword tells the compiler that a method is being subscribed to a delegate.         |
| Subscribe or add a method to a delegate | `myClassInstance.myDelegate += eventHandler(OtherClass::aStaticMethod);`   | In the code, the static method **OtherClass::aStaticMethod** becomes subscribed to the delegate.              |
| Call a delegate                         | `myClassInstance.myDelegate("Hello");`                                     | This call to the delegate prompts the delegate to call each method that is subscribed to the delegate. The subscribed methods are called in the same order in which they were added to the delegate. One subscribed method must be completed before the delegate calls the next method. |

## Example

The two classes in the following code example demonstrate how to define an event, subscribe to an event, and raise an event. The **PointWithEvent** class defines a delegate, **moved**. The **move** method calls the **moved** delegate, thereby notifing any objects that have subscribed to the event. The **PointKeeper** class defines the **writeMove** method and assigns it as the event handler for the **moved** delegate of the **Point** instance created in the **createAndMove** method. 

```xpp
class PointWithEvent
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

    void move(real x_offset, real y_offset)
    {
        x += x_offset;
        y += y_offset;
        this.moved(abs(x_offset) + abs(y_offset));
    }

    delegate void moved(real distance)
    {
    }

}

class PointKeeper
{

    public void createAndMove()
    {
        PointWithEvent point = new PointWithEvent(1.0, 2.0);

        point.moved += eventhandler(this.writeMove);

        point.move(4.0, 5.0);
        // Output is "9.0".
    }

    public void writeMove(real distance)
    {
        info(any2Str(distance));
    }

}
```
