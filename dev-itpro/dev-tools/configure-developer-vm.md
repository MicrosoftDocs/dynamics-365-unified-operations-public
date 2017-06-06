---
# required metadata

title: Configure a one-box development environment
description: This article describes recommended configurations of your one-box developer environment.
author: RobinARH
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 2051
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 23361
ms.assetid: 09dbb06c-dbc7-468d-a78e-e89a97a59fe6
ms.search.region: Global
# ms.search.industry: 
ms.author: robadawy
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Configure a one-box development environment

[!include[banner](../includes/banner.md)]


This article describes recommended configurations of your one-box developer environment.

Setup
-----

1.  Start Visual Studio, and on the toolbar, click **Dynamics 365 **&gt; **Options**.
2.  Expand the **Microsoft Dynamics** node, and then click **Projects**.
3.  Verify that the **Organize projects by element type** check box is selected, and click ****OK.****
4.  To view the line numbers in your code editor, select **Tools** &gt; **Options** &gt; **Text** **Editor** &gt; **All Languages**.
5.  Select the **Line numbers** check box.

 

## Debugging
For better performance of the X++ debugger, you might want to turn off IntelliTrace. IntelliTrace collects the complete execution history of an application. It is not supported for X++ debugging and causes performance issues in the IDE when debugging large packages like Application Suite. To turn off Intellitrace, click **Options** &gt; **IntelliTrace** &gt; **Enable IntelliTrace**, clear the check box, and then click **OK**. Note that Intellitrace is only available in the Enterprise version of Visual Studio 2015.    



