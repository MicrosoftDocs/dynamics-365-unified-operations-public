---
# required metadata

title: X++ interfaces
description: This topic describes interfaces in X++.
author: RobinARH
manager: AnnBe
ms.date: 06/17/2019
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
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 150303
ms.assetid: 1b2d76d1-52d9-46b2-937f-5a3b62f2d516
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Interfaces

[!include [banner](../includes/banner.md)]

This topic describes interfaces in X++. An <em>interface</em> is a specification for a set of public instance methods. An interface defines and enforces similarities between unrelated classes without having to derive one class from the other. All interfaces are public, even if you don't explicitly add the <strong>public</strong> keyword *<strong><em>in front of the *</em>interface</strong> keyword *<strong><em>in the *</em>classDeclaration</strong> code. The methods on an interface are also public. Once again, explicit inclusion of the keyword <strong>public</strong> is optional. To create an interface, follow these steps.

1.  In Server Explorer, right-click the project, and then click **Add**.
2.  In the **New Item** dialog box, select **Interface**, and then enter a name for the interface.
3.  Click **Add**.

When you add the **implements** keyword on a class declaration, the class must declare the methods that are specified by the interface. A class declaration can implement multiple interfaces. Just list the interfaces after the single occurrence of the **implements** keyword, and separate the interface names by using commas. All interface methods that a class implements must be explicitly declared as **public** by using the **public** keyword in the class. A class that implements an interface must also be declared as **public**. An interface can extend another interface by using the **extends** keyword. However, an interface can't extend more than one interface.

## Interface example

In the following example, an **Automobile** class implements an **IDrivable** interface. The **is** keyword is supported and lets you test whether a class implements an interface.

    public interface IDrivable
    {
        public int getSpeed()
        {
        }

        public void setSpeed(int newSpeed)
        {
        }
    }

    class Automobile implements IDrivable
    {
        int m_speed;

        public int getSpeed()
        {
            return m_speed;
        }

        public void setSpeed(int newSpeed)
        {
            m_speed = newSpeed;
        }
    }

    class UseAnAutomobile
    {
        void DriveAutomobile()
        {
            IDrivable yourIDrivable;
            Automobile myAutomobile;
            str sTemp = "object is not an IDrivable";

            myAutomobile = new Automobile();

            if (myAutomobile is IDrivable)
            {
                yourIDrivable = myAutomobile;
                yourIDrivable.setSpeed(42);
                sTemp = int2str(yourIDrivable.getSpeed());
            }

            Global::info(sTemp);
            return;
            // output
            // Message (06:46:33 pm)
            // 42
        }
    }

