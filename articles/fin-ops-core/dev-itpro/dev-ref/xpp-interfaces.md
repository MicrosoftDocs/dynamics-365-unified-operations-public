---
title: X++ interfaces
description: Learn about interfaces in X++, which specify sets of public instance methods, define, and enforce similarities between unrelated classes.
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

# X++ interfaces

[!include [banner](../includes/banner.md)]

An *interface* specifies a set of public instance methods. An interface defines and enforces similarities between unrelated classes without requiring one class to derive from the other.

All interfaces are public, even if you don't explicitly add the **public** keyword in front of the **interface** keyword in the interface declaration. The methods on an interface are also public. Explicit inclusion of the keyword **public** is optional.

To create an interface, follow these steps:

1. In Server Explorer, right-click the project, and then select **Add**.
1. In the **New Item** dialog box, select **Interface**, and then enter a name for the interface.
1. Select **Add**.

When you add the **implements** keyword on a class declaration, the class must declare and define the methods that the interface specifies. A class declaration can implement multiple interfaces. List the interfaces after the single occurrence of the **implements** keyword, and separate the interface names by using commas.

You must explicitly declare all interface methods that a class implements as **public**. You must also declare a class that implements an interface as **public**. An interface can extend another interface by using the **extends** keyword. However, an interface can't extend more than one interface.

Prefix the name of an interface with `I`.

## Interface example

In the following code example, the **Automobile** class implements the **IDrivable** interface. The **is** keyword tests whether a class implements an interface.

```xpp
interface IDrivable
{
    int getSpeed()
    {
    }

    void setSpeed(int newSpeed)
    {
    }
}

class Automobile implements IDrivable
{
    int speed;

    public int getSpeed()
    {
        return speed;
    }

    public void setSpeed(int newSpeed)
    {
        speed = newSpeed;
    }
}

class UseAnAutomobile
{
    void DriveAutomobile()
    {
        IDrivable drivable;
        Automobile myAutomobile = new Automobile();
        str temp;

        myAutomobile = new Automobile();

        if (myAutomobile is IDrivable)
        {
            drivable = myAutomobile;
            drivable.setSpeed(42);
            temp = int2str(drivable.getSpeed());
        }
        else
        {
            temp = "Instance is not an IDrivable.";
        }

        info(temp);
    }
}
```

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
