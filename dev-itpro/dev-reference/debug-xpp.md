---
# required metadata

title: Debug X++ code
description: This topic reviews how you can debug X++ code by using the debugging feature in Microsoft Visual Studio. 
author: RobinARH
manager: AnnBe
ms.date: 2015-12-11 23 - 34 - 19
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 61
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 23921
ms.assetid: 6be739c0-30da-4f91-97be-a8764fb8078c
ms.search.region: Global
# ms.search.industry: 
ms.author: robadawy
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Debug X++ code

This topic reviews how you can debug X++ code by using the debugging feature in Microsoft Visual Studio. 

To debug X++ code, you use the debugger in Microsoft Visual Studio. The process is similar to the process that is used for any other application that is created in Visual Studio. For example, the standard tools for examining the application are available when your code is stopped at a breakpoint.

## Debug your code
To debug X++ code, follow these steps.

1.  In Visual Studio, open the X++ code to debug.
2.  Find the line or lines where you want execution to stop, and set breakpoints in those lines. To set a breakpoint in a line, click in the left column of the code editor or press F9 while the cursor is on that line. A red dot indicates that a breakpoint has been set. [![32\_DevoToolsConcept](./media/32_devotoolsconcept.png)](./media/32_devotoolsconcept.png)
3.  Set a startup project and a startup object. Startup objects can be any form, any class that has the **main** method, or any menu item. You can set the startup object in the **Properties** pane for the project. Alternatively, right-click the element in Solution Explorer, and then click **Set as Startup Object**.![setasstartupobject](./media/setasstartupobject.jpg)
4.  On the **Debug** menu, click **Start Debugging**.
5.  In the application, perform the action that causes the code that you're interested in to run. Typical actions include opening a form. Processing stops at the breakpoints that you set. [![33\_DevoToolsConcept](./media/33_devotoolsconcept.png)](./media/33_devotoolsconcept.png)
6.  Use the tools in Visual Studio to examine the application. For example, you can hover over variables in the X++ code to see their values. You can also use commands on the **Debug** menu to step through the code. Additionally, tools such as the **Autos** pane in Visual Studio will show important information about the state of the application. [![34\_DevoToolsConcept](./media/34_devotoolsconcept.png)](./media/34_devotoolsconcept.png)Another tool that is specific to Dynamics 365 for Operations is the Infolog. Often, **info()** statements are added to code to log status messages while the application is running. You can view these Infolog messages directly in Visual Studio. On the **View** menu, click **Infolog**. [![35\_DevoToolsConcept](./media/35_devotoolsconcept.png)](./media/35_devotoolsconcept.png)
7.  After you've finished debugging the application, exit Dynamics 365 for Operations. Visual Studio will exit debugging mode.


See also
--------

[Technical Concepts Guide](developer-landing-page.md)

[https://ax.help.dynamics.com/en/wiki/technical-concepts-guide/](https://ax.help.dynamics.com/en/?p=178721)

