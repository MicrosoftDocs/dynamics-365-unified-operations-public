---
# required metadata

title: Update Visual Studio development tools | Microsoft Docs
description: This topic explains how to update the development tools.
author: RobinARH
manager: AnnBe
ms.date: 2016-02-09 23:23:12
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: 61
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 33571
ms.assetid: e7f0859f-74e5-484f-9ead-443a01d7d319
ms.region: Global
# ms.industry: 
ms.author: robadawy

---

# Update Visual Studio development tools

This topic explains how to update the development tools.

Use this tutorial to update your Visual Studio development tools with a new version. It explains how to uninstall your existing Visual Studio development tools and install the new extension. The new extension is in the form of an installable VSIX file. This file is a part of the binary hotfix available on the Dynamics Lifecycle Services (LCS) site. The VSIX file is located in the **DevToolsService\\Scripts** folder of the binary hotfix package. Whenever you update a developer machine with an AOS binary hotfix, it is also recommended to install the development tools that are packaged within the same binary hotfix.

## Uninstall the existing Visual Studio extension
In order to install a new version of the development tools, you'll need to uninstall the existing version first. Verify the version of the development tools that you have installed. If you don't have it installed, you can skip this section.

### Verify your current version of the Visual Studio extension

1.  Open the Visual Studio **Help &gt; About Microsoft Visual Studio** dialog and find **Dynamics 365 for Operations Developer Tools**.
2.  Select it and click **OK**.

### Uninstall the extension

1.  Open the Visual Studio **Tools &gt; Extensions and Updates** dialog. [![ToolsExtensionsUpdates\_DevoToolsHotfix](./media/toolsextensionsupdates_devotoolshotfix.png)](./media/toolsextensionsupdates_devotoolshotfix.png)
2.  Select **Dynamics 365 for Operations Visual Studio Tools** and click **Uninstall**. [![](./media/vsextensions2.jpg)](./media/vsextensions2.jpg)
3.  When the extension is uninstalled, exit Visual Studio.

## Install a new version of the extension
1.  Make sure Visual Studio is not running.
2.  Double-click (or right-click and **Open**) the VSIX file of the new version.
3.  Follow the installation instructions.
4.  When installation is complete, you can start Visual Studio and start developing your application.


