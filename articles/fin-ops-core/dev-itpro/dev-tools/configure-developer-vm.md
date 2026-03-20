---
title: Configure one-box development environments
description: Learn about the recommended configurations of your one-box developer environment, including overviews for setup and debugging environments.
author: josaw1
ms.author: josaw
ms.topic: how-to
ms.date: 02/26/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 09dbb06c-dbc7-468d-a78e-e89a97a59fe6
---

# Configure one-box development environments

[!INCLUDE [banner](../includes/banner.md)]

This article describes recommended configurations for your one-box developer environment.

## Setup

1. Start Visual Studio, and on the toolbar, select **Dynamics 365** > **Options**.
1. Expand the **Microsoft Dynamics** node, and then select **Projects**.
1. Verify that the **Organize projects by element type** check box is selected, and select **OK**.
1. To view the line numbers in your code editor, select **Tools** &gt; **Options** &gt; **Text** **Editor** &gt; **All Languages**.
1. Select the **Line numbers** check box.



## Debugging
For better performance of the X++ debugger, turn off IntelliTrace. IntelliTrace collects the complete execution history of an application. It's not supported for X++ debugging and causes performance issues in the IDE when debugging large packages like Application Suite. To turn off Intellitrace, select **Options** &gt; **IntelliTrace** &gt; **Enable IntelliTrace**, clear the check box, and then select **OK**. Intellitrace is only available in the Enterprise version of Visual Studio.        





[!INCLUDE [footer-include](../../../includes/footer-banner.md)]
