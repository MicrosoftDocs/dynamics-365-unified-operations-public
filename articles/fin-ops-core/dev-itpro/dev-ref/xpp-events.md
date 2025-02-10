---
title: Events and delegates
description: Learn aboutevent terminology and keywords in X++, including a table that outlines descriptions for various terms used to describe event metaphors.
author: josaw1
ms.author: josaw
ms.topic: language-reference
ms.date: 08/27/2021
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Events and delegates

[!include [banner](../includes/banner.md)]

This article describes event terminology and keywords in X++.

You can use the event design pattern to make your code more modular and reusable. The term *event* is a metaphor that explains how delegates are used. When something important occurs during a program run, other modules might have to process the occurrence. These important occurrences are known as *events*. When an event occurs, the program tells its notifier for the event that the notifier must send notifications about the event. A notification must be sent to all the event handlers that are subscribers of the notifier. When the program tells its notifier to send the notifications, we call that process *raising* an event.

A delegate can be defined in a table, form, or query, and not just in a class.

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

The two classes in the following code example demonstrate how to define an event, subscribe to an event, and raise an event. The **PointWithEvent** class defines a delegate, **moved**. The **move** method calls the **moved** delegate, thereby notifying any objects that have subscribed to the event. The **PointKeeper** class defines the **writeMove** method and assigns it as the event handler for the **moved** delegate of the **Point** instance created in the **createAndMove** method.

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

## Event handlers and Pre/Post methods

In legacy X++, it was possible to prescribe in metadata that certain methods were to be executed prior to and after the execution of a method. The information about what subscribes call was recorded on the publisher, which isn't useful in the environment. It's now possible to provide Pre and Post handlers through code, by providing the SubscribesTo attribute on the subscribers.

### Example of pre and post methods

```xpp
[PreHandlerFor(classStr(MyClass2), methodstr(MyClass2, publisher))]
public static void PreHandler(XppPrePostArgs arguments)
{
    int arg = arguments.getArg("i");
}

[PostHandlerFor(classStr(MyClass2), methodstr(MyClass2, publisher))]
public static void PostHandler(XppPrePostArgs arguments)
{
    int arg = arguments.getArg("i");
    int retvalFromMethod = arguments.getReturnValue();
}

public int Publisher(int i)
{
    return 1;
}
```

This example shows a publishing method called Publisher. Two subscribers are enlisted with the PreHandlerFor and PostHandlerFor. The code shows how to access the variables, and the return values.

This feature is provided for backward compatibility and, because the application code doesn't have many delegates, to publish important application events. Pre and Post handlers can easily break as the result of added or removed parameters, changed parameter types, or because methods are no longer called, or called under different circumstances. Attributes are also used for binding event handlers to delegates:

```xpp
[SubscribesTo(
    classstr(FMRentalCheckoutProcessor),
    delegatestr(FMRentalCheckoutProcessor, RentalTransactionAboutTobeFinalizedEvent))]
public static void RentalFinalizedEventHandler(
    FMRental rentalrecord, Struct rentalConfirmation)
{
}

    delegate void RentalTransactionAboutTobeFinalizedEvent(
        FMRental fmrentalrecord, struct RentalConfirmation)
{
}
```

In this case, the SubscribesTo attribute specifies that the method RentalFinalizedEventHandler should be called when the FmRentalCheckoutProcessor.RentalTransactionAboutToBeFinalizedEvent delegate is called. Since the binding between the publisher and subscribers is done through attributes, there's no way of specifying the sequence in which subscribers are called.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
