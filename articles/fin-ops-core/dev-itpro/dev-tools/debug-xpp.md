---
title: Debug X++ code by using the debugger in Visual Studio
description: This article reviews how you can debug X++ code by using the debugging feature in Microsoft Visual Studio.
author: gianugo
ms.date: 06/20/2017
ms.topic: article
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: gianura
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 6be739c0-30da-4f91-97be-a8764fb8078c
---

# Debug X++ code by using the debugger in Visual Studio

[!include [banner](../includes/banner.md)]

This article reviews how you can debug X++ code by using the debugging feature in Microsoft Visual Studio.

To debug X++ code, you use the debugger in Microsoft Visual Studio. The process is similar to the process that is used for any other application that is created in Visual Studio. For example, the standard tools for examining the application are available when your code is stopped at a breakpoint.

## Debug your code

To debug X++ code, follow these steps.

1. In Visual Studio, open the X++ code to debug.
2. Find the line or lines where you want execution to stop, and set breakpoints in those lines. To set a breakpoint in a line, click in the left column of the code editor or press F9 while the cursor is on that line. A red dot indicates that a breakpoint has been set.

   [![Red dot.](./media/32_DevoToolsConcept.png)](./media/32_DevoToolsConcept.png)

3. Set a startup project and a startup object. Startup objects can be any form, any class that has the **main** method, or any menu item. You can set the startup object in the **Properties** pane for the project. Alternatively, right-click the element in Solution Explorer, and then click **Set as Startup Object**.

   ![Set as startup object.](./media/setasstartupobject.jpg)

4. On the **Debug** menu, click **Start Debugging**.
5. In the application, perform the action that causes the code that you're interested in to run. Typical actions include opening a form. Processing stops at the breakpoints that you set.

   [![Run.](./media/33_DevoToolsConcept.png)](./media/33_devotoolsconcept.png)

6. Use the tools in Visual Studio to examine the application. For example, you can hover over variables in the X++ code to see their values. You can also use commands on the **Debug** menu to step through the code. Additionally, tools such as the **Autos** pane in Visual Studio will show important information about the state of the application.

   [![Hover.](./media/34_DevoToolsConcept.png)](./media/34_devotoolsconcept.png)

   Another tool that is specific to finance and operations applications is the Infolog. Often, **info()** statements are added to code to log status messages while the application is running. You can view these Infolog messages directly in Visual Studio. On the **View** menu, click **Infolog**.

   [![Infolog.](./media/35_DevoToolsConcept.png)](./media/35_devotoolsconcept.png)

7. After you've finished debugging the application, exit the application. Visual Studio will exit debugging mode.

## Add ToString methods to your classes

It's often a benefit to add **ToString** methods to your classes. The effort spent doing this comes back many times and it's easy to do.

> [!NOTE]
> Since ToString methods can be called at unpredictable times, it isn't a good idea to change the state of the object in the **ToString** method.

## Identify unselected fields

It's a common source of bugs to use fields from a table when those fields don't appear in the field list in a **select** statement. Such fields will have a default value according to their type. You can use debugger breakpoints to determine if a value has been selected or not.

Consider the following code:

```xpp
class MyClass
{
    public static void Main(Args a)
    {
        FMRental rental;
        select EndMileage, RentalId from rental;
        rental.Comments = "Something";
    }
}
```

Set a breakpoint on the assignment statement. Make your class the startup object in your project, and start by pressing F5. When the breakpoint is encountered, view the `rental` variable by expanding it in the **Locals** window. The fields that have been selected, `EndMileage` and `RentalId`, appear with their selected values, while the unselected fields appear as `null`. This means that their values weren't fetched from the database. Obviously, this is a debugging artifact. The values of the unselected fields will be the default value for the type of the field. Step over this and notice how the debugger changes the rendering to the actual value.

> [!NOTE]
> If the table is set to Cache, the system will always fetch all fields from the entire table, irrespective of the field list provided in the code.

## The Auto and Infolog windows

The debugger lets you easily access certain parts of the state of the application. This information is available in the **Autos** window, where the current company, the partition, the transaction level, and the current user ID are listed.

![Autos window.](./media/autos_debugfeatures.png)

There is also a window showing the data that is written to the Infolog.

![Infolog window.](./media/infolog_debugfeatures.png)

## Breakpoint features

The Visual Studio debugger supports conditional breakpoints and breakpoints that are triggered by hit count. You can also have the system perform specific actions for you as you hit the breakpoint.

- **Hit count** enables you to determine how many times the breakpoint is hit before the debugger breaks execution. By default, the debugger breaks execution every time that the breakpoint is hit. You can set a hit count to tell the debugger to break every 2 times the breakpoint is hit, or every 10 times, or every 512 times, or any other number you choose. Hit counts can be useful because some bugs don't appear the first time your program executes a loop, calls a function, or accesses a variable. Sometimes, the bug might not appear until the 100th or the 1000th iteration. To debug such a problem, you can set a breakpoint with a hit count of 100 or 1000.
- **Condition** is an expression that determines whether the breakpoint is hit or skipped. When the debugger reaches the breakpoint, it'll evaluate the condition. The breakpoint will be hit only if the condition is satisfied. You can use a condition with a location breakpoint to stop at a specified location only when a certain condition is true. For example, suppose you're debugging a banking program where the account balance is never allowed to go below zero. You might set breakpoints at certain locations in the code and attach a condition such as `balance < 0` to each one. When you run the program, execution will break at those locations only when the balance is less than zero. You can examine variables and program state at the first breakpoint location, and then continue execution to the second breakpoint location, and so on.
- **Action** specifies something that should occur when the breakpoint is hit. By default, the debugger breaks execution, but you can choose to print a message or run a Visual Studio macro instead. If you decide to print a message instead of breaking, the breakpoint has an effect very similar to a Trace statement. This method of using breakpoints is called trace points.

### Using breakpoints with conditions

Consider the following code:

```xpp
class PVsClass
{
    public static void Main(Args a)
    {
        int i;
        for (i = 0; i < 10; i++)
        {
            print i;
        }
    }
}
```

Put a breakpoint on the print statements by pressing F9 while that statement is selected. This will create a normal, unconditional breakpoint. Now, use the mouse to open the context menu for the breakpoint and select **Condition**. Put in a condition that indicates that the breakpoint should happen when the value of the 'i' variable exceeds 5. Set the class as a startup project, and the class containing the code as the startup item in the project. Run the code. Feel free to modify the value of 'i' using the debugger. Now, remove this breakpoint, and use the Hit count feature to accomplish the same thing.

> [!NOTE]
> A breakpoint can have several conditions. It's often helpful to hover the cursor over the breakpoint, causing an informative tooltip to appear. Trace points are often useful to trace execution. Insert a trace point on the line in question and log the value of the variable. The trace output will appear in the output window in the debugger.

## The Immediate window

The **Immediate** window is a debugger feature that lets you enter expressions and statements to evaluate at any given time. This feature isn't implemented in the X++ stack. However, you can still benefit from the immediate window. The snippets must be expressed in C\#, not in X++.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

