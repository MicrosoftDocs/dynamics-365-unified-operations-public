---
# required metadata

title: Configure a one-box development environment
description: This article describes recommended configurations of your one-box developer environment.
author: RobinARH
manager: AnnBe
ms.date: 2015-12-11 23 - 19 - 58
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 23361
ms.assetid: 27c1d08a-1105-4fad-bd9b-adeb3e66a548
ms.search.region: Global
# ms.search.industry: 
ms.author: robadawy
ms.dyn365.intro: Feb-16
ms.dyn365.version: AX 7.0.0

---

# Configure a one-box development environment

This article describes recommended configurations of your one-box developer environment.

Setup
-----

1.  Start Visual Studio, and on the toolbar, click **AX **&gt; **Options**.
2.  Expand the **Microsoft Dynamics** node, and then click **Projects**.
3.  Verify that the **Organize projects by element type** check box is selected, and click ****OK.**** [![OptionsProjects](./media/optionsprojects.jpg)](./media/optionsprojects.jpg)
4.  To view the line numbers in your code editor, select **Tools** &gt; **Options** &gt; **Text** **Editor** &gt; **All Languages**.
5.  Select the **Line numbers** check box.

[![](./media/2.png)](./media/2.png)

## Debugging
For better performance of the X++ debugger, you might want to turn off IntelliTrace. IntelliTrace collects the complete execution history of an application. It is not supported for X++ debugging and causes performance issues in the IDE when debugging large packages like Application Suite. To turn off Intellitrace, click **Options** &gt; **IntelliTrace** &gt; **Enable IntelliTrace**, clear the check box, and then click **OK**. Note that Intellitrace is only available in the Enterprise version of Visual Studio 2015. [![optionsIntellitrace](./media/optionsintellitrace.jpg)](./media/optionsintellitrace.jpg)  

